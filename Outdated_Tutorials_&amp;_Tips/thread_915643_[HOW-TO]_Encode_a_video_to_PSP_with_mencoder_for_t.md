---
title: "[HOW-TO] Encode a video to PSP with mencoder for the best quality/size ratio"
date: 2008-09-10
forum: Outdated Tutorials &amp; Tips
---

### Post by Tristan_F on 2008-09-10
I had a very hard trouble finding how to encode a video for the PSP using mencoder. Of course there is always ffmpeg or WinFF but I am more familiar with mencoder so I prefer the last one. Moreover, all the command-line I found using ffmpeg gives a movie which size is about 350Mo. With mencoder you can achieve a size of about 250Mo.

The command I use is the following one : 

```
mencoder -sws 9 -vf scale -zoom -xy 480 -ovc x264 -oac faac -faacopts br=64:mpeg=4:object=2:raw -channels 2 -srate 24000 -x264encopts crf=26:me=umh:me_range=16:subq=6:trellis=2:global_header:level_idc=30 -of lavf -lavfopts format=psp
```

You can take a look at the quality result [here]("http://tristan.ferroir.free.fr/index.php/2008/08/23/convertir-une-video-pour-la-psp-windows-et-linux-best-settings-to-convert-video-for-the-psp-windows-and-linux/#more-43"). I used the trailer of Hulk.

Comments are welcome either here or on the previous linked page.

---

