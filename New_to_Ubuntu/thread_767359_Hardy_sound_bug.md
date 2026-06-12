---
title: "Hardy sound bug"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by piratesmack on 2008-04-25
Alright this bug isn't too annoying, but When running a music player like rhythmbox, I can't get sound in youtube videos.

Anyone know a fix or experiencing this?

---

### Post by hermes0710 on 2008-04-25
Same thing happens to me. What is your sound card? Might be hw problem.

---

### Post by piratesmack on 2008-04-25
> **hermes0710 said:**
> Same thing happens to me. What is your sound card? Might be hw problem.

Sounblaster Audigy SE I believe

Never had this problem with Gutsy

Maybe a bug with firefox 3 beta 5?

---

### Post by hermes0710 on 2008-04-25
No it's not. It's Alsa thing...

I just installed epiphany browser, same thing happend. Console output:

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

See: [https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089]("https://bugs.launchpad.net/ubuntu/+source/pulseaudio/+bug/202089")

---

### Post by piratesmack on 2008-04-25
> **hermes0710 said:**
> No it's not. It's Alsa thing...

I just installed epiphany browser, same thing happend. Console output:

```
ALSA lib pcm_dmix.c:874:(snd_pcm_dmix_open) unable to open slave
```

Yep I get the same output

---

### Post by Mazza558 on 2008-04-25
It's a bug in PulseAudio if I can remember the development forum for Hardy. It should be fixed for 8.04.1

---

### Post by PeterJS on 2008-04-25
This is a known issue woth flash and pulse audio, if you're on 32 bit you can install **libflashsupport** to make flash pulse audio aware. Howerver last I heard there were issues with libflashsupport on 64 bit machines which is why libflashsupport was pulled as a dependancy of flashplugin-nonfree in the latter days of the Betas.

---

### Post by hermes0710 on 2008-04-25
I reinstalled pulseaudio and it works now.

```
sudo apt-get install --reinstall pulseaudio
```

Make sure that there are not any instances of firefox/epiphany/amarok etc running (in broken state in the background).

Keep me posted

---

### Post by piratesmack on 2008-04-25
> **PeterJS said:**
> This is a known issue woth flash and pulse audio, if you're on 32 bit you can install **libflashsupport** to make flash pulse audio aware. Howerver last I heard there were issues with libflashsupport on 64 bit machines which is why libflashsupport was pulled as a dependancy of flashplugin-nonfree in the latter days of the Betas.

Awesome 

```

sudo apt-get install libflashsupport

```

Seems to have done it for me

---

### Post by piratesmack on 2008-04-25
hm so which fix should I use?

reinstall pulseaudio or install libflashsupport?

---

### Post by isaacj87 on 2008-04-25
> **piratesmack said:**
> hm so which fix should I use?

reinstall pulseaudio or install libflashsupport?

Try installing libflashsupport first. It may crash your browser more often. But it's a "pick your poison" type situation. :(

---

### Post by piratesmack on 2008-04-25
> **isaacj87 said:**
> Try installing libflashsupport first. It may crash your browser more often. But it's a "pick your poison" type situation. :(

Yeah that's the one I used

It doesn't seem to be causing problems so I guess I'll stick with it

---

### Post by alsamman on 2008-04-25
i got youtube and rhythmbox to work at the same time by installing libflashsupport. Now its only a matter of getting anything that uses sound to work with TuxGuitar:confused:

---

### Post by piratesmack on 2008-04-25
hm I guess libflashsupport is causing some problems

Sometimes when watching videos on youtube, firefox will close 

Output:

```

Segmentation fault

```

So I guess I'll try reinstalling pulse audio

---

### Post by dannytatom on 2008-04-25
Tell me how it goes, as I'd like to get this workin myself. :x

---

### Post by piratesmack on 2008-04-25
> **dannytatom said:**
> Tell me how it goes, as I'd like to get this workin myself. :x

hm I tried reinstalling pulseaudio with firefox, rhythmbox, and everything else closed, but it didn't seem to work. 

I guess I'll stick with the libflashsupport thing and deal with firefox crashing every once in a while

---

### Post by isaacj87 on 2008-04-25
> **piratesmack said:**
> hm I tried reinstalling pulseaudio with firefox, rhythmbox, and everything else closed, but it didn't seem to work. 

I guess I'll stick with the libflashsupport thing and deal with firefox crashing every once in a while

Yup. I guess that's all we can really do now. Firefox crashes, but not enough for me to be bothered. I'm sure the devs will come up with a solution soon enough :)

---

### Post by piratesmack on 2008-04-25
> **isaacj87 said:**
> Yup. I guess that's all we can really do now. Firefox crashes, but not enough for me to be bothered. I'm sure the devs will come up with a solution soon enough :)

oh well, I'm still impressed with Hardy

This is the only problem I've had with it so far

---

### Post by piratesmack on 2008-04-25
hm this libflashsupport thing is more unstable than I thought. I can't watch more than 3 youtube videos without it crashing. I think I might just uninstall it and not use rhythmbox while watching youtube videos

---

### Post by piratesmack on 2008-04-27
Update:
This bug doesn't seem to effect the 64bit version

---

### Post by crjackson on 2008-04-27
> **piratesmack said:**
> Update:
This bug doesn't seem to effect the 64bit version

So you are saying that flash plays fine with other audio apps. in a default Hardy install of Pulse audio?

---

### Post by piratesmack on 2008-04-27
> **crjackson said:**
> So you are saying that flash plays fine with other audio apps. in a default Hardy install of Pulse audio?

yep. I'm not exactly sure why, though

---

### Post by crjackson on 2008-04-27
> **piratesmack said:**
> yep. I'm not exactly sure why, though

Alright then, I guess I'll check out the 64-bit version later this week.  Thanks.

---

### Post by piratesmack on 2008-04-28
Useful tip:
Flash does stop responding every once in a while on the 64bit version of ubuntu, but this only seems to happen when you watch a like a series of youtube videos or something. It's completely tolerable and doesn't happen very often. I think this is because of nspluginwrapper. When it does stop responding, just open up a terminal and type:
```

killall npviewer.bin

```

Then the page will reload and firefox will start working again

---

### Post by salvador_luna on 2008-04-28
Having the same problem here.

But i wonder what version of firefox are you using?

I uninstalled firefox 3 because it crashes on my system too often, so i replaced it with firefox 2.

I'll try libflashsupport on it and post my results.

---

