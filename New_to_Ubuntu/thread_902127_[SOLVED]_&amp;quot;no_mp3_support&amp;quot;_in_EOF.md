---
title: "[SOLVED] &amp;quot;no mp3 support&amp;quot; in EOF song editor"
date: 2008-08-27
forum: New to Ubuntu
---

### Post by talknerdytome on 2008-08-27
I've only been running Ubuntu for 2 or 3 weeks now, but seem to be picking it up pretty quickly. I've gotten sucked into Frets On Fire and so of course now I'm trying to make my own songs...found EOF, downloaded the linux source file [here]("http://www.t3-i.com/eof.htm"). Searched the forums and found instructions for installing it [here]("http://ubuntuforums.org/showthread.php?p=5295087"). 

I added liballegro and then ran "make -f makefile.linux", that worked just fine. Then I realized I forgot the lame and oggvorbis support, so I installed those from Synaptic. Still getting "MP3 support disabled. Please install LAME and Vorbis tools if you want MP3 support". 

I ran "sudo apt-get install lame vorbis-tools" just to make sure, both were installed and up to date. I'm honestly not sure what I'm doing wrong here. Any ideas?

---

### Post by mcduck on 2008-08-27
> **talknerdytome said:**
> I've only been running Ubuntu for 2 or 3 weeks now, but seem to be picking it up pretty quickly. I've gotten sucked into Frets On Fire and so of course now I'm trying to make my own songs...found EOF, downloaded the linux source file [here]("http://www.t3-i.com/eof.htm"). Searched the forums and found instructions for installing it [here]("http://ubuntuforums.org/showthread.php?p=5295087"). 

I added liballegro and then ran "make -f makefile.linux", that worked just fine. Then I realized I forgot the lame and oggvorbis support, so I installed those from Synaptic. Still getting "MP3 support disabled. Please install LAME and Vorbis tools if you want MP3 support". 

I ran "sudo apt-get install lame vorbis-tools" just to make sure, both were installed and up to date. I'm honestly not sure what I'm doing wrong here. Any ideas?

Most likely you are missing the *development* libraries for lame & vorbis tools. (probably called lame-dev and vorbis-tools-dev, but you should check that with Synaptic/apt-cache).

Pretty much always when you get an error while compiling about some required package missing it's actually a development library that's missing, not the package itself.

---

### Post by northern lights on 2008-08-27
The following packages should resolve the issue```
sudo apt-get update && sudo apt-get install libvorbis0a libvorbisenc2 libvorbisfile3 libvorbis-dev vorbis-tools lame lame-extras liblame-dev liblame0
```

---

### Post by talknerdytome on 2008-08-27
I ran the command line Northern Lights gave above, everything installed fine. Restarted. Still the same error in EOF. Went back into Synaptic and searched through vorbis, lame, and mp3 to make sure I had all the right packages. I do have the development tools installed for vorbis and lame as well. I went ahead and installed several other things just to see if it would help, but still the same error.

* Update - turns out this is just an error within the Linux version. The guy who made the program replied to me at the Frets On Fire forums and verified that, hopefully there will be a fixed version out soon.

---

