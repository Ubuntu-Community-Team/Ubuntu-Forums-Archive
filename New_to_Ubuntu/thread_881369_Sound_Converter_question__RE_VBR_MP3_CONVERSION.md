---
title: "Sound Converter question  RE: VBR MP3 CONVERSION"
date: 2008-08-05
forum: New to Ubuntu
---

### Post by paker on 2008-08-05
I was trying to get a decent MP3 from FLAC.
Initial file size = 40 MB.
Converted to MP3, VBR (V1)   10 MB

Right click on the MP3 file. 157 kbps instead of 256 kbps, target bit rate for VBR V1. Weird. Maybe Sound Converter not working in VBR? What about CBR?

Opened Sound Converter again. Converted FLAC to MP3, CBR 256 kbps. I got 20MB file. Right click, 256 kbps. Sound Converter working fine in CBR.

Uhm.....

I opened Audacity.
Imported 40 mb flac.
Exported to MP3, VBR V1. Again, I got 10 MB file with 159 kbps.

At this point, I cannot doubt Sound Converter any more. Maybe the music is so information lean that it didn't need allocated 256 kbps? Makes sense to anyone?

---

### Post by ibuclaw on 2008-08-06
Am I right in thinking that the song is around 5 minutes long?

I think you may need to review in detail the advanced settings of the encoding, but it kind sounds like the stereo mp3 channels are being encoded as two separate streams, or joint-stereo isn't enabled/availiable as an option.

Do bare in mine that this is mp3LAME encoder, and not mp3PRO, there may be some subtle differences between the two.

Perhaps you would might be interested in using .ogg as your music format of choice instead?

Regards
Iain

---

