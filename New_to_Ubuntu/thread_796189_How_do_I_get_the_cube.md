---
title: "How do I get the cube?"
date: 2008-05-16
forum: New to Ubuntu
---

### Post by clixis on 2008-05-16
I am a brand new Ubuntu Hardy Heron user and all is well,EXCEPT
I am unable to get compiz 3-D disktop visual effects.
I installed the the compizconfig-settings-manager package
and turned on System &#8594; Preferences &#8594; Advanced Desktop Effects Settings
and set System &#8594; Preferences &#8594; Appearance &#8594; Visual Effects to get Extra Effects. But nothing happens.

Is there something else I need to do to enable or show the 3D desktop?

Also, I was unable to switch workspaces until I turned off visual effects.
Finally, when I rebooted Linux, all the Advanced Desktop Effects Settings for the cube had been cleared!

I'm sort of lost here. Any help would be appreciated.

---

### Post by abn91c on 2008-05-16
you video card must support openGl and 3d effects otherwise compiz would not work

---

### Post by ByteJuggler on 2008-05-16
What video driver are you using?  What video card do you have?  You possilbly need the vendor of your card's propriatary driver for the 3d acceleration to work.

---

### Post by Schendje on 2008-05-16
If you've turned all the Cube settings in Advanced Desktop effects Settings to "on" you also need to make sure you've got a couple of workspaces. If you only have one workspace, it isn't going to switch (sounds obvious, but this is were I went wrong myself :P).

Ctrl+alt+left of ctrl+alt+right changes cube side, pressing ctrl+alt and dragging your screen with the mouse gives you the Cube.

---

### Post by issih on 2008-05-16
Ok, the way things work chaged slightly for hardy heron.

You need to install the package simple-ccsm (I think thats what its called)

This is a little gui application that attempts to offer the most popular compiz effects, and apply sensible presets to them. I think it is designed specifically for people just starting out like yourself :). Once that is installed, there will be a new option in the visual effects tab of the appearance dialog. Select this new option ("custom") and now you have control over which compiz plugins (e.g. cube) are used on your system. Once you have selected "custom" you can configure the plugins either through the simple-ccsm or the full blown package you already have. But you NEED the simple package installed to get the "custom" option to appear in the first place.

Hope that helps

---

### Post by clixis on 2008-05-16
My video card is Radeon R300 (ATI) and the driver is fglrx.  Hope this helps clear thing up.

---

### Post by philinux on 2008-05-16
Compizconfig-settings-manager installs ccsm as the menu item "Advanced destop effects settings". So the OP has the right app.

---

### Post by issih on 2008-05-16
Unless they tweaked things in an update since hardys release, no he doesn't have the right app..You absolutely HAVE to have simple-ccsm in the first place to be able to select custom effects. Simple-ccsm is basically a wrapper program for the full ccsm, and does install ccsm as a dependancy, but ccsm on its own, without the simple package does nothing for you any more. It certainly didn't here, and there are a lot of threads about it, trust me :)

---

### Post by philinux on 2008-05-16
Like I said this is how it is in Hardy. I dont have simple-ccsm installed.

---

### Post by issih on 2008-05-16
Weird, I just uninstalled simple-ccsm to see what would happen...You are right, you can get ccsm to work without it, I swear it didn't when I first installed hardy, and there were a lot of threads about it where simple-ccsm made the difference. Maybe something has been tweaked recently. Its still a bit screwy though, I now have no custom effects option and I am apperently not on any of the options available I am greyed out on none, normal and extra, so I guess I am actually somehow on custom, just not visibly.

I'd give simple-ccsm a go if you are having trouble, I know I needed it after first install, but it appears things are generally a bit screwy here

---

### Post by philinux on 2008-05-16
Maybe it was needed in the early beta's but what I'm seeing is perfect, no bugs whatsover. And expo is really neat.

---

### Post by clixis on 2008-05-16
Well, I finally got the cube working - sort of - after about the fourth try. I don't know what I did differently. I can rotate the desktops with the keyboard or the mouse, but as of yet I don't see the entire cube - it's the size of the screen, not smaller like in the compiz demos on YouTube. I'll figure that out later.

As for simple-ccsm, that was already installed. I couldn't find it in any of the package lists, however.

Thanks for the help.

---

### Post by philinux on 2008-05-16
Press ctrl Alt and left mouse to rotate the 3d cube when in an app.

If showing desktop use can press and hold scroll wheel to move it round

This is mine.

---

### Post by mc4man on 2008-05-16
> it's the size of the screen, not smaller like in the compiz demos 
try, in ccsm click on rotate cube and adjust the zoom setting

---

### Post by barney385 on 2008-05-16
Kewl, thanks for the demonstration Phillinux.
 
:smile:

---

### Post by vaensterhaent on 2008-05-16
hi! I'm a noewbie as well, where can i download compiz? what's the code that I can write in inside "Terminal"?

---

### Post by philinux on 2008-05-16
Compiz is installed by default in 8.04 Hardy.

But some weird reason compizconfig settings manager isn't.

---

### Post by bouta on 2008-05-16
i am a newbie at linux..i just opened add/remove in application..searched for compiz ..installed advance desktop effect setting and compiz fusion icon.then opened advanced desktop from system>preferences. and configured the cube thingy..oh i dont have a video card too ..and it works perfect without a glitch

---

