---
title: "Any way on Ubuntu to get a .SWF file (flash) onto a DVD and play it on a DVD player?"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by Obero on 2008-11-24
I haven't researched much into it, but I think it's possible. Just wondering how I'd do it on Ubuntu? I would figure using a converter to change the .SWF into like, an .AVI file. Then use the .AVI to burn on a DVD authoring file. I'm just not sure how to do all of this, also what's a general format that all DVD players use (is it .AVI?) and what DVD authoring software is out there that adds the menu, etc.?

---

### Post by Obero on 2008-11-24
Guys, anyway to do this? I researched and I've seen DVDStyler, but I'm still not sure.

---

### Post by a0u on 2008-11-24
Use [edit.py]("http://www.unixuser.org/%7Eeuske/vnc2swf/pyvnc2swf.html#edit") in pyvnc2swf to convert from *.swf to *.flv.
Then, use ffmpeg to convert from *.flv to *.avi.

DVD authoring: [https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring) (note that it's slightly outdated, but should still be somewhat useful)

---

### Post by Obero on 2008-11-24
> **a0u said:**
> Use [edit.py]("http://www.unixuser.org/%7Eeuske/vnc2swf/pyvnc2swf.html#edit") in pyvnc2swf to convert from *.swf to *.flv.
Then, use ffmpeg to convert from *.flv to *.avi.

DVD authoring: [https://help.ubuntu.com/community/DVDAuthoring](https://help.ubuntu.com/community/DVDAuthoring) (note that it's slightly outdated, but should still be somewhat useful)

Hmm, what's ffmpeg? And are you sure .avi works with all DVD players?

---

### Post by a0u on 2008-11-24
> **Obero said:**
> Hmm, what's ffmpeg? And are you sure .avi works with all DVD players?
"**FFmpeg** is a computer program that can record, convert and stream digital audio[]("http://en.wikipedia.org/wiki/Sound_recording") and video in numerous formats."
FFmpeg homepage: [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)
It's already in the Ubuntu repositories.

I believe DVDs use MPEG-2, in which case you can probably just use edit.py to convert directly to *.mpg.

[**HOWTO: Make DVD Videos Using Tovid: The Video Disc Authoring Suite**]("http://ubuntuforums.org/showthread.php?t=183936")

---

### Post by Hakanu on 2008-11-24
.avi will be detected by all dvd player firmware, yeah. It isn't really necessary to use any dvd authoring at all if you get it into an avi, but you won't have the option to create menus or have anything else on there. The ubuntu default (Brasero Disc Burning) should be able to get everything you want done, done. After you get it in a solid movie format, just fire up Brasero and it's pretty self explanatory.

---

### Post by halitech on 2008-11-24
DVDs use VOB files which are basically Mpeg files files split a certain way. Depending on your dvd player, you may be able to play mpg, avi and divx directly without putting them into a dvd format.

---

### Post by Obero on 2008-11-24
> **a0u said:**
> "**FFmpeg** is a computer program that can record, convert and stream digital audio[]("http://en.wikipedia.org/wiki/Sound_recording") and video in numerous formats."
FFmpeg homepage: [http://ffmpeg.mplayerhq.hu/](http://ffmpeg.mplayerhq.hu/)
It's already in the Ubuntu repositories.

I believe DVDs use MPEG-2, in which case you can probably just use edit.py to convert directly to *.mpg.

[**HOWTO: Make DVD Videos Using Tovid: The Video Disc Authoring Suite**]("http://ubuntuforums.org/showthread.php?t=183936")

Ok, sorry about the .SWF thing. It's not flash, it's already .flv.

Okay so now what do I do? How do I get the .flv to MPEG-2?

Then after that, what software do I use to author MPEG-2 with a DVD menu?

---

### Post by Obero on 2008-11-24
> **Hakanu said:**
> .avi will be detected by all dvd player firmware, yeah. It isn't really necessary to use any dvd authoring at all if you get it into an avi, but you won't have the option to create menus or have anything else on there. The ubuntu default (Brasero Disc Burning) should be able to get everything you want done, done. After you get it in a solid movie format, just fire up Brasero and it's pretty self explanatory.

Wouldn't you have to author the movie format somehow? I mean I wouldn't expect just burning the movie file on a DVD and then it would work, or would it? I think there'd have to be some kind of menu, although I'm not too concerned about a menu, I just want it to work with my Samsung and Sony DVD players.

---

### Post by halitech on 2008-11-24
if you want a dvd menu, you can use tovid (as suggested above), ManDVD or dvdauthor. Personally I suggest ManDVD as it works fine for me

---

### Post by Obero on 2008-11-24
> **halitech said:**
> DVDs use VOB files which are basically Mpeg files files split a certain way. Depending on your dvd player, you may be able to play mpg, avi and divx directly without putting them into a dvd format.

I'm a noob at this, but the DVD player I'm planning on using is Sony if that helps.

---

### Post by a0u on 2008-11-24
> **Obero said:**
> Okay so now what do I do? How do I get the .flv to MPEG-2?

If you haven't already:
```
sudo aptitude install ffmpeg
```Then:
```
ffmpeg -i input.flv output.mpg
```

---

### Post by Obero on 2008-11-24
> **a0u said:**
> If you haven't already:
```
sudo aptitude install ffmpeg
```Then:
```
ffmpeg -i input.flv output.mpg
```

So theoretically, it would be like:

```
ffmpeg -i blah.flv blah2.mpg
```?

After that, what software do you guys recommend to use? Can anyone give me a link to the latest software that I should use? Also, I've been researching and I've seen some sort of DVD burning format as "VCD." What I'm trying to do is basically get a .FLV on a DVD and then play it on a DVD player on a TV. So is what I'm trying to do a VCD, or...?

---

### Post by a0u on 2008-11-24
VCD != DVD (different formats, although VCD is supported by some DVD players)

Halitech suggested [ManDVD]("http://www.getdeb.net/app/ManDVD"), and from the screenshots it seems to have a nice GUI.

---

### Post by FakeOutdoorsman on 2008-11-24
> **a0u said:**
> If you haven't already:
```
sudo aptitude install ffmpeg
```Then:
```
ffmpeg -i input.flv output.mpg
```
A better command would be:
```
ffmpeg -i input.flv -target dvd output.vob
```
The target option will take care of the bitrate and frame size automatically.  You could also use "-target pal-dvd" (25 fps) or "-target ntsc-dvd" (29.97 fps) if you want to be framerate specific.

---

### Post by halitech on 2008-11-25
I'm not sure if it supports flv files or not but another option if this will be the only movie on the disk is DeVeDe as you can actually select Video CD. Only downside is no menu (but if its the only file then doesn't really matter)

---

### Post by bumanie on 2008-11-25
Devede should encode that to dvd format - if my memory serves me correctly, I converted one video file that was .swf with devede. It's available in the repositories - > sudo apt-get install devedeffmpeg should also be able to convert that file also - it's available in the repositories (need medibuntu repository enabled to get it).

---

### Post by Obero on 2008-11-25
So I'm going to use DeVeDe. Is it Video CD or Video DVD? There's two options. Also, is it only one movie? And will it play on a DVD player? Also, will this burn on a CD-R?

---

### Post by halitech on 2008-11-25
if you want to put it on a CD-R then select Video CD. 

only you know if its 1 movie, how many titles do you have that you want to put on the disk?

---

### Post by Obero on 2008-11-25
> **halitech said:**
> if you want to put it on a CD-R then select Video CD. 

only you know if its 1 movie, how many titles do you have that you want to put on the disk?

1, but is it possible for 2 with DeVeDe?

---

### Post by halitech on 2008-11-25
sure, you just don't get a menu with multiple files so its better for just 1 file or 2(or 3) parts of the same movie/show/event. If you want a menu for multiple shows, go with ManDVD

---

### Post by Obero on 2008-11-25
> **halitech said:**
> sure, you just don't get a menu with multiple files so its better for just 1 file or 2(or 3) parts of the same movie/show/event. If you want a menu for multiple shows, go with ManDVD

ok, also just to confirm. How would I turn the .flv into the DVD file?

Someone here posted:

```
ffmpeg -i input.flv -target dvd output.vob
```

but can you specifically show me how to put in the actual files? do i get the entire address like home/desktop/etc. or what?

---

### Post by Songwind on 2008-11-25
> **Hakanu said:**
> .avi will be detected by all dvd player firmware, yeah. It isn't really necessary to use any dvd authoring at all if you get it into an avi, but you won't have the option to create menus or have anything else on there.

Actually, most HD-DVD and Blu-Ray players won't play AVI files.  I think that the MPAA probably applied some pressure, to make it harder for people to watch downloaded videos.

---

### Post by halitech on 2008-11-25
there are a few DivX players out there that will play most formats but not many and for my money, I'd rather buy a video card with TV and just play them from my computer then buy a DivX player (or for that matter, just watch them on my computer seeing as how my monitor and tv are the same size)

---

### Post by pmooney78 on 2008-12-05
> **Obero said:**
> ok, also just to confirm. How would I turn the .flv into the DVD file?

Someone here posted:

```
ffmpeg -i input.flv -target dvd output.vob
```

but can you specifically show me how to put in the actual files? do i get the entire address like home/desktop/etc. or what?

OK, here's a detailed description of what I think the easiest way to handle this type of situation is, using DeVeDe -- which really is easier for someone at your experience level, I think ... it runs mencoder internally, which is an alternative to ffmpeg. If the command-line gives you the heebie-jeebies, try DeVeDe.

Start up DeVeDe. It will ask you what kind of disc you want to produce. Short answer: Produce a DVD unless you're (a) sure your DVD player plays video CDs (many do, but not all), or (b) willing to waste a blank CD and several hours trying it. (Video CD was a popular format in Asia, but never made it big in the States. Blank CDs are still cheaper than blank DVDs, but if you shop smart, not by much. If you don't know what you're doing, a video DVD is the best bet.)

Next, select what you want the "output format" to be. If you don't know what you're doing, choose "create an ISO image." (Trust me, it's the best default option.)

You'll see a section where you can add additional "titles" in the upper-left corner. Ignore that unless you're sure you what to add multiple titles and know what you're doing. In the upper-right corner, you'll see a section where you can add your video files. Click the "Add" (that's the "plus sign") button to add your first video file. A dialog box will pop up. Near the top, you'll have a button to push that lets you select the "source video file." That's the file you're converting, your .flv file. Navigate to it -- wherever it is on your hard drive -- and double-click on it.

DeVeDe will analyze the file. This could take several minutes on a large file. While it's analyzing, it'll look like it's just sitting there. If you have a slow computer, go start a pot of coffee or water your plants and come back in five minutes or so. DeVeDe should have finished analyzing the file. Now you should see the name of your input .flv file in that box you clicked on at the top, and you'll have some options for controling the technical aspects of how it will be converted. LEAVE THESE ALONE unless you know what you're doing (or the file that will be produced is too big -- but honestly, for converting an .flv file, it's not particularly likely, because I'm assuming your source .flv file is not as long as a feature-length movie). The defaults usually make sense in this situation (in fact, they're overkill in terms of quality, but again, don't worry about that unless the resulting DVD will be too big -- that is, bigger than about 4.3 gigabytes). Click "OK" on this dialog box after making any adjustments that need making (or if you're not making any adjustments). 

If you really, really want a menu to pop when the DVD loads in your DVD player, leave that "create a menu" box checked in the lower-left corner checked. But if you only have one title, that's a superfluous option -- it will just pop up with a menu with one option, which means that you have to pick your remote control up again and hit the "Play" or "OK" button to get it to start playing. ANNOYING! (I think so, anyway.) Uncheck the box if you want the DVD to just start playing.

When everything is set up the way you want it to be, click "Go" (or maybe it's "Next"? I'm at work and don't have a copy of DeVeDe running ... darn employer insists on running Windoze). It will ask where you want the output file (the ISO image) to be created. Make an intelligent choice. You'll notice that the box says "Don't choose a folder on a VFAT/FAT32 drive." FAT32 is the native Windoze drive format, and VFAT is a techical term for how Linux handles these drives (for our purposes, they mean the same thing). The implication is that you shouldn't choose a drive that was originally formatted by Windoze unless you know for sure that it's formatted as NTFS (the non-braindead Windoze file system). There are good reasons for this, trust me ... but I'm not going to go into them. What you want to do is to choose a folder on a drive that's formatted as one of the native Linux file systems (ext2/ext3, reiserFS, xfs, jfs ...). If you have NO IDEA what any of this means, just choose your home directory. REMEMBER WHERE YOU'RE SAVING THIS FILE! Click OK. The conversion process will start, and could take a long time. (I have the world's oldest computer, and converting .avi, .mpg, or .mov usually takes twelve to forty-eight hours. Your results may vary. If you don't have the world's oldest computer, it'll probably be faster. I wouldn't hold my breath, though.)

When everything is done, a box will pop up telling you so. You can quit DeVeDe. It will ask you if you want to save the project. Probably, you don't. 

Find the image file in the location where you saved it. Right-click on it ... you should see an option to burn the image to DVD using your default DVD-burning software. (DON'T open the image with Archive Manager and extract the contents ... you're making life harder for yourself if you do.) If you don't see an option to burn to DVD when you right-click, open up your DVD burning software and choose the option to "burn an image to disc." Put a blank DVD in your drive and start burning.

You're done! Test your DVD in your DVD player to make sure everything came out OK.

Hope that helps. :)

---

