---
title: "Persistent Usage of LiveCd"
date: 2008-05-08
forum: New to Ubuntu
---

### Post by tcoffeep on 2008-05-08
Greetings!

Now, to get to the meat of my post here...

With the latest update, I don't have a Linux PC of my own any longer, as I had problems with the beta of Gutsy and took it out physically on my laptop (eh...heh), so I am now using my gf's parent's computer constantly with 8.04, and am wondering about something...
Everytime I load up the LiveCD, I have to reinstall everything I installed, and it's quite tiring, seeing as someone else is usually downloading heavily while playing WoW or something similar.
Is there some way to have what I download, (ie - updates, programs, and the like), to stay on the comp (runs Windows Vista) without actually installing the OS on the comp (seeing as my gf's father would tear me a new one...)?
What I mean is that I play multiple MUDs, but I mainly use the java clients many supply off of their homepages and whatnot, and usually spend quite a while downloading java (which can take up to 20 minutes). Essentially, I'm looking to see if there's a way I can d/l it, and use it while using the livecd even if I have to turn off the comp.
If not, is there any possible way to work-around this?

Hoping this hasn't been asked already. I tried looking around in both forums and google, but couldn't find anything, outside of google pointing to a multitude of USB installs, which is essentially useless to me.

Please help! I am in dire need of assistance!

---

### Post by tcoffeep on 2008-05-08
I'm inclined to bump this thread, seeing as noone has responded. I will bump it once ever 30 minutes, as to not be completely annoying. It's just that this is very important to me, seeing as I'm fed up with the way Vista runs, and having to approve of everything that -I- ask it to do.
This isn't specifically for Java, either, seeing as I am in the process of learning to use the C++/Ruby/Python programming languages, and I've -never- liked the MS-DOS prompt.
Once I got settled into Linux, I've been unable to get out of this hole -sparkle-.

---

### Post by sy88 on 2008-05-08
LiveCD's weren't meant to be used that way.  If you want to install programs and such permanently, it would require an installation of the OS on something permanent (ie. HDD).

Why not try the USB idea though?  It's a portable installation of Linux so you could install whatever you want on it and it'll stay as long as you boot to USB.

---

### Post by tcoffeep on 2008-05-08
Because I'm currently at a lack for work, and have to get my Ubuntu fix through LiveCD. (lack of work = lack of cash = usb costs money)

---

### Post by Squizz on 2008-05-08
Why not install VMWare and then Ubuntu as a virtual machine?

Failing that, download the things you need and save the install file onto a usb or something.  You'll still need to reinstall them every time you run the live CD, but at least you won't have to download them.

---

### Post by tcoffeep on 2008-05-08
> **Squizz said:**
> Why not install VMWare and then Ubuntu as a virtual machine?

Failing that, download the things you need and save the install file onto a usb or something.  You'll still need to reinstall them every time you run the live CD, but at least you won't have to download them.

I wouldn't know the first thing about VMWare. From what I've read, it's rather slow. Know anywhere I could learn more about it?
The site I use to download (( filehippo.com )) has two versions of VMWare, and with my ignorance on the subject, I have no idea what I'm looking for.

[edit] :: currently download VMWare Player. Let's hope it works (^_^)

---

### Post by Archmage on 2008-05-08
Why aren't you saving your important data on a usb-stick or something like this?

---

### Post by Squizz on 2008-05-08
I run XP on my Ubuntu machine in VMWare, but I've never done it the other way around.  I'm fairly certain it should be quite easy for you to set up though.

Be careful when you're setting the amount of RAM that your virtual machine will use though - I usually give it half of what's available.

[http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware](http://www.tanguay.info/web/tutorial.php?idCode=installUbuntuOnVmware)

That tutorial has lots of screenshots etc if you're not feeling too confident about it :)

Good luck!

---

### Post by shifty_powers on 2008-05-08
seriously the easiest solution is good old [wubi](http://wubi-installer.org/).

> 

Wubi is an officially supported Ubuntu installer for Windows users that can bring you to the Linux world with a single click. Wubi allows you to install and uninstall Ubuntu as any other Windows application, in a simple and safe way. Are you curious about Linux and Ubuntu? Trying them out has never been easier!
Download Now 


Wubi is Simple

No need to burn a CD. Just run the installer, enter a password for the new account, and click "Install", go grab a coffee, and when you are back, Ubuntu will be ready for you.

Wubi is Safe

You keep Windows as it is, Wubi only adds an extra option to boot into Ubuntu. Wubi does not require you to modify the partitions of your PC, or to use a different bootloader, and does not install special drivers. It works just like any other application. Wubi is spyware and malware free, and being open source, anyone can verify that.

Wubi is Discrete

Wubi keeps most of the files in one folder, and if you do not like it, you can simply uninstall it as any other application.

Wubi is Free

Wubi and Ubuntu cost absolutely nothing (free as in beer), but yet provide a state of the art, fully functional, operating system that does not require any activation and does not impose any restriction on its use (free as in freedom).


(taken from the wubi front page).

Best of both world in my opinion ;) dual boot without partitioning :D

---

### Post by Paqman on 2008-05-08
> **sy88 said:**
> LiveCD's weren't meant to be used that way.  If you want to install programs and such permanently, it would require an installation of the OS on something permanent (ie. HDD).


Not so, you can [create a persistent LiveCD install](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence). You can use a USB stick or a hard drive as the storage device.

If you've ever used Knoppix it has a tool which automates this process. Since Ubuntu is designed as a desktop system you have to set it up yourself, but the prinicple is the same.

---

### Post by shifty_powers on 2008-05-08
> **Paqman said:**
> Not so, you can [create a persistent LiveCD install](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence). You can use a USB stick or a hard drive as the storage device.

If you've ever used Knoppix it has a tool which automates this process. Since Ubuntu is designed as a desktop system you have to set it up yourself, but the prinicple is the same.

well yes, but why bother in his case? he should be fine to just use wubi, which would be quicker and easier than having to faff around waiting for a livecd to get going all the time....

---

### Post by sy88 on 2008-05-08
> **Paqman said:**
> Not so, you can [create a persistent LiveCD install](https://help.ubuntu.com/community/LiveCD/Persistence?action=show&redirect=LiveCDPersistence). You can use a USB stick or a hard drive as the storage device.

If you've ever used Knoppix it has a tool which automates this process. Since Ubuntu is designed as a desktop system you have to set it up yourself, but the prinicple is the same.

Heh, I misinterpreted his intentions.  I thought he didn't want to write ANYTHING to hdd and that usb was not an option.  Sorry for the misleading comments.

---

### Post by tcoffeep on 2008-05-08
Okay, so, I'm now contemplating this new Wubi.

I've checked the homepage, and what I get is this :::

- It creates a partition-free version of Ubuntu

But I wonder this :::

- Doesn't fsck (-wink-) up Vista at all, so that I can't be held liable by the owner of this comp if something goes ka-boom?

Am I missing anything?

---

### Post by kwacka on 2008-05-08
is there any particular reason to use an Ubuntu Live-cd?

There are several other distributions that would do the job that ARE suited to running from cd.

Try something like Puppy Linux, you can boot & run from cd or USB stick, runs entirely from memory (so faster than Live CD), there are packages that you can add, can save settings, etc to cd-rw/usb.

---

### Post by kansasnoob on 2008-05-08
Paqman had an idea that I think has merit, remember ............ this is someone else's computer! I know how loud I'd scream if someone installed anything on my machine!!!!!!!!!!! It's my machine!!!!!!!!!!! Use it all you want, but don't install anything!!!!!!!!!!!

If you still have the hard drive from the puter you killed you can pick up external HD cases for about $10.00, add a USB cable, wipe the drive, and then install whatever you want on that drive.

---

### Post by shifty_powers on 2008-05-08
> **tcoffeep said:**
> Okay, so, I'm now contemplating this new Wubi.

I've checked the homepage, and what I get is this :::

- It creates a partition-free version of Ubuntu

But I wonder this :::

- Doesn't fsck (-wink-) up Vista at all, so that I can't be held liable by the owner of this comp if something goes ka-boom?

Am I missing anything?

basically, there is never NO risk. There is technically a risk when you use the live-cd. However, I personally would happily say that the risk from using wubi is as near to non-existent as makes no difference.

It will create a file, (the size of which you determine), which will contain your entire ubuntu installation. The whole lot, your home directory, everything. (iirc, it is one file which will be dynamically resized depending on how much you use ubuntu. you determine the MAX size when you install wubi).

When you turn on the computer, you will be given the chance to boot into ubuntu or windows. If you choose ubuntu, then it will access everything it needs from that one file on the windows partition in a completely transparent fashion to you. It will only ever acess that one file unless you mount the windows partition in ubuntu and start messing around.

Plus, it is easy to uninstall when you get your pc back in order and no longer need it ;)

I've used it loads of times, (admittedly only under xp, but vista should be no different), and never had a problem :D

Hope that answers a few questions for you ;)

Not used it on

---

### Post by kansasnoob on 2008-05-08
"When you turn on the computer, you will be given the chance to boot into ubuntu or windows."

And when GF's dad turns on HIS computer and has that option I suspect $h!t will hit the fan!

---

### Post by shifty_powers on 2008-05-08
> **kansasnoob said:**
> "When you turn on the computer, you will be given the chance to boot into ubuntu or windows."

And when GF's dad turns on HIS computer and has that option I suspect $h!t will hit the fan!

thats rather presumptuous of you ;) and thats for the op to judge.

Personally, if i did it on my gf's parents pc, they wouldn't be bothered...

---

### Post by tcoffeep on 2008-05-08
I've just been reading some reviews on Wubi and from what some people are saying, they had a massive HD failure, unless this is more slander against Ubuntu (as I've seen much of in the past for some reason).
*and on a note : my gf's father get's mad when I try to show him how to to check his Hotmail account. He's not very computer-savvy, and until I began using it, didn't update for almost a year and a half!!! --talk about security risk (epic-sigh)--*

So, in essence, does the bootloader change from Vista's original, or does it go GRUB? (I'm just wondering because I can easily switch it up a bit and have it so no bootloader pops up and it goes on as it always has, and when I'm getting my fix I just F8 during loading...would that work, I wonder?)
I'm very interested in this Wubi, seeing as to d/l both VMWare and the Ubuntu 8.04 vmx file would take a total of 6 hours (horrid net service 'round here), but this slander scares me, but he mentioned it was in beta, and I'm unsure if it is or isn't anymore.

---

### Post by SteveNorman on 2008-05-08
If he is freaking out about his computer you better stick to the live cd. 

downloading something like VMware will show up in your virus scans as an intruder. On my XP it triggers zone alarm as "trying to act like a server", even if the VMware network is disabled.

When his vista poops out he is probably going to blame you if you dwnload anything.

PClinuxOS has the minime distro that is meant to be run from a live cd or usb..



also I think gmail gives you memory which can be used as a virtual HD, so maybe you can send files there?

its a nuisance having to load all the plugins everytime you use a live cd,, but its better than crashing dudes machine.

That external hard drive idea sounds promising. you can load a transportable distro on it like minime and take it with you.

---

### Post by tcoffeep on 2008-05-08
Would anyone know if a laptop HD is compatible with a full-scale tower? If yes, that'd totally save me from much unneeded hassle!

[edit] : nevermind. I looked it up. Now looking for a laptop ide hard drive adapter. Thanks for all the help!!! ^_^

---

### Post by Paqman on 2008-05-10
If it's not your PC definitely _do not_ install Ubuntu without the owner's permission.

If you absolutely have to use Linux on it, use a LiveCD and a USB stick for persistence. Like I said, Knoppix can do this really easily. Unfortunately Knoppix isn't a very polished distro, and probably isn't very good for newbies or those wanting a nice-looking desktop. If you can be bothered to do the setup Ubuntu will give you a much nicer environment.

---

