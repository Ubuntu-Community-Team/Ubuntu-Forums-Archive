---
title: "Time and Date Settings - NTP"
date: 2008-09-06
forum: New to Ubuntu
---

### Post by edwardp on 2008-09-06
Just installed Xubuntu 8.04.1 and there appears to be a problem with the Time and Date Settings.

When I selected to use the time server, a window appeared that NTP support was not installed and I chose to install it.

The NTP package was then downloaded and installed.  

However, when I attempt to change that pull down item from Manual to use the time server, the window to install NTP appears again and it keeps appearing each time I try to change that menu item, even after NTP was already installed.  It then defaults back to Manual each time.

:confused:

---

### Post by fballem on 2008-09-06
> **edwardp said:**
> Just installed Xubuntu 8.04.1 and there appears to be a problem with the Time and Date Settings.

When I selected to use the time server, a window appeared that NTP support was not installed and I chose to install it.

The NTP package was then downloaded and installed.  

However, when I attempt to change that pull down item from Manual to use the time server, the window to install NTP appears again and it keeps appearing each time I try to change that menu item, even after NTP was already installed.  It then defaults back to Manual each time.

:confused:

Ran into this myself on ubuntu. As far as I can tell, the NTP server synch is installed. If you haven't already done so, please reboot your machine. Once you're back in, please right click on the time display and check the settings. On mine, it now shows that it is being synchronised.

Hope this helps,

---

### Post by edwardp on 2008-09-07
The XFCE clock does not show anything like that when the clock is right-clicked.  The only options are to show the type of clock (analog, digital, LCD), whether to use 12 or 24 hours and whether to show seconds.

Even after a reboot, the Time/Date settings still prompts to install NTP support.  I still do not know whether the clock is syncing with a time server.  

In /etc there is an ntp.conf file showing ntp.ubuntu.com as the time server.

Because the system is so slow, I'm tempted not to even bother with it anymore.

---

### Post by fballem on 2008-09-07
> **edwardp said:**
> The XFCE clock does not show anything like that when the clock is right-clicked.  The only options are to show the type of clock (analog, digital, LCD), whether to use 12 or 24 hours and whether to show seconds.

Even after a reboot, the Time/Date settings still prompts to install NTP support.  I still do not know whether the clock is syncing with a time server.  

In /etc there is an ntp.conf file showing ntp.ubuntu.com as the time server.

Because the system is so slow, I'm tempted not to even bother with it anymore.

Sorry, I don't run XFCE. What I was looking for was an option that would allow you to Adjust Date and Time Settings. I've attached a screenshot. In the screen shown, you would select Unlock (at which point you get asked for your password) then make the change. After you do this, and save the change, you will need to restart your computer.

---

### Post by edwardp on 2009-11-08
The system that I had this problem on, no longer functions (BIOS failed), but the clock is working perfectly on my other desktop running Xubuntu 9.10.  :D

---

