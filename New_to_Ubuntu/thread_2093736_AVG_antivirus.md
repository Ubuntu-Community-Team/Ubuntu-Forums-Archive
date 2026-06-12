---
title: "AVG antivirus"
date: 2012-12-11
forum: New to Ubuntu
---

### Post by johnwill on 2012-12-11
I have reloaded AVG Free Antivirus as advercated by forum members
I note that all commands are from the Terminal: Have successfully updated [Sudo avgupdate]but seem unable to get an automatic scan whilst running Linux and e-mails, [avgsetup]any help would be appreciated. The reason for reloading Avg antivirus is because I have a dual boot with Windows 7.

---

### Post by Mr. Hibba on 2012-12-11
What errors or warnings does it display in the terminal?  (I just found out about AVG on Linux, so I'm still learning it too.)

---

### Post by DuckHook on 2012-12-11
Don't know who has advocated it. I certainly don't. However, don't want to start another round of controversy here, so will comment thus:

The anti-virus app most Linux-users use is ClamAV. It has a graphical front-end that can be found in the software store as ClamTk, which makes it very easy for new Linux users. Moreover, because it is in the Ubuntu repository, it will continue to be supported and updated. With AVG, you will have to self-manage the app.

However, would point you to this thread, which is more of a guide/FAQ in the security subforum, and therefore something that is quite authoritative.

[http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812)

It's rather overwhelming for new users, but the gist of it is this:

Most users from Windows are actually too lax about security, but focus altogether on the wrong things: they want anti-virus (completely unnecessary) but will not turn on their firewall or turn off cookies and scripting on their browser (all necessary--or, at least, highly recommended). I've lost count of the new Linux users who want to both install anti-virus and to disable passwords at the same time, thus dragging over two of the very worst practices from Windows, not to mention that the two desires are incompatible and mutually contradictory.

Major apologies for my rant, but this old fart just had to get it off his chest.](*,)

Now that that's done, please appreciate that antivirus will slow your system down due to scanning and system overhead. If your system is relatively new, this might be okay, but on my old systems, I don't want  to load a single unnecessary module. If you have antivirus loaded on your Windows install (very necessary), then this is enough. Linux cannot "infect" the Windows partition (it doesn't work that way), although...

hmmm... are you worried about Windows infecting Linux? If so, then I suppose that this is a long-shot possibility. For what it's worth, I run Windows in a virtual machine with full anti-virus, anti-spyware, anti-everything-and-the-kitchen-sink. I don't *think* I'm at risk, but then, I never fire up Windows except four or five times a year and I never surf or download in it.

Hope your Linux experience is rewarding!:D

---

### Post by lisati on 2012-12-11
I might have advocated AVG five years ago, when the Ubuntu-friendly version had a GUI available. These days, my preference is running my own email server using Postfix/Amavis/ClamAv/Spamassassin together with some home-grown policy scripts.

---

### Post by DuckHook on 2012-12-11
> **lisati said:**
> ...These days, my preference is running my own email server using Postfix/Amavis/ClamAv/Spamassassin together with some home-grown policy scripts.

...that puts you in the upper flakes of the upper crust of power-users. Wow.

---

### Post by mastablasta on 2012-12-12
Clam is not that good for catching MSviruses. also MS security essentials is more of a a joke with a good easy to use GUI. 
 
i think avira has free linux version, though i think it's cli only. avast also has a linux version. both are free and according to latest tests quite good at catching things.

---

### Post by Mark Phelps on 2012-12-12
Kaspersky also has a free Rescue CD image that you can download and burn to CD -- and then, boot from that to run the AV app.

---

