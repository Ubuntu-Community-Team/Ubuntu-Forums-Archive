---
title: "First of its kind ! will you head forward ?"
date: 2009-05-15
forum: Programming Talk
---

### Post by mysoogal on 2009-05-15
Hi I would like to share this tiny script i use and hope you can join this interesting project, I'm still not sure if i should post this here, I would like to invite other php developers, python developers, I welcome anybody that's willing to improve this script, as far from my understanding, there is a current issue with flash streaming in Linux operating system, I would like to remove that problem by taking the lead and heading towards the feature which I honestly believe flash Media player should be completely dropped and replaced. now the way I believe I can Achieve this best is by implementing a video plug-in standard. I have found that vlc is widely compatible with every single operating system. on mac,windows,Linux etc. the important part of this Media player is the Mozilla vlc plug-in which is available for windows and macs. this plug-in provides a clean and wide range of operating system compatibilities something flash media player is not fully able to complete, the vlc plug-in also enables the video script developers more flexibility with Audio/Codec support, as a example, you can stream Ogg audio with video through Vlc web plug-in. can you imagine trying this with a flash media player. you might ask why would you want to do this ? I want to free  video sharing script developers and its users from Flash technology, as some of you developers notice that Flash is a closed source its impossible to play with the code. the way to remove this obstacle is by getting more people interested in alternative technologies, such as vlc cross-platform open-source multimedia framework, something flash can dream about. The core of this problem which fuels it are the developers which seemly support and utilizes it's priority code. I don't intend to blame every developer, everybody has to make money to survive. i truly understand this, but this has to balance the markets. you-tube currently is using flash and its everywhere just as flash technology. this gives Adobe Systems Incorporated a massive market for its products which flash is one of its products now. this is what the problem is. there simply isn't enough open source projects that play important rules in the video sharing world. apart from ffmpeg mencoder which are processing videos. but not in a xvid or ogg but in a flv1 which will be 110% be used with flash media player.

so i hope some of you understand what I'm trying to do here, i simply need some good php developers,to fix this script add few features open source it, deploy on source.forge and start the process. stage6 was a very good example and a good lesson, we could say this script is heading towards what stage6 was, but with a vlc plug-in instead so it supports many video/audio Codec which can be accessed through any operating system. stage6 didn't die because it lacked users it had millions monthly users 8 million page views monthly. it simply died because it got to big to handle.

I believe the same could be Achieved through vlc plug-in. 

Here, is the Project files.
hosted on turboupload : [Download]("http://www.turboupload.com/y52gamiru4us/TinyVideoScript.zip.html")
 


here are the screen dumps

# this is the index.php

[IMG]http://i41.tinypic.com/33vi1x2.png[/IMG]

# this is the upload.htm, which pulls upload.php --- > which pulls fvec.php
[IMG]http://i40.tinypic.com/1zeueb.png[/IMG]

# this is the play.php / uses vlc tested and working on Windows/Linx/Mac
works in all browsers IE6/7/8 FF2/3 etc
[IMG]http://i43.tinypic.com/2wcnrzr.png[/IMG]

# this is the opensource SQLbuddy which i use to remove records 
[IMG]http://i44.tinypic.com/jkexsh.png[/IMG]


**[SIZE="3"]i would like to Ask some of you developers if its possible to bypass this fvec encode by sothinkmedia.com[/SIZE]** the main file which handles encoding it seems is fvec.php i would like mencoder to handle the encoding, with my limited coding experience im not able to complete this. there is 3 minute limit of encoding time on using [http://sothinkmedia.com/flash-video-encoder-linux/index.htm](http://sothinkmedia.com/flash-video-encoder-linux/index.htm)

if your interested, have a go, you just need to install the fvec demo version, for Linux in /usr/bin/fvec

make mysql database called fvec import the sql command to make tables. look inside the zip for sql file for database.


thanks for your time,
mysoogals :KS

---

### Post by Sinkingships7 on 2009-05-15
Adobe Flash isn't going anywhere. I may have misunderstood your (very long) post, but you seem to by implying that Flash should be replaced by something open source and universal, so to speak. If this is the case, it won't happen. Sorry.

If I'm wrong, then I apologize and wish for you to put this is shorter, simpler terms.

---

### Post by mysoogal on 2009-05-15
next integration ! progress bar !

> [http://www.bram.us/projects/js_bramus/jsprogressbarhandler/#download](http://www.bram.us/projects/js_bramus/jsprogressbarhandler/#download)

i will be trying to integrate the upload bar into this script.

---

### Post by mysoogal on 2009-05-15
> **Sinkingships7 said:**
> Adobe Flash isn't going anywhere. I may have misunderstood your (very long) post, but you seem to by implying that Flash should be replaced by something open source and universal, so to speak. If this is the case, it won't happen. Sorry.

If I'm wrong, then I apologize and wish for you to put this is shorter, simpler terms.

yes, ```
implying that Flash should be replaced by something open source and universal
``` 

never said will be easy ! all Empires go down sometimes !;)

---

### Post by Sinkingships7 on 2009-05-15
Then a question: what would this new technology bring over the old Adobe Flash technology, besides being open source? I ask this because, unless there's something terribly revolutionary about this project, there will be no incentive for companies like YouTube to go and convert their millions of videos to use it.

EDIT: or is this project supposed to be of the same nature as projects like Gnash, where it is a client alternative which still runs Flash, but in a reversed-engineered fashion?

---

### Post by simeon87 on 2009-05-15
Even if Flash is to be replaced, I don't think the replacement will be build by a gathering of arbitrary people who happen to have read a forum post... it would have to come from people with solid experience in this area who know how Flash could be improved upon.

---

### Post by mysoogal on 2009-05-15
> **Sinkingships7 said:**
> Then a question: what would this new technology bring over the old Adobe Flash technology, besides being open source? I ask this because, unless there's something terribly revolutionary about this project, there will be no incentive for companies like YouTube to go and convert their millions of videos to use it.

EDIT: or is this project supposed to be of the same nature as projects like Gnash, where it is a client alternative which still runs Flash, but in a reversed-engineered fashion?

well it could be little of Gnash, With Flash Media player a developer is locked with flv ,now with h264,AAC? mp3 vp6, if it was based on vlc plug-in, I could've used alternative audio such as vorbis with xvid and stream that through vlc plug-in. this gives me many options how i want my video to be used encoded or watched and what type of quality to provide.

the technologies Vlc plug-in brings deal mainly towards video / audio support, which suppress what adobe media player can provide to the end user. sorry if you guys misunderstand, i don't mean flash should be replaced, but only the video side of it.


just to note that totem Mozilla plug-in ! should also play flv on Mozilla. it plays divx embed video without divx web player, why not flash flv to :O

---

### Post by mysoogal on 2009-05-16
it seems, this is even better then Gnash and replacing Flash player on youtube, im sure with little change to the script all swf could be replaced with totem plugin

the proof is here !

[http://ubuntuforums.org/showthread.php?t=1120401&highlight=flash+player+slow](http://ubuntuforums.org/showthread.php?t=1120401&highlight=flash+player+slow) :)

---

### Post by skullmunky on 2009-05-20
oh, i get it, you want to make something like youtube, but using a different video format instead of flv, such as ogg/theora.  I think that's a worthwhile goal.  for using mencoder, a little searching here and on the php forums will probably turn up some examples.  good luck!

---

### Post by mysoogal on 2009-05-20
> **skullmunky said:**
> oh, i get it, you want to make something like youtube, but using a different video format instead of flv, such as ogg/theora.  I think that's a worthwhile goal.  for using mencoder, a little searching here and on the php forums will probably turn up some examples.  good luck!



that is exactly what i want to do, can you imagine on the upload page asking you

hey what kind of audio video format would you like your video to be encoded to  ?

option 1 : h264 ? AAC ?
option 2 : xvid ? vorbis ?
Option 3 : Divx ? ogg ?

etc 

you get the idea and have vlc play all these formats.

that really is the goal i have. nobody else is thinking the same. ;)

this sort of thing, would be kinda same as stage6 but with vlc and be able to encode to many different audio video formats and present that through vlc plug-in.


now that is cool isn't it not. can you imagine you-tube being like this. it would be very cool to use.

---

### Post by bfhicks on 2009-05-20
> **mysoogal said:**
> 

hey what kind of audio video format would you like your video to be encoded to  ?

option 1 : h264 ? AAC ?
option 2 : xvid ? vorbis ?
Option 3 : Divx ? ogg ?

...

now that is cool isn't it not. can you imagine you-tube being like this. it would be very cool to use.


I think the biggest thing here is the end-user. Most people do NOT CARE about what format it is. They want to upload a video, and watch it. I think people who care about what format already know how to do such things already. I know linuxjournal.com already streams ogg videos online. 

Doing it as a pet-project would be unique and fun, but I fear it would never be main stream because most people just aren't interested.

---

### Post by slavik on 2009-05-20
most ...

I am still waiting for avisynth 3 and still dreaming of yatta and dgmpgdec

and how about having mencoder work on just audio or just video?

---

### Post by soltanis on 2009-05-21
> **bfhicks said:**
> I think the biggest thing here is the end-user. Most people do NOT CARE about what format it is. They want to upload a video, and watch it. 

Although I'd just like to point out to you that when I re-encoded some flash videos (.flv) to Ogg/Theora (.ogv), it cut the size of the file in half with no loss in quality. I think people might care if their movies loaded twice as fast.

---

### Post by simeon87 on 2009-05-21
> **soltanis said:**
> Although I'd just like to point out to you that when I re-encoded some flash videos (.flv) to Ogg/Theora (.ogv), it cut the size of the file in half with no loss in quality. I think people might care if their movies loaded twice as fast.

They will care about speed but all the abbreviations will be jibberish to them. If the software were to select "the best option" for them (best quality versus filesize ratio), they'll be even happier.

---

### Post by mysoogal on 2009-05-21
> **simeon87 said:**
> They will care about speed but all the abbreviations will be jibberish to them. If the software were to select "the best option" for them (best quality versus filesize ratio), they'll be even happier.

i would pick vorbis audio over mp3 or AAC anytime.:D most of my video clips are in ogm with h264 and vorbis audio ;)

hmm well this might be a pet project, but wasn't youtube one of these pet projects in the first place ? hmm google ? yahoo ?

i believe its just time, it took a while for stage6 to become well known and easy to use. this wont be different

---

### Post by mysoogal on 2009-06-05
its starting to look good ~ 

a world without flash media player looks so fine ! ;)


working site,  visit [www.mysoogal.com](www.mysoogal.com) 

make sure you have vlc mozilla plugin for firefox, also make sure you have the new vlc like 9.8 or 9.9 versions 

[IMG]http://i39.tinypic.com/2hqseuv.png[/IMG]

---

### Post by Bulletbeast on 2009-06-05
*-- error, delete please --*

---

### Post by Bulletbeast on 2009-06-05
> **mysoogal said:**
> that is exactly what i want to do, can you imagine on the upload page asking you

hey what kind of audio video format would you like your video to be encoded to  ?

option 1 : h264 ? AAC ?
option 2 : xvid ? vorbis ?
Option 3 : Divx ? ogg ?

You can't, *shouldn't* have *that* on the upload page. It would mean the user would have to upload, and then the server will have to process, hundreds of megabytes of raw, uncompressed video.

---

### Post by Tibuda on 2009-06-05
I got it working totem-gstreamer. Why do say it requires VLC?

---

### Post by mysoogal on 2009-06-05
> **danielrmt said:**
> I got it working totem-gstreamer. Why do say it requires VLC?

if you talking about my site, totem can take over some embeded type of videos. like divx divx it will replace the embed player with totem. in this case you might not have the vlc plugin installed so totem is default plugin player for web now

when you install the vlc plugin and restart firefox it will show the vlc player instead :KS

---

### Post by mysoogal on 2009-06-05
> **Bulletbeast said:**
> You can't, *shouldn't* have *that* on the upload page. It would mean the user would have to upload, and then the server will have to process, hundreds of megabytes of raw, uncompressed video.


**Of Course I can  and i will DO it without a doubt** ! ;) 

the proof is in creativity and history is full of great things  ! those that say you can't you shouldn't, are always left behind and cry afterward when it truly works :D
> 
The Wright Brothers - First Flight, 1903


they always said you can't and never would fly ! ;)

---

