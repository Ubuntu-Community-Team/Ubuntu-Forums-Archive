---
title: "Can't Boot From USB HELP"
date: 2011-11-12
forum: New to Ubuntu
---

### Post by Jackbenimble7 on 2011-11-12
Hey everyone, so I'm trying to boot Ubuntu from my USB because my CD drive is broken. I've been following the instructions linked here

[https://help.ubuntu.com/community/Installation/FromUSBStickQuick](https://help.ubuntu.com/community/Installation/FromUSBStickQuick)

**To be clear, I'm using a 1GB memory stick, not 2GB; don't have any larger than 1GB. Tis may be the problem, but I don't know.**

I downloaded Ubuntu 11.10 and made the ISO file on my USB. Then I restarted my computer and switched the option to boot from USB. I then restarted my computer again. It seemed like Ubuntu loaded as it gave me a screen that had options like "Boot from hard drive" "Help" etc, but once I chose an option (or just allowed it to autoinstall), the screen would flash with white code on a black screen for about 10 seconds. After this, the screen just went black and didn't change. I had to turn off my computer. 

Can anyone explain what's going on here?

---

### Post by Mark Phelps on 2011-11-12
I've not done this ... but the text clearly says "at least" 2GB.  So,what would lead you to believe that 1GB would be enough?

Try is using the right size USB stick.

If that still fails, then try booting a different PC using the same 2GB USB stick.  IF it fails again, then the stick wasn't prepared properly.

---

### Post by Jackbenimble7 on 2011-11-12
Nothing "lead" me to believe a 1GB flash drive would work. I clearly stated in my post that I used a 1GB flash drive because I didn't have a larger drive.

I guess I should revise my question to "Has anyone tried this installation with a 1GB flash drive, or does anyone know if a 1GB flash drive will work?"

---

### Post by oldfred on 2011-11-12
No idea if it will fully work in 1GB flash. But it sounds like you have the video issue.

Natty Video issues. MAFoElffen
[http://ubuntuforums.org/showthread.php?t=1743535](http://ubuntuforums.org/showthread.php?t=1743535)

How to set NOMODESET and other kernel boot options in grub2 
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

---

### Post by WasMeHere on 2011-11-12
Welcome to the Ubuntu Forums Jackbenimble7,

I boot Ubuntu from a 1 GB partition on a USB stick, so it should work.

1. What if you ***press F6*** (the function F6 key above the 6 and 7 keys), when you come to that screen with where you can select how to continue. Then you can select boot options, select one or more each time, and try to boot into a live session!

2. Another way might be to use gparted to delete the partition if any, and make a new partition with FAT32 file system, boot flag and lba.

3. And after that install your system again with the same method.

4. Finally, if that does not work, try Unetbootin to make the boot-USB!

But I think that it is a graphics issue, and you should try method 1 to select boot options via the F6 key.

Have fun finding out about Ubuntu :-)
Olle

---

### Post by Jackbenimble7 on 2011-11-12
I'm not sure what you guys mean when you say it might be a graphical issue. 

Olle, I tried pressing F6, but it just brings me to the menu I described in my first post. I tried all the options which were

Boot from USB
Boot from Hard Drive
Test Memory
Help

There might have been a few more options, but the point is, none of them did anything helpful. Also, I've tried Ubuntu 11.04 and 11.10, both did the same thing. Maybe I'll give 10.0 a shot. 

However, I'd like to get the most updated version, and if there's any more information you could give me about graphical issues, I'd really appreciate it.

---

### Post by WasMeHere on 2011-11-12
> **Jackbenimble7 said:**
> I'm not sure what you guys mean when you say it might be a graphical issue. 

Olle, I tried pressing F6, but it just brings me to the menu I described in my first post. I tried all the options which were

[COLOR="Red"]Boot from USB
Boot from Hard Drive
Test Memory
Help[/COLOR]

There might have been a few more options, but the point is, none of them did anything helpful. Also, I've tried Ubuntu 11.04 and 11.10, both did the same thing. Maybe I'll give 10.0 a shot. 

However, I'd like to get the most updated version, and if there's any more information you could give me about graphical issues, I'd really appreciate it.
Press F6 (again) when you have that menu ([COLOR="Red"]red[/COLOR] in the quoted text above) on your screen!

---

### Post by WasMeHere on 2011-11-12
> **oldfred said:**
> ...
[https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

Browse through this link suggested by oldfred. It shows with screenshots what you should see, and what to do.

Good luck :-)
Olle

---

### Post by jjex22 on 2011-11-12
Having a netbook, the vast majority of installs I do are USB based. I have definitely used a 1GB drive to burn a ~700MB CD drive before, though not for a while. 

Usually when a USB install kicks out, kernel panics of just halts it's because one of the transfers has become corrupted. - Download the Iso again, and format the drive - if you are using mac use disk utility to erase the drive, if windows format from my computer by right clicking the drive and making sure "quick format" is not checked. 

Once formatted, run the pendrive linux installer again and wait for it to finish then eject the drive from the OS before removing. I no longer recommend unetbootin for Ubuntu as I've had real trouble getting it to make ubuntu 11.10 USB's.

If this fails again then the 2GB could have now become an issue. In this instance, download the mini.iso from here:

[https://help.ubuntu.com/community/Installation/MinimalCD](https://help.ubuntu.com/community/Installation/MinimalCD)

and use this to do a net install. it's not as pretty, but just as functional - think dos installer rather than windows 7! just remember you may well have to plug your netbook into your router/modem via a lan cable as the mini.iso may well not have your wifi driver, and this install will download the files from the internet.

Hope this helps, any questions, just ask!

---

### Post by Jackbenimble7 on 2011-11-12
11.10 refuses to work even after new download and new compilation with Universal USB. Tried all options at the menu it gives me after reboot, including pressing F6, and still nothing happens. I'm going to try 10.0, always liked that interface more than Unity/GNOME 3 anyway. 

I'll let you know how it turns out.

---

### Post by WasMeHere on 2011-11-12
> **Jackbenimble7 said:**
> 11.10 refuses to work even after new download and new compilation with Universal USB. Tried all options at the menu it gives me after reboot, including pressing F6, and still nothing happens. I'm going to try 10.0, always liked that interface more than Unity/GNOME 3 anyway. 

I'll let you know how it turns out.

Ubuntu 10.04 LTS 'lucid lynx' is good particularly for middle-aged and old computers. It is very stable.

---

### Post by jjex22 on 2011-11-12
> **Jackbenimble7 said:**
> 11.10 refuses to work even after new download and new compilation with Universal USB. Tried all options at the menu it gives me after reboot, including pressing F6, and still nothing happens. I'm going to try 10.0, always liked that interface more than Unity/GNOME 3 anyway. 

I'll let you know how it turns out.

I completely agree with you on this one - I am using 11.10 on my desktop as I'm hoping i'll get used to it soon, but I do have to say that gnome 2 runs a lot better on mobile devices such as laptops and netbooks - it isn't showing a significant resource difference to 10.04 when run in 2d mode, but there is no argument that it's definitely slower especially on my netbook.

---

### Post by Jackbenimble7 on 2011-11-12
Wanted to let everyone know I downloaded Ubuntu 10.10, and am currently typing on a unix based OS. Amen. 

Thanks for all the help everyone, and I'm sure I'll be asking questions in the near future.

---

