---
title: "[SOLVED] Does Ubuntu have a system restore?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by Bigtime_Scrub on 2008-06-21
Is there a way to make Ubuntu go back to the way it was when I first installed it? I cannot just reinstall because my CD-ROM is broken and for the life of me nothing boots from USB. I need a system recovery method. I dont want to keep my settings, or back up anything, its the primary reason for me wanting to do a system restore. I hate all the settings I messed with and I dont know how to change them back.

---

### Post by Felicity_X on 2008-06-21
I am more of a newbie than you are, so do not take notice of this unless you get confirmation from someone more experienced than I.

Boot the system as normal and it should give you the option to press <ESC>.  This will bring you to the "Grub" level.  You should see listed the various phases of your system.  Each will be listed twice, once as is (I presume including your alterations) and once labelled "(recover)", which I believe is the original kernel.  I think if you go back as far as you wish and ask to boot the "(recover)" version of that phase it will deliver the system as it was prior to any subsequent settings alterations.

Ask DRS305, as I am sure he would be able to help you.

---

### Post by Bigtime_Scrub on 2008-06-21
I tried that. It just booted as normal like nothing happened. I think what that is used for is fixing system problems or to boot into a different Kernal if you are all 1337 and like to play with that stuff.

---

### Post by cariboo on 2008-06-21
There is no restore function in Ubuntu, CD-rom drive are pretty cheap, you should be able to beg, borrow or pick one up from your local goodwill or other thrift store for a couple of dollars.

Jim

---

### Post by dje on 2008-06-21
> **Felicity_X said:**
> I am more of a newbie than you are, so do not take notice of this unless you get confirmation from someone more experienced than I.

Boot the system as normal and it should give you the option to press <ESC>.  This will bring you to the "Grub" level.  You should see listed the various phases of your system.  Each will be listed twice, once as is (I presume including your alterations) and once labelled "(recover)", which I believe is the original kernel.  I think if you go back as far as you wish and ask to boot the "(recover)" version of that phase it will deliver the system as it was prior to any subsequent settings alterations.

Ask DRS305, as I am sure he would be able to help you.

this is untrue ;)
the recovery kernel mode just drops you to a root prompt so you can perform system maintenance if the normal boot parameters do not work

dje

---

### Post by hyper_ch on 2008-06-21
you could however, boot another way... from a usb stick, through network from the cd... even creating a custom initrd that will boot the cdimage on the harddisk...

---

### Post by dje on 2008-06-21
> **jimv said:**
> ```
rm -r ~/*

```
will wipe out your profile, and bring you back to the gnome defaults.

**but that will delete everything in your home folder, including any personal files**

---

### Post by Bigtime_Scrub on 2008-06-21
I used the shred command. If anyone uses it be warned it will wipe your HD 100% of anything and everything. I then loaded a copy of Kubuntu (because I like KDE :)) and I reinstalled fresh :-D

---

### Post by Miljet on 2008-06-21
Does anyone find it strange that the CD-ROM works fine for installing Kubuntu but didn't work for re-installing Ubuntu?

---

### Post by King_Critter on 2008-06-21
> **jimv said:**
> ```
rm -r ~/*

```
will wipe out your profile, and bring you back to the gnome defaults.

The correct command, if you wanted to remove all preferences, would be:

```
rm -r ~/.*
```

However, even that isn't a good idea because there's a lot of stuff you probably don't want to remove (such as browser bookmarks, custom fonts, macros for various programs, etc.). You'd be better off manually deleting the hidden files you know you want to get rid of.

---

### Post by Bigtime_Scrub on 2008-06-21
> **Miljet said:**
> Does anyone find it strange that the CD-ROM works fine for installing Kubuntu but didn't work for re-installing Ubuntu?

I didnt mention I used an external drive to do this.

---

### Post by subaruwrc01 on 2008-06-21
> **jimv said:**
> ```
rm -r ~/*

```
will wipe out your profile, and bring you back to the gnome defaults.

That's definitely malicious code.

---

### Post by jonofan on 2008-06-22
> **dje said:**
> this is untrue ;)
the recovery kernel mode just drops you to a root prompt so you can perform system maintenance if the normal boot parameters do not work

dje

So the recovery mode takes you to a prompt. What does the older non-recovery mode do? Does it take you back to before you installed updates?

---

### Post by dje on 2008-06-22
> **jonofan said:**
> So the recovery mode takes you to a prompt. What does the older non-recovery mode do? Does it take you back to before you installed updates?

no it just uses an older kernel, it will still drop you to a root prompt with the same settings and updates as any other kernel, using an older kernel does not 'take you back in time' ;)

---

