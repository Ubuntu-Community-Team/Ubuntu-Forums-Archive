---
title: "Genius Look 316 Webcam with Linux Support Doesn't work"
date: 2008-01-09
forum: Philippine Team
---

### Post by wersdaluv on 2008-01-09
I just bought the Genius Look 316 webcam (since samhain referred it to me :P :D). I can't make it work. According to the box, it has linux support. I found a linux driver in the box but it's for kernel 2.5.6.

Anyway, the driver can be found here if you want to see it--> [http://www.genius-europe.com/en/produktdetail.php?ID2=35&ID=31&ID3=336](http://www.genius-europe.com/en/produktdetail.php?ID2=35&ID=31&ID3=336)

here is more info

```
lsusb
Bus 004 Device 001: ID 0000:0000  
Bus 003 Device 001: ID 0000:0000  
Bus 002 Device 002: ID 0ac8:305b Z-Star Microelectronics Corp. 
Bus 002 Device 001: ID 0000:0000  
Bus 001 Device 001: ID 0000:0000  

```

```
[  164.120000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (7)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (9)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (14)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (13)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (16)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (11)
[  166.480000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: VIDIOCMCAPTURE: invalid format (6)

```

```
lsmod | grep videodev
videodev               29312  2 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

```

---

### Post by perbiu on 2008-01-09
Yung Genius Look 312P ko gumagana na may Linux Support logo din, ganito yung lumabas sa Hardware Information.
/dev/video0 ay yun TV Tuner ko
/dev/video1 yun Webcam ko

[IMG]http://img2.freeimagehosting.net/uploads/1c90c67f4f.jpg[/IMG]

---

### Post by Samhain13 on 2008-01-09
Hala ka Wers! Baka naman sira yang nakuha mo? Heto lang naman ang sinunod ko eh:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

As far as I can remember, sa Gutsy wala ka nang kailangan i-install. May driver na para diyan. Baka nag-conflict lang yung ni-install mong driver dun sa gumaganang driver na kasama na sa Gutsy.

Heto nga lang yung sinasabi ng "lsmod | grep videodev" ko:
```

videodev               29568  1 gspca
v4l2_common            18560  1 videodev
v4l1_compat            15364  1 videodev

```

[edit]
Heto, picture: :guitar:

---

### Post by perbiu on 2008-01-09
Tanong ko lang kung bakit ayaw gumana? Saan software mo ba na subukan yung Webcam? Sa akin na try ko sa GyachI-E. Out of the Box gumana na.
:guitar:

---

### Post by wersdaluv on 2008-01-10
> **perbiu said:**
> Tanong ko lang kung bakit ayaw gumana? Saan software mo ba na subukan yung Webcam? Sa akin na try ko sa GyachI-E. Out of the Box gumana na.
:guitar:

VLC, Camorama, XawTV, Gyachi, Kopete, and Skype :D

---

### Post by wersdaluv on 2008-01-10
> **Samhain13 said:**
> Hala ka Wers! Baka naman sira yang nakuha mo? Heto lang naman ang sinunod ko eh:
[https://help.ubuntu.com/community/Webcam](https://help.ubuntu.com/community/Webcam)

As far as I can remember, sa Gutsy wala ka nang kailangan i-install. May driver na para diyan. Baka nag-conflict lang yung ni-install mong driver dun sa gumaganang driver na kasama na sa Gutsy.

Heto nga lang yung sinasabi ng "lsmod | grep videodev" ko:
```

videodev               29568  1 gspca
v4l2_common            18560  1 videodev
v4l1_compat            15364  1 videodev

```

[edit]
Heto, picture: :guitar:

Onga parekoy! Magkaiba tayong **lsmod | grep videodev**. Tsk tsk tsk

Bakit kaya? Mmmmmm...

---

### Post by wersdaluv on 2008-01-10
> **perbiu said:**
> Yung Genius Look 312P ko gumagana na may Linux Support logo din, ganito yung lumabas sa Hardware Information.
/dev/video0 ay yun TV Tuner ko
/dev/video1 yun Webcam ko

[IMG]http://img2.freeimagehosting.net/uploads/1c90c67f4f.jpg[/IMG]

Pre, ano ang lsmod | grep videodev at dmesg mo? 

:KS

---

### Post by wersdaluv on 2008-01-10
Samhain, ano rin pala dmesg mo? :)

---

### Post by Samhain13 on 2008-01-10
Ano sa dmesg ang kailangan mo? Ang haba eh.

Heto, baka relevant...

```

arielle-cruz@memphis:~$ dmesg | grep camera
[   50.804805] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-rt/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 

```

---

### Post by perbiu on 2008-01-10
```
[] usb 2-2: new full speed USB device using uhci_hcd and address 2
[] usb 2-2: configuration #1 chosen from 1 choice
[] zc0301: V4L2 driver for ZC0301[P] Image Processor and Control Chip v1:1.07
[] usb 2-2: ZC0301[P] Image Processor and Control Chip detected (vid/pid 0x0AC8:0x301B)
[] usb 2-2: No supported image sensor detected
[] usbcore: registered new interface driver zc0301
[] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[] usbcore: registered new interface driver gspca
[] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

```

```
videodev               29312  4 gspca,zc0301,bttv
v4l2_common            18432  4 zc0301,tuner,bttv,videodev
compat_ioctl32          2304  2 zc0301,bttv

```

Yung zc0301 yung camera.

---

### Post by wersdaluv on 2008-01-12
For this, I reformatted, but it still doesn't work.

I just installed gspca-source. 

My dmesg looks better now
```
[ 5198.356000] Linux video capture interface: v2.00
[ 5198.636000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: USB SPCA5XX camera found.(ZC3XX) 
[ 5201.228000] usbcore: registered new interface driver gspca
[ 5201.228000] /build/buildd/linux-ubuntu-modules-2.6.22-2.6.22/debian/build/build-generic/media/gspcav1/gspca_core.c: gspca driver 01.00.12 registered

```

My new lsmod | grep videodev is 
```
videodev               29312  2 gspca
v4l2_common            18432  1 videodev
v4l1_compat            15364  1 videodev

```

Whenever I try to run it on Gyachi, no error message comes out anymore but the webcam window just hangs and never shows the webcam's video.

I ran XawTV and what happened was
```
:~$ xawtv
This is xawtv-3.95.dfsg.1, running on Linux/i686 (2.6.22-14-generic)
xinerama 0: 1024x768+0+0
can't open /dev/video0: Device or resource busy
v4l-conf had some trouble, trying to continue anyway
v4l2: open /dev/video0: Device or resource busy
v4l2: open /dev/video0: Device or resource busy
v4l: open /dev/video0: Device or resource busy
no video grabber device available
```

On VLC, 
```
:~$ vlc
VLC media player 0.8.6c Janus
[00000292] v4l demuxer error: cannot open device (Device or resource busy
```

As for Camorama, a window popped out with an error message. I attached the screenshot.

---

### Post by Samhain13 on 2008-01-12
Na-test mo ba yung camera kung gumagana sa ibang computer tulad ng napag-usapan natin nila Jucato sa chat nung isang gabi?

---

### Post by wersdaluv on 2008-01-12
> **Samhain13 said:**
> Na-test mo ba yung camera kung gumagana sa ibang computer tulad ng napag-usapan natin nila Jucato sa chat nung isang gabi?

Oh yes. It worked perfectly on Windows XP.

---

### Post by perbiu on 2008-01-12
Yung pinost ko na screenshot, paki puntahan niyo lang yung Hardware Information, pero sa screenshot mo parang Kubuntu gamit niyo, at tignan kung kung ano yung Advance Tab nang Webcam niyo, baka kasi hindi /dev/video0 yung Webcam. Kung minsan kasi baka /dev/video lang o /dev/video1 /dev/vid0. Nagreformat pa kayo? puede naman Live CD lang gamitin. Subukan niyo subukan sa Live CD ng Ubuntu Gnome.
:guitar:

---

### Post by wersdaluv on 2008-01-12
> **perbiu said:**
> Yung pinost ko na screenshot, paki puntahan niyo lang yung Hardware Information, pero sa screenshot mo parang Kubuntu gamit niyo, at tignan kung kung ano yung Advance Tab nang Webcam niyo, baka kasi hindi /dev/video0 yung Webcam. Kung minsan kasi baka /dev/video lang o /dev/video1 /dev/vid0. Nagreformat pa kayo? puede naman Live CD lang gamitin. Subukan niyo subukan sa Live CD ng Ubuntu Gnome.
:guitar:

Thank you so much, perbiu!

I'm on GNOME, actually. I tried that and saw that my webcam really is using /dev/video0. I had to reformat because the live CD doesn't have vlc, camorama, etc. Also, I can't install gspca-source there.

:KS

---

### Post by Samhain13 on 2008-01-13
> Kung minsan kasi baka /dev/video lang o /dev/video1 /dev/vid0.

Oo nga naman! Salamat sa pagpaalala.
Anyway, in my case, it's **/dev/video0**.

Hay, ang laking topak ng makina mo Wers ah. Ano nga kaya ang problema... talaga bang kailangan mong i-install yung gspca-source?

{edit]
To test using the Live CD, gamitin mo Ekiga Softphone. Cancel mo lang yung account/start-up wizard. Tapos dun sa bandang kaliwa, piliin mo yung camera view tulad nang na sa screenshot. Puwede mo pang galawin yung Brighness, Contrast, etc.

---

### Post by wersdaluv on 2008-01-13
Good idea! I'm going to boot on the live cd.

By the way, I tried my webcam on ekiga and... see the attached image.

Nga pala, kaya english gamit ko para in case may banyagang makabasa nito, maintindihan at baka matulungan ako. :D

---

### Post by Samhain13 on 2008-01-13
Ok, "check your permissions" daw. Kasama ba yung user mo sa Video group? Hindi ko maalala yung command kung papano magdagdag ng isang user sa isang group o kung papano magdagdag ng group kung wala pa yung Video group. Pero hanapin mo na lang, pasensya na at nabubuhay lang ako sa kodigo. :)

[edit]
Pero dahil mabait ako, heto pala yun:

```

$ groups USERNAME

```

Dapat may kasamang "video" diyan, tulad nito:

>  arielle-cruz : arielle-cruz adm dialout fax cdrom floppy tape audio dip **video** plugdev scanner lpadmin admin netdev powerdev

Puwede mo rin malaman kung sino-sino na ang laman ng isang group o kung meron na bang ganoong group:

```

arielle-cruz@memphis:~$ **grep video /etc/group**
video:x:44:arielle-cruz

```

Anyway, heto baka mas makatulong: [http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/](http://www.cyberciti.biz/faq/howto-linux-add-user-to-group/)

---

### Post by wersdaluv on 2008-01-18
Mukhang ipapamigay ko na lang ang camera ko. ahehehe

Thanks anyway, guys! Maraming salamat talaga!

:KS

---

### Post by Samhain13 on 2008-01-19
Hindi mo na sinubukan yung groups?
Anyway, nakakalungkot naman. Pero ika nga ng Orient Pearl, "huwag mong isuko..." :)

---

### Post by perbiu on 2008-01-20
Tignan mo yung BIOS mo sa may bandang PnP Operating System kung meron ka at Enable mo o Disable. Pag ayaw parin subukan mo ibang Distro, Mint o Fedora. Pag ayaw parin ito yung address ko..
:guitar:

---

### Post by wersdaluv on 2008-01-21
> **perbiu said:**
> Tignan mo yung BIOS mo sa may bandang PnP Operating System kung meron ka at Enable mo o Disable. Pag ayaw parin subukan mo ibang Distro, Mint o Fedora. Pag ayaw parin ito yung address ko..
:guitar:

San yang PnP operating system?

Btw, naka-irqpoll boot parameter ako dahil pag di ako naka-ganon, walang usb device na gumagana. Connected kaya yon?

Maraming salamat.

---

