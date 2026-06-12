---
title: "Optimizing Ubuntu"
date: 2008-08-01
forum: New to Ubuntu
---

### Post by diego898 on 2008-08-01
I am new to ubuntu, and wanted to know what ways are there to optimize it? I heard recompiling the source on your own machine can speed things up. But that thats a big step in optimization. Are there any tweak tweak guides to optimizing ubuntu? Defragging (I dont think ext3 defragments right) ? disabling uncessary services? (I dont really know what services do what)?

---

### Post by Ingenue on 2008-08-01
I am green to Ubuntu too and I have been wondering about this myself. I'm unsure about how to defrag. Thanks for reading my mind. 

I can feel the answers rolling in now....

---

### Post by mordak13 on 2008-08-01
Check out [http://ubuntu-tweak.com/]("http://ubuntu-tweak.com/") maybe it can do what you want. Kind of a cool program.

---

### Post by Paqman on 2008-08-01
> **Ingenue said:**
> I'm unsure about how to defrag.

Linux filesystems like ext3 don't pick up enough fragmentation to make defragging worthwhile. If you're mounting and using NTFS or FAT32 partitions you might want to defrag them from within Windows from time to time (chances are you'll be doing this anyway if you're dual-booting)

As for optimising Ubuntu, depends what you want to optimise. A good place to start is the apps started at login. Go to System > Prefs > Session and see what is on the list that you don't need.

You can also [free up a lot of disk space](http://ubuntuforums.org/showthread.php?t=140920) on the default install.

I'd recommend against starting to recompile software or the kernel. If that's where you want to go, Ubuntu is probably not the right distro for you. Ubuntu is focused on usability, not optimisation.

---

### Post by hrod beraht on 2008-08-01
> **Ingenue said:**
> I'm unsure about how to defrag.
You don't have to. The ext3 filesystem that linux uses essentially tries not to write files in a fragmented way to begin with, so defragging isn't necessary. See [[COLOR="Blue"]this article[/COLOR]]("http://geekblog.oneandoneis2.org/index.php/2006/08/17/why_doesn_t_linux_need_defragmenting") for a nifty explanation of fragmentation and why it isn't a major problem with linux.

Bob

---

### Post by diego898 on 2008-08-01
> **Paqman said:**
> Linux filesystems like ext3 don't pick up enough fragmentation to make defragging worthwhile. If you're mounting and using NTFS or FAT32 partitions you might want to defrag them from within Windows from time to time (chances are you'll be doing this anyway if you're dual-booting)

As for optimising Ubuntu, depends what you want to optimise. A good place to start is the apps started at login. Go to System > Prefs > Session and see what is on the list that you don't need.

You can also [free up a lot of disk space](http://ubuntuforums.org/showthread.php?t=140920) on the default install.

I'd recommend against starting to recompile software or the kernel. If that's where you want to go, Ubuntu is probably not the right distro for you. Ubuntu is focused on usability, not optimisation.

Well I read somewhere that it was possible to recompile the ubuntu kernel to make it faster. Since Im new to linux, I was just wondering how and why this would be done

---

### Post by gjoellee on 2008-08-01
I have been searching around finding tweaks etc, and I have added them to my home page [www.polishubuntu.co.nr]("http://www.polishubuntu.co.nr")

here is the direct link: [http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2)

this does truly really help for 95% of the people who have done the tweaks...

---

### Post by diego898 on 2008-08-01
Does anyone know about why in Ubuntu Tweak under System the submenu CPU has an option where how much percent it is used when pluged in, and its at 85% only, not 100%. Does anyone know why?

---

### Post by oldos2er on 2008-08-01
> **gjoellee said:**
> I have been searching around finding tweaks etc, and I have added them to my home page [www.polishubuntu.co.nr]("http://www.polishubuntu.co.nr")

here is the direct link: [http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2](http://www.polishubuntu.piczo.com/optimizeubuntu8.04forspeed/?cr=2)

  

 Just be careful, and backup every file before you alter it. Also, every instance where this person says to use "sudo gedit..." should be substituted with "gksudo gedit...."

 Also, the program sysv-rc-conf is superior to the GUI 'Sessions Preferences' program, because it shows you every service, not just a few. Not recommended if you don't know what you're doing.

---

### Post by the8thstar on 2008-08-01
Everyone is free to do whatever they wish. I tried a few optimizations myself but it actually made things sluggish... The end results depend largely on your hardware, so BE VERY CAREFUL.

---

### Post by UbuntuNerd on 2008-08-01
this is the best way I have found to keep Ubuntu running smooth!!!

[http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html]("http://www.ubuntugeek.com/cleaning-up-all-unnecessary-junk-files-in-ubuntu.html")

---

### Post by UbuntuNerd on 2008-08-01
and if you come across a command that looks like this (sudo apt-get autoclean) while find out how to optimize Ubuntu don't use it b/c it could remove some applications you need.

---

### Post by SarahKH on 2008-08-01
Don't worry about defragging stuff.  Yes, ext3 can become fragmented.  However, unless you are seriously hammering the drive (terrabytes of changes a day) I wouldn't worry about it.  Seriously.  I wouldn't even worry about it in Windows these days (well ok, once a year), drives are a lot faster these days than they were in the past so it's all marginal. 

Go...erm... System > Preferences > Sessions 

This is basically what fires up for you, as opposed to system wide. Untick the various things you don't need; so if you're not blind you really don't need the screen reader 7 magnifier stuff firing up and hanging around.  Tracker is, IMHO a waste of space and can die.  But if you like indexed searches keep it around.  They've all got handy descriptions to figure out if you want it or not.

See if that's enough improvement for you, it might be, it might not be.  If not install something like bum or rcconf and start stopping system services.  Google is your friend as to WTF that odd named thing does and if it's kinda needed (ProTIP:  Don't kill network-manager.  You need it. Really you do). 

You might also find replacing network-manager with something like wcid also improves things; wcid will attempt to connect to the wired or preferred wireless network at boot time rather than waiting for you to login to do it.

---

### Post by diego898 on 2008-08-02
> **UbuntuNerd said:**
> and if you come across a command that looks like this (sudo apt-get autoclean) while find out how to optimize Ubuntu don't use it b/c it could remove some applications you need.


I used this command already!! Does that mean I'm in trouble?!

---

### Post by Martje_001 on 2008-08-02
> **diego898 said:**
> Well I read somewhere that it was possible to recompile the ubuntu kernel to make it faster. Since Im new to linux, I was just wondering how and why this would be done
Since you're new, you don't wan't to do that. Still you can try of course:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

---

### Post by Martje_001 on 2008-08-02
> **diego898 said:**
> I used this command already!! Does that mean I'm in trouble?!
No. It only removes packages don't needed by the system. Also try these:
```
sudo apt-get clean
sudo apt-get autoremove
```

---

### Post by cariboo on 2008-08-02
If you are a demon for punishment, or really bored check out [Linux from Scratch]("http://www.linuxfromscratch.org/"). By using this method of installing Linux you waill have a distribution optimized for your system.

Jim

---

### Post by ibuclaw on 2008-08-02
> **Martje_001 said:**
> Since you're new, you don't wan't to do that. Still you can try of course:
[http://www.howtoforge.com/kernel_compilation_ubuntu](http://www.howtoforge.com/kernel_compilation_ubuntu)

I seriously advice that no one should try the above link, as it breaks quite a few CoC rules for our forums :)
It is also rather outdated...

And besides, we have our very own [Master Kernel Thread]("http://ubuntuforums.org/showthread.php?t=311158") for all you ever need to know about compiling kernels in Ubuntu...

Regards
Iain

---

### Post by Martje_001 on 2008-08-02
> **tinivole said:**
> I seriously advice that no one should try the above link, as it breaks quite a few CoC rules for our forums :)
I'm sorry?

---

