---
title: "Manually Change Screen Resolutions"
date: 2008-07-29
forum: New to Ubuntu
---

### Post by tim.n9puz on 2008-07-29
I just installed XUbuntu 8.04 on a machine with built-in nVidia display hardware. I have enabled the proprietary drivers and installed the nvidia-settings package to make changes to the resolution.

It appears the default resolution is 640x480 or less.

When I run the nvidia settings app most of the options, including resolution are so far down the screen that I cannot see the choices, get to the "OK/Cancel" buttons, etc. I cannot drag the corner of the application's window to let me see the bottom of the window.

Is there a configuration file I can edit manually to specify a certain resolution like 1024x768 so I can see and use all of the configuration screens?

Thanks for the help.

---

### Post by ingvildr on 2008-07-29
You could hold Alt then click on the application to be able to move it from anywhere.

---

### Post by Diabolis on 2008-07-29
Yes, you can modify the **xorg.conf** file.
```
sudo nano /etc/X11/xorg.conf
```

---

### Post by Diabolis on 2008-07-29
The section that you want to edit looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 9200se"
	DefaultDepth    24
        	SubSection "Display"
                	Depth           24
                	Modes           "1280x1024" "1024x768"
	        EndSubSection
EndSection

```

---

### Post by bks on 2008-07-29
> **tim.n9puz said:**
> Is there a configuration file I can edit manually to specify a certain resolution like 1024x768 so I can see and use all of the configuration screens?

You could try checking the resolution listed in the xorg.conf. Use a text editor to open it up (I appologize, I don't know the name of the default editor for xubuntu).
```

sudo texteditor /etc/X11/xorg.conf

```

Be sure to replace "texteditor" with the name of the editor you're using. Then look for a heading that says "Screen" or "Monitor" and under that there should be some resolution(s) listed. If 1024x768 isn't there that could be your problem.

Alternatively if you're unsure how to make the changes, attach a copy of your xorg.conf to this thread and one of us can look at it.

---

### Post by ace007 on 2008-07-29
I had a similar problem with nVidia.  I installed envy from the repos and then envy automatically installed the driver that would work with my card.  After a restart, I had more options for resolution from the nvidia-settings program.

---

### Post by bks on 2008-07-29
> **Diabolis said:**
> Yes, you can modify the **xorg.conf** file.
```
sudo nano /etc/X11/xorg.conf
```

LOL, I was a day late and a dollar short!

---

### Post by Diabolis on 2008-07-29
> **bks said:**
> LOL, I was a day late and a dollar short!

Yeah, hehe.

> **ace007 said:**
> I had a similar problem with nVidia.  I installed envy from the repos and then envy automatically installed the driver that would work with my card.  After a restart, I had more options for resolution from the nvidia-settings program.

+1 if you don't feel comfortable editing configuration files, I've heard that envy works pretty well.

---

### Post by sailor2001 on 2008-07-29
several options /usr/share/applications/screen and resolutions   or....gksudo display--config -gtk   or....envyng (listed in synaptics

---

### Post by tim.n9puz on 2008-07-29
> **ingvildr said:**
> You could hold Alt then click on the application to be able to move it from anywhere.

What a dummy... I didn't realize you could do that. Thanks!

Unfortunately now that I can slide the display around my only two resolution choices are still 640x480 and 320x240. Yech.

---

### Post by tim.n9puz on 2008-07-29
> **bks said:**
> You could try checking the resolution listed in the xorg.conf. Use a text editor to open it up (I appologize, I don't know the name of the default editor for xubuntu).
```

sudo texteditor /etc/X11/xorg.conf

```

Be sure to replace "texteditor" with the name of the editor you're using. Then look for a heading that says "Screen" or "Monitor" and under that there should be some resolution(s) listed. If 1024x768 isn't there that could be your problem.

Alternatively if you're unsure how to make the changes, attach a copy of your xorg.conf to this thread and one of us can look at it.

I edited xorg.conf and added a section with "1024x768". That resolution still does not show up as a choice anywhere.

Also, in looking through the original xorg.conf file I don't see "640x480" or any other specific resolution/screen size listed either.

---

### Post by tim.n9puz on 2008-07-29
> **Diabolis said:**
> The section that you want to edit looks like this:
```
Section "Screen"
	Identifier	"Default Screen"
	Monitor		"Configured Monitor"
	Device		"Radeon 9200se"
	DefaultDepth    24
        	SubSection "Display"
                	Depth           24
                	Modes           "1280x1024" "1024x768"
	        EndSubSection
EndSection

```


The original file did not have 'SubSection "Display"' category so I added one as shown above. Still, the only choices that show up in the screen config menu are 640x480 and 320x240.

---

### Post by pcrussell50 on 2008-07-29
I have the same problem with 8.4 in both ubuntu and xubuntu.  800x600 is the only choice.  Funny thing is, the 7.10 versions of same did not have this problem.  Does anyone think this qualifies as a "bug", since it worked in an older version and doesn't in a newer one?  I'd be happy to file a bug report, but iirc, it's not all that easy.  also, there is no sound in xubuntu 8.4, but there is sound in ubuntu 8.4.  sound worked in 7.10. weird.

also worthy of note:  i boot the same machine into windblows, and all is normal with screen resolutions and sound. 

-Peter

---

### Post by Diabolis on 2008-07-29
After you modify/update the xorg.conf file, you have to restart xserver in order to see the changes.

How to restart xserver, press: <Ctrl><Alt>Backspace

---

### Post by tim.n9puz on 2008-07-29
> **Diabolis said:**
> After you modify/update the xorg.conf file, you have to restart xserver in order to see the changes.

How to restart xserver, press: <Ctrl><Alt>Backspace

Yes. At first I tried just restarting the xserver from that option in envyng. When that didn't work I began rebooting the machine after each change. No success as yet.

I know there are issues with not having complete access to nvidia driver source but darn, it sure seems like an awfully common video sub system to have this much trouble. I've got Ubuntu of one flavor or another running on 5 machines and I think this is the worst install yet in terms of hours of my life I'd like back.

Tim

---

