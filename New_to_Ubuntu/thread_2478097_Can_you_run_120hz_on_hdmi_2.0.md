---
title: "Can you run 120hz on hdmi 2.0?"
date: 2022-08-16
forum: New to Ubuntu
---

### Post by lilson89 on 2022-08-16
Hi there! Welcome all, I've just started to use Linux and I was wondering is it possible to set 120hz refresh rate using 4K resolution. I've got TV LG C1 as my main screen that doesn't have any display port so that forces me to use HDMI 2.0 due to my graphic card GTX1080. Using Windows I have ability to change refresh rate to 4K/120 but in Ubuntu I can only use 2k/120hz. Is there any way to make it happen? 

Thank You.

---

### Post by kevidigi on 2022-08-16
I take it you've installed all the third-party (i.e., nvidia) drivers for your graphics card?

---

### Post by lilson89 on 2022-08-16
Yup 515.

---

### Post by Holger_Gehrke on 2022-08-17
Are you sure that HDMI 2.0 is what your card supports ? According to Wikipedia's page on HDMI, you need HDMI 2.1 for 3840x2160p@120hz. Another possible reason is that Linux in general goes by what the display tells it is capable of through EDID (Extended Display Identification Data). TVs are notorious for transmitting EDID information that is incomplete or simply wrong. You can install the package read-edid and then run
```

sudo read-edid|parse-edid

```
in a shell to find out what your display says it's capable of.

Holger

---

### Post by lilson89 on 2022-08-17
Thank You Holger for the reply. I think I have found the answer...unfortunately. Right regarding HDMI 2.0 :

"HDMI 2.1 has 48Gbps carry capacity, compared to  just 18Gbps for HDMI 2.0. Now, the 18Gbps of HDMI 2.0 assumes video  delivery with HDR, 4:4:4 chroma, and 10-bit colour coding. At a  resolution of 3840 x 2160, that would fill up the entire bandwidth with a  maximum framerate of 60Hz, and often 4:4:4 won&#8217;t be possible, only  4:2:2. However, if we can force 8-bit colour coding (16.7 million  colours), no HDR, [and 4:2:0 chroma subsampling]("https://www.benq.eu/en-uk/knowledge-center/knowledge/is-chroma-sampling-important-for-monitors.html"), then 4K 120Hz actually turns out to &#8220;cost&#8221; about 16Gbps, which is technically possible on HDMI 2.0."

These are the criteria that need to be met in order to achieve 120Hz but after some digging I found also this:

"According to the changelog, this simply(?) seems to be a missing feature  in the Linux driver. YUV420 color subsampling fallback is only enabled  when connected over DisplayPort, not HDMI. Questionable why HDMI was  added in the Windows driver only." 

That would explain why I can run 120Hz on Windows but not using Linux. Sadly I think that because nVidia drivers are proprietary currently theres no solution unless changing graphic card to newer generation.

Edit: I did managed to achieve 420 chroma and 8-bit through nvidia-settings but still no 120Hz available.

---

### Post by ActionParsnip on 2022-08-18
[https://www.techreviewer.com/tech-answers/hdmi-20-21-refresh-rate/](https://www.techreviewer.com/tech-answers/hdmi-20-21-refresh-rate/)

---

