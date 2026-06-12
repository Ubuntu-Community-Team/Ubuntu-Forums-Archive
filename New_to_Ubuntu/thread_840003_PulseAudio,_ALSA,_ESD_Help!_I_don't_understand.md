---
title: "PulseAudio, ALSA, ESD?? Help! I don't understand"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by raccoonone on 2008-06-25
I've been having various sound problems, and they seem to be related to the fact that there are several different sound (drivers?). If I have Amarok set to use PulseAudio (the default) and Pidgin set to use ALSA, I get no sounds from Pidgin if I'm playing music in Amarok. However, after setting them both to use ALSA they're working just fine together. Can someone explain what the difference is, and when I should be using which one? I also seem to be having a problem with some programs (namely VLC) being really quiet. Do I need to set VLC to use ALSA too?

*edit*
I've been having sound issues with programs that run through Wine too. And it was suggested that I remove all the PulseAudio libraries. Is that safe to do? I tried to remove them, but it said I would need to remove Amarok and VLC, as well as ubuntu-desktop. Can I get rid of PulseAudio and keep Amarok?

---

### Post by Methuselah on 2008-06-25
Everything should be able to go through pulseaudio.
The point is for pulseaudio to be the gatekeeper so that no program grabs on to the sound hardware exclusively.

---

### Post by raccoonone on 2008-06-25
Thanks. How do I get Pidgin to work with PulseAudio then? If I have Amarok set to pulseaudio then I get no sound out of Pidgin.

---

### Post by Methuselah on 2008-06-25
It's difficult for me to give you direct advice on your setup.
But please try this page:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

It offers some hints on how to setup pulseaudio to work perfectly with Amarok and ESOUND application among other things. 
It helped me rectify some problems I had with skype at one point.

---

### Post by raccoonone on 2008-06-25
Thanks! Following the directions to make ALSA use PA seems to have fixed the issues with Pidgin. I still have trouble with Wine, any suggestions there? I tried the pasuspender command, but that doesn't seem to have helped.

---

### Post by Methuselah on 2008-06-25
What are your problems with wine?
Is an audio driver configured there?

Launch winecfg in a terminal or Wine->Configure Wine from the menus and select the audio tab and see what's selected. 
Just try the Alsa driver first, that's what wine should select by default anyway.  
IIRC, I am able to get sound from wine programs that otherwise work.

---

### Post by raccoonone on 2008-06-25
I have the ALSA driver selected in winecfg. I have Winamp (Lite) and AIM installed, and neither has sound. I also just tried installing foobar2000, and it has no sound either.

---

### Post by Methuselah on 2008-06-25
I have to do some further experiments with my setup to see if I'm ok here.

---

### Post by Methuselah on 2008-06-25
Sound works fine for me.
ALSA drivers selected.

```

wine --version

```

is 1 and everything is pretty much vanilla Hardy.

---

### Post by raccoonone on 2008-06-25
Yep, I have version 1.0 also. Did you test AIM 5.9 or Winamp on your computer?

---

### Post by Methuselah on 2008-06-25
> **raccoonone said:**
> Yep, I have version 1.0 also. Did you test AIM 5.9 or Winamp on your computer?

I tested some youtube videos in firefox running in Wine.

---

### Post by raccoonone on 2008-06-25
> **Methuselah said:**
> I tested some youtube videos in firefox running in Wine.

I finally got my sound working with Winamp, but I still can't get AIM to work. I followed this guide, if anyone else has a similar issue to me: <http://blog.paulbetts.org/index.php/2007/05/27/make-wine-and-pulseaudio-get-along/>

---

### Post by Methuselah on 2008-06-26
BTW, Pidgin in native linux should be an alternative to AIM.
Not sure if you knew or just preferred AIM.

---

### Post by raccoonone on 2008-06-26
Yes, I know. But Pidgin doesn't support AIM Expressions, and I haven't been able to find any other linux IM client that does. So I've been trying to get AIM to work via Wine.

---

