Archives list and review status of patches in mm.git, per tree and subsystem.

This repository contains patches in
[mm.git](https://git.kernel.org/pub/scm/linux/kernel/git/akpm/mm.git/) trees
(`mm-hotfixes-stable`, `mm-hotfixes-unstable`, `mm-stable`, `mm-unstable`,
`mm-new`, `mm-nonmm-stable`, `mm-nonmm-unstable`), and their review status.
It also contains the summary of the changes on the data since last update, and
the data per selected subsystems.  The purpose is to help high level view of
the development and review status.

The data is updated by the owner of this repo, usually once per day or twice.
The update is done via
[mm_tree_snapshot.sh](https://github.com/sjp38/lazybox/blob/master/linux_hack/mm_tree_snapshot.sh).

Review Status
=============

The review status is defined based on who authored and who reviewed the given
patch.  The author/reviewers are identified using roles of the subsystems for
the patch, based on `MAINTAINERS` file.  Reviewers of a given patch are
identified using `Reviewed-by:` and `Acked-by:` tags of the patch.  Hence,
below 12 categories exist:

    Author        Reviewer
    ------------------------
    no-role       nobody
    no-role       no-role
    no-role       reviewer
    no-role       maintainer

    reviewer      nobody
    reviewer      no-role
    reviewer      reviewer
    reviewer      maintainer

    maintainer    nobody
    maintainer    no-role
    maintainer    reviewer
    maintainer    maintainer

Data Structure
==============

The data is organized in files as below:

`patches/`
---------

`patches/` directory contains the patch files.  Files under the directory
having `.series` suffix list the baseline and the list of patches on the branch
of the file name.  For example, `patches/mm-new.series` file contains the list
of patches on `mm-new` tree.

`summary/`
----------

`summary/` directory contains the summarized data, including counts, review
status and list of patches per tree, in files.

`summary.md` shows counts of patches in each tree, categorized by their review
status.

`full_commits_list.md` file shows the full list of the commits per branch, with
review status per commit.

`changes_from_last_update.md` file shows the changes on the summarized data,
that made since the last update on this repo.

`subsystem/` directory contains directories of subsystem names.  Each of the
directory contains `summary.md`, `full_commits_list.md` and
`changes_from_last_update.md` files for the given subsystem.  For example,
`summary/subsystem/DAMON/summary.md` file contains the data for patches that
touching DAMON subsystem sourcee files.  The list of subsystems is manually
added and hard-coded on 
[mm_tree_snapshot.sh](https://github.com/sjp38/lazybox/blob/master/linux_hack/mm_tree_snapshot.sh).

`commits_info.json` contains full data.  It is being used for making the
`changes_from_last_update.md` file.  It could also be used for printing the
data in custom format.
