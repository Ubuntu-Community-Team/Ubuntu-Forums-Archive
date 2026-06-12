---
title: "can't p play dvd with vlc"
date: 2011-10-07
forum: New to Ubuntu
---

### Post by seimon on 2011-10-07
**sorry wrong title, wanted to write vlc, not movieplayer (but more or less the same problem as with vlc)**

hello everybody

i'm quite new at ubuntu (10.10) and wanted to watch a dvd with vlc the first time. that didn't work. i'm quite sure i've installed all the recommended packages (libdvd etc...) and spent a lot of time in many forums to see, if somebody knew this problem. but no i don't know what to do anymore.

at first, vlc did nothing, when i tried to watch the dvd, nothing happened. vlc stayed open, but did nothing.
then i found out that it must have something to do with the the fact, that the dvd is saved of copying (i'm sorry, don't know the english word for that).
so i installed a dvd-region tool and changed the region for my drive to 2 (europe). that helped a little bit, at least vlc started to play the dvd, but with a grey screen and buffering sound (don't know if buffering is the right english word, could just hear some pieces of the sound, but i could hear the sound).

anyhow i started to change the video output settings, the made some difference (sometimes vlc crashed, somtimes screen stayed black, sometimes it opened some stupid new windows i couldn't close anymore), but nothing helped.

uninstalled and installed vlc again and now i don't have anymore ideas.

so i decided to join that forum. i didn't do a lot of new search in this forum because im quite tired of that and it's my first entry here, so i hope i'm doing the rules

thx a lot, maybe you can help me.
by the way, i'm using ubuntu 10.10, 2.6.35-30, on a hp pavilion dm4 2040ez, if that helps.

thx you guys

---

### Post by ajgreeny on 2011-10-07
Is this just the one DVD or all DVDs that will not play, and are you sure you have the libdvdcss2 installed in the system?   Run ```
locate libdvdcss
``` to find out if you do or not.

Do you mean this is a copied DVD and if so how was that done?

---

### Post by seimon on 2011-10-07
thx a lot for your reply.
i'm quite sure i did, because i installed many such thing and on every page i visited i did what they recommanded.

but when i run "locate libdvdcss" nothing appears in the terminal. is this okay like that?

no, i meant it is a dvd which is saved against copying, normal movie, bought in a store. when i took a dvd which was not saved, vlc could play ist.

thx

---

### Post by FormatSeize on 2011-10-07
Try to install libdvdcss.
```

sudo apt-get install libdvdcss
sudo apt-get update
```

---

### Post by proxy.qtz on 2011-10-07
Have you installed the Ubuntu restricted packages?

---

### Post by ajgreeny on 2011-10-07
> **FormatSeize said:**
> Try to install libdvdcss.
```

sudo apt-get install libdvdcss
sudo apt-get update
```
To do this with that command you will need to enable the medibuntu repositories.
[Medibuntu]("http://www.medibuntu.org/")

---

### Post by seimon on 2011-10-07
> **proxy.qtz said:**
> Have you installed the Ubuntu restricted packages?


yes, i did.

thank you a lot for your help, but unfortunately nothing helped...

---

### Post by pqwoerituytrueiwoq on 2011-10-07
```
sudo apt-get install libdvdread4;sudo /usr/share/doc/libdvdread4/install-css.sh
```
[https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs](https://help.ubuntu.com/community/RestrictedFormats/PlayingDVDs)
try that

---

### Post by seimon on 2011-10-07
already did that before, did it again, nothing again.

i tried it with another dvd too, this one won't even be opened by vlc (vlc crashes). will be opened by movie player, but movie player can't play it either.

any other ideas?

---

### Post by beew on 2011-10-07
Open the terminal and type > vlc cdda:// and see if it plays.

---

### Post by seimon on 2011-10-07
thx for input, vlc doen't play. vlc seems to think that dvd is an audio cd. when vlc is opened, terminal starts to write a very long list like that:

```
[0x9ec5904] cdda access error: cannot read sector 12782
[0x9ec5904] cdda access error: could not read block 12783 from disc
[0x9ec5904] cdda access error: cannot read sector 12783
[0x9ec5904] cdda access error: could not read block 12784 from disc
[0x9ec5904] cdda access error: cannot read sector 12784
[0x9ec5904] cdda access error: could not read block 12785 from disc
[0x9ec5904] cdda access error: cannot read sector 12785
[0x9ec5904] cdda access error: could not read block 12786 from disc
[0x9ec5904] cdda access error: cannot read sector 12786
......

```it never stops writing until i close vlc. when i close vlc-player, terminal says:

```
[0x9ec50a4] es demux error: cannot peek
[0x9ec50a4] es demux error: cannot peek
[0x9ec50a4] es demux error: cannot peek
[0x9ec50a4] es demux error: cannot peek

```

---

### Post by nothingspecial on 2011-10-07
> **seimon said:**
> **sorry wrong title, wanted to write vlc, not movieplayer (but more or less the same problem as with vlc)**



Fixed :)

---

### Post by beew on 2011-10-07
Sorry I meant to say > vlc dvd://

---

### Post by seimon on 2011-10-07
> **nothingspecial said:**
> Fixed :)

thx!


when i do ```
vlc dvd://                      
``` the terminal goes really crazy. it seems to write and delete, forward, back, totally crazy. and always the same words:
[COLOR=Lime]
[0xb160541c][/COLOR] main video output error: [COLOR=Red]Invalid picture reference count [0xb160684, 0][/COLOR]

really funny. i can't write anything in the terminal, can stop that only by doing alt+f4, even when vlc is closed a long time ago. really funny.

---

### Post by seimon on 2011-10-07
solved it by installing ubuntu 11.04.

works fine here.

thank you all.

---

