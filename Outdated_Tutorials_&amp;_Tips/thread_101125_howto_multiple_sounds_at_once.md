---
title: "howto multiple sounds at once"
date: 2005-12-09
forum: Outdated Tutorials &amp; Tips
---

### Post by ubuntu_demon on 2005-12-09
howto multiple sounds at once in Ubuntu Breezy (Gnome) including working sound in almost all games and system sounds.

thnx to the user intangible and the wiki I was able to compile this howto.

This guide is on your own risk(although there isn't much risk involved). I advise making backups of the files you edit. I'm posting this guide as a forum user and not as a staff member. 

If you don't have any sound at all you may need other modules to get your sound working properly. Please search for your (sound) chipset / motherboard in the video & sound section : [http://ubuntuforums.org/forumdisplay.php?f=114](http://ubuntuforums.org/forumdisplay.php?f=114) Also look at the links I give at the end of this post. If you still have problems after that please start a new thread in the video & sound section and at least post your $ lspci 

If you don't know what sound card or audio chipset you have do :

```
$ lspci
```

and look for a line with a words like audio/multimedia/sound

ac'97 : this esd guide works
other chipsets/soundcards on which esd works : this esd guide will probably work
other chipsets/soundcards on which esd doesn't work : try alsa 
audigy2 : try alsa (see below for more on audigy 2)

This guide consists of three parts : oss,esd,alsa. Everyone do the oss part and do either the esd or the alsa part.

**Let's start with oss :**

intended audience : everyone

First make sure ubuntu is installed properly:

```
$sudo apt-get install ubuntu-base ubuntu-desktop
```

This will install alsa-oss. oss is needed for sound in a lot of games :

```
$sudo apt-get install alsa-oss
```

You will probably need this module for oss :

```
$sudo modprobe snd_seq_oss
```

If the modprobe didn't give an error make sure it gets loaded with each boot :

```
$ sudo pico /etc/modules
```

and add this line : 
```
snd_seq_oss
```

OSS stuff (mostly games) will still tie up the sound card, but they don't run all the time. Just configure most things to use esound/esd and you'll be good. 

**esd :**

intended audience : esd works but multiple sounds at once doesn't work properly. I tested this guide on a couple of machines. But for some soundcards / motherboards alsa is the better choice.

Ubuntu uses a program called esd to allow multiple applications to access the sound card at one time. However, many third party applications not in Ubuntu main aren't designed to use esd to access the card. On some sound cards, this causes these applications to not produce sound. To work around this problem, esd must be configured to release the sound card when it is not using it. Place the following in your /etc/esound/esd.conf:

```
$sudo gedit /etc/esound/esd.conf
```

and make it look like this :

```

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

```

```
$sudo gedit /etc/libao.conf
```

and make it look like this :

```

default_driver=esd

```

Now go to system->preferences->sound
-make sure system sounds are enabled
-enable sound server startup
-enable sounds for events
-system bell > sound an audible bell

safe all your open work. ctrl-alt-backspace to restart gdm.

Try if everything works. If a program doesn't have sound make sure it uses esd/esound.

You can try to "route" the sound of some program for example applicationx to esd using this command :
$esddsp *applicationx*

If you don't have multiple sounds (and it isn't an application which can't use esd which is blocking everything) try alsa.

**alsa :**

intended audience : esd doesn't work at all or the esd multiple sounds guide above didn't work (good enough)
drawback : no system sounds

Follow the instructions in this thread :
[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)

You can try this if it doesn't work :

```
$sudo gedit /etc/esound/esd.conf
```

and make it look like this :

```

[esd] 
auto_spawn=0
spawn_wait_ms=100
default_options= -terminate -nobeeps -as 2

```

**audigy 2 :**

Do the OSS and ALSA part of the guide.

[quote=wiki.ubuntu.com/DebuggingSoundProblems]
If you have ALSA set up with an Audigy 2 and everything "should" be working according to the manual, there is a chance that the following will fix it:

Run 'alsamixer'. If you have multiple cards, run it for the appropriate card, like in my case 'alsamixer -c 1'

Browse the channels until you find the "Analog/Digital Output Jack" and press 'M' to enable it if it's disabled
[/quote]

**some links :**
[https://wiki.ubuntu.com/DebuggingSoundProblems](https://wiki.ubuntu.com/DebuggingSoundProblems)
[http://www.ubuntuforums.org/showthread.php?t=44753](http://www.ubuntuforums.org/showthread.php?t=44753)
[https://wiki.ubuntu.com/SoundProblemsHoary](https://wiki.ubuntu.com/SoundProblemsHoary)

---

### Post by BoyOfDestiny on 2005-12-09
I want to confirm that if you have an Audigy2, alsa is the better choice. I can run literally dozen of apps producing sound (although I normally don't... but to test), so I'm guessing it's using hardware mixing...

Just grab alsa-oss and in multimedia selector set alsa as the out...

---

### Post by ubuntu_demon on 2005-12-09
[QUOTE=BoyOfDestiny]I want to confirm that if you have an Audigy2, alsa is the better choice. I can run literally dozen of apps producing sound (although I normally don't... but to test), so I'm guessing it's using hardware mixing...

Just grab alsa-oss and in multimedia selector set alsa as the out...[/QUOTE]
thnx for the input!

---

### Post by lysis on 2005-12-13
I myself have an Audigy 1.

I want to use a program called TeamSpeak2RC2 (full duplex microphone prog for speaking with other people VOIP) and Enemy Territory (RtCW Engine Based Game) at the same time. TS if I recall is OSS. I have an ALSA wrapper installed from synaptic that allows my audigy to use TS properly using ALSA.  How can I get them both making sound at the same time?  I do have onboard sound, but if that's enabled I do  not have the ability to use my sound wheel on my keyboard anymore (mundane thing to worry about but i use it a lot . . .)

---

### Post by ubuntu_demon on 2005-12-13
[QUOTE=lysis]I myself have an Audigy 1.

I want to use a program called TeamSpeak2RC2 (full duplex microphone prog for speaking with other people VOIP) and Enemy Territory (RtCW Engine Based Game) at the same time. TS if I recall is OSS. I have an ALSA wrapper installed from synaptic that allows my audigy to use TS properly using ALSA.  How can I get them both making sound at the same time?  I do have onboard sound, but if that's enabled I do  not have the ability to use my sound wheel on my keyboard anymore (mundane thing to worry about but i use it a lot . . .)[/QUOTE]

That's still an unsolved problem at least when doing it on one soundcard/sound chip. AFAIK currently the best way to solve it is to use one sound card/chip for enemy territory and the other one for VOIP.  So in other words you might be able to use the audigy for ET and the sound chip for VOIP.

Try searching on the forum for a more specific answer.

---

### Post by whyameye on 2005-12-18
After trying various solutions to the "multiple sounds at once" problem I finally found what I feel is the best solution: jackd and with oss2jack. No other solution that I know of (including the ones provided in this thread) allow multiple oss apps to share sound simultaneously. As oss is still the defacto standard and many apps work only with oss (for example, Audacity), oss2jack and jackd is really your only solution if you don't want to have to be aware of what interface your app needs etc. I followed the directions for installing oss2jack here: [http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html). Going this route, your ALSA, JACK, and OSS apps all play with each other nicely simultaneously. You also get the benefits of low latency and professional flexibility with JACK.

I recommend installing realtime-lsm for the low latency, and use qjackctl when first playing with JACK for tweaking.

---

### Post by ubuntu_demon on 2005-12-19
[QUOTE=whyameye]After trying various solutions to the "multiple sounds at once" problem I finally found what I feel is the best solution: jackd and with oss2jack. No other solution that I know of (including the ones provided in this thread) allow multiple oss apps to share sound simultaneously. As oss is still the defacto standard and many apps work only with oss (for example, Audacity), oss2jack and jackd is really your only solution if you don't want to have to be aware of what interface your app needs etc. I followed the directions for installing oss2jack here: [http://fort.xdas.com/~kor/oss2jack/install.html](http://fort.xdas.com/~kor/oss2jack/install.html). Going this route, your ALSA, JACK, and OSS apps all play with each other nicely simultaneously. You also get the benefits of low latency and professional flexibility with JACK.

I recommend installing realtime-lsm for the low latency, and use qjackctl when first playing with JACK for tweaking.[/QUOTE]
thnx for the info!

I'll look into it when I have time. Multiple oss applications doesn't happen very often but it happens (primarily with games).

Have you tried combining the howto from this thread with the oss2jack howto ? Since not every application is able to use oss.

---

