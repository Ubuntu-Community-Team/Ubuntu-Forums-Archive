---
title: "How to solve this python installation problem ?"
date: 2012-05-02
forum: Programming Talk
---

### Post by prismctg on 2012-05-02
i got this error when i m installing python 3.2 idle in 12.04```
installArchives() failed: Selecting previously unselected package idle-python3.2.
(Reading database ... 
(Reading database ... 5%
(Reading database ... 10%
(Reading database ... 15%
(Reading database ... 20%
(Reading database ... 25%
(Reading database ... 30%
(Reading database ... 35%
(Reading database ... 40%
(Reading database ... 45%
(Reading database ... 50%
(Reading database ... 55%
(Reading database ... 60%
(Reading database ... 65%
(Reading database ... 70%
(Reading database ... 75%
(Reading database ... 80%
(Reading database ... 85%
(Reading database ... 90%
(Reading database ... 95%
(Reading database ... 100%
(Reading database ... 323602 files and directories currently installed.)
Unpacking idle-python3.2 (from .../idle-python3.2_3.2.3-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Processing triggers for gnome-menus ...
Processing triggers for menu ...
Setting up idle-python3.2 (3.2.3-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/lib/python3.2/sysconfig.py", line 334, in _init_posix
    _parse_makefile(makefile, vars)
  File "/usr/bin/lib/python3.2/sysconfig.py", line 220, in _parse_makefile
    with open(filename, errors="surrogateescape") as f:
IOError: [Errno 2] No such file or directory: '/usr/bin/lib/python3.2/config-3.2mu/Makefile'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/lib/python3.2/site.py", line 537, in <module>
    main()
  File "/usr/bin/lib/python3.2/site.py", line 525, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/bin/lib/python3.2/site.py", line 263, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/bin/lib/python3.2/site.py", line 238, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/bin/lib/python3.2/site.py", line 228, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/bin/lib/python3.2/sysconfig.py", line 577, in get_config_var
    return get_config_vars().get(name)
  File "/usr/bin/lib/python3.2/sysconfig.py", line 474, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/bin/lib/python3.2/sysconfig.py", line 339, in _init_posix
    raise IOError(msg)
IOError: invalid Python installation: unable to open /usr/bin/lib/python3.2/config-3.2mu/Makefile (No such file or directory)
dpkg: error processing idle-python3.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 idle-python3.2
Error in function: 
Setting up idle-python3.2 (3.2.3-0ubuntu1) ...
Traceback (most recent call last):
  File "/usr/bin/lib/python3.2/sysconfig.py", line 334, in _init_posix
    _parse_makefile(makefile, vars)
  File "/usr/bin/lib/python3.2/sysconfig.py", line 220, in _parse_makefile
    with open(filename, errors="surrogateescape") as f:
IOError: [Errno 2] No such file or directory: '/usr/bin/lib/python3.2/config-3.2mu/Makefile'

During handling of the above exception, another exception occurred:

Traceback (most recent call last):
  File "/usr/bin/lib/python3.2/site.py", line 537, in <module>
    main()
  File "/usr/bin/lib/python3.2/site.py", line 525, in main
    known_paths = addusersitepackages(known_paths)
  File "/usr/bin/lib/python3.2/site.py", line 263, in addusersitepackages
    user_site = getusersitepackages()
  File "/usr/bin/lib/python3.2/site.py", line 238, in getusersitepackages
    user_base = getuserbase() # this will also set USER_BASE
  File "/usr/bin/lib/python3.2/site.py", line 228, in getuserbase
    USER_BASE = get_config_var('userbase')
  File "/usr/bin/lib/python3.2/sysconfig.py", line 577, in get_config_var
    return get_config_vars().get(name)
  File "/usr/bin/lib/python3.2/sysconfig.py", line 474, in get_config_vars
    _init_posix(_CONFIG_VARS)
  File "/usr/bin/lib/python3.2/sysconfig.py", line 339, in _init_posix
    raise IOError(msg)
IOError: invalid Python installation: unable to open /usr/bin/lib/python3.2/config-3.2mu/Makefile (No such file or directory)
dpkg: error processing idle-python3.2 (--configure):
 subprocess installed post-installation script returned error exit status 1
```

---

### Post by r-senior on 2012-05-02
Bizarre - it's looking for files in /usr/bin/lib !!!

It should be looking in /usr/lib.

Just tried it here and all is well:

```
$ sudo apt-get install idle-python3.2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  python3-tk
Suggested packages:
  tix python3-tk-dbg
The following NEW packages will be installed
  idle-python3.2 python3-tk
0 upgraded, 2 newly installed, 0 to remove and 3 not upgraded.
Need to get 61.2 kB of archives.
After this operation, 294 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 http://gb.archive.ubuntu.com/ubuntu/ precise/main python3-tk amd64 3.2.3-1 [27.8 kB]
Get:2 http://gb.archive.ubuntu.com/ubuntu/ precise/main idle-python3.2 all 3.2.3-0ubuntu1 [33.4 kB]
Fetched 61.2 kB in 0s (66.1 kB/s)      
Selecting previously unselected package python3-tk.
(Reading database ... 211892 files and directories currently installed.)
Unpacking python3-tk (from .../python3-tk_3.2.3-1_amd64.deb) ...
Selecting previously unselected package idle-python3.2.
Unpacking idle-python3.2 (from .../idle-python3.2_3.2.3-0ubuntu1_all.deb) ...
Processing triggers for man-db ...
Processing triggers for desktop-file-utils ...
Processing triggers for gnome-menus ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf.index...
Setting up python3-tk (3.2.3-1) ...
Setting up idle-python3.2 (3.2.3-0ubuntu1) ...

```

What version of Ubuntu are you running and have you done any configuration that's out of the ordinary? 

Do you already have python3 installed from the repositories?

How did you do the install? What command did you use?

---

### Post by prismctg on 2012-05-02
I m using ubuntu 12.04 , usually  i install software from software center and yes python3 is installed in my pc . Recently i installed activepython 3.2.May be  that is creating problem

---

### Post by r-senior on 2012-05-03
Could you try installing with the same command I used so that we can compare the output:

```
sudo apt-get install idle-python3.2
```

---

### Post by prismctg on 2012-05-03
> **r-senior said:**
> Could you try installing with the same command I used so that we can compare the output:

```
sudo apt-get install idle-python3.2
```

hm.. i also try this .. but same output as i mention before

---

### Post by MadCow108 on 2012-05-03
usr/bin/lib is really weird.
probably your activepython installation is screwing things up, try to remove it.
usr/bin/lib should be the first thing you (re)move.

---

