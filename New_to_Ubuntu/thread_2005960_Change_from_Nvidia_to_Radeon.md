---
title: "Change from Nvidia to Radeon"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by Drowz0r on 2012-06-18
Hello everyone

I've recently changed from an Nvidia GeForce 8800GT512MB card to a Radeon HD 6870 card. I checked to see if the Radeon was compatible and had drivers first, which it does. I also run dual screens.

My issue is, I plugged the new card in and booted up ubuntu, and it gets throught the bios and everything fine (on both screens) then goes to the purple screen before the ubuntu loader, then it just goes black and doesn't boot my desktop up.

I run off my ubuntu disc and both displays run fine. So it seems I need to run off some kind of basic driver or tell the ubuntu on my hard drive to use different drivers. I guess there is a "safe mode" or something I go into? Or something I can do from the disc?

I'm running and typing to you all on the disc version now... so all hardware checks out ok.

Thanks in advance all.

---

### Post by QIII on 2012-06-18
Did you first uninstall the NVIDIA driver? If you didn't, that is more than likely the problem.  You need to uninstall drivers *before *you remove a graphics card and replace it with another OEM's card.

The NVIDIA driver can be uninstalled and the ATI driver installed in recovery mode, if need be.

See my signature.

To get to recovery mode in a useful way,  select recovery mode, then select networking in the recovery menu.  That will get you access to the web and mount your drive as read write.  Type exit.

When you get back to the recovery menu, select Root with Networking.  Remember that you will be running with Root access, so be very careful.

Uninstall the NVIDIA driver from the command line

Then follow the instructions in the link in my signature.  Print a copy of the initial post from another computer if need be.

---

### Post by Drowz0r on 2012-06-18
> **QIII said:**
> Did you first uninstall the NVIDIA driver?

No I don't really know how. I can't uninstall the NVIDIA driver with the NVIDIA card in it can I? And it doesn't even boot into my desktop with the radeon card so I can't install anything that way.  When putting the ubuntu CD in I can run off that using some kind of  default(?) driver but that's as far as I've got. Can I install stuff like that?
> **QIII said:**
> 
The driver can be installed in recovery mode, if need be.

See my signature.


Which link? There is one on how to install ATI drivers but it doesn't detail how to get into recovery mode.

> **QIII said:**
> 
To get to recovery mode in a useful way,  select recovery mode, then  select networking in the recovery menu.  That will get you access to the  web and mount your drive as read write.  Type exit.


Where do I select recovery mode? o.o From booting on the CD or some kind of grub boot menu or something? Do I click something on start up?

> **QIII said:**
> 

When you get back to the recovery menu, select Root with Networking.   Remember that you will be running with Root access, so be very careful.

Then follow the instructions in the link in my signature.  Print a copy  of the initial post from another computer if need be.

I'll run it off my tablet and do it that way. Seems safest :)

Thanks for your reply. Any chance on answers to the above?

---

### Post by QIII on 2012-06-18
If you still have the NVIDIA card, it might be easier to start over by putting it back in.

> **Drowz0r said:**
> No I don't really know how. I can't uninstall the NVIDIA driver with the NVIDIA card in it can I?

Yes, you can.  That might be easier, since you can do that from the Additional Drivers functionality.  On rebooting after uninstalling the NVIDIA driver, you would revert to the open source driver.  However, you might find yourself needing to use the "nomodeset" kernel option, which we can talk you through.  But it would probably be easier if you uninstall the driver, shut down, remove the NVIDIA card, install the ATI card and reboot, you should start with the default open source driver for your ATI card.

>  And it doesn't even boot into my desktop with the radeon card so I can't install anything that way.  When putting the ubuntu CD in I can run off that using some kind of  default(?) driver but that's as far as I've got. Can I install stuff like that? Where do I select recovery mode? o.o From booting on the CD or some kind  of grub boot menu or something? Do I click something on start up?If you hold down the space bar as you boot up, you will be presented  with the GRUB menu and you can boot to recovery mode from there.  However, if you still have the NVIDIA card, booting with it installed and removing the driver with the graphical tools might be easier.

> Which link? There is one on how to install ATI drivers but it doesn't detail how to get into recovery mode.I described how to get into recovery mode above.  However, if you put the NVIDIA card back in, you may be able to boot without issues and avoid the recovery mode completely when uninstalling the NVIDIA driver.

> I'll run it off my tablet and do it that way. Seems safest :)Not quite sure how you intend to do that.  Get the NVIDIA card back in.  Uninstall the driver. Shut down.  Put the ATI card in. Reboot.   It should start with the default driver.  Then, follow the instructions in my signature.

---

### Post by Dlambert on 2012-06-18
If it's possible I would just recommend a fresh install.

---

### Post by sffvba[e0rt on 2012-06-18
Running a Radeon HD 6850...

On boot-up hold left shift.  When you get the GRUB menu, press e to edit it.  On the second last line (the one with something like "nosplash) add **nomodeset**... press ctrl+x to boot.

Once in on the desktop environment remove the additional drivers already installed (for nvidia)... then reboot following the same steps above for nomodeset, run the additional drivers utility again and install (not the post update because it normally doesn't work).

Then in a terminal run **sudo aticonfig --initial**.

Reboot and your done.


404

PS - And if I stop being so lazy I would have added this with screen shots to my blog ages ago :/

---

### Post by Drowz0r on 2012-06-18
Hello again

Ok guys, thanks. I'll give it a shot. I suppose a format is always a good plan B.

Thanks again!

---

### Post by QIII on 2012-06-18
> **Dlambert said:**
> If it's possible I would just recommend a fresh install.

The "Blast off and nuke 'em from orbit" method is entirely unnecessary.

---

### Post by QIII on 2012-06-18
> **not found said:**
> run the additional drivers utility again and install (not the post update because it normally doesn't work)./

With ATI, the Additional Drivers method does not always work well, but I do agree with the comment about avoiding the "...-updates" version.

---

### Post by Drowz0r on 2012-06-18
> **not found said:**
> Running a Radeon HD 6850...

On boot-up hold left shift.  When you get the GRUB menu, press e to edit it.  On the second last line (the one with something like "nosplash) add **nomodeset**... press ctrl+x to boot.



I did that, completely but it just takes me to a black screen with a blinking (text) cursor (like this _ ) at the top left of the screen and nothing happens.

Rebooted but just went back to how it was before.

Rebooted to get back into grub and it wouldn't.

Rebooted and went back into grub but it froze.

Rebooted again, got  into grub,pressed E for edit and found the line I edited is now missing.

---

### Post by QIII on 2012-06-18
The nomodeset only works for that one boot unless it is later made persistent.

Did you try just starting over by putting the NVIDIA card back in?

Edit:  I just saw your edits.

I'm at work so I can't give you detailed instructions, but in [this thread](http://ubuntuforums.org/showthread.php?t=1195275)  you should find instructions for reinstalling GRUB.

---

### Post by Drowz0r on 2012-06-18
> **QIII said:**
> 

If you hold down the space bar as you boot up, you will be presented  with the GRUB menu and you can boot to recovery mode from there.  However, if you still have the NVIDIA card, booting with it installed and removing the driver with the graphical tools might be easier.



I'm in recovery mode and I have four optons, resume normal boot, check all files, remount and drop to root shell prompt. I think the last one is the one I'm after but it just freezes and I can't select anything.

> **QIII said:**
> 

Not quite sure how you intend to do that.  Get the NVIDIA card back in.  Uninstall the driver. Shut down.  Put the ATI card in. Reboot.   It should start with the default driver.  Then, follow the instructions in my signature.

Look at your guide on my tablet, that is :)

I do have the NVIDIA card but it's in another machine atm, so swapping these cards around would take a while :c

---

### Post by Drowz0r on 2012-06-18
> **QIII said:**
> The nomodeset only works for that one boot unless it is later made persistent.

Did you try just starting over by putting the NVIDIA card back in?

Edit:  I just saw your edits.

I'm at work so I can't give you detailed instructions, but in [this thread]("http://ubuntuforums.org/showthread.php?t=1195275")  you should find instructions for reinstalling GRUB.

Managed to get my original card back, on loan for a little bit :)

It's in, just need to find out how to uninstall the drivers o.o

---

### Post by wyliecoyoteuk on 2012-06-18
Easy one, open the Dash and type "dri"
the "additional drivers" icon should pop up in the list. open it and select the highlighted driver, then click remove.
When completed, reboot, then shut down and swap the cards and boot up again.

---

### Post by Drowz0r on 2012-06-18
> **Drowz0r said:**
> Managed to get my original card back, on loan for a little bit :)

It's in, just need to find out how to uninstall the drivers o.o

Ok, uninstalled the additional drivers and rebooted.

It booted into the desktop and was all laggy. Seems right for missing drivers.

---

### Post by Drowz0r on 2012-06-18
> **wyliecoyoteuk said:**
> Easy one, open the Dash and type "dri"
the "additional drivers" icon should pop up in the list. open it and select the highlighted driver, then click remove.
When completed, reboot, then shut down and swap the cards and boot up again.


I did it through the software centre, uninstalling all additional drivers but thanks :)

---

### Post by Drowz0r on 2012-06-18
Ok so even after removing all additional drivers, after a reboot the screen stlll shows as black with my radeon card inserted and running ubuntu from my HDD but it works fine when running ubuntu from CD

---

### Post by Drowz0r on 2012-06-18
Ok, so I figured I'd go into the CD ubuntu mode thing again to get to some of my files and save them before just doing a format. Seems a lot easier than trying to sort this.

When I go in there I get an error when trying to access some folders. It says ""You do not have the permissions necessary to view the contents of "<folder name>"

Can someone help me get access to these folders so I can fix this please? :(

---

### Post by Drowz0r on 2012-06-18
> **QIII said:**
> The nomodeset only works for that one boot unless it is later made persistent.

Did you try just starting over by putting the NVIDIA card back in?

Edit:  I just saw your edits.

I'm at work so I can't give you detailed instructions, but in [this thread]("http://ubuntuforums.org/showthread.php?t=1195275")  you should find instructions for reinstalling GRUB.

Ok so I did a fresh format instead. When using the generic driver the card works but when using the driver detailed in the thread in your signature it doesn't work :(

When using the driver you show how to install, only one monitor will work at a time on split screen. Both monitors work on dual screen. When trying to use split screen I get an error "The selected configuration for displays could not be applied.
required virtual size does not fit available size: requested =(2560, 1024) minimum (320,200), maximum=(1280,1280)"

I don't understand :/

Also when trying to install the accelerated graphics I get this error:

E: Unable to locate package libva-egl1

---

### Post by Drowz0r on 2012-06-18
It's working, finally :O

Basically, after all the fiddling, it cost me a format and a few files but it's working now.

---

