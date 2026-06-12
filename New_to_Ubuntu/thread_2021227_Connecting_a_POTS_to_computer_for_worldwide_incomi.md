---
title: "Connecting a POTS to computer for worldwide incoming/outgoing calls via Internet"
date: 2012-07-08
forum: New to Ubuntu
---

### Post by hanzj on 2012-07-08
Hello,

If we go to the local phone company and ask for telephone service, we would be able to make calls in the local calling area (it's in Southeast Asia) if we are in the local area ourselves. But we want to be able to connect the telephone line to a computer and to the internet in such a way that:
[LIST]
[*]We can make free calls to phone numbers in the same local area wherever we are in the world using our computer.
[*]When people call our phone number, one of three things will happen:

[LIST=1]
[*]Our other phone will ring and we would be able to speak with them on that other phone device.
[*]Our computer will ring, and we will be able to speak with them through our computer.
[*]The caller will be sent to voicemail, which will then be sent to our gmail address as a WAV file.
[/LIST]
[/LIST]

What are the hardware requirements for this? 
What are the software requirements?
What other things do we need to know?
We are non-techie people, so please give easy-to-understand instructions and explanations.

Thanks.


UPDATE: Neither Google Voice nor Skype sell phone numbers for the country I want.

---

### Post by alphacrucis2 on 2012-07-08
Skype sort of does this for you already doesn't it? Not free for call to landline though.


If you didn't want to use skype you could possibly set up your own soft pbx that accepts incoming sip calls from the net and routes the calls to a local POTS or dedicated SIP line to the local Telco. Check out FreePBX

[http://www.freepbx.org/](http://www.freepbx.org/)

---

### Post by hanzj on 2012-07-08
Alphacrucis,
Neither Google Voice nor Skype sell phone numbers for the country I want.

---

### Post by alphacrucis2 on 2012-07-08
I'm sure you could do what you want using freepbx/asterisk but it is probably overkill. I also notice for some reason Ubuntu have the asterisk pbx software in the repos but not freepbx (which is the GUI front end for configuring and controlling asterisk). I would say that asterisk is pretty much useless with such a configuration tool. You may want to ask your question on the freepbx forums as the people there will have plenty of knowledge of telephony.

[http://www.freepbx.org/forums/viewtopic.php](http://www.freepbx.org/forums/viewtopic.php)

---

### Post by hanzj on 2012-07-08
1. If freepbx/asterisk is overkill, what would be "just right"?
2. I don't mind overkill as long as freepbx/asterisk is easy enough for a non-techie to configure.

---

### Post by alphacrucis2 on 2012-07-08
> **hanzj said:**
> 1. If freepbx/asterisk is overkill, what would be "just right"?
2. I don't mind overkill as long as freepbx/asterisk is easy enough for a non-techie to configure.

Given that the freepbx part doesn't appear to be packaged for Ubuntu it would probably require compiling from source which might be tricky. I found some scripts for doing it but they appear to be quite old so may require considerable tweaking. As I said ask your question on the freepbx forum. They may have a simpler solution than installing a full blown pbx system. Incidentally the company I work for use freepbx/asterisk and it works very well. I'm not much help though as I haven't had anything to do with it. They run it on Centos

---

### Post by hanzj on 2012-07-09
We'll  use whichever Linux distro runs FreePBX the best. If installing and running FreePBX on Ubuntu is tricky, no problem -- I'll use something else.

---

