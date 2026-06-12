---
title: "Might have erased important kernel?"
date: 2014-04-20
forum: New to Ubuntu
---

### Post by GarlicxSauce on 2014-04-20
Hi everyone,

I think i might have messed up with my hard drive, yesterday evening i've run ubuntu tweaks in the attempt of cleaning up the hard drive and leave it free for software updates ( i do it weekly), when i started my laptop this morning after i've typed the initial password to decrypt the hard drive, instead of booting it told me that there was an issue into finding the right kernel ( i dont remember the exact message), i've rebooted it and it made a disk check and told me it couldnt find the disk anymore, in full panic i've restarted the machine manually and this time it was able, after another disk check, to regularly load ubuntu.

Besides backing up immediately, do you have any advice about what to do?

Many thanks in advance

---

### Post by startas on 2014-04-20
Just reinstall ubuntu and dont do this thing anymore. It will be much faster than searching for the end of the universe.

---

### Post by Warren Hill on 2014-04-20
Assuming you have good backups reinstalling is probably the easiest.

On the assumption you don't have good backups then you may want to look at this question on AskUbuntu

[http://askubuntu.com/a/446949/107450](http://askubuntu.com/a/446949/107450)

To recover your personal data to an external drive before reinstalling.

---

### Post by bapoumba on 2014-04-20
> **startas said:**
> Just reinstall ubuntu and dont do this thing anymore. It will be much faster than searching for the end of the universe.

Hmm, I would wait of some other input before reinstalling.

I cannot walk you through debugging, but reinstalling is the last resort option imho. Please do your backups and wait for more activity in this thread, thanks.

---

### Post by GarlicxSauce on 2014-04-20
Thanks a lot for the help, im currently backing everything up, so that in the case that i need to reinstall nothing is lost.

---

### Post by fantab on 2014-04-20
You can [**chroot**]("http://ubuntuforums.org/showthread.php?t=1156240") into your Ubuntu install with Ubuntu DVD/USB media. Then you can re-install the kernel if you think you may have messed with it.
[URL="https://help.ubuntu.com/community/BasicChroot"]https://help.ubuntu.com/community/BasicChroot
[/URL]
```
sudo apt-get update && sudo apt-get dist-upgrade
sudo apt-get install linux
```

Hopefully that should restore or fix your kernel...

You can also reinstall with Ubuntu Live media without losing your settings and data:
[http://askubuntu.com/questions/269880/re-install-ubuntu-without-losing-data-in-home-folder](http://askubuntu.com/questions/269880/re-install-ubuntu-without-losing-data-in-home-folder)

---

### Post by GarlicxSauce on 2014-04-20
I'll try the latter and see how it goes, thanks!

---

