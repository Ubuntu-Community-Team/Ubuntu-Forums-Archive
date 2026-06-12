---
title: "Installing Gimpshop"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by zaklinux on 2008-06-08
Okay, so I hear that there is a great free opensource photoediting software called Gimpshop and I decide to install Ubuntu 8.04 to try it out.

Got Ubuntu to install, but I'm not sure how to install applications. 

I read online that Deb packages are supposedly the easiest and so I  download a deb package from the Gimpshop website.

I double click on the file, install the package....and now what?

Where is my application? Should it not be under Applications > Graphics? 

I'm confused.

---

### Post by ChompTheMan on 2008-06-08
"GIMPshop is a modification of the free/open source GNU Image Manipulation Program (GIMP), intended to replicate the feel of Adobe Photoshop."

What you need is the actual program the GIMP.  GIMPshop changes the graphical user interface of the GIMP to more closely resemble Photoshop.  So install the GIMP by opening the Synaptic Package Manager and installing the GIMP from there or open up your terminal and type in:

```
sudo apt-get install gimp
```

You may also wish wish to install the package *gimp-data-extras*, as it comes with extra brushes, palletes, and gradients, and *gimp-gap* which contains packages for animations.

---

### Post by aysiu on 2008-06-08
Ubuntu already comes with GIMP.

GIMPShop is just a different-looking interface for the same application.

---

### Post by zaklinux on 2008-06-08
Oh okay. I get it.

Thanks for the quick reply.

So I think I need to take a step back. I don't think I installed it properly because Gimp looks the same as always. 

(I've removed my previous installation of gimpshop from the synaptic manager)

From the beginning:

1) Downloaded GIMPshop 2.2.8 Source from gimpshop.com
2) Extracted folder gimp-2.2.8 to desktop
3) .....?

Once again, I would appreciate any body's help.

---

### Post by zaklinux on 2008-06-08
Bump....

anyone?

---

### Post by zaklinux on 2008-06-08
Tried again using the deb package installer and I can confirm that its installed because I can see it in synaptic manager.

But my Gimp doesn't look any different.

Help?

---

### Post by zaklinux on 2008-06-08
tried 

*sudo apt-get install libtiff4 libtiff-tools*

as per the suggestion of another similar thread.

No dice. Still no change.

---

### Post by Blueball32 on 2009-02-18
If its still up to date:

Go to your terminal and simply write

> gimp

This brings up an install menu and starts gimpshop! ;)

---

