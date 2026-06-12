---
title: "mp3s won't play"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by Nutopia on 2008-06-03
Hi. I've downloaded a number of MP3s... the files are good... but they won't play in any of the music players I have installed. I've tried in Rhythmbox and Amarok. I hit play and nothing happens. Any ideas?

---

### Post by hyper_ch on 2008-06-03
install the ubuntu-restricted-extra package.

---

### Post by boywholinuxed on 2008-06-03
if u r using ubuntu try playing the songs totem player,it'll detect that mp3 format is missing and will install the codec for you.

if u r using kubuntu ,try amarok and amarok will do the same what totem did for ubuntu

---

### Post by Inxsible on 2008-06-03
Applications>>Add/Remove. Search for "gstreamer" without the quotes and install all those codecs.

Then try again.

---

### Post by NikoC on 2008-06-03
To be a bit more specific:
Applications > Add/Remove
Search for 'mp3' and you will find 'Ubuntu restricted extras'.
Mark it for installation and apply.

Edit: I think you might also want to enable the 3rd party repositories and the restricted, universe and multiverse repositories via Synaptic (Synaptic > Settings > Repositories)

Edit2: okay, you guys were quicker than I was in replying ;)

---

### Post by Nutopia on 2008-06-03
I installed ubuntu-restricted-extra through the Synaptic package manager.

Still won't play. I hit the play button, the play button turns to a pause button, but the progress meter stays at 0:00.

---

### Post by NikoC on 2008-06-03
And if you install another player like vlc?

---

### Post by Valsodar on 2008-06-03
have you installed the gstreamer codecs (go to Applications->Add/Remove search for gstreamer and install the gstramer extra plugins), otherwise mp3 do not play in ubuntu (also verify if your player works by playing an ogg file)

---

### Post by SunnyRabbiera on 2008-06-03
you may with to enable extra repositories, and medibuntu, doing both is very easy.

---

### Post by rraj.be on 2008-06-03
try this link.

[https://help.ubuntu.com/community/RestrictedFormats]("https://help.ubuntu.com/community/RestrictedFormats")

---

### Post by Nutopia on 2008-06-03
I tried playing in vlc. When I hit play it looks like it is playing - the progress bar is moving - but nothing is heard. I've tried it with a few different files - nothing.

My audio does work and my volume is turned up. I just went to youtube and played a video to make sure I wasn't being stupid - definitely heard the youtube video.

I have the gstreamer extra plugins installed. I also re-installed them. Nothing.

---

### Post by SunnyRabbiera on 2008-06-03
what version of ubuntu are you using?
what processor/kernel type are you using?
intel 32 or AMD 64?

---

### Post by Nutopia on 2008-06-03
Version 8.04
Intel processor.

I was able to play MP3s before the upgrade to 8.04 - I haven't been able to play them since.

---

### Post by avtolle on 2008-06-03
8.04 uses Pulse Audio as the default for handling audio. Re: VLC, have you selected the Pulse Audio plugin for audio? Just a thought.

---

### Post by Nutopia on 2008-06-03
avtolle - I'm not sure how to check that?

---

### Post by SunnyRabbiera on 2008-06-03
as so then you upgraded from gutsy to hardy, now we are getting somewhere.
i suspect something might have happened to your mp3 codec during your transition, I suggest enabling the extra repositories for starters:
go to synaptic and to settings, then to repositories and make sure all repositories except for the source code one is marked off in tab 1.
then in tab 2 make sure the partner repositories are marked off too except for the source code repo.
after that hit the refresh button.
you may need more gstreamer plugins to start out with, but you may also want to check out medibuntu:
[https://help.ubuntu.com/community/Medibuntu]("https://help.ubuntu.com/community/Medibuntu")

Now by any chance did you use automatix?

---

### Post by avtolle on 2008-06-03
> **Nutopia said:**
> avtolle - I'm not sure how to check that?
First, open VLC. Then, select "Settings", and Preferences under Settings. A fairly mundane graphic will appear. In the bottom right, check Advanced. In the left-most box, then select Audio, which will give you some general informaton. Expand the Audio list, and you will see as an option Output Modules. Select that; in the window on the right, if Pulse Audio is enabled, it will appear in the whatever the thing is called. If not, click on the down arrow, and select Pulse audio output. Then, click on Save on the bottom left, and restart VLC, and try to play an mp3. Hope this helps, and sorry for the not-exact descritpion of steps. It's one of the things that for me, if I was there, I'd do quickly and show you, but trying to describe the steps clearly is difficult. :-(

---

### Post by Nutopia on 2008-06-03
Actually I upgraded from Feisty Fawn.

I've enabled all of those repositories... and I ran the medibuntu commands in terminal. 

I also converted one of the mp3s to ogg - and the ogg file won't play either.

i dont use automatix

---

### Post by Nutopia on 2008-06-03
> **avtolle said:**
> First, open VLC. Then, select "Settings", and Preferences under Settings. A fairly mundane graphic will appear. In the bottom right, check Advanced. In the left-most box, then select Audio, which will give you some general informaton. Expand the Audio list, and you will see as an option Output Modules. Select that; in the window on the right, if Pulse Audio is enabled, it will appear in the whatever the thing is called. If not, click on the down arrow, and select Pulse audio output. Then, click on Save on the bottom left, and restart VLC, and try to play an mp3. Hope this helps, and sorry for the not-exact descritpion of steps. It's one of the things that for me, if I was there, I'd do quickly and show you, but trying to describe the steps clearly is difficult. :-(
 
I gave that a shot but still isn't doing anything. Won't play ogg either.

---

### Post by SunnyRabbiera on 2008-06-03
> **Nutopia said:**
> Actually I upgraded from Feisty Fawn.

I've enabled all of those repositories... and I ran the medibuntu commands in terminal. 

I also converted one of the mp3s to ogg - and the ogg file won't play either.

i dont use automatix

ah, there too might be the source of your issues.
But we will try our best to help you.

---

### Post by avtolle on 2008-06-03
> **Nutopia said:**
> Actually I upgraded from Feisty Fawn.

I've enabled all of those repositories... and I ran the medibuntu commands in terminal. 

I also converted one of the mp3s to ogg - and the ogg file won't play either.

i dont use automatix
That's why I suspect the Pulse audio plugins aren't enabled in any of your audio players. I've not looked at Rhythmbox, but would hope the adding of the codecs would solve the problem there, as it is the "default" player for 8.04.

---

### Post by Nutopia on 2008-06-05
Just a quick update - all of the sudden everything is working again! Not sure why or how, but I tried to play the exact same mp3 file again today and it will now play in every music player I have installed. I did run 'update' today - so maybe something in there fixed it? anyway, thanks for everyone's input!

---

### Post by Bianibi on 2008-06-06
I have the exact same problem, but, I ran update and nothing happened, VLC doesn't play any audio either, and I did everything that was mentioned in this post.
Any ideas?

---

### Post by Bianibi on 2008-06-06
Ok, fixed!
System->Preferences->Sound 
Everything was set to "automatic", I changed it to "ASLA"
It also fixed a problem I had with Totem where it played video but no audio.

[http://ubuntuforums.org/showthread.php?t=786815&highlight=rhythmbox](http://ubuntuforums.org/showthread.php?t=786815&highlight=rhythmbox)

---

