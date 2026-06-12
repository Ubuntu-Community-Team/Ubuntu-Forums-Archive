---
title: "Nvidia Geforce2 Configuration"
date: 2008-11-04
forum: New to Ubuntu
---

### Post by lenordbater on 2008-11-04
I'm running a fresh install of 8.10.  So far everything's working except for my graphics card.  lspci gives me: 

```
 nVidia Corporation NV11 [GeForce2 MX/MX 400] (rev b2)

```

Which should require the Nvidia legacy drivers, but that package has apparently changed. 

When I go to system>administration>Hardware Drivers, I get the message: "No Proprietary Drivers Are In Use On This System" 

What do I need to do to get Nvidia's proprietary driver installed and working on this machine? 

Thanks!

---

### Post by lenordbater on 2008-11-04
Update: After using EnvyNG, I get the message, "Nvidia 71.86.04  [failed]" on boot, and then "Ubuntu is running in low-graphics mode".   I tried using Nvidia 96.43.05 and got the same results.  

I seem to have made the problem worse.  Now that's progress.

---

### Post by lenordbater on 2008-11-04
So now I've removed the Nvidia drivers alltogether, but I'm stuck in 1024 x 768, instead of the beautiful 1920 x 1080 that I had after my clean install - before I started trying for 3d acceleration.  

I tried: sudo dpkg-reconfigure -phigh xserver-xorg, but still either get the "Low Graphics Mode" or a straight boot into 1024 x 768 mode, and of course I have no options under System>Preference>Screen Resolution except for even lower resolutions.  

Any suggestions on either going back to the original configuration, or getting the nvidia legacy drivers working?

---

### Post by Elfy on 2008-11-04
Lets try and sort it then - the legacy drivers were in the release notes as being a problem - nvidia's that is.

Do this - open software sources in the System Admin menu - go to the updates tab and enable proposed, close and reload as it requires.

Now run update manager in System Admin menu - you should see an update for jockey and possibly an update to 96.43.09 , if they are there update - check the other proposed updates as they could possibly cause you a problem - I have not had any though.

Once that has done - you're card should work properly, I would check that xorg has the addargb line.

You might though need the 71 driver not sure for your card - there are a bunch of bug reports, this one is getting the most attention [https://bugs.launchpad.net/bugs/251107](https://bugs.launchpad.net/bugs/251107)

---

### Post by lenordbater on 2008-11-04
Thanks for the help.  I followed your suggestions, and upgraded to the beta version of the Nvidia drivers.  After following some of the xorg.conf instructions on the bug report thread, I still had no luck.  

So, I thought, what the hell, I'll just change my driver back to nv in my xorg.conf and - while I won't have 3d acceleration, I'll at least have my resolution back.  I was wrong - after changing the driver line under "device", I still boot onto "Low Graphics Mode".  

Any other suggestions?  Is there a way to get Ubuntu to re-detect my graphics hardware like it did in the initial install?

---

### Post by Elfy on 2008-11-04
Make copy of xorg ```
sudo cp /etc/X11/xorg.conf /etc/X11/xorg.conf.0511
```

Then I would uninstall nvidia with synaptic and reboot into recovery mode - use the menu to run xfix and then resume.

You'll now be running with vesa - go backto synaptic and install 96.43.09 - if you are only seeing 96.43.05 make sure you have proposed enabled and all updates/upgrades done.

That should do it I think,

---

