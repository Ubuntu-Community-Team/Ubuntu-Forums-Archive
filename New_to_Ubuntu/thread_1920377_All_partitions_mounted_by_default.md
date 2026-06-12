---
title: "All partitions mounted by default?"
date: 2012-02-04
forum: New to Ubuntu
---

### Post by Resplendent Raven on 2012-02-04
I just starting using Ubuntu 11.10 and i've noticed that i am never required to enter my password to browse another partition, i prefer to have them unmounted and requiring password authorization.
So how do i change this?

---

### Post by drs305 on 2012-02-04
You can edit /etc/fstab, add the partition(s) you do not want mounted and use "noauto" in the options section.

I don't know if you have experience with fstab or not, so begin by looking at this guide on [Understanding Fstab]("http://ubuntuforums.org/showthread.php?&t=283131") and then post the questions you have.

Don't worry if you need help - that's what we are here for.

---

### Post by Resplendent Raven on 2012-02-04
I'll look into it, but coming from 9.04 where i got used to mounting with password, i am curious about the underlying reasons for this change of mounting philosophy.

---

### Post by drs305 on 2012-02-04
> i am curious about the underlying reasons for this change of mounting philosophy. 
I can't answer that as I'm no philosopher.  And of course back in 9.10 we often entertained questions as to why the partitions didn't automount. ;-)  

If you wait a bit you will get a better answer than what I just posted. Although that is one way to do it, I now recall you didn't want any of the extra partitions to mount. There is a setting in gconf or dconf that will probably do that. The 'noauto' option is convenient when you only want specific partitions to remain unmounted.

---

### Post by Resplendent Raven on 2012-02-04
> **drs305 said:**
> I can't answer that as I'm no philosopher.  ;-)

I don't know who the man on your avatar is, but you could've fooled me on the philosopher aspect with it :p

Anyway since i am not really used to editing files i prefer the easiest solution.

---

### Post by drs305 on 2012-02-04
Ok, I found it. I'll give you the GUI method, although it can be done by command line as well.

Open dconf-editor as root. If you don't have it, install 'dconf-tools' first, then:
```
gksu dconf-editor
```
Go to org > gnome > desktop > media-handling 
It looks like the *automount* and perhaps *automount-open* settings are the ones you would be interested in.

Let us know if that works for you.

---

### Post by Resplendent Raven on 2012-02-04
I rebooted after turning them both off, but it didn't change it.
When i press the Home folder on the Unity bar and then click on the devices listed it gives me access straight away.

---

### Post by drs305 on 2012-02-04
I assumed that changing the settings as root would affect all users, and I still expect it does. But you might try also opening dconf-editor as a normal user ("dconf-editor" without the 'gksu') and untick them there as well just in case the system looks only at the user settings and root's doesn't override them.

---

### Post by Resplendent Raven on 2012-02-04
I'm sorry i didn't apply the terminal command and just opened it as a user, let me try again.

---

### Post by Resplendent Raven on 2012-02-04
Still doesn't work.

---

### Post by mcduck on 2012-02-05
IF you don't want a partition to be mounted automatically, and don't want users to be able to mount them, you need to include the "noauto" and remove "user" from that partition's options in /etc/fstab.

However I'm quite sure this will not give you a password window when you try to access the partition from Nautilus, you simply won't be able to do it at all unless you use command-line to mount the partition manually)

---

### Post by drs305 on 2012-02-05
I would have thought the dconf automount setting was the solution, as the description of the setting states:
> If set to true, then Nautilus will automatically mount media such as user-visible hard disks and removable media on start-up and media insertion.

However, since noone has come up with the easy solution, we can modify your fstab to include each partition you don't want automounted. The information we'd need is probably best provided by the boot info script, which gives us the UUID's, names, current fstab settings, etc. You can download the script from the following link. Run the script, post the contents of RESULTS.txt, and we can create the entries manually for you.
[http://bootinfoscript.sourceforge.net]("http://bootinfoscript.sourceforge.net")

Still hoping someone comes up with a universal automount setting solution...

---

### Post by Morbius1 on 2012-02-05
> I  just starting using Ubuntu 11.10 and i've noticed that i am never  required to enter my password to browse another partition, i prefer to  have them unmounted and requiring password authorization.
So how do i change this?     > I'll look into it, but coming from 9.04 where i got used to mounting with passwordEdit as root the following file:
```
/var/lib/polkit-1/localauthority/10-vendor.d/com.ubuntu.desktop.pkla
```and alter the first paragraph from this:
> [Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
ResultActive=yesTo this:
> [Mounting, checking, etc. of internal drives]
Identity=unix-group:admin
Action=org.freedesktop.udisks.filesystem-*;org.freedesktop.udisks.drive-ata-smart*
**[COLOR=#0000FF]#[/COLOR]**ResultActive=yes
**[COLOR=#0000FF]ResultActive=auth_admin_keep[/COLOR]**
Don't forget to comment out ( # ) the ResultActive=yes line. Then save the file - no reboot necessary.

---

### Post by Resplendent Raven on 2012-02-05
Thank you all for your kind help.

Morbius1's solution worked for me and was exactly what i was looking for, still would be nice i guess if such a thing could be done from the systemsettings menu.

---

