---
title: "[SOLVED] Can't capture mouse in Virtualbox"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by Charlie Chick on 2008-10-19
Hello Everybody,

I've just installed Windoze XP in Virtualbox. The installation went well but I can't capture the mouse in XP. I keep on clicking the 'capture' box, but it simply doesn't work. Can anybody shed some light on what I'm doing wrong, please?

Many thanks.

Charlie

---

### Post by SabreWolfy on 2008-10-19
Not sure if it is directly related, but you could try installing the Guest Additions to see if that helps. The default hotkey for VirtualBox is the right control key -- try pressing that to see if it does anything.

---

### Post by bumanie on 2008-10-19
I had the same issue some time ago. I have not managed to have a mouse capture in a vbox release past 1.54 version - I have therefore stuck with that version. I have not used every updated version, but the couple I tried, I could not capture the mouse pointer. You may have to find an older version to use. I did send a bug report, at the time, but didn't hear anything of it.

---

### Post by SabreWolfy on 2008-10-19
Mouse capture has always "just worked" for me. Immediately after creating the machine, I have to click inside it first to capture the mouse, but after installing the Guest Additions, I no longer need to click to capture. The mouse moves seamlessly between Ubuntu and W*ndows and I just select what I want in W*ndows.

---

### Post by Charlie Chick on 2008-10-19
Thank you all for your contributions. I read about Guest additions on the Virtualbox website but nowhere does it say where I download it from and how to install it.

I need to add that I'm using ver 1.5.6 and that the keyboard works just fine.

---

### Post by Jim_in_Germany on 2008-10-19
To install guest additions, click on the devices button at the top of the Virtual Box Window and then on "Install Guest additions".
This will integrate the .iso image of the Guest additions into your virtual PC. You can then access it as if it were a CD under "My Computer -> D:"

In fact, I just checked this on my Windows XP Virtual Box instalation and it is enough to just select "Install Guest Additions". Then (as long as you don't have XP configured otherwise) the installation dialogue for the Guest Additions starts automatically.

---

### Post by Charlie Chick on 2008-10-19
Jim, thanks for the suggestion. Unfortunately, it didn't work. As I'm running version 1.5.6 and the latest version is 2.0.2, I'm going to install the latest version and see if it makes any difference.

---

### Post by Jim_in_Germany on 2008-10-19
Before you do that, do you have the option "Install guest additions" listed when you click the "Devices" button on your guest OS?
I'm also running 1.5.6 and it works for me.

If you decide to upgrade anyway, here is a good tutorial for installing / configuring Virtual Box on Hardy 8.04
[http://ubuntuforums.org/showthread.php?t=770745]("http://ubuntuforums.org/showthread.php?t=770745")

Edit: Or do you mean that installing the guest additions didn't help?

---

### Post by Charlie Chick on 2008-10-20
Jim, unfortunately the installation of guest additions hung and I was forced to shut Windoze down via the keyboard. 

I eventually solved the problem by uninstalling the old version (1.5.6) and then installing the new version (2.0.2). This allowed me to install the guest additions without problem and I now have a full working copy of Windoze on my computer.

Thank you to all for your help.

---

