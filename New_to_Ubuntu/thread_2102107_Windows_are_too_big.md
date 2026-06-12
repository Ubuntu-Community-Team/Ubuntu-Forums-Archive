---
title: "Windows are too big"
date: 2013-01-06
forum: New to Ubuntu
---

### Post by misswham on 2013-01-06
Morning.  I have ubuntu 12.04 and my windows are too big.  Example.  The Prefix and Title window above this message box is too big and when I am uploading a picture to my google acct, The open and send buttons are beneath the window and I either have to move to the desktop below mine or i have to physically shrink the window to hit the button.  How can I change this?

---

### Post by gordintoronto on 2013-01-06
It sounds like the monitor resolution is incorrect. What video adapter is in your computer? If you run the Terminal command: lspci
then look for the line which includes "VGA" it will tell you.

---

### Post by faceyourfaces on 2013-01-06
Is there any chance you can grab us a screenshot?

---

### Post by misswham on 2013-01-06
how do u grab a screenshot?

---

### Post by misswham on 2013-01-06
this is whats on the VGA line when i put the code in

01:00.0 VGA compatible controller: NVIDIA Corporation GT216 [GeForce GT 240M] (rev a2)

---

### Post by gordintoronto on 2013-01-06
Did you install an Additional Driver? If so, you should be able to fix this in Nvidia X Server Settings.

---

### Post by mag1strate on 2013-01-06
[https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia](https://help.ubuntu.com/community/BinaryDriverHowto/Nvidia)

The instructions on this page should help you install the Nvidia Drivers using the additional hardware section :D

---

### Post by misswham on 2013-01-07
In the additional drivers, the first one is checked.

NVIDIA accelerated graphics driver (version curren) {Recommended} is checked

There are 3 other choices.  Which one is supposed to be checked to get what I need.  The other 3 are.

NVICIA accellereated graphics driver (post-release updates) (version current-updates)

NVIDIA accelerated graphics driver (**experimental**beta)(version experimental-304)

NVIDIA accelerated graphics driver (**experimental**beta)(version experimental-310)

Which one is supposed to be checked or is what I have fine.  

It also says

Tested by the Ubuntu developers
License: Proprietary
3D-accellerated proprietary grahpics driver for NVIDIA cards.  Required if you want to run Unity.

This driver is required to fully utilise the 3D potential of NVIDIA graphics cards, as well as provide 2D accelleration of newer cards.

This driver is activated and currently in use.  

So this is the one thats already activated.  Now I read somewhere that I am supposed to click 3D when I log on but I only have a regular Unity and 2D Unity as an option but my desktop effects seem to work fine.  A little slow and buggy sometimes but nothing major except these windows being too big and if I make the font small, they seem to shrink but in firefox the windows on some sites like the login windows are bigger than the spot they should be in also.

---

### Post by gordintoronto on 2013-01-07
"Version current" is the normal thing to have installed.

Now you can run nvidia X server settings. The second line on the left is "X Server Display Configuration." Select it. On the right, it should display the brand and model of your monitor, and what resolution it is running at. At the bottom, the same information should be displayed, but you can change the resolution.

If you tell us what information is displayed, we should be able to help you. If the brand and model of your monitor are not displayed, please look at the monitor and try to figure it out. The actual model number is essential information.

P.S. "Unity" is Unity 3D.

---

### Post by misswham on 2013-01-07
Model:  MS_Nvidia Default Flat Panel (DFP-0 on GPU-0)

Config  Seperate X screen (requires X restart)

Resolution Auto 1920x1080

Thats whats on the X Server Display Configuration

i changed a few resolutions but the one that its on is the best.

---

### Post by gordintoronto on 2013-01-08
Is this a laptop? What brand and model?

---

### Post by misswham on 2013-01-09
no desktop all in one sony vaio.

---

### Post by gordintoronto on 2013-01-09
That describes a large family of computers. Which model do you have?

---

