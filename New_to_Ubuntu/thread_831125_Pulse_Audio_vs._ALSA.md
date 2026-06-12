---
title: "Pulse Audio vs. ALSA"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Maupertus on 2008-06-16
I've got a question and I can't really find the awnser in the forums or the PULSE Audio pages.

Why did Ubuntu switch to Pulse?

When I did an upgrade, the sound by the PULSE drivers was messed up, so I put everything in the soundpreferences back to ALSA.

After following [this](http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulse+audio) guide I think I've ironed everything out, although I know have an extra process that has to get started when my session starts.

So why did Ubuntu go over to Pulse, is it faster or lighter or does it offer better hardware support?

One explanation I found said that Pulse made multiple audio streams possible, but I never had any problem with ALSA on that account.

---

### Post by lswest on 2008-06-16
Well ALSA should have only let one application use the sound card at once, whereas PulseAudio (seeing as it's a sound server) will allow multiple apps access to the sound card, and you can even stream audio to the sound server over LAN.  Basically that's the reason why (from what I gather).

---

### Post by Maupertus on 2008-06-16
> **lswest said:**
> Well ALSA should have only let one application use the sound card at once, whereas PulseAudio (seeing as it's a sound server) will allow multiple apps access to the sound card, and you can even stream audio to the sound server over LAN.  Basically that's the reason why (from what I gather).

Strange, I never had any issues playing mp3's while watching flash-sites (example)

So when I put all the sound preferences on ALSA in Hardy, is HArdy still using Pulse via ALSA, or does it disregard Pulse?

---

### Post by Barrucadu on 2008-06-16
That can't be the reason - I frequently play flash games with music while listening to music in Quod Libet and I don't have Pulse installed, just ALSA.

---

### Post by sdennie on 2008-06-16
I honestly have no idea why it was included in Hardy.  For the vast majority of users it offers no new interesting functionality the way it's configured in Hardy and, as is evidenced by the number of threads related to Pulse Audio on these forums, it has caused more problems than it has solved (which, as far as I can tell, is approximately 0).

---

### Post by stchman on 2008-06-16
> **Maupertus said:**
> I've got a question and I can't really find the awnser in the forums or the PULSE Audio pages.

Why did Ubuntu switch to Pulse?

When I did an upgrade, the sound by the PULSE drivers was messed up, so I put everything in the soundpreferences back to ALSA.

After following [this](http://ubuntuforums.org/showthread.php?t=776739&highlight=perfect+pulse+audio) guide I think I've ironed everything out, although I know have an extra process that has to get started when my session starts.

So why did Ubuntu go over to Pulse, is it faster or lighter or does it offer better hardware support?

One explanation I found said that Pulse made multiple audio streams possible, but I never had any problem with ALSA on that account.

I prefer ALSA as it lets my surround sound speakers function (except VLC).  Pulse also has some issues with Flash.

Go with ALSA.

---

### Post by markbuntu on 2008-06-16
The weird thing is that pulseaudio sits on top of alsa instead of replacing it, adding another layer of complications and increasing latency to add a few minor functions and it kicks all the alsa functionality out in doing so.

I can understand pulseaudio adding network functionality to sound but really, does it have to take over the entire sound scheme just so a few people can taunt others in on line gaming?

The primary reason for including pulseaudio in 8.04 was to give the pulseaudio developers an easier update path. The same reason we got such a piece of crap firefox beta.

This has gone too far. A LTS release should not include buggy apps just to give the Developers and easier time. It goes completely against the Ubuntu philosophy that everything should "just work".

The Ubuntu Team have lost their focus.

---

### Post by Endolith on 2008-12-02
> **lswest said:**
> Well ALSA should have only let one application use the sound card at once, whereas PulseAudio (seeing as it's a sound server) will allow multiple apps access to the sound card

OSS only lets one application use the sound card at once.  ALSA lets multiple applications.  I think the only benefit of PulseAudio is the network functionality and independent volume controls for each app?  It's not very clear.

> **markbuntu said:**
> This has gone too far. A LTS release should not include buggy apps just to give the Developers and easier time. It goes completely against the Ubuntu philosophy that everything should "just work".

The Ubuntu Team have lost their focus.

Agreed.  Intrepid continued the pattern, with almost half of users having "serious problems", according to polls on here.  Is there another distro that tries to achieve what Ubuntu used to?  Maybe Linux Mint?

---

### Post by markbuntu on 2008-12-02
Wow, I forgot I wrote that. Anyway, I discovered that the problem is not with pulseaudio but with an entirely bogus implementation in Ubuntu which has continued with Intrepid.

After I decided to just knuckle down and get pulseaudio working, which I did and along the way managed to accumulate a ton of scattered information about sound in general which is concolidated in my guides. 

The 10,000 page guide to sound in Hardy

[http://ubuntuforums.org/showthread.php?t=843012](http://ubuntuforums.org/showthread.php?t=843012)

The Multiple Sound card guide:

[http://ubuntuforums.org/showthread.php?t=922860](http://ubuntuforums.org/showthread.php?t=922860)

The quick start guide to Intrepid:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

I find pulseaudio to be an excellent replacement for the alsa hodgepodge. It does many things quite well and if you have more than one sound card/device it is an abolute must. No more fooling around with asoundconf.

For the life of me I just do not understand why the Pulse Audio Volume Control is left out of the standard install and why the default in Sound is automatic which does nothing but automatically create conflicts. 90% of peoples sound problems can be solved with 10 more packages and a few changes in the Sound defaults.

At least Mandriva includes the pulseaudio volume control.

---

### Post by sdowney717 on 2008-12-02
I seem to loose sound randomly which only a reboot fixes.
Running Ibex.
Irritating to find out you have no sound when you start a video.
Does one of your links describe this 10 package fix?

---

### Post by markbuntu on 2008-12-02
> **sdowney717 said:**
> I seem to loose sound randomly which only a reboot fixes.
Running Ibex.
Irritating to find out you have no sound when you start a video.
Does one of your links describe this 10 package fix?

The quick start guide to Intrepid:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

You may have other problems but try this first.

There is another thing that many people do not seem to grasp. That is that there are over 50,000 different pieces of hardware for the pc in over 500,000 different combinations. It is impossible for any organization to test all this before releasing a product. 

This becomes especially true when the driver writers have only sketchy and incomplete information and are unable to test every variation of every product which is the case with sound cards and chips in linux. 

So please, bear with us, we are trying our best.

---

### Post by SnappyU on 2008-12-10
> **markbuntu said:**
> The quick start guide to Intrepid:

[http://ubuntuforums.org/showthread.php?t=997506](http://ubuntuforums.org/showthread.php?t=997506)

You may have other problems but try this first.

There is another thing that many people do not seem to grasp. That is that there are over 50,000 different pieces of hardware for the pc in over 500,000 different combinations. It is impossible for any organization to test all this before releasing a product. 

This becomes especially true when the driver writers have only sketchy and incomplete information and are unable to test every variation of every product which is the case with sound cards and chips in linux. 

So please, bear with us, we are trying our best.

Yes, and that's why MS still commands highest market penetration in the PC industry, because somehow it manages to create a virtuous cycle and work with the OEM/hardware vendors to get enough of these "50k+" hardware working in "500k+" combo so that users do not need to worry about sound working or not.

I have Ubuntu on my day (work) machine and for half a year I lived with the headphone jacks not working.  Then I finally got it to work after trawling through too many forums and pages to care.  Now I'm left with Skype that refuses to accept mic input.

I truly hope that someone in the ubuntu or linux community come up with something like the DirectX/HAL framework so that hardware OEMs just write to according to a standard HAL driver while software writers just code for the "DirectX" layer.  Pulse shows much promise, but as it is, sound configuration for ubuntu reminds me too much of the 80s-early90s when getting sound to work properly was a hit-and-miss affair.

I'll still use Ubuntu although I have a Vista retailbox-license sitting around and I can easily afford to get an XP license for my notebook 'cos I really hope Ubuntu will succeed.  

I hope new Ubuntu releases do not tear up plumbings that are already tried-and-tested to be working unless absolutely necessary.  Otherwise, it becomes just another geek's wetdream to spend hours, days and weeks, pouring over forums and tinkering conf files for that satisfaction of getting it to work ... ... only to start the cycle again when the next release arrives.

Give me something that just works without tinkering and I really do not mind paying a quid a year just to show my support for Ubuntu. :)

---

### Post by Endolith on 2008-12-10
> **markbuntu said:**
> There is another thing that many people do not seem to grasp. That is that there are over 50,000 different pieces of hardware for the pc in over 500,000 different combinations. It is impossible for any organization to test all this before releasing a product.

Microsoft and Apple do it; why can't Ubuntu?  Why is Canonical releasing a product with a half-baked audio subsystem that causes a large number of people to have sound problems, when the previous audio subsystem worked just fine?  Why can't they wait until the bugs have been ironed out before shipping it out the door?

---

### Post by markbuntu on 2008-12-11
> **SnappyU said:**
> Yes, and that's why MS still commands highest market penetration in the PC industry, because somehow it manages to create a virtuous cycle and work with the OEM/hardware vendors to get enough of these "50k+" hardware working in "500k+" combo so that users do not need to worry about sound working or not.

I have Ubuntu on my day (work) machine and for half a year I lived with the headphone jacks not working.  Then I finally got it to work after trawling through too many forums and pages to care.  Now I'm left with Skype that refuses to accept mic input.

I truly hope that someone in the ubuntu or linux community come up with something like the DirectX/HAL framework so that hardware OEMs just write to according to a standard HAL driver while software writers just code for the "DirectX" layer.  Pulse shows much promise, but as it is, sound configuration for ubuntu reminds me too much of the 80s-early90s when getting sound to work properly was a hit-and-miss affair.

I'll still use Ubuntu although I have a Vista retailbox-license sitting around and I can easily afford to get an XP license for my notebook 'cos I really hope Ubuntu will succeed.  

I hope new Ubuntu releases do not tear up plumbings that are already tried-and-tested to be working unless absolutely necessary.  Otherwise, it becomes just another geek's wetdream to spend hours, days and weeks, pouring over forums and tinkering conf files for that satisfaction of getting it to work ... ... only to start the cycle again when the next release arrives.

Give me something that just works without tinkering and I really do not mind paying a quid a year just to show my support for Ubuntu. :)

Well, if the hardware manufacturers and vendors actually supported linux that would make a big difference but the fact is most don't. Why don't you complain to them to support your hardware in linux because that is where the problem lies.

For the most part the linux driver writers, who are mostly volunteers are left with little to no information to go on and so are reduced to guessing. 

Anyway, we don't need complaints here, we need help. If you want to complain, buy vista, then you can complain.

If you want stability use Debian.

---

### Post by Sirron on 2008-12-11
One thing pulseaudio enables that ALSA alone does not is decent support for multiple sound cards.

I have an on-board HD audio sound card, to which I have connected a headset, and a separate Xfi xtreme gamer sound card to which I have connected speakers.

With pulseaudio, it is possible to move individual audio streams between the cards whilst they're still playing, using a GUI. The streams usually have sensible names, so you know what's playing, and where.

With alsa (when I had an Audigy SE instead of the Xfi), all I could do was disable the Audigy and force everything to go through the headset.

---

### Post by Sirron on 2008-12-11
> **Endolith said:**
> Microsoft and Apple do it; why can't Ubuntu?  Why is Canonical releasing a product with a half-baked audio subsystem that causes a large number of people to have sound problems, when the previous audio subsystem worked just fine?  Why can't they wait until the bugs have been ironed out before shipping it out the door?

I also use vista, and every now and the entire sound system stops working. :)

---

### Post by SnappyU on 2008-12-13
> **markbuntu said:**
> Well, if the hardware manufacturers and vendors actually supported linux that would make a big difference but the fact is most don't. Why don't you complain to them to support your hardware in linux because that is where the problem lies.

For the most part the linux driver writers, who are mostly volunteers are left with little to no information to go on and so are reduced to guessing. 

Anyway, we don't need complaints here, we need help. If you want to complain, buy vista, then you can complain.

If you want stability use Debian.

Actually, I would recommend XP over vista if you ask me. ;)

Well, pardon me, but I didn't know that complaints or more like comments, are not allowed here.

The thing with sound here is not quite the drivers actually.  I might have been wrong, but it is more with configuration.  And that is what is lacking.  Call it complaints or comments, but that is what is lacking in the otherwise perfect Ubuntu.

Audio aside, btnx was working just fine in Hardy Heron with the mouse detection and configuration.  It even detected the tilt button of my Microsoft notebook mouse and allowed me to configure it to do something else when the MS drivers on XP did not.  Now, that is what makes Ubuntu really appealing.  But in Intrepid, btnx does not work.  Only recourse is to use the more "advanced" input configuration using xmacro and xbindkeys I found in [http://ubuntuforums.org/showthread.php?t=968530](http://ubuntuforums.org/showthread.php?t=968530)

It is interesting to know how the underlying plumbing work.  But this is 2008, not 1998 or 1988.  Why are we still figuring out a better way to detect mouse and input devices?  Especially when something was already working (BTNX).  It's nice that we can drive cars and use them to get to places without having to know exactly how the combustion engine work.  Most people just want to go to places to get things done.  Most do not want to or need to know how exactly it work.

Anyway, no offense to you Mark.  The points I raise echoes throughout the linux / Ubuntu community and part of the reason why Ubuntu is somewhat more successful is because it has solved part of this problem by making the OS easy for ppl to install, use and upgrade with little or no technical knowledge.

There are prob others like me who wish we have the time to tinker with the OS to get the sound working etc, but we don't.  Let's not just alienate others and suggest that we go use Windows XYZ / Mac OS at the drop of the hat.  Not very helpful there. :)

---

### Post by SnappyU on 2008-12-13
Just a piece of good news.  I finally managed to configure my mic to capture reliably.

Under System->Preferences->Sound Preferences
All playback->Pulse Audio Sound Server
Audio Conferencing->Sound Capture->HDA ATI SB ALC861VD Analog (OSS)

I'm running Ubuntu 8.10 upgraded from 8.04

Recording in Gnome sound recorder works.

Skype test with echo123 works with the following config:
Options->Sound Devices
Sound In->pulse  (Refers to Mic)
Sound Out->pulse (Refers to Speaker)
Ringing->pulse
Allow Skype to automatically adjust my mixer levels is left unchecked

In my case, letting Skype adjust my mixer levels messes the sound capture. 


YMMV, have fun! :)

---

### Post by CatKiller on 2008-12-13
> **Maupertus said:**
> Why did Ubuntu switch to Pulse?

PulseAudio is better than ALSA. It is also much newer, which means that it hasn't been tested as widely as ALSA and that applications largely haven't been written with PulseAudio in mind. Some applications, including older versions of Flash, still expect OSS, which is even older, and much more limited.

Hardy shipped with a bad PulseAudio configuration. This is unfortunate, and has soured many people to PulseAudio. The configuration in Intrepid is much better, and I'd imagine that both the configuration and PulseAudio itself will improve in future releases as PulseAudio matures. Generally speaking, software matures more quickly if it is widely used. Using PulseAudio in Ubuntu at some point was probably necessary to get that level of improvement. An LTS release with a less than optimal PulseAudio configuration might not have been the best point to do so, on reflection, but we can't change that now.

Whilst the flexibility of PulseAudio is great (and is significantly better than ESD, which is what it actually replaced - as has already been noted here, it still uses ALSA to spit sound out of a connected sound card) I suspect that its greatest strength is that it is cross-platform, meaning that application developers have one fewer reason to treat Linux as the red-headed stepchild when it comes to releasing their applications. They can use PulseAudio for sound, and not have to do anything else to get the sound working on Windows, Linux, BSD, or OS X. While I might have preferred the developer effort to go into improving JACK, which is also cross-platform and very flexible, I guess that there may well be some technical reasons why it was better to have (yet) another sound server system for Linux.

---

### Post by arrancaru on 2008-12-13
IMHO pulseaudio is unecessary for almost every ubuntu user and adds latency and bugs to a thing fundamental that must be "just works", the sound system. There is no way to beat windows in desktop without accomplish basic functionality first.

---

### Post by CatKiller on 2008-12-13
I've never seen PulseAudio add latency. It is miles better than ESD.

"Beating Windows on the Desktop" is irrelevant. The only goal worth pursuing is to make Ubuntu as good as it can be.

---

### Post by baytuni on 2008-12-13
yes pulse causes skype to create incredible amounts of audio lags.

---

### Post by CatKiller on 2008-12-13
> **baytuni said:**
> yes pulse causes skype to create incredible amounts of audio lags.

That would be why I hadn't seen it then; I don't use Skype.

Isn't Skype one of those applications that uses OSS? Does running Skype through padsp help? I'm only really asking out of idle curiosity - I have no intention of running Skype myself.

---

### Post by sdennie on 2008-12-13
> **CatKiller said:**
> I've never seen PulseAudio add latency. It is miles better than ESD.

"Beating Windows on the Desktop" is irrelevant. The only goal worth pursuing is to make Ubuntu as good as it can be.

At least in Hardy, Pulse was unusable for me.  I tried to watch a movie in mplayer with Pulse on and the daemon immediately went to 100% CPU and caused the movie to skip, sound to be out of sync, etc.  These are the sorts of things that will turn people off of Linux.  *I* know how to fix these problems but, the average user won't.

As far as I'm aware, ALSA was never considered broken by the vast majority of users.  It's still not clear to me why it was "fixed" with Pulse.

---

### Post by baytuni on 2008-12-13
> **CatKiller said:**
> That would be why I hadn't seen it then; I don't use Skype.

Isn't Skype one of those applications that uses OSS? Does running Skype through padsp help? I'm only really asking out of idle curiosity - I have no intention of running Skype myself.
What do you mean by "Does running Skype through padsp help?" I have pulseaudio-utils installed. But how do i use skype through it?

---

### Post by CatKiller on 2008-12-13
> **baytuni said:**
> What do you mean by "Does running Skype through padsp help?"

From **man padsp:**

> DESCRIPTION
       padsp starts the specified program and redirects its access to OSS com&#8208;
       patible audio devices (/dev/dsp and auxiliary devices) to a  PulseAudio
       sound server.

So instead of running *skype*, say, you'd run *padsp skype*. I have no idea if it would help, which is why I asked.

---

### Post by CatKiller on 2008-12-13
> **vor said:**
> At least in Hardy, Pulse was unusable for me.

I think everyone agrees that the Hardy PulseAudio configuration was bad. Without a time machine, though, there's not much we can do about that, other than make it better for future releases. Which is already happening.

> As far as I'm aware, ALSA was never considered broken by the vast majority of users.  It's still not clear to me why it was "fixed" with Pulse.

ALSA isn't broken. PulseAudio still uses ALSA. But ESD (which is what PulseAudio **actually** replaces) is not as compatible with everything else in the way that PulseAudio is.

I'm no PulseAudio apologist, but many people seem to be blaming PulseAudio for things that really aren't anything to do with PulseAudio, and without really understanding what it is.

---

### Post by sdennie on 2008-12-13
> **CatKiller said:**
> 
ALSA isn't broken. PulseAudio still uses ALSA. But ESD (which is what PulseAudio **actually** replaces) is not as compatible with everything else in the way that PulseAudio is.


So my question is, why add a potentially broken layer between an application and ALSA? I know the default sink for pulse is ALSA but the vast majority of users only require ALSA.

To put a different spin on this, imagine if Dapper Drake had shipped with compiz enabled by default.  It would have been broken, buggy, and would turn people off of Ubuntu.  This is what has happened with pulse.  The first thing I do when I help people install Ubuntu is disable pulse because, 1) It's not needed and 2) It's bound to cause problems.

There is a fine line between "awesome" and "broken".  Pulse still sits on the "broken" side of that line.

---

### Post by Sirron on 2008-12-13
It's clear that Pulse Audio on the Ubuntu Desktop is analogous with Compiz, and to some extent, proprietary graphics drivers; it's nice to have if you know what it's for, but for the average, web browsing user, it can be more trouble than it's worth.

What is needed here is a decent GUI that allows for full configuration of audio input and output, much along the lines of the Appearance settings tool - which of course allows the enabling of Compiz. Pulse audio could be disabled by default, and where appropriate, the tool would simply need to inform the user that the setting they're trying to change requires pulse audio to be enabled, explain the pros and cons, and let them enable it if they decide it's what they need. Setting up a microphone properly on ubuntu is far too difficult, an intuitive interface that brings all the settings together would hopefully solve that. *I wouldn't know where to begin to create it so don't tell me to ^^*

---

### Post by epitaph on 2008-12-13
I'm just sharing my opinion with the following.

I had some serious sound issues with my main desktop system when I first installed Hardy. I did 3-4 different guides that had me install a plethora of packages (literally tens of them) in an attempt to get PulseAudio to work in a more proper manner. After polluting my system with an epic amount of extra utilities, configuration panels and whatnot I gave up and removed every single thing referencing PulseAudio from my system and just began to use ALSA. All of my issues were alleviated after this and I was amazed that no one had suggested in any of the guides/threads I read to consider abandoning PulseAudio.

I think PulseAudio sounds like a great idea in theory, though perhaps it isn't far enough along at this point to be utilized for tasks that ALSA appears to handle very well. For me, I can run Ventrilo through wine, play a game of Quake3 and listen to music all at once with no issues (no lag, no stuttering, almost zero processor usage) whereas with PulseAudio a lot of these issues were present.

I'm sure someone out there is saying "yeah well you didn't use the padsp command or the (insert command here) to fix it I bet". Personally, I'd prefer not have to add complication and bend over backwards to have things work. I'd rather have the computer work for me instead of me work for the computer.

I don't dislike PulseAudio, though I will say that removing it on my desktop (I still use it on my laptop with no issues) was a good idea and I don't plan to bring it back. Hopefully PulseAudio will mature greatly and change the way Linux sound is treated.

---

### Post by baytuni on 2008-12-13
by the way "padsp skype" did not work for me.

---

### Post by gychang on 2008-12-13
> **Sirron said:**
> One thing pulseaudio enables that ALSA alone does not is decent support for multiple sound cards.

I have an on-board HD audio sound card, to which I have connected a headset, and a separate Xfi xtreme gamer sound card to which I have connected speakers.

With pulseaudio, it is possible to move individual audio streams between the cards whilst they're still playing, using a GUI. The streams usually have sensible names, so you know what's playing, and where.



this is a good piece of information for a newbie like me, so I have motherboard AC97 and USB soundcard so I will try this puselaudio.

gychang

---

### Post by seeker5528 on 2008-12-13
> **Endolith said:**
> OSS only lets one application use the sound card at once.  ALSA lets multiple applications.  I think the only benefit of PulseAudio is the network functionality and independent volume controls for each app?  It's not very clear.

I don't think OSS or ALSA ever had this limitation. If you had Soundblaster or other hardware that did hardware mixing, it could work, and in some cases did work.

Both of these allow applications to request exclusive access, this is where the first problem came in. Most commonly people don't have sound hardware that does hardware mixing, so applications and sound servers just assume they should request exclusive access, breaking things for those of us who actually have capable hardware. This seemed more common with applications that use OSS than application that use ALSA.

The ALSA guys created DMIX as part of ALSA to tackle this issue with software at a low level. The only problem with that is, the OSS compatibility stuff has not been updated to allow OSS applications to use DMIX. Again if you have hardware that does hardware mixing this shouldn't be a problem except many applications try to grab exclusive access.

Pulse Audio has some nice features, so I don't have have any problems with it being available and having applications that require it. But I don't like that it continues to try to solve yesterdays problem by assuming if you use it, all audio should go through it.

Later, Seeker

---

### Post by Sirron on 2008-12-14
> **gychang said:**
> this is a good piece of information for a newbie like me, so I have motherboard AC97 and USB soundcard so I will try this puselaudio.

gychang

See _[http://ubuntuforums.org/showthread.php?t=988509](http://ubuntuforums.org/showthread.php?t=988509)_

---

### Post by SnappyU on 2009-01-12
Just to update that the setup I thought I got working was not consistent and it broke again!! :(

I followed some other threads and totally removed PulseAudio and now Skype and sound in Intrepid is working.  :):)



> **SnappyU said:**
> Just a piece of good news.  I finally managed to configure my mic to capture reliably.

Under System->Preferences->Sound Preferences
All playback->Pulse Audio Sound Server
Audio Conferencing->Sound Capture->HDA ATI SB ALC861VD Analog (OSS)

I'm running Ubuntu 8.10 upgraded from 8.04

Recording in Gnome sound recorder works.

Skype test with echo123 works with the following config:
Options->Sound Devices
Sound In->pulse  (Refers to Mic)
Sound Out->pulse (Refers to Speaker)
Ringing->pulse
Allow Skype to automatically adjust my mixer levels is left unchecked

In my case, letting Skype adjust my mixer levels messes the sound capture. 


YMMV, have fun! :)

---

### Post by me.translucent on 2011-02-23
For OSS applications, PulseAudio provides the padsp utility, which replaces device files such as /dev/dsp, tricking the applications into believing that they have exclusive control over the sound card. In reality, their output is rerouted through PulseAudio.
-Source wikipedea :)

---

### Post by Perfect Storm on 2011-02-23
[[img]http://s4.postimage.org/jbyj0j85e/Thread_Necromancer.jpg[/img]](http://www.postimage.org/)


Thread closed.

---

