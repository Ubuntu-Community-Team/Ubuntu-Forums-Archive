---
title: "ubuntu will not boot."
date: 2019-09-26
forum: New to Ubuntu
---

### Post by robbyjm on 2019-09-26
whenever i turn my pc on, i am met by a black screen. i can't get to the bios, windows, or ubuntu. here's exactly what i did to get to this point. 

first, following along with the install ubuntu guide, i created a bootable usb using rufus on windows 10. then, from the windows 10 recovery menu in settings, i selected to boot from said usb. after booting, i went through the install process for ubuntu. for my partitions, i created a logical ext4 partition mounted at / and another logical ext4 partition mounted at /home. after that i went through the rest of install process. everything went fine. i rebooted, ran sudo apt-get update and sudo apt-get upgrade then went to the "software" application to look for xfce. i found it weird that after a search nothing came up, so from the terminal i ran sudo apt-get install xcfe4 and installed the desktop environment. then, i logged out, selected xcfe from the desktop environments, typed in my password and tried to log in. i was met with a black screen for about a second before i was brought back to the original log in screen where i was promoted to select my user. i tried a few more times but i was getting stuck in the same loop. eventually, i just selected the default desktop environment and tried to research why that wasn't working. i found that sometimes also installing lxde helps fix this problem. i did this, logged out, logged back in, same problem. stuck at a black screen for a second then back to the login prompt. i decided to reboot at this point. from here on, i was not able to get back into any operating system. windows or ubuntu. just a black screen forever once i turn my computer on. i can't seem to get into the bios either, however I blame that on windows 10 fast boot or something.

im kind of stuck here, any help at all would be greatly appreciated. &#55357;&#56898;

---

### Post by crip720 on 2019-09-26
See if you can boot with the usb again.  Fast boot should not prevent you from going to bios,only from reading/writing from ubuntu to windows.  Do you mean install lxde desktop, or install lightdm?

---

### Post by robbyjm on 2019-09-26
I can't boot from anything even with the usb in. I have a feeling that I am in fact in ubuntu but the log in screen is not showing up. ultimately, i was just trying to install an additonal desktop environment, xfce.

---

### Post by robbyjm on 2019-09-26
alright, the only way i can get to something is by unplugging my hard drive that had windows and ubuntu installed on it and booting from the live usb. after i got to the desktop, i tried plugging the hard drive back in and using gparted to delete the ubuntu partition but it wont show up.

---

### Post by robbyjm on 2019-09-26
i plugged in the hard drive, rebooted from the live usb, and now im back in windows. i have no idea what is happening.

---

### Post by yancek on 2019-09-26
> from the windows 10 recovery menu in settings, i selected to boot from said usb.

Booting an Ubuntu installation medium is usually done by going into the computer BIOS setup/firmware and selecting the usb device to boot from rather than from a windows menu.  You aren't by any chance using the software described at the link below?

[https://docs.microsoft.com/en-us/windows/wsl/install-win10](https://docs.microsoft.com/en-us/windows/wsl/install-win10)

Did you install windows 10?  Generally, a pre-installed windows 10 system will be UEFI/GPT and there will only be primary partitions, no Extended or Logical partitions on a GPT drive.  If you are able to boot the Ubuntu install usb, you could open a terminal and run the following command and post the output here as that will give some basic info on the setup.

```
sudo parted -l
```

---

### Post by robbyjm on 2019-09-26
alright, i may have narrowed down one problem to being an xfce compatibility issue. i just made a xubuntu live usb, booted from that, and after the "xubuntu" logo appeared on screen for a few seconds, then the screen went black. i was able to to do the same process as before to get back into windows. turn the computer off. unplug the hard drive. turn the comptuer on. plug the hard drive back in. reboot. the problem is i can't use any of the windows 10 recovery options because no matter how i restart my computer i sit on a black screen unless i unplug my hard drive and use a live ubuntu usb or i do the trick to get back to windows. windows will not restart normally and i have no way of getting to the bios. i don't know what is preventing windows from booting normally

---

### Post by robbyjm on 2019-09-27
If I click any of the options in this menu, [https://www.laptopmag.com/articles/access-bios-windows-10](https://www.laptopmag.com/articles/access-bios-windows-10) my computer doesn't restart. I don't know why, but it's preventing me from getting to the BIOS or anything else on my computer. What I'm going to try now is making a windows 10 media creation usb and attempt to boot from that.

---

