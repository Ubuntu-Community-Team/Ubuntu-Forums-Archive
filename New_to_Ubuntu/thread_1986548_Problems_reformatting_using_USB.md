---
title: "Problems reformatting using USB"
date: 2012-05-25
forum: New to Ubuntu
---

### Post by bhull05 on 2012-05-25
Hello all,

I'm encountering errors while trying to reformat a laptop while using a USB flash drive.

I followed these instructions for putting the file information onto the flashdrive: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

When I boot my computer I open up Bios and boot from the Sandisk on which I put the information. Next, I have the 'Installer boot menu' displayed on my screen. My options are:

1. Run ubuntu from the USB
2. Install ubuntu on a hard disk
3. test memory
4. Boot from first hard disk
5. Advanced options
6. Help

I am selecting (2) 'Install ubuntu on a hard disk.

A lot of text scrolls across the screen until it comes to the following line.

[7.168030] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x79A9

[7.174374] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x8DFC

[7.174491] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x8E3A

I have tried a few times but it always comes to this and sits there for over 30 minutes and is frozen. The computer sounds as if it's processing but nothing changes.

This is my first attempt at an install, I would appreciate any help.

Cheers!

---

### Post by wilee-nilee on 2012-05-25
> **bhull05 said:**
> Hello all,

I'm encountering errors while trying to reformat a laptop while using a USB flash drive.

I followed these instructions for putting the file information onto the flashdrive: [http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows](http://www.ubuntu.com/download/help/create-a-usb-stick-on-windows)

When I boot my computer I open up Bios and boot from the Sandisk on which I put the information. Next, I have the 'Installer boot menu' displayed on my screen. My options are:

1. Run ubuntu from the USB
2. Install ubuntu on a hard disk
3. test memory
4. Boot from first hard disk
5. Advanced options
6. Help

I am selecting (2) 'Install ubuntu on a hard disk.

A lot of text scrolls across the screen until it comes to the following line.

[7.168030] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 1 at offset 0x79A9

[7.174374] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 2 at offset 0x8DFC

[7.174491] [drm] nouveau 0000:01:00.0: Parsing VBIOS init table 3 at offset 0x8E3A

I have tried a few times but it always comes to this and sits there for over 30 minutes and is frozen. The computer sounds as if it's processing but nothing changes.

This is my first attempt at an install, I would appreciate any help.

Cheers!

I think you might need the nomodeset option, at that choices gui, hit f6, then tick nomodeset then boot in.

---

### Post by bhull05 on 2012-05-25
I can't figure out how to 'tick to the nomodeset' option you describe. But I now have it going through to the purple 'Ubuntu' screen with the 5 orange dots. The screen freezes when these dots become solid orange, and then, after 2 minutes, my screen freezes in a series of white and black 'bars' and 'squares' that appear in random, horizontal orientation..?

---

### Post by wilee-nilee on 2012-05-25
> **bhull05 said:**
> I can't figure out how to 'tick to the nomodeset' option you describe. But I now have it going through to the purple 'Ubuntu' screen with the 5 orange dots. The screen freezes when these dots become solid orange, and then, after 2 minutes, my screen freezes in a series of white and black 'bars' and 'squares' that appear in random, horizontal orientation..?

The thread might help.
[http://ubuntuforums.org/showthread.php?t=1613132](http://ubuntuforums.org/showthread.php?t=1613132)

---

