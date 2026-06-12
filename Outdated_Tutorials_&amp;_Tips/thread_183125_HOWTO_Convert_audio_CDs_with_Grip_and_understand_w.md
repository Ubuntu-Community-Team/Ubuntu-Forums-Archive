---
title: "HOWTO: Convert audio CDs with Grip and understand what you are doing."
date: 2006-05-27
forum: Outdated Tutorials &amp; Tips
---

### Post by MetalMusicAddict on 2006-05-27
This guide is constantly worked on and should always be as up-to-date with the current version of Ubuntu . :) This guide will deal mostly how to set up the encoder for Grip but will be expanded and refined.

Here I will attempt to help you convert you audio CDs to computer formats.

_**[SIZE="4"] References [/SIZE]**_

[LIST]
[*]_Grip_
[LIST]
[*][Grip switches]("http://nostatic.org/grip/doc/ar01s04.html#gripswitches")
[*][Grip-users page]("http://sourceforge.net/mailarchive/message.php?msg_id=8217031")
[/LIST]
[/LIST]

[LIST]
[*]_LAME_ [SIZE="1"](mp3)[/SIZE]
[LIST]
[*][LAME commandline switches]("http://lame.cvs.sourceforge.net/*checkout*/lame/lame/USAGE")
[*][More ]("http://lame.sourceforge.net/doc/html/switchs.html")
[*][Hydrogenaudio LAME FAQ]("http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings")
[/LIST]
[/LIST]

[LIST]
[*]_WAVPACK_
[LIST]
[*][WAVPACK commandline switches]("http://www.wavpack.com/wavpack_doc.html")
[/LIST][/LIST]

[LIST]
[*]_MUSEPACK_
[LIST]
[*][In the CLI type: man mppenc]("http://www.musepack.net")
[/LIST][/LIST]

[LIST]
[*]_FLAC_
[LIST]
[*][FLAC commandline switches]("http://flac.sourceforge.net/documentation_tools_flac.html")
[/LIST][/LIST]

[LIST]
[*]_Ogg-Vorbis_
[LIST]
[*][Vorbis commandline switches]("http://mp3.radified.com/ogg_switches.htm")
[/LIST][/LIST]

[LIST]
[*]_FAAC_
[LIST]
[*][FAAC commandline switches]("http://www.audiocoding.com/modules/wiki/?page=faac#HelpScreen") [SIZE="1"](mentions windows but the switches are right)[/SIZE]
[/LIST][/LIST]

[LIST]
[*]_AACPLUSENC_
[LIST]
[*][AACPLUSENC commandline switches]("http://teknoraver.campuslife.it/software/mp4tools/") [SIZE="1"](Coming soon.)[/SIZE]
[/LIST]
[/LIST]

_**[SIZE="4"] Getting The Software [/SIZE]**_

Lets start off by enabling the "Multiverse" repos by going to **System->Administration->[COLOR="Navy"]Synaptic Package Manager[/COLOR]**.

Once up, go to **Settings->[COLOR="Navy"]Repositories[/COLOR]**.

On the "Ubuntu 6.10" tab make sure the Universe and Multiverse repos are checked. Hit the **"Close"** button then hit the **"Reload"** button in the upper-left of Synaptic.

After the refresh we're gonna go to the terminal just to switch it up on ya. ;)
[SIZE="1"](Skip the above step if your using Ubuntu 7.04 and above.)[/SIZE]

Open a terminal and type:
```
sudo apt-get install grip lame
```
This will get the [Grip]("http://nostatic.org/grip/") and [LAME]("http://lame.sourceforge.net/") packages needed.

Or use this to get Grip plus extra codecs.
```
sudo apt-get install grip lame faac flac vorbis-tools wavpack mppenc aacplusenc
```

_**[SIZE="4"]Configuring The Encoder[/SIZE]**_
We'll use .mp3's as the example.

Go to **Applications->Sound & Video->[COLOR="Navy"]Grip[/COLOR]** to launch Grip.
Once Grip is up click on the **"Config"** tab then the **"Encode"** tab. This is where we will do most of our work.

You should see this at first:
[[IMG]http://img137.imageshack.us/img137/9918/small5wm.png[/IMG]]("http://img82.imageshack.us/img82/6259/bigg8dp.png")

OK. Heres where it got all confusing for me and where I'm really gonna help you.

Change the the **"Encoder"** drop-down menu options to look like:
[LIST]
[*]Encoder: lame
[*]Encoder executable: /usr/bin/lame
[*]Encoder command-line: -h -b %b %w %m
[*]Encode file extension: mp3
[*]Encode file format ~/mp3s/%A/%d/%n.%x
[/LIST]


Let me explain 2 things. Anything with a **[COLOR="Navy"]-[/COLOR]** in front of it, like, **[COLOR="Navy"]-h[/COLOR]** is a option passed to the **[COLOR="Navy"]Encoder[/COLOR]**. Anything with a **[COLOR="Red"]%[/COLOR]** is a option passed to [COLOR="Red"]**Grip**[/COLOR].

So this; **[COLOR="Navy"]-h -b[/COLOR] [COLOR="Red"]%b %w %m[/COLOR]** means.

[LIST]
[*]**[COLOR="Navy"]-h[/COLOR]** High quality.
[*]**[COLOR="Navy"]-b[/COLOR]** Specified minimum allowed bitrate (8,16,24,...,320. ie: -b 320).
[*][COLOR="Red"]**%b**[/COLOR] The bitrate that files are being encoded at.
[/LIST]
-These 2 below shouldn't be messed with unless you know what you are doing.-
[LIST]
[*]**[COLOR="Red"]%w[/COLOR] **The filename of the wave file being ripped.
[*]**[COLOR="Red"]%m[/COLOR]** The filename of the file being encoded.
[/LIST]

All that will result in a Joint Stereo, 128kbps CBR 44.1khz.mp3

_**[SIZE="4"] My Settings [/SIZE]**_
[URL="http://img146.imageshack.us/img146/6550/big0se.png"]
[IMG]http://img146.imageshack.us/img146/8467/small1nq.png[/IMG][/URL]
My **"Encoder command-line"** looks like, **[COLOR="Navy"]-h -V 3[/COLOR] [COLOR="Red"] %w %m[/COLOR]**.

[LIST]
[*]**[COLOR="Navy"]-h[/COLOR]** High quality.
[*][COLOR="Navy"]**-V 3**[/COLOR] Variable Bitrate switch with a quality level of 3. The "space" in between the capital **[COLOR="Navy"]"V"[/COLOR]** and the **[COLOR="Navy"]"3"[/COLOR]** are needed.
[See the LAME commandline switches links above for more options.
[/LIST]
-These 2 below shouldn't be messed with unless you know what you are doing.-
[LIST]
[*]**[COLOR="Red"]%w[/COLOR]** The filename of the wave file being ripped.
[*]**[COLOR="Red"]%m[/COLOR]** The filename of the file being encoded.
[/LIST]

_**[SIZE="4"] Other Examples [/SIZE]**_

Say you wanted a really normal standard like a **High-quality, Stereo, CBR 192**.mp3
**[COLOR="Navy"]-h -b 192 -m s[/COLOR] [COLOR="Red"] %w %m[/COLOR]** would be your **"Encoder command-line"** setting.

[INDENT]**[COLOR="Red"]Note[/COLOR]** - Anything not strictly defined will revert to defaults. ie: If you wanted a 48kHz sampling rate for your .mp3 and didn't define it it will be created at 44.1kHz.[/INDENT]

```

**_MP3_** - Needs the "lame" package from the repos. [(click here for example pic)]("http://img73.imageshack.us/img73/2797/lamekd4.png")
[SIZE="2"]**[COLOR="Navy"]-V 3 --vbr-new[/COLOR] [COLOR="Red"]%w %m[/COLOR]**[/SIZE]

_**FLAC**_ - Needs the "flac" package from the repos. [(click here for example pic)]("http://img292.imageshack.us/img292/3679/flacic6.png")
[SIZE="2"]**[COLOR="Navy"]-V --best -T TITLE=%n -T ALBUM=%d  -T TRACKNUMBER=%t -T ARTIST=%a -T GENRE=%G -T DATE=%y -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**[/SIZE]

_**WAVPACK**_ - Needs the "wavpack" package from the repos. [(click here for example pic)]("http://img261.imageshack.us/img261/6887/wavpackft3.png")
[SIZE="2"]**[COLOR="Navy"]-w "Artist=%a" -w "Title=%n" -w "Album=%d" -w "Year=%y" -w "Track=%t" -w "Genre=%G" -hh -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**[/SIZE]

_**MUSEPACK**_ - Needs the "mppenc" package from the repos. [(click here for example pic)]("http://img141.imageshack.us/img141/8171/screenshotfu4.png")
[SIZE="2"]**[COLOR="Navy"]--standard --ape2 --artist "%a" --title "%n" --album "%d" --year "%y" --track "%t" --genre "%G" -[/COLOR] [COLOR="Red"]%m %w[/COLOR]**[/SIZE]

_**OGG**_ - Needs the "vorbis-tools" package from the repos. [(click here for example pic)]("http://img159.imageshack.us/img159/5571/oggpu8.png")
[SIZE="2"]**[COLOR="Navy"]-q 6 -a %a -l %d -t %n -d %y -N %t -G %G -b %b -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**[/SIZE]

_**FAAC**_ - Needs the "faac" package from the repos. [(click here example pic)]("http://img69.imageshack.us/img69/9366/faacog4.png")
[SIZE="2"]**[COLOR="Navy"]-w -q 192 --artist "%A" --track "%t" --title "%n" --album "%d" --year "%y" --genre "%G" -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**[/SIZE]


_**AACPLUSENC**_ - Needs the "aacplusenc" package from [Medibuntu]("http://www.medibuntu.org"). [(click here example pic)]("http://img69.imageshack.us/img69/9366/faacog4.png")
[SIZE="2"]**[COLOR="Navy"] --artist "%A" --track "%t" --title "%n" --album "%d" --year "%y" --genre "%G" -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**[/SIZE]


```

[INDENT]**[COLOR="Red"]Note[/COLOR]** - Make sure you have your Universe and Multiverse repos open to get the appropriate codecs if you're using Ubuntu 6.10 and below.[/INDENT]


So hopefully this will help anyone wanting to use Grip. :) Remember to read through my references. They will really help once you get your head around how arguments are passed. Use what's best for you.

---

### Post by MetalMusicAddict on 2006-05-29
With new CDs is there an advantage to CDparanoia?

---

### Post by george_apan on 2006-05-29
Seriously, people should stop recommending CBR encodings and command line switches they know nothing about. Presets are there for a reason. Stick to them and use only a suitable -V x switch. See the relative page at the HA wiki if you're interested: [http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#Recommended_Encoder_Settings)

---

### Post by MetalMusicAddict on 2006-05-29
Whos _recommending_ a CBR setting?

---

### Post by george_apan on 2006-05-29
Well, you are. Why else would you give an example of a "High-quality, Stereo, CBR 192" encoding? This is not a high quality encoding by all means. It is instead a perfect waste of bits. And the first setting you give is also a 128kbps CBR encoding. Please give examples of command lines people should actually use.

---

### Post by MetalMusicAddict on 2006-05-29
> **george_apan]Well, you are. Why else would you give an example of a "High-quality, Stereo, CBR 192" encoding?[/QUOTE]
No, Im not.  said:**
> This is not a high quality encoding by all means. It is instead a perfect waste of bits.
I whole heartedly agree. Maybe you could have assumed some would use _my_ settings, humm?
> And the first setting you give is also a 128kbps CBR encoding.
The 1st setting is what comes up as the default. Its there to show them what their screen would look like at the beginning. Its an _example_ to help people to understand what they are doing.  I made this HOWTO to do just that.
> Please give examples of command lines people should actually use.Im not here to tell people what to use. Thats a personal choice. I have given plenty of links to help them with that choice.


Please read and understand a little more before jumping to incorrect conclusions. Or at least ask first. ;)

---

### Post by george_apan on 2006-05-29
Well, you made a thread about creating mp3s. If you do not wish to provide any sane settings then you should point (in a clear way) people to wherever they could find such information. Sorry if I came out a little hard on you, I didn't mean to. Anyway, my advice for you if you want to listen to it, is to drop the "-m s" switch for your personal settings. It does way more harm than good to your encoding. And for this howto you can give a few examples like "if your want a standard sized (~128kbps) mp3 use only the -V 5 switch", or "if you want an encoding that is as close to the original as possible without wasting bits use the -V 2 switch".

---

### Post by MetalMusicAddict on 2006-05-29
[QUOTE=george_apan]Anyway, my advice for you if you want to listen to it, is to drop the "-m s" switch for your personal settings. It does way more harm than good to your encoding.[/QUOTE]
Exactly how? From what Ive read if I dont add the "-m s" to force "stereo" -V 3 will use joint stereo. Which sacrifices seperation for fidelity. Dont really wanna do that. :)

---

### Post by george_apan on 2006-05-29
[QUOTE=MetalMusicAddict]Exactly how? From what Ive read if I dont add the "-m s" to force "stereo" -V 3 will use joint stereo. Which sacrifices seperation for fidelity. Dont really wanna do that. :)[/QUOTE]
This is a common misunderstanding. Joint-stereo is always better than forced stereo with LAME. You can read more here: [http://www.hydrogenaudio.org/forums/index.php?act=ST&f=15&t=683](http://www.hydrogenaudio.org/forums/index.php?act=ST&f=15&t=683) Especially post #2.

---

### Post by MetalMusicAddict on 2006-05-29
From HAF:
[QUOTE=tangent]While this may be true for a few popular encoders which have screwed up Joint Stereo implementation (FHg, **Xing**, etc), this is not true for LAME.[/QUOTE]
Ahh... I see. In my early mp3 creation days I used AudioCatalyst which used Xing. So when I went to [Audiograbber]("http://www.audiograbber.com-us.net") I tried to use similar settings. Though I did up my VBR settings when I went to LAME. 

With Grip/LAME now Ill do some studio and home listening tests to see if its makes a audiable difference. If not Ill ditch it. I dont suspect it will.

What do you think about **[COLOR="Navy"]-h -p -V 3 --vbr-new[/COLOR]**? Specificlly the **[COLOR="Navy"]-p[/COLOR]** switch. Is error protection needed?

---

### Post by MetalMusicAddict on 2006-05-29
If others are interested I can add info on FLAC, FAAC and other formats. Im learning about how to now.

---

### Post by george_apan on 2006-05-30
[QUOTE=MetalMusicAddict]
What do you think about **[COLOR="Navy"]-h -p -V 3 --vbr-new[/COLOR]**? Specificlly the **[COLOR="Navy"]-p[/COLOR]** switch. Is error protection needed?[/QUOTE]
-h is not a good idea. -q 2 (-h) became -q 3 in newer versions of LAME and that is the recommended setting which is also the default. -q 2 is equivalent to the older -q 1 and might show some regressions. And -p is not a good idea either. It uses 16 bits/frame and will raise the bitrate with no quality increase and lower the quality for a given bitrate. I don't think there are any decoders out there that check CRCs anyway. Just **[COLOR="Navy"]-V 3 --vbr-new[/COLOR]** would be fine. Generally just stick to the presets (-V x). Anything that should be tweaked for higher quality is already tweaked by the LAME developers. --vbr-new is also a good idea with LAME 3.96 and newer since the algorithm it uses is a lot faster with no audible quality regression.

---

### Post by Denim on 2006-05-30
Thanks for the How-to. I'm new with this OS, but have used EAC / LAME in the past. My final goal would be to get a FLAC and LAME MP3 file (each in the desired directory (folder)). To soon to ask questions on that, but had to send a thanks for what has been provided so far.

---

### Post by MetalMusicAddict on 2006-05-30
[QUOTE=Denim]Thanks for the How-to. I'm new with this OS, but have used EAC / LAME in the past. My final goal would be to get a FLAC and LAME MP3 file (each in the desired directory (folder)). **To soon to ask questions on that**, but had to send a thanks for what has been provided so far.[/QUOTE]
Its OK. Ask away. Maybe george_apan can recommend some things. ;)

One thing I have left out was some of the Grip specific commands. Its own documentation is pretty good. LAME is really and how it works with Grip is where I was fuzzy.

Finding an app in linux to replace Audiograbber or EAC has been 2 year ordeal. I finally sat down and spent a whole day to figure out Grip (still learnin'). Seems to be the best, full-featured ripper/encoder for Gnome.

---

### Post by Denim on 2006-05-30
Now that I've used grip, I see that my goal of creating a FLAC and MP3 file with 1 action is likely impossible. However, I am impressed with the speed of creating the initial WAV files. I was getting about 7 - 8X rip speeds. I had all of the paranoia options on, and only had a moment where the happy face changed his mood. If this rips with the same reliability as EAC, then it's a great tool. 

I deviated from your command settings for LAME and used the presets that I have used before. It's currently notworking correctly, but I'll get to the bottom of that soon.

I did want to ask about ID3 tagging. My previous experience was to include the ID3 tags in the LAME commands. Any opinions / thoughts here on the best strategy? I haven't tried it yet and not sure if it will even fit, or work.

---

### Post by MetalMusicAddict on 2006-05-30
[QUOTE=Denim]Now that I've used grip, I see that my goal of creating a FLAC and MP3 file with 1 action is likely impossible.[/QUOTE]
No its quite possiable. :) I have also added FLAC and FAAC to the encoder options but havnt used 'em as I dont know alot about 'em yet.> However, I am impressed with the speed of creating the initial WAV files. I was getting about 7 - 8X rip speeds. I had all of the paranoia options on, and only had a moment where the happy face changed his mood. If this rips with the same reliability as EAC, then it's a great tool. 

I deviated from your command settings for LAME and used the presets that I have used before. It's currently notworking correctly, but I'll get to the bottom of that soon.
What are you trying to get? Post your encoder line.
> I did want to ask about ID3 tagging. My previous experience was to include the ID3 tags in the LAME commands. Any opinions / thoughts here on the best strategy? I haven't tried it yet and not sure if it will even fit, or work.
Im adding tags with the Grip GUI. Really sir, the Grip "Help" tab will help and look at the link I posted for Grip switches. :) Just play around.

---

### Post by Denim on 2006-05-30
I'm posting and troubleshooting this problem as I go, and appreciate your willingness to help. 

Problem solved. I was using -V 0 --vbr-new, but forgot the  %w %m. The MP3 files were not getting populated with the data. Instead, I had a 2K file. This was good for me, I used lame from the command line for troubleshooting. 

I suggest listing the V switches (with %W %m) so that users can cut and paste into Grip. I'll respond tomorrow if I get the chance to provide the list.

Thanks again!

---

### Post by george_apan on 2006-05-31
@ Denim

I don't think it's possible to get multiple outputs (flac + mp3) with grip. The best you can do is rip to wav and then encode that to flac and mp3. However, you can have a try with ABCDE. It's a shell script (no gui here) and it supports multiple outputs by using a comma-separated list: -o flac,mp3. You can have a look at this howto: [http://ubuntuforums.org/showthread.php?t=109429](http://ubuntuforums.org/showthread.php?t=109429)

---

### Post by MetalMusicAddict on 2006-05-31
[QUOTE=Denim]I'm posting and troubleshooting this problem as I go, and appreciate your willingness to help. 

Problem solved. I was using -V 0 --vbr-new, but forgot the  %w %m. The MP3 files were not getting populated with the data. Instead, I had a 2K file. This was good for me, I used lame from the command line for troubleshooting.[/QUOTE] 
Glad you got it. 
> I suggest listing the V switches (with %W %m) so that users can cut and paste into Grip. I'll respond tomorrow if I get the chance to provide the list.

Thanks again!
I wont list all the switches because Ive already provided many links to them. Listing them all so people can cut and paste IMHO makes people a little lazy. The guide already makes it easy. Just a little reading is needed. I even already had your problem addressed.

> -These 2 below shouldnt be messed with unless you know what you are doing.-
[LIST]
[*]**[COLOR="Red"]%w[/COLOR] **The filename of the wave file being ripped.
[*]**[COLOR="Red"]%m[/COLOR]** The filename of the file being encoded.
[/LIST]
;)

---

### Post by barney_1 on 2006-06-02
Thanks for the guide.  I just stumbled across the program earlier today (errr yesterday now I gues) and spent a few hours getting cozy with the switches.  I'm impressed with it's ease of adaptation to my music titling and tagging schemes.  I'd recommend this prog, especially after the shock of seeing the limitations of Sound Juicer.

---

### Post by MetalMusicAddict on 2006-06-06
[QUOTE=barney_1]Thanks for the guide.  I just stumbled across the program earlier today (errr yesterday now I gues) and spent a few hours getting cozy with the switches.  I'm impressed with it's ease of adaptation to my music titling and tagging schemes.  I'd recommend this prog,** especially after the shock of seeing the limitations of Sound Juicer.**[/QUOTE]
Thats ultimately why I sucked it up and learned Grip. Sound Juicer just doesnt cut it for people who are serious about their music. Grip looks to be the most fully featured ripper/encoder for linux.

---

### Post by stoffe on 2006-06-27
You should add info about how to do Ogg Vorbis properly (instead). As much as Sound Juicer may not cut it for people who are serious about music, MP3 does not cut it for people serious about their freedom. ;)

---

### Post by MetalMusicAddict on 2006-06-27
[QUOTE=stoffe]You should add info about how to do Ogg Vorbis properly (instead). As much as Sound Juicer may not cut it for people who are serious about music, MP3 does not cut it for people serious about their freedom. ;)[/QUOTE]
If you wanna write it up you can post it or give it to me and Ill add it as a *alternative* choice. ;)

Do you know of a command line reference for vorbis? Im also gonna add FAAC and FLAC when I get the time/proper documentation.

I wanna add I love vorbis but it doesnt cut it for the battery life on mine and most DAPs. Its more CPU intensive and therefore drains battieries faster.

---

### Post by bionnaki on 2006-07-09
so, what should I put if I want an alt-preset-standard rip?

---

### Post by krazyd on 2006-07-10
> **bionnaki said:**
> so, what should I put if I want an alt-preset-standard rip?

-V 2 = --alt-preset-standard

The alt-presets aren't used anymore. See here:
[http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28Variable_bitrate.29_settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28Variable_bitrate.29_settings)

---

### Post by pchr on 2006-07-10
I too spent a few hours looking into the different mp3 rippers, grip felt like the best for me.

Regarding the talk of CBR/VBR, I use CBR myself, I've heard of a few mp3 playing devices that get upset with VBR files and disc space is cheap.

Anywho here's some settings I use:

I change the "Encode File Format" line to read: ~/Recordings/%A/%d/%t %n.%x
Where "Recordings" would be the folder in your home directory where you store your mp3s.  The only addition is the %t which adds the track number to the start of the file name.  This is very useful for devices/software that don't read the tags.

On options I set "Number of CPUs to use" to 2.  I've got a hyper threading CPU and the 686 kernel and this has the effect of encoding two tracks at a time.  (this is cool to watch (if you're a bit sad), you get two little encoding graphs)

Finally I disable the CD Paranoia stuff, I look after my CDs and my CD player in PC is good quality and this speeds things up a fair bit.  If a CD does rip wrong I can always turn CD Paranoia on and re-rip.

---

### Post by bionnaki on 2006-07-10
> **krazyd said:**
> -V 2 = --alt-preset-standard

The alt-presets aren't used anymore. See here:
[http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28Variable_bitrate.29_settings](http://wiki.hydrogenaudio.org/index.php?title=LAME#VBR_.28Variable_bitrate.29_settings)

oh, didnt know. been using aps for awhile now.

anyways, so what should I enter for the commandline?

---

### Post by bionnaki on 2006-07-10
-V 3 --vbr-new %w %m
perhaps?

---

### Post by ign on 2006-07-11
this thread is been extremely useful, thanks to the previous posters.
is there a way to make encode many files at the same time time using lame (for examples, all the WAVs in a folder to MP3)?
i've seen a lot of scripts around the forums, but i find them complicated, isn't there a simpler way to do that?

---

### Post by seelk on 2006-07-28
How can I have my files come in a Proper format?  Currently the filenames and folders all come lower case and with underscores.  Is there a way to fix that?

---

### Post by MetalMusicAddict on 2006-07-28
> **seelk said:**
> How can I have my files come in a Proper format?  Currently the filenames and folders all come lower case and with underscores.  Is there a way to fix that?
Its in **Config->Misc->[COLOR="Blue"]"Do not lowercase filenames"[/COLOR]**

---

### Post by Kobo_W_Italy on 2006-12-12
Thanks for the perfect guide!!!! Finally I can rip cd!!!! :D :D

---

### Post by MetalMusicAddict on 2006-12-12
No problem. :) I plan on updating it soon to help people create other formats.

---

### Post by jkroto on 2006-12-20
> **MetalMusicAddict said:**
> This is written from a Dapper point of view but should work fine for other versions of Ubuntu. :) This guide will deal mostly how to set up the encoder for Grip but will be expanded and refined.


MetalMusicAddict,
Have been looking at this thread to help get my grip with better settings.  I see a few posts after the original you had a discussion with respect to VBR and settings.  Are the settings in your original post still your current settings to get a good rip/encode.

Also, a very basic question, what is the difference between rip and rip+encode?  Or when should one be used and not the other?

thanks for any guidance.

---

### Post by MetalMusicAddict on 2006-12-20
> **jkroto said:**
> MetalMusicAddict,
Have been looking at this thread to help get my grip with better settings.  I see a few posts after the original you had a discussion with respect to VBR and settings.  Are the settings in your original post still your current settings to get a good rip/encode.
I didnt change the 1st post to reflect my settings because I was hoping I gave enough info for people to understand and choose for themselves. Maybe I should change it to reflect the chat after the 1st post. In the end heres what I settled on:

**_MP3_** - Needs the "lame" package from the repos.
**[COLOR="Navy"]-V 3 --vbr-new[/COLOR] [COLOR="Red"]%w %m[/COLOR]**

Heres some other settings of mine:

_**FLAC**_ - Needs the "flac" package from the repos.
**[COLOR="Navy"]-V --best -T TITLE=%n -T ALBUM=%d  -T TRACKNUMBER=%t -T ARTIST=%a -T GENRE=%G -T DATE=%y -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**

_**OGG**_ - Needs the "vorbis-tools" package from the repos.
**[COLOR="Navy"]-q 6 -a %a -l %d -t %n -d %y -N %t -G %G -b %b -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**

_**FAAC**_ - Needs the "faac" package from the repos.
**[COLOR="Navy"]-w -q 192 --artist "%A" --track "%t" --title "%n" --album "%d" --year "%y" --genre "%G" -o[/COLOR] [COLOR="Red"]%m %w[/COLOR]**

Make sure you have all your repos open.
> Also, a very basic question, what is the difference between rip and rip+encode?  Or when should one be used and not the other?
"Rip" will just give you the uncompressed .WAV file right from the disk. "Rip+Encode" takes the .WAV file and converts them to yout format of choice.
> thanks for any guidance.
Im glad someone likes the guide. :)

Im gonna give more info on how I came to these settings when I update the 1st post. Im gonna do it this week. Still, feel free to ask me about my settings.

---

### Post by jkroto on 2006-12-30
> **MetalMusicAddict said:**
> I didnt change the 1st post to reflect my settings because I was hoping I gave enough info for people to understand and choose for themselves. Maybe I should change it to reflect the chat after the 1st post. In the end heres what I settled on:

MetalMusicAddict,
Thank you for the information and the simple answer to my questions.  I was reading up on lame, grip and other things generally related from the links you provided in your first post.  This did help me to understand the settings available.  I am using your suggestions, as I would suspect if you find them acceptable, so I don't need to re-invent the wheel.  Although I do realize that different people would have different setting for various reasons, including size, quality, etc.  I need to sacrifice some quality to cram as much onto my MP3 player as possible.  I save the lossless flac's and shn's for my quality home stereo.

A few more questions:
1. So far, I do encode everything I rip to mp3.  I understand the other possible encoders options, but do the other ripping options make any difference to the final produce (be it MP3 or other?)
2. In your travels here have you run across any good converters of flac or shn.  I have search but found no good answers.  I download taper friendly shows in those formats and do retain the lossless versions, but like to convert some for ipod use.

Thanks again,
John

---

### Post by MetalMusicAddict on 2006-12-30
> **jkroto said:**
> MetalMusicAddict,
Thank you for the information and the simple answer to my questions.
No problem. ;)
> I was reading up on lame, grip and other things generally related from the links you provided in your first post.  This did help me to understand the settings available.  I am using your suggestions, as I would suspect if you find them acceptable, so I don't need to re-invent the wheel.  Although I do realize that different people would have different setting for various reasons, including size, quality, etc.  I need to sacrifice some quality to cram as much onto my MP3 player as possible.  I save the lossless flac's and shn's for my quality home stereo.
Im glad the info is helping someone. :)
> A few more questions:
1. So far, I do encode everything I rip to mp3.  I understand the other possible encoders options, but do the other ripping options make any difference to the final produce (be it MP3 or other?)
I would say the "[COLOR="Navy"]**-V 3**[/COLOR]" is where you would see a difference. Its the VBR quality setting. So file size and fidelity is where you would see a immediate difference. I would just say play with them. :) I took a day to play with all of this and see what worked for me.
> 2. In your travels here have you run across any good converters of flac or shn.  I have search but found no good answers.  I download taper friendly shows in those formats and do retain the lossless versions, but like to convert some for ipod use.

Thanks again,
John
I havnt had any need so far to go from a lossless format to another. Transcode will probably be a answer you will get alot. I think theres a GUI besides DVD:RIP but I havnt seen it in a bit.

---

### Post by klato on 2006-12-31
Thanks for this guide!  I use -V 2 --vbrnew for my music now.  Only thing is that I can't get Grip to save my settings when I exit (i.e. Do Not Lowercase filenames and my file naming scheme is lost every time :( Using Grip 3.3.1

---

### Post by MetalMusicAddict on 2006-12-31
> **klato said:**
> Thanks for this guide!  I use -V 2 --vbrnew for my music now.  Only thing is that I can't get Grip to save my settings when I exit (i.e. Do Not Lowercase filenames and my file naming scheme is lost every time :( Using Grip 3.3.1

Hmm.... :-k 

Try deleting your .grip file in your home dir and see if it saves after that. Also, did you run Grip as root at any time?

---

### Post by SuperMike on 2006-12-31
My daughter tried Grip with lame encoding and found that one 12 song audio CD took several hours to complete. We only went with the default settings. What would you guys recommend I change on the settings so that this runs faster but doesn't impede the sound quality that bad for an iPod?

---

### Post by MetalMusicAddict on 2006-12-31
> **SuperMike said:**
> My daughter tried Grip with lame encoding and found that one 12 song audio CD took several hours to complete. We only went with the default settings. What would you guys recommend I change on the settings so that this runs faster but doesn't impede the sound quality that bad for an iPod?

What point took several hours? The "Rip" or "Encode" process?

---

### Post by dcstar on 2006-12-31
> **MetalMusicAddict said:**
> What point took several hours? The "Rip" or "Encode" process?

Exactly, if was the "Rip" phase, then switching on "Disable paranoia" & "Disable extra paranoia" in Config-Rip will speed things up as far as reading the CD - albeit at the cost of possibly not reading 100% correctly off scratched or dirty disks.

---

### Post by dcstar on 2006-12-31
I also set my System-Preferences-Removable Drives and Media Preferences to use grip for the Audio CD Disks application.

I then set grip to "Auto-rip on insert", this had the side-effect of opening multiple instances of grip when I inserted another CD for ripping to Mp3 whilst the first disk had not completed, and both instances of grip then tried to rip and encode the one disk!

I got around this by turning off "Poll disk drive for new disk", then the new instance would start up and begin the process, but the old instance would not see the new CD.

If anyone knows of the command line switch to only have one instance of grip running, I'd like to know of it.......          ;)

---

### Post by MetalMusicAddict on 2006-12-31
> **dcstar said:**
> Exactly, if was the "Rip" phase, then switching on "Disable paranoia" & "Disable extra paranoia" in Config-Rip will speed things up as far as reading the CD - albeit at the cost of possibly not reading 100% correctly off scratched or dirty disks.
Thats where I was going with the question. 12hrs is a oddly long time though. I would think your CD drive was rather slow or that the CD was really scratched.
> **dcstar said:**
> I also set my System-Preferences-Removable Drives and Media Preferences to use grip for the Audio CD Disks application.

I then set grip to "Auto-rip on insert", this had the side-effect of opening multiple instances of grip when I inserted another CD for ripping to Mp3 whilst the first disk had not completed, and both instances of grip then tried to rip and encode the one disk!

I got around this by turning off "Poll disk drive for new disk", then the new instance would start up and begin the process, but the old instance would not see the new CD.

If anyone knows of the command line switch to only have one instance of grip running, I'd like to know of it.......          ;)
Im unsure of this one.

---

### Post by techstop on 2007-01-01
Thanks for the howto MMA! No thanks to the thread crapping by george_apan! :roll: 

grip really is great, especially compared to that woeful program soundjuicer. grip has everything I need and it works well. One more reason not to boot back into Windows (for EAC). Cheers! \\:D/

---

### Post by MetalMusicAddict on 2007-01-01
> **techstop said:**
> One more reason not to boot back into Windows (for EAC). Cheers! \\:D/

Yea. Same here. I REALLY wanted to get away from Audiograbber so I just sat down and took a day or so to work out Grip.

If anyone knows of something to add here let me know. I wonder If I should make this a WIKI page?:-k

---

### Post by MetalMusicAddict on 2007-01-06
Anyone here know alot about cdparanoia?

---

### Post by porco.rosso on 2007-01-08
Please let me understand:

FIRST:

when I put this setting on lame:

lame -h --cbr 192 -m s almost.wav

answer is:

couldn't find 192

when I put this setting on lame:

lame -h --cbr192 -m s almost.wav

I obtain this output:

lame: unrec option --cbr192
LAME version 3.96.1 ([http://lame.sourceforge.net/](http://lame.sourceforge.net/))
CPU features: MMX (ASM used), 3DNow! (ASM used), SSE
Using polyphase lowpass filter, transition band:  8269 Hz -  8535 Hz
Encoding almost.wav to almost.wav.mp3
Encoding as 22.05 kHz  32 kbps single-ch MPEG-2 Layer III (11x) qval=2
    Frame          |  CPU time/estim | REAL time/estim | play/CPU |    ETA 
  7474/7476  (100%)|    0:04/    0:04|    0:13/    0:13|   40.173x|    0:00 
average:  32.0 kbps

ReplayGain: -2.4dB

and the file encoded is a 763,1 kB file with 32 kbps and MPEG-1 layer 3 type.

SECOND:

with the SAME setting on GRIP: -h --cbr192 -m s %w %m

I obtain this file a 3 MB file with 128kbs and MPEG1 layer 3 type.

HOW IS IT POSSIBLE? Something missed in my test?

ANOTHER QUESTION:

if I'd like to have a MPEG-3 layer 3 constant bit rate file at 192 or 320 kbit and with a frequency of 44,1 KHz...

WHAT THE HELL I MUST SET IN GRIP??? :)

and why output in file properties is different from output declared in terminal?

and why output in terminale is different from output in Grip whit the same command?

Why grip doesn't work with your 192 kbit configuration?

Thanks a lot for the answers 

this is driving me mad...

---

### Post by MetalMusicAddict on 2007-01-08
> **porco.rosso said:**
> Please let me understand:

FIRST:

when I put this setting on lame:

lame -h --cbr 192 -m s almost.wav

answer is:

couldn't find 192

when I put this setting on lame:

lame -h --cbr192 -m s almost.wav

I obtain this output:
Whats the "almost" part? Is that only through the terminal?
> SECOND:

with the SAME setting on GRIP: -h --cbr192 -m s %w %m

I obtain this file a 3 MB file with 128kbs and MPEG1 layer 3 type.

HOW IS IT POSSIBLE? Something missed in my test?

ANOTHER QUESTION:

if I'd like to have a MPEG-3 layer 3 constant bit rate file at 192 or 320 kbit and with a frequency of 44,1 KHz..

WHAT THE HELL I MUST SET IN GRIP??? :)
The correct arguments. :) Some of the info I have above is wrong. :(
> and why output in file properties is different from output declared in terminal?
Because different apps read the files differently for some reason. Happens to me as well.
> and why output in terminale is different from output in Grip whit the same command?
Because the arguments that you put in the "Encoder command-line" field are arguments for Grip *and* LAME. In a terminal you just passing the commands to LAME.
> Why grip doesn't work with your 192 kbit configuration?
Because I was wrong. :(
> Thanks a lot for the answers 

this is driving me mad...
No problem I understand. Gets me turned around sometimes as well. Like today. :)

We'll breakdown below what was the issue.

Taken from [HERE]("http://lame.cvs.sourceforge.net/*checkout*/lame/lame/USAGE").
> [SIZE="1"]Constant Bit Rate (CBR)
-b  n          set bitrate (8, 16, 24, ..., 320)
--freeformat   produce a free format bitstream.  User must also specify
               a bitrate with -b, between 8 and 640 kbps.

Variable Bit Rate (VBR)
-v             VBR
--vbr-old      use old variable bitrate (VBR) routine (default)
--vbr-new      use new variable bitrate (VBR) routine
-V n           VBR quality setting  (0=highest quality, 9=lowest)
-b  n          specify a minimum allowed bitrate (8,16,24,...,320)
-B  n          specify a maximum allowed bitrate (8,16,24,...,320)
-F             strictly enforce minimum bitrate
-t             disable VBR informational tag 
--nohist       disable display of VBR bitrate histogram

--abr n        specify average bitrate desired[/SIZE]

**[COLOR="Navy"]-h --cbr 192 -m s[/COLOR] [COLOR="Red"] %w %m[/COLOR]** was the old, incorrect line.

**[COLOR="Navy"]-h -b 192 -m s[/COLOR] [COLOR="Red"] %w %m[/COLOR]** Is correct.

Where **[COLOR="Navy"]-h[/COLOR]** was the correct switch for bitrate. It uses CBR by default unless told otherwise.

Now remember, with **[COLOR="Navy"]-h[/COLOR]** and **[COLOR="Navy"]-m s[/COLOR]** I'm forcing "high quality" and "stereo". These settings might not be need as LAME has gotten better. Its for you to decide.

Thanx for bringing this to my attention. I really recommend reading *_all_* the links Ive posted above. Its all I did to sort out the problem. ;)

---

### Post by porco.rosso on 2007-01-08
Thanks a lot for your fast answer, your help in this wiki is truly appreciated, and excuse my bad English, I'm writing from Florence, Italy.

Thank You Again!

---

### Post by jkroto on 2007-01-09
> **MetalMusicAddict said:**
> Anyone here know alot about cdparanoia?

MMA,
Sorry, don't know if I can help with what you might be looking for.  Although I was researching the same b/c I have one CD that won't rip/encode the last track.  I assume it is scratched or otherwise defiled.  I was trying to figure out what I can change to have it push through the problem but no luck so far.
What are you trying to figure out?

---

### Post by MetalMusicAddict on 2007-01-09
> **MetalMusicAddict said:**
> Anyone here know alot about cdparanoia?

> **jkroto said:**
> MMA,
Sorry, don't know if I can help with what you might be looking for.  Although I was researching the same b/c I have one CD that won't rip/encode the last track.  I assume it is scratched or otherwise defiled.  I was trying to figure out what I can change to have it push through the problem but no luck so far.
What are you trying to figure out?

I was just wondering uses/settings that might be beneficial to the guide. I want to understand how it works. I have to do some reading on my own but time is scarce lately. ;)

---

### Post by Rumpanzle on 2007-01-10
Thanks for the nice HOWTO!

Maybe one addition. I couldn't figure out how to make one big image of all the tracks, like you might want to have from a mix cd. So I dug into the cdparanoia documentation an came out with a commandline like "cdparanoia 1- target.wav".

To use that in Grip go to Configuration/Rip/Ripper and change the Ripper from the default "grip (cdparanoia)" to "cdparanoia". Change the commandline from the default "-d %c %t:[.%s]-%t:[.%e] %w" to "1- %w". To rip you select only Track 1. You can watch Track 1 to be ripped, after that you only notice a grow on your targetfile till the rip is finished.
(I tried another method, but it had drawbacks, too)

If there is an easy method to rip an image...shame on me, I couldn't figure it out.

---

### Post by MetalMusicAddict on 2007-01-10
> **Rumpanzle said:**
> Thanks for the nice HOWTO!

Maybe one addition. I couldn't figure out how to make one big image of all the tracks, like you might want to have from a mix cd.
I _think_ theres a way to do this but Im unsure. I looked around for awhile and couldnt find it. :(
> So I dug into the cdparanoia documentation an came out with a commandline like "cdparanoia 1- target.wav".

To use that in Grip go to Configuration/Rip/Ripper and change the Ripper from the default "grip (cdparanoia)" to "cdparanoia". Change the commandline from the default "-d %c %t:[.%s]-%t:[.%e] %w" to "1- %w". To rip you select only Track 1. You can watch Track 1 to be ripped, after that you only notice a grow on your targetfile till the rip is finished.
(I tried another method, but it had drawbacks, too)

If there is an easy method to rip an image...shame on me, I couldn't figure it out.
Im still gonna look into it. Ill post back with anything I find.

---

### Post by dessip on 2007-02-01
Hey,

Thank you for this help, its excellent, but i have a few problems if you wouldn't mind helping

this is my encode settings:
```
 -b 192 -B 192 --add-id3v2 --pad-id3v2 --ta &#8220;%a&#8221; --tt &#8220;%n&#8221; --tl &#8220;%d&#8221; --ty &#8220;%y&#8221; --tn &#8220;%t&#8221; %w %m 
```

But the problem is i am getting these characters after every encode
```
â&#8364;
```
so i was wondering if there was a way that i can remove them, or if there is something wrong with my encode settings.

I am getting the random character on the Title, Album and Artist field. And thou its not a major problem because i could remove it all myself, but the problem is, im about to import my CD collection with about 200-300 CD's and i really dont want to have to change all the tracks to remove that, and i really dont want to install windows just to do this.

Thanks in advance,

---

### Post by MetalMusicAddict on 2007-02-01
> **dessip said:**
> Hey,

Thank you for this help, its excellent, but i have a few problems if you wouldn't mind helping

this is my encode settings:
<code> -b 192 -B 192 --add-id3v2 --pad-id3v2 --ta “%a” --tt “%n” --tl “%d” --ty “%y” --tn “%t” %w %m </code>

But the problem is i am getting these characters after every encode
<code>â€</code>
so i was wondering if there was a way that i can remove them, or if there is something wrong with my encode settings.

I am getting the random character on the Title, Album and Artist field. And thou its not a major problem because i could remove it all myself, but the problem is, im about to import my CD collection with about 200-300 CD's and i really dont want to have to change all the tracks to remove that, and i really dont want to install windows just to do this.

Thanks in advance,

Ill look at it in depth later but Im gonna say you dont need all those tagging options. There's a config tab for the id3 tags and it might be causing a conflict. Try changing that there or your string.

Ill come back to this later though.

---

### Post by MetalMusicAddict on 2007-03-25
> **Rumpanzle said:**
> Thanks for the nice HOWTO!

Maybe one addition. I couldn't figure out how to make one big image of all the tracks.

If there is an easy method to rip an image...shame on me, I couldn't figure it out.

Via another thread. Last time I tried this it didnt work for me but I will post a confirmation soon. (tired now):( 

> **AlistairH said:**
> I've just downloaded Grip as I couldn't get Sound Juicer to rip to MP3 properly. I'm glad I did because Grip has the ability to rip multiple, concurrent tracks as one audio file.

On the Grip interface you'll find the RIP tab. There you'll find the option to Rip Partial Track which implies you can rip a section of a track rather than the whole thing. However, use the following trick to rip multiple tracks as one file.

1. With a CD in your CDROM drive switch to the **TRACKS** tab on Grip.
2. Select the first track of the multiple tracks you wish to rip.
3. Switch back to the **RIP** tab and make sure that **Rip Partial Track** checkbox is selected.
4. Take a note of the figure in the **End Sector** box.
5. Switch back to the **TRACKS** tab and select the next track.
6. Back to the **RIP** tab and take a note of the **End Sector** figure for this track.
7. Carry on doing this for how many consecutive tracks you want to rip as one audio file.
8. On the **TRACKS** tab make sure only the first song has a tick mark in the corresponding  **Rip** checkbox.
9. Switch back to the **RIP** tab and in the **Start Sector** box make sure it has a 0 (zero).
10. In the **End Sector** box the figure should be the total of all the End Sector figures you recorded in the previous steps.

Click on the **Rip + Encode** button and away you go.

You can also do this in reverse by selecting the last track you want and putting a negative number in for the Start Sector figure. A little bit more complicated but it works.

The Grip version I'm using, ver 3.3.1, complains afterward when I try to quit the application that it is busy doing something. However, the audio file has already been created. Simply confirm that you want to quit doesn't seem to cause any harm. I'm presuming this error has something to do with the technique I'm using here but as it does appear to be critical I won't lose sleep over it.

---

### Post by Jarn on 2007-04-01
Is Grip as good as EAC? Does it clear the cached audio data, etc.?

---

### Post by MetalMusicAddict on 2007-04-01
> **Jarn said:**
> Is Grip as good as EAC? Does it clear the cached audio data, etc.?

Best thing I can say is try it for yourself. It is the most feature-rich linux ripper/encoder.

---

### Post by Jarn on 2007-04-01
Edit: blanked

---

### Post by ukripper on 2007-05-31
Worked perfectly and ripping +Encoding is really fast . Encoding mp3's at 192 KBs by using -h -b 192 -m s  %w %m  switch. Great howto.
Thanks

---

### Post by MetalMusicAddict on 2007-06-01
> **ukripper said:**
> Worked perfectly and ripping +Encoding is really fast . Encoding mp3's at 192 KBs by using -h -b 192 -m s  %w %m  switch. Great howto.
Thanks

Your welcome.

I'm still looking to add info to this HOW-TO. If anyone has any good info to add Id like to hear it.

---

### Post by ukripper on 2007-06-02
Currently just encoding mp3s without a hitch. Once i make any changes to current setings i will post here.

---

### Post by kaj on 2007-06-12
I use the encoder gogo instead of lame. It is much faster (3 to 5 times).
I have only tried the default commands, but maybe I should experiment a little.
But I can't hear any difference in quality using lame or gogo, and the file sizes are about the same.

---

### Post by ukripper on 2007-06-13
> **kaj said:**
> I use the encoder gogo instead of lame. It is much faster (3 to 5 times).
I have only tried the default commands, but maybe I should experiment a little.
But I can't hear any difference in quality using lame or gogo, and the file sizes are about the same.

where can you find that encoder - gogo?

---

### Post by vanadium on 2007-06-13
It should be easy to set up Grip for encoding several formats at the same time. In Config - Encode - Encoder - Encoder executable, you could probably just stick your own custom little bash proggie instead of /usr/bin/lame. The "encoder command-line" would then reduce to "%w %m", the Encoder file extension" should remain empty.

Suppose the bash script is ~/bin/flacmp3

It would be in its simplest form:

!#/bin/bash
lame -V 2 --vbr-new "$1" "$2"
flac -8 "$1" "$2"

The script must be executable, of course. Then "encoder executable" will read "~/bin/flacmp3.

It is just an idea I give: I did not try this myself.

---

### Post by MetalMusicAddict on 2007-06-13
> **ukripper said:**
> where can you find that encoder - gogo?

It's in the repos. Just search for package **gogo**.

---

### Post by ukripper on 2007-06-14
> **MetalMusicAddict said:**
> It's in the repos. Just search for package **gogo**.

Thanks mate, does it work without any problem with Grip or i have to encode seperately after ripping?

---

### Post by MetalMusicAddict on 2007-06-18
> **ukripper said:**
> Thanks mate, does it work without any problem with Grip or do I have to encode separately after ripping?

Should work like any other codec. Never tried this one myself.

---

### Post by Nameless_one on 2007-07-02
I have a question, but I am not sure about the forum's policy about questions in HOWTOs. If this isn't the right place, just say so and I'll delete this and start a thread somewhere. So, here goes: 

I am using grip (used the tutorial to configure it to encode in VBR with lame, too, thanks for that), and I want the encoded files to end up under a default directory, under folder for artist name etc., as is provided by default. However, the folder and the files end up with underscores instead of spaces and other chars. I looked around for a setting covering this, but I found nothing. 

Any ideas?

---

### Post by MetalMusicAddict on 2007-07-02
> **Nameless_one said:**
> I have a question, but I am not sure about the forum's policy about questions in HOWTOs. If this isn't the right place, just say so and I'll delete this and start a thread somewhere. So, here goes:
Naa... Here's cool.

> 
I am using grip (used the tutorial to configure it to encode in VBR with lame, too, thanks for that), and I want the encoded files to end up under a default directory, under folder for artist name etc., as is provided by default. However, the folder and the files end up with underscores instead of spaces and other chars. I looked around for a setting covering this, but I found nothing. 

Any ideas?
Config->Misc: "Do Not Change spaces to underscores"

---

### Post by Nameless_one on 2007-07-02
Oh thanks. And I suppose I should add charactes like ":" to "Characters not to strip from filenames" eh? Because I think it did that too. 

Thank you :) Missed that.

---

### Post by Sweet Spot on 2007-07-16
I seem to be having a hell of a time getting GRIP to work for me. I have tried using LAME, Oggenc and FLAC. I can get it to encode to FLAC, but unfortunately the files aren't tagged except for the names of the songs. 


The problem I'm having as of now with Mp3's, is that when the rip is finished, the .wav file disappears as is told to do, but I'm left with absolutely no other file. I don't know where the Mp3 went to, or if it's even created at all ? If you look at the attachment, I did tell Grip where to put all the files..does that look correct ? And yes, of course the actual directory does exist.... 

Encoding to Ogg seems to be working fine, so I'm  not sure of what's up with encoding to Mp3. Any help would be greatly appreciated. Till then, I rip to Ogg I guess. 

Doug

For my Mp3 files, I have it set up as such:

---

### Post by MetalMusicAddict on 2007-07-16
Sweet Spot

Can you please post the entire string for "Encode File Format"? Its chopped off in the screenshot. Also, make sure you have LAME installed. If you didnt know, its not there by default.

Once I'm done ripping my current CD. Ill take screenshots of my settings.

Also you can see what the issue is if you open up a terminal and run grip from there. If it errors on something it will show there.

---

### Post by Sweet Spot on 2007-07-16
Here you go MMA:

"~/1- All Stuff/Ripped CD's/%A/%d/%n.%x"

As for LAME being installed, I'm pretty sure it is. When I go to /usr/bin, I do see LAME.  I think it's one of the first things I installed via Synaptic when I installed Feisty the other day. I think I made a point to install all the encoders and codecs which aren't 'supported' because I'm not using Automatix this time round. 

edit: Hmm, upon looking, I didn't *(don't) have liblame installed. Could that be it ? Going to install now. 

Doug

Nope, that didn't help anything. Is there another setting I'm missing ? What about the Encode filter command in the encode options tab ? Does that need filling out ?

---

### Post by Sweet Spot on 2007-07-17
Trying another go today, but noticed a different problem now. My Ogg files aren't tagged properly, in that there are no numbers for the songs.  I made sure to add the %t in place of the %d which I didn't need, but no matter which option I tick, I can't get file numbers next to the song names. Also, playing the ripped Ogg files on my iRiver IHP 120, it thinks that they're FLAC files for some reason ?  Now I'm really confused. 

Doug

---

### Post by MetalMusicAddict on 2007-07-17
> **Sweet Spot said:**
> Trying another go today, but noticed a different problem now. My Ogg files aren't tagged properly, in that there are no numbers for the songs.  I made sure to add the %t in place of the %d which I didn't need, but no matter which option I tick, I can't get file numbers next to the song names. Also, playing the ripped Ogg files on my iRiver IHP 120, it thinks that they're FLAC files for some reason ?  Now I'm really confused. 

Doug

Look carefully at your settings. 1 typo can make a world of difference. Make sure your settings for ogg-vorbis aren't calling for FLAC somehow. You can use FLAC in a .ogg container.

Theres alot of things I could tell you to check but really its best to look over and study the info in the 1st post. I have alot of relevant links as well as my personal settings as examples. I know its alot but all the answers are there. My ogg-vorbis setting puts the track number in the tag.

---

### Post by Sweet Spot on 2007-07-17
Nothing is working for me with Grip at this point. I keep trying different settings, but none seem to change much at all. I'm reading, but to be honest, the tutorial doesn't really seem to be helping me very much, which may totally be my fault. No matter what I do, Mp3 files do not appear, so I guess are not encoded at all from the wav files. 

I'm getting a bit tired of trying to set it up now too, and am afraid that some information comes across as being almost cryptic to me. What's weird is that I used to set up stuff like this all the time, for things like EAC and Razor lame, with no problems whatsoever. 

There are definitely more settings available than you actually cover in the screen captures, and I may be messing with them in a way which is doing me no good ?

This may sound like overkill, but I'd really appreciate it if you could show me your settings EXACTLY so I can use them as an example, and work it from there. Is that possible ?   Also, do the repos link to the newest and most stable version of LAME (3.97) upon install ?  I'm just really going out of my mind trying to figure out why the LAME exe isn't doing its job, and why Oggenc seems to be creating files which look like Ogg's, but are tagged as FLAC's. I'm also still not getting anything accomplished with the ID tags. Getting desperate now. 

doug

---

### Post by MetalMusicAddict on 2007-07-17
> **Sweet Spot said:**
> Nothing is working for me with Grip at this point. I keep trying different settings, but none seem to change much at all. I'm reading, but to be honest, the tutorial doesn't really seem to be helping me very much, which may totally be my fault. No matter what I do, Mp3 files do not appear, so I guess are not encoded at all from the wav files. 

I'm getting a bit tired of trying to set it up now too, and am afraid that some information comes across as being almost cryptic to me. What's weird is that I used to set up stuff like this all the time, for things like EAC and Razor lame, with no problems whatsoever.
EAC/Audiograbber here. :)
> There are definitely more settings available than you actually cover in the screen captures, and I may be messing with them in a way which is doing me no good ?

This may sound like overkill, but I'd really appreciate it if you could show me your settings EXACTLY so I can use them as an example, and work it from there. Is that possible ?   Also, do the repos link to the newest and most stable version of LAME (3.97) upon install ?  I'm just really going out of my mind trying to figure out why the LAME exe isn't doing its job, and why Oggenc seems to be creating files which look like Ogg's, but are tagged as FLAC's. I'm also still not getting anything accomplished with the ID tags. Getting desperate now. 

doug

Sure. Ill archive up my settings and attach them in a little bit. ATM I have to finish some things in windows.

---

### Post by Sweet Spot on 2007-07-17
Thanks man, I really appreciate it. Gonna just hang back with this huge headache in the meantime. :(

Doug

---

### Post by Sweet Spot on 2007-07-17
Latest blunder: I'm not sure of how I achieved getting that no access error ! ?  The second shot shows that I'm not crazy, and do have lame.....  The no access thing is now happening w/Ogg as well. What have I done ? JANE @@ ! GET ME OFF THIS CRAZY THIIING !  :o

---

### Post by MetalMusicAddict on 2007-07-17
> **Sweet Spot said:**
> Latest blunder: I'm not sure of how I achieved getting that no access error ! ?  The second shot shows that I'm not crazy, and do have lame.....  The no access thing is now happening w/Ogg as well. What have I done ? JANE @@ ! GET ME OFF THIS CRAZY THIIING !  :o

HeHe. I already see 3 issues.

Your "Encode FIle Format" settings. You're missing the **~** at the beginning and your putting .mp3 at the end. Thats a global setting and should always be: **.%x**.

ie:** /mp3/%A/%d/%n.mp3** in your settings should be: **~/mp3/%A/%d/%n.%x**

Your "Encode File Extension" doesn't need the dot in front of it either. ie: Should just be: **mp3**.

I would also look at your "Rip FIle Format" settings as well.

I've attached my settings. You must show hidden files and back up your files 1st. (just in case)

---

### Post by kgr132 on 2007-07-17
Awesome HOWTO! You just moved me one step closer to ditching Windoze permanently. Thanks.
-K-

---

### Post by Sweet Spot on 2007-07-18
MMA, thanks man, I think I"m getting there finally ! Problem was that I was trying so many variations of what you have listed, that even when one setting was right, the other was nixed, and as you said..if just one thing is off, the whole thing suffers.  I may be technically minded, but I've always been confused about this particular set up in any piece of software, and think it would be useful for people such as myself to have everything spelled out, as you did at one point by saying that "there must be a space in between 'x' and 'y'  ... This way less mistakes would be made. 

I have a question for you now:  On the options tab in encoding, is the encoding bitrate ONLY relative to the argument set for Mp3's, or does it also apply to the VBR of Ogg files even though putting in q6 etc.. tells it what the vbr should be in the first place. Is it redundant, or will it over ride the Q setting ?  And...if you set the encoding bit rate to 'x', but you have a command line argument which tells it to encode at vbr 'x', which will be correct ?  I hope you understand what I"m asking. 

One more question. In regards to ID tags, which line should I mess with in order to eliminate things like album name and artist name, the encoding command line, or the ripping command line ?  For example: I like to have my songs only show the track number and name of the song. So, if I'm encoding with ogg, should I just take the tag out from the encoding line, or from the ripping one ? I'm assuming the former.  I guess this is related to the tick boxes in the ID3 section, in which it says to untick the boxes if encoding with anything other than the Mp3 format... 

Thanks man, you've been extremely helpful  !

Doug

---

### Post by MetalMusicAddict on 2007-07-18
> **Sweet Spot said:**
> MMA, thanks man, I think I"m getting there finally ! Problem was that I was trying so many variations of what you have listed, that even when one setting was right, the other was nixed, and as you said..if just one thing is off, the whole thing suffers.  I may be technically minded, but I've always been confused about this particular set up in any piece of software, and think it would be useful for people such as myself to have everything spelled out, as you did at one point by saying that "there must be a space in between 'x' and 'y'  ... This way less mistakes would be made. 
I understand but if I spelled out *every* little detail this HOW-TO would become too much info (borders on that now) I'm sure. I also want people to learn. ;)
> I have a question for you now:  On the options tab in encoding, is the encoding bitrate ONLY relative to the argument set for Mp3's, or does it also apply to the VBR of Ogg files even though putting in q6 etc.. tells it what the vbr should be in the first place. Is it redundant, or will it over ride the Q setting ?  And...if you set the encoding bit rate to 'x', but you have a command line argument which tells it to encode at vbr 'x', which will be correct ?  I hope you understand what I"m asking. 
Anything set in "Encoder command-line" will override that setting.
> One more question. In regards to ID tags, which line should I mess with in order to eliminate things like album name and artist name, the encoding command line, or the ripping command line ?  For example: I like to have my songs only show the track number and name of the song. So, if I'm encoding with ogg, should I just take the tag out from the encoding line, or from the ripping one ? I'm assuming the former.  I guess this is related to the tick boxes in the ID3 section, in which it says to untick the boxes if encoding with anything other than the Mp3 format... 
The only format effected by the ID3 tab is .mp3s. I go with the defaults thats why with my .mp3 settings the "Encoder command-line" arguments are so few. If you look at the other formats I have more arguments. They fill in the tags for the particular format. So if you want only particular fields filled in you .mp3s you'll have to define them in "Encoder command-line". I have pages for all the arguments in the 1st post. Though, I need to find a better one for vorbis.

"Encoder file format" only effects the way the file itself is named. If you notice, it stays fixed when you change formats in the drop-down.
> Thanks man, you've been extremely helpful  !

Doug
No problem. Just pass the info along. Help others. ;)

---

### Post by The other One on 2007-07-19
Excellent guide, MMA. I'm another former EAC user that wasn't happy with soundjuicer.

Anyhoo, is it possible to simply re-encode existing .wavs on my HDD? I've read vague mentions of this on the Grip website and here - I think - but can't find the options/controls to do this.

---

### Post by MetalMusicAddict on 2007-08-05
> **The other One said:**
> Excellent guide, MMA. I'm another former EAC user that wasn't happy with soundjuicer.

Anyhoo, is it possible to simply re-encode existing .wavs on my HDD? I've read vague mentions of this on the Grip website and here - I think - but can't find the options/controls to do this.

Sorry man. I'm so late on this one. AFAIK Grip can't do it. I usually just cd into the dir and convert them.

ie:
```
cd /media/Audio/Artist/Album
```
then
```
[COLOR="Red"]flac[/COLOR] [COLOR="Blue"]-V --best[/COLOR] *.wav
```
[COLOR="Red"]flac[/COLOR] <- app name of the format you want to go to.
[COLOR="Blue"]-V --best[/COLOR] <- arguments for that format.
*.wav <- this will process any .wav file in the dir you're cd'ed into.

Then I tag with [EasyTag]("http://easytag.sourceforge.net"). I used to use [Tag&Rename]("http://www.softpointer.com/tr.htm") in windows but have found EasyTag more than capable once I got used to how it worked.

---

### Post by vanadium on 2007-08-15
I see two problems with Grip as a qualitative equivalent to Exact Audio Copy for secure rips.

1) I do not see a logging function in Grip! During the ripping of a track, a smiley appears showing whether all goes well. Does this mean that we need to be sitting watching the screen to be sure tracks were ripped error free?

2) cdparanoia (which grip uses) is said not to handle caching drives well: it simply checks the rip by requesting the data again. A caching drive will resend the data from the cash instead of reading them again. Thus, the same  (possibly erroneous) data are send again, cdparanoia sees the data are identical and assumes the rip is ok.

A minor, third issue I see is that grip does not easily allow to store different configurations. You cannot have naming settings for regular album cd's and other naming settings for "Various artist" CDs, for example. You cannot quickly switch from ripping to mp3 to ripping to flac, for example.

Please comment and correct me if I am wrong (I'd be glad I was ...). I currently reverted to ripping with cdparanoia on the command line, because this way the status bars remain visible after the rip.

---

### Post by MetalMusicAddict on 2007-08-15
vanadium. As this is a HOWTO thread I don't feel this is the place to discuss this.

---

### Post by eeried on 2007-08-20
Hello,
Can you set a bitrate when you want to rip and encode in FLAC? If that's possible Which bitrate can you set? I'd like the best quality.

Should I simply add -8 to the command line in Grip?

--best= highest compression but what I'm looking for isn't compression but quality although FLAC is a lossless format.

If I understand right after reading the FLAC doc is the default compression rate is 5.

So "best" or which number?

thanks in advance

Grip is great I think (on Xubuntu).

---

### Post by MetalMusicAddict on 2007-08-20
All the -number switches apply a amount of compression. So in this case compression=quality.  -best is equal to -8. -8 and -best are the most amount of compression you can apply and gives you the smallest file. So even though its the most compression yoy will not notice a audible difference between it and And the .wav or a .FLAC file with less compression. I don't know why anyone would use another setting. :)

Since Grip doesn't handle the tagging you have to put those arguments in the encoder line.

My setting looks like:
```
[SIZE="1"]-V --best -T TITLE=%n -T ALBUM=%d  -T TRACKNUMBER=%t -T ARTIST=%a -T GENRE=%G -T DATE=%y -o %m %w[/SIZE]
```

---

### Post by vanadium on 2007-08-20
Indeed, with FLAC, you always retain the original audio quality. The only reason why you would use a lower setting is the speed of creating the compressed file. For archival purposes, I guess you indeed would want a maximum compression even at the expense of longer compression times.

---

### Post by IronArjen on 2007-08-31
Great,

Finally after one year struggling I can share my music with my MP3 player. 
One question: is it possible to create folders that start with Capitals, or all words that start with capitals. Really a detail.

Thanks, 

Another  addict

---

### Post by IronArjen on 2007-08-31
MetalMusicAddict,

Can you add to the HOWTO the following in order that programs recognize the tracks (ID3!)

In the Config tab, goto the ID3 tab and mark both Add ID3 and ID3v2 tags.

In this way the mp3 files will have an internal tag that e.g. Rhytmbox etc. uses to identify what it is, which they do independly of the archive name.

---

### Post by Mr.nano on 2007-09-06
Hey guyz, just a quick question:
From time to time I'm not pleased with the songs' names that CDDB gives me and so I want just to edit some of them to make them shorter.  So whta's the deal, how do I do that?

---

### Post by MetalMusicAddict on 2007-09-07
> **Mr.nano said:**
> Hey guyz, just a quick question:
From time to time I'm not pleased with the songs' names that CDDB gives me and so I want just to edit some of them to make them shorter.  So whta's the deal, how do I do that?

On Grip there's a little button that looks like a pencil. That toggles the editor.

---

### Post by iamah on 2007-09-13
Sound Juicer is very pretty and all but I spent 1 hour trying to select a friggin mp3 profile, no sucess... 

thanks for this tutorial, it works great...

---

### Post by sunus on 2007-09-16
> **vanadium said:**
> Indeed, with FLAC, you always retain the original audio quality. The only reason why you would use a lower setting is the speed of creating the compressed file. For archival purposes, I guess you indeed would want a maximum compression even at the expense of longer compression times.

My understanding is that encoding using --best for Flac files adds considerably to the encoding time for little additional compression and this is why it is not the default setting.

I also vaguely recall reading that one of the few players that support the playing of Flac files expects the default setting to be used.

---

### Post by SnTholiday on 2007-09-27
Thanks for all the great information but I don't understand how you configure Grip for the output folder you want to use. Thanks.

---

### Post by MetalMusicAddict on 2007-09-27
> **SnTholiday said:**
> Thanks for all the great information but I don't understand how you configure Grip for the output folder you want to use. Thanks.

The "Encode file format" field determines that. As well as "Rip file format", partially. The former will be the final destination.

---

### Post by hfw on 2007-09-30
Thanks for the tutorial.  I spent a bunch of time to try and get this figured out.  It finally looks like it's working.

---

### Post by MetalMusicAddict on 2007-10-01
10/1/07 - Resources and examples for WAVPACK have been added.

---

### Post by MetalMusicAddict on 2007-10-07
10/7/07 - Updated "Other Examples" section with links to example pics.

---

### Post by feisty_hot_lover on 2007-11-18
Great howto you got here.  I would like to see a section added to the tutorial about how to set Grip up to take advantage of the existing ~/Music directory in 7.10.  It's not obvious to new users especially that the ~/ refers to a directory structure.  I also would like to see the default switches changed in Grip to better reflect the Ubuntu way of doing things.  For example Sound Juicer directory layout is like this ~/Music/Album Artist/Album Title/number_title.flac but the Grip layout is like this ~/Music/Album Artist/Album Title/Artist/*.flac.  This layout appears when there is multiple artist for a single album and as a result you can wind up with 20 directory's each containing just one .flac or .mp3 or whatever, just makes everything messy.

This brings up my problem, I can't figure out how to make Grip behave like Sound Juicer when creating the directory's.  Would you or anybody who can, tell me what to change in order to mimic Sound Juicer's directory layout

My current Grip settings.
Rip file format (~/Music/%A/%d/%n.wav)
Encoder command line (-V -o %m %w)
Encode file format (~/Music/%A/%d/%n.%x)
M3U file format (~/Music/%A-%d.m3u)

---

### Post by MetalMusicAddict on 2007-12-02
> **feisty_hot_lover said:**
> Great howto you got here.  I would like to see a section added to the tutorial about how to set Grip up to take advantage of the existing ~/Music directory in 7.10. 
This I can do.
> I also would like to see the default switches changed in Grip to better reflect the Ubuntu way of doing things.
This I cant do as its a upstream decision.
> For example Sound Juicer directory layout is like this ~/Music/Album Artist/Album Title/number_title.flac but the Grip layout is like this ~/Music/Album Artist/Album Title/Artist/*.flac.  This layout appears when there is multiple artist for a single album and as a result you can wind up with 20 directory's each containing just one .flac or .mp3 or whatever, just makes everything messy.

This brings up my problem, I can't figure out how to make Grip behave like Sound Juicer when creating the directory's.  Would you or anybody who can, tell me what to change in order to mimic Sound Juicer's directory layout

My current Grip settings.
Rip file format (~/Music/%A/%d/%n.wav)
Encoder command line (-V -o %m %w)
Encode file format (~/Music/%A/%d/%n.%x)
M3U file format (~/Music/%A-%d.m3u)

This I can help with. Though the naming convention is completely screwy to me and unused anywhere but SoundJuicer it seems. Most naming goes like: **~/Music/%A/%d/%a - %d - %t - %n.%x**

Do it like this:
**Rip file format (**~/Music/%A %d/%t_%n.wav**)**
**Encoder command line (**-V -o %m %w**)**
**Encode file format (**~/Music/%A %d/%t_%n.%x**)**
**M3U file format (**~/Music/%A-%d.m3u**)**

---

### Post by MetalMusicAddict on 2007-12-07
December 7th 2007
 * Added MUSEPACK support.

It isnt quite in the repo yet but I had it backported from Hardy and should be in the repos soon.

---

### Post by mcp_dk on 2008-01-19
thanks for the tutorial. Is there anyway to specify output of the encoded file to a samba share? I have a NAS that i want the files to end up on. I have tried
[http://192.168.0.102/music/%A/%d/%n.%x](http://192.168.0.102/music/%A/%d/%n.%x)
and
smb:192.168.0.102/music/%A/%d/%n.%x

but both options just creates either a smb: or a http: folder in my homeshare.

---

### Post by cozmicharlie on 2008-01-23
> **jkroto said:**
> MetalMusicAddict,

2. In your travels here have you run across any good converters of flac or shn.  I have search but found no good answers.  I download taper friendly shows in those formats and do retain the lossless versions, but like to convert some for ipod use.

Thanks again,
John

You might try PACPL [http://viiron.googlepages.com/](http://viiron.googlepages.com/)

---

### Post by vorostatz on 2008-04-30
I have followed the tutorial and installed everything maually via the sudo apt-get.  My file paths to the encoder are correct and yet no matter which encoder I choose I get this message

Invalid Encoder Executable
Check your encoder config, and ensure it specifies the full path to the encoder executable.

I am very new to linux and I am sure I am just making some silly mistake.  Anyone have any ideas

---

### Post by Bakon Jarser on 2008-05-25
Thanks for this.  So glad to be getting rid of SoundJuicer.  Due to a bug in GStreamer sound juicer can't do VBR.

---

### Post by MetalMusicAddict on 2008-05-27
> **mcp_dk said:**
> thanks for the tutorial. Is there anyway to specify output of the encoded file to a samba share? I have a NAS that i want the files to end up on. I have tried
[http://192.168.0.102/music/%A/%d/%n.%x](http://192.168.0.102/music/%A/%d/%n.%x)
and
smb:192.168.0.102/music/%A/%d/%n.%x

but both options just creates either a smb: or a http: folder in my homeshare.

You would just use the same path as the mountpoint in your fstab.

---

### Post by PureW on 2008-08-29
Hello, thanks for this great guide on ripping.

I have a problem with the swedish characters å ä and ö. Created folders and files looks good but Amarok has trouble showing the tags correctly.

In Grip under Config->ID3 I have chosen to only add ID3V2 tags with UTF8-encoding. (I think this was default.)

I also wonder if "-h -V 3" is the highest quality setting?

---

### Post by lil_rich on 2008-12-08
> **vanadium said:**
> It should be easy to set up Grip for encoding several formats at the same time. In Config - Encode - Encoder - Encoder executable, you could probably just stick your own custom little bash proggie instead of /usr/bin/lame. The "encoder command-line" would then reduce to "%w %m", the Encoder file extension" should remain empty.


I found a great, and easy, way of archiving in two formats. I wanted to archive FLAC files of all of my CDs, but want ogg files for my DAP. Between my wife and I, we have about 500 CDs, so we really wanted an efficient, "one click" method. Here's what I have:

I select the "flac" encoder with the parameters suggested in this thread (I don't bother with "-best", I use -6 for flac compression). Then, in the "options" tab of the encoder settings, there is an input called "Encoder filter command". This is for any replay gain or noise filtering that you might want to apply to the encoded file (the flac file in my case). However, you can apply anything you like to the file, so I just enter:
```
oggenc -q 6 %m -o ~/Music/ogg/%A/%d/%t-%A-%n.ogg
```
Grip sends the relevant switches to name the ogg file (I put mine in a separate directory to my flac files). oggenc preserves the Vorbis tags, so all of the tags are correct.

Now, to archive a CD, all I do is put it in the drive, and hit "rip & encode"!

---

