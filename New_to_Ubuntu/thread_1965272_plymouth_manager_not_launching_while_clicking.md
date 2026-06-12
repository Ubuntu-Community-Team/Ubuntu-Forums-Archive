---
title: "plymouth manager not launching while clicking?"
date: 2012-04-25
forum: New to Ubuntu
---

### Post by shri_ved on 2012-04-25
My plymouth manager is not launching when i click at system tools > plymouth manager. When I try to do it by typing plymouth-manager in terminal then it return with following details

[B]shreyas@ARGUS:~$ plymouth-manager
Traceback (most recent call last):
  File "plymouth-manager.py", line 23, in <module>
    main.PlymouthManager()
  File "/usr/share/plymouth-manager/src/main.py", line 148, in __init__
    if value == funcmain.getCurrentRes():
  File "/usr/share/plymouth-manager/src/funcmain.py", line 34, in getCurrentRes
    tmpBuf = open("/etc/default/" + hwinfo.getBoot(), "r")
IOError: [Errno 2] No such file or directory: '/etc/default/burg'
[/B]
I want to change my splash login screen. I could launch this manager once but that time also there was a problem in this utility because it did not change my splash screen & now it is not even launching at all. please help.

Note: I have reinstall this application several time by

sudo apt-add-repository ppa:mefrio-g/plymouthmanager
sudo apt-get update
sudo apt-get install plymouth-manager

but still it is not activating. Whats the problem??

---

