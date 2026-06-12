---
title: "need a terminal window for ubuntu8.04server"
date: 2012-04-08
forum: New to Ubuntu
---

### Post by dgloe on 2012-04-08
I just installed harty heron 8.04 server on one i386 computer and I installed desktop harty hedghog 5.04on another i386 computer. Two separate machines. Could someone please recommend a low overhead terminal window I can install on the server. I don't need all the overhead gnome desktop has. An xTerm type window is all I need,so I can run gui administrative tools like network-admin, services-admin, system-config-printer, system-config-samba and Synaptic Package Manager. Any help will be much appreciated.

---

### Post by lmarmisa on 2012-04-09
> **dgloe said:**
> I just installed harty heron 8.04 server on one i386 computer and I installed desktop harty hedghog 5.04on another i386 computer. Two separate machines. Could someone please recommend a low overhead terminal window I can install on the server. I don't need all the overhead gnome desktop has. An xTerm type window is all I need,so I can run gui administrative tools like network-admin, services-admin, system-config-printer, system-config-samba and Synaptic Package Manager. Any help will be much appreciated.

You have installed versions of Ubuntu that have no support:

[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases)

Consider to use more modern versions.

In relation with your question, I recommend Webmin:

[http://www.webmin.com/](http://www.webmin.com/)

---

### Post by dgloe on 2012-04-09
Thank you Imarmisa. Webmin it is!!!! The compute the 8.04 is installed on is quite old. Thought I would over come the Ubuntu learning curve before I spent $ to build a new one.

---

### Post by lmarmisa on 2012-04-09
I recommend two essential tools too: [ssh]("http://en.wikipedia.org/wiki/Secure_Shell") and [scp]("http://es.wikipedia.org/wiki/Secure_Copy") (sshfs).

[https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo](https://help.ubuntu.com/community/SSH/OpenSSH/ConnectingTo)

[https://help.ubuntu.com/community/SSH/TransferFiles#SSHFS](https://help.ubuntu.com/community/SSH/TransferFiles#SSHFS)

[http://blog.damontimm.com/how-to-mount-a-sftp-folder-ssh-ftp-on-ubuntu-linux-using-sshfs-fuse/](http://blog.damontimm.com/how-to-mount-a-sftp-folder-ssh-ftp-on-ubuntu-linux-using-sshfs-fuse/)

---

### Post by dgloe on 2012-04-10
Imarmisa, I really appreciate your willingness to help me. It's people like you that make us newbies want to dump MS completely for Linux/Unix/Ubuntu. I looked into Webmin and decided to take your original advice and learn the Harty 8.04 server edition command line. Learning it will be better in the long run. I have edited the Smb.conf to set shares works good. Thank You, **** Loeffler

---

### Post by oldos2er on 2012-04-11
8.04 server is supported until April 2013.

---

