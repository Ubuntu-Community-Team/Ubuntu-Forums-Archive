---
title: "dvd burner"
date: 2008-05-13
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-13
I am looking for a burner that will copy subtitles and different languages any ideas
 I have DVDs on my hard drive with subtitles and different languages. They are from my windows xp days I used to use nero but couldnt install subs or different languages I just wondered if Ubuntu had something to Extract files from my hard drive and burn them onto a DVD

---

### Post by shifty_powers on 2008-05-13
k3b, imgburn, brasero?

---

### Post by nicedude on 2008-05-13
I am looking for a burner that will copy subtitles and different languages any ideas?

I don't understand your question as a DVD burning program just burns images or files to a physical disk. Do you need something to extract video from DVD's along with subtitles or something to take a video file and sub title file and stick them together on a DVD for playback?

Check out mencoder or acidrip (frontend to mencoder) if your trying to extract DVD's with subs.

---

### Post by Xiong Chiamiov on 2008-05-13
He isn't the most clear person around here, but I think what he's asking for is a way to burn a DVD with multiple audio tracks and optional subtitles, that you turn on in some way.  If he's not, then, well, I'm interested.  So far I've had to convert my .mkv's into mpeg4's with hard subs to be able to burn them.  I ran across a program to make menus, once, but it always crashed on me.

---

### Post by jolx on 2008-05-13
devede can put movies and subtitles together

---

### Post by Xiong Chiamiov on 2008-05-13
> **jolx said:**
> devede can put movies and subtitles together
Exactly.  That's what I've been using, but I'd like to *not* have them muxed together into a hardsub.  I want to be able to burn a DVD with both Japanese and English audio, and have the option of having the subs on or off.  DeVeDe just picks a sub track and an audio track and mushes 'em together into an mp4.

---

### Post by philipluna66 on 2008-05-13
Thats exactlly it. i want to put English and Spanish audios and subs and be able to pick which I want for example English audio and spanish subs. It must be possible cos I have All startrek The nect Generation and I can do it with them

---

### Post by nicedude on 2008-05-14
I am not sure then phillip and I must confess I still use WinXP when I want to author DVD's since there are no comparable softwares to the ones I use, ie. Cinema craft encoder, pro coder, tsunami DVD author & tsunami video conversion . If anyone knows of linux based software that can even come close to these than please PM me as I would like to know myself. I think the main problem is that professional DVD authoring programs are very expensive and as such they prefer to protect them by requiring a Windows closed source system for operation ( fat lot of good it does them though as I paid $0 :-)  )

Though anymore I just prefer to not convert at all since you can easily obtain all your video needs in a Divx or Xvid format along with any .srt subtitle files and then use a Nvidia card to pipe them to your TV set. Also I would recommend checking out portable hard drives with built in video decoding, I bought a 500GB model for $200US and it plays DIVX, XVID, MPEG & DVD's if DVD is direct copied to it - all from the portable hard drive direct to a TV via RCA cables allowing me to walk around with 500 movies ready to play on any modern TV, in the space of a medium size book ( my brand portable is "Inoi" )

Well hope you find a solution that works for you :-)

---

### Post by ramjet_1953 on 2008-05-14
What you need is a combination of k3b and k9copy.

Both of these programs are for KDE, but work fine under GNOME.

You can load both using Synaptic Package Manager.

K9copy will squeeze your DVD9 disks down to DVD5 without any noticeable loss in quality. You have the option to maintain the full menu options on the original DVD.

k3b will then burn the iso produced by k9copy onto a blank DVD5.

k9copy does offer the option to directly burn the DVD, but I have found it buggy and if the burn fails, you end up with a coaster.

Regards,
Roger :cool:

---

### Post by nicedude on 2008-05-14
Nero is available for Linux as well as windows. Its what I found to be the best to use on Ubuntu for burning ISO's and data disks without getting a single coaster. K3b on the other hand doesn't seem to like my DVD drive and showed hit & miss performance for me.

---

### Post by shifty_powers on 2008-05-14
> **philipluna66 said:**
> Thats exactlly it. i want to put English and Spanish audios and subs and be able to pick which I want for example English audio and spanish subs. It must be possible cos I have All startrek The nect Generation and I can do it with them

maybe not ideal for linux users, but convertxtodvd which i use with wine, does the job perfectly. It's a simple but powerful program which will do exactly what you want.

i've burnt dvd's of stuff like love hina, with both japanese and english audio AND japanese and english subtitles. And it wasn't hardmuxed either.

It's not free software, but it's not hard to get hold of ;)

---

### Post by Xiong Chiamiov on 2008-05-14
> **shifty_powers said:**
> maybe not ideal for linux users, but convertxtodvd which i use with wine, does the job perfectly. It's a simple but powerful program which will do exactly what you want.

i've burnt dvd's of stuff like love hina, with both japanese and english audio AND japanese and english subtitles. And it wasn't hardmuxed either.

It's not free software, but it's not hard to get hold of ;)
We don't support software piracy in this forum.  I will have to check into (ahem) buying it.

@ramjet: That would be great, except I don't have them on DVDs, since they're fansubs.

---

### Post by shifty_powers on 2008-05-15
heh, well that's what i love about ubuntu, for the most part. You CAN@T pirate something under a gpl ;)

---

