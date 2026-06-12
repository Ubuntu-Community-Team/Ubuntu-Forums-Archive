---
title: "Resolution Too Large"
date: 2008-04-27
forum: New to Ubuntu
---

### Post by Faded on 2008-04-27
Hello There,

I just finished Installing Hardy into my Computer, Installation went well (From what I know) and everything.

However when I attempt to boot up the computer it tells me my Resolution (1680x1050) is to much.

I understand 800x600 is the basis for Ubuntu and whatnot, so how would I fix this?

Much Appreciated :)

Carlos.

---

### Post by Bodsda on 2008-04-27
If you can get to a command prompt type this then follow the on screen instructions

```
sudo dpkg-reconfigure xserver-xorg
```

---

### Post by Faded on 2008-04-27
I noticed that before. I'll try that and see if it Helps :)

---

### Post by mgmiller on 2008-04-27
I'm a little confused by your question.  What resolution do you want?  Have you tried going to System > Preferences > Screen Resolution and selecting what you want from the drop down lists?

If this doesn't work, post back and I can give you more explicit instructions.  It would also be helpful to know what video card and monitor you have.

---

### Post by Faded on 2008-04-27
Basically I tried to use Ubuntu via Live CD in which the Resolution I was given was 800x600. My proper resolution is 1680x1050. 

I did try System > Preferences > Screen Resolution however the 1680x1050 Resolution does not show.

If I remember correctly the Video Card I have is a 'NVIDIA GeForce 6150 SE' and the Monitor is the HP w2207h.

```
sudo dpkg-reconfigure xserver-xorg
```

I just tried to do this however I'm being told that xserver-xorg is not Installed, or rather not a valid package.

---

### Post by eapache on 2008-04-27
Right-click on the menu, select 'Edit Menus'.

Scroll down to Applications > Other and check the box beside Screens & Graphics.

Close the menu editor.

Open the Screens & Graphics application from the menu.

Try configuring your monitor there...

---

### Post by Bodsda on 2008-04-27
type this in a terminal

```
sudo apt-get install xserver-xorg
```

---

### Post by Faded on 2008-04-27
The issue really is, I can't even get into the menus. The Monitor says 'Resolution Too Large' and stays with that message.

---

### Post by Bodsda on 2008-04-27
reboot, when grub loads select recovery mode not normal -- then whenyou get to command prompt type

```
sudo apt-get install xserver-xorg && sudo dpkg-reconfigure xserver-xorg
```

---

### Post by daimaru on 2008-04-27
just boot when you get to the part where it says resolution too large hit ctrl+alt+F1 log in with username and password then type 
```
sudo nano /etc/X11/xorg.conf
```in the file scroll to the section "Screen" edit the lines where it says:
```
Modes        "1600x1200"    "1024x768"
```and add your resolution ( make sure its the default 24 bit one ) 
so for this example add the highest resolution at the beginning.
```
Modes "1680x1050" "1600x1200"   "1024x768"
```restart or do a ctrl+alt+backspace
EDIT: just in case you never used nano before hit ctrl+x when your done editing. that will save your file.

---

### Post by mgmiller on 2008-04-27
> I did try System > Preferences > Screen Resolution however the 1680x1050 Resolution does not show.

This implies that you could see and work with your desktop at some point.  If you can get back there:

1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select generic LCD (assuming it's an LCD)
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

---

### Post by Faded on 2008-04-27
I just tried the 

```
sudo dpkg-reconfigure -phigh xserver-xorg && sudo apt-get install xserver-xorg
```

However when trying that I get this error;

```
xserver-xorg postinst warning: overwriting possibly-customized configuration file; backup in /etc/X11/xorg.conf.20080427171106
```

Any ideas?

---

### Post by mgmiller on 2008-04-27
That's not an error message, it's just telling you that it backed up your old file before it ran.

---

### Post by Faded on 2008-04-28
> **mgmiller said:**
> This implies that you could see and work with your desktop at some point.  If you can get back there:

1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select generic LCD (assuming it's an LCD)
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

I was able to 'somehow' get into the Desktop with 'Low Graphics Mode' so I went and tried to change the settings as you said here. However whenever I change it to my Monitor and Resolution I hit test and it still continues to tell me the 'Resolution is Out of Range' for my Monitor.

---

### Post by mgmiller on 2008-04-28
Are you also changing the refresh rate?  make sure that is also correct as it can also cause the "out of range" monitor error.  This error is hard coded into your monitor and is not produced by Ubuntu.  Your monitor is seeing either a resolution and/or a refresh rate that is out of range.

---

