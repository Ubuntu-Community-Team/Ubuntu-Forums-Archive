---
title: "[How to] Laptops with intel graphics - internal and external display fix"
date: 2007-06-04
forum: Outdated Tutorials &amp; Tips
---

### Post by Bluecircle on 2007-06-04
This should work for anyone using intel graphics on a laptop, who needs to use both an internal and external monitor with different resolutions.

I have a laptop with integrated intel graphics (i915). I have an internal 1366x768 display, and an external 1920x1200 display. I've found out that the i810 xorg driver will only work with the internal display, and the intel xorg driver will only work with the external display properly. So here is what I did:

First make 2 files in your home directory, one called internal, and one called external. Then paste this code into the files:

Internal:

```

#
# Change to display to internal LCD
#

clear

sudo /etc/init.d/gdm stop
sudo apt-get remove xserver-xorg-video-intel -y
sudo apt-get install xserver-xorg-video-i810 -y
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```

External:

```

#
# Change to display to external LCD
#

clear

sudo /etc/init.d/gdm stop
sudo apt-get remove xserver-xorg-video-i810 -y
sudo apt-get install xserver-xorg-video-intel -y
sudo dpkg-reconfigure -phigh xserver-xorg
sudo /etc/init.d/gdm start

```

Then go to the terminal and type this (if you are not in your home dir, cd to it):

```

chmod 775 internal
chmod 775 external

```

Now, whenever you are switching to the internal LCD go to TTY1 (CTRL+ALT+F1), and type "./internal", likewise do "./external for the external LCD.

Disclaimer: This works for me and my setup, but I have not tested it with any other system, so please give feedback on whether this works or not. Also I'm pretty new at this, so I probably did something the long way. ;)

---

### Post by Bluecircle on 2007-06-05
bump for missing the first page.

---

### Post by honeydew on 2007-06-14
can you possibly post your xorg.conf for external.. I also have the intel 915 and want to run the external on 1920x1200.. please help me with this! thanks =]

---

### Post by honeydew on 2007-06-14
Oh.. I have looked a little closer at what your script is doing.. thanks! I will try this tonight.

---

### Post by Bluecircle on 2007-06-14
Oh, I forgot to add, obviously when you run the script you want to select the correct driver. So when you run ./external, select "intel" and vise versa.

Also, this problem is fixed on Gutsy.

---

