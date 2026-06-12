---
title: "How to enable full HTML5 support on Firefox?"
date: 2015-10-25
forum: New to Ubuntu
---

### Post by remmas-sido on 2015-10-25
Hello guys 
I want to enable support for the following: 
1 - HTMLVideoElement
2 - H.264 
3 - WebM VP8
4 - Media Source Extensions
5 - MSE & H.264
6 - MSE & WebM VP9
Can someone give me a clear instructions about how to enable all of things listed above?
Thank you

---

### Post by Geoffrey_Arndt on 2015-10-25
What media app(s) do you already have installed?  Did you install the Ubuntu restricted-extras package?   Some of the things you listed are already supported by default in VLC (but I would install the package I referenced first).   I think the latest Firefox now enables html5/h.264 by default, but if you have flash plugin installed, it tries to use it first (less memory intensive).   

Anyway, I'm definitely not a media guru, but a little info about your system and what you've done or tried so far will help someone who might otherwise ignore this post?

---

### Post by Vladlenin5000 on 2015-10-25
[https://support.mozilla.org/en-US/kb/html5-audio-and-video-firefox](https://support.mozilla.org/en-US/kb/html5-audio-and-video-firefox)

---

### Post by remmas-sido on 2015-10-25
> **Geoffrey_Arndt said:**
> What media app(s) do you already have installed?  Did you install the Ubuntu restricted-extras package?   Some of the things you listed are already supported by default in VLC (but I would install the package I referenced first).   I think the latest Firefox now enables html5/h.264 by default, but if you have flash plugin installed, it tries to use it first (less memory intensive).   

Anyway, I'm definitely not a media guru, but a little info about your system and what you've done or tried so far will help someone who might otherwise ignore this post?

Do you mean that I should install VLC? or Totem restricted extras?

---

### Post by Geoffrey_Arndt on 2015-10-25
A good place to start is to install VLC and "Ubuntu Restricted Extras" (if not already done - - as that should be one of the first tweaks you do after an initial install of Ubuntu) (BTW - never heard of Totem restricted extras).   The media player Totem is often installed at install also, but that's your choice.

Also, check VladLenin5000's post re Mozilla Firefox plugins . . .

---

### Post by tristan16 on 2015-10-26
Can we PLEASE get a sticky somewhere for this? It's been discussed many times in many places: [https://askubuntu.com/questions/475351/firefox-html5-video-support](https://askubuntu.com/questions/475351/firefox-html5-video-support)

That link should give you all the information you need. If you need more details or different solutions, try this: [http://bfy.tw/2TnZ](http://bfy.tw/2TnZ)

---

### Post by masdeal on 2015-10-27
Open Firefox and go to about:config page. Then press the button which says &#8220;i&#8217;ll be careful, I promise&#8221;.


Then in the search box type media.media and hit enter. From the long list, look for the following and toggle them all to &#8216;true&#8217;:


media.fragmented.mp4.*
media.mediasource.enabled
media.mediasource.mp4.enabled


Be sure to leave the following set to false:
media.fragmented-mp4.use-blank-decoder

---

