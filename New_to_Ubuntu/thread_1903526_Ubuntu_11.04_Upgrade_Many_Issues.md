---
title: "Ubuntu 11.04 Upgrade Many Issues"
date: 2012-01-02
forum: New to Ubuntu
---

### Post by pjobson on 2012-01-02
Did the upgrade from 10.10 to 11.04, now GRUB is out of range for my old 1024x768 monitor, I can hit enter on what I assume is the correct entry for linux, if I don't hit enter it just sits there showing that my video is out of sync indefinitely.. this starts the boot process, but it never seems to get passed CUPS, either CUPS actually takes over 4 hours to start or there is something seriously wrong.

It would be cool if I could get to single user mode, but back to the GRUB out of sync issue.

This is the second system which has basically turned into trash after using the command line do-release-upgrade 10.10 to 11.04 upgrade.  

Does do-release-upgrade ever work or just some kind of sick joke?

Seriously though .. is there any way to get this system back to a "healthy state" or is it time to get out the CD and start from scratch?

---

### Post by pjobson on 2012-01-02
Was able to get to the command prompt...

Foolishly I tried to do do-release-upgrade to go to 11.10, now when it gets to what I assume is GRUB and the video is still not syncing, I hit enter and it just stays there...  of course I can't really tell.  F1-F9 and Alt+F1-F9 do nothing.  Can't get passed it.

Think I'll wait for a few years, before I get back to Ubuntu.  A buddy of mine said that he had no problems what-so-ever with the do-release-upgrade, what I stupidly assumed would be an hour or two to upgrade has flushed the entire day down the toilet.

---

### Post by LinuxFan999 on 2012-01-02
Upgrading through the update manager is not recommended.
The recommended way to upgrade is to burn a CD of the release that you want to upgrade to, and install it over the release that you are currently using (formatting only the / partition, and the /boot partition, if present).

---

