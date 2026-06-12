---
title: "ssh"
date: 2012-02-18
forum: New to Ubuntu
---

### Post by musicman123 on 2012-02-18
Hello
 
[FONT=Times New Roman][SIZE=3]I am trying to install ssh server to Ubuntu 8.x as I am getting connection refused message when I try to login from a windows machine using Putty or from another Linux machine.[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Details are[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]I am running Ubuntu 8.x after installing it into windows ( XP )[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I can only find openssh client in the Synaptic Package manager[/SIZE][/FONT]
[FONT=Times New Roman][SIZE=3]I have run what I think is an update from the front end Applications Add/Remove and still no openssh[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Any help would be very much appreciated[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Regards[/SIZE][/FONT]
 
[FONT=Times New Roman][SIZE=3]Musicman123 [/SIZE][/FONT]

---

### Post by kevdog on 2012-02-18
What happens from command line when you type:
sudo apt-get install openssh-server

---

### Post by Paqman on 2012-02-18
First if all, the only 8.X version of Ubuntu that is still supported is 8.04 Server. If you're running anything else, you'll need to install a newer version instead.

Assuming you are running 8.04 server, the package you need is [openssh-server]("apt:openssh-server").

---

