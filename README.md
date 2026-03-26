# custom-mcp-servers

Custom-built MCP Servers
A suite of MCP (Model Context Protocol) servers built for Quality Engineering and SDLC workflows, enabling AI assistants to capture network traffic, generate test plans, and produce API specifications — all through natural language.
MCP Servers:
All servers run on a remote machine and communicate with the AI assistant via HTTP transport. Prompts are defined as /.github/prompts/*.prompt.md files (not @mcp.prompt() decorators).
Server				Port	Public Tools	Description
-----------------------------------------------------------------
DevTools to HAR		8001	10				Captures live network traffic from Chrome/Edge via CDP; returns HAR 1.2 JSON content
JMeter				8002	7				Creates JMeter 5.4.3 / OpenJDK 11 test plans (.jmx) from HAR content or OpenAPI 3.0.3 specs; returns JMX strings
OpenAPI				8003	6				Generates OpenAPI 3.0.3 specs from Spring Boot source code or HAR traffic; merges and validates specs
Rest Assured		8004	5				Generates Java API functional test frameworks (Cucumber + Rest Assured + TestNG) from OpenAPI specs or HAR traffic
WireMock			8006	5				Converts HAR traffic into WireMock 3.9.1 stub mapping files (.json) with response body files
Postman				8007	9				Generates Postman Collection v2.1 JSON, environments, and Newman CI/CD configs from HAR or OpenAPI
Playwright			8008	6				Generates Playwright + TypeScript test projects with page objects from HAR or OpenAPI
Contract Testing	8009	6				Generates Pact v4 contracts and Spring Cloud Contract Groovy DSL from OpenAPI or HAR

Note: Each server includes a health-check tool (included in the counts above) that returns server name, version, status, and uptime.

Requirements:
-Python 3.10+
-Chrome/Chromium/Edge with --remote-debugging-port=9222 --remote-debugging-address=0.0.0.0 (launched locally on the client machine; MCP server connects over the intranet)
-See requirements.txt for Python packages (fastmcp, requests, urllib3, PyYAML)

Further Reading:
Topic	Resource
MCP Specification	modelcontextprotocol.io
FastMCP Framework	FastMCP GitHub
Chrome DevTools Protocol	chromedevtools.github.io
HAR 1.2 Spec	softwareishard.com/blog/har-12-spec
OpenAPI 3.0.3 Spec	swagger.io/specification/v3
Rest Assured	rest-assured.io
Cucumber	cucumber.io/docs
TestNG	testng.org
WireMock	wiremock.org
Postman / Newman	learning.postman.com
Playwright	playwright.dev
Pact	docs.pact.io
Spring Cloud Contract	spring.io
