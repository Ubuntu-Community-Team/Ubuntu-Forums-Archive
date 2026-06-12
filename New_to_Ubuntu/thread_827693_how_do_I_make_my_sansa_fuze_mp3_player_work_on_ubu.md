---
title: "how do I make my sansa fuze mp3 player work on ubuntu?"
date: 2008-06-13
forum: New to Ubuntu
---

### Post by orwellus on 2008-06-13
Hello:

I have Ubuntu Feisty. Today, I bought my first mp3 player at Wal Mart. It is a sansa fuze 2GB flash player. Here is a link for the product:

[http://electronics.pricegrabber.com/mp3-players/m/66194542/](http://electronics.pricegrabber.com/mp3-players/m/66194542/)

As this is my first mp3 player, I'm have a little getting it to work, mainly because I'm not exactly sure what to do. I want to use it play videos. I plugged in the usb cable, the mp3 mounted and showed up on my desktop. I downloaded a video, went into the sansa thing on my desktop, and pasted the video in the video folder. When I tried to play it on my mp3 player, no video. 

So can any give my some instructions on how to make the mp3 player work using ubuntu? I'm clearly not doing something right. 

Thanks

---

### Post by aysiu on 2008-06-13
I have a Sansa Clip (it doesn't play video) so I can only guess, but in the player, have you tried changing the USB mode to MSC (as opposed to MTP or Autodetect)?

---

### Post by orwellus on 2008-06-14
Thanks for the reply. Yes I did set the mp3 player to setting you suggested. The player mounts okay in ubuntu, and I can get audio and pictures to come up, alright, just by using the drag and drop method into the sansa fuze folder(s). But, the video is still not working. I asked at the sansa fuze website, and they said I need to have the sansa media converter installed on my desktop, which only works with Windows XP. I tried to install the sansa media converter, through crossover office, but no success. It installs fine, but the program will not open. I'll keep searching for a work around, though.

---

### Post by aysiu on 2008-06-14
Sorry I can't be more help. Hopefully someone with a Sansa Fuze can step in here.

---

### Post by orwellus on 2008-06-15
Okay, well I have some good/bad news.

The good news, I was able to make videos show in my fuze player using a program called iriverter.

The bad news is iriverter converts the videos into a .avi format, which my fuze player does not support. (It only supports mp4 for videos). I did try to download a mp4 file, and just do a drag and drop into the fuze video folder, but that didn't work either. I guess the video file needs to converter some how.

Anyone know of a program similar to iriverter that can converter videos into the mp4 format?

---

### Post by Kronie on 2008-06-15
all i can think is alltoavi which is windows-based program which might launch under wine(it converts stuff from dvd, avi..etc to mp4).. and it automatically converts videos for ipod (ur player has same screen except its scaled a lil). it has presets for it.. let me see if i can find it in my mess

---

### Post by orwellus on 2008-06-15
I did a google search for that program you recommended, and it looks like it is similiar to iriverter. But, like iriverter, it just converts video files to .avi

Darn it.

---

### Post by cariboo on 2008-06-16
You can use avidemux to convert your video files to mpeg4. It is available in the repositories and you can use synaptic to install it.

Jim

---

### Post by orwellus on 2008-06-16
I installed avidemux, but it's a little complicated for me. It looks like avidemux is maybe a movie maker, and I can't figure out how to convert anything to mp4.

Is there just a simple program, like iriverter, for mp4 conversion?

---

### Post by cariboo on 2008-06-16
Avidemux looks complicated, but it is pretty easy to use. Just open the video you want to convert and then just leave the default settings for video and audio. In the format button click it and select mp4, next click the save icon, give it a name with an mp4 extension and your done.

Jim

---

### Post by Kronie on 2008-06-16
well, i did convert videos with winavi for my psp... and psp is on mpg4 too. but it doesnt seem to be wine-friendly..

---

### Post by orwellus on 2008-06-16
I'm still having issues trying to convert videos through avidemux. I tried to convert a .wmv video clip. I opened the clip in avidmux, and a little video box appeared in avidemux. I didn't change anything on the side (I left the video and audio options set as copy). I clicked on the format tape, changed it to MP4, hit save, and it asked me to name the video file. I tried it two ways: First I saved it name of file (so for example I named the file "clip"). Then I tried to save it by adding .mp4 at the end (so "clip.mp4). Nether way worked. My mp3 player does not recognize the file. I tried to play the converter video file in both mplayer and vlc on my laptap, and it did not play. So I am obviously not doing something right. Just for a test, I tried to open a mp4 video clip, I download, into avidemux, and avidemux immediately shut down. I have the same problem when trying to play mp4 files using vlc, instead of playing the mp4 file, it immediately shuts down. So maybe I'm missing a codec. MP4 files do play in mplayer, though. So I don't know.

---

### Post by orwellus on 2008-06-18
Well, I did a clean install of Gutsy, and tried Winff, ConvertIt, avidemux, but still no luck. I can't get the sansa player to recognize the video files. I have ffmpeg installed, and I'm pretty sure I have all the codecs, as well as win32. Still, having the problem opening mp4 videos in vlc, too. So maybe I am missing something.

---

### Post by orwellus on 2008-06-19
Well still not having much luck getting videos to show up on my player. Not sure if anyone is even looking at this post, but if you are, I found some specs for a video file at this site:

[http://www.anythingbutipod.com/forum/showthread.php?t=27460](http://www.anythingbutipod.com/forum/showthread.php?t=27460)

Maybe somebody could create a script from that, or point me in the right direction as to what I need to do to make a video converter convert the video file for my player.

Currently, I have convertIT installed on my system.

---

### Post by evan.rotert on 2008-06-26
Ok, I have a more basic problem.  I just got my 8GB Fuze today, and I've been unable to make Ubuntu see it in any mode (Autodetect, MTP, or MSC).  It doesn't appear to be charging as it's plugged in to my computer, either.  I'm running a fully-updated Hardy Heron system.  Help!  Is there anything I need to do differently to get my computer to see this player?

~Evan

---

### Post by highfructose327 on 2008-07-01
evan.rotert I have the same problem when I plug in my Sansa Fuze so I run  > sudo modprobe -r ehci_hcd this removes the module and my Fuze loads, but; trasnfers are slooooow so than if I run  > sudo modprobe  ehci_hcd
 
 it loads the module and reloads my Fuze and transfer speeds are decent it is an ugly work around , but ;it works.  hope it helps.


I recently tried plugging in my sansa fuze and then unplugging and plugging it back in very quickly and it loaded without having to remove any modules. My only concern would be possibly damaging the player or the usb port so I will probably continue to use the first method.

---

### Post by blierp on 2008-07-03
thanks highfructose327, i already figured out i needed to unload ehci_hcd but never tried to reactivate it :) It is a bit of a hassle but at least i can transfer mp3's at usb 2.0 speed again instead of the painfully slow 1.0 speed.

---

### Post by DarKnyht on 2008-07-16
> **orwellus said:**
> Well, I did a clean install of Gutsy, and tried Winff, ConvertIt, avidemux, but still no luck. I can't get the sansa player to recognize the video files. I have ffmpeg installed, and I'm pretty sure I have all the codecs, as well as win32. Still, having the problem opening mp4 videos in vlc, too. So maybe I am missing something.

They have a special application for the Fuze that is Windows only to convert the videos.  I am guessing that it is a special form of mpeg-4 file.

---

### Post by Commander_Bob on 2008-07-24
> **highfructose327 said:**
> evan.rotert I have the same problem when I plug in my Sansa Fuze so I run  this removes the module and my Fuze loads, but; trasnfers are slooooow so than if I run   it loads the module and reloads my Fuze and transfer speeds are decent it is an ugly work around , but ;it works.  hope it helps.


I recently tried plugging in my sansa fuze and then unplugging and plugging it back in very quickly and it loaded without having to remove any modules. My only concern would be possibly damaging the player or the usb port so I will probably continue to use the first method.

I just got my Sansa Fuze and have the same problem. Your work around works but it causes my keyboard to go crazy for a little and all the USB stuff to start over, a lot of windows open. Is there any better ways now?

Thanks,
Justin

---

### Post by halitech on 2008-07-24
you could try MPxConverter to change them to mp4. I use it with my Camnex to convert avi to amv (format it uses) but I'm pretty sure mp4 is an option as well

---

### Post by Commander_Bob on 2008-07-25
I have a new workaround that works for me. If I use the USB port on the front of my computer then all I have to do to get the Fuze recognized is type lsusb.

---

### Post by spicifer on 2008-08-02
I've been experimenting quite a lot with mencoder, trying to get videos that work with Sansa Fuze. As far as I can tell, Sansa Fuze requires a very specific format for the AVI container it uses and I've been unable to get mencoder (or any other program) to reproduce it. You can read about [my experiments here]("http://spicifer.blogspot.com/2008/08/video-on-sandisk-sansa-fuze.html"), along with some further information about the video format.

I also wrote about [my other experiments with the Fuze]("http://spicifer.blogspot.com/2008/07/sandisk-sansa-fuze-8gb-on-ubuntu-804.html"), with playlists and such, if anyone's interested.

---

### Post by ale63 on 2008-08-05
> **aysiu said:**
> I have a Sansa Clip (it doesn't play video) so I can only guess, but in the player, have you tried changing the USB mode to MSC (as opposed to MTP or Autodetect)?

Hi, with sudo mtp-detect I got the following with my samsung yp-s3 connected...any suggestions? Thanks

libmtp version: 0.2.6.1

Attempting to connect device(s)
Device 1 (VID=04e8 and PID=5091) is UNKNOWN.
Please report this VID/PID and the device model to the libmtp development team
PTP: Opening session
Detect: Successfully connected 1 devices
USB low-level info:
   Using kernel interface "usbfs"
   bcdUSB: 512
   bDeviceClass: 0
   bDeviceSubClass: 0
   bDeviceProtocol: 0
   idVendor: 04e8
   idProduct: 5091
   IN endpoint maxpacket: 512 bytes
   OUT endpoint maxpacket: 512 bytes
   Device flags: 0x00000000
Microsoft device descriptor 0xee:
	0000: 1203 4d00 5300 4600 5400 3100 3000 3000	..M.S.F.T.1.0.0.
	0010: 0400                                   	..
Microsoft device response to control message 1, CMD 0x04:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000 0403 0904 3a03 5300	............:.S.
	0030: 6100 6d00 7300 7500 6e00 6700 2000 4500	a.m.s.u.n.g. .E.
	0040: 6c00 6500 6300 7400 7200 6f00 6e00 6900	l.e.c.t.r.o.n.i.
	0050: 6300 7300 2000 4300 6f00 2e00 2c00 4c00	c.s. .C.o...,.L.
	0060: 7400 6400 2e00 0803 5300 3300 0000 2203	t.d.....S.3...".
	0070: 6300 3500 3300 6600 3400 3600 3100 3800	c.5.3.f.4.6.1.8.
	0080: 3000 3000 3000 3000 3000 3000 6600 3500	0.0.0.0.0.0.f.5.
	0090: 0008 73f7 1b08 73f7 1f08 73f7 5908 73f7	..s...s...s.Y.s.
	00a0: 6100 0000 0000 0000 0200 0000 0022 0100	a............"..
	00b0: 0022 0200 0000 0000 0000 0000 8000 0000	."..............
	00c0: 0000 0000 0000 0000 0000 0000 0000 0000	................
	00d0: 0000 0000 0000 0000 0100 0002 0000 781f	..............x.
	00e0: bf00 781f be00 0000 0008 0e25 ac08 0e2b	..x........%...+
	00f0: 7008 0e2e 7c08 0e30 1808 0e32 ac08 0e35	p...|..0...2...5
	0100: 0c08 0e35 a408 0e36 7808 0e37 8c08 0e39	...5...6x..7...9
	0110: 1c08 0e3a 9c00 0000 0000 0000 0000 0000	...:............
	0120: 0000 0000 0000 0000 0022 0100 0022 0200	........."..."..
	0130: 00ff ffff ffff ffff ff00 0000 040b ec00	................
	0140: 000b ec00 0005 f600 0005 f600 0002 fb00	................
	0150: 0000 2462 0300 11f9 0300 1ad2 0300 2462	..$b..........$b
	0160: 0200 24f9 0300 0cd2 0100 2462 0100 2172	..$.......$b..!r
	0170: 0100 11f9 0100 2195 0100 1ad2 0100 2c8a	......!.......,.
	0180: 0100 26af 0100 3c78 0100 2eaa 0100 24f9	..&...<x......$.
	0190: 0100 24f9 0100 37ae 0100 2edd 0100 36c7	..$...7.......6.
	01a0: 0100 36d2 0100 3677 0000 0009 9900 000b	..6...6w........
	01b0: f600 000e f300 0013 b500 0016 b100 001d	................
	01c0: e600 0027 3b00 0029 9f00 002f d800 0035	...';..).../...5
	01d0: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	01e0: be00 0053 7c00 0057 6400 005a c400 0060	...S|..Wd..Z...`
	01f0: 3500 0066 1c00 006b 8e00 0071 7500 007d	5..f...k...qu..}
	0200: fe00 0009 da00 000b f600 000e f300 0013	................
	0210: b500 0017 4e00 001d e600 0027 3b00 0029	....N......';..)
	0220: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	0230: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	0240: b400 005f b000 0065 6d00 0066 1c00 006b	..._...em..f...k
	0250: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	0260: f600 000e f300 0013 b500 0017 ec00 001e	................
	0270: f900 0028 a300 0029 9f00 002f d800 0035	...(...).../...5
	0280: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	0290: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
	02a0: 6d00 006b a600 0071 6300 0077 9c00 0084	m..k...qc..w....
	02b0: 1000 0009 da00 000b f600 000e f300 0013	................
	02c0: b500 0016 b100 001d e600 0027 3b00 0029	...........';..)
	02d0: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	02e0: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	02f0: b400 005f b000 0062 cf00 0066 1c00 006b	..._...b...f...k
	0300: 8e00 0071 7500 007d fe00 000a dc00 000c	...qu..}........
	0310: 9400 000e f300 0015 b800 0017 ec00 0022	..............."
	0320: 6400 002b 3a00 002d dd00 0033 b600 0038	d..+:..-...3...8
	0330: 9900 003e e400 0045 2d00 004a 1800 004d	...>...E-..J...M
	0340: be00 0056 7c00 0059 b400 0063 2000 0069	...V|..Y...c ..i
	0350: 1200 006f 8400 0075 7600 007b e800 008b	...o...uv..{....
	0360: 3900 0009 da00 000b f600 000e f300 0013	9...............
	0370: b500 0016 b100 001e f900 0029 4100 002b	...........)A..+
	0380: 1e00 0031 9000 0037 c100 003b ce00 0041	...1...7...;...A
	0390: c800 0047 8600 004d be00 0053 7c00 0057	...G...M...S|..W
	03a0: 6400 005a c400 0060 3500 0066 1c00 006b	d..Z...`5..f...k
	03b0: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	03c0: f600 000e f300 0013 b500 0017 ec00 001e	................
	03d0: f900 0029 4100 002b c500 0031 9000 0037	...)A..+...1...7
	03e0: c100 003d f400 0044 2500 0047 8600 004d	...=...D%..G...M
	03f0: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
Microsoft device response to control message 2, CMD 0x04:
	0000: 2800 0000 0001 0400 0100 0000 0000 0000	(...............
	0010: 0001 4d54 5000 0000 0000 0000 0000 0000	..MTP...........
	0020: 0000 0000 0000 0000 0403 0904 3a03 5300	............:.S.
	0030: 6100 6d00 7300 7500 6e00 6700 2000 4500	a.m.s.u.n.g. .E.
	0040: 6c00 6500 6300 7400 7200 6f00 6e00 6900	l.e.c.t.r.o.n.i.
	0050: 6300 7300 2000 4300 6f00 2e00 2c00 4c00	c.s. .C.o...,.L.
	0060: 7400 6400 2e00 0803 5300 3300 0000 2203	t.d.....S.3...".
	0070: 6300 3500 3300 6600 3400 3600 3100 3800	c.5.3.f.4.6.1.8.
	0080: 3000 3000 3000 3000 3000 3000 6600 3500	0.0.0.0.0.0.f.5.
	0090: 0008 73f7 1b08 73f7 1f08 73f7 5908 73f7	..s...s...s.Y.s.
	00a0: 6100 0000 0000 0000 0200 0000 0022 0100	a............"..
	00b0: 0022 0200 0000 0000 0000 0000 8000 0000	."..............
	00c0: 0000 0000 0000 0000 0000 0000 0000 0000	................
	00d0: 0000 0000 0000 0000 0100 0002 0000 781f	..............x.
	00e0: bf00 781f be00 0000 0008 0e25 ac08 0e2b	..x........%...+
	00f0: 7008 0e2e 7c08 0e30 1808 0e32 ac08 0e35	p...|..0...2...5
	0100: 0c08 0e35 a408 0e36 7808 0e37 8c08 0e39	...5...6x..7...9
	0110: 1c08 0e3a 9c00 0000 0000 0000 0000 0000	...:............
	0120: 0000 0000 0000 0000 0022 0100 0022 0200	........."..."..
	0130: 00ff ffff ffff ffff ff00 0000 040b ec00	................
	0140: 000b ec00 0005 f600 0005 f600 0002 fb00	................
	0150: 0000 2462 0300 11f9 0300 1ad2 0300 2462	..$b..........$b
	0160: 0200 24f9 0300 0cd2 0100 2462 0100 2172	..$.......$b..!r
	0170: 0100 11f9 0100 2195 0100 1ad2 0100 2c8a	......!.......,.
	0180: 0100 26af 0100 3c78 0100 2eaa 0100 24f9	..&...<x......$.
	0190: 0100 24f9 0100 37ae 0100 2edd 0100 36c7	..$...7.......6.
	01a0: 0100 36d2 0100 3677 0000 0009 9900 000b	..6...6w........
	01b0: f600 000e f300 0013 b500 0016 b100 001d	................
	01c0: e600 0027 3b00 0029 9f00 002f d800 0035	...';..).../...5
	01d0: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	01e0: be00 0053 7c00 0057 6400 005a c400 0060	...S|..Wd..Z...`
	01f0: 3500 0066 1c00 006b 8e00 0071 7500 007d	5..f...k...qu..}
	0200: fe00 0009 da00 000b f600 000e f300 0013	................
	0210: b500 0017 4e00 001d e600 0027 3b00 0029	....N......';..)
	0220: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	0230: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	0240: b400 005f b000 0065 6d00 0066 1c00 006b	..._...em..f...k
	0250: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	0260: f600 000e f300 0013 b500 0017 ec00 001e	................
	0270: f900 0028 a300 0029 9f00 002f d800 0035	...(...).../...5
	0280: d200 003b ce00 0041 c800 0047 8600 004d	...;...A...G...M
	0290: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
	02a0: 6d00 006b a600 0071 6300 0077 9c00 0084	m..k...qc..w....
	02b0: 1000 0009 da00 000b f600 000e f300 0013	................
	02c0: b500 0016 b100 001d e600 0027 3b00 0029	...........';..)
	02d0: 9f00 002f d800 0035 d200 003b ce00 0041	.../...5...;...A
	02e0: c800 0047 8600 004d be00 0053 7c00 0059	...G...M...S|..Y
	02f0: b400 005f b000 0062 cf00 0066 1c00 006b	..._...b...f...k
	0300: 8e00 0071 7500 007d fe00 000a dc00 000c	...qu..}........
	0310: 9400 000e f300 0015 b800 0017 ec00 0022	..............."
	0320: 6400 002b 3a00 002d dd00 0033 b600 0038	d..+:..-...3...8
	0330: 9900 003e e400 0045 2d00 004a 1800 004d	...>...E-..J...M
	0340: be00 0056 7c00 0059 b400 0063 2000 0069	...V|..Y...c ..i
	0350: 1200 006f 8400 0075 7600 007b e800 008b	...o...uv..{....
	0360: 3900 0009 da00 000b f600 000e f300 0013	9...............
	0370: b500 0016 b100 001e f900 0029 4100 002b	...........)A..+
	0380: 1e00 0031 9000 0037 c100 003b ce00 0041	...1...7...;...A
	0390: c800 0047 8600 004d be00 0053 7c00 0057	...G...M...S|..W
	03a0: 6400 005a c400 0060 3500 0066 1c00 006b	d..Z...`5..f...k
	03b0: 8e00 0071 7500 007d fe00 0009 da00 000b	...qu..}........
	03c0: f600 000e f300 0013 b500 0017 ec00 001e	................
	03d0: f900 0029 4100 002b c500 0031 9000 0037	...)A..+...1...7
	03e0: c100 003d f400 0044 2500 0047 8600 004d	...=...D%..G...M
	03f0: be00 0053 7c00 0059 b400 005f b000 0065	...S|..Y..._...e
Device info:
   Manufacturer: Samsung Electronics Co.,Ltd.
   Model: S3
   Device version: V1.01
   Serial number: C53F4618000000F5
   Vendor extension ID: 0x00000006
   Vendor extension description: microsoft.com: 1.0; microsoft.com/WMPPD: 10.0; microsoft.com/WMDRMPD: 10.1microsoft.com/WMPPD: 11.,; 
   Detected object size: 64 bits
Supported operations:
   1001: get device info
   1002: Open session
   1003: Close session
   1004: Get storage IDs
   1005: Get storage info
   1006: Get number of objects
   1007: Get object handles
   1008: Get object info
   1009: Get object
   101b: Get partial object
   100b: Delete object
   100c: Send object info
   100d: Send object
   100f: Format storage
   1011: Self test device
   1014: Get device property description
   1015: Get device property value
   1016: Set device property value
   9801: Get object properties supported
   9802: Get object property description
   9803: Get object property value
   9804: Set object property value
   9805: Get object property list
   9806: Set object property list
   9810: Get object references
   9811: Set object references
   9101: Get secure time challenge
   9102: Get secure time response
   9103: Set license response
   9104: Get sync list
   9105: Send meter challenge query
   9106: Get meter challenge
   9107: Get meter response
   9108: Clean data store
   9109: Get license state
   910a: Send WMDRM-PD Command
   9201: Report Added/Deleted Items
Events supported:
   None.
Device Properties Supported:
   0xd402: Friendly Device Name
   0xd101: Secure Time
   0xd102: Device Certificate
   0xd401: Synchronization Partner
Playable File (Object) Types and Object Properties Supported:
   3000: Undefined Type
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3001: Association/Directory
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   3008: MS Wave
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 1, 2,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   3009: MP3
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 85,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   300c: ASF
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 353,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   3801: JPEG
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc88: Height UINT32 data type range: MIN 0, MAX 1920, STEP 1 GET/SET
      dc87: Width UINT32 data type range: MIN 0, MAX 3072, STEP 1 GET/SET
   b901: WMA
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 353, 355,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
   ba05: Abstract Audio Video Playlist
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
   ba03: Abstract Audio Album
      dc01: StorageID UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc02: ObjectFormat UINT16 data type ANY 16BIT VALUE form READ ONLY
      dc04: ObjectSize UINT64 data type READ ONLY
      dc07: ObjectFileName STRING data type GET/SET
      dc03: ProtectionStatus UINT16 data type enumeration: 0, 1,  READ ONLY
      dc41: PersistantUniqueObjectIdentifier UINT128 data type READ ONLY
      dc0b: ParentObject UINT32 data type ANY 32BIT VALUE form READ ONLY
      dc4f: NonConsumable UINT8 data type enumeration: 0, 1,  GET/SET
      dc44: Name STRING data type GET/SET
      dc46: Artist STRING data type GET/SET
      dc9b: AlbumArtist STRING data type GET/SET
      dc89: Duration UINT32 data type range: MIN 0, MAX -1, STEP 1 GET/SET
      dc8b: Track UINT16 data type ANY 16BIT VALUE form GET/SET
      dc8c: Genre STRING data type GET/SET
      dc9a: AlbumName STRING data type GET/SET
      de9a: AudioBitRate UINT32 data type range: MIN 5120, MAX 327680, STEP 1 GET/SET
      de99: AudioWAVECodec UINT32 data type enumeration: 0,  GET/SET
      de93: SampleRate UINT32 data type range: MIN 8192, MAX 49152, STEP 1 GET/SET
      de94: NumberOfChannels UINT16 data type enumeration: 1, 2,  GET/SET
      dc96: Composer STRING data type GET/SET
      dc99: OriginalReleaseDate STRING data type GET/SET
      dc91: UseCount UINT32 data type ANY 32BIT VALUE form GET/SET
      d901: BuyFlag UINT8 data type enumeration: 0, 1,  GET/SET
      dc82: RepresentativeSampleSize UINT32 data type range: MIN 0, MAX -1, STEP 1 READ ONLY
      dc81: RepresentativeSampleFormat UINT16 data type enumeration: 14337,  GET/SET
      dc83: RepresentativeSampleHeight UINT32 data type range: MIN 0, MAX 240, STEP 1 GET/SET
      dc84: RepresentativeSampleWidth UINT32 data type range: MIN 0, MAX 320, STEP 1 GET/SET
      dc86: RepresentativeSampleData array of UINT8 data type byte array:  GET/SET
Storage Devices:
   StorageID: 0x00010001
      StorageType: 0x0003
      FilesystemType: 0x0002
      AccessCapability: 0x0000
      MaxCapacity: 3957993472
      FreeSpaceInBytes: 3457982464
      FreeSpaceInObjects: 5877
      StorageDescription: S3
      VolumeIdentifier: c53f4618000000f5
Special directories:
   Default music folder: 0x00008007
   Default playlist folder: 0x00008001
   Default picture folder: 0x00008008
   Default video folder: 0x00008009
   Default organizer folder: 0x00000000
   Default zencast folder: 0x00008005
   Default album folder: 0x0000800a
   Default text folder: 0x00008006
MTP-specific device properties:
   Friendly name: (NULL)
   Synchronization partner: &#65246;&#65514;&#65279;&#65514;&#65279;&#65514;&#65279;&#65514;&#65279;&#41185;
libmtp supported (playable) filetypes:
   RIFF WAVE file
   ISO MPEG-1 Audio Layer 3
   Microsoft Advanced Systems Format
   JPEG file
   Microsoft Windows Media Audio

Secure Time:
<DRMCLOCK type="status"><VALUE>#20000301 04:40:12Z#</VALUE><FLAG>DRM_CLK_NEEDS_REFRESH</FLAG></DRMCLOCK>

Device Certificate:
<DEVCERT version="1.0"><CERTIFICATE type="DEVICE"><DATA><UNIQUEID private="1">CgoKCgoKCgoKCgoKCgoKCgoKCgo=</UNIQUEID><PUBLICKEY private="1">kUr5wvhWERhkKV24XM2q6dr8jXcq7pVXlGBQqum7g2a1Tl5J7hnDew==</PUBLICKEY><KEYDATA>ZCQ6vydxvNbEa5RJQyDQh1QgGIA=</KEYDATA></DATA><MSDRM_SIGNATURE_VALUE>aNnJCdBCg8yh+7zXXHEkB4X5sEuZ266AflZafA7q1tOTbwkZscR7TA==</MSDRM_SIGNATURE_VALUE><SYMSIGNATURE>S75ZboUYQhOYUpojIRwSpDXQTLw=</SYMSIGNATURE></CERTIFICATE><FALLBACK><SECURITYVERSION>2.4.105.105</SECURITYVERSION><CERTIFICATE private="1">kUr5wvhWERhkKV24XM2q6dr8jXcq7pVXlGBQqum7g2a1Tl5J7hnDewIEaWl0BWucoPpCfdQwdHGtSqbYo2r8AHke1nGstkYSc1fO6XJ+jRGaYbAW</CERTIFICATE></FALLBACK><CERTIFICATE type="GROUP"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><FEATURES><CLOCK>2</CLOCK><SECURECLOCK><URL>http://go.microsoft.com/fwlink/?LinkId=25817</URL><PUBLICKEY>!CNhvvz1WaNV1AFUmetxkvm9iD4UrE9cnGUi!qcqdxMiXmD1*ikYGA==</PUBLICKEY></SECURECLOCK><METERING>1</METERING><LICENSE_ACQ>1</LICENSE_ACQ><LICENSE_SYNC>1</LICENSE_SYNC><ENCRYPTION>1</ENCRYPTION><SYMMETRIC_OPT>1</SYMMETRIC_OPT></FEATURES><LIMITS><MAXCHAINDEPTH>2</MAXCHAINDEPTH><MAXLICENSESIZE>10240</MAXLICENSESIZE><MAXHEADERSIZE>5120</MAXHEADERSIZE></LIMITS><PUBLICKEY>2hOkxOCK1QPe10JHYvfVUjYjLBMzXCftotZMbbB+VhO0gpWYnFSNJA==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>zVgOV3F4q2xlvMfFBZtW/YaNhE/9IBGpQpxDJG4cljg81O1sxP/KhA==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION"><DATA><SECURITYLEVEL>2000</SECURITYLEVEL><AUTH_ID>1229</AUTH_ID><PUBLICKEY>8l60FgPW1vHhfaAFYkoYXMMHTFZCfCf98BXPcKJLbBjofB1fy8Bcbw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>LpLd030TMk4F6v2kAjf3LecPk0UOgCjPmQrGsKUfmyRBTRujDP3/LQ==</MSDRM_SIGNATURE_VALUE></CERTIFICATE><CERTIFICATE type="AUTHORIZATION_ROOT"><DATA><AUTH_ID>1</AUTH_ID><PUBLICKEY>a1t3hxrg!qbOgktnbYaEEi4teCse!gz6RvTPuC!zizKJlpU7xoduSw==</PUBLICKEY></DATA><MSDRM_SIGNATURE_VALUE>YoS6xu8BvaENyvqIISjhFbO5wmakFMYg2/C8ALN0uuXvYRVe3JJZYw==</MSDRM_SIGNATURE_VALUE></CERTIFICATE></DEVCERT>
WMPInfo.xml Does not exist on this device
PTP: Closing session
OK.

---

### Post by highfructose327 on 2008-08-05
Commander_Bob that is cool that lsusb worked for you, hopefully that will work for others as well. I had tried that in different usb ports I had no luck.

---

### Post by Hodariz on 2008-10-10
Im really new with Ubuntu and not sure which version i am using because my friend installed it for me. I have tried putting my Sansa Fuze into various modes and cannot get my computer to register it as even a storage device and it doesnt charge. What should I do the rectify the situation?

---

### Post by Commander_Bob on 2008-10-10
> **highfructose327 said:**
> Commander_Bob that is cool that lsusb worked for you, hopefully that will work for others as well. I had tried that in different usb ports I had no luck.

I think it works because the USB port on the front of my computer is not the same as the USB ports on the back. I added it after I got my computer. What I do lsusb the USB port is also a card reader (SD, compact flash, ect) and it shows up as
Bus 002 Device 003: ID 058f:9360 Alcor Micro Corp. 8-in-1 Media Card Reader
I think that why it works.

Hodariz to find the version of Ubuntu you have go to System->About Ubuntu and you should see something like 
"Thank you for your interest in Ubuntu 8.04 - the Hardy Heron - released in April 2008." a few lines down the page.

I don't know what the problem is but the Sanasa will not charge until it is recognized by the computer. Mine starts charging only after I type lsusb.

---

### Post by Hodariz on 2008-10-11
Hi, I got it to work, I do have the latest versions of hardy heron. I have sansa fuze 8Gb and I had to run
sudo modprobe -r ehci_hcd
sudo modprobe ehci_hcd
to get it to work.
Thanks though (now its time to figure out how to get my Chicony Electronics Webcam to work xD)

---

### Post by Stargazer777 on 2008-12-26
I just received a 8 GB sansa fuze for christmas and I am having the same trouble. I had the videos in MP4 format and I tried changing them to AVI with the iriverter, and once the video was converted my Fuze was recognising that the file was there (Still said that it couldn't play the files), where as with an MP4 it didnt even come up in the list. I hope this can help with coming up with a solution!

---

### Post by highfructose327 on 2009-01-09
Hello I believe Guido from the Sansa forums may have found a fix for mounting 8g Fuze 

He edited the :

> ```
 /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi
```

 If you go through this file searching for "Sansa" you will find also this line unter an entry for "Sansa Clip/Fuze":

 
```
<match key="@storage.originating_device:usb.product_id" int_outof="0x7432;0x7433;0x74c0"> 
```

As our Fuze 8G has the product ID 0x74c1 (shown by 'lsusb'), it became clear to me that a proper entry for this player is simply missing here. I changed this line to:

 ```
 <match key="@storage.originating_device:usb.product_id" int_outof="0x7432;0x7433;0x74c0;0x74c1">

```
 

saved the file and got a nice mp3-player icon on the desktop as soon as I plugged in the Fuze. Also Rhythmbox is started automatically and reads in all mp3 files, which were moved to the player before via file manager drag-and-drop. Note: I removed the hidden ".is_audio_player" file before.



I have not tested this since I am not using 8.04. I am using Ubuntu 8.10 which has never had a problem seeing my Fuze. Hope this helps, Thanks Guido

This is a link to the original post at the Sansa forums:

[HTML]http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=12910&page=4[/HTML]

---

### Post by darrien on 2009-02-01
hey 

ive have a sansa fuze for 4 months 

i have had the same problems 

follow this link to get a youtube video downloader that converts them to the correct format
[http://www.download.com/YouTube-Downloader/3000-2071_4-10647340.html]("http://www.download.com/YouTube-Downloader/3000-2071_4-10647340.html")

---

### Post by byteborg on 2009-02-15
> **darrien said:**
> hey 
follow this link to get a youtube video downloader that converts them to the correct format
[http://www.download.com/YouTube-Downloader/...]("#")

This is a windows program. What exactly does it do?
What tools/library does it use to convert?
What parameters (if applicable)?
What are the specifications of the converted videos that work on your device?

All the best,
/k

---

### Post by gackt on 2009-03-24
[Here you go!]("http://forums.sandisk.com/sansa/board/message?board.id=sansafuse&thread.id=7957")

---

### Post by autopapa on 2009-04-30
Hello all,

Since I&#7743; new to ubuntu (and thusfar it has been great) I thought I read all the postings around the Sansa fuze mount problems first and try them out. However there is quite some stuff posted, none of it seems to work with my system 
Here are some details :

[LIST]
[*]laptop with ubuntu 8.10
[*]Sansa Fuze 8Gb, with microSD 8Gb (not loaded at this point)
[*]Sansa firm version V01.01.11F
[/LIST]

I tried the following:
-configured the sansa on MSC, 
-tried to use the same usb port were previous memory stick was
-removed and replaced the package ehci_hcd
-used lsusb, but nothing shows up 
-updated, according to the Guido tip, file /usr/share/hal/fdi/information/10freedesktop/10-usb-music-players.fdi with id 0x74c[1-3]

nothing works, though the Sansa says it&#347; connected.
Tried it on windows XP (servicepack 2) : doesn'work either.

Still about a week ago, when I bought it I put one number on it, as to confirm to myself that it wouldn't be difficult... I&#7743; lost as to where to look for a solution.:confused:

Who could help me ? Thanks!

Autopapa

---

### Post by mrsocksman on 2009-06-26
Seriously guys, havn't you heard? It is near impossible to get videos on your Sansa Fuze. Trust me, i own one and the videos don't work(even with the sansa media converter on Windows), and check out the codec [http://www.anythingbutipod.com/forum/showthread.php?t=27460](http://www.anythingbutipod.com/forum/showthread.php?t=27460) it's gonna be a while till they let you have diff types of video on it.

---

### Post by Commander_Bob on 2009-06-26
I have had no problems with the Sansa Media Converter in Windows, but I have only tried a few movies.

---

### Post by clonne4crw on 2009-06-26
I has a Sansa Fuze. Under System Settings > USB Mode, select MSC. Connect it then.

---

### Post by clonne4crw on 2009-06-26
> **mrsocksman said:**
> Seriously guys, havn't you heard? It is near impossible to get videos on your Sansa Fuze. Trust me, i own one and the videos don't work(even with the sansa media converter on Windows), and check out the codec [http://www.anythingbutipod.com/forum/showthread.php?t=27460](http://www.anythingbutipod.com/forum/showthread.php?t=27460) it's gonna be a while till they let you have diff types of video on it.

NO ITS NOT!!!!! Using SMC on Windows, if the video is a MP4, then it works FLAWLESSLY. If its not, I use FFMPEG to convert it to that first, then run it through SMC.

---

### Post by pizpot on 2009-09-01
hi, let me mention how i use my fuze with 9.04. it is a v2 8 gb silver fuze. to convert videos, i knew right away it would be a pain to get the format right, so I tried the sansa converter in virtualbox and guess what? no problemo. I can even run my motorola software and use it to type texts on my krzr while converting vids with the fuze plugged in. you have to get the Sun version of virtualbox and not open or whatever version for usb to work. you have to right click the little usb icon on the bottom of the virtualbox window and enable the devices that are plugged in every time. but it sure beats booting to windows or farting around too much with avis. you need more codecs if it doesnt work btw.

I put some tv shows on it, and watched them eating breakfast, and this little player is very adequate.

(firmware version: 02.02.26A... and yeah, can't convert without the player plugged in, which is lame lame lame because it takes hours... bad for my battery, bad for me too cause i like to use it not have it babysit my conversion like DRM or something)

---

### Post by clonne4crw on 2009-09-01
You don't have to leave the player plugged in while SMC is converting. You can unplug it during the process, and it will keep going. Just make sure you don't unplug it while its copying files over to the player. When it finishes, it will complain about the player not being found, but you can copy the files from the Sansa Media Converter directory in My Documents.

---

### Post by maltman on 2010-07-28
I have a sansa fuze, and have both Ubuntu and Windows. And there is software that works in both environments that will properly convert videos to a format playable on the fuze.
Specifically, you can use Video4Fuze [http://code.google.com/p/video4fuze/]("http://code.google.com/p/video4fuze/").
It just uses mencoder behind the scenes to get the video right.
However the Fuze also requires a very specific structure for the AVI container format and cannot play the AVI files created using mencoder directly.
So it also uses fuzemux to remux the video file.
It works great and is really simple to use.

---

### Post by onekama_michigan on 2011-01-01
Video4fuze worked well for me!  Quick, seamless and even a nice looking GUI.  Thanks

> **maltman said:**
> I have a sansa fuze, and have both Ubuntu and Windows. And there is software that works in both environments that will properly convert videos to a format playable on the fuze.
Specifically, you can use Video4Fuze [http://code.google.com/p/video4fuze/](http://code.google.com/p/video4fuze/).
It just uses mencoder behind the scenes to get the video right.
However the Fuze also requires a very specific structure for the AVI container format and cannot play the AVI files created using mencoder directly.
So it also uses fuzemux to remux the video file.
It works great and is really simple to use.

---

