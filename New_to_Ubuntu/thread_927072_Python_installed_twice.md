---
title: "Python installed twice?"
date: 2008-09-22
forum: New to Ubuntu
---

### Post by densha on 2008-09-22
Hi. Brand new to Ubuntu. Decided to install the server package to handle some web dev work where I needed to install some custom python modules that my shared host wouldn't install for me. Everything went well, but im curious if I pulled a beginner move.

Does this mean that I have 2 seperate installs of python on my system? When I attempt to do a 'apt-get remove python', it doesn't want to remove the python2.5 stuff, however if I do 'apt-get remove python2.5' it wants to unstall python and python2.5 .

xorsyst@ubuntu:/usr/bin$ dpkg -l *python*
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Installed/Config-f/Unpacked/Failed-cfg/Half-inst/t-aWait/T-pend
|/ Err?=(none)/Hold/Reinst-required/X=both-problems (Status,Err: uppercase=bad)
||/ Name           Version        Description
+++-==============-==============-============================================
ii  python         2.5.2-0ubuntu1 An interactive high-level object-oriented la
ii  python2.5      2.5.2-2ubuntu4 An interactive high-level object-oriented la
No packages found matching python2.5-config.
No packages found matching python-config.
xorsyst@ubuntu:/usr/bin$

If it is indeed installed twice, should I just remove both and reinstall python? Thanks.

---

### Post by zephyrcat on 2008-09-22
Short Answer: Don't worry about it. That is how it should be, I believe. 

Long Answer: The Ubuntu repositories provide multiple versions of python (python2.5, python2.4, etc.). If you need a specific version, you can install just that version (assuming they have it). To make things easier, though, there is also a package called just "python." This package simply depends on whatever the current default package. In this case, when you installed "python", all that it did was install the python2.5 package, because "python" depends on "python2.5".

Hope that helps!

---

### Post by densha on 2008-09-22
Thanks, that was exactly what I needed and wanted to hear. Appreciate it!

---

### Post by zephyrcat on 2008-09-22
Your welcome. Glad I could help!

---

