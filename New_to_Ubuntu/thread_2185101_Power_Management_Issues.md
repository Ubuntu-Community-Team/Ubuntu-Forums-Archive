---
title: "Power Management Issues"
date: 2013-11-01
forum: New to Ubuntu
---

### Post by NekoMao on 2013-11-01
I just installed Lubuntu, and I am having issues with Power Management.

When I close my laptop lid, the computer goes into either suspend or hibernation (sorry, I don't know what the difference between them is.) I went to my settings, and messed with the Power Manager that was installed (It was the same one that Xubuntu uses, I forgot what it was called.) However, no matter what I did, nothing changed. I set the preferences so that if the lid is shut, nothing happens, and that didn't work. I even rebooted my laptop to see if the settings would work then, but no such luck.

I browsed around google and found some people with the same issues. Other people were having issues with Xubuntu's Power Manager not working in Lubuntu (I had issues with it when I used Xubuntu), so I uninstalled it. I saw people were recommending Gnome's Power Manager, so I tried installing that. I first tried installing it through Synaptic Package Manager, that didn't work. I reinstalled it. Then I installed something called Gnome Control Center, which didn't help things either. Last resort, I tried installed Gnome Package Manager through terminal, and it didn't work, either.

When I look at Synaptic Package Manager, it says that Gnome Power Manager is installed, but I cannot find it anywhere in the menu.

So now, I still have no way of editing my power settings, and I can't find Gnome Power Manager anywhere.

I'm not a "beginner" using Linux, but I am a dummy when it comes to using computers, so I apologize for my ignorance. I appreciate any help, thank you.

---

### Post by Bucky Ball on 2013-11-01
> **NekoMao said:**
> 

I'm not a "beginner" using Linux, but I am a dummy when it comes to using computers ...

? This appears to be a contradiction. I don't follow.

Anyway, 

1/ Lubuntu doesn't use Gnome, it uses LXDE;
2/ You don't mention what you want your machine to actually do when you close the lid.

For clarity, you want your machine to 'Do nothing' when you close the lid? This is not great because that scenario will leave the machine, and screen, on as if the lid was open, probably causing overheating and possibly damaging the machine.

---

### Post by NekoMao on 2013-11-01
When I say that I am not a beginner, well, I've been using Linux systems as my primary OS for around 7 years or so. However, I'm not good with computers, I still don't know what a lot of terms mean, or how to fix certain issues by myself.

Well, the reason why I said "Do Nothing" was because that was the only option that Xubuntu's Power Management gave me, other than suspend or hibernate. What I would like it to do is have the screen turn black or shut off, but the laptop to remain on. 

Also, [COLOR=#000000]I know Lubuntu doesn't primarily use Gnome. For it's power management, it had Xubuntu's power manager thing on it. I've had issues with it before, and it wasn't working right for me now. I Googled the issue and saw some people switching to Gnome's power manager, so I decided to try that, but it didn't appear to fix my issue, either, as I cannot find the Power Manager. [/COLOR]

---

### Post by Bucky Ball on 2013-11-01
Thanks for that explaination. 

Just a side note: your details say you are using 11.04. I'm presuming that is not correct as it is no longer supported ...

Okay, now I'm wondering why you would want the screen to switch of but the hard drives and system to stay on ... why, exactly? Suspend basically does the same but spins down the drives. This saves energy, electricity, your money.

I don't know of a way to switch the screen off but leave the drive on. You were achieving this with Gnome? 

You could try launching the Gnome power manager from a terminal. Look up the command to launch it. What I do know is that you can get some strange conflicts when attempting to run more than one power manager. Good luck with it. ;)

---

### Post by NekoMao on 2013-11-01
I am using Lubuntu 13.10.

Yes, I was achieving that with Gnome. When I used Ubuntu, Kubuntu, Xubuntu, and Mint, they all worked like that for me. Though, when I used Xubuntu, I had issues getting it to work at first. I believe I had to install Gnome's power manager in it to achieve the desired effect. Honestly, I find it kind of weird that you're asking why I'd want to do this, as almost everyone I know with a laptop has their system set up that way, no matter if they're running Linux, Windows, Mac, or some other freaky thing.

Also, I tried uninstalling Gnome Power Manager and reinstalling Xubuntu's power manager, and it's manager still did not work. I'm uninstalling that and reinstalling Gnome's, and I'm going to try looking up the commands to run it in terminal. I still wish someone here would help me as to what's happening though. :C I'd hate to have to switch to yet another distro over something like this.

---

### Post by NekoMao on 2013-11-01
Ok, Gnome Power Manager is installed, and when I tried running the command in terminal to launch it, I get this error:

"**** (gnome-control-center:11583): WARNING **: Could not find settings panel "power"** "

It also brings up something called "System Settings", which has the options: Language Support, Printers, and Software & Updates. But I see no selection for power managerment...

---

### Post by Rex Bouwense on 2013-11-01
Your power manager settings for xfce are under Menu->Preferences->Power Manager and they seem to work quite well for me using        Lubuntu 13.10.  Since the screen saver has been removed in this version it is quite easy to have the black screen come up.  Just navigate from Power Manager->On Battery (or ON AC)-> Monitor, where you can choose the time that your screen will go black.  Does this not work for your installation of 13.10?

---

### Post by walterorlin on 2013-11-01
[https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021](https://bugs.launchpad.net/ubuntu/+source/xfce4-power-manager/+bug/1222021) is a bug that sounds like this might be it as it is doing it in spite of the power manager.

---

### Post by NekoMao on 2013-11-01
walterorlin, that sound exactly like my problem. 

I've noticed I'm having several other issues with Lubuntu as well, like my print screen button does not work, despite having "scrot" installed. I think I might just switch back to the Gnome desktop environment or something...

---

### Post by Bucky Ball on 2013-11-01
As 13.10 is new it will have teething problems. This could be one of them. Try again in a month or three.

---

### Post by vasa1 on 2013-11-01
> **NekoMao said:**
> ..., like my print screen button does not work, despite having "scrot" installed  ...

Did you check your home folder  and the Pictures folder?

By the way, whichever DE you choose, please raise just one issue per thread. That would be helpful to others who may have the issue that isn't in the title or tags you've chosen and possibly to you as well.

**Edit**
I just checked with default settings: pressing Print doesn't do anything for me as well using default settings. I did not notice this before because I just copied over certain modifications from the previous version.

**Edit 2**
I've made a post with what I think is an appropriate title here:  ["Print Screen" doesn't work in Lubuntu 13.10?]("http://ubuntuforums.org/showthread.php?t=2185294&p=12836083")

---

### Post by Bucky Ball on 2013-11-02
> **vasa1 said:**
> ... please raise just one issue per thread. That would be helpful to others who may have the issue that isn't in the title or tags you've chosen and possibly to you as well.

+1. The answer to the print screen question seems to be provided on vasa1's linked thread.

---

### Post by spatialguy on 2014-09-26
I had the same issue: 
- close the lid of my ubuntu 14.04 laptop
- laptop goes in suspend
- wake up to a black screen (reboot or console and kill x to get desktop back)

 fiddled around with powertools and no luck.
BUT: 
Light locker (screensaver) settings where also set to start a screen saver etc.
===Disabled light locker and now===
Close lid->suspend->open lid->wakeup is working!

So check if multiple screen savers/powertools are interfering...

---

### Post by oldos2er on 2014-09-26
Old thread closed.

---

