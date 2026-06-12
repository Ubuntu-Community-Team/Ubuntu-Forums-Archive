---
title: "How to stop PC from defaulting which dual OS starts, if user does not choose ?"
date: 2016-11-17
forum: New to Ubuntu
---

### Post by elvis6 on 2016-11-17
I have dual OS on my PC, and when it boots up or re-starts, it gives me the choice of Ubuntu or the other OS.
If I don't manually select one within about 10 seconds of that screen appearing, it automatically defaults to starting the other OS.

This however, is a problem in situations like this : due to the PC running slow, it takes a long time to close down and re-boot, 
and I get impatient with it, and walk away from the PC to take on another brief task, planning to walk back in time to choose the OS to start with.
But often-times, for various reasons, I cannot get back to the PC in time to manually make the choice, so it automatically defaults to the other OS,
against my wishes.

So is it possible to change the settings to either, or both of these options :

1) Have the PC stay put on the screen where it asks you to choose the OS you want to boot, and not to advance at all, if you do not respond.
or  
2) Have the PC default to Ubuntu, so if the user does not respond at all, to this prompt, it defaults to Ubuntu, rather than the other OS.

---

### Post by oldrocker99 on 2016-11-17
Here are detailed instructions for a boot defaulting to Ubuntu (or, for that matter, That Other OS):
[https://launchintolinux.wordpress.com/2013/03/09/how-to-change-the-default-os-in-an-ubuntu-dual-boot-setup/](https://launchintolinux.wordpress.com/2013/03/09/how-to-change-the-default-os-in-an-ubuntu-dual-boot-setup/)

Good luck!

---

### Post by elvis6 on 2016-11-17
> **oldrocker99 said:**
> Here are detailed instructions for a boot defaulting to Ubuntu (or, for that matter, That Other OS):
[https://launchintolinux.wordpress.com/2013/03/09/how-to-change-the-default-os-in-an-ubuntu-dual-boot-setup/](https://launchintolinux.wordpress.com/2013/03/09/how-to-change-the-default-os-in-an-ubuntu-dual-boot-setup/)

Good luck!

Thank you. I read and understand the concept of that tutorial. However, there seems to be some inconsistencies in the values that it refers to...
In Step #1, it states that "GRUB labels its lines starting with 0, so an OS that’s located on the fifth line would actually be 4".
Now, Ubuntu is the first on the list for me, so according to the above, it would be referred to as "0"

However, later in Step #2, it instructs that once you open the GRUB file, to change the value at the GRUB_DEFAULT setting, to the one you want.
However, the GRUB_DEFAULT setting already is set at "0", which theoretically according to the above, it should default to Ubuntu when re-booting.
But of course, it is defaulting to the other OS upon startup. So, it seems it's not truly defaulting to "0" on start-up, as the file instructs.

What am I missing ?

---

### Post by CantankRus on 2016-11-17
You can use the command **grub-reboot**.
> grub-reboot - set the default boot entry for GRUB, for the next boot **only**

Get your grub menu list...
```
grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' | nl --starting-line-number=0
```
eg my grub
```
[COLOR="#006400"]**glen@Xenial:~$**[/COLOR] grep menuentry /boot/grub/grub.cfg | grep "^menuentry" | sed -e 's/.*Memory test.*//g' -e "s/menuentry '//g" -e 's/ --class.*//g' -e "s/'//g" -e '/^$/d' | nl --starting-line-number=0
     0	Ubuntu
     1	Ubuntu 16.10 (16.10) (on /dev/sda3)
     2	elementary OS 0.4 Loki (0.4) (on /dev/sdb5)
     3	Ubuntu 16.04.1 LTS (16.04) (on /dev/sdc1)
     4	Ubuntu 16.04.1 LTS (16.04) (on /dev/sdc3)
     5	Ubuntu Xenial 16.04 ISO 
     6	Ubuntu Yakkety 16.10 ISO 
     7	Lubuntu 16.04 ISO 
     8	Ubuntu-Gnome 16.04 ISO 
     9	Xubuntu 16.04.1 ISO 
    10	Elementary 0.4 ISO 
```

If I want to boot into elemetary(#2) while I go make a coffee :P
I can use just the number or the complete menu entry.
```
sudo grub-reboot 2 [COLOR="#808080"]&& sudo reboot[/COLOR]

```
**[SIZE=3]or[/SIZE]**
(use quotes)
```
sudo grub-reboot "elementary OS 0.4 Loki (0.4) (on /dev/sdb5)" [COLOR="#808080"]&& sudo reboot[/COLOR]
```

grub-reboot sets the entry for next boot but does not actually perform a reboot so you add the [COLOR="#808080"]&& sudo reboot[/COLOR] command.
If you're not doing other OS installs using the number should be sufficient.

---

### Post by oldfred on 2016-11-17
Is this an UEFI system that is using UEFI defaults? Not grub?

---

### Post by Dennis N on 2016-11-18
> 1) Have the PC stay put on the screen where it asks you to choose the OS you want to boot, and not to advance at all, if you do not respond.

A simple way to make grub wait a longer time is to adjust the grub timeout in /etc/default/grub to a sufficiently large number. I have been setting
[FONT=Courier New]**GRUB_TIMEOUT=900**[/FONT]
which corresponds to 15 minutes, and allows me enough time to leave the computer and make a cup while it starts.

Be sure to run sudo update-grub after doing this to push this change to the actual menu.

---

### Post by SW54880 on 2017-01-06
> **Dennis N said:**
> A simple way to make grub wait a longer time is to adjust the grub timeout in /etc/default/grub to a sufficiently large number. I have been setting
[FONT=Courier New]**GRUB_TIMEOUT=900**[/FONT]
which corresponds to 15 minutes, and allows me enough time to leave the computer and make a cup while it starts.

Be sure to run sudo update-grub after doing this to push this change to the actual menu.

If you change
GRUB_TIMEOUT=900
to
GRUB_TIMEOUT=-1
grub will wait for you to select the os you want to boot.

---

### Post by eionmac on 2017-01-07
THANKS> SW54880 ,  I had forgotten the minus number   "-1" gave an infinite wait. Browsing tips re-leans lessons regards eionmac

---

### Post by elvis6 on 2017-01-26
> **Dennis N said:**
> A simple way to make grub wait a longer time is  to adjust the grub timeout in /etc/default/grub to a sufficiently large  number. I have been setting
[FONT=Courier New]**GRUB_TIMEOUT=900**[/FONT]
which corresponds to 15 minutes, and allows me enough time to leave the computer and make a cup while it starts.

Be sure to run sudo update-grub after doing this to push this change to the actual menu.

> **SW54880 said:**
> If you change
GRUB_TIMEOUT=900
to
GRUB_TIMEOUT=-1
grub will wait for you to select the os you want to boot.

When I make that change and update grub, I get the following error message "Warning: Setting GRUB_TIMEOUT to a non-zero value when GRUB_HIDDEN_TIMEOUT is set is no longer supported".

So, it's not working, when I make the above change.
However, the above message seems to ***imply*** that if I modify "GRUB_HIDDEN_TIMEOUT", it ***may*** work.
So, according to that message, if I "un-set" the above, will it then work ?
If so, how do I modify that line ? Currently my "GRUB_HIDDEN_TIMEOUT" equals 0.

---

### Post by sotiris2 on 2017-01-27
My defaults file also has a line > GRUB_HIDDEN_TIMEOUT_QUIET=true

If you also have that maybe try changing it to false ?

---

