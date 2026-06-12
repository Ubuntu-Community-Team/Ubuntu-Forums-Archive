---
title: "question about Slackware and Vector Linux ?"
date: 2007-12-20
forum: Other OS Talk
---

### Post by mocqueanh on 2007-12-20
I'm using Xubuntu 7.1, now i want to add Vector and Slackware OS into my machine.
Because my PC is old (Celeron and 256 MB RAM)

But i cant find the download links for 6 CDs of Slackware ( [http://www.slackware.com/getslack/](http://www.slackware.com/getslack/) ) canf find download links here.
And dont want to download as torrent.


When using Xubuntu (ALT edition), each time reinstall Win, i restore my GRUB by:

boot from Xubuntu ALT disc, choose rescue broken system, choose reinstall GRUB, and tell Ubuntu which the partition of Xubuntu's /boot
(very easy to restore GRUB with Xubuntu)


But i wanna ask you: restore GRUB by Slackware and Vector Linux is easy as Xubuntu ? And how ?

*Sorry for ask other distro here, cause' forums of Vector and Slackware not have huge user online like Ubuntu community*  :lolflag:

---

### Post by tommcd on 2007-12-20
Here is the mirror I use:
[http://slackware.mirrors.tds.net/pub/slackware/slackware-12.0-iso/](http://slackware.mirrors.tds.net/pub/slackware/slackware-12.0-iso/)
Just click the link you posted, click on a country you want, then a mirror, then slackware-12-iso. You only need the first 2 iso discs to install Slackware.
After you install Slackware (or Vector) update your grub menu as per post #4 from this thread:
[http://ubuntuforums.org/showthread.php?t=393379](http://ubuntuforums.org/showthread.php?t=393379)
Slackware uses lilo instead of grub. If you want to continue using grub (as I do), just choose not to install lilo when installing Slack and update your grub menu as per post #4 from the above link.
EDIT: The slackware forum at linuxquestions.org is very good. A lot of really hardcore Slackers hang out there that really know their stuff.
BTW, you may want to consider Zenwalk as an alternative to Vector. Zenwalk is based on Slackware, and it is excellent!
[http://zenwalk.org/](http://zenwalk.org/)

---

### Post by mocqueanh on 2007-12-20
So, if i want to install LILO of Slack, can LILO recognize my Xubuntu, Vector and XP ?

And how to restore LILO each time re-install XP ?

---

### Post by tommcd on 2007-12-20
> **mocqueanh said:**
> So, if i want to install LILO of Slack, can LILO recognize my Xubuntu, Vector and XP ?

And how to restore LILO each time re-install XP ?

If you install lilo to the MBR it will likely pick up Windows, but you will probably have to manually edit /etc/lilo.conf to add Xubuntu and Vector, and then run /sbin/lilo as root. Lilo is not interactive as grub is. To make changes in lilo you manually edit /etc/lilo.conf and then rerun /sbin/lilo. Here is a brief tutorial:
[http://wiki.zenwalk.org/index.php?title=Multiboot_with_LILO](http://wiki.zenwalk.org/index.php?title=Multiboot_with_LILO)
I would recommend sticking with grub for multiboot setups like this. It is easier to use imo. You can multiboot with lilo, you just need to be able to edit lilo.conf properly.

---

