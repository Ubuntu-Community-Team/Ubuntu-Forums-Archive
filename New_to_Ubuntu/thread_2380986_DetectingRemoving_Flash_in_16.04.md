---
title: "Detecting/Removing Flash in 16.04?"
date: 2017-12-24
forum: New to Ubuntu
---

### Post by sterator on 2017-12-24
It's my understanding that Flash on 16.04 - or any version of Ubuntu - is a huge security hole. I have no desire to run flash, and I'd just as soon be rid of it. Is there a way to get rid of it without harming the system? 

Is there a way to detect if it's in the system in the first place?

Thank you!

---

### Post by &amp;KyT$0P# on 2017-12-24
> **sterator said:**
> Is there a way to detect if it's in the system in the first place?
Please post the output (if any) from running this command in Terminal -
```
dpkg-query -W | grep -i flash
```

You might also find it helpful to read [this thread]("https://ubuntuforums.org/showthread.php?t=2372341").

---

### Post by sterator on 2017-12-25
> **halogen2 said:**
> Please post the output (if any) from running this command in Terminal -
```
dpkg-query -W | grep -i flash
```


This is the result:
```

flashplugin-installer    28.0.0.126ubuntu0.16.04.1
```





> 
You might also find it helpful to read [this thread]("https://ubuntuforums.org/showthread.php?t=2372341").

Thank you for the link and for the terminal command!

---

### Post by sterator on 2017-12-25
so..if there is an item, "flashplugin-installer" and no other items with "flash" in their name, can we conclude that flash is not installed, that I only have an installer?

And, can said installer be removed without harming the system?

---

### Post by bcschmerker on 2017-12-25
There are four Packages to watch out for, viz., **adobe-flash-properties-gtk**, **adobe-flash-properties-kde**, **adobe-flashplugin**, and **flashplugin-installer**.  The Package **flashplugin-installer** is part of the restricted-extras metapackage for your subdistro.  The file libflashplugin.so will reside in either /usr/lib/adobe-flashplugin or /usr/lib/flashplugin-installer, depending on which Package is in your system.  Running:
```
sudo apt purge --remove adobe-flash* flashplugin-installer

```will clear the installer(s) and configuration files.

---

### Post by sterator on 2017-12-26
Thank you, bcschmerker..

running that command got rid of anything flash that would be returned by

				 				 					 						 	```
[[COLOR=#000000][/COLOR]]("https://ubuntuforums.org/member.php?u=609186")[COLOR=#000000]dpkg-query -W | grep -i flash[/COLOR]
```

and even let me know what it was going to do (remove flash-installed) before I got the Y/n choice.

---

### Post by again? on 2017-12-26
FYI 
Flash Player is pre-installed in Google Chrome, but not enabled.

---

