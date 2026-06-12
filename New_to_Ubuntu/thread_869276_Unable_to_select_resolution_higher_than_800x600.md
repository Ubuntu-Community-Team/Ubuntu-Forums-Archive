---
title: "Unable to select resolution higher than 800x600"
date: 2008-07-24
forum: New to Ubuntu
---

### Post by rorschak on 2008-07-24
Fresh install on an empty laptop with a 1280x800 screen.

When I go into System->Preferences->Screen Resolution my choice is either 800x600 or 640x480.

The graphics card is Sis Mirage 3+ 256MB.

---

### Post by appi2012 on 2008-07-24
You might give the instructions on the bottom of this page a shot:
[https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC)

---

### Post by rockstarrem on 2008-07-24
Go to System > Administration > Hardware Drivers. If you see a checkbox that ISN'T checked next to a proprietary driver then go ahead and check it and apply it. Restart the computer and screw with the resolution again.

---

### Post by rorschak on 2008-07-24
> **rockstarrem said:**
> Go to System > Administration > Hardware Drivers. If you see a checkbox that ISN'T checked next to a proprietary driver then go ahead and check it and apply it. Restart the computer and screw with the resolution again.

Hardware Drivers doesn't list a single driver. That's probably the problem.

---

### Post by rockstarrem on 2008-07-24
Did you try the link appi gave you? [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC)

---

### Post by koji042 on 2008-07-24
I think the problem is that your computer can't properly detect the screen settings.

In that case, what you do is go to Places > Computer > Filesystem > usr > share > applications and find the application called "Screens and Graphics"

From there, just go to Generic and find "LCD Panel 1280x800".
It should work after that.

Hope that helps. :)

---

### Post by rorschak on 2008-07-24
> **rockstarrem said:**
> Did you try the link appi gave you? [https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC](https://wiki.ubuntu.com/LaptopTestingTeam/AcerAspire3002WLC)

Yes, I gave it 3-4 tries. Everytime it exited late in the keyboard config phase, with a warning about having overwritten a setting.

---

### Post by northern lights on 2008-07-24
Okay, try this:

First, let's backup your current xorg.conf```
cp /etc/X11/xorg.conf /etc/X11/xorg.backup
```

Now, let's reconfigure the xserver:

Run ```
sudo /etc/init.d/gdm stop
``` from a terminal. You will be leaving the graphical environment, so remember the next two steps!

Press Alt+F1 to log in and execute ```
sudo dpkg-reconfigure -phigh xserver-xorg
```

Then restart the interface with ```
sudo /etc/init.d/gdm start
```

Try to change resolution again.

In case something gets (even more) screwed, revert back with```
cp /etc/X11/xorg.backup /etc/X11/xorg.conf
```

---

### Post by philinux on 2008-07-24
Try using this in a terminal.

gksu displayconfig-gtk

---

### Post by rorschak on 2008-07-24
In the
  sudo dpkg-reconfigure -phigh xserver-xorg
step it fails with
  xserver-xorg postinst warning: overwriting possibly-customised configuration file; backup in /etc/X11/xorg.conf.<date>

It doesn't seem to change anything.

---

### Post by rorschak on 2008-07-24
> **philinux said:**
> Try using this in a terminal.

gksu displayconfig-gtk

That is essentially the same hint as the one koji042 came with earlier. It looks promising, but when I test the higher resolution, it clearly doesn't work.

I'm afraid the problem is on a more fundemental level.

---

### Post by philinux on 2008-07-24
I have a feeling the integrated video card is not supported.

---

### Post by northern lights on 2008-07-25
> **philinux said:**
> I have a feeling the integrated video card is not supported.
me too.

Can you please post the output of ```
sudo lshw -C display
```
Thank you.

---

### Post by coffeecat on 2008-07-25
> **rorschak said:**
> I'm afraid the problem is on a more fundemental level.

It's probably that SiS graphics. I've no experience of SiS but from what I've read it's best avoided when using Linux. It might be worth googling that particular graphics card - and searching the forum - but I wouldn't hold out much hope. I came across a thread on another forum where someone with a different laptop but the same SiS graphics couldn't even boot up into the Ubuntu CD, nor any other distro's CD.

---

### Post by mingle on 2008-07-25
Hi,

Try what Philinux suggests. I had the same issue.

When the Display-Config GUI appears you should be able to select the correct display size under the appropriate tab.

Cheers,

Mike.

---

### Post by rorschak on 2008-07-25
> **northern lights said:**
> Can you please post the output of ```
sudo lshw -C display
```
Thank you.

  *-display UNCLAIMED     
[INDENT]       description: VGA compatible controller
       product: 771/671 PCIE VGA Display Adapter
       vendor: Silicon Integrated Systems [SiS]
       physical id: 0
       bus info: pci@0000:01:00.0
       version: 10
       width: 32 bits
       clock: 66MHz
       capabilities: pm agp agp-3.0 vga_controller cap_list
       configuration: latency=0[/INDENT]

---

### Post by rorschak on 2008-07-25
> **coffeecat said:**
> It's probably that SiS graphics. I've no experience of SiS but from what I've read it's best avoided when using Linux. It might be worth googling that particular graphics card - and searching the forum - but I wouldn't hold out much hope. I came across a thread on another forum where someone with a different laptop but the same SiS graphics couldn't even boot up into the Ubuntu CD, nor any other distro's CD.

That is very depressing reading.

---

### Post by northern lights on 2008-07-25
> **philinux said:**
> I have a feeling the integrated video card is not supported.

I ain't a feeling anymore - it's not supported indeed.

In the repos, there's no driver better than VESA for the SiS 771/671.

Apparently, SiS does have linux drivers for their 3D chipsets, but only makes them available for their own R&D and their customers (i.e. motherboard manufacturers, not to the end user). Don't ask me why. Corporate dicks.

Also, this SiS R&D employee Barros has publicized the source of a 2D driver at least. This guy Dennis, himself owner of a laptop with the chipset, has collected all sorts of version of this source (compiled for 32/64bit and various distros) [here]("http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x").

You'll get hi-res, but I don't see you enabling 3D in linux.

Start hating on SiS...

[EDIT]
If you're interested in the history of this accumulation, check [http://ubuntuforums.org/showthread.php?p=4232057]("http://ubuntuforums.org/showthread.php?p=4232057")
[/EDIT]

---

### Post by rorschak on 2008-07-25
> **northern lights said:**
> 

Also, this SiS R&D employee Barros has publicized the source of a 2D driver at least. This guy Dennis, himself owner of a laptop with the chipset, has collected all sorts of version of this source (compiled for 32/64bit and various distros) [here]("http://ncc-1701a.homelinux.net/WikiBerd/index.php?page=LinuxSis67x").


I followed the directions on how to modify xorg.conf and rebooted. On the first try the laptop started up in a panic mode, where I had to select screen size. It then went into 800x600. I rebooted again, the startup was clean, and I could now select 1280x800 in System -> Preferences -> Screen Resolution.

The screen is now usable. Fantastic.

---

