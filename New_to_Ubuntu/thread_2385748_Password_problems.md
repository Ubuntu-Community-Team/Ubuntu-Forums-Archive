---
title: "Password problems"
date: 2018-02-24
forum: New to Ubuntu
---

### Post by dannyk2 on 2018-02-24
Hello everyone
I very recently bought a new desktop computer. The only problem was i didn't know how to install Ubuntu MATE 17.10.1 to the SSD drive. So my niece took the machine (i am disabled) along to PC World (Team Know How) to have the machine set-up along with Ubuntu MATE 17.10.1 installed on the SSD drive. When i had the machine back everything worked great that is until i tried to update the OS where i was asked for a passwork? I've tried everything that i can think of but nothing worked. I even opened a terminal and typed: passwd username. The only output i had was: password for username? Could someone help me out here please.

---

### Post by Impavidus on 2018-02-24
You have a personal password in Ubuntu, which you need for admin tasks and for login, unless passwordless login has been configured (which is apparently the case here). It's possible to reset the password. These two links tell basically the same stuff:
[https://help.ubuntu.com/community/LostPassword](https://help.ubuntu.com/community/LostPassword)
[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Some general information on running things with root privileges:
[URL="https://help.ubuntu.com/community/RootSudo"]https://help.ubuntu.com/community/RootSudo
[/URL]

---

### Post by dannyk2 on 2018-02-25
Hi Impavidus
Think i better tell you that the machine in question is a brand new Desktop computer with an i7 CPU.
And i have only just found out that i am dual-booting Ubuntu 17.10.1 and openSUSE Leap 42.3.

I have tried to access the boot-menu by pressing F2 at boot-up. I cannot find any mention of "Recovery mode".

Would it be any better if i did a fresh install of Ubuntu MATE 17.10.1?

The only problem with doing a fresh install is i don't know how to install an OS onto an SSD drive so would need a tutorial for that.

---

### Post by Impavidus on 2018-02-25
By pressing F2 you probably got into the UEFI menu. The grub menu would be the stage after that. You may be able to access it by pressing shift or escape. But with both Ubuntu and opensuse installed, I don't know which one is in control of the booting process.

Do you have a live usb (or dvd), like the one you can use to install Ubuntu? Run a live session and try [Boot-Repair](https://help.ubuntu.com/community/Boot-Repair). Try the second option: install Boot-Repair in Ubuntu. Then create a BootInfo summary and post the link you get here. That should give all details we need to fix this. Don't run the recommended repair yet, although it may do exactly what we need (i.e., make the grub menu visible).

---

