---
title: "web2py: Can't create applications, permission denied"
date: 2012-02-15
forum: Programming Talk
---

### Post by supercheetah on 2012-02-15
I'm a newbie to web2py, and to web frameworks like it in general really.

I just installed web2py (apt-get install web2py), and I'm just trying to get through the [tutorial]("http://web2py.com/books/default/chapter/29/2"), but I'm already running into problems.

I try to run *web2py -S welcome*, but I get the following error:

```

New installation: unable to create welcome.w2p fileweb2py Web Framework
Created by Massimo Di Pierro, Copyright 2007-2011
Version 1.97.1 (2011-06-26 19:25:44)
Database drivers available: pysqlite2, pymysql, CouchDB
Traceback (most recent call last):
  File "/usr/bin/web2py", line 120, in <module>
    gluon.widget.start(cron=True)
  File "/usr/lib/pymodules/python2.7/gluon/widget.py", line 1098, in start
    import_models=options.import_models, startfile=options.run)
  File "/usr/lib/pymodules/python2.7/gluon/shell.py", line 183, in run
    _env = env(a, c=c, import_models=import_models)
  File "/usr/lib/pymodules/python2.7/gluon/shell.py", line 122, in env
    environment = build_environment(request, response, session)
  File "/usr/lib/pymodules/python2.7/gluon/compileapp.py", line 233, in build_environment
    current.cache = environment['cache'] = Cache(request)
  File "/usr/lib/pymodules/python2.7/gluon/cache.py", line 376, in __init__
    self.disk = CacheOnDisk(request)
  File "/usr/lib/pymodules/python2.7/gluon/cache.py", line 229, in __init__
    os.mkdir(folder)
OSError: [Errno 13] Permission denied: 'applications/welcome/cache'

```

Can anyone tell me what's going on here?

---

### Post by conradin on 2012-02-15
Run web2py -S welcome
as sudo web2py -S welcome
so the program can create the files it needs. I think its just a config file, you probably wont need to run it as root again after that.

---

### Post by supercheetah on 2012-02-15
That's weird.  That seems like a bug to me.  There shouldn't be a reason that root is needed to create an application.

PS It did work.

---

