---
title: "From Vista to Ubuntu 8.04.1"
date: 2008-07-23
forum: New to Ubuntu
---

### Post by klars on 2008-07-23
Hi all!
I am new here + i just moved from Vista to Ubuntu 8.04.1
Please suggest me what i should do now (i have updated it and chosen all update types in update configuration window (don't remember name).
I have installed wine, but it is just wine 1.0 but out there is wine 1.1.1   how i can get this package without destroying my system in future? I have installed steam + on steam i have installed Counter strike source + Day of defeat source (soon will install others). CSS quits after going into server. DODS dont have fonts - there are black [] insted of fonts. CSS cold use some beter fonts too.
I really need professional help on this if I am to stay in ubuntu otherwise i will have no choise and install back that Vista again, but i know there is many peoples that have managet to get it working. My pc have good configuration.
THANKS!

What ever you tell, just try not to kill my ubuntu control... :)

---

### Post by klars on 2008-07-23
How can i get the newest software from its creators like latest nvidia drivers for geforce 8800 gts? Ubuntu have theyre own software dreams and sometimes it is bit older then i whant it to be :confused:

OK the biggest probleme is my wine 1.0 version...

---

### Post by Dark_Stang on 2008-07-23
If you're looking to play windows games you should keep windows around to play them. However, if you want to play around with Ubuntu to see what it's like, I encourage it. There are plenty of games you can play on Ubuntu. Two first person shooters I play on a completely random basis are Alien Areana and Nexuiz.

Edit: As far as getting the latest software, you can download them from the maintainer's websites. However you may have to compile it yourself to get it working well. The beauty of using the software Ubuntu (and it's community) maintains is that you get something that's already setup for you, and something that you know will work for you.

---

### Post by klars on 2008-07-23
But there are meny who play windows games on ubuntu, am i wrong?
Like CSS and DODS

---

### Post by Canis familiaris on 2008-07-23
> **klars said:**
> But there are meny who play windows games on ubuntu, am i wrong?

Yes. But it is tricky.

---

### Post by klars on 2008-07-23
Well? Enyone from you have done something like that? I am listening! :popcorn:

Common guys - you do know how to do that ):

---

### Post by ad_267 on 2008-07-23
I have counter strike source working.

I followed this: [http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731](http://appdb.winehq.org/objectManager.php?sClass=version&iId=3731)

---

### Post by klars on 2008-07-23
Enything useful that i should do with ubuntu new installation? i am new with ubuntu and linux at all.

---

### Post by ad_267 on 2008-07-23
One thing you will probably want to do is install the ubuntu-restricted-extras package. [https://help.ubuntu.com/community/RestrictedFormats](https://help.ubuntu.com/community/RestrictedFormats)

Also this is probably a good read, how to install anything in Ubuntu: [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)

Other than that just have fun, read the forums and ask if you need help. Some things are a bit different and take getting used to. I've loved every minute of using Linux and wish I'd switched sooner.

---

### Post by combatwombat_nz on 2008-07-23
> **klars said:**
> How can i get the newest software from its creators like latest nvidia drivers for geforce 8800 gts? Ubuntu have theyre own software dreams and sometimes it is bit older then i whant it to be :confused:

OK the biggest probleme is my wine 1.0 version...

[http://www.nvidia.com/Download/index.aspx?lang=en-us](http://www.nvidia.com/Download/index.aspx?lang=en-us)

Takes you to nVidia's driver download page. ###WARNING### You do need to have a clue when it comes to using these drivers. Unfortunately this is not "Windows Preschool" style driver loading.

Download the driver for your architecture/card. eg AMD 64 and GeForce 8800.
Then when it is saved to your desktop you need the terminal:
chmod +x ~/Desktop/NVIDIA*run
then
when you are ready to install the driver you need to do it from the terminal outside of the Gnome/KDE or whatever you use. Press CTRL+ALT+BackSpace to get there. Then CTRL+ALT+F2. Login. Then type:
sudo ~/Desktop/NVIDIA*run
This will start the installation of the driver.
Answer whatever it asks affirmatively, then when it finished:
sudo reboot
###2nd Warning### Every time you update Ubuntu's kernel through it's automatic update system you will need to reinstall the driver with sudo ~/Desktop/NVIDIA*run again. This gets old real fast. There is a post here somewhere about the process for doing this automatically.

---

### Post by klars on 2008-07-23
Thx for info! :)

How i can get 1 user that can get in with no password (ok, simple pass is ok...) and there he can chage admin settings with root password or something like that? I whant to do everything in one account and i have other peoples in home...

---

### Post by klars on 2008-07-23
How i can make some useful configuration with users? Anyone have any links?

---

### Post by klars on 2008-07-23
And what is with that "Ubuntu Studio"? it was on 7.. Ubuntu

---

### Post by mlentink on 2008-07-23
Might I respectfully point to the link in my sig. Just so as to avoid dissappointment. 
You have already been pointed to [this]("http://monkeyblog.org/ubuntu/installing/") but [this one]("http://www.psychocats.net/ubuntu/") is also quite good. And obviously [https://help.ubuntu.com/](https://help.ubuntu.com/)

But in general: if you're looking to run windows applications, running them in windows is your best option. On the other hand, there are a huge number of native programs that might do what you want. Granted, less games. See also here: [http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by billgoldberg on 2008-07-23
> **klars said:**
> Enything useful that i should do with ubuntu new installation? i am new with ubuntu and linux at all.

Check the codec and customization link in my signature.

Also for help on getting games working ok, check the wineaqq website for instructions.

---

### Post by billgoldberg on 2008-07-23
> **klars said:**
> Thx for info! :)

How i can get 1 user that can get in with no password (ok, simple pass is ok...) and there he can chage admin settings with root password or something like that? I whant to do everything in one account and i have other peoples in home...

If you are talking about a root account, don't do it.

You are obviously new to linux and would screw up your system in record time.

---

### Post by Dutch70 on 2008-07-23
You may also want to check this thread for a multimedia and video **how to**
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Dutch

---

### Post by angelsguitar on 2008-07-23
> **klars said:**
> Enything useful that i should do with ubuntu new installation? i am new with ubuntu and linux at all.

I would recommend you take a look at this multimedia how-to:

[http://ubuntuforums.org/showthread.php?t=766683]("http://ubuntuforums.org/showthread.php?t=766683")

It will allow you to run most multimedia formats (even Windows ones) and enable dvd playback support in Ubuntu, which is not enabled by default due to copyright reasons.

I always follow this how-to when I install a fresh copy of Ubuntu in a machine (just after downloading updates, of course).

---

### Post by angelsguitar on 2008-07-23
> **Dutch70 said:**
> You may also want to check this thread for a multimedia and video **how to**
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683)

Dutch

Oh, well, someone made the suggestion first while I was typing.  My previous post points to that same how-to.  Ops! Sorry for that.

> How i can get 1 user that can get in with no password (ok, simple pass is ok...) and there he can chage admin settings with root password or something like that? I whant to do everything in one account and i have other peoples in home...

As someone stated before, it is not recommended to log in as root; you could damage your system.  If you want, you can configure Ubuntu to log one of the preconfigured users (like yourself!) automatically, so you don't have to put the password everytime you log in.  To do that, go to System - Administration - Login Window, input your password when asked, then click on the Security Tab (once the window opens).  Once there, click on "Enable automatic login" and choose the user you want the system to log in automatically from the list.

> And what is with that "Ubuntu Studio"? it was on 7.. Ubuntu

UbuntuStudio is a version of Ubuntu preconfigured and optimized to do Multimedia work, like Audio/Video/Graphics recording and editing.

---

### Post by Zlatan on 2008-07-23
> **klars said:**
> Hi all!
I am new here + i just moved from Vista to Ubuntu 8.04.1
Please suggest me what i should do now (i have updated it and chosen all update types in update configuration window (don't remember name).
I have installed wine, but it is just wine 1.0 but out there is wine 1.1.1   how i can get this package without destroying my system in future? I have installed steam + on steam i have installed Counter strike source + Day of defeat source (soon will install others). CSS quits after going into server. DODS dont have fonts - there are black [] insted of fonts. CSS cold use some beter fonts too.
I really need professional help on this if I am to stay in ubuntu otherwise i will have no choise and install back that Vista again, but i know there is many peoples that have managet to get it working. My pc have good configuration.
THANKS!

What ever you tell, just try not to kill my ubuntu control... :)

another short advise: [www.ubuntuguide.org]("http://ubuntuguide.org/wiki/Ubuntu:Hardy")

---

### Post by HieroPosche on 2008-07-23
As someone who is still fairly new to linux (a year and a half and I'm still new)  Gaming should be the least of your priorities when starting out.

It is certainly possible to run almost anything from windows in linux, but it takes significant know-how and considerably more time to accomplish it.

Sounds like the best bet for you would be a dual boot system.  If you have sufficient HD space (which I'd assume you do since you're running vista) follow one of the dozens of howto's to create a linux/windows system so you you will still have your games on hand.  That's how I started and it made the transition a lot easier.

If you're determined, I know more than a few guys who use a program (I believe) called CrossOver. I think you have to pay for it, but they claim it's considerably more stable a platform for games than wine.

In any event, Welcome to Linux!  Have fun, read a lot, and ask for help often.  Those are pretty much the keys to creating a system that works for you and does what you need it to. :)

---

### Post by mlentink on 2008-07-23
> **HieroPosche said:**
> Sounds like the best bet for you would be a dual boot system.

+1
Some of my customers simply do not want anything other than Windows in their network, so I oblige. With a dual boot (XP though, one can compromise only so far... ;-) )
system, you can always revert to windows to play those games. I simply do not have the time to invest in trying to get software made for another OS to work in linux, so I go for what works. Which actually is quite a lot.

---

### Post by Dutch70 on 2008-07-23
> angelsguitar;5441258]Oh, well, someone made the suggestion first while I was typing.  My previous post points to that same how-to.  Ops! Sorry for that.


At least we are in agreement...:)

And we both have a guitar in our avatar...except mine is prettier...lol, j/k. That's a really nice looking guitar in your avatar...:guitar:

[B]To klars...
+2 on dual booting, that should tell you something.[/B] 

Dutch

---

### Post by a0u on 2008-07-24
> **klars said:**
> Thx for info! :)

How i can get 1 user that can get in with no password (ok, simple pass is ok...) and there he can chage admin settings with root password or something like that? I whant to do everything in one account and i have other peoples in home...

You can already do everything you need in your account.

Windows is so insecure because it is careless with granting administrator privileges.  "Administrator" in Windows has a very different meaning than it does in Linux.  Community Docs has [a very good explanation](https://help.ubuntu.com/community/RootSudo) about why you should never need the root password.

---

