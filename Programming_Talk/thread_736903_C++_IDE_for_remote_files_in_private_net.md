---
title: "C++ IDE for remote files in private net"
date: 2008-03-27
forum: Programming Talk
---

### Post by alan888 on 2008-03-27
Hi:

I'm very new in the programming world. I don't know if this exist or not but my problem is that I have a program that work with some equipment (oscilloscope and generator). This programm must run in a  linux PC in a private net. I'm in a other private net working in this program, 

I can make "ssh -X" to the router and later to the linux PC, but this PC only have very simple tool for edit text (gedit 2.2.2) without highlight C++ special words. I can't install any additional software to the remote linux PC.

I just looking a method or tool for work over the remote file with a IDE, like Anjuta or something like that. without having to copy files to the router and then to the remote linux PC.

Thanks.-

---

### Post by supirman on 2008-03-27
You can use sshfs.  It will essentially allow you to have a directory on your local machine which is populated with files from another machine via ssh.


This way, you can use anjuta or any editor locally to edit the code.

See:
[https://help.ubuntu.com/community/SSHFS](https://help.ubuntu.com/community/SSHFS)

---

