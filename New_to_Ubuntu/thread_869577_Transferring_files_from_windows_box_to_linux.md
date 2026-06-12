---
title: "Transferring files from windows box to linux?"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by AOZ on 2008-07-24
I need to get around 12GB of music from my windows box onto linux. Were on the same LAN is there an easy way to do this?  thanks in advance

-Omar

---

### Post by SNuxoll on 2008-07-24
Yup, hit alt+f2 is gnome to bring up the run command dialog, type in shares-admin and you can probably figure it out from there.

---

### Post by TBOL3 on 2008-07-25
Yep, I'm assuming that you already have a network setup.  If you don't just go to System > Administration > network, and choose how your are being connected (either Ethernet, modem, wireless, or something else.  Choose a static IP address for both computers (do not do this when trying to go outside of your LAN).  Also, I would choose two numbers that are almost identical (except for the last digit).

So, now that you have a network (if you didn't), what you need to do is create a shared folder.  So, press Alt+F2 and type:

gksudo nautilus (sorry I can't get code tags to work).

Navigate to /home/<your user name>

Create a simple folder, say MyShared.

Right click on the folder and choose sharing options.

Allow the folder to be shared, and allow access to the files in it.

When a message box comes up, saying that ubuntu will change the permissions, click on yes.

<Note:  You needed to be in root to allow the computer to share the folder, I cant find a way to use sudo on it.>

On your other mashine, do a search for the shared folders, you might have to type in your computer's IP address.  

<To find your IP address type in ifconfig in the terminal>

<I'm sorry, but I don't know much about finding shared folders in windows, but it's somewhere in windows explorer>

Go to the shared folder on your windows box.

Put the files in that folder.

When you are done, remove that folder from shared status.

Do whatever you want with the files.

I hope this helps.

EDIT:  Nevermind about opening a root window, and allowing shares, just type in shares-admin.  That is much better.  I'm sorry, I just found it.

---

### Post by AOZ on 2008-07-25
Thanks guys for the quick replies. Im just working through the program now hopefully it will work

---

### Post by hyper_ch on 2008-07-25
simplest way

(1) install openssh-server on linux
```

sudo apt-get install openssh-server

```

(2) get winscp from [http://www.winscp.com](http://www.winscp.com) on windows

(3) install winscp on windows

(4) run winscp on windows and use as address the linux box's IP, as username the username you use to login at the linux box and as password the password you use to login at the linux box.

(5) transfer the file into your home folder somewhere

---

