---
title: "Unknown password, unable to do a recovery"
date: 2013-10-27
forum: New to Ubuntu
---

### Post by artiomms on 2013-10-27
Hello!

I recently bought an AC100 Toshiba laptop. Out of the box ut runs Android; however there is a way to install ubuntu on it (but it is a bit tricky).
As I have no knowledge of ubuntu whatsoever, I bought a used one with Lubuntu preinstalled.

Now there's a problem: the previous owner has lost the root password, and thus I can't really do anything. It gets me to the admin account at once, but asks for the password when connecting to WiFi, updating the system etc.

I checked for information on how to reset this password, and read about how to get into recovery mode. 
But at startup, it seems impossible to get into grub. I tried holding shift, but it still goes straight into Lubuntu. Also, it seems I can't get into BIOS to boot via USB.
There is a way to get to Andoid recovery mode, but even when I choose to recover the Android OS, it loads Lubuntu!

It is like this: Press power button -->  Toshiba logo flashes for half a second --> some text starts appearing (I think it's loading lubuntu?) --> Lubuntu desktop.
 
There is info on how to make a new install, but since I know so little, I can't even follow the guide: [http://ac100.grandou.net/installing_linux](http://ac100.grandou.net/installing_linux)

Any help is much appreciated!

---

### Post by whitesmith on 2013-10-27
Your post causes my tired mind to reel. Keeping one thing at a time: Ubuntu, by design, comes with no root password. The preferred method of doing "rooty" things is to preface a command requiring root access with **sudo**, and then use your regular user password. Obviously this is cleaner and safer for less experienced users. Better as well for a net admin, since the root PW no longer has to be handed out. So, try this. Open a terminal (ctrl+alt+t) and type```
fdisk -l
``` Ubuntu should output nothing at all, just drop down to whatever prompt you are using. Now type ```
sudo fdisk -l
```Use your regular password. If you now have output, that is the correct PW to use with sudo. Post back your results and we can discuss your other issues then.

---

### Post by artiomms on 2013-10-28
> **whitesmith said:**
> Your post causes my tired mind to reel. Keeping one thing at a time: Ubuntu, by design, comes with no root password. The preferred method of doing "rooty" things is to preface a command requiring root access with **sudo**, and then use your regular user password. Obviously this is cleaner and safer for less experienced users. Better as well for a net admin, since the root PW no longer has to be handed out. So, try this. Open a terminal (ctrl+alt+t) and type```
fdisk -l
``` Ubuntu should output nothing at all, just drop down to whatever prompt you are using. Now type ```
sudo fdisk -l
```Use your regular password. If you now have output, that is the correct PW to use with sudo. Post back your results and we can discuss your other issues then.

The thing is, I have no "regular password". It automatically takes me to an account called "ubuntu", which the previous owner must have set up. I am able to log out and enter as guest, but that has no use, right?

When following your advice, after ```
sudo fdisk -l
``` it says ```
[sudo] password for ubuntu:
``` which I do not possess. Thank you for your advice, anyway!

---

### Post by Impavidus on 2013-10-29
It seems this is one of those locked-down devices manufacturers seem to love in this mobile era. If you don't like it the way it works out of the box you're in bad luck. It's very hard to change things.

To get into recovery mode you can try hitting shift repeatedly. This sometimes works better than holding shift. Also, try both shift keys. As it seems these netbooks with Ubuntu don't use grub but some kind of Android Fastboot, it may not work. If you can't get into recovery mode one would normally boot a live medium, but it seems these machines don't like live USBs and they may not have traditional bios menus, which really complicates matters. I found this page telling in some detail how to get a decent ubuntu on these machines: [https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100). It sounds far more complicated than installing on mainstream laptops.

Also, just a wild guess based on the fact Ubuntu is installed on these machines as an image (instead of from a live session) and the username is the same as in a live session, try a blank password. Just hit enter when it asks for one. Something else to try is using ubuntu as password. Yes, it's terribly insecure but it might work.

Once you get sudo working you can modify passwords and usernames to something easier and more secure.

---

### Post by artiomms on 2013-10-29
> **Impavidus said:**
> It seems this is one of those locked-down devices manufacturers seem to love in this mobile era. If you don't like it the way it works out of the box you're in bad luck. It's very hard to change things.

To get into recovery mode you can try hitting shift repeatedly. This sometimes works better than holding shift. Also, try both shift keys. As it seems these netbooks with Ubuntu don't use grub but some kind of Android Fastboot, it may not work. If you can't get into recovery mode one would normally boot a live medium, but it seems these machines don't like live USBs and they may not have traditional bios menus, which really complicates matters. I found this page telling in some detail how to get a decent ubuntu on these machines: [https://wiki.ubuntu.com/ARM/TEGRA/AC100](https://wiki.ubuntu.com/ARM/TEGRA/AC100). It sounds far more complicated than installing on mainstream laptops.

Also, just a wild guess based on the fact Ubuntu is installed on these machines as an image (instead of from a live session) and the username is the same as in a live session, try a blank password. Just hit enter when it asks for one. Something else to try is using ubuntu as password. Yes, it's terribly insecure but it might work.

Once you get sudo working you can modify passwords and usernames to something easier and more secure.

I have tried pressing shift at different times, repeatedly hitting shift etc. Nothing seem to work. 
Yes, I too, have seen the page, but since I have so little knowledge, it is too hard to follow the guide. It seemed easy at first glance, but was I wrong.. 
Good idea, but space does not work, neither does ubuntu. A reinstall would solve everything, it just seems so close to figure out the password, as all difficult steps to install ubuntu already are done..

---

### Post by jewisharific on 2013-10-29
Have you tried approaching the previous owner for the password?

---

### Post by DuckHook on 2013-10-30
> **jewisharific said:**
> Have you tried approaching the previous owner for the password?

> **artiomms said:**
> ...the previous owner has lost the root password

@OP

The instructions in the link provided by *Impavidus* are actually very clear--meaning that these instructions are not obscure, are step-by-step and will get you to your goal--but I can appreciate why they would overwhelm a non-technical user.

For my part, I can't really add anything except what the wiki has already laid out. Any help on this forum would also likely just be a repetition of what it already tells you to do. The good news is that it sounds like a do-able procedure which should give you a pristine installation with your very own password. The bad news is that it is complex and involved, and not for beginners or the faint of heart. In fact, it sounds very similar to the firmware replacement process that some of us use to turn simple $100 routers into the equivalent of $1000 commercial multifunction devices. And just like that process, this one sounds like it could also brick your gadget. You should be aware of this possibility before you proceed further.

Therefore, my suggestion is not a technical one, but a practical one: co-opt the services of your local geek (a six-pack of beer might do it), and ask him/her to perform the surgery for you. Be aware that s/he may brick your toy, but it's only half-usable to you now anyways.

---

### Post by jewisharific on 2013-10-30
I understand the previous owner lost the root password, but if you can get the user password, and that user is set up in the sudoers file, then you won't need the root password.

---

### Post by DuckHook on 2013-10-30
> **jewisharific said:**
> I understand the previous owner lost the root password, but if you can get the user password, and that user is set up in the sudoers file, then you won't need the root password.Yes, that would work.

@OP

Now that *jewisharific* has me thinking outside the box, another possible solution is to take out the HDD, mount it on another computer, *chroot* into it and either change the root password to whatever you like, or create a new user and add it to the *sudoers* group. Either method should give you a working account with root/sudo privileges.

---

