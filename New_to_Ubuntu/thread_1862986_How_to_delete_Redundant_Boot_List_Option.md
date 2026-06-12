---
title: "How to delete Redundant Boot List Option ?"
date: 2011-10-17
forum: New to Ubuntu
---

### Post by mglennpooh on 2011-10-17
I love Linux & Wubi because I can install, uninstall, & reinstall whenever I please. Indeed, I love this 1st week after the new release because I get that MAD Scientist Feeling every time - **I am become like Shiva, the Destroyer of Worlds !!!**

However, I'm also a **newbie** who noticed there's an extra option for Ubuntu on my boot list which lingers even after I uninstall my last installation. I'm especially concerned because I've noticed a growing momentary hesitation during the boot which I suspect is related to this lingering extra. The hesitation is attended by a momentary purple screen then a quick black-out then an increasingly hesitant purple-with-tiny-white-dots screen before the login prompt finally pops up. 

I've ran diagnostic tests on both Ubu11.10 & Win7 with no ill report. I suspect this isn't the 1st time some of the more experienced among you have heard or dealt with this. My big worry is my 64bit Intel T4400 which has minimal capacity for higher functions (?!?).
[B]
*R*S*V*P*  [/B]

---

### Post by garvinrick4 on 2011-10-17
Should boot the latest of kernels installed. Keep at least 2 of them so if one does not boot the other one will.

Can get rid of in synaptic:
Type the kernel you want to get rid of in search window of synaptic and it will give you image to remove.

The extra kernels have no effect whatsoever on anything,  the one you choose to boot with just is in use
and the others are just there as backups.

---

### Post by -kg- on 2011-10-17
> **garvinrick4 said:**
> Should boot the latest of kernels installed. Keep at least 2 of them so if one does not boot the other one will.

Can get rid of in synaptic:
Type the kernel you want to get rid of in search window of synaptic and it will give you image to remove.

The extra kernels have no effect whatsoever on anything,  the one you choose to boot with just is in use
and the others are just there as backups.

No, I don't think he's talking about a kernel upgrade...

> ...Linux & [COLOR="Red"]***Wubi***[/COLOR] because I can install, uninstall, & reinstall whenever I please...

...noticed there's an extra option for Ubuntu on my boot list which lingers even [COLOR="Red"]***after I uninstall my last installation.***[/COLOR]

Extra kernels aren't left in GRUB if you uninstall a regularly installed OS, and since this is WUBI we're talking about, certainly you aren't going to have any kernels at all (until you install another instance).

I'm not real sure how WUBI works as far as the bootloader goes.  Are you saying the selections are building up, even after uninstalling it?  How many selections do you have in your bootloader now?

I have read that, when uninstalling a WUBI installation, you uninstall it using Windows "Install/Uninstall Software" in the Control Panel just like any other software package under Windows.  That's what you're doing when you uninstall an installation, right?  I would think that, upon properly uninstalling it, it would also correct the Windows boot manager.

I really don't know much about WUBI, so hopefully someone will come along with greater knowledge.

---

### Post by mglennpooh on 2011-10-17
I mean the normal black screen with white letter list immediately between off-off & the boot, not the command prompt terminal. I have the one odd extra Ubuntu which has lingered on this boot option list since I uninstalled a failed 5 hour 11.10 Upgrade after Wubi installed 11.04. I now download both the Wubi & ISO due to tar.xz incompatibility with my Windows - Wubi utilizes the ISO instead of downloading the tar.xz file. 

FYI - Wubi uninstalls any remnant of the previous before installing the new kernel & such, but I suspect the HP Pavilion Boot Option List is beyond Wubi's jurisdiction. 

I'm worried about this odd extra option on my Dual Boot Selection Screen...1+1=2, not 3. I think this is causing an increasing hesitation in my boot which may ultimately return at once all the one fingered salutes I've given in the last week.

---

### Post by Mark Phelps on 2011-10-17
If this extra entry is left over from an older Wubi install, you can remove it a couple of different ways (in MS Windows, or course):
1) Use BCDEdit, in command mode, to remove the entry.  Risky but works -- like all command mode functions.
2) Download and install EasyBCD, then launch it, and use the Edit Boot Menu option to remove the unwanted entry.  Safer because it uses a GUI, so you don't have to worry about misspelling command options.

---

### Post by mglennpooh on 2011-10-17
I opted for the easy way out and was able to select Edit Boot Menu then click on the odd 2nd Ubuntu listing then click DELETE - HA - HA - HA - HA !!! Sorry, got that MAD Scientist Feeling going again.
 
Google & download 100% free EasyBCD for General Partitioning, Boot, & System Editor - incl Wubi Problems within Windows, Macintosh, Linux, etc. 

Thank You, Mark Phelps

---

### Post by garvinrick4 on 2011-10-17
> Sorry, got that MAD Scientist Feeling going again.
You sure Like your new found powers, Linux is great isn't it, only gets better mglennpooh, enjoy your
Ubuntu.

---

