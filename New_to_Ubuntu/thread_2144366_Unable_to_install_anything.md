---
title: "Unable to install anything"
date: 2013-05-11
forum: New to Ubuntu
---

### Post by moronninja on 2013-05-11
So, I used the windows installer to make a dualboot. My wireless card is not supported by linux, so i have to use NDISwrapper to install the drivers. but i can't install it because i have no internet connection. I also can't see some of the screen because i have a weird sized monitor and I need an internet connection to get my Nvidia drivers onto Ubuntu. I am unable to install anything because the install button is greyed out when i use software center, and I have not found a terminal solution yet.
Someone please help me, this is very frustrating!!!
I am using Ubuntu 12.04 lts

---

### Post by UltimateCat on 2013-05-11
If indeed your wireless card is not supported by linux and you do not have a internet connection this may be almost impossible my friend.
 I am not a Moderator and do not have the knowledge they posses for this kind of work-around.

I will share with you what (might help) otherwise as I said I am not a Moderator or Linux Guru-

Installing 'wireless tools' may help. Use a friend or neighbors computer, put this package on a usb memory stick and take it to your machine with Ubuntu 12.04 installed on it and use 'dpkg -i' to install it-- Re-start your computer. 
[https://help.ubuntu.com/community/WifiDocs/WiFiHowTo](https://help.ubuntu.com/community/WifiDocs/WiFiHowTo)

The only other thing I can think of is to try a wired cable if you have one. Or if this machine is a Desktop PC you could purchase a newer Network Interface Card and Ubuntu should see it w/o any issue's and start up your wireless right away.

You said that the install button in your Software Center is greyed out...I'm not the expert here but I don't think that that should be so-

---

### Post by Sam Mills on 2013-05-11
Is there any way you could move the computer near the modem or run a wire to the computer?

---

### Post by sathyastorm on 2013-05-11
what modem are you using

---

### Post by nsync on 2013-05-12
you could temporarily use a dial-up modem and install what you need, if you have one.

---

### Post by ibjsb4 on 2013-05-12
[Keryx]("http://ubuntuguide.net/update-ubuntu-off-line-via-another-windowslinux-pc-using-keryx")

---

