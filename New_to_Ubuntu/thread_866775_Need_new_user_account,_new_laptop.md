---
title: "Need new user account, new laptop"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by buffalochick on 2008-07-22
I just got the laptop, excellent little machine, but its main boot O/S is ubuntu. Want to play, get to know it, but can't sign on. Can I make a new user, hijack this one... Or change the order in which the laptop boots to do xp first? Ubuntu is default and I can't log in. Seller on vacation... Any help is appreciated.

---

### Post by Sef on 2008-07-22
> Ubuntu is default and I can't log in. Seller on vacation... Any help is appreciated.

So you bought the laptop, and you are unable to sign in, correct?

If so, then read this post on how to [reset the password]("http://www.psychocats.net/ubuntu/resetpassword").

---

### Post by sailor2001 on 2008-07-22
to reset boot order, count down listings when you boot up and remember the number, starting with 0 for ubuntu until you get to the xp boot loader (maybe 4?) and then in our ubuntu terminal (applications/accessories) type in: gksudo gedit /boot/grub/menu.lst  and change the default boot number to our xp bootloader number. click save and exit

---

### Post by Vadi on 2008-07-22
I'd recommend using a graphical program such as [StartUp-Manager]("apt:startupmanager") after you got access to the boot machine to manage the boot order. It's much more intuitive and less chances of you messing up by accident.

---

