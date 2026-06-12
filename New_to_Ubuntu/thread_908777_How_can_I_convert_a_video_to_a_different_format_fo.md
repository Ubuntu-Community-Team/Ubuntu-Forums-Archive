---
title: "How can I convert a video to a different format for playback on the Xbox 360?"
date: 2008-09-02
forum: New to Ubuntu
---

### Post by curiousnoob on 2008-09-02
I have a file that I am trying to convert but have not been able to find an application that will work or perhaps I am using them wrong.

This is the format the file is currently in:
VIDEO
Duration: 1h 32m
Size: 700.1MB
Dimensions: 480 x 360
Codec: Microsoft MPEG-4 4.2
FPS: 30

AUDIO
Codec: MPEG 1 Audio, Layer 3 (MP3)

And I want it in any format that will work on the Xbox 360. Here are formats that are compatible: 
Q: What does the Xbox 360 console support for AVI?

A: The Xbox 360 console supports the following for AVI:

    * File extensions: .avi, .divx
    * Containers: AVI
    * Video profiles: MPEG-4 Part 2 (Simple Profile and Advanced Simple Profile)
    * Video bit rate: 5 Mbps with resolutions of 1280 × 720 at 30 fps. See the question about max bit rate, resolution, and frames per second.
    * Audio profiles: Dolby® Digital (2 channel and 5.1 channel), MP3
    * Audio max bit rate: No restrictions. See the question about max bit rate, resolution, and frames per second. 

Q: What does the Xbox 360 console support for H.264?

A: The Xbox 360 console supports the following for H.264:

    * File extensions: .mp4, .m4v, mp4v, .mov, .avi
    * Containers: MPEG-4, QuickTime
    * Video profiles: Baseline, main, and high (up to level 4.1)
    * Video bit rate: 10 Mbps with resolutions of 1920 × 1080 at 30 fps. See the question about max bit rate, resolution, and frames per second.
    * Audio profiles: AAC, 2-channel, Low Complexity
    * Audio max bit rate: No restrictions. See the question about max bit rate, resolution, and frames per second. 

Q: What does the Xbox 360 console support for MPEG-4 Part 2?

A:The Xbox 360 console supports the following for MPEG-4:

    * File extensions: .mp4, .m4v, .mp4v, .mov, .avi
    * Containers: MPEG-4, QuickTime
    * Video profiles: MPEG-4 Part 2 (Simple Profile and Advanced Simple Profile)
    * Video bit rate: 5 Mbps with resolutions of 1280 × 720 at 30 fps. See the question about max bit rate, resolution, and frames per second.
    * Audio profiles: AAC, 2-channel, Low Complexity
    * Audio max bit rate: No restrictions. See the question about max bit rate, resolution, and frames per second. 

Q: What does the Xbox 360 console support for WMV (VC-1)?

A: The Xbox 360 console supports the following for WMV:

    * File extensions: .wmv
    * Containers: ASF
    * Video profiles: WMV7 (WMV1), WMV8 (WMV2), WMV9 (WMV3), VC-1 (WVC1 or WMVA) in simple, main, and advanced up to level 3
    * Video bit rate: 15 Mbps with resolutions of 1920 × 1080 at 30 fps. See the question about max bit rate, resolution, and frames per second.
    * Audio profiles: WMA7/8, WMA9 Pro (stereo and 5.1), WMA Lossless
    * Audio max bit rate: No restrictions. See the question about max bit rate, resolution, and frames per second.

---

### Post by crispy_420 on 2008-09-02
Try here:

[http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide](http://gentoo-wiki.com/HOWTO_Mencoder_Introduction_Guide)

Not 100% here, don't have an xbox.

---

### Post by aimpau on 2008-09-02
Install avidemux:

```

sudo apt-get install avidemux-gtk

```

---

