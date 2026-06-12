---
title: "Xubuntu is still coming in boot options after uninstalling."
date: 2008-11-18
forum: New to Ubuntu
---

### Post by rams123 on 2008-11-18
I installed Xubuntu inside XP. Then I uninstalled it. But when I start my computer I'm still getting Xubuntu at boot options.

Like this-

> Microsoft Xp
Ubuntu (Installed inside Xp)
Xubuntu

When I click Xubuntu computer is restarting. What I have to do , to remove Xubuntu in boot options ? Help me.

---

### Post by Keen101 on 2008-11-18
I'm confused by your post.

Did you install ubuntu inside xp with WUBI?

Did you also install xubuntu (outside xp)?

If you installed ubuntu with WUBI, and uninstalled it, then the boot options should have went away. But, if you also installed xubuntu (outside xp) then the GRUB menu is what is dispplaying the boot options.

anyway... can you please clarify?

---

### Post by Twitch6000 on 2008-11-18
> **rams123 said:**
> I installed Xubuntu inside XP. Then I uninstalled it. But when I start my computer I'm still getting Xubuntu at boot options.

Like this-



When I click Xubuntu computer is restarting. What I have to do , to remove Xubuntu in boot options ? Help me.

Ahh I had a slighty similar problem with my Windows computer.

This is due to the Windows Boot.inf you will have to edit it and tell it to not have xubuntu on there anymore.


Inorder to get to the boot.inf do this - go to My Computer>tools>folder options>view then click view hidden folders and click off hide protected operating systems.

Then go to the boot.inf in the main drive.

The Xubuntu list will look something like this -

multi(0)disk(0)rdisk(0)partition(1)\WINDOWS="Microsoft Windows XP Home Edition" /noexecute=optin /fastdetect(note don't delete your windows boot or you won't be ableto get to it)

---

### Post by caljohnsmith on 2008-11-18
You'll need to modify your Windows boot.ini file, which you can do via [these directions]("http://support.microsoft.com/kb/289022") from Microsoft; just delete the line in boot.ini that says:
```
C:\wubildr.mbr="Xubuntu"
```
And you should be all set. :)

---

