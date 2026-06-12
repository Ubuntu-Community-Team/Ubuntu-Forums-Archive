---
title: "Ripping streamed audio to .mp3"
date: 2006-05-02
forum: Outdated Tutorials &amp; Tips
---

### Post by Edward The Bonobo on 2006-05-02
*[COLOR="Sienna"]This is my first ever contribution to the Ubuntu Community&#8230;[/COLOR]*

[SIZE="4"]**How To: Capturing streamed audio as .mp3**[/SIZE]

[SIZE="3"]**Why?**[/SIZE]

Internet radio stations are a rich resource.  More and more of them are archiving their audio material.  Sometimes this can be simply downloaded, simply as a Podcast (usually .mp3, sometimes .ogg).  More often the audio is &#8216;streamed&#8217; &#8211; i.e. the file plays directly but can&#8217;t be saved. 

This guide tells you how to capture Real Audio .ra and .rm streams (the most common kind).  

Some stations also stream .mp3 and .ogg.  There is a separate guide for those, susing StreamTuner and StreamRipper, [here]("http://www.ubuntuforums.org/showthread.php?t=28356").
You can also record the audio from the sound output using something like [Audacity]("http://audacity.sourceforge.net/") &#8211; but the quality is limited by your sound card.  With this method you&#8217;ll be grabbing the digital audio stream file directly.  This process is called **&#8216;Ripping&#8217;**, as opposed to **&#8216;Recording&#8217;**

***NOTE:**  In most countries it is legal to capture streamed audio, provided that this is for personal use and not for further duplication or commercial re-use.  **However **- note the comments [here]("http://www.mega-nerd.com/erikd/vsound/").  Use at your own risk.*

[SIZE="3"]**Steps **[/SIZE]
[LIST=1]
[*]Install Real Player. - this is the easiest way to listen to the audio steams
[*]Install the other software you&#8217;ll need &#8211; Vsound and Sox to grab the audio stream.  Lame to convert it to an .mp3.
[*]Find an audio stream &#8211; it can be slightly tricky to find the URL
[*]Capture your stream - you'll end up with a large .wav file.
[*]Convert your stream to a .mp3 file - to shrink it down to size and make it work on your portable player.
[/LIST]

[SIZE="2"]**How to install Real Player**[/SIZE]

Real Player is a proprietary package.  For information on how to install it, read [here]("https://wiki.ubuntu.com/RealplayerInstallationMethods").  You will also need to configure it to play Real Audio formats.  Read the Real Player section [here]("https://wiki.ubuntu.com/RestrictedFormats"). 

**Install the other software you&#8217;ll need**

Read [here ]("http://help.ubuntu.com/starterguide/C/ch02.html")for general instructions on how to install software.

The packages you need are vsound, lame and sox.  
[LIST]
[*][Vsound]("http://www.vsound.org") grabs audio streams
[*][Sox]("http://sox.sourceforge.net/") converts them to a very large .wav file
[*][Lame]("http://lame.sourceforge.net/index.html") is a handy package for converting most audio file types to most others.
[/LIST]
You may already have these installed.  Otherwise, with Universe and Multiverse repositories enabled, type the following in a terminal window:
```

sudo apt-get install vsound

```
```

sudo apt-get install sox

```
```

Sudo apt-get install lame

```

And you&#8217;re ready to start looking for audio streams.

**Finding your Audio Stream.**

Vsound needs to know the URL of the audio stream it is grabbing.  This may not be obvious at first glance.
For example, some sites, like NPR (eg [here]("http://www.npr.org/templates/story/story.php?storyId=4627437")), nest the URL inside a .smil (Standard Multimedia Integration Language) file.  If you click on the links you will be offered the .smil file to either play in Real Player or save to disk.  Save it.  Then open it with a text editor (right-click).  Inside, you will see the URL.

Elsewhere (eg. BBC Radio, [here]("http://www.bbc.co.uk/radio4/progs/listenagain.shtml") ) you will be offered a .ram file (On the BBC site, right click on 'Play in standalone Real Player' buttons).  Again, save it locally and peek inside using a text editor.  

In either case you&#8217;re looking for a URL which ends with a *something.ra *or *something.rm* filename.

Select and copy the URL.

**Capture your Audio Stream**

Now let&#8217;s get to work.  

***NOTE: **before you start, you are going to me making some massive .wav files &#8211; approx 10MB per minute of recording.  Make sure you have enough disk space for the time you want to record.  You&#8217;ll need about (2.1 x 10 x recording length in minutes)MB.*

Open up a terminal window:
```

vsound &#8211;d &#8211;t &#8211;f *myfilename.wav *realplay *url_of_the_stream_you_want_to_rip*

```
Realplayer will open up and play the stream (the &#8211;d parameter means you can listen while ripping).  At the same time, it will generate a large Sun ULAW format file containing the stream.  When it&#8217;s got what you want, close down Real Player.  Sox will start up, create a .wav file from the ULAW, then delete the ULAW.  This may take some time &#8211; but you can monitor it in a file browser.

**Converting to .mp3**

To convert the massive, unwieldy .wav to a more manageable .mp3 (approx 10% of its size), simply:
```

lame myfilename.wav myfilename.mp3

```
A dialogue will open in your terminal showing the process.  Again, this may take time, depending on your processor speed and the file size.  You can use [Audacity ]("http://audacity.sourceforge.net/") to edit the .mp3 further &#8211; eg to make breaks between songs.

This information was based in part on the following article: [http://www.linux-magazine.com/issue/57/Ripping_Audio_Streams.pdf](http://www.linux-magazine.com/issue/57/Ripping_Audio_Streams.pdf)

[SIZE="3"]**NOTES**[/SIZE]
There is an alternative method just using mplayer and lame here:
[http://www.ubuntuforums.org/showthread.php?t=40193](http://www.ubuntuforums.org/showthread.php?t=40193)

[COLOR="Sienna"][I]btw:  I&#8217;ve structured this file in a particular way which I believe is a good model for How Tos:
**Why** &#8211; start by explaining why the reader might want to follow it: what real world problem will it help with.
**Steps** &#8211; break it up into manageable steps.  List each one and explain what it&#8217;s for.
**Main body** &#8211; keep it brief and simple, explaining what you&#8217;re doing as you go along.
**Link** to other related info. as appropriate.[/I][/COLOR]

---

### Post by shof2k on 2006-05-05
Nicely written!

There is an alternative method just using mplayer and lame here:
[http://www.ubuntuforums.org/showthread.php?t=40193](http://www.ubuntuforums.org/showthread.php?t=40193)

---

### Post by Edward The Bonobo on 2006-05-05
Excellent!  I'll link it.  A question, though...does the mplayer method bypass the soundcard?  That's a major consideration for me, because I have an ancient, crappy, low-spec machine.

Thanks for the compliment about the writing.  I have a bee in my bonnet.  I'm a newbie and not much of a geek.  My learning curve has consisted of a lot of figuring out which bits I do and don't need to know to get my machine into a state where I can use it as a useful life tool.  I reckon that HowTos should start with "Why would anyone want to know this?"  The explanation should focus on the end benefits.

ie not
*libgobbledygook is a thrunge grocket for Gwhoosit libraries*
but
*If you install this, it will make it faster to convert music files.*

---

### Post by shof2k on 2006-05-05
Well it doesn't play the output so I guess it bypasses the sound card, (hence the data dump in step 1).

The best way to learn linux is to find something that bothers you and try to fix it.  I've learnt shed loads about grub, acpi, sound cards, graphics just by playing with it on my laptop....and how to reinstall :)

I agree that functionality should be above techy speak.  Luckily the ubuntu great and the good seem to share this. I have to say this is one of the most approachable and friendliest groups in linux.

---

### Post by groggyboy on 2006-05-05
and gentoo - gentoo has an amazing community.  maybe even better than ubuntu's?

nice HOWTO, just what I was looking for!

i've always had trouble getting podcasts to work for me.  not in windows, back in the day, and not in linux, either.  this sidesteps the whole podcast issue! (provided that the podcaster has streamed content as well)

cheers,
groggyboy

---

### Post by shof2k on 2006-05-07
gentoo has a special 'techy' status.  There is nothing that those guys can't do.  

Aww shucks you're all great!!! :)

---

### Post by Edward The Bonobo on 2006-05-08
With the danger of this turning into a mutual backslapping fest...

(I was going to type 'circle jerk', but thought better of it)

It's the communities that have kept me going these last few months.  The learning curve is *damned *steep for a non-techie like me.  Luckily community support is part of the package.

**NEXT SELF-SET PROBLEM**

Some stations *only *stream live - expecially when issues of music licencing are involved.  So I need to set up some kind of timer routine which will start up vsound while I'm out/ in bed.  Then...because the files get big...it will have to kill Real Player after not too long.

Any ideas where I should start?

---

### Post by Colonel Kilkenny on 2006-05-08
VLC has also capability of capturing streams and transcoding them to mp3.

---

### Post by Edward The Bonobo on 2006-05-08
That sounds promising - especially if it can transcode directly to .mp3 without the intervening .wav stage.

The documentations a little confusing, to my non-geek eye.  Can anyone point me at a How To?  (or, in general, more info.)

---

### Post by Edward The Bonobo on 2006-05-08
It says [here ]("http://www.videolan.org/vlc/features.html")that VLC doesn't support Real audio formats.

---

### Post by shof2k on 2006-05-08
I'm shooting in the dark here, but if you knew the times you could schedule a batch cron job or something similar to capture the stream in whatever format, then run another job to convert to mp3.

Perhaps a techy could design a simpler timer gui for it?

If I get some time between keeping the wife and bairn happy I'll have a look.

---

### Post by Edward The Bonobo on 2006-05-09
Yes...I'd figured out it was probably something to do with a cron.

In this case, it would have to:

[LIST=1]
[*]Start of Vsound at time X...Issue: do station URLs remain constant?
[*]Kill Real Player at time Y, or after M minutes
[*]Ideally, run Lame on the .wav file and delete it once the .mp3 has been made.
[/LIST]

Yes, a cron GUI would be useful.  Maybe there's one out there?  It would be nice to be able to build up commands line by line - basically, I guess, write a script file (is that the right Lx terminology).

In this instance - it would be *extremely* useful if the process could be run in, say, 15 minute batches to deliver a series of manageable .mp3s, rather than one huge .wav to be converted at the end.  I'm not sure if it would be feasible to have Vsound and Sox/Lame running in parallel, though.  Apart from anything, on my machine with a tiny processor (PII 333Hz), it runs at full tilt during the conversion which (I presume) might interfere with the stream grabbing.

Any more tame geeks out there?

---

### Post by Edward The Bonobo on 2006-05-09
Kcron - a KDE front-end for cron: [http://docs.kde.org/stable/en/kdeadmin/kcron/index.html](http://docs.kde.org/stable/en/kdeadmin/kcron/index.html)

Available as .deb

---

### Post by Edward The Bonobo on 2006-06-21
I've linked the HowTo to a new page, listing rtps URLs for various stations [https://help.ubuntu.com/community/RadioURLs](https://help.ubuntu.com/community/RadioURLs).  So far I've only added BBC ones, but I'll be extracting more v. soon.

Any suggestions for other cool/interesting stations I should include?

---

### Post by chriswyatt on 2007-05-02
:( Why do I always run into problems.  I've installed all the packages, followed all the instructions but this happens:

```
chrisw@chrisw-laptop:~$ vsound -d -t -f ./goodeveningwales.wav realplay rtsp://rmv8.bbc.net.uk/wales/radiowales/goodeveningwales_tue.ra
About to start the application. The output will not be available
until the application exits.
Warning: LD_PRELOAD="/usr/lib/vsound/libvsound.so"
Opening ALSA PCM device default
Missing file ./vsound15399.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.
```

Is -t the same as --timing ?  I tried to put --timing in there but it thought it was part of the URL.  Oh, and the ./ before the filename was just another thing I tried, same output either way.

---

### Post by Edward The Bonobo on 2007-05-24
I *think* I've had the same error message simply from a wrong url - although yours looks right.

---

### Post by DesiArnez6 on 2007-06-23
I also receive the same exact error. Haven't found the "cure" yet, but i'll try a few more streams.

---

### Post by ahaslam on 2007-06-23
Just a thought...
Would it be possible to rip a realplayer stream directly to mp3 with something like mencoder & lame?
I rip dvd's to xvid in a similar way & I know mplayer can be used with streaming media, just not tried it...

---

### Post by Bealer on 2007-06-25
I get a similar error with VSound:

```

robert@Rob:~$ sudo vsound realplay rtsp://rmlive.bbc.co.uk/bbc-rbs/rmlive/ev7/live24/radio1/live/r1_dsat_g2.ra
About to start the application. The output will not be available
until the application exits.
/usr/bin/vsound: 177: realplay: not found
Missing file ./vsound8852.au.
This means that the libvsound wrapper did not work correctlty.
Here are some the possible reasons :
 - You are trying to record a stream (RTSP or PNM protocol) from 
   the internet. You will need to use the --timing option.
 - The program you are trying to run is setuid. You will need to 
   run vsound as root.
 - Vsound was not properly installed and hence won't work at all.

```

---

