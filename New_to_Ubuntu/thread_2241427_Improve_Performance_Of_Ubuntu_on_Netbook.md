---
title: "Improve Performance Of Ubuntu on Netbook"
date: 2014-08-26
forum: New to Ubuntu
---

### Post by daniel2 on 2014-08-26
I have a Samsung NC110 that I have installed Ubuntu onto. It runs fairly well but I would like to know if there are some things I can do to improve performance. When I ran Windows I cut out a lot of things from Startup and used basic GUI rather than Aero. Just wondering if there are similar or better things I can do with Ubuntu

Thanks!

---

### Post by Vladlenin5000 on 2014-08-26
> **daniel2 said:**
> (...) used basic GUI rather than Aero. Just wondering if there are similar or better things I can do with Ubuntu


Hi, welcome.
Considering you're a fan of that awful 90's look & feel (modern Windows up to 7, without the 'eye candy' it's a 95/98 Windows) you can use lighter desktop environments like the ones standard in two different Ubuntu flavors: Xubuntu and Lubuntu. I would recommend the former if you really want that old school look & feel. Otherwise just stick with the standard Ubuntu, with Unity as the desktop environment (if you're already running Windows 7 in that machine you shouldn't have any problem with the standard Ubuntu).

Unlike Windows, a Linux distro usually sets only a few core services at the startup and, although not unusual, there aren't many apps that set themselves as a startup service. As such, don't worry or at least don't worry as much as you're used to with things at startup.

---

### Post by Jonathan Precise on 2014-08-26
Hi daniel2. Welcome to the forums!
How much RAM does your netbook have? Did it run the full Windows, or Windows starter?

You could try and install GNOME Fallback:
```
pkexec apt-get install gnome-flashback.
```

Make sure it doesn't delete anything critical (like ubuntu-desktop, ubuntu-standard, unity, gnome-session, etc.).

[HR][/HR]

Then log out. When you log back in, click on the ubuntu icon close to your user name. You can select "GNOME Flashback (Metacity)", and log in as you usually do. It will look different, but at least it saves resources.

---

### Post by mörgæs on 2014-08-26
Please run ```
sudo lshw -sanitize > lshw.txt
``` and post lshw.txt in CODE tags.

---

### Post by daniel2 on 2014-08-29
That command doesn't appear to work. It can't find gnome-flashback. The netbook has 2gb ram and had Windows Starter installed

---

### Post by ThatBum on 2014-08-29
I have a Eee PC with similar specs. It runs Xubuntu and is fairly quick, but the Intel GMA lacks GPU oomph. Can't even play HD Youtube on it, but it couldn't do that in 7 either...Unity is heavyweight relative to xfce so that might be bogging it down.

As previously stated, it's about as fast as it's going to get. It is an Atom CPU, you know. :P You could try installing [FONT=courier new]preload[/FONT] for additional readahead caching. Maybe [FONT=courier new]tlp[/FONT] for power saving.

---

### Post by Frogs Hair on 2014-08-29
> **daniel2 said:**
> That command doesn't appear to work. It can't find gnome-flashback. The netbook has 2gb ram and had Windows Starter installed The command will create a text file in the home folder and displays information about the computer/hardware.

---

### Post by ThatBum on 2014-08-30
In that case why not just use [FONT=courier new]sudo lshw -sanitize > ~/lshw.txt[/FONT], and post the contents of lshw.txt?

---

### Post by Frogs Hair on 2014-08-30
That's what [COLOR=#000000]mörgæs was asking but the output doesn't appear in the terminal and could give the impression the command didn't work.     [/COLOR]

---

