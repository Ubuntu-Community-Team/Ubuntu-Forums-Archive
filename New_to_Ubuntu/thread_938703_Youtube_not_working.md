---
title: "Youtube not working"
date: 2008-10-05
forum: New to Ubuntu
---

### Post by fredscripts on 2008-10-05
Hi!!

When I'm gonna play some video on youtube...

Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player. 

I've clicked the link and followed the tar.gz install instruccions of the adobe's website.

Then I open firefox again but still not working.

I also installed from the add/remove the Macromedia Flash package. No luck.


Any suggestions? :(

---

### Post by ggaaron on 2008-10-05
Use the repositories and synaptic to install flash, adobe flash is named flash-nonfree I think, GNU flash player is gnash.

---

### Post by billgoldberg on 2008-10-05
Open up a terminal and copy/paste this.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

You will need to type your password (you won't see what you type) and press enter. It could be that you'll need to press enter a few during the process.

Besides flash, this will install some other codecs you will most likely need at some point.

---

### Post by shifty_powers on 2008-10-05
```
sudo apt-get install ubuntu-restricted-extras
```

will install flash and lots of other very useful things... :D

---

### Post by ENigma885 on 2008-10-05
u need to install flashplugin and flashsupport u can easily open a terminal window *(Applications >> Accessories >> Terminal)* then paste 
```
sudo apt-get install flashplugin-nonfree libflashsupport

```

---

### Post by billgoldberg on 2008-10-05
> **ENigma885 said:**
> u need to install flashplugin and flashsupport u can easily open a terminal window *(Applications >> Accessories >> Terminal)* then paste 
```
sudo apt-get install flashplugin-nonfree libflashsupport

```

Whatever you do, don't install libflashsupport.

If you have problems, switch to ALSA (go to sound -> preferences -> sound and switch everything to ALSA).

---

### Post by ENigma885 on 2008-10-05
> **billgoldberg said:**
> Whatever you do, don't install libflashsupport.

If you have problems, switch to ALSA (go to sound -> preferences -> sound and switch everything to ALSA).

libflashsupport is a support library for sound output of Flash 9+ with PulseAudio. In many cases the Flashplugin alone has some incompatibilities with the PulseAudio output. This package resolves this issue.

And switching to ALSA is **not** a solution. It will only make other problems with other PulseAudio application.

*_I recommend_* installing the 2 packages, in my previous post, and go to *System >> Prefer.>> Sound * and select PulseAudio. Personally i use this configuration and everything including flashes works fine and even better simultaneously with other outputs. So i don't have to stop other applications using the sound device via PulseAudio.

---

### Post by fredscripts on 2008-10-05
> **billgoldberg said:**
> Open up a terminal and copy/paste this.
```

sudo wget http://www.medibuntu.org/sources.list.d/hardy.list -O /etc/apt/sources.list.d/medibuntu.list && wget -q http://packages.medibuntu.org/medibuntu-key.gpg -O- | sudo apt-key add - && sudo apt-get update && sudo apt-get install -y ubuntu-restricted-extras non-free-codecs w32codecs totem-mozilla libdvdcss2
```

You will need to type your password (you won't see what you type) and press enter. It could be that you'll need to press enter a few during the process.

Besides flash, this will install some other codecs you will most likely need at some point.

Thanks you all for answering!!

I've run this command in the terminal and then restart firefox to check youtube...but the message


Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

when I try to watch any video still appears.

:(

---

### Post by Bucky Ball on 2008-10-05
Synaptic package manager:

**ubuntu-restricted-extras**

---

### Post by billgoldberg on 2008-10-05
> **fredscripts said:**
> Thanks you all for answering!!

I've run this command in the terminal and then restart firefox to check youtube...but the message


Hello, you either have JavaScript turned off or an old version of Adobe's Flash Player. Get the latest Flash player.

when I try to watch any video still appears.

:(

That should have installed the flash player.

Go to your home folder.

Press "ctrl+h". You will now see all hidden folders.

Search for the ".mozilla" folder.

Open it, you'll see a plugins folder

There should be a file calle "libflashplayer.so" in it.

If there is one and youtube still doesn't work, make sure you haven't disabled javascript in firefox.

--

You might want to give Flash Player 10 RC a try:

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

--

About libflashsupport, I know what it is and still advice you not to install it.

Switching to ALSA is a good solution.

Just because you don't have problems with it doesn't mean others won't have.

I myself, together with loads of others had serious problems with libflashsupport causing crashes.

---

### Post by fredscripts on 2008-10-05
> **billgoldberg said:**
> That should have installed the flash player.

Go to your home folder.

Press "ctrl+h". You will now see all hidden folders.

Search for the ".mozilla" folder.

Open it, you'll see a plugins folder

There should be a file calle "libflashplayer.so" in it.

If there is one and youtube still doesn't work, make sure you haven't disabled javascript in firefox.

--

You might want to give Flash Player 10 RC a try:

[http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/](http://linuxowns.wordpress.com/2008/08/12/install-flash-player-10-rc-on-ubuntu/)

--

About libflashsupport, I know what it is and still advice you not to install it.

Switching to ALSA is a good solution.

Just because you don't have problems with it doesn't mean others won't have.

I myself, together with loads of others had serious problems with libflashsupport causing crashes.

Yes there is the "libflashplayer.so" in the plugins folder.

How can I see the javascript stuff??

Thanks!

---

### Post by billgoldberg on 2008-10-05
> **fredscripts said:**
> Yes there is the "libflashplayer.so" in the plugins folder.

How can I see the javascript stuff??

Thanks!

--

In firefox, go to

"edit -> preferences".

Click the "content" button on the top.

There you can see if javascript is on or not.

If it is on and still doesn't work, try logging out and back in.

Or type 

```
killall firefox 
```

in a terminal.

Then try again.

---

### Post by fredscripts on 2008-10-05
Ok just found it, edit preferencies and then a box with Enable javascript. It is activated.



What's happening?? :S

---

### Post by billgoldberg on 2008-10-05
> **fredscripts said:**
> Ok just found it, edit preferencies and then a box with Enable javascript. It is activated.



What's happening?? :S

Read the post above yours.

If logging in and out doesn't work, than I the only thing I can suggest is you try the link I gave on the previous page for flash player 10.

---

### Post by fredscripts on 2008-10-05
Yep my mistake :). I killall firefox and then open it again and I can watch the videos...but without sound :S, I can listen to the mp3 of my hard drive trhough rythmbox, so the sound is working.


I remember having the same youtube-sound issue in 7.10. It seems that firefox doesn't like external soundcard plugged by USB.

Will try to recover the post I opened of that issue one year ago. If there's no solution yet, unfortunately will have to go back to windows one year more :(

---

### Post by billgoldberg on 2008-10-05
> **fredscripts said:**
> Yep my mistake :). I killall firefox and then open it again and I can watch the videos...but without sound :S, I can listen to the mp3 of my hard drive trhough rythmbox, so the sound is working.


I remember having the same youtube-sound issue in 7.10. It seems that firefox doesn't like external soundcard plugged by USB.

Will try to recover the post I opened of that issue one year ago. If there's no solution yet, unfortunately will have to go back to windows one year more :(

Read the suggestions here:

[http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/](http://linuxowns.wordpress.com/2008/05/07/hardy-sound-problems-2/)

---

### Post by fredscripts on 2008-10-05
oh WOW!!! just run "sudo apt-get install libflashsupport" and now I have sound both youtube and the system!! :D:D

Thank you all very much for your help!!!

Now let's see if I can fix some Bittorrent issues and I can move definitely to the Ubuntu world :)

---

### Post by billgoldberg on 2008-10-05
> **fredscripts said:**
> oh WOW!!! just run "sudo apt-get install libflashsupport" and now I have sound both youtube and the system!! :D:D

Thank you all very much for your help!!!

Now let's see if I can fix some Bittorrent issues and I can move definitely to the Ubuntu world :)

If you have stability issues with flash on firefox, remove libflashsupport and switch your sound to ALSA.

Anyway, glad you got your problem fixed.

If you would be so kind to mark the thread as solved.

Thanks.

---

### Post by Bucky Ball on 2008-10-05
> **fredscripts said:**
> 

Now let's see if I can fix some Bittorrent issues and I can move definitely to the Ubuntu world :)

Have your tried Transmission under Applications->Internet?

---

### Post by ENigma885 on 2008-10-05
> **billgoldberg said:**
> 
About libflashsupport, I know what it is and still advice you not to install it.

Switching to ALSA is a good solution.

Just because you don't have problems with it doesn't mean others won't have.

I myself, together with loads of others had serious problems with libflashsupport causing crashes.

looks like libflashsupport is still needed.

ALSA will prevent the PulseAudio access to the sound device. And it looks illogical to work around the default sound server as long as it works fine and there's a right way to configure it properly.

> **fredscripts said:**
> oh WOW!!! just run "sudo apt-get install libflashsupport" and now I have sound both youtube and the system!! :D:D


That's wat i called > **ENigma885 said:**
> 
....and even better **_simultaneously_** with other outputs. So i don't have to stop other applications using the sound device via PulseAudio.

anyway...it's fixed now

---

### Post by fredscripts on 2008-10-05
> **billgoldberg said:**
> If you have stability issues with flash on firefox, remove libflashsupport and switch your sound to ALSA.

Anyway, glad you got your problem fixed.

If you would be so kind to mark the thread as solved.

Thanks.

Oh man just gonna post it. I have terrible stability issues. Firefox crashes every 5 minutes.

Would try to remove libflashsupport. What do you mean to switch my sound to ALSA? On system Sound, on Defaul Mixer Tracks, in Device I have: Playback: ALSA PCM on front: 1(USB Audio) via DMA...

The other options are:

Sound Blaster MP3+ (Alsa mixer)
Capture: ALSA PCM on front: 1(USB Audio) via DMA...
Capture: Monitor source of ALSA PCM on font: 1(USB...


the "..." means that I cannot read more lol


Any suggestions?

Thanks again!

---

### Post by gandaran on 2008-10-05
> **fredscripts said:**
> Oh man just gonna post it. I have terrible stability issues. Firefox crashes every 5 minutes.

Would try to remove libflashsupport. What do you mean to switch my sound to ALSA? On system Sound, on Defaul Mixer Tracks, in Device I have: Playback: ALSA PCM on front: 1(USB Audio) via DMA...

The other options are:

Sound Blaster MP3+ (Alsa mixer)
Capture: ALSA PCM on front: 1(USB Audio) via DMA...
Capture: Monitor source of ALSA PCM on font: 1(USB...


the "..." means that I cannot read more lol


Any suggestions?

Thanks again!

theres another way to fix the flash sound problem, remove libflashsupport and flash 9 and install flash 10, flash 10 fixes the flash/pulseaudio bug
just make sure you got the latest firefox update (3.0.3) and get the flash 10 here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

---

### Post by fredscripts on 2008-10-05
> **gandaran said:**
> theres another way to fix the flash sound problem, remove libflashsupport and flash 9 and install flash 10, flash 10 fixes the flash/pulseaudio bug
just make sure you got the latest firefox update (3.0.3) and get the flash 10 here [http://labs.adobe.com/downloads/flashplayer10.html](http://labs.adobe.com/downloads/flashplayer10.html)

Thanks for answering!!

Sorry for newbie questions but...:

How can I check my firefox version? any firefox -v command?


How can I remove flash 9? Because as you may have seen in this thread , I ve downloaded and installed a lot of things!!!

---

### Post by gandaran on 2008-10-05
> **fredscripts said:**
> Thanks for answering!!

Sorry for newbie questions but...:

How can I check my firefox version? any firefox -v command?


How can I remove flash 9? Because as you may have seen in this thread , I ve downloaded and installed a lot of things!!!

firefox version; toolbar » help » about mozilla firefox 
remove flash; open synaptic package manager, scroll down to **flashplugin-nonfree** and **libflashsupport** mark for complete removal and click the apply button, look also if you have any other flash installed like gnash or swfdec
did you install any other flash package? like the adobe tarball?

make sure you have removed all flash before installing flash 10, you can do that by simply playing a flash video, if you see the missing plugins message it means it is completely removed.

---

### Post by fredscripts on 2008-10-05
Thanks for the help.

I did install all the packages the people told me on this thread.

I'm writing down this steps to update to flash 10. However, now I've been running firefox for more than half an hour without any kind of issue. I will wait two or three days (now that everything is running fine, why take the risk hehe you understand).

---

