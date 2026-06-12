---
title: "How do i send MB beep from bash"
date: 2012-12-21
forum: Programming Talk
---

### Post by Drenriza on 2012-12-21
Hey guys.

I have a PC (_**ubunt 12.04 lts**_) where i have added a passive CPU cooler. On this PC i have installed sensors to see the CPU temp

```
sensors |grep temp
```

I then wanted to make a small bash script that checks every minut, to see what the temprature is. So it it reaches 60 celcius a motherboard beep (from the script) is played to notify me about the temprature.

But how does one send a MB beep from within bash? Is it even possible?

Or is their some other fancy program who can solve this in a easy matter.

Thanks on advance.
Kind regards.

---

### Post by haqking on 2012-12-21
```
sudo apt-get install beep
```

[http://manpages.ubuntu.com/manpages/hardy/man1/beep.1.html](http://manpages.ubuntu.com/manpages/hardy/man1/beep.1.html)

I am guessing this might do what you want

---

### Post by sudodus on 2012-12-21
So you want your computer to shout "Help, I'm getting too hot!"

That can be done in a little more fancy way using espeak

```
espeak "Help, I'm getting too hot"
```

Install from the repos

```
sudo apt-get install espeak
```

Or would you prefer a primitive beep, that would work without the speakers on? Then use haqking's ***beep***.

---

### Post by rnerwein on 2012-12-21
> **sudodus said:**
> So you want your computer to shout "Help, I'm getting too hot!"

That can be done in a little more fancy way using espeak

```
espeak "Help, I'm getting too hot"
```Install from the repos

```
sudo apt-get install espeak
```Or would you prefer a primitive beep, that would work without the speakers on? Then use haqking's ***beep***.
hi
beep don't work on my box - audio connected.
but thanks for the hint of espeak - haven't know it before ( 12.04 LTS it is installed by default). espeak works on my box - even when music is playing.
cheers :p

got a couple of errors:
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib audio/pcm_bluetooth.c:1614:(audioservice_expect) BT_GET_CAPABILITIES failed : Input/output error(5)
ALSA lib pcm_dmix.c:957:(snd_pcm_dmix_open) The dmix plugin supports only playback stream
ALSA lib pcm_dmix.c:1018:(snd_pcm_dmix_open) unable to open slave
Cannot connect to server socket err = No such file or directory
Cannot connect to server socket
jack server is not running or cannot be started

but it don't hassle me - it works

---

### Post by sudodus on 2012-12-21
> **rnerwein said:**
> hi
beep don't work on my box - audio connected.
but thanks for the hint of espeak - haven't know it before ( 12.04 LTS it is installed by default). espeak works on my box - even when music is playing.
cheers :p

got a couple of errors:
...
but it don't hassle me - it works

The same for me. I redirect the error output to /dev/null.

Maybe you'd be interested in the german voice:

```
espeak -v de "Ach du lieber Augustin" 2>/dev/null
```

---

### Post by drmrgd on 2012-12-21
> **sudodus said:**
> So you want your computer to shout "Help, I'm getting too hot!"

That can be done in a little more fancy way using espeak

```
espeak "Help, I'm getting too hot"
```

Install from the repos

```
sudo apt-get install espeak
```

Or would you prefer a primitive beep, that would work without the speakers on? Then use haqking's ***beep***.

Ha!  This is awesome (or I'm just easily amused).  I've wasted the last 15 minutes or so playing with this, making my computer say all kinds of crazy things.  Not sure how much it helped the OP, but it sure made my night!  :D

---

### Post by haqking on 2012-12-21
> **drmrgd said:**
> Ha!  This is awesome (or I'm just easily amused).  I've wasted the last 15 minutes or so playing with this, making my computer say all kinds of crazy things.  Not sure how much it helped the OP, but it sure made my night!  :D

I know i did the same earlier, I can confirm there is no adult filter....LOL

---

### Post by pqwoerituytrueiwoq on 2012-12-21
you could record a wav file to use google text to speach and play hte audio file with the aplay command

---

### Post by slavik on 2012-12-22
in C:
```

printf("\a");

```

---

### Post by RaumTrug on 2012-12-23
maybe you'll want to modprobe the module "pcspkr" to make "beep" or "\a" work. Or remove it from blacklist. occasionally other progs might beep then, too, which can be annoying and is reason for why it is blacklisted by default. more modern pc's might work differently with the beeper (i.e. route it via soundcard, so mixer levels might need to be set with alsamixer).

"aplay" is also an option, in case you want the sound via your soundcard - just feed it with a .wav of something annoying that you won't overhear.

---

