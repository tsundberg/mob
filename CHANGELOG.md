# 1.0.0 (unreleased)
- BREAKING: Changed default behavior of MobNextStay=false to MobNextStay=true.
- BREAKING: wip branch name 'mob-session' of base branch 'master' no longer supported. Instead, every wip branch uses the naming pattern 'mob/<base-branch-name>'. So, for the base branch 'master' the wip branch name is now 'mob/master'.
- BREAKING: with `mob start --branch green` on the base branch `master` the wip branch is now named `mob/master__green`.

# 0.0.26
- Adds way to configure the voice command via the environment variable `MOB_VOICE_COMMAND`.
- Allow disabling voice or notification by setting the environment variables `MOB_VOICE_COMMAND` or `MOB_NOTIFY_COMMAND` to an empty string.
- Fixes a bug where a failure in executing the voice command would lead to omitting the notification.
- `mob config` now shows the currently used `MOB_VOICE_COMMAND` and `MOB_NOTIFY_COMMAND`.
- Add `mob next --message "custom commit message"` as an option to override the commit message during `mob next`.

# 0.0.25
- Adds flag `--return-to-base-branch` (with shorthand `-r`) to return to base branch on `mob next`. Because 'mob' will change the default behavior from returning to the base branch to staying on the wip branch on `mob next`, this flag provides the inverse operation of `--stay`. If both are provided, the latter one wins.
- Adds flag `-i` as a shorthand notation for `--include-uncommitted-changes`.
- Fixes a bug that prevented `mob start` to work when on an outdated the WIP branch 
- `mob next` push if there are commits but no changes.

# 0.0.24
- Fixes a bug where mob couldn't handle branch names with the '/' character 

# 0.0.23
- Commit message of wip commits is no longer quoted (see #52)

# 0.0.22
- Adds `mob start --branch <branch>` to allow multiple wip branches in the form of 'mob/<base-branch>/<branch>' for a base branch. For example, when being on branch 'main' a `mob start --branch green` would switch to a wip branch named 'mob/main/green'.
- Adds `mob moo` (Thanks Niko for the idea)
- Deprecated `MOB_DEBUG` in favor of the parameter `--debug`
- Deprecated `MOB_START_INCLUDE_UNCOMMITTED_CHANGES` in favor of the parameter `--include-uncommitted-changes` instead
- Show warning if removed configuration option `MOB_BASE_BRANCH` or `MOB_WIP_BRANCH` is used.

# 0.0.20
- `mob start` on a branch named `feature1` will switch to the branch `mob/feature1` and will merge the changes back to `feature1` after `mob done`. For the `master` branch, the `mob-session` branch will still work (but this may change in the future, switching to `mob/master` at some point).
- Removes configuration options for base branch and wip branch. These are no longer necessary.
- `mob status` added. Thanks to Jeff Langr for that contribution! 

# 0.0.19
- Removes zoom screen share integration.
- Less git commands necessary for 'mob start'
- Mob automatically provides sound output on windows without any installation

# 0.0.18
- Fixes a bug where boolean environment variables such as `MOB_NEXT_STAY` set to any value (including empty value) falsely activated their respective option.
- Simplified `mob start` when joining a mob session. It uses `git checkout -B mob-session origin/mob-session` to override any local `mob-session` in the process. It reduces the amount of commands necessary and makes the mob tool more predictable: the `origin/mob-session` always contains the truth.
- Removes `mob share` command. You can still enable the zoom integration via `mob start 10 share` although this is now DEPRECATED and will eventually be removed in the future.

# 0.0.16
- `mob start` prints out untracked files as well 
- `mob start --include-uncommitted-changes` now includes untracked files in the stash 'n' pop as well 
- keying in an unknown command like `mob conf` will internally call `mob help` to print out the usage options instead of calling `mob status`
- fixed a bug where overriding `MOB_START_INCLUDE_UNCOMMITTED_CHANGES` via an environment variable could print out a wrong value (didn't affect any logic, just wrong console output)

# 0.0.15
- Any `git push` command now uses the `--no-verify` flag

# 0.0.14
- New homepage available at https://mob.sh
- `mob config` prints configuration using the environment variable names which allow overriding the values

# 0.0.13
- Fixes bug that prevented users wih git versions below 2.21 to be able to use 'mob'.
