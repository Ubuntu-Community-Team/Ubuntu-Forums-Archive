---
title: "too many bugs in Lubuntu, get another distro?"
date: 2012-07-05
forum: New to Ubuntu
---

### Post by SonnyE on 2012-07-05
(Update 2: I'm adding a post to this thread on July 11 to say how I've worked around some problems in Lubuntu 12.04. Lubuntu runs with low RAM and processor usage, so it's all right for some purposes.)

I am new to Linux. This is the first time I've installed any Linux. I've almost given up on it because of the bugginess, but I'm still trying so some help would be appreciated.

(Skip to near the end if you just want to tell me what else to use instead of fixing problems in Lubuntu.)

I don't know how to file an official bug report yet, and there are so many I don't know if it would be worthwhile to file them separately, when there might be a simpler solution to most of them all at once, such as using a different distro or OS (Windows XP works fine) or buying a new computer. I'm planning to buy a new desktop computer anyway. The reason I wanted to try Linux was to test whether Rosegarden 12.04 works well enough to be worth setting up a Linux-based desktop system just to run it. The Windows port of Rosegarden was all bugs and crashes but it's not supported by the Rosegarden project, so I don't want to judge Rosegarden by it. I'm not comfortable with the Linux set up I'm using right now and wouldn't judge Rosegarden if it didn't run in it either.

downloaded Lubuntu 12.04 desktop i386 on 2012-06-22, began installation 2012-06-29

system info: HP Pavilion ze4800, ~512 MB RAM, 2.12 GHz AMD processor with 530 MHz power saving mode, 80 GB hard drive, dual boot install from Live CD of Lubuntu 12.04 desktop i386, with Windows XP Home Edition Service Pack 3 on the other partition.

- [update: solved, it did install a mixer, I just didn't know how to start it: alsamixer] (a crucial problem, considering my purpose for using Linux) The start up fails at creating a mixer. There's only a single volume control, without a balance control. (Windows XP creates a mixer for sound to the speakers: CD, wave synth, midi synth, microphone, pc speaker, etc., and a separate mixer for recording, with balance controls and mutes for each source.)

/var/log$ grep "mixer" syslog.1

Jul  4 17:14:24 s-ze4800 kernel: [   22.748038] AC'97 1 access is not valid [0xffffffff], removing mixer.
Jul  4 17:14:24 s-ze4800 kernel: [   22.748049] ali mixer 1 creating error.

- (major problem) Gnome-mplayer included doesn't play ordinary mp3 or FLAC audio files, doesn't give any sign that it doesn't or couldn't play the particular files, letting them seem empty (0:00) and Gnome-mplayer is set as the default mp3 and FLAC player, although Audacious included does play those mp3 and FLAC files. (update: I set Audacious as the default player for mp3 and FLAC)

- (suggestive of a major problem) There are no desktop event sounds, even though the checkboxes for those were checked by default in Customize Look and Feel, under the tab Other, and sound is on as proved by Audacious playing a FLAC file.

- Brightness buttons are significantly delayed in effect compared with their speed in Windows XP. (a minor problem, or major considering I want low latency for playing a software synth through the computer keyboard?)

- On the desktop, windows leave trails on windows below them for several times as long as Windows XP, despite the FOSS graphics driver it installs being compatible with 3-d on my old graphics (the "radeon" driver for Radeon IGP 320M.) I still don't know how to check whether it's using graphic acceleration at all. That's something normal desktops have a GUI interface that at least tells the user.

[update: no problem, it didn't delete the files, it just put them in a new folder called .Trash-1000 on my Windows partition] When the desktop file manager included, pcmanfm, is used to manipulate files on the Windows side of the partition, delete ("are you sure you want to send this file to the trash?") sends the file to the trash on the Linux side, from which it cannot be restored or deleted ("error: the file does not exist") until it vanishes after reboot. It's a bug to allow deleting files to the trash when restore is actually broken for those files, instead of warning they'll be deleted permanently.

- Setting a compose key (aka Multi_key in xmodmap) requires using the command line and doesn't cause a compose key to be available for input. (Although the key chosen shows up as changed to Multi_key in xev, it becomes a useless key.) The GUI interfaces included have no options for even something as simple and standard to Linux as setting a compose key. Starting from English US the GUI interface doesn't have a way to add languages or input methods, just greyed out buttons for that. (Currently I can use a compose key only in UXTerm or XTerm, but not in desktop applications or LXTerminal, and not in tty unless I set that manually using a complicated command. Trying right now various advice about how to enter characters by Unicode number, and even that fails to produce any results. !falta! Stoerung! un echec)

- Advice about how to do particular things in Linux is generally not applicable within Lubuntu, since programs available and directories used for settings have been changed significantly from what was common a few years ago. Yet there isn't a new standard guide or plan that the ordinary user is directed to study.

- Some other programs included crashed occasionally and automatic bug reports were sent. I didn't have time to write down what they all were.

- I also just now received the message "sorry, Ubuntu 12.04 has experienced an internal error." (update: This happens when starting Gnome-mplayer.)

- Some links to programs in the menu do nothing, such as Input Method Switcher.

- The battery utility in the sys tray says "Adaptor is online  Your battery is charging (0%)" when actually my battery is fully charged, and I just hope it's not overcharging it.

- [solved, work around by editing] The Spreadsheet Gnumeric included can more or less handle an ods file from LibreOffice (which I made for planning my next computer purchase) that contained ordinary numbers and totals of cell ranges, but it required editing of a format mistranslation: drop down menus within cells that showed up unexpectedly and were in the way of reading the numbers.

- [solved, work around] In the dual boot installer, the partition size slider does not indicate which OS gets which amount of the hard drive. (I found a thread on this forum that answered that, though the posters didn't seem completely sure, and added my own result as an answer. Right side = Lubuntu.)

- [solved, work around] It didn't complete the installation, stuck in Live CD mode. (I found via Google that the Ubiquity slideshow for Lubuntu that was supposed to be displayed during installation had to be removed manually to make the installer finish running on some systems.)

- [solved, turned off feature] Suspend and hibernate malfunction. On my laptop the screen turns off, power use and fan speed go up, and there's no way out except manual power down and boot from scratch. Xfce power manager, included, does allow turning suspend and hibernate off, but not directly: In places there's only a choice between suspend and hibernate for what the computer will do when it "sleeps." So I chose to have it never "sleep."

Since I started this thread, I've resolved or worked around the following problems:

- [solved, get used to it, it's for online security] The user doesn't get root and isn't allowed to set a short password for sudo, even if it's the user's own computer used alone at home.

- [solved, uninstalled] The Penguin games included have animation that looks glitchy and unreliable. For example, cards in spider jumping or flashing invisible as they move, which looks several times less solid than Windows XP, and pegs in mastermind leaving permanent trails on part of the background.

- [solved, ignore, the developers are already aware it's a problem] Some buttons do nothing, such as Help in Xfce power manager. (Others have reported this as a bug.)

New bugs that came up after I started this thread:

- Synaptic package manager failed on updating new packages. I selected 6 to update, and something seems to want gtk to be installed, and I don't know if it is, so none of them got installed.

tldr:

I'm not skilled enough at Linux yet to install Arch or a plain Debian, so I want something that has a desktop with more complete and functioning settings than this install of Lubuntu, and is audio capable.

What other distro or other fix does anyone suggest? (update: planning to try Rosegarden in Lubuntu first)

---

### Post by kalkems on 2012-07-05
Hi!
Have you tried Ubuntustudio?  This distro is created with musicand graphics in mind.  I've installed Ubuntustudio a few times at work and our music students use it and some find it works well.

---

### Post by SonnyE on 2012-07-05
No, as I said this is my first time. I wanted Ubuntu Studio first but it comes on a DVD, which I can't burn. Also, for some reason I thought Lubuntu would be easier to start as a first taste of Linux.

Is there a way to run Ubuntu Studio's installer directly from the hard drive instead of from a DVD?

---

### Post by sudodus on 2012-07-05
> **SonnyE said:**
> No, as I said this is my first time. I wanted Ubuntu Studio first but it comes on a DVD, which I can't burn. Also, for some reason I thought Lubuntu would be easier to start as a first taste of Linux.

Is there a way to run Ubuntu Studio's installer directly from the hard drive instead of from a DVD?

I think you must boot the installer from another drive, not the one where you want to install the system. But the easiest way is to ***make a USB boot drive either a flash drive (pendrive) or an external hard disk drive***.

Format it to the FAT32 file system, add the boot and lba flags and use ***Unetbootin*** to make it bootable from the downloaded iso file. This should work with both CD or DVD size iso file as long as the USB drive is big enough. 4 GB would be enough for most DVD iso files (because they are usually not maxed to fill a DVD disk).

---

### Post by Elfy on 2012-07-05
> **SonnyE said:**
> No, as I said this is my first time. I wanted Ubuntu Studio first but it comes on a DVD, which I can't burn. Also, for some reason I thought Lubuntu would be easier to start as a first taste of Linux.

Is there a way to run Ubuntu Studio's installer directly from the hard drive instead of from a DVD?

You can install Ubuntu studio from within lubuntu.

There are a few available packages to choose from.

ubuntustudio-audio 
ubuntustudio-desktop
ubuntustudio-video

Have a look in the software centre

You can also add an iso to grub and boot with that


[https://help.ubuntu.com/community/Grub2/ISOBoot](https://help.ubuntu.com/community/Grub2/ISOBoot)

To be honest it is likely that you'll be better of trying to deal with the issues though - start threads for each issue - putting them in a long list is not the best way to proceed.

It will get very long and very confusing as to which bit is for what fast.

---

### Post by mastablasta on 2012-07-05
ok first off... most of your issues seem hardware related that would not be there with linux compatible hardware. secondly, if you check the versions of crucial programmes in Lubuntu you will see that plenty do not have a 1.x verison but rather 0.x. That should give you a hint. what i am saying is that it could be working perfectly or it could just as easilly annoy you to hell.
 
> **SonnyE said:**
>  
- On the desktop, windows leave trails on windows below them for several times as long as Windows XP, despite the FOSS graphics driver it installs being compatible with 3-d on my old graphics (the "radeon" driver for Radeon IGP 320M.) I still don't know how to check whether it's using graphic acceleration at all. That's something normal desktops have a GUI interface that at least tells the user. 
Opensource drivers do not have a GUI interface. if you could use porprietary drivers it would be there. there is a command you can run to check 3D acceleration. i forgot it, so someone esle will give it to you, but you can test it by running glxgears.
>  
- When the desktop file manager included, pcmanfm, is used to manipulate files on the Windows side of the partition, delete ("are you sure you want to send this file to the trash?") sends the file to the trash on the Linux side, from which it cannot be restored or deleted ("error: the file does not exist") until it vanishes after reboot. It's a bug to allow deleting files to the trash when restore is actually broken for those files, instead of warning they'll be deleted permanently.

as i said before... pcmanfm version is 0.9.10 which tells you something ;-)
have you tried using thunar?
also even if the file is out of the bin the file is not actually removed from disk. it is still there until you overwrite it. adidtionally wouldnt' you say it's a small miracle that it can read and write to NTFS partition while windows can't read ext partition without plugins. you probably wanted it to move the deleted fiel to windows "recycle bin". i don't think it will happen.
 
> 
- Advice about how to do particular things in Linux is generally not applicable within Lubuntu, since programs available and directories used for settings have been changed significantly from what was common a few years ago. Yet there isn't a new standard guide or plan that the ordinary user is directed to study.

 
Commands given in Ubuntu wiki and for example in Ubuntu manaul (see my signature) and here on forums or some other trusted sites work in all *buntu versions. the difference with Lubuntu and Ubuntu is that Lubuntu uses LXDE desktop while Ubuntu uses Gnome. everything else is more or less the same.
 
> 
- [solved, work around by editing] The Spreadsheet Gnumeric included can more or less handle an ods file from LibreOffice (which I made for planning my next computer purchase) that contained ordinary numbers and totals of cell ranges, but it required editing of a format mistranslation: drop down menus within cells that showed up unexpectedly and were in the way of reading the numbers.

USe what works. Libre office has more features. A Koffice is also being developed. but spreadsheet programme is still a bit buggy i think.
 
 
> 
- [solved, work around] It didn't complete the installation, stuck in Live CD mode. (I found via Google that the Ubiquity slideshow for Lubuntu that was supposed to be displayed during installation had to be removed manually to make the installer finish running on some systems.)

To me it crashed, so yeah... version 0.x :-)
 
> 
- [solved, turned off feature] Suspend and hibernate malfunction. On my laptop the screen turns off, power use and fan speed go up, and there's no way out except manual power down and boot from scratch. Xfce power manager, included, does allow turning suspend and hibernate off, but not directly: In places there's only a choice between suspend and hibernate for what the computer will do when it "sleeps." So I chose to have it never "sleep."

This is kernel issue. plenty of bugs reported and being solved. again on some hardware it works well. i have an old mashicne where is's flawless and a newer one where hibernation only works and evn that one removes the sound setup. go figure...
 
> 
- [solved, get used to it, it's for online security] The user doesn't get root and isn't allowed to set a short password for sudo, even if it's the user's own computer used alone at home.

It's a feature. you are assuming that on a computer connected to the internet no one can connect to your computer and use malware/scripts to take control of it. password is there as a security layer to prevent that malware to run itself. not to annoy the user. removing it and using root all the time... well it's your computer, your data to be stolen, so go ahead...it's how windows98 and below worked and it's how they got hacked. and just in case you thought this can't happen in linux that is not secured - it can. and also it did (check the forums).
 
> 
- [solved, uninstalled] The Penguin games included have animation that looks glitchy and unreliable. For example, cards in spider jumping or flashing invisible as they move, which looks several times less solid than Windows XP, and pegs in mastermind leaving permanent trails on part of the background.

could be a hardware issue with GPU drivers.
 
> 
- Synaptic package manager failed on updating new packages. I selected 6 to update, and something seems to want gtk to be installed, and I don't know if it is, so none of them got installed.

 
GTK are libraries for programmes. you prevented them to install. withouth them programmes won't update, so of course they won't install.
 
Give Xubuntu or other *buntus a try.
Also debian is nice. but for beginners i would suggest a debian based distro. there are plenty of them that are user friendly (Linux Mint, Snowlinux, Chrunchbang...)

---

### Post by SonnyE on 2012-07-05
Thanks for the advice and link about loading Ubuntu versions via the hard drive. I'm considering using UNetbootin for that, so that I won't mess up my Grub with typos.

------------


About the mixer bug:

/var/log$ grep "mixer" syslog.1

Jul  4 17:14:24 s-ze4800 kernel: [   22.748038] AC'97 1 access is not valid [0xffffffff], removing mixer.
Jul  4 17:14:24 s-ze4800 kernel: [   22.748049] ali mixer 1 creating error.

I found a bug report page on that bug:

[https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/439156](https://bugs.launchpad.net/ubuntu/+source/alsa-driver/+bug/439156)

with this advice in the bottom post:

> Matej Kenda (matejken) wrote on 2010-09-15:	 #22
I am using Compaq Evo N1015v on 10.10.

This issue is still happening.

I found this page, where using additional options is advised:

modprobe snd-index8x0 ac97_quirk=1 xbox=1

[http://alsa.opensrc.org/index.php/Intel8x0#Sound_not_working_on_Fujitsu-Siemens_Desktops_with_ICH845](http://alsa.opensrc.org/index.php/Intel8x0#Sound_not_working_on_Fujitsu-Siemens_Desktops_with_ICH845)


(alsa.opensrc.og etc. is a broken link)

the "Multimedia audio controller" recognized by Lubuntu is:

ALi Corporation M5451 PCI AC-Link Controller Audio Device (rev 02)

Here's a video driver page:

[http://support.amd.com/us/gpudownload/windows/previous/10/Pages/radeon_linux.aspx?os=Linux%20x86&rev=10.10](http://support.amd.com/us/gpudownload/windows/previous/10/Pages/radeon_linux.aspx?os=Linux%20x86&rev=10.10)

which was linked by this Ubuntu thread as a solution to the audio issue:

[http://ubuntuforums.org/showthread.php?t=1638055&page=2](http://ubuntuforums.org/showthread.php?t=1638055&page=2)

This page gives up-to-date instructions on driver installation:

[http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers](http://askubuntu.com/questions/124292/what-is-the-correct-way-to-install-ati-catalyst-video-drivers)

which links to this page:

[http://wiki.cchtml.com/index.php/Hardware](http://wiki.cchtml.com/index.php/Hardware)

where it shows that my video card (Radeon IGP 320(M)) is no longer supported by AMD and my only option is to use the open source driver.

I also found links leading to video driver updates as the suggested solution back when I was looking into solving the suspend and hibernate malfunctions.

This all adds up to suggesting there is no way to run Ubuntu of any kind with the audio and video features fully working on this computer. Unless some trick like the one involving "modprobe" works. But I haven't yet found documentation for what options to use on modprobe and where to put that command (in a tty? in a file? what file?)

---

### Post by sudodus on 2012-07-05
> **SonnyE said:**
> Thanks for the advice and link about loading Ubuntu versions via the hard drive. I'm considering using UNetbootin for that, so that I won't mess up my Grub with typos.



Warning: ***Backup*** your internal drive before doing things like that with the hard drive!

---

### Post by TenPlus1 on 2012-07-05
Try using Xubuntu as your first taste of Ubuntu...  Lubuntu is a great Os albeit very light and lacking some of the features of a main desktop like Xubuntu, Ubuntu and Kubuntu has...

---

### Post by SonnyE on 2012-07-05
@mastablasta

I'm sorry, you misunderstood, I didn't do anything to prevent gtk installing and for all I know, I have gtk. It's just that the something run by the Synaptic package manager had a complaint about gtk in the details window.

I just tried it again and the details looked a lot the same, but this time it says it was successful.


> debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
(Reading database ... 125069 files and directories currently installed.)
Preparing to replace libgnutls26 2.12.14-5ubuntu3 (using .../libgnutls26_2.12.14-5ubuntu3.1_i386.deb) ...
Unpacking replacement libgnutls26 ...
Preparing to replace libdbusmenu-glib4 0.6.1-0ubuntu3 (using .../libdbusmenu-glib4_0.6.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement libdbusmenu-glib4 ...
Preparing to replace libdbusmenu-gtk3-4 0.6.1-0ubuntu3 (using .../libdbusmenu-gtk3-4_0.6.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement libdbusmenu-gtk3-4 ...
Preparing to replace libdbusmenu-gtk4 0.6.1-0ubuntu3 (using .../libdbusmenu-gtk4_0.6.2-0ubuntu0.1_i386.deb) ...
Unpacking replacement libdbusmenu-gtk4 ...
Preparing to replace xserver-common 2:1.11.4-0ubuntu10.2 (using .../xserver-common_2%3a1.11.4-0ubuntu10.3_all.deb) ...
Unpacking replacement xserver-common ...
Preparing to replace xserver-xorg-core 2:1.11.4-0ubuntu10.2 (using .../xserver-xorg-core_2%3a1.11.4-0ubuntu10.3_i386.deb) ...
Unpacking replacement xserver-xorg-core ...
Processing triggers for man-db ...
debconf: unable to initialize frontend: Gnome
debconf: (Unable to load Gtk -- is libgtk2-perl installed?)
debconf: falling back to frontend: Dialog
Setting up libgnutls26 (2.12.14-5ubuntu3.1) ...
Setting up libdbusmenu-glib4 (0.6.2-0ubuntu0.1) ...
Setting up libdbusmenu-gtk3-4 (0.6.2-0ubuntu0.1) ...
Setting up libdbusmenu-gtk4 (0.6.2-0ubuntu0.1) ...
Setting up xserver-common (2:1.11.4-0ubuntu10.3) ...
Setting up xserver-xorg-core (2:1.11.4-0ubuntu10.3) ...
Processing triggers for libc-bin ...
ldconfig deferred processing now taking place
W: Waited for dpkg --assert-multi-arch but it wasn't there - dpkgGo (10: No child processes)


So I hope that isn't a problem.

---

### Post by SonnyE on 2012-07-05
@mastablasta

By the way, I also installed and ran glxgears because you said so and it ran at 33 fps with a high of 52 and a low of 7. I think it was supposed to run at 60 because that's my refresh rate.

---

### Post by hakermania on 2012-07-05
I would recommend a new person to Linux to have a taste of Ubuntu, first.

Ubuntu doesn't lack any feature of a stable and nice OS and everyone (even mokeys) can go through the installation process, as it doesn't ask something difficult.
So, (almost) no matter the circumstances, I'd say to try Ubuntu, and, if you find it too heavy for your needs, you can migrate to Lubuntu (which works perfectly fine for me, by the way) or any other distro.

But, I highly recommend, your first taste to be from Ubuntu, so as to be used to the terminal etc, and, when you have to deal with a problem with some other linux distro, to have some skills...

---

### Post by SonnyE on 2012-07-05
Okay, hackermania, I just deleted my stored passwords from Chromium.

---

### Post by MG&amp;TL on 2012-07-05
> **hakermania said:**
> I would recommend a new person to Linux to have a taste of Ubuntu, first.

Ubuntu doesn't lack any feature of a stable and nice OS and everyone (even mokeys) can go through the installation process, as it doesn't ask something difficult.
So, (almost) no matter the circumstances, I'd say to try Ubuntu, and, if you find it too heavy for your needs, you can migrate to Lubuntu (which works perfectly fine for me, by the way) or any other distro.

But, I highly recommend, your first taste to be from Ubuntu, so as to be used to the terminal etc, and, when you have to deal with a problem with some other linux distro, to have some skills...

If he's getting ~30fps from glxgears, I'm thinking that even Unity2D might be a bit of a stretch. My PC only just runs unity2d, and I get ~700FPS.

Just two cents, I'm sure the OP is capable of installing whatever distro they like. :)

---

### Post by SonnyE on 2012-07-05
About glxgears. I discovered that if I keep moving moving my mouse constantly, then I can get 59.9 fps, which is all it's supposed to be able to get because it's sync'ed to the video refresh rate of 60 Hz. So it seems like it's some sort of problem with what's installed rather than my video hardware.

----------

Also, I just tried this series of commands, to try to solve the "ali mixer 1 creating error":

modprobe -r snd-intel8x0
modprobe snd-intel8x0 ac97_quirk=1 xbox=1

Then I rebooted, and there was no change. (There's still no mixer, still the same errors in syslog and Gnome-mplayer still doesn't play, but Audacious does.)

---

### Post by mastablasta on 2012-07-05
try this in terminal:
 
> ```
glxinfo | grep direct
``` 
should get you 
 
direct rendering: Yes

 
you likely don't have it. these older cards are nto well supported by opensource drivers since ATI didn't want to open them. s what they did is reverse engineering. usualyl they work nicely in XP but XP is OS from 2001. if you used a very old Ubuntu you would get porprietary drivers for that chip and they would work better.
 
bottom line - what can you do. nothing much the only and simplest thing i can think of is to use xorg edgers PPA -. the developlemt version of the drivers.

---

### Post by VinDSL on 2012-07-05
> **Elfy said:**
> You can install Ubuntu studio from within lubuntu.
I might add...

You can install LXDE/Openbox from within Ubuntu too, e.g. make your own "Lubuntu".  :)

Lubuntu and Peppermint are nice Ubu-based distros, but if you like LXDE I've found it more rewarding to simply install it on top of Ubuntu, and choose LXDE @ boot.

The "problem" with canned LXDE packages is they try to make them too lightweight.  When you add "bloat" to LXDE, by loading it on top of a standard Ubuntu install, it actually becomes a much more pleasant experience.  ;)

---

### Post by SonnyE on 2012-07-05
@mastablasta

direct rendering: Yes

I knew graphics features are supported by the OSS driver, I just don't know if the Lubuntu desktop is using those features.

---

### Post by VinDSL on 2012-07-05
> **SonnyE said:**
> direct rendering: Yes
Run LXDE/Openbox on top of Ubuntu and you'll have 3D rendering too...  :D


[INDENT][[IMG]http://vindsl.com/images/vindsl-desktop-5-jul-2012-1(650x520).png[/IMG]]("http://vindsl.com/images/vindsl-desktop-5-jul-2012-1.png")[/INDENT]

---

### Post by SonnyE on 2012-07-06
I received a PM in reply to this thread, but the sender has PMs turned off or not allowed, so I'm replying here.

I'm sure I've made more errors than I've noticed or corrected yet. Can you be more specific?

At least I'm still finding it interesting to attempt to get Lubuntu running smoothly and maybe later some other version of Ubuntu.

---------------

Additional steps I've taken to see if the audio mixer will be created:

1. I flashed my BIOS using a program from the manufacturer, HP, because the syslog said some about some CPU ID "This is indicative of a broken BIOS." That didn't make any noticeable difference.

2. I tried other options in /etc/modprobe.d/alsa-base.conf (one at a time then rebooting:)

options snd-intel8x0 ac97_quirk=swap_hp
options snd-intel8x0 ac97_quirk=hp_only
options snd-intel8x0 ac97_quirk=default

I still get, in the syslog:

Jul  5 20:58:39 s-ze4800 kernel: [   22.920038] AC'97 1 does not respond - RESET
Jul  5 20:58:39 s-ze4800 kernel: [   22.936106] AC'97 1 access is not valid [0xffffffff], removing mixer.
s

3. I tried different options edited into grub.conf, such as

GRUB_CMDLINE_LINUX="acpi_osi=\"Linux\""

and uncommented the beep, so I get a beep which shows that my editing went into effect, but there was no improvement.

Right now, GRUB_CMDLINE_LINUX=""

I haven't tried "acpi=off" yet, because people say that's harder to recover from if it goes wrong.

4. I installed the b43legacy driver for the wireless card, in case not having that set up was interfering with the boot sequence setting everything up including the mixer. The wireless card works now, but I don't use it anyway and there was no other improvement.

---

### Post by SonnyE on 2012-07-06
SOLVED main problem:

Just type "alsamixer" in LXTerminal, UXTerm, or XTerm. It opens the mixer.

There wasn't a link to the mixer in the default Lubuntu programs menu or sys tray, and I *assumed* there would be already and that one would appear if I could get the boot to stop logging "AC'97 1 access is not valid [0xffffffff], removing mixer." and "ali mixer 1 creating error."

What's actually going on with those errors might be that since the internal modem uses an AC97 link too, not just the sound chip, those might be errors where PHONEIN and PHONEOUT don't get added as mixer channels. I found those terms in the binary:

/lib/modules/3.2.0-26-generic/kernel/sound/core/oss$ cat snd-mixer-oss.ko

Once I realized that I had a mixer program already in the computer somewhere, I happened to run across a page that used the word alsamixer, and I thought why not try it as a command, and put it into LXTerminal.

The mixer is in ASCII graphics, but it works so far. It took me a few minutes to find out how to adjust the left and right volume separately. (There's a page at Arch Linux that mentions the instructions for that being a bit confusing, [https://bbs.archlinux.org/viewtopic.php?id=137557](https://bbs.archlinux.org/viewtopic.php?id=137557) so I'm not alone in that.)

---

### Post by I2k4 on 2012-07-06
If I read right, you only have 512k RAM?  I would not run anything later than Ubuntu 10.10 /Mint 11 on that.  At the moment, I'm loving Lubuntu 10.10 dual booting W7 on my little Acer netbook, but that said:

- I'm glad I tested Persistent Live USB on more intuitive Ubuntu Desktop before installing Lubuntu.  Lubuntu is very fast and stable but cruder and less newbie friendly than others. 

- The preinstalled software on Lubuntu was not what I wanted to stay with and I spent (wasted) a lot of time removing and replacing preinstalled packages with stuff I wanted - compared with Mint LXDE that has preinstalled just about everything I routinely want and runs nearly as fast as Lubuntu.

I suggest installing several competing versions on _Persistent Live USB and include some of the older and less demanding ones_.  You'll see how different they are from each other, and how much differently they run on your equipment.

---

### Post by SonnyE on 2012-07-06
I have 512 MB of physical RAM, I think, because there are two 256 MB cards and the memory test utility says there are no errors in the RAM, but Lubuntu Task Manager is reporting only 431 MB right now. On the positive side, it reports only 200 MB of that are in use, so I seem to be OK for RAM right now.

If I get Rosegarden running and run low on RAM when I try to use more features of it at the same time, I'll gladly buy the set of RAM cards that would give me 1 GB total, because there would be a purpose to it, having more fun.

I would like to have a distro that has more options for settings and system information in the menus though. My idea of a good OS is one where anything a user wants to do is available both by menu and by command. Lubuntu seems to make things available **either** by menu **or** by command, and a little bit falling through the cracks that isn't available easily either way. Ubuntu with Unity I'm afraid of because from what I've read about it, it seems to have a menu that requires guessing what programs are installed and their names when it doesn't show them. That seems like a really bad design idea and a game I don't want to play, using a special text input box that's for guessing what's not shown in the menu.

So I'm interested in maybe setting up Ubuntu with LXDE, as others suggested to me.

---

### Post by sudodus on 2012-07-06
If you know what you want and how to add it, you can start with the Ubuntu ***mini iso***.

Another alternative is ***Knoppix*** with good hardware detection. After testing live, you can install it to an 'almost debian' system.

---

### Post by MG&amp;TL on 2012-07-07
> **SonnyE said:**
> 

I would like to have a distro that has more options for settings and system information in the menus though. My idea of a good OS is one where anything a user wants to do is available both by menu and by command. Lubuntu seems to make things available **either** by menu **or** by command, and a little bit falling through the cracks that isn't available easily either way. Ubuntu with Unity I'm afraid of because from what I've read about it, it seems to have a menu that requires guessing what programs are installed and their names when it doesn't show them. That seems like a really bad design idea and a game I don't want to play, using a special text input box that's for guessing what's not shown in the menu.

So I'm interested in maybe setting up Ubuntu with LXDE, as others suggested to me.

You seem to be missing the point here slightly. :)

Pretty much everything is available by command, and most is available by a graphical interface. What do you want to do?

You've been reading negative reviews by the angry people who didn't like the change. Positive reviews are always thin on the ground when free software changes, it seems. The point of unity is that your most-used apps are on a launcher at the side, and anything else you just search for. It uses fuzzy matching and such, so you could probably type "Music" and Rhythmbox (a music player) and the sound control might come up. It's not something I'd recommend with your level of hardware acceleration and RAM, though. There are, however, plenty of people who like it (myself included) so use it or find out the facts before calling it a 'bad design idea'.

Ubuntu with LXDE would be Lubuntu. All you'd have is the Ubuntu applications rather than the Lubuntu ones. Which would be rather pointless, I feel. But whatever you choose.

---

### Post by VinDSL on 2012-07-07
> **MG&TL said:**
> You've been reading negative reviews [...]

Ubuntu with LXDE would be Lubuntu. All you'd have is the Ubuntu applications **[COLOR="DarkRed"]rather than[/COLOR]** the Lubuntu ones. Which would be rather pointless, I feel.
Actually, installing LXDE/Openbox on top of Ubuntu 3D gives you all the LXDE/Lubuntu apps, **[COLOR="DarkRed"]plus[/COLOR]** all the Unity apps, GTK 2-3 themes, icon sets, and so forth, and so on.

Add GS (Gnome3 gnome-shell) to the mix, and you have the best of all possible worlds available at login.  :)

The "problem" with most LXDE distros is they're too slim and limiting, e.g. lightweight - Lubuntu is but one example. Add some muscle with Ubuntu 3D/Gnome3/GTK+3 support, and you got the world by the tail...

---

### Post by MG&amp;TL on 2012-07-07
> **VinDSL said:**
> Actually, installing LXDE/Openbox on top of Ubuntu 3D gives you all the LXDE/Lubuntu apps, **[COLOR=DarkRed]plus[/COLOR]** all the Unity apps, GTK 2-3 themes, icon sets, and so forth, and so on..

Correction:

If you install the *lubuntu-desktop* package, you get Lubuntu apps.
If you install the *lxde* package, you just get the desktop. And a few supporting apps, such as leafpad, if you really want to be finicky. :)

```
apt-cache depends lxde
lxde
  Depends: lxde-core
  Depends: lxappearance
  Depends: lxinput
  Depends: lxsession-edit
  Depends: lxshortcut
  Depends: gpicview
  Depends: lxterminal
  Depends: leafpad
  Depends: xarchiver
  Depends: lxrandr
  Depends: obconf
  Depends: lxde-icon-theme

```

;)

---

### Post by VinDSL on 2012-07-07
> **MG&TL said:**
> Correction:

If you install the *lubuntu-desktop* package, you get Lubuntu apps.
If you install the *lxde* package, you just get the desktop. And a few supporting apps, such as leafpad, if you really want to be finicky. :)
Fair enough!  I just wanted to be perfectly clear about this.

LXDE/Openbox loaded on top of Ubuntu 3D is NOT Lubuntu.

Lubuntu, so called, is just your typical, buggy, lightweight hack.

If you want to go that route, I would suggest installing Peppermint Two OS (a Lubuntu fork, that actually works).

I'm talking about installing Ubuntu 3D, configuring it, then loading LXDE/Openbox on top of it.

Put another way, running LXDE/Openbox as your DE/WM, instead of Unity3D/Compiz or Unity2D/Metacity.

What I'm suggesting (and doing) is apple n' oranges, compared to Lubuntu - that's all I'm saying.

I know it's hard to wrap your mind around the concept. I'm the only one doing it, AFAIK.  

Maybe I'll make a HOWTO thread.

* Oops!  Just realized this is the "Absolute Beginner Talk" forum...  :oops:

---

### Post by MG&amp;TL on 2012-07-08
> Lubuntu, so called, is just your typical, buggy, lightweight hack.We do our best. ;)

> I'm talking about installing Ubuntu 3D, configuring it, then loading LXDE/Openbox on top of it.

Put another way, running LXDE/Openbox as your DE/WM, instead of Unity3D/Compiz or Unity2D/Metacity.The first paragraph....that's...bizarre. Removing compiz should kill unity, although Unity 2d should be okay...so you're not really loading on top of it, you're loading...past it? That is interesting, I shall look at your screenshots more closely. :-k

The second paragraph sounds pretty normal, you're just installing LXDE on Ubuntu. Maybe I misunderstand?

> I know it's hard to wrap your mind around the concept. I'm the only one doing it, AFAIK.  A better phrasing might have been "I know this is weird, I'm the only one doing it AFAIK".

> Maybe I'll make a HOWTO thread.You do that (although maybe a wiki page would be better). PM me if you do. :lol:

---

### Post by SonnyE on 2012-07-11
Here's where I update what I've been doing, because I don't like threads with bug complaints being left hanging as if they were never solved and the posters just quit open-source software or went offline.

> - (major problem) Gnome-mplayer included doesn't play ordinary mp3 or FLAC audio files, doesn't give any sign that it doesn't or couldn't play the particular files, letting them seem empty (0:00) and Gnome-mplayer is set as the default mp3 and FLAC player, although Audacious included does play those mp3 and FLAC files. (update: I set Audacious as the default player for mp3 and FLAC)


Solved by work-around: uninstalled Gnome-mplayer. There was an error message that gave me enough information to know the version of Gnome-mplayer that came with Lubuntu 12.04 i386 wasn't compiled to be compatible with my processor, which is a 32-bit i386 compatible (mobile Athlon AMD XP2800+.)

> - Setting a compose key (aka Multi_key in xmodmap) requires using the command line and doesn't cause a compose key to be available for input. (Although the key chosen shows up as changed to Multi_key in xev, it becomes a useless key.) The GUI interfaces included have no options for even something as simple and standard to Linux as setting a compose key. Starting from English US the GUI interface doesn't have a way to add languages or input methods, just greyed out buttons for that. (Currently I can use a compose key only in UXTerm or XTerm, but not in desktop applications or LXTerminal, and not in tty unless I set that manually using a complicated command. Trying right now various advice about how to enter characters by Unicode number, and even that fails to produce any results. !falta! Stoerung! un echec)


> - Some links to programs in the menu do nothing, such as Input Method Switcher.


Solved by uninstalling ibus and Input Method Switcher. According to some bug reports, in Lubuntu 12.04, ibus causes loss of ability to use a compose key.

Voilà. Now my computer is multilingual with a working compose key, even if I'm not.

----------

As for trying Rosegarden:

I got Vmpk, Rosegarden, Jack Audio, and QSynth working together. Then I added Frescobaldi for editing a glitch in Rosegarden 11.11.42 score output: too many rests in a bar, which Lilypond couldn't handle. Then I tried ZynAddSubFX and got it to output sound using Alsa-OSS.

The main problem I have now is the computer freezes to 1/1000 speed if I try to lock too much memory. I guess I want more RAM and an easy way to install Ubuntu Studio without a DVD.

---

### Post by ub07 on 2012-07-11
> **SonnyE said:**
> 
I guess I want more RAM and an easy way to install Ubuntu Studio without a DVD.

There are places online where you can order Ubuntu on DVDs or bootable USB memory sticks and have it shipped to you for just a few dollars. I have to do this because I don't have a fast internet connection.

---

### Post by Elfy on 2012-07-11
> **SonnyE said:**
> ... I guess I want more RAM and an easy way to install Ubuntu Studio without a DVD.
I gave you that in post #5

---

