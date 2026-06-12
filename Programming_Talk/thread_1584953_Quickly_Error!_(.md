---
title: "Quickly Error! :("
date: 2010-09-29
forum: Programming Talk
---

### Post by pivotraze on 2010-09-29
Okay, so I just started on my first Quickly project, and it failed to build it. Here is my command and it's response:
```
cody@cody-laptop:~$ quickly create ubuntu-application GSchoolNotes
Creating project directory gschoolnotes
Creating bzr repository and commiting
Traceback (most recent call last):
  File "/usr/share/quickly/templates/ubuntu-application/create.py", line 114, in <module>
    wt.commit("Initial project creation with Quickly!")
  File "<string>", line 4, in commit_write_locked
  File "/usr/lib/python2.6/dist-packages/bzrlib/workingtree_4.py", line 197, in commit
    result = WorkingTree3.commit(self, message, revprops, *args, **kwargs)
  File "<string>", line 4, in commit_write_locked
  File "/usr/lib/python2.6/dist-packages/bzrlib/mutabletree.py", line 200, in commit
    *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/bzrlib/commit.py", line 286, in commit
    possible_master_transports=possible_master_transports)
  File "/usr/lib/python2.6/dist-packages/bzrlib/cleanup.py", line 131, in run
    self.cleanups, self.func, self, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/bzrlib/cleanup.py", line 165, in _do_with_cleanups
    result = func(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/bzrlib/commit.py", line 402, in _commit
    self.config, timestamp, timezone, committer, self.revprops, rev_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/branch.py", line 708, in get_commit_builder
    timestamp, timezone, committer, revprops, revision_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/repository.py", line 1765, in get_commit_builder
    timestamp, timezone, committer, revprops, revision_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/repofmt/pack_repo.py", line 117, in __init__
    revprops=revprops, revision_id=revision_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/repository.py", line 114, in __init__
    self._committer = self._config.username()
  File "/usr/lib/python2.6/dist-packages/bzrlib/config.py", line 280, in username
    raise errors.NoWhoami()
bzrlib.errors.NoWhoami: Unable to determine your name.
Please, set your name with the 'whoami' command.
E.g. bzr whoami "Your Name <name@example.com>"
ERROR: create command failed
Aborting

```

---

### Post by Some Penguin on 2010-09-29
```

bzrlib.errors.NoWhoami: Unable to determine your name.
Please, set your name with the 'whoami' command.
E.g. bzr whoami "Your Name <name@example.com>"

```

Have you actually done this?

---

### Post by pivotraze on 2010-09-29
Just ran the "whoami" command. Here is running then running what I'm trying:

```
cody@cody-laptop:~$ whoami
cody
cody@cody-laptop:~$ quickly create ubuntu-application Test
Creating project directory test
Creating bzr repository and commiting
Traceback (most recent call last):
  File "/usr/share/quickly/templates/ubuntu-application/create.py", line 114, in <module>
    wt.commit("Initial project creation with Quickly!")
  File "<string>", line 4, in commit_write_locked
  File "/usr/lib/python2.6/dist-packages/bzrlib/workingtree_4.py", line 197, in commit
    result = WorkingTree3.commit(self, message, revprops, *args, **kwargs)
  File "<string>", line 4, in commit_write_locked
  File "/usr/lib/python2.6/dist-packages/bzrlib/mutabletree.py", line 200, in commit
    *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/bzrlib/commit.py", line 286, in commit
    possible_master_transports=possible_master_transports)
  File "/usr/lib/python2.6/dist-packages/bzrlib/cleanup.py", line 131, in run
    self.cleanups, self.func, self, *args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/bzrlib/cleanup.py", line 165, in _do_with_cleanups
    result = func(*args, **kwargs)
  File "/usr/lib/python2.6/dist-packages/bzrlib/commit.py", line 402, in _commit
    self.config, timestamp, timezone, committer, self.revprops, rev_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/branch.py", line 708, in get_commit_builder
    timestamp, timezone, committer, revprops, revision_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/repository.py", line 1765, in get_commit_builder
    timestamp, timezone, committer, revprops, revision_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/repofmt/pack_repo.py", line 117, in __init__
    revprops=revprops, revision_id=revision_id)
  File "/usr/lib/python2.6/dist-packages/bzrlib/repository.py", line 114, in __init__
    self._committer = self._config.username()
  File "/usr/lib/python2.6/dist-packages/bzrlib/config.py", line 280, in username
    raise errors.NoWhoami()
bzrlib.errors.NoWhoami: Unable to determine your name.
Please, set your name with the 'whoami' command.
E.g. bzr whoami "Your Name <name@example.com>"
ERROR: create command failed
Aborting
cody@cody-laptop:~$ 

```

After all that, it tells me "create.py" has crashed.

---

### Post by pivotraze on 2010-09-29
Solved. Running "bzr whoami "MyName <MyEmail@gmail.com>" makes it work. Wow, I'm stupid xD

---

### Post by mahrizal on 2011-11-24
[@pivotraze :]("http://ubuntuforums.org/member.php?u=879620") thanks 
it works for me too

---

