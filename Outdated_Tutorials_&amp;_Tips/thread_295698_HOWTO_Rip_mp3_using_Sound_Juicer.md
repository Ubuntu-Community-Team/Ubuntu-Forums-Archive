---
title: "HOWTO: Rip mp3 using Sound Juicer"
date: 2006-11-08
forum: Outdated Tutorials &amp; Tips
---

### Post by Ack99 on 2006-11-08
If you have and iPod and is using Amarok to upload songs to it, you probably noticed that you can upload .ogg files... ](*,) 

So, if you want to rip cds as mp3's here is what to do:

[LIST=1]
[*]install Gstreamer plugin:
```
sudo apt-get install gstreamer-plugin-bad
```
in Dapper or
```
sudo apt-get install gstreamer-plugin-ugly
```
in Edgy
[*]Open Sound Juicer CD Extractor
[*]go **Edit > preferences** and in the format are choose **edit profile**
[*]click **New** and name it MP3
[*]Select the MP3 profile and set the **GStreamer pipeline** to:
```
 audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux
```
in dapper or
```
 audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux
```
in Edgy
[*]Set the File Extension to **mp3**, and select the Active check box
[*] Restart Sound Juicer
[/LIST]

and you can now rip mp3's :-D

---

### Post by tscook on 2006-11-08
When I do this the extracted files become 1-6 hours of pops, hisses and glitches.  Sort of cool considering I am ripping noise CDs, but not the kind of noise I am aiming for.

---

### Post by wilberfan on 2006-11-11
> **Ack99 said:**
> If you have and iPod and is using Amarok to upload songs to it, you probably noticed that you can upload .ogg files... ](*,) 

So, if you want to rip cds as mp3's here is what to do:

[LIST=1]
[*]install Gstreamer plugin:

```
sudo apt-get install gstreamer-plugin-ugly
```
in Edgy 

I came to a screeching halt at the very first step!

>  sudo apt-get install gstreamer-plugin-ugly
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Couldn't find package gstreamer-plugin-ugly

---

### Post by jcrochford on 2006-11-12
It sounds like you haven't fully enabled the Universe and Multiverse repositories.  Check this out:

[https://help.ubuntu.com/community/Repositories/Ubuntu#what](https://help.ubuntu.com/community/Repositories/Ubuntu#what)

Once you've got them enabled, try the instructions above again.  You shouldn't have any problem getting the gstreamer-plugin-ugly via the command line or from Synaptic Package Manager.  Good luck!

---

### Post by wilberfan on 2006-11-12
> **jcrochford said:**
> It sounds like you haven't fully enabled the Universe and Multiverse repositories.  Check this out:

[https://help.ubuntu.com/community/Repositories/Ubuntu#what](https://help.ubuntu.com/community/Repositories/Ubuntu#what)

Once you've got them enabled, try the instructions above again.  You shouldn't have any problem getting the gstreamer-plugin-ugly via the command line or from Synaptic Package Manager.  Good luck!

I DO have those repositories enabled!   In Synaptic I found a 'gstreamer0.10-plugins-ugly'--you think that's what he meant?

---

### Post by bennyj on 2006-11-12
> **wilberfan said:**
> I DO have those repositories enabled!   In Synaptic I found a 'gstreamer0.10-plugins-ugly'--you think that's what he meant?

Yes

---

### Post by Circus-Killer on 2006-11-17
okay, i followed the first post, however one thing didnt work out. the pipeline suggested for edgy gave me garbled output (even though i am using edgy).

i used the pipeline suggested for dapper and that seemed to work fine.
(and yes, i am using gstreamer0.10)

---

### Post by mhosken on 2006-11-18
I found installing gstreamer0.10-plugins-ugly-multiverse and using lame in the pipeline worked for me

---

### Post by m.musashi on 2006-11-23
I also got nothing but noise using the code given. Using lame in the pipeline working fine. In my case the gstreamer plugins were already installed. I just added lame in preferences and it worked fine.

---

### Post by endersshadow on 2006-11-24
The OP's Gstreamer line didn't work for me, but this one did:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc
```

---

### Post by peterbakker on 2006-11-25
thanks @endershadow
finally a working pipeline. now i can flush the wine audiograbber.
However, this one encodes @128, would somebody be kind enough to tell how to enable 192kb or VBR ?
i tried every pipeline i could find, but none worked till so far:rolleyes:

---

### Post by szf on 2006-11-25
> **peterbakker said:**
> However, this one encodes @128, would somebody be kind enough to tell how to enable 192kb or VBR ?
i tried every pipeline i could find, but none worked till so far:rolleyes:

I haven't found a way to actually enable vbr... more gstreamer goodness. I caught from other posts to use:

[FONT="Courier New"]$ gst-inspect-0.10 lame[/FONT]

To capture the valid arguments. vbr=0 is supposed to be off, but the other modes don't yield a vbr-encoded file either (!).

I finally settled on this mp3 profile in Sound Juicer:

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192

Which does give a 192 kb/s cbr... but my older (grip encoded) files were vbr.

---

### Post by eternalfire129 on 2006-12-09
thanx mhosken, replacing that segment of code with simply lame finally made it work ;)

---

### Post by beefcurry on 2006-12-09
It does shock me.... why is this thread in the wrong forum?

---

### Post by eternalfire129 on 2006-12-10
ignore this post (i dont kno how to delete my own post lol)

---

### Post by eternalfire129 on 2006-12-11
again dont kno how to delete my posts due to errors in them sorry... could somebody tell me how to take them off?

---

### Post by radiobuzzer on 2006-12-12
Sorry, the UGLY pipeline suggested for Edgy in the first post didn't work for me either. I have AMD 64 x2, I don't know if it makes any difference but there are a lot of programs not working here. 

What I got as a result of the streaming was one large 700MB .mp3, which wasn't actually neither .mp3 or .wav . Does anybody have any idea what this file format might have been, cause I gave back the CDs and I can't read the extracted content?

Gladfully the lately suggested pipeline for LAME did the job.

---

### Post by bsalt on 2006-12-12
> **Ack99 said:**
> 
```
 audio/x-raw-int,rate=44100,channels=2 ! ugly name=enc vbr=0 bitrate=196 ! id3v2mux
```
in Edgy

and you can now rip mp3's :-D

I digg this. Thanks ack99!

---

### Post by eternalfire129 on 2006-12-13
i have a simple solution for mp3 ripping, use goobox, it doesnt give u the bullshit sound juicer gives lol plus it just looks better lol ;)

---

### Post by deeptingler on 2006-12-16
This worked for me on edgy as I was get 40mb mp3 files which were just garbage before this

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192

Thanx to SZF above for this

---

### Post by bsalt on 2006-12-16
yeah i forgot to add that that didn't work for me either. oops. i should've waited until i tried the code. ;)

---

### Post by guillaumeh on 2006-12-23
Is there a way to enable mp3 extraction system-wide , i.e. not only for the current user but everyone ?

---

### Post by maruchan on 2007-01-02
Just wanted to reply to the thread and say that in Edgy, the following line worked *perfectly* for me:

```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192
```

---

### Post by AndrewB on 2007-01-02
Thanks for the set-up refresher. :cool: 
worked for me in Edgy
```
audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=256
```

---

### Post by gorilla_king on 2007-01-02
this worked in edgy and the other didnt for me. might suggest chaning the tutorial as everyone else said the same thing

> audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=256

---

### Post by SZF2001 on 2007-01-04
I know it's retarded that I'm still on Breezy, but that's another topic.

When I try any of the pipeline commands with "lame", or "ugly", or "bad", none of them are recodnized. I tried "mad" because, you know, that's what Breezy's gstreamer is for MP3's. And yes, I also have Lame installed.

If only my computer could handle Dapper...

---

### Post by sgornick on 2007-01-04
When I use bitrate=196 as indicated in the first post in this thread I get:
 "Sound Juicer could not extract this CD. - Reason: Internal GStreamer error: negotiation problem"

Per MP3 entry on Wikipedia, [http://en.wikipedia.org/wiki/MP3](http://en.wikipedia.org/wiki/MP3) 
Bit rates available in MPEG-1 Layer 3 are 32, 40, 48, 56, 64, 80, 96, 112, 128,
160, 192, 224, 256 and 320 kbit/s

When I change bitrate= to bitrate=192 it works fine for me, as do the others.   

Was the 196 a typo?  If so, is there some way to petition to have an admin edit the first post in this thread so that the bad information isn't perpetuated indefinitely?  This thread is the first that appears in UbuntuForums.org when doing a search on: mp3 sound juicer

---

### Post by .tommie on 2007-01-04
> **sgornick said:**
> When I use bitrate=196 as indicated in the first post in this thread I get:
 "Sound Juicer could not extract this CD. - Reason: Internal GStreamer error: negotiation problem"

Per MP3 entry on Wikipedia, [http://en.wikipedia.org/wiki/MP3](http://en.wikipedia.org/wiki/MP3) 
Bit rates available in MPEG-1 Layer 3 are 32, 40, 48, 56, 64, 80, 96, 112, 128,
160, 192, 224, 256 and 320 kbit/s

When I change bitrate= to bitrate=192 it works fine for me, as do the others.   

Was the 196 a typo?  If so, is there some way to petition to have an admin edit the first post in this thread so that the bad information isn't perpetuated indefinitely?  This thread is the first that appears in UbuntuForums.org when doing a search on: mp3 sound juicer

Indeed... You are a genius! ;-)

---

### Post by klausthorn on 2007-01-05
> **guillaumeh said:**
> Is there a way to enable mp3 extraction system-wide , i.e. not only for the current user but everyone ?

yes, set your favourite settings as a user in sound-juicer, then dump them into files with:
gconftool-2 --dump /system/gstreamer/0.10/audio > file1
gconftool-2 --dump /apps/sound-juicer > file2

as root then load the files into the systemwide default configuration:
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load  file1
gconftool-2 --direct --config-source xml:readwrite:/etc/gconf/gconf.xml.defaults --load  file2

you might want to backup /etc/gconf/gconf.xml.defaults and edit file2 to remove some personal sound-juicer settings.

changes might be visible only after logout&login

---

### Post by rmjb on 2007-01-06
Just to add my 2 cents. The lame pipeline from the first post worked once I change the rate to 192. What's wrong is that in the Sound Juicer help files they have the lame pipeline with 196 also.

- rmjb

---

### Post by steveyos666 on 2007-01-08
Any way to have the music have details? When I rip CD's it only has the track name as the name of the file, but the stuff under properties is all blank. I try to change it with easytag or whatever it's called, but it doesn't show up on my iPod as being changed. And yeah I put songs on there after I changed them, still blank on there :(

---

### Post by wwood on 2007-01-10
Hi.

I got mine working with ID3 tags straight out of Sound Juicer using the pipeline by adding the '! id3v2mux' bit (the other bit on its own was fine, cept tags were blank):

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192 ! id3v2mux

There is also another useful discussion at

[https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58](https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58)

---

### Post by steveyos666 on 2007-01-10
> **wwood said:**
> Hi.

I got mine working with ID3 tags straight out of Sound Juicer using the pipeline by adding the '! id3v2mux' bit (the other bit on its own was fine, cept tags were blank):

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192 ! id3v2mux

There is also another useful discussion at

[https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58](https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58)

Cool, thank you :D

---

### Post by SebMKd on 2007-01-12
Finally found a solution that works!! Making Sound Juicer a very nice MP3 encoder with ID3 tags. 8) 
I'm using **Dapper **and I had a few Gstreamer plugins already installed. However, in the end I found that **Gstreamer0.10-plugin-ugly-multiverse** was the one that made the pipeline works!
(Though I have now installed Gstreamer0.10-plugin bad, bad-multiverse, ugly and ugly-multiverse; which I had on an ADD-ON CD, since my Dapper doesn't have internet)

The pipeline I entered is: _audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux_ 

I haven't tried other bitrates, but if I do I will create a new profile. Thus making Sound Juicer very efficient and easy to use to rip CDs.

Thanks to all that contributed and helped me indirectly.

---

### Post by Master Dwarf on 2007-01-14
> Finally found a solution that works!! Making Sound Juicer a very nice MP3 encoder with ID3 tags.
I'm using Dapper and I had a few Gstreamer plugins already installed. However, in the end I found that Gstreamer0.10-plugin-ugly-multiverse was the one that made the pipeline works!
(Though I have now installed Gstreamer0.10-plugin bad, bad-multiverse, ugly and ugly-multiverse; which I had on an ADD-ON CD, since my Dapper doesn't have internet)

The pipeline I entered is: audio/x-raw-int,rate=44100,channels=2 ! lame name=enc bitrate=192 ! id3v2mux

I haven't tried other bitrates, but if I do I will create a new profile. Thus making Sound Juicer very efficient and easy to use to rip CDs.

Thanks to all that contributed and helped me indirectly.Yeah!  This last one did the trick for me. Thanks SebMKd.

---

### Post by vgrisham on 2007-02-03
> **wwood said:**
> Hi.

I got mine working with ID3 tags straight out of Sound Juicer using the pipeline by adding the '! id3v2mux' bit (the other bit on its own was fine, cept tags were blank):

audio/x-raw-int,rate=44100,channels=2!lame name=enc bitrate=192 ! id3v2mux

There is also another useful discussion at

[https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58](https://help.ubuntu.com/community/CDRipping#head-f109ee313aa77bf2997e6499584438e9f7691d58)

That did the trick! Thanks!:guitar:

---

### Post by bsalt on 2007-02-03
This is from the Sound Juicer help file (under Preferences):

audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux

The only reason this doesn't work is bitrate=196. That is not a working bitrate. So just change the bitrate to 192, 256, 320, 128, or whatever else you want, and it'd be good. It saves a lot of time, I've found.

---

### Post by Ev1lV1king on 2007-02-08
I have been trying to get this to work too, but every time I rip mp3s, the sound is just a bunch of garbage noise, and the filesizes are very large (55 megs/song roughly). I've tried using the pipelines stated in this thread, but none of them have worked out so far.

---

### Post by rmjb on 2007-02-08
> **Ev1lV1king said:**
> I have been trying to get this to work too, but every time I rip mp3s, the sound is just a bunch of garbage noise, and the filesizes are very large (55 megs/song roughly). I've tried using the pipelines stated in this thread, but none of them have worked out so far.

Do you have the gstreamer ugly installed?

- rmjb

---

### Post by Ev1lV1king on 2007-02-08
ok I've figured out what my problem is, apperently the gstreamer-ugly universe plugin only has playback codecs while the multiverse plugin handles encoding... I had it set up before where gstreamer-ugly (universe) would handle playback, and liblame0 would handle encoding, but apperently this does not work? Anyway, after I installed the multiverse one, I had no problems.

---

### Post by alextj on 2007-02-12
But how about VBR? I really don't like having my music in CBR, when there is such a great thing as VBR. I want to use [COLOR="RoyalBlue"]-V 2 --vbr-new[/COLOR] command line option for lame encoding. How do I do that in Juicer?

---

### Post by jocheem67 on 2007-02-15
That is a known problem with gstreamer versus sound-juicer..did you try changing vbr=0 to vbr=1...

In feisty there's a new profile mp3 where vbr is already set, but ofcourse that's with a newer sound-juicer version.

I've been trying to compile sound-juicer but am in dependancy hell at the moment. Lots of missing-ones...bugger...

In the meantime, if you insist on vbr: use grip or even better abcde. There is a "abcde" howto on this forum. It&#347; command-line and adresses lame directly. With a nice .abcde.conf file you've got a great ripper.

Soundjuicer and vbr are a bad combi at the moment.

---

### Post by alextj on 2007-02-16
**jocheem67**, thanks for your reply.
I have actually started using EAC (Exact Audio Copy), which is best CD ripping software that I have been using to date. Unfortunately the only way to run it is with WINE because it is Win only.
But it runs just great, I have already ripped large part of my collection and haven't had any problem with it. Thanks to WINE project that is keeping me away from Windows, for many reasons!

---

### Post by jocheem67 on 2007-02-18
EAC is idd the best, and there is no equivalent for a linux based comp., though there are some projects going.

again : in feisty the pipeline will contain vbr by default.

I stick to abcde, love that command-line thing, with the moving arrow...:)

---

### Post by DMS86 on 2007-02-20
it worked just fine for me with dapper with the first pipeline (i changed it to bitrate 320) and i had no problems.

thank you!

---

### Post by moshuptrail on 2007-02-25
I followed these [instructions]("http://www.dontforward.com/linux/2006/10/to-get-soundjuicer-to-rip-cds-directly.html") and did not install anything additional.
Seems to work fine.  I changed the bitrate to 128 since my ears are no longer capable of discerning the difference and it takes a little less space in my mp3 player.

---

### Post by haelen on 2007-03-30
Hi,

I'm trying to rip to MP3 under Kubuntu Edgy. Should I still be using the gstreamer plugings of the 'multiverse ugly' variety?

Currently I'm getting hefty file sizes produced at 0 bitrate (no audio whatsoever).


TIA,
Tim

**Addendum** Due to prolonged frustration I've tried *Grip *which seems to work for me 'out of the box'.

---

### Post by ewout klimbie on 2007-04-18
Thanks for the howto, i now have a working MP3 VBR ripper. I ended up using the following GStreamer Pipeline:
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=1 vbr=4 preset=1001 ! id3v2mux
```
The mode tag is set to joint stereo, vbr is set to new mode and preset is set to standard (about 192kbps).
As pointed out by someone before me, if you want different settings open up a terminal and type:
```
gst-inspect-0.10 lame
```
to see all the possible parameters.

---

### Post by CosmicBabs on 2007-08-02
If you are still having problems check this webpage
[https://help.ubuntu.com/community/CDRipping](https://help.ubuntu.com/community/CDRipping)

It worked for me

---

### Post by xyverz on 2007-09-20
I had a rant here, but then saw the previous post.  nevermind.  I'll try using that url first.

---

### Post by happy-and-lost on 2007-09-23
Gutsy here, which may be the root of the problem. When I use

*audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=320 ! id3v2mux*

I get great 320kps mp3s, but when I use 

*audio/x-raw-int,rate=44100,channels=2 ! lame name=enc vbr=0 bitrate=196 ! id3v2mux*

I get 224kps (I think they might be vbr) mp3s. Why?!

---

### Post by ok67 on 2007-10-09
196 is a typo, it should be 192

---

### Post by Fruhwirth on 2007-10-27
Contrary to what the HOWTO advised, i used
> 
audio/x-raw-int,rate=44100,channels=2!lame name=enc vbr=0 bitrate=192 ! id3v2mux

And my files are now coming out beautiful.  The guide says Dapper users should  "channels=2 ! ugly" with spaces and all, but that did not work for me. 

Thanks all.  working great.

---

### Post by Auslegung on 2007-12-07
I am using 7.10 and CANNOT figure this out.  I have followed every direction I have found and nothing works.  I have downloaded gstreamer, I have done [this]("https://help.ubuntu.com/community/CDRipping") but there is no 'OK' button on my Sound Juicer, only a 'Close' button.  I have changed the gstreamer pipeline in my "mp3 encoding" profile a dozen times to everything I've seen people tell me to and nothing works.  Will someone please help me?

---

### Post by klein de usa on 2007-12-07
hi
ubuntu 7.10 fresh install 
sound juicer with mp3 Gstreamer pipeline (audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux)

worked fine up till a reboot a hour ago now all it tells me when i try to extract a file !!!!!!Sound Juicer could not extract this CD.
Reason: Access denied

---

### Post by motoperpetuo on 2008-03-02
Here's the lazy man's not-too-specific, no-command-line-needed version of how to get Sound Juicer to rip CDs to mp3 format:

1)Install the lame and lame-extras packages through Synaptic.
2)Install a whole slew of gstreamer plug-ins, also through Synaptic. Grab all of the standard ones and any of the "good" “bad” and “ugly” ones that seem to have anything to do with sound.
3)Restart Sound Juicer and the mp3 option should be there under Edit|Preferences, Output Format.

If this doesn't work initially, I suggest going back to Synaptic and grabbing more gstreamer packages. I had to do that a few times.

I've struggled with getting this to work off and on since starting to use Ubuntu and Mint about a year ago and just got it working today. Granted, I did this in Mint, but I think it would work in Ubuntu (since I find that Mint is basically the lazy man's Ubuntu). I apologize if these directions are kind of sloppy, I'm just excited to have tackled one of the few remaining major functionality setbacks I had left in Linux. Hope this works for some of you out there.

---

### Post by dave373 on 2008-03-13
I have just been battling with "Sound Juicer" trying to enable the MP3 option. I tried creating profiles and disabling other profiles, all in vain.
Even though I had a profile that was "active", I could not see it in the 'output format' box.

Eventually, I started installing every package through the 'Add/Remove' that contained gstreamer, one-by-one, until it worked.

End result: After I installed  "**Ubuntu restricted extras**", I could finally see the MP3 selection in the output format box.

Hope this helps someone...:)

---

### Post by Virgilius on 2008-03-16
I can rip from Sound Juicer, but everytime it transfers from my MP3 player (a Creative NEEON 2) from my computer, the track name shows as Chinese characters mixed with roman alphabet. Any solution to this annoying problem?

---

### Post by nilbus on 2008-05-22
In the latest ubuntu, install the package **gstreamer0.10-plugins-ugly-multiverse**, and mp3 should just appear in the list of output formats.  

ubuntu-restricted-extras just happens to work because this package is included in it, but it also has a bunch of extra stuff you might not want.

---

### Post by Bakon Jarser on 2008-05-25
> **nilbus said:**
> In the latest ubuntu, install the package **gstreamer0.10-plugins-ugly-multiverse**, and mp3 should just appear in the list of output formats.  

ubuntu-restricted-extras just happens to work because this package is included in it, but it also has a bunch of extra stuff you might not want.

It rips it in terrible quality.  128kbps is unacceptable.  Anyone know how to encode at 256kbps?

**Edit:** Nevermind.  I've ditched sound juicer forever and am using grip.  Hard to set up but works great now that it is set up.

---

### Post by dri on 2008-05-27
> **dave373 said:**
> Hope this helps someone...:)

Hats off!

---

### Post by big_dog1968 on 2008-05-31
**Is there a way (a simple) way to adjust the bit rate quality for mp3's ripped with sound juicer.** 
I installed grip, but I don't see an adjustment labeled bit rate, 128, 256, 320...etc. I hate that I am having to use win XP on a dual boot for such a basic use as ripping CD's that way I want. somewhere I eard K3B was good, but you can only adjust the bit rate for Ogg and not MP3. Other than that K3B is an acceptable tool for ripping. 

Any ideas? 

When replying, please assume that I am inexperienced with Ubuntu. I have all the plug ins necessary to rip MP3's. It is just about the bit rate and ease of adjustment. In other words, I don' know how to/want to get into the command line each time I want to rip CD's (call me crazy). 

Any help appreciated.:)

---

### Post by Bakon Jarser on 2008-05-31
> **big_dog1968 said:**
> **Is there a way (a simple) way to adjust the bit rate quality for mp3's ripped with sound juicer.** 
I installed grip, but I don't see an adjustment labeled bit rate, 128, 256, 320...etc. I hate that I am having to use win XP on a dual boot for such a basic use as ripping CD's that way I want. somewhere I eard K3B was good, but you can only adjust the bit rate for Ogg and not MP3. Other than that K3B is an acceptable tool for ripping. 

Any ideas? 

When replying, please assume that I am inexperienced with Ubuntu. I have all the plug ins necessary to rip MP3's. It is just about the bit rate and ease of adjustment. In other words, I don' know how to/want to get into the command line each time I want to rip CD's (call me crazy). 

Any help appreciated.:)

Grip isn't easy to set up but once you get it the way you want, it works great.  Here's the guide I followed.  You'll have to read through some of the comments to get all the info, such as folder hierarchy.

[http://ubuntuforums.org/showthread.php?t=183125](http://ubuntuforums.org/showthread.php?t=183125)

---

### Post by jsgarvin on 2008-06-11
> **dave373 said:**
> I have just been battling with "Sound Juicer" trying to enable the MP3 option. I tried creating profiles and disabling other profiles, all in vain.
Even though I had a profile that was "active", I could not see it in the 'output format' box.

Eventually, I started installing every package through the 'Add/Remove' that contained gstreamer, one-by-one, until it worked.

End result: After I installed  "**Ubuntu restricted extras**", I could finally see the MP3 selection in the output format box.

Hope this helps someone...:)

Yup, thanks.  That fixed it for me perfectly. :guitar:

---

### Post by growingneeds on 2008-09-01
From the Synaptic Package Manager, install the following package, along with its dependencies: gstreamer0.10-plugins-ugly-multiverse

---

### Post by pandan on 2008-09-02
> **dave373 said:**
> I have just been battling with "Sound Juicer" trying to enable the MP3 option. I tried creating profiles and disabling other profiles, all in vain.
Even though I had a profile that was "active", I could not see it in the 'output format' box.

Eventually, I started installing every package through the 'Add/Remove' that contained gstreamer, one-by-one, until it worked.

End result: After I installed  "**Ubuntu restricted extras**", I could finally see the MP3 selection in the output format box.

Hope this helps someone...:)

I had this problem in xubuntu gutsy 7.10.  
I installed all the gstreamer plugins and while mp3 pipeline was there, it was not present for selection in the Sound Juicer Preferences dialog.

Only when I installed the "gnome-media" package did it then work.

I have just sucessfully extracted a Marvin Gaye album to mp3.:guitar:
Before I was using scripts and lame from the command line!

---

### Post by Jakey_TheSnake on 2008-10-19
Seeing as there's a lot of topics flying around the forum, I'll make a howto based on my own research. This will tell you how to enable mp3 encoding (i.e. enabling you to rip CDs as .mp3 files), and then overcome the cursed CBR 128kbps that is imposed on you. 

If you open Sound Juicer (called Audio CD Extractor in *Accessories>Sound & Video{/i]) and select [i]Edit>Preferences* the output format box will have a few options, by default none of them MP3. If you hit edit profiles, however, you will see an mp3 option, yet if you select it, you find it cannot be used to encode your mp3s yet (by default). 

To enable mp3 encoding, you need to open a terminal and enter:

```
sudo apt-get install ubuntu-restricted-extras
```

Now you can select the mp3 option. 

However, all mp3's ripped will be CBR 128kbps. 

To change this, we need to go to *Edit>Preferences* again, select edit profiles again and edit the MP3 one. In the "_G_Streamer pipeline" box, replace what is in there with this:

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr=4 vbr-quality=0 vbr-min-bitrate=160 vbr-max-bitrate=256 ! xingmux ! id3v2mux
```

You can change your max and min bit rates as you wish by changing the number on the end of the *"vbr-min-bitrate=160"* and *"vbr-max-bitrate=256"* commands (leave syntax as is), it is currently tailored to my liking. 

[N.B, please note some people at this point have had the "CD Quality MP3" option drop off their list again. To resolve this, please enter the first code in the terminal again]

Hope this helps people struggling with ripping mp3's, 

- Jake

---

### Post by RealG187 on 2008-10-31
I have ubuntu-restricted-extras and gstreamer0.10-plugins-ugly-multiverse packages installed but no MPr option shows up!

---

### Post by williambertram on 2008-11-11
Here's what worked for me:

[http://blog.mypapit.net/2007/05/how-to-rip-mp3-cd-using-sound-juicer-ubuntu-tips.html](http://blog.mypapit.net/2007/05/how-to-rip-mp3-cd-using-sound-juicer-ubuntu-tips.html)

All I did was sudo apt-get install gstreamer0.10-plugins-ugly-multiverse

I was able to select MP3 in Sound Juicer, and the quality is good.

Looks like the package name may have been changed based on earlier posts in this thread.

---

### Post by RealG187 on 2008-11-13
I have that package and still no luck

---

### Post by ebash on 2008-11-16
The plugin id3v2mux only writes ID tags in version 2.4. If your hardware MP3 player doesn't see properly the track, artist and album names it could be because it doesn't support 2.4 tags. The most portable format for ID tags is 2.3, at the moment gstreamer doesn't support this format.

There's a new plugin in gstreamer's bugzilla that adds support for IDv2.3. If you want to try it the instructions are available in the bug comment:

[http://bugzilla.gnome.org/show_bug.cgi?id=459226]("http://bugzilla.gnome.org/show_bug.cgi?id=459226")

Simply download the .tar.gz attached to the bug and follow the instructions in README.txt.

---

### Post by MasterOfTheHat on 2009-01-29
When I went to Add/Remove and tried to install ubuntu-restricted-extras, it threw an error that I couldn't install the package because another installed package was blocking it. I had to go into Synaptic and select ubuntu-restricted-extras to figure out what package was blocking it. For some reason, I had libavcodec51 installed, (default for Ubuntu??), and I needed libavcodec-unstripped-51. Synaptic verified that I wanted to remove libavcodec51 and install the new one, then it ran through the whole process without a hitch. When it was finished, I loaded up Sound Juicer and the option for "CD Quality, MP3 (.mp3 type)" was in my Output Format drop-down. :D

---

### Post by RealG187 on 2009-07-16
How can I rip to MP3 at 64 Kppb?

```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 bitrate=64 ! id3v2mux
```
Shows up in sound-juicer's preferences but not Rhythmbox's

---

