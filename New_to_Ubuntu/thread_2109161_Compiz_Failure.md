---
title: "Compiz Failure"
date: 2013-01-26
forum: New to Ubuntu
---

### Post by Dagwood on 2013-01-26
Hello
I've recently installed 12.10 onto an old HP-Compac d530 machine. This install went okay, however all I have is a hazy violet screen without any desktop icons. I will get an error message "The Application Compiz Has Closed Unexpectantly". Trying to re-launch it or shut down does nothing. I believe I need to switch the driver from 3D to 2D support.
Can anyone walk me through the steps I need to take to get my machine working. Is there a "safe mode" at boot up that would allow me to disable Compiz? Any advice you can pass my way would be very much appreciated.:)

---

### Post by elgordodude on 2013-01-26
Compiz in 12.10 has been a little intense on legacy hardware. Disabling 3D hasn't helped in my experience but you can change the desktop environment by clicking on the little ubuntu icon in the login box at boot.

If that doesn't help you can install GNOME and that should work fine. First drop out of compiz with Ctrl+Alt+F1 then run ```
sudo apt-get install gnome-panel
``` then reboot, at login click the ubuntu icon and select GNOME. Note that gnome won't start until the **next** time you log in as it needs to start when ubuntu does. Good luck!

---

### Post by Dagwood on 2013-01-28
> **elgordodude said:**
> Compiz in 12.10 has been a little intense on legacy hardware. Disabling 3D hasn't helped in my experience but you can change the desktop environment by clicking on the little ubuntu icon in the login box at boot.

If that doesn't help you can install GNOME and that should work fine. First drop out of compiz with Ctrl+Alt+F1 then run ```
sudo apt-get install gnome-panel
``` then reboot, at login click the ubuntu icon and select GNOME. Note that gnome won't start until the **next** time you log in as it needs to start when ubuntu does. Good luck!

Thanks for the response. I seem to be able to get to the desktop without a problem, however none of the icons appear on the left hand side nor does the "system" bar at the top. Is this because "Compiz" isn't starting or is it something else. BTW I haven't tried disabling Compiz yet.

---

### Post by DanaLG on 2013-01-28
I am having the exact same problem. I get ton the login screen, but have no icons next to the usernames to click on. The ubuntu logo in the top left, or bottom left are not clickable. When I log in I get a blank desktop, it has a nicely colored background but I have no icons what so even.

I am using the Windows downloader and I am running it on an older DELL, but it is within the specification of ubuntu. I have deleted and re-installed ubuntu 4 times and and I keep getting the same thing.

One time while on the blank desktop I got a message that my ubuntu needed to be updated. I ran though the update process, in hopes that it would fix the problem. When It was done it prompted me to reboot. I did and got the exact same result.

The only error message I ever get is that the Compiz has crashed.

---

### Post by Frogs Hair on 2013-01-28
If you have terminal access (Ctrl + Alt +T ) try the following . _12.10 Only_

The dconf-tools are needed for the next command and are recommended for installation  ```
sudo apt-get install dconf-tools
```
Reset Compiz ```
dconf reset -f /org/compiz/
``` Reset Unity ```
setsid unity
```

If the terminal does not open you can enter the commands in TTY using Ctrl + Alt + F1 and use Ctrl + Alt + F7 to return to the desktop environment.

---

### Post by Dagwood on 2013-01-28
Thank you. 
Was able to switch to Gnome.

---

