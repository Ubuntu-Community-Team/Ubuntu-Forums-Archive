---
title: "[SOLVED] Need Help In Manythings"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Gewalop on 2008-06-21
Hi everyone

i started many threads asking for help, and i noticed the great efforts that everyone make to get them solved

i want help in few things, so i put them in one thread


------------

* Everytime i try to install deb package i get Errors that i need libraries, i mean i want to install VLC from deb package, it says i need "libiso9660-5"
i want to install driver for my modem "Intel 536EP" it says i need
[COLOR="Red"]linux-image-2.6.24-17-generic
linux-image-2.6.24-18-generic
linux-image-2.6.24-20-generic[/COLOR]
i mean COME ON i'm using Ubuntu 8.04 LTS, and i need 2.6.24-20-generic, why?

------------

* how am i gonna connect to a wireless lan, i tried to find some network manager in Ubuntu that has wireless in it, i couldn't all i got was (Wired Connetion , Point To Point,) and no wireless


------------

* is there anyway that i could download all needed libraries then backup them for another computer


-----------


thank you

---

### Post by hyper_ch on 2008-06-21
(1) it is also adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

a generic topic title like "noob here" or "need help" does not help at all. As you may have notices, just about everyone posting in here has some kind of a problem or issue or question ;) 

(2) it is also adviced to open seperate threads for unrelated problems.

---

### Post by bijeeshvs on 2008-06-21
u cannot login to the GUI as root, but u can login into a terminal as root by simply opening a terminal from "applications=> accessories=> terminal " and type "su" then enter root password, and thats it u are root........................

---

### Post by bijeeshvs on 2008-06-21
about the wireless thing 

i am not so sure but i think its in the DVD of ubuntu install,
think u can use synaptic for installing wireless network tools

---

### Post by sailor2001 on 2008-06-21
it's wise to first check in synaptics for needed programs. That way all the dependency s are met as well as the program being able to be updated when necessary.

---

### Post by bodhi.zazen on 2008-06-21
> **bijeeshvs said:**
> u cannot login to the GUI as root, but u can login into a terminal as root by simply opening a terminal from "applications=> accessories=> terminal " and type "su" then enter root password, and thats it u are root........................

Please do not post information on enabling the root account, especially to new users, without appropriate information.

Appropriate information, IMO, includes at least (although I am sure other mods could add to the list):


[list=number]
[*]How to use sudo and gksu.
[*]Permissions.
[*]The risks of enabling the root account and circumventing linux permissions.
[*]How to re-lock the root account.
[/list]


While you are free to run your box the way you wish, enabling the root account is in general felt to be bad advice to new users and is discouraged on these forums.

[New forum policy on log-in-as-root tutorials - Ubuntu Forums](http://ubuntuforums.org/showthread.php?t=716201)

---

### Post by Gewalop on 2008-06-22
soz about asking about root thing, kk

okay, what about the modem thing

---

### Post by bodhi.zazen on 2008-06-22
> **Gewalop said:**
> soz about asking about root thing, kk

okay, what about the modem thing

What is this modem thing of which you speak ?

You will need to provide more information that that. Hardware ? what have you tried ? what is the problem ?

---

### Post by Nepherte on 2008-06-22
> **Gewalop said:**
> soz about asking about root thing, kk
You're not the blame. It is a perfectly normal reaction, certainly if you just migrated from windows where working with administrator accounts seems to be the normal way of doing things. We are here to point you out that linux works in a different way (in casu with sudo).

---

### Post by Gewalop on 2008-06-22
this modem thing
> i want to install driver for my modem "Intel 536EP" it says i need
[COLOR="Red"]linux-image-2.6.24-17-generic
linux-image-2.6.24-18-generic
linux-image-2.6.24-20-generic[/COLOR]
i mean COME ON i'm using Ubuntu 8.04 LTS, and i need 2.6.24-20-generic, why?

---

### Post by Nepherte on 2008-06-22
I don't really see a problem with the whole vlc thing requiring libiso9660-5. When I want to install vlc, I have to install that lib too. Just install it along with vlc.

I'm not sure what it is with the linux-image thing. I don't think -20 is in the official repositories yet. But again, installing the latest kernel fix is not a bad thing. As long as you keep your old kernel as well, you can boot from whatever you want.

---

### Post by bodhi.zazen on 2008-06-22
> **Gewalop said:**
> this modem thing

Please keep in mind we are all volunteers here. As far as why ? because the hardware manufacturer of your modem does not support linux.

Many people are on dsl or wireless so modems are somewhat outdated and you *may* have some difficulty here.

In terms of your kernel question you should install "linux-kernel-generic". This is a meta package and should keep everything working, unless you care to compile your own kernel of  course ...

Last, rather then "ranting" you might try posting the error message your are getting. I (an others) know how to handle specific hardware and specific error messages.

I do not know what to do with " i mean COME ON i'm using Ubuntu 8.04 LTS, and i need 2.6.24-20-generic, why?" How do you fix something like that ? No OS is "perfect" including windows.

---

### Post by Gewalop on 2008-06-23
> No OS is "perfect" including windows.

As for that I say, no OS is perfect especialy Windows

thanx for the help

okay, so where to download

[COLOR="Red"] linux-image-2.6.24-17-generic 
 linux-image-2.6.24-18-generic 
 linux-image-2.6.24-18-generic 
 linux-image-2.6.24-20-generic[/COLOR]

---

### Post by Nepherte on 2008-06-23
Normally you should have received an update notification for it, if you have the necessary repositories enabled. I figure you wouldn't need to install each kernel, you can't run multiple kernels at once anyways. To install:
```
sudo apt-get install linux-image-2.6.24-19-generic
```
This one is the latest kernel in the update repository. To enable it, navigate to system > management > software sources (or something that looks like it). Then choose the updates tab and check hardy-updates.

Another, perhaps better solution is to install the linux-generic package. This is a meta package that will make sure the necessary things are installed and that you will get updates for kernels in the future.
```
sudo apt-get install linux-generic
```

---

### Post by Gewalop on 2008-06-24
thanx big time dude!

solved

---

