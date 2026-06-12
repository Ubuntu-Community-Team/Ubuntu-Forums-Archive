---
title: "Converting DVD VOB files for PS3"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by teeceegee on 2008-04-22
Hello Folks,

Has anyone had any success converting DVD VOBs into a more compressed (but still good quality) format that I can play on my PS3? I'm just looking to put episodes of shows I watch frequently onto the PS3 so I don't have to go and find/change the DVD every time I want to watch it.

I'm not particularly bothered exactly what the format is. I'm not interested in sharing the files with anyone else. I've tried ffmpeg and mencoder and various tools around them but nothing seems to work, yet a divx file downloaded from the internet works fine.

Does anyone have any success in encoding from a ripped DVD VOB to a PS3 compatible file format?

Cheers
TCG

---

### Post by grifter13 on 2008-04-22
> **teeceegee said:**
> Hello Folks,

Has anyone had any success converting DVD VOBs into a more compressed (but still good quality) format that I can play on my PS3? I'm just looking to put episodes of shows I watch frequently onto the PS3 so I don't have to go and find/change the DVD every time I want to watch it.

I'm not particularly bothered exactly what the format is. I'm not interested in sharing the files with anyone else. I've tried ffmpeg and mencoder and various tools around them but nothing seems to work, yet a divx file downloaded from the internet works fine.

Does anyone have any success in encoding from a ripped DVD VOB to a PS3 compatible file format?

Cheers
TCG

Hey TCG,

I posted the almost the same question a few days back.  However it was regarding streaming media from a DLNA server (mythtv and twonki in my case) to PS3.  Regarding re-encodeing I use ffmpeg with the following options :

ffmpeg -y -i MY_VOB.VOB -an -v 1 -threads auto -vcodec h264 -b 1024k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 2048k -bufsize 2M -cmp 1 -s 780x420 -f mp4 -pass 1 /dev/null

ffmpeg -y -i MY_VOB.VOB -v 1 -threads auto -vcodec h264 -b 1024k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 780x420x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 output_file.mp4

There is no magic to the bitrate (-b option) I chose, 1024K gives me an the clearity and file size that I am willing to accept.  However I do recommend that you set the resolution (-s option) the same as whats in your content.  Otherwise you will be double scaleing (from ffmpeg and PS3) which will give you pretty bad picture quality.  This is especially true if you are up-scaling.
I hope this helps.

grift

---

### Post by grifter13 on 2008-04-22
Oh incidentally this page is where I got the information from :

[COLOR="Blue"]https://help.ubuntu.com/community/iPodVideoEncoding[/COLOR]

Yeah I know, it was intended for IPod, but its the same thing.

grift

---

### Post by teeceegee on 2008-04-23
Grifter

Thanks very much for your suggestions. I'll try these out tonight and report back.

TCG

---

### Post by joshrobinson on 2008-04-23
i would use dvdrip, its a gui front-end for command line converting
its in the repo's

---

### Post by twright on 2008-04-23
or you could use winFF

---

### Post by teeceegee on 2008-04-24
> **grifter13 said:**
> Hey TCG,

I posted the almost the same question a few days back.  However it was regarding streaming media from a DLNA server (mythtv and twonki in my case) to PS3.  Regarding re-encodeing I use ffmpeg with the following options :

ffmpeg -y -i MY_VOB.VOB -an -v 1 -threads auto -vcodec h264 -b 1024k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 1 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 2048k -bufsize 2M -cmp 1 -s 780x420 -f mp4 -pass 1 /dev/null

ffmpeg -y -i MY_VOB.VOB -v 1 -threads auto -vcodec h264 -b 1024k -bt 175k -refs 1 -loop 1 -deblockalpha 0 -deblockbeta 0 -parti4x4 1 -partp8x8 1 -me full -subq 6 -me_range 21 -chroma 1 -slice 2 -bf 0 -level 30 -g 300 -keyint_min 30 -sc_threshold 40 -rc_eq 'blurCplx^(1-qComp)' -qcomp 0.7 -qmax 51 -qdiff 4 -i_qfactor 0.71428572 -maxrate 768k -bufsize 2M -cmp 1 -s 780x420x480 -acodec aac -ab 96 -ar 48000 -ac 2 -f mp4 -pass 2 output_file.mp4

There is no magic to the bitrate (-b option) I chose, 1024K gives me an the clearity and file size that I am willing to accept.  However I do recommend that you set the resolution (-s option) the same as whats in your content.  Otherwise you will be double scaleing (from ffmpeg and PS3) which will give you pretty bad picture quality.  This is especially true if you are up-scaling.
I hope this helps.

grift

Just a quick update.

I tried the commands provided by grift (as shown) and the results were not good. The video was skewed at an angle of about 30 degrees. I suspect that this is something to do with the fact that the video was in PAL format. I tried changing the resolution in the commands from 720x480 to the PAL resolution of 720x576 but without much difference (this has been just playing the resultant video back in Ubuntu, there seemed little point trying it on the PS3 until I could get it watchable on the PC).

I've not had much chance to play with this as I'm quite busy at the moment but I'll try an NTSC DVD to see if that works and if it does look to see if I can get the commands working with PAL.

Cheers
TCG

---

### Post by teeceegee on 2008-04-24
> **joshrobinson said:**
> i would use dvdrip, its a gui front-end for command line converting
its in the repo's

Thanks josh, I have looked at this as well but didn't find the right combination of parameters. Do you have suggestions?

Cheers
TCG

---

### Post by teeceegee on 2008-04-24
> **twright said:**
> or you could use winFF

Thanks for the suggestion twright. I will try this out and see what results I get.

Cheers
TCG

---

### Post by grifter13 on 2008-04-24
> **teeceegee said:**
> Just a quick update.

I tried the commands provided by grift (as shown) and the results were not good. The video was skewed at an angle of about 30 degrees. I suspect that this is something to do with the fact that the video was in PAL format. I tried changing the resolution in the commands from 720x480 to the PAL resolution of 720x576 but without much difference (this has been just playing the resultant video back in Ubuntu, there seemed little point trying it on the PS3 until I could get it watchable on the PC).

I've not had much chance to play with this as I'm quite busy at the moment but I'll try an NTSC DVD to see if that works and if it does look to see if I can get the commands working with PAL.

Cheers
TCG

I'm sorry to hear that it did not work for your particular content.  I'm afraid I don't have any experience with PAL format contents, since all mine are in NTSC.  However I pretty sure there is something in FFMPEG that will support/convert PAL.  Kept me posted on how it goes, I'm interested about PAL myself.

Grift

---

### Post by teeceegee on 2008-04-25
A quick update for you. I had no luck getting my PAL content working so I tried some NTSC stuff. This looked no better on the PC than had the PAL so I thought I'd throw it at the PS3 anyway and it was fine on there. Given that I tried the PAL content too but with that I got sound but no picture so we're not quite there yet. I'll keep trying.

I had some success with winFF but it seems to be a big buggy (for me at least) in as much as it seems to expect logging files to be present and can't create them. I got past one problem but can't use 2 pass encoding because it gives the following error:

ratecontrol_init: can't open stats file

if anyone knows the name of the file it can't open I can create it and hopefully get this working.

Cheers
TCG

---

