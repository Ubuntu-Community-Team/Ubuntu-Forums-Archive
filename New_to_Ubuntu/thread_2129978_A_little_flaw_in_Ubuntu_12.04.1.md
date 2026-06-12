---
title: "A little flaw? in Ubuntu 12.04.1"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by amhndu on 2013-03-27
Before anything , I must say that I am an absolute beginner regarding Ubuntu & Linux .I recently switched to Ubuntu from M$ Windows.Ubuntu is very smooth , but I found a little flaw when an application is full screen.I was checking my SFML 2.0 [en.sfml-dev.org]("http://en.sfml-dev.org") build by writing a simple program in C++ that goes full screen and closes on a close request ( [x] button ) or a keyboard shortcut ,when it wasn't full screen it worked fine,but after going full screen there was no way out, I tried Alt + F4 , Ctrl + W, Alt + Tab, Super key, even Ctrl + Alt + Del to log out,Alt + F2 to run xkill but I was stuck, I had to do a cold reboot. When i amended the code to exit on Esc key press, It worked though.The problem is when it goes full screen , unless the app wants to exit you are stuck shouldn't ubuntu had responded to my calls or what i should have done in such a case, in windows pressing Ctrl + F4 or opening task manager all worked.BTW what else can I do to troubleshoot when ubuntu is non responsive. Amish

---

### Post by ManamiVixen on 2013-03-27
If you are running 12.04.1, do "sudo apt-get update && sudo apt-get dist-upgrade" to upgrade to 12.04.2 and see if that helps.

---

### Post by amhndu on 2013-03-27
I'll update as soon as I'll have fast Internet Connection
Thanks for the reply.

---

### Post by Impavidus on 2013-03-28
Those combinations like ctrl+w, ctrl+q etc. are program specific (and therefore not always the same), so they don't work automatically. I always make sure I've programmed a key for exiting a program before I add the functionality to go full screen. And before you do a cold reboot, try alt+SysRq+REISUB. This causes a reboot without the risk of file system corruption.

---

### Post by amhndu on 2013-03-28
Ok , i'll use that SysReq combination in such adversity but what about the shortcuts defined by ubuntu like alt + f4 ,if an application is not responding in fullscreen mode then how to regain access to desktop as no I cant simply kill it with say xkill.

---

