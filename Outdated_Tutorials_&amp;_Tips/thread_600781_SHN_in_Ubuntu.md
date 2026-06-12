---
title: "SHN in Ubuntu"
date: 2007-11-02
forum: Outdated Tutorials &amp; Tips
---

### Post by cozmic charlie on 2007-11-02
There has been a number of recent posts with new users frustrated trying to play shn  (shorten) files in Ubuntu Gutsy.  SHN is an older lossless format that is not supported any more and has been surpassed by a number of newer lossless formats such as flac that offer better functionality (such as support for ID tags).  However, it is one the early lossless formats used by trading communities such as the Grateful Dead tapers and is still used extensively for live music downloads.  I made the switch to Ubuntu about 1 year ago and it has taken me that long to figure out different programs that can handle shn files - not many do and very few players will play them.  That leaves the new user with a couple options: 1. convert all your shn files to another format such as flac, or 2. use Wine or dual boot to Windows.  I do not like option #2.  I was only   able to completely switch to Ubuntu when I figured out the programs needed to handle shn.  I thought I would pass on the knowledge I have gained to new users to save them the headaches of searching the forums etc etc to try and do something that should be simple.  I have written a section for Fiesty and one for Gutsy since their have been significant changes from Fiesty. This is how I did it so if anyone has a better way - great I hope you add to the conversation.  In my opinion whatever we can do to help new users make the transition to Ubuntu the better.  I really get upset when someone in the forum chides a new user because they did not search the forums or Google the topic.  Many people just want to use their computers, and don't want to spend countless hours searching the forums only to find answers they can't understand.  This is geared to new users so I tried to keep it as simple as possible.  OK - I will climb off the soapbox and get down to business. 

I have changed this HowTo based on my experience in Gutsy.  I have organized it into a section for Fiesty and Gutsy since their are significant changes to Gutsy.  Luckily, Gutsy has actually made playing shn much easier.  The downside is though for those that like XMMS, it is not ready for Gutsy and does not play well (yet) on Gutsy (more about this below).  

**_SETTING UP SHN IN FIESTY_**

What you need list of programs I recommend (following is a more detailed description).
   XMMS (in repos)
   SoundKonverter (in repos) 
   PACPL (available at sourceforge or here [http://viiron.googlepages.com/](http://viiron.googlepages.com/))
   gtkpod-aac (in repos)
   Azureus (in repos but best to install from source)
   shorten codec ([http://www.etree.org/shnutils/shorten/](http://www.etree.org/shnutils/shorten/))
   XMMS-shn ([http://www.etree.org/shnutils/xmms-shn/](http://www.etree.org/shnutils/xmms-shn/)) 

**_Detailed description:_**
Player - the only one I found in Fiesty that plays shn is XMMS.  I have checked a few other players (Exaile, Amarok, Quod Libet) but none of these to my knowledge play shn files.  In Gusty you have more options (see below).

Converter - here you have a couple options.  For those that want a GUI (visual interface), SoundKonverter (yes it is a kde program but it works fine in Ubuntu) works great.  I recommend PACPL - a very powerful decoder/encoder written in Pearl.  However, it is command line based (it does have a simple GUI you can install) but it is easy.

Ipod - gtkPod- aac (Ipods with native Apple firmware will not play shn so I convert to Apple Lossless.  However, you can use Rockbox ([http://www.rockbox.org/](http://www.rockbox.org/)) as an alternative and play shn and flac.  Rockbox is available for Linux and it is easy to set up.  I have it on my iPod and it works great.  

Tags - exfalso One disadvantage of shn is no tags.  I recommend if you want tags to convert them to flac or another lossless format that supports tags.  Exfalso supports m4a and that is why I use it.  Remember if you are sharing files you need to keep at least one copy as is or you will not be able to reseed that file.  

Organizer - XMMS can organize (I believe it has a plug in for m3u) but you may not find it easy to use.  Rythmbox is most like iTunes for those that want an iTunes like experience.  Others may have suggestions here.  I recommend you experiment and see which you like.

Bittorrent - if you want to start a flame war just post to the forum that xxx bittorrent is best.  Everyone has their favourite and it really depends on what you need.  I have tried many and I like Azureus.  It is well supported with lots of great plug ins.  What I like most though is the many options for using it over a network.  I love Azsmrc (a server/client plug in that you can use in Linux or Windows) but you don't need it.  If you have a network just set up a share file that Azureus will check and automatically download any torrent placed in the folder.  Download the torrent to the shared folder over your network and Azereus will automatically download the files - it's so simple.

**_Now that you have everything you need let's set up for shn.  Follow these steps._**

1.  Make sure you have all the other codecs installed.  This HowTo (and others) is a great help ([http://ubuntuforums.org/showthread.php?t=413624](http://ubuntuforums.org/showthread.php?t=413624)).  Make sure you have Medibuntu in your repository.  Make sure to install the ffmpeg codec (in Synaptic) and either the gstreamer-10 ffmpeg or xine-ffmpeg (libxine1-ffmpeg) codec depending on which engine you use.  For beginners, Ubuntu comes installed with the gstreamer engine.  This has always worked for me but some have better luck with the Xine engine.  So which ever you use just make sure and install the ffmpeg plug in.  This is important because the latest version of ffmpeg does support shn. 

2.  Go to synaptic or whatever you use (apt-get or aptitude-get) and download the programs you need.  To start with all you need is XMMS (the other's can be added later).  In Feisty their is an  XMMS plug in for shn however it does not work for me - try it first though and if it works for you then you are one of the lucky ones and you need not go any further.  If it does not work then read on.  For shn to work you also need the XMMS-dev installed (in Synaptic).  If you don't install it, the XMMS-shn installer will give you a "no target" error that XMMS is not installed so make sure to install them.

3.  Download the shorten tar files from here for shn ([http://www.etree.org/shnutils/shorten/](http://www.etree.org/shnutils/shorten/)) and here ([http://www.etree.org/shnutils/xmms-shn/](http://www.etree.org/shnutils/xmms-shn/)) for the XMMS-shn.  Download these to the desktop (makes it much easier).

4.  Next we are going to install the shn files you have on the desktop.  One of the most useful HowTo's is located here ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)) - this is the resource for how to install the various file formats in Ubuntu.  Bookmark it, you will refer to it frequently.  Go about half way down to the section on installing source files.  This is excellent and even has a video to walk you through it.  Note - two items that are essential that will make life much easier on Ubuntu are Build Essential and checkinstall.  Go to synaptic and install both of these before you install anything else.  If you use checkinstall instead of make-install it adds it to Synaptic so you can easily uninstall later if needed. 

5.  Installing the shorten file.  Now you should have this on the desktop.  All you need to do is follow the instructions here ([http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/)).  A mistake many make is that you have to change to the directory that the files are saved on.  Watch the video and you will see how easy it is.  The basic steps are:
open the terminal:--------------  jerry@jerryscomputer:~$
change the directory:-----------   jerry@jerrycomputer:~$ cd /home/jerry/Desktop/shorten-3.6.1
./configure:------------------------   jerry@jerrycomputer:~Desktop/shorten-3.6.1$ ./configure    
make:------------------------------   jerry@jerrycomputer:~Desktop/shorten-3.6.1$ make
checkinstall:----------------------   jerry@jerrycomputer:~Desktop/shorten-3.6.1$ sudo checkinstall

 during check install it will ask if you want to create docs - just say no.  It will also ask for a description type "shorten" then hit enter and enter again.  Just keep hitting enter every time it stops until it is finished

6.  Now do the same with the XMMS-shn files.  Follow the same steps in #4 above.  When it asks for a name just type in xmms-shn.  If it gives a message no target, reboot the computer and try again.  Sometimes you have to reboot.  You can also play with the Prefix for the make file if you know what you are doing.  You should not have to though.

That's it - you should be able to play shn.  Now, the shn codec should come up as an option in SoundKonverter or you can also use PACPL to convert shn to any format.  PACPL allows you to code and add tags in one step - very convenient.  To add to the ipod you convert to whatever format using SoundKonverter or PACPL.  

**_PLAYING SHN IN GUTSY_**

Good news is this is actually much easier.  The bad news (for some) is xmms does not work well in Gutsy.  You will read threads that xmms is not supported any more - this is not true.  Go to the xmms web site and you will see.  However, xmms does not work well in Gutsy - from the xmms web site "xmms does not work with GTK-2" (GTK-2 is what Gutsy uses).  They are working on a new version but it is not ready yet.  You will see xmms2 - this is not a GTK-2 replacement for xmms, it is a server based xmms.  My recommendation for now is skip using xmms in Gutsy until a GTK-2 version is released.  Luckily though because ffmpeg now supports shn you can play shn in Rythmbox.  I have not found any players (Exaile, Banshee, Amarok, Beep, Audacious, Helix, Quodlibet) that play shn.  But, in Gutsy Rythmbox, Totem and gnome mplayer will play shn once the codec is set up.  Because, I mostly listen to live downloaded music in lossless I want a player to play flac, m4a (apple lossless) and shn.  Rythmbox will play all these.  I like Banshee though - I like the ease of use and I think Banshee sounds better than Rythmbox.  So I set it up with Rythmbox and gnomeplayer to play shn and Banshee for everything else.  You don't have to though - you can use Rythmbox for everything.  It is just personal preference.  Now lets set it up and you will see how easy it is.

Setting up in Gusty:
1.  As in Fiesty make sure you have all the codecs installed - especially the ffmpeg (Xine or gstreamer whichever you prefer).  I have never had a problem with gstreamer but some report they have better success using Totem-xine.  That is fine just make sure you install the xine-ffmpeg.  As I mentioned above, ffmpeg now supports shn so this means shn can be converted, played etc in the gstreamer or xine apps (Totem, Mplayer, Rythmbox, Soundconverter, SoundKonverter etc).

2.  You must stil load the shorten codec though.  Follow steps 3, 4 and 5 above to install the shorten codec.

3.  That's it, now you should be able to play shn in Rythmbox.  You can also use Soundconverter (a gnome app) to convert shn to other formats though I still prefer SoundKonverter because it offers more options).  PACPL is one of the best encoders/decoders for Ubuntu because of the large number of audio and video formats it works with- I highly recommend it. 

4.  Also, since most people that have shn also have flac format make sure and add flac support (in synaptic).  As I mentioned above xmms is not ready for Gusty so forget it for now until they come out with the next version.  

I hope this helps.  Note there is most likely another way to do this and I hope this thread attracts others that add their methods so a new person can just go to one thread and find the answer.

I plan to write more HowTo's geared to the live music downloader and covering conversion, bittorrent, tagging, backup and organizing in future How To's so check back often.  My next will be a HowTo for PACPL.  If anyone has any requests for a HowTo or suggestions let me know - drop me an email or post here.  

Good luck, enjoy and rock on Ubuntu. :guitar:

---

### Post by n3tfury on 2007-11-03
you should look at some of the other forums and post there or perhaps add to a wiki?  that's alot of good info.

---

### Post by cozmic charlie on 2007-11-04
> **n3tfury said:**
> you should look at some of the other forums and post there or perhaps add to a wiki?  that's alot of good info.

I am somewhat new to posting How To's - didn't know you could post to different forums.  I will check out the Wiki and see if I can figure out how to do it.  Thanks for the kind words - my goal is to help people transition to Ubuntu as easy as possible so your advice is appreciated.

---

### Post by mikeize on 2007-11-05
Thanks for the info!  Any hope of amarok playing shn in gutsy?

-mike

---

### Post by cozmic charlie on 2007-11-05
> **mikeize said:**
> Thanks for the info!  Any hope of amarok playing shn in gutsy?

-mike

I don't know - I hope so I like Amarok and if it did I would use it.  I have checked the Amarok forums and found posts that claim it should since it uses ffmpeg and the Xine engine.  You might try checking it - make sure you have both ffmpeg and libxine1-ffmpeg installed.  I checked it last night and it did not work for me.

---

### Post by mikeize on 2007-11-05
I've got 'xine-plugin' and 'xine-ui' installed, but I can't find anything about 'xine-ffmpeg'.  I've got the gstreamer and ffmpeg codecs installed...  

As of now, amarok won't play my shn's... and yeah, I use amarok for all my mp3's, it would be nice not to have to have to use a separate player for my shn's, and actually I can't play them in xine either, though I used to be able to in feisty.

-mike

**edit**  okay, I can actually play them in mplayer (but can't search/index the track).

---

### Post by cozmic charlie on 2007-11-05
> **mikeize said:**
> I've got 'xine-plugin' and 'xine-ui' installed, but I can't find anything about 'xine-ffmpeg'.  I've got the gstreamer and ffmpeg codecs installed...  

As of now, amarok won't play my shn's... and yeah, I use amarok for all my mp3's, it would be nice not to have to have to use a separate player for my shn's, and actually I can't play them in xine either, though I used to be able to in feisty.

-mike

**edit**  okay, I can actually play them in mplayer (but can't search/index the track).

Great you have it working under the gstreamer engine.  You should also be able to play in Rythmbox - there you can organize, see the tracks etc.  You could also try the gnome-player.  It is a very simple player but it shows the tracks etc. 
 
In Synaptic, there is a program called called libxine1-ffmpeg. Do a search in Synaptic of ffmpeg, it should be in the Universe repository.  You most likely already have ffmpeg installed if it is working in mplayer so all you should need is the libxine1-ffmpeg.

Amarok can use either Xine or gstreamer so you might try switching engines in Amarok and see if it works with gstreamer.  Post back if you get it to work.

---

### Post by mikeize on 2007-11-05
Thanks cozmic charlie!

I actually have all of that stuff (gstreamer, ffmpeg, and libxine-ffmpeg).  Heck I've even got rhythmbox, but never tried it.  I'm checking it out now, and while it's not as slick and pretty as amarok, I think I'll just use that as my main music app.  A lot of my best music is shn, after all.  I'll spend some time over at the amarok site though, agitating for (better?) shn support.  Now 'go on home your mama's callin you'

-mike

---

### Post by cozmic charlie on 2007-11-05
> **mikeize said:**
> Thanks cozmic charlie!

I actually have all of that stuff (gstreamer, ffmpeg, and libxine-ffmpeg).  Heck I've even got rhythmbox, but never tried it.  I'm checking it out now, and while it's not as slick and pretty as amarok, I think I'll just use that as my main music app.  A lot of my best music is shn, after all.  I'll spend some time over at the amarok site though, agitating for (better?) shn support.  Now 'go on home your mama's callin you'

-mike

Excellent - enjoy!

---

### Post by mikeize on 2007-11-06
I got an email from someone at amarok, and they said that it's up to what you're using to run amarok (ie, xine).  BUT...  he also said that amarok can't play anything which it can't read the meta-data for.  So far I haven't found any tag-editor for shn files.  Got any info on that?

-mike

**edit**  turns out I'm just going to convert all my shn's to flac with soundconverter, after reading up on the shn/flac thing.

---

### Post by cozmic charlie on 2007-11-06
> **mikeize said:**
> I got an email from someone at amarok, and they said that it's up to what you're using to run amarok (ie, xine).  BUT...  he also said that amarok can't play anything which it can't read the meta-data for.  So far I haven't found any tag-editor for shn files.  Got any info on that?

-mike

**edit**  turns out I'm just going to convert all my shn's to flac with soundconverter, after reading up on the shn/flac thing.


You really can't tag shn.  That explains why Amarok does not play them.

I am doing the same with my shn files.  Slowly converting them to flac.  Much better support for flac and you can tag.  I don't use Soundconverter but I know in SoundKonverter you can decode, tag and rename the files all at once.  You can also do the same with PACPL.  Saves a few steps.

---

### Post by proving_ground on 2009-06-28
Great how-to. There's a lot of GD recordings I need to convert from shn > flac so that I can tag and stream from squeezecenter. 

Thanks!

---

### Post by cozmicharlie on 2009-06-30
> **proving_ground said:**
> Great how-to. There's a lot of GD recordings I need to convert from shn > flac so that I can tag and stream from squeezecenter. 

Thanks!

Great - glad it worked and you can enjoy all those GD shows in lossless.

---

