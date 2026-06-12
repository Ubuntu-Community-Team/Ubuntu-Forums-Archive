---
title: "So I installed BorgServer"
date: 2009-09-26
forum: Recurring Discussions
---

### Post by jrothwell97 on 2009-09-26
So, as my programming class entails learning to code in the Devil's Own Language (Visual Basic.NET) I was forced to install Windows Server 2003 (which, as a student, I get free [as in beer, of course] through Dreamspark.)

Of course, it hosed the bootloader, and I'm still trying to beat GRUB and Windows's bootloader into playing nicely with each other - in effect, at the moment, I can start into Windows normally or I can boot from a *buntu LiveCD to access the files I need from my extfs formatted drives. This means I've been stuck in BorgOS for around a week now.

In short, although I do miss Ubuntu (and will certainly be installing Karmic to restore the bootloader at the end of next month) Windows, as a whole, is underrated. True, Vista was terrible, but Server 2003 is basically a rebranded XP with a few more configuration options.

Overall, it took be about four hours to set up - about the same as an Ubuntu installation. I'm not bothered about hardware acceleration, so I haven't installed that, although if anyone *can* point me to a guide to installing a GeForce2 MX 400 graphics card on WS2K3, I would be very grateful.

First, the bad points: the Registry is, of course, a problem. Also, Windows Update, as an update service, *sucks*, and how they can accuse Ubuntu of being difficult to update is incredibly cheeky. There are also the little things - I miss being able to hold ALT and grab any window to move it, and being able to switch to a virtual terminal with Control+Alt+f(x).

Now for the important points. **Windows, as an OS, is underrated.** True, I'm dubious about Windows Server's value as a server OS when practically any update or driver installation requires a restart - however, with a little tweaking, it's very good as a power user's OS.

I know someone will come whinging about how Windows is less secure than Linux, and this is true - by default. The answer is as follows.

**Do not use an administrator account for day-to-day use - use a power user account instead and use runas /user:Administrator in the same way as su if you *absolutely must*. Treat the Administrator account like an administrator account - using it should be get in, do what you need to, get out. Use strong passwords for both accounts.**

At present, I'm running Windows without anti-virus software or even a firewall, and I've yet to experience any issues. The simple reason for this is that I **exercise common sense**. IE8, although its rendering engine is typically IE and tab grouping doesn't work, at least includes *some* security measures which stop the majority of attempted attacks dead in their tracks. Normally I browse the web in Chrome anyway, so this isn't too much of an issue.

True, using runas /user:Administrator can be a pain sometimes, but it keeps the system secure. Let's not forget that Debian and Fedora use the same system.

Overall, although it's certainly not perfect *cough* Registry *cough*, Windows is better than people give it credit for (with the possible exception of early versions of Vista, but since they're soon going to be obsolete anyway, that doesn't really matter). I'd sooner be using *nix, but don't for a moment blame Microsoft for anti-virus software slowing down the system. If users had a bit more common sense, and updated their systems to eliminate IE6, anti-virus software would become unnecessary overnight.

---

### Post by bodhi.zazen on 2009-09-26
Moved to recurring discussions as it seems to be yet another windows vs ubuntu threads.

4 hours to set up Ubuntu ? :lolflag:

I set up Linux servers is about 10 minutes.

---

### Post by jrothwell97 on 2009-09-26
Well, this is pretty much due to the fact that I like my OS to behave in a certain way. So setting up Ubuntu usually involves

[list=1][*]installing LaTeX and LyX
[*]installing Tomboy
[*]configuring fstab to handle my external drives properly
[*]Installing Flash
[*]installing AbiWord
[*]installing Wine
[*]depending on how infuriated I am with OpenOffice.org, installing BorgOffice under Wine
[*]enabling hardware graphics acceleration
[*]Installing updates
[*]reconfiguring my keymap
[*]Setting up bashrc
[*]Setting up Evolution
[*]setting up network folders[/list]

In short, these are all the sorts of things you'd usually do when configuring an OS after installing it - reconfiguring it to suit your needs.

All these are generally easier in Ubuntu than in Windows, and it's still better out of the box. However, the crux of my argument is that the majority of perceived "problems" with Windows (such as antivirus software slowing down the system, and malware in general) are caused by user error, and not by MS themselves.

---

### Post by bodhi.zazen on 2009-09-26
The installing parts of what you say are a simple apt-get and are trivial, can be scripted if you wish.

The config files vary, some can be managed with rsync.

Flash , Openoffice, wine, Evolution, and an expensive graphics card are not what I would consider typical applications on a server, Mircosoft or Linux. I ran a Windows NT server for some time and it had none of those applications on it, those are desktop applications and configurations.

It should take you no more then an hour or so to set up a Linux desktop, especially Ubuntu.

---

### Post by jrothwell97 on 2009-09-26
> **bodhi.zazen said:**
> The installing parts of what you say are a simple apt-get and are trivial, can be scripted if you wish.

The config files vary, some can be managed with rsync.
Yes - however, the apt-get itself takes time, along with installing updates. Also, I tend to configure apps right after installing them (setting the default font in LyX to Palatino, installing the fonts I need and changing the default interface font to something like FreeSans or Helvetica.)

> **bodhi.zazen said:**
> Flash, Openoffice, wine, Evolution, and an expensive graphics card are not what I would consider typical applications on a server, Mircosoft or Linux. I ran a Windows NT server for some time and it had none of those applications on it, those are desktop applications and configurations.
Exactly: I said, in the post, that I was dubious about Windows Server's merits as a server, since it needed to be rebooted so often and also seemed rather sluggish.

However, in effect, all Windows Server is is a rebranded XP with some of the default configuration changed.

And the GeForce2 MX 400 is hardly an "expensive" graphics card - its driver is in the "legacy" section of nVidia's website.

> **bodhi.zazen said:**
> It should take you no more then an hour or so to set up a Linux desktop, especially Ubuntu.

Again, this depends on your needs. I get all the configuration and installing done immediately, which is why it would take me around fourteen years to properly configure a consumer Toshiba laptop with its dreadful bloatware.

For me, it takes four hours or so. That's it.

---

