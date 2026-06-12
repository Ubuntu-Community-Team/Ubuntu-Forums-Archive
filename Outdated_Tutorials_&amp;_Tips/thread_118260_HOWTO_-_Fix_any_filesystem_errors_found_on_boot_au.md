---
title: "HOWTO - Fix any filesystem errors found on boot automatically"
date: 2006-01-16
forum: Outdated Tutorials &amp; Tips
---

### Post by dcstar on 2006-01-16
Edit /etc/default/rcS to have:

FSCKFIX=yes

Then any errors found will be fixed automatically.


(This really should be a default setting for a distro like Ubuntu so "Ordinary" users don't have to manually run fsck and answer "Y" to any fix prompts they encounter - any "Propeller head" users concerned about losing data after a non-clean exit can set it back to "No". If someone passes idea this onto the Ubuntu developers it may help a lot of people using future releases.......)

---

### Post by UbunT00L on 2006-01-30
I totally agree.  My cousin let his computer sit idle for a week because of filesystem errors on boot, and waited until I came over.  I simply ran fsck and said yes to fix the errors, and thought to myself.....why isn't this automated?  Thanks for the FSCKFIX=yes suggestion, I'll change that the next time I'm over at his house.

---

### Post by magnusbb on 2006-01-30
I agree. Thanks for a great tip.

---

### Post by BLTicklemonster on 2006-01-30
Wait a minute, fix what kind of errors? All errors? Graphics card drivers installed wrong errors? Mouse settings set wrong while trying to set up an internet mouse errors? (like who do you know who doesn't have a mouse with forward and back buttons on their mouse... and ubuntu doesn't load up with them working already... )


I'm interested in hearing more, because this sounds like a really neat trick.

---

### Post by UbunT00L on 2006-01-31
Umm, we're talking about filesystem errors only....

fsck would be the equivilant to windows' scandisk or chkdsk.

---

### Post by sal on 2006-01-31
after using this method this is what i saw on my last reboot:
Tue Jan 31 15:20:01 2006:  * Checking root file system  e2fsck 1.38 (30-Jun-2005)
Tue Jan 31 15:20:01 2006: /: clean, 104724/1221600 files, 719542/2441880 blocks

Tue Jan 31 15:20:14 2006: /home: clean, 1177/1028160 files, 166497/2054311 blocks
Tue Jan 31 15:20:14 2006: e2fsck 1.38 (30-Jun-2005)

is this normal because i have never seen the "e2fsck 1.38 (30-Jun-2005)" in the boot log before.

any help thanks.

---

### Post by dcstar on 2006-02-01
[QUOTE=sal]after using this method this is what i saw on my last reboot:
Tue Jan 31 15:20:01 2006:  * Checking root file system  e2fsck 1.38 (30-Jun-2005)
Tue Jan 31 15:20:01 2006: /: clean, 104724/1221600 files, 719542/2441880 blocks

Tue Jan 31 15:20:14 2006: /home: clean, 1177/1028160 files, 166497/2054311 blocks
Tue Jan 31 15:20:14 2006: e2fsck 1.38 (30-Jun-2005)

is this normal because i have never seen the "e2fsck 1.38 (30-Jun-2005)" in the boot log before.

any help thanks.[/QUOTE]
That's exactly what you want to see - if there were any errors you would see the reports of that.

---

### Post by sal on 2006-02-02
[QUOTE=dcstar]That's exactly what you want to see - if there were any errors you would see the reports of that.[/QUOTE]

ok, cool. thanks. i just wanted to make sure nothing got screwed up.

---

### Post by BLTicklemonster on 2006-02-02
[QUOTE=UbunT00L]Umm, we're talking about filesystem errors only....

fsck would be the equivilant to windows' scandisk or chkdsk.[/QUOTE]
Good enough, thanks!

---

### Post by captainron042 on 2008-06-15
OK, I assume this will fix my startup problem. Unfortunately, I'm a newer Linux user and need a bit more instruction. 

Where do I go to edit this? thanks in advance.

BTW, here is a "screenshot" of my error

[IMG]http://img99.imageshack.us/my.php?image=errordy2.jpg[/IMG]

[http://img99.imageshack.us/img99/4029/errordy2.jpg](http://img99.imageshack.us/img99/4029/errordy2.jpg)

---

### Post by Cato2 on 2008-06-28
Yes, this should fix this error - however you might need to manually fix the error mentioned before you can edit the config file, e.g. type 'fsck /dev/sda3' if that's the filesystem in error.

---

### Post by HunterThomson on 2008-07-06
Where is this in Archlinux? I only have passwd and useradd in /etc/default...


Well I was looking in etc and found rc.sysinit and am thinking this is the same file as the rcs in ubuntu??? Anyway there dosen't seem to be a way to do that in Archlinux.... Could I just add it??? This is just a bash script so I guess I could just wright it my self:)

---

