---
title: "Internet Question"
date: 2010-12-20
forum: Programming Talk
---

### Post by YourMomsASmurph on 2010-12-20
I'm looking for technical documentation on the signal outputed from a modem that a computer can read and understand as the "internet." 
Also Exactly how that information is read by a computer.

Can anyone point me in the right direction?

( Am attempting to make something that will convert an Internet signal into a series of laser pulses and back again at it's destination. So an understanding of the signal would be helpful.)

---

### Post by iponeverything on 2010-12-20
There are number of researchers doing work in this area. If you are indeed serious and capable of independently developing the technology, then tracking down "technical documentation", protocol specs or others working in same area will be child's play for you.

---

### Post by wmcbrine on 2010-12-20
> **YourMomsASmurph said:**
> I'm looking for technical documentation on the signal outputed from a modem that a computer can read and understand as the "internet."It doesn't quite work like that. The Internet is several layers up from the modem. I guess you could start [here](http://en.wikipedia.org/wiki/OSI_model) for a broad overview; but as iponeverything implies, I think you've greatly underestimated the complexity of the problem.

If you do proceed, I don't think you'll want to work at the level of modem signals.

[quote=iponeverything]There are number of researchers doing work in this area.[/quote]This is an odd comment to me -- it seems to suggest that we don't already have laser-transmitted Internet. But I've got it right at my house (fiber to the premises). :)

---

### Post by iponeverything on 2010-12-20
> **wmcbrine said:**
> It doesn't quite work like that. The Internet is several layers up from the modem. I guess you could start [here](http://en.wikipedia.org/wiki/OSI_model) for a broad overview; but as iponeverything implies, I think you've greatly underestimated the complexity of the problem.

If you do proceed, I don't think you'll want to work at the level of modem signals.

This is an odd comment to me -- it seems to suggest that we don't already have laser-transmitted Internet. But I've got it right at my house (fiber to the premises). :)

:) I didn't think of fiber that way, I talking about Line-of-Sight Laser transmissions.

---

### Post by muteXe on 2010-12-20
[http://www.amazon.co.uk/Sams-Teach-Yourself-TCP-Hours/dp/0672329964/ref=sr_1_1?s=books&ie=UTF8&qid=1292861108&sr=1-1](http://www.amazon.co.uk/Sams-Teach-Yourself-TCP-Hours/dp/0672329964/ref=sr_1_1?s=books&ie=UTF8&qid=1292861108&sr=1-1)

[http://www.amazon.co.uk/TCP-IP-Illustrated-Protocols-APC/dp/0201633469/ref=sr_1_2?s=books&ie=UTF8&qid=1292861125&sr=1-2](http://www.amazon.co.uk/TCP-IP-Illustrated-Protocols-APC/dp/0201633469/ref=sr_1_2?s=books&ie=UTF8&qid=1292861125&sr=1-2)

---

### Post by YourMomsASmurph on 2010-12-20
I assumed that this was a lot harder than it seemed and odds are I don't have the expertise to complete the project. Yet. 

But by the time I am done school in 2-5 years I hope to have either completed it or at least have a good enough understanding to start creating it. 


Thanks

---

### Post by trent.josephsen on 2010-12-20
You've mentioned engineering before -- may I ask what specifically your major is?

---

### Post by YourMomsASmurph on 2010-12-20
Computer Engineering - Software Option. In my second Year. So I'm far from having the knowledge base I need to complete this project, but Ive been trying to push the boundaries of my education so I can get a better idea of the applications of the material we are learning. 

Though this idea came from a dream I had where I built a device that I could hook up to any phone and it would give me the Internet.

(Planning on using a laser and a photo-receptor to learn the basics of processing and transmitting the signal, then I will switch to converting it to an audio signal /w speakers as o/p and the mic as input.)

I expect it to take a few years to complete, but it would be a fun project.

---

### Post by wmcbrine on 2010-12-20
You're planning to reinvent the [acoustic coupler](http://en.wikipedia.org/wiki/Acoustic_coupler)?

---

### Post by YourMomsASmurph on 2010-12-20
Lol :(. I figured something similar existed (Assumed it was the same principal dial up and fax machines worked on.) Didn't know the exact device already existed :P

---

### Post by Tony Flury on 2010-12-21
also bear in mind that most of what you want to do would not be sensible as software - even at modem speeds - decoding the audible signal into a binary signal that you could transmit via laser you will have to go a lot faster than most software could handle.

The vast majority of this sort of device - the decoding and retransmission is done via hardware - dedicated chips, or specifically programmed ASICs.

All of the above applies to modem - i.e. data transmitted via audible tones.

Broadband (ADSL) signals are transmitted via your phone line but aren't in an audible range at all - in fact they are a digital transmission - so finding audio hardware that will "hear" them is going to be tough if not impossible.

---

