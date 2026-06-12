---
title: "[SOLVED] Hi. I have question about WAV &amp;amp; WMV Files"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by Georgia boy on 2008-08-18
Hi. I installed Ubuntu 8.04 on Saturday night. Got my feet wet without putting cement boots on. :)
After figuring out about my setting up the Thunderbird and Evolution I started receiving my emails. 

A couple of them had WMV files. I had to send them back to myself to open in my Windows XP for viewing. What can I use to be able to view WAV and WMV files in Ubuntu that is already a package that comes for downloading that is Ubuntu supported? I need something to be able to view what some of my friends and family members send. For some reason I was thinking that there was a package available for the download from the Ubuntu supported section. Maybe I'm misthinking. That happens at times. :)

Or do I have to search for something to use. As you can see I'm new at this and am lost trying to learn. Eventually I want to completly conver over from Windows but until then I need to learn all I can about what I need to do things with. 

All help and suggestions are greatly appreciated.

Thanks in advance

Tom

---

### Post by halitech on 2008-08-18
vlc should play them by default but may want to install ubuntu-restricted-extras in order to get full support in most apps.

---

### Post by tuxxy on 2008-08-18
Did you install the restricted-extras package, this includes codec packs amongst other things.

Search for ubuntu-restricted-extras in synaptic, or type this in termninal

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Oldsoldier2003 on 2008-08-18
> **halitech said:**
> vlc should play them by default but may want to install ubuntu-restricted-extras in order to get full support in most apps.

```
sudo apt-get install ubuntu-restricted-extras
```

---

### Post by Morpheun on 2008-08-18
[https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%208.04](https://help.ubuntu.com/community/RestrictedFormats#Ubuntu%208.04)

use that guide

---

### Post by Georgia boy on 2008-08-19
Thanks for the responces. Is Vic a restricted format or the Ubuntu supported format? When I clicked on the WMV link that was in the email sent, nothing happend. 

I went to the link that Morphen sent and it has some interesting reading there. I noticed that it mentioned OGG VOrbis and OGG Theora. What are those? 

Would they be able to play automatacilly the WMV and WAV files like Openoffice.org does for the ppt? Or is this something totally and completly different?

Thanks in advance for the help.

Tom

---

### Post by ace007 on 2008-08-19
Formats that do not come supported out of the box can be remedied by installing the restricted package above.  They are not included out of the box due to some sticky legal issues.

By installing the package above the codecs will be automatically installed in a place that all applications can now access them.  You will need to install a media player that recognizes the .WAV filetype as something it should open.

Rhythmbox is the default music player I think.  

Ogg is just another container type, like .mp3 or .wav. Vorbis describes the compression algorithm used to squeeze the file down to a acceptable size. Ogg is open source and is the "preferred" format of the open source community.  Technically speaking everytime you buy an mp3 or wmv or many others, you're suppose to pay a few pennies to the guy who invented it. Whereas Ogg is for anyone to use.

---

### Post by halitech on 2008-08-19
> **Georgia boy said:**
> Thanks for the responces. Is Vic a restricted format or the Ubuntu supported format? When I clicked on the WMV link that was in the email sent, nothing happend. 
VLC is actually a program (Video Lan ???, it slipped my mind at the moment) that will play almost every format with no need to install anything else

> I went to the link that Morphen sent and it has some interesting reading there. I noticed that it mentioned OGG VOrbis and OGG Theora. What are those? 
they are just different compression formats that are free as opposed to the windows versions of wma/wmv which you have to pay to use.

> Would they be able to play automatacilly the WMV and WAV files like Openoffice.org does for the ppt? Or is this something totally and completly different?

if you download (or have one on your system already) you can right click - open with and select the media player you want and put a check in where it says always use

> Thanks in advance for the help.

Tom

very welcome and hope it helps :)

---

### Post by Georgia boy on 2008-08-20
Halitech, I haven't checked that out yet. Is VLC in the regular downloads for Ubuntu already downloaded or do I have to just download and apply and I'll be able to view the other stuff? Is it listed as VLC?

That would be great! I'll have to check that out. Stll learning as you can see.

I really appreciate everyones help. I'm wanting to be fully open source on Ubuntu. So, I'll be also looking at how to download the free MP3's from Cnet music downloads as a different format. I'm going to try and stay away from proprietary stuff. That's why I'm even using stuff such as Openoffice.org on my Windows system also.

Again thanks for all of your help!!!! :)

Tom

---

### Post by Georgia boy on 2008-08-21
Hi. I found VLC in the all open source applications of the add/remove applications section. It mentions that it is provided by the Ubuntu community. Does that mean that it is approved by Ubuntu or just introduced and used by the Ubuntu users?

This isn't a restricted application right? It is completely open source that is just not supported? How does it get updated or does it if not supported? Just wondering.

So, I just go into the All Open Source section and check VLC and apply and then I should be able to watch those WMV files sent to me.
If so, then I'll have to check it out.

Thanks for all of the help information. I really appreciate it. I'm always trying to learn something new. Eventually I want to completely convert over to Linux from Windows. So the more I learn the easier it will be and the better off I'll be.
Thanks
Tom

---

### Post by anotherdisciple on 2008-08-21
I'll give you 2 months... it's an easy transition IMO. I dual booted Vista for a few months and realized that I never used vista... so when I upgraded... I just formatted straight over the vista partition.

It takes a little know-how to get things set up the way you like them in linux (especially if you are used to windows), but after that... it's pretty user friendly. That's why I usually set up linux for my friends. I install all the codecs, java, fonts, vlc, wine, etc. ... make sure all of their hardware is working... and after that... they don't have too many questions or problems.

My only problem that I can't completely figure out in ubuntu is how to get my suspend to work EVERY TIME. It's extremely inconsistent. Not that big of a deal though. If you turn off unused services, set grub to load the default immediately, etc. It starts up pretty fast.

---

### Post by Georgia boy on 2008-08-23
Okay, downloaded the VLC. Didn't work for some reason. Said it needed some codes or something. Tried to download them but don't know if it came out right or not. When I tried to play the WMV file it still wouldn't work. So, I removed the VLC to see if you could help me figure out what I'm doing wrong. 

Any ideas?  Maybe having trouble understanding but still trying to learn what I can. 

Thanks in advance!!!!!!!!!
Tom

---

### Post by garyed on 2008-08-23
I use Totem movie player & it does everything I need especially wmv & mp3.
It should be in the   Applications>>Add/remove 
When I first clicked on a wmv file it didn't natively support it just asked
if I wanted to download the add ons & it did it all for me. If you're still having trouble you might try it because it was very simple.
Just FYI the add on is called Gstreamer.

---

### Post by Georgia boy on 2008-08-24
Thanks Gary.I was checking in the applications and it shows I have both Totem and Gstreamer added. Wonder what I'm doing wrong.
Have to check it out.

Thanks
Tom

---

### Post by garyed on 2008-08-24
If you click on the file does Movie player open?
If not you might try right clicking on it & select "open with" / "another 
application" & look for Movie Player.

---

### Post by Georgia boy on 2008-08-24
It opens. But it says that I need something. When I tell it to search it comes back and say that there is another Gstreamer I need. When I read what it tells me I find that the Gstreamer is from a restricted site. How can this be when I also notice that it has the little icon showing that it is a Ubuntu community supported item or am I misreading this?  :confused:

Just don't make sense. I would have thought that this would be supported by an open source. The other Gstreamer I downloaded before is an open source. Just can't figure out this one. Don't really want to go to the restricted downloads due to the copyright thing. :(

Any ideas?

Thanks
Tom

---

### Post by garyed on 2008-08-24
I seem to remember that gstreamer has some sort of copyright but I think its OK for personal use(just guessing). I'm pretty sure you could find something else that would work if you're nervous about it but that's all i use.

---

### Post by lyni on 2008-08-24
have you installed the ubuntu restricted extras? they are in the synaptic package manager. all you have to do is click on it and mark it for installation and click apply. it does it all for you.

---

### Post by Georgia boy on 2008-08-24
Thanks guys. I went ahead and downloaded the Gstreamer. Works like a champ. I had checked out the Gstreamer site. Says that they are Open Source. So, why is this in the restricted zone?
Here is the site I visited:

[http://gstreamer.freedesktop.org/apps/](http://gstreamer.freedesktop.org/apps/)

Very interesting site. An open source but still restricted? 

Any how all of you guys are the greatest!!!!! 

Thanks a bunch!!

I'm happy now. I can watch what they send me from their Windows.:popcorn:
Tom

---

