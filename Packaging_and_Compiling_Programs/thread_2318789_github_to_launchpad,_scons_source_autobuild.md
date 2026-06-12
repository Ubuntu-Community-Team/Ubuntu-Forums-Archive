---
title: "github to launchpad, scons source autobuild"
date: 2016-03-29
forum: Packaging and Compiling Programs
---

### Post by greensoma on 2016-03-29
Hey there,

I have a project which gets developed on github. It gets build via scons. I want to create deb packages for this app via launchpad.
Yesterday i tried to import the source from git to bzr/launchpad but it failed with some strange python errors.

```
Traceback (most recent call last):
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/scripts/code-import-worker.py", line 96, in <module>
    sys.exit(script.main())
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/scripts/code-import-worker.py", line 91, in main
    return import_worker.run()
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/lib/lp/codehosting/codeimport/worker.py", line 583, in run
    return self._doImport()
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/lib/lp/codehosting/codeimport/worker.py", line 737, in _doImport
    inter_branch.fetch(limit=revision_limit)
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/bzrplugins/git/branch.py", line 722, in fetch
    self.fetch_objects(stop_revision, fetch_tags=fetch_tags, limit=limit)
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/bzrplugins/git/branch.py", line 745, in fetch_objects
    determine_wants, self.source.mapping, limit=limit)
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/bzrplugins/git/fetch.py", line 718, in fetch_objects
    limit)
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/bzrplugins/git/fetch.py", line 484, in import_git_objects
    mapping.revision_id_foreign_to_bzr)
  File "/srv/importd.launchpad.net/production/launchpad-rev-17967/bzrplugins/git/mapping.py", line 334, in import_commit
    raise UnknownCommitExtra(commit, [item[0] for item in commit.extra])
bzrlib.plugins.git.errors.UnknownCommitExtra: Unknown extra fields in <Commit 6e87314d83a9beab56fdd115277e230ef683c53d>: ['gpgsig'].
Import failed:
Traceback (most recent call last):
Failure: twisted.internet.error.ProcessTerminated: A process has ended with a probable error condition: process ended with exit code 1.
```

Does someone know whats going on there? Is it even possible to build a project with scons on launchpad? Is there maybe another way to get a PPA up and running?

---

