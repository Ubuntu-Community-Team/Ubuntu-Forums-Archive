---
title: "-ANY- LInux distro where DRX3 works, *please*"
date: 2007-09-22
forum: Other OS Talk
---

### Post by altariel on 2007-09-22
Having spent the better part of the last few** days** in -trying- to get that STUPID*** RealMagic Hollywood Plus MPEG decoder card ***working under 
-[COLOR="DarkSlateBlue"] Mandriva 2007[/COLOR] (system wouldn't even recognize it, not even after trying to install the packages for it!)
-[COLOR="Navy"] PCLinuxOS 2007[/COLOR] (the only thing happening when trying to load the em8300  driver (after hours of playing around with the options!)  is that the whole fricking screen goes flickering green and DIES so that the only way to see anything on the screen again is a Ctlr-Alt-Del reboot!)
- [COLOR="Navy"]Ubuntu 7.04[/COLOR] (complains about 
FATAL: Module adv717x not found.
FATAL: Error running install command for em8300
(and checking there is no adv717x kernel module so the message is understandable ???) 


I am sick to death right now about the whole issue ... 

What use are packages in a distribution if the packages simply DON*T WORK after installation? Silently failing without any output -or clues to why- except if you force them to? 

I knew pretty well WHY I all these years kept the old  [COLOR="Red"]WinXP[/COLOR] on this old computer ... 

but I was SO disgusted at some of the Microsoft ideas lately that I thought I would finally replace it ... add to that that I couldn't move the windows install to a bigger harddrive without Windows refusing to boot any more :( all the times I tried -that- solution ... (I virtualilzed it but of course the virtual machine players  don't give the option to use the card in the virtual machine)  

But yes, I -did- dread the issue, have never gotten the impression that all of the features of the card would work with the dxr3 project  ... but had NO IDEA of the hassle to even get SOMETHING working ... 

I mean, the card is OLD and has been around -for ages- why should it be THIS hard to get it working???? 

[B]
[COLOR="Purple"]Please, give me the name of  [COLOR="SeaGreen"]ONE WORKING LINUX distribution[/COLOR] where this particular card WORKS - preferably "out of the box" (that is, maybe after installing the right packages, but NO MORE DAYS fiddling around with trying to patch together information about obscure error messages (or even HOW to get any error messages at all out of it!) and such, please ... 
[/COLOR]
[/B]

I'm no stranger to "fiddling around", having used FreeBSD and Linux for YEARS, but THIS begins to feel unmanageable :( ... 

As for the** rest of the hardware**? 

Well, it is a very old computer after all :-/ ... 

(and please, don't reply with "buy a new computer" - as long as I am unemployed once again *sigh* there is no other option if I want to keep the possibilty to watch my legally bought DVDs here in the living room than to try to get the stuff working) 


* Abit BX6 rev 2.0 motherboard (BIOS updated to latest 2000 version)
* 450 Mhz CPU (which is why I need that **** card) 
* 384 MB RAM (and that is maximum since one of the RAM banks is broken) 
* nVidia RIVA TNT2 Model 64/Model 64 Pro]
* the "new" 40 GB  WDC WD400BB-32AUA1 Western Digital harddrive 
* _NEC DVD_RW ND-1300A DVD burner 
* Pioneer DVD-ROM ATAPIModel DVD-106S 012 DVD-ROM 
*  CM8738   vendor: C-Media Electronics Inc soundcard (bought is as a Zoltrix) 
* AHA-2940U2/U2W SCSI controller card
* Microtek Scanmaker X6EL SCSI scanner

edit: 
This computer is MAINLY kept for just one purpose - 
[COLOR="DarkOrchid"]**watching DVDs**[/COLOR] ... 
and *occasionally* used by visitors since I don't let other non-trusted folks use my main computer (running FreeBSD 6.2 and Kubuntu 6.10, will probably update the Kubuntu some time soon) 


so I really need a distro where getting DVD watching/dumping/burning is NOT a great obstacle in itself! 
no, I won't install Automatix either, have read too much rather scary stuff about that package ... 
another edit: yes, I -did- get basic DVD playable by installing the appropriate codecs and lib-for-wathing-dvds ;) - but as long as I can't send the data trough the MPEG-decodercard the system is pretty much UNUSABLE due to the heavy heavy CPU/swap-usage :( 


so
- watching DVDs
- making backup-copies of DVDs
- and occasional OpenOffice-editing, web-browsing, im-chatting, music listening, simple audio and graphics editing  
should all be possible in that linux distribution! 


I perhaps should add that I otherwise was rather impressed by Ubuntu 7.04 so it really is a pity I can't seem to get the card working here :(
But playing around with the Ubuntu 7.04 even on this OLD computer impressed me so much that I really MUST upgrade the Kubuntu 6.10 :)

---

### Post by boneface on 2007-12-02
Hello there

I've been struggling to get my  dxr3 working in any linux too..
I have the 4 em8300 packages installed from synapic aswell as em8300-0.16.2 from sourceforge.
Just now i have got it to work by changing some code in the file 

em8300-0.16.2/modules/em8300_main.c

line 803

replace "pci_module_init" to pci_register_driver

then run
make
make install 
./ldm
em8300setup

also the gui for mplayer does not seem to work for me, instead the cli does:
mplayer -vo dxr3 /moviefile

i think it could be the lack of permissions ubuntu has stopping me from using the gui version
as i must use "sudo su" to compile the modules and load them.etc (just a guess)

Hope that can be of some help.

Boneface

editL my ubuntu version is 7.10

---

### Post by boneface on 2007-12-02
update:
chmod 7777 /dev/em8300* makes mplayer now work just fine.

---

### Post by kwisher on 2008-03-22
altariel,

I have the same scanner as you and i cannot seem to get it working with Mint/Daryna. Can you provide any help?

TIA

---

### Post by altariel on 2008-04-14
> **kwisher said:**
> altariel,

I have the same scanner as you and i cannot seem to get it working with Mint/Daryna. Can you provide any help?

TIA

Sorry for not having found the question till now ... 
Am right now not at home so that I could check the scanner in question (and have since then upgraded the computer somewhat) but I *think*  I did not have too much trouble to get it up and running with kooka in Kubuntu ...

One thing to watch out for, in particular with SLOW computers though, is that the BIOS needs to find the scanner for the Linux to find the scanner ... one way to achieve this is to start the computer, let it run for some time and then do a warm reboot ... at least that's the solution I found and which I use most ... 
or, in my case possible at least, start the computer and interrupt the starting process when the message is on the screen to type Ctrl-A to fix SCSI-related stuff and -there- go through the process several times of probing all SCSI-devices till the BIOS/SCSI-system finally finds the scanner (which usually takes several minutes -up  to a quarter of an hour on my slow system at least) ..

Edit: 
[http://linux.about.com/library/cmd/blcmdl5_sane-microtek2.htm](http://linux.about.com/library/cmd/blcmdl5_sane-microtek2.htm)
might be of interest? 
[http://forums.suselinuxsupport.de/index.php?showtopic=50449](http://forums.suselinuxsupport.de/index.php?showtopic=50449)

---

