---
title: "[SOLVED] how do I change my start up music?"
date: 2008-07-25
forum: New to Ubuntu
---

### Post by Zoonosis on 2008-07-25
I go to System/Preferences/Sound and change it to a .wav file I have, but I just get silence. Is there an easy fix? I'm not the best w/ Linux, but I'd like to learn it because I hate windows. Anyways, thanx for the help. :D

---

### Post by kpkeerthi on 2008-07-25
Does the wav file play when you open it in Totem or mplayer?

---

### Post by pedro_orange on 2008-07-25
Can you play this file in Ubuntu in RB or whatever is your music player of choice?
If not you might want to install some plugins that allow you to play that type of file.

---

### Post by Zoonosis on 2008-07-25
> **kpkeerthi said:**
> Does the wav file play when you open it in Totem or mplayer?

Yup

---

### Post by SunnyRabbiera on 2008-07-25
You mean the main login theme correct?

---

### Post by Zoonosis on 2008-07-25
When I log onto my account.

---

### Post by SunnyRabbiera on 2008-07-25
like at the logon screen?
I am just asking as there is the main drum beat when gdm starts (thats your log in screen) and the african sounding theme as gnome logs in (gnome is your desktop manager)

---

### Post by Zoonosis on 2008-07-25
> **SunnyRabbiera said:**
> like at the logon screen?
I am just asking as there is the main drum beat when gdm starts (thats your log in screen) and the african sounding theme as gnome logs in (gnome is your desktop manager)

The after I type in my username and password

---

### Post by SunnyRabbiera on 2008-07-25
when you are login into gnome then.
Alright, now is this login theme you made yourself or something you downloaded from the net?
Its possible you may have to edit it.

---

### Post by Zoonosis on 2008-07-25
I downloaded the music file.

---

### Post by SunnyRabbiera on 2008-07-25
alright, might I ask where?
some random site you went to or something?
its possible that this was a bad download even if it does work in your players.

---

### Post by Zoonosis on 2008-07-25
> **SunnyRabbiera said:**
> alright, might I ask where?
some random site you went to or something?
its possible that this was a bad download even if it does work in your players.

[http://www.moviesoundclips.net/sound.php?id=43](http://www.moviesoundclips.net/sound.php?id=43)

and I've tried other songs, they don't work also.

---

### Post by SunnyRabbiera on 2008-07-25
Hmm, well let me experiment a little here.

---

### Post by Zoonosis on 2008-07-25
ok

---

### Post by SunnyRabbiera on 2008-07-25
Alrights its the wav file from that one website you gave me.
You may want to convert one of the mp3's to a wav with a application called audacity.
Audacity is a free open source sound editor, go to system> administration and to synaptic package manager and search for audacity.
If you are unsure on how to use it use this guide:
[www.monkeyblog.org/ubuntu/installing](www.monkeyblog.org/ubuntu/installing)

---

### Post by Zoonosis on 2008-07-25
> **SunnyRabbiera said:**
> Alrights its the wav file from that one website you gave me.
You may want to convert one of the mp3's to a wav with a application called audacity.
Audacity is a free open source sound editor, go to system> administration and to synaptic package manager and search for audacity.
If you are unsure on how to use it use this guide:
[www.monkeyblog.org/ubuntu/installing](www.monkeyblog.org/ubuntu/installing)

I have Audicity and the one i downloaded was .wave . Should I transfer it into the: /usr/share/sounds . How can I allow changes to that folder? I'm not using Root login so I can't change it so I can transfer the file.

---

### Post by SunnyRabbiera on 2008-07-25
You dont need to move it there.
Just convert the file as I suggested, if you have a MP3 availible download that first then use audacity to convert it to a .wav.
I am betting those waves on that one site you linked are not properly coded for uses like this.
But if you need to know how to move files to the root owned folders, its easy to do.
Open up a terminal and type in gksudo nautilus, enabling nautilus to go into root user mode.

---

### Post by Zoonosis on 2008-07-25
still no :(

---

### Post by SunnyRabbiera on 2008-07-25
Huh... what other files did you try to download, all from the same site?
I am just wondering here as I was able to get mine working.
did you get all the codecs and such you need? that might be a part of the issue though I am unsure as I dont know what you did to make multimedia to work.

---

### Post by Zoonosis on 2008-07-25
:O It worked!! You rock! Thank you so much!

---

### Post by SunnyRabbiera on 2008-07-25
Thats cool, I knew it might have been something.
What fixed your issue?

---

### Post by Zoonosis on 2008-07-25
The download .mp3 then use audicity to convert. I tried the other thing first and then re-read your post. Sry bout that. And thanks again! :D

---

### Post by SunnyRabbiera on 2008-07-25
No prob.

---

