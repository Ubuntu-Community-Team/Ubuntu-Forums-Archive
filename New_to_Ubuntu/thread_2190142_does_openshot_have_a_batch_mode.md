---
title: "does openshot have a batch mode"
date: 2013-11-26
forum: New to Ubuntu
---

### Post by squakie on 2013-11-26
I need to be able to process many files from a list through openshot.  I don't need to do any editing, I just need to export the files as mpeg4-video (mp4), due to something I messed up that caused the internal recording type to be MPEG-P5.

I have another thread open looking for help on how to generate the list, now I need to know if it's possible to have openshot read that list and export each file as mp4.

So far, the only thing I have found is a Wiki - and it doesn't say anything about batch mode.  I've been trying to go to the openshot web site, but it keeps acting like it is no longer there.

Any insight would be greatly appreciated.

---

### Post by deadflowr on 2013-11-26
I don't think you can batch convert with openshot.

But I know you can, or at least should be able to, with ffmpeg.
And quite possibly with the gui winff (WinFF).

---

### Post by squakie on 2013-11-26
You know, I'm stupid I guess, but I've just never understood any of the options that go with ffmpeg - I just don't know anything about video to what those things mean.  WinfFF - I have that installed.  I'll try a single file conversion to see if it does what I need, and if so, I'll look for a batch mode.

Thanks!

---

### Post by squakie on 2013-11-26
Well, winff errored out:

invalid cbp at 11 17q=0.0 size=       0kB time=55.65 bitrate=   0.0kbits/s    
[mpeg2video @ 0x22e9ec0] Warning MVs not available
[mpeg2video @ 0x22e9ec0] concealing 585 DC, 585 AC, 585 MV errors
[ac3 @ 0x22ecd00] incomplete frame
frame= 1781 fps=477 q=0.0 Lsize=       0kB time=58.94 bitrate=   0.0kbits/s    
video:901631kB audio:11052kB global headers:0kB muxing overhead -99.999998%

I don't know what that means, unless it also doesn't know what an internal format of "MPEG-PS" is either.

---

### Post by squakie on 2013-11-27
Don't think this is going to work out.  The videos I tried converting with OpenShot look fine in a Window, but use the media center and put them full screen on a HDTV and they flicker badly - I assume because the original source was tape so the frame rate is off.  

Just going to give up, reinstall XP in a small partition so I can convert everything again.  Only problem:  the software that came with the USB video adapter outputs the files as MPEG-PS - I don't get a choice.  So until I can solve some sort of conversion anyway, everything remains the same.

---

### Post by FakeOutdoorsman on 2013-11-27
Install Windows XP to convert videos? You don't need to do that.

Some questions:
[list]
[*]What is this USB device?
[*]What's the software that outputs the files from it?
[*]Does the device and/or the software work in Linux?
[*]What's "media center"?
[*]Which brand and model of TV?
[/list]

Please show some information about the file(s) you want to convert (please show the complete console output and please use the code tag):
```
ffmpeg -i input.mpg
```

---

### Post by squakie on 2013-11-28
EasyCap USB device using the included Honestech software.  I have another thread asking for help on what the heck to do with some code that is apparently a driver module.  I have one that uses the chipset that hasn't been supported in Linux.  The software is also Windows-only, and no it won't work in Wine - it needs access to USB.  I also have a Dazzle DVC-100 with a post open on it because it is recognised, but I'm only getting audio - the video is just "moise" bars that match the amplitude of the sound.  I also have a Roxio VHS to DVD adapter and software (can you tell I've been trying to find SOMETHING that will work in Linux?).  It is also USB, and the software is Windows only.  Never have found any way to even get it recognized by Linux, but even if Windows, the video from it was rather choppy - I assume the sampling rate.

However, all that is off topic from this thread.  I have searched and indeed there is no batch mode for OpenShot.

If you'd like to help on my other questions on this same topic, please see my other posts.  I need all the help I can get.

---

