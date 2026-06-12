---
title: "Trouble installing python-ldap from the repos"
date: 2008-02-07
forum: Programming Talk
---

### Post by aashay on 2008-02-07
This is what i am getting while installing python-ldap from the ubuntu repositories:
```
Setting up python-ldap (2.3-2ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-ldap (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-ldap
E: Sub-process /usr/bin/dpkg returned an error code (1)

```
Trying to remove it gives the following error: 
```
Removing python-ldap ...
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 953, in run
    runtimes = get_installed_runtimes(with_unsupported=True)
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error processing python-ldap (--remove):
 subprocess pre-removal script returned error exit status 1
Traceback (most recent call last):
  File "/usr/bin/pycentral", line 1394, in <module>
    main()
  File "/usr/bin/pycentral", line 1388, in main
    rv = action.run(global_options)
  File "/usr/bin/pycentral", line 875, in run
    runtimes = get_installed_runtimes()
  File "/usr/bin/pycentral", line 198, in get_installed_runtimes
    default_version = pyversions.default_version(version_only=True)
  File "/usr/share/pycentral-data/pyversions.py", line 126, in default_version
    _default_version = link = os.readlink('/usr/bin/python')
OSError: [Errno 22] Invalid argument: '/usr/bin/python'
dpkg: error while cleaning up:
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 python-ldap
E: Sub-process /usr/bin/dpkg returned an error code (1)
```
So I guess I'm stuck with a broken installation of python-ldap that can't be cured. Any idea how I could repair this??

---

### Post by dwblas on 2008-02-07
See if you have the /usr/bin/python link from the first error message.  If its not there, then link /usr/bin/pyton2.5, or whatever you have, to /usr/bin/python.

---

### Post by aashay on 2008-02-08
Already did it. Makes no difference. Made links, copies, renamed stuff... nothing works!!

---

### Post by aashay on 2008-02-08
It finally worked!! Took your advice and deleted the old files and make new links. For some reason, it decided to work!! Thanks

---

### Post by dwblas on 2008-02-08
It was probably a permission problem.  I should have said that earlier.  Anyway, glad it's working.

---

