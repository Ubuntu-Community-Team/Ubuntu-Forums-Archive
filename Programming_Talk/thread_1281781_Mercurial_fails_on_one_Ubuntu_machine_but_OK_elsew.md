---
title: "Mercurial fails on one Ubuntu machine but OK elsewhere"
date: 2009-10-03
forum: Programming Talk
---

### Post by AncientPC on 2009-10-03
The command: hg clone [https://cs371d-pj1.googlecode.com/hg/](https://cs371d-pj1.googlecode.com/hg/) cs371d-pj1

I've installed, re-installed, purged and installed but whenever I run the above command I get:
```
** unknown exception encountered, details follow
** report bug details to http://www.selenic.com/mercurial/bts
** or mercurial@selenic.com
** Mercurial Distributed SCM (version 1.1.2)
** Extensions loaded: 
Traceback (most recent call last):
  File "/usr/bin/hg", line 20, in <module>
    mercurial.dispatch.run()
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 20, in run
    sys.exit(dispatch(sys.argv[1:]))
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 29, in dispatch
    return _runcatch(u, args)
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 45, in _runcatch
    return _dispatch(ui, args)
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 367, in _dispatch
    ret = _runcommand(ui, options, cmd, d)
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 416, in _runcommand
    return checkargs()
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 376, in checkargs
    return cmdfunc()
  File "/var/lib/python-support/python2.6/mercurial/dispatch.py", line 361, in <lambda>
    d = lambda: util.checksignature(func)(ui, *args, **cmdoptions)
  File "/var/lib/python-support/python2.6/mercurial/util.py", line 715, in check
    return func(*args, **kwargs)
  File "/var/lib/python-support/python2.6/mercurial/commands.py", line 595, in clone
    update=not opts.get('noupdate'))
  File "/var/lib/python-support/python2.6/mercurial/hg.py", line 120, in clone
    src_repo = repository(ui, source)
  File "/var/lib/python-support/python2.6/mercurial/hg.py", line 61, in repository
    repo = _lookup(path).instance(ui, path, create)
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 234, in instance
    inst.between([(nullid, nullid)])
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 155, in between
    d = self.do_read("between", pairs=n)
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 119, in do_read
    fp = self.do_cmd(cmd, **args)
  File "/var/lib/python-support/python2.6/mercurial/httprepo.py", line 95, in do_cmd
    proto = resp.headers['content-type']
  File "/usr/lib/python2.6/rfc822.py", line 388, in __getitem__
    return self.dict[name.lower()]
KeyError: 'content-type'
```

When I run the same command on other Ubuntu boxes it works fine.

---

### Post by jpkotta on 2009-10-03
Are you sure the URL is correct?  AFAICT, there is no repo there, and no project with that name.

OTOH, Mercurial shouldn't crash and burn like that, even if there is no repo.  What version of Mercurial are you using?

---

### Post by AncientPC on 2009-10-03
It's working now.  It looks like after purging Mercurial, restarting the system and then reinstalling fixed it.

Should be unnecessary, but perhaps some files were in use preventing the reinstall to replace all files?

---

### Post by jpkotta on 2009-10-04
> **AncientPC said:**
> Should be unnecessary, but perhaps some files were in use preventing the reinstall to replace all files?

Maybe.  I saw that on my system the mercurial files listed in the stack trace were in /var/lib, and were all symlinks.  I don't know why that is or how they are handled on install/reconfigure/remove.  But I do know that for regular files on a Unix system, they can be replaced even if they're in use.  Any programs that have the files open will keep the old version, and any programs that open the file after the replacement will get the new version.

---

