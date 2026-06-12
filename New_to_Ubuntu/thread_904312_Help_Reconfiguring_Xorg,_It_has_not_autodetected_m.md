---
title: "Help Reconfiguring Xorg, It has not autodetected my Graphics card!"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by chewit on 2008-08-29
Hi, I'm having an issue with xorg detecting my graphics card. In my xorg.conf file it says this:

[http://ubuntuforums.org/attachment.php?attachmentid=83224&stc=1&d=1220006409]("http://ubuntuforums.org/attachment.php?attachmentid=83224&stc=1&d=1220006409")

So I decide to try this command in the terminal "sudo dpkg-reconfigure xserver-xorg"

This command gets this:

[http://ubuntuforums.org/attachment.php?attachmentid=83223&stc=1&thumb=1&d=1220006406]("http://ubuntuforums.org/attachment.php?attachmentid=83223&stc=1&thumb=1&d=1220006406")

But after going through the steps, all it configures is my keyboard. Then I get this error message:
[http://ubuntuforums.org/attachment.php?attachmentid=83222&stc=1&d=1220006409]("http://ubuntuforums.org/attachment.php?attachmentid=83222&stc=1&d=1220006409")

I am using ATi Radeon 7000 PCI 64mb

I have successful used this card on Ubuntu before, but I have now done a fresh install and this has happened

---

### Post by gn2 on 2008-08-29
Looks like the card is working fine judging by the screenshots?

It is detected, it's listed as "configured video device"

---

### Post by chewit on 2008-08-29
I thought it would say what the card was and the driver it was using.

---

### Post by overdrank on 2008-08-29
> **chewit said:**
> Hi, I'm having an issue with xorg detecting my graphics card. In my xorg.conf file it says this:

[http://ubuntuforums.org/attachment.php?attachmentid=83224&stc=1&d=1220006409]("http://ubuntuforums.org/attachment.php?attachmentid=83224&stc=1&d=1220006409")

So I decide to try this command in the terminal "sudo dpkg-reconfigure xserver-xorg"

This command gets this:

[http://ubuntuforums.org/attachment.php?attachmentid=83223&stc=1&thumb=1&d=1220006406]("http://ubuntuforums.org/attachment.php?attachmentid=83223&stc=1&thumb=1&d=1220006406")

But after going through the steps, all it configures is my keyboard. Then I get this error message:
[http://ubuntuforums.org/attachment.php?attachmentid=83222&stc=1&d=1220006409]("http://ubuntuforums.org/attachment.php?attachmentid=83222&stc=1&d=1220006409")

I am using ATi Radeon 7000 PCI 64mb

I have successful used this card on Ubuntu before, but I have now done a fresh install and this has happened

Hi and I see you are using xubuntu but this link may help with the older ati card
[http://ubuntuforums.org/showthread.php?t=764633](http://ubuntuforums.org/showthread.php?t=764633)

---

### Post by falcon61102 on 2008-08-29
It doesn't necessarily have to say your card and all the modes that are compatible with it.  From what I understand is that was how the older X used to handle it but the newer versions of X are moving away from that.  The important thing is that your drivers are installed and configured correctly, if that is done then it's not overly important what's all written out in the xorg.conf.

---

