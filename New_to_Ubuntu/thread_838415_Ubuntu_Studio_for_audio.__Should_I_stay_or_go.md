---
title: "Ubuntu Studio for audio.  Should I stay or go???"
date: 2008-06-23
forum: New to Ubuntu
---

### Post by jukingeo on 2008-06-23
Hello all,

I have been over a month on Ubuntu as of now and last week I upgraded to Ubuntu Studio

What I mainly want to do is use a Linux distribution for:

1) Audio and Video recording and editing
2) Games, mainly console emulations (Atari 2600, NES, Sega Genesis, Dos games, etc).  But I would like to try out Linux games as well.
3) Internet Surfing (streaming audio/video a must).
4) Standard email, letter writing tasks.

In a nutshell I want to do everything that I can do in Windows XP.  While I know that may not be entirely possible, I do want to accomplish the above four things.

Since having Ubuntu, I been having much trouble getting my Sound Blaster X-Fi sound card to work properly in Ubuntu.  This sound card seems to only accept OSS.   Ubuntu Studio seems to prefer the newer ALSA system which does make my life a bit more difficult in configuring my machine.   This is what has happened over the course of the past few weeks:

I had to install OSS twice on my machine.  The first time none of my games worked and I had to install Pulse Audio as an overlay.  This knocked out my streaming internet.  When I found a fix and performed it, it knocked out my sound completely.  This was due to the fact that the fix was for ALSA and not OSS.

So I removed everything (soundwise) from my machine and started over.  I loaded up OSS again (a new version was issued in the interim) and most of my sound is working (without the need for Pulse).  However, there were a few things that still didn't work and my streaming internet is still down.  None of the Ubuntu Studio applications I can get running with sound as of now.

In the course of attempting to fix these issues, I came to wonder that perhaps maybe I am barking up the wrong Linux distribution tree in the first place.   Sure Ubuntu Studio is made for audio recording and editing...but it is also fairly new?

I found this website:

[http://linuxrockstar.blogspot.com/2006/08/quick-linux-audio-distribution-guide.html](http://linuxrockstar.blogspot.com/2006/08/quick-linux-audio-distribution-guide.html)

I see that of the distro's on the list, Ubuntu Studio isn't even on it (granted the list is from 2006).

I am curious if anyone is in the same boat as I am that wanted to use Ubuntu (mainly) for games and audio editing work, but perhaps found one of these other distributions easier to work with?

SuSE JackLab and Musix sound like promising distributions.

But basically I would like the honest opinion from someone who has used these distributions (or any other on the list) and compared it to Ubuntu Studio.

Is there that much of a difference between the distro's?  If so, what?  Would it be a good idea for me to switch?  Or should I stay with Ubuntu Studio?

All in all while I like Ubuntu and Ubuntu Studio, I am finding that getting something as simple as my sound card to operate properly with everything is turning into a big massive migraine headache.

As always, I appreciate any advise or suggestions.

Thank You,

Geo

---

### Post by phidia on 2008-06-23
Have you looked at the sound troubleshooting guide [here]("http://ubuntuforums.org/showthread.php?t=205449")?
I used suse and too many other distros. There are legitimate reason to look for a different distro but if you have only been using linux for a short time I'm not sure switching will be a real solution-maybe though?
There is no perfect distro anyway-IMO there is only a disto you can live with.
The sound problem is probably resolvable check the link I provided and a good alternative place to find answers is at [linuxquestions]("http://www.linuxquestions.org/"). They have a hardware database there too and if that card won't work perhaps you can replace it with one that is more supported? (A PCI slot audio card)
Hope that's helpful.

---

### Post by markbuntu on 2008-06-23
Pulseaudio has just become a nightmare for many people. And if you are using Ubuntu Studio for recording it is the last thing you need since it puts another layer of management on top of your sound environment and can increase latency etc.

Just use alsa and get the alsa-oss wrapper for your oss apps and all the alsa-plugins for jack and oss etc. You shouldm have all the jack stuff already, you just need to configure it to work with alsa and your sound card.

There are a number of discussions about this in the Multimedia Production forum which is more about what you want to do than the stuff in the other forums.

---

### Post by jukingeo on 2008-06-23
> **phidia said:**
> Have you looked at the sound troubleshooting guide [here]("http://ubuntuforums.org/showthread.php?t=205449")?
I used suse and too many other distros. There are legitimate reason to look for a different distro but if you have only been using linux for a short time I'm not sure switching will be a real solution-maybe though?
There is no perfect distro anyway-IMO there is only a disto you can live with.
The sound problem is probably resolvable check the link I provided and a good alternative place to find answers is at [linuxquestions]("http://www.linuxquestions.org/"). They have a hardware database there too and if that card won't work perhaps you can replace it with one that is more supported? (A PCI slot audio card)
Hope that's helpful.

Hmmm, I guess I do have to fill you (as well as everyone) with a few more details.  My system is a dual boot right now so I can use both Windows XP and Ubuntu.  The thing was that I wasn't without my issues with setting up the Sound Blaster X-Fi on my system through Windows.  In fact something went wrong with my first attempt and I had to do an entire reinstall of Windows XP.  Then I was smart and configured the Soundblaster X-Fi FIRST before adding anything else back on the machine.

Luckily since that mishap I have not had a single problem with the Soundblaster X-Fi with Windows XP.  So when it comes to this system I am very reluctant to change the sound card.  In fact I more then likely will never do it.

Will I eventually have a full Linux system?  Yes, but for now I am determining the feasibility of whether I should move forward with Linux (with the idea of leaving Windows XP behind). The big determining factor would be to check out the applications such as Audacity, Ardour, Rosegarden...etc.  However, as you can see that is where the dilema lies.  Since I am having trouble with the X-Fi sound card in Ubuntu and I have no sound, I cannot check out the applications.

But if you are saying the other distro's are "just as bad" as Ubuntu (Studio), then obviously I will stay here as supposedly the support is greatest on this distribution of Linux.

The only other thing then is that I need SOME kind of sound. However as it seems that ALSA is the way to go over OSS.  But yet I am not willing to tear my machine apart and put another sound card in the HOPES that it will work.  What I would fear most is that the presence of another sound card would disturb my Windows XP settings for the X-fi card.  Naturally, that is not an option (at least on this machine).

The only way I would put another sound card on this machine that is more compliant with Ubuntu's ALSA configuration, would be through an external USB sound card.  If I have to switch my speakers going from Windows to Ubuntu, then so be it.

Now the question I have is there a USB external sound card that will work with ALSA in Ubuntu?

Thanx,

Geo

---

### Post by jukingeo on 2008-06-23
> **markbuntu said:**
> Pulseaudio has just become a nightmare for many people. And if you are using Ubuntu Studio for recording it is the last thing you need since it puts another layer of management on top of your sound environment and can increase latency etc.

Just use alsa and get the alsa-oss wrapper for your oss apps and all the alsa-plugins for jack and oss etc. You shouldm have all the jack stuff already, you just need to configure it to work with alsa and your sound card.

There are a number of discussions about this in the Multimedia Production forum which is more about what you want to do than the stuff in the other forums.

As of now I don't have Pulse on my system.  Apparently when I had a problem the first time around with the OSS driver and Pulse, I ended up removing it all and starting from scratch.  During this time a new version of OSS was released and this time I was able to get sound on most of my applications WITHOUT putting Pulse back on.  So as I did point out, if I don't need it, I am NOT going to put it back on.

What you suggest about a "wrapper" was pretty much what I was looking for.

More then half my problems with checking out the Ubuntu Studio programs is that the applications go through Jack...of which I don't know anything about.  I did read a document in which that the hind end of Jack could be patched through to my sound card using OSS.  So that did get me to thinking that I could probably use my Ubuntu Studio applications with ALSA, up to the point of Jack...then Jack can talk to my sound card via OSS.  So yes, I believe that would work.  However, thusfar quite a few things went wrong with attempting to set up sound in Ubuntu.   To be frank, it has been a royal pain in the A$$.

So, how does this "wrapper" work and where do I get?

Finally, where is a good guide on how to use Jack?  The Jack website isn't exactly overflowing with information on it, let alone how to configure it.

Thanx,

Geo

---

### Post by markbuntu on 2008-06-23
Check with Synaptic that these are all installed:

aconnectgui  (ALSA MIDI connection utility)
alsa-oss  (alsa wrapper for OSS apps)
alsaplayer-alsa  (PCM player for alsa)
alsa-utils  (command line utilities)
asoundconf-gtk  (choose default alsa sound card)
gnome-alsamixer (GUI alsa mixer for Gnome)
gstreamer0.10-alsa (gstreamer plugin)
xmms2-plugin-alsa (xmms2 plugin)
libasound2-plugins (jack, OSS, pulseaudio)
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device)

Then search for jack with synaptic or use the add remove function in the menu and get jackcontrol and jackeq and patchage and anything else that looks promising. Then you can use jackcontrol to set up jack. Try doing a google search for jackd and look for the wiki.

As I said, there are a lot of threads about recording, editing, setting up and using jack, etc in the Multimedia Production Forum. You should really pay it a visit.

About getting your Soundblaster X-Fi to work. Go to the top page of the forums and use the search function from there, that way your search will look in all the forums instead of just here. I am sure someone around here has got it working and you can find out how they did it.

---

### Post by jukingeo on 2008-06-23
> **markbuntu said:**
> Check with Synaptic that these are all installed:

Ok, these are my findings:

aconnectgui  (ALSA MIDI connection utility) ---Yes
alsa-oss  (alsa wrapper for OSS apps)   ---Yes
alsaplayer-alsa  (PCM player for alsa)  ---No, what does it do?
alsa-utils  (command line utilities)    ---Yes 
asoundconf-gtk  (choose default alsa sound card) ---No, what does it do?
gnome-alsamixer (GUI alsa mixer for Gnome)  ---No, what does it do?
gstreamer0.10-alsa (gstreamer plugin)  ---Yes
xmms2-plugin-alsa (xmms2 plugin)  ---No, What does it do?
libasound2-plugins (jack, OSS, pulseaudio) ---Yes
libesd-alsa0 Enlightened Sound Demon (allows  multiple audio streams on one device) ---Not even on Synaptic List

I didn't install anything yet.  I figure I would check back with you to find out what some of these things do.

> Then search for jack with synaptic or use the add remove function in the menu and get jackcontrol and jackeq and patchage and anything else that looks promising. Then you can use jackcontrol to set up jack. Try doing a google search for jackd and look for the wiki.

Yes, I have most of what you mentioned above.  I did download and install Ubuntu Studio...so many of those applications came with it.  As for the Wiki on Jackd...I get a redirect to this Wiki:

[http://en.wikipedia.org/wiki/Jackd](http://en.wikipedia.org/wiki/Jackd)

As you see, it doesn't mention much.  I did go to the official Jack website and again, it doesn't really mention much.


>  As I said, there are a lot of threads about recording, editing, setting up and using jack, etc in the Multimedia Production Forum. You should really pay it a visit.

About getting your Soundblaster X-Fi to work. Go to the top page of the forums and use the search function from there, that way your search will look in all the forums instead of just here. I am sure someone around here has got it working and you can find out how they did it.

Ok, I am not THAT new to Ubuntu or these forums.  I should have brought you up to speed of where I been and where I am now.  

Yes, I know about the search and I know it doesn't work very well either.  I have to go to "Advanced Search" and type what I want in.  The box on the top right corner has a habit of searching entire documents (not just the title) and it returns quite a bit of irrelevant information (I am hoping they fix that soon).  That said, yes, I have found a solution to get my sound card "partially" running.  I DO have sound now as we speak.  My games are working fine (with the sole exception of my NES emulator), I can play audio through Totem Audio/Movie Player.   However, none of the audio/video applications with Ubuntu Studio are working and neither is my streaming internet.  The Ubuntu system sounds ARE working.

There was a huge thread on OSS and X-Fi and I am a part of that thread.  Unfortunately the thread is still running as it appears there are many issues...especially from the upgrade from Ubuntu version 7.10 to 8.04.

The problem as of now is that the ALSA drivers that are meant for the X-Fi do not work very well and they are tremendously hard to get to cooperate with Ubuntu.   It was in the X-Fi thread that I heard about OSS in the first place and that it is fairly painless to get operating.

The trouble is that once I got sound in one area of my system, I worked on a another area only to have something else go wrong.

As I mentioned above, this is actually the second time I installed OSS because my first installation got blown away by an internet streaming audio fix that I thought would work, but later found out it was only for the ALSA driver (and those people who have Sound Blaster Live on their system), and not the OSS driver.  So that was partially my fault because I didn't indicate to author of the fix that I was operating a different card with OSS.

So as of now I DO have some sound.

What doesn't work with sound is as follows:

1) All Ubuntu Studio applications (Audacity, Ardour, RoseGarden, Hydrogen, Cinelerra, Open Movie Editor...lets just say just about everything).

2) Streaming internet audio (You Tube, Yahoo, etc).

3) GFCE NES Emulator.


I do have posts in the Multimeda section, but thusfar help is slow going.  I got as far that I know that I need to get Jack working with Ubuntu Studio in order to get most of the applications running there.  If I can do that AND get my streaming internet, then I should be good to go for a while.  At least I would like to be able to do what I wanted and test some of the Ubuntu Studio Applications out.

So in my frustration with trying to get Ubuntu Studio working, I was wondering if others has any of these kinds of sound problems with the other distro's for Linux...specifically the others that were meant for audio and video editing applications.

So that brings me where I am now.

Thanx,

Geo

---

