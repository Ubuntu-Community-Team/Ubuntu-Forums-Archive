---
title: "Going Flashless?"
date: 2012-01-27
forum: New to Ubuntu
---

### Post by Javelin Dan on 2012-01-27
Please bear with me as this is more of an Ubuntu question than an Apple user&#8217;s question. I just got done installing and setting up Ubuntu 10.10 Powerpc on my wife&#8217;s eMac G-4. I have to say I&#8217;m more than pleased with everything so far, except of course the fact that I&#8217;m not able to run Flash videos &#8211;knew this going in. I installed Download Helper and am able to run anything on YouTube through several media players (VLC works awesome!), but there are other types of videos, for instance some tutorial videos, I can&#8217;t play (Download Helper tells you this). I scoured the Ubuntu forums and also online, and saw that supposedly VLC in conjunction with the &#8220;Flash Replacer&#8221; plug-in should work with about anything (did I get that right?). So I disabled Download Helper (should I have uninstalled it?), installed Flash Replacer, and I did get the Flash Replacer icon in the right hand corner of the toolbar. But it doesn&#8217;t animate, or spin, or whatever it&#8217;s supposed to do to let you know that it is enabled. I&#8217;m thinking either I&#8217;m not doing something right (an EXTREME possibility) or maybe I&#8217;ve got some competing software, or something. Is there a way to deal with this without a lot of command-line shenanigans since I suck at that? I could sure use some advice from anyone who knows more about this than I do. Thanks.

---

### Post by darckwolff on 2012-01-27
Do you honestly not want to use any form of flashplayer? There GNASH, Adobe, and others available that would let you do it right on the browser.

---

### Post by Javelin Dan on 2012-01-27
Please enlighten me...

---

### Post by Javelin Dan on 2012-01-27
I guess I should expand. I looked in the repository and Gnash is already installed &#8211; nothing plays. I saw a post on a past forum where someone suggested using gnash in conjunction with Lightspark. Not sure, but I believe this may be a Windoze-machine only option. I couldn&#8217;t find it in my (powerpc) repository. I don&#8217;t really care if I have Flash or don&#8217;t, I just want to be able to play videos. The VLC route would suite me fine if I can make it play anything. Can I?

---

### Post by evilsoup on 2012-01-27
In the Ubuntu Software Centre, search for 'flash player' (without the quotes) and you'll see a big list of options.

I personally use 'Adobe Flash plugin 10', and have had no problems playing youtube videos, and very few problems with other websites. Other people have ideological objections to using closed-source software, and they instead use GNASH, which is inferior in all comparisons I've heard (because of Adobe's probably-illegal EULA scaring away most potential developers). There is also something called 'Lightspark', I have no knowledge about that though.

But anyways, the point is you can easily have flash on Ubuntu.

EDIT: Ooo I didn't realise that powerPC ubuntu has different repositories, nevermind.

---

### Post by andrew.46 on 2012-01-27
You have had a look at this:

[http://www.youtube.com/html5](http://www.youtube.com/html5)

?

---

### Post by Frogs Hair on 2012-01-27
I ran without flash on an old computer because the CPU requirements for flash began to exceed the  processors capabilities  . I could live without videos , but it got to the point where it wasn't possible to use some websites .

---

### Post by Javelin Dan on 2012-01-27
Andrew.46  - Yeah, I've seen some  stuff on HTML5 and that looks to be the wave of the near future, but right now it would just give me what I already have; a format that plays some videos but not all.  The Download Helper / VLC thing is probably better for me at this point because it will play all Flash videos - just not some other ones.

Frogs Hair - This computer is no slouch...it absolutely rocks with Ubuntu 10.10, and the videos it does play through VLC look way better than anything I've seen on Flash. I was just wondering if there's a way to get _*everything*_  to run. I also worried about being able to get on some sites, particularly my wife's on-line banking site (she couldn't access all pages with OS 10.3 Panther and the old version of Firefox it ran), but it works great with Ubuntu.  If I can just resolve the video thing I'll be happy as a clam that's buried in the sand where no one's diggin' for it!

---

### Post by Frogs Hair on 2012-01-27
I wasn't doubting your computers capabilities just pointing out that it can be difficult get services on some sites without flash . It really depends on what sites you need to interact with .

---

### Post by Javelin Dan on 2012-01-29
[FONT=Arial]Well, sort of solved - at least I’ve achieved a compromise that I find acceptable. Here’s what I did:[/FONT]

    [FONT=Arial]I went back into the synaptic package manager where as stated before, I found “gnash” already installed. I also installed “gnash-common” and “browser-plug-in-gnash”. I will freely admit that I had no idea what I was doing at this point, I was just pressing buttons. I then went back into Firefox “plug-ins” and unistalled everything that I had disabled except “Download Helper” which I enabled again. I restarted Firefox, tried Youtube and then a tutorial video that I couldn’t previously open. and low and behold I had Flash! Admittedly, it’s crappy Flash - slow to start, runs choppy and starts and stops, but at least I can apparently open any page with Flash content. Download Helper works as before so if I’m on a page where that runs I have the option of downloading it and running it through Media Player or VLC (far and away my best choice!). So it’s a compromise to be sure, but at least it’s one I can live with indefinitely. When HTML5 becomes more main-stream, I’ll certainly employ that but for now I’m OK with it. I continue to monitor this thread for a week or two in case anyone weighs in with a better idea. Thanks to all who responded. [/FONT]

---

