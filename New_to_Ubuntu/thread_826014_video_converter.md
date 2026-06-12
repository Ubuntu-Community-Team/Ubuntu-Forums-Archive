---
title: "video converter"
date: 2008-06-11
forum: New to Ubuntu
---

### Post by lunaluna on 2008-06-11
i need one for converting among varius formats and in good quality (if possible)...
any recommendations? :popcorn:

---

### Post by Cypher on 2008-06-11
[FFMPEG]("http://ffmpeg.mplayerhq.hu/") is king.

---

### Post by lunaluna on 2008-06-11
> **Cypher said:**
> [FFMPEG]("http://ffmpeg.mplayerhq.hu/") is king.

can i find this on the repos?
does it have a gui?

---

### Post by wolfen69 on 2008-06-11
winff is the gui for it.

---

### Post by decoherence on 2008-06-11
not sure about a GUI for ffmpeg. You might look at gtranscode, a front end for transcode, which is another command-line video converter.

i haven't got a pile of experience with it though. i'm happy with ffmpeg on the command line.

---

### Post by Cypher on 2008-06-11
FFMPEG is definitely avialable in the [repos]("http://packages.ubuntu.com/hardy/ffmpeg"). But know that the version in the repo doesn't have MP3 audio support for legal reasons. So you'll want to recompile FFMPEG with MP3 support using these links as guides:
[http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server](http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server)
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)

---

### Post by lunaluna on 2008-06-11
what is the latest version of ffmpeg?

---

### Post by Sirocco on 2008-06-12
**mencoder**, **ffmpeg**, **gstreamer**  (comand-line) from package manager and simple script for Nautilus [http://www.gnome-look.org/content/show.php/avi+%26+mp4+converter?content=64899]("http://www.gnome-look.org/content/show.php/avi+%26+mp4+converter?content=64899")

---

### Post by FakeOutdoorsman on 2008-06-12
> **lunaluna said:**
> what is the latest version of ffmpeg?
The developers of ffmpeg don't make regular releases.  They recommend getting the latest source code and compiling it yourself.  As mentioned before, ffmpeg in the Ubuntu repos has not been compiled to support restricted formats.  You can either use a different program (such as mencoder), use a third-party repository that has a compiled version of ffmpeg that supports restricted formats (such as [Medibuntu]("http://www.medibuntu.org/")), or compile it yourself.  If you don't mind compiling, then refer to my guide [HOWTO: Compile the latest ffmpeg and x264 from source]("http://ubuntuforums.org/showthread.php?t=786095").  Since I don't use WinFF, I'm unsure if it works with a recent version of ffmpeg due to the option names often changing between revisions.

---

### Post by Paradoxfox93 on 2008-06-14
> **Cypher said:**
> FFMPEG is definitely avialable in the [repos]("http://packages.ubuntu.com/hardy/ffmpeg"). But know that the version in the repo doesn't have MP3 audio support for legal reasons. So you'll want to recompile FFMPEG with MP3 support using these links as guides:
[http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server](http://symbiotix.net/articles/compiling-ffmpeg-mp3-ubuntu-revised-ubuntu-gutsy-server)
[http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/](http://po-ru.com/diary/bleeding-edge-ffmpeg-on-ubuntu-feisty/)


make[1]: Entering directory `/home/chakravanti/ffmpeg/libswscale'
Makefile:20: ../subdir.mak: No such file or directory
make[1]: *** No rule to make target `../subdir.mak'.  Stop.
make[1]: Leaving directory `/home/chakravanti/ffmpeg/libswscale'
make: *** [install-headers] Error 2

****  Installation failed. Aborting package creation.

I get this following the fiesty instruction on the checkinstall

---

### Post by cariboo on 2008-06-14
Install the ubuntu-restricted-extras and it will install most of the codecs you will need for multimedia, including flash and java.

Make sure you have all the repositories selected. To do this go to System-->Administration-->Software Sources and make sure all the boxes are ticked except for the CD-ROM click the close button and will be asked to reload, do that, and your ready to go. After you have done this go to System-->Administration-->Synaptic Package Manager, search for ubuntu-restricted-extras, mark it for installation and click apply. It is going to isntall around sixty packages so you might as well go get a cup of your favorite beverage and it should be done, depending on your internet connection.

---

