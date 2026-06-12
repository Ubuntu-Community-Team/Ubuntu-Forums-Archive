---
title: "[SOLVED] Network History all Spikey"
date: 2008-10-24
forum: New to Ubuntu
---

### Post by stoogiebuncho on 2008-10-24
This is probably a stupid question.  I've spent some time today getting conky set up on my machine, and it made me realize that my internet connection is spiking from around 650kb/s to zero and back up again.

Is this normal?  Speedtest.net reports that I'm getting 2554kb/s downloads, so what's with the difference? 

I attached a screenshot showing both the conky monitor and the system monitor.

---

### Post by Squish on 2008-10-24
Ive had something like that before. I looked at my network, and I wasnt surfing, yet there were huge spikes like that.


Then I realized that I was also connected to a local area network, and realized that the network doesnt monitor just internet, but anything you are networked too.

Does this apply to you?

---

### Post by stoogiebuncho on 2008-10-24
I'm not on a LAN, actually, and those spikes only happen when I'm actually downloading or uploading something.

The thing that was confusing me is if I'm download one big file, why isn't a longer extended spike instead of 6 or 8 spikes that each only last about a second?

Is that just how it normally is?

---

### Post by Duck2006 on 2008-10-24
Could it be spiking as the packets come through, as it would not come through in one long line, but packets at a time.

---

### Post by stoogiebuncho on 2008-10-24
Thanks, that's helpful.  I guess we could call this solved now.

---

### Post by LowSky on 2008-10-24
Look at the traffic every time you recieve something you are laso sending something as well, most likely the communication that is occuring is to let the other system know you finshed download a part of the file and to send the next packet.

---

