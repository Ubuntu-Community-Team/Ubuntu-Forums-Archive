---
title: "VC500 (CX23102) S-video no colour"
date: 2016-10-06
forum: New to Ubuntu
---

### Post by georgeqgreg on 2016-10-06
Hi everyone. I'm on Ubuntu 16.04 and when I use the s-video input on my VC500 (CX23102 chip) everything's in black and white. There's colour when connected to a TV, or to the VC500 in Windows, but not on Ubuntu. For some reason the included firmware (v4l-cx231xx-avcore-01.fw) is different from the one included with the official Windows drivers, but using that firmware causes no change in behaviour I've noticed. Composite connection works normally.

I'd love if I could get s-video input working in colour, thanks.

---

### Post by colmax on 2016-10-07
Not sure why you choose to use s-video
Would appear linux has gone greyscale because the driver doesn't support 8bit or above mode
Silly question but have you checked display settings
or maybe it's seeing your display as monochrome
Seems it isn't supported
Try diamond site for a driver spose
Cheers

---

### Post by georgeqgreg on 2016-10-07
I choose s-video because it's better than composite! The VC500 offers composite and s-video input, for displaying (for example) video game consoles that output those connections, in programs like VLC, OBS, or Cheese.

The Diamond website has a "linux driver" but it appears to be a copy of what's in the kernel already.

---

### Post by colmax on 2016-10-07
I respect your decision
Maybe type vc500 into the forum search engine
I found some entries there
Wish i was more help
Cheers

---

### Post by georgeqgreg on 2016-10-07
I read those VC500 posts, it didn't seem like any of them had my problem, nor did any of them seem helped. This is the Conexant version of the VC500 btw, a variant of the OTG102. (recognized as the Geniatech OTG102)
I noticed (via SHA256 hash) that the firmware included in Ubuntu is different from the one offered here [https://www.linuxtv.org/downloads/firmware/#conexant](https://www.linuxtv.org/downloads/firmware/#conexant) (and that one is the same as the one in Diamond's Windows driver) so I tried copying it to /lib to see if that would help, but it didn't seem to cause any change. I wonder if it's something with the driver itself.

Here's how s-video capture looks in Cheese
[IMG]http://i.imgur.com/VgcvnxR.png[/IMG]

And here's composite capture
[IMG]http://i.imgur.com/Lb9Bdae.png[/IMG]

I wondered if it's interpreting the s-video input's luminance as composite, (as some OTG102 variants feature a second composite input in lieu of an s-video connector) so I tried what I think is a bad cable where composite is transmitted rather than luma, but that was also black and white. If it really is as such, then it's at least stripping the colour information out of the luma input, maybe it's not getting the chroma data? I don't know how it works.

---

