---
title: "To 64 bit or not to 64 bit?"
date: 2008-10-22
forum: New to Ubuntu
---

### Post by Vunutus on 2008-10-22
I currently run only 32 bit XP Home on this computer, but am wanting to switch to vista business/ubuntu (vista only because I can get it free legally). I have a fairly old (~2 years or so) Athlon 64 single core CPU. I've heard horror stories about 64 bit XP so I stayed away from it. I've heard that Vista 64 bit handles it better, however. 

Is it worth it for me to dual boot 64 bit vista and 64 bit ubuntu? Will I have any sort of compatibility problems with games or software?

---

### Post by jseiser on 2008-10-22
The greatest software problem you will have is that flash is pretty hit or miss.  Their is no linux 64 bit flash.  You can use ndiswrapper to run the 32bit flash or try using swfdec or gnash.  I have had success with all three, and also had some installs that wouldnt work with either of them.  If you arent going to be crunching numbers and using tons of ram, then you really wont see a difference in 32 vs 64.  I will say, when doing really intensive work, the 64bit seems to handle it better, but again, what are you going to be doing on the PC.  That said, all my PC's are 64bit except 1.

---

### Post by stmiller on 2008-10-22
64bit Linux is actually very mature (compared to Windows). With 64bit Ubuntu as of Hardy flash in the browser just works. Ubuntu has done a lot of work for 64bit for the end user.

---

### Post by wolfen69 on 2008-10-22
[advantages and disadvantages]("http://ubuntuforums.org/showthread.php?t=765428")

---

### Post by tjwoosta on 2008-10-22
> Their is no linux 64 bit flash.

thats not true!!

i have 64bit Hardy and flash works perfectly

its as simple as
```
sudo apt-get install flashplugin-nonfree
```

infact i have never encountered anything that doesn't work in 64bit


i guess sun java doesnt exist for 64bit, but you can easily use 32bit java or 64bit open jdk 

the only thing that should stop you from upgrading to 64bit would be if you have issues with drivers

but if you can find all the drivers that you need, then i say go for it, install 64bit

---

### Post by aimpau on 2008-10-22
In 64 bit, you'll be using more ram, thus must have a good motherboard with a good PSU and processor.

It's more about the cost actually.

---

### Post by jerome1232 on 2008-10-22
> **tjwoosta said:**
> thats not true!!
i have 64bit Hardy and flash works perfectly


It is true, flash is 32 bit, we just have nspluginwrapper that makes it work in a 64 bit browser.

Actually sun's Java works too you just have to install a 32 bit chroot environment, install a 32-bit browser and do it that way. so it's a huge hassle.

edit: 64-bit does use a bit more ram, but I have 1 GB of ram and don't notice a difference.

---

### Post by hyper_ch on 2008-10-23
you can install sun java also directly from the repos - works fine here.

---

### Post by Sef on 2008-10-23
> Actually sun's Java works too you just have to install a 32 bit chroot environment, install a 32-bit browser and do it that way. so it's a huge hassle.

There is a java bit version of Java out now.  There is also [OpenJDK]("http://ubuntuforums.org/showthread.php?t=774956")- a open source version of Java..

---

### Post by jerome1232 on 2008-10-23
Your right, They do have a 64 bit binary. I've always just used whatever ubuntu-restricted-extras give me because I never actually use java.

---

### Post by crazyness003 on 2008-10-23
[LEFT]Go 64bit. The more people use it -> the greater the demand for it -> The better it'll be supported. Plus, I've seen bootup times 60-80% higher in 64bit. Yes more ram is consumed, but then again, once its booted, you wot feel a difference. I like to use it just becasue I can, i dont use it for its intended purpose (massive number crunching, like video encoding, decrypting, or process-intensive mathamatical calculations)

Then again, flash works for me (dont remember how). Flash 10 is almost flawless. The same things that bug 32 bit do so in 64. Everything else is a wonder.

Also, if you plan on using some EXTREMELY new stuff, there might not be 64bit support for it, so consider that as well.

If you're like me, you go 64 bit just because. Otherwise, its your choice
[/LEFT]

---

### Post by pissedoffdude on 2008-10-23
I"m running 64-bit ubuntu and have no problems at all.  Though I will admit I ran into some problems using 64-bit ubuntu in the past, it was really matured.  Flash, Java, and and playing vids should work without a hitch. For Java, however, you'll need to use the icedtea firefox plugin, as sun offers no 64-bit browser plugin. That being said, 64-bit Hardy works great.  You probably won't run into any issues because of the processor architecture.

---

### Post by roger_1960 on 2008-10-23
Hi

Dont know about Vista but I am running 8.4.01 64bit on an Acer laptop with 512Mb Ram and an AMD Turion 64 Mk36  I have not had any problems at all and think it is slightly quicker than 32 bit.

---

