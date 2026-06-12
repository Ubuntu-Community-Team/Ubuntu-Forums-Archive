---
title: "When playing tracks ripped by ruby ripper in Amarok song title changes."
date: 2008-11-29
forum: New to Ubuntu
---

### Post by osc1882 on 2008-11-29
Face Palm.jpg
Just when I think my digital life couldn't be happier, lol.
I have ripped quite a few disk using ruby Ripper to flac, ogg and mp3's and they have all turned out really great as far as I can tell. I love this ripper. 

But I went to go play them in Amarok and when I go to play one of these new tracks, as soon as I go to play the track, Amarok changes the title to the title of the last song on the cd. I went to right click on the file themselfs and they all show the correct song title. Amarok is not changing the tags themselfs just what is shows as the song title in side of Amarok. I need to find out what is going on, so I know if there is something wrong with my files, Amarok or just a setting that needs to be changed. 

To try to enplane more, lets say I'm playing this cd
[http://en.wikipedia.org/wiki/Meteora_(album](http://en.wikipedia.org/wiki/Meteora_(album))
I would put the cd in a play list and as soon as I started playing track 1, Amarok would change the song title from the correct song title to the track title "Numb", the last track on the cd. 

This is bad, I have to put my ripping on hold until I understand what is going on.

Anyone who can help, one thousand thank yous.

---

### Post by Xiong Chiamiov on 2008-11-29
If you are using KDE, the easiest way to rip CDs is to simply browse to it (audiocd:/ in dolphin or konqueror), pick the folder appropriate to the format you want the music in, and copy it to where you want it.

Are you having this problem while playing CDs, or playing ripped music?  Have you tried using a different player?  If it's ripped, what if you queue up several albums, or mix the tracks around?  Does it always show the title of the last song in the playlist, or is it the last song on the CD, even if that song isn't queued?

---

### Post by osc1882 on 2008-11-29
I have to use this ripper. It's ether this ripper or EAC useing wine, and I have had a lot of trouble doing the later and Ruby Ripper is awesome. But it has to be one or the other.

And it has to be Amarok because Amarok is the very best.

Even if I don't load the whole cd into a play list it still changes it in Aramok to the last track in the cd. Very odd. It doesn't do this to my Ogg rips.

---

### Post by osc1882 on 2008-11-29
Anyone?

---

### Post by osc1882 on 2008-11-30
Maybe I should move this? Would that help? Is that possible?

---

### Post by Xiong Chiamiov on 2008-11-30
Why is it that you have to use this particular ripping software?

---

### Post by mc4man on 2008-11-30
I used to see the same thing, what the solution  then was to encode to 2 codecs at once.

I tended then to encode to flac so I'd set up a low quality mp3 to run with it.

Afterwards i just deleted the mp3 folder.

Now it's not a problem using 0.5.3-1 on hardy and 0.5.4 on intrepid, don't remember what the other ver. was or were I got it.

(I just build any new ver. that comes out, though my main setup is hardy and 0.5.3-1 is working fine.

What version are you using?

Quickly built and ran the 0.5.4 on hardy doing just a single codec(neroacc) and no problem.
If you use either the .3 or .4 ver. and continue to have this issue let me know and I'll package and upload a .deb for you.

> Ruby Ripper is awesome; Amarok is the very best

Couldn't agree more

---

### Post by osc1882 on 2008-11-30
I got the install from getdeb.net. It is version 0.5.4

Right now i am using it to rip to Ogg, Flac and MP3 at the same time. The Oggs come out great but the other two change. And it's not even that Aramok changes the files, because it doesn't, I can still check out the tags out side of Aramok and it says the correct into. But if Aramok is doing this with only these files that I am making then there must be something wrong. 

I have to this or the windows program EAC because I have to be able to off set the CD rom and I need log files and cue files. Plus holy crap, once you set it up correctly Ruby Ripper will rip to up to 4 different formats at the same time with the click on one button. 

Is there a different, maybe better way to install ruby ripper? And I'll play around with maybe only ripping to two formats at once instead of 3. Even tho I need 3.

---

### Post by mc4man on 2008-11-30
I would go to the rubyripper site, download the source and build it yourself.

I believe it was a getdeb that was causing me the same issue

Not that many packages are needed to compile, you'd start with installing build-essential and take from there.

```
sudo apt-get build-essential checkinstall
``` 

You need a few specific packages for a full featured build, the readme inside the source tells but doesn't give the full names.

> 3. HOW TO INSTALL

Dependencies:
* cdparanoia
* ruby

Suggested:
* ruby-gettext (for translations)
* ruby-gtk2 (for gtk2 gui)
* cd-discid or discid (for proper freedb support)
* eject or diskutil for MacOS (for eject support)
* flac, oggenc, lame (if the codec is wanted)
* wavgain, vorbisgain, mp3gain (for replaygain support)
* normalize (for normalize support)

For instance ruby means libruby1.8
ruby-gettext means libgettext-ruby1.8
ruby-gtk2 means libgtk2-ruby1.8
(version #'s are for hardy, when available I also always install the -dev package also

I build a lot of sources so it's hard to tell what else is beneficial, but not that hard to work out.
when you run the configure it will tell you what's not enabled. A few things I've never satisfied even though I've tried, not to important here.

After running the make you can test from inside the source folder by running rubyripper_gtk2.rb (just double click on and choose 'run'

you can build yourself a package with checkinstall

After the configure just run make (vs. make install
Then test your build as described above, if good run
```
sudo checkinstall --install=yes
``` (or use no if you want to create the package and install later / used instead of the make install command

> doug@doug-desktop:~/Desktop/rubyripper-0.5.4 (2)$ ./configure --enable-lang=de,hu --enable-gtk2 --enable-cli --prefix=/usr
Checking the NEEDED dependencies....
cdparanoia found...

Checking the OPTIONAL dependencies...
Testing support for the graphical frontend...
ruby-gtk2 bindings found

Testing support for freedb metadata fetching...
cd-discid or discid found...

Testing support for ejecting the disk tray...
eject or disktutil found...

Testing support for different codecs on your system...
flac found...
oggenc (vorbis) found...
lame (mp3) found...

Testing support for replaygain...
wavegain NOT found.
vorbisgain found...
mp3gain found...

Testing support for normalize...
normalize NOT found
Creating the Makefile...
A summary of your settings:

Using the following locations for install:
* Executables: /usr/bin
* Localization files: /usr/share/locale
* Icon file: /usr/share/icons/hicolor/128x128/apps
* Desktop file: /usr/share/applications
* Ruby library: /usr/lib/site_ruby/1.8

Gtk2 frontend will be installed
Cli frontend will be installed
Languages to be installed: de, hu

You can now run make install
Make sure you've got the writing privileges


Before running the build version I'd go into home dir., find .rubyripper and for the moment rename it (.rubyripper1
It contains all your settings, if your build is good you can either redo any customizations in the gui or delete the new .rubyriper and rename the old one back and see how it goes.

Because I've changed some of the default encoding and naming parameters, what I do is copy them to a text file as back up. ( the indivual lines from the gui
If rubyripper ever suddenly has issues the best thing to do is delete .rubyripper and start fresh (or delete some individual files inside

If you build I'd use the line I showed above - installs to /usr and includes the cli version also.

The cli can be used for auto ripping if you have the interest or need.


Anything else just ask or if wanted I'll provide you with a package.
( it's not very hard to build once you get it down - 2 minutes tops

---

### Post by MrWES on 2008-11-30
Google ABCDE, A Better CD Extractor. It's command line but works very well and fast.

Bill

---

### Post by dwasifar on 2008-11-30
You don't say why you are obliged to use Ruby Ripper.  I use Grip, with the Lame encoder, and I have no problems with the results in Amarok or with any other application or device.  I strongly recommend it.  People have also had good results with Audiograbber run under Wine.

Perhaps Ruby is creating both ID3v1 and ID3v2 tags and setting their contents differently.  Just looking at the file properties, or what Amarok shows you, doesn't tell you the whole story about what's really in the tags.  I suggest you install a tag editor (Kid3 is my preference) and have a look at them.

---

### Post by osc1882 on 2008-12-01
Blah.
I have tried everything.
Uninstalled. Deleted the setting folder and then built if from scratch. I told it to off set my CD rom and then told it to rip mp3 to -V 0. Still same problem.
I would really like to get this worked out. I need to make a ton of high quality rips.

---

### Post by mc4man on 2008-12-01
I found two of my older ripped albums that still do it, none of the others do.

If I can figure out what makes them different, or re cause the issue and fix, i'll post. 
see screen  (so you know it wasn't just you

---

### Post by mc4man on 2008-12-01
I did exact rip and encodes of one of the cd's with the issue, It came out fine.
I also noticed in the logs that one of the 2 'bad' rips showed I had also done an mp3 with the flac, so it couldn't have been that.

A little closer look showed the 2 'bad' ones in addition to a .m3u had a .cue file.
Removing the .cue solved the issue. adding to the 'good' rip caused it to show the same issue.
Putting it back in the orig. 'bad' and the issue reappeared.

So are you creating a .cue in your rips?
If so try removing it.

> 
I need to make a ton of high quality rips.

If this happens to fix for you there is a simple way to set RR up in an 'autorip' mode (basically just insert cd and walk away or otherwise go about your business, when it ejects insert the next one, ect. RR works silently in the background.
Let me know

---

### Post by osc1882 on 2008-12-01
Yes. Deleting the cue did the trick. And that sucks because I need a cue. I need a log and a cue. I only 'really' need a cue for the flac rips. Any thoughts?

---

### Post by osc1882 on 2008-12-01
K. So I used Aramok to play some flac tracks that I did not rip that had a cue file in the same folder and Aramok did not change the track name on those. So it's just the ones I am ripping.

---

### Post by mc4man on 2008-12-01
Whay are you using the .cue for?

It only affects playback when it's in the folder, each .cue is named so you could have a storage folder to keep in till needed, then move back in.

Or just leave in place and remove the .cue extension till needed.

Or try posting an issue here
[http://code.google.com/p/rubyripper/issues/list](http://code.google.com/p/rubyripper/issues/list)

Do you have a .cue from other ripper from same cd to compare/

---

