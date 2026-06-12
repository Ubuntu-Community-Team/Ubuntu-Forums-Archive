---
title: "Bzr (Bazzar) with Trac"
date: 2007-11-22
forum: Programming Talk
---

### Post by timmie on 2007-11-22
Hello,
did anyone succeed in runing bzr together with trac on gutsy?

There's a bzr-trac plugin in the repos but it doesn't really work.

```

Traceback (most recent call last):
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 406, in dispatch_request
    dispatcher.dispatch(req)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 191, in dispatch
    chosen_handler = self._pre_process_request(req, chosen_handler)
  File "/var/lib/python-support/python2.5/trac/web/main.py", line 263, in _pre_process_request
    chosen_handler = f.pre_process_request(req, chosen_handler)
  File "/var/lib/python-support/python2.5/trac/versioncontrol/api.py", line 73, in pre_process_request
    self.get_repository(req.authname).sync()
  File "/var/lib/python-support/python2.5/trac/versioncontrol/api.py", line 94, in get_repository
    ((self.repository_type,)*2))
TracError: Unsupported version control system "bzr". Check that the Python bindings for "bzr" are correctly installed.


```

A help on how to set it up would be very nice.

Thank you.

Timmie

---

### Post by Jc2k on 2008-01-08
Are you the Tim that posted here?

[https://bugs.edge.launchpad.net/trac-bzr/+bug/162970](https://bugs.edge.launchpad.net/trac-bzr/+bug/162970)

```
sudo apt-get install python-setuptools
```

Helped me get a bit further - still not working though

---

