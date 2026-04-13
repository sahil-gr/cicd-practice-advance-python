🔥 1. Policy-as-Code PR Gatekeeper (Enterprise Level)

💡 Problem

Build a CLI tool that:

	Uses GitHub App authentication
	Runs on PR events
	Fetches PR files + diffs
	Enforces policies from a YAML config
	
🧩 Requirements
		Parse config like:
		```yaml
			rules:
			  - name: no-plain-secrets
			    file_patterns: ["*.yaml", "*.yml"]
			    regex: "password: .*"
			    action: fail

			  - name: terraform-tag-check
			    file_patterns: ["*.tf"]
			    required_tags: ["owner", "env"]
		```
		Use API to:
			* Get PR changed files
			* Read patch/diff

		Apply rules dynamically

		Post PR comment with violations

🚀 Advanced Twist

	Parallelize file processing
	Add retry logic + rate limit handling
	Support both:
		GitHub App
		PAT fallback