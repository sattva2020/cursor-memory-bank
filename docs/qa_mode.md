# QA Mode Playbook

The Memory Bank QA functions act as on-demand validation layers that can be triggered from any mode. They rely on the enhanced flow described in the [QA Mode Visual Map](../.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc) and reuse the phase guidance defined in the level-specific workflows (`Level2`, `Level3`, and `Level4`). This document explains when to call QA, which commands to use, and which checks will execute.

## When to Run QA

| Scenario | Recommended Command | Purpose |
| --- | --- | --- |
| **Quick health check during any phase** | `QA` | Runs the universal Memory Bank, task tracking, and reference consistency checks before returning to the active workflow. |
| **Gate after CREATIVE before BUILD** | `VAN QA` | Executes the full VAN QA technical validation to confirm readiness for implementation-heavy workstreams. |
| **Mid-implementation spot check** | `QA` | Validates recent progress updates while ensuring IMPLEMENT tasks remain aligned with [Level 2 workflow expectations](../.cursor/rules/isolation_rules/Level2/workflow-level2.mdc) or the more comprehensive [Level 3 implementation standards](../.cursor/rules/isolation_rules/Level3/implementation-intermediate.mdc). |
| **Pre-release sweep on complex projects** | `QA` followed by `VAN QA` | Combines universal QA with the phased gate defined in the [Level 4 phased implementation playbook](../.cursor/rules/isolation_rules/Level4/phased-implementation.mdc) to ensure all checkpoints are satisfied. |

> 💡 **Tip:** QA commands pre-empt any ongoing instruction. Once you type `QA` or `VAN QA`, the system pauses other work until validation finishes.

## What QA Validates

The QA Mode Visual Map breaks the process into universal checks plus phase-aware validations:

- **Universal Validation:** Confirms Memory Bank files (`projectbrief.md`, `activeContext.md`, `tasks.md`, `progress.md`) exist, are in sync, and have accurate cross-references before continuing.【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L8-L77】
- **Task Tracking Verification:** Ensures `tasks.md` reflects current scope, status, and dependencies so the task list remains the single source of truth.【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L79-L112】
- **Reference Validation:** Verifies that documentation cites the correct Memory Bank entries and maintains bidirectional links.【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L114-L142】
- **Phase-Specific Validation:** Applies targeted rules depending on the active phase (VAN, PLAN, CREATIVE, IMPLEMENT) to confirm that phase deliverables are complete before resuming the workflow.【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L144-L204】

## Level-Aware QA Expectations

QA inherits expectations from the complexity-level instructions, so run the command that matches your current task level:

- **Level 2 — Simple Enhancements:** Ensure initialization, planning, and implementation checkpoints from the [Level 2 workflow](../.cursor/rules/isolation_rules/Level2/workflow-level2.mdc) are satisfied before accepting QA success.
- **Level 3 — Intermediate Projects:** Cross-check QA results with the [Level 3 workflow](../.cursor/rules/isolation_rules/Level3/workflow-level3.mdc) and the [implementation standards](../.cursor/rules/isolation_rules/Level3/implementation-intermediate.mdc) to confirm tasks and documentation stay comprehensive.
- **Level 4 — Advanced Builds:** Use QA as a gate between stages of the [Level 4 phased implementation roadmap](../.cursor/rules/isolation_rules/Level4/phased-implementation.mdc), which embeds QA checkpoints before advancing to the next milestone.【F:.cursor/rules/isolation_rules/Level4/phased-implementation.mdc†L232-L276】

## Command Reference

| Command | Use It When | Output |
| --- | --- | --- |
| `QA` | You need an anytime validation sweep aligned with the active phase. | Generates a phase-aware success or failure report and lists remediation steps if issues are found.【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L206-L212】【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L216-L237】 |
| `VAN QA` | You want the dedicated VAN QA technical validation gate after CREATIVE or before BUILD. | Produces the comprehensive VAN QA validation report and blocks BUILD access until passing results are recorded.【F:.cursor/rules/isolation_rules/visual-maps/van_mode_split/van-mode-map.mdc†L245-L276】 |

## Reports and Follow-Up

Successful QA runs update the Memory Bank and let you resume work immediately; failures provide targeted fixes and instruct you to rerun QA after remediation.【F:.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc†L206-L237】 For VAN QA, refer to the [dedicated report templates](../.cursor/rules/isolation_rules/visual-maps/van_mode_split/van-qa-utils/reports.mdc) to understand the output format and failure messaging.

## Additional Resources

- [QA Mode Visual Map](../.cursor/rules/isolation_rules/visual-maps/qa-mode-map.mdc) — full process flow and command precedence rules.
- [Van Mode QA Utilities](../.cursor/rules/isolation_rules/visual-maps/van_mode_split/van-qa-utils/reports.mdc) — canned reports and remediation prompts for VAN QA.
- [Level 2 Workflow](../.cursor/rules/isolation_rules/Level2/workflow-level2.mdc), [Level 3 Workflow](../.cursor/rules/isolation_rules/Level3/workflow-level3.mdc), [Level 4 Phased Implementation](../.cursor/rules/isolation_rules/Level4/phased-implementation.mdc) — level-specific checkpoints QA expects to see completed.
