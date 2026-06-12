---
title: "[SOLVED] cnn.com live video wont play"
date: 2008-06-01
forum: New to Ubuntu
---

### Post by chchandler on 2008-06-01
I can play the videos available, except for the live streaming ones.  I even tried using Totem movie player and directing it to open the location of the stream and it just sits there.

Has anyone else had any luck playing the CNN live streaming video?

FWIW, this is what WON'T work:

[http://www.cnn.com/video/live/live.html?stream=stream2](http://www.cnn.com/video/live/live.html?stream=stream2)

All of these DO work:

[http://www.cnn.com/video/#/video/living/2008/05/30/dnt.fl.single.moms.lawn.care.wbbh](http://www.cnn.com/video/#/video/living/2008/05/30/dnt.fl.single.moms.lawn.care.wbbh)

Any help appreciated!!

---

### Post by ajgreeny on 2008-06-01
No, I can't get it to play either.  It gives an error message saying "Stream can not be reached.  See FAQ"   The FAQ are [here]("http://edition.cnn.com/help/live.html") so may help you more.[URL="http://edition.cnn.com/help/live.html"]
[/URL]

---

### Post by chchandler on 2008-06-01
Yes, I had read them.  Not much help.  I've also posted a message using their technical issues form, I'll post here if I get a reply.

---

### Post by papsynot on 2008-08-01
this worked for me:


sudo apt-get install mplayer

mplayer -vo x11 -playlist [http://www.cnn.com/video/live/cnnlive_1.asx](http://www.cnn.com/video/live/cnnlive_1.asx)
mplayer -vo x11 -playlist [http://www.cnn.com/video/live/cnnlive_2.asx](http://www.cnn.com/video/live/cnnlive_2.asx)
mplayer -vo x11 -playlist [http://www.cnn.com/video/live/cnnlive_3.asx](http://www.cnn.com/video/live/cnnlive_3.asx)
mplayer -vo x11 -playlist [http://www.cnn.com/video/live/cnnlive_4.asx](http://www.cnn.com/video/live/cnnlive_4.asx)

1,2,3,4 depends whether they're streaming those extra live feeds.

---

### Post by tuxxy on 2008-08-01
damn I got stream error too

---

### Post by PlanetT on 2008-09-18
Hi All!

I've just received the following reply from cnn support:

"CNN.com Live Video is not currently available for Linux users because of the Windows Media elements.  While we don't have a specific date when it will be compatible with your platform, we will make your request known to the development team.

Thanks for your interests in CNN.com video content.

Sincerely,


CNN.com Technical Operations
"

That's sucks!

---

### Post by bikerider42 on 2008-09-18
vlc will play it! just add the stream and it plays.... there was a post about this not long ago... hope it helps

---

### Post by djinn1973 on 2008-10-02
> **bikerider42 said:**
> vlc will play it! just add the stream and it plays.... there was a post about this not long ago... hope it helps

No,it wont...

---

### Post by seaq on 2008-11-04
I'm watching it right now (elections pipeline) using this feed:


[http://www.cnn.com/video/live/cnnlive_1.asx](http://www.cnn.com/video/live/cnnlive_1.asx)


and using totem

Directly from the website it didn't worked, but as stated in some other thread using the url worked like a charm.

The original thread uses vlc, in my case i'm with totem, also i've got ubuntu-restricted-extras  installed.

---

### Post by spawn. on 2008-11-04
...wow..CNN Live is getting pwned by Fox News on election coverage.

---

### Post by fooman on 2008-11-04
i got the stream error as well,  but at the bottom of the window is a message..."you have flash intalled,  try our flash beta player now".

when i click on that,  flash10 plays it.  :)

---

### Post by jlo_sandog on 2008-11-07
CNN now has a Flash based player (CNN.com Live Beta). It won't work if it detects Linux on the  agent string. If you spoof the user agent string with a Mac string such as the one below the player will work. You need Flash 10.

Mozilla/5.0 (Macintosh; U; Intel Mac OS X 10.5.1; en-US;rv:1.9.0.1) Gecko/200871615 Firefox/3.0.1

---

### Post by KrazyPenguin on 2008-11-11
Just wanted to add that I can NOW watch CNN Live directly.

Here is what I am using:

Ubuntu 8.10 / Firefox 3.0.3

and Adobe Flash Beta 10.xx.xx.

This is great news, another step in the right direction for LINUX!!!


:guitar:

---

### Post by chchandler on 2008-11-11
Yup, I installed the Adobe Flash 10 and it works.  I'm marking this one closed!!!!

KrazyPengiun is right... another step inthe right direction for Linux.

---

### Post by rshel on 2008-12-13
I have flash 10 installed.  No luck playing any cnn video even after following the main a/v sticky.

---

### Post by PC_load_letter on 2009-03-08
I don't know about you guys, but for the life of me I still can't watch CNN videos. Neither on Opera 9.64, nor with FF 3.0.7 with Shockwave Flash 10.0 r22. Youtube vids. run perfectly fine.

I am running 32bit Ubuntu 8.10. 

Any ideas how to fix this?

---

