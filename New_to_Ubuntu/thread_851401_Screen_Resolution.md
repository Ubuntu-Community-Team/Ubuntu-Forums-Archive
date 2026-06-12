---
title: "Screen Resolution"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by Agoriuq on 2008-07-06
Hello: I've just installed ubuntu 8.04, I have a VIA/S3G KM400/KN400 video adapter and a 17" Viewsonic Monitor. The problem is that I can't get a screen resolution higher than 800x600. I already searched lots of forums for an answer but I just can't get the right one for me. Thanks in advance.

---

### Post by Nikitas350 on 2008-07-06
Post here the xorg.conf (run the command "gedit /etc/X11/xorg.conf")

---

### Post by adobrakic on 2008-07-06
I fixed it by copying and pasting this:

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

into xorg.conf, under the "screen" section, of course.

---

### Post by Togorashi on 2008-07-08
So I'm a total newb in linux.   I just upgraded to 8.04 from 7.something and I only had access to 640X480.   I tried to copy and paste the above into the appropriate file, but I got an error message saying that I didn't have permission to save the file.  Do I have to log in somehow?     Thanks.

---

### Post by kestrel1 on 2008-07-08
> **Togorashi said:**
> So I'm a total newb in linux.   I just upgraded to 8.04 from 7.something and I only had access to 640X480.   I tried to copy and paste the above into the appropriate file, but I got an error message saying that I didn't have permission to save the file.  Do I have to log in somehow?     Thanks.
To edit the xorg.conf file try this:
```
sudo gedit /etc/X11/xorg.conf
```
You will be asked for your password & you should be able to edit the file.

---

### Post by Togorashi on 2008-07-08
That did it.   Thanks so much.

---

