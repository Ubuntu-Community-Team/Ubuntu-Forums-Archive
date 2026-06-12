---
title: "ISO to WMV format"
date: 2012-03-14
forum: New to Ubuntu
---

### Post by goodgriefpenfold on 2012-03-14
Hello,

I'm sure there are many ways of doing this but i'm hoping to pick your collective brains.

In your view what is the best way of converting an iso image to wmv format. The reason that i ask is that i stream media from my nas drive to my xbox.

I am new to ubuntu having migrated from windows.

Regards

---

### Post by mikechant on 2012-03-15
I think you need to explain more fully. What is in the iso? An iso file contains an entire file system - directory structure and files - so converting an iso to wmv doesn't really make sense.

Do you mean that the iso file contains various wmv files? If so, I think you can extract them just by right clicking on the iso file and selecting 'open with archive manager' - this should allow you to access and extract the files contained in the iso.

---

### Post by goodgriefpenfold on 2012-03-15
Hi 

Its to back up my Family home movies that I want to keep safe on my network drive. (Sign your getting older i suppose!) I want them to be in wmv format because thats what my media centre (xbox) will play when streamed from said drive.

---

### Post by mikechant on 2012-03-16
This doesn't really get us any further.

To repeat: converting an iso file to wmv format does not make any sense. An iso file is an entire filesystem, not a type of video file.

If the iso file contains a number of wmv files then the method described above will allow you to extract them without conversion.
If the iso file contains video files in some other format they will need extracting and then converting.

Please try opening the iso file as described above, and then tell us what it contains.

---

### Post by dolphin194 on 2012-03-16
It is not possible to convert an ISO to WMV format, as they are completely different types of files.

An ISO file is an archive that stores other types of files, similar to a folder, and A WMV file is a video.

[B]But...
[/B]You can rip the DVD with a DVD ripper such as *AcidRip* and then convert it to a WMV.

---

### Post by yetiman64 on 2012-03-16
> **dolphin194 said:**
> It is not possible to convert an ISO to WMV format, as they are completely different types of files.

An ISO file is an archive that stores other types of files, similar to a folder, and A WMV file is a video.+1 this is correct OP.

> **dolphin194 said:**
> [B]But...
[/B]You can rip the DVD with a DVD ripper such as *AcidRip* and then convert it to a WMV.

From the OP,
> Its to back up my Family home movies that I want to keep safe on my network drive.We really need to know what format those home movies are in to help you OP. Are they home movies in DVD format ? If so the quote above from dolphin194 would apply.

If not and you have several mpgs avis or other file types stored in an iso, then they cannot be converted as a whole to wmvs. 
As mikechant has stated you need to extract the files and then convert each individual file to wmv format, **not** the iso itself.

Personally I get good results with ffmpeg from the command line converting video files to wmv and have a command here you could try out IF this second scenario is the case. Or you could look at winff a graphical front end for ffmpeg, you may find it easier to use.

---

### Post by d4m1r on 2012-03-16
.iso is basically a container, you should be able to open it with 7zip or the .rar plugin for Ubuntu however.

The .iso might already contain .wmv files within it, and then all you'd have to do is extract them.

---

### Post by Andrew_P on 2012-03-16
WMV is a Windows video media file format.  ISO is a CD or DVD disk image file format, usually used to store and transmit the entire contents of a CD or DVD electronically so that the recipient can burn the image to a CD-R or DVD+R disc and re-create the physical storage medium.  WMV files can be played with a media player, such as Windows Media Player or Totem Movie Player.  ISO files can't be "played" on anything, although they may contain WMV files and anything else that could be stored on a CD, DVD or hard drive.

If your stuff is in an ISO file, you have two options:
1. Burn the ISO file to an optical disc so that you can read its contents with the CD or DVD drive in your computer; or,
2. "Mount" the ISO disc image with a utility such as "zenity" so that Linux can open it and read it as if it were a removable optical disc.  (For convenience, it is best to do this with scripts that are stored in your user space and can be called from the GUI file manager with a mouse click or two.)

---

### Post by goodgriefpenfold on 2012-03-16
Thanks for the replies. Scholars and gents the lot of you. Made me realize i was thinking about it the wrong way.

Used handbrake in the end to rip it from the dvd again and convert it to h.264 which my xbox reads a treat.

Problem solved and i now understand what an iso is.

Kindest Regards

):P

---

