---
title: "Installation problems"
date: 2012-12-02
forum: New to Ubuntu
---

### Post by mvanbv00 on 2012-12-02
Installation*
My computer running Windows 7 got an error the other day basically saying that some of the boot files went corrupt or missing. To repair it I would basically have to buy Windows again, and since I have had many issues with Windows, I do not want to buy it again or try to repair it. 

So at this point, my computer won't boot at all. At startup for Windows it gives the message about missing or corrupt files. The only options Windows gives me is to repair windows or to boot normally. Neither of these work. They just freeze the computer. 

I made a cd on my roommates computer with the .iso image of the vector linux and tried to load it on my computer by loading the cd in the tray and pressing F12 while booting to give me the option to boot with the cd. The Windows takes over and goes straight to the repair screen or boot normally screen. 

What are my options? I really don't care if I have to delete the Windows 7 off my computer because it's already corrupt and I would have to buy another version of Windows anyway. Is there anyway I can install Linux around the Windows or is there anyway I can delete the the Windows? I don't get any options by pressing the function keys at boot up.

---

### Post by Frogs Hair on 2012-12-02
Hello and Welcome

What happens if you choose to install instead of boot live ?

If that option works you can overwrite the hard drive with ubuntu. I don't know what the F12 function does on your computer because key bindings vary from system to system.

There is a page like this for 12.04 also. Follow the links on the page for more information.   

[http://www.ubuntu.com/download/help/install-desktop-latest](http://www.ubuntu.com/download/help/install-desktop-latest)

---

### Post by mastablasta on 2012-12-03
> **mvanbv00 said:**
> I made a cd on my roommates computer with the .iso image of the vector linux and tried to load it on my computer by loading the cd in the tray and pressing F12 while booting to give me the option to boot with the cd. The Windows takes over and goes straight to the repair screen or boot normally screen. 

 
that means that CD is corrupt (bad burn) or image is corrupt (bad download).
 
make sure you do md5sum check after download: [https://help.ubuntu.com/community/HowToMD5SUM](https://help.ubuntu.com/community/HowToMD5SUM)
make sure you burn the image as image (i.e. you should get a number of files and folder on CD) at slow speed.
 
edit: if oyu hve windows repair DVD you can also use that to repair the boor of windows 7.

---

### Post by mvanbv00 on 2012-12-03
[IMG]http://s1278.beta.photobucket.com/user/mvanbv00/media/15975_500817636619215_1025228568_n.jpg.html[/IMG][IMG]http://i1278.photobucket.com/albums/y513/mvanbv00/failedhd.jpg[/IMG]

I think that my hard drive is the problem. All of the Windows failure screens and then this message while trying to install Unbutu lead me to believe that my hard drive failed.

---

### Post by Bashing-om on 2012-12-03
mvanbv00; Hi !
As your disk is windows, I am not certain this will work. But worth a try.

Boot up the ubuntu install CD into "try ubuntu" mode.
Once booted to the desk top, click on the top icon in the launcher (left side of screen)->
dash -> enter the term "disk utility" -> click on the icon that pops up below this search box.
This starts the disk utility; with an option to test the integrity of the disk, if it has "smart" ability.  

Another option is to zero out that disk, using a terminal command, and see if ubuntu will then install( as above, are you sure the download is good and the burn to cd is good?)
[INDENT][INDENT]just try'n to help <== BDQ

[/INDENT][/INDENT]

---

### Post by mvanbv00 on 2012-12-04
Bashing-om...

I tried launching Ubuntu from the try Ubuntu mode and running the disk utility to format the hard drive. I got an error message from Ubuntu when I tried to format the disk saying something along the lines that it could not access the disk to format it. So now I'm pretty sure that it is my hard drive. I ordered a new hard drive last night so I should have that in the next 3 days. I'll keep updated when I install Ubuntu. 

Also, I'm pretty sure that my copy of the burn to the cd is good. I ran the md5sum check on the .iso image that I created. The cd was also used to run the "try Ubuntu" mode, so it should be a good download and burn.

Thanks for everyone's help.

---

### Post by Bashing-om on 2012-12-04
It still "might" be possible to reclaim that drive.
From the liveCD "try ubuntu" mode; activate a terminal (ctl+alt+t key combo) and run this terminal command:
```
sudo dd if=/dev/zero of=/dev/sda bs=1M
```Will write zeros to all of the disk; if dd is able to write to disk, may take several hours to complete. Then install ubuntu.
[INDENT][INDENT]hth <== BDQ

[/INDENT][/INDENT]

---

### Post by mvanbv00 on 2012-12-06
So I got my new hard drive and installed it. I inserted the Ubuntu boot disk and nothing happened. I thought it could be a bad burn or download so I checked the md5sum and sure enough the md5sum files didn't match. So I re-downloaded ubuntu.iso and checked it and it matched. So I inserted the new disk and still nothing. 

I can hear the fan turn on and the screen back light turns on but just sits at a black screen. I tried pressing F12 and the other function buttons and nothing happens. 

Help... Is there something else wrong with my computer or am I doing something wrong? Do I have to do something to the new hard drive to make it work?

---

### Post by Bashing-om on 2012-12-06
Is your equipment ide (flat ribbon cable) ? Did you reconnect the ribbon correctly and pin the master/slave pinning on the hard disk drive correctly ?

sata ? Check that the power cable is a solid connection; the data cable can not have any sharp bends (not likely a cause in this case).
Cabling, pinning and power is all that comes to mind. Bios does come up, no ?

[INDENT]still try'n to help <== BDQ

[/INDENT]

---

### Post by mvanbv00 on 2012-12-06
Bios does not load. Pressing the function keys such as F12 or F8 does nothing. Installing the hard drive (SATA) was simply plugging it in the slot I took the old one out of. There was not any power cable to get bent or unplugged or anything like that for the HD. The pins are all the same as the old HD. 

I have also since tried the LinuxLive USB boot method. It verifies that the .iso is downloaded correctly. It will not load either. My flash drive has a light that illuminates when the computer recognizes it, and it will not light up on the computer.

---

### Post by mastablasta on 2012-12-07
it can be a bad drive or bad sata cable. if you can try to get another cable.
 
i had a similar thing once on XP. boot files were corrupted. had reinstalled, used repair console, the whole thing repeated.... just before throwing out the drive i decided to replace the cabel and it's been working great since then.
 
btw windows 7 boto can be repaired using windows 7 dvd or repair disk and then via repair console ont hat disk.

---

### Post by mvanbv00 on 2012-12-08
I finally got my system to work. After I installed the new HD nothing would load. The BOIS wouldn't even load after pressing F12 or any other function key. The boot CD wouldn't load because my computer wasn't configured to boot from the CD drive. After trying numerous solutions that I found after googling my issues, I finally found one that worked. With Toshiba, holding the 0 key and booting restores the system to default settings. This didn't work the way it was supposed to, but it allowed me to boot from the disk, finally!! 

So I installed Mint and everything is working fine now. Thank you everyone for all of your help.

---

### Post by Bashing-om on 2012-12-08
Out standing ! You do good work!

Glad ya got it sorted out. Please mark this thread as solved (thread tools above),

and Happy trails to you. <== BDQ

---

