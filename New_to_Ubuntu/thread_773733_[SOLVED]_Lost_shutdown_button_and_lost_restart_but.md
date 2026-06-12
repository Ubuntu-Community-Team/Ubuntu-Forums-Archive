---
title: "[SOLVED] Lost shutdown button and lost restart button"
date: 2008-04-29
forum: New to Ubuntu
---

### Post by sbonner on 2008-04-29
Greetings!

Using Hardy.  I had the buttons in my shutdown menu options after the upgrade, but now they are gone, leaving only log out, lock screen, switch user, suspend and hibernate.  I have been hitting logout, which causes screen to go black and unresponsive while still powered up.  Eventually, I tap the power button, and see a quick flash of commands failing to execute that seem to be related to initiating the login screen, then the thing shuts down.  When I restart, all works normally, except the missing buttons are still missing.  Every way I know to shut the computer down leads to this incomplete menu.  I have combed the forums, but failed to find exactly the issue I'm having.

I don't know if recent changes could have caused it.  I have been working furiously the past two days to try to enable compiz (and failing) and initiating visual effects (and failing - trying normal or extra gets error message popup "desktop effects could not be enabled").  I also edited the grub boot menu to remove references to the now-gone XP dual boot, then restored the boot menu from backup in hopes that the missing button problem was from that, with no luck.  Besides that, I think the problem started before I edited the grub boot menu.  I've done a lot more bug-fixing over the past few days, but I can't remember them all, only some of what I did tonight.

Anyone know what would cause this, or how to get the default shutdown options menu back?

I would greatly appreciate any help!

---

### Post by warbread on 2008-04-29
Does [this link ]("http://www.tech-recipes.com/rx/2387/ubuntu_restore_restart_shut_down_log_out_button")help you?

---

### Post by sbonner on 2008-04-29
No, but it might lead to something:

"GDM (Gnome Display Manager) is not running.

You might be using a different display manager, such as KDM (KDE Display Manager), CDE login (dtlogin), or xdm. If you wish to use this feature, then your system will need to be configured to use GDM instead."

Anyone know how I can find out what is running, disable it, and set up GDM to run all the time?  I looked in Session Preferences and Services, but neither mention a display manager, much less the ones listed in the error message above.

Thanks for any and all help!

---

### Post by warbread on 2008-04-29
Try 

```
:-$ sudo dpgk-reconfigure gdm
```

---

### Post by sbonner on 2008-04-29
It says command not found.

---

### Post by alienexplorers on 2008-04-30
Try just shutting down the power on your computer and then reboot.  Has worked for me before.

---

### Post by sbonner on 2008-04-30
I've shutdown a few times since it started, but using the attempted logout method.  I will force shutdown via the power button now and come back to tell you how it worked.

---

### Post by sbonner on 2008-04-30
Shutdown did not help.  Thanks, though.

---

### Post by sbonner on 2008-04-30
Well, I got the buttons back, but boy was it a hard path.

I've been incessantly combing the forums and elsewhere for information on the problem.  One person had a similar problem that they attributed to having compiz fusion along with Kubuntu.  Well, I had installed Kubuntu, and decided to stick with Gnome.  So, I thought, "I'll just get rid of Kubuntu desktop and see if that fixes anything.  And I did.  Kubuntu and everything associated with it.

Then I boot, and after GRUB, instead of a login screen, I get a mess of messages and a command line.  Of course, I don't know what command to give, being a noob, so I'm freaking out, trying various options, and finally putting in the live disk to reinstall (been wanting to get rid of grub anyway -- it's a remainder of the week or so when I was dual-booting).  But the live disk won't boot -- it stops at the same point, but without even a command line, just blank screen.

I find some crazy code from solrac924 - 
" Re: BusyBox v1.1.3... please help - can't boot ubuntu.

i mean when you boot up & see GRUB, highlight Ubuntu & press 'E'. then highlight the kernal "...vmzlinuz..." & press 'E'. after deleting "quiet slash", add the following boot parameters: "noapic nolapic acpi=off pci=noacpi irqpoll pnpbios=off vga=0x317"
this should mount the filesystem. does it boot all the way now?"

This did not solve the problem, but it did scroll commands as processed, and I saw, zipping by, an error message saying that GDM was not initiated because it was not the default session.  Egads.

So, I type "sudo gdm", and lo-and-behold Gnome starts up!  And those buttons are back!  I restart, find it still gets the command line, and type sudo gdm again.

Now I have to figure out how to reset gdm as the default session before I restart again.  So, I find this, from a forum staff person, aysiu :
" Re: how to set default desktop as Gnome instead of KDE?
KDM defaults to whatever you used last.
GDM will ask you if you want to make whatever you're selecting the default (if it is not already the default).

Sounds as if your display manager is messed up. If KDM isn't working out for you, you can use GDM instead. Have you tried this terminal command?
Code:

sudo dpkg-reconfigure gdm"

Huzzah!  That sets up gdm, I still have my once-missing buttons, and all is well until I screw something else up tomorrow!

Big thanks to warbread and alienexplorers for trying to help, and also especially big thanks to both solrac924 and aysiu for helping other people in a way that lets me find the trail later and figure it out!

Thanks all!

Now, I just have to figure out how to get rid of grub for direct boot, make this compiz stuff work (or at least initiate visual effects), and install awn or, failing that, simdock.  This linux stuff is proving I'm not the geek I thought I was!

---

### Post by warbread on 2008-04-30
> **sbonner said:**
> 
Code:

sudo dpkg-reconfigure gdm"

Huzzah!  That sets up gdm, I still have my once-missing buttons, and all is well until I screw something else up tomorrow!


And if only I had typed that correctly 5 posts ago, this problem could have been solved quicker.

Sorry about that.

---

### Post by sbonner on 2008-04-30
I didn't realize the command you gave me earlier was the same one I found later (sans typo).  So much happened between that all the earlier steps were forgotten by the time I got to the end.

Thanks much for all help!

---

### Post by Diabolis on 2008-05-01
> **warbread said:**
> Does [this link ]("http://www.tech-recipes.com/rx/2387/ubuntu_restore_restart_shut_down_log_out_button")help you?

It fixed my problem. It is weird, I did change my gdm theme, but I do not remember un-checking the "show actions menu" box.

---

