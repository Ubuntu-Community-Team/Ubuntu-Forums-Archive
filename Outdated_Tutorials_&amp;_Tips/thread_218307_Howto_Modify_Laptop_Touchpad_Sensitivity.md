---
title: "Howto: Modify Laptop Touchpad Sensitivity"
date: 2006-07-18
forum: Outdated Tutorials &amp; Tips
---

### Post by Thund3rstruck on 2006-07-18
One of the things that really irritated me when I made the Ubuntu switch was the sensitivity of the laptop touchpad. It seemed to fly all over the screen and while browsing the web it appeared to open phantom links. 

Here is a short walkthrough for turning off the 'tapping' feature in your touchpad and other touchpad irritations. 

Backup your Xorg
```

$ sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.backup

```

Open your xorg configuration file for editting
```

$ sudo gedit /etc/X11/xorg.conf

```

Add this line at the bottom of the "InputDevices" section
```

Option          "SHMConfig"           "on"

```

Reboot the system or restart your gdm session
```

$ sudo shutdown -r now

```

Install qsynaptics package 
```

$ sudo apt-get install qsynaptics

```

Run qsynaptics
```

$ qsynaptics

```

Once in qsynaptics, select the "Tapping" item from the listbox on the left hand side of the program and change the button configuration to Tapping "One Finger" means none.

---

### Post by philidox on 2008-03-20
THANK YOU THANK YOU THANK YOU!!! That was just what I was looking for.

---

### Post by kpkeerthi on 2008-03-20
Alternatively, add this option after SHMConfig under "Input Devices"
```

Option "MaxTapTime" "0"

```

---

### Post by st0n3cutt3r on 2008-04-10
> **philidox said:**
> THANK YOU THANK YOU THANK YOU!!! That was just what I was looking for.

my feelings exactly. @Thund3rstruck:  now why doesn't your post have a 'thank you' button?

---

### Post by Fabiooltje on 2010-01-10
I have Kubuntu, so for me some things were different: 

[LIST]
[*] not qsynaptics but gsynaptics (I installed it via kpackage)
[*]not gedit but xedit
[/LIST]
But otherwise, thanks a lot, because this was the solution for me, too!

---

### Post by Fabiooltje on 2010-01-11
Hmmm... Another thing "different" is, that after restarting my laptop, the gsynaptics settings have returned to default. So tap-to-click was "on"  again and I had to switch it off by launching the gsynaptics again... 
If I have to do that every time... 

There is no "save these settings" button in my gsynaptics. 

Is there a way to make sure gsynaptics remembers the correct settings, or to change the settings automatically during startup of the computer?

---

