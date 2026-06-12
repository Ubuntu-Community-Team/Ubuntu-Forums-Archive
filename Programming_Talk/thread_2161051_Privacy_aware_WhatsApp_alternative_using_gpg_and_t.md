---
title: "Privacy aware WhatsApp alternative using gpg and tor?"
date: 2013-07-09
forum: Programming Talk
---

### Post by kramer65 on 2013-07-09
Seeing the recent NSA/the-government-knows-everything-about-you leaks I've been going over all my ways of communications of which Whatsapp is one. Seeing that messages are supposedly sent unencrypted, and the fact that there is one company that at the least is able to collect all these messages, I was thinking of a privacy-aware Whatsapp alternative. Although I regularly program/script using Python and php I'm a novice with things like tor/bitcoint etc, let alone the technologies they are written with/in. I do have a basic understanding of how some of those technologies work and I was therefor thinking about a general setup for a privacy-aware whatsapp. Seeing that there is so much knowledge here on SO I was just wondering whether the following setup could theoretically work:

Let's take as a startingpoint the fact that it should be as easy to use as whatsapp. So identification should still go by phonenumber. I know this could potentially still be a treat to privacy, but the main things that should change are:

[LIST]
[*]All communication should be encrypted end to end.
[*]Similar to bitcoin, there should be no central authority for authentication.
[*]For parties intercepting messages, it should be impossible to know both the sender AND the receiver (similar to tor).
[/LIST]

I am then thinking of a system in which any message is encrypted at the sender its device using the public key of the recipient to which the sender wants to send the message. Messages are subsequently sent using (a) tor(-like system) in which messages are routed around several relays before reaching their end goal. These relays can be the present tor-relays, or any device which at any moment accesses the network. It should only be possible to identify the sender of a messages by opening the message and therefore the sender is only known once the message is received and unpacked by the party for which the message was intended (i.e. the party in possession of the private key).

There are of course a couple of issues:

[LIST=1]
[*]How are the public keys published?
[*]How can parties join the network? Authentication for the phone number should be done just like whatsapp does it by sending a one time sms-message from the device.
[/LIST]

For this I thought of the following solutions:

[LIST=1]
[*]All parties involved in the network should publish something like one hundred (or more) public keys including an index of its published keys and an index of the keys it's peers publish. In this way, any key is redundantly published and can be found in a decentralised way.
[*]Any party which is authenticated will open it's connection to authenticate other parties. This means that when you want to authenticate your mobile phone number on the network for the first time, your phone/device sends out an sms-message to several already authenticated devices which in turn can authenticate the new device on the network (just like bitcoin decentrally authenticates transactions). In some countries, receiving sms/text-messages costs money. That is of course a problem, but as the network grows, it could prefer newer authenticated users over older ones so as to evenly spread the pressure of authenticating new parties by receiving authentication messages.
[/LIST]

As you can see it is so far a pretty theoretical idea, of which I now wonder how practically viable this is. My questions are therefore;

[LIST=1]
[*]Is this a viable setup?
[*]What are the main challenges of such a system?
[*]How complex would it be to write/setup such a system?
[/LIST]

---

### Post by duanedesign on 2013-07-09
a PGP key would help you with soe of your issues. I realize this might not be as robust a solution as you are wanting but it has been used for many years with great success.
Some links about PGP keys:
[http://screencasts.ubuntu.com/2010/11/10/002-HowToCreatePGP](http://screencasts.ubuntu.com/2010/11/10/002-HowToCreatePGP)
[https://help.ubuntu.com/community/GnuPrivacyGuardHowto](https://help.ubuntu.com/community/GnuPrivacyGuardHowto)
[http://www.gnupg.org/gph/en/manual.html](http://www.gnupg.org/gph/en/manual.html)

---

### Post by trent.josephsen on 2013-07-09
Are you familiar with [OTR](http://www.cypherpunks.ca/otr/index.php)? Don't reinvent the wheel.

---

### Post by kramer65 on 2013-07-10
@trent.josephsen
Thanks for that, I didn't know OTR. Although it is not the ultimate solution I want to go for, it could definitely be a starting point. The main difference is that I want to authenticate users by mobile phone number, just like whatsapp does. The reason that I want to do this, is because it prevents the need to manually add everybody to your list, which is I think the main reason that whatsapp got so popular.

So wouldn't it be possible to use OTR as a startingpoint, and complement it with a decentralised authentication system for the mobile phone numbers through sms/text-messages?

---

### Post by nvteighen on 2013-07-10
Yesterday I read about [Surespot]("https://www.surespot.me/"). It's a Free Software alternative to Whatsapp that you might be interested to look at.

---

### Post by kramer65 on 2013-07-10
@nvteighen
I've just been finding a lot of different things as well, like [http://threema.ch/en/](http://threema.ch/en/) , [https://crypto.cat/](https://crypto.cat/) and yesterday, one of the original authors of the pirate bay announced [https://heml.is/](https://heml.is/)

Since I just wanted to get a privacy-aware chat system in the world, that mission already seems accomplished. So I'll let it rest for now.. :)

Thanks anyway for all the ideas!

---

