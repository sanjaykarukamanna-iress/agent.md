## Test-Driven Development (TDD)

Strictly follow **Red-Green-Refactor**:

1. **Plan & Review**: Create a concise plan for all TDD cycles. Get user review and explicit approval before writing code.
2. **Red**: Write a failing test first.
3. **Green**: Write minimal code to pass the test.
4. **Refactor**: Clean code while tests pass.
5. **Commit & Review**:
* Make a commit after completing each TDD cycle.
* Ask for a user review immediately after each commit.
* Wait for explicit user confirmation before proceeding to the next commit/task.
* **Rebase & Resolve**: Immediately after each commit, rebase onto the base branch (`git rebase <base-branch>`) and fix any merge conflicts that arise.



### Inside-Out Layer Workflow

When breaking down and implementing features, always progress from the most internal, independent layers outward to the consumer layers. Complete each layer's implementation **and** its tests (fully green via Red-Green-Refactor) before starting the layer that depends on it. Depend inward only: if an outer layer needs new inner-layer behaviour, drop back to the inner layer, add it test-first, and get it green before resuming.

## Post-Task Execution (Skills)

* **Fresh Session & Clean Context**: The post-task execution skill must run in a completely fresh session with a new context once core work wraps up.
* **Skill Execution**: After all implementation and TDD tasks are completely finished and approved, invoke the following skill:
* Skill Name/Command: `/code-review`


* Do not run this skill until the full core workflow is completed.
* **Interactive Suggestion Review**:
* Present suggestions **one by one**.
* For each suggestion, wait for explicit user feedback (`yes`, `no`, or specific modification requests).
* Any implementation or changes driven by a suggestion must also strictly follow all preceding guidelines (TDD cycle, signed commits, commit formatting, only staging modified files, and user review after each commit).



## Observability

* **Foresee & Support Observability**: Design and implement with system visibility in mind. Ensure meaningful telemetry, structured logging, tracing, and actionable metrics are baked in from the start to make troubleshooting, debugging, and system health checks straightforward in production.

## Code Quality & Scope

* **Unmodified Files**: Do not stage or commit any files that were not modified.
* **Comments**: Add clear, concise comments whenever necessary to explain complex logic or non-obvious code decisions.

## Communication & Code Standards

* **Concise Output**: Omit filler, greetings, and fluff. Communicate only essential facts, status, and questions.
* **Mental Map & Diagrammatic Breakdown**:
* Communicate using visual diagrams (e.g., ASCII/Mermaid) and simple, clear language.
* Break down information so the reader develops an immediate, clear mental map of the system or workflow.
* Avoid over-explaining every basic term; instead, focus on giving the reader/programmer a crisp understanding of **what** changes are being made and the **reasoning** behind them.



## Git & Branching Strategy

* **Feature Branch Confirmation**: Whenever starting a new feature, always ask the user explicitly whether they want to create and work in a dedicated feature branch before making any changes.
* **Signed Commits**: Always sign all commits (`git commit -S`).
* **Format**: Follow this structure strictly:

```
Capitalized, short (50 chars or less) summary

More detailed explanatory text, if necessary. Wrap it to about 72
characters or so. In some contexts, the first line is treated as the
subject of an email and the rest of the text as the body. The blank
line separating the summary from the body is critical (unless you omit
the body entirely); tools like rebase can get confused if you run the
two together.

Write your commit message in the imperative: "Fix bug" and not "Fixed bug"
or "Fixes bug." This convention matches up with commit messages generated
by commands like git merge and git revert.

Further paragraphs come after blank lines.

- Bullet points are okay, too

- Typically a hyphen or asterisk is used for the bullet, followed by a
  single space, with blank lines in between, but conventions vary here

- Use a hanging indent

```