---
title: "VGA port appears to be dead after loading Lubuntu on a Lenovo T42 Thinkpad"
date: 2020-04-17
forum: New to Ubuntu
---

### Post by RatTerrier on 2020-04-17
To anyone able and willing to help. I am very (and I mean very) new to the Ubuntu community (although, records show that I have created an account on this site 8 years ago (who knew; including me?) tonight is the night for returning here. I have an old, "throw-away" IBM, Lenovo, T42 Thinkpad computer that I replaced Windows 7 with Lubuntu a few years ago, as a challenge to myself (I thank Googling stuff for my success). While I was successful in accomplishing that challenge, I stored the computer until last night. After miraculously charging it back to life then connecting an external monitor to it via the  external VGA port, I was surprised to find that the secondary monitor was not receiving a video signal. It occurred to me that I may have invalidated the VGA driver since I blew Windows 7 away. If this is true, is there a fix for this? A driver download patch? Please understand, that I am a layman, Ubuntu is not my usual world and practically anything in it will be new and unusual for me.

Thank you

---

### Post by mörgæs on 2020-04-17
If the computer has been sitting idle for some years then the present Lubuntu is not worth keeping. 

First I suggest that you do a fresh install of Lubuntu 20.04 with the monitor detached. Please post back when this works.

---

### Post by guiverc on 2020-04-17
I have a couple of T42p & T43 thinkpads (but mine are listed as IBM not Lenovo).  Mine anyway are x86 (i686 grade) so Lubuntu 18.04 LTS is the latest mine will run. 

I'm not aware of any drivers that will make it work, I'd replace the cable, check for dirt of other in the connectors (do you have a electronics sucking tool or something suitable to suck dust that may have got in the way etc), and try a different monitor.  I'd suspect dirt, bent connector or something hardware related more than software fixable, having never had to do anything to make mine work.

Also is your screen capable of analogue signals? as the age of those thinkpads means I'm pretty sure they won't send a digital signal, so a digital only monitor won't see any 'digital' signal.

---

### Post by mörgæs on 2020-04-17
Sorry, guiverc is correct. The T42 is older than Windows 7 (probably born with XP) and has a 32 bit processor.

---

### Post by RatTerrier on 2020-04-18
Thank you. Very good to know. i do appreciate your feed back and if I'm actually successful at repeating this install, I will let you know for sure.

Regards,

I think it had Windows XP when it was given to me.

Good question about the analogue signal. I can tell you that it is an older monitor that is VGA capable. The monitor itself is kind of ancient and is a company throw-away. To be honest, I do not even know why I'm even playing around with these old beasts but perhaps  I'm looking for excuses to not do the things that I really want to do; but....I'm always looking to learn new things

Thank you for your reply and yes, the cable hasn't been used in years either so could be dirty. Perhaps it needs a good cleaning.

Regards,

Oh Yes....I forgot to mention, this does say IBM (Lenovo, I thought was IBM's trademark for this series....maybe I was incorrect)

---

### Post by RatTerrier on 2020-04-18
> **mörgæs said:**
> If the computer has been sitting idle for some years then the present Lubuntu is not worth keeping. 

First I suggest that you do a fresh install of Lubuntu 20.04 with the monitor detached. Please post back when this works.

I did attempt to upgrade to Ubuntu 20.04 and managed to attempt the upgrade only to learn that PAE is not enabled on my T42. With a little bit of research, I discovered that, while it is possible to attempt an enable via an Ubuntu DVD, I read a comment from someone who tried that to say it did not work. This may be very good news for me though because, I already have enough other hobbies to get to. Thank you for suggesting the updrade though as I learned a few things along the way. Oh...If you can think of a trick to try regardiing enabling PAE I'm all ears, otherwise I can put this up on its shelf again for another 10 years.

---

### Post by mörgæs on 2020-04-18
For a non-PAE computer using 18.04 and [this approach]("https://help.ubuntu.com/community/PAE") is the best option within the Buntu family.

Bodhi Linux is another candidate.

---

