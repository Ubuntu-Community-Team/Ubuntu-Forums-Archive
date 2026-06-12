---
title: "How To Downgrade Ubuntu?"
date: 2008-11-15
forum: New to Ubuntu
---

### Post by nakama85 on 2008-11-15
As much as I love Ubuntu I am having problems with 8.10. Its Kinda Weird actually. I have everything working flawlessly but I have some serious speed issues. My performance bogs down like crazy even when running something as simple as gnometris. I can't figure it out. Well anyway I was wondering if there is a way to downgrade to previous version but the biggest hurtle is that I did a fresh install of 8.10

Unless someone knows how to solve the speed issue.

Thanks for any help

---

### Post by nakama85 on 2008-11-15
any takers? 
Or should I download the previous distro and do another fresh install?

---

### Post by nhasian on 2008-11-15
what are your system specs?  when things slow down, run *top* in a terminal.  are there any apps that hog up the resources?

I know that 8.10 indexes files and that could slow down your system.  you could disable that by going to System/Prefences/Search and Indexing, then untick the *Enable Indexing* option.

---

### Post by nakama85 on 2008-11-15
> **nhasian said:**
> what are your system specs?  when things slow down, run *top* in a terminal.  are there any apps that hog up the resources?

I know that 8.10 indexes files and that could slow down your system.  you could disable that by going to System/Prefences/Search and Indexing, then untick the *Enable Indexing* option.

system specs- 3g P4 (not dual core) 4G Ram, 500g sata hd, onboard video

I am actually wondering if it is my video card.... when I run top the biggest mem hog is firefox..

Indexing would only affect hd speed correct, or am i wrong?

thanks for your help

---

### Post by nakama85 on 2008-11-15
also "xorg" takes up alot of mem sometimes. what is "xorg"

---

### Post by nakama85 on 2008-11-15
i just realised that xorg kills my proccessor sometimes. as well as gimp when doing something like foreground select

---

### Post by nhasian on 2008-11-15
i'm happy to help.  you seem to have a pretty decent machine.  what kind of onboard video card do you have in your computer?  If your not sure you can type in a terminal:

```
lshw
```

Also under System/Preferences/Appearance in the *Visual Effects* tab which setting are you using?  None, Normal, or Extra?  you could lower the eye candy to make things more snappy.

---

### Post by iponeverything on 2008-11-15
> **nakama85 said:**
> also "xorg" takes up alot of mem sometimes. what is "xorg"

xorg is the X windows server. It's what gnome, kde and the other window managers run on top of. Yes indexing will bog down you system a lot. 

You can turn it off to see if it speeds things up. I have the turned off on all my systems.  Both of which are only P3's.  They both run well. 1 Ibex the other is Hardy.

---

### Post by nakama85 on 2008-11-15
> **nhasian said:**
> i'm happy to help.  you seem to have a pretty decent machine.  what kind of onboard video card do you have in your computer?  If your not sure you can type in a terminal:

```
lshw
```

Also under System/Preferences/Appearance in the *Visual Effects* tab which setting are you using?  None, Normal, or Extra?  you could lower the eye candy to make things more snappy.

this is what it shows


 *-display UNCLAIMED
             description: VGA compatible controller
             product: 82915G/GV/910GL Integrated Graphics Controller
             vendor: Intel Corporation
             physical id: 2
             bus info: pci@0000:00:02.0
             version: 04
             width: 32 bits
             clock: 33MHz
             capabilities: pm bus_master cap_list
             configuration: latency=0

---

### Post by nakama85 on 2008-11-15
> **nhasian said:**
> what are your system specs?  when things slow down, run *top* in a terminal.  are there any apps that hog up the resources?

I know that 8.10 indexes files and that could slow down your system.  you could disable that by going to System/Prefences/Search and Indexing, then untick the *Enable Indexing* option.

the box for enable indexing is not checked. However in the files tab
"index file contents" is checked
"index mounted directories" is checked
"index and watch my home directory" is checked

should I un-check these?

---

### Post by nakama85 on 2008-11-15
visual effects are set to none

---

### Post by nhasian on 2008-11-15
Intel should be ashamed of themselves.  their video adaptors have always sucked.  Yes, if you invested in a cheap Nvidia graphics adaptor you will be much happier.  I'm not sure as I dont have an intel adaptor, but are there restricted drivers you can enable for that card?  go to System/Administration/Hardware Drivers.  It should tell you if there are any drivers you need to activate for your system.

---

### Post by lovinglinux on 2008-11-15
> **nakama85 said:**
> As much as I love Ubuntu I am having problems with 8.10. Its Kinda Weird actually. I have everything working flawlessly but I have some serious speed issues. My performance bogs down like crazy even when running something as simple as gnometris. I can't figure it out. Well anyway I was wondering if there is a way to downgrade to previous version but the biggest hurtle is that I did a fresh install of 8.10

Unless you can't solve the speed issue, you can "downgrade" by doing a fresh install of 8.04.1. The fact that you did a fresh install of 8.10 is not a problem. In fact it would be a problem if you had upgraded instead of installing a fresh one.

If you have a separate partition for /home, then even better. If you don't, make a backup of /home and when you install the older version make sure you create a separate partition for it, so you can preserve most of your settings when restoring the system again.

I did a fresh install of Intrepid release candidate a few weeks ago. I didn't liked the result, so I "downgraded" to 8.04.1 again, keeping the /home partition. I don't even notice any difference from before testing Intrepid, despite a few configurations that I had to redo.

---

### Post by jesrani on 2008-11-15
> **nakama85 said:**
> As much as I love Ubuntu I am having problems with 8.10. Its Kinda Weird actually. I have everything working flawlessly but I have some serious speed issues. My performance bogs down like crazy even when running something as simple as gnometris. I can't figure it out. Well anyway I was wondering if there is a way to downgrade to previous version but the biggest hurtle is that I did a fresh install of 8.10

Unless someone knows how to solve the speed issue.

Thanks for any help

I like Ubuntu and have been using 7.10 happily. I had upgraded to 8.04 and am very happy with this. Before I upgraded to 8.10 I saved the image using PartImage program. 8.10 was giving hanging up at times and the screen froze. So I just restored the image and was back to 8.04.
Of course this wont help you at all as you have not taken any backups but you should in the future.

---

### Post by nakama85 on 2008-11-16
thanks everyone for all the help.
Sadly I do have another graphics card however even with nvidia driver installed ubuntu will not even boot with that card connected. Unfortunately I have googled this issue and many other people have it as well with this particular card and there is nothing I can do about it.

That being said. I think I will install an older version when I have the time.
thanks

---

### Post by Geistanon on 2009-05-02
This is interesting. I started with 8.10, and when I upgraded to 9.04 I had exactly the same issues (graphics performance = terrible). I looked through this thread, tried the suggestions, and it seems that downgrading is my best bet to resolve it?

---

### Post by MontelEdwards on 2009-05-02
If you edit your sources.list and replace jaunty with intrepid, it should work i think.

---

### Post by lovinglinux on 2009-05-02
> **monteledwards said:**
> If you edit your sources.list and replace jaunty with intrepid, it should work i think.

Mixing sources is not a good idea. It might broke a lot of things.

---

### Post by ranjank on 2010-07-31
How to downgrade from Ubuntu 10.10 Alpha 2 to Ubuntu 10.04 . Sorry for replying to old thread , when googled got this thread .

---

### Post by Paul820 on 2010-07-31
You shouldn't have upraded your 10.04 to 10.10 Alpha if you are using 10.04 as your day to day computer as alpha will be buggy. It would have been better to run it in a VM or on another partition.

---

### Post by MontelEdwards on 2010-07-31
Listen, I am going to state a fact here.
**YOU CANNOT DOWNGRADE UBUNTU**
**YOU CANNOT DOWNGRADE UBUNTU**
**YOU CANNOT DOWNGRADE UBUNTU**
not matter if youre going from stable to alpha, or whatever.

If you try and downgrade a package in Synaptic then its going to try and remove a ton of packages.
Now of course I could go on telling you how to do it manually with dpkg --forces but that still leaves the fact that what if in a upgrade configuration files change? syntax changes etc.

There're just too many things wrong that could happen forcing a downgrade. At the end of the day, it is so much easier just to do a clean reinstall.

And listen, I know its its fun for new Ubuntu people to try the 'latest' bleeding edge version but its really not worth it. If you want to try it, run it in  a VM.

I always advise users to NEVER use the Alphas unless they're highly experienced with Linux in whole. Not just Ubuntu.

Just wait for the late betas, and Release Canidates.

Oh, and never mix sources too. 

This is what the Debian guys call SNS syndrome. 
Shiny new Shite (: the need to have the newest, even if its the worst.

Good luck,
 - Montel

---

### Post by ranjank on 2010-07-31
I will do a clean install , I have APT Backup [CD]

---

### Post by Stancel on 2010-08-01
The only way I know of to downgrade is if you have the iso of the previous version, burn it to a CD and install.

---

### Post by Elfy on 2010-08-01
Closed - necro thread.

---

