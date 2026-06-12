---
title: "Increasing Resolution?"
date: 2008-05-27
forum: New to Ubuntu
---

### Post by Codemastadink on 2008-05-27
Hey guys. So the highest resolution i can set my screen to is 640X480 and i can not seem to get it any higher. I have the latest video driver, but i do need it bigger. I saw somewhere that you can edit the code in X to accept higher res. Anyone know how to do this?

---

### Post by adobrakic on 2008-05-27
i edited my 'xorg.conf' by editing the screen section. I added:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
DefaultDepth 16
     Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection
```

---

### Post by Helgiks on 2008-05-27
If the above doesn't help you than post the output of ```
$ cat /etc/X11/xorg.conf
``` And someone will be able to help you.

---

### Post by Codemastadink on 2008-05-27
> **adobrakic said:**
> i edited my 'xorg.conf' by editing the screen section. I added:

```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Configured Video Device"
DefaultDepth 16
     Subsection "Display"
        Depth       16
        Modes "1280x1024" "1024x768" "800x600" "640x480"
    EndSubsection
EndSection
```

> **Helgiks said:**
> If the above doesn't help you than post the output of ```
$ cat /etc/X11/xorg.conf
``` And someone will be able to help you.


Wow. Crazyest thing just happened. I turned on the computer to try those solutions, and guess what! IT was fixed lol idk how but the resolution is like 1,000X700 roughly, dont remember the exact numbers but it works :)

One more thing though, the background on the desktop is still big, the default bird picture still only displays from the head to about just below the chest. any way i can fixx that>?

---

### Post by iaculallad on 2008-05-27
> **Codemastadink said:**
> Hey guys. So the highest resolution i can set my screen to is 640X480 and i can not seem to get it any higher. I have the latest video driver, but i do need it bigger. I saw somewhere that you can edit the code in X to accept higher res. Anyone know how to do this?

You can follow the steps I posted in this [thread]("http://ubuntuforums.org/showthread.php?t=807451") to set your resolution higher.

---

