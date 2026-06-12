---
title: "Can't get desktop from terminal!!"
date: 2011-09-06
forum: Oneiric Ocelot Testing and Discussion (CLOSED)
---

### Post by ventrical on 2011-09-06
H i,

  I had some problems installing Oneiric on a 500GBST SATA drive. I tried all sorts of suggestions but can't seem to get the screen up. Since I cannot take screen shots of my problem I did a small video to show what is going on. I am not sure of the next steps to take to get the graphical desktop. It works great from a pre-installed version of Ubuntu Lucid on an IDE drive - with compiz and all 3D grapics - so - I am not sure if I have a  graphics problem that is conflicting with the SATA drive.

Thanks for any ro all help..

*note*

  I currently have Maveric 10.10 installed.  I thought I had a problem with he SATA partition .. but I do not think this was the case. i hope I am not being off topic here. I eventually want to put Oneiric back on to that drive.  Thanks:)


[http://www.youtube.com/watch?v=HRpe_RAbGEg](http://www.youtube.com/watch?v=HRpe_RAbGEg)

---

### Post by lucazade on 2011-09-06
> **vent rical said:**
> .. I am not sure if I have a  graphics problem that is conflicting with the SATA drive . .
[/URL]

This sounds more or less like da Butterfly Effect of Chaos Theory.
It states that, in theory, the flutter of a butterfly's wings in China could, in fact, actually effect weather patterns in New York City, thousands of miles away. In other words, it is possible that a very small occurance can produce unpredictable and sometimes drastic results by triggering a series of increasingly significant events.

trying to be serious does the oneiric livecd work correctly? does it start up?
or it is only your installation to be compromised?

---

### Post by ventrical on 2011-09-06
I'm serious man!

Both alpha and beta1 cds installed out of the box on other machines.An Acer Aspire 3620 and a U8668-D dual core 2.88GHz with only 8 MBs of AGP sdram... so .. yeah .. the <cds are fine.

---

### Post by ventrical on 2011-09-06
> **lucazade said:**
> This sounds more or less like da Butterfly Effect of Chaos Theory.
It states that, in theory, the flutter of a butterfly's wings in China could, in fact, actually effect weather patterns in New York City, thousands of miles away. In other words, it is possible that a very small occurance can produce unpredictable and sometimes drastic results by triggering a series of increasingly significant events.

trying to be serious does the oneiric livecd work correctly? does it start up?
or it is only your installation to be compromised?

You asked me to start another thread and I did. I don't get your humor.

---

### Post by lucazade on 2011-09-06
> **ventrical said:**
> You asked me to start another thread and I did. I don't get your humor.

i'm asking if that error about radeon is present in both a livecd session and also when you install oneiric on hd.
humor was about the conflict of your hd and the graphics drivers, where two distinct things can conflict in such way. :)

---

### Post by ventrical on 2011-09-06
The CDs work great with graphics. No error. Just after install and reboot.

Thanks anyways.

---

### Post by 3rdalbum on 2011-09-06
Er... I just had a look at your video. It clearly says "Ubuntu 10.10" and that "new release 'Natty' is available". I'm not sure how Oneiric comes into this.

Also, X needs to be run as root, so you would have to do "sudo startx", except that it isn't the correct way of starting X anymore. On Ubuntu 11.04 and earlier you would use:

```
sudo service gdm start
```

On Ubuntu 11.10 you would use:

```
sudo service lightdm start
```

---

### Post by effenberg0x0 on 2011-09-07
If you can't get to a X Session using sudo service gdm restart or sudo service lightdm restart, I think you probably would have to install proper video drivers for your video card.

I have an NVidia Video Card. A few actually. Many times when I update Ubuntu, I have to re-run the NVidia driver setup to be able to have a X Session again. Otherwise I'm stuck at the prompt just like you show us in your video. It's something very normal, like every week. As I already keep the Video driver in my home directory, usually all it takes is to run something like sudo ~/NVidia*.bin && sudo service lightdm restart

So I am guessing that may be whats going on there. I don't know what Video Card you have, but you can probably go the manufacturer site and download drivers for Linux with some instructions on how to install them. Usually you would just have to download the setup file, unzip it, chmod the downloaded file +x and run it. 

If you are not sure of the brand or model, you can try something like this:

```

[03:04 ][al:AL-DESK:~]
$ **lspci | grep VGA**
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)

```

Also, depending on the card, you may have open source drivers, proprietary drivers or both available on the net. In my case, for example, I have NVidia Open Source drivers (developed by community) and NVidia Proprietary Drivers. The proprietary ones are better, so I choose to use them and I download them from NVidia site. If I wanted to use the Open Source ones, I could easily use synaptic/apt-get (the Nouveau driver). 

So basically you'll have to do some research to find out exactly what is your video card manufacturer, model, if there are proprietary drivers for Linux OS in the manufacturer site available for download (with proper install instructions), what would be the Open Source alternative, choose between proprietary x Open Source and then proceed to install.

Regards,
Effenberg


PS: Check out these links:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
[http://askubuntu.com/questions/8019/how-can-i-enable-ati-open-source-drivers](http://askubuntu.com/questions/8019/how-can-i-enable-ati-open-source-drivers)

---

### Post by ventrical on 2011-09-07
> **effenberg0x0 said:**
> If you can't get to a X Session using sudo service gdm restart or sudo service lightdm restart, I think you probably would have to install proper video drivers for your video card.

I have an NVidia Video Card. A few actually. Many times when I update Ubuntu, I have to re-run the NVidia driver setup to be able to have a X Session again. Otherwise I'm stuck at the prompt just like you show us in your video. It's something very normal, like every week. As I already keep the Video driver in my home directory, usually all it takes is to run something like sudo ~/NVidia*.bin && sudo service lightdm restart

So I am guessing that may be whats going on there. I don't know what Video Card you have, but you can probably go the manufacturer site and download drivers for Linux with some instructions on how to install them. Usually you would just have to download the setup file, unzip it, chmod the downloaded file +x and run it. 

If you are not sure of the brand or model, you can try something like this:

```

[03:04 ][al:AL-DESK:~]
$ **lspci | grep VGA**
01:00.0 VGA compatible controller: nVidia Corporation GF106 [GeForce 450 GTS] (rev a1)

```Also, depending on the card, you may have open source drivers, proprietary drivers or both available on the net. In my case, for example, I have NVidia Open Source drivers (developed by community) and NVidia Proprietary Drivers. The proprietary ones are better, so I choose to use them and I download them from NVidia site. If I wanted to use the Open Source ones, I could easily use synaptic/apt-get (the Nouveau driver). 

So basically you'll have to do some research to find out exactly what is your video card manufacturer, model, if there are proprietary drivers for Linux OS in the manufacturer site available for download (with proper install instructions), what would be the Open Source alternative, choose between proprietary x Open Source and then proceed to install.

Regards,
Effenberg


PS: Check out these links:
[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)
[https://help.ubuntu.com/community/BinaryDriverHowto/ATI](https://help.ubuntu.com/community/BinaryDriverHowto/ATI)
[http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html](http://manpages.ubuntu.com/manpages/jaunty/man4/radeon.4.html)
[https://help.ubuntu.com/community/RadeonHD](https://help.ubuntu.com/community/RadeonHD)
[http://askubuntu.com/questions/8019/how-can-i-enable-ati-open-source-drivers](http://askubuntu.com/questions/8019/how-can-i-enable-ati-open-source-drivers)

  Ok.. thanks!! This is exactly it - that which I have been looking for. As I note before that I had tried all those other commands as mentioned by a previous poster - and they did not work.

 Also - as >I had mentioned - I had installed Oneiric first and I could not get a desktop - so then the partiton got locked somehow. Somebody suggested I use LinuxOS and I did - and I could not unlock <protected partition> So I experimented with a Maveric install and this at least reformatted the drive (as was also suggested).

So I will try those commands out.. Mostly I just want to know the onboard video driver - I may have to get a new Fast-PCI card for video.

  I will keep all you helpers updated on this.

Thanks.

---

### Post by ventrical on 2011-09-07
> **3rdalbum said:**
> Er... I just had a look at your video. It clearly says "Ubuntu 10.10" and that "new release 'Natty' is available". I'm not sure how Oneiric comes into this.

Also, X needs to be run as root, so you would have to do "sudo startx", except that it isn't the correct way of starting X anymore. On Ubuntu 11.04 and earlier you would use:

```
sudo service gdm start
```On Ubuntu 11.10 you would use:

```
sudo service lightdm start
```

I went through all this a few days ago. No luck!! I installed Maveric because it was suggested that they may be  problem with my SATA drive.

 I am going to try the video check and if I get it working - then re-install Oneiric.

---

### Post by nidzo732 on 2011-09-07
Try this
[http://ubuntuforums.org/showthread.php?p=11226551#post11226551](http://ubuntuforums.org/showthread.php?p=11226551#post11226551)

---

### Post by ventrical on 2011-09-07
Here is the PC hardware setup:

dale@dale-desktop:~$ lspci
00:00.0 Host bridge: ATI Technologies Inc Radeon Xpress 200 Host Bridge (rev 01)
00:01.0 PCI bridge: ATI Technologies Inc RS480 PCI Bridge
00:11.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:12.0 IDE interface: ATI Technologies Inc IXP SB400 Serial ATA Controller (rev 80)
00:13.0 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.1 USB Controller: ATI Technologies Inc IXP SB400 USB Host Controller (rev 80)
00:13.2 USB Controller: ATI Technologies Inc IXP SB400 USB2 Host Controller (rev 80)
00:14.0 SMBus: ATI Technologies Inc IXP SB400 SMBus Controller (rev 82)
00:14.1 IDE interface: ATI Technologies Inc IXP SB400 IDE Controller (rev 80)
00:14.2 Audio device: ATI Technologies Inc IXP SB4x0 High Definition Audio Controller (rev 01)
00:14.3 ISA bridge: ATI Technologies Inc IXP SB400 PCI-ISA Bridge (rev 80)
00:14.4 PCI bridge: ATI Technologies Inc IXP SB400 PCI-PCI Bridge (rev 80)
01:05.0 VGA compatible controller: ATI Technologies Inc RC410 [Radeon Xpress 200]
02:02.0 Ethernet controller: Realtek Semiconductor Co., Ltd. RTL-8139/8139C/8139C+ (rev 10)
dale@dale-desktop:~$ 

I also think that I have a SATA issue with this PC. I am running it now from a LUCID IDE drive and there seems to be problems with the boot-up of the SATA drive - it soprt of comes and goes.. so for now I am going to put it on the shelf  and continue testing Oneiric using my other systems.

thanks everyone for your help! :)

---

### Post by effenberg0x0 on 2011-09-07
Hey,

I see that you VGA card (Radeon Xpress 200) is supported by the Open Source Radeon driver. There's an official Ubuntu howto with good instructions for you:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Try to follow the instructions there and get back with results. I believe you'll have no issue putting it to work.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-07
> **effenberg0x0 said:**
> Hey,

I see that you VGA card (Radeon Xpress 200) is supported by the Open Source Radeon driver. There's an official Ubuntu howto with good instructions for you:

[https://help.ubuntu.com/community/RadeonDriver](https://help.ubuntu.com/community/RadeonDriver)

Try to follow the instructions there and get back with results. I believe you'll have no issue putting it to work.

Regards,
Effenberg


Thanks.

Looks like a lot of work ! :)

Will give it a try though.

  Just a note.. I have no GUI .. so I can only get the command line.

---

### Post by effenberg0x0 on 2011-09-08
Hey,

Look, I never had an ATI card and never had to deal with one at work. But, from what I am reading, Ubuntu supports it out of the box, no xorg.conf needed, no other complex tweaking. If that is indeed the case, you could safely run something like the following and get your gui back in 2 minutes.

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get purge fglrx
sudo reboot now

```

Restart the system manually if the reboot command above doesn't work.

You should be able to have a gui. If you don't, try:

```

sudo dpkg-reconfigure lightdm
sudo service lightdm restart

```It seems pretty straightforward. Give it a try.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-08
The fglrx was not installed .. so i installed it.

i'll be back

---

### Post by ventrical on 2011-09-08
> **effenberg0x0 said:**
> Hey,

Look, I never had an ATI card and never had to deal with one at work. But, from what I am reading, Ubuntu supports it out of the box, no xorg.conf needed, no other complex tweaking. If that is indeed the case, you could safely run something like the following and get your gui back in 2 minutes.

```

sudo mv /etc/X11/xorg.conf /etc/X11/xorg.conf.backup
sudo apt-get purge fglrx
sudo reboot now

```Restart the system manually if the reboot command above doesn't work.

You should be able to have a gui. If you don't, try:

```

sudo dpkg-reconfigure lightdm
sudo service lightdm restart

```It seems pretty straightforward. Give it a try.

Regards,
Effenberg

 I get the error (mv:cannot stat '/etc/X11/xorg.conf' no such file or directory

---

### Post by ventrical on 2011-09-08
> **ventrical said:**
> I get the error (mv:cannot stat '/etc/X11/xorg.conf' no such file or directory


It tells me DPKG_MAINSCRIPT_PACKAGE missing

---

### Post by ventrical on 2011-09-08
I do have the grub bootloader but as far as the gui.....  I am right back at:

Checking Battery State..............

sheesh 2 more hours on this ...

thank anyways

much appreciated..

---

### Post by effenberg0x0 on 2011-09-08
It should be more simple than that. The links I provided you cover all the information needed to install a Radeon driver. I don't know what is going on there. At this point maybe you should do a dist-upgrade or a full reinstall in order to get things back from scratch. Both processes are quick anyway and, given your current status, you ain't got much to loose. Obviously you'll get a working system if you do one of those two options. But I think you should consider installing a stable version (Natty) of Ubuntu instead. Oneiric is, as of right now, very likely to not be stable (at this point of development - beta software) and it is targeted at developers / bug reporters / package maintainers, support guys, IT people, people used to dealing and fixing bugs and general problems, etc. I am guessing this is not you p&#341;ofile and that you probably need a more reliable system. Just my 2 cents. Either way you choose, remember to back up your information before attempting anything further.

Regards,
Effenberg

---

### Post by ventrical on 2011-09-09
> **effenberg0x0 said:**
> It should be more simple than that. The links I provided you cover all the information needed to install a Radeon driver. I don't know what is going on there. At this point maybe you should do a dist-upgrade or a full reinstall in order to get things back from scratch. Both processes are quick anyway and, given your current status, you ain't got much to loose. Obviously you'll get a working system if you do one of those two options. But I think you should consider installing a stable version (Natty) of Ubuntu instead. Oneiric is, as of right now, very likely to not be stable (at this point of development - beta software) and it is targeted at developers / bug reporters / package maintainers, support guys, IT people, people used to dealing and fixing bugs and general problems, etc. I am guessing this is not you p&#341;ofile and that you probably need a more reliable system. Just my 2 cents. Either way you choose, remember to back up your information before attempting anything further.

Regards,
Effenberg

Hey,

I just did a full install!!! Thats about 5 fresh installs on one machine. Natty won't install , neither will Maveric or any other distro .. but .. as I have posted before.. I can run Lucid off an IDE drive.(not the SATA)

  I am going to mark this thread SOLVED because nobody seems to have the commands to enter into terminal to install the particular driver in question .

  I'll put it on the shelf for later consideration. In the meantime I have other installs to tend to.

---

### Post by frncz on 2011-09-09
> **ventrical said:**
> I do have the grub bootloader but as far as the gui.....  I am right back at:

Checking Battery State..............

sheesh 2 more hours on this ...

thank anyways

much appreciated..

I also ended up with the same hang-up (Checking Battery State..............) when I tried to upgrade natty to oneiric on a Acer Aspire D255.
I re-installed natty from a USB with no problem. I will wait for a more 'ready' oneiric.

---

### Post by cariboo on 2011-09-09
@frncz, your problem is different from ventrical's, what have you done to try and solve your problem? Getting stuck at Checking Battery, is usually an indication of a graphics driver problem, what graphics chipset does your system use?

---

### Post by effenberg0x0 on 2011-09-09
> **ventrical said:**
> Hey,

I just did a full install!!! Thats about 5 fresh installs on one machine. Natty won't install , neither will Maveric or any other distro .. but .. as I have posted before.. I can run Lucid off an IDE drive.(not the SATA)

  I am going to mark this thread SOLVED because nobody seems to have the commands to enter into terminal to install the particular driver in question .

  I'll put it on the shelf for later consideration. In the meantime I have other installs to tend to.

I think no one could really understand what is going on there. I certainly did not. The links I gave you cover absolutely all the details regarding the installation of a Radeon driver. And its hard for me to link a SATA problem with a video driver issue. I can't see the relation.

Anyway, as I said before, Oneiric is still beta and problems at this phase of development are normal. If you are able to get more detailed information about the problem you are facing with the video driver, the SATA vs IDE problem you mentioned and the exact errors you get when attempting to install Maverick and Natty, I suggest you post a bug report at Launchpad. You can have a look at dmesg, cat /var/log/syslog, cat /var/log/Xorg.0.log in order to try to find the exact error messages (just an example).

Remember that if you managed to do a clean install of Lucid, you could always do a dist-upgrade (sudo apt-get dist-upgrade) to move to a more current version without needing to do a full wipe / install of Ubuntu from scratch.

Good luck,
Effenberg

---

### Post by ventrical on 2011-09-09
> **effenberg0x0 said:**
> I think no one could really understand what is going on there. I certainly did not. The links I gave you cover absolutely all the details regarding the installation of a Radeon driver. And its hard for me to link a SATA problem with a video driver issue. I can't see the relation.

Anyway, as I said before, Oneiric is still beta and problems at this phase of development are normal. If you are able to get more detailed information about the problem you are facing with the video driver, the SATA vs IDE problem you mentioned and the exact errors you get when attempting to install Maverick and Natty, I suggest you post a bug report at Launchpad. You can have a look at dmesg, cat /var/log/syslog, cat /var/log/Xorg.0.log in order to try to find the exact error messages (just an example).

Remember that if you managed to do a clean install of Lucid, you could always do a dist-upgrade (sudo apt-get dist-upgrade) to move to a more current version without needing to do a full wipe / install of Ubuntu from scratch.

Good luck,
Effenberg


 I visited the websites that have been posted by you and other members - however - I cannot see anything in the information there which will help me install this particular driver. One page starts out on the right path but then leaves the <order of operation so to speak> and goes out into left feild somewhere. Simply speaking I can't find  the top down , bottom up line of code required. I guess I have to be walked through it.

Lucid:

 As I mentioned before , here and in another form - I did not do a clean install of Lucid on this particular machine. What I said was that I took an IDE HDD from another PC with Lucid already installed on that HDD from the other machine and installed the HDD into the machine in question.

  As I posted before - that all 3D graphics are working along with compiz.. etc.. so the graphics card is working. However, using a 7.5 GB IDE drive is not what I want to use. I want to use the SATA 500GB.

 Now, as I have said, I have <installed> Oneiric about 5 times now. I have got up to the stage where I can get the Grub Boot Loader. It gives me options to boot from either Maveric or Oneiric (and also recovery mode).

  I entered all the commands that were suggested by the members here , but to no avail. I still think this problem is solvable but there is a sequence of code that I am missing and I think it has to do with the actual command line code to install that particualr driver. Then again it can be somthing else totally.

Based on the fact that I can get 3D graphics with Lucid from an IDE drive then I am assuming that it is a video graphics driver error.

 But then there is another problem. And that is that when I try to install  Ubuntu Lucid or Xubuntu Lucid it gives me an error that the "installer has failed". I then proceeded to run Linux Pheonix_OS  and it would not allow me to partition the (SATA) drive. I also tried Puppy Linix and it reported that the drive was protected.

 After all of this I then proceeded to install Maveric 10.10 and got the same thing  <checking battery state>.

 I then seen your message last night and proceeded to try another fresh install of Oneiric. It paritioned the SATA drive (250X250) , installed great, got the grub boot loaded and then = <checking battery state>!!!

 I then entered the commands you had suggested and it then reports that those items are 'not there' and I can't capture that info unless I use my camera and send it up on you-tube.

----------

  I have done distro-upgrade before  from Lucid to Maveric and from Maveric to Natty (during Natty Beta) and then a clean install of Natty - but that was over 4 months ago.  The Maveric install was seamless as was the Natty install but I scraped Natty becase it had big problems with Broadcom drivers .. just No Way to get those driver to work.

  Now , I have excellent wireless but this one prob with this one machine.seems to be very elusive.

  I guess  I can try a distro upgrade but I don't want to corrupt a perfectly good install of Lucid on my IDE drive.

  I am not giving up on this problem. It is just that I have other work and other Oneiric distros to tend too and I don't want anybody wasting valuable time here on one machine.

 Thanks very much and best regards,

ventrical

---

### Post by frncz on 2011-09-09
> **cariboo907 said:**
> @frncz, your problem is different from ventrical's, what have you done to try and solve your problem? Getting stuck at Checking Battery, is usually an indication of a graphics driver problem, what graphics chipset does your system use?

I don't have the machine here but I think the graphics chipset is Graphics Adapter: Intel Graphics Media Accelerator (GMA) 3150
Display: 10.1 inch, 16:9, 1024x600 pixels.

I did not try much to solve the problem as I did not know how. Realising that Oneiric is still at an early stage, I switched back to Natty. I am happy to try Oneiric again, with some help for the graphics issue. 

Regards

---

### Post by ventrical on 2011-09-10
OK.. I ran some commands from the terminal and it gave me this:

root@dale:~# dmesg | grep drm
[   10.321844] [drm] Initialized drm 1.1.0 20060810
[   10.612895] [drm] radeon defaulting to kernel modesetting.
[   10.612903] [drm] radeon kernel modesetting enabled.
[   10.616427] [drm] initializing kernel modesetting (RS400 0x1002:0x5A61 0x8086:0xD600).
[   10.616481] [drm] register mmio base: 0xFDEF0000
[   10.616484] [drm] register mmio size: 65536
[   10.616681] [drm] Generation 2 PCI interface, using max accessible memory
[   10.616722] [drm] Supports vblank timestamp caching Rev 1 (10.10.2010).
[   10.616726] [drm] Driver supports precise vblank timestamp query.
[   10.616766] [drm] radeon: irq initialized.
[   10.617272] [drm] Detected VRAM RAM=64M, BAR=128M
[   10.617283] [drm] RAM width 128bits DDR
[   10.626616] [drm] radeon: 64M of VRAM memory ready
[   10.626620] [drm] radeon: 512M of GTT memory ready.
[   10.626658] [drm] GART: num cpu pages 131072, num gpu pages 131072
[   10.705540] [drm] radeon: 3 quad pipes, 1 z pipes initialized.
[   10.952498] [drm] Loading R300 Microcode
[   11.366510] [drm] radeon: ring at 0x0000000040001000
[   11.366540] [drm] ring test succeeded in 2 usecs
[   11.366826] [drm] radeon: ib pool ready.
[   11.366962] [drm] ib test succeeded in 0 usecs
[   11.367827] [drm] Radeon Display Connectors
[   11.367832] [drm] Connector 0:
[   11.367835] [drm]   VGA
[   11.367839] [drm]   DDC: 0x68 0x68 0x68 0x68 0x68 0x68 0x68 0x68
[   11.367841] [drm]   Encoders:
[   11.367844] [drm]     CRT1: INTERNAL_DAC2
[   11.367846] [drm] Connector 1:
[   11.367849] [drm]   S-video
[   11.367851] [drm]   Encoders:
[   11.367853] [drm]     TV1: INTERNAL_DAC2
[   11.437507] [drm] Radeon display connector VGA-1: Found valid EDID
[   11.501957] [drm] fb mappable at 0xD8040000
[   11.501963] [drm] vram apper at 0xD8000000
[   11.501965] [drm] size 3145728
[   11.501968] [drm] fb depth is 24
[   11.501971] [drm]    pitch is 4096
[   11.502265] fbcon: radeondrmfb (fb0) is primary device
[   11.503482] fb0: radeondrmfb frame buffer device
[   11.503485] drm: registered panic notifier
[   11.503501] [drm] Initialized radeon 2.10.0 20080528 for 0000:01:05.0 on minor 0
root@dale:~#


So if anybody sees somthing that I can change or do to fix this then your help is aprpeciated.

---

### Post by ventrical on 2011-09-10
ON a whim I decided to use the code:

sudo apt-get install fglrx

and -  BOOM .. UNITY desktop!!!!!

:)

---

### Post by ventrical on 2011-09-12
BOOM! On another whim I aquired a Nvidia Gforce512 and , voila' 3D .. and the driver jockey worked excellent. Not sure why it didn't work for ATI. More 'ancient' bugs I'm sure . :)

---

### Post by effenberg0x0 on 2011-09-12
Which is why I always bought NVidia cards for Linux. I don't have anything against ATI nor I believe its of any use to engage in those stupid flame wars about "the best VGA card" etc... But I think it is unquestionably easier to set up NVidia cards in Linux achieving a very decent performance with almost no tweaking...

Regards,
Effenberg

---

### Post by ventrical on 2011-09-12
Absolutely! It's not that bad of an investment but I still like making graphics cards do what others say they can't do ! :)

---

