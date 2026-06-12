---
title: "How to increase DPI?"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by Houmie on 2012-05-29
Hi,

I have installed lubuntu 12.04 and everything is too small. How can I increase the DPI please for better readability?

[-o<

Many Thanks,

---

### Post by fantab on 2012-05-29
You can do this from System Settings - Universal Access - Text Size

---

### Post by Houmie on 2012-05-30
> **fantab said:**
> You can do this from System Settings - Universal Access - Text Size

Well you can do this in Ubunto with Unity.

I can't find that in Lubuntu. :confused:

---

### Post by Houmie on 2012-05-31
Literally Lubuntu is using LXDE and I can't see a way to set the operating system's text size of the menus etc (DPI) a bigger value.

In Ubuntu its easily done through Universal Access. I don't seem to find the same option in Lubuntu. :(

---

### Post by shashanksingh on 2012-05-31
I just found [this]("http://askubuntu.com/questions/66224/how-to-change-the-screen-dpi-in-11-10")

Maybe the gnome-tweak-tool may help

---

### Post by fantab on 2012-05-31
> **Houmie said:**
> Literally Lubuntu is using LXDE and I can't see a way to set the operating system's text size of the menus etc (DPI) a bigger value.

In Ubuntu its easily done through Universal Access. I don't seem to find the same option in Lubuntu. :(

Read **[Here]("http://forum.lxde.org/viewtopic.php?f=24&t=1486")**

---

### Post by Rex Bouwense on 2012-05-31
Go to Preferences->Customize Look and Feel  and then change your default font to whatever you want it to be.

---

### Post by tchiri on 2012-06-08
If you have an Nvidia video card, you should have the file /etc/X11/xorg.conf.  In the Device section of this file, you can add the two Option lines to suit your need:

```

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    Option       "UseEDIDDpi" "False" #override the auto dpi
    Option         "DPI" "95 x 96" #change this to your liking
EndSection

```Hope this helps.  I found the info after an extensive search.

---

### Post by seppalta on 2012-06-08
First, go to **Preferences/Customize Look & Feel** (LXAppearance) and be sure the boxes labeled **hinting **and **antialising** are checked.    Other font adjustments can be made there as well as in **Preferences/Openbox Configuration**.

---

### Post by Ruhani04 on 2012-06-15
I have the same problem. I know it was possible to change the DPI in 11.10.
Not sure why they changed this. I will come back hopefully with an answer.
I am just surprised that some people replied without understanding the question.
And none of the answers really provide a solution.

---

### Post by singedwings on 2012-11-12
See bottom of this post for a solution

[http://forum.lxde.org/viewtopic.php?f=24&t=1486]("http://forum.lxde.org/viewtopic.php?f=24&t=1486")

No need to muck around with EDID settings etc :)

---

