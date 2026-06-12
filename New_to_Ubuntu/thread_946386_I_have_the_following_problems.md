---
title: "I have the following problems:"
date: 2008-10-13
forum: New to Ubuntu
---

### Post by Preturbed on 2008-10-13
Kubuntu on a laptop. I have a short list of problems that I'd like some help with.

[LIST=1]
[*]When I shut the laptop, the system attempts to hibernate/suspend depending on how it's set, but fails. Looks like it hangs up in terminal.
[*]No sound. I don't know what to do about this.
[*]**[COLOR="Red"]FIXED[/COLOR]** I installed KDE4 over KDE3, decided I didn't like it, then reverted back to KDE3. Now instead of coming up to the login screen, I have to login to terminal, type sudo kdm, login again from the kdm screen. I don't want to do this.
[/LIST]

Help please,
Preturbed

---

### Post by handydan918 on 2008-10-13
> **Preturbed said:**
> Kubuntu on a laptop. I have a short list of problems that I'd like some help with.

[LIST=1]
[*]When I shut the laptop, the system attempts to hibernate/suspend depending on how it's set, but fails. Looks like it hangs up in terminal.Hibernate/suspend is problematic with all flavors of Linux. It will be nice when this gets fixed, but for now it is still kinda complicated. > 
[*]No sound. I don't know what to do about this.Maybe you could post the output of ```
lspci | grep -i audio
```and lsmod | grep snd and maybe someone can see what you are dealing with.> 
[*]I installed KDE4 over KDE3, decided I didn't like it, then reverted back to KDE3. Now instead of coming up to the login screen, I have to login to terminal, type sudo kdm, login again from the kdm screen. I don't want to do this.
[/LIST]Perhaps you could either look thru, or post the contents of
```
/etc/init.d/kdm
```There are a few possibilities...> 
Help please,
Preturbed

---

### Post by hyper_ch on 2008-10-13
It is adviced to use a descriptive topic title, that means a topic title that gives some clue about the content in the thread itself...

A generic topic title like "noob here" or "need help" does not help at all. As you may have noticed, just about everyone posting in here has some kind of a problem or issue or question ;) 

And it is also adviced to use seperate threads for unrelated problems so that you can mark each one individually as solved.

Or in short terms: Help others to help you ;)

---

### Post by taqkavar on 2008-10-13
Agrre with the above guy, some of us here are behind slow connections.

> 
When I shut the laptop, the system attempts to hibernate/suspend depending on how it's set, but fails. Looks like it hangs up in terminal.

If you just don't want it to hibernate/suspend go to "System > Preferences > Power Management" and set the options for "when laptop lid is closed" in "On AC power" and "On Battery" to do nothing.

If you want to get hibernate/suspend to work, then tell us what laptop you use, and what is its graphic card.

---

### Post by OffAxis on 2008-10-13
> I installed KDE4 over KDE3, decided I didn't like it, then reverted back to KDE3. Now instead of coming up to the login screen, I have to login to terminal, type sudo kdm, login again from the kdm screen. I don't want to do this.
you should check

```
sudo dpkg-reconfigure kdm
```

and make sure it's set to 'kdm' instead of 'kdm-kde4'.

---

### Post by Preturbed on 2008-10-13
More info, more to come. OffAxis fixed my login problem. Here come the audio specs. 

00:1f.5 Multimedia audio controller: Intel Corporation 82801DB/DBL/DBM (ICH4/ICH4-L/ICH4-M) AC'97 Audio Controller (rev 03)

============

snd_intel8x0           35356  2
snd_ac97_codec        101028  1 snd_intel8x0
ac97_bus                3072  1 snd_ac97_codec
snd_pcm_oss            42144  0
snd_mixer_oss          17920  1 snd_pcm_oss
snd_pcm                78596  3 snd_intel8x0,snd_ac97_codec,snd_pcm_oss
snd_seq_dummy           4868  0
snd_seq_oss            35584  0
snd_seq_midi            9376  0
snd_rawmidi            25760  1 snd_seq_midi
snd_seq_midi_event      8320  2 snd_seq_oss,snd_seq_midi
snd_seq                54224  6 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_seq_midi_event
snd_timer              24836  2 snd_pcm,snd_seq
snd_seq_device          9612  5 snd_seq_dummy,snd_seq_oss,snd_seq_midi,snd_rawmidi,snd_seq
snd                    56996  15 snd_intel8x0,snd_ac97_codec,snd_pcm_oss,snd_mixer_oss,snd_pcm,snd_seq_dummy,snd_seq_oss,snd_rawmidi,snd_seq,snd_timer,snd_seq_device
soundcore               8800  1 snd
snd_page_alloc         11400  2 snd_intel8x0,snd_pcm


EDIT: Hey I found my graphics card that way too! Here's the grep thing from that.

00:02.0 VGA compatible controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)
00:02.1 Display controller: Intel Corporation 82852/855GM Integrated Graphics Device (rev 02)

---

