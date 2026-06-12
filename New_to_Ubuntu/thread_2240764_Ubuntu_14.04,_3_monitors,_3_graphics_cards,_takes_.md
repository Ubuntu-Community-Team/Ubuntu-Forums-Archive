---
title: "Ubuntu 14.04, 3 monitors, 3 graphics cards, takes ages to get desktop working"
date: 2014-08-22
forum: New to Ubuntu
---

### Post by mike231 on 2014-08-22
My first post.

I've go Ubuntu 14.04 with 3 monitors (all different) and 3 graphics cards all identical (RADEON HD 5450 - PCI Express 2.1 Bus Outputs: HDMI/ DVI/ VGA )

When I boot up it only ever starts up with one or two monitors  showing the login screen - very occasionaly 3.[/SIZE]

Then when I login again it's only one or two monitors active.

I go to the "Screen Display" in the GUI, all my monitors are there and identified - usually ( but not always )

I choose "Apply" and the monitors update, sometimes two become usable, sometimes one, on sometimes 3. Eventually if I keep Applying and restarting I'll get three useable monitors.

I had the same issue before I upgraded to 14.04 but to a lesser extent.

After upgrading I tried installing the proprietry Catalyst drivers for the cards but I had no joy with those so ubinstalled them.

I then tried disabling the gpu-manager
as suggested here: [https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489](https://bugs.launchpad.net/ubuntu/+source/ubuntu-drivers-common/+bug/1310489)

I figured out that /etc/X11/xorg.conf  has something to do with it, here's what mine looks like:

Section "Device"
    Identifier "Default Card 0"
    BusID "PCI:1@0:0:0"
EndSection


Section "Device"
    Identifier "Default Card 1"
    BusID "PCI:2@0:0:0"
EndSection


Section "Device"
    Identifier "Default Card 2"
    BusID "PCI:3@0:0:0"
EndSection


This never changes even when I mess with the GUI Display Settings - I feel like it should, shouldn't it?

Yesterday, it took me 2 hours of applying and rebooting to get a working environment. 2 hours!!


I've tried different combinations from my graphics cards: 2 monitors from 1, 1 from another; I've tried different outputs, dvi & hdmi. They are all currently on vga.

There must be an easier way?

Any clues, tips or ideas?

Cheers
Mike

---

### Post by mike231 on 2014-08-23
Hmmm... tumble weed...

maybe I'm asking in the wrong forum?

---

### Post by mike231 on 2014-08-27
My (unsatisfactory) solution.

Each time I log in I go to Screen Display (it never saves the settings) arrange the screens appropriately, click Apply, and see what happens.
I get mixed results, sometimes screens overlap across monitors, sometimes they are on top of each other, sometimes just one, two or all three monitors have desktops on them.
If the Screen Display settings fail I **sudo restart lightdm  **to restart X, and start again.
Eventually after between 5 and 15 minutes, I'll get a working environment.

There does not seem to be any pattern or logic to it.

Now I start every day annoyed!

---

### Post by mike231 on 2014-12-08
.... to avoid having to go through this rather than shutting down at the end of the day I just **suspend **rather than shutdown.

But I dread updates as I have to go through the whole process again.

---

### Post by mike231 on 2014-12-08
now i can only get to one of the screens if I move the cursor *really quickly*!

---

