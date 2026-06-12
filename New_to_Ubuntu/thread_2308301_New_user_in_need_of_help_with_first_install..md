---
title: "New user in need of help with first install."
date: 2016-01-01
forum: New to Ubuntu
---

### Post by Stand_Woodall on 2016-01-01
Okay, I am new to this forum and to ubuntu as a whole. This is my first post and I am in need of a bit of help. Sorry if this topic is similar to another, I have looked through other posts and at various blogs and wikis but none of the answers have quite satisfied so I am hoping this post will do the trick.

My situation:
I have recently purchased a chromebook, it will be arriving soon in the mail. The chromebook is for school but I heard you can put linux on a chromebook system using the dual boot features it has in order to give yourself a bit more variety. I bought an external usb drive for this purpose. I want to install ubuntu on the drive so when I boot I can do it from the usb and not use up the memory on the chromebook (it only has 32 gigs or so). I have the drive, but not the chromebook yet, I want to set up the drive on my desktop so it is ready to just plug and use when I get the laptop. All the guides I have read say I need a usb installer or a cd, I don't have either of these and I don't think I have the resources to make them either.

Questions: Do I need to format the external drive into fat32 or ext4 before installing ubuntu on it?
If I do need to reformat, can/should I reformat a small portion for the OS and a larger portion for files? (I plan on using the external solely for ubuntu purposes).
Can I make do without having a usb installer or a cd to install from? (All I have is the iso currently).
If what I am trying to do is possible, would somebody be nice enough to give me a list of steps to follow, as I feel completely out of my depth when I read the online guides I have come across?

If you need any more information to help me I'd be happy to provide it, I am currently just kind of lost on what to do.
Thank you for taking your time and reading this.

---

### Post by Frogs Hair on 2016-01-01
Hello and Welcome

The operating system on a Chrome Book is Ubuntu based which is Linux. The method for installing Ubuntu is very different than multi booting a Windows based pc and methods may vary depending on what other Linux operating systems you intend to use.


[https://www.linux.com/learn/tutorials/795730-how-to-easily-install-ubuntu-on-chromebook-with-crouton](https://www.linux.com/learn/tutorials/795730-how-to-easily-install-ubuntu-on-chromebook-with-crouton)

---

### Post by Stand_Woodall on 2016-01-01
Okay, this guide is helpful, but it leaves me with a few more questions, if you don't mind answering them.

The guide says the ubuntu version I will be isntalling is either unity, kde, or xfce. Do you recommend one over another for somebody completely new to linux systems? Or should I just pick whichever looks best for me?
Also will I be able to use my external drive to save my steam directory and other large files being used by the added ubuntu system? I intend for it to help overcome some of the memory limitations that come with a chromebook.

---

### Post by Frogs Hair on 2016-01-01
KDE and XFCE are preferences of the writer of the tutorial and you can also install the default Ubuntu desktop depending on the hardware your chrome book has. Unity uses more resources. Of the two, mentioned in the text I prefer XFCE. Search for other tutorials also.

---

### Post by Stand_Woodall on 2016-01-01
Okay, thank you. Oh, about my external, do you know if I should reformat it before using it with the chromebook?

---

### Post by Frogs Hair on 2016-01-01
> **Stand_Woodall said:**
> Okay, thank you. Oh, about my external, do you know if I should reformat it before using it with the chromebook?  I can't help with that , but others will see your thread and answer if they can. :)

---

### Post by Stand_Woodall on 2016-01-01
Okay, thank you so much for your help!

---

### Post by Geoffrey_Arndt on 2016-01-01
Linux OS including any of the "Buntus" require a Linux filesystem for install.  FAT32 is OK for sharing files/data, but is not suitable for a Linux install.    You could partition the external drive (one partition for data - NTFS, another for Linux OS on ext4).

Note you may need to replace the default BIOS of the Chromebook with something like "SeaBIOS" to allow for dual-boot, external usb install.

As a side note, you'll see that Google really didn't design the Chromebook for anything but ChromeOS . . . . so, no way around the various hacks to install via Crouton or similar "work around".    My preferred way to run ChromeOS (if I have to) . . . is by running Chromium or Chrome Browsers on a standard, pre-installed Linux laptop . . . . [http://linuxpreloaded.com/](http://linuxpreloaded.com/)

---

### Post by Stand_Woodall on 2016-01-01
So, if I understand you right Geoffrey, you are saying Chromebooks are not meant to use anything but  ChromeOS, (which is fine by me fyi), but that you recommend forgoing the chromebook altogether for a linux preloaded?

I want a chromebook for it's chromeOS functions, I also want to be able to boot the machine from my external as well, with a linux system installed on there. Are you saying this is not possible? I am confused by your reply.

---

### Post by Geoffrey_Arndt on 2016-01-01
Yes, you can do at least 3 different types of "multiple OS" configurations on Chromebooks, but I've only read several articles over the last couple of years about that.   There are many "caveats" . . . things to consider in planning that.   And it takes considerable planning from what I read.  For example, you would want to select a Chromebook that has the most Linux friendly CPU such as Intel Celeron versus others that some such as Samsung use.

Most folks that I know in the tech world actually "replace" Chrome OS with Linux versus doing a dual-boot or dual-OS because they're not impressed by the default ChromeOS . . it's actually quite limited compared to Ubuntu (or any full OS).

Most (if not all) software programs/services in ChromeOS are already available in Chrome or Chromium (the browsers) . . . and running those in a System 76 laptop with Ubuntu provides the best of both worlds.    One main reason ChromeOS is so popular in schools is the simplicity of setup, maintenance, security, etc.   That is indeed far easier using Chromebooks than a school using Edubuntu IF they don't have at least a couple of admins that understand and can support Linux.   The other reason is the cost is far less to purchase the Chromebooks, and I suspect there are special deals for educational institutions.   

So, I'm just saying for personal reasons, I like the opposite scenario you're going to do - - have Linux as the main host OS, and run an Chromebook like OS using extensions in Chrome Browser.    Hope that's clearer.    

BTW, using Linux is certainly more costly at first, but I think you get a bigger bang for the buck over time . . . . and still have your privacy and freedom.

---

### Post by Stand_Woodall on 2016-01-01
Okay, so now I think I get it. You are saying to use the crouton, or some other similar process to replace my chromeOS with a linux OS, and then as far as my external is concerned that is simply where I would save things instead of on the 32 gb I have of space?
Also, what do you mean by more costly, with what I have what else might I need to buy?

---

### Post by Geoffrey_Arndt on 2016-01-02
OK, let's see . . . . easiest question first, so,

>  re Cost.    Chromebooks can be purchased for a range of $179.00 to $499.00 (larger ssd, screens, ram, etc.).   Linux laptops from the OEM link I already provided range from about $499.00 and upwards of $2500.00 (not including high end gaming systems.    So, the initial cost of a full pre-installed Linux OS can be considerably more than a standard Chromebook.

>   Crouton is not the method used to "replace" the default Chromebook "ChromeOS" with Linux.   Crouton and Chrubuntu are two methods that allow for several linux distros (typically Xubuntu) to be installed on a Chromebook.   You would then switch back and forth between Xubuntu and ChromeOS via key combos (not actually rebooting or restarting like in a traditional dual-boot OS.   To replace the ChromeOS is another technique (sorta like jailbreaking a locked-phone).

>   Data can be saved to both the internal SSD of the Chromebook OR an external device (flash-stick or hard drive or SD card) . . . .  HOWEVER, typically, a Chromebook is set up by default to save data to the Google Cloud (internet server database).   That's one major difference between it and a standard Linux or Windows or Mac laptop, where the default is to save it to the internal hdd or ssd.

Now, what does your school or school admins/teachers require?   If they require a standard Chromebook (are they supplying it?), then you just need to follow their policies.

---

### Post by Stand_Woodall on 2016-01-02
Nothing is required by my school. I bought a chromebook because at a base level, all I need is something to take notes on in class, and something portable in the times between being in my room with my desktop. I bought a chomebook because it satisfies these requirements. Linux is an afterthought, it is not the main attraction, nor am I looking for something better, I am just trying to make the best out of what I have already.

---

### Post by Geoffrey_Arndt on 2016-01-02
Sounds like a basic Chromebook is perfect for you, without modifications.   

Or even just a good divided college notebook, as I used to be very good and fast making  mindmap's of the prof's lectures . . . nothing more creative and complete than that.

---

### Post by Stand_Woodall on 2016-01-02
You're missing the point... I know I -can- use a basic chromebook and be fine, but that leaves me without Steam while I'm away from my house, which is the whole reason I am here in the first place. I want the linux install because it allows me an extra luxury outside of my necessities. I really don't need to do anything fancy, I was just wondering if it were possible to put linux on my portable drive and boot from it, but I've gotten no answer to that question directly, and instead have been getting alternatives and solutions to problems I didn't think I had.
Are you telling me it's not possible to do what I want with the portable drive, or that I don't need it, because those are different things, and both lead to very different courses of action.

---

### Post by Geoffrey_Arndt on 2016-01-02
OK, so here's what you wrote:

"[COLOR=#0000ff]all I need is something to take notes on in class, and something  portable in the times between being in my room with my desktop. I bought  a chomebook because it satisfies these requirements. Linux is an  afterthought[/COLOR] . . "

Yes, it is possible to install Linux to an external usb hard drive connected to a Chromebook.   But what are the specs (& make/model) of the Chromebook so you can confirm IF Steam will run on a Chromebook - - _as they don't exactly have high-end gpu's_.   Most Chromebooks only come with 2 GiB of ram, . . . I assume the one you're getting has more?   And that you have the Intel x386 architecture?  

The key to the install will be to replace the BIOS of ChromeOS which is designed to run a stable Chromebook, including recovery.

I do have a Chromebook (Acer v710) but haven't done what you're trying to do . . as mine is a 1st gen. Chromebook that doesn't allow for the newer methods to install Linux (other than Crouton/Chrubuntu which is not worth it to me). 

[COLOR=#ff0000]EDIT:   but, for what you describe you want to do, I think Crouton is the easiest option for you.   And the external drive is not needed at all unless it's need just to save more data (but a flash-stick, nano size would be more portable).

[/COLOR]
h[URL="http://www.pcworld.com/article/2691209/5-powerful-things-you-didnt-know-chromebooks-could-do.html"]ttp://www.pcadvisor.co.uk/how-to/laptop/bring-steam-gaming-your-chromebook-3591011/

[/URL][URL="http://www.pcworld.com/article/2691209/5-powerful-things-you-didnt-know-chromebooks-could-do.html"]http://www.pcworld.com/article/2691209/5-powerful-things-you-didnt-know-chromebooks-could-do.html

https://www.youtube.com/watch?v=7KGcd9sSQok[/URL]

---

### Post by Stand_Woodall on 2016-01-02
It's an acer chromebook 15, I checked the specs on my game, it's incredibly simple, needs Win2000, the games I am planning on are very low end. The main game I want is Tales of Maj'Eyal, and secondarily Wazhack and Talisman:digital edition. Just things to pass time, I don't plan on running fallout 4 or anything while I'm away from home.

[http://us.acer.com/ac/en/US/content/model/NX.MUNAA.002](http://us.acer.com/ac/en/US/content/model/NX.MUNAA.002)

---

### Post by Geoffrey_Arndt on 2016-01-02
OK Stan, see my edited reply above . . . Crouton is not hard to do, I've seen done at my local LUG (Linux Users Group) . . . and there are several well done youtube demos on that.   It might be worth trying that first, and only if it's not what you're looking for, then try the external hdd install - - which requires more work/hacking to do.   Dave Bennett on youtube does a pretty good job of demo'ing . . . give it a shot.

---

### Post by Stand_Woodall on 2016-01-02
Alright, I'll check out the crouton method before anything else

---

### Post by Javelin Dan on 2016-01-02
Here is an easy to follow tutorial dating back to Ubuntu 9.10. using an internet based installer software called “Universal USB Installer” from Pen Drive Linux. Here's the link to the tutorial: [http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive](http://www.howtogeek.com/howto/14912/create-a-persistent-bootable-ubuntu-usb-flash-drive)/. Here's a link to the Pen Drive Linux to acquire the software: [http://www.pendrivelinux.com/](http://www.pendrivelinux.com/).
 

 Just realize that the tutorial was written a number of years ago and size requirements have changed. If I were going to run a persistent Ubuntu OS from a flashdrive, I would use at least a 16 GB drive, and strongly consider a 32 GB drive. Good luck.

---

### Post by Geoffrey_Arndt on 2016-01-02
Dan, 

The OP is using a Chromebook . . . . it uses "Verified Boot" . . . Googles own version of Secure Boot.   So, this is not the way to go as the system is locked from usb boot of non-Chrome signed OS.

The Crouton install method bypasses the need for a USB Thumbdrive installer anyway (the installer is Terminal based - similar to apt-get.)

---

### Post by Knightwise on 2016-01-04
The best way to format your drive so you can use it with your chromebook both in ChromeOS and in Linux. Alternatively  if you plug it into a mac or a windows machine you will be able to read and write to the external drive.

---

### Post by Stand_Woodall on 2016-01-04
What is the best way? You didn't seem to mention it specifically in your post.

---

### Post by Stand_Woodall on 2016-01-04
Okay, so I got the chromebook, I have crouton xfce fully installed, and I put steam on it, but now I'm running into the problem of not being able to save the games to my external hard drive.
It seems like the /media/removable/(my external) isn't able to be found by steam. Any ideas?

---

### Post by Geoffrey_Arndt on 2016-01-04
Ok, congrats on getting crouton w/xfce setup.    

Regarding saving games, I'm not really familiar with Steam, it's file formats or data processes.   

But, let me ask, what filesystem does the hdd have now?  Can you save a regular file (like a downloaded txt or jpg file) using the chromebooks file manager?  Does the drive show up in the file manager (does it mount on hot plug . . . does it mount if connected prior to turning on the Chromebook?

While you're running XFCE, is the drive found in the Thunar File Manager and can you access it, write to it, etc.?

Unless there's a Chromebook guru at these boards, perhaps the CHromebook official forums (or even the Valve/Steam forums) would be next best place to check into.

---

### Post by Stand_Woodall on 2016-01-11
Okay so I went to access my linux installation from the chromebook today and it does not seem to be cooperating. I am getting a fatal server error: no screens found. I am not sure in any sense what has gone wrong here and do not know how to fix it either, can somebody here help me with this issue. I'll c/p the full message I get when I attempt to sudo startxfce4

chronos@localhost / $ sudo startxfce4
Entering /mnt/stateful_partition/crouton/chroots/precise...
/usr/bin/startxfce4: Starting X server

_XSERVTransmkdir: ERROR: euid != 0,directory /tmp/.X11-unix will not be created.

X.Org X Server 1.11.3
Release Date: 2011-12-16
X Protocol Version 11, Revision 0
Build Operating System: Linux 2.6.42-61-generic x86_64 Ubuntu
Current Operating System: Linux localhost 3.14.0 #1 SMP Fri Dec 11 19:22:03 PST 2015 x86_64
Kernel command line: cros_secure console= loglevel=7 init=/sbin/init cros_secure oops=panic panic=-1 root=/dev/dm-0 rootwait ro dm_verity.error_behavior=3 dm_verity.max_bios=-1 dm_verity.dev_wait=1 dm="1 vroot none ro 1,0 2506752 verity payload=PARTUUID=904bb064-68e7-f543-95c8-b8bafd9d8929/PARTNROFF=1 hashtree=PARTUUID=904bb064-68e7-f543-95c8-b8bafd9d8929/PARTNROFF=1 hashstart=2506752 alg=sha1 root_hexdigest=a99a7e22c8228fbfb954df719406e10a5dafe1d3 salt=32744491f9d3c04f950b392d467e87fa21fadaec93574ec1293213e6e079a458" noinitrd vt.global_cursor_default=0 kern_guid=904bb064-68e7-f543-95c8-b8bafd9d8929 add_efi_memmap boot=local noresume noswap i915.modeset=1 tpm_tis.force=1 tpm_tis.interrupts=0 nmi_watchdog=panic,lapic 
Build Date: 12 February 2015 02:49:01PM
xorg-server 2:1.11.4-0ubuntu10.17 (For technical support please see [http://www.ubuntu.com/support](http://www.ubuntu.com/support)) 
Current version of pixman: 0.30.2
Before reporting problems, check [http://wiki.x.org](http://wiki.x.org)
to make sure that you have the latest version.
Markers: (--) probed, (**) from config file, (==) default setting,
(++) from command line, (!!) notice, (II) informational,
(WW) warning, (EE) error, (NI) not implemented, (??) unknown.
(++) Log file: "/tmp/Xorg.crouton.1.log", Time: Mon Jan 11 10:34:22 2016
(==) Using system config directory "/usr/share/X11/xorg.conf.d"

Fatal server error:
no screens found

Please consult the The X.Org Foundation support 
at [http://wiki.x.org](http://wiki.x.org)
for help. 
Please also check the log file at "/tmp/Xorg.crouton.1.log" for additional information.

ddxSigGiveUp: Closing log
Server terminated with error (1). Closing log file.
/usr/bin/xinit: giving up
/usr/bin/xinit: unable to connect to X server: No such file or directory
/usr/bin/xinit: server error
Unmounting /mnt/stateful_partition/crouton/chroots/precise...

---

