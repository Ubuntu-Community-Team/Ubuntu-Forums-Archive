---
title: "Won't let me enter root password!"
date: 2008-07-13
forum: New to Ubuntu
---

### Post by YoB1U1N1T1U on 2008-07-13
I'm a noob to Linux. I'm installing a program (Wolfenstein enemy territory) and it asks for the root password in terminal. 

The cursor is right there, but I can't type anything!

help!

---

### Post by lisati on 2008-07-13
I assume that you are using "sudo" to do the installation: don't panic if the password doesn't show when you type it, because it is kept invisible for security reasons. Just type in your normal password and press "Enter".

---

### Post by YoB1U1N1T1U on 2008-07-13
thanks for super fast reply.

It asks for " It is recommended to install as the super User. Please enter the root passwork or hit enter to continue as is."
Password:

I just typed in my password without seeing it or mask, and hit enter. It says "su: authentication failure." Are you sure I'm typing in the password?

the root password is the same password I use to login correct?
thanks

---

### Post by lisati on 2008-07-13
> **YoB1U1N1T1U said:**
> thanks for super fast reply.

It asks for " It is recommended to install as the super User. Please enter the root passwork or hit enter to continue as is."
Password:

I just typed in my password, and hit enter. It says "su: authentication failure."

the roor password is the same password I use to login correct?
thanks
If you're running a command from the terminal to install your program, put "sudo" in front of the command, and use the same password as you use to login with.

---

### Post by YoB1U1N1T1U on 2008-07-13
I'm just double clicking a .run file to install. It is on my desktop. I'm not familiar with command yet.

---

### Post by hyper_ch on 2008-07-13
well, how would you try to run it from the command line?

---

### Post by YoB1U1N1T1U on 2008-07-13
.run package. I just doubled clickon that. It brought me to terminal to enter password.

---

### Post by ChameleonDave on 2008-07-13
> **YoB1U1N1T1U said:**
> I'm just double clicking a .run file to install. It is on my desktop. I'm not familiar with command yet.
Open up the terminal program.

Type this into it:

```

sudo ~/Desktop/*.bin

```

That will run the file on the desktop ending in ".bin".  If you have more than one such file on the desktop, then put the actual name instead of the asterisk.

---

### Post by YoB1U1N1T1U on 2008-07-13
alright. Instead, I just dragged and droped the .run into terminal, and it auto. typed the address there. I just typed sudo in front and bam it worked...

BUT:

now I get error that says "error while loading shared libraries: libgth-1.2.so.0..." I looked it synaptic and I have libgth-2.0-0 installed.

what to do?

---

### Post by ChameleonDave on 2008-07-13
> **YoB1U1N1T1U said:**
> alright. Instead, I just dragged and droped the .run into terminal, and it auto. typed the address there. I just typed sudo in front and bam it worked...

BUT:

now I get error that says "error while loading shared libraries: libgth-1.2.so.0..." I looked it synaptic and I have libgth-2.0-0 installed.

what to do?
Really?  I haven't got anything to do with libgth.

I am now downloading the game to see.

---

### Post by YoB1U1N1T1U on 2008-07-13
There is a 30 pages thread on this forum just on installing this game.

I read there that I should install libgth 1.2

---

### Post by Paqman on 2008-07-13
> **YoB1U1N1T1U said:**
> 
The cursor is right there, but I can't type anything!


When entering your password into the terminal the cursor won't react when you hit the keys. This is normal. Rest assured, your password is going in. Just try typing it in and hit enter, it'll work fine.

---

### Post by hyper_ch on 2008-07-13
(1) install apt-file
(2) update apt-file
```

sudo apt-file update

```
(3) search for the file
```

apt-file search libgth-1.2.so.0

```

Then you will get a list of packages that have this file included.

---

### Post by ChameleonDave on 2008-07-13
> **hyper_ch said:**
> 
sudo apt-file update
Nope.  That bit just fails, saying it can't find the files it needs.

Anyway.

I downloaded the .bin and ran it.  It installed just fine.  If you run if without sudo, it simply asks you for your root password (disabled by default on Ubuntu) and says that it will just install it in your home directory if you don't give it, which is absolutely fine.  I decided to run the installer again with sudo.  It then recognises that it is already root, and doesn't ask for the root password.  I don't anything difficult about it.

When I got into the game, I found I couldn't join any of the servers because they had a more up-to-date version of the software.  Since I downloaded the software just minutes before from the official site, this is idiocy on the part of the developers.  There didn't appear to be any sound either.

I'm not going to persevere with it.  There are games in the repos which work.

---

### Post by hyper_ch on 2008-07-13
it fails at certain packages but still gets a list ;)

---

### Post by ChameleonDave on 2008-07-13
> **hyper_ch said:**
> it fails at certain packages but still gets a list ;)

```

david@Chameleon:~/Desktop$ sudo apt-file update
[sudo] password for david:                     
Can't get http://au.archive.ubuntu.com/ubuntu/dists/hardy-backports/Contents-i386.gz
Can't get http://archive.canonical.com/ubuntu/dists/hardy/Contents-i386.gz          
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz
Can't get http://au.archive.ubuntu.com/ubuntu/dists/hardy-proposed/Contents-i386.gz
Can't get http://packages.linuxmint.com/dists/elyssa/Contents-i386.gz
Can't get http://packages.linuxmint.com/dists/elyssa/Contents-i386.gz
Can't get http://packages.linuxmint.com/dists/elyssa/Contents-i386.gz
Can't get http://packages.linuxmint.com/dists/elyssa/Contents-i386.gz
Can't get http://ppa.launchpad.net/reacocard-awn/ubuntu/dists/hardy/Contents-i386.gz
Can't get http://ppa.launchpad.net/kubuntu-members-kde4/ubuntu/dists/hardy/Contents-i386.gz
Can't get http://98111.free.fr/apt/dists/gutsy/Contents-i386.gz
Can't get http://javadesktop.org/lg3d/debian/dists/stable/Contents-i386.gz
Can't get http://getswiftfox.com/builds/debian/dists/unstable/Contents-i386.gz
Can't get http://ppa.launchpad.net/lxde/ubuntu/dists/hardy/Contents-i386.gz
Can't get http://security.ubuntu.com/ubuntu/dists/hardy-security/Contents-i386.gz
Can't get http://au.archive.ubuntu.com/ubuntu/dists/hardy-updates/Contents-i386.gz
david@Chameleon:~/Desktop$ sudo apt-file search libgth-1.2.so.0
[sudo] password for david:
david@Chameleon:~/Desktop$

```

---

### Post by hyper_ch on 2008-07-13
are you sure the file is called libgth-1.2.so.0 and not libgthread-1.2.so.0?

---

### Post by PCMan on 2008-07-13
> **YoB1U1N1T1U said:**
> I'm a noob to Linux. I'm installing a program (Wolfenstein enemy territory) and it asks for the root password in terminal. 

The cursor is right there, but I can't type anything!

help!

When you input your password, nothing will show.
There is no ****. This is for security reason (don't let others know the length of your password).
So, just keep typing your password, and hit enter key when you're done.

---

### Post by YoB1U1N1T1U on 2008-07-13
thanks

I finally got this installed. But now I have more issues. The game needs to Download maps/updates, when it tries to do this, the game just quites. I think the problem is that it has no access/permission to root? correct? 


thanks

---

### Post by ChameleonDave on 2008-07-13
> **YoB1U1N1T1U said:**
> thanks

I finally got this installed. But now I have more issues. The game needs to Download maps/updates, when it tries to do this, the game just quites. I think the problem is that it has no access/permission to root? correct? 


thanks
No.  As I said, to give it root access, all you have to do is run the script with sudo.

If you don't run it with sudo, it will install it to your home directory, which is also fine.

---

