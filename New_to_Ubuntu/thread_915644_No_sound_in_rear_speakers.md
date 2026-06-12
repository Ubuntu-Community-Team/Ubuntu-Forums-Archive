---
title: "No sound in rear speakers"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by roscal on 2008-09-10
Well, Ive googled and searched this forum, to no avail.

Rear speakers aren't working after a fresh install of Hardy.

They worked in Feisty, and also work in Windows.

I'm using on board audio with a new motherboard.

The options in the mixer are somewhat limited now, much less than before I 'upgraded'. I have the audio set to auto detect if that means anything.

The mixer now seems to be K mixer.

I jacked up all the limited available options in Alsa, through the Terminal.

Any help is welcome thanks.
Maybe I need a sound card????
Thanks for any help.

---

### Post by skippuff54 on 2008-09-10
are ur speakers hooked directly to the soundcard or do u use a stereo with receiver?

maybe u need to try another driver for ur soundcard. what kind of soundcard do u have? see if anyone else is havin issues with it (search forums).

what kind of tasks are u usin ur soundcard for? just music playback, audio mixing? cause u might want to try different media players or mixing software.

---

### Post by roscal on 2008-09-10
The speakers are hooked up to on board audio, on a new 
**GeForce7050M-M** , motherboard, using the on board audio connectors.

The speakers are a couple of years old.. Logitech 5.1 setup.

There seems to be a lot less options to mess with in the mixer (K Mix), than before I changed this MB and upgraded to Hardy.

Maybe I'm missing something in setting it up, or the MB audio is indeed, the villian?
Thanks....

---

### Post by skippuff54 on 2008-09-10
sounds like u r only gettin 2 channel sound for some reason. see if u can find another mixin program (or several) besides kmix...search the forums for fixin progs or just use s/kynaptic

another issue could be ur sound drivers. seems like u'll need drivers that tell the computer to deliver 5.1 channels of sound rather than the normal two. also search for what u can find about 5.1 channel sound in terms of ur card and MB, and make sure ur hardware specs list multiple channel output

try out some add'l software first. sounds like u have higher demands than the avg user and might benefit from another piece of software

---

### Post by roscal on 2008-09-10
Speakers are hooked directly to the MB.
No external stereo is connected.

I have tried XMMS (audio), VLC (video), Amarok, Kaffine and others,.. **no sound in rear speakers**.

The mixer (now KMix) has limited option controls for some reason:

Master
PCM
Front
Front Mic
Line
Mic

That's it, thats all I have to play with.

As I mentioned, I also entered alsamixer in Terminal, and jacked up the available options.

Basically, I'm getting stereo sound, but no sound out of the rear speakers, or 5.1 audio, is available.

---

### Post by skippuff54 on 2008-09-10
r u sure alsa supports ur card and its chipset? u googled and searched forums for this right? cause i just typed ubuntu 5.1 sound in google a couple of relevant items popped up though i didn't notice ur card specifically.

one highlight from [http://jafferhaider.wordpress.com/2007/02/20/getting-51-on-your-ubuntu-step-by-step-for-intel-865gbf/]("http://jafferhaider.wordpress.com/2007/02/20/getting-51-on-your-ubuntu-step-by-step-for-intel-865gbf/") > I found out that 5.1 is by default muted in Ubuntu (at least it was for me). Even after I installed the ALSA drivers, I wasn’t getting surround sound, and so that’s when I double clicked the volume control, went to Edit > Preferences, and enabled the following components:
Master Surround
Surround
Center
PCM
Make sure you have these sounds unmuted, or else you can install all the drivers you want, you won’t get a squeak out of your subwoofer, center and rear channels.

If doing that doesn’t fix your problem, then I present the procedure that I followed while installing the ALSA package (drivers, lib and utils).

First you need to go to the ALSA Soundcard Matrix and pray to the soundcard gods that ALSA supports your card. Use the list of Vendors near the bottom to search for your card. You can find the chipset name of your card by going in System > Preference > Sound. It’ll be one of the entries in the dropdown list of drivers

other than that i'd say look in the hardware forums...i think u know what u're doin, sounds like somethin specific to ur card

---

### Post by roscal on 2008-09-10
Thanks for your replies Skip.
No luck for me though.
I'm stuck with Kmix and limited input/output options.
Using Kubuntu btw.

---

### Post by skippuff54 on 2008-09-10
anytime, wish i knew more to tell ya. the last items i can offer up are to search sourceforge.net for any more robust mixin progs that might be out there....or u could always try ubuntu, gnome desktop 

either way good luck to ya, post back if u figure somethin out

---

### Post by sandeep108 on 2008-12-09
Sorry to resurrect this old thread. 

I seem to have the same problem. After upgrading (new install to 8.10) NO surround sound. Alsa mixer detects the sound card fine, I select all the Center, surround, 3d, etc. all enabled and maxed out, but NO surround, center, LFE or anything is playing, except the front two speakers.

I had no problem with 7.04. The sound worked perfectly.

Anybody can help in getting back my surround in 8.10? I have an Audigy2 ZS connected to a 5.1 system.

---

### Post by sandeep108 on 2009-01-02
Bump... anybody help in getting surround sound in 8.10? I updated everything including some pulse audio stuff. But no joy...

---

### Post by sandeep108 on 2009-01-17
Well, after playing around a bit, selecting multi-channel playback does the trick. However the sound stuttered terribly. After another update today, it is much better, but there is still some stuttering, which is not there if I select normal Alsa mixer.

Is this being experienced by others? Any way to get around this?

---

### Post by TekNullOG on 2009-01-25
Where do you activate multi-channel playback?

---

### Post by sandeep108 on 2009-01-26
Preferences>Sound>Playback - instead of auto detect, in the drop down menu I get several choices.

---

