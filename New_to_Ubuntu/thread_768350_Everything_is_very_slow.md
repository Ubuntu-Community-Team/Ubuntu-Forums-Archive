---
title: "Everything is very slow"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by NOLU on 2008-04-26
After upgrading to Heron, I'm finding every aspect of Ubuntu extremely slow. I have turned off the effects but it is still very very annoying and I'm certainly not enjoying this as I was with the previous one.

The only thing I have done is install a module to get the virtualbox going but I have uninstalled that and restarted but it's still very slow.

Is there some way I can find out what is causing this please?

Thanks.

---

### Post by Michael.Godawski on 2008-04-26
With everything do you mean the internet browsing, the opening of applications, the booting process?

Frankly speaking Hardy does not work for me at all. My terminal, synaptic and the network applet are not working, so hardy is not usable for me at that moment. I hope for a fix. But the weird thing is I get no error or crash report. I stick with Gutsy.

It is not that easy to tell you what might be causing the slowness.

---

### Post by daranz on 2008-04-26
I'd suggest checking top (from terminal) or the System Monitor (System > Administration) to see what's using the most CPU/resources. Also, check /var/log/syslog for any repeating errors.

---

### Post by NOLU on 2008-04-26
Scrolling in the internet is awfully slow. Pages opening up slow. Just found I have no sound on youtube and when playing, it judders.

As I said, yesterday with 7.10 all was well but now even with the effects off, it's just a slow all around. Even when opening up something from AWN, it takes 30 seconds to maximise from it.

---

### Post by NOLU on 2008-04-26
> **daranz said:**
> I'd suggest checking top (from terminal) or the System Monitor (System > Administration) to see what's using the most CPU/resources. Also, check /var/log/syslog for any repeating errors.

Biggest thing running is Firefox. Other than that, there isn't much running. Even scrolling down the list was slow.

---

### Post by NOLU on 2008-04-26
Would it be something like graphics card drivers that could be causing this?

---

### Post by Sponzenbroekske on 2008-04-29
I got the same problem, sometimes it runs ok, other times its just annoying slow and even freezes, then i gotta pull the plug :s ctrl+alt+backspace or F1 doesnt even work during the freezes :s
I read a lot about slow heron but no solution, would it be a bug??

---

### Post by lwvmobile on 2008-04-29
What version are you upgrading from and what are you hardware specs. I know that past 6.10 and 7.04 Ubuntu needs a bit more juice so to speak.

---

### Post by martrn on 2008-04-29
> **Sponzenbroekske said:**
> I got the same problem, sometimes it runs ok, other times its just annoying slow and even freezes, then i gotta pull the plug :s ctrl+alt+backspace or F1 doesnt even work during the freezes :s
[..], would it be a bug??

What kernel are you using ?
```
uname -r 
```
To find out.
What processesor are you using ?

Do you have the system running ok without anything like wireless network cards ?

How can yours be exactly the same problem if the op has installed a modul to get the virtual box woking ?

---

### Post by tewald on 2008-04-29
I too installed Hardy ( not upgraded my 7.10 installation ) to find out that gnome ( or GTK ? ) is terribly slow.
With 7.10 I have a snappy desktop, but now I can actually see Evolution redraw itself when I restore/resize it's window ( I know... Evolution is not that fast... but now it's very annoying ).
My hardware specs:

Athlon XP 2400
1.5 GB RAM
MB Asus A7V8X-X
VGA Nvidia GeForce 6200 ( 64 bits )

I installed NVIDIA's driver using synaptics and downloading the drivers from the site.

I even compiled a new kernel with no success.

glxgears did not change the values, so I have a few possible origins for the problem:
- Xorg 7.3 ( this is a pure guess )
- GTK ( even with "simple" engine I see all windows redrawing )
- some obscure kernel/xorg/nvidia driver option?

Is there anyone else with the same issues? Any suggestions?

Thanks!

Thomas

---

### Post by martrn on 2008-04-29
> **tewald said:**
> I too installed Hardy ( not upgraded my 7.10 installation ) to find out that gnome ( or GTK ? ) is terribly slow.
With 7.10 I have a snappy desktop, but now I can actually see Evolution redraw itself when I restore/resize it's window ( I know... Evolution is not that fast... but now it's very annoying ).
My hardware specs:

Athlon XP 2400
1.5 GB RAM
MB Asus A7V8X-X
VGA Nvidia GeForce 6200 ( 64 bits )

I installed NVIDIA's driver using synaptics and downloading the drivers from the site.

I even compiled a new kernel with no success.

glxgears did not change the values, so I have a few possible origins for the problem:
- Xorg 7.3 ( this is a pure guess )
- GTK ( even with "simple" engine I see all windows redrawing )
- some obscure kernel/xorg/nvidia driver option?

Is there anyone else with the same issues? Any suggestions?

Thanks!

Thomas

These are separate issues / you should be really posting a new topic.....

1. NOLU is building or using some kind of virutisation box / know to slow machines down extramly / using virtulisation software / resource hungry / etc.

2.  Sponzenbroekske is describing a freezing locking routine, not complaining about general slowness.

3. you compiling a new kernel with no success.

I have my own kernel successfully compiled and a computer with simular specs to yours and it flys (using my own custom kernel)....  So I would guess that it is either/and some obscure kernel option, and/or the fact you are using the NVIDIA's driver using synaptics.

You need to rid all references for the NVIDIA driver from synaptics or repositories and download it from nvidia, and follow the [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") not recommended option,

---

### Post by NOLU on 2008-04-30
Everything was fine with 7.10. It's just since the upgrade and I have virtualbox installed but it's not running. Nothing much is running when I check other than Firefox.

I did get an answer elsewhere that it could be an ATI driver problem but no one was able to help in finding out what driver I would need. Seems to be an issue with ATI drivers.

I'll get specs later (not at home)

---

### Post by Jaxilian on 2008-04-30
I agree that Ubuntu 8.04 is slower than 7.10. Especially in the startup. The bar freezes for a short bit and then continues. About 15-20 sec slower

Other than that everything works for me. It would be interested to know what changes were made in the startup between the two versions.

---

### Post by Prefix100 on 2008-04-30
Yeah, same, everthing lags for me. I mean everything. 

But ONLY when using wireless.

Videos, Music, File Browsing, Web Browsing, Switching Desktops - you name it.

Also during lag I looked for top, there wasnt anything out of oridinary, cpu usage and mem usage were fine.

Unplug my wireless adapter, and everything works like a charm.

---

### Post by tewald on 2008-04-30
> **martrn said:**
> These are separate issues / you should be really posting a new topic.....

1. NOLU is building or using some kind of virutisation box / know to slow machines down extramly / using virtulisation software / resource hungry / etc.

2.  Sponzenbroekske is describing a freezing locking routine, not complaining about general slowness.

3. you compiling a new kernel with no success.

I have my own kernel successfully compiled and a computer with simular specs to yours and it flys (using my own custom kernel)....  So I would guess that it is either/and some obscure kernel option, and/or the fact you are using the NVIDIA's driver using synaptics.

You need to rid all references for the NVIDIA driver from synaptics or repositories and download it from nvidia, and follow the [https://help.ubuntu.com/community/NvidiaManual]("https://help.ubuntu.com/community/NvidiaManual") not recommended option,

NOLU only informed that he has installed a module to use virtualbox ( not IN virtualbox.. or so I understand ). Anyway... I just posted here because of the complain of general slowness of the graphics system ( which is also my problem )
And I have installed NVIDIA's driver removing all nvidia related packages from my system. Something that helped a little was disabling via-agp and use nvidia agp driver.
I will make some experiences with my kernel to see if there's any improvement.

Thanks for the reply!

---

