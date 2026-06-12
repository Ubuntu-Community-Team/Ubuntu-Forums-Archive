---
title: "Amarok 2 Poor Sound Quality"
date: 2011-09-23
forum: New to Ubuntu
---

### Post by Mega_Fauna on 2011-09-23
Hi,

Amarok 2 has very poor sound quality. It sounds blurring and bassy, and as if heard through water. VLC and Banshee all play just fine.

Have tried both the backends GStreamer and Xine and they make no difference.

Should I be posting this on the Amarok website instead?


Ubuntu 11.04 - the Natty Narwhal
Amarok 2.4.3

---

### Post by nickleboyblue on 2011-09-23
Have you had any problems with sound anywhere else?  Have you tried other music programs besides Amarock?  Does your hardware require specialized drivers?

---

### Post by Mega_Fauna on 2011-09-23
> **nickleboyblue said:**
> Have you had any problems with sound anywhere else?  Have you tried other music programs besides Amarock?  Does your hardware require specialized drivers?

Hi, thanks for your reply.

No, no other problems I've heard (yet).

NO specialized drivers, standard Aer Aspire laptop.

Yes, I have tried other programs but I'm on Linux because of Amarok, I don't want to switch to something lesser;)

---

### Post by KMKAR on 2011-09-23
Hi all. Here I'm having (in my guess) the same issue with these versions & laptop:
Ubuntu: v 11.04
Amarok: v 2.4.0
Device: Toshiba Satellite A505-s6005

All other software using the sound device works perfectly, but using Amarok (no matter which preset of equalizer I use) the sound is like garbage, with poor definition.

Any clues?

Thanks in advance!

---

### Post by Mega_Fauna on 2011-10-02
Bump!

---

### Post by Mega_Fauna on 2011-10-17
My solution was to install phonon-vlc (with Synaptic) and switch the backend to exactly that.

Settings
[INDENT]--> Configure Amarok[/INDENT]
[INDENT]--> [Playback][/INDENT]
[INDENT]--> [Configure Phonon][/INDENT]
[INDENT]--> tab: Backend[/INDENT]
[INDENT]--> Select 'VLC' and press [Prefer] to push it to the top of the list.[/INDENT]
[INDENT]--> [Apply][/INDENT]
[INDENT]--> [OK] out[/INDENT]
--> Probably restart Amarok 2, I can't remember.

Solution and more suggestions _[here]("http://forum.kde.org/viewtopic.php?f=116&t=97343&p=205497#p205497")_.

---

### Post by KMKAR on 2011-10-18
> **Mega_Fauna said:**
> My solution was to install phonon-vlc (with Synaptic) and switch the backend to exactly that.

Settings
[INDENT]--> Configure Amarok[/INDENT]
[INDENT]--> [Playback][/INDENT]
[INDENT]--> [Configure Phonon][/INDENT]
[INDENT]--> tab: Backend[/INDENT]
[INDENT]--> Select 'VLC' and press [Prefer] to push it to the top of the list.[/INDENT]
[INDENT]--> [Apply][/INDENT]
[INDENT]--> [OK] out[/INDENT]
--> Probably restart Amarok 2, I can't remember.

Solution and more suggestions _[here]("http://forum.kde.org/viewtopic.php?f=116&t=97343&p=205497#p205497")_.
You know.. That was one of my first tries to solve the poor audio quality, but it didn't worked for me. (Also I've tried some other Backends..)

Anyone else has some info about it?

Regards!

---

