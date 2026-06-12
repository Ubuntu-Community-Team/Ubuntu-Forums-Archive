---
title: "Why ubuntu is somuch internet dependent?"
date: 2008-05-31
forum: New to Ubuntu
---

### Post by rozan on 2008-05-31
I was using window before n i decided to shift to linux. I got installed ubuntu (hardy heron) which is the latest edition i guess. But as i installed ubuntu i found its music player cannot play a very common file format like mp3, it needs codec. So i downloaded this codec "gst-ffmpeg-plugin-0.10.4". 
When i tryed to configure, it shows error message  somethin like "no gstreamer- 0.10 >=0.10.13 (GStreamer) found".
Then again i tryed to install another media player "vlc-0.8.4a" again error, this time it says "missing header file ffmpeg/avcodec.h."
I searched how to install new applications but can only find installing new app. using synaptic package manager.
I cannot use synaptic coz i dont hav internet connection.
So how do i get this problem solved.

---

### Post by tacutu on 2008-05-31
there is an application called aptoncd which lets you create CDs for off-line installation. See if it suits your needs.

---

### Post by SunnyRabbiera on 2008-05-31
well truthfully windows is no better in some major respects...
most of the applications you would want would be on the net.

---

### Post by hovzio on 2008-05-31
Deb packages are cool... go to getdeb.net and download deb files. They are kinda like .exe, the problem are the dependencies. Some debs will work others will not due to the fact that thay need some other libs etc. Its worth a try.

Tacutu's idea is the way to go. You can have whole repos (whole might be an exageration, depends on the repo) on dvd and then setup apt to access the dvd.

---

### Post by attari on 2008-05-31
> **rozan said:**
> 

Because all the good stuff is out there! :)

[Cool Ubuntu Applications]("http://www.attari.net/index.php?My_space...:Ubuntu:Cool_Ubuntu_Applications")

---

### Post by anewguy on 2008-05-31
Actually, ubuntu is not dependent on the net.  If you want to do upgrades, install patches, download FREE software to use, etc., etc., etc., then you will need access to the net somewhere.  

If you back away from your immediate frustration (btw - there are a LOT of posts in this forum and the how-to's for getting all the flavors of multi-media going) and think about it, for most of the things you might want updates to (yes, there are codecs for media player, etc., for Windows as well) you need internet access as well.

So, if we back away from that assumption we get to your problem - apparently the computer you have installed Ubuntu on has no way to access the internet (or perhaps it is wireless and you might need help setting that up?).  Still, you have access somewhere to internet or you wouldn't be posting here.  There are ways to pull the files you want down to a Windows computer and then put them on a media you can use in your Ubuntu machine.  I always hated this answer when I was starting out, but the truth of the matter is that you will be far better served looking through these forums for information on doing so rather than us tell you.  I know that sounds lousy, but you really do have to be able to search these forums on your own to try to find answers.  I'm not trying to be cruel to you, just honest from my own experience (what experience I actually have).

Best of luck, and please be patient with Ubuntu - it really is a completely different animal from Windows.

---

### Post by Martje_001 on 2008-05-31
Read [this](http://www.howtoforge.com/dvd_images_of_ubuntu_repositories) (if you have a dvd-burner and an internet connection somewhere (friend?) ).

---

### Post by edm1 on 2008-05-31
Well the debs of everything found in the repositories can be found at packages.ubuntu.com for example that [mp3 package is here]("http://packages.ubuntu.com/hardy/gstreamer0.10-fluendo-mp3").

---

### Post by ugm6hr on 2008-05-31
> **anewguy said:**
> There are ways to pull the files you want down to a Windows computer and then put them on a media you can use in your Ubuntu machine.

To get you started - this is worth reading:
[http://ubuntuforums.org/showthread.php?t=766683](http://ubuntuforums.org/showthread.php?t=766683) (make sure you take care reading just the Hardy / 8.04LTS stuff, and 32- vs 64-bit as relevant to you (since there is a lot of information regarding multiple Ubuntu versions in there).

Once you've worked out which packages you want - use this service to get them:
[http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/)

---

### Post by Abu_Dayya on 2008-05-31
I think ubuntu is not shipped with codecs in a base install is due to copyrights issues. Ubuntu is committed to being a FREE os. But you can install any other software yourself

---

### Post by alzwded on 2008-05-31
I can't remember if Medibuntu or ubuntu studio was the one with the codecs preinstalled (or neither for that matter) - if you ever need to reinstall try getting an ubuntu flavour which says it has them, like kiwi linux. As for the debs, gather all the names you need then apt-get --download-only and put them on a cd. And don't blame ubuntu for not having codecs, as far as i can recall xp doesn't have "basic" codecs beyond mp3 and it's own wm* formats, anything other than that you need to download anyway. Hope you will succede in playing all your files :)

EDIT: as far i can see, yes, kiwi linux adds support for a lot of things not included out of the box in ubuntu, such as codecs, dvd and pppoe support, and most of the packages come from the ubuntu repos

---

