---
title: "Disable RAM card to save battery life"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by benpietras on 2013-09-13
Pretty much as said above. I've a 1x 2GB & 1x 8GB in my laptop and I'd like a way to toggle the 8GB stick on/off for more power/longer battery life.

Is it possible to do this at the OS level?

---

### Post by Pako Pako on 2013-09-13
I am unsure how much physical work you want to deal with.

The easiest method is to pull out the card/stick itself. You can also unmount and "safe removal" the drive from Disk Utility (Ubuntu) under the System -> Administration OS menu.

With "safe removal," power goes out and you either have to re-plug the stick in to re-mount it. (Although I think there was a command to re-power USB ports. I remember I had an issue with PowerTop that it would turn USB ports off... and forget to re-power them.)

---

### Post by Kirboosy on 2013-09-13
[FONT=system]Welcome to the forums!

There isn't a way that you can disable RAM through software easily. Here is a list of things you can try to improve battery life
**1**. [B]Switch off the wireless card if you do not plan to access your network or Internet connection
2. [/B]**Turn the volume level down, or mute it, if you do not plan to use it.**
**3. Reduce the LCD's brightness level**[B]
4. Disable Bluetooth[/B]
5. **Use the power management settings on your computer that come built in**
**6. Shut down or hibernate the laptop rather than using standby, if you plan on not using it for a while**
**7. Run simple applications that don't use much RAM, disk drive or processing power**

Hope that helps!
~Caboose
PS. You may not see a huge improvement in battery life but every little bit helps.
PSS You can also pull the stick out completely but that would mean you have to open the laptop and remove/install the RAM as needed. (Make sure to fully power off the computer before working with RAM)
[/FONT]

---

### Post by QIII on 2013-09-13
Hello!

Good suggestions above.

Unless you can find a utility that does it, I don't think that there is any way via the OS to actually reduce the power going to the RAM, just the amount of RAM the OS will address.  A point to keep in mind, however, is that memory draws the same amount of power whether it is being used or not.  You can specify the mem=Value parameter to the kernel at boot time.  But that will just change the amount of RAM the OS will address.  The motherboard will still be powering the modules and you won't get any savings.

This is a subject that can generate heated discussions, but I'll give you my take.

The amount of power consumed by your memory is miniscule compared the the power consumed by your screen, which is the biggest hog on your laptop.  Then comes your CPU and GPU -- depending on what is going on one or the other may be using more, so I'd call them a tie for hogs #2 and #3.  Then comes the disk if it is mechanical.  Add in all the other widgets.  Then comes memory towards the bottom.

Even "low voltage" memory saves at best single digits in terms of watts.  

Memory uses less power than mechanical hard drives.  If you reduce the amount of memory, you increase the likelihood of swapping.  That means power consumption by the drive.  Reducing the amount of memory available may actually increase power use.  I don't know what the relative difference in power consumption between memory and SSD read/write cycles would be when swapping.  The increase in the use of swap on the drive (if you have a mechanical drive) might well be more expensive than just having all that memory there.

Frankly, I'd worry less about the memory than about CPU throttling and limiting the CPU/GPU and screen consumption.  

Beyond that, I think your best bet would be entering your BIOS/EFI at power-on and seeing what options your have for undervolting, underclocking or disabling there, but you will degrade performace.  You even risk instability or physical damage if you go too far.

Some motherboards let you store multiple BIOS/EFI settings, so you might even be able to toggle between the normal settings and a special low power one.

Best wishes!

---

### Post by Pako Pako on 2013-09-13
Oops. I thought the original post read "(flash) memory stick" and not "(RAM) memory stick."

I **second QIII's post** -- if you want to "not-use" that memory, you'd have to remove it physically (while the machine is off and the battery disconnected and yourself grounded) or else the system will send power to the stick. No OS I know of is capable of shutting down the RAM.

RAM does use incredibly little wattage. To the point I advised a friend with a laptop and no power cable to boot a small linux distribution from a liveCD (in this case, Puppy), and do work all off the machine's RAM (unmounting all other drives).

Screen dimming, choke/throttle-down your CPU/GPU, disabling unused wireless (Bluetooth, infraRed), disabling USB ports (PowerTop annoyingly does this), reduce HDD use (platter or SSD based -- the less the system seeks the drive the less power it uses), etc. are more effective (and efficient) ways to reduce power consumption.

As for undervolting -- does Ubuntu support that? I know there are custom kernels (PHC) that have voltage tuning, but updates are few and far inbetween?

---

### Post by benpietras on 2013-09-19
Thank you all for the advice - it seems RAM is not so greedy as I thought.

The machine is an asus ux32a. ALPM runs ok ([https://wiki.ubuntu.com/Kernel/PowerManagementALPM](https://wiki.ubuntu.com/Kernel/PowerManagementALPM)), but despite the quite low powered i5 3317 the battery life is unremarkable.

---

### Post by mastablasta on 2013-09-19
what kind of battery is inside? is this the one: [http://www.asus.com/Notebooks_Ultrabooks/ASUS_ZENBOOK_UX32A/#specifications](http://www.asus.com/Notebooks_Ultrabooks/ASUS_ZENBOOK_UX32A/#specifications)
(nice maschine)

maybe if it's old it can hold less charge. another option is to use tlp (power manager). i think if this is the one, the intel GPU might be the culprint (yeah RAM doesn't use as much. it has an impact but not so big to matter much). how much do you get with this lappy on average??

---

### Post by tgalati4 on 2013-09-19
Get a second battery.  You may be able to declock (slow down) the RAM access speed in BIOS.  That might save some power.  On a desktop machine I was able to throttle the RAM speed + or - 10% in BIOS, but I have no way of measuring power savings.  On my IBM Thinkpad T43p, I recompiled my kernel with hooks to undervolt the processor which resulted in 2 to 7 watts of power savings (out of 22 watts baseline).  It raised a 2-hour battery life to 2:20.  So an extra 20 minutes of battery life.  Not a lot, but enough to give some margin when you are out and about.

I would look into 9-cell batteries, or DVD-slot batteries, or just a second, standard battery pack to give you the battery life that you expect.  Fiddling with RAM won't get you there.

---

