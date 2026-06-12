---
title: "Surround sound in Ubuntu"
date: 2008-10-16
forum: New to Ubuntu
---

### Post by mac9416 on 2008-10-16
Following this great [howto]("http://www.automaticable.com/2008-05-28/how-to-enable-surround-sound-on-ubuntu-hardy/#more-280") I have confirmed that I have different sounds coming out of all ports (it has six sound jacks labeled front, side, c/sub, line, mic, and out) when playing Narnia, but that's about it. I need to know what wires lead from what ports to what speakers sitting where. Can anyone help?

---

### Post by mac9416 on 2008-10-16
> I need to know what wires lead from what ports to what speakers sitting where. Can anyone help?
Narnia looked great even on a cheap projector! The view width was around 5ft! :popcorn:

PS: bump

---

### Post by oldsoundguy on 2008-10-16
unplug all but one speaker and activate one outlet jack at a time with the software .. switch the speaker around to find which output is which.  It will take time if your sound card or surround amp is not marked properly to work with the computer. Mine is.

---

### Post by mac9416 on 2008-10-16
So, let's say that I have a new motherboard with six sound ports and want to set it up to play surround sound. What would Iplug where and where would I put what I plugged?

---

### Post by oldsoundguy on 2008-10-16
new motherboard should be marked (and for 7.1 there will be 7 outputs) .. front l, front r, front c sub, rear l, rear r, and rear c (just set up a new HP that was so marked)  HOWEVER if you have an external digital amp and wish to use it, you will have to use the digital out (it is one of those 6/7 outlets and the manual will tell you which one.) and select digital out for Alsa. (that is what I use running a 5.1 system.)

---

### Post by mac9416 on 2008-10-16
Thanks for the response!

That helps some, but My motherboard isn't marked that way.
First, I don't have any digital speakers, so that's out of the question.
Secondly, I think the motherboard is 5.1, because the outputs look like this:
side|front|c/sub
000
000
mic|out|line
And that's all I know. 
> front l, front r, front c sub, rear l, rear r, and rear c
Perhaps each port connects to two speakers? You know, the ones with line running into one(right), out of that and into the other(left)?

---

### Post by oldsoundguy on 2008-10-16
get a copy of the manual for the board .. without being able to look at it, not a clue!  (a PDF manual can be obtained and printed from the FCC site by plugging in the FCC number that is on the motherboard.)

now this is just a guess .. but would venture that it front is just that .. side are the back speakers (both most likely wired as a 3 wire or stereo with each positive being on on the tip and ring of the jack sharing a common ground.) c/sub is both the center and the sub woofer .. how that is wired is any body's guess.  
There are NO professional standards for computer audio and each maker can darn well do as they please to suit their own needs.  Some go so far as to make the darn things proprietary so that you have to buy THEIR speakers! (can you say APPLE?)

---

### Post by mac9416 on 2008-10-16
Shame, shame, Apple.:mad:
Ok, thanks for the advice. That's crazy that there isn't a standard! Well, I guess I'll just look up that number.
Thanks!

---

### Post by mac9416 on 2008-10-16
Here's a pic of what the layout is:

---

### Post by mac9416 on 2008-10-16
And the manual obtained from Gibabyte's website here:
[http://america.giga-byte.com/FileList/Manual/motherboard_manual_ga-ep35-(d)s3l_e.pdf]("http://america.giga-byte.com/FileList/Manual/motherboard_manual_ga-ep35-(d)s3l_e.pdf")

---

### Post by oldsoundguy on 2008-10-16
page 19 and 20 page 71 .. looks that each is a 1/8" stereo type connector (3 conductor).  If they follow any known form the tip of the connector will be the right speaker, the ring will be the left speaker.  On the center/sub the tip should be the center and the ring the sub.

---

### Post by markbuntu on 2008-10-16
Color coding is sort of half assed semi-standardized for those connectors so your results may vary.

gray, side
black, rear
yellow, sub
pink, mic
green, line out or front or headphones
blue, line in
orange, center

All you can really do is try them since windoze will remap them and so can pulseaudio.

---

### Post by BMWDriver on 2008-10-17
So what speakers are you going to use ? A 5.1 sound system ?

---

### Post by mac9416 on 2008-10-18
I thought 5.1 but after looking at the manual I think I can get 7.1.

---

