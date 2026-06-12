---
title: "Problem when installing python-lldb-5.0"
date: 2018-02-09
forum: New to Ubuntu
---

### Post by jkt2 on 2018-02-09
Hello I seem to have broken apt on my computer, though I have had and used Linux for a time I am by no means an expert. 


```
sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following additional packages will be installed:
  python-lldb-5.0
The following NEW packages will be installed:
  python-lldb-5.0
0 upgraded, 1 newly installed, 0 to remove and 130 not upgraded.
2 not fully installed or removed.
Need to get 0 B/115 kB of archives.
After this operation, 788 kB of additional disk space will be used.
Do you want to continue? [Y/n] Y
(Reading database ... 447083 files and directories currently installed.)
Preparing to unpack .../python-lldb-5.0_1%3a5.0.1~svn324026-1~exp1_amd64.deb ...
Unpacking python-lldb-5.0 (1:5.0.1~svn324026-1~exp1) ...
dpkg: error processing archive /var/cache/apt/archives/python-lldb-5.0_1%3a5.0.1~svn324026-1~exp1_amd64.deb (--unpack):
 trying to overwrite '/usr/lib/python2.7/dist-packages/lldb', which is also in package python-lldb-4.0 1:4.0-1ubuntu1~16.04.2
Errors were encountered while processing:
 /var/cache/apt/archives/python-lldb-5.0_1%3a5.0.1~svn324026-1~exp1_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

There seem to be an issue with conflicting packages here, I have tried to unistall lldb-4.0 but to no effect it sill prompts me with the same message

```
sudo apt-get purge lldb-4.0
Reading package lists... Done
Building dependency tree       
Reading state information... Done
You might want to run 'apt-get -f install' to correct these:
The following packages have unmet dependencies:
 liblldb-4.0-dev : Depends: lldb-4.0 (= 1:4.0-1ubuntu1~16.04.2) but it is not going to be installed
 lldb-5.0 : Depends: python-lldb-5.0 but it is not going to be installed
E: Unmet dependencies. Try 'apt-get -f install' with no packages (or specify a solution).

```

Attempting to resolve it with autoclean also fails

```
sudo apt-get autoclean
Reading package lists... Done
Building dependency tree       
Reading state information... Done
```

What to do here?

---

### Post by &amp;KyT$0P# on 2018-02-09
What happens if you try -
```
sudo apt-get purge python-lldb-4.0
```

---

