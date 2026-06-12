---
title: "Sound Problems! - Crackling sound when playing any audio - but no errors!"
date: 2008-08-29
forum: New to Ubuntu
---

### Post by Mazza558 on 2008-08-29
Hey all,

Every time I try to play a sound on Ubuntu, it plays correctly but the sound is never actually produced. There are no errors at all, but all I hear is a crackling sound.

All sound settings are set to "Automatic". "Open Sound System" works according to the Sound preferences, but flash videos or anything online still crackles. 

Help! Thanks in advance.

---

### Post by bangmalley on 2008-08-31
set it to "ALSA".
flash doesn't support OSS natively.

---

### Post by ben2talk on 2008-11-04
> **bangmalley said:**
> set it to "ALSA".
flash doesn't support OSS natively.

Wow, I ran into this problem today - started up my com and only get crackling out - and it is already set for ALSA.

Rebooted to XP - unfortunately I have to report that XP is proving more reliable than ubuntu as usual....

Any ideas?

I fixed it. I suggest you check your mixer (ALT and F2) I get two options, gnome-alsamixer is good.  For some reason one of my settings had changed - I played with the sliders while Rhythmbox was playing a tune.

I don't understand the crackle - but it's gone now.

---

### Post by krawlx on 2009-01-07
Thanks for this thread.  It pointed me in the right direction to fixing the same problem.  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me.  As for the crackling sound...I assumed it was internal computer noise.  When I plug in my headphones to my laptop I get the same noise.  

Hope this helps someone in the future.

---

### Post by bobpur on 2009-01-07
Another thing to check are your volume controls.

My setup has the volume slider on the screen and my Logitech speakers has a knob on the right front speaker. Try to keep the on-screen slider about halfway and use the speaker control for volume adjustments.

If the slider is cranked up anything coming out of your speakers will be distorted or made worse by cranking up the speaker volume.

My setup will still rattle the windows and the dishes in the cupboard with the slider halfway and the speakers cranked up.

Good luck.

---

### Post by beefcurry on 2009-02-27
> **krawlx said:**
> Thanks for this thread.  It pointed me in the right direction to fixing the same problem.  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me.  As for the crackling sound...I assumed it was internal computer noise.  When I plug in my headphones to my laptop I get the same noise.  

Hope this helps someone in the future.

That solved my issue :) thanks, don't know why the PCM slider suddenly went down to zero.

---

### Post by wisd0m on 2009-03-22
> **krawlx said:**
> Thanks for this thread.  It pointed me in the right direction to fixing the same problem.  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me.  As for the crackling sound...I assumed it was internal computer noise.  When I plug in my headphones to my laptop I get the same noise.  

Hope this helps someone in the future.


worked, thanks.

---

### Post by GJCT on 2009-04-13
Hi,

I have this same problem. About a week into using Ubuntu (8.10) my laptops speakers started crackling. This also happens when I plug in external speakers or headphones (through the headphone jack). It seemed to stop crackling when I used skype, but now the crackling is present all the time (whenever any audio is playing). I have tried playing around with my volume controls in my alsa mixer (VIA 8233), as per the suggestions above, but nothing seems to work.

Could anybody help me? (bearing in mind I'm a real beginner!) 

Thanks in advance.

Glen

---

### Post by rmkrishnan33 on 2009-04-14
> **beefcurry said:**
> That solved my issue :) thanks, don't know why the PCM slider suddenly went down to zero.



This solved my problem too. Thanks for the help.

---

### Post by Rackstar on 2009-04-20
Solved my problem also, was already looking way too far. Thanks

---

### Post by GJCT on 2009-04-23
As I previously posted, changing the volume settings hasn't worked for me. I did find this fix which would seem to work:

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html)

If only I knew how to do it! Can anybody tell me how to implement this - do I just enter it in terminal (I guess not because I tried that and it didn't work)?

Thanks for your help.

---

### Post by GJCT on 2009-05-06
> **GJCT said:**
> As I previously posted, changing the volume settings hasn't worked for me. I did find this fix which would seem to work:

[http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html](http://www.mail-archive.com/alsa-user@lists.sourceforge.net/msg08159.html)

If only I knew how to do it! Can anybody tell me how to implement this - do I just enter it in terminal (I guess not because I tried that and it didn't work)?

Thanks for your help.

bump

---

### Post by mickey57 on 2009-05-21
...This worked for me;
[http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html]("http://www.ubuntugeek.com/how-to-remove-pulse-audio-ubuntu-810-intrepid-ibex.html")
....and I am running  Karmick

---

### Post by GenuineXP on 2009-05-28
I am also experiencing problems with crackling sounds (I'm using Ubuntu Jaunty AMD64). I do not want to remove my sound server (PulseAudio).

In past releases, I found that lowering the PCM and Master volumes helped, but it doesn't do much anymore. When I pull the PCM volume down to zero, I hear nothing but annoying crackling whenever audio is playing (as has been reported by others in this thread). However, ramping it up to the maximum doesn't help either, and I still hear a good deal of annoying crackling when listening to music.

Does anyone have any idea of what's actually causing this? I'd really like to fix it. I'm not sure PulseAudio is the culprit, because I shut it down to do music composition and I still hear crackling from programs like Renoise.

Thanks.

---

### Post by brookie on 2009-05-28
dont know if this is the same problem but i had a scratching sound when scrolling in firefox or dragging windows around
the noise came out of my inspiron 600 speakers but not the speakers i have plugged into my creative sound card
here's what i did: 
right click volume icon
open volume control
select the intel alsa mixer
click preferences
check the 'PMC Outpath & Mute' options box
a new options tap appears on your intel alsa volume control
click the options tab
slect 'post 3D

that's it! no more scratchy, crackly sounds when i scroll or drag windows
btw, i use Audigy 2zs Notebook OSS drivers in my Sound Preferences, beccause music using ALSA was choppy and crackly.

cheers,
brookie

---

### Post by HonzaPokorny on 2009-06-09
> **krawlx said:**
>  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me. 

Thanks! You guys rock!

---

### Post by BurnGates on 2009-06-09
Sound seems to be working fine on my machine, except when I shut down I get a lot of noise through my speakers. I am playing my sound out through a Cambridge Audio stereo amp - hope this won't get damaged...

---

### Post by tomasterisk on 2009-07-25
> **krawlx said:**
> Thanks for this thread.  It pointed me in the right direction to fixing the same problem.  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me.  As for the crackling sound...I assumed it was internal computer noise.  When I plug in my headphones to my laptop I get the same noise.  

Hope this helps someone in the future.

That is exactly what it did. Thanks!

I, also, had the same problem as you - and fixed it the same way, maxing the PCM slider.

Tom

---

### Post by iheartmuseums on 2009-08-05
> **krawlx said:**
> Thanks for this thread.  It pointed me in the right direction to fixing the same problem.  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me.  As for the crackling sound...I assumed it was internal computer noise.  When I plug in my headphones to my laptop I get the same noise.  

Hope this helps someone in the future.

Thanks for this, solved the problem I was having with ALSA crackling! Cheers.

---

### Post by epidemiks on 2009-10-01
> **rmkrishnan33 said:**
> This solved my problem too. Thanks for the help.

Mine too.

Why is it always the simplest things?

I was ready to smash and/or burn my computer before finding this thread!
:lolflag:

---

### Post by Brilovessand on 2009-11-06
wow. i did the PCM slide bar, and it FINALLY work. 
i miss windows...
:frown:

---

### Post by BaseEight on 2010-01-19
Thanks, that solved my problem as well.  The first time i noticed it was while playing Supertuxkart but I had played that game before with no issues.  Now I should probably set all my audio options back to their default settings.

Thanks for the help!
BaseEight

---

### Post by pirog on 2010-02-06
Hi guys,

I have Pulse and ALSA installed in Karmic and whenever I clicked on radio stations in Rhythmbox, first I'd hear crackling noise then the music. Only after installing OpenArena did I make it worse. Every time I'd click to shoot, there would be this annoying crackling noise.
I went to my GNOME Alsa Mixer and discovered, among all the usual options, "Digital" sound control. I turned it all the way down to zero and fired-up my OpenArena == No noise, only pure satisfaction in sound quality!

Hope it helps.

---

### Post by Chris Kupka on 2010-08-18
> **krawlx said:**
> Thanks for this thread.  It pointed me in the right direction to fixing the same problem.  My solution was this: right click on the speaker icon and select 'Open Volume Control.' Then, check the PCM slider.  Sliding it to the top fixed this problem for me.  As for the crackling sound...I assumed it was internal computer noise.  When I plug in my headphones to my laptop I get the same noise.  

Hope this helps someone in the future.

Wow, put off fixing this issue this summer cos I was busy and thought it'd be too time consuming.  In the end it took 5 seconds.  Unbelievable.

Thanks!

---

### Post by roy.nico on 2010-08-20
Hello, 

here is my own experience. I have been fighting a long time with crackly sound under lucid. I found the "solution" yesterdays : i removed the proprietary drivers for my nvidia onboard graphic card, reboot, and it was ok. Now, i can't have the nice 3D desktop effects, but at least i can hear music...

But why the graphics drivers interfere with the sound ... big mystery

nico

---

### Post by stephen730 on 2011-06-21
Okay, first off, I tried to hit the pcm down, up, and all that. It seemed to work but then, the crackle came back (amarok, last.fm, general sounds). 

What i did to fix this: Just clicked on the sound icon>sound preferences and thats it. It opened the window to the last tab, had ALSA Sound output under the APPLICATIONS tab and it went away. I did not TOUCH anything, and... it was in the middle of playing popping crackling music (danger - 00:01). In the middle of it, right after the window popped up it was gone. I repeat, i did not play with the sliders.

So yah. wtf.

---

### Post by Mech4troN on 2011-07-28
wow,awesome...it did help someone. Me! i must have been to the VolumeControl like 28 times and i overlooked the PCM slider totally. i guess connecting my iPhone to ubuntu and trying to get it to sync with Rhythmbox killed the sound somehow...that is the only explanation i can come up with...don't know why though,and no,the sync didn't work.and i have jaunty that is without support and iTunes i only tried to install once.didn't work.further help or advice is very very welcome.thanks ever so much!!

---

