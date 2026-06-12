---
title: "Very strange Skype behaviour"
date: 2011-10-30
forum: New to Ubuntu
---

### Post by Eiji Takanaka on 2011-10-30
Hi there, i recently started up skype on my computer, and noticed some very odd behaviour. On the start-up of skype, whilst running wireshark, i noticed a few packets going to fairly odd locations. At first i assumed they may probably be packets heading for the 'friends list' to ascertain who is 'online' or not. But i decided to have a little look at a packet headed for a locatikon of the ssl2 variety. It turns out the packet was headed for 89.23.174.21. A quick bit of recon on google and that happens to be an identified spam bot server of the russian variety.  I can't believe this would be normal skype behaviour, the udp packets being sent to random addresses here in the u.k do not as far as im aware correlate to the 'friends' i have on skype either.  Has anyone else noticed this strange behaviour?

---

### Post by Eiji Takanaka on 2011-10-30
I thought i'd attach a couple of screenshots to show what i mean....

The first shows skype on this computer initiating udp sends to unknown addresses.

This is somewhat odd i thought.

The second shows a ssl2 connection being made with a random customer computer based in the U.K this time. Again initiated from this machine by skype. Surely spam works the other way round? This time the computer connected to was not the aformentioned russian machine but instead a customer based machine in the u.k. I take it this is not ordinary skype protocol.

Any thoughts or ideas on the subject would be greatly appreciated.

Cheers 

- dan

---

### Post by alphacrucis2 on 2011-10-30
> **Eiji Takanaka said:**
> I thought i'd attach a couple of screenshots to show what i mean....

The first shows skype on this computer initiating udp sends to unknown addresses.

This is somewhat odd i thought.

The second shows a ssl2 connection being made with a random customer computer based in the U.K this time. Again initiated from this machine by skype. Surely spam works the other way round? This time the computer connected to was not the aformentioned russian machine but instead a customer based machine in the u.k. I take it this is not ordinary skype protocol.

Any thoughts or ideas on the subject would be greatly appreciated.

Cheers 

- dan

Skype protocol is proprietary so who knows what it is supposed to be doing apart from Skype themselves.

---

### Post by Ms. Daisy on 2011-10-30
> **alphacrucis2 said:**
> Skype protocol is proprietary so who knows what it is supposed to be doing apart from Skype themselves.True, but regardless one can apply some logic to the situation.  What legitimate reason would any program on his computer have to call a Russian spam bot server?
I'm curious if you found anything related on [http://community.skype.com/](http://community.skype.com/)

---

### Post by Eiji Takanaka on 2011-10-31
Exactly Miss Daisy, At the worst there is either something in the coding of skype, warranting this odd behaviour, or at the best the servers that skype use to do business are fundamentally compromised. Either way that's not particularly good all round.   The fact that the ssl2 connection changed between two differing connections, the first time from a russian spam bot, to secondly a customer based u.k connection is definitely extremely odd behaviour.   I was wondering if any one else could run a test and see if they notice any strange start-up behaviour also.   Doing so would increase the chances that it is not a local phenomenon, but instead some bad code running in skype. From an attackers viewpoint,would it not be technically possible to log onto this rogue server, and then forward the traffic to and from the skype services? I.e man in the middle attack? That would be my first thoughts on the scenario, but we could kind of use more people to undergo the experiment, to collect/collate and narrow down the margin of error.   Cheers  - dan.

---

### Post by dave0109 on 2011-10-31
Skype uses peer-to-peer (p2p) connections to spread the load of the worldwide VoiP calls.  When you login to Skype, you're effectively letting them use spare cpu time on your computer.

So, chances are, it's just routing some packets to someone else that's using Skype. It's likely that this will change if you keep monitoring it. Whether you trust them (or Microsoft now), is entirely up to you though! :D

---

### Post by fractalman on 2011-10-31
This story has been going round the last few weeks about skype, not sure if it has any implications for linux users

[http://beforeitsnews.com/story/1205/257/Possible_Governmental_Backdoor_Found_Case_R2D2.html](http://beforeitsnews.com/story/1205/257/Possible_Governmental_Backdoor_Found_Case_R2D2.html)

---

### Post by Ms. Daisy on 2011-10-31
> **Eiji Takanaka said:**
> ...we could kind of use more people to undergo the experiment, to collect/collate and narrow down the margin of error. I would be happy to do such research, except that it's beyond my capabilities at the moment.  Network traffic is next on my list of things to conquer.

---

### Post by Eiji Takanaka on 2011-11-02
Fair doos, good luck with that! It's a pretty interesting area to research into i find. 

Wireshark and/or nessus, and nmap are useful auditing tools!

Gives you a bit of insight into what packets are coming/going from where.

And as aforementioned in this post, you don't necessarily need to be able to analyse the source code of the program to realise it exhibits odd behaviour, by utilizing a deep packet inspection program, and inspecting the traffic flow. 

You can also see if anyone happens to of logged onto your wep wireless network and see which websites they might be visiting. Cheeky beggars! ;) (Unless of course they use a vpn tunnel of some sort and then you can't. ;)

---

