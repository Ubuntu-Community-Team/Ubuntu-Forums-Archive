---
title: "HOWTO: Rip your Audio CDs to MP3's"
date: 2005-12-04
forum: Outdated Tutorials &amp; Tips
---

### Post by front243 on 2005-12-04
Allright, I have cut and pasted this from [my blog]("http://linuxnewbie.wordpress.com/2005/12/05/make-quality-mp3-rips-in-kubuntu").

Alright, I will teach you how to make high-quality MP3 from Audio CD’s in this tutorial.

First we need to grab some software, so type this in a console:

```
sudo apt-get install lame grip cdparanoia
```

Type your password if you are asked for it. Now we need to start ‘grip’ which is the frontend we will use to rip. Either type ‘grip’ in the console or start it from the menus. In Kubuntu at least it is located in the Multimedia menu.

When you have started grip go to the Config tab and another line of tabs opens, select Rip and Ripper subtabs. Now enter this information:

Ripper: cdparanoia
Ripping executable: /usr/bin/cdparanoia
Rip command-line: -d %c %t[.%b]-%t[.%e] %w
Rip file format: ~/mp3/%A-%d/%t_%n.wav

Now click the Encode tab and Encoder subtab. Make these choices, better cut-and-paste from this page:

Encoder: lame
Encoder command-line: -V 2 –vbr-new –add-id3v2 –pad-id3v2 –ta “%a” –tt “%n” –tl “%d” –ty “%y” –tn “%t” %w %m
Encode file extension: mp3
Encode file format: ~/mp3/%A-%d/%t_%n.%x

Done? Ok, now we’re finished! You can try some of the other options, but just remember not to touch those options I outlined because they are important to get good-quality rips.

All you have to do now is flick a disc in your CDRom drive, and select Rip+Encode from the Rip tab, all your nice mp3’s will be saved in the mp3 subfolder of your home folder.

To end this article I have to thank the people at the [Hydrogenaudio Forums]("http://www.hydrogenaudio.org/") for their recommendations. I used their recommended settings in this article.

---

### Post by Cl1mh4224rd on 2005-12-16
Looks good. I've used the same LAME settings in EAC on Windows.

Unfortunately, Grip (or possibly LAME) doesn't seem to want to actually encode the ripped tracks.

Grip's Status tab says:
> [i]Ripping track 1 to blah.wav
Rip finished
Ripping is finished
1: Encoding to blah.mp3
Eject disc
Finished encoding on cpu 0
Deleting blah.wav[/i]
...but there's no MP3...

**SOLVED:** Eh-heh... I was lazy and copied the encoder command-line string from front243's post. Turns out the double quotes and double dashes had been converted at some point ("" to &#8220;&#8221;, and -- to &#8211;). Fixed those up in Grip and it works beautifully.

Corrected string:
> -V 2 --vbr-new --add-id3v2 --pad-id3v2 --ta "%a" --tt "%n" --tl "%d" --ty "%y" --tn "%t" %w %m

---

### Post by kathymacau on 2005-12-24
[QUOTE=Cl1mh4224rd]Looks good. I've used the same LAME settings in EAC on Windows.

Unfortunately, Grip (or possibly LAME) doesn't seem to want to actually encode the ripped tracks.

Grip's Status tab says:

...but there's no MP3...

**SOLVED:** Eh-heh... I was lazy and copied the encoder command-line string from front243's post. Turns out the double quotes and double dashes had been converted at some point ("" to “”, and -- to –). Fixed those up in Grip and it works beautiful

Corrected string:[/QUOTE]

Thanks guys, busy ripping tracks for tomorrows Xmas lunch.

---

### Post by rklump on 2005-12-27
[QUOTE=front243]To end this article I have to thank the people at the [Hydrogenaudio Forums]("http://www.hydrogenaudio.org/") for their recommendations. I used their recommended settings in this article.[/QUOTE]

Looks great. But I have a problem: I get LAME version 3.96.1 by apt-get. In what repo is the recommended LAME version? That is, LAME version 3.97b2 (b=beta). 

The recommended LAME version is available at [Rarewares]("http://www.rarewares.org/mp3.html/"), but it is not compiled.  :(

---

### Post by cwhitmore75 on 2005-12-27
Perhpas this is a bit off topic...

But when I rip and encode using the setting outlined above the bitrate XMMS shows for the files is 32 kb/s.  File sizes seem comparable to larger bitrate files and the sound seems as good if not better.  However other mp3's I encoded using sound juicer show the correct bitrate in XMMS.

Is there something I am missing?  Or perhaps something I need to change in the encoder command line?

Any suggestions are appreciated.

---

### Post by Cl1mh4224rd on 2006-01-01
[QUOTE=cwhitmore75]Perhpas this is a bit off topic...

But when I rip and encode using the setting outlined above the bitrate XMMS shows for the files is 32 kb/s.  File sizes seem comparable to larger bitrate files and the sound seems as good if not better.  However other mp3's I encoded using sound juicer show the correct bitrate in XMMS.

Is there something I am missing?  Or perhaps something I need to change in the encoder command line?

Any suggestions are appreciated.[/QUOTE]
Well, the command-line options above encode the MP3 as VBR ([variable bit-rate](http://en.wikipedia.org/wiki/Variable_bit_rate)). I can't be sure, but I wonder if XMMS is just grabbing the bit-rate from the first frame of the song and that's it. The first frame is typically silence, so that may be why it's only showing 32kbps.

Sound Juicer, I don't know... does it encode MP3s as CBR (constant bit-rate)? If it does, that would be why it displays correctly.

---

### Post by tofuconfetti on 2006-01-08
Can someone post the EXACT repository line to add to sources.list where the lame encoder can be downloaded. I still can't get any synaptics source to recognize lame even exists.  I've even tried installing it from the *.deb package with dpkg and it doesn't install the libmp3lame.so.* file.  I need it so that audacity can output mp3's.  I also understand that audacity asks for the wrong lib file and have that one solved IF I can every get lame installed.  This is unusually stubborn compared to other distributions.

Thanks.

NOTE: I found it, not sure why this one isn't there by default ??

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) breezy universe main restricted multiverse

---

### Post by matthewinuk on 2006-03-21
many thanks. my mp3s are souning great
;)

---

### Post by WetWilly on 2006-03-22
managed to rip using the correct string by Cl1mh4224rd, but its rips WAAAAY slower than using sound juicer to encode .ogg


Sound Juicer around 8-9x

Grip 2-3x....

anyone knows why?

---

### Post by nothi on 2006-08-23
I have a problem with my Grip and Sound Juicer. the first one ripps my cds very slow, and quality is ok, but it cuts 4-5s from each file. What's the problem?

SJ ripps my cds faster, but files are broken, and they'r very big - 3 minutes = 22mb. What's wrong? 

During configuring both of programs i followed all steps from this thread. There is olso one more problem with SJ. It starts olny once. I needto reboot my system to run SJ one more time. 
Can you help me, please?

---

### Post by megamania on 2006-09-30
> **nothi said:**
> I have a problem with my Grip and Sound Juicer. the first one ripps my cds very slow, and quality is ok, but it cuts 4-5s from each file. What's the problem?

I am experiencing the same problem: tracks ripped to mp3 with Grip (3.3.1) are missing the first 2-5 seconds.

Does anybody know how to fix this? It makes the program completely useless...

---

### Post by senn on 2006-10-01
sorry megamania , but i dont use grip i use RipperX to encode to mp3 its easy to use and the quality is good, you can find it in add/remove under audio/video.

---

### Post by Lord Landis on 2006-11-20
Holy crap, senn, you were right!  RipperX is far better than SoundJuicer, and a lot easier to use.  Now if only it were a GTK2 application...  Then again, if it works well, it doesn't need to be pretty.

---

### Post by TwistedTripper on 2006-11-30
> I am experiencing the same problem: tracks ripped to mp3 with Grip (3.3.1) are missing the first 2-5 seconds.

Does anybody know how to fix this?

I am experiencing the same said loss. Has anyone come up with a solution?

---

### Post by Hopey on 2006-12-08
> **TwistedTripper said:**
> I am experiencing the same said loss. Has anyone come up with a solution?

Same here. Anyone know a solution?

EDIT:

Ok some digging and trying to remember 3-4 year old things when I tried grip+paranoia last time. I've had this problem before when using external paranoia with grip. Solution is to use internal paranoia, it should work better. Here is what is said in paranoias troubleshoot section:

"Cdparanoia doesn't get the track beginning and end exactly correct
This can happen for two reasons; one is the drive's/discs fault (discussed here) and the other is bug when using -B; that one is discussed on the bugs page.

Drives are not required to be able to seek exactly to any position; they simply must be able to hit within one second. Add to this the fact that the disc itself is premitted to be off by a bit as well, and you can well land well too early or too late.

The good news is that such discs and CDROM drives are rare. I've not been able to reproduce reports of drive models with this problem myself, and all the untested reports are currently by Toshiba drive owners. More news on this subject as I get it; new TOC code to appear at some point in alpha 10 might provide a good workaround for this problem."

I hope this helps someone out ther :) Amazing that simple thing as ripping mp3 is still so crappy in linux :O

---

### Post by Twizz on 2007-04-29
Ah! Thx, I actually tried the GRIP(cdparanoia) Insted of just cdparanoia, and it fixed the 1-4 second mess up at the start of the songs.  I used all the same info provided in this HOWTO, just changed the ripper.  It seems to rip faster now also.   Which is a good thing since I have to re-rip all my CD's now lol  Thank you for the help :)

> **Hopey said:**
> Same here. Anyone know a solution?

EDIT:

Ok some digging and trying to remember 3-4 year old things when I tried grip+paranoia last time. I've had this problem before when using external paranoia with grip. Solution is to use internal paranoia, it should work better. Here is what is said in paranoias troubleshoot section:

"Cdparanoia doesn't get the track beginning and end exactly correct
This can happen for two reasons; one is the drive's/discs fault (discussed here) and the other is bug when using -B; that one is discussed on the bugs page.

Drives are not required to be able to seek exactly to any position; they simply must be able to hit within one second. Add to this the fact that the disc itself is premitted to be off by a bit as well, and you can well land well too early or too late.

The good news is that such discs and CDROM drives are rare. I've not been able to reproduce reports of drive models with this problem myself, and all the untested reports are currently by Toshiba drive owners. More news on this subject as I get it; new TOC code to appear at some point in alpha 10 might provide a good workaround for this problem."

I hope this helps someone out ther :) Amazing that simple thing as ripping mp3 is still so crappy in linux :O

---

### Post by joris1977 on 2008-04-21
Nice howto!, I was looking for a native linux ripper for some audiobooks and  Grip seems to do fine. 

I had to change the %x to mp3 to make Grip encode to mp3's otherwise it wouldn't work. This is in Hardy, maybe a bug, but i am not sure.

so i changed this line

Encode file format: ~/mp3/%A-%d/%t_%n.%x

to

Encode file format: ~/mp3/%A-%d/%t_%n.mp3

and it worked

---

### Post by Avatar_5 on 2008-04-30
Thanks for this HOWTO, it still works perfectly a few years down the line.

Thanks for easing my Windows to Ubuntu transition. :)

---

