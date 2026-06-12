---
title: "Howto: Convert anything to DVD using mplayer and tovid"
date: 2005-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by sapo on 2005-05-02
Hi, i took one week to find out how to convert my xvid stuff to DVD cause i just bought a new dvd recorder and the transcode package is "unstallable" here.. so i've found the sollution with a little (still alpha) aplicattion called **tovid**.

It is still a new project so it has its problems, but was the first application i could install and convert a xvid movie to DVD format in less then 10 minutes, so here i go ;)

You can read more about it in the official website @ [http://tovid.sourceforge.net/index.html](http://tovid.sourceforge.net/index.html)

And Here some Gui screenshots and explanation:
[http://tovid.sourceforge.net/guitour.html](http://tovid.sourceforge.net/guitour.html)

Basically to run tovid you will need the following packages:

mplayer
mjpegtools
ffmpeg
normalize
makemenu
makexml
dvdauthor
ImageMagick
mjpegtools
SoX
vcdimager

As almost all of this programs are "usefull" i think that almost everybody will have all of them already installed, if you does not, just apt-get it with synaptic  ;-)

To download tovid just go to:
[http://sourceforge.net/projects/tovid/](http://sourceforge.net/projects/tovid/)

To install it.. just use:

```

tar xzvf tovid_0.18b.tar.gz
cd tovid_0.18b
./configure
make
sudo make install

```

After installing just use (you will need python): 

```

./tovidgui.py

```

the interface is very simple to use, but i ll add some hints, the first time i used it i tried to make a dvd without menu and it didnt work, so just take a random jpg image to use as menu (just for testing).

First click in Add Menu and select your menu image, then just click in add video and give it a name.

Then just make your choices and click on Encode, it will give you a list of commands to be run, here i dont know why **the commands arent working**  ](*,) 

But i just copy and paste them on the terminal and it works like a charm  :grin: 

```

The following commands will be run:
=========================================
makemenu -ntsc -dvd -align left -background "/home/sapo/Desktop/8.jpg" -textcolor "rgb(255,255,255)" -highlightcolor "rgb(255,255,0)" -selectcolor "rgb(255,0,0)" "matrix.avi" "/tmp/menu"
------------------------
tovid -overwrite -ntsc -dvd -full -vbitrate 3000 -abitrate 224 "/home/sapo/matrix.avi" "/tmp/Matrix" 
------------------------
makexml -dvd -overwrite -menu "/tmp/menu.mpg" "/tmp/Matrix.mpg" "/tmp/Untitled_disc"
------------------------

```

Then just run:

```

dvdauthor -x "/path/to/disc_name.xml"

```


So, the program is REALLY SIMPLE to use.. so if anyone wants to know something about it just ask, i ll add some screenshots later ;)

---

### Post by Eatingdogs on 2005-05-08
Thanks a lot for the awesome guide! I've been looking at how to do this. I appreciate all the hard work man. I registered just to thank you!

---

### Post by RastaMahata on 2005-05-08
shouldnt this be moved to the HOWTO forums?

Anyway, I dont want to install mplayer :( boohoo

---

### Post by sk545 on 2005-08-02
Just to clarify a few things:

makemenu and makexml are NOT packages in the repository, they are scripts that come with tovid, so that needs to be edited above.

Also, normalize is now called 'normalize-audio' so install that instead than do 'ln -s /usr/bin/normalize-audio /usr/bin/normalize'.  Otherwise the tovid (0.19) configure step will say you don't have normalize.

Basically, here is the one line apt-command to install all the dependencies:

 # apt-get install wxpython2.5.3 normalize-audio imagemagick sox dvdauthor vcdimager transcode libdvdcss2 lsdvd mplayer-386 

You should have had python already installed as part of ubuntu.  You probably will have to apt-get mencoder-586 as well, although i am not quite sure which mencoder to install.  Mencodr-586 installed fine for me, so i just used that.  I mean there is something called a 'mencoder-custom', but its broken for now.

---

### Post by andy.parry on 2005-08-20
I've downloaded version 0.20 and am having problems installing it. Haven't tried version 0.18

The GUI is a seperate package, but no one seems to mention that, above. And the ./tovidgui.py  is part of that.

I presume that the gui should be installed into it's own directory, otherwise it would overwrite some of the files that are part of the tovid package.

The configuration file appears to be missing from the gui package I've got. i.e., I can't do ./configure in the gui directory.  The configure.in file is the only thing similar.

I think I'm like most users. We want to use Linux as it's fast and smooth and cool and we hate MS, but trying to install apps is a pain in the arse. Versions change quickly so the docs are always out of date. After you've spent hours looking through google for a solution and trying command after command you just want to blow your bloody brains out.

 ](*,) 

Good job I'm in the UK, where we can't get guns, eh!   [-X

---

### Post by sk545 on 2005-08-23
Yes, the gui and the script are separate.  There is a configure file in the gui tar.gz:

```

tovid-gui-0.20$ ls
aclocal.m4  config.status  icons       Makefile.am  README
AUTHORS     configure      INSTALL     Makefile.in  tovidgui.py
ChangeLog   configure.in   install-sh  missing      tovid-temp.I6B4I1
config.log  COPYING        Makefile    NEWS         tovid-temp.PdVuvb

```

> I presume that the gui should be installed into it's own directory, otherwise it would overwrite some of the files that are part of the tovid package. 

Nothing gets overwritten.  It all gets installed in /usr/local/bin.

---

### Post by Tralobyte on 2005-08-23
[QUOTE=andy.parry]I've downloaded version 0.20 and am having problems installing it.[/QUOTE]
Check out the HOWTO I made a couple days ago at [http://ubuntuforums.org/showthread.php?t=58665](http://ubuntuforums.org/showthread.php?t=58665) which does the same thing but uses LiVES and DVDStyler. I tested it with a pretty clean Ubuntu install, it doesn't take very long to set up, and I like the GUIs more than that of tovid. There is no need to use the command line unless you want to add subtitles, and using LiVES gives you an extra layer of control over the video.

Thanks for the HOWTO, though. Linux is all about choice and variety :)

---

### Post by sexycatsinhats on 2005-08-23
[QUOTE=andy.parry]I've downloaded version 0.20 and am having problems installing it. Haven't tried version 0.18

The GUI is a seperate package, but no one seems to mention that, above. And the ./tovidgui.py  is part of that.

I presume that the gui should be installed into it's own directory, otherwise it would overwrite some of the files that are part of the tovid package.

The configuration file appears to be missing from the gui package I've got. i.e., I can't do ./configure in the gui directory.  The configure.in file is the only thing similar.

I think I'm like most users. We want to use Linux as it's fast and smooth and cool and we hate MS, but trying to install apps is a pain in the arse. Versions change quickly so the docs are always out of date. After you've spent hours looking through google for a solution and trying command after command you just want to blow your bloody brains out.

 ](*,) 

Good job I'm in the UK, where we can't get guns, eh!   [-X[/QUOTE]

well, you could just download the debian package from [here](http://julien.valroff.free.fr/) which is a lot easier than compiling it.

---

### Post by sk545 on 2005-08-29
lol, i didn't even know it had a debian repo.  However, tovid 0.21 is out and fixes many things.  0.20 was a little buggy:

---

