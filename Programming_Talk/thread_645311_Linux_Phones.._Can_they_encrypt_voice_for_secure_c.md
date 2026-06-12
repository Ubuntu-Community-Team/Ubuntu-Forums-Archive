---
title: "Linux Phones.. Can they encrypt voice for secure connection.."
date: 2007-12-19
forum: Programming Talk
---

### Post by hopelessone on 2007-12-19
Hi,

With the new linux phones around... i was thinking... 
can you encrypt your voice..so big brother can't listen in ??

assuming the other phone has the same encryption...??

Thanks..

---

### Post by starcannon on 2007-12-19
I would never expect anything to be "safe" or "private" on any sort of wireless network, I don't even believe my own LAN to be a stronghold of all that is sacred to me.
I would also assume that encrypted messages in any format are likely to raise flags and be looked at harder and if possible decrypted.
At the end of the day, I to own a tinfoil hat, I just don't wear it every where I go.
All the same, its an interesting concept, though I'm not sure how it would work, would assume that with exception of push-to-talk mode that you'd need your Cell Provider to support the encryption as well no?

Cheers

---

### Post by jpkotta on 2007-12-20
Please don't read into what I'm saying too much.  I'm not a cell phone guru.

GSM is handled by hardware.  As in, you send a data stream to the GSM chip, and it will wrap it in the GSM protocol, without worry about most of the details.  GSM has encryption.  [http://en.wikipedia.org/wiki/Gsm#GSM_security](http://en.wikipedia.org/wiki/Gsm#GSM_security)

I think CDMA phones have a worthless cipher on them too.  Basically enough so no one would casually listen to conversations, but not enough to be considered secure in any real sense.

Strictly, the only other device that would need to know how to decrypt is the one you're trying to talk to.  Anything in between in principle shouldn't need to decrypt the data.  This is probably not how it works though; I think once the data reaches the base station, it goes through the regular (unencrypted) phone networks.

I think you could get a truely secure wireless network, it's just hard to get it right.  I'd trust an SSH connection over the internet, that's arguably more vunerable than a wireless connection (in terms of potential attackers).

---

### Post by slavik on 2007-12-20
it is definately possible, but I don't know if it has been done.

---

### Post by hopelessone on 2007-12-20
I mean the linux kernel has loop encryption built in... 

we could program input voice then send via normal GSM protocols...to a phone with the same encryption...
100's of encryption types... would make it very very hard to decrypt... 

i wonder why no one has thought or done this before?

kinda like encrypting your hard drive on the fly...but do it with voice..

Anyone...?

---

### Post by [h2o] on 2007-12-20
> **hopelessone said:**
> I mean the linux kernel has loop encryption built in... 

we could program input voice then send via normal GSM protocols...to a phone with the same encryption...
100's of encryption types... would make it very very hard to decrypt... 

i wonder why no one has thought or done this before?

kinda like encrypting your hard drive on the fly...but do it with voice..

Anyone...?

Probably because encryption is often a quite calculation intense thing to do. More stress on the CPU leads to more power consumption which will decrease battery time.

But it is possible and actually done. I am pretty sure most armed forces have cell phones that use encryption, I know ours has.

---

### Post by hopelessone on 2007-12-21
i found this:
Encrypting (GSM) mobile phone calls over VPN with an Asterisk PBX
[http://events.ccc.de/congress/2006/Fahrplan/events/1495.de.html](http://events.ccc.de/congress/2006/Fahrplan/events/1495.de.html)

sounds interesting...

yeah you are right on the CPU load and battery life...

if anyone has anything else interesting keep an eye out and post here...

thanks..

---

