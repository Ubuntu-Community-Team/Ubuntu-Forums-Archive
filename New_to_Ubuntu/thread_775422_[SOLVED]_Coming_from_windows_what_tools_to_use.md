---
title: "[SOLVED] Coming from windows what tools to use?"
date: 2008-04-30
forum: New to Ubuntu
---

### Post by nhasian on 2008-04-30
Finally took the plunge and installed Ubuntu 8.04 on my HP DV9500t laptop.  I need some help finding out what programs in linux to use instead of the windows counterpart.  

For example in windows I commonly use uTorrent, Alcohol 120%, imgburn, firefox and thunderbird.

Firefox is already installed in Hardy Heron, and I was easily able to install Thunderbird via the add/remove button and set it as the default mail client.

So what do i use in place of uTorrent, Alcohol 120% and imgburn?

---

### Post by kesman on 2008-04-30
You could use Deluge for bittorrent, and for image mounting, you don't need any special tools. Dunno if the file browser in Hardy supports it but you might be able to mount an image by simply with right-clickin it and selecting mount or something if it's there.
Otherwise, it could be done via terminal. Let's say you have an image file in your /home -dir and it's name is image.iso. Then you would simply put in terminal:
```

mkdir /home/username/mountpoint
sudo mount -o loop /home/user/image.iso /home/user/mountpoint
sudo chown user /home/user/mountpoint

```
and it's there.

---

### Post by howlingmadhowie on 2008-04-30
for uTorrent i'd suggest one of:
Transmission (is already installed)
Azureus (is in the repositories)
rtorrent (commandline torrent client/server).

personally i use rtorrent installed in a screen session on my nas. it regularly has uptimes of more than a month and the whole thing uses about 5W.

i've never heard of Alcohol_(computer_program)
imgburn sounds like a dvd/cd burner. the gnome desktop has one installed. if you want something with more options, you can always install k3b

---

### Post by Ek0nomik on 2008-04-30
> **nhasian said:**
> Finally took the plunge and installed Ubuntu 8.04 on my HP DV9500t laptop.  I need some help finding out what programs in linux to use instead of the windows counterpart.  

For example in windows I commonly use uTorrent, Alcohol 120%, imgburn, firefox and thunderbird.

Firefox is already installed in Hardy Heron, and I was easily able to install Thunderbird via the add/remove button and set it as the default mail client.

So what do i use in place of uTorrent, Alcohol 120% and imgburn?

uTorrent:  Deluge, kTorrent, Transmission, rTorrent.
Burning Programs:  Gnomebaker, K3b.

There are plenty others as well, just run a Google search and you will get tons of software names.

---

### Post by cartisdm on 2008-04-30
+1 for Azureus

---

### Post by Ek0nomik on 2008-04-30
Azureus is a bit heavy on resources.  Just a word to the wise.

---

### Post by hyper_ch on 2008-04-30
I also favor rTorrent + screen

As for burning programs you might want to add Brasero... although I think K3B is the best one.

---

### Post by piratesmack on 2008-04-30
> **nhasian said:**
> Finally took the plunge and installed Ubuntu 8.04 on my HP DV9500t laptop.  I need some help finding out what programs in linux to use instead of the windows counterpart.  

For example in windows I commonly use uTorrent, Alcohol 120%, imgburn, firefox and thunderbird.

Firefox is already installed in Hardy Heron, and I was easily able to install Thunderbird via the add/remove button and set it as the default mail client.

So what do i use in place of uTorrent, Alcohol 120% and imgburn?

**uTorrent:** use Transmission (preinstalled). Or uTorrent is even designed to run in Wine.

**Alcohol_120%:** I'm not sure what you use it for, but Ubuntu already has everything it needs to extract isos from cds, mount isos etc
If you want to mount an iso, just run the command
```

sudo mount -o loop NAME.iso /media/cdrom

```

**imgburn:** The default burner, Brasero, should be good enough

---

### Post by vishzilla on 2008-04-30
bittorrent: Deluge (utorrent-like) or the default Tranmission

Alcohol: Terminal as mentioned above

imgburn: Brasero or K3B

---

### Post by MaindotC on 2008-04-30
nhasian - if you ever need a table of Linux equivalent software from Windoze, I have a couple of bookmarks:

[http://gentoo-wiki.com/Windows_equivalent_programs](http://gentoo-wiki.com/Windows_equivalent_programs)
[http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software](http://www.libervis.com/wiki/index.php?title=Table_of_Equivalent_Software)
[http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software](http://wiki.linuxquestions.org/wiki/Linux_software_equivalent_to_Windows_software)

I used keywords "Linux equivalent software".  And of course you usually can type the program name + linux in Google and find something as well.

---

### Post by park8b156 on 2008-04-30
Just remember if you want to burn .avi files you have to convert the file to ISO image using DeVeDe,  then it will throw it to your home folder. Next you can use K3B to burn the File to DVD.

---

### Post by erginemr on 2008-04-30
You can also use **gmountiso** as a frontend to mounting ISO images from terminal:
[http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/](http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/)
You can install it either from Synaptic or from the terminal with:
```
sudo aptitude install gmountiso
```

For linux alternatives to windows programs, you can also refer to:
[http://www.linuxalt.com/](http://www.linuxalt.com/)
in addition to the nice links given by **strAlan** before.

---

### Post by erginemr on 2008-04-30
You can also use **gmountiso** as a frontend to mounting ISO images from terminal:
[http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/](http://tuxenclave.wordpress.com/2007/12/01/gmount-iso-virtual-drive-for-linux/)

You can install it either from Synaptic or from the terminal with:
```
sudo aptitude install gmountiso
```

For linux alternatives to windows programs, you can also refer to:
[http://www.linuxalt.com/](http://www.linuxalt.com/)

in addition to the nice links given by **strAlan** before.

---

### Post by Paqman on 2008-04-30
I'm loving Transmission, actually. I used to use Azureus, but Transmission has all the features I liked about Azureus available from a much cleaner interface.

---

### Post by nhasian on 2008-04-30
wow thanks for all the helpful responses.  I hope when i become proficient enough with linux and Ubuntu that I can return the favor and help someone else out in the forums.

---

### Post by MaindotC on 2008-05-01
I think my post of all deserves a star...

---

### Post by Vicfred on 2008-05-01
I use 'emesene' for msn live replacement, XChat for IRC, VLC media player and Azureus for p2p. :D

---

### Post by MaindotC on 2008-05-01
Or you can just add a bunch of music videos to a playlist on youtube and select "play all".

---

### Post by MemoryDump on 2008-05-01
check this post I had started: [http://ubuntuforums.org/showthread.php?t=728001](http://ubuntuforums.org/showthread.php?t=728001)
it should give you an idea what most ppl are running under Linux :P

---

### Post by stchman on 2008-05-01
> **nhasian said:**
> Finally took the plunge and installed Ubuntu 8.04 on my HP DV9500t laptop.  I need some help finding out what programs in linux to use instead of the windows counterpart.  

For example in windows I commonly use uTorrent, Alcohol 120%, imgburn, firefox and thunderbird.

Firefox is already installed in Hardy Heron, and I was easily able to install Thunderbird via the add/remove button and set it as the default mail client.

So what do i use in place of uTorrent, Alcohol 120% and imgburn?

KTorrent is a great torrent client.
K3b is a great CD/DVD burning app.
K9Copy is a great program, like DVDShrink.

If running Gnome load the KDE libraries up at startup.

[http://www.stchman.com/kde_fast.html](http://www.stchman.com/kde_fast.html)

---

