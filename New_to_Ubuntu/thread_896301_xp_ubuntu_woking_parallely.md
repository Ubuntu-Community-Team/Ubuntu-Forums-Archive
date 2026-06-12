---
title: "xp ubuntu woking parallely"
date: 2008-08-21
forum: New to Ubuntu
---

### Post by thehellboy on 2008-08-21
hi, i'm using ubuntu 7.04 and i want to use windows xp parallely with ubuntu, so that i can switch to xp and ubuntu easily without restarting.. is there any software or we can configue it.. do help me..

---

### Post by Dill on 2008-08-21
You'll probably want to install Windows XP using something like VirtualBox:

[http://www.virtualbox.org/](http://www.virtualbox.org/)

These look like some good instructions for installing it, as well:

[http://blog.cintegrity.net/blog/article/25](http://blog.cintegrity.net/blog/article/25)

Cheers, 
Dylan

---

### Post by Abdulkarim on 2008-08-21
its too difficult to do what you want but my suggestion is that try to istall both xp and ubuntu in diffent partions then through that you can access the files in xp while you are running ubuntu but viseversa you can't.

---

### Post by sherin on 2008-08-21
why dont you try Hardy , which comes with the option to install ubuntu on a windows box?

---

### Post by prshah on 2008-08-21
> **thehellboy said:**
>  so that i can switch to xp and ubuntu easily without restarting

> **sherin said:**
> why dont you try Hardy , which comes with the option to install ubuntu on a windows box?

The key phrase is "without restarting"; even if he uses wubi (as you've suggested), he will still need to restart back and forth between Windows and Ubuntu.

As previously suggested, the only solution for switching without rebooting is virtualisation, for example with VirtualBox.

OP should also first check if any Windows apps that you require can be used in WINE.

---

### Post by billgoldberg on 2008-08-21
I wast just going to mention it.

Some of you really need to learn to read the first post good.

The OP is already using Ubuntu and he doesn't want a dual boot.

--

Virtual Box will do it fine. There are other ways to virtualize XP like qemu, but virtual box will do just fine.

---

### Post by manishtech on 2008-08-21
VirtualBox is the only way in which it can be done.

Apart fom VirtualBox there are other virtualization softwares available like qemu , zen etc etc...
I use qemu for my work..

---

### Post by thehellboy on 2008-08-21
i'm gonna try virtual box.. and tell u the results.. which is better v box or qemu or zen..

---

### Post by linux6994 on 2008-08-21
I use vmware-player as opposed to virtualbox, its just a matter of preference. Running XP virtually when needed is just fine. I have some word docs that will not open formatted correctly so I to use XP for those. That's the only reason. Once openoffice corrects that long lasting bug I will have no more need even for XP.

---

### Post by ByteJuggler on 2008-08-21
I use both VMWare and VirtualBox, either will do fine for you.  But, be aware you need lots of RAM for running a VM.

Re Virtualbox, it has a "seamless" mode where it combines your Windows XP desktop running in the VM with your Ubuntu desktop, so you appear to have Windows apps running directly on your Ubuntu desktop.  It's pretty nifty.

---

### Post by tarps87 on 2008-08-21
I've been using VirtualBox for a while now, it has had a few problems with games not running but that's as it running a game, on an os running on another os so probably due to lack of hardware. Other than that its fine. I'm just wondering if there is any thing that makes either VirtualBox or vmware better?

---

### Post by rache1111 on 2008-08-21
I would recommend vmware because their clients are available on osx and windows. So if you ever needed to move your virtual machine somewhere else, it would be much easier. vmware server is also free, you just need to get a serial from vmware's website.

Download the tar.gz file from:
[http://register.vmware.com/content/download-106.html](http://register.vmware.com/content/download-106.html)

and install according to these instructions:
[http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29](http://maketecheasier.com/installing-vmware-server-in-hardy-heron/2008/04/29)


Good luck and have fun!

---

### Post by linuxguymarshall on 2008-08-21
Use VirtualBox or if you have the cash there is a trial version of Parallels in the repos that can be upgraded to a full account

---

### Post by sherin on 2008-08-29
oops ... i missed the "restart" stuff.  i do back virtual box . it worked well for me ....

---

### Post by tjwoosta on 2008-08-29
> my suggestion is that try to istall both xp and ubuntu in diffent partions then through that you can access the files in xp while you are running ubuntu but viseversa you can't.

actually, you could access both partitions very easily from the other 

(access vista from ubunut, or acess ubuntu from vista)

the only thing you would need to do is install an ext3 or ext2 driver in vista

this is the one i use and it works great[http://www.fs-driver.org/]("http://www.fs-driver.org/")

(this would allow vista to mount the ubuntu partition just like any other partition)

---

### Post by yoman on 2008-08-29
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by mlentink on 2008-08-29
> **rache1111 said:**
> I would recommend vmware because their clients are available on osx and windows. 

So are VirtualBox's.

I can't admit to being an expert here. I use VirtualBox (the prorietary version, not the OSE version because I need USB support) regularly becuase some of my clients insist on using that-other-os's-software. With the seamless option, that's a breeze. My rating: good stuff.

---

