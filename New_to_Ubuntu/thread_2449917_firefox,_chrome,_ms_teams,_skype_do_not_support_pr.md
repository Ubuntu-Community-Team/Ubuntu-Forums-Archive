---
title: "firefox, chrome, ms teams, skype do not support pre-UVC webcam but guvcview, vlc do"
date: 2020-09-04
forum: New to Ubuntu
---

### Post by bdutta on 2020-09-04
Currently on 20.04 (latest patch level, as of last night -- and I keep system fairly updated) running on an otherwise fully functional i5-8400 with IGP + 16GB RAM (single channel) + 240GB-SDD etc. My main webcam went bust, so I fished out a 20+ year old pre-UVC webcam (Intel Pro CS430) while waiting for the replacement webcam to arrive (will take a while). This webcam works reasonably well in guvcview, vlc, ffmpeg etc. It uses the 'gspca_spca505' driver as I could see from following the kernel module chain.

However this thing refuses for some reason to work with any other application like: firefox or google-chrome or chromium browser, or microsoft teams, or skype. All of them do see the /dev/video0 device, but for some reason report some kind of hardware failure. I could imagine that all of them are perhaps dependent on some sort of video hardware abstraction library which is missing support for the pre-UVC cams, and other applications like guvcview, vlc etc. use perhaps some alternative libraries that makes it work somehow.

I did follow the instruct to see if LD_PRELOAD of the v4l1 compatibility library, or even the v4l2 convert library, while launching those apps, but none of them worked. I mean the applications themself do launch successfully, they do see the video device, but fail to properly initiatize or open it, to show any video at all -- no inverted screen, no black screen, nothing. Wonder what could be up ? Any help / pointers that help getting this webcam working would be much appreciated.

PS: I have tried this webcam on Ubuntu MATE 20.04, standard Ubuntu 20.04, Lubuntu 20.04, Lubuntu 18.04, with same result.

---

