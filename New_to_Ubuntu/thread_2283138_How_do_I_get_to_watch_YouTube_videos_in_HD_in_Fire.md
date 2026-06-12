---
title: "How do I get to watch YouTube videos in HD in FireFox?"
date: 2015-06-19
forum: New to Ubuntu
---

### Post by AkwatiKata on 2015-06-19
I am so happy my Ubuntu installation succeeded the way I wanted it to, however... when I went to YouTube to see if my video drivers work, I noticed I could not watch videos in higher than 360p.
So I searched around and found something about needing to install the GreaseMonkey add-on, but that was an old post (2009) and it didn't seem to work.
Then I installed YouTube and that did give HD, but somehow I couldn't go to full screen and worse, much much much worse, my AdBlock and Ghostery don't work on it and I am forced to watch ads!
So there are two options: 1- watch YouTube videos in HD through Firefox, thus keeping my eyeballs and immortal soul free from ads, or 2- get the YouTube program to go full screen and somehow block the eyeball shattering and soul crushing ads (gah... I feel so dirty now I saw a YouTube ad:frown:)

ps: I am a total Ubuntu noob, so any solution that doesn't include writing command lines is welcome; thanks!

---

### Post by dino99 on 2015-06-19
which graphic card/chipset is it ? (a tiger or a cat ?)

---

### Post by AkwatiKata on 2015-06-21
NVIDIA GeForce 9500m GS
But it's like I said, through the YouTube application I can watch videos in HD. I have also installed the open source drivers for my GPU, so I don't get it; does Firefox have a problem recognizing my GPU?

---

### Post by Bucky Ball on 2015-06-21
You installed the open-source driver, but are you using it? If you haven't switched the nvidia one off or uninstalled it (did you install it via Additional Drivers or enable third-party repos at boot?) you either are probably still using it or, if you never installed it in the first place, you already are using the open source driver and have been. 

Let's see the result of this command in a terminal, thanks:

```
sudo lshw -C video
```

Post the output here between code tags (see last link in my signature).

---

### Post by Vladlenin5000 on 2015-06-21
Your open source drivers are already installed and in use. You wouldn't have video at all otherwise. You might have installed proprietary drivers and that's actually the recommended for your nvidia card.
Make sure you use HTML5, not Flash, in [Firefox]("https://support.mozilla.org/en-US/kb/html5-audio-and-video-firefox"). HTML5 is the current standard for Youtube and all other major similar services.

---

### Post by AkwatiKata on 2015-08-16
Late reply; I was on a long vacation.
Vladlenin5000 is right; I couldn&#8217;t watch any videos if my video card wasn&#8217;t installed correctly. I think it's a Firefox issue because, as I've said, when I install the YouTube app I can watch videos in HD through it. However, it won't go full screen and worse, it shows ads and assorted horrors. So how do I get Firefox to show HD videos? Vladlenin5000 says to make sure my Firefox uses HTML5. How? I checked the link you gave, but I couldn't find the relevant information. Then I installed the Firefox extension "YouTube ALL HTML5" to no avail. I also checked in Firefox Tools>Add-ons>Plugins and there was no Flash there. There was no Flash in Tools>Add-ons>Extensions either.
Now I'm more confused than before.

---

### Post by Vladlenin5000 on 2015-08-16
I've been installing many machines, old and new, and as long as the graphics subsystem is working properly (proprietary drivers are often required) there's nothing you need to do to have Youtube working beautifully in FF out of the box (in the now default HTML5), FullHD, fullscreen, etc.

---

### Post by Dennis N on 2015-08-16
As Vlad says, HTML5 is the default format now. No flash is used if your browser supports it. You won't be blocking ads if they are embedded in the presentation. Google wants to make money. Not all videos are HD. Some are old stuff in lower resolution - ancient music videos from the 80s for example. Are you sure HD is one of the quality options available for the particular video?

---

### Post by mc4man on 2015-08-16
You could go here & ck., at least 5 out of the 6 should be enabled, the 6th (MSE & H.264) can be done but require creating a new preference
[https://www.youtube.com/html5](https://www.youtube.com/html5)

---

### Post by tristan16 on 2015-08-16
I found a solution for this a couple days ago. You can enable HD YouTube videos in Firefox on Ubuntu with 2 simple steps!

1. Go to [www.youtube.com/html5](www.youtube.com/html5) and request the HTML5 player (you can skip this if you don't have Flash Player installed).

2. Go to about:config in Firefox, and double-click these settings to change them to "true"

```

media.mediasource.enabled
media.mediasource.webm.enabled

```

Once you change these to "true", you should be able to get HD YouTube videos. Otherwise you could always install Adobe Flash Player and request that player.

---

### Post by AkwatiKata on 2015-08-17
*******!!!! I'm trying to upload the screen shot and that doesn't work either!
Anyway, it says I only have HTMLVideoElement and WebM VP8 active. The others are red.

---

### Post by howefield on 2015-08-17
> **AkwatiKata said:**
> *******!!!! I'm trying to upload the screen shot and that doesn't work either!

See your pm.

Use the paperclip icon in the posting window to attach an image to your post.

---

### Post by AkwatiKata on 2015-08-17
this

---

### Post by mc4man on 2015-08-17
Run this to get .h264 enabled
```
sudo apt-get install gstreamer1.0-libav
```

For mediasource vp9 you need to enable 2 options in FF, go in address bar
```
about:config
```
search media.mediasource, set the 2 bold options in screen to true (double l. click on false in the Value column to change

---

