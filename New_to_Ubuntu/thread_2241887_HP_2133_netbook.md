---
title: "HP 2133 netbook"
date: 2014-08-29
forum: New to Ubuntu
---

### Post by Jushua on 2014-08-29
Okay, i have this HP 2133 netbook and i haven't touched this ever since it became too laggy(windows vista). I decided to change this OS to Ubuntu.. is this possible? 
Like is it possible to put it live boot on usb? 

Also it wouldn't matter if netbook came from korea right? because everything is in korean LOL

thank you in advance for helping me out !

---

### Post by ThatBum on 2014-08-29
Sure. I used [http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/desktop/create-a-usb-stick-on-windows) for my Eee PC.

Note that you may need to change the boot priorities in BIOS to get it to boot from USB.

---

### Post by Jushua on 2014-08-29
does ubuntu run well and the eee pc? also it should be compatible with other netbooks right ?

---

### Post by ThatBum on 2014-08-29
Specifically, I run Xubuntu on my Eee PC because the lil' netbook is not very powerful. I suggest you do the same, Ubuntu's Unity interface is a fairly heavyweight desktop environment compared to xfce, and your machine doesn't seem to have a lot of graphics oomph.

Xubuntu is rather responsive and more power efficient compared to Win7, which it came with.

Otherwise it should be fine if the all the hardware is supported. The 2133 sports a x86-compatible VIA processor, so the 32-bit version should at least be compatible in a basic fashion. However, the netbook may contain obscure ill-supported hardware so you should test it in live mode to be sure.

Also, back up the data you want to keep from the previous OS before doing anything, as always.

---

### Post by Jushua on 2014-08-29
I was actually thinking about running Xubuntu, but everything works the same for xubuntu and ubuntu right ? for the apps? or commands so to say.

wait so i can boot and test it live, then if i like it i can install it into the harddrive? 

sorry for all these questions, i'm like a starter for linux/ubuntu - i always wanted to install one so i thought it was right oppurtunity to.

---

### Post by ThatBum on 2014-08-29
Most everything that will run on Ubuntu will run on Xubuntu, they share a lot of packages in their repository. Though, if you want to run a GNOME program on xfce, it would need to install a load of dependencies, but it's no big deal.

And yes, you can boot from the USB stick and run the OS from a ramdisk. In addition to testing the OS, it's very useful for rescuing Windows installations, for example, so it's good to have one around. Note that any changes you make while in the live OS will be lost on shutdown unless you enable persistence in the USB boot disk installer. That is, unless you install the OS to the internal hard disk, or modify the hard disk in any other way manually.

---

### Post by dave131 on 2014-08-29
You could also take a look at lubuntu.

---

### Post by ThatBum on 2014-08-29
Ah yeah, that too. It never particularly struck my fancy, so I don't have any experience with it, but whatever humps your camel I suppose.

---

### Post by mastablasta on 2014-08-29
also it loads the OS into ram so it will be slower than installed os.

Xubuntu just has a different desktop environment (XFCE) than Ubuntu (Gnome with Unity). commands are the same in all of them. just user interfaces are different.

if you have a 10" screen you might want to also try Kubuntu and install netbook-plasma interface (designed with small netbooks in mind).

the good thing is you can give it a try and see if it works, and if you are happy with what you see and how it works you can proceed to install it. if not, then no harm done.

as Linux is modular you can take or add as you want. you can even install just minimal stuff and a windows manager: [http://www.psychocats.net/ubuntu/minimal](http://www.psychocats.net/ubuntu/minimal)

some hardware doesn't have Linux drivers (the hardware makers didn't make them or at least gave the specs to be made by others) and in those cases there are only two options - replace the hardware or run windows.

---

### Post by mr-woof on 2014-08-29
I've got Crunchbang installed on my eee netbook, runs like a dream :-)

---

### Post by stalkingwolf on 2014-08-29
I have run all the ones mentioned in addition i have tried zorin, ultimate edition, Mint 13 mate and several and several others all ran fine on my EEE and my HP minis.  UE was a bit slow. but worked fine.  Everything that i use is in synaptic on all of them.

---

### Post by uRock on 2014-08-29
I have an older EeePC. I usually try not to recommend other distros, but in this case Linux Mint has proven to be the best for my Netbook. All of the extra buttons, such as the one to turn the touch pad off and on and using the touch pad to scroll through pages, work out of the box with Linux Mint. These can be configured in ubuntu, but when it comes to the Netbook, I prefer a distro I can just install and get busy with.

[http://www.linuxmint.com/](http://www.linuxmint.com/)

Linux Mint can be installed on using a USB drive in the same manner ubuntu is installed.

---

### Post by Rob Sayer on 2014-08-29
I think it'd be good to actually have the OP say what sort of spec he/she has on this netbook.  Kinda hard to really recommend say Xubuntu or Lubuntu ...

However, I will say that I wouldn't install the Unity version of ubuntu on any netbook I've ever seen.  Mine came with Windows 7 Starter and has 1 Gb RAM.  There's just no way Unity is ever going on there.  It's too slow for me on my 4Gb i3 laptop.

No, the commands in the various ubuntu desktops don't work the same.  And no, you can't assume that because someone runs it on their netbook that you'll have the same experience installing it.

If you have 1Gb or more try Xubuntu.  If it's less than 1Gb try Lubuntu.  I've had Lubuntu installed in the past and it is pretty damn fast but I found 14.04 too buggy and it's too clunky.  But on a 512Mb machine I'd use it.  Or a lighter linux distro altogether.

Just download the live CD and do an MD5 sum on it.  Then burn it to USB and boot it.

---

### Post by MartyBuntu on 2014-08-29
Had an Acer Aspire One netbook loaded with Mint 13 (MATE desktop) for a few years...

Last month I switched it to Ubuntu Studio 14.04 (XFCE desktop).
Surprisingly, XFCE was a little better on resources than MATE. Many of the audio apps I run on Ubuntu Studio on my desktop and more powerful laptop can't be handled by my netbook's weaker Atom processor, but in all other aspects, it's a fairly usable machine.

---

### Post by ThatBum on 2014-08-29
> **Rob Sayer said:**
> I think it'd be good to actually have the OP say what sort of spec he/she has on this netbook.

[Here's the specsheet]("http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/ds_HP2133Mini-NotePC.pdf"). No solid number on memory however.

Mint's default Cinnamon environment might be too heavy for it as well, so watch out for that.

Also I just noticed that one of the OS options is SUSE. So it does have linux support after all.

---

### Post by uRock on 2014-08-29
> **ThatBum said:**
> [Here's the specsheet]("http://www.hp.com/hpinfo/newsroom/press_kits/2008/mobility/ds_HP2133Mini-NotePC.pdf")Mint's default Cinnamon environment might be too heavy for it as well, so watch out for that.

Mint works fine on mine.:) I've installed every *buntu, Windows XP Pro, 7 Pro, and now have 8.1 Pro on it at some point. Mint with Cinnamon has been much nicer looking and/or better performing than all of the others with the default configurations.

---

### Post by 3rdalbum on 2014-08-30
> **Rob Sayer said:**
> 
However, I will say that I wouldn't install the Unity version of ubuntu on any netbook I've ever seen.  Mine came with Windows 7 Starter and has 1 Gb RAM.  There's just no way Unity is ever going on there.

So did mine. Runs Unity quite happily. I don't know what's wrong with your i3 laptop, but my netbook is fairly good with it.

---

### Post by Rob Sayer on 2014-08-30
> **3rdalbum said:**
> So did mine. Runs Unity quite happily. I don't know what's wrong with your i3 laptop, but my netbook is fairly good with it.

There's nothing wrong with my laptop.  KDE runs on it very well.  Unity is the best thing that ever happened to Mint.

---

### Post by stalkingwolf on 2014-09-03
my experience with the current netbooks is they usually run to 1.6 to 1.8 gz processors and 1-2 gb ram.  my first was a 9" eee that i bought for 25.00. i got it cheap because it had the japaneese version of windows on it.  I intended to  put ubunto on it anyway. (8.04).  Dont remember the actual specs other than it had a ssd.  It did what i wanted.

---

### Post by Jushua on 2014-09-09
if i burn it to a usb drive, can i just use the usb ever again? like remove the files off the usb. it may seem like dumb question but i don't want to lose anything on my computer..

---

### Post by uRock on 2014-09-09
Yes, it can be reformatted.

---

