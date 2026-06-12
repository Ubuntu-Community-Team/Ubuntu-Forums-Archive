---
title: "Ubuntu 14.04LS installed on Compaq SR1220NX, slow GUI"
date: 2014-05-29
forum: New to Ubuntu
---

### Post by twalp on 2014-05-29
Prepping old 2.93Ghz Celeron PC for relatives. After upgrading to 2GB of memory and installing a new 7200rpm HDD, I installed Windows 7 Home Premium and it works quite smoothly. 

One user at intended recipient's home tends to corrupt Windows systems so I figured I'd try Linux for my first time. Chose Ubuntu after reading article at Howtogeek.

First installed 14.04Ls 64-bit in VMWare Player on my personal i7 PC as a dry run. Impressive results but then my 32GB system is running Windows 8.1 on an SSD.

Installed 32-bit 14.04LTS on thumbdrive, then booted the Compaq SR1220NX from it.  Experienced first disappointment. Typing password or any text is SLOW: type 8 characters and wait almost 8 seconds for them to appear. Mouse left-clicking similar. Opening and closing a Window takes several seconds as it slowly fades in or out.  I figured this was caused by USB 2 so I installed the OS in dual-boot mode.

After installing ~250MB updates it runs a little better but still keyboard and display much like they did when run from a thumbdrive. We're talking molasses-in-Winter keyboard and display behavior. Firefox seems to run okay once it's open, searches return relatively quickly, but window opens/closes with long fade in/out.

FYI, the SR1220NX uses an Intel 845GV chipset, Celeron 2.93Ghz CPU. 2GB memory installed.

Note that "About this PC" lists for "Graphics:" "Gallium 0.4 on llvmpipe (LVM 3.4, 128bits)" whereas going through "Systems Settings | Details" the "Graphics:" shows "Intel 846G x86/MMX/SSE2". That's the only seeming inconsistency I've found, other details listed are identical and match physical system.

What's best advice given my overarching goal of providing non-Windows word processor and browser to one goofus in family? Please remember my newbness if you're going to suggest driver changes or troubleshooting.

---

### Post by QIII on 2014-05-29
Hello!

Unity, the default Ubuntu Desktop Environment (DE), may not fit in the "revives old hardware" category.

You might be better off using Xubuntu or Lubuntu, which have much lighter DEs than Ubuntu's Unity.

As for guarding against a user corrupting the system -- don't think you'll be helping there.  It is very easy to get into much greater trouble more quickly with a Linux machine than even with Windows.  Linux assumes you know exactly what you are doing and it will do exactly what you tell it to without asking if you are sure.  You can actually remove critical system files without warning if you want to.

To avoid this, the user in question would have to be excluded from the sudoers list (not be an Administrator in Windows terms), which would limit the user's ability to do some things that might be useful -- such as installing some software or updating the system.

---

### Post by twalp on 2014-05-29
> **QIII said:**
> Hello!

Unity, the default Ubuntu Desktop Environment (DE), may not fit in the "revives old hardware" category.

You might be better off using Xubuntu or Lubuntu, which have much lighter DEs than Ubuntu's Unity.

As for guarding against a user corrupting the system -- don't think you'll be helping there.  It is very easy to get into much greater trouble more quickly with a Linux machine than even with Windows.  Linux assumes you know exactly what you are doing and it will do exactly what you tell it to without asking if you are sure.  You can actually remove critical system files without warning if you want to.

To avoid this, the user in question would have to be excluded from the sudoers list (not be an Administrator in Windows terms), which would limit the user's ability to do some things that might be useful -- such as installing some software or updating the system.


Thank you for replying, QIII.  I may try one of your suggested distributions if I can determine that its installation won't destroy the existing Windows 7 *and* there's a way to dual-boot to it or W7.

Insofar as the "user corrupting the system" I'm referring more to getting it infected by malware, or a drive-by attack. Is a user of Linux potential prey to malicious social engineering as he is with Windows?

Would you mind telling me how to exclude a user from the sudoers list, if it's not too complicated?

---

### Post by sudodus on 2014-05-29
I think the main risk factor in on your side of the keyboard. Browsing habits make a big difference. Linux is not vulnerable to Windows specific malware, but there are many attacks, that do not depend on the operating system. There are also (not many, but anyway) linux specific malware.

See this link [https://wiki.ubuntu.com/BasicSecurity](https://wiki.ubuntu.com/BasicSecurity)

---

### Post by sudodus on 2014-05-29
> **trwilde said:**
> Would you mind telling me how to exclude a user from the sudoers list, if it's not too complicated?

Create a normal desktop user (without administrator privileges). You should keep one account with administrator privileges to be able to do system work but you can keep its password secret for the risky users.

---

### Post by twalp on 2014-05-29
Thank you Sudodus for your advice!

I live booted Lubuntu and it worked beautifully on the SR1220NX. Thank you QIII for the tip.  What an amazing difference in speed! (I realize that the hardware was the limiting factor, but this experience illustrates how much much less demanding Lubuntu's DE must be.)

---

### Post by twalp on 2014-06-11
> **sudodus said:**
> Create a normal desktop user (without administrator privileges). You should keep one account with administrator privileges to be able to do system work but you can keep its password secret for the risky users.

I created a "normal desktop user" but cannot figure out how to make the system automatically login as that user instead of the original admin user that was created during Lubuntu installation. I figure I can keep the latter for admin work on the system, but I don't want the system booting into the original admin user.

---

### Post by sudodus on 2014-06-11
You can use the ```
users-admin
``` graphical user interface and change the admin account 

from
Password: Not asked on login

to 
Password: Asked on login

and then you have the option to make it log in automatically into the "normal desktop user" (Password: Not asked on login) if you wish.

---

### Post by twalp on 2014-06-12
> **sudodus said:**
> You can use the ```
users-admin
``` graphical user interface and change the admin account 

from
Password: Not asked on login

to 
Password: Asked on login

and then you have the option to make it log in automatically into the "normal desktop user" (Password: Not asked on login) if you wish.

Thank you, sudodus, for replying.  When I installed **Lubuntu **the user I created was named "Jack" and assigned him a password, as required.  Knowing that this user has admin rights I went to System Tools | Users and Groups. I noticed that Jack had "Account Type: **Custom**" and "Password: **Asked on Login**". That struck me as odd because the system boots to the Desktop without asking Jack to login. Being a rank noob I just accepted this as something I don't understand yet.

Per your suggestion I added a user named "Jill" and set "Password: **Not asked on login**". I figured that with Jack set to "**Asked on login**" and Jill set to "**Not asked on login**", the system would boot directly into her account after reboot. But, instead, it still boots directly into Jack's account.  What am I missing?

BTW, I noticed you suggested using "users-admin" to get to the same control panel that I used. Is there an easier way to open users-admin than navigating to Accessories and running LXTerminal? There must be because that seems less direct than "System Tools | Users and Groups".

---

### Post by sudodus on 2014-06-13
It seems to me, that your system does not take the input via users-admin alias "System Tools | Users and Groups" into account. I don't know why, I have used that method several times.

Read the whole text of this link (don't rush and do something that might cause problems later on)

[http://askubuntu.com/questions/281074/can-i-set-my-user-account-to-have-no-password](http://askubuntu.com/questions/281074/can-i-set-my-user-account-to-have-no-password)

Maybe this link will help you

[http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm](http://askubuntu.com/questions/100010/no-password-asked-at-login-screen-just-start-session-button-with-lightdm)

and you find a lot more, when you browse the internet for ***ubuntu login without password***

---

