---
title: "Unable to install 22.04LTS server on Dell PE 610"
date: 2022-07-22
forum: New to Ubuntu
---

### Post by byrnejb on 2022-07-22
I have an old Dell PowerEdge on which I am trying to install Ubuntu 22.04 from a USD drive.  I created the usb image from an iso file downloaded from the Ubuntu mirror at U of Waterloo.  The downloaded iso file passed the sha256 checksum test.

The problem is that the startup simply ends before it gets to the install part.  The system simply halts.  There is no video.  I can reboot using c-a-d but the boot sequence is always the same.

Unfortunately, the console messages blaze by far too quickly for me to read and the display goes blank at the moment the system halts leaving nothing to see.

I have checked the flash drive and it appears correct.  In any case I have used several without any change in the outcome.  I am able to install FreeBSD on the same system so it appears not be be some flaw with the hardware.  I have tried to install on a different system with the same result.

I have no idea what to do.

---

### Post by oldfred on 2022-07-22
What video card/chip?

If any of these, they are now obsolete:
The stock kernel of Ubuntu 17.04 and later  is doing away with Direct Rendering Manager (DRM) support for a number of ancient graphics processors. 3Dfx Banshee/Voodoo3+, ATI Rage 128, Matrox G200/G400, SIS, VIA, and Savage hardware
This was done because they expose insecure APIs to user-space.

---

### Post by MAFoElffen on 2022-07-24
He has Matrox G200eW... Which he can use "nomodeset" as a Kernel Boot option to do Low Res Graphics... And do Vesa Modes later with VesaFB...

oldfred is right in that Xorg's MGA driver was not meant meant to work with the Matrox intergrated GPU. Linux Kernel 4.13 - 5.9 did not support it, but...

The Linux Kernel added the opensource driver for MGA 100, 200 & 400 in Linux Kernel 5.10. ([https://www.phoronix.com/news/Linux-5.10-Matrox-G200](https://www.phoronix.com/news/Linux-5.10-Matrox-G200)) That opensource driver was developed by SUSE. It has DRM support. And is tied to VesaFB. ([https://github.com/torvalds/linux/blob/master/drivers/video/fbdev/matrox/matroxfb_base.c](https://github.com/torvalds/linux/blob/master/drivers/video/fbdev/matrox/matroxfb_base.c)) It is still in Linux Kernel up through current Linux Kernel 5.19-rc+HEAD. ([https://cateee.net/lkddb/web-lkddb/DRM_MGAG200.html](https://cateee.net/lkddb/web-lkddb/DRM_MGAG200.html)) Not sure how well it plays with Wayland. I have heard it does work, but have also heard of problems with for some, so safe bet would be to use Xorg... With Xorg, it will use the Xorg Modesetting driver...

Use Linux boot option parameters: 
```

video=vesafb:mode_option=1920x1200-16,mtrr=3,scroll=ywrap

```

---

### Post by byrnejb on 2022-07-25
The issue is solved by (e)diting the install option and adding [FONT=Courier New]nomodeset[/FONT] to the [FONT=Courier New]linux [/FONT]command.  The monitor is a cabinet mounted KVM monochrome 800x600-0.

---

### Post by byrnejb on 2022-07-25
However, the installer fails at the point where is is requesting the name of the user and the machine.  I have download the installer update but the problem remains.  It simply reports that there was a problem with the installer and asks to restart.

---

### Post by SeijiSensei on 2022-07-25
Have you tried installing a desktop version of Ubuntu on this machine? Does the installation fail in the identical way?

[https://cdimage.ubuntu.com/jammy/daily-live/current/jammy-desktop-amd64.iso](https://cdimage.ubuntu.com/jammy/daily-live/current/jammy-desktop-amd64.iso)

---

### Post by MAFoElffen on 2022-07-27
I have a lot of Dell PowerEdge Server hardware. I am also a Certified On-Site Warranty Service Tech for Dell, HP and Lenovo... And my day-to-day Workstation at home is a SuperMicro Server MB with the same integrated GPU (Matrox). I've been running Ubuntu on Dell Server hardware since Ubuntu 10.04 LTS.

In fact, for that series PE 1U rack server, there is a hack, where you can mount a 16 lane PCIe GPU card as just using 8 lanes... But you have to carefully modify the case. Not for the unskilled mod'er. Or you could mount a 1x GPU card at low res... Being you are using 800x600, I can see that low res in not a problem.

Your posts are a bit cryptic (by omission) in the information you have provided so far. You did not say what you are trying to install. I am suspecting Ubuntu  20.04 or 22.04. Server? And did you check the md5sum of the image before  you created the install image? On boot of the install image, did you see  if checking the filesystem files for integrity? Did those all check out  well? Because when I see people reporting failures in the installer, at random places, a corrupted installer image is usually the culprit.

Even if you are running the server live install image, that is a LiveCD, meaning it boots a Linux Kernel and filesystem as a Live Image Environment (LIE). We have jokingly update the terminology from the old "LiveCD" to "You are running a "LIE". (I know. Twisted humor...) 

Anyways, once you have started the Live (Server) Installer and get to the partitioner, look in the upper right hand corner of the panel for the button. I think it says "Help" Select. A drop down menu appears. Select "Drop to Shell" or similar... It will get you to a command prompt... From the command prompt, first:
```

sudo apt install pastebinit

```
Then:
```

wget -N -t 5 -T 10 https://github.com/Mafoelffen1/system-info/raw/main/system-info && chmod +x system-info && ./system-info

```
That will download and run my Ubuntu Forums 'system-info' (The new version from [DEV/TEST]("https://github.com/Mafoelffen1/system-info")). That 'new' version is just about ready to get pushed to [STABLE]("https://github.com/UbuntuForums/system-info"). The script will create a report that will answer what you are working with and we are recommending answers for. Select upload, and write down the link that the Pastebin uploads to... And post that link in a post here. (By making sure 'pastebinit' is installed first, it will default the routines in that script to upload the Pastebin to [https://paste.ubuntu.com](https://paste.ubuntu.com) )

Note: This way will not install anything to your own computer. It will temporarily install and run everything from the Live Image Environment. (The safest way...) Then 
```

exit

```
Will get you back to the installer...

###
A bit of preliminary work needs to be done first, before you install, in the way of storage... Those PE servers came with Dell PERC RAID cards. Depending on the Generation of the server, when I look it up in general (I don't have your Service Tag Number), I see it used the old PERC cards, which topped out at recognizing up to 2TB each drive... But since the hot-swap bays are 2.5", I doubt you are trying to use anything larger. 

Another quark, is that you first have to define the storage of those drives. On boot, use the hot-key to get into the PERC BIOS setup. If you have more than one drive, you could define a RAID Array, but... I really didn't go that way. You can use a single drive, or multiple single drives, by defining "single drive" RAID 0 Arrays for each drive. PERC cards do not do JBOD. So that is the way you do pseudo JBOD with those Cards. If you do not not understand that, I will explain that 'differently'. Then when the Installers partitioner starts, it will see whatever RAID Arrays you defined. If not, then the partitioner will not see any storage at all.

I guess it might help if we knew what your end goal was... The plan. (what you are trying to do and the job it will do for you.)

---

### Post by MAFoElffen on 2022-07-27
I was thinking... I'm curious.

If that error happens at that same place again, using the same as what you entered originally... when the Live Installer gets an error like that, it shows a link on the bottom of the screen pane to look at the Installer Log, where you could go to the end of that log and see what kind of error occurred. Then take a picture on your phone to upload as an attachment?

If not, use the instructions I just posted to drop to the shell and
```

dmesg | tail -50

```
Or look at the Subiquity Logs:
```

sudo egrep -A 1 -e 'subiquity.client.controllers.identity:' /var/log/installer/subiquity-client-debug.log

```
That last command is where in that specific log, where it should have entered the info you said it got an error on... When it should have populated the variables for realname, username, and hostname, and called IndentityData(). The line after that shows the result of that call (SUCCESS or FAILED).

It does that after exiting that screen pane and before initializing the next screen pane. It writes that log to the Target Drive, so you may have to preface that command path/filename with the /dev/sdX/... of that target drive.

---

