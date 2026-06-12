---
title: "[SOLVED] want to remotely connect to my server"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by UbuntuNerd on 2008-07-07
This may sound like a dumb question but I was wondering if some one can help me decide the best way to connect from within my network and remotely to my ubuntu server, I also have a vista and ubuntu desktop in my home network?

---

### Post by jamesrfla on 2008-07-07
Do you want to setup like a remote desktop connection or telnet? What version of Ubuntu are you using?

---

### Post by UbuntuNerd on 2008-07-07
yep i wan to be able to work on the server with out the screen and be able to remotely control it if i need to both the server and the desktop are ubuntu 8.4

---

### Post by jamesrfla on 2008-07-07
Okay first you need to enable remote desktop. I have done this before. Go to System>preferences>remote desktop. Then select share desktop and the other ones too for your preference.

---

### Post by UbuntuNerd on 2008-07-07
that would be the ubuntu desktop i figure since the server is already ubuntu it can make it easier

---

### Post by jamesrfla on 2008-07-07
I am getting kinda confused. Are both of the Ubuntu computers the Desktop edition 8.04?

---

### Post by UbuntuNerd on 2008-07-07
i have an ubuntu server 8.4,ubuntu desktop 8.4, vista desktop

---

### Post by hrod beraht on 2008-07-07
> **jperez78 said:**
> yep i wan to be able to work on the server with out the screen and be able to remotely control it if i need to both the server and the desktop are ubuntu 8.4

The standard way to administer headless servers is to use SSH (Secure Shell). So, assuming you checked the SSH box during install of the server, then all you have to do is *ssh username@servername* or *ssh username@ipaddress*.

Bob

P.S. Did you give the server a static ip address?

---

### Post by jamesrfla on 2008-07-07
Okay the Ubuntu server you can't do remote desktop but you can do telnet or in Linux it is called ssh telnet. The Ubuntu desktop you can share and you can access it from the Vista computer only unless you get a GUI for the server edition.

---

### Post by UbuntuNerd on 2008-07-07
how do i find out if i have ssh install on my desktop?
 ps: i know i have it on the server b/c i check the box when i first installed it

---

### Post by jamesrfla on 2008-07-07
Type ssh (your ip address of your desktop) into the terminal of your server edition. Example ssh 192.168.1.2

---

### Post by hrod beraht on 2008-07-07
> **jperez78 said:**
> how do i find out if i have ssh install on my desktop?
 ps: i know i have it on the server b/c i check the box when i first installed it

You don't need it on your desktop computer if the ssh daemon was installed on the server.
To access the server, just open a terminal window and type *ssh username@servername* or *ssh username@serveripaddress* using the username you created when you installed the operating system on the server.

Example: [COLOR="SeaGreen"]ssh joe@192.168.1.100[/COLOR]

Bob

---

### Post by jamesrfla on 2008-07-07
So your going to use ssh to access the server edition and your going to use Remote desktop to access the Desktop edition desktop.

---

### Post by bodhi.zazen on 2008-07-07
you can access both over ssh

use ssh -X to forward X apps

[uwiki]SSHHowto[/uwiki]

---

### Post by Atomic Dog on 2008-07-07
This howto:  [http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html](http://www.vanemery.com/Linux/XoverSSH/X-over-SSH2.html)
  might also be interesting to you.

---

### Post by UbuntuNerd on 2008-07-07
thank you guys for all your help it looks like i got some work to do thanks again for taking the time to answer!!!

---

