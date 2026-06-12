---
title: "Help installing Timidity"
date: 2008-05-02
forum: New to Ubuntu
---

### Post by monstercometh on 2008-05-02
Hello all,
Before I begin, I would just like to say I am a complete noob at ubuntu 8.04. My friend recommended it to me as something to fool around with on my old laptop that sits around collecting dust. So please don't take offense to anything ridiculous I might be saying :)

I wanted to get Guitar Pro 5 on my laptop as I am something of a part-time musician (I realize there are better linux alternatives like Tuxguitar, but I want to have the exact functionality as the rest of my bandmates to prevent compatibility issues in the future). So I did the whole jig with WINE and installing the setup.exe, which worked 100% except for the sound. Now, I knew this would be a problem because I had read about it before I started. People were recommending "Timidity" to get MIDI functionality, so I went to the website and downloaded the tar.gz, extracted to desktop. I had experience from installing flash player (heh), so I pretty much winged it and hoped for the best.

This is what happened:
1) Open terminal, "cd" to destination folder
2) Typed "./configure" because that seemed like the main file in the package
3) This shows up:
checking build system type... i686-pc-linux-gnulibc1
checking host system type... i686-pc-linux-gnulibc1
checking target system type... i686-pc-linux-gnulibc1
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking whether grep returns status... yes
checking if --enable-debug option specified... no
checking for emacs... no
checking for xemacs... no
checking for gcc... gcc
checking for C compiler default output file name... configure: error: C compiler cannot create executables
See `config.log' for more details.

Looked around for what to do next seeing as there was an error, and found out I am supposed to type "make" and then "make install". Typed it into terminal, and this error shows up:
make: *** No targets specified and no makefile found.  Stop.

Any suggestions? I'm pretty sure I set up the ALSA driver correctly since my sound works fine as well as microphone. Also seems like I configured WINE right because I have xfire and ventrilo working correctly. Again, I'm a complete noob so I could be completely wrong.

Cheers to all, I look forward to my escapades in ubuntu :)
--monster

---

### Post by spiderbatdad on 2008-05-02
Timidity is in synaptic package manager. Seems it causes a problem with some files in my system...sorry if I sound lost. 
However, in the process of installing timidity and uninstalling it, some how Totem inherits and retains the ability to play midi files. As a quirk, after the file plays, Totem says it needs to search for a codec and cannot play the file.  So, I have to close that dialogue, but Totem does play the file. You might be very interested in Rosegarden, also in synaptic for tansposing midis into sheetmusic, creating multi tracks, etc, etc, Rosegarden is a very powerful tool.

The reason you have been unable to compile the tar package is that you need to install build-essential first.```
sudo apt-get install build-essential
```

---

