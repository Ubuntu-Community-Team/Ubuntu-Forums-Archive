---
title: "[SOLVED] Moving files in the terminal"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by Nazty_Nayt on 2008-06-22
Ok, so I'm studying this video on youtube, basically about understanding the terminal.  Right now it's about moving files.  The file I decided to move is called initrd.img which was at the root of my file system.  I moved it to my usr folder.  Now I can't get it to go back, according to the video the line I'm supposed to run is this...

```
desktop:/usr$ cp initrd.img ../.
```  

How ever when I do that I get this 
cp: cannot stat `initrd.img': No such file or directory

I tried moving it back to the root manually, but it said I don't have permissions for that even though I'm the sudo user.

Can anyone help me out here?

---

### Post by fahadsadah on 2008-06-22
Ouch...
Why did you choose to move initrd?

Anyway, please post the output of an
```
ls /usr
```

---

### Post by Nazty_Nayt on 2008-06-22
Just installed a few days ago.  And just trying to learn, I didn't have any files really so I just went with that.  :(

Here's the log.

desktop:~$ ls /usr
bin    include     lib    lib64  naytsfolder  share  X11R6
games  initrd.img  lib32  local  sbin         src

---

### Post by fahadsadah on 2008-06-22
/initrd.img is an important boot file.
You wouldn't move a file like NTLDR on Windows would you?

The solution is ```
sudo mv /usr/initrd.img /
```

Next time, I would move a file within my home directory.

---

### Post by Nazty_Nayt on 2008-06-22
Thanks alot, and honestly I didn't know, that's why I'm trying to learn, I appreciate the help.  So I'm guessing "/" is my root directory then?

Thanks again.

:guitar:

---

### Post by Oldsoldier2003 on 2008-06-22
> **Nazty_Nayt said:**
> Thanks alot, and honestly I didn't know, that's why I'm trying to learn, I appreciate the help.  So I'm guessing "/" is my root directory then?

Thanks again.

:guitar:

yes / is the root of the file system

---

### Post by fahadsadah on 2008-06-22
> **Nazty_Nayt said:**
> Thanks alot, and honestly I didn't know, that's why I'm trying to learn, I appreciate the help.  So I'm guessing "/" is my root directory then?

Thanks again.

:guitar:

You're welcome!
You don't learn by doing stuff correctly, you learn by making mistakes!

---

### Post by forestpixie on 2008-06-22
I've just got RTFM'd in an openoffice forum - so thanks for cheering me up :D

All of your files/directories are located in / - that includes your /home drive - but that is owned by you.

If you are going to play like that make sure you have back ups so you can reinstall easily.

The other otion would be to install buntu in a virtual machine and you can do whatever you like and it won't cause any damage to your 'real' installation.

I'm doing exactly that with the next version and have reinstalled it 3 or 4 times already :D

Good luck with it all

---

### Post by Nazty_Nayt on 2008-06-22
> **forestpixie said:**
> I've just got RTFM'd in an openoffice forum - so thanks for cheering me up :D

All of your files/directories are located in / - that includes your /home drive - but that is owned by you.

If you are going to play like that make sure you have back ups so you can reinstall easily.

The other otion would be to install buntu in a virtual machine and you can do whatever you like and it won't cause any damage to your 'real' installation.

I'm doing exactly that with the next version and have reinstalled it 3 or 4 times already :D

Good luck with it all


Well, as you can probably see from my log, I don't have alot on here right now anyways, and I got the install cd still, right now I'm just getting a feel for everything, and I'm really loving the customization options with the desktop, and all that.  I do know I'm never going back to vista though!  :)

---

### Post by forestpixie on 2008-06-22
Never get rid of the install cd - you can use it to repair your system in some instances, which I guess will likely be useful :D

Wouldn't know about vista only seen it a couple of times, last win I had was win2k.

Might be worth looking at the vm thing in the future - I find it very useful if I want to have a quick look at a new distro without installing it to a harddrive.

---

### Post by Nazty_Nayt on 2008-06-22
Hey can someone help me figure out how to move a file from my desktop to my root.  I can't drag, and drop.  I tried it in the terminal, and it says no such file or directory does not exist.  The file is "Debian_expiremental-i-.tar.gz"

The command I'm running is 
```
-desktop:~$ mv .Debian_expiremental-i-.tar.gz /
```

---

### Post by Oldsoldier2003 on 2008-06-22
> **Nazty_Nayt said:**
> Hey can someone help me figure out how to move a file from my desktop to my root.  I can't drag, and drop.  I tried it in the terminal, and it says no such file or directory does not exist.  The file is "Debian_expiremental-i-.tar.gz"

The command I'm running is 
```
-desktop:~$ mv .Debian_expiremental-i-.tar.gz /
```

to move it from the gui youll need to launch nautilus as root/superuser.

```
gksu nautilus
```

or you can ```
sudo mv .Debian_expiremental-i-.tar.gz /.Debian_expiremental-i-.tar.gz
```

---

### Post by forestpixie on 2008-06-22
You are not at your desktop, you only think you are the real desktop is Desktop :)

sudo mv ~/Desktop/file /new/destination

should work I think

---

### Post by Oldsoldier2003 on 2008-06-22
> **forestpixie said:**
> You are not at your desktop, you only think you are the real desktop is Desktop :)

sudo mv ~/Desktop/file /new/destination

should work I think

good catch :) I should have told him to ls -al and it would have shown him the file wasn't there !

---

### Post by forestpixie on 2008-06-22
I spent ages trying to get to the xorg file in x11 when I first pitched up with the windows case is unimportant mentality :D . Once you've got that, desktop and Desktop are obviously different - it's just so intuitive for new users ;)

---

### Post by Nazty_Nayt on 2008-06-22
Thanks again, that should be all of my questions for me, (tonight anyways).  Got more stuff to do tomorrow so, I'll probably have more then.

Thanks again

:guitar:

---

