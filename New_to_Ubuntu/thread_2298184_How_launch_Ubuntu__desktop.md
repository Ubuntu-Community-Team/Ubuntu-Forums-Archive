---
title: "How launch Ubuntu  desktop ?"
date: 2015-10-09
forum: New to Ubuntu
---

### Post by Harry_Baya on 2015-10-09
I am new to this.  I can SSH into the Linux prompt.  Ti used the commands below to install the Ubuntu desktop..  They ran to completion.   [SIZE=4]**What do I do now to use the desktop?**[/SIZE]  Can I do this from the command prompt provided by SSH?

sudo apt_get update
sudo apt-get install ubuntu-desktop.

Will I be able to use a browser on the desktop to download the install files for PHP, Apache and MySql?

---

### Post by TheFu on 2015-10-09
Reread your question. I had assumed you were using ssh from 1 computer (unknown OS) to remote shell into some other computer either across the room, across the town or across the world. Continue reading if that is true.
OTOH, if you used ssh to connect to ssh on the same PC, it is only academically interesting, not really useful for day-to-day stuff.

ssh provides a text interface.  It is possible to have ssh setup a "tunnel" for a GUI to run, but that doesn't remove the need for the computer you sit behind to provide an appropriate "GUI Server".  Also - the default Ubuntu Desktop doesn't work over remote GUI sessions. You need to use something that doesn't need a 3d accelerated GPU.

[http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications](http://blog.jdpfu.com/2010/09/07/running-remote-desktops-and-remote-applications) tries to explain the different ways to accomplish what you are asking.  

The short answer is to use x2go with LXDE (not unity). Install it using the x2go PPA following those instructions.

---

### Post by Sweet_Baby_Jamie on 2015-10-09
Ordinarily to switch from one interface to another, you can log out and choose a session when you log in.

---

