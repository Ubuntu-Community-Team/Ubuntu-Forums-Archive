---
title: "Iv broken my Ubuntu after updating AMD graphics driver!!"
date: 2019-06-10
forum: New to Ubuntu
---

### Post by danworsley2 on 2019-06-10
As in the title above, I recently installed ubuntu 18.04 on my HP 17-ak014na laptop, but I have been experiencing some minor issues with graphics, mainly the odd screen flicker and some bad rendering. I am fairly new to Linux, so tonight I did a bit of research and thought to try fix the issue. After reading up some articles on AMDs website it turned out it was much easier than I thought! I downloaded the latest amd64 linux drivers from AMDs website for my Radeon R4 Integrated Graphics, it came in the form of a .deb package. I ran the package through the standard ubuntu package installer, then rebooted the laptop. Now the laptop will not boot, its stuck in a boot loop. Is there anything I can do to revert back to the original driver? Thanks in advance. Dan.

---

### Post by cruzer001 on 2019-06-10
From the AMD site:
> Uninstalling the AMD GPU-PRO Driver 

If for any reason you wish to remove the AMDGPU-PRO graphics stack you can do this using the uninstallation script which was part of the installation and is present in your path. From the command prompt enter the following command:

amdgpu-pro-uninstall
Now you need to get to a command prompt.

Do you make it to the first screen?  Where you can choose ubuntu or something else.  If so, then one way to do it at that screen is **press:**
> Ctrl + Alt + F1
and login

After your finished
```
sudo reboot
```

And welcome to the forums :)

---

### Post by danworsley2 on 2019-06-11
Thanks for your response mate

Ctrl Alt F1 didn't work, but instead iv used the recovery option in grub to get a root terminal up. The amdgpu-pro-uninstall is coming back as an unrecognised command so it looks like the script is missing.

Also to add, I tried adding nomodeset at the end of the kernel line in grub, that got as far as getting the mouse pointer up but I was then faced with a blank screen.

Is there anything else I could try? Not sure if I'm able to reload the stock Ubuntu radeon graphics driver that I was using before?

Cheers

---

### Post by cruzer001 on 2019-06-11
Hello

Ubuntu will default back to the generic driver when pro is removed.  You could use apt in recovery mode to remove it.
```
apt purge amdgpu-pro*
```
That should do it and reboot.
To verify whats installed:
```
lshw -C display
```

Found this
[https://ubuntuforums.org/showthread.php?t=2405576&p=13820596#post13820596](https://ubuntuforums.org/showthread.php?t=2405576&p=13820596#post13820596)

---

### Post by danworsley2 on 2019-06-11
That didn't work either :lolflag:

I downloaded the PDF driver installation instructions from AMD's website tonight and it looks like they haven't updated it for a while. None of the commands for uninstalling the driver worked.

Iv given up and gone in with a live cd, backed up my files and reinstalled Ubuntu, This time I will leave the drivers alone! 

Thank you for your efforts I really appreciate it!

---

### Post by mastablasta on 2019-06-12
you need to check and make sure the drivers actualyl support not only your chip, but also Ubuntu version, xserver version, wayland version... all in all many things. if all of those things are available then you can install them.

if you are experiencing difficulties with default driver, perhaps you can resolve them by troubleshooting them. i believe some had issues that radeon was enabled by default, while in fact if they manually enabled amdgpu (not amdgpu-pro) it would improve the experience. all in all you need to take a deeper look before deciding what to do with the driver. this is one of the issues with desktop linux. it is quite difficult for average user to know what to do even when you identify the issue. Ubuntu (and most other distros) come with some sane defaults, but many times these are not good for specific users. and to change them and improve usability of the OS for those users requires a lot of reading and operating system knowledge. 
in windows just would just install the drivers and usually it would work. if drivers don't work on the OS version, you normally won't be able to install them. in linux you can still install the drivers and face the blank screen or blinking cursor.

---

