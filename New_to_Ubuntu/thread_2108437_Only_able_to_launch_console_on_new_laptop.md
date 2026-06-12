---
title: "Only able to launch console on new laptop"
date: 2013-01-24
forum: New to Ubuntu
---

### Post by bkrembs on 2013-01-24
I just got a new laptop, and am desperately in need of help to get Ubuntu running on it.  Please help me not to have to return to Windows!


Here are the details thus far:
[LIST=1]
[*]I have a [ASUS G75VW-DH72B]("http://www.tigerdirect.com/applications/SearchTools/item-details.asp?EdpNo=7590087&CatId=4935") laptop
[*]The Ubuntu installer kept freezing, but I was able to work around it by setting "nosetmode" in the startup grub screen (hattip to [a G75V tutorial]("http://ubuntuforums.org/showthread.php?p=12241087#post12241087") I thought would be more relevant)
[*]I installed "apt-get install nvidia-current"
[/LIST]

However, any time I boot I get dropped directly into a terminal.  If I manually "startx", I see the following in /var/log/Xorg.0.log  

```

NVIDIA: Failed to load the NVIDIA kernel module.  Please check your system's kernel log for additional error messages

```

There is no /var/log/messages file, and a grep for more info in /var/log doesn't seem to turn up much.

Help?

UPDATE:
For anybody else experiencing this, I believe my problem was that none of the available nvidia-* Ubuntu drivers were compatible with my hardware.  

I ended up going directly to [Nvidia's driver site]("http://www.nvidia.com/Download/index.aspx?lang=en-us") and downloading the latest -- that worked perfectly.  Additionally, [this wiki page]("https://help.ubuntu.com/community/NvidiaManual") was helpful.

---

### Post by Bashing-om on 2013-01-24
bkrembs; Hi ! Welcome to the forum.

Try this;
Boot up the install with grub's altered boot parameter "nomodeset"
12.04: launcher->System Setting->Additional drivers: install recommended driver.
12.10 Software Sources-> tab Additional Drivers: install recommended driver.

Not sure but may have to (un)install the effects of "sudo apt-get install nvidia-current", maybe the installer (Additional Drivers) will take care of it.

[INDENT][INDENT]just try'n to help

[/INDENT][/INDENT]

---

### Post by Calinou on 2013-01-24
If your laptop uses Optimus (pretty much any laptop with a NVIDIA graphics card), do not install the NVIDIA drivers "normally". You will have to use Bumblebee instead. By default, only the integrated graphics card is used.

---

