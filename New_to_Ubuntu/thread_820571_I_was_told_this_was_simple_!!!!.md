---
title: "I was told this was simple !!!!"
date: 2008-06-06
forum: New to Ubuntu
---

### Post by kevgray on 2008-06-06
Hi all,
Everything I read says Linux is simple !!!
I'm a new user, I've installed UBUNTU 7.10 (I think).

**[COLOR="Red"]I have no SOUND[/COLOR]** - my soundcard is AUDIGY 2 ZS

**[COLOR="Red"]I can't PRINT[/COLOR]** - my printer is BROTHER MFC-235C

Someone please tell me how to solve my problems.

Considering staying with XP..........!!!!! at least - it works....

Cheers
Kev

---

### Post by avtolle on 2008-06-06
[http://ubuntuforums.org/showthread.php?t=590793](http://ubuntuforums.org/showthread.php?t=590793) will help you install the printer if you are indeed under 7.10. On the sound card, someone else will need to help you.

---

### Post by Duck2006 on 2008-06-06
> I have no SOUND - my soundcard is AUDIGY 2 ZS

Unless they have fixed the drivers you may not get it working.

---

### Post by diablo75 on 2008-06-06
I have an Audigy 2 ZS and have never had a problem getting it to produce sound.

You should check your volume mixer, and make sure you have all the relevant levels showing on your mixer.  Double-click on the speaker icon in your top task bar, and then in the menus at the top of the mixer, one of them has "Properties" in it.  This opens something up that's similar to the "Properties" box you found in Windows, which would show you a listing of all the possible input/output sources your sound card has, such as PCM (and/or) PCM Front, etc.  Check off as many as you can, would be my suggestion.  Then start a sound playing, like an mp3, and start experimenting with the levels to see if any of the muted ones needed to be turned up first.


Also, by chance, does your motherboard have on-board sound?  IF so, and if it is enabled in your BIOS, it's possible that Ubuntu is directing sound towards that device instead of your sound blaster.  Go into your BIOS and disable the AC 97 (that's probably what it is, but otherwise it would just be called On Board/Integrated sound).

---

### Post by Perfect Storm on 2008-06-06
Open the terminal (applications tab ---> Accessories ---> terminal) and type;

```
alsa-mixer
```

Check if anything/somehing is turned down or muted 
(press m to unmute/mute)

---

### Post by diablo75 on 2008-06-06
> **kevgray said:**
>  I've installed UBUNTU 7.10 (I think).


Where did you download it from?

---

### Post by billgoldberg on 2008-06-06
> **kevgray said:**
> Hi all,
Everything I read says Linux is simple !!!
I'm a new user, I've installed UBUNTU 7.10 (I think).

**[COLOR="Red"]I have no SOUND[/COLOR]** - my soundcard is AUDIGY 2 ZS

**[COLOR="Red"]I can't PRINT[/COLOR]** - my printer is BROTHER MFC-235C

Someone please tell me how to solve my problems.

Considering staying with XP..........!!!!! at least - it works....

Cheers
Kev

After reading your post, I don't want to help you.

---

