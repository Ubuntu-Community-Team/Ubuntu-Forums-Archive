---
title: "Need help changing resolution"
date: 2008-11-05
forum: New to Ubuntu
---

### Post by nitsud11 on 2008-11-05
I feel rather dumb posting this but I am in need of some help. Earlier I was changing my screen resolution in GNOME and I selected a resolution that did not work with my monitor, and I got a black screen. I have no idea how I am supposed to change my resolution now that I can not see anything. I also have kde installed so that is what I am typing this under. I know I made a dumb mistake but can anyone help me?

---

### Post by mapes12 on 2008-11-05
I've not tied it but logic would indicate that if you can access your system via the KDE desktop environment then you should be able to change the screen res via the KDE utility for screen res settings which will also carry acroos to Gnome. I haven't used KDE so don't know where to find the KDE screen res utility but my guess is that it will be there somewhere.

---

### Post by nitsud11 on 2008-11-05
The KDE utility will only effect the KDE environment and not GNOME's. I have tried to access the GNOME utility through KDE but I am having no luck.

---

### Post by Separ on 2008-11-05
Try dropping to a terminal (in GNOME) by hitting ctrl+alt+F1 and log in. Then type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

---

### Post by mapes12 on 2008-11-05
Which version of Ubuntu are you running? Can you post the content of your /etc/X11/xorg.conf file for us to look at please.

---

### Post by nitsud11 on 2008-11-05
> **Separ said:**
> Try dropping to a terminal (in GNOME) by hitting ctrl+alt+F1 and log in. Then type ```
sudo dpkg-reconfigure -phigh xserver-xorg
```
Sorry for taking so long to respond. Both my log in screen and kde have changed to a much smaller resolution, but I am still getting a black screen in GNOME. I am running Ubuntu 8.10.

---

### Post by madsc89 on 2008-11-05
What graphics card are you using?
How did you install the driver for it?
Does recovery mode work?

---

### Post by nitsud11 on 2008-11-05
> **madsc89 said:**
> What graphics card are you using?
How did you install the driver for it?
Does recovery mode work?
My graphics card is a nividia geforce 6150 LE. I don't remember how I installed the driver. When I try logging in in recovery mode all I get is a black screen as well.

---

### Post by madsc89 on 2008-11-05
I had the opposite problem after installing CCC manually; my login screen was out of range, and my desktop was not. I changed my /etc/X11/xorg.conf file, and the login screen got fixed, plus the "screen resolution" in System got a max resolution similar to what I added In xorg.conf.

At least if you've got an ATI card, and are able to login with recovery mode, you can try the following:


```
sudo gedit /etc/X11/xorg.conf
```


Find the screen section, mine looked like this:
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		EndSubSection
EndSection

```

Add the line "Modes" with your preferred resolutions under Subsection "Display" Do not add any higher resolutions than your screen can handle. If you've got a 3:4 LCD, you can add this:
```
		Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"
```

I changed mine into this:
```

Section "Screen"
	Identifier "aticonfig-Screen[0]"
	Device     "aticonfig-Device[0]"
	Monitor    "aticonfig-Monitor[0]"
	DefaultDepth     24
	SubSection "Display"
		Viewport   0 0
		Depth     24
		Modes		"1280x1024" "1024x768" "1280x960" "640x480" "800x600"

	EndSubSection
EndSection

```

---

### Post by madsc89 on 2008-11-05
> **nitsud11 said:**
> My graphics card is a nividia geforce 6150 LE. I don't remember how I installed the driver. When I try logging in in recovery mode all I get is a black screen as well.

That's no good!:p

Have you got a Live CD?
Try booting using that one.

---

### Post by madsc89 on 2008-11-05
OK.

Lets try a shot in the blind:

Log in to GNOME (your main login). Then you wont be able to see anything:p BUT, I am going to guide you to your resolution:p

This is what to do:

1. Log in and wait for the drive to finish loading what it is loading:P

2. Move your mouse as far up and to the left as possible, and press the left button. This will open the Applications tab.

3. Push right two times. Now you're on system.

4. Push down, then right. then you are in preferences.

5. press S. Now this is tricky, because I don't know what entries you have starting with s, however, my screen resolution is the second. You should try starting with the first one, it can do minimal damage.

6. press enter, tab.

7. push down 7 times (or so). Then tab 4 times. Enter.

If nothing happens, repeat step 2-7. The menus remember that you already pushed S, so now you will open the next entry starting with S. That is: _repeat_ the steps, do not push S more than one time in stage 5.

Hope it helps.

---

### Post by nitsud11 on 2008-11-05
OK I am dumb. Very very dumb. When I first tried this: "sudo dpkg-reconfigure -phigh xserver-xorg", I was able to log in to gnome and be able to see my screen. Can you believe though that I then went to change the resolution and picked a bad one.....again. I tried that command again but it did nothing. I don't know what I am supposed to do now. I am a very dumb man.

---

### Post by alienexplorers on 2008-11-05
Boot ubuntu into gnome.
Login and wait for drive activity to stop.
Hit ctrl+alt+f1
Login again
run "gnome-display-properties"
Hit tab and then down arrow a couple times.
Hit tab 6 times.
hit enter.
reboot

---

### Post by nitsud11 on 2008-11-05
> **madsc89 said:**
> OK.

Lets try a shot in the blind:

Log in to GNOME (your main login). Then you wont be able to see anything:p BUT, I am going to guide you to your resolution:p

This is what to do:

1. Log in and wait for the drive to finish loading what it is loading:P

2. Move your mouse as far up and to the left as possible, and press the left button. This will open the Applications tab.

3. Push right two times. Now you're on system.

4. Push down, then right. then you are in preferences.

5. press S. Now this is tricky, because I don't know what entries you have starting with s, however, my screen resolution is the second. You should try starting with the first one, it can do minimal damage.

6. press enter, tab.

7. push down 7 times (or so). Then tab 4 times. Enter.

If nothing happens, repeat step 2-7. The menus remember that you already pushed S, so now you will open the next entry starting with S. That is: _repeat_ the steps, do not push S more than one time in stage 5.

Hope it helps.
Thank you for your efforts but I am having no luck. :(
I have to leave now but thank you to everyone who tried to help.

---

### Post by nitsud11 on 2008-11-05
> **alienexplorers said:**
> Boot ubuntu into gnome.
Login and wait for drive activity to stop.
Hit ctrl+alt+f1
Login again
run "gnome-display-properties"
Hit tab and then down arrow a couple times.
Hit tab 6 times.
hit enter.
reboot
Ok I am sorry how do I run "gnome-display-properties"? I tried simply typing "gnome-display-properties", but I got a message saying can not open display-properties or something of that sort.

---

