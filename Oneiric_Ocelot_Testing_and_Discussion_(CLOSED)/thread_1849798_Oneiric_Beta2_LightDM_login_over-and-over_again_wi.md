---
title: "Oneiric Beta2 LightDM login over-and-over again with correct password"
date: 2011-09-25
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by Arie Baars on 2011-09-25
Hi there, just started to update my Natty to Oneric Beta phase.

My problem is:

Cannot get passed the Oneric LightDM login screen with the correct user-password combination. After entering the screen goes into something else (black screen with startup messages, and then a mouse-pointer), and returning to the same login screen, without any messages. These steps continue over-and-over again, and I'm stuck for now. 

There is also a "Guest" account (with no password) which starts OK and presents the new desktop. Then the sudo command do not work anymore with the correct passwords.

- Tried to reset the root and user passwords with a LIVE-CD, no effect
- /var/log/auth.log shows pam_unix(lightdm:auth) getting password / could not retrieve user's password / check pass: user unknown etc.

Some background:
Running on a Asus 1000H EeePC with seperate partitions, update a clone-copy of a working Natty version to the latest Oneric (Beta2). Changes the UUID and fstab to complete a working clone.
The upgraded with "update-manager -d", presenting the available 11.10 version, and after a while the update looks OK, and boots up with no specific errors.

---

### Post by tista on 2011-09-25
> **Arie Baars said:**
> Hi there, just started to update my Natty to Oneric Beta phase.

My problem is:

Cannot get passed the Oneric LightDM login screen with the correct user-password combination. After entering the screen goes into something else (black screen with startup messages, and then a mouse-pointer), and returning to the same login screen, without any messages. These steps continue over-and-over again, and I'm stuck for now. 

There is also a "Guest" account (with no password) which starts OK and presents the new desktop. Then the sudo command do not work anymore with the correct passwords.

- Tried to reset the root and user passwords with a LIVE-CD, no effect
- /var/log/auth.log shows pam_unix(lightdm:auth) getting password / could not retrieve user's password / check pass: user unknown etc.

Some background:
Running on a Asus 1000H EeePC with seperate partitions, update a clone-copy of a working Natty version to the latest Oneric (Beta2). Changes the UUID and fstab to complete a working clone.
The upgraded with "update-manager -d", presenting the available 11.10 version, and after a while the update looks OK, and boots up with no specific errors.

@Arie Baars,

Could you login into VT from recovery boot?
and then, after login as root, could you change your accounts password on VT?

cheers.

---

### Post by elllit06 on 2011-09-25
Hello,

I just had the same issue. I couldn't for the live of me log in.  Then, when I changed into the console, I wanted to see what happens  when I type my password. And voila: Wrong characters. Well, not entirely  wrong, but characters as if its an **English (US, i guess) keyboard  layout**, instead of German as expected.

So, maybe this solves your issue as well: Try to type your password as if you have an English keyboard layout.

Bye

**EDIT**: After the first login it is back to "normal"!

**EDIT2**: Ok, I was a little too euphoric, when I realized that I could use the German layout within Unity (lock-screen, terminal, ...). But actually the English layout still persist, when restarting LightDM. Although, after the login the correct layout is used within Unity.

---

### Post by Arie Baars on 2011-09-25
Just tried several options
- can login into recovery menu with "normal" root password
- change the root and/or user password to new values (with passwd) does not resolve, no problems with that one
- checked password by typing literally on command line, no issues
- second login on LightDM still the same, enter user's password, part of boot screen, arrow waiting for ..., and login again.

---

### Post by tista on 2011-09-25
> **Arie Baars said:**
> Just tried several options
- can login into recovery menu with "normal" root password
- change the root and/or user password to new values (with passwd) does not resolve, no problems with that one
- checked password by typing literally on command line, no issues
- second login on LightDM still the same, enter user's password, part of boot screen, arrow waiting for ..., and login again.

OK...

So could you change the DM from lightdm to gdm?
```
sudo apt-get install --reinstall gdm
```
and then installer shows up the prompt to change default display manager... so select gdm and soon installation would be finished.
finally restart your machine, if successfully finished, gdm login screen would come up after plymouth splash...

After all, if you could login on your account via gdm, then check your account setting and reinstall (switch to) lightdm, OK? usually lightdm would be come with prompt from "sudo dpkg-reconfigure lightdm" again...

Today lightdm seems to have some bug about passwords:
[https://bugs.launchpad.net/ubuntu/oneiric/+source/lightdm/+bug/821771]("https://bugs.launchpad.net/ubuntu/oneiric/+source/lightdm/+bug/821771")
and this fix is now only for workaround... :sad:

please give it a try!

cheers.

---

### Post by Arie Baars on 2011-09-26
Changed to GDM in stead of LightDM with sudo apt-get install --reinstall gdm. After the reboot there is no login screen anymore, only a part of the bootup messages. So no solution for now ;-)
Changed back to LightDM, old problem persists again.

---

### Post by Harry33 on 2011-09-26
> **Arie Baars said:**
> Changed to GDM in stead of LightDM with sudo apt-get install --reinstall gdm. After the reboot there is no login screen anymore, only a part of the bootup messages. So no solution for now ;-)
Changed back to LightDM, old problem persists again.

You have to reconfigure your system to use GDM first.

```

sudo dpkg-reconfigure gdm

```

---

### Post by Arie Baars on 2011-09-26
Also done "sudo dpkg-reconfigure gdm", same result with boot messages (last one Starting TiMidity++ ALSA midi).

---

### Post by effenberg0x0 on 2011-09-26
Wild guessing (might be VGA drivers, compiz, unity related - but I have a feeling I am right about this): 

```

sudo mv ~/.Xauthority ~/.Xauthority.old
sudo service lightdm restart

```

Effenberg

---

### Post by jbicha on 2011-09-26
As was mentioned in comment 3, I believe the problem is that the keyboard layout used for install is not set as default for lightdm for first reboot. See bugs [831026]("http://pad.lv/831026") ,  [834487]("http://pad.lv/834487") and [856461]("http://pad.lv/856461").

---

### Post by effenberg0x0 on 2011-09-26
> **jbicha said:**
> As was mentioned in comment 3, I believe the problem is that the keyboard layout used for install is not set as default for lightdm for first reboot. See bugs [831026]("http://pad.lv/831026") ,  [834487]("http://pad.lv/834487") and [856461]("http://pad.lv/856461").

Hey jbicha, you're most likely correct. I ran quickly through the thread and was under the wrong impression that he had ruled that out, which is why I guessed on "wrong .Xauthority after update" (that does produce an endless lightdm loop, seen it myself today again). 

Thanks,
Effenberg

---

### Post by Arie Baars on 2011-09-27
> **effenberg0x0 said:**
> Wild guessing (might be VGA drivers, compiz, unity related - but I have a feeling I am right about this): 

```

sudo mv ~/.Xauthority ~/.Xauthority.old
sudo service lightdm restart

```

Effenberg

Whoowh that did the trick, thanks!
Just the beautifull dash layout I was expecting, great :p

---

