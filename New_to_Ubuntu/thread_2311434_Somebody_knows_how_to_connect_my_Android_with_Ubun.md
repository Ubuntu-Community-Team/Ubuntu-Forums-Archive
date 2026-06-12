---
title: "Somebody knows how to connect my Android with Ubuntu?"
date: 2016-01-27
forum: New to Ubuntu
---

### Post by omer8 on 2016-01-27
Hello friends,

I'll be happy if somebody explain to me how to connect to my Ubuntu PC and Android (Nexus 5).

Thanks.

---

### Post by Lars_Roth on 2016-01-27
I have the same problem. I have solved it by downloading an app.= Ftp server. Then I have an FTP addon in Firefox and transfer between. It works very well.

---

### Post by ajgreeny on 2016-01-27
Here you go.
[http://ubuntuforums.org/showthread.php?t=2226702](http://ubuntuforums.org/showthread.php?t=2226702)

It's a long thread now, but it has worked for all the Android tabs or phones that I have tried it with.

---

### Post by cwmoser on 2016-01-27
I plug my USB cable into my Android phone (OnePlus One) and an icon pops up on the Desktop.
The way I have my phone set up, I have to go to its Notification screen and select to make
the connection for File Sharing rather than Battery Charging.  Then, Ubuntu pops up a Nautilus
file explorer window.

I do have this setting on my phone:
Settings -> Developer Options -> Select USB Configuration = MTP

---

### Post by him610 on 2016-01-27
I have a Moto-X with Android 5.1 which connects to a USB port with the supplied USB cable. The files manager opens displaying the Internal Storage folder of the Moto-X. Nothing more needs to be done.
@cwmoser - message on phone indicates it opens as Media device (MTP). The other option is Camera (PTP).

Cheers

---

### Post by SeijiSensei on 2016-01-28
Some network options:

**Share selected directories from Ubuntu**: Samba on Ubuntu with AndSMB on Android
**Transfer files to/from phone**: Any browser on Ubuntu with Wifi File Transfer Pro ($) on Android
**Stream audio/video from Ubuntu**: Minidlna on Ubuntu with BubbleUPnP on Android (+MXPlayer for video)

NFS isn't an option unless you root the phone.  However CIFS ("Windows Networking") works with Samba on Ubuntu and AndSMB as the client on the phone.  For $3 you can install Wifi File Transfer Pro which runs a little web server on port 1234 of the phone. You can interact with the phone's directories from Ubuntu (or anywhere else) with a browser.  Buying the "Pro" version removes a limit on the size of transferred files.

Minidlna is an easy-to-configure DLNA server that runs on Ubuntu and lets you stream media to your phone via the BubbleUPnP client app.  MXPlayer is a fine video player that handles all sorts of files including ones with ASS subtitles and FLAC audio.

I usually just connect with a USB cable, but I do run minidlna so I can stream audio and video to other devices in the house.  I also have a home office server that runs Samba, and I can connect to that with AndSMB.  I used Wifi File Transfer Pro back when USB connections with Android were not yet stable in Ubuntu; I rarely use it nowadays.

---

### Post by mastablasta on 2016-01-29
strange. is this to do with newer version of android?

We just plugged it in (Kubuntu) and accessed it like any other external media. 

also there is also owncloud or seafile for sync...:P

---

### Post by mcduck on 2016-01-29
> **mastablasta said:**
> strange. is this to do with newer version of android?

We just plugged it in (Kubuntu) and accessed it like any other external media. 

also there is also owncloud or seafile for sync...:P

Must be something else. I have a Nexus 5 and all I do is plug the cable in the phone & laptop, and then change the connection mode from the phone's notification popup to File Transfers(MTP). (I have the default setting on charge only, changing it to file transfers by default would of course mean you'd only need to plug in the cable...)

Edit which version & variant of Ubuntu are you using? While the latest versions can handle MTP by default, at least if you are using Gnome or Unity desktop (with Nautilus as your file manager), other desktops & file managers and older Ubuntu versions might not support it.

---

### Post by centaurusa on 2016-01-30
> **omer8 said:**
> 
I'll be happy if somebody explain to me how to connect to my Ubuntu PC and Android (Nexus 5).


If the need is to transfer files between the two devices, one way to do this is with the Software Data Cable app.  See: [https://linuxnorth.wordpress.com/2012/04/23/a100-to-ubuntu-file-transfer/](https://linuxnorth.wordpress.com/2012/04/23/a100-to-ubuntu-file-transfer/)

---

### Post by mc4man on 2016-01-30
> **mastablasta said:**
> strange. is this to do with newer version of android?

We just plugged it in (Kubuntu) and accessed it like any other external media. 

also there is also owncloud or seafile for sync...:P

Marshmallow now defaults to USB charging. After plugging in you get a notification drop down for mtp, etc. 
(though certainly possible that the notification could go missing

---

