---
title: "Help in setting up new desktop"
date: 2013-03-14
forum: New to Ubuntu
---

### Post by harfin on 2013-03-14
I have been using my ageing Dell E520 for several years now as a dual boot with Windows XP pro. Unfortunately it's struggling with space I think, and the number of upgrades there have been since I first installed vn 9.04 form CD back in July 2009. I am currently on Release 12.04 (precise) 32-bit, with Kernel Linux 3.2.0-39-generic, GNOME 3.4.2, Intel® Celeron(R) CPU 3.06GHz and 1.5Gb RAM with a Seagate external 1Tb drive and a CDRW drive. There is a Belkin NWireless device connecting it wirelessly to my Broadband BT HomeHub and I use Evolution as my email client and Chrome for my browser.


I am seriously considering a new Zoostorm desktop with the following spec: 
AMD A4-3300 2.5Ghz Dual Core APU Cache: 1MB, with 4GB DDR3 1333Mhz RAM and a 320GB SATA 2.5” HDD, AMD Radeon HD 6410D Graphics Card High Definition, Audio 5.1 channel It has 1 x PS/2 Keyboard Port, 1 x D-Sub VGA Port, 1 x HDMI Port, 6 x USB 2.0 Port, 1 x RJ-45 Port and 3 x Audio Jacks and 1 x PCI-e x 16 Slot, 1 x PCI Slot, and 1 x PCI-e Slot.


I envisage running XP on the current Dell (still a few things only run on Windows) and use the new pc for my normal home computer running just Ubuntu. Moving files etc from one PC to the other is not a problem.


Are there known incompatibility issues with Ubuntu and any of the proposed new PC's components?


I do have the original Ubuntu set-up CD - v 9.04, but the proposed PC is a 64 bit machine, so is that appropriate?


If not, is there a step by step guide to setting up a new PC? 


Any advice / guidance would be greatly appreciated.

---

### Post by Impavidus on 2013-03-14
Get a new install disk for either 12.04 or 12.10 64 bit. Installing an obsolete version and upgrading to the latest version is much more trouble and a larger download than just getting a new installation disk (or usb) and you can't upgrade from 32 to 64 bit.

It's a processor with integrated graphics, combined with a separate graphics card, which sometimes gives problems, but it seems most people get it to work OK. It seems proprietary drivers are available for that graphics card, but, being from AMD, I wouldn't really count on it they will continue to support it for Linux for as long as you're going to use that computer. Their reputation isn't very good on that matter.

---

### Post by grahammechanical on 2013-03-14
So, you are clear in your mind that you want this hardware. The real test would be to run a Ubuntu live session. If more of us ran System Testing on Ubuntu then this web page would be more useful to people like you. It is called Ubuntu Friendly.

[https://friendly.ubuntu.com/](https://friendly.ubuntu.com/)

Regards.

---

### Post by harfin on 2013-03-14
Thanks so much for that.

The Zoostorm comes without any o/s so will the pc on being switched on automatically see the usb stick (previously loaded with vn 12.10) and activate it?
 
Is there any advantage in using my old CD to at least get the pc up and running with Ubuntu and then switch it off and re-boot with the usb stick and it's new version?

Alan

---

### Post by harfin on 2013-03-14
Thanks [COLOR=#000000]grahammechanical.

I noticed [/COLOR][COLOR=#000000] Ubuntu Friendly this morning somewhere for the first time when I opened a gizmo called System Test. I guess that is what you are referring to.  More than happy to System Test if that's of help.

I am not committed (some would argue that I should be!) yet to the Zoostorm, but it's a a good price and I am not a heavy PC user as regards gaming and the like.  I use it mostly for transcription work (paper data to database), a bit of Desktop publishing and email / voip.

Regards
Alan[/COLOR]

---

### Post by mastablasta on 2013-03-14
> **harfin said:**
> Thanks so much for that.

The Zoostorm comes without any o/s so will the pc on being switched on automatically see the usb stick (previously loaded with vn 12.10) and activate it?

yup. download the iso. check the md5sum, then use unetbootin or linuxlive useb to "burn" the image to USB stick. then test the stick to see if it works well.

live OS will load into ram and won't touch the disk. if they allow it that is. i was recentl yin a country where 90% of notebooks ship with no OS preinstalled. but no one allowed to boot before you bought it. lame!

> 
Is there any advantage in using my old CD to at least get the pc up and running with Ubuntu and then switch it off and re-boot with the usb stick and it's new version?


in linux drivers are built into kernel for the most part. so with 9.04 you would be using old kernel likely from 2008 on hardware from 2012. how well do you think it will go? sure some thing will work or some generic drivers will be used but chances of things going wrong / not working are quite high.

so i suggest as others did to use the latest version and 64 bit (if not latest then at least 12.04 LTS). latest version is also very different from version before it in that it uses unity interface which need 3D acceleration to work well.

you also asked if everyting will work. hard to say. it should. one thing to consider besides APU and another GPU is also the sound chip. will the sound card work? i don't know. but if this is a built in chip a new linux compatible card costs as little as 12 or 13 EUR.

edit: forgot to mention - you needed a step by step guide - have a look at ubuntu manual link in my signature.

---

### Post by harfin on 2013-03-14
Thanks for that
> **mastablasta said:**
>  so i suggest as others did to use the latest version and 64 bit (if not latest then at least 12.04 LTS). latest version is also very different from version before it in that it uses unity interface which need 3D acceleration to work well.

So should I be using the latest version or the 12.04LTS
[COLOR=#000000]
[/COLOR]> **mastablasta said:**
>  [COLOR=#000000]forgot to mention - you needed a step by step guide - have a look at ubuntu manual link in my signature.[/COLOR]

I have downloaded that on to the same USB stick that I'll be downloading the o/s to.  Thanks again for that!


As to sound,I've had hassles with my existing PC with sound (incorporated chip), so no change there!  Even now the sound often doesn't operate after a 12.04 new linux kernel upgrade, but it does after a subsuquent boot (or two)

So it seems like the consensus is to give it a go!  I'll hold off for a couple of days before I order it, just in case there are any other thoughts arrive. 

Thanks all.

Alan

---

### Post by harfin on 2013-03-14
[COLOR=#000000]Thanks for that [/COLOR][B]mastablasta
[/B][COLOR=#000000]
Re > [/COLOR][COLOR=#000000]check the md5sum[/COLOR][COLOR=#000000]  isn't that to do with dual boot systems of Ubuntu? The new pc will be a sole ubunto machine

[/COLOR][COLOR=#000000]Re unetbootin? [/COLOR][COLOR=#000000]linuxlive?
[/COLOR][COLOR=#000000]
I have the ISO now on my external expansion drive, but when I tried that start-up disk creator it seemed to be wanting to do something to my existing PC, I haven't ordered the new one yet, so at that point I aborted the USB Stick bootup

Regards
Alan[/COLOR]

---

### Post by TK999 on 2013-03-14
Checking an md5sum or shaXsum is to verify file integrity, and is not relevant to dualboots. It's useful to check that the file is not damaged and was not tampered with; the download page lists the correct values you should get.

---

### Post by mastablasta on 2013-03-15
> **harfin said:**
> 
So should I be using the latest version or the 12.04LTS
[COLOR=#000000]

For new hardware use the latest version. Though i suppose 12.04 should also work.

[/QUOTE]
[/COLOR]As to sound,I've had hassles with my existing PC with sound (incorporated chip), so no change there! Even now the sound often doesn't operate after a 12.04 new linux kernel upgrade, but it does after a subsuquent boot (or two)
[/QUOTE]

What is the chip? suggets you post separate thread on this. if it's intelHD i know a work arround that work like 70% of the time. :) i have simillar issue.

> **harfin said:**
> [COLOR=#000000]Re isn't that to do with dual boot systems of Ubuntu? The new pc will be a sole ubunto machine

As explained it's done to check file integrity. i.e. to make sure that the image you downloaded is exactly the same as the one on server. if oyu download via torrent then this is done for you during torrent download process.
> 
[/COLOR][COLOR=#000000]Re unetbootin? [/COLOR][COLOR=#000000]linuxlive?
[/COLOR]

not sure what is wrong. but here is how i use them. i install them on my windows mashcine. i have .iso there located in some folder (for example downloads). then i plug in a usb stick. launch the programme. select the USB stick as install destination and the linux image file as the linux i want to put on the usb stick. the programme then does it's job and that is it. USB stick get's reformated (if this option is selected - i think linuxliveUSb can do it without reformat. it's best to have fat32 file format on usb stick for this to work nicely. i think it might also work well with ntfs though i am not sure. 

LinuxliveUSB has an option of adding portable virtual box on the key. you can then just click on virtualise this key and the linux will start in virtual box inside windows.

if you do this on linux you can use dd and you need to be carefull with that command. unebootin also has a linux version.

---

### Post by harfin on 2013-03-15
Thanks for the help, [COLOR=#000000]mastablasta. [/COLOR]

I posted a thread quite so e time ago regarding the issue of sound) and since then I have tolerated the status quo I think the thread was > [http://ubuntuforums.org/showthread.php?t=1230172&highlight=sound](http://ubuntuforums.org/showthread.php?t=1230172&highlight=sound)

I was thinking about the LTS version, thinking being that five years of guaranteed support for that version is a reasonable span to have everything working optimally.

Regards
Alan

---

### Post by harfin on 2013-03-22
Well that was a disaster!

The USB stick seemed to start off OK, once I had selected the usb in the bios, but after a bit of a start it just stalled.  Tried rebooting a couple of times, all to no avail.

So I decided to load windows xp from my oriiginal disc, and that went on fine.  Took a long while but it is up and running. So there's nowt wrong with the new pc.  Couple of wee problems but nothing life-threatening.  

So loaded chrome ok (using my existing Google account), and went off to ubuntu.org to see what I could do.  I decided it might be simpler to download the windows/ubuntu version direct to the new PC with windows as 1st boot-up option.  Seemed to be OK, but when I rebooted and selected to load ubuntu, it started off again seemingly OK, but once again it stalled on the screen "loading Ubuntu for first time" and it went off to sleep again.

So, I think my best option might just be to download the full CD version of Ubuntu (the new pc has a dvd writer on it) and hopefully that might work.  It's a shame really that the previous attempt hadn't worked as I could have elected the 64 bit version, but the only option for CD / DVD disc creation is the 32 bit, it seems.

Anyone else got any suggestions?

Alan

---

### Post by mastablasta on 2013-03-22
> **harfin said:**
> The USB stick seemed to start off OK, once I had selected the usb in the bios, but after a bit of a start it just stalled. Tried rebooting a couple of times, all to no avail.

In other words you never got any menu or something like that? which means something is likely wrong with the downloaded image. have you checked it's md5sum? anothe roption is that USB stick is not bootable or simply not recognised by computer. I bough a nice mini USB with 16 Gb,, resistant to dust and water, goes nicely on keychain. but the darn thing won't boot. no matter what. well actualyl if i use plop boot manager and floppy i can make it boot but it does not boot by itself like other USB sticks i have.


> So loaded chrome ok (using my existing Google account), and went off to ubuntu.org to see what I could do. I decided it might be simpler to download the windows/ubuntu version direct to the new PC with windows as 1st boot-up option. Seemed to be OK, but when I rebooted and selected to load ubuntu, it started off again seemingly OK, but once again it stalled on the screen "loading Ubuntu for first time" and it went off to sleep again.


you may need to add one of the boot options: [https://help.ubuntu.com/community/BootOptions](https://help.ubuntu.com/community/BootOptions)

try nomodeset

> So, I think my best option might just be to download the full CD version of Ubuntu (the new pc has a dvd writer on it) and hopefully that might work. It's a shame really that the previous attempt hadn't worked as I could have elected the 64 bit version, but the only option for CD / DVD disc creation is the 32 bit, it seems.


huh? not sure what you mean.  an image is an image. there are 32 bit and 64 bit images. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop)

you can use both. but 12.10 needs a DVD i believe if that is what you mean.

---

### Post by harfin on 2013-03-22
> **mastablasta said:**
> In other words you never got any menu or something like that? which means something is likely wrong with the downloaded image. have you checked it's md5sum? another option is that USB stick is not bootable or simply not recognised by computer. I bough a nice mini USB with 16 Gb,, resistant to dust and water, goes nicely on keychain. but the darn thing won't boot. no matter what. well actualyl if i use plop boot manager and floppy i can make it boot but it does not boot by itself like other USB sticks i have. 

Strangely enough mine is 16 Gb but I think mit must be bootable, as when the PC looked the usb stick it did start a Ubunto screen. It got as far as showing "Ubuntu" on the screen, but that was it.  Must admit I didn't really understand the msdsum bit; silly me. So the image could have been flawed.

> **mastablasta said:**
> huh? not sure what you mean.  an image is an image. there are 32 bit and 64 bit images. [http://www.ubuntu.com/download/desktop](http://www.ubuntu.com/download/desktop) you can use both. but 12.10 needs a DVD i believe if that is what you mean.

I saw somewhere that on recall that it was the fact that I had to have a DVD writer to get the 64 bit option, and as I only have a CD writer on  my old Dell, I could only get it via the USB stick.  Now that I've got the new PC running Windows I should be able to download the file on the new one and burn it onto DVD.  Haven't tried the burn part of the DVD drive yet though !

I'll report how I got on!

Thanks again for your patience !

Alan

---

### Post by harfin on 2013-03-22
> **harfin said:**
>  I'll report how I got on! Thanks again for your patience ! Alan

Some progress!

I couldn't get the pc to boot from the DVD - it just reverted to Windows.  So I put the DVD in once the PC was actually in Windows.  And at that Ubuntu started up.  Went through an install process and then asked for my log on name and password.  That caused it to start "*Running Ubuntu for first time"*.  Then it hung again!  

This time I did forced a reboot, and a screen flipped up giving me an option to run Ubuntu in "*safe mode.  *That worked, and after heaps of lines of guff scrolled down, I got to a familiar Ubunto screen.  

So I could then do a check for updates and got over 200 Mg of updates!  So, did that, and tried to reboot.

Again it won't just run through from the Windows or Ubuntu option screen to Ubuntu when I select it.  Tried a cold boot also and that doesnt achieve anything.

So at the moment my method is 
[LIST]
[*]boot,
[*]select Ubuntu at option screen
[*]let it get to a stall point
[*]turn the pc off
[*]switch on again
[*]select 'safe' mode
[*]get a reasonably normal ubuntu set up.
[/LIST]

So, any suggestions anyone?

Alan

---

### Post by arpanaut on 2013-03-22
If you have the integrated graphics and the Nvidia card, you might want to look into Bumblebee.
or disable the integrated and install the proper graphics driver for your card.

---

### Post by harfin on 2013-03-23
> **arpanaut said:**
> If you have the integrated graphics and the Nvidia card, you might want to look into Bumblebee.
or disable the integrated and install the proper graphics driver for your card.

Now I'm totally lost!
Alan

---

### Post by harfin on 2013-03-23
I'm pleased to say, that I think (hope?) that I now have a functioning PC. I searched the forum again, using the key words Vesa, and found a solved thread regarding my graphics card.  On that thread the user was prompted to ensure that the old driver was removed and that the Ubuntu one be installed.  Following that advice I carried out the recommended terminal commands and it seems to have worked.  

The last couple of times I rebooted, I got through to my desktop without having to go through the 'safe' mode, so I'm hoping that all will now be well.

My thanks to those who have offered advice and help; you're all stars!

Regards
Alan

---

### Post by harfin on 2013-03-24
New pc working OK.  No problems with booting up now, but still have couple of things to improve:
[LIST=1]
[*]I need to change the order of boot so that Ubuntu is the first option at the initial screen, rather than Windows XP as it is at the moment.  Anyone tell me how I do this?
[*]At some stage, If I would like to have the system just booting up entirely; is there a manual or 'how to do page' or something similar that shows one how to do it?
[/LIST]
[SIZE=2]
Thanks again everyone, am almost there!

Alan
[/SIZE]

---

