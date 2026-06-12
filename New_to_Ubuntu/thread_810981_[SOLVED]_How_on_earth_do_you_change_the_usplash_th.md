---
title: "[SOLVED] How on earth do you change the usplash theme."
date: 2008-05-28
forum: New to Ubuntu
---

### Post by philinux on 2008-05-28
startupmanager fails to install it. I've got 4 different theme-etc.so files in /usr/lib/usplash.

This fails

sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.

So I'm stuck with the default ubuntu usplash.

---

### Post by bwhite82 on 2008-05-28
Here's a gui:

sudo apt-get install startupmanager

---

### Post by doorknob60 on 2008-05-28
```
sudo apt-get install startupmanager
```

Then it makes an entry in System>Admin for you :)

EDIT: Gosh dangit too late -.-

---

### Post by philinux on 2008-05-28
> **Soldierboy said:**
> Here's a gui:

sudo apt-get install startupmanager

Errr read the first post sorry. :confused:
startupmanager fails to install it.

---

### Post by stchman on 2008-05-28
> **philinux said:**
> startupmanager fails to install it. I've got 4 different theme-etc.so files in /usr/lib/usplash.

This fails

sudo update-alternatives --config usplash-artwork.so

There is only 1 program which provides usplash-artwork.so
(/usr/lib/usplash/usplash-theme-ubuntu.so). Nothing to configure.

So I'm stuck with the default ubuntu usplash.

You can also install the gnome-splashscreen-manager as that will give you control of the graphic that appears after you log on.

---

### Post by philinux on 2008-05-28
Not the same thing at all. Thats the one between login and desktop.
Poor to say the least as it flashes an image at you for milliseconds but you get darkness before and after.

---

### Post by bwhite82 on 2008-05-28
So the file-name of the theme is usplash-artwork.so? Or is it something else. If its something else, then that should be put on the end instead.

---

### Post by philinux on 2008-05-28
This must make sense to somebody

---

### Post by bwhite82 on 2008-05-28
Yeah so...
sudo update-alternatives --config usplash-theme-fingerprint.so

---

### Post by philinux on 2008-05-28
Look I've been through this loop before.

 sudo update-alternatives --config usplash-theme-fingerprint.so
[sudo] password for philcb: 
No alternatives for usplash-theme-fingerprint.so.

---

### Post by bwhite82 on 2008-05-28
Try copying them to /etc/alternatives and re-run the command.

---

### Post by philinux on 2008-05-28
I know what you saying but thats not what the instructions are.

Sum fails I've reported it at launchepad

Bedtime here too cheers. Thanks for the effort.

---

### Post by bwhite82 on 2008-05-28
Also, have you tried the theme's instructions here?

[https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765](https://sourceforge.net/docman/display_doc.php?docid=40914&group_id=187765)

---

### Post by philinux on 2008-05-29
```
sudo update-alternatives --install /usr/lib/usplash/usplash-artwork.so usplash-artwork.so /usr/lib/usplash/usplash-theme-fingerprint.so 10

sudo update-alternatives --config usplash-artwork.so

sudo update-initramfs -u

```

Seems to have worked - time to reboot.

Other themes suggest using startupmanager which fails and leaves you with the default.

If I use the commands above to select a different usplash it fails. Odd

Now - how do we get rid of the solid colour background you have to stare at for 15 seconds after logging in.

---

### Post by bwhite82 on 2008-05-29
> Now - how do we get rid of the solid colour background you have to stare at for 15 seconds after logging in.

After some research, it appears that setting is hard coded. I mean changing the color is easy (as you know), but getting rid of it altogether is another matter entirely. I also presume to think that even if you got rid of it, your screen would default to X's black because gnome is not yet loaded. At any rate, you can mess with the settings in this file:

/etc/gdm/PreSession/Default

---

### Post by philinux on 2008-05-29
I've now got the fingerprint usplash loaded. Nice. 

Startupmanager now seems borked as well. Removed it and reinstalled. It doesn't seem to like anything other than the default usplash.


I've set my background colour to black. Saves getting colour changes.

black 7 sec, image for 1 sec, black for 7 seconds.

Now it's just black for 15 seconds. :lolflag:

---

