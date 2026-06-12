---
title: "New kernals affecting Graphics"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by briml3y on 2008-10-16
I recently updated using ubuntu's built in update feature, meaning that 
I update when ever it tells me they are available. I recently updated and I believe it installed a new linux kernal and headers. After restarting i received a low graphics box and just clicked continue, as this has happened before, but upon loading my desktop i could not get my grpahics drivers to work. I have a GeForce 8400M gs graphics card. I normally use EnvyNg to update my graphics drivers but every time I attempt to use it now i get an error. 

Here is a screen shot of the error

[IMG]http://i78.photobucket.com/albums/j100/briml3y/Screenshot.png[/IMG]

Ive tried re installing envyng, nvida-settings, nvidia-xconfig,and restricted drivers ap aswell

---

### Post by Bakon Jarser on 2008-10-16
The same day of the kernel update I also got an nvidia driver update.  Go into synaptic package manager and click on File > History and you can see a list of all updates.

---

### Post by briml3y on 2008-10-16
I found the list but it showed no update for Nvidia, any suggestions on what i should do?

---

### Post by nhasian on 2008-10-16
in the grub menu you can still boot to the older kernel for a few days till the EnvyNg gets updated with a newer nvidia module right?  I've never used EnvyNg but i installed the nvidia drivers directly from Nvidia's website.  I have to rerun the nvidia driver setup file every time i update the kernel because it gives me the low graphics dialogue as well until i do :)

---

### Post by GuitarRocker2562 on 2008-10-16
System -> Administration -> Hardware Drives may have the driver ready to be installed for you.

---

### Post by briml3y on 2008-10-17
I still can't get envyNg to work properly and yes you can still load up from the older kernals but for some reason my screen resolution wouldn't go above 600x800. My temporary solution i found on another topic was to

Reboot into Recovery Mode
Run fix x server
then boot regularly

I can't tell you if i have to do this every time i start up because i have not had a chance to test it but until EnvyNg works without errors thats how i will do it

And going to hardware drivers and enabling the nvidia drivers did not change the screen resolution at all

---

### Post by JiMMaR on 2008-10-29
err , this may be kinda too late , but anyway here I go
I had the same problem , the only solution I found was to do this
1 - fix xorg
2 - update the driver
3 - just use the old kernal , it works fine

now I just wanna know if there is a way to rollback and just remove the new kernal or something

---

### Post by cggaret on 2008-10-29
I've had this happen many times with kernel updates. I always uninstall the driver with envyng before rebooting when I notice that the kernel has updated, and then I reinstall the driver with envyng after rebooting, and then reboot again.  It should work for you if you use envyng to uninstall, then reboot, then use envyng to install, then reboot.  If this doesn't work, you may have to completely remove everything to do with the nvidia driver.  [This page]("http://albertomilone.com/latest_nvidia_udsf_feisty.html") might also be helpful, even though it was written for feisty.

---

