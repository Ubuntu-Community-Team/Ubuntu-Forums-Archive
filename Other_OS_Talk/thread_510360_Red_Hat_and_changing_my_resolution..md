---
title: "Red Hat and changing my resolution."
date: 2007-07-26
forum: Other OS Talk
---

### Post by Roasted on 2007-07-26
We're running Red Hat at school for a security class. In my display settings, I have a lot of options for screen resolution. However, whenever I make changes, nothing saves. I've tried logging on and off with the checkbox "save current setup" checked and unchecked, as well as restarted the computer with the checkbox checked and unchecked as well.

AKA, I've tried everything I could think of. Yet, nothing works. It even recognizes my graphics card. How can I change the resolution?

---

### Post by dca on 2007-07-26
check your /etc/X11/xorg.conf file...  Look under:  Section "Screen" and see what resolutions set at...  If you still  run into problems you can also try the Fedora forums because RH is built on it...

---

### Post by Roasted on 2007-07-26
I checked out the XF86Config file, and under "modes" all that's there is 800x600 and 480x640. I brought it up in VI mode, and after hitting I to insert new text and putting 1280x1024 there, it still won't work. Even after saving it and rebooting.

It's seriously mind numbing how stupid this is. If I save the option and select it, WHY would it revert back? Why can't my school just use Ubuntu...

---

### Post by igknighted on 2007-07-26
> **Roasted said:**
> I checked out the XF86Config file, and under "modes" all that's there is 800x600 and 480x640. I brought it up in VI mode, and after hitting I to insert new text and putting 1280x1024 there, it still won't work. Even after saving it and rebooting.

It's seriously mind numbing how stupid this is. If I save the option and select it, WHY would it revert back? Why can't my school just use Ubuntu...

What version of Red Hat?  I would go to the forum of the corresponding version of CentOS.  CentOS IS RHEL, 100% binary compatible.  It just has no RHEL logos.

I would look up in your monitor's handbook what the proper sync rates are and add those in to the config file in the monitor section, mine looks like this: 
```
Section "Monitor"
        Identifier   "Monitor0"
        VendorName   "Unknown"
        ModelName    "Unknown"
        HorizSync    30 - 79
        VertRefresh  56 - 75
        Option      "DPMS"
EndSection
```.  Also, what is your HW like?  Graphics adapter, driver being used, monitor size/desired res etc.

---

### Post by Roasted on 2007-07-27
The computer I was on I believe had an Intel 865 or something for the graphics card.

We all had to install Red Hat. Some of the other students selected their desired resolution during the install. I did not. However, even though Red Hat could recognize my graphics card and proper drivers, it was unable to change the resolution to anything BUT the default resolution of 800x600. Quite frankly, I thought that was garbage. Ubuntu does it just fine, as well as Suse, and in my opinion Suse sucks. I was very surprised to see Red Hat didn't do it as easily. :(

---

