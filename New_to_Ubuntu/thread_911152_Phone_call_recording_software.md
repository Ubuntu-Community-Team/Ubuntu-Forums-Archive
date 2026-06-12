---
title: "Phone call recording software?"
date: 2008-09-05
forum: New to Ubuntu
---

### Post by drsyntax on 2008-09-05
Hello,

is there a program that works with ubuntu that can work as an answer machine for phone calls if no one replied and save the call if someone answered the phone ?

note: i'll not use this program to spy on others calls :)

Thanks,
Tamer Mohsen

---

### Post by perlsyntax on 2008-09-05
You could make your own program.

---

### Post by ronnielsen1 on 2008-09-05
In synaptic there is 
> Mgetty is a versatile program to handle all aspects of a modem under Unix.

The program 'mgetty' allows you to use a modem for handling external
logins, receiving faxes and using the modem as a answering machine without
interfering with outgoing calls.
and
> Voice over Internet Protocol (VoIP) SIP Phone
Soft-phone for making telephone calls using SIP over an IP network.

Twinkle supports direct IP phone to IP phone communication or a network
using a SIP proxy to route your calls.

In addition to making basic voice calls Twinkle provides you the
following features regardless of the services that your VoIP service
provider might offer.

 2 call appearances (lines)
 Multiple active call identities
 Custom ring tones
 Call Waiting
 Call Hold
 3-way conference calling
 Mute
 Call redirection on demand
 Call redirection unconditional
 Call redirection when busy
 Call redirection no answer
 Reject call redirection request
 Blind call transfer
 Call transfer with consultation (attended call transfer) (new)
 Reject call transfer request
 Call reject
 Repeat last call
 Do not disturb
 Auto answer
 Message Waiting Indication (new)
 Voice mail speed dial (new)
 User definable scripts triggered on call events
  E.g. to implement selective call reject or distinctive ringing
 RFC 2833 DTMF events
 In-band DTMF
 Out-of-band DTMF (SIP INFO)
 STUN support for NAT traversal
 Send NAT keep alive packets when using STUN
 NAT traversal through static provisioning
 Missed call indication
 History of call detail records for incoming, outgoing, successful and missed
 DNS SRV support
 Automatic fail-over to an alternate server if a server is unavailable
 Other programs can originate a call via Twinkle, e.g. call from address book
 System tray icon
 System tray menu to originate and answer calls while Twinkle stays hidden
 User definable number conversion rules
 Simple address book (new)

Audio codecs
 G.711 A-law (64 kbps payload, 8 kHz sampling rate)
 G.711 u-law (64 kbps payload, 8 kHz sampling rate)
 GSM (13 kbps payload, 8 kHz sampling rate)
 Speex narrow band (15.2 kbps payload, 8 kHz sampling rate)
 Speex wide band (28 kbps payload, 16 kHz sampling rate)
 Speex ultra wide band (36 kbps payload, 32 kHz sampling rate)
 G.726 (16, 24, 32 or 40 kbps payload, 8 kHz sampling rate)

KDE goodies
 Balloon pop-up from system tray when a call comes in
 Interface to KAddressBook: dial phone numbers from your address book
 Display names from KAddressBook on incoming calls
 Display photos from KAddressBook on incoming calls

Website: [http://www.twinklephone.com](http://www.twinklephone.com)
Haven't tried either

---

### Post by drsyntax on 2008-09-05
i need something similar to this one : [http://www.modemspy.com/en/index.php](http://www.modemspy.com/en/index.php) but for linux

---

### Post by Angry penguin on 2008-09-05
> **drsyntax said:**
> i need something similar to this one : [http://www.modemspy.com/en/index.php](http://www.modemspy.com/en/index.php) but for linux



mgetty looks like it will do what you want it to. Here are some more links for getting it working as well as a howto for an asterisk server which will do the same thing.

[http://www.freeos.com/articles/3715/](http://www.freeos.com/articles/3715/)
[http://linuxgazette.net/120/smith.html](http://linuxgazette.net/120/smith.html)
[http://blog.makezine.com/archive/2006/08/how_to_set_up_a_linux_answerin.html](http://blog.makezine.com/archive/2006/08/how_to_set_up_a_linux_answerin.html)

---

### Post by drsyntax on 2008-09-08
> **Angry penguin said:**
> mgetty looks like it will do what you want it to. Here are some more links for getting it working as well as a howto for an asterisk server which will do the same thing.

[http://www.freeos.com/articles/3715/](http://www.freeos.com/articles/3715/)
[http://linuxgazette.net/120/smith.html](http://linuxgazette.net/120/smith.html)
[http://blog.makezine.com/archive/2006/08/how_to_set_up_a_linux_answerin.html](http://blog.makezine.com/archive/2006/08/how_to_set_up_a_linux_answerin.html)


thank you , but the main thing i want is the call recording if some one replied and the answering machine if no one replied the phone :(

---

