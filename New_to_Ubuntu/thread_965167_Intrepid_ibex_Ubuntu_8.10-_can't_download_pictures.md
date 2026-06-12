---
title: "Intrepid ibex Ubuntu 8.10- can't download pictures from camera"
date: 2008-10-31
forum: New to Ubuntu
---

### Post by jack_harper2007 on 2008-10-31
Hi i'm using a Kodak CX7300 camera and have this problem: i can't download the pictures from the camera to the PC, i find this strange because the camera connects just fine but when i try to use F-Spot to download the pictures F-Spot freezes, also when i try to open the camera as a folder i can see the icons of the pictures (without the preview) but i can't open them or copy them to the computer. Also after i unmounted the camera can't mount it again it always displays this error: "Could not lock the device"
I've also tried to switch the camera to different USB port but it's the same thing.

In the previous versions of Ubuntu i didn't had any problems with the camera :(

Can someone help me figure this out? Thanks!!

---

### Post by bodhi.zazen on 2008-10-31
I had a Kodak briefly (1 year ago) and they do not support Linux. 

I called customer support and it was a no-go, so I returned the camera.

I hope you have better luck with yours.

---

### Post by cykotiktek on 2008-10-31
I am having this same issue with my canon camera

---

### Post by azebuski on 2008-10-31
I have never had any luck using Kodak cameras with Linux.  HP PhotoSmart cameras and photo printers all seem to work great with Ubuntu.

---

### Post by chrisod on 2008-10-31
I have downloaded thousands and thousands of pictures from my Kodak Z740 with Ubuntu 7.X and 8.04. It just works, I've never done anything special that I can remember. Have you tried importing the pictures with gThumb? That is what I use to import, then I use Picasa to manage the photo library. It works flawlessly.

---

### Post by jack_harper2007 on 2008-10-31
Well i've been trying to use other software like gtkam to import the pictures but still nothing :( 
I'll try and use gThumb like chrisod suggested i'll tell you guys if it worked ;)

---

### Post by jack_harper2007 on 2008-10-31
Ok used gthumb but still couldn't download any pictures from the camera. This message appeared:"An error occurred in the io-library ('Could not lock the device'): Camera is already in use"

Any more ideas?

---

### Post by PierreDeKat on 2008-10-31
I'm wondering if your mounting may have gotten confused for some reason.

Perhaps try disconnecting the camera, restarting your computer, and then plugging it in again.

Once you get it plugged back in, you'll have a popup option thing, and this time, try selecting "Open Folder" first, instead of the "F-Spot" option.

I've never liked F-spot, and I've always treated a camera like any other media I want to copy and paste files from.

Anyway, I do know that "Open Folder" worked for me this morning. And it could be that there's a bug in F-Spot that's confusing the mounting.

---

### Post by clive littlewood on 2008-10-31
Hi

If the other suggestions don,t work try digicam from the repos.

I have used this with many cameras and it seems to work for me ootb.

Hope this helps

Clive    :)

---

### Post by jbg7474 on 2008-10-31
I think USB stuff seems broken in 8.10.  I can't sync a Palm device either.

---

### Post by jack_harper2007 on 2008-11-01
> **clive littlewood said:**
>  If the other suggestions don,t work try digicam from the repos. 
Thanks clive littlewood i did what you suggested but it didn't work :(

> **jbg7474 said:**
> I think USB stuff seems broken in 8.10.  I can't sync a Palm device either.
jbg7474 i don't think that the usb stuff is "broken" in ubuntu 8.10 i can syc my ZEN player and cellphone without any problem, and software (f-spot...) detects pictures in my camera i just can't transfer them to my computer, i think your is a different, but equally annoying, problem ;)

---

### Post by swerner on 2008-11-01
I have the same problem.  However, I see that the camera is mounted at the same time as gphoto tries to download the images.  When I unmount the camera from my desktop, and restart the photo download it works.

---

### Post by tereshkosg on 2008-11-01
hey guys,

have similar problem with Nikon Coolpix ...

not waisting too much time on figuring out what exactly was wrong I tried ...

sudo umount -a  (don't have anything mounted except the camera, so don't care)

immediately after that a dialog popped out , saying that a camera had been plugged in.
in the popped up dialog chose to browse the folder and was able to copy the pictures.
hope that helps. 

Cheers

---

### Post by Ahunt on 2008-11-02
I am having a similar problem here. I have a Panasonic DMC-FX2, circa 2004. It works fine on Hardy, although previously could not be identified on Feisty and Gutsy. It works fine on Hardy Live CD session, too. In both installed Hardy and Live CD it is identified, loads the drive and the pictures can be exported using F-Spot or as files directly from the camera.

I tried running an Intrepid live CD session, plugged in the camera and got the error:

```
Unable to mount Panasonic (Matsushita) Lumix DMC-FZ10 Camera

Error initializing camera: -1: Unspecified error
```

So it isn't even identifying the right model of camera (FZ10 vs FZ2) and cannot be read or pictures downloaded. Other USB devices read just fine in Intrepid live session.

Looks like time for a bug report on Intrepid! I am sticking with Hardy.

---

### Post by Ahunt on 2008-11-02
After having posted above I serched LaunchPad to see if this bug has been reported. It has been reported as Bug #285682

[https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682)

I also added a note on the bug report linking it to this page for cross reference.

---

### Post by Ahunt on 2008-11-03
Someone more knowledgeable than I has suggested that if your camera will not read on Intrepid, but it has a removable-style SD card, that a USB card reader may be the solution. You would pull the card out of the camera and plug it into the USB card reader and Ubuntu *should * identify it as a generic USB drive, enabling the photos to be copied from the card as files.

Has anyone tried this?

---

### Post by Robbyx on 2008-11-03
I have just found a way around my problem.


1. Update the system software, using the update manager in system--admin-- update manager. Maybe some of those new files that were just downloaded made a difference to what follows.

2. Go into your file manager. I am using PCMan File Manager. This seems to see the camera. I can not spot it in Nautilus, but I may be looking in the wrong place.  Plug in the camera and in my case it was mounting and showing as a drive in PCMan.

3. Browse to the camera card and download the pictures.

At present none of the picture managers automatically open when the camera is connected to the usb port.

Robin

---

### Post by jack_harper2007 on 2008-11-03
> **Ahunt said:**
> Someone more knowledgeable than I has suggested that if your camera will not read on Intrepid, but it has a removable-style SD card, that a USB card reader may be the solution. You would pull the card out of the camera and plug it into the USB card reader and Ubuntu *should * identify it as a generic USB drive, enabling the photos to be copied from the card as files.

Ahunt that works, it is a way to transfer the pictures from the camera, but in my opinion that works as a "temporary" solution since not everyone has a SD card or USB card reader and we should be able to import the pictures from cameras without having to "find ways to get around problems" ;)
But i did what you suggested and came across some weird results: When i inserted the SD card in my camera and connected it to the PC i was able to view and transfer the pictures from the card and pictures from the internal memory of the camera (without having to copy the pictures from the internal memory to the card ;) ), i could view and import the pictures by using F-Spot or "open folder" :O I think this is wierd because when i remove the SD card from the camera i can no longer view or import pictures from the internal memory and when i try to use F-Spot to download the pictures F-Spot freezes.
So i can import and view pictures just fine as long as i have the SD in the camera. Again i think that's weird and i think that keeping the SD card in to be able to import and view pictures from the camera is not a very good solution, i mean it works but not everyone has a SD card :(

So for now if any one is having troubles importing or viewing pictures from cameras you could try inserting an SD card and then try and use F-spot or "open folder" to import the pictures from the internal memory of the camera and/or the SD card and see if it works... (i'm still not marking this thread as "solved" because i think there has to be a better solution)

---

### Post by Ahunt on 2008-11-04
I am glad to hear that the USB card reader works. I agree that while it works it isn't the ideal solution, but is, instead, a "work-around".

Here is something even stranger - my Panasonic DMC-FZ2, has only an SD card for memory, no other internal memory. As mentioned in Hardy the camera is identified and the pictures can be downloaded from the SD card through the camera just fine.

In Intrepid the camera is not recognized and no download can be carried out, without, perhaps a separate USB card reader, although I haven't got one and so haven't checked it. I am still running Hardy and only did a test on Intrepid. I don't see any reason to switch right now!

I don't use F-Spot, I prefer to work with the files directly, so that isn't an issue for me that it doesn't open.

I totally agree with you that while work-arounds can work there is no reason that hardware should be supported in one release of Ubuntu and then not supported in the next one. From this thread it is clear that many brands and models of camera have been dropped in Intrepid. This is going to frustrate the heck out of a lot of people and may drive them to re-install Windows, if only to get their cameras working again.

I continue to maintain that the lack of consistency in hardware support is the biggest reason that people don't move to Ubuntu - something may work now, but may not work in the future. This has to improve for Ubuntu and Linux in general to gain more acceptance. As it is, it doesn't "just work."

---

### Post by Ewan the moomintroll on 2008-11-04
I've had the same problem wit a lumix dmc-fz30. it worked with 8.04.

---

### Post by billgoldberg on 2008-11-04
I filed the bug a few weeks back now and all the info is provided, so I hope the issue get fixed soon.

---

### Post by pki on 2008-11-04
Here you can already download and install the fixed packages.

I installed this
[https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-2_2.4.2-0ubuntu3~ppa1_i386.deb](https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-2_2.4.2-0ubuntu3~ppa1_i386.deb)

and this
[https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-port0_2.4.2-0ubuntu3~ppa1_i386.deb](https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-port0_2.4.2-0ubuntu3~ppa1_i386.deb)

Now my lumix is working again.

---

### Post by Ahunt on 2008-11-04
Bill: Thanks for filing the bug report! You beat me to it!

TKI: Let's hope those debs get incorporated into the updates, if they haven't already done so. We are sticking with Hardy, so if anyone can confirm that the problem is fixed through the update process perhaps they can post here to finish the issue.

I am watching the bug report, as I am sure Bill is, too and so will post here if it gets addressed at that level. 

I think it is helpful for both users and developers to link the bug report and this forum thread, so I posted each URL on the other one.

---

### Post by pki on 2008-11-05
The fix is in the respository now.

#sudo apt-get upgrade

fixed the problem now on my interpid wind notebook

---

### Post by JacobOfLinux on 2008-11-06
pki: thank you.  I have installed both of those .deb packages and now my Panasonic Camera works, it is a DMC-FX3 (DMC-FZ10).

---

### Post by Ahunt on 2008-11-09
That is good news that this problem *seems* to have been fixed by updates sent out since the release of Intrepid. I have added a note to that effect on the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682").

If anyone has found that the updates have not enabled a camera that did work on Hardy to work on Intrepid can they please make a post here, so we can figure out if this is fixed or not - thanks!

---

### Post by jtmicky on 2008-11-09
It is still not working for me.  I have both of the new libgphoto2 packages installed via the repos:

[FONT="Courier New"]ii  libgphoto2-2   2.4.2-0ubuntu3 
ii  libgphoto2-por 2.4.2-0ubuntu3[/FONT]

My camera is a Sony DSC-W150 and connects in PTP mode.  Worked fine under Hardy.

When I connect my camera, it is mounted and a icon appears on the desktop for the camera.  When I start gthumb with [FONT="Courier New"]gthumb --import-photos[/FONT] I receive the following error:

[FONT="Courier New"]An error occurred in the io-library ('Could not lock the device'): Camera is already in use.[/FONT]

Once I unmount the camera and restart gthumb I am able to import.

---

### Post by walter.kramer on 2008-11-09
I still have the same problem.  My camera is a Leica Digilux 3 (basically the same camera as the Panasonic DMC-L1)  Worked fine under Hardy but I get no response under intrepid, not even an icon to tell me that the computer recognises a new device.  I have to run Knoppix and transfer the files to a USB key and then reboot into Intrepid before I can add new images to my collections.

Intrepid is fully updated on my machine so I don't think the updates have worked for all cameras that used to work under Hardy.

Thanks

---

### Post by Teledesign on 2008-11-10
Can't mount or see a Canon Ixus 970 IS

I'm using Kubuntu. I've just updated it - still not working.

It worked just fine with 8.04

Andrew

---

### Post by swerner on 2008-11-10
> **pki said:**
> Here you can already download and install the fixed packages.

I installed this
[https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-2_2.4.2-0ubuntu3~ppa1_i386.deb](https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-2_2.4.2-0ubuntu3~ppa1_i386.deb)

and this
[https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-port0_2.4.2-0ubuntu3~ppa1_i386.deb](https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-port0_2.4.2-0ubuntu3~ppa1_i386.deb)

Now my lumix is working again.

This didn't fix my problem with a Canon S5 IS.

---

### Post by swerner on 2008-11-12
For the people with the problem where the camera is mounted in the background and want to use gphoto, a workaround has been posted [_here_]("http://ubuntuforums.org/showthread.php?p=6161390#post6161390").

Basically, in "Preferences > Removable drives and media" you put "**gvfs-mount -s gphoto2 & gnome-volume-manager-gthumb %h**".  The problem with this is that all your cameras currently plugged in will be unmounted.  You could workaround this by writing a script.

Kudos to [_Denis_]("http://ubuntuforums.org/member.php?u=31882").

---

### Post by kroetenmist on 2008-11-13
hi,

my camera (canon ixus 55) has the same problem :

> "An error occurred in the io-library ('Could not lock the device'): Camera is already in use"

in the german support forum other users reported similar problems. here are a list of cameras wich doesn`t work since intrepid:

canon ixus 55
Caplilo G3
Nikon 4200
Fuhitsu F31/fd

[IMG]http://launchpadlibrarian.net/19612413/167989.png[/IMG]

---

### Post by Ahunt on 2008-11-16
A new posting on the bug report [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682) indicates that there is still a problem with Canon 400D cameras as well.

 Also on the bug report one user indicated that his SD-USB card reader also did not work. I asked one knowledgeable user about this problems and he said "Anything to do with USB is not as simple as driver files. There are a handful of kernel modules that apply to USB, and they vary according to the chip set on your motherboard. Since 8.10 has a new kernel, these have probably changed, as a start. Add in new versions of libraries and new versions of applications, and there are a few places where these incompatibilities could arise."

We still seem to have a lot of cameras that are not working!

---

### Post by walter.kramer on 2008-11-17
For what it may be worth.  I reinstalled Intrepid last night, keeping home intact of course.  This seems to have fixed the problems I was having with my Leica and Panasonic cameras.  Somehow the updates were ineffective on my system until now.  This might be a last resort for Leica and Panasonic users still having problems.

---

### Post by enoch_zembecowicz on 2008-11-20
I'm having the same issue myself, with both a Nikon Coolpix L12 and a Nikon D60.
I've noticed that if I start f-spot as root it will work about half the time.

Here's console output for when I does not work:

```

** No session dbus found. Starting one **
[Info  23:19:44.970] Initializing DBus
[Info  23:19:45.106] Initializing Mono.Addins
[Info  23:19:45.310] Starting new FSpot server
[Info  23:19:46.316] Starting BeagleService
[Info  23:19:46.317] Hack for gnome-settings-daemon engaged

(f-spot:2387): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Personal Data, Nov 11, 2008 - gnome-dev-disc-dvdr-plus - Mountpoint file:///media/cdrom0 True True Cdrom
Cdrom
KINGSTON - gnome-dev-harddisk-usb - Mountpoint file:///media/KINGSTON True True Harddrive
Harddrive
truecrypt1 - gnome-dev-harddisk - Mountpoint file:///media/truecrypt1 True True Loopback
item ImportCommand+SourceItem
Testing gphoto path = usb:001,015
PortInfo Universal Serial Bus, usb:001,015
Error Lock: LibGPhoto2.GPhotoException: Could not lock the device
  at LibGPhoto2.Error.CheckError (ErrorCode error) [0x00000] 
  at LibGPhoto2.Camera.Init (LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.InitializeCamera () [0x00000] 
  at MainWindow.ImportCamera (System.String camera_device) [0x00000] 
cleanup context
cleanup context
[Info  23:19:57.901] Exiting

```


And here's the output I get when it does work:
```

** No session dbus found. Starting one **
[Info  23:20:14.606] Initializing DBus
[Info  23:20:14.740] Initializing Mono.Addins
[Info  23:20:14.951] Starting new FSpot server
[Info  23:20:15.937] Starting BeagleService
[Info  23:20:15.937] Hack for gnome-settings-daemon engaged

(f-spot:2509): GdkPixbuf-WARNING **: GdkPixbufLoader finalized without calling gdk_pixbuf_loader_close() - this is not allowed. You must explicitly end the data stream to the loader before dropping the last reference.
Personal Data, Nov 11, 2008 - gnome-dev-disc-dvdr-plus - Mountpoint file:///media/cdrom0 True True Cdrom
Cdrom
KINGSTON - gnome-dev-harddisk-usb - Mountpoint file:///media/KINGSTON True True Harddrive
Harddrive
truecrypt1 - gnome-dev-harddisk - Mountpoint file:///media/truecrypt1 True True Loopback
item ImportCommand+SourceItem
Testing gphoto path = usb:001,015
PortInfo Universal Serial Bus, usb:001,015
Error NotSupported: LibGPhoto2.GPhotoException: Unsupported operation
  at LibGPhoto2.CameraFilesystem.GetFile (System.String folder, System.String filename, CameraFileType type, LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.GetPreview (Int32 index) [0x00000] 
Error NotSupported: LibGPhoto2.GPhotoException: Unsupported operation
  at LibGPhoto2.CameraFilesystem.GetFile (System.String folder, System.String filename, CameraFileType type, LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.GetPreview (Int32 index) [0x00000] 
Error NotSupported: LibGPhoto2.GPhotoException: Unsupported operation
  at LibGPhoto2.CameraFilesystem.GetFile (System.String folder, System.String filename, CameraFileType type, LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.GetPreview (Int32 index) [0x00000] 
Error NotSupported: LibGPhoto2.GPhotoException: Unsupported operation
  at LibGPhoto2.CameraFilesystem.GetFile (System.String folder, System.String filename, CameraFileType type, LibGPhoto2.Context context) [0x00000] 
  at GPhotoCamera.GetPreview (Int32 index) [0x00000] 
Stopping
cleanup context
cleanup context

```

What would be a good way to find out what IS locking the usb device?

---

### Post by kroetenmist on 2008-11-20
> I reinstalled Intrepid last night, keeping home intact of course. This seems to have fixed the problems


well, this is what i am trying to avoid.

---

### Post by timbosity on 2008-11-21
HI, Seem to have the same problem as you folks with canon ixus500 and powershot550S. they both used to show perfectly fine in gutsy and hardy in thunar (Im into XFCE and xubuntu) and then was able to do what I wanted to from there. However since the intrepid nada. I have tried mount: mount /dev/bus/usb/001/011 (which is what shows up when I plug the yokes in) but didnt work. Didnt want to push it further without checking here but it seems to be a general problem??

---

### Post by clive littlewood on 2008-11-21
Hi All

Just for info i have just plugged in my nikon coolpix L11 and Fspot has recognised it and imported the photos. !!!!!

This was not happening when i first installed Ibex.    :(

So i would assume that updates have worked for me.     :)


Clive

---

### Post by hansley on 2008-11-24
Hi everyone,

Kubuntu user here, and I'm still having the same problem (cam won't mount) after all the available current updates.  I'm using a Canon A630.

The cam shows in lsusb:

```
billm@blue:~$ lsusb
Bus 002 Device 007: ID 04a9:313a Canon, Inc.
Bus 002 Device 004: ID 05e3:070e Genesys Logic, Inc. X-PRO CR20xA USB 2.0 Internal Card Reader
Bus 002 Device 001: ID 1d6b:0002 Linux Foundation 2.0 root hub
```

but nothing in either mount or fdisk -l.

Another interesting tidbit: if I have vmware player running, it notices the camera when it's connected and offers to connect it to the running VM session.

The camera worked great under 8.04.

-Bill

---

### Post by Stratok on 2008-12-03
Oks I have a cannon DC22 that worked on 8.04, it stoped working in my 2 computers at the same time (probably an update) like 1 week before intrepid was released... I upgraded to intrpid... still does not work.
some people suggested to downgrade libgphoto... but i dont know how to do that...

---

### Post by apostate on 2008-12-05
> **Ahunt said:**
> That is good news that this problem *seems* to have been fixed by updates sent out since the release of Intrepid. I have added a note to that effect on the [bug report]("https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682").

If anyone has found that the updates have not enabled a camera that did work on Hardy to work on Intrepid can they please make a post here, so we can figure out if this is fixed or not - thanks!

HP Photosmart is still busted. 

"An error occurred in the io-library ('Could not lock the device'): Camera is already in use."

---

### Post by Stratok on 2008-12-05
ok, I tried to import photos (canon DC22) from a fresh hardy instalation, it works, in my laptop works under xp, does not work under hardy (updated), and in intrepid it does not work either...
The solution people posted at the begining of this thread was upgrading libgphoto, since it was working, and the upgraded version does not work... I want to downgrade it...
In my lap I still have hardy, so I just opened synaptic, searched libgphoto, and downgraded libgphot2-2 and libgphoto2-port 0 (select package and press ctrl+e) to version 2.4.0-8ubuntu 6..., than I searched packages again and locked the version (in upper menu: package-> lock version)
Now my camera works works again...

I'VE FOUND THE PROBLEM!

In intrepid you cannot downgrade this packages because they dont apear in the downgrade list, so I manualy downloaded the .deb files from the hardy repository, but I cannot install them because it says that a newer version is installed. 

Now I go to synaptic, and If I try to remove libgphoto2-2 or libgphoto2-port0 it will try to remove  a lot of programs with that, nautilus, fspot, gthumb, etc...
is there a way of downgrading without uninstalling everything?
(I dont want to search the uninstalled software one by one to reinstall everything again...)

---

### Post by ifinishwhatistar on 2008-12-20
So is there still no solution to this problem?  I have a Canon Powershot SD800 on a fully updated intrepid and the device fails to mount with the same errors everyone else has posted (just in nautilus, independent of software).  Is this being worked on?

---

### Post by nymusicman on 2008-12-22
I don't know why, but it's just a matter of unmounting the camera before you use your photo import software.

---

### Post by Eugine Axehead on 2008-12-23
> **ifinishwhatistar said:**
> So is there still no solution to this problem?  I have a Canon Powershot SD800 on a fully updated intrepid and the device fails to mount with the same errors everyone else has posted (just in nautilus, independent of software).  Is this being worked on?

Nope ! Not for me anyway.

My camera is a Kodak  DX4530, that worked flawlessly  on Gutsy.  Works sporadically (at best) on (a fully updated) Intrepid, if you  switch it on and off a few times.   Have to use a laptop  running  'doze to get the pics off via a USB  fob, then  stick them on my Ubuntu machine - Not at all annoying :(

I get the  error message  mentioned above :-

An error occurred in the io-library ('Could not lock the device'): Camera is already in use.

Seems to be the same on all packages, or even if I just navigate to the camera having de-installed all the packages.

---

### Post by kroetenmist on 2008-12-23
i am soooooooooooooo sick of ubuntu now. nothing works. no even my old camera.

---

### Post by Eugine Axehead on 2008-12-23
>  i am soooooooooooooo sick of ubuntu now. nothing works. no even my old camera. 


When I first moved over to  Ubuntu (6.06), I put in a hell of a lot of time getting everything to work, from  odd IPV6 issues with my router downwards. I  was rewarded with a perfectly working, solid, system - Thanks to support and kind help from a variety of different forums.  

What sapps the enthusiasm though is  when things get broken  with updates -   This is the latest of a continual stream of things for me. You  feel like you are going backwards for no good reason.  I guess you could just sit there refusing any updates,  but it's hardly progressive and may, ultimately,   leave you open to security issues.

I think there are 2  types of people, those that  have infinite patience and those that just want to get on with  using the computer.   I have to confess to   having shifted over   from being one of the former to the latter type of person. 

I realise that we  shouldn't complain because all this (generally wonderful)  stuff is done on a non commercial basis.   From my personal perspective though.  After   2 and bit years,   I think maybe time to call it a day - Time to check out Apple I think !

---

### Post by celem on 2008-12-30
> **jbg7474 said:**
> I think USB stuff seems broken in 8.10.  I can't sync a Palm device either.

Off Topic: The USB stuff is broken. I noticed your Palm comment. I MUST have my Palm and after a LOT of trials with other options, I use J-Pilot set to /dev/ttyUSB1 It syncs great and prints out a proper calendar for my wife. I got the Palm to work with evolution and Gnome pilot but the evolution calendar won't work for me as Saturday and Sunday occupy one box and it cannot be changed. I removed evolution and installed Thunderbird

---

### Post by Ahunt on 2009-01-05
I know that the suggestion was made earlier that those camera owners who have units that use SD cards can use an "SD card reader". Some posters here reported that worked for them, while others reported that it didn't.

I just picked up an SD card reader, a "USB ALL-IN-ONE FLASH CARD READER"  [http://factorydirect.ca/catalog/product_spec.php?pcode=CA2300](http://factorydirect.ca/catalog/product_spec.php?pcode=CA2300) 

I tried it out on Hardy and it works fine, as does my Panasonic DMC-FZ2 camera. My camera does not work on the Intrepid Live CD, but I tried the reader out on Intrepid Live CD (which is "original", no updates applied) and it works fine there as well. In both cases I was able to download photos from the SD card using the reader. 

This reader works with four different SD card formats. The packaging specifically indicates that it is Linux-compatible, as well and Mac and Windows. The unit is Chinese in origin and, humourously, the brand name on the packaging is "Enjoy Technology, Enjoy Life".

For those people who tried an SD reader and found it didn't work, the problem may have well been the reader itself.

---

### Post by lazyart on 2009-01-05
Card readers work a lot better than cameras do.  Most cameras are only going to transfer at USB1.1 speeds anyway.

I have a PhotoBank.  A 40 gb external hard drive case with memory card slots attached.  I can either use it as a card reader or plug a card in and hit copy on the unit and it copies the memory card to the hard disk.  Then later I plug the drive into the computer and copy from there.  Either way works just fine in Intrepid.

---

### Post by Ahunt on 2009-01-05
lazyart: That is an interesting set-up you describe. Was that something commercially available or did you build it?

---

### Post by leah1984 on 2009-01-07
hi i am having the exact same issues,except i use the app. digicam to upload and shofoto to edit them,i also recenlty uploaded to intrepid,and it all worked fine before hand,i also have the issue of all of my drop menus font disapears quickly after i open them,the icons are there  but the actual words disapear?? any help with this? i am also using a brand new kodak easyshare z1012 is.one more difference is when i plug my camera in a kodak icon appears on my desktop and i can open the files copy and paste them wherever i want.also tryed my fujifilm and when i go to import into digicam i get the message "cannot connect to camera,make sure camera is turned on and plugged in" when i know that both are done.

---

### Post by leah1984 on 2009-01-07
> **pki said:**
> Here you can already download and install the fixed packages.

I installed this
[https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-2_2.4.2-0ubuntu3~ppa1_i386.deb](https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-2_2.4.2-0ubuntu3~ppa1_i386.deb)

and this
[https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-port0_2.4.2-0ubuntu3~ppa1_i386.deb](https://launchpad.net/%7Epitti/+archive/+files/libgphoto2-port0_2.4.2-0ubuntu3~ppa1_i386.deb)

Now my lumix is working again.

i have downloaded these packages but already have the later versions installed,how do i change them?

---

### Post by Captain_tux on 2009-01-07
Sorry, but I'm too busy to read through 6+ pages of replies. To the OP: Here's the solution I found to a somewhat similar problem I had. **F-Spot** opened up for me, but that's not to say you can't use any program you want. Good luck.

[http://ubuntuforums.org/showthread.php?t=948221](http://ubuntuforums.org/showthread.php?t=948221)

---

### Post by Junkieman on 2009-01-07
> **leah1984 said:**
> when i plug my camera in a kodak icon appears on my desktop and i can open the files copy and paste them wherever i want

I use a canon camera and gThumb to import. gThumb also reports that it can't connect to the camera, but I can browse the camera in Nautilus and copy the files off.

What works for me is I unmount the camera before opening gThumb, then it didn't report the error, and the import works fine. Strange...

---

### Post by MikeMcKay on 2009-01-21
For what it's worth . . .

I've had persistent problems very similar to those described above and solved it by running gnome-volume-properties and disabling the option, "Import digital photographs when connected".  

This removes the "A Digital Camera has been detected" (or whatever) dialogue box that appears when you connect the camera.  I now download from the gThumb application.

---

### Post by Ahunt on 2009-02-08
Some further information on this problem. Accidentally I found a new work-around for those people whose cameras were working on Hardy but stopped working on Intrepid. I was recently trying out a live CD of Xubuntu and when I plugged my Panasonic DMC-FZ2 camera in, it connected fine! It seems odd that Xubuntu Intrepid works while Ubuntu Intrepid doesn't, but go figure!

So we now have potentially three work arounds if your camera doesn't work on Ubuntu Intrepid, plus the file editing mentioned above:

* Get an SD card reader (works only if your camera uses removable SD cards)
* Stay with Hardy, after all it will be supported long after Intrepid is gone
* Try Xubuntu 8.10 Intrepid Ibex (ISO download [http://www.xubuntu.org/get](http://www.xubuntu.org/get) )

---

### Post by mgmiller on 2009-02-16
I have a Cannon SD 550 that also has this problem.  Perfect in Hardy, not in Intrepid.  I found that if you right click the icon on the desktop that represents the camera and select "unmount", gthumb, or your other apps will then work as before.  This has been stated by others above this post.

What I did discover was from this post:
[http://ubuntuforums.org/showthread.php?p=6161390#post6161390](http://ubuntuforums.org/showthread.php?p=6161390#post6161390)

Alternative commands in the 
```
gnome-volume-properties
``` such as
```
gvfs-mount -s gphoto2 & gnome-volume-manager-gthumb %h
```did not work for me.

Someone named [zzztownsend]("http://ubuntuforums.org/member.php?u=313492") on that post gave the following instructions that worked perfectly for me.  I will paraphrase them here:

```
mkdir ~/bin
gedit ~/bin/get-photos
```paste in the following code:
```
#!/bin/bash
gvfs-mount -s gphoto2
gthumb --import-photos
```save the file.

make the file executable:
```
chmod +x ~/bin/get-photos
```(Or just right click the file and under the permissions tab, click to allow executing as a program)

finally, in
```
gnome-volume-properties
```for the entry for Digital Camera, click the "Import digital photographs when connected", then click the browse button and go to the file you just created and click it to select it.  It's path should appear in the command line.
(Of course, you could also just type the path into the command line as well).

That's it.

Interestingly, if I put the command:
```
gvfs-mount -s gphoto2 & gthumb --import-photos
```
into the gnome-volume properties, it does not work.  Go figure...

I also found that if I insert an SD card from my camera into a card reader, instead of just opening a file browser which lets me use nautilus to wander around on the card, it also triggers gthumb which finds the pictures straight away and offers to delete them after copying, which is a real time saver.  The option to browse the card with nautilus is still there if I close gthumb.

Also, my son has a newer canon SD 800 which continues to work perfectly in Intrepid.  He did not need to do any of this fiddling about, just plug and play as it has since 7.10 for him.

---

### Post by presence1960 on 2009-02-16
> **Ahunt said:**
> Someone more knowledgeable than I has suggested that if your camera will not read on Intrepid, but it has a removable-style SD card, that a USB card reader may be the solution. You would pull the card out of the camera and plug it into the USB card reader and Ubuntu *should * identify it as a generic USB drive, enabling the photos to be copied from the card as files.

Has anyone tried this?

+1

I have always taken the card out and insert it into my card reader. For reasons I cannot explain using the usb cord never appealed to me even when I used Windows. Card readers are pretty inexpensive anyway whether internal or external.

---

### Post by mgmiller on 2009-02-17
> Originally Posted by **Ahunt**                     [[IMG]http://ubuntuforums.org/images/buttons/viewpost.gif[/IMG]]("http://ubuntuforums.org/showthread.php?p=6096406#post6096406")                 
                 *Someone more knowledgeable than I has suggested that if your camera will not read on Intrepid, but it has a removable-style SD card, that a USB card reader may be the solution. You would pull the card out of the camera and plug it into the USB card reader and Ubuntu [I]should * identify it as a generic USB drive, enabling the photos to be copied from the card as files.

Has anyone tried this?[/I]
If you read the end of my post #58, you will see that I have a camera affected by this problem, but the card reader still works fine.  In fact, Intrepid makes finding the pictures on the card even easier.

In spite of this, I still prefer to just plug the camera into the USB cable.

---

### Post by Xkper on 2009-02-23
I had the same problem ("Could not lock the device").

I removed gphoto2-2.4.2 and libgphoto2-2.4.2, and installed gphoto2-2.4.4 and libgphoto2-2.4.4 available here: [http://sourceforge.net/project/showfiles.php?group_id=8874](http://sourceforge.net/project/showfiles.php?group_id=8874)

The version 2.4.4 is not available in the repositories yet.

That fixed the problem, now I can use Picasa or other program to download photos from my HP R927 camera.

I hope this reply is useful.

---

### Post by drhiii on 2009-02-24
I think USB stuff is broken in 8.10 too.  Everything working in every verion of Ubuntu, until I upgraded into 8.10.  That includes an upgrade, and a fresh install.  All of my USB devices fail to read/write.  They appear as read only.  This only happened when moving to 8.10.

Anyone?



> **jbg7474 said:**
> I think USB stuff seems broken in 8.10.  I can't sync a Palm device either.

---

### Post by Ahunt on 2009-02-27
If all your USB devices are "read only" that is probably a permissions problem and just a matter of changing that in PolicyKit:

System->Administation->Authorizations.

---

### Post by drhiii on 2009-03-02
Tx for the response.  I finally got it sorted out, sort of...

Not all the USB devices were read only.  In a quirky behavior, one device which had been read throughout other versions went ready only when 8.10 was upgraded, then in a fresh install.  Same behavior.  Turns out 8,10 saw the device as damaged.  I ran an fsck against it and it worked, and so did other devices that had gone read only.  Go figure.  Something at boot saw a corrupted disk and decided others would be affected too.

Anyway, tx for the response.  


> **Ahunt said:**
> If all your USB devices are "read only" that is probably a permissions problem and just a matter of changing that in PolicyKit:

System->Administation->Authorizations.

---

### Post by Ahunt on 2009-03-23
For people following this issue it has been reported on the bug report on Launchpad [https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682](https://bugs.launchpad.net/ubuntu/+source/gvfs/+bug/285682)


 JP Foster (23 March 2009):

"I am seeing this same bug in Jaunty now.
Killing gvfs-gphoto2-volume-monitor allows me to access the camera."

---

### Post by Ahunt on 2009-04-26
Just an update here. I installed Jaunty on Thursday 23 April 2009 and my camera works fine on it - Panasonic DMC FZ2. It looks like the problem in Intrepid has been fixed.

I would like to hear from other Jaunty users if you find the problem has not been fixed for your camera.

---

### Post by causeitsme on 2009-05-02
My Kodak C433 still doesn't work. I can pull the pics off by inserting the SD card but, that's a pain. 

I get this message: 

Error initializing camera: -60: Could not lock the device

Also, if I turn the camera off and then back on again I get a new (second) entry for Kodak Co. Digital Camera under Places>Removable Media. These don't go away until I log off and back on.

These are not mounted and won't mount. If I try to mount them I get: 

"Unable to Mount Volume: Error initializing camera: -105: Unknown model. 

Ubuntu 9.04 32bit

---

### Post by causeitsme on 2009-05-02
Sorry. In my post above i stated that: "Also, if I turn the camera off and then back on again I get a new (second) entry for Kodak Co. Digital Camera under Places>Removable Media. These don't go away until I log off and back on."

This is not correct. What happens is that as soon as I turn the camera on, I get 2 'Kodak Co. Digital Camera' If I turn it off and on again, there will be another added, and will keep adding them as long as I turn the camera off and on.

---

### Post by Fenboy on 2009-05-06
Hi guys and gals.  First a big thanks to all you Linux gurus who keep helping us newbies out.  I've fixed several problems from searching or browsing the forums here.

I've just done encountered this problem after doing an on-line upgrade from 8.04 to 8.10 and I'm wondering if a clean install from CD would solve it.

I may be wrong but it seems that the problem probably lies in the options for removable media being moved from the <system> <properties> menu to the <edit> <properties> menu in Nautilus.  An upgrade leaves you with both sets of options which are probably conflicting.

I have deselected everything in the <system> <properties> menu and in the new Nautilus media options I've selected Photos: open gThumb Image Viewer.

The result is that when I plug in either my Canon G5 or 400d I first get this error 
"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"
but then gThumb opens connected and ready to import.

Obviously this is not a perfect solution but it is better than having to use a card reader or unmount the camera from Nautilus so that gThumb can connect.

I hope some of you find this useful.  It is working for me. now.

---

### Post by apostate on 2009-05-06
> **Fenboy said:**
> Hi guys and gals.  First a big thanks to all you Linux gurus who keep helping us newbies out.  I've fixed several problems from searching or browsing the forums here.

I've just done encountered this problem after doing an on-line upgrade from 8.04 to 8.10 and I'm wondering if a clean install from CD would solve it.

I may be wrong but it seems that the problem probably lies in the options for removable media being moved from the <system> <properties> menu to the <edit> <properties> menu in Nautilus.  An upgrade leaves you with both sets of options which are probably conflicting.

I have deselected everything in the <system> <properties> menu and in the new Nautilus media options I've selected Photos: open gThumb Image Viewer.

The result is that when I plug in either my Canon G5 or 400d I first get this error 
"DBus error org.freedesktop.DBus.Error.NoReply: Message did not receive a reply (timeout by message bus)"
but then gThumb opens connected and ready to import.

Obviously this is not a perfect solution but it is better than having to use a card reader or unmount the camera from Nautilus so that gThumb can connect.

I hope some of you find this useful.  It is working for me. now.

It is most likely this will work as designed again for you in Jaunty. It does for me.

---

### Post by oceania68 on 2009-06-18
I have same problem with my Kodak easyshare... it does work with linux the first time round but if you try to re accessing it, forget it... you have to not reboot but shut down completely then restart... And it is no good suggesting apps to use if the camera doesnt mount... U need to fix the mounting issue first, once that is done, Im sure digicam will work or even gthumb.... and everyone should forget F-spot all together, it has never worked... I have looked at many peoples issue with this, and it is definately a bug issue for Ubuntu, to be precise, a "re-accessing" bug issue. Launchpad closed it as an non bug issue... I think no one wants the headache of fixing it, in my opinion anyway.. And this is the type of reason why people still use windows... my kodak is a breeze on Xp... So first thing, do not suggest apps until the mounting problem is solved, thats the reason why the apps can't find the camera... it's not mounted. Cure the mounting problem and you'll have access... and I suggest removing F-spot from the Ubuntu, thats useless.. Digicam is good, Picassa for managing is good, and if you update, make sure the apps are compatible.. cheers ... remember.... Mounting Issues for USB devices...

---

### Post by ramjet_1953 on 2009-06-18
Off topic, slightly, but have you tried removing the memory card from the camera, mounting it into a USB adapter and reading it that way?

I know this doesn't solve interfacing to the camera, but you should at least be able to download the photos.

I do this anyway, with my Olympus 5050-Z as it downloads faster than plugging-in the camera.

Regards,
Roger :D

---

### Post by mgmiller on 2009-06-19
> I have same problem with my Kodak easyshare

Read this thread about the wonderful people at Kodak:
[http://ubuntuforums.org/showthread.php?t=843710&highlight=kodak](http://ubuntuforums.org/showthread.php?t=843710&highlight=kodak)

With Linux, you have to make sure that your hardware is properly supported.  I have several Canon digital cameras that are flawless with Ubuntu on every machine I use them on, as does my son.

The situation is analogous to buying hardware for a Mac.  You have to make sure it's supported.

If you have problems with your Kodak camera, you can try going through the bug reports and hopefully someone will fix it.  When the time comes to buy a new camera, let Kodak know why you aren't buying one of theirs and let the new company know why you are.

Bottom line, don't blame Ubuntu (or Linux for that matter) for this kind of problem, it's the hardware manufacturers fault.

---

### Post by bodhi.zazen on 2009-06-19
> **mgmiller said:**
> Read this thread about the wonderful people at Kodak:
[http://ubuntuforums.org/showthread.php?t=843710&highlight=kodak](http://ubuntuforums.org/showthread.php?t=843710&highlight=kodak)

With Linux, you have to make sure that your hardware is properly supported.  I have several Canon digital cameras that are flawless with Ubuntu on every machine I use them on, as does my son.

The situation is analogous to buying hardware for a Mac.  You have to make sure it's supported.

If you have problems with your Kodak camera, you can try going through the bug reports and hopefully someone will fix it.  When the time comes to buy a new camera, let Kodak know why you aren't buying one of theirs and let the new company know why you are.

Bottom line, don't blame Ubuntu (or Linux for that matter) for this kind of problem, it's the hardware manufacturers fault.

+1

I have returned several Kodac products. Pictures are a jpeg and there really is no need for linux drivers. The problem is Kodac built unnecessary drivers so that the pictures are not accessible from linux. Without these drivers Linux can mount flash drives and read jpeg without any problem.

Just say no to closed source, restrictive software, Kodac or otherwise. More so when alternates exist, as in the case of cameras. There are many outstanding non-Kodac digital cameras on the market.

---

### Post by epicoder on 2009-06-19
I have an easyshare, what worked for me was running gThumb as root.

---

### Post by retiefdv on 2009-12-07
I am very worried that this very obvious bug seems to get no attention from anybody at Canonical. It is an extreme embarrassment to try and convince a person to switch from Windows to Linux, but then to have to tell them that they should not expect to plug in a digital camera and see it working. This is something that did work in previous versions of Ubuntu. It works on all Windows PC's and laptops. One of the key things that most people do with their computers these days is to download pictures from their digital cameras to view, process and organise. The fact that a work-around is needed to do this basic task on Ubuntu is something that I feel must really get the urgent attention of the Ubuntu development team. What must I do to raise this bug to the level where it can get some attention?

---

### Post by mgmiller on 2009-12-07
> I am very worried that this very obvious bug seems to get no attention from anybody at Canonical.

That's not true.  This bug was addressed and fixed in subsequent versions.  As I recall, I even got it working in 8.10.

A person who is new to Ubuntu will not be installing version 8.10.  They will either use 8.04.3 which is the current LTS  version, which I use in my office every day, and which works perfectly with digital cameras, or they will install the current release, 9.10, which also works.  

8.10 is not available for download any more and reaches EOL (end of life) in 4 months.

Have you tried using your digital camera in a live CD for 8.04.3 or 9.10?

---

### Post by nymusicman on 2009-12-07
> **retiefdv said:**
> I am very worried that this very obvious bug seems to get no attention from anybody at Canonical. It is an extreme embarrassment to try and convince a person to switch from Windows to Linux, but then to have to tell them that they should not expect to plug in a digital camera and see it working. This is something that did work in previous versions of Ubuntu. It works on all Windows PC's and laptops. One of the key things that most people do with their computers these days is to download pictures from their digital cameras to view, process and organise. The fact that a work-around is needed to do this basic task on Ubuntu is something that I feel must really get the urgent attention of the Ubuntu development team. What must I do to raise this bug to the level where it can get some attention?

Not trying to be rude, but I have one word for you. Upgrade!

---

### Post by dert on 2010-03-27
> **clive littlewood said:**
> Hi

If the other suggestions don,t work try digicam from the repos.

I have used this with many cameras and it seems to work for me ootb.

Hope this helps

Clive    :)

Hey!  That was a neat suggestion!  I assumed my Canon Powershot A630 would work OOB, but it didn't.  Digicam went in and poof!  Camera worked.  Neat.  Thanks!

---

### Post by dert on 2010-03-27
> **nymusicman said:**
> Not trying to be rude, but I have one word for you. Upgrade!

I did upgrade.  I'm on 9.10 - Ubuntu Studio even, which is supposed to be a good media package.  I plugged in my camera (as noted above) and it DID NOT WORK.  So the point made by our dear reader is quite valid.  I did switch from Windows to Linux just a few days ago.  I assumed a basic task like plugging in my camera and seeing my pictures would be immediately available but it wasn't.  I had to download digicam or "digikam" as it's now spelled.  That worked.

I think the Ubuntu Core team needs to evaluate what is necessary and what is not with an out of box install now that they really are the distro people look to when considering a windows switch.  Ubuntu isn't just about Linux power or moderate users any more.  Most people downloading these days have NEVER seen linux before and try it, believing the hype that it's a good desktop system.  With respect, as I am a fairly knowledgeable person and am enjoying my new install, Ubuntu is not yet a good Desktop system for the novice user switching from Windows.  In Windows, everything EVERYTHING works immediately with some irritating exceptions like printers.  Plug in your camera..poof!  Wireless device...POOF!  Video Card...POOF..sort of (they work but the driver install with win is WAY WAY WAY easier than here)!  And if it doesn't, one click of an exe file makes it go.  SIMPLE!

I understand the complexity with Open Source.  The Canonical Team relies on 3rd party developers (many volunteer) to provide code.  That code may or may not meet the GPL sniff test but it might also be the only way Ubuntu would have these features out of box (like pesky MP3 for instance-that's a biggy!).  So what do you do?  They could go RedHat and start charging for installs.  Like have a paid for version with ALL the bells and whistles included and be able to hire permanent talent and legal people to make sure everything's cool.  They could still have the free version which is pretty good, but a struggle to get close to Windows.  My point is, they have choices facing them soon.  Not one trial user I know stayed with Ubuntu after their struggles.  Windows may suck...but at least it sucks easily.  Ubuntu may rule, but it's kingdom is pretty small...and may get smaller if they don't start thinking OUT OF THE BOX.  (hee hee hee...clever, eh?)

---

### Post by nymusicman on 2010-03-27
> **dert said:**
> I did upgrade.  I'm on 9.10 - Ubuntu Studio even, which is supposed to be a good media package.  I plugged in my camera (as noted above) and it DID NOT WORK.  So the point made by our dear reader is quite valid.  I did switch from Windows to Linux just a few days ago.  I assumed a basic task like plugging in my camera and seeing my pictures would be immediately available but it wasn't.  I had to download digicam or "digikam" as it's now spelled.  That worked.

I think the Ubuntu Core team needs to evaluate what is necessary and what is not with an out of box install now that they really are the distro people look to when considering a windows switch.  Ubuntu isn't just about Linux power or moderate users any more.  Most people downloading these days have NEVER seen linux before and try it, believing the hype that it's a good desktop system.  With respect, as I am a fairly knowledgeable person and am enjoying my new install, Ubuntu is not yet a good Desktop system for the novice user switching from Windows.  In Windows, everything EVERYTHING works immediately with some irritating exceptions like printers.  Plug in your camera..poof!  Wireless device...POOF!  Video Card...POOF..sort of (they work but the driver install with win is WAY WAY WAY easier than here)!  And if it doesn't, one click of an exe file makes it go.  SIMPLE!

I understand the complexity with Open Source.  The Canonical Team relies on 3rd party developers (many volunteer) to provide code.  That code may or may not meet the GPL sniff test but it might also be the only way Ubuntu would have these features out of box (like pesky MP3 for instance-that's a biggy!).  So what do you do?  They could go RedHat and start charging for installs.  Like have a paid for version with ALL the bells and whistles included and be able to hire permanent talent and legal people to make sure everything's cool.  They could still have the free version which is pretty good, but a struggle to get close to Windows.  My point is, they have choices facing them soon.  Not one trial user I know stayed with Ubuntu after their struggles.  Windows may suck...but at least it sucks easily.  Ubuntu may rule, but it's kingdom is pretty small...and may get smaller if they don't start thinking OUT OF THE BOX.  (hee hee hee...clever, eh?)

I see you point but only semi conceed. I think this world is expecting linux to do something that no other OS in the world is expected to do. And I believe it jumps through major hoops just to do it. 

Here is what I mean,

Windows: For years (at least with 98 - XP) Windows came pretty bare minimal. They did almost nothing out of the box. You bought an item, it came with the CD, you jumped through hoops figuring out if you bought the camera that gets plugged in with no drivers, the one that gets plugged in before the driver install or the one that gets plugged in afterward. Most annoying. Or you bought a device knew that name of the piece of software that would use that device out of the box, downloaded it and installed it. But Windows never held themselves responsible for making sure their OS worked with your device before you bought it.

Mac OS (any): Mac OS comes with everything right out of the box, but it's designed to work on their machines and their machines only. As a matter of fact, your not allowed to install it on any machine other than a Mac, although I am aware of people doing such.

Linux: Linux tries to assume what device you are going to buy, try there darndest to get it working before you buy it and provide the software to use it out of the box. On top of that they try to do that no matter what computer you install it on. Whether it be a Dell, HP, no-name or even Mac. I would say that Canonical does a fabulous job trying to determine what drives the users of Ubuntu out of the box. The only problem is they have a commitment to the Gnome Desktop Environment, which in my opinion has terrible photo management software. So we on the forums tell you to open synaptic and download an awesome program like Digikam (which is part of the KDE Desktop Environment). I would say just the fact that you can choose between a multitude of software to play with a camera is pretty good all by itself.

Anyway, I'm sorry about the rant, it just drives me a little crazy that when someone wants to edit photos on Windows they are willing to learn/find a program called Photoshop, they will go to the store, buy it, install it and use it. Yet if they want to edit photos in linux, they learn there is a program called GIMP to download through Synaptic and they complain that it wasn't installed out of the box. I know GIMP is a bad example because as of right now it is out of the box but in the next release it won't be and I guarantee the forums will be flooded with requests on how to edit photos in Ubuntu, why is it not out of the box, etc...

Okay so opinion war settled. Give Canonical some credit. Considering what they are up against with Mac and Windows, they are doing pretty good for themselves and the linux community.

---

### Post by chris.olive on 2010-04-01
I have the same problem with a Nikon Coolpix 990 and 9.10 it all worked fine [plug and play] in previous distros but now when I plug in I get no message to say the camera is connected but when I remove /turn off the camera I get* Unable to mount Nikon Nikon Digital Camera E990 Error initialising camera: -105: Unknown model,* Nikon won't help no support for Linux.
I have tried the web and Ubuntu Forums with no success, unfortunately my laptop does not have CF slot in the card reader.
The camera will not mount on the desktop [also 9.10]but will read cards in the built in card reader there, I could I know by a stand alone reader but would that work?
I know the camera is old [10 years] but it works fine and I do not really want to change it, any ideas out there?

Cards now work fine after I formatted them in the camera and re-shot, but still problems with the camera, it must be lack of drivers etc.

---

