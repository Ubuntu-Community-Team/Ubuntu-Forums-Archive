---
title: "Need help installing....ubuntu 6.10"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by ed.linux on 2008-06-11
Ok...this is what happens...

I have an IBM 380ED ThinkPad....when I boot ubuntu 6.10 if I only press enter to select 'Start or Install Ubuntu' it loads, then a message appears saying: 'ACPI: Unable to locate RSDP' then it shows a BusyBox command line. And I didn't knew how to proceed. When googling, I found that pressing F6 before selecting 'Start or Install Ubuntu'would allow me to modify the boot options, and that I should type in NOAPCI APCI=OFF, that solved the problems for the message 'ACPI: Unable to locate RSDP', however I am unable to install ubuntu yet.

It occured to me to type in the BusyBox, which has always this word '<initramfs>', so after that I type /bin/sh init and then it starst loading something but after loading, it says that it cannot mount some files, right now I do not recall which, but it seems to have something to do with installation files.

Can somebody help me??   ooo by the way, the Laptop has no OS at all....no operative system.

Please help!!! :confused:

---

### Post by benfindlay on 2008-06-11
The first and easiest thing I'd suggest is to get a newer version of ubuntu. 6.10 is no longer supported. The current version (8.04) is supported until 2011 so should be much more stable and user freindly for you to get to work.

---

### Post by overdrank on 2008-06-11
> **ed.linux said:**
> Ok...this is what happens...

I have an IBM 380ED ThinkPad....when I boot ubuntu 6.10 if I only press enter to select 'Start or Install Ubuntu' it loads, then a message appears saying: 'ACPI: Unable to locate RSDP' then it shows a BusyBox command line. And I didn't knew how to proceed. When googling, I found that pressing F6 before selecting 'Start or Install Ubuntu'would allow me to modify the boot options, and that I should type in NOAPCI APCI=OFF, that solved the problems for the message 'ACPI: Unable to locate RSDP', however I am unable to install ubuntu yet.

It occured to me to type in the BusyBox, which has always this word '<initramfs>', so after that I type /bin/sh init and then it starst loading something but after loading, it says that it cannot mount some files, right now I do not recall which, but it seems to have something to do with installation files.

Can somebody help me??   ooo by the way, the Laptop has no OS at all....no operative system.

Please help!!! :confused:

Hi and what are the specs on the system, the specs on the web are cpu 166mhz and 16mb memory? You may look at DSL or puppy linux

---

### Post by gameryoshi600 on 2008-06-11
> **benfindlay said:**
> The first and easiest thing I'd suggest is to get a newer version of ubuntu. 6.10 is no longer supported. The current version (8.04) is supported until 2011 so should be much more stable and user freindly for you to get to work.
I agree. first get a newer version. 7.10 or 8.04 will do good. then come if you have problems. its better cause more people have the ones that are still supported

---

### Post by wolfen69 on 2008-06-11
> **overdrank said:**
> Hi and what are the specs on the system, the specs on the web are cpu 166mhz and 16mb memory? You may look at DSL or puppy linux

if it does indeed have those specs, you will not be able to install anything except maybe an old distro on floppies. getting more ram will allow you to install puppy or dsl.

---

### Post by ed.linux on 2008-06-11
I already am downloading version 8.04 somebody told me to do so...I will try it when I get home...specs if I recall correctly it has 512mb for ram...don't know either the MHZ or the HD size, but it used to run windows 2000, should be able to run linux as well isn't it??

Thanks to all of you.

---

### Post by wolfen69 on 2008-06-11
you may want to consider running Xubuntu. it will be a little bit faster.

---

### Post by Linux_Man on 2008-06-11
If it used to run Windows 2000 then as wolfen69 said, use Xubuntu if you want to stay in the Ubuntu family. Myself I would recommend using Puppy or DSL instead as something built for Windows 2000 will be slow running even Xubuntu probably.

---

### Post by ed.linux on 2008-06-11
what exactly is puppy or dsl??? and could you explain me the difference or guide me on what is the difference between ubuntu and xubuntu??

---

### Post by overdrank on 2008-06-11
> **ed.linux said:**
> what exactly is puppy or dsl??? and could you explain me the difference or guide me on what is the difference between ubuntu and xubuntu??

Hi and puppy and DSL (damn small linux) are different distro's. Xubuntu is for low memory system and uses the window manager XFCE. Ubuntu uses gnome as the desktop environment. [http://distrowatch.com/](http://distrowatch.com/)

---

### Post by powerpleb on 2008-06-11
> **overdrank said:**
> Hi and puppy and DSL (damn small linux) are different distro's. Xubuntu is for low memory system and uses the window manager XFCE. Ubuntu uses gnome as the desktop environment. [http://distrowatch.com/](http://distrowatch.com/)

If it used to run Win2K (and especially if you have 512mb ram) you can probably do better than Puppy or DSL, they are a bit... erm... stark.

Xubuntu kicks ***, so does Zenwalk and so does MEPIS AntiX if you want something lighter but not too light if you know what I mean.

---

### Post by bumanie on 2008-06-11
Puppy and dsl (damn small linux) are minimalist linux distributions. I think dsl is 50-60 mb and puppy is around 100 mb. Never used dsl, but have used puppy from a live cd. It is very fast as it loads into ram and operates out of ram, it can of course, also be installed to a hard drive as per normal. Although small, it has html editor word processor, burning and ripping programs etc. and has a repository for adding extra programs. The latest version, I believe is compatible with slackware, so if there is anything you can't find in the puppy repository, you should be able to find it in the slackware repository.

---

### Post by ed.linux on 2008-06-11
Thank you guys...I will try all your suggestions...

wish me luck!

---

### Post by ed.linux on 2008-06-11
> **powerpleb said:**
> 

Xubuntu kicks ***, so does Zenwalk and so does MEPIS AntiX if you want something lighter but not too light if you know what I mean.

I didn't quite understood what you meant there...XDDD

---

### Post by powerpleb on 2008-06-11
> **bumanie said:**
> Puppy and dsl (damn small linux) are minimalist linux distributions. I think dsl is 50-60 mb and puppy is around 100 mb. Never used dsl, but have used puppy from a live cd. It is very fast as it loads into ram and operates out of ram, it can of course, also be installed to a hard drive as per normal. Although small, it has html editor word processor, burning and ripping programs etc. and has a repository for adding extra programs. The latest version, I believe is compatible with slackware, so if there is anything you can't find in the puppy repository, you should be able to find it in the slackware repository.

I've used them both quite a lot as I have an old laptop with 128mb RAM. DSL is good and fast but it drives me crazy after a while because it comes with a dodgy version of Firefox. Puppy doesn't have many packages available and it uses SeaMonkey which I don't really like.

I ended up settling for MEPIS AntiX because it had some of the speed and minimalism of Puppy and DSL with the practicality of Debian packages. It also got my wireless working with minimal effort which is unusual.

---

### Post by ed.linux on 2008-06-11
So MEPIS AntiX is another distribution??? or what is it?

---

### Post by powerpleb on 2008-06-12
> **ed.linux said:**
> So MEPIS AntiX is another distribution??? or what is it?

Yes, it uses IceWM and Fluxbox which are the two best lightweight window managers in my opinion. It is based on Debian, which means it has lots of software available and it's fairly easy to configure/use.

[http://antix.mepis.org/index.php/Main_Page](http://antix.mepis.org/index.php/Main_Page)

---

### Post by Sef on 2008-06-12
> specs if I recall correctly it has 512mb for ram.

With 512 ram, Ubuntu should run ok.  It won't be super fast, but not super slow either.  My last computer had 512 ram with 1.3 GHz, and Ubuntu ran nicely in it.

---

### Post by ed.linux on 2008-06-12
Something weird happened...

After being booting ubuntu several times...I cannot boot it anymore.....

I am using a Floppy loaded with a cd loader image....it used to work fine..but now I cannot even boot ubuntu...not the 6.01 nor the 8.04....

:confused:

---

