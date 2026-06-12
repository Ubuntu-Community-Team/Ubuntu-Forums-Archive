---
title: "[SOLVED] HOWTO: StreamTuner + StreamRipper, another way to get music"
date: 2005-10-15
forum: Outdated Tutorials &amp; Tips
---

### Post by arnieboy on 2005-10-15
Written by **[Nano]("http://ubuntuforums.org/member.php?u=195")**

I don't know how many music albums I have but it's never enough! I always need new music and I'm sure many of you need it too!

So here I want to give you some tips (for whoever didn't already know) about how to get some good quality music, and legally, as it's legal to record a TV program and then watch it when you come home.

Let's start with Streamtuner.
"streamtuner is a stream directory browser. Through the use of a plugin system, it offers an intuitive GTK+ 2.0 interface to Internet radio directories such as SHOUTcast and Live365."
In addition it can catalogue all your local music files for a fast access to them.

Ok, let's install it.


```
sudo apt-get install streamtuner
```


Ok, it should create an entry in your meny under Applications -> Sound & Video.
Since you have it installed let's teach it to open your favorite music player everytime you want to listen one of the listed radios.
In streamtuner open Edit -> Preferences. In the Application tab you will see a table. In the right column you will see "xmms %q" (I think it's the default setting), replace "xmms" with your favorite player but don't forget "%q" at the end of the string. In my case it is set to "beep-media-player %q".

Now you can listen to a lot of radio stations, many of them broadcasting at a very good bitrate.

Now, wouldn't it be cool to record your favorite ones in your hard disk?
Let's go.

To rip streaming radios we'll use "streamripper".

```
sudo apt-get install streamripper
```


Now, let's tell Streamtuner how to use Streamripper properly.
Again, open Edit -> Preferences.

In the same table as before we'll edit the last row of the table, where it says "Record a stream".
Here we will delete the right column cell and replace it with this:

> x-terminal-emulator -e streamripper %q -d /mnt/Data01/Ripped -r -q

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

### Post by Jenda on 2005-10-16
> So here I want to give you some tips (for whoever didn't already know) about how to get some good quality music, and legally, as it's legal to record a TV program and then watch it when you come home.
Are you absolutely sure about this? It seems to me that this would be included in "unauthorized replication".

---

### Post by arnieboy on 2005-10-16
[QUOTE=Jenda]Are you absolutely sure about this? It seems to me that this would be included in "unauthorized replication".[/QUOTE]
ask nano

---

### Post by mtron on 2005-10-20
[QUOTE=Jenda]Are you absolutely sure about this? [/QUOTE] 

As we both live in the EU (that's all i can say), this is totally ok for private use, however you are not allowed to "share" them, use them at a public preformance, sell them ect.

So, no stress (till now) Let's hope it says like this.

---

### Post by Jenda on 2005-10-20
Indeed. That makes sense. Not that I really care. As long as I don't feel like I'm robbing the author, then I'll do anything.

---

### Post by Nano on 2005-10-22
In theory it is legal since the radio station already paid the rights to broadcast the tracks.
Of course, you cannot distribute/sell any of the songs.

---

### Post by renebs on 2005-11-26
[QUOTE=arnieboy]Written by **[Nano]("http://ubuntuforums.org/member.php?u=195")**

I Hope you will get some cool music with this combo.
At least I do.

Cheers![/QUOTE]

Just have to say one thing: Thanks for **Arnieboy** and all the people involved on these softwares (streamripper, Streamtuner, xmms, etc.)

---

### Post by dejitarob on 2006-01-05
The [station]("http://magnatune.com/artists/music/World/World-http_shuffle.m3u") I am attempting to do this on apparently prevents you from ripping songs. It has a delay between each track for a few seconds and when I try to use streamripper it just cycles through 'bufferring..' then 're-connecting...' It just loads a blank track '-.mp3' instead of the actual streaming content so it never actually rips anything.

*Edit:* Apparently, 'meta interval -1' signifies that it is plain HTTP not shoutcast. Thus I can just open up the .m3u to get the actual song locations.

---

### Post by Harry_Sack on 2006-02-27
Does anyone know how I could make the terminal open new tabs instead of a new terminal window for every stream?
I like to record several streams at the same time, but then I have to have like ten terminal windows open at the same time.

Thanks for the howto!
Found lots of good music previously unknown to me.

---

### Post by billdd on 2006-03-28
Hey Arnie, Thanks for the info.  I just installed ubuntu today and love it.  Followed your instructions and got streamtuner installed in seconds.  Thanks.
Bill

---

### Post by arnieboy on 2006-03-28
[QUOTE=billdd]Hey Arnie, Thanks for the info.  I just installed ubuntu today and love it.  Followed your instructions and got streamtuner installed in seconds.  Thanks.
Bill[/QUOTE]
yeah I am a big fan of streamtuner myself. got to know of hard rocking 80's.com from there. stuck on to it since then.

---

### Post by billdd on 2006-03-29
Hi, I installed Streamtuner with no problems.  Then I followed the directions posted here when I installed Streamripper.  It installed o.k. and the app runs but I'm getting an error message when I try to rip streams.  It says it can't create the file.  
Here is how I have the streamtuner set.  I even created a Music folder with a Ripped folder in it on my desktop.  It didn't work.  Any suggestions? 

x-terminal-emulator -e streamripper %q -d /mnt/Desktop/Music/Ripped -r -q

Thanks,
Bill

---

### Post by mtron on 2006-04-03
are you sure that the path /mnt/Desktop is correct? is this a boot - up mounted device via fstab?

can you post the line from fstab?

---

### Post by Nordoelum on 2006-04-03
Tryed it for around 10 minutes. Its just awesome to rip the mp3 song :P

---

### Post by Wolfi3 on 2006-04-11
Yes, it works brilliantly :D 

The -r switch was just what I needed - very important to save the bandwidth of small stations cos if every user was taking 2 streams they would soon run out of bandwidth.

---

### Post by xXx 0wn3d xXx on 2006-04-11
It works great. I just rip club 977 stations and idobi radio constantly. I have since added 75 + songs to my collection and that's after 4 hours of ripping occasionally :)

---

### Post by neonlug on 2006-04-18
Has anyhone had difficulty getting the songs completly?  I stream .977 for example and the first few seconds of the song are on the previous mp3.  Of course the mp3 of every song is missing the first few parts of the song.  So I end up having to do alot of editing to get all parts of the song.

If anyhone could tell me what I could do to correct this please let me know.

Thank you,

Phillip

---

### Post by joeybunda on 2006-06-21
Well blow me down. This is better than sliced bread!

---

### Post by GStubbs43 on 2006-11-14
Hey I know this is an old thread but...

First, thanks for this howto Arnieboy and Nano! It's a great way to get music!

Now, I have a couple questions:
1) Is it possible to get Streamtuner to work with Songbird? Right now I have Songbird listening to Localhost:8000 and it works great, so I guess I could just click record, then open Songbird and play it, but...
2) Is it possible to get Streamripper to rip to ogg instead? Or is mp3 better for most stations since they probably stream using mp3s?

---

### Post by haiku99 on 2006-12-04
thanks, good info....BTW, I just installed streamtuner and streamripper using automatix2 and thaat worked perfectly on machine running Dapper...

---

### Post by wilberfan on 2007-01-12
I've managed to open a stream, and Streamtuner starts up Amarok OK, but when I hit record, this is all that displays in a terminal window:

> Connecting...
stream: Streamripper_rips
server name: Cougar/9.01.01.3829
bitrate: 0
meta interval: -1
relay port: 8000
[getting track name... ]

The cursor just stops and blinks at the end of "getting track name...".    The System Monitor shows that streamripper is running (well, 'sleeping').    The STOP button on Streamtuner is greyed-out, though...   I don't think anything is being recorded.

Anyone have any idea what's (not) going on?

---

### Post by WardLoockx on 2007-02-23
> **wilberfan said:**
> I've managed to open a stream, and Streamtuner starts up Amarok OK, but when I hit record, this is all that displays in a terminal window:



The cursor just stops and blinks at the end of "getting track name...".    The System Monitor shows that streamripper is running (well, 'sleeping').    The STOP button on Streamtuner is greyed-out, though...   I don't think anything is being recorded.

Anyone have any idea what's (not) going on?

Anybody that knows how to fix it ? Because I have the same problem.

```

Connecting...
stream: Streamripper_rips
server name: Apache/1.3.37 (Unix) PHP/5.2.0 mod_ssl/2.8.28 OpenSSL/0.9.7e-p1 mod_perl/1.29 FrontPage/5.0.2.2510
bitrate: 0
meta interval: -1
relay port: 8000
[getting track name... ]


```

Greets,
Ward

---

### Post by Nano on 2007-02-24
Could you please tell us the streaming feed you're trying to rip?

---

### Post by WardLoockx on 2007-02-24
This one [http://www.deep.fm/play/iTunes128K.pls](http://www.deep.fm/play/iTunes128K.pls)

But it works with that stream under windows :( !

---

### Post by WardLoockx on 2007-02-24
I think he is connecting with port 80 Because it says it's an apache server. But I don't see any option to change the port :(

---

### Post by WardLoockx on 2007-02-25
okay I found it out.

When I Try to connect with the pls file it won't work but when I download the file.

> wget [http://www.deep.fm/play/iTunes128K.pls](http://www.deep.fm/play/iTunes128K.pls)

and when I open it

> 
[playlist]
numberofentries=2
File1=http://publisher-01.deep.fm/deepfm-128.mp3
Title1=DeepFM @ 128 kbits (128K)
Length1=-1
File2=http://publisher-02.deep.fm/deepfm-128.mp3
Title2=DeepFM @ 128 kbits (128K)
Length2=-1
Version=2


Now try the File1 or File2 link :) 
> 
streamripper [http://publisher-02.deep.fm/deepfm-128.mp3](http://publisher-02.deep.fm/deepfm-128.mp3)

And yes, he is ripping !! :KS

---

### Post by zazen666 on 2007-03-30
HI, I need a little help,
Regarding this:


Since you have it installed let's teach it to open your favorite music player everytime you want to listen one of the listed radios.
In streamtuner open Edit -> Preferences. In the Application tab you will see a table. In the right column you will see "xmms %q" (I think it's the default setting), replace "xmms" with your favorite player but don't forget "%q" at the end of the string. In my case it is set to "beep-media-player %q".


I want to use my VLC media player, so do I simply set it to "VLC %q"?

Thanks

---

### Post by maphew on 2008-03-03
zazen: yes it is enough to simply replace xmms with vlc.

---

### Post by maphew on 2008-03-03
> **wilberfan said:**
> I've managed to open a stream, and Streamtuner starts up Amarok OK, but when I hit record, this is all that displays in a terminal window:

The cursor just stops and blinks at the end of "getting track name...".    The System Monitor shows that streamripper is running (well, 'sleeping').    The STOP button on Streamtuner is greyed-out, though...   I don't think anything is being recorded.

Anyone have any idea what's (not) going on?

I'm getting the same problem trying to record [http://www.cbc.ca/listen/streams/r1_whitehorse_32.html](http://www.cbc.ca/listen/streams/r1_whitehorse_32.html)
I can listen but not record. In the end the only way I managed to get a recording was to bypass streamripper and use VLC by itself. This works but there are lot more clicks and it's is easier to select a combination of options that don't work than do. This is the combination which finally worked for me:

* start VLC
* File > Open Network Stream
* for HTTP/HTTPS/FTP/MMS: [http://www.cbc.ca/listen/streams/r1_whitehorse_32.html](http://www.cbc.ca/listen/streams/r1_whitehorse_32.html)
* check 'steam/save', select 'Settings', then 'Outputs':
  * check 'Play Locally'
  * check 'File', set filename as you wish
  * Encapsulation method: 'Raw'
  * check 'Audio codec', and select 'mpga' from the list, bitrate as you like (96kb is okay  for this particular stream)

It's the audio codec part which tripped me up the most, even though I was saving mp3 selecting mp3 as a code yields a 0 byte file. 

I tried to use the recipe from [http://www.linux.com/articles/43721](http://www.linux.com/articles/43721) for creating a command line script, copying pasting the source & target urls from the procedure outlined above, but this didn't work:

vlc [http://www.cbc.ca/listen/streams/r1_whitehorse_32.html](http://www.cbc.ca/listen/streams/r1_whitehorse_32.html) :sout=#transcode{acodec=mpga,ab=96,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst="/home/matt/Radio/cbc-north.mp3"}

VLC media player 0.8.6c Janus
[00000304] main private error: no sout stream module matched "transcodechannels=2"
[00000303] main stream output error: stream chain failed for `transcodechannels=2:duplicatedst=stddst=/home/matt/Radio/cbc-north.mp3'
[00000301] main input error: cannot start stream output instance, aborting
[00000292] main playlist: nothing to play
[00000292] main playlist: stopping playback

Still, at least I can record *something* :)

SOLVED: for command line vlc the syntax for :sout needs to be single quoted, like so:

```

   vlc http://www.cbc.ca/listen/streams/r1_whitehorse_32.html ':sout=#transcode{acodec=mpga,ab=96,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst="/home/matt/Radio/cbc-north.mp3"}'

```

The same in a bash script, you should only need to edit the INSTREAM and OUTFILE lines to use elsewhere
```

#!/bin/sh
NOW=$(date +%F_%k-%M)
INSTREAM=http://www.cbc.ca/listen/streams/r1_whitehorse_32.html
OUTFILE=/home/shared/Audio/Radio/cbc-north_$NOW.mp3
echo ...
echo ...Recording CBC North internet radio to
echo	$OUTFILE
echo ...expect a 5 second delay before hearing anything
echo ...and a few "access_mms" errors prior to that.
echo ...
/usr/bin/vlc $INSTREAM ':sout=#transcode{acodec=mpga,ab=96,channels=2}:duplicate{dst=display,dst=std{access=file,mux=raw,dst="'$OUTFILE'"}}'

```


solution found via [http://forum.videolan.org/viewtopic.php?f=4&t=40822](http://forum.videolan.org/viewtopic.php?f=4&t=40822)

---

### Post by richieboy on 2008-03-14
i can't figure this out!!!!  i used the search tool in shoutcast and now all i have in the left pane are "top streams" and "search".  how do i get all the different categories back?

---

### Post by nikolai on 2008-03-14
> **richieboy said:**
> i can't figure this out!!!!  i used the search tool in shoutcast and now all i have in the left pane are "top streams" and "search".  how do i get all the different categories back?

+1.  I think something is wrong on the shoutcast server.

---

### Post by mtron on 2008-03-15
yes, also listen doesn't display any shoutcast streams currently :( 
Maybe they made a protocol change?

---

### Post by sureinlux on 2008-03-25
Hi,
 I am using streamtuner and loving it. The problem for me seems to be with streamripper. I configured streamripper as directed in the first post of this thread. But, whenever I press the record button, a new terminal opens saying 'connecting...' and nothing happens after that.
 Any help on that would be great.
 Thanks

---

### Post by sureinlux on 2008-03-25
Hi,
 I just solved it. I am behind a proxy server. so added -p <url> . Worked like a charm.

---

### Post by rggavubt on 2008-03-25
Thanks for the post.  I got everything working but have a question.  Does it record one song or just keep recording until you turn it off.  I'm playing the recording now and it seems to record for as long as you have it on??

---

### Post by Big Dan on 2008-03-29
For those of you using Hardy streamtuner don't 'work' because xmms, streamtuner's default player isn't included in Hardy's repos. 

To fix this open streamtuner and edit the preferences (Edit > Preferences) Change the player to totem and you're all set.

---

### Post by phoenix180 on 2008-05-01
> **Big Dan said:**
> For those of you using Hardy streamtuner don't 'work' because xmms, streamtuner's default player isn't included in Hardy's repos. 

To fix this open streamtuner and edit the preferences (Edit > Preferences) Change the player to totem and you're all set.

I can't get streamtuner to work with Amarok in Kubuntu-8.04 or 8.04 KDE4-and I have installed all of the gstreamer codecs and the restricted depositories..I'm not sure what I'm doing wrong.

---

### Post by fozner on 2008-05-16
I can't get streamripper to work for ogg streams. It just sits there. Well, it seems to work on some of them and not on others.

I finally just went:

wget [http://ogg/stream/path.ogg](http://ogg/stream/path.ogg) &
echo "pkill wget" > t
at 5:30pm -f t

ok sure there is no splitting of songs but that can be done later

---

### Post by markbuntu on 2008-05-24
Streamtuner will play through totem but not through rythmbox. It sives the error "could not open child process, file or directory missing" or something like that. 

But, tunapie will load shoutcasts into rythmbox so if you want to browse shoutcasts and use them in rythmbox you can get tunapie with synaptics. The first time it runs it said, to me anyway, no sound device found or something like that but the next time I started it it ran right away. I just had to open edit/preferences and browse down to rythmbox and select it. If rythmbox is already running tunapie restarts it with the new stream(s) listed in the radio box.

---

### Post by ArtInvent on 2009-03-09
It seems that the latest VLC has different menus/options and maybe works better from the GUI. I'm using VLC 0.9.4 with Ubuntu Intrepid to rip a radio stream that is a 128k mp3 format. It seems possible to rip it without re-encoding and without resorting to the command line. I've only tried this with mp3 streams but it seems to work extremely well. It was kind of hit-and-miss trying to figure out how to do this because VLC's menus are not exactly self-explanatory in this respect, so here's what finally worked.

[SIZE=4]Easily record an MP3 stream with no re-encoding with VLC[/SIZE]

1. Go to Media | Convert/Save
2. 'Network tab' - enter the stream address. For instance, if the stream is at [http://68.183.324.32:8000/radio128.mp3](http://68.183.324.32:8000/radio128.mp3)
just copy that URL to the "Address" box, and the 'Protocol' button should change to HTTP automatically.
3. hit Convert/Save button at bottom, up pops the Stream Output dialog.
4. Check off 'Play locally' and 'File'.
5. Enter the filename such as 'Recording.mp3'
6. 'Encapsulation' tab - select 'RAW'
7. 'Audio codec' tab - check 'Audio' - Codec - 'MPEG Audio'
for the bitrate I left this at 128k and 2 channel, don't know if this makes any difference as we should just be recording whatever the stream is without re-encoding (I beleive.)
8. Hit 'Save'. Stream should start playing and recording.
9. Hit the stop transport button to end the recording.

It seems you can pause and restart the recording by hitting the Pause/Play button.

Warning: if you hit stop, and then hit play again, the previous recording will be lost, and a new one will start with the same filename. Make sure you rename or move your recording before hitting the play button again!

As far as I can hear, the recording sounds as good as the original stream, so as I say, I believe no re-encoding is being done, but not 100% sure.

---

### Post by blueled on 2009-10-19
Very useful thread, thank you all for the detailed info, but...

I cannot find any file in the ./streamtuner folder to backup the Preselections of the stations I added. Does anybody know how do we back it up, or in a clean install I have to type everything again from scratch?

---

### Post by sigurnjak on 2009-10-19
It seems Ubuntu Streamtuner still has issues with shoutcast . 
So ,i thought to post a link for fix :
[http://netherlandsdaniel.blogspot.com/2009/03/fix-shoutcast-plugin-of-streamtuner-in.html](http://netherlandsdaniel.blogspot.com/2009/03/fix-shoutcast-plugin-of-streamtuner-in.html)

---

