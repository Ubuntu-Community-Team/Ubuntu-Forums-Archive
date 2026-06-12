---
title: "&quot;Upgrading&quot; from Ubuntu 11.04 to Kubuntu?"
date: 2012-11-10
forum: New to Ubuntu
---

### Post by pakopako on 2012-11-10
Feel silly asking this, but I think I'm forced to upgrade my Ubuntu 11.04 now.
I'm a little worried about jumping to Ubuntu 11.10 (and eventually 12.04 LTS) because of my old hardware (a Toshia M200 laptop with a smaller HDD) and my rationalized fear of UNITY (I stuck with Gnome in 11.04).

So I thought "why not Lubuntu?" (even if it doesn't use GNOME) -- is there a specific way to jump from Ubuntu 11.04 to Lubuntu 11.10 (and then to 12.10)? The [official help]("https://help.ubuntu.com/community/Lubuntu/Documentation/UpgradeToLubuntu") *skips over 11.04* and so does the [Psychocats help page]("http://www.psychocats.net/ubuntu/purelubuntu"). Another psychocats page shows how to turn [Gnome to pure LXDE]("http://www.psychocats.net/ubuntu/purelxdenatty"), but is that all?

Also... I'm not sure, but I think my processor lacks PAE (it's one of those 400 MHz-bus Centrinos) so that's another reason why I might not be suited for upgrades past 11.10 (The 12.04 Ubuntu LiveCD wouldn't boot.)

---

### Post by monkeybrain2012 on 2012-11-10
Make a live usb and test it out. Instead of doing upgrade it is a lot faster and and safe to do a clean install, just back up your data first.

No, there is no upgrade route from Ubuntu to Lubuntu.

---

### Post by NikTh on 2012-11-10
> **monkeybrain2012 said:**
> Make a live usb and test it out. Instead of doing upgrade it is a lot faster and and safe to do a clean install, just back up your data first..

+1 . 

I have nothing to add. 

I suggest Lubuntu too.

But your title says : "Upgrading" from Ubuntu 11.04 to **Kubuntu**? :)

---

### Post by newb85 on 2012-11-10
There isn't an upgrade from Ubuntu to Lubuntu, but you could simply upgrade your system to a newer Ubuntu and then add the Lubuntu interface.

I do, however, support previous recommendations for a clean install.

---

### Post by pakopako on 2012-11-10
> **monkeybrain2012 said:**
> Make a live usb and test it out. Instead of doing upgrade it is a lot faster and and safe to do a clean install, just back up your data first.
Actually, because of my laptop make-and-model, I can't use LiveUSB. I'm almost out of CDs at the moment, but let me ask since I can't find it on Wikipedia: does Lubuntu 12.04 requires PAE on my processor? (I might just jump over to Xubuntu 12.10, which has a non-PAE kernel, or Kubuntu 12.04 which looks... like it'll still need new hardware.)

A question does arise, however. How do I "back up" data in Ubuntu? No so much saved worksheets, but GiMP plug-ins and Firefox passwords? Do I just compress the entire $home/pakopako directory, or do I have to do some more hunting-and-pecking?

> **NikTh said:**
> But your title says : "Upgrading" from Ubuntu 11.04 to **Kubuntu**? :smile:
Heh. I didn't even notice that. Fixed.

---

### Post by Bartender on 2012-11-10
Unless I'm mistaken, Lubuntu 12.04 is NOT an LTS.  Something to think about.

Your /home folder will have your Firefox settings.  Not sure about GIMP.  

I'm running Lubuntu 12.04 on an old Pentium 4 PC without any problems so I don't think [PAE]("https://help.ubuntu.com/community/EnablingPAE") will trip you up.  I understand the basic idea behind PAE but not the details...

There are several different ways of looking at backing up.  For some, it's just saving the .jpg's, .mp3's, .mkv's, .odt's etc. and starting over with all the little settings/configurations, etc.  To me, it might make more sense to simply save the files and start over with settings, because sometimes these settings don't carry over to newer versions of the software successfully.

EDIT: I didn't know that this [PAE stuff]("http://www.webupd8.org/2012/05/how-to-install-ubuntu-1204-on-non-pae.html") could stop you from installing - will have to look into this some more.  Funny that I've had no problems so far with my old clunker PC's

---

### Post by jerome1232 on 2012-11-10
> **Bartender said:**
> Unless I'm mistaken, Lubuntu 12.04 is NOT an LTS.  Something to think about.


You are mistaken. It is LTS.

You can simply install lubuntu-desktop, which will get you everything that's on a Lubuntu install, it'd be much neater and cleaner if you could do a full install however.

---

### Post by Bartender on 2012-11-10
> **jerome1232 said:**
> You are mistaken. It is LTS.

Here's a quote from the [Lubuntu]("http://lubuntu.net/blog/lubuntu-1204-now-available") website...

*"Unlike Ubuntu, Lubuntu 12.04 is not a LTS, this version will be supported for 18 months. However, a lot of work has been done to improve the stability of the system."*

---

### Post by jerome1232 on 2012-11-10
*places foot in mouth*

Just seems odd, they use the same repo's, which repo's will be up for the duration of the LTS sending along updates. I'll have to digg for more clarification on that.

I wonder if the lxde aspects will just stop receiving updates after 18 months maybe.

---

### Post by Bartender on 2012-11-10
I had thought Lubuntu 12.04 was LTS.  Was surprised to read that it's not just a coupla days ago.

We're getting a bit off-topic here, but a person could do something like what you suggested.  

Install Ubuntu 12.04, then install the lubuntu-desktop package.  As you mention, I prefer not to install DE's on top of each other, but in this case one could uninstall lubuntu-desktop 12.04 when support runs out, then install the latest version of the Lubuntu DE.  You'd still have the Ubuntu 12.04 DE "underneath" the Lubuntu DE...

---

### Post by pakopako on 2012-11-10
> **Bartender said:**
> Your /home folder will have your Firefox settings.  Not sure about GIMP.  

I had thought Lubuntu 12.04 was LTS.  Was surprised to read that it's not just a coupla days ago... Install Ubuntu 12.04, then install the lubuntu-desktop package... You'd still have the  Ubuntu 12.04 DE "underneath" the Lubuntu DE...[/quote]
It's the odd things everyone finds out when they have to. (I know I'm learning a lot these past few hours.)

Alright then, I'll probably pack my /home folder up and jot down all the programs I installed before re-formatting my partition?

Because of my laptop's lack of boot-from-USB, I'll have to jump into a new distro with both feet. (Unless other *buntus can be used via WUBI. [Looks like they can?](http://www.dedoimedo.com/computers/wubi.html))

Because of my non-PAE processor, I believe I'm limited to trying Xubuntu 12.10 or Lubuntu 12.04 running from a 7GB WUBI space (just so I can see everything still runs). Hopefully I'll be able to reinstall all my software and transfer over the settings from my home-folder.

---

### Post by NikTh on 2012-11-10
> **jerome1232 said:**
> *places foot in mouth*

Just seems odd, they use the same repo's, which repo's will be up for the duration of the LTS sending along updates. I'll have to digg for more clarification on that.

I wonder if the lxde aspects will just stop receiving updates after 18 months maybe.

> **Bartender said:**
> I had thought Lubuntu 12.04 was LTS.  Was surprised to read that it's not just a coupla days ago.

And what is the mess here ? 
Lubuntu yes , is not an LTS version due to LXDE environment. 
Lubuntu 12.04 contains Ubuntu's 12.04 repos and all the packages and security updates will be supported unitl April 2017 (like Ubuntu 12.04 LTS) **except** the packages of LXDE environment. PcmanFM , leafpad , lxterminal , lxpanel.. etc. 
So from one perspective we can say Lubuntu 12.04 is  semi-LTS version :)

---

### Post by Bartender on 2012-11-11
> **pakopako said:**
> I'm not sure, but I think my processor lacks PAE (it's one of those 400 MHz-bus Centrinos)

Can you provide more clarification?  "Centrino" is an Intel marketing term for an all-Intel unit.  CPU, GPU, and wi-fi.  I've been googling PAE this morning and it appears that you'd have to have a really ancient processor to worry about this.  With one exception; the 400MHz Pentium M's.  Is that what you meant by the above?

Here's a [link with instructions]("http://askubuntu.com/questions/128396/how-can-i-tell-if-a-machine-has-pae") for checking whether you're PAE-capable or not...

---

### Post by pakopako on 2012-11-12
> **Bartender said:**
> I've been googling PAE this morning and it appears that you'd have to have a really ancient processor to worry about this.  With one exception; the 400MHz Pentium M's.  Is that what you meant by the above?
I did the same search when that error popped up on my 12.04 liveCD, so yes I have an ancient processor:-({|=, and yes, it's that one exception](*,).

---

### Post by NikTh on 2012-11-13
> **pakopako said:**
> I did the same search when that error popped up on my 12.04 liveCD, so yes I have an ancient processor:-({|=, and yes, it's that one exception](*,).

Hmm , then I guess you have to follow the "hard way" . Install through minimal CD. 

Here are the mini isos => [https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

[Here is a guide with pictures]("http://maketecheasier.com/install-a-minimal-ubuntu-on-old-laptop/2012/02/24") but is just an example. You have to install the packages you want and not what is listed in the guide. 

Thanks

---

