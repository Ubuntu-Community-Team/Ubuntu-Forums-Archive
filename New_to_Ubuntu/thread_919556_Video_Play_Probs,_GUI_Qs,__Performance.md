---
title: "Video Play Probs, GUI Qs,  Performance"
date: 2008-09-14
forum: New to Ubuntu
---

### Post by Lord Udedenkz on 2008-09-14
Hey I just installed just like a day ago. And I have internet, and mp3s play fine, and I figured out why my sound was so low, and after lots of cursing and praising of XPs autodetect features I even made the resolution and refresh rate work, and flash, and make the PF from 18Gb to 4 and then make it work again. So it was like, ok.

One problem is that Video Play Back seems to show tearing - vsync style tearing which is really weird. Does not happen on XP without syncing anything. Also some corruption here and there playing video files, it just get pixely and stuff for no reason then comes back. I installed that which was recommended by me when I first opened an MP3 file.
Also sound had a weird, staticy feel. not sure about now...
Suggestions? 
HD MKV files use less CPU it seems then on XP though. (12.5% - 50% Ubuntu, 33% - 50% XP)

Is it possible to have a different Wallpaper for every workspace? That would be cool.Also, everything seems rather Anti-Aliased/Cleartypeesque, anyway to kinda make it more crisp? Maybe also a skin that has things a bit better, smaller loading bars for example? Also there seems to be a variation in size of the fonts making some things hard to read online as they are smaller then normal.

Also, does this OS automatically take full advantage of hardware features for the best performance and stuff? I mean like, MacOS takes good advantage of C2D and thus achieves masterful performance... One of the reasons I installed ubuntu is because I want a fast OS with good functionality and security for the 'private collections' for collage. Or how do I make it faster and more hardware pushy?

Also, it does downscale GPU and CPU clock speeds like in XP? this thing gets hot at full clock speeds, not fun for the hand...

Finally, U can emulate DOS with some virtual environment ubuntu app right? Wanna play some Lost Vikings 2.

Specs,
Ubuntu x86_64
Core 2 Duo T8300 @ 2.4Ghz 3MB L2
800Mhz FSB
666Mhz DDR2 Dual Channel 2GB RAM
Nvidia 8600M GT 256 DDR2
7200RPG 160 GB HD (25% WinXP64, 25% WinXPSP3, 12.5%Ubuntu, 4GB Swap, Unformatted Rest - For Now)
1280*800 16:10 Widescreen 60Mhz LCD
Realtek Sound Something
PM965 Intel Motherboard or something of that sort

---

### Post by Mornedhel on 2008-09-14
That's a lot of questions in one post.

> **Lord Udedenkz said:**
> Is it possible to have a different Wallpaper for every workspace? That would be cool.

I think there's a Python script for that somewhere, but Gnome does not do this by default. KDE does, however.

> **Lord Udedenkz said:**
> Also, everything seems rather Anti-Aliased/Cleartypeesque, anyway to kinda make it more crisp? Maybe also a skin that has things a bit better, smaller loading bars for example? Also there seems to be a variation in size of the fonts making some things hard to read online as they are smaller then normal.

System > Preferences > Appearance for most settings. You can install more themes from art.gnome.org, and some are also available in the repositories. You should probably get the msttcorefonts package, since most websites make heavy use of the typical Arial, Times, Trebuchet, etc. fonts.[/quote]

> **Lord Udedenkz said:**
> Also, does this OS automatically take full advantage of hardware features for the best performance and stuff? I mean like, MacOS takes good advantage of C2D and thus achieves masterful performance... One of the reasons I installed ubuntu is because I want a fast OS with good functionality and security for the 'private collections' for collage. Or how do I make it faster and more hardware pushy?

Yes, it does. All modern OSes do. (Yes, we even have USB support now !)

> **Lord Udedenkz said:**
>  Also, it does downscale GPU and CPU clock speeds like in XP? this thing gets hot at full clock speeds, not fun for the hand...

I don't know if it does that according to temperature, but it does underclock my CPU when I'm on battery, so it's very possible.

> **Lord Udedenkz said:**
> Finally, U can emulate DOS with some virtual environment ubuntu app right? Wanna play some Lost Vikings 2.

Check out dosbox.

---

### Post by Lord Udedenkz on 2008-09-14
Ok I will look for that.

Got the MSFONTS thing. I think it might be working.

Oh ok then... it is just weird that VSync-like issues happen while the CPU is not being used to the max on video... so I asked. On second thought, that seems unrelated. Ubuntu uses more CPU then XP as well at more or less idle - esque situations. 
I was thinking more of the GPU, but anyway.

Ok.

Also, I can't seem to get into config for Network Tools - Devices - the interface does not exist or something like that. It is using it though which is rather - wtf scenerio.

Also, about swap - so I originally made it 18GB, then resized it to 4GB. Then it didnt work so then I set it to swapon, restarted it was again off again. There is no apply button after setting the swap to swapon so I don't have a clue. It doesn't use swap anyway, but I have it so, I would like it to be automatically detected each time.

---

### Post by Mornedhel on 2008-09-14
> **Lord Udedenkz said:**
> Also, I can't seem to get into config for Network Tools - Devices - the interface does not exist or something like that. It is using it though which is rather - wtf scenerio.

Huh, same problem. Never noticed that before. What did you need to config ? You can usually do everything from the Network Manager applet on your system tray.

> **Lord Udedenkz said:**
>  Also, about swap - so I originally made it 18GB, then resized it to 4GB. Then it didnt work so then I set it to swapon, restarted it was again off again. There is no apply button after setting the swap to swapon so I don't have a clue. It doesn't use swap anyway, but I have it so, I would like it to be automatically detected each time.

18GB is waaaaay too much. 4GB sounds right (enven though you're unlikely to use it all - if you ever use it at all). Swapping is done automagically, so swapon is for unusual cases. Your swap is most likely correctly detected. Just to make sure, run 'grep swap /etc/fstab', should output exactly one line with 'swap' somewhere. If you feel like it, you can get a more visual experience by installing gparted and running it from Administration > Partition Editor.

---

### Post by Udedenkz on 2008-09-14
*nm*

---

