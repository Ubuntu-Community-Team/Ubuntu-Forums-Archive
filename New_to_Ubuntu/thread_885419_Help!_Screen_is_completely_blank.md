---
title: "Help! Screen is completely blank"
date: 2008-08-10
forum: New to Ubuntu
---

### Post by Jidderstein on 2008-08-10
I had everything working fine a little while ago, installed the drivers for my ATI graphics card with envy and it worked great. However, just out of curiosity i opened the list of restricted drivers currently being used (can't describe in detail because i can't see my system any more, this is from memory) and ticked the box saying "enable" next to some ATI graphics related driver. I applied the settings and restarted my computer to see what would happen.

When it finished booting, the screen was completely blank, i couldn't see my desktop at all. The monitor was lit up and turned on, everything is plugged in, but its just black. I tried booting in safe mode and attempting to fix X server to no avail. I tried rebooting a few more times to access my desktop but after booting in safe mode, the screen is now plain white, still no desktop. I booted into windows to make this thread and everything works fine here. How can i undo this horrible mistake when I can't see anything? Please help!

---

### Post by cdtech on 2008-08-10
When you were in the recovery terminal what command did you use? Did you use:
```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Jidderstein on 2008-08-10
I am using Linux Mint, which is Ubuntu based so i use these forums for support. It might be different though, because when i booted in recovery mode there was an option i scrolled down to that said "attempt to fix X server". That's all i did so far.

---

### Post by Jidderstein on 2008-08-10
I tried again a minute ago to access the command line from recovery mode to try the command that was suggested. I selected "drop to root prompt" or something like that, and it asked for my password. I typed it in my normal password that has always worked for everything on my linux system, and its giving me an incorrect login error. Am I just screwed up beyond repair now or what?

---

### Post by neoplasme on 2008-08-16
Same thing happen to me...don't know how to fix it sorry but only to say try to uninstall the driver. has for the login your keybord is now probably in azerty mode. I don't know why it happened to me to! so try to find what key means what. ex. q is a etc...

---

