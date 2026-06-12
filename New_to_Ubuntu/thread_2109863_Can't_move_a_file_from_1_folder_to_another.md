---
title: "Can't move a file from 1 folder to another"
date: 2013-01-28
forum: New to Ubuntu
---

### Post by checkmate110 on 2013-01-28
Hi all,  I am playing around in ubuntu trying to learn linux. I was following a tutorial.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

  It was going fine until I got to this part, "you should move it into the /usr/local/src directory we made in Step 1 ". Well that's the easiest part yet, I thought... After an hour I gave up! 

I tried copying and pasting about 30 times but the paste button was always greyed out.  I opened another instance of the file browser and tried to drag and drop and I got a message that I lacked sufficent permissions. I even tried to redownload it to the right folder and that didn't work. 

Very frustrating that I am unable to do something so simple. 

I'm using Ubuntu 12.10.

---

### Post by Nr90 on 2013-01-28
/usr/local/src is owned by root. This makes it impossible for your regular user to write to that folder.
sudo chown $USER /usr/local/src
Should do the trick.

That said, you could just compile in a directory in your home folder.

---

### Post by nns2006 on 2013-01-28
> **checkmate110 said:**
> Hi all,  I am playing around in ubuntu trying to learn linux. I was following a tutorial.

[https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo)

  It was going fine until I got to this part, "you should move it into the /usr/local/src directory we made in Step 1 ". Well that's the easiest part yet, I thought... After an hour I gave up! 

I tried copying and pasting about 30 times but the paste button was always greyed out.  I opened another instance of the file browser and tried to drag and drop and I got a message that I lacked sufficent permissions. I even tried to redownload it to the right folder and that didn't work. 

Very frustrating that I am unable to do something so simple. 

I'm using Ubuntu 12.10.

Learning is OK unless it mess with your system files. And the very reason why you are not able to move files because these are system files which can be moved only through "root" account. though you may copy it by using 'sudo' command. But be careful.

---

### Post by checkmate110 on 2013-01-28
> **Nr90 said:**
> /usr/local/src is owned by root. This makes it impossible for your regular user to write to that folder.
sudo chown $USER /usr/local/src
Should do the trick.

That said, you could just compile in a directory in your home folder.

Nr90,thanks for the quick response. 

I tried what you said but it's the same situation. Do I have to use the command line to move files around?

Like I said the intent here is just to learn linux (for now).

Is this kind of permission lockdown unuque to ubuntu?

---

### Post by frank604 on 2013-01-28
use nautilus as root.  to do so you can do it in a few ways.

1) press alt+f2 then enter "sudo nautilus"

or

2) open terminal, ctrl+alt+t, type in "sudo nautilus"

Now you should be able to copy into directories that are owned by root.

I prefer the terminal way as any debug/error output will be shown in terminal as you use nautilus.

---

### Post by elgordodude on 2013-01-28
> Is this kind of permission lockdown unuque to ubuntu?

No, this is common throughout the *nix universe including all versions of linux.

Some other ways are to use sudo nautilus /usr/local/src to enable write permissions in a gui, or sudo mv /folder/file /usr/local/src

But be careful with your system files, it's best to learn where you can be confident you won't break anything.

---

### Post by Nr90 on 2013-01-28
I would just compile in a different directory. Any folder in your home directory will have the right permissions and you won't have to screw around with ownership.

This owner ship is not specific to Ubuntu. In linux/unix all files have associated permissions.
Windows has this as well, but the distinction between administrator and regular user is not as clear as in linux/unix.

---

### Post by checkmate110 on 2013-01-28
> **frank604 said:**
> use nautilus as root.  to do so you can do it in a few ways.

1) press alt+f2 then enter "sudo nautilus"

or

2) open terminal, ctrl+alt+t, type in "sudo nautilus"

Now you should be able to copy into directories that are owned by root.

I prefer the terminal way as any debug/error output will be shown in terminal as you use nautilus.

frank604, this what I got.


jeff@VMmain:~$ sudo nautilus
[sudo] password for jeff: 
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

jeff@VMmain:~$

---

### Post by Nr90 on 2013-01-28
The proper way to call graphical programs as root from the terminal is gksu nautilus.
Have a look here: [https://help.ubuntu.com/community/RootSudo#Graphical_sudo](https://help.ubuntu.com/community/RootSudo#Graphical_sudo)

That said moving the files as root will only help you here, but you won't be able to compile later unless you compile as root.

---

### Post by Impavidus on 2013-01-29
> **Nr90 said:**
> /usr/local/src is owned by root. This makes it impossible for your regular user to write to that folder.
sudo chown $USER /usr/local/src
Should do the trick.

That said, you could just compile in a directory in your home folder.
/usr/local is meant for non-standard stuff, so you won't break your system by changing things there. By default it just contains a few almost empty directories. In general however it is recommendable not to change ownership of anything in the sytem directories.

/usr/local/src is typically used as archive for source code of programs manually installed in /usr/local/bin. For most people (especially beginners) /usr/local/src will be empty.

---

### Post by checkmate110 on 2013-01-29
Thanks for all the tips.

 Like I said, this is just a learning experience for me and something to do with the extra time I have since I retired. I'm doing this on an old computer that I am trying different flavors of linux on and hope to learn enough to one day set up a lunux server for my lan.

Can anybody recommend a good book or online tutorial to get me going?

Thanks again.

---

### Post by Bashing-om on 2013-01-29
checkmate110; Hi !

These links will prove of interest, good starting points.
[https://help.ubuntu.com/community/FilePermissions](https://help.ubuntu.com/community/FilePermissions)
[http://rute.2038bug.com/index.html.gz](http://rute.2038bug.com/index.html.gz)
[http://ubuntu-manual.org/](http://ubuntu-manual.org/)
[http://ubuntuguide.org/wiki/Ubuntu_Precise](http://ubuntuguide.org/wiki/Ubuntu_Precise)
[http://www.linux-tutorial.info/](http://www.linux-tutorial.info/)
[http://mywiki.wooledge.org/FullBashGuide](http://mywiki.wooledge.org/FullBashGuide)

In no particular order, the pursuit will keep you occupied for the duration !

---

