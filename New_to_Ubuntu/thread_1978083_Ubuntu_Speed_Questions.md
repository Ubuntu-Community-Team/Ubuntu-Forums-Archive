---
title: "Ubuntu Speed Questions"
date: 2012-05-11
forum: New to Ubuntu
---

### Post by comradeandy on 2012-05-11
First off I'd like to come out and say that I am fairly new to using Linux, I have been using Linux Mint 12 and Ubuntu 11.04 for a few months and I have recently installed Ubuntu 12.04 LTS. 

I'm a speed freak, so much that I can't stand to use any other browser except Chrome because even the slightest difference annoys me. Call me weird but when an application takes a second longer to open, I notice it. My question is ***why*** is Ubuntu 12.04 LTS so much slower than Mint 12? 

By slow I mean it opens applications noticeably slower such as Firefox and Chrome. It installs applications slower than Linux Mint 12, and even start up times are faster for me on Linux Mint 12.

Why is this? As far as I know Linux Mint 12 is based off Ubuntu. Could it be that Gnome 3 is simply faster than Unity as an interface? Any input is appreciated. 

Also, here are my computer specifications if anyone is interested. Note, on both operating systems I do not have my video card driver installed. For some reason, it never worked for me I simply get an error every time I try to install. (Yes it's an ATI card)

AMD 1090T Six Core Processor
16GB Ram
1TB 10,000 RPM HD
ATI 5570 HD 1GB GDDR5

---

### Post by kc1di on 2012-05-11
You could check your theory about Gnome 3 and Unity and Cinnamon by installing those desktops and comparing them to each other and reporting to the rest of us your findings.  Would be interesting. 

you can install Gnome 3 by going to the the software center and searching for gnome I believe the first entry is gnome desktop.

Cinnamon requires a little mere but here's a page that will instruct you on how to do it.

[http://www.ubuntugeek.com/how-to-install-cinnamon-1-4-in-ubuntu-12-0411-10.html]("http://www.ubuntugeek.com/how-to-install-cinnamon-1-4-in-ubuntu-12-0411-10.html")

After they are installed you can access them by logging out and at the signin screen click on the little ubuntu logo in the upper right of the sign in block. that will give you a list of available desktops.
By the way welcome to the forums.

---

### Post by Perfect Storm on 2012-05-11
Mint 12 is based on Ubuntu 11.10 so they use different kernel and versions of different libs etc. than ubuntu 12.04.

---

### Post by comradeandy on 2012-05-11
I will try installing Gnome 3 and see if that makes a difference. 

It's so interesting how one is faster than the other, surprisingly I'm not the only one out of my friends that believes so. I would think that Ubuntu would try to make their operating system as fast as possible. I wonder what Linux Mint is doing differently. 


I would love to use Ubuntu 12.04 LTS as my main operating system however I simply cannot get over the lag of opening programs, installing programs, and certain programs slowing down.

---

### Post by comradeandy on 2012-05-11
> **Artificial Intelligence said:**
> Mint 12 is based on Ubuntu 11.10 so they use different kernel and versions of different libs etc. than ubuntu 12.04.

Interesting. I would think that Ubuntu would want to make their software as fast as possible. What's different in each software is probably beyond what I can comprehend but the slowdowns are very apparent to me.  

I'd love to figure this out and use Ubuntu 12.04 as my main operating system, the support forums and chat rooms are much more helpful and the community is much larger.

---

### Post by jim Kane on 2012-05-11
> **comradeandy said:**
> I will try installing Gnome 3 and see if that makes a difference. 


i would be interested if you could try Xubuntu with your setup
Ubuntu always seems slower to me in comparison

---

### Post by d4m1r on 2012-05-11
You must be doing something wrong, as I have half the RAM you do (but still plenty @ 8GB) and Ubuntu is lighting fast in comparison to Windows 7 for example....Boots up in half the time, and launches any application in under a second. Not sure how my 12.04 install does in comparison, but if it's built of 11.10, then it should be almost identical performance.

My guess if your 12.04 install is broke or actually installing drivers for your GPU would solve these "speed issues".

---

### Post by mastablasta on 2012-05-12
> **comradeandy said:**
> Interesting. I would think that Ubuntu would want to make their software as fast as possible. What's different in each software is probably beyond what I can comprehend but the slowdowns are very apparent to me.  

I'd love to figure this out and use Ubuntu 12.04 as my main operating system, the support forums and chat rooms are much more helpful and the community is much larger.

Kernel has not much to do with ubunut. it's like you are comparing XP and win7. they have different kernel, win7 is "slower" but has more features.

additioanlly installing propper drivers might be the key.

---

### Post by I2k4 on 2012-05-13
> **mastablasta said:**
> ... it's like you are comparing XP and win7. they have different kernel, win7 is "slower" but has more features.

Agree with this.  After a lot of experimenting via Live USB I concluded Ubuntu ended its "XP" phase with version 10.10 and started a Vista/W7 phase with 11.04 / Unity.  Mint numbers seem to be one behind, such that Mint 12 is based on Ubuntu 11.10.  

On my little Acer netbook there was no speed comparison between any formulation of Ubuntu 10 and much slower 11 or later.  I'm going to live with Lubuntu 10.10 on the netbook until the machine breaks.  On my stronger Dell laptop I'm still playing with Live USB but found Mint 12 clunky and Ubuntu 12.04 worse. 

I think, like big new gee whiz Vista, this much more ambitious OS with new Linux kernel, new Gnome shell, new Unity, and new GUI layers to let you forget about them, is going to take a couple of years and Moore's Law hardware improvements to be good.  

That said, I've noticed that support for 10.10 has ended and things are not updating.

---

### Post by Javelin Dan on 2012-05-16
[FONT=Arial]Guess I’ll weigh in on this too. Currently running 12.04 (Power pc) on my wife’s eMac G4 (1-GB RAM, 40 GB hard drive). It definitely runs a tick slower than my beloved 10.10 did. I agree with the analogy of comparing XP and Windows 7. In spite of the slight penalty in speed, I love this distro and what it can do. I also love the 5-years Long Term Support. I installed the Lubuntu desktop mostly because I didn’t like the Unity set-up, but partly to see if I could pick up any speed - nothing noticeable there. This will probably be the last new OS for this computer. With the “resource creep” I keep seeing in Ubuntu (and other off-shoots), I doubt that this box will run or even boot up in anything new 5-years down the road. Not complaining, just sayin”…[/FONT]

---

### Post by Ubun2to on 2012-05-16
I thought Gnome 3 was slower than Unity...??? (At least in my experience.)
Anyway, try Unity 2D, and keep in mind the lag for some applications can be them not loading when you login. Startup applications generally open much faster-it's like water. Hot water boils faster, as it is already partially heated.
I decided to research this a little bit, and the system requrments are lower for LM13 than Ubuntu 12.04.
Ubuntu:
1 GB RAM
15 GB disk space
800*600 capable monitor
CD/DVD drive or USB (for installer)
1 GHz CPU x86
Source- [https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)
LM 13:
512 MB RAM (1 GB preferred)
5 GB disk space
800*600 capable monitor
CD/DVD drive or USB (for installer)
No CPU minimum specified
Source- [http://blog.linuxmint.com/?p=2010](http://blog.linuxmint.com/?p=2010)
The requirements are a little lower, but still, it's not that big of a difference, unless you're running an 8 year old machine. If you have a fair amount of RAM (as in 3 GB or more), I would investigate further.

---

