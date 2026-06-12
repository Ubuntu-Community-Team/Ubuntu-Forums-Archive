---
title: "open source media formats.."
date: 2008-05-12
forum: Other OS Talk
---

### Post by billdotson on 2008-05-12
What are some open source media formats out there?  I try to stay as clean as possible in regard to patented stuff.  I know matroska video and audio are completely open source, but I have yet to see any program that can encode, transcode from/to or decode matroska.

I know there is .ogg audio that is open source, and there is .ogm for video, but that is merely a container.  As far as I know it still uses an mpeg type video codec and the only thing different is that it allows .ogg audio streams within it.  There is also FLAC, SPEEX, etc.

Also, about xvid, is it still illegal to distribute compiled binaries of that?  What ways can you get it legally without compiling it yourself?  Downloading a program like mplayer or something that has it compiled as part of the program?

I have heard of Theora, that, along with ogg audio appears to make an .ogg video.  If this is the case then I would definitely like to use .ogg as my preferred video format from now on, transcoding into proprietary formats only when completely necessary (youtube or google video upload).  I am unsure of how to setup use to decode/transcode/encode/play these ogg files (theora video and ogg audio) in Windows XP.  I saw something about directshow filters, but the last time I downloaded a directshow filter pack, I think something like Haali Splitter it contained patented (probably royalty requiring) codecs as well.

Thanks, I am trying to get off proprietary, patented media.  Maybe some day we will all be free.

---

### Post by Judo on 2008-05-12
This is in the wrong section, but I'll answer it to the best of my knowledge.

Xiph.org's standards are all patent-free.  That includes the OGG container, Theora video, Vorbis audio, and multiple other standards such as subtitles and whatnot.  They've done a good job, but they're not the only ones.  Matroska is also patent-free.  Anything that is patent-free can be used freely, which is why this community likes it so much.  I also think FFMPEG's Snow and Nut formats are patent-free, but I could easily be wrong on that.  Although, I hope I'm right about Snow because they say it may have better compression than h.264.

All other standards, or formats, that I've heard of are technically proprietary because they use some sort of intellectual property.

Xvid, as long as I can remember, has been free software so it can be freely redistributed in source and binary forms.  However, being MPEG-4 ASP (DivX, 3ivx, LMP4, etc.), what it produces cannot always be distributed freely.

Sadly, Theora's compression is barely better than MPEG-1, but I still like it.  On Windows, I would probably use MediaCoder, or just MEncoder in CLI because I'm a bit of a geek to encode it.  And I bet if you complain to doom9 enough, he'll add some support for it in MeGUI.  As for decoding, I love VLC and Media Player Classic (with CCCP, of course).

---

### Post by billdotson on 2008-05-12
Hmm, thanks.  Where should I stick this if I wanted to get it completely answered (you did fine, thanks for the input you did give, I would just like a bit more information about how to set it up and some other things)

Thanks.

---

### Post by saulgoode on 2008-05-12
> **Judo said:**
> Sadly, Theora's compression is barely better than MPEG-1, but I still like it. 

This is not even close to being true (the MPEG-1 part, not whether you like it). While Theora's compression/quality ratio may not be quite as good as MPEG-4VLC, it is certainly competitive with MPEG4-ASP, WMV-9/10, and XVID/DIVX -- and far surpasses that of MPEG-2 (MPEG-1 is not even worth mentioning).

---

### Post by eldepeche on 2008-05-14
Wikipedia has big matrices of different audio and video codecs. Check out: 
[http://en.wikipedia.org/wiki/Comparison_of_audio_codecs](http://en.wikipedia.org/wiki/Comparison_of_audio_codecs)
[http://en.wikipedia.org/wiki/Comparison_of_video_codecs#Codecs_list](http://en.wikipedia.org/wiki/Comparison_of_video_codecs#Codecs_list)
[http://en.wikipedia.org/wiki/Comparison_of_container_formats](http://en.wikipedia.org/wiki/Comparison_of_container_formats)

Another thing to realize is that Ogg/OGM and Matroska are container formats, while Vorbis, FLAC, Speex (Xiph.org lossy audio for voice recordings) are codecs. The only free video codec I know of is Theora, so a totally free video file would be a Theora video stream with Vorbis audio in a Matroska or OGM container.

---

### Post by MetalMusicAddict on 2008-05-14
> **eldepeche said:**
> so a totally free video file would be a Theora video stream with Vorbis audio in a Matroska or OGM container.
.ogm was a hack. .ogv should be used now for video.

> **billdotson said:**
> What are some open source media formats out there?  I try to stay as clean as possible in regard to patented stuff.  I know matroska video and audio are completely open source, but I have yet to see any program that can encode, transcode from/to or decode matroska.

I know there is .ogg audio that is open source, and there is .ogm for video, but that is merely a container.  As far as I know it still uses an mpeg type video codec and the only thing different is that it allows .ogg audio streams within it.  There is also FLAC, SPEEX, etc.

Also, about xvid, is it still illegal to distribute compiled binaries of that?  What ways can you get it legally without compiling it yourself?  Downloading a program like mplayer or something that has it compiled as part of the program?

I have heard of Theora, that, along with ogg audio appears to make an .ogg video.  If this is the case then I would definitely like to use .ogg as my preferred video format from now on, transcoding into proprietary formats only when completely necessary (youtube or google video upload).  I am unsure of how to setup use to decode/transcode/encode/play these ogg files (theora video and ogg audio) in Windows XP.  I saw something about directshow filters, but the last time I downloaded a directshow filter pack, I think something like Haali Splitter it contained patented (probably royalty requiring) codecs as well.

Thanks, I am trying to get off proprietary, patented media.  Maybe some day we will all be free.

Matroska (.mka/.mkv) and OGG (.oga/.ogv/.ogg<-now legacy) and .ogm was a hack) are both containers. It's the codecs inside that matter as to whether or not they can be decoded.

FLAC, SPEEX, Vorbis are all audio codecs.

Xvid and Theora are video codecs. XviD is open source but you can't legally distributed the binaries in some countries because it's patent encumbered. (related to MPEG4) Theora is open and free. Was developed by a company then given away.

Just spend some time searching Wikipedia. They have great info on all of this. HydrogenAudio Forums is another great resource.

---

### Post by andrew.46 on 2008-05-25
Hi:

> **billdotson said:**
>  I know matroska video and audio are completely open source, but I have yet to see any program that can encode, transcode from/to or decode matroska.

Make a backup copy of your own DVDs (if legal in your country) with ogg vorbis sound, h264 video, matroska container, mplayer, mencoder:

[http://www.andrews-corner.org/matrix.html](http://www.andrews-corner.org/matrix.html)

All open source.

  Andrew

---

### Post by MaxIBoy on 2008-05-26
> **billdotson said:**
> 
I have heard of Theora, that, along with ogg audio appears to make an .ogg video.  If this is the case then I would definitely like to use .ogg as my preferred video format from now on, transcoding into proprietary formats only when completely necessary (youtube or google video upload).

Youtube works perfectly with theora. I've done it twice:
[http://www.youtube.com/watch?v=iIuMJ_hWgvI](http://www.youtube.com/watch?v=iIuMJ_hWgvI)
[http://www.youtube.com/watch?v=2pcfBt3qgsc](http://www.youtube.com/watch?v=2pcfBt3qgsc)


I agree, I like to stick with open standards when possible. For instance, I've been using PNG instead of BMP (that one is obvious.) 

I actually don't think you're missing much.

---

### Post by geni on 2008-05-27
Wikipedia has a few hundred Theora/Vorbis vids. For example

[http://en.wikipedia.org/wiki/Image:Sturmgesch%C3%BCtz_III_modern_day_video.ogg](http://en.wikipedia.org/wiki/Image:Sturmgesch%C3%BCtz_III_modern_day_video.ogg)

(transcoded from mpg to Theora/Vorbis with ffmpeg2theora)

---

### Post by geni on 2008-07-31
Firefox just added support for Theora through the <video> tag to their nightly build.

---

