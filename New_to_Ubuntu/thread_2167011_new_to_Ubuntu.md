---
title: "new to Ubuntu"
date: 2013-08-12
forum: New to Ubuntu
---

### Post by brian7 on 2013-08-12
I just installed ubuntu and i have some questions for any body out there, oh by the way, i am dual booting with windows 7 on my laptop, first just out of my insestant need to know (also my need to know in windows), where can i find the version number or name of the OS i am using. second, i am having troubles getting some of the software from windows to work in ubuntu and i spent over 8 hours trying so i finally gave up and came here so any help in that department would be gratefully appreciated.


thanks brian7

---

### Post by nathan-b on 2013-08-12
Hi there!

In Windows, go to Control Panel -> System Settings -> System (I believe) and it will tell you all about your OS. In Ubuntu, try searching for "system monitor" in the dash and open that, I think it will have some OS info.

As for running windows programs in Ubuntu, they will not work at all by default, which it seems like you've noticed. The two main ways to get Windows programs to work in Linux are running them with a program called Wine, or actually running the Windows operating system in a program called virtualbox. Wine will run a lot of programs really well, for example I use it to run a windows music player called foobar2000. There is good information about wine at [https://help.ubuntu.com/community/Wine](https://help.ubuntu.com/community/Wine) 

For virtualbox to be pleasant you need a reasonably powerful computer, not bleeding-edge by any means but not ancient either. Could you post the type of computer you're running Ubuntu on? Virtualbox information is here:
[https://help.ubuntu.com/community/VirtualBox](https://help.ubuntu.com/community/VirtualBox)

Keep in mind that there is very nice software designed for Linux which can be an alternative for just about any Windows program, google might help find some alternatives if you can't get a windows program to work in wine or Virtualbox.

---

### Post by carl4926 on 2013-08-12
MyComputer > Right click > Properties

Windows software is for windows
But as already mentioned > Wine can be used
Related to this is something called 'Crossover'

But FYI: In most cases there is software in Linux that does exactly the same job as a similar windows based program.

Eg: MS Office > Libre Office

---

### Post by coldraven on 2013-08-12
Another method is to open the dash by pressing Winkey+A, then type "details".
Details will show your system information.

The Winkey is called "Super" in Ubuntu, if you hold it down you will see most of the desktop shortcuts.

---

### Post by grahammechanical on 2013-08-12
Or you can run some commands. In the Dash you will find the Terminal. Load it up and type

```
 uname -a
```

This is what I see

> Linux sdb8-saucy-btrfs 3.11.0-1-generic #4-Ubuntu SMP Fri Aug 9 02:29:21 UTC 2013 x86_64 x86_64 x86_64 GNU/Linux

There is the name that I have given to this installation, which reminds me where on the hard disk this is and what version of Ubuntu I am running and that it is on the btrfs file system. All that is personal choice. I also see that I am running the Linux kernel 3.11.0-1 which was installed on Aug 9 and is the 64 bit version. 

```
 lsb_release -a
```

> No LSB modules are available.
Distributor ID:    Ubuntu
Description:    Ubuntu Saucy Salamander (development branch)
Release:    13.10
Codename:    saucy

That about says it all. Except this regarding the Details page and Graphics. In Ubuntu 12.04 it is normal for Graphics to be "unknown" and Experience to be "Standard." In later versions of Ubuntu if the graphic adapter is named then you are running a proprietary video driver. If it says something like "Gallium" then it is the Nouveau open source driver. Experience still says "Standard."

Regards.

---

### Post by Mark Phelps on 2013-08-12
> i am having troubles getting some of the software from windows to work in ubuntu and i spent over 8 hours trying so i finally gave up and came here so any help in that department would be gratefully appreciated.

While Wine does work with some things, it's not a Window emulator, so the experience varies enormously with each and every application or game you try to use.  The WineHQ website has an application compatibility search tool you should use.  Enter the app name and version and look at the ratings.  Anything not listed, or rated less than Gold is going to be a waste of time trying to get it to work in Wine.

If running MS Windows apps is going to be a major part of your coming over to Linux, then you must steel yourself for a very disappointing experience in the long run, because even if a current Windows app works well, that's no indication that future versions will still work.

---

### Post by brian7 on 2013-08-12
well, thank everybody, but what i really want if the linux = to One Note, if i can find that then i will be very happy in linux ubuntu:o

---

### Post by ant2 on 2013-08-12
If you use Firefox you may consider [Quick Fox Notes]("https://addons.mozilla.org/en-US/firefox/addon/quickfox-notes/")

---

