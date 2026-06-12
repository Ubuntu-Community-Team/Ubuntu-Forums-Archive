---
title: "[SOLVED] upgrading from 8.04 to 8.10"
date: 2008-11-21
forum: New to Ubuntu
---

### Post by leemajors on 2008-11-21
hi there,

i followed the instructions for upgrading from 8.04 to 8.10 from here:

[http://www.ubuntu.com/getubuntu/upgrading](http://www.ubuntu.com/getubuntu/upgrading)

everything went smoothly as far as i could see (no errors or any issues) until it came to restarting -- the ubuntu loading graphic comes up but it doesn't load the graphical interface any more.

instead i'm presented with a console with a few error messages, the one i can remember at this stage is "unable to find resume image, proceeding with normal boot." 

at which point I'm just given a login prompt. I can login fine, and issue commands and sudo to issue the "reboot" command but no GUI.

any tips? happy to post more error messages if useful.

---

### Post by bobnutfield on 2008-11-21
Try:

> sudo /etc/init.d/gdm start

If it does not work, post back the errors messages.

---

### Post by cancerdude on 2008-11-21
startx or sudo startx

---

### Post by jimreynold2nd on 2008-11-21
What I can think of is that you installed nvidia or ATI driver by downloading the driver from nvidia or ati website then install. Upgrading from 8.04 to 8.10 updates the kernel and the kernel interface compiled when you install the drivers no longer works.
What you can do is reinstall the display driver by hand (like you did) or preferable via apt (so that it can be automatically upgraded with the kernel next time).

---

### Post by leemajors on 2008-11-21
> 
Try:
sudo /etc/init.d/gdm start 


OK, when I try that I get:

Starting GNOME Display Manager... [OK]

and then am just given the prompt again.

an interesting thing to note is when it was first booting up I saw an error message I hadn't seen before. It flashed up only briefly, so I can't tell you what it said but it began with "BUG!" 

after trying your initial suggestion I rebooted a few times to see the error message again but so far it's not shown up again.

---

### Post by bobnutfield on 2008-11-21
OK, just as jimreynold2nd suggested, I wanted to see the error messages because I blelieve as well it is just a matter of your video driver being incompatible with the new version of Ubuntu.  If you do type "startx", you will probably get an error message that says you have screens available, but none have a configuration.

Check in /etc/X11/xorg.conf to see what video driver is loaded.  If it is nVidia or fglrx, you will need to change it to vesa temporarily to get a desktop back.  Once you have a desktop, you can reinstall the proprietory drivers.

---

### Post by leemajors on 2008-11-21
Sorry, I forgot to post the other messages I see when I first boot up:

kinit: name_to_dev_t(/dev/disk/by-uuid/some-huge-hash-id)=dev(8,4)
kinit: trying to resume from /dev/disk/by-uuid/some-huge-hash-id

then just with the unable to resume message.

I will look at the other suggestions here as well and try and gather some more information.

---

### Post by leemajors on 2008-11-21
bobnutfield, when i tried startx it told me there were no screens.

having a look through xorg.conf, the "Configured Video Device" was "fglrx"

not sure how to fix this. I do remember, when first installing 8.04, having to choose another device to allow me to change screen resolution, but i wouldn't have a clue how to rectify this without having a GUI to help me :)

any further suggestions on how to continue would be greatly appreciated!

---

### Post by jimreynold2nd on 2008-11-21
Well... did you try reinstalling the video driver?

---

### Post by leemajors on 2008-11-21
> **jimreynold2nd said:**
> Well... did you try reinstalling the video driver?

unfortunately, without the GUI, I wouldn't even know where to begin. how would i go about doing that?

---

### Post by bodhi.zazen on 2008-11-21
> **leemajors said:**
> OK, when I try that I get:

Starting GNOME Display Manager... [OK]

and then am just given the prompt again.

Hit Ctrl-Alt-F7 to get to the GUI interface. Post any errors.

---

### Post by jimreynold2nd on 2008-11-21
You didn't tell me which graphic card you use, but this error is common on nvidia's so I am guessing you use nvidia...
1) login
2) at command prompt, type 'sudo apt-get install nvidia-glx'
3) restart
4) login again, this time do 'sudo nvidia-xconfig'. Restart.

---

### Post by leemajors on 2008-11-21
> **bodhi.zazen said:**
> Hit Ctrl-Alt-F7 to get to the GUI interface. Post any errors.

no errors -- just a blank screen with a flashing cursor at the top left.

---

### Post by leemajors on 2008-11-21
> **jimreynold2nd said:**
> You didn't tell me which graphic card you use, but this error is common on nvidia's so I am guessing you use nvidia...


Sorry, hadn't noticed your asking me what graphic card I use.

It's an ATI Mobility Radeon 9600 Pro Turbo, with (I think) 128 mb of RAM. Running on a Dell Inspiron 8600 (laptop) with 2gigs of RAM. So, not nvidia.

---

### Post by leemajors on 2008-11-21
any further advice for this problem? apologies for the bump but i can't use my computer at the moment :(

---

### Post by bodhi.zazen on 2008-11-22
> **leemajors said:**
> any further advice for this problem? apologies for the bump but i can't use my computer at the moment :(

Looks like a bug, I do not know if there is a fix.

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/284408)

---

### Post by jimreynold2nd on 2008-11-22
Uhh... sorry. Its gonna be sudo apt-get 'something', but I never used ATi so I dunno which package to install.

:(

---

### Post by leemajors on 2008-11-22
[QUOTE=bodhi.zazen;6227904]Looks like a bug, I do not know if there is a fix.

oh dear! 

when you say there might not be a fix, do you mean a fix to the current situation or might there be a way to revert to a more generic video card?

Having a look through that bug page, it seems I might be able to fix by disabling the "fglrx" driver and instead use the freee drivers.

Could someone with more Ubuntu knowledge than me possibly let me know how I might go about doing this? I would greatly appreciate it!

:)

UPDATE: I removed the fglrx driver by using sudo apt-get remove xorg-driver-fglrx, but still no luck when trying to start the gui.

---

### Post by davec64 on 2008-11-22
Try reinstalling FGLRX.

Once installed:```
dpkg-reconfigure -phigh xserver-xorg
```

Make choices that are suitable for your graphics card.

Then:

```
aticonfig --initial
```

if this doesn't work you haven't lost anything!

To me it sounds like your xorg configuration might have got screwed initially.:)

---

### Post by davec64 on 2008-11-22
Just found an installation li9ink hat might help:

[https://help.ubuntu.com/community/BinaryDriverHowto/ATI]("https://help.ubuntu.com/community/BinaryDriverHowto/ATI")

---

### Post by leemajors on 2008-11-22
> **davec64 said:**
> Just found an installation li9ink hat might help:


thanks, do you think i should reinstall the fglrx driver or install the open source ATI driver?

---

### Post by leemajors on 2008-11-22
in the meantime i tried to reinstall the fglrx driver. it won't let me, saying:

"overwriting possibly customised configuration file. backup in /etc/path.to.xorg.conf.2008date."

---

### Post by louieb on 2008-11-22
Have you tried booting to recovery mode and chose the xfix option?

Another thing to try is choose the old kernel and boot it just to see if you get the GUI.

---

### Post by bodhi.zazen on 2008-11-22
> **leemajors said:**
> in the meantime i tried to reinstall the fglrx driver. it won't let me, saying:

"overwriting possibly customised configuration file. backup in /etc/path.to.xorg.conf.2008date."

That is a normal message, it is just telling you ti backed up the old config file.

Go ahead and try re-starting X :

```
sudo /etc/init.d/gdm stop
sudo /etc/init.d/gdm start
```

---

### Post by msenn on 2008-11-22
i agree with louieb:  try starting in recovery mode then running "xfix".  you'll probably have to reconfigure what ever video settings you were using before.  it worked for me.

---

### Post by leemajors on 2008-11-25
hooray!

thanks to all who helped with this problem.

in the end, after removing the fglrx driver and reinstalling it, a simple boot to recovery mode and running xfix has solved the problem.

i still have yet to boot up normally, but everythings working nicely and i've got my computer back so i'm happy :D

thanks again everyone!

---

