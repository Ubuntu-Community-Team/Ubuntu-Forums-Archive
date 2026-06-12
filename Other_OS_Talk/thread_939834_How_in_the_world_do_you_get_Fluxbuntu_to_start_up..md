---
title: "How in the world do you get Fluxbuntu to start up...?"
date: 2008-10-06
forum: Other OS Talk
---

### Post by jason.b.c on 2008-10-06
After boot up i get a black screen with white text and a login prompt , i type my user name - then password and i wind up with the following:


> <my username>@ubuntu:`$  <blinking prompt>  

and still that same black over white text screen,  what gives...?:confused:

---

### Post by ronnielsen1 on 2008-10-06
What happens when you type startx or xwin?

---

### Post by snowpine on 2008-10-06
Hi Jason, try typing 'startx' (without the quotes) to start the graphical interface. This is not normal startup behavior for Fluxbuntu; when you boot up, you should see a white screen with a clock, then a graphical login screen with a white background. Do you see any of these things? Were there any error messages during the install process? What are your system specs?

---

### Post by jason.b.c on 2008-10-06
> **ronnielsen1 said:**
> What happens when you type startx or xwin?

i get > Fatal Server Error   - No screens found 

---

### Post by jason.b.c on 2008-10-06
> **snowpine said:**
> . This is not normal startup behavior for Fluxbuntu; 


I wouldn't have thought so...

> 
when you boot up, you should see a white screen with a clock, then a graphical login screen with a white background.


none of the kind...

> 
 Do you see any of these things? Were there any error messages during the install process?


none that i could tell...


> 
 What are your system specs?


ATI Radeon 9200 64mb PCI VGA card

AMD athlon 64 (4200 i believe)

640 mb's ram

two hard drives - 40gb and an 80

:confused:

---

### Post by jason.b.c on 2008-10-06
so no ideas..?

---

### Post by snowpine on 2008-10-06
Well, your system specs are more than enough for Fluxbuntu. :)

Are you using the 64 bit or 32 bit release? I have never tried the 64 bit, but I've had nothing but good luck with the 32 bit. Have you checked the md5sum, burned at low speed, etc.?

You could try asking for help over at community.fluxbuntu.org, but unfortunately things are a little slow over there...

---

### Post by jason.b.c on 2008-10-06
> **snowpine said:**
> Well, your system specs are more than enough for Fluxbuntu. :)

Are you using the 64 bit or 32 bit release? I have never tried the 64 bit, but I've had nothing but good luck with the 32 bit. Have you checked the md5sum, burned at low speed, etc.?

You could try asking for help over at community.fluxbuntu.org, but unfortunately things are a little slow over there...

i am using the 32 bit version...

and burned the disk at 1x speed

---

### Post by snowpine on 2008-10-06
Well I'm stumped, sorry. :(

Any particular reason you need Fluxbuntu and not, for example, Ubuntu + Fluxbox (or a more up-to-date distro like Crunchbang)?

---

### Post by ronnielsen1 on 2008-10-06
Sounds like it picked up on the wrong video drivers. I assume this is a boot disk. Try the vesa option when the livecd boots

---

### Post by ronnielsen1 on 2008-10-06
Once you have a gui I'm sure we can figure out the ati card

---

### Post by ronnielsen1 on 2008-10-07
Any luck?

---

### Post by bapoumba on 2008-10-07
Moved to "Other OS Talk" where there might be better exposure to other fluxbuntu users.

---

### Post by jason.b.c on 2008-10-07
> **ronnielsen1 said:**
> Any luck?

none at all....

about to give up...

---

### Post by I-75 on 2008-10-08
I wish I had good news for you, I don't. I tried installing it into two laptops. One installed but seem to freeze at the splash screen at the 5 o clock position. I re-did the login with "nosplash and it also froze. 

 The other laptop, I kept getting those no screens found errors. I only wanted to use Fluxbuntu because it was said to be good for low hardware computers with 64 MB RAM.. Even with 160 MB RAM was a no go. 

I ended up using Absolute Linux and DSL on those two laptops. I did some searching on the internet and there is a serious bug with the release that was never resolved.

[https://bugs.launchpad.net/fluxbuntu-project/+bug/157724](https://bugs.launchpad.net/fluxbuntu-project/+bug/157724)

---

### Post by snowpine on 2008-10-08
Apparently there is a "Fluxbuntu Remaster" that attempts to solve certain boot problems. I've never tried it and can't vouch for it, but it's worth a try I suppose: [https://bugs.launchpad.net/fluxbuntu-project/+bug/157724](https://bugs.launchpad.net/fluxbuntu-project/+bug/157724)

ps I do not recommend Fluxbuntu for 64mb of ram because of this problem: [http://community.fluxbuntu.org/index.php?topic=491.msg2082](http://community.fluxbuntu.org/index.php?topic=491.msg2082)

I posted the issue both here and on the Fluxbuntu forums back in July, and haven't had a single answer, so if anyone knows how to fix this, I'd be much obliged. :)

To the OP, frankly if you are having this much trouble with Fluxbuntu, I think you'll be better off with another distro that is still receiving bug fixes and support. Fluxbuntu is very much a "do-it-yourself" project at this point.

ps Just to clarify I-75's "there is a serious bug with the release" statement, Fluxbuntu 7.10 is a release *candidate*; it does not claim to be bug-free. :)

---

