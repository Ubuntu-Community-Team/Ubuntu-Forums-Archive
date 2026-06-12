---
title: "Some errors with pictures and a YouTube video"
date: 2013-09-12
forum: New to Ubuntu
---

### Post by ImTroyMiller on 2013-09-12
Here's what I have for hardware...
Gigabyte 970A-D3 Rev 3.0 motherboard
NVidia GeForce GTX 650 Ti Boost video/graphics card
AMD FX 6300 Six Core Processor
32gb of RAM(4x8gb sticks) Corsair Vengence
Asus DVD/Blu-Ray
1tb Hard Drive "00RKKA0"(With Windows 7 Professional)
1tb Hard Drive "07ZF5A0"(With Ubuntu 12.04 Precise Pangolin)
75gb Hard Drive "00FLA1"(No OS)

--------

I installed Ubuntu 12.04 onto the hard drive "07ZF5A0" and had some errors.  I decided to reinstall Ubuntu and now I have an Ubuntu boot option in my BIOS that is left over from the first installation.  It's labeled as "Ubuntu" and is the top choice in this picture...

[[IMG]http://i49.photobucket.com/albums/f270/ImTroyMiller/InBIOS.jpg[/IMG]]("http://s49.photobucket.com/user/ImTroyMiller/media/InBIOS.jpg.html")

When I select it, the screen blinks and just goes right back to the same screen above.  I need to know how to delete this option from this BIOS.  I would prefer to just have the drives(the three hard drives and the DVD/Blu-Ray drive) as BIOS boot options.

Right now, if I choose Hard Drive "00RKKA0", it'll boot into Windows 7, which is what I want.  If I chose Hard Drive "07ZF5A0", I get the GRUB menu, but it looks big and bulky.  Is there anyway to configure it so that it looks a little bit sharper?

--------

When I select to boot from Hard Drive "07ZF5A0", and I choose the generic Ubuntu, I can't use my mouse or keyboard until 3-5 minutes after the main login screen appears.  I know the PC is not frozen because the cursor is blinking within the username textbox.

--------

Once I am actually logged in, I get this error at random times.

[[IMG]http://i49.photobucket.com/albums/f270/ImTroyMiller/UbuntuProgramError.jpg[/IMG]]("http://s49.photobucket.com/user/ImTroyMiller/media/UbuntuProgramError.jpg.html")

--------

This is a video of another error I receive.  This error flashes, and then takes me back to the main login screen.  This error repeats over and over again.

[http://www.youtube.com/watch?v=Y6Uq0lDoVjM](http://www.youtube.com/watch?v=Y6Uq0lDoVjM)

Here's a picture of the text that was displayed...

[[IMG]http://i49.photobucket.com/albums/f270/ImTroyMiller/UbuntuError.png[/IMG]]("http://s49.photobucket.com/user/ImTroyMiller/media/UbuntuError.png.html")

--------

Only two out my eight USB ports work.  I experienced the same thing when I had installed Windows 7, but after putting in the DVD that came with my motherboard, and installing the drivers, they all worked.

I don't believe that the DVD will work with Linux, although I haven't tried.

How can I get these USB ports working?

---

### Post by mastablasta on 2013-09-13
is the image you installed from good?

did you use proprietary nvidia drivers?

do logs say anything more about error?

---

### Post by ImTroyMiller on 2013-09-13
The DVD I installed from is good.  The image was downloaded from Ubuntu.com.  I used the same DVD to install Ubuntu on my old PC and it ran fine.

I am not using the proprietary NVidia drivers.

I don't know of any error logs.

---

### Post by Mephisto Pheles on 2013-09-13
Try to reformat that drive or partition and reinstall, check if your disk is OK first.

Looks like you need several drivers, since you yourself say you needed them for Windows as well.
Try "additional drivers" in "Settings" menu first.
If that doesn't work, on windows visit the websites of the manufacturers and look for linux drivers.
You should be able to access the windows partitions from linux to install them (probably you'll need gdebi).

And install/use the nvidia drivers on linux.

---

### Post by ImTroyMiller on 2013-09-13
I actually had already checked the disk and it was okay.  It's a brand new hard drive also.  I am already on my second installation, it has the same problems.

In "additional drivers", there is only the NVidia proprietary drivers.

The manufacture's website says, "Due to different Linux support condition provided by chipset vendors, please download Linux driver from chipset vendors' website or 3rd party website."  So it looks like I'll have to find them from a 3rd party.

---

### Post by ImTroyMiller on 2013-09-13
After searching a bit more, it looks like my motherboard isn't compatible with Linux, at all.

---

### Post by Mephisto Pheles on 2013-09-13
Relax, not so fast.. giving up is too easy ;)


check out this post 
enable IOMMU in the BIOS on my motherboard (Gigabyte 970A-D3). 
[https://bbs.archlinux.org/viewtopic.php?id=159467](https://bbs.archlinux.org/viewtopic.php?id=159467)

it has links back to this board
[http://ubuntuforums.org/showthread.php?t=2114055](http://ubuntuforums.org/showthread.php?t=2114055)
[http://ubuntuforums.org/showthread.php?t=2111223](http://ubuntuforums.org/showthread.php?t=2111223)

google
linux on Gigabyte 970A-D3

---

### Post by ImTroyMiller on 2013-09-13
That got it working.  Thank you.

What happens if I leave IOMMU on and boot Windows 7?

---

### Post by ImTroyMiller on 2013-09-14
I'd also like to get rid of that Ubuntu boot option that's within the BIOS boot menu.

---

### Post by ImTroyMiller on 2013-09-14
The time changes each time I switch between OS.  The time in Windows 7 leaps forward seven hours, then I correct it and boot Ubuntu, and Ubuntu's time is seven hours behind.  Their are at a tug-o-war.  I did a search and read that it's due to BIOS settings, but didn't find a direct answer.

---

### Post by ImTroyMiller on 2013-09-15
I have had this error pop up a couple of times so far...

[[IMG]http://i49.photobucket.com/albums/f270/ImTroyMiller/UbuntuError2221.jpg[/IMG]](http://s49.photobucket.com/user/ImTroyMiller/media/UbuntuError2221.jpg.html)

[[IMG]http://i49.photobucket.com/albums/f270/ImTroyMiller/UbuntuError2222.jpg[/IMG]](http://s49.photobucket.com/user/ImTroyMiller/media/UbuntuError2222.jpg.html)

It got stuck on that twice already, but it usually loads without error.

---

### Post by QIII on 2013-09-15
Hello!

Please start a new thread for each individual issue.  This thread has several different things going on that will make it hard for others to follow -- and reduce your chances of getting help.

Also, please attach images using the "paper clip" button above the text input box rather than pasting large images.  Large images may cause problems for those with low-bandwidth connections or data limitations on their service.

Thanks.

---

