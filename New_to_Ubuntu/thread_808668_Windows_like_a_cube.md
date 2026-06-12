---
title: "Windows like a cube?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by Jaded Misanthrope on 2008-05-26
I have enabled 'wobbly windows' on my copy of Ubuntu, but I have seen people press some keys or do something else to make their view 'zoom out' and show the workspaces or whatever as a cube--how can I do this?

---

### Post by perillux on 2008-05-26
use the same program that you used to enable wobbly windows:
system > preferences > advanced desktop effects settings

then at the left click "desktop" and check the "desktop cube" and the "rotate cube".
The default keybindings to use the cube are ctrl+alt+(left arrow or right arror)   or ctrl+alt+(mouse click)
you can also hold shift while doing that first combination to move a window with you as the cube spins.  To change the amount of workspaces right-click your workspace applet at the bottom right panel and go to preferences.
You can also use the Advanced Desktop Effects Settings manager, to add images to the top and bottom of the cube, the menu item to do this is called "cube caps" under "utility".

---

### Post by adobrakic on 2008-05-26
i dont have "advanced desktop effects settings" under preferences, could it be somewhere else?

---

### Post by Joeb454 on 2008-05-26
Open a terminal (Applications > Accessories > Terminal) and type (or copy & paste) ```
sudo apt-get install compizconfig-settings-manager
``` Then you should have the option ;)

---

### Post by philinux on 2008-05-26
compizconfig-settings-manager is not installed by default as some hardware would be unable to make use of it.

---

### Post by adobrakic on 2008-05-26
I've enabled desktop cube, but how do i actually make it appear?

---

### Post by stalkier on 2008-05-26
> **Jaded Misanthrope said:**
> I have enabled 'wobbly windows' on my copy of Ubuntu, but I have seen people press some keys or do something else to make their view 'zoom out' and show the workspaces or whatever as a cube--how can I do this?

You'll need CCSM, emerald, and Fusion-Icon installed. CCSM is not installed by default (though I think it should be...as many of us do). Just goto Synaptic Package Manager - click Search - type Compiz.

Emerald and Fusion-Icon are for Emerald Themes. Adds more eye candy. I use it on both of my systems. You can get themes and more here:

[http://www.gnome-look.org/](http://www.gnome-look.org/)

Hope that helps.

---

### Post by akiratheoni on 2008-05-26
> **adobrakic said:**
> I've enabled desktop cube, but how do i actually make it appear?

Make sure 'rotate cube' is also enabled, then go to General Options -> Desktop Size -> Horizontal Desktop Size should be 2, change it to 4. 

Then use Ctrl+Alt+Left click and it should zoom out.

---

### Post by adobrakic on 2008-05-26
Is there a certain place i should do ctrl+alt+left click? 
When i do it, it does nothing. I opened two programs to make sure i need more than one program for it to do anything, but still it doesn't work.
When i go to System > Preferences > Appearance > Visual Effects and try to make it to normal or extra, it doesnt let me. could that be the problem?

---

### Post by philinux on 2008-05-26
> **adobrakic said:**
> Is there a certain place i should do ctrl+alt+left click? 
When i do it, it does nothing. I opened two programs to make sure i need more than one program for it to do anything, but still it doesn't work.
When i go to System > Preferences > Appearance > Visual Effects and try to make it to normal or extra, it doesnt let me. could that be the problem?

Sounds like your video driver is not installed. What are your system specs.

Look in System >Admin >Hardware drivers

---

### Post by sam_delta on 2008-05-26
> **adobrakic said:**
> Is there a certain place i should do ctrl+alt+left click? 
When i do it, it does nothing. I opened two programs to make sure i need more than one program for it to do anything, but still it doesn't work.
When i go to System > Preferences > Appearance > Visual Effects and try to make it to normal or extra, it doesnt let me. could that be the problem?
you probably need to install video card drivers, whats your video card?, if you dont know, you can find out by posting the output of```
lspci
```
you might consider making another thread for this

sam

---

### Post by adobrakic on 2008-05-26
When i open that, it says "No  proprietary drivers are in use on this system."

---

### Post by adobrakic on 2008-05-26
> **sam_delta said:**
> you probably need to install video card drivers, whats your video card?, if you dont know, you can find out by posting the output of```
lspci
```
you might consider making another thread for this

sam

00:00.0 Host bridge: VIA Technologies, Inc. VT8375 [KM266/KL266] Host Bridge
00:01.0 PCI bridge: VIA Technologies, Inc. VT8633 [Apollo Pro266 AGP]
00:0a.0 Communication controller: Agere Systems LT WinModem (rev 02)
00:0b.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
00:11.0 ISA bridge: VIA Technologies, Inc. VT8233A ISA Bridge
00:11.1 IDE interface: VIA Technologies, Inc. VT82C586A/B/VT82C686/A/B/VT823x/A/C PIPC Bus Master IDE (rev 06)
00:11.2 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.3 USB Controller: VIA Technologies, Inc. VT82xxxxx UHCI USB 1.1 Controller (rev 23)
00:11.5 Multimedia audio controller: VIA Technologies, Inc. VT8233/A/8235/8237 AC97 Audio Controller (rev 40)
01:00.0 VGA compatible controller: S3 Inc. VT8375 [ProSavage8 KM266/KL266]


that's what i get when i type that in

---

### Post by ubuntu-freak on 2008-05-26
> **adobrakic said:**
> I've enabled desktop cube, but how do i actually make it appear?

 
You need to enable "Rotate Cube" as well. 
 
Nathan

---

### Post by adobrakic on 2008-05-26
Yeah, i've also enabled 'rotate cube'

---

### Post by philinux on 2008-05-26
What happens when you press ctrl+ alt+ left arrow key

---

### Post by rajaram_s on 2008-05-26
If your graphics card is not supported, try using the hardy heron. It has better gardware support.... especially with the integrated graphics accelerators of Intel

---

### Post by ubuntu-freak on 2008-05-26
Are people reading his first post? He has effects, he doesn't need drivers to enable effects, he doesn't need fusion-icon and Emerald to rotate a desktop cube either.
 
Nathan

---

### Post by adobrakic on 2008-05-26
> **philinux said:**
> What happens when you press ctrl+ alt+ left arrow key


Nothing, right now if i would press it, it would just highlite something on the forums.

---

### Post by philinux on 2008-05-26
I dont think your integrated/graphics card can run it.

---

### Post by adobrakic on 2008-05-26
Yeah, that's what i figured. Thanks for your help

---

### Post by ubuntu-freak on 2008-05-26
> **adobrakic said:**
> Nothing, right now if i would press it, it would just highlite something on the forums.

 
Minimize all windows, then scroll on the desktop. Also, are you keeping ctrl + alt pressed while you click and drag your mouse around? They need to be pressed and held while you drag.
 
Nathan

---

### Post by ubuntu-freak on 2008-05-26
> **adobrakic said:**
> Nothing, right now if i would press it, it would just highlite something on the forums.

> **philinux said:**
> I dont think your integrated/graphics card can run it.

 
Wobbly windows works for him, so desktop cube will also.
 
Nathan

---

### Post by philinux on 2008-05-26
Did I miss the wobbly windows bit. :)

---

### Post by ubuntu-freak on 2008-05-26
It's in his first bleeding post. Also, he isn't pressing the keys properly, as even without composite, pressing Ctrl+Alt Left/Right will switch workspaces.
 
Nathan

---

### Post by philinux on 2008-05-26
Nah Nathan the OP has gone awol.

---

### Post by ubuntu-freak on 2008-05-26
> **philinux said:**
> Nah Nathan the OP has gone awol.

 
I didn't even realise. They both have no avatar. You knew? It's out of order for him to hijack a thread, especially considering the OP has only posted in it once.
 
Nathan

---

### Post by philinux on 2008-05-26
> **reassuringlyoffensive said:**
> I didn't even realise. They both have no avatar. You knew? It's out of order for him to hijack a thread, especially considering the OP has only posted in it once.
 
Nathan

Well never mind, the wobbly windows got me to look back on the thread. Duh. The Op has prolly got it sorted by now....

---

### Post by ubuntu-freak on 2008-05-26
> **philinux said:**
> Well never mind, the wobbly windows got me to look back on the thread. Duh. The Op has prolly got it sorted by now....

 
I sent the OP a PM with some instructions anyway, but I should post it here as well I guess. I'll edit my post on page 1.
 
Nathan

---

### Post by ubuntu-freak on 2008-05-26
Nevermind, here will do.
 
Copy and paste this command to install CCSM:
 
**sudo apt-get install compizconfig-settings-manager**
 
Navigate to System > Preferences > Advanced Desktop Effects Settings, then enable "Desktop Cube" and "Rotate Cube". You may also like the plugin "Cube Caps", as it decorates the top and bottom of the cube.
 
To rotate your desktop, press and hold down Ctrl+Alt, then press the left mouse button and drag it around to rotate the cube. You can also quickly rotate with the left/right arrow keys. Also, it makes sense to right-click on the workspace switcher and have four virtual desktops, instead of two.
 
Nathan

---

### Post by philinux on 2008-05-26
Isn't it a shame you cant have apps on the cube caps. And full 3d rotate.

Here's wishing.

---

### Post by perillux on 2008-05-26
also in case it's still not working, make sure you have the binding set correctly.

Click the actual "rotate cube" button, and then the "bindings" tab and maximize the "rotate cube" drop down, and make sure the keyboard (in blue) bindings are set properly.

---

