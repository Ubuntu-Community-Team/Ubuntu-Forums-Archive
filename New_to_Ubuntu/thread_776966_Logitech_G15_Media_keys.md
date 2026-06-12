---
title: "Logitech G15 Media keys"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by bidget on 2008-05-01
Has anyone gotten these to work? I've followed numerous tutorials and managed to get the lcd to work, but unfortunately I couldn't care less about the lcd. All I really want is to be able to press play/pause and it play or pause xmms. I followed this tutorial:

[https://help.ubuntu.com/community/LogitechG15](https://help.ubuntu.com/community/LogitechG15)

But unfortunately it doesn't give the keycodes for any of the media keys. I've tried using things like xbindkeys, gnome keyboard shortcuts, and compiz's shortcuts. All I want to be able to do is bind the media keys to a simple command such as "xmms --play-pause" or "xmms --stop"

Anybody accomplished this? I've been trying to get it to work for quite a while now... :(

---

### Post by bidget on 2008-05-01
Oh I am also using the new 8.04, if that changes anything.

---

### Post by bidget on 2008-05-01
Bump... :(

---

### Post by SunnyRabbiera on 2008-05-01
well I am unsure about xmms, but there is a default tool you can possibly use to make the multimedia keys work for you, its in system> preferences under "keyboard shortcuts"

I dont know if that helps, but its worth a shot

---

### Post by bidget on 2008-05-01
I've already got all those keys bound. Maybe I have to somehow get the keyboard shortcuts app to recognize that xmms is my default music player? Anyone able to point me in the right direction here :(

---

### Post by SunnyRabbiera on 2008-05-02
> **bidget said:**
> I've already got all those keys bound. Maybe I have to somehow get the keyboard shortcuts app to recognize that xmms is my default music player? Anyone able to point me in the right direction here :(

well XMMS is a bit old, you may wish to play around with a integrated application like rhythmbox, or exaile.

---

### Post by trdc on 2008-05-02
Just to confirm, I used the same guide as you and Rhythmbox works perfectly. I don't particularly like xmms so can't help you with that.

---

### Post by bidget on 2008-05-02
Haven't tried rythmbox but I've tried exaile, amarok, audacious and  I also tried running winamp under wine but it didn't work very well. Audacious looked great and appeared to function exactly like winamp, but it didn't work. All of the others I intensely disliked. Is there no way to get my computer to recognize these media keys??

---

### Post by SunnyRabbiera on 2008-05-02
there might not be, media keys can be a little shaky.
rhythmbox seems to be a good choice for you though, if you didnt like those others... its kind of itunes like but its getting better.

---

### Post by bidget on 2008-05-02
Ugh I hate itunes :(

---

### Post by rubicon on 2008-05-02
Launch **xev** via console and in newly opened window try to press your MM keys. If you notice appropriate messages in console, then your keys are properly recognized by Xserver.

---

### Post by Benjamin_Vedder on 2008-05-04
hello

Hardy has drivers for g15 in the repos. Mine works fine with amarok. Just type sudo apt-get install g15daemon g15composer in the terminal, reboot, and then in amarok open tools > script manager and get more scripts. Install the scripts Gnome Mulrimedia keys and G15 amarok plugin plus and run them. Now you should be able to use the multimedia keys and the music you are playing should be shown in the display. Good luck. Tell me if it works.

---

### Post by bidget on 2008-05-04
I don't use amarok... Xev gives me the following output when I hit the play/pause button.


FocusOut event, serial 31, synthetic NO, window 0x3e00001,
    mode NotifyGrab, detail NotifyAncestor

FocusIn event, serial 31, synthetic NO, window 0x3e00001,
    mode NotifyUngrab, detail NotifyAncestor

KeymapNotify event, serial 31, synthetic NO, window 0x0,
    keys:  59  0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   
           0   0   0   0   0   0   0   0   0   0   0   0   0   0   0   0 

But where in there is code so I can bind the key to a command??

---

### Post by zeifertstc on 2008-12-03
I don't know if my solution will help anybody else in this topic but here goes. I haven't been too fond of xmms since Warty. As soon as Audacious hit the repos, I couldn't have been happier. Luckily, in 8.04 at least, there's a real easy way to get your Logitech G15 (V1 for me with 18 G keys) is to go into Audacious plugins. Click the "General" tab and select "Gnome Shortcuts". Close preferences and, voila, your next, previous, play/pause and stop keys should all work fine.

Also, if you have surround enabled (by default it is if you have 5.1 speakers, you just have to unmute your channels and make a .asoundrc file with a few lines of code), you can get your keyboard volume control to master control all channels at the same time.

Go to System -> Sound -> Devices

Find the channels you need to master with the keyboard control in the scrollable box at the bottom. Hold Ctrl and click each one. Close that box and test out your volume control as well. I did this within a few seconds of reading this thread.

So, thank you for pointing me in the right direction to solve this on my own and I hope my findings are beneficial to others as well. :)

---

### Post by LtPitt on 2008-12-17
Yipeee!

My g15 is just perfect now!

I just missed the volume (now it's 2:48 am in Italy).
I can sleep.

Happy.

:D

---

### Post by Vich on 2009-03-18
> **zeifertstc said:**
> I don't know if my solution will help anybody else in this topic but here goes. I haven't been too fond of xmms since Warty. As soon as Audacious hit the repos, I couldn't have been happier. Luckily, in 8.04 at least, there's a real easy way to get your Logitech G15 (V1 for me with 18 G keys) is to go into Audacious plugins. Click the "General" tab and select "Gnome Shortcuts". Close preferences and, voila, your next, previous, play/pause and stop keys should all work fine.

Also, if you have surround enabled (by default it is if you have 5.1 speakers, you just have to unmute your channels and make a .asoundrc file with a few lines of code), you can get your keyboard volume control to master control all channels at the same time.

Go to System -> Sound -> Devices

Find the channels you need to master with the keyboard control in the scrollable box at the bottom. Hold Ctrl and click each one. Close that box and test out your volume control as well. I did this within a few seconds of reading this thread.

So, thank you for pointing me in the right direction to solve this on my own and I hope my findings are beneficial to others as well. :)

OMG I love you! Actually, I'm just very happy that you shed light on that. Now I have my g15 display AND keys working exactly as I want :)

Thankyou!

---

