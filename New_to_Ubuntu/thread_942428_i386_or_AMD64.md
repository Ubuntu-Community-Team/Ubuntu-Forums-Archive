---
title: "i386 or AMD64?"
date: 2008-10-09
forum: New to Ubuntu
---

### Post by GXice on 2008-10-09
Hi all, I'm going to take my first step into Linux tomorrow, wish me luck! :D

For now, the lucky distro I want to use is Xubuntu. I just like the icy blue interface, not so much a fan of the orange Ubuntu one. Or can I install Ubuntu and then just apply the Xubuntu desktop environment?

Anyway, getting off track. I have no idea which version I should download. The system itself is an AMD x2 5000+, so should I go for the AMD64 one?

If there are compatability problems like with Windows 64bit, I'll just grab the i386 version.

---

### Post by medic2000 on 2008-10-09
Not try 64bit. Because well the world isnt fully ready for it :)

Xubuntu is nice and a littler faster than Ubuntu. But first i suggest you to try pure Ubuntu. You can change the theme easily of course.

---

### Post by SOULRiDER on 2008-10-09
I use a Core2Duo processor with 64bit and i have no issues whatsoever, IMHO you should try using 64bit Ubuntu. You can install Ubuntu and then install XFCE, Xubuntu's desktop enviroment.

---

### Post by GXice on 2008-10-09
> You can install Ubuntu and then install XFCE, Xubuntu's desktop enviroment.

OK awesome, I'll do that then. But I already have a 32bit CD here with Ubuntu 8.04, so any special reason to download the 64bit version? I'm talking performance gains - will I notice any more speeeeeeeeed? :D

---

### Post by Bölvaður on 2008-10-09
> **GXice said:**
> OK awesome, I'll do that then. But I already have a 32bit CD here with Ubuntu 8.04, so any special reason to download the 64bit version? I'm talking performance gains - will I notice any more speeeeeeeeed? :D

There is little difference in speed between 32 and 64 bit versions. Perhaps it depends on the work you do.

But what you really should do is to install the default ubuntu as it comes off the cow (this is a qoute from my professor).

I would not advice you to install xfce deksktop evironments on that, not yet atleast. First change the themes (you can find themes on gnome-art and other websites that has to do with gnome).
Everything you can see can be changed, but it is way too drastic to change from gnome to xfce (xfce is really nice I am using it atm, but I recomand gnome over it any day).


1. install ubuntu
2. change themes
3. explore the programs in add/remove
4. fittle with compiz-fusion until you get annoyed with it
5. fittle with conky
6. reinstall newer version of ubuntu with all the knowledge you've gained.

---

### Post by GXice on 2008-10-09
> but it is way too drastic to change from gnome to xfce (xfce is really nice I am using it atm, but I recomand gnome over it any day).

Why is it drastic? I looked at screenshots, they look very similar, just the colour scheme and fonts are a bit different. But yes, I'll take your advice. I'll get used to GNOME first, as it seems to be the default "noob" thing to do. :D

---

### Post by deadite66 on 2008-10-09
from my experience i get xorg crashing in x64 both gutsy & hardy.
no problems with x86

---

### Post by Therion on 2008-10-09
If Xubuntu is what appeals to you, download and install Xubuntu.  There's no specific "path" of learning that starts with Gnome and then proceeds to something else.  If you like the look and feel of Xubuntu, install it.  Or, if you're unsure, burn a few LiveCD's (Ubuntu, Xubuntu maybe Kubuntu too!) and test drive them all before you install.  But don't get suckered into thinking there's a proper way to do this.  It's up to you what you want and what you want to install.

As for 32bit vs. 64-bit: I see no reason not to install the 64-bit version since your processor supports it.  Will you see a speed difference?  Probably not.  What I notice is... Well... I call it "smoothness".  The 64-bit versions of Ubuntu just seem to run more smoothly.  It's a hard thing to explain exactly, but having run both 32 and 64-bit systems, I can tell you I'll put up with a LOT before I'll go back to running a 32-bit distro again.  With recent releases of Ubuntu I've had zero problems under 64-bit.

---

### Post by medic2000 on 2008-10-09
In 64bit arent the programs limited than 32bit for now?

---

### Post by jerome1232 on 2008-10-09
Biggest gains for 64bit are number crunching
(compiling, video/audio encoding, compression, encryption, gaming)

And you can use as much ram as your motherboard will allow.

There are a few cases where commercial programs aren't avaible for 64bit, many of them work anyways (64bit is backwards compatible, it's library files that get you in trouble because they'll want the 32bit versions sometimes)

---

### Post by medic2000 on 2008-10-09
So if use a rare or new program maybe there isnt a 64bit version of it yet?

---

### Post by baizon on 2008-10-09
Hi, install the 64bit of Ubuntu _only_ if you have more than 4.0GB of memory and/or you compile many times and many programs, else i recommend the 32bit version.

---

### Post by Therion on 2008-10-09
> **medic2000 said:**
> So if use a rare or new program maybe there isnt a 64bit version of it yet?
You install the 32-bit version.

---

### Post by medic2000 on 2008-10-09
> **Therion said:**
> You install the 32-bit version.
If it is possible to install 32bit version of program on 64bit OS then 64bit has no disadvantages?

Is it?

---

### Post by Therion on 2008-10-09
> **medic2000 said:**
> If it is possible to install 32bit version of program on 64bit OS then 64bit has no disadvantages?

Is it?
I'm not going to promise you that no matter what you won't EVER run across some kind of a problem if you decide to install 64-bit.  

Personally, I've been running 64-bit Ubuntu for about the past two years and I've never had a problem.  Period.  Zero issues.  None.  Nada.  If you don't WANT to install 64-bit, then don't.  Stick with the 32-bit version if that's what works for you.  If it wasn't this way, I wouldn't be using a 64-bit distro; I don't have time to wrangle with my OS: It needs to be "install and go".

[quote="Linux.com"]32-bit binaries

As it turns out, the good people of Debian (on which Ubuntu is based) have already solved the problem of running 32-bit binaries on 64-bit Linux. The IA32 libraries provide everything you need to run 32-bit binaries. The command sudo apt-get install ia32-libs will install the libraries. If you get an error about an asound library being uninstallable, you should be able to fix it with the command sudo apt-get install libasound2=1.0.15-3ubuntu4.

That's it! Your 32-bit binaries and any included libraries should now be functional. [/quote]
I've never needed to do this in Hardy... It may be included by default, I don't know.  Like I said, it's never been an issue for me.  I install and I rock on...  I never even have to consider I'm running a 64-bit distro becuase it's never been an issue.


[Source](http://www.linux.com/feature/142075)

---

### Post by Gannon8 on 2008-10-09
> **jerome1232 said:**
> Biggest gains for 64bit are number crunching
(compiling, video/audio encoding, compression, encryption, gaming)

Yes, 64-bit will make your computer run faster with the more memory-intensive stuff. If you do a lot of video editing, serious gaming, or are planning to run a server, choose 64bit.

Actually, you might as well choose it anyway (Why not? :popcorn:)

---

### Post by Big_Kahunaca on 2008-10-09
> **Gannon8 said:**
> Actually, you might as well choose it anyway (Why not?

Seconded.  If the capabilities are there, why not use them.  64-bit is backwards compatible and chances are probably slim that you'd run into a problem.

I'm using the 64-bit version of Xubuntu 8.10 beta right now, it works fine, I can do everything I could do back in the 32-bit world.

---

### Post by medic2000 on 2008-10-09
I didnt know it was back compatible.Heheh then count me in. This night a new 64bit user was born! :P

---

### Post by Therion on 2008-10-09
> **Gannon8 said:**
> Actually, you might as well choose it anyway (Why not?)> **Big_Kahunaca said:**
> Seconded.  ...

I'm using the 64-bit version of Xubuntu 8.10 beta right now, it works fine, I can do everything I could do back in the 32-bit world.
Thanks, I was starting to feel like the Lone (64-bit) Ranger...

> **medic2000 said:**
> I didnt know it was back compatible.Heheh then count me in. This night a new 64bit user was born! 
Prepare for a faster, yet smooooooother, ride.

---

### Post by medic2000 on 2008-10-09
Yeahhhh! And with a 64bit Ubuntu accompanying 64bit Arch+Kdemod3 Core2Duo will rule! Thanks for the enlightment. Now lets rock 64biters!:guitar:

---

### Post by CAPLinux on 2008-10-09
I have a question for everyone,  I am currently running 32bit Hardy on an AMD Turion 64bit CPU.  I am in the process of maxing out the memory at 2GB.  Can I upgrade to 64bit without having to completely reinstall?  I want to start using VirtualBox to learn about Ubuntu server, and how to set it up with samba, so having the benefit of 64bit would be useful.

Thanks Everyone for your help. :)

---

### Post by jerome1232 on 2008-10-09
Unfortunately you have to nuke the installation to upgrade to 64bit.

---

### Post by OutOfReach on 2008-10-09
Yes, you have to reinstall to get 64 bit.

---

### Post by CAPLinux on 2008-10-09
OK, I thought that would be the answer I would get.  OK I have three partitions, /, /home and swap.  If I nuke the installation, how do I ensure my user accounts can access their home folders?

---

### Post by jerome1232 on 2008-10-09
Don't format /home and when setting up give all your users the same name as before.

---

