---
name: xquik-x-data
description: Use when the user needs to search, extract, summarize, or automate X data with Xquik through its public REST API, OpenAPI spec, or remote MCP manifest. Covers setup, choosing REST or MCP, source checks, API-key hygiene, and result handling.
license: Apache-2.0
---

# Xquik X Data Skill

Use this skill when a user wants to work with X data through Xquik.

## Source Links

- Public API spec: `https://xquik.com/openapi.json`
- Remote MCP manifest: `https://xquik.com/.well-known/mcp.json`
- Public repository: `https://github.com/Xquik-dev/x-twitter-scraper`

## Workflow

1. Check the OpenAPI spec or MCP manifest before naming exact endpoints, tools, or request fields.
2. Use REST for application code, scripts, batch exports, and webhook-backed workflows.
3. Use the remote MCP manifest when the user is configuring an MCP-capable agent.
4. Keep API keys in environment variables or the user's approved secret store. Never print keys.
5. Return compact results by default: query used, result count, key fields, and next-page guidance.
6. For larger jobs, ask for the time range, target accounts or keywords, output format, and maximum records.

## Guardrails

- Do not describe private infrastructure or unsupported routing details.
- Do not scrape X directly when the user asked to use Xquik.
- Do not invent endpoint names. Verify them from the OpenAPI spec first.
- Do not make pricing, coverage, or freshness claims unless the current public docs state them.

## Common Task Patterns

### Search X Posts

1. Fetch the OpenAPI spec.
2. Locate the tweet search operation.
3. Build the request from the documented schema.
4. Include authentication using a secret environment variable.
5. Normalize output into the user's requested format.

### Configure Remote MCP

1. Fetch the MCP manifest.
2. Confirm the server name, version, and repository link.
3. Add the remote MCP URL using the user's client-specific configuration format.
4. Test with a read-only query before using the setup in a larger workflow.

### Analyze Results

Summaries should separate:

- Source query and filters.
- Number of records returned.
- Time range represented in the data.
- Top accounts, posts, topics, or links relevant to the user's question.
- Missing data or pagination that may affect conclusions.
