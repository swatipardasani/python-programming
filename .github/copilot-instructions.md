# copilot-instructions for python-programming

Purpose
- Short guidance for AI coding agents to be immediately productive in this repository.

Repository snapshot (big picture)
- This is a small teaching/demo repo of Python/Jupyter learning materials stored under [CODES/](CODES).
- Major components: a set of topic notebooks ([notebook1.ipynb..notebook8_filehandling.ipynb](CODES)), a central cheat sheet (`cheat_sheet_codes.ipynb`), an example Java program ([CODES/javahello.java](CODES/javahello.java)), and small data files ([CODES/data.db](CODES/data.db), [CODES/data.xml](CODES/data.xml)).
- There is no service-oriented architecture, CI, or packaging: treat changes as educational content updates rather than production deploys.

Key files to inspect first
- [CODES/cheat_sheet_codes.ipynb](CODES/cheat_sheet_codes.ipynb): condensed examples and the best entry point for patterns used across notebooks.
- [CODES/notebook6_functions.ipynb](CODES/notebook6_functions.ipynb) and [CODES/notebook7_classes.ipynb](CODES/notebook7_classes.ipynb): show canonical code style used in exercises.
- [CODES/gcp_connection.ipynb](CODES/gcp_connection.ipynb): may include external integration notes (do not expose credentials).

Developer workflows & commands
- Run and edit notebooks via VS Code or Jupyter Lab. Typical commands in the dev container:

```bash
# start Jupyter in workspace root
jupyter lab --no-browser --port=8888

# compile/run the Java example
javac CODES/javahello.java && java -cp CODES HelloWorld
```

- There are no automated tests or build scripts; treat PRs as content revisions. If adding Python packages, include a `requirements.txt` at repo root.

Project-specific conventions
- Notebooks are topic-scoped and named `notebookX_*`. Add new examples as small, focused cells; prefer runnable, idempotent cells (no hidden state assumptions).
- Data and example assets live under `CODES/`—keep relative paths inside notebooks (e.g., `CODES/data.db`) and avoid absolute paths.
- Avoid committing secrets: `gcp_connection.ipynb` may reference GCP — do not add credential files; flag secrets to maintainers if discovered.

Integration points and externals
- Only obvious external integration is GCP (see `CODES/gcp_connection.ipynb`). Expect that notebooks may assume user-level credentials configured in the environment.

How to update content (PR guidance)
- For small edits: update the relevant notebook and create a short PR describing the learning goal.
- When changing examples that create files, ensure notebooks clean up or write to `CODES/tmp/` to avoid cluttering the repo.

Prompt examples for editing tasks
- "Update [CODES/notebook6_functions.ipynb](CODES/notebook6_functions.ipynb) to include a recursive factorial example with input validation and a tiny test cell." 
- "Refactor [CODES/cheat_sheet_codes.ipynb](CODES/cheat_sheet_codes.ipynb) to add a `pandas` example reading `CODES/data.db` and show the first 5 rows. Add a one-line note about how to create the DB." 

What not to do
- Don't assume CI, unit tests, or packaging — this repo is educational. Don't add or commit credentials.

If anything is unclear or you need more context, ask the maintainers for the intended learning objective before making large edits.

-- End of instructions
