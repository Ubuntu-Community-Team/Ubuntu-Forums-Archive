---
title: "Ipod troubles with Rhythmbox"
date: 2008-09-08
forum: New to Ubuntu
---

### Post by projecthikari on 2008-09-08
I took some songs off of a CD and simply...

The songs will not go onto the Ipod. It seems I have trouble with .ogg files or something. I have enough space, there is no doubt in that. Will Ipod simply not read .ogg?

---

### Post by kpkeerthi on 2008-09-08
ipods support mp3 and aac. no support for .ogg. See [www.rockbox.org](www.rockbox.org).

---

### Post by dioltas on 2008-09-08
Ya, kpkeerthi is right. Ipod wont play .ogg. You'll have to convert them to mp3. To rip to mp3 from cd using rhythmbox you have to install a gstreamer package, can't remember exactly what it's called though


[Here's a guide to ripping to mp3 using sound juicer, probably better than rhythmbox for ripping music.]("http://ubuntuforums.org/showthread.php?t=957")
I can't remember exactly how to enable it in rythmbox, but you need some gstreamer package alright I think. Im not at home now so I can't check my settings or what packages I have installed.

---

### Post by ricardisimo on 2008-09-27
Something else is up, though, because on Feisty (and before, I think) Rhythmbox would automatically re-encode any audio file you dragged and dropped to your ipod to mp3, so as to avoid having to keep two versions of every song on your hard drive - one ogg, say, and another mp3. Not any more, or at least not very well. Rhythmbox can play the converted files off of the ipod, but the ipod itself cannot. Anyone know what's up with that?

Also, gtkpod claims to have a script at its disposal for exactly the same conversion, but it has never worked for me. Am I perhaps missing a component?

---

### Post by t0p on 2008-09-27
If you want to rip tracks off a cd so they'll be in mp3 format, you need to install the appropriate codecs.  A whole bunch of proprietary codecs are available by installing the **ubuntu-restricted-extras** package.  You can get it through Synaptic or by typing into the terminal:

```
sudo apt-get install ubuntu-restricted-extras
```

This'll give you many music and video codecs, plus flash, java, and more!

---

### Post by ricardisimo on 2008-09-27
No, that's not the issue. I can rip to mp3, play mp3s, etc. I just prefer ogg for most purposes. What I cannot do is sync ogg files to my ipods. No problem, Rhythmbox would re-encode on-the-fly for synching purposes... or at least it used to do so. Not any more.

---

### Post by ricardisimo on 2008-09-28
I changed the preferred format in Rhythmbox to "Lossy (mp3)" or whatever, as another thread suggested. That seemed silly, and nothing to do with this issue, but I've seen sillier in linux, so I tried it. Nothing.

Any other recommendations? Thanks in advance.

---

### Post by ricardisimo on 2008-10-01
Would anyone know about the issue I mentioned earlier, with the script in gtkpod?

Or, could someone could tell me whether or not they can drag and drop ogg files onto their iPod via Rhythmbox, and actually be able to play them on a docking station or earphones? I would greatly appreciate it. Thanks.

---

### Post by ricardisimo on 2008-10-05
Hello? Anyone there? Can anyone on Hardy try dragging and dropping an ogg or flac file into their ipod via rhythmbox to tell me if it works for them? Thanks.

---

### Post by BandD on 2008-10-05
What kind of ipod do you have?

I am able to drag and drop .ogg files to my ipod and it transcodes them on the fly as you say.  I've never been able to get gtkpod to do that either.

I also don't really use the Apple firmware anymore either, I use rockbox instead.  Lately I've been transferring actual .ogg files to my Ipod.  

But I just tried it with Rhythmbox and it worked for me.

---

### Post by ricardisimo on 2008-10-05
I'm using the Apple firmware on two different 60G video, one 4G Nano and a Shuffle. The latter never worked, noy on Linux, not on my wife's Mac, nowhere. The other three worked perfectly every which way until Hardy, whether I used gtkpod or Rhythmbox. I'd still like to find out if there's just one little app somewhere that didn't get installed with Hardy that will fix the problem.

Rockbox, eh? I was thinking of trying linuxipod. We'll see.

---

### Post by bleedpurple on 2009-01-17
> **BandD said:**
> What kind of ipod do you have?



I have the same problem as described in this thread. I have an ipod shuffle.

---

### Post by eilios on 2009-01-17
> **bleedpurple said:**
> I have the same problem as described in this thread. I have an _ipod shuffle_.

> **ricardisimo said:**
> I'm using the Apple firmware on two different 60G video, one 4G Nano and a _Shuffle. The latter never worked_, noy on Linux, not on my wife's Mac, nowhere. The other three worked perfectly every which way until Hardy, whether I used gtkpod or Rhythmbox. I'd still like to find out if there's just one little app somewhere that didn't get installed with Hardy that will fix the problem.

Rockbox, eh? I was thinking of trying linuxipod. We'll see.

Well, I think we can see the problem :).
Try Rockbox and see if that works. But I doubt that the shuffle will be able to work - I think it's just a firmware issue.

---

### Post by BandD on 2009-01-17
> **bleedpurple said:**
> I have the same problem as described in this thread. I have an ipod shuffle.

What generation shuffle are you using?  What version of Ubuntu are you using?

---

