---
title: "HOWTO: Install Sofa Media Center"
date: 2007-06-07
forum: Outdated Tutorials &amp; Tips
---

### Post by squidy on 2007-06-07
Here is how to install [Sofa Media Center]("http://sofa.sf.net") on your Ubunbu (all versions):

[LIST=1]
[*]Sofa depends on Clutter, a library for rich graphical user interfaces. To install Clutter, you will first need to add one of theses sources to your system based on your current installed version of Ubuntu:
```
deb [http://debian.o-hand.com](http://debian.o-hand.com) dapper/
deb [http://debian.o-hand.com](http://debian.o-hand.com) edgy/
deb [http://debian.o-hand.com](http://debian.o-hand.com) feisty/
```

Once the sources added, run this command to get the new packages names:
```
sudo apt-get update
```
[*]Once the update is done, run this command to install all required Clutter dependancies:
```
sudo apt-get install libclutter-0.2-0 libclutter-0.2-dev libclutter-cairo-0.1-0 libclutter-cairo-0.1-dev libclutter-gst-0.1-0 libclutter-gst-0.1-dev
```

[*]To build Sofa, you will need these packages installed, which you might already have installed if you often build software on your machine:
sudo apt-get install build-essential libgconf2-dev libdbus-glib-1-dev libsigc++-2.0-dev libtool intltool libgstreamer-plugins-base0.10-dev

[*]You will first need to download the latest release from Sourceforce [here]("http://sourceforge.net/project/showfiles.php?group_id=192958"). In this guide, we'll use sofa-0.2.2.tar.gz. Place it in your favorite place to work, we'll assume it is your home directory. Use this command to decompress it.
```
tar xzvf sofa-0.2.2.tar.gz
```


[*]You should now have a sofa-0.2.2 directory containing all the files to build Sofa. Run these three commands to build and install Sofa on your system.
```
./configure --prefix=/usr
make
sudo make install
```
[*]Only the demo module is turned on by default. To activate other modules, you have to run sofa-config. You have to place a check in all the modules you want in the column Active.

[/LIST]

Uninstallation:

1. From the sofa-0.2.2 folder you extracted at step 5, write: 
```
make uninstall
```

---

### Post by PsychedelicReaction on 2007-06-08
i get this error in the configure stage
> 
Package gstreamer-plugins-base-0.10 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gstreamer-plugins-base-0.10.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gstreamer-plugins-base-0.10', required by 'clutter-0.1', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

i tried with apt but that package doesn't seem to exist

---

### Post by sabrewolf2006 on 2007-06-08
nevermind :)

---

### Post by sabrewolf2006 on 2007-06-08
> **PsychedelicReaction said:**
> i get this error in the configure stage

```
Package gstreamer-plugins-base-0.10 was not found in the pkg-config search path.
Perhaps you should add the directory containing `gstreamer-plugins-base-0.10.pc'
to the PKG_CONFIG_PATH environment variable
Package 'gstreamer-plugins-base-0.10', required by 'clutter-0.1', not found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables DEPS_CFLAGS
and DEPS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```
i tried with apt but that package doesn't seem to exist

the package it requires is gstreamer0.10-plugins-base-dev
which is the development headers of gstreamer0.10-plugins-base

the package names don't always correlate with the deb package name (which is annoying but hey)</rant>

Hope this helps

---

### Post by sabrewolf2006 on 2007-06-08
> **squidy said:**
> Hi!

I've written an how to install Sofa Media Center, which is a new app I created in the last months.  I'm looking forward to all your comments.:p

[How to Install Sofa Media Center]("http://sofa.sourceforge.net/?s=downloads").

Wow, like it.. can't wait to see this project grow..
A gtk MMS :D
[http://wiki.mymediasystem.org/wiki/index.php/What_is_MMS](http://wiki.mymediasystem.org/wiki/index.php/What_is_MMS)

---

### Post by sabrewolf2006 on 2007-06-08
Here's a couple of improvements you could make.. (you probably had some of these in mind anyways)


1. Fetch cover art via D-BUS for rhythmbox
(I store my cover art within the library.. for example /home/music/Alien Ant Farm - ANThology/cover.jpg

Rhythmbox can display this and displays it in the preview too..

2.Use GStreamer to interpret filetypes for video..
GStreamer is able to tell you what files it can play (video or otherwise)..

Sofa currently only lists files ending .mpg (I put .mp4 and .ogg and .vob in ~/ )

although you could probably abstract this to libtotem and it will handle it..

3. Video library location..
Will it be possible to change the video library location through sofa-config?

---

### Post by ellow on 2007-06-08
> **sabrewolf2006 said:**
> the package it requires is gstreamer0.10-plugins-base-dev
which is the development headers of gstreamer0.10-plugins-base

the package names don't always correlate with the deb package name (which is annoying but hey)</rant>

Hope this helps

the package name is libgstreamer-plugins-base0.10-dev, with:

    sudo apt-get install libgstreamer-plugins-base0.10-dev

works fine.

---

### Post by squidy on 2007-06-09
> **ellow said:**
> the package name is libgstreamer-plugins-base0.10-dev, with:

    sudo apt-get install libgstreamer-plugins-base0.10-dev

works fine.

Thanks, I added it to the manual.

---

### Post by squidy on 2007-06-09
> **sabrewolf2006 said:**
> Here's a couple of improvements you could make.. (you probably had some of these in mind anyways)


1. Fetch cover art via D-BUS for rhythmbox
(I store my cover art within the library.. for example /home/music/Alien Ant Farm - ANThology/cover.jpg

Rhythmbox can display this and displays it in the preview too..

2.Use GStreamer to interpret filetypes for video..
GStreamer is able to tell you what files it can play (video or otherwise)..

Sofa currently only lists files ending .mpg (I put .mp4 and .ogg and .vob in ~/ )

although you could probably abstract this to libtotem and it will handle it..

3. Video library location..
Will it be possible to change the video library location through sofa-config?

Hi, 

Thanks for your suggestions, I do have plans but I am open to suggestions:

1. It is already there, sofa looks for album art saved by the "Album Art plugin".  But I've seen rare occasions in the latest Rhythmbox where the album art would only show on rhythmbox... 

2. I'll add .mp4, .ogg, and .vob in the next update, I'll have a look at libtotem!

3. I sure did have this planned... My videos are not in my home neither :)

In the mean while, I do have some bugs to correct: the videoplayer does not respect aspect ratio is on.  I'd like a better UI too!

Thanks for your comments.

---

### Post by ellow on 2007-06-09
when compile, whit make i have this error:

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libclutter-cairo-0.1.so: undefined reference to `cairo_set_user_data'
collect2: ld returned 1 exit status
make[3]: *** [sofa] Error 1
make[3]: se sale del directorio `/home/ellow/sofa-0.2.2/src'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/ellow/sofa-0.2.2/src'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/ellow/sofa-0.2.2'
make: *** [all] Error 2


please help

---

### Post by squidy on 2007-06-09
Never saw this, what version of Cairo do you have?  You should have Cairo 1.4.2 or later...

---

### Post by ellow on 2007-06-09
i have cairo 1.4.2-0ubuntu1

---

### Post by sabrewolf2006 on 2007-06-09
> **squidy said:**
> Hi, 

Thanks for your suggestions, I do have plans but I am open to suggestions:

1. It is already there, sofa looks for album art saved by the "Album Art plugin".  But I've seen rare occasions in the latest Rhythmbox where the album art would only show on rhythmbox... 

2. I'll add .mp4, .ogg, and .vob in the next update, I'll have a look at libtotem!

3. I sure did have this planned... My videos are not in my home neither :)

In the mean while, I do have some bugs to correct: the videoplayer does not respect aspect ratio is on.  I'd like a better UI too!

Thanks for your comments.

Awesome, what are your plans.?
I could see GNOME inclusion the way this is going.. way to equivalence with Windows Media Centre

I  think the UI you've got is pretty sweet actually - nice and simple.. could do with tweak in regards to long titles 

I'd like to help ya out.. but I have almost no programming experience.. short of bash scripting and doing a couple of tutorials in C and C#.. nothing special

---

### Post by squidy on 2007-06-09
Well the plans are : 
- stabilising the current version
- add full support for translationa (the code is there, but they are not installed)
- create .deb, rpm and gentoo ebuild
- slight adjustment in the UI (includes long-title support, current playing status, better video file navigation), 
- add a menu entry at install
- clean-up of the UI code
- submit a patch to Rhythmbox giving it a more complete dbus API which would result in a better Sofa experience
- add a F-spot module

Any other idea?

I guest the best place to save those feature would be the bugtraker...

---

### Post by sabrewolf2006 on 2007-06-09
Apart from those changes I listed earlier in relation to the UI which you've got covered.. nope -
its all good :)

Ooh an F-Spot module.. like slideshow to music type thing.. Awesome :D (could just about convince me to reinstall mono for that.. would eog be more suited to this since its part of gnome?)

probably

---

### Post by squidy on 2007-06-09
Well F-Spot has a photo catalog which eog does not have.. and on my Ubuntu install, F-spot is installed by default I think.

---

### Post by sabrewolf2006 on 2007-06-09
Oh yes of course - duh! (sorry, I need sleep)

I've started planning an RSS reader and drawing mockups..
(basic idea is that the feed is added via browser.. an 'Add this feed to sofa' extension to epiphany/firefox to avoid adding cruft, just fetching from a file list from wherever)
Have you already got the basics of one or am I going onto new ground?

---

### Post by squidy on 2007-06-09
Go ahead! I have not started a RSS reader.  Instead of implementing one, isn't there one we could interface with?  Gnome Reader, Firefox's toolbar, anyother... we would simply need to extract current watched rss feeds and display them...

You will have to create a new menu type to display a lot of text... 
Have fun ;)

---

### Post by sabrewolf2006 on 2007-06-10
That was what I was thinking.. integrate with the 'Live Bookmarks' or something

There is a GNOME project called Straw that may be worth looking at.. or Blam

Would it be possible to have a menu/panel that simply displays the webage generated (For the Firefox Live Bookmarks idea) as a first step?

Ack! Talk about throwing myself in at the deep end!

Can you suggest a 'dummy' menu type that I can copy and turn into textview (this is what I'm going to call the new menu type)?

In my mockups on this I have the menu filling the whole screen, minus the top section where it says sofa..
(considered having music playing while viewing rss.. is this possible? I have noticed the music is paused whenever you leave the rhythmbox module)

I have attached what I've got so far.. very little changes in regards to making a 'simple' module other than renaming it.. but I have included a file with thoughts on how to get started with this

Tell me what ya think to the mockups.. is this what you had in mind for an RSS module?

---

### Post by squidy on 2007-06-11
Hi Craig,

This forum isn't the place to discuss technical details, I created a Feature request to keep this details.  Please continue your work there.  

[http://sourceforge.net/tracker/index.php?func=detail&aid=1735104&group_id=192958&atid=943496](http://sourceforge.net/tracker/index.php?func=detail&aid=1735104&group_id=192958&atid=943496)

I rapidely checked your code, you seem on a good start!  I included some tips on how to implement the menus in the Feature Request.  I also added my though on how the UI should work.

---

### Post by LaSaDa on 2007-06-13
Hi,
this sounds like an awesome project, but i cant install it.. When i (inside the terminal) try to "sofa-config" i get this message:
> sofa 0.2.2
Copyright (c) 2007 Pierre-Luc Beaudoin
This is free software.  You may redistribute copies of it under the terms of
the GNU General Public License <http://www.gnu.org/licenses/gpl.html>.
There is NO WARRANTY, to the extent permitted by law.


(sofa-config:17700): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(sofa-config:17700): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(sofa-config:17700): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed
Segmentation fault (core dumped)

any ideas?

---

### Post by thelovebug on 2007-06-13
> **LaSaDa said:**
> Hi,
this sounds like an awesome project, but i cant install it.. When i (inside the terminal) try to "sofa-config" i get this message:


any ideas?

For what it's worth, I get the exact same message for both sofa-config and sofa itself.

---

### Post by squidy on 2007-06-14
> **LaSaDa said:**
> Hi,
this sounds like an awesome project, but i cant install it.. When i (inside the terminal) try to "sofa-config" i get this message:


any ideas?

Try rebooting your computer (easiest way to restart gconfd) because there is a filed bug with it: it doesnot see installed schemas before being restarted.  You can also wait a little, I should release Sofa 0.2.3 in the next week which as a complete patch to this.

---

### Post by LaSaDa on 2007-06-15
Already tried that :b but i guess ill just have to wait then :)

---

### Post by squidy on 2007-06-15
I'm looking for help to build .deb for Ubuntu, anyone wants to help?

---

### Post by phoenixnr on 2007-06-20
(sofa-config:17700): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(sofa-config:17700): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed

(sofa-config:17700): Pango-CRITICAL **: pango_color_parse: assertion `spec != NULL' failed
Segmentation fault (core dumped)

Same error for me. :( Any dates on the next version?

---

### Post by phoenixnr on 2007-06-23
Bump

---

### Post by FatAngus on 2007-06-23
I also get the same error:(

---

### Post by squidy on 2007-07-01
Sofa 0.2.3 is out.  It solves this bug.  

Sorry for the late answer, I was moving!

---

### Post by William the Conquerer on 2007-07-01
I just tried 0.2.3 and I'm getting the following error:

/usr/lib/gcc/i486-linux-gnu/4.1.2/../../../../lib/libclutter-cairo-0.1.so: undefined reference to `cairo_set_user_data'
collect2: ld returned 1 exit status
make[3]: *** [sofa] Error 1
make[3]: Leaving directory `/home/william/compile/sofa-0.2.3/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/william/compile/sofa-0.2.3/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/william/compile/sofa-0.2.3'
make: *** [all] Error 2

when I run make

---

### Post by idn on 2007-07-03
I got this working but there is a problem with all the images including the RB artowrk, its all scrambed, although it is loading the correct image.

Maybe integration into MPD would be a good idea? Nice project though and it looks very promising, also congrats on your good documentation!!

---

### Post by squidy on 2007-08-03
William: apparently you don't have the correct Cairo version.  What version are you using? What version of Ubuntu are you on?

---

### Post by squidy on 2007-08-03
What is MPD? never heard of it.  You are the first to report this image scrambling bug... can you try running the Clutter demos and see if they render correctly, it might be on their side.

Oh and by the way, Sofa 0.2.4 is out!

---

### Post by stijngysemans on 2007-09-01
nice program
hopefully the f-spot plugin is coming soon!

---

### Post by alohre on 2007-09-24
anyone have sofa running on gutsy ? I found all the clutter packages already in the gutsy repos, except the cairo one. Altso trying to compile it myself (clutter 0.4) results in sofa not finding the clutter libs at all. Any suggestions/ideas ?

---

