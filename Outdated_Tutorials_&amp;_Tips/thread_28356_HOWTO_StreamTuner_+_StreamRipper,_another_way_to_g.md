---
title: "HOWTO: StreamTuner + StreamRipper, another way to get music."
date: 2005-04-19
forum: Outdated Tutorials &amp; Tips
---

### Post by Nano on 2005-04-19
I don't know how many music albumbs I have but it's never enough! I always need new music and I'm sure many of you need it too!

So here I want to give you some tips (for whoever didn't already know) about how to get some good quality music, and legally, as it's legal to record a TV program and then watch it when you come home.

Let's start with Streamtuner.
"streamtuner is a stream directory browser. Through the use of a plugin system, it offers an intuitive GTK+ 2.0 interface to Internet radio directories such as SHOUTcast and Live365."
In addition it can catalogue all your local music files for a fast access to them.

Ok, let's install it.
Enable the "universe" in your repository and type:
```

sudo apt-get install streamtuner

```

Ok, it should create an entry in your meny under Applications -> Sound & Video.
Since you have it installed let's teach it to open your favorite music player everytime you want to listen one of the listed radios.
In streamtuner open Edit -> Preferences. In the Application tab you will see a table. In the right column you will see "xmms %q" (I think it's the default setting), replace "xmms" with your favorite player but don't forget "%q" at the end of the string. In my case it is set to "beep-media-player %q".

Now you can listen to a lot of radio stations, many of them broadcasting at a very good bitrate.

Now, wouldn't it be cool to record your favorite ones in your hard disk?
Let's go.

To rip streaming radios we'll use "streamripper". ;)
```

sudo apt-get install streamripper

```

Now, let's tell Streamtuner how to use Streamripper properly.
Again, open Edit -> Preferences.

In the same table as before we'll edit the last row of the table, where it says "Record a stream".
Here we will delete the right column cell and replace it with this:
```

x-terminal-emulator -e streamripper %q -d /mnt/Data01/Ripped -r -q

```
Where "/mnt/Data01/Ripped" is the location where you want all the mp3s to be stored.

The "-r" option means Streamripper will create a relay server. In other words, if you don't do it you will be downloading the ripped version twice, once by streamripper and once by your media player. You might not care if you have broadband but you will otherwise.
The "-r" option, as we said, will create the relay using by default the 8000 port but, in case it's busy (video streaming, others) it will continue serching for the next open port. Usually, if 8000 is busy 8001 won't.

Example. You found a nice radio. You tune it, your player opens it and you hear it. You like it and decide to start ripping it. You press the Record button. A console will open and streamtuner will start doing its job.
Now, you can listen at whatever you want with your media player (other streaming radios, local files, etc) that streamripper will keep doing it's job. But if you want to listen what is being ripped, instead of connecting to the streaming radio you can connect to the relay created by streamripper.
To do so, just open with your media player [http://localhost:8000/](http://localhost:8000/) (or [http://localhost:8001/](http://localhost:8001/), etc).

Hope you will get some cool music with this combo.
At least I do.

Cheers!

---

### Post by Duffman on 2005-04-19
1) Cool does it record in different mp3 files for each song or one big one that you have to seperate?

2) Can you record multiple stations at once?

---

### Post by Nano on 2005-04-19
[QUOTE=Duffman]1) Cool does it record in different mp3 files for each song or one big one that you have to seperate?

2) Can you record multiple stations at once?[/QUOTE]
 1) Yes, it stores the files separately unless you specify otherwise. The "-q" option will even add sequence number to output filese, useful when there's crossfade between files.

2) Yes, you can record as many stations as your bandwidth allow you.

---

### Post by prodi_g on 2005-04-27
I've read through the thread on how to use streamripper with streamtuner.  I've modified the streamtuner record preferences just as it is suggested.  however, when i acutally record, streamripper hangs when it is trying to get the track info.  any thoughts???? 

thanks

---

### Post by kmyram on 2005-04-27
[QUOTE=prodi_g]I've read through the thread on how to use streamripper with streamtuner.  I've modified the streamtuner record preferences just as it is suggested.  however, when i acutally record, streamripper hangs when it is trying to get the track info.  any thoughts????[/QUOTE]

I took out the -d directory parameter and then it worked...

---

### Post by prodi_g on 2005-04-27
Thanks for the help.  I guess I just won't have any control over where it stores the ripped file but it's a small setup for enjoying ripping radio.

---

### Post by Beano on 2005-04-27
So - I cant seem to get it working. Admittedly im a bit of a noob when it comes t Linux at the moment. 

Ive enabled my universe repositories. 

Ive apt-get installed steamtuner - There doesnt seem to be an entry for it in my applications. Same goes for streamripper ... apt-get installed ... no entry in the menu .... anyone got any idea what ive done wrong? 

Thanks.

---

### Post by Nano on 2005-04-28
[QUOTE=kmyram]I took out the -d directory parameter and then it worked...[/QUOTE]
 The -d parameter indicates in which folder it will store the ripped streaming.
You can use it if the indicated location folder exists.

---

### Post by peekpt on 2005-04-28
This two programs are awesome! 
The nice thing is that the stream record separates the mp3's and give them id3 and filename!
Tremendous...

---

### Post by bassMonkey on 2005-04-29
This is superb... thank you!

---

### Post by psoleko on 2005-04-29
Thanks for the excellent guide. I've been looking for something like this for a while. Now I can get hard to find Greek music in Linux. Much appreciated.

---

### Post by fishfork on 2005-04-29
You can do this in MPlayer as well, by the way, though it's not well documented. Something like:

mplayer -dumpstream [url] -dumpfile [file]

Great for RealPlayer stuff. It saves it still compressed as a .rm file.

---

### Post by face on 2005-05-01
Great tip  :grin: 

thx
Jens

---

### Post by lark5000 on 2005-05-10
Hmm, Shoutcast works no problem for me, but not Live365.  Basically it says 2 categories, 0 streams.  Anyone know how to fix this?

---

### Post by Rehevkor on 2005-05-11
I just love this forum :D I keep finding cool stuff to do with Ubuntu.

Thanks!

Edit: This is one neat program. I'm recording a stream on my Ubuntu-equipped notebook without playback, and I'm picking up the relay stream on my desktop (better speakers) through Winamp. Sweet :D

---

### Post by Rehevkor on 2005-05-12
Well, there is one annoyance...
streamripper doesn't cleanly seperate songs, at least not on club977. It usually takes several seconds after a crossfade for it to realize the song has changed and start writing to a new file, so there's always a few seconds from the beginning of the next song tacked on to the end of the one before it.

Is there a way to alter the timing of song changes in streamripper? Maybe specify an offset in seconds?

---

### Post by bluemax on 2005-05-12
This is great, and it works perfectly. I'd actually been using streamripper in Windows XP before I switched to Ubuntu. It's a cool little program.

---

### Post by andlinux21 on 2005-05-27
[SIZE=3][FONT=Comic Sans MS][COLOR=Navy]Thanks for the good tip now I can get some of my favorite stations[/COLOR] \\:D/ [/FONT][/SIZE]

---

### Post by Technoviking on 2005-06-05
[QUOTE=lark5000]Hmm, Shoutcast works no problem for me, but not Live365.  Basically it says 2 categories, 0 streams.  Anyone know how to fix this?[/QUOTE]
Known bug, the streamtuner package in backport has the patch.

Mike

---

### Post by kuap on 2005-06-06
[QUOTE=Rehevkor]Well, there is one annoyance...
streamripper doesn't cleanly seperate songs, at least not on club977. It usually takes several seconds after a crossfade for it to realize the song has changed and start writing to a new file, so there's always a few seconds from the beginning of the next song tacked on to the end of the one before it.

Is there a way to alter the timing of song changes in streamripper? Maybe specify an offset in seconds?[/QUOTE]

I have the same problem... and I was going to ask the same question.

Are there any other stations that you know about where the streamripper works better?

Thanks

---

### Post by Flasher on 2005-06-08
[QUOTE=kuap]I have the same problem... and I was going to ask the same question.

Are there any other stations that you know about where the streamripper works better?

Thanks[/QUOTE]
 it happens because *streamripper* starts writing to a new file when the title changes... and the title changes a bit later...

---

### Post by Musagetes on 2005-06-08
Thank you for this howto, great tips!

I am however experiencing some problems. When I hit the record button, streamtuner opens a console but immediately closes it again, and nothing seems to be recording. Anybody else had this and know how to get it working?

---

### Post by wirjo on 2005-06-10
Awesome guide, thanks!

---

### Post by jazz on 2005-06-20
beautiful, but the latest version of streamripper, 1.61.8 has much better song splitting algorithms, and it even has very good id3tag detection/appendin thnigy !!

u have to manually compile it though !

download, extract and issue the following commands :

```

./configure CFLAGS="-O2 -march=pentium4 -mtune=pentium4 -mfpmath=sse -mmmx -msse -msse2 -fno-ident -ffast-math -pipe" CPPFLAGS="-O2 -march=pentium4 -mfpmath=sse -mmmx -msse -msse2 -fno-ident -ffast-math -pipe"


make && sudo make install

```

Works beautifully !! thanx mate  ;-) 

Bye,
Jazz

---

### Post by nuggien on 2005-06-30
i guess streamripper can only rip shoutcast streams and not live365?

---

### Post by i3dmaster on 2005-06-30
Fantastic! This is so cool! Thank you very much for sharing!

---

### Post by NotSoSuperUser on 2005-06-30
Is this legal on commercial radio stations such as the BBC and Virgin?

---

### Post by twowheeler on 2005-07-01
I am coming a little late to this party.  It installs fine, and seems to work for some things.  However the stream I really wanted to capture is a .asx playlist site, can that be made to work?

The site is:  [http://azulweb.streamguys.com/witf/witf.asx](http://azulweb.streamguys.com/witf/witf.asx)

Suggestions, anyone?

---

### Post by greyhound4334 on 2005-09-05
There were a couple of earlier questions

1. terminal just dies when you hit record: you need to set up a terminal emulation program for the record action.   For me (running KDE), the default xterminal app wasn't available (I think it's a gnome app).  So I use xterminal instead.  apt-get install xterminal.  Then use > xterminal -e "streamripper %q -d /space1/streamrip -r -s -q" note the double quotes!

2. some people noted problems with the overlapping of songs in the recorded streams.  Do a "man streamripper" in a terminal to see some options you can use with streamripper to deal with this.  If you page through the man pages, there are a couple of specific "how to" examples for dealing with this problem.

HTH!

---

### Post by globalman on 2005-11-28
Nano

i love uuuuuuuu!!! :cool:

:-({|=    :-\" 


cheeers man =D>

---

### Post by globalman on 2005-11-28
Nano \\:D/ 

i love youuuu :cool: 

:-({|=   :-\" 

cheeeers man  =D>

---

### Post by tuza on 2005-12-02
This is a great HOWTO, thanx Nano.

By the way, I installed streamtuner on my Ubuntu 5.10 Breezy, but the icon does not appear in Application -> Sound&Movie catalog, I had to run in it from terminal, by typing: streamtuner. I would like to have it appear in my Sound&Movie catalog. Any tip?

---

### Post by Ramses de Norre on 2006-04-11
It came automaticaly here, did you try killall gnome-panel?
Otherwise make one yourself: applications > system tools > applications menu editor
sound & video > select new entry
command: streamtuner
icon: /usr/share/pixmaps/streamtuner.png

EDIT: topic is a little outdated I see :d

---

### Post by sophtpaw on 2006-05-01
[QUOTE=nuggien]i guess streamripper can only rip shoutcast streams and not live365?[/QUOTE]

i'm glad i found this post. Because i 've tried, unsuccessfully tried getting help with Streamtuner.

My problem has been to record radio. And now i hear you say that it doesn't record live365?? if that is so that would then explain why i'm not successfully ripping live365 livestreams.
I've gone to edit/preferences and changed the script, which aguessi therefore didn't need to, as is mentioned at the top of this thread and which worked only after i removed '-d' as was also subsequently mentioned, but it is still the same story. It looks like its recording(terminal comes up and goes through the motions) but ultimately it is not saved anywhere that i can locate once i shut the terminal down.
I've not tried shoutcast streams yet

--
sophtpaw

---

### Post by nismoskys on 2006-05-13
[QUOTE=bassMonkey]This is superb... thank you![/QUOTE]
agreed.

---

### Post by airzer0 on 2006-05-20
very nice how to awsome
   [SIZE="7"][/SIZE] UBUNTU OR DIE:twisted:

---

### Post by Adler on 2006-06-28
Nano,

**Great Post**.

I'm a SuSE want to be and migrated to UBUNTU 6.06. Because everything works as posted. 

Cool! 

This is one of the best posts that I've seen any where. And thanks for the How To.

---

### Post by Adler on 2006-06-28
I've never heard such great Music!

I've been recording mp3s forever, but live is best! This just blows me away. I'm going to record for a good 12 hours.

What is the eventual format here and can it be recorded -- expanded -- to CD?

I don't have a mp3 player in my car.

---

### Post by Gen2ly on 2007-02-14
thanks bro the

> x-terminal-emulator -e streamripper %q -d /mnt/Shared_Disk/Music/Recorded -r -q

was a life saver.

---

### Post by Adler on 2007-02-15
Hi All,

OK, I've got so much music going, how do I burn .mp3s to Music CDs?

I hope that was clear.

Adler

---

### Post by Nano on 2007-02-16
> **Adler said:**
> Hi All,

OK, I've got so much music going, how do I burn .mp3s to Music CDs?

I hope that was clear.

Adler

If you don't have it already installed just go for:

```

sudo apt-get install serpentine

```

Once it's installed open it and you will find a nice user friendly GUI to convert mp3 to music CDs.

Screenshots of Serpentine in action:
[http://www.flickr.com/photos/cogumbreiro/sets/72157594164085642/](http://www.flickr.com/photos/cogumbreiro/sets/72157594164085642/)

---

### Post by Adler on 2007-02-16
Nano,

Thanks for that. Are you able to "span" CDs? I mean create multiple CDs, if the size of the .mp3 files is too large for a single CD?

Adler

---

### Post by Nano on 2007-02-17
> **Adler said:**
> Nano,

Thanks for that. Are you able to "span" CDs? I mean create multiple CDs, if the size of the .mp3 files is too large for a single CD?

Adler

To be honest with you I haven't played a music CD in such a long time nor I have created them. 
However, of course you won't be able to put more than 70-80 mins of music in a music CD. 
For that Serpentine shows you how much space left there is while you add new mp3s to the burn queue.

---

### Post by sb770 on 2007-02-20
Excellent, I am glad that streamripper works with Ubuntu...  This was one of my favorite and most used apps in XPland.  This is making for a smooth transition back to Linux (used to be on Gentoo for a while, but got tired of the recompiles and constant issues) -- not even dual booting this time.  Thanks Ubuntu community!

---

### Post by dtvarnum on 2007-05-06
Great article. I tried and streamripper wasn't in the menu. It still worked though. However how do you "stop" the recording? The record button in streamtuner didn't work.

dtv

---

### Post by Paul_world10 on 2007-06-06
I really enjoy the variety.

---

### Post by Chemroydal Tissue on 2007-08-31
This works really well on the preselected stations, but I'm having problems recording a local station. When I try to record [mms://pubint-wcbe.wm.llnwd.net/pubint_wcbe](mms://pubint-wcbe.wm.llnwd.net/pubint_wcbe), a Terminal opens normally, but hangs at "[getting track name...]" Any way to adjust streamripper so that it doesn't try to retrieve a track title?

---

### Post by bharani on 2007-09-06
somebody pelease help..stream tuner notworking with record button..it just opens a terminal and an error then closes the terminal...any problem with the copy rights...

---

### Post by secretspicy15 on 2007-09-06
bharani--
What is the command for "Record a stream" in your streamtuner preferences?

Go to Edit->preferences and choose the Applications tab, and scroll down to where it says "Record a stream" The command should be

```

x-terminal-emulator -e streamripper %q 

```

or something along those lines, with the optional flags and such... I had trouble with it when I tried to specify the directory with the -d flag, so I just let it copy into the default directory (which is a folder named after the radio station in my home folder)

I hope this helped.

TJ

Edit: You may need to use something other than x-terminal-emulator if you run KDE or something else... if that's the case, others on this thread have covered this problem...

Edit (again): I got the -d flag to work... I had forgotten to enclose the filepath in double quotes... d'oh!  So if you want to specify the directory your music goes to, append ```
-d "/foo/bar/music"
``` (or whatever the path is to your music directory) to the command.

---

### Post by bharani on 2007-09-07
x-terminal-emulator -e streamripper %q -d /opt/ripped -r -q  


this is my command...I worked b4..i didn't have a problem with files getting into /opt/ripped...all of a sudden the problem appeared from past two days...I guess it could be because of any updated I have installed...but I still not getting it right...please help...

---

### Post by bharani on 2007-09-07
please have a look at my error

---

### Post by secretspicy15 on 2007-09-07
shoot, looks right to me... sorry, wish I could be of more help....

---

### Post by Nano on 2007-09-07
> **bharani said:**
> please have a look at my error

Are you sure you have write permissions under /opt/?
Try first in your home directory.

---

### Post by bharani on 2007-09-07
Nano,
               situation is much complicated than you think it is...like ripped without any changed until two days ago...then all of a sudden this error pops out..well digging through the forums in stream ripper site reveals that some coding changes need to be made..because such stations are changing the character set of relay stream exclusively to avoid SR...i hope to see a solution soon...

---

### Post by poccino on 2007-09-28
I installed Streamtuner and xmms but I have no audio.
Ni problem with rythmbox.
How is it possible?

---

### Post by Cannaregio on 2007-11-30
> **dtvarnum said:**
> Great article. I tried and streamripper wasn't in the menu. It still worked though. However how do you "stop" the recording? The record button in streamtuner didn't work.

dtv

Yep. This seems to be a problem, at least for me, even now.
I have to kill the terminal to stop. There must be a more elegant way.

---

### Post by jake3988 on 2007-12-10
> **Cannaregio said:**
> Yep. This seems to be a problem, at least for me, even now.
I have to kill the terminal to stop. There must be a more elegant way.

Nope!  Streamripper in fact actually says in its manpage that's how you kill it.





However, I have a question of my own: Playing /tmp/streamtuner.shoutcast.DNF22T.m3u.
Win32 LoadLibrary failed to load: avisynth.dll, /usr/lib/win32/avisynth.dll, /usr/local/lib/win32/avisynth.dll


Seems like a w32codecs problem... but I have w32codecs installed... :(

---

### Post by Paul_world10 on 2008-02-22
Thank you, works perfect.

---

### Post by sp3ctum on 2008-05-08
Hi. Thanks for the howto, it works great. However, some of my songs that I've ripped can't be played. They are empty shells of the file with nothing inside.
Others create an error in Totem, and it has the following information:

[B][SIZE="5"]"An error occurred

Failed to connect to stream:OK"[/SIZE][/B]

What does this mean, (what causes it), and how can it be prevented from happening again?

---

### Post by donato roque on 2009-07-10
Thank you, Nano.  I've been looking for this information in different
forums for a while now.

---

