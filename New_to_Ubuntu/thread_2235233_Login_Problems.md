---
title: "Login Problems"
date: 2014-07-19
forum: New to Ubuntu
---

### Post by tyron2 on 2014-07-19
Hi all, I installed ubuntu yesterday but I'm having trouble logging in. It keeps saying invalid password even though I'm 100% sure both the username and password are correct. I looked at videos online that suggested holding down the left shift key during the boot process which would lead to a menu and following several steps would allow me to change the password. I tried holding down the left shift key at different stages during the boot process but I couldn't get the timing right and I couldn't access the menu that would allow me to change the password. So instead I uninstalled and reinstalled ubuntu 3 times and on the final reinstallation I set the username to "a" and the password to "a" but when I rebooted and tried to log in using this username and password it still says the password is invalid, even though it can't be. Please help!

---

### Post by whitesmith on 2014-07-19
The minimum password length with Ubuntu is 6 characters, so the system would never have accepted "a" as a password -- and would have advised you that your choice is invalid. Where, in the installation process, are you entering a password? What other info is it asking for?

---

### Post by sammiev on 2014-07-19
You can try [this]("https://help.ubuntu.com/community/LostPassword").

---

### Post by yancek on 2014-07-19
Which release of Ubuntu are you using.  People will probably assume 14.04 so if it's not, indicate so?
How did you install?  DVD or flash drive?  Did you check the integrity of the downloaded Ubuntu iso before installing?  Could you post some info on your hardware, how old/new is this computer.

---

### Post by tyron2 on 2014-07-20
It's ubuntu 12.04 and I've got a dell inspiron N5050. I downloaded a setup wizard from wubi and it installed ubuntu on my laptop.  I've attached a jpg with a screenshot of the info the wizard asks for prior to installation. It had no problem accepting a one letter password.

---

### Post by tyron2 on 2014-07-20
Problem's sorted now, tried a different installation method using the cd. Works a treat, thanks for the help!

---

### Post by John_Beck on 2014-08-07
Tyron2 -

Having the same issue - what was the different install method?  Was that an option presented by the Wubi download page?

---

### Post by whitesmith on 2014-08-07
> **John_Beck said:**
> Tyron2 -

Having the same issue - what was the different install method?  Was that an option presented by the Wubi download page?

You should be aware that Wubi is no longer supported.

---

