---
title: "A Hardy Sound Problem"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by HebrewTheHammer on 2008-05-19
Dear Ubuntu community.

I recently tried to dual boot windows and my mother board fried. coincidence? i think not. My fault, i will not falter(by thinking i need windows) again.

Anyway...4 mother boards later i was able to run my computer of my old hard drive using my old existing Ubuntu. Gutsy. i encountered no problems but only used it for a day before i updated to Hardy.

Now that i have updated to hardy i am having trouble with my sound.


<BEEF>

Whenever i boot my computer my sound works fine on normal application(E.G.) rythembox  Mplayer etc.

however when i use the internet and watch videos on the internet...my sound then only works for videos on the internet.(particularly HD flash videos and youtube)

my sound ceases to work on regular application until the next reboot.

</BEEF>

Now. I understand that  new mother boards with old hard drives is typically a No-No. but did not encounter any problems before my update.

so im not sure if it is my mother board/hard-drive or if it my update to Hardy.

thanks for the help 

-The Hebrew Hammer-

---

### Post by meborc on 2008-05-19
i would bet the problem is in PulseAudio (it is included by default in hardy and it wasn't in gutsy)... there is more info in it here [https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)

i can't help you though as everything works fine here... but maybe you now know where the culprit is ;)

---

### Post by joshsmith on 2008-05-19
the answer is to install the package libflashsupport
it wasnt installed by default as it makes firefox slightly more crashy (a solution is in the works right now)

---

### Post by legrandyon on 2008-05-19
Hi,
I had the same sound problems and I confirm that the method is to follow the installation explained in 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
(Note that for the 8.04, to change the network preferences in Pulse Audio, you need to click application > Sound & video > Pulse Audio device chooser, which launches it, and then click the icon, and choose "Configure local sound server")
and the installation of the libflashsupport with synaptic (need to restart firefox afterwards). Now multiple sound sources work well together.

One program still doesn't work though : realplayer. I had just installed a new beta version that uses Alsa that hardly worked (keep rebuffering). Now it doesn't work at all (and unfortunately, my favourite radio station uses this format :(  ). Any idea to fix that or to use something else to stream the files of that format ?
Thanks in advance.
LGY

---

### Post by HebrewTheHammer on 2008-05-19
> **legrandyon said:**
> Hi,
I had the same sound problems and I confirm that the method is to follow the installation explained in 
[https://wiki.ubuntu.com/PulseAudio](https://wiki.ubuntu.com/PulseAudio)
(Note that for the 8.04, to change the network preferences in Pulse Audio, you need to click application > Sound & video > Pulse Audio device chooser, which launches it, and then click the icon, and choose "Configure local sound server")
and the installation of the libflashsupport with synaptic (need to restart firefox afterwards). Now multiple sound sources work well together.

One program still doesn't work though : realplayer. I had just installed a new beta version that uses Alsa that hardly worked (keep rebuffering). Now it doesn't work at all (and unfortunately, my favourite radio station uses this format :(  ). Any idea to fix that or to use something else to stream the files of that format ?
Thanks in advance.
LGY

OK

is there any other way for this to work.

cause i am now thinking of just going back to gutsy.

frost wire doesn't work now
and i still have to redo all my other sources for all my other stuff and i just isn't even seeming worth it

is there anyway to make it run like it did on gutsy. (sound that is)

---

### Post by efffourthirty on 2008-08-19
Wow, following that Pulseaudio guide worked great on my machine.  Even in a from scratch install, I was having performance issues everywhere even with a good video card.  Firefox was crashing my Virtualbox, resizing windows was choppy and flash sound was inconsistent.

Now everythings great.

Corey Thomas

---

### Post by hitman1985 on 2008-08-19
but what if ur about to use skype or something like that and the super pulse audio just messes up everything ?

is there a fix to get rid of all the pulseaudio stuff again ?

i was runing everything fine but only one app sound, but every sound worked, now that i have pulse audio installed, no sound for skype, and a crappy microphone noise on most programs!

there we go again :( i m starting to go nuts about this problem!

---

### Post by efffourthirty on 2008-08-19
> **hitman1985 said:**
> but what if ur about to use skype or something like that and the super pulse audio just messes up everything ?

is there a fix to get rid of all the pulseaudio stuff again ?

i was runing everything fine but only one app sound, but every sound worked, now that i have pulse audio installed, no sound for skype, and a crappy microphone noise on most programs!

there we go again :( i m starting to go nuts about this problem!

I did have trouble with Skype but following this guide worked:

[http://www.pulseaudio.org/wiki/PerfectSetup](http://www.pulseaudio.org/wiki/PerfectSetup)

It list setup procedures for several popular applications.

Corey Thomas

---

### Post by hitman1985 on 2008-08-19
thx, i bet thats helpfull to most people, 

i got my skype working right now, just a bad microphone quality what sounds similar to the way that you dont have bandwith, kinda squeek in sqeek out something like that, but all the general tutorials just get me confused, so im leavin it like it is :)

---

