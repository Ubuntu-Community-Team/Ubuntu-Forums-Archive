---
title: "Simple command to play audio file for Xfce Timer"
date: 2014-02-25
forum: New to Ubuntu
---

### Post by mlnease on 2014-02-25
Hello,

I'd like to set Xfce4 Timer to play a particular audio file (in Parole) at a certain time.  This requires a command line; the file is at /home/mn/Music/Coyote.wav.  Can someone please tell me how to write this command?

I have a feeling I'd find this syntax(?) useful for a lot of other purposes (shortcuts?  launchers?) as well.  

Thanks in advance.

---

### Post by tgalati4 on 2014-02-25
```
aplay /home/mn/Music/Coyote.wav
```

I can think of at least 5 other ways to do this.  Your challenge is to come up with the others.

---

### Post by mlnease on 2014-02-25
'Ludicrous Speed' is right--thanks for the quick response.  As for the challenge, well--although I've been using Ubuntu (now Xubuntu) exclusively--and a lot--for quite a few years, I've never actually written a line of code (except for a bit of HTML years ago on a job) and wouldn't know where or how to begin.  I've always used the command line when possible (mainly copying and pasting) but basically I'm a GUI user.  

I've noticed before that there's a kind of disconnect between coders and non-coders.  The former sometimes seem to me to take it for granted that all users do or should know how to write code and in an ideal world maybe we all would.  But I don't.

Thanks a million for your line, though--works great (but you knew that).

---

### Post by tgalati4 on 2014-02-26
I thought the primary reason to use linux was that you could bend it.  Otherwise we are all non-thinking zombies blindly clicking at web links saying:  "Oooh Shiny I have to have that."

```
mplayer /home/mn/Music/Coyote.wav
```

Come on there are a few more.

---

### Post by andrew.46 on 2014-02-28
**No. 3**

sox has a nice utility called *play*:


```

andrew@ilium~/shared/luckynight$ **[COLOR="#FF0000"]play luckynight.wav [/COLOR]**

luckynight.wav:

 File Size: 10.7M     Bit Rate: 1.41M
  Encoding: Signed PCM    
  Channels: 2 @ 16-bit   
Samplerate: 44100Hz      
Replaygain: off         
  Duration: 00:01:00.48  

In:100%  00:01:00.48 [00:00:00.00] Out:2.90M [      |      ] Hd:0.4 Clip:0    
Done.

```

**No. 4**

although the same effect can be had by using sox with the -d option:

```

andrew@ilium~/shared/luckynight$ **[COLOR="#FF0000"]sox luckynight.wav -d[/COLOR]**

luckynight.wav:

 File Size: 10.7M     Bit Rate: 1.41M
  Encoding: Signed PCM    
  Channels: 2 @ 16-bit   
Samplerate: 44100Hz      
Replaygain: off         
  Duration: 00:01:00.48  

In:100%  00:01:00.48 [00:00:00.00] Out:2.90M [      |      ] Hd:0.4 Clip:0    
Done.

```

I believe that makes a total of 4 simple commandlines to play a wav file :). Many more to come...

---

### Post by tgalati4 on 2014-03-01
Number 5:  ```
avplay -nodisp -autoexit -nostats login.wav
```

Number 6:  You can play a sound through DBUS, but I haven't figured out the syntax yet:

[https://developer.gnome.org/notification-spec/](https://developer.gnome.org/notification-spec/)

---

### Post by andrew.46 on 2014-03-01
**No. 7**

Among many other faces vlc has a purely commandline interface:

```

andrew@ilium~/shared/luckynight$ **[COLOR="#FF0000"]cvlc luckynight.wav [/COLOR]**
VLC media player 2.1.3 Rincewind (revision 2.1.3-0-ge6a71cc)
[0x20b4ac8] dummy interface: using the dummy interface module...
[0x1ff7678] main playlist: end of playlist, exiting

```

**No. 8**

Audacious has a 'headless' option:

```

audacious --headless --quit-after-play luckynight.wav 

```

I have a few more in mind but I don't want to hog the spotlight :)

---

### Post by Yellow Pasque on 2014-03-01
> play a particular audio file **(in Parole)** at a certain time

Is it just me, or did everyone in this question (including OP) ignore the "in Parole" part?

---

### Post by tgalati4 on 2014-03-01
I ignored it because installing it would pull in a lot of XFCE4 libraries, so I presumed it was an XFCE-specific application.

```
man parole
```

might provide some clues.  We are just providing different options.  

So anyone run *parole* and how do you play a file?

---

### Post by Yellow Pasque on 2014-03-01
I think it's mpris compatible, so you could probably control it from command line like that. I'm still a little hazy on exactly what the OP was trying to do..

---

### Post by sam_baker2 on 2014-03-02
~also mlneas, you may want to look at alarm-clock-applet.
It does most everything xfce4-timer does and has the added
option to repeat on certain days.

---

### Post by mlnease on 2014-03-02
(Thanks.)

Equalum Forum.

---

