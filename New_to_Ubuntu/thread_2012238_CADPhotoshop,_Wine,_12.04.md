---
title: "CAD/Photoshop, Wine, 12.04"
date: 2012-06-28
forum: New to Ubuntu
---

### Post by Jeska on 2012-06-28
Well, I've successfully completed a clean install of 12.04 on my HP Dv76199us laptop with i7, 8GB DDR3, and a Radeon dedicated graphics card. I've fiddled and played to get the VLC player to work (Yay!)

Now to get Photoshop, and eventually vectorworks to run....  I hope!!

I've installed wine 1.4.1, and a trial version of CS2. I'm not picky about the version, this is a combo that was reported to work. 

Problem is, I can't find CS2 to start it up!! Erm.... I know that it's supposed to be in a c drive somewhere, but how would I go about finding this? (there's no Start button!!!  Ha ha ; )

Next question, in all of my research, wine is resoundingly recommended for photoshop, but there are so many variables!!  My graphics card, version of ubuntu, version of wine and version of PS all need to get along. How on earth do I figure out what to use??? Now I'm finding other people who swear by Wine 3.1 with CS5. 

Plus, most of the info and advice I'm finding is 2-5 years old, and this stuff is moving so fast. I would love a current step by step tutorial if one exists.

So, In summary:
How do I start up photoshop in my ubuntu wine configuration?
What's the best combo of programs for my box to make PS work?
How do I find the most current info?
Any tutorials? (with pictures? this learning curve seems steep over here!)

Thanks for the help! 

I look forward to being the advice giver one of these days....

<edit: I originally posted that I was using CS3, but it was actually CS2>

---

### Post by Jeska on 2012-06-28
Ok, I've found the answer to question number one, and feel much better knowing that I'm not the only only confused by the Unity gui. 

[http://ubuntuforums.org/showthread.php?t=1992949&highlight=photoshop+wine](http://ubuntuforums.org/showthread.php?t=1992949&highlight=photoshop+wine)

This OP was hilarious, and the answers helpful. Crayons, Ha!!!

So I started up CS2, and surprise! It didn't work.  But I've seen this one already in my searching, so I'm "back to the books" on it : ) 

Still looking forward to any recommendations for a better combination of programs. Thanks!

---

### Post by Futant on 2012-06-29
Hello, have you considered using Gimp instead of Photoshop? It's very similar, easy to pick up and there are loads of cool plugins and stuff because its open source. I used it for years before moving Linuxwards.

---

### Post by Lyfang on 2012-06-29
Try the latest Wine development release, Wine 1.5.7.

Install from Terminal:
```
sudo add-apt-repository ppa:ubuntu-wine/ppa
``````
sudo apt-get update && sudo apt-get install wine
```Also check out the Wine Application Database (AppDB): [http://appdb.winehq.org/](http://appdb.winehq.org/)

---

### Post by Jeska on 2012-07-09
I tried installing cs2 again, and it worked! I went ahead and got the newer 1.5 wine, so maybe that did it. Now to get vectorworks installed... (crossing fingers)

I'm open to giving Gimp a go. I found a great list of tweaks for it to make it function closer to PS. The truth is that I've been using PS for so many years... I have a good work flow with key commends etc...  I don't really want to learn an entire new program again.  

Maybe after I get this whole Linus thing mastered and learn Vectorworks ; )

Thanks for the feedback guys!

---

### Post by mastablasta on 2012-07-10
vectorworks has silver rating it seems. however it seems no one has yet tested it with latest WINE version: [http://appdb.winehq.org/objectManager.php?sClass=application&iId=488](http://appdb.winehq.org/objectManager.php?sClass=application&iId=488)

---

