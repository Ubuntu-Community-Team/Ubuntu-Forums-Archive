---
title: "Infamous 800x600 max resolution problem."
date: 2008-10-10
forum: New to Ubuntu
---

### Post by Jakey_TheSnake on 2008-10-10
As stated above. I'm running Hardy, I have checked Hardware Drivers and it says "No proprietary drivers are in use on this system". 

Please advise.

---

### Post by cam381 on 2008-10-10
Check the restricted drivers manager. These are drivers provided by your hardware and are proprietary. Ubuntu cannot offer support for this because they are not open-source. If there are none in use, then use the manager. Please post back.

---

### Post by SpenceMakesSense on 2008-10-10
try running 
```
gksu displayconfig-gtk
``` then changing the moniter type to a moniter with a larger max resolution

---

### Post by roger_1960 on 2008-10-10
Hi

Try in terminal:

sudo displayconfig-gtk  enter your password

then change "model" and resolution to suit your monitor.

---

### Post by Jakey_TheSnake on 2008-10-10
> **cam381 said:**
> Check the restricted drivers manager. These are drivers provided by your hardware and are proprietary. Ubuntu cannot offer support for this because they are not open-source. If there are none in use, then use the manager. Please post back.

Restricted drivers manager is not an option in Hardy, only Gutsy. 

And to the above two posters: I did try, selected my monitor model and increased resolutions became available, but upon pressing the test button the screen was (after a short delay) covered in a mesh with the dialog box open in top left asking me to keep or discard changes. I am reserved about selecting keep configuration because of this 'mesh'. 

I used the 'fglrxinfo' command in the terminal and got this out of it:

> display: :0.0  screen: 0
OpenGL vendor string: Mesa project: [www.mesa3d.org](www.mesa3d.org)
OpenGL renderer string: Mesa GLX Indirect
OpenGL version string: 1.4 (2.1 Mesa 7.0.3-rc2)


I'm thinking it's a graphics card issue. Well, pretty certain.

Oh, and I got this from the 'lspci' command:

> 01:05.0 VGA compatible controller: Matrox Graphics, Inc. MGA G400/G450 (rev 04)

I think my graphics card is Matrox, so I'm guessing this is right, but I don't quite understand the output of the fglrxinfo in relation to this.

---

### Post by Ryadt on 2008-10-10
Try ```
sudo dpkg-reconfigure xserver-xorg
```

Also Restricted Drivers is known as Hardware Drivers in Hardy.;)

---

### Post by Dave Otter on 2008-10-10
I did asd Roger_1960 suggested and at the stage the mesh appeared on the
screen I checked keep resolution.This worked fine

---

### Post by Jakey_TheSnake on 2008-10-10
> **Ryadt said:**
> Try ```
sudo dpkg-reconfigure xserver-xorg
```

Also Restricted Drivers is known as Hardware Drivers in Hardy.;)

If you read my first post you'd know I tried that and got nothing. This is what I mean by nothing: [http://img88.imageshack.us/img88/9236/screenshothardwaredrivecg0.png](http://img88.imageshack.us/img88/9236/screenshothardwaredrivecg0.png) ;)

I have no idea what that does, it's something to do with the keyboard though so :l

---

### Post by SteveNorman on 2008-10-10
what graphics card are you running? You will need to load drivers yourself for it.

---

### Post by Jakey_TheSnake on 2008-10-10
Matrox Millenium G400 DualHead. 

Monitor config changed correctly, and changed the graphics card option to match mine in the "gksu displayconfig-gtk" options thing. 

I've got to log out and then back in for changes to take affect, if you don't hear from me soon then it's failed.

---

### Post by Jakey_TheSnake on 2008-10-10
Well, it's worked, unfortunately for some reason on the login screen I'm only seeing the top quarter or so of it, very large. But once I log in the resolution is ow it should be. 

I'll try restarting and report back. 

If somebody could check whether there's any kind of updates for my graphics card driver though please... =) I will love you forever.

---

### Post by Jakey_TheSnake on 2008-10-10
And yes, okay, resolution is now fine, but I'm definitely only seeing the top left quarter of the login screen when it's up. Of course luckily there's not much clicking to do, but it would still be nice to have it displayed properly. Thoughts?

---

### Post by roger_1960 on 2008-10-10
Hi

Have a look at this post:

[http://ubuntuforums.org/showthread.php?t=933400](http://ubuntuforums.org/showthread.php?t=933400)

Second answer looks likely

---

### Post by Jakey_TheSnake on 2008-10-11
Thank you all, especially those I have thanked for their posts. 

This thread can be marked as solved now, I'm new here but I don't think regular users can do this even if they are the author.

---

### Post by roger_1960 on 2008-10-11
Hi

Glad it helped!

If you are the author and logged in you should be able to add "solved" by clicking on "thread tools" (in red) at the top of the post and selecting mark as solved.

---

