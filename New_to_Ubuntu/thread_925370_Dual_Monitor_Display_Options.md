---
title: "Dual Monitor Display Options"
date: 2008-09-20
forum: New to Ubuntu
---

### Post by Keytard on 2008-09-20
I'm a new Ubuntu user (Hardy Heron 8.04), coming from Vista.

I've got two monitors but I can't get them to do any kind of "extended desktop" like functions. I can get them to display the same thing, but not to be extensions of one desktop.

I've searched the forums and tried a bunch of things (including installing nvidia drivers) but the only result was that desktop effects no longer worked.

Any help would be great, and I'm not super techy so limiting jargon would be appreciated.

---

### Post by howefield on 2008-09-20
have you installed nvidia-settings ?

Makes setting up two monitors a breeze.

In terminal type
```
sudo apt-get install nvidia-settings
```

Once installed, again in terminal type
```
gksudo nvidia-settings
```

and configure accordingly. (Extended desktop is twinview)

---

### Post by Keytard on 2008-09-20
That didn't work. It wanted me to do an "x config" so I took a stab at that, but it didn't go well. This is what I ended up with

[http://i483.photobucket.com/albums/rr194/Keytard_photos/Screenshot.png](http://i483.photobucket.com/albums/rr194/Keytard_photos/Screenshot.png)
Where did I go wrong?

---

### Post by Keytard on 2008-09-20
I've done something wrong and completely ****** up.

I tried to install the X-config, and now my computer doesn't know any of my displays. Its treating it like I've got one "unknown" 800x600 display. And when I restart it says something like "graphics not working" and it wants to use "low graphics mode" or something along those lines. Then it asks me what my display is (at this point I don't have any additional monitor hooked up, just my laptop). And so I tell it what my monitor is Acer Aspire 5610 (its listed in the available options) and what my graphics card is (Intel Graphics Media Accelerator GMA 950, which seems to be on the list). But it still thinks that I have the 800x600 "unknown" monitor.

It seems that no combination of installing, uninstalling, reinstalling, updating, or restarting my computer has fixed this. I don't know what to do.

---

### Post by overdrank on 2008-09-20
> **Keytard said:**
> I've done something wrong and completely ****** up.

I tried to install the X-config, and now my computer doesn't know any of my displays. Its treating it like I've got one "unknown" 800x600 display. And when I restart it says something like "graphics not working" and it wants to use "low graphics mode" or something along those lines. Then it asks me what my display is (at this point I don't have any additional monitor hooked up, just my laptop). And so I tell it what my monitor is Acer Aspire 5610 (its listed in the available options) and what my graphics card is (Intel Graphics Media Accelerator GMA 950, which seems to be on the list). But it still thinks that I have the 800x600 "unknown" monitor.

It seems that no combination of installing, uninstalling, reinstalling, updating, or restarting my computer has fixed this. I don't know what to do.

Hi and I am a little confused. Why are you installing the nvidia drivers if your graphics card is intel?

---

### Post by Keytard on 2008-09-21
Because I have no idea what I'm doing.

---

### Post by rustutzman on 2008-09-21
See if this helps [http://ubuntuforums.org/showthread.php?t=221174](http://ubuntuforums.org/showthread.php?t=221174)

Russ

---

### Post by Keytard on 2008-09-21
Success! Thanks for your help!

---

### Post by jimmy the saint on 2008-09-21
One thing to consider:  Are the monitors of equal resolution?  If not, you will find yourself with dead space and icons and windows that wind up existing in the ether.  One solution for this is to use xubuntu, because Xfce4 does a better job handling dual monitor setups than does Gnome.

---

