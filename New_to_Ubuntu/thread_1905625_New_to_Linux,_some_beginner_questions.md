---
title: "New to Linux, some beginner questions"
date: 2012-01-07
forum: New to Ubuntu
---

### Post by Takeox on 2012-01-07
Hello, I have been running Ubuntu 11.10 alongside with Windows 7 (using Wubi) for a few days and I am amazed on how fast, secure and easy to use it is (I'm even starting to love the Terminal, much prettier than Windows cmd:D), so now I'm planning to shrink my C:\ drive to 400 Gb to make a 100 Gb partition for Ubuntu, and see if I can replace Windows to make Ubuntu my primary OS.

I have researched about replacing Windows with Ubuntu (what I've learned is that for every aspect there is an open-source solution/alternative for Windows programs), and I am about to take the  jump, but I have one solely question: What about gaming? I have researched about Wine and PlayOnLinux, but I have read that the overall gaming performance is not as good as in Windows. How much is the difference? I use my desktop mainly for gaming so this is an important point to consider. Actually, the only games I would like to play on Ubuntu are Battlefield 3 and Steam games (not from Valve, games that require the Steam client to run)

System specs:
CPU Intel Core 2 Quad  Q9400 @ 2.6 Ghz
4Gb DDR2 800Mhz Corsair
Asus Sriker II Formula Motherboard
2x Nvidia GTX 260 running in SLI (my monitor resolution is 1920x1080)
500Gb Sata II 7200RpmHDD ( Windows + Linux)
1Tb Sata II 7200 Rpm HDD (Games and Storage)

I have also heard about Ubuntu Gaming Edition. What is the difference, except that it comes with wine and some other apps preinstalled? Gaming performace improvement?

Sorry if this goes in another category, if not, please move it or tell me to move it.

Regards
Takeox

---

### Post by Basher101 on 2012-01-07
the difference is about a year (thus all the high-end games of **_last_** year start to be stupported). Wine can also have some problems with directX since it is exclusiveley made for windows, so some games might not run perfectly because some .dll files are missing. If you really plan to switch OS, do not do so entireley. My current setup looks like this:

i got a 1,5 TB HDD
i gave ubuntu 100 GB
i gave windows 100 GB
and i set up a shared partition with the rest of the space where i install all my windows games to and store music, downloads, videos from both OSs. (note: i have no swap because my 8 GB ram are more than enough :p)

i stripped everything from windows i do not need for gaming...so i first installed all the drivers, then deleted everything non-relevant: browsers, antivirus, LAN-drivers (to cut it off the internet), and all the programs...so the only thing left are the games, the drivers for them and thats it. 

For everything else is Ubuntu. You should go for this dualboot to keep the best form both worlds.

regards

---

### Post by Paqman on 2012-01-07
Unfortunately Ubuntu is not nearly as good for gaming as Windows. There's nothing wrong with having a dual-boot to keep your Windows games around.

Wine is useful, but mostly with older games. Very few games work perfectly without fiddling about, although support improves all the time. Play On Linux does makes life a lot easier, I definitely recommend it. However, at the end of the day it's always easier and more painless to just use Windows. The games are native, the graphics drivers are better and you don't need to faff about with compatibility layers.

Probably not what you wanted to hear, but gaming really is Linux's Achilles' Heel on the desktop. Many of us would have happily deleted Windows years ago if it wasn't for games.

---

### Post by carl4926 on 2012-01-07
In all honesty
If you need real gaming
You will be better using windows

Many games do run in wine. I use some and they actually work better than in windows. But most are not like that.

It sounds like you'll be keeping windows, so it shouldn't be a problem.

Take the leap, you'll not look back!

---

### Post by Takeox on 2012-01-07
Thanks you so much for your quick answers.Yeah, I was also thinkming on dual booting. But, it might be frustating to reboot and switch over to another OS every time I wan to play something. Isn't there a way to rn both OS simultaneusly, like a Virual Machine??


Takeox

---

### Post by jockyburns on 2012-01-07
Personally I'd install Ubuntu alongside Windows  as a dual boot, so you can choose which OS to use. Win games don't run as well under Ubuntu, using Wine or P.O.L as they do in Windows. (I used to play Eve Online) but since moving to Ubuntu I've had to give that up) Installing Eve in Wine turned out to be a total nightmare (and that's just one game)
So as said, install Ubuntu as a dual boot on your comp, then when you want to play games, you can boot to Windows and when you want to do other things you can boot to Ubuntu. 
Best of both worlds.

---

### Post by BlinkinCat on 2012-01-07
Here's some info on dual booting if you want it - :)

[https://help.ubuntu.com/community/WindowsDualBoot](https://help.ubuntu.com/community/WindowsDualBoot)

---

### Post by Basher101 on 2012-01-07
a virtual machnie is some solution, but only if you have the hardware for it.

Also, the virtual graphics card of the Virtual machine won't be near the performance of your real one, so you will only be able to play some older games.

---

### Post by Paqman on 2012-01-07
> **Takeox said:**
> Isn't there a way to rn both OS simultaneusly, like a Virual Machine??


Yes, but VMs suck massively for gaming, due to very limited hardware graphics acceleration support. Until a couple of years ago there was no GPU support at all in VMs. 

That's not a Linux-specific problem btw, it's the same on VMs under any OS.

---

### Post by Takeox on 2012-01-07
Seems like I'll follow your example BSher101 :D
I must say, I'm totally surprised on how fast do i get answers here. I posted a problem ( actually sent a mail to windows customer support) 1 year ago. Never became an answer, and i was only adviced to call the service center via telephone ( which is quite expensive since I live in chile, southamerica) 

What do you mean with virtual graphics card? Can't both OSs run stthe same time using the sam hardware?

Takeox

---

### Post by Basher101 on 2012-01-07
A **_virtual_** machine has that name for a reason. All the hardware is emulated, it is virtual. That is why the virtual graphics card of **_any_** virtual machine is not very capable and won't be able to run the latest games, only older ones. If you insist on gaming, a dualboot with a stripped windows is your best go. (If stripping it is too much of a hassle just leave it as it is...stripping does increase boot speed but it may not be worth the work for others..)

p.s. i will always answer new threads because i click the "New Posts" button every 20 seconds :p

---

### Post by Takeox on 2012-01-07
Mmm, I see..... What is actually strippling? I'm going to research about and see if it convices me lol :D

Btw, thank you so much for your advice ;)

Regards

Takeox

---

### Post by Paqman on 2012-01-07
> **Takeox said:**
> What do you mean with virtual graphics card? Can't both OSs run stthe same time using the sam hardware?


Virtual Machines create a virtual version of all the componants of a machine (graphics cards, network cards, etc). They present this to the OS as "virtual machine", and the OS interacts with it.

The problem with VMs is that the virtual graphics card can't really exploit the full power of the actual graphics card. Unlike CPUs, which have built-in support for virtualisation, graphics cards aren't very virtualisation-friendly. That's not surprising, since most of the money behind virtualisation is focussed on servers, not desktops.

---

### Post by Basher101 on 2012-01-07
by stripping you delete everything you do not need for gaming (e.g. browsers, windows tools, programs, and so on...) i was looking into making a custom windows 7 installation DVD where i install only the things i want, but i failed and ended up installing it with all the bloatware i had to remove afterwards (i cannot remove all of it). I saw some screenshots of ppl making such a custom install and using only 2 GB (a normal install takes 16 GB)

---

### Post by JKyleOKC on 2012-01-07
> **Takeox said:**
> What do you mean with virtual graphics card? Can't both OSs run at the same time using the same hardware?The VMs have their own virtual hardware, that "goes in between" the program they are running and the actual hardware that displays the output. This additional in-between layer is what slows things up and may cause performance to be poorer.

I'm not a gamer so have never experienced such problems myself, but your hardware specs indicate that you should be able to get passable (if not perfect) performance using VirtualBox 4.1 inside of Ubuntu. My suggestion is that you follow your original dual-boot plan, to be sure of keeping Windows available if it's needed, then install VirtualBox from the Oracle site rather than from the Software Center (to be sure of having the latest version), and see whether it's good enough for your needs. If it is, you won't need to re-boot to use Windows, and if it's not, you can remove the software and go with your original approach.

---

### Post by Takeox on 2012-01-07
Lol I thought you meant creating a RAID 0 array,it seems to be easier than what I thought :D.

So yeah,just games on my Windows and the rest goes to Ubuntu:p
Which means: PROBLEM SOLVED!!

Thanks to all of you guys :D

Takeox

---

### Post by Paqman on 2012-01-07
> **Basher101 said:**
> by stripping you delete everything you do not need for gaming (e.g. browsers, windows tools, programs, and so on...)

Check out nLite or vLite, depending on your version of Windows. Generally speaking I found it a bit more of a pain than it was worth. Unless you have quite an in-depth knowledge of the Windows system it can be difficult to know what can be safely removed.

---

### Post by Basher101 on 2012-01-07
> **JKyleOKC said:**
> My suggestion is that you follow your original dual-boot plan, to be sure of keeping Windows available if it's needed, then install VirtualBox from the Oracle site rather than from the Software Center (to be sure of having the latest version), and see whether it's good enough for your needs. If it is, you won't need to re-boot to use Windows, and if it's not, you can remove the software and go with your original approach.

+1 
covering all apsects.

---

### Post by Takeox on 2012-01-07
> **JKyleOKC said:**
> The VMs have their own virtual hardware, that "goes in between" the program they are running and the actual hardware that displays the output. This additional in-between layer is what slows things up and may cause performance to be poorer.

I'm not a gamer so have never experienced such problems myself, but your hardware specs indicate that you should be able to get passable (if not perfect) performance using VirtualBox 4.1 inside of Ubuntu. My suggestion is that you follow your original dual-boot plan, to be sure of keeping Windows available if it's needed, then install VirtualBox from the Oracle site rather than from the Software Center (to be sure of having the latest version), and see whether it's good enough for your needs. If it is, you won't need to re-boot to use Windows, and if it's not, you can remove the software and go with your original approach.

That's what I am planning to do :D

---

### Post by Basher101 on 2012-01-07
> **Takeox said:**
> That's what I am planning to do :D

hope you are successful and enjoy your stay with ubuntu. You should also check out how you can custimize your interface and try out different Desktop Environments (you have currently 2 installed, Unity and Gnome 3. You can switch them on the login screen when clicking on the small icon on the right where you type your password).

always keep in mind the philosophy behind the Free Open Source Software movement.


regards

p.s. mark your thread as [SOLVED] with the forum tools at the top right if you do not have any further questions.

---

### Post by candtalan on 2012-01-07
> **Takeox said:**
>  I must say, I'm totally surprised on how fast do i get answers here 

LOL great! it is partly because many of those who use such as Ubuntu really *love* it and the community which supports it. Some questions are harder than others though.....
:-)

And - Welcome to Ubuntu!

---

### Post by asifnaz on 2012-01-07
If you are a hardcore gammer you should use windows for gaming or buy a gaming console

---

### Post by Takeox on 2012-01-07
> **candtalan said:**
>  And - Welcome to Ubuntu!

Hahaha with that phrase I imagine myself as a sailor whose mates telll him "welcome aboard the USS Ubuntu" :D

---

