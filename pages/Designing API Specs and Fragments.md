id:: 6ae04245-3a28-4d09-a35a-ae4209a343be

- [Designing API Spec and Fragments](https://docs.mulesoft.com/anypoint-code-builder/des-designing-api-specs)
- Creating a New API Specification Project
  - Upon creation of an API specification project, Anypoint Code Builder creates a hollow API specification. For example, this OAS 3.0 (YAML) specification:
    - ```
      openapi: "3.0.0"
      info:
        version: 1.0.0
        title: OAS Example
      paths: {}
      ```
- [Generating Code in MuleSoft Vibes](https://docs.mulesoft.com/anypoint-code-builder/mulesoft-vibes#how-mulesoft-vibes-generates-code)
  - MuleSoft Vibes uses MuleSoft-optimized AI pipelines to generate high-quality code for API specifications and integration flows. The pipelines are exposed to MuleSoft Vibes through these MCP tools:
    - `generate_mule_flow`
    - `generate_api_spec`
  - Because these tools run on pipelines optimized specifically for MuleSoft use cases, users typically receive higher-quality code outputs (on average, 60% better) compared to generic generation.
  - [MuleSoft DX MCP Server](https://docs.mulesoft.com/mulesoft-mcp-server/getting-started) enables AI-powered development assistants in your IDE to interact with Anypoint Platform, helping you manage APIs, applications, and platform resources directly from your coding environment.
- [MuleSoft DX MCP Server `generate_api_spec` Tool](https://docs.mulesoft.com/mulesoft-mcp-server/reference-mcp-tools#generate-api-spec)
  - Prerequisites:
    - Logging in to Anypoint Code Builder with your Anypoint Platform credential
    - Enabled Einstein in Access Management
  - With the following parameters:
    - `language = oas`
    - `languageVersion = 3.0`
    - `specSyntax = yaml`
  - And with the following prompt:
    - > Create a REST API for a pet store with endpoints to list pets, get pet by ID, create a new pet, update a pet, and delete a pet. Include proper error responses.
  - The tool generates an API specification like this:
    - ```
      openapi: 3.0.0
      info:
        title: Pet Store API
        version: 1.0.0
      paths:
        /pets:
          get:
            summary: List all pets
            responses:
              '200':
                description: Successful response
          post:
            summary: Create a new pet
            requestBody:
              required: true
              content:
                application/json:
                  schema:
                    type: object
                    properties:
                      name:
                        type: string
                      category:
                        type: string
        /pets/{id}:
          get:
            summary: Get pet by ID
            parameters:
              - name: id
                in: path
                required: true
                schema:
                  type: string
            responses:
              '200':
                description: Successful response
              '404':
                description: Pet not found
      ```
- Using MuleSoft Vibes to scaffold the API specification
  - [To design an API spec with MuleSoft Vibes](https://docs.mulesoft.com/anypoint-code-builder/vibes-api-ai-create-spec#design-spec-ai), enter a message that describes your API specification.
  - Include these required details and consider including optional details to generate precise spec:
    - Base details:
      - > Optionally provide the API name, version, and description.
    - Security Details:
      - > Include a required security scheme of Basic Authentication, Digest Authentication, or Pass Through. Specify responses, query parameters, and headers.
        >
        > The following additional details apply:
        >
        > **Header Requirements**
        >
        > Headers must include the name, whether it’s required, and one of the following types:
        >
        >   - Array
        >   - Boolean
        >   - Date only
        >   - DateTime
        >   - DateTime only
        >   - File
        >   - nil
        >   - Number
        >   - Object
        >   - String
        >   - Time only
        >
        > Optionally, provide a description, format, minimum and maximum length, default value, and example for the header.
        >
        > **Query Parameter Requirements**
        >
        > Query parameters must include the name, whether it’s required, and one of the following types:
        >
        >   - Array
        >   - Boolean
        >   - Date only
        >   - DateTime
        >   - DateTime only
        >   - File
        >   - nil
        >   - Number
        >   - Object
        >   - String
        >   - Time only
        >
        > Optionally, provide a description, format, minimum and maximum length, default value, and example for the query parameter.
        >
        > **Response Requirements**
        >
        > Responses must include the status code and description.
    - Resources and Methods
      - > **Resource Requirements**
        >
        > Each resource can include one or more of the following methods:
        >
        >   - GET
        >   - POST
        >   - PUT
        >   - PATCH
        >   - DELETE
        >   - HEAD
        >   - OPTIONS
        >
        > For GET and HEAD methods, you can include a summary, responses, requests, and query or header parameters.
        >
        > For POST, PUT, PATCH, and OPTIONS methods, you can include a summary, responses, requests, body, and query or header parameters.
        >
        > **Response Requirements**
        >
        > Responses must include the status code and description. Response bodies are optional and can include a description, type, media type, and example.
        >
        > **Request Requirements**
        >
        > Requests must include a description and body.
        >
        > **Header Requirements**
        >
        > Headers must include the name, whether it’s required, and one of the following types:
        >
        >   - Array
        >   - Boolean
        >   - Date only
        >   - DateTime
        >   - DateTime only
        >   - File
        >   - nil
        >   - Number
        >   - Object
        >   - String
        >   - Time only
        >
        > Optionally, provide a description, format, minimum and maximum length, default value, and example for the header.
        >
        > **Query Parameter Requirements**
        >
        > Query parameters must include the name, whether it’s required, and one of the following types:
        >
        >   - Array
        >   - Boolean
        >   - Date only
        >   - DateTime
        >   - DateTime only
        >   - File
        >   - nil
        >   - Number
        >   - Object
        >   - String
        >   - Time only
        >
        > Optionally, provide a description, format, minimum and maximum length, default value, and example for the query parameter.
  -