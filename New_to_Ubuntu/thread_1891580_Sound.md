---
title: "Sound"
date: 2011-12-05
forum: New to Ubuntu
---

### Post by saintj0n on 2011-12-05
Hi.
I am using Lubuntu 10.04 and have just installed recently so I am still learning what is on my system and what isn't.  My sound doesn't work.  I load up a .m3u file and play it on Mplayer and it acts like it is playing but no sound comes out of the speaker whatsoever.  How can I troubleshoot this?:confused:

---

### Post by click4851 on 2011-12-06
well, ok so you probably know already that an .m3u file is just a playlist. Doesn't do much by itself. Do you have an optical drive you could test an audio cd to start? Course you want to check and make sure your sound isn't muted.

---

### Post by 2F4U on 2011-12-06
Did you test it with other audio formats like flac, vorbis, etc., so that we could find out whether it is an issue with the audio driver, codecs or something else?

---

### Post by Rodney9 on 2011-12-06
Sound troubleshooting
Have a look at this site - 

[https://help.ubuntu.com/community/SoundTroubleshooting](https://help.ubuntu.com/community/SoundTroubleshooting)

and this one, more up todate, but still a work in progress, however very good - 

[https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit](https://docs.google.com/document/d/1iTlJ8BfqXUjaHO__TEdlkvuqB1WLOkGaudngc5SFLMI/edit)

For How-To's, Information and Screen-Casts on Lubuntu go to the
Lubuntu One Stop Thread - 

[[COLOR="Blue"]Lubuntu One Stop Thread[/COLOR]]("http://ubuntuforums.org/showthread.php?t=1844755")

Rodney

---

### Post by DapperMe17 on 2011-12-06
Do you have the "ubuntu-resticted-extras" package installed? 

That package will contain all of the required codecs.

:popcorn:

---

### Post by saintj0n on 2011-12-06
> **DapperMe17 said:**
> Do you have the "ubuntu-resticted-extras" package installed? 

That package will contain all of the required codecs.

:popcorn:

Yep.  Its installed.

---

### Post by saintj0n on 2011-12-06
Ok.  I figured out that if I unplug the cable from my sound card and plug it into the onboard sound port then I get sound.  How can I switch to the card?

---

### Post by marinara on 2011-12-07
try this
[http://ubuntuforums.org/showpost.php?p=11096695&postcount=6](http://ubuntuforums.org/showpost.php?p=11096695&postcount=6)

it will change the default sound card.  It worked for me, i needed to disable HDMI

---

