---
title: "Compiz- special desktop effects unavailable."
date: 2008-06-22
forum: New to Ubuntu
---

### Post by a.v.l on 2008-06-22
I have compiz installed and but I'm unable to see special desktop effects to set up the desktop cube ect. Visual effects are on "extra" and my nividia card has the latest driver installed. What's wrong please?

---

### Post by XTR0RDiNAiRE on 2008-06-22
ive been tryin to get help with this problem since i first got ubuntu, good luck with this
i never figured it out

if u get help and figure it out, let me know sumthing
appreciate it


--i really want to get avant windows navigator
but no luck

---

### Post by nikgare on 2008-06-22
Is compiz actually working?
Can you enable it via the Visual Effect tab of the Appearence dialogue box?
You can gain more control of compiz by installing compizconfig-settings-manager and more plugins by installing compiz-fusion-plugins-extra and 
compiz-fusion-plugins-main

Nik

---

### Post by Victormd on 2008-06-22
Assuming you have your graphics card properly installed (which by your post, it seems you do), you can try installing these (open a terminal and copy and paste one line at a time):
```
sudo apt-get update
sudo apt-get install linux-restricted-modules-generic restricted-manager
```
```
sudo apt-get install compizconfig-settings-manager compiz compiz-core compiz-fusion-plugins-main compiz-fusion-plugins-extra compiz-gnome compiz-plugins libcompizconfig-backend-gconf libcompizconfig0
```

---

### Post by a.v.l on 2008-06-22
> **nikgare said:**
> Is compiz actually working?
Can you enable it via the Visual Effect tab of the Appearence dialogue box?
You can gain more control of compiz by installing compizconfig-settings-manager and more plugins by installing compiz-fusion-plugins-extra and 
compiz-fusion-plugins-main

Nik

Thanks I now have the advanced desktop setting window having installed your suggestion but although I have selected desktop cube and to have it rotate It dosesn't appear as a cube. Perhaps I need to make a few other adjustments, can someone help.

---

### Post by WBL on 2008-06-22
Is there something called "Advanced Desktop Effects Settings" under System-->Preferences?

-WBL

---

### Post by a.v.l on 2008-06-22
> **WBL said:**
> Is there something called "Advanced Desktop Effects Settings" under System-->Preferences?

-WBL

Yes there is now.

---

### Post by XTR0RDiNAiRE on 2008-06-22
this is the message that i get

mario@mario-desktop:~$ compiz compiz-core compiz-fusion-plugins-main
Checking for Xgl: not present. 
Detected PCI ID for VGA: 	Flags: bus master, VGA palette snoop, 66MHz, medium devsel, latency 64
01:05.0 0300: 1002:791e (prog-if 00 [VGA controller])
Checking for texture_from_pixmap: not present. 
Trying again with indirect rendering:
Checking for texture_from_pixmap: present. 
Checking for non power of two support: present. 
Checking for Composite extension: not present. 
aborting and using fallback: /usr/bin/metacity

---

### Post by WBL on 2008-06-22
> **a.v.l said:**
> Yes there is now.

You can enable the cube and other effects in Advanced Desktop Effects Settings.  For example, put a checkmark by "Desktop Cube" to get the cube.

-WBL

---

### Post by XTR0RDiNAiRE on 2008-06-22
ok this is where i get stuck, i have advanced desktop effects, then i open it, i click on the effects that i want to use, but then nothing happens
how do i apply or what do i do next?

---

### Post by a.v.l on 2008-06-22
> **WBL said:**
> You can enable the cube and other effects in Advanced Desktop Effects Settings.  For example, put a checkmark by "Desktop Cube" to get the cube.

-WBL

Yes I've done that and I'm fairly sure I have the cube, but it fills the whole screen when I select a different desktop. Can I resize the cube somehow?

---

### Post by Old_Grey_Wolf on 2008-06-22
Look at Settings Manager, General Options, Desktop Size. The Horizontal Virtual Size should be 4.

I assume you have tried to rotate the cube with cntl-alt-Left mouse button.

---

### Post by a.v.l on 2008-06-22
> **Old_Gray_Wolf said:**
> Look at Settings Manager, General Options, Desktop Size. The Horizontal Virtual Size should be 4.

I assume you have tried to rotate the cube with cntl-alt-Left mouse button.

OK set size to 4 and I can see I have a cube in the making, but it is full  screen size and only appears as a cube when I select a different desktop ( as it swings from one to the other) I imagine it should be smaller for me to get the appearance of a complete cube shape. control-alt-left mouse button does nothing.

---

### Post by Old_Grey_Wolf on 2008-06-22
In Settings Manager, is Rotate Cube checked? It should be. Then try to rotate the cube with cntl-alt-Left mouse button.

If I do not respond in the future...I do not know what time zone you're in and I do have a life...Try this link [http://ubuntuforums.org/showthread.php?t=809695](http://ubuntuforums.org/showthread.php?t=809695)

---

### Post by TrashmanL on 2008-06-22
I think I already know the answer to this, but I'm asking just in case. Is this available for Feisty? I have a laptop with Hardy that has this, my main machine has Feisty and does not. When I tried to install these packages, it said "package not found." This usually means its not available for my version, but I also know there are ways around this sometimes...

And don't tell me to upgrade! I'm considering it... but my current settings are working so beautifully and I'm afraid that upgrading will screw up everything I've worked for! Eventually, I realize I'll have to, though...

---

### Post by inportb on 2008-06-22
It is not officially available for Feisty, but you can get Compiz-Fusion off a certain tuxboy repository. Search for it, I guess?

---

