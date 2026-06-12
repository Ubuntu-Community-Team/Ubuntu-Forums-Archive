---
title: "Git pull From bundles of Repositories"
date: 2009-11-22
forum: Programming Talk
---

### Post by huangyingw on 2009-11-22
Hello,
    Currently, I have a repository under GIT control, and clone it to several machines.
    And I want to pull together the revisions from all other machines. While, to access a share repository for pulling, I have to ```
smbmount the \\remoteIP\path to /media/smb 
```first, and then ```
git pull /media/smb 
```
    For only one remote repository, this method is accessible. But, if I have more than 10 cloned repositories, or if I have to co-work with more than 10 partner, how could I pull the revisions from repositories quickly and conviniently?
    I have to write a script to smbmount->git pull->umount->...?

---

### Post by wmcbrine on 2009-11-22
Git is very flexible in how it accesses remote repositories. You don't say what kind of systems these are. But, in my case, I used ssh, which I already had running -- no need to mount anything.

In your case, perhaps it would make more sense to have a central repository, have each person push their changes to it, and you pull from there?

---

### Post by huangyingw on 2009-11-23
> **wmcbrine said:**
> Git is very flexible in how it accesses remote repositories. You don't say what kind of systems these are. But, in my case, I used ssh, which I already had running -- no need to mount anything.

In your case, perhaps it would make more sense to have a central repository, have each person push their changes to it, and you pull from there?
yes, thanks. Your ideas of central repository is really a good idea. For most of my teamates, setting up ssh is too difficult for them to learn.
I have just done an experiment, with everyones push to the central repository, there might be confilct that need to be merged. While, this seems to be quite easy, I just pull to local again, and merge, and then push back to the central, thus, the remote conflict is resolved locally.
I write this out, might be helpful to others.

---

### Post by huangyingw on 2009-11-23
> **huangyingw said:**
> yes, thanks. Your ideas of central repository is really a good idea. ....
I just found a little problem, in GIT, push back to central is OK, while, in HG, one push back, and another continued to push back, would result in a lots of errors
```

pushing to /media/smb/myproject/git/demo
searching for changes
** unknown exception encountered, details follow
** report bug details to http://mercurial.selenic.com/bts/
** or mercurial@selenic.com
** Mercurial Distributed SCM (version 1.3.1)
** Extensions loaded: 
Traceback (most recent call last):
  File "/usr/bin/hg", line 27, in <module>
    mercurial.dispatch.run()
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 16, in run
    sys.exit(dispatch(sys.argv[1:]))
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 27, in dispatch
    return _runcatch(u, args)
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 43, in _runcatch
    return _dispatch(ui, args)
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 449, in _dispatch
    return runcommand(lui, repo, cmd, fullargs, ui, options, d)
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 317, in runcommand
    ret = _runcommand(ui, options, cmd, d)
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 501, in _runcommand
    return checkargs()
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 454, in checkargs
    return cmdfunc()
  File "/usr/lib/pymodules/python2.6/mercurial/dispatch.py", line 448, in <lambda>
    d = lambda: util.checksignature(func)(ui, *args, **cmdoptions)
  File "/usr/lib/pymodules/python2.6/mercurial/util.py", line 402, in check
    return func(*args, **kwargs)
  File "/usr/lib/pymodules/python2.6/mercurial/commands.py", line 2333, in push
    r = repo.push(other, opts.get('force'), revs=revs)
  File "/usr/lib/pymodules/python2.6/mercurial/localrepo.py", line 1481, in push
    return self.push_addchangegroup(remote, force, revs)
  File "/usr/lib/pymodules/python2.6/mercurial/localrepo.py", line 1598, in push_addchangegroup
    ret = self.prepush(remote, force, revs)
  File "/usr/lib/pymodules/python2.6/mercurial/localrepo.py", line 1566, in prepush
    remotehds = remote.branchmap()
  File "/usr/lib/pymodules/python2.6/mercurial/localrepo.py", line 389, in branchmap
    self._branchtags(partial, lrev)
  File "/usr/lib/pymodules/python2.6/mercurial/localrepo.py", line 367, in _branchtags
    self._updatebranchcache(partial, lrev+1, tiprev+1)
  File "/usr/lib/pymodules/python2.6/mercurial/localrepo.py", line 461, in _updatebranchcache
    newbranches.setdefault(c.branch(), []).append(c.node())
  File "/usr/lib/pymodules/python2.6/mercurial/context.py", line 101, in branch
    def branch(self): return self._changeset[5].get("branch")
  File "/usr/lib/pymodules/python2.6/mercurial/util.py", line 150, in __get__
    result = self.func(obj)
  File "/usr/lib/pymodules/python2.6/mercurial/context.py", line 59, in _changeset
    return self._repo.changelog.read(self.node())
  File "/usr/lib/pymodules/python2.6/mercurial/changelog.py", line 175, in read
    text = self.revision(node)
  File "/usr/lib/pymodules/python2.6/mercurial/revlog.py", line 994, in revision
    self._chunkraw(base, rev)
  File "/usr/lib/pymodules/python2.6/mercurial/revlog.py", line 955, in _chunkraw
    return self._getchunk(start, length)
  File "/usr/lib/pymodules/python2.6/mercurial/revlog.py", line 948, in _getchunk
    return self._loadchunk(offset, length)
  File "/usr/lib/pymodules/python2.6/mercurial/revlog.py", line 930, in _loadchunk
    d = df.read(readahead)
OverflowError: long int too large to convert to int
root@TryUbuntu:~/myproject/git/demo# hg pull
pulling from /media/smb/myproject/git/demo
searching for changes
adding changesets
transaction abort!
rollback completed
abort: unknown compression type '\x96'!

```
Bug of HG?

---

