---
title: "HOW TO: Mounting Sansa e200 series MP3 player on Ubuntu 8.04.x LTS"
date: 2009-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by Francewhoa on 2009-10-16
[FONT=Arial][SIZE=2]You're trying to mount your Sansa MP3 player but it isn't mounting. This bug is already know but not yet fixed on all Ubuntu versions. You can follow the progress at [https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998/](https://bugs.launchpad.net/ubuntu/+source/libgphoto2/+bug/355998/)[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]The following is a temporary workaround. It takes only a few minutes to do. In short you need to change only one word in a system file. Then your Sansa will mount.[/SIZE][/FONT] :guitar:
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**REQUIREMENTS**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Arial][SIZE=2]Works with The following Sansa MP3 players: 2 GB (e250), 4 GB (e260), 6 GB (e270), and 8 GB (e280). [/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Ubuntu 8.04.3 LTS (Hardy Heron Desktop Edition)[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]Sansa original version 1 firmware. It might work with version 2 but I never tried. If it works please post your result below in a comment.[/SIZE][/FONT]
[*][FONT=Arial][SIZE=2]NANO command line text editor or equivalent. Read more about installing NANO at [https://help.ubuntu.com/community/Nano#Installing%20Nano](https://help.ubuntu.com/community/Nano#Installing%20Nano)[/SIZE][/FONT]
[/LIST]
    [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**OPTIONAL**[/SIZE][/FONT]
 
[LIST]
[*][FONT=Arial][SIZE=2]Rockbox firmware 3.2 or more recent. This is an optinal firmware for the Sansa MP3 player.[/SIZE][/FONT]
[/LIST]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]**STEPS FOR ABSOLUTE BEGINNERS**[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]Un-plug your Sansa from Ubuntu. [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]If you have a microSD into the Sansa memory expansion remove it. Sometime the Sansa will boot in loop on mount. This is to avoid this. This is only for the first mount. For the following mounts you can leave the microSD  into the memory expansion.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Open TERMINAL. To do so navigate to APPLICATION > ACCESSORIES > TERMINAL [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Type in the following command in TERMINAL. Then press RETURN key.[/SIZE][/FONT]
 ```
sudo nano /usr/share/hal/fdi/preprobe/10osvendor/20-libgphoto2.fdi 
```[FONT=Arial][SIZE=2]When ask for a password type in your Ubuntu administrator password. Then press RETURN key.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]The file **20-libgphoto2.fdi **will open into the TERMINAL NANO text editor.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Press **F6** on your keyboard. This is the search feature.


Type in the following then press return key.
[/SIZE][/FONT]```
[FONT=Arial][SIZE=2]e280[/SIZE][/FONT]
```[FONT=Arial][SIZE=2]

The search will bring you to the following two lines[/SIZE][/FONT]
```
<merge key="camera.libgphoto2.name" type="string">Sandisk Sansa e280</merge> 
<merge key="camera.libgphoto2.support" type="bool">true</merge> 

``` [FONT=Arial][SIZE=2]In this example I'm using a Sansa e280. Make sure the first line match you Sansa model number. If not continue searching through the lines.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]In the following line change the 'true' for a 'false'.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]BEFORE[/SIZE][/FONT]
```
<merge key="camera.libgphoto2.name" type="string">Sandisk Sansa e280</merge> 
<merge key="camera.libgphoto2.support" type="bool">true</merge> 

```[FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]AFTER[/SIZE][/FONT]
```
<merge key="camera.libgphoto2.name" type="string">Sandisk Sansa e280</merge> 
<merge key="camera.libgphoto2.support" type="bool">false</merge> 

```[FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Press CTL-X keys.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Press Y key. Then press RETURN key.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]You're now back to TERMINAL. Close TERMINAL window.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]You don't need to reboot Ubuntu. [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Make sure your Sansa USB mode is set to MSP not MTP. This is a Sansa setting not Ubuntu. I never tried with MTP. It might work. [/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]Plug-in your Sansa. Go to PLACES > COMPUTER[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]You have successfully mount your Sansa. You'll see two new icons: Sansa e280 & USB Drive. USB Drive doesn't work. Double click on Sansa e280 icon. Open the folder FILES. This is where you can copy your MP3 & audio files manually if needed.[/SIZE][/FONT]
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 [FONT=Arial][SIZE=2]
[/SIZE][/FONT] 
 *[FONT=Arial][SIZE=2]Note: Updating your Ubuntu might overwrite above change. As a result the Sansa won't mount. To fix this redo above steps again. This is a workaround until the bug is permanently fix.[/SIZE][/FONT]*

---

### Post by SR_ELPIRATA on 2009-11-28
Wanted to ask, because I can access my 'loaned' Sansa e260 without problems, it mounts, I can see the internal folders and everything, I can even copy pictures, music and videos if I want, BUT... after unmounting, when I turn on the unit, nothing shows at all in each section (video, pictures or music) and if u go to settings and info it says that there is memory being used.

At first I thought it was because I had everything in folders inside each section, but I removed them, also renamed all the files so no spaces were shown, and yet it doesnt detect any of the files there.

Oddly... I can use the recorder and it will save those files in the corresponding section and I can use them, just not the music, pictures and videos.

Any help is appreciated...

ELP

---

### Post by VirusCollector on 2009-12-05
Using Sandisk Sansa Clip (v1): This fix worked(yay!) but only when the USB was set to the option mentioned. Auto Detect did not work.

...However, I can't write to it, I can only delete things. Weird.

---

### Post by AZBiker on 2010-12-08
Thanks for posting this!

This bug STILL isn't fixed in Lucid.

---

### Post by Shobuz99 on 2010-12-12
I have a related issue and want to know if anyone has this problem.
I am using Ubuntu 10.04 LTS on a desktop.
I have a Sansa 4GB player. 
If I connect the Sansa 4GB player to any USB port BEFORE I cold boot
the machine, my boot process hangs at the 'splash' screen for the BIOS.
If I disconnect the Sansa 4GB player from the USB, the machine continues to process through the boot startup. Why is this happening?
I can cold boot with no problem if I have either a 160GB USB drive or flash drive externally connected; but not the Sansa 4GB player.
The only way I can get the Sansa to connect is AFTER my machine is booted up and ready. It works fine from that point.
Is my computer trying to determine if the Sansa 4GB player is a 'bootable' drive and can't get a response from it? Very weird, to me.

Shobuz99

---

### Post by abrianb on 2010-12-30
My e280 does the same. I cant write to the device after Ubuntu boots up. The bug is not fixed.

---

