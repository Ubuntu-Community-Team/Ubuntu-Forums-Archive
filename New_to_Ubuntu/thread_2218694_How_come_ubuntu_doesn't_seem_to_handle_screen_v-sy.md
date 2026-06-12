---
title: "How come ubuntu doesn't seem to handle screen v-sync well?"
date: 2014-04-21
forum: New to Ubuntu
---

### Post by H7O on 2014-04-21
I tried running Ubuntu on nVidia Titan Black Edition, AMD R7 240x card, and built in Intel 3000/4000, all of them had some sort of v-sync problem with lots screen tearing in browsers and/or video players.

Anyone knows what's the underlying problem of this? I've seen many people complain about tearing in Ubuntu when I googled this issue. 

Is screen tearing a challenging issue with Linux platforms in general? I mean, do you guys face similar problems but learned to live with it? Or you don't mind screen tearing? Or it's just my luck that all of the video cards I tried somehow have tearing issues under Ubuntu?

Edit: here is a tearing test video to see whether or not your system has tearing related issues [http://www.youtube.com/watch?v=5xkNy9gfKOg ]("http://www.youtube.com/watch?v=5xkNy9gfKOg")
My Ubuntu 14.04 shows severe tearing in chrome and slight tearing in firefox with this test.

---

### Post by 23dornot23d on 2014-04-21
It seems its your first post - if you have had so many issues .... please point us to the links where you asked the questions beforehand.

Just one will do and we can see where the problem lies.

---

### Post by H7O on 2014-04-21
> **23dornot23d said:**
> It seems its your first post - if you have had so many issues .... please point us to the links where you asked the questions beforehand.

Just one will do and we can see where the problem lies.

You never had issues with tearing in ubuntu before? 

If so, what's your hardware specs? 

Also, open question to everyone, what is the most powerful and latest video card + motherboard that is properly supported by Ubuntu that I could buy?

Properly supported means having 5.1 audio and tear-free video via HDMI working properly without fiddling around with compiz / alsa / pulseaudio / browsers launch parameters / etc..

My problems are:
1- Any AMD / nVidia video card open source drivers don't know how to handle sound via HDMI (i.e. no sound). 
2- Any propriety drivers stutters and freezes the screen. 
3- All have tearing issues at one app or the other.

The only graphics chip that performs somewhat in a decent and reliable manner is the Intel 3000/4000 graphics chip. It works well (tear-free + 5.1 Audio via HDMI) with VLC and Firefox but not chrome or chromium. 

At the end, I really don't mind buying a specific system that could run Ubuntu (by default) properly. So I'd really appreciate if you guys could recommend something decent (not old and under-powered) and hassle free.

---

### Post by 23dornot23d on 2014-04-21
The question has changed to - what is the best system to buy to run surround sound ..... high resolution graphics onto a TV ........

Sort of makes me wonder why you started off that way - it comes across - Ubuntu is not going to suit my needs , but what would you use

it for ?

How much are you going to spend on it ........ ?

> 
At the end, I really don't mind buying a specific system that could run  Ubuntu (by default) properly. So I'd really appreciate if you guys could  recommend something decent (not old and under-powered) and hassle free.                 



[System76]("https://www.system76.com/") I keep hearing a lot about ....... but I have never had one ........ but they tend to be made to suit Linux.

---

### Post by H7O on 2014-04-21
> **23dornot23d said:**
> The question has changed to - what is the best system to buy to run surround sound ..... high resolution graphics onto a TV ........

Sort of makes me wonder why you started off that way - it comes across - Ubuntu is not going to suit my needs , but what would you use

it for ?

How much are you going to spend on it ........ ?

[System76]("https://www.system76.com/") I keep hearing a lot about ....... but I have never had one ........ but they tend to be made to suit Linux.

You seem overly sensitive about my question. Focusing more on questioning the legitimacy of the question rather than the question itself.
 
I don't know what caused this, but nevertheless let me just explain the reasoning behind my question so we could hopefully get passed questioning the intentions behind it.

My question comes after many attempts to fix this tearing issues by searching forums and applying many recommended solutions offered to others facing the same issue, but nothing worked for several video cards I've tried.

This lead me to the conclusion that this is potentially a widespread issue. But to be absolutely sure and fair, I wanted to ask if it is indeed a widespread issue, hence my original post.

If people answered my post with "no, we never faced issues with tearing" then I would've followed up with a question of "what hardware you're using?".

And the reason why I'm interested in what hardware that works best, stems from my dis-interest in continuing my hunt for solving the tearing issues in my hardware.

I don't know if the system you linked would have tearing issues or not, but what I'm really really interested to know (if I may ask) is do you see tearing effect in videos / youtube in chrome in your ubuntu setup?

---

### Post by 23dornot23d on 2014-04-21
I tried running Ubuntu on nVidia Titan Black Edition - solution below

[http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu1404/](http://ubuntuhandbook.org/index.php/2014/04/install-nvidia-driver-331-67-ubuntu1404/)

__________________________________________

There is a bug on certain legacy Intel 3000/4000

[https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379](https://bugs.launchpad.net/ubuntu/+source/fglrx-installer/+bug/1276379)

____________________________________

AMD R7 240x card - solution below .....

[http://ubuntuforums.org/showthread.php?t=2213035](http://ubuntuforums.org/showthread.php?t=2213035)

____________________________________

> 
And the reason why I'm interested in what hardware that works best,  stems from my dis-interest in continuing my hunt for solving the tearing  issues in my hardware.


Type in a terminal - and post back the results please.

**lspci -v**

---

### Post by H7O on 2014-04-22
I've tried the nVidia solution you linked before and it didn't work for me.

The Intel graphics had the most stable out of the box drivers (except for tearing in chrome).

The catalyst 14.3 drivers mentioned in your AMD fix link have lots of problems with stutter and freezing.

---

### Post by Impavidus on 2014-04-22
For what it's worth, I haven't had any graphics problems in a long time. But then, I just have an ordinary laptop, nothing very powerful.

When new hardware is released to the market, it usually take a while before it is properly supported by Linux. That's because manufacturers provide good Windows drivers at introduction, but not the Linux drivers. Sometimes you just have to wait some months for the bugfixes in the drivers.

I never tried sound over hdmi.

---

### Post by sandyd on 2014-04-22
Closed for review.

---

### Post by Elfy on 2014-04-22
re-opened - keep this on-topic please

---

### Post by H7O on 2014-04-22
> **Impavidus said:**
> For what it's worth, I haven't had any graphics problems in a long time. But then, I just have an ordinary laptop, nothing very powerful.

When new hardware is released to the market, it usually take a while before it is properly supported by Linux. That's because manufacturers provide good Windows drivers at introduction, but not the Linux drivers. Sometimes you just have to wait some months for the bugfixes in the drivers.

I never tried sound over hdmi.

Many thanks for the response. May I trouble you to try playing this tearing test video on youtube in chrome full screen mode?

[http://www.youtube.com/watch?v=5xkNy9gfKOg](http://www.youtube.com/watch?v=5xkNy9gfKOg)

Do you see tearing in the scrolling columns?

P.S. I've honestly just upgraded few hours ago my Ubuntu box to Core i5 4670k + new Mini ATX Gigabyte MB as I thought Intel 4600 graphics chip could solve the issue (seeing how my older Intel graphics chip fared better than my nVidia and ATI dedicated cards), but the tearing issue after the upgrade seems to persist in chrome.

---

### Post by Old_Grey_Wolf on 2014-04-22
It get a little tearing in Chrome in full screen mode; however, Firefox works fine in full screen mode. That is using the Youtube you linked to.

Seems it is not the drivers in Ubuntu but the browsers.

Edit: 10 seconds into the Youtube video the screen stops tearing in Chrome.

---

### Post by H7O on 2014-04-23
> **Old_Grey_Wolf said:**
> It get a little tearing in Chrome in full screen mode; however, Firefox works fine in full screen mode. That is using the Youtube you linked to.

Seems it is not the drivers in Ubuntu but the browsers.

Edit: 10 seconds into the Youtube video the screen stops tearing in Chrome.

Thank you so much, I knew I wasn't crazy to think there is a potential of having a large number of users (if not all) experience this and not just me.

Btw, The first 10 seconds is important as the scrolling moves at slow speed making the tearing very visible. Firefox might still has it, but it's a bit more difficult to detect.

p.s. The scrolling also keeps changing speeds throughout the video.

---

### Post by QIII on 2014-04-23
Hmmm...

No tearing in FF.  Don't have Chrome or Chromium.

I have Catalyst set for tear-free and quality graphics, though.

What I ***do ***get is some stuttering in full screen, but that seems to be our lot in Linux with the old version of Flash we have.

---

### Post by H7O on 2014-04-23
> **QIII said:**
> Hmmm...

No tearing in FF.  Don't have Chrome or Chromium.

I have Catalyst set for tear-free and quality graphics, though.

What I ***do ***get is some stuttering in full screen, but that seems to be our lot in Linux with the old version of Flash we have.
Thank you so much and you're absolutely right about the stutter. However, I believe it's not flash related though (it persist if you somehow download the video and play it back via VLC).

---

### Post by Old_Grey_Wolf on 2014-04-23
There is the "potential" that I "might" get tearing if I ran the same test with Windows booted on this hardware. I am not going to try it as I would spend an hour updating Windows in the middle of the night.

---

### Post by H7O on 2014-04-23
> **Old_Grey_Wolf said:**
> There is the "potential" that I "might" get tearing if I ran the same test with Windows booted on this hardware. I am not going to try it as I would spend an hour updating Windows in the middle of the night.

Don't worry, fortunately, chances are you won't. Not in Windows, OSX, iOS. This problem seems exclusively to Linux (or at least Ubuntu, as I haven't tried other desktop flavors of Linux).

---

### Post by Impavidus on 2014-04-23
Some tearing in firefox, both using flash and html5. Never noticed it in other videos. I don't have chrome or windows, so I can't compare.

---

### Post by 3rdalbum on 2014-04-23
There is a little bit of tearing on all platforms that use X11. Unfortunately it will only be resolved in the next generation of display servers which are Mir and Wayland.

Most Linux users don't notice the tearing. I rarely do.

---

### Post by H7O on 2014-04-23
> **3rdalbum said:**
> There is a little bit of tearing on all platforms that use X11. Unfortunately it will only be resolved in the next generation of display servers which are Mir and Wayland.

Most Linux users don't notice the tearing. I rarely do.

Thanks, That was really helpful. Put me at ease that it's not about my choice of hardware. 

I've googled "X11 screen tearing" and came across this redddit post [http://www.reddit.com/r/linux/comments/zz338/does_your_xorg_flickertear/](http://www.reddit.com/r/linux/comments/zz338/does_your_xorg_flickertear/)

Will hopefully give it a read later tonight to see if I could find some solution.

---

