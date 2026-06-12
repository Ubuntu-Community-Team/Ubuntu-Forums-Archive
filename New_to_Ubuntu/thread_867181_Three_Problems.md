---
title: "Three Problems"
date: 2008-07-22
forum: New to Ubuntu
---

### Post by gray_bryan on 2008-07-22
I am running Ubuntu on my MacBook using Virtual Box. I allot it to use 1024MB of memory, and 60MB of 128MB of Video Memory. 
Problem one, I cant change the screen resolution to other than 640x480 or 600x800 which is no good because i cant see all of the screen and therefore sometime cant click on continue or other options.
Problem two, I cant get any sound out of it. I have the setting in Virtual Box to allow it to use the Audio, but it just wont.
Problem three, CD's aren't being read. I can insert them, and even eject the disc from the drive in Ubuntu, but it wont read it.
Thanks in advance for the help

---

### Post by coffeecat on 2008-07-22
I'm posting from my Mac Mini which is running Ubuntu 8.04 in VirtualBox fine without any of the problems you describe, so I'll give you some pointers. But just a couple of comments first. You won't get another post out of me for about 18 hours because I'm going to bed now and I have a busy day tomorrow. Also - I've answered a few first-time posts recently and got not an acknowledgemenet nor a response. I feel I was wasting my time. I'm sure you're different ( :) ), but I won't post to this thread again unless you've posted first.

First suggestion: nothing to do with VirtualBox, but you might want to consider clicking on the report button for your post and asking the mods to move this thread to 'Apple Users'. You might get more responses.

You've allocated more memory than Ubuntu needs. I've set it up with 512Mb of base memory and it runs fine. It also runs fine on my laptop (non-virtualised) with only 512 MB. Also, you don't need that much video memory. VirtualBox uses a sort of virtualised vesa. That's why you can't enable Compiz. I've set mine up with only 16MB and I can get 1920x1200 fullscreen on my 24" widescreen monitor with it.

To increase the screen resolution, you need to install the Guest Additions. Look in Section 4 of the VirtualBox manual - downloadable as a pdf. You also need to look at section 2.3.2 to compile the guest additions. Install the package 'build-essential' to get the developer tools you need. I seem to remember that the kernel headers and dkms are already installed by default.

Installing the Guest Additions will also give you vastly improved mouse control and you'll also be able to set up shared folders.

**Audio** Highlight your Ubuntu virtual machine in the left pane of your VB control window. Now click on Audio on the right. Is the 'Enable Audio' box ticked? I've got CoreAudio as Host Audio Driver and it all works fine.

**CD** Now click on CD/DVD-ROM. Make sure 'Mount CD/DVD drive' is ticked. And make sure the correct host drive is ticked and selected.

**Edit:** I'm assuming here you're using version 1.6.2 of VirtualBox. If you're not, you might want to consider upgrading.

---

