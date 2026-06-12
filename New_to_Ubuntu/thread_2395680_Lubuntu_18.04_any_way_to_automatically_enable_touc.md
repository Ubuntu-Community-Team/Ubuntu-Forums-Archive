---
title: "Lubuntu 18.04 any way to automatically enable touchpad?"
date: 2018-07-05
forum: New to Ubuntu
---

### Post by plizmon on 2018-07-05
Hello there, VERY new linux user here, and new to the forum. Please forgive me - I wasn't sure where to post this.
I have just downloaded Lubuntu 18.04 onto an Acer Aspire One netbook. It all seems to be working fine, but each time I start it up, it starts with the touchpad disabled. I can enable it by using 'Fn + F7', but I have to do this every time I start up. Is there any way of making this change permanent (or making it happen automatically on start up)?
Please assume I don't know how *anything* works, or where anything is (I know how to open LXTerminal, and that's about it!) - I'm pretty confident with Windows but Linux is a whole new game to me!
Thanks in advance for any assistance

---

### Post by TheFu on 2018-07-07
[https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en](https://help.ubuntu.com/stable/ubuntu-help/startup-applications.html.en)   Just setup a macro to press those keys after login. **xdotool** is a common tool for that.  **xdotool key --clearmodifiers A-F7** will cause {alt}-F7 to be pressed.  I don't know how to press a non-standard key like Fn, sorry. [https://askubuntu.com/questions/854568/cant-assign-a-command-for-fn-key](https://askubuntu.com/questions/854568/cant-assign-a-command-for-fn-key) says Fn is a hardware key and not controlled by the OS.

[https://help.ubuntu.com/stable/ubuntu-help/index.html.en](https://help.ubuntu.com/stable/ubuntu-help/index.html.en)

A touchpad not working at boot could be any number of problems, but I'm thinking it is most likely a BIOS setting.  I definitely could be wrong.

Warning: The way that Windows does things isn't usually helpful towards understanding Linux. From the ground up, Unix is a completely different animal than Windows.  But skills learned on Unix/Linux without the GUI transfer to every other popular OS, including Windows. There are many things in Windows which work in the Unix-way, but average Windows users don't know and don't use those aspects.  90% of the power for Unix/Linux comes from outside the GUI.

---

### Post by plizmon on 2018-07-11
Thanks TheFu, at least I won't spend a lot of time looking for an answer that doesn't exist!

---

