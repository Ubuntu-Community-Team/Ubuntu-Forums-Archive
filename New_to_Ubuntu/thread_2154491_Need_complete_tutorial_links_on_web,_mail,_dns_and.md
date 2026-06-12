---
title: "Need complete tutorial links on web, mail, dns and ftp server"
date: 2013-06-14
forum: New to Ubuntu
---

### Post by saer7429 on 2013-06-14
Hi everyone! i'm new to ubuntu but before this i have used fedora for a while. i need help on getting some links on tutorials regarding the topic. can't find the right one. I have to setup 4 servers as my assignments and make it connect to each other. each server is on different machine. really blur about the configurations. also, are there any method to connect the servers to a laptop that act as a router or anything like that? alternatively, if there are tutorials on how to set it up on vmware or virtualbox would be helpful. thanks in advance. :)

---

### Post by oldfred on 2013-06-15
A master thread on learning/books/terminal/bash/Linux etc
Linux Command Line Learning Resources - cortman
[https://help.ubuntu.com/community/CommandLineResources](https://help.ubuntu.com/community/CommandLineResources)
[http://ubuntuforums.org/showthread.php?t=1909108](http://ubuntuforums.org/showthread.php?t=1909108)

[http://www.ubuntu.com/download/server/install-ubuntu-server](http://www.ubuntu.com/download/server/install-ubuntu-server)
[URL="https://www.virtualbox.org/manual/ch01.html#intro-installing"]
https://www.virtualbox.org/manual/ch01.html#intro-installing[/URL]
[http://www.psychocats.net/ubuntu/virtualbox](http://www.psychocats.net/ubuntu/virtualbox)
[https://help.ubuntu.com/community/VirtualBox/Installation](https://help.ubuntu.com/community/VirtualBox/Installation)

---

### Post by Cheesemill on 2013-06-15
The [Linode library]("https://library.linode.com/") is a good resource.

---

### Post by saer7429 on 2013-06-15
Thanks. Great resources. :D
By the way, regarding on the ftp server. 
Should I use samba or vsftpd?

---

### Post by Cheesemill on 2013-06-15
What are you trying to achieve?

Samba and ftp are completely different things. If this is going to be an internet facing server then don't use Samba otherwise your asking to be hacked.

---

### Post by saer7429 on 2013-06-15
oh,ok.
my purpose is to create a server that can share file.
it's not going to the internet. just in the local environment.

---

