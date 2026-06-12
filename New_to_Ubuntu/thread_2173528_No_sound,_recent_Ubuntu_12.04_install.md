---
title: "No sound, recent Ubuntu 12.04 install"
date: 2013-09-10
forum: New to Ubuntu
---

### Post by SpazCool on 2013-09-10
No music, no youtube, no...anything. I just installed Ubuntu 12.04 a couple of days ago, I've been busy installing all of the programs and add-ons that I want/need. Anyways, I'm looking for possible solutions/ideas to fix this. 

The home screen, upon boot, does make a trumpetting sound to greet me, I think this is the only place that makes a noise. Also, the sound controls are all set on the highest volume.

I'm hoping you guys/gals can help me out.

Thanks.

---

### Post by deadflowr on 2013-09-10
The sound settings page lists a sound card, I'm guessing.
and you have unmuted the volume?
If you're comfortable with a quick terminal command enter this
```
lspci | grep Audio
```
which should list any sound cards you have.
Post back any info you get.
Use code tags when posting them. It's the # symbol in the reply box.

---

### Post by SpazCool on 2013-09-10
This is what I got.

# lspci | grep Audio 00:1b.0 Audio device: Intel Corporation 6 Series/C200 Series Chipset Family High Definition Audio Controller (rev 05) #

And, I'm really not sure what the code tag is, not seeing # anywhere, sorry.

---

### Post by SpazCool on 2013-09-10
Alright, adding to list of oddities. Skype is working just fine. The volume is really low, but I can hear and be heard by others. So, the volume is a problem for my browsers and music player, at the moment. It might be two different problems, maybe a missing plugin for the internet and....something...not working on the music player.

---

### Post by SpazCool on 2013-09-11
Alright, I've checked my plugins and it seems that I've done something to completely screw up my Adobe Flash Player installation. It appears that the plugins are the most likely culprit, so I've started a new thread to deal with that. I'll mark this one as closed. Thanks for the help.

---

