---
title: "[SOLVED] Ipod Trouble"
date: 2008-09-18
forum: New to Ubuntu
---

### Post by Truant_84 on 2008-09-18
So I've been managing my iPod through Banshee for awhile now and until recently have never had any problems. All of my music is either mp3's from isohunt, or AAC's that I rip from cds through audio cd extractor. When I try to add new files to my ipod, all that gets added are the song titles. When I go to play the songs it acts like the files aren't there. Any ideas?

---

### Post by Truant_84 on 2008-09-19
Bump

---

### Post by pyromanic123boom on 2008-09-19
try amarok...I guess you could say it's the linux replacement for itunes when it comes to handling your ipod.

---

### Post by erykroom on 2008-09-19
Try a different music player like rhythmbox or exaile

edit: If you use gnome then amarok takes a lot of resurces. Much lighter than amarok is exaile and it has basically the same functionality (only it uses gtk)

---

### Post by Truant_84 on 2008-09-19
I actually figured out what the problem is. My ipod apparently doesn't like AAC files that I ripped from CD's in Sound Juicer. Now the problem is that the program doesn't give me the option to rip cd's as mp3's. Any suggestions?  Ipod's don't accept the ogg vorbis file type, correct?

---

### Post by erykroom on 2008-09-19
Try to rip your cd-s with Sound Juicer. There you can choose the format: mp3 ogg flac and so on.

---

### Post by erykroom on 2008-09-19
And you should also check if you have installed "libmad0" and "libmad0 devel" packages

---

### Post by Truant_84 on 2008-09-19
I have been using Sound Juicer and already have both of those packages installed. Sound Juicer does not give me the option to rip as mp3.

---

### Post by clive littlewood on 2008-09-19
Hi

Audio CD extractor in add/remove programs will extract as mp3

So will K3b.

I would use Amarok for your ipod.

Hope this helps

cl

---

### Post by Truant_84 on 2008-09-19
Sound Juicer DOES NOT give me the option to rip as mp3. When go to "edit profiles" under "preferences," mp3 is listed, but it won't give me the option to rip as mp3. I just tried k3b. It told me that my optical drive was in use by another program, even though k3b was the only program I had open. I told it to close the program blocking the use of my optical drive and then tried to rip the cd again. This time it just gave me an error message and ejected the cd.

---

### Post by erykroom on 2008-09-19
If you take preferences in sound juicer there should be an place where you can change ogg to mp3 and when you start ripping the files will be in mp3 format

---

### Post by Truant_84 on 2008-09-19
Does anyone know what the gstreamer pipeline would have to be in order to create a profile to rip mp3-s with in sound juicer?

---

### Post by Teamgeist on 2008-09-19
Hi.

First install the package ubuntu-restricted-extras

```
sudo apt-get install ubuntu-restricted-extras
```

After that SoundJuicer will give you the option to rip in MP3.

Even though the gstreamer-pipeline will be pre-configured in Soundjuicer once you installed the package above, her it is
```
audio/x-raw-int,rate=44100,channels=2 ! lame name=enc mode=0 vbr-quality=6 ! id3v2mux
```

---

### Post by Truant_84 on 2008-09-19
So I ran the command line, eventually it brought me to a blue terms and conditions screen inside the terminal, I'm unable to move past that, hitting "enter" doesn't bring me out of the screen.

---

### Post by Teamgeist on 2008-09-19
hehe... the arrow keys on your keyboard will highlight the "ok"-Button. Then hit "Enter" and you will be able to proceed.

You will figure it out. Don't worry. :)

---

### Post by Truant_84 on 2008-09-19
Ok, so I actually finished things through the update manager which brought up the sun-java add-ons. My sound juicer still doesn't give me the option to rip as mp3 though. I'm having a bad linux day.

---

### Post by Teamgeist on 2008-09-19
Ok, thats odd...

Try this

```
 sudo apt-get install gstreamer0.10-plugins-good gstreamer0.10-plugins-bad gstreamer0.10-plugins-bad-multiverse gstreamer0.10-plugins-ugly gstreamer0.10-plugins-ugly-multiverse lame 
```

Unfortunately I will have to go now. It's like 9:30 p.m. here in Germany on a Friday night and there is beer thats needs my attention somewhere. :popcorn:

Will be back tomorrow. Would be nice if you post here if you succeeded, though.

/edit: If this did not help try this:

```
 sudo apt-get install gstreamer0.10-fluendo-mp3 
```

---

### Post by Truant_84 on 2008-09-19
Awesome, that last command line solved everything. Thanks so much!

---

### Post by Teamgeist on 2008-09-19
Well, awesome!

Still odd, but if you're ready to go now, good.

Still make sure you have the lame-enocoder installed.

```
sudo apt-get install lame
```

Also, now that you're a Pro at the command line, have a look at his.
[www.medibuntu.org](www.medibuntu.org)

---

