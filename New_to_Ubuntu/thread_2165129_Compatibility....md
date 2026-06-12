---
title: "Compatibility...?"
date: 2013-08-03
forum: New to Ubuntu
---

### Post by pat4 on 2013-08-03
Hi,
New here so please be gentle.. I have a new computer on order and have decided that it is time I tried out Ubuntu / Linux. The software is totally new to me having been a Windows user for (too many) years.  I have downloaded a copy of the 12.04 LTS release and burned it to disc ready for installing it when my new machine arrives.

A quick question.. I have a large number of photographs, mainly .jpg format and some video in .avi and .wmv format stored on a couple of external USB hard drives. The drives are formatted in the NTFS system and the photos are stored in folders created under the Windows (XP) system.

Will Ubuntu / Linux recognise these folders (and ultimately the contents) or do I have to look at an alternative archiving system?

Any and all help appreciated.

Thanking you in anticipation..

P4

---

### Post by wildmanne39 on 2013-08-03
Hi, yes ubuntu will recognize your files, it can read window partitions.

Please becareful when installing ubuntu so you do not overwrite your files.

I suggest having the external drives unplugged while installing ubuntu, it will be less confusing when partitioning your drive.

---

### Post by ian-weisser on 2013-08-03
> **pat4 said:**
> I have a large number of photographs, mainly .jpg format and some video in .avi and .wmv format stored on a couple of external USB hard drives. The drives are formatted in the NTFS system and the photos are stored in folders created under the Windows (XP) system.

Will Ubuntu / Linux recognise these folders (and ultimately the contents) [...]?

Yes.
Ubuntu can read/write NTFS-formatted drives.
Many applications in Ubuntu can open .jpg, .avi, and .wmv files.

---

### Post by TheFu on 2013-08-03
First, do not just install 12.04 when you get the new PC, run the OS from the CDROM and see what works and what doesn't with your hardware.  UEFI, as new computers have, bring new problems for installing Linux.  You need to read up on that, as many people with lots and lots of Linux experience do not have **any** experience with UEFI systems. You will need to be the expert at that. There is a UEFI install howto for Ubuntu - google will find it.

For your other questions, I have mostly good news - Linux will almost certainly read the NTFS partitions perfectly and will have little issue playing and viewing JPG and AVI files.  There are built-in viewers for these, but I prefer **geeqie** for images and **VLC** for any video.

Now, for the bad news.  WMV is just a container format - the actual codec used inside can be 100% compatible with Linux or not. There is no way to tell until you try each file.  WMV files can support DRM, if that is the case, you'll never see the contents.  I say this only to provide information - I'd also say that WMV files I've found on free online websites almost always playback fine, no issue at all.

If VLC can't play the video, then I don't need to see it.  VLC has most codecs built-in, so it isn't like Windows with codec-paks that need to be installed.  By default, Ubuntu doesn't install tools that playback patent encumbered files - mp3, and many video files. During the install, you should select those to be installed. I think it is a checkbox.

Now onto the stuff you didn't ask - NTFS does not have all the same permissions capabilities that Linux file systems provide. Basically, there are ZERO real file permissions on NTFS partitions as far as Linux is concerned. If you plan to backup Linux files, you really, really, really want a Linux-based file system with Linux permissions, Linux hard/soft link capabilities and support for Linux ACLs.  For pictures, videos and audio files, these permissions may or may not be important, but for security and programs these extra permissions are important.

I'd also like to point out that when it comes to commercial streaming and Linux, it is hit or miss.  Websites that use Silverslight won't work.  Some newer Flash streams with DRM will not work on Ubuntu either.  I've been unable to get Amazon Streaming to work with Ubuntu the last few months, though it did work for years before that.  Oddly, Amazon Streaming works with Mint13 (installed it last week as a test - worked).  Anyway, thought you might be interested in that too.  Youtube and Hulu have always worked.  I don't think that Netflix has ever worked - at least not natively on Linux.

There you have it. Any other questions?  BTW, good choice on 12.04 - most users should go with that version, not the latest versions, IMHO.

---

### Post by Vladlenin5000 on 2013-08-03
First of all I can't praise enough the highly valuable and thorough explanation presented in the previous post. That said I must add that I've been using Linux exclusively for almost a decade - mostly Ubuntu and before Mandrake/Mandriva - and I never found a multimedia file I couldn't play properly, provided I have also installed the required proprietary codecs for some formats. Ubuntu, like many other distros, by default don't install those but all can be added easily during the installation process or just installed after - look for *ubuntu-restricted-extras -.* Also the Medibuntu repository have a few other interesting extras ;).

To be honest, I do a lot of video conversions and DVD/BluRay editing and can't imagine myself going back to Windows to do that, that would be a good definition of nightmare. However, I must admit that at the end it boils down to having the correct software/codecs or not, regardless of the operating system. The thing is, in my opinion and from the point of view of what I need it for, Linux and Ubuntu in particular have better software tools combined with stability and - I'll be flamed for that :D - an improved productivity thanks to the new Unity desktop environment.

---

### Post by pat4 on 2013-08-04
Thank you to all who have responded, answered my queries and more  besides. I am sure the advice contained in the posts wil prove useful.  My fear was that I would lose access to my family photos etc., if I  didn't back them up in a different format or directory structure.

Hopefully,  as I become competent with Ubuntu I will be able to repay the favours  shown by offering my own advice within this forum.

Kind regards...

---

