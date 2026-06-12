---
title: "Ubuntu runs on DELL with bad NVIDIA but ... help!"
date: 2012-01-17
forum: New to Ubuntu
---

### Post by FrancescoTrevisan on 2012-01-17
My old Dell9400 laptop running XP stopped working a few months ago. In 4 years the NVIDIA GeForce 7900 GS stopped working 3 times. This time Dell will not replace it under warranty. What to do! Still a nice machine with 17" 1920x1264 screen 2.16Ghz Intel Core Duo and 2048MB Ram and 320GB HD. I tried the "stove" trick by removing the NVIDIA and putting it in the kitchen stove for 15 min, some people say that it fixes the bad soldering and it starts working again. no such luck on mine.
 
I am thinking that it would be nice to be able to fix it and just keep it in the kitchen to play the MP3 collection through the stereo system. Maybe even use it to quickly check recipies!!
I tried installing my older UBUNTU 11.04 CD, did the vga=771 thing to see the screen and did a full install erasing all partitions. during installation and updating everything smooth.
On restart the screen turns black, drive is still loading but nothing to see.
I force it to shutdown, download "Boot-Repair-Disk" and run it in 32bit failsafe mode.
In GRUB options I add a few kernel options so that the configuration now reads 
 
GRUB_CMDLINE_LINUX_DEFAULT="quiet splash i915.modeset=0 xforcevesa nomodeset radeon mode=1" 
I don't really know what I am doing but to me it sounds like the video has to "go through" the bad NVIDIA and come out on the screen without having anything to do with the NVIDIA BIOS and drivers.
 
Well, the DELL lives again and it starts up in safe video mode, but ... surprise ... full screen resolution of 1920 x 1200. what better then this!! however in the monitor menu it clearly shows 0Hz screen resolution and unknown hardware. 
 
In additional Driver search it suggests several NVIDIA and it suggest to Activate the driver. I did that and the Dell was back in darkness.
 
After repeating the full installation again I now have it to the point that it starts fine, no NVIDIA drivers and still NOT Activated. I am keeping it with whatever drivers Ubunto is resorting to. the issue is that now it will only go up to 1280x1024 (5:4) (desktop goes off screen if the BIOS is set on streching video.
 
any suggestions on how to get it to show 1920x1020? 256color or 16bit more then OK. Should I add a vga=893 ? I am not very UBUNTU proficient. Thank you for the kind assistance

---

### Post by Kslawdog on 2012-01-17
Man, that's real nice what the heck is a warranty for anyways!... anyway, sounds like get a new video card or just live with it.  Ubuntu is pretty good about running hardware without drivers but not perfect.  sounds like it would be good enough for music though. sorry couldn't be any more help.  I have never seen a dell that didn't have problems, not my favorite brand.

---

### Post by Dngrsone on 2012-01-17
Check to see if your machine falls under the NVidia Class-action settlement; you might be able to replace it yet.

Personally, I have had issues with the Unity batch of Ubuntu distributions.  Try installing 10.04, and see if it doesn't work out better for you.

Also, you could try going minimalist with Damn Small, Puppy, or Mint.

---

### Post by FrancescoTrevisan on 2012-01-18
I had no knowledge of a NVIDIA settlement. I live in Vicenza, northern Italy, I will see if the italian division of DELL has info.
 
Anyway, as it turns our, every single time I start UBUNTU in forced video mode I get 1920x1200, not bad. no lag in moving windows around the desktop and videos play back ok.  When I get into Monitor settings I tell it to use the current setting as default and then I restart in normal mode (nothe forced video) . the system boots but the screem size is smaller at 1280x1024 and a window on the top right specifies that the requested resolution of 1920... is not available and the new default is 1280...
 
How can I get around this? strange that forced video startup shows full resolution? the only odd thing is that monitor is indicated as unknown, frequency at 0Hz and no other options are available.  In regular mode resolution defaults to 1280x1024 at 61Hz and Monitor is still unknown.
 
Before deciding to try older version of UBUNTU I would like to study a wourkaround this.  Any idea? how can I make UBUNTU start in forced video as default?
 
Thank you for kind support.

---

