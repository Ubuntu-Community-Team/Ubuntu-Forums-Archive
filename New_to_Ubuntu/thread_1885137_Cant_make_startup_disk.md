---
title: "Cant make startup disk"
date: 2011-11-22
forum: New to Ubuntu
---

### Post by NevermindWatever on 2011-11-22
I'm trying to make a start up disk of a different OS only this OS (11.10) won't let me. I have tried Brasero and it wont let me choose my usb stick to write to. When i tried K3B it won't load the iso. file, and the last time i used Startup Disk Creator and it wont load the the iso. file either. At this stage i am fed-up with this OS(11.10) and really need a change. Can anyone PLEASE help???

---

### Post by MG&amp;TL on 2011-11-22
Try unetbootin. You can install it via software-center or:

```
sudo apt-get install unetbootin
```

Are you sure the ISO isn't corrupted? ou could try and md5sum

I appreciate that you are an end-user, but in the words of bodhi.zazen (a forum member): 

"If you don't code, criticising the work of others is poor taste"-if you can't, or don't want to code, at least start filing bugs and writing documentation-this will make a difference to the quality of releases. :)

Personally I have found 11.10 the most stable yet. I guess it's hardware dependent.

---

### Post by dniMretsaM on 2011-11-22
UNetbootin will probably be your best bet. And you might want to check the ISO since neither K3B or Startup Disk Creator can read it. What OS?

> **MG&TL said:**
> "If you don't code, criticising the work of others is bad taste"-if you can't, or don't want to code, at least start filing bugs and writing documentation-this will make a difference to the quality of releases. :)

That sure sounds familiar...

---

### Post by MG&amp;TL on 2011-11-22
That's where I saw it first. :D

I need to remember quotes better. :oops:

---

### Post by NevermindWatever on 2011-11-22
My apologies, I have taken back what i said. I did not mean to offend anyone.(Good thing i can take a kick up the ***) 
When i started with Ubuntu i had 10.10 and it worked perfect, never had a problem with it. I then upgraded to 11.04 and the flash player was crashing and the nvidia driver wasn't working properly so i upgraded to 11.10 and thats when lots of stuff started to go wrong.
**MG&TL**- You said you think it might be hardware dependent, so i think i'll wait till my new Toshiba Qosmio arrives and try it from there. 
Once again, sorry if i offended. I'll bite my lip next time.

---

### Post by dniMretsaM on 2011-11-22
> **NevermindWatever said:**
> My apologies, I have taken back what i said. I did not mean to offend anyone.(Good thing i can take a kick up the ***) 
When i started with Ubuntu i had 10.10 and it worked perfect, never had a problem with it. I then upgraded to 11.04 and the flash player was crashing and the nvidia driver wasn't working properly so i upgraded to 11.10 and thats when lots of stuff started to go wrong.
**MG&TL**- You said you think it might be hardware dependent, so i think i'll wait till my new Toshiba Qosmio arrives and try it from there. 
Once again, sorry if i offended. I'll bite my lip next time.

I don't think you offended anyone. It's just kind of good advice in general.

---

### Post by LegendaryBibo on 2011-11-22
Ubuntu has their own startup disk creator specifically meant for Ubuntu LiveUSBs. I believe it's on every Ubuntu install, you might like that better than Unetbootin.

---

### Post by dniMretsaM on 2011-11-23
> **LegendaryBibo said:**
> Ubuntu has their own startup disk creator specifically meant for Ubuntu LiveUSBs. I believe it's on every Ubuntu install, you might like that better than Unetbootin.

He said he tried that and it didn't work.

---

### Post by MG&amp;TL on 2011-11-23
> **NevermindWatever said:**
> My apologies, I have taken back what i said. I did not mean to offend anyone.(Good thing i can take a kick up the ***) 
When i started with Ubuntu i had 10.10 and it worked perfect, never had a problem with it. I then upgraded to 11.04 and the flash player was crashing and the nvidia driver wasn't working properly so i upgraded to 11.10 and thats when lots of stuff started to go wrong.
**MG&TL**- You said you think it might be hardware dependent, so i think i'll wait till my new Toshiba Qosmio arrives and try it from there. 
Once again, sorry if i offended. I'll bite my lip next time.

No problem, everyone has their own opinion. :D

Sorry, I had just dealt with three threads containing various grades of Ubuntu-hate, and was feeling a little grumpy. My apologies for being so quick to bite. Please don't bite your lip, just remember the coders!

Yeah, because Linux has to write its own drivers to do stuff for free (MacOS and Windows pay people to write the drivers for their system), high-end graphics cards, newer CPUs, bizarre wireless doesn't work. See if your new laptop is any better. :)

Try unetbootin and see if it works any better. :)

---

### Post by NevermindWatever on 2011-11-24
Hay there, sorry i took so long to get back. Was very busy with work. 
Unetbootin did the trick, back to 10.10 now and everything seems back to normal YIPEEEE!!!!!!:P Haven't had time to check all programs yet but Flash is fine again and my display is not freezing anymore, also, _F_ile _E_dit _V_iew bar is back to where it should be **_on the window_** (and not on the control bar on my desktop). Cant thank you enough. Still cant figure out what was wrong with the update to 11.10 but i will "keep on truckin" with Linux because i am a big fan of open source software,   (and also because i hate MS). 

Anyway, thanks again and i'll be back as soon as i can only next time i hope it's to help somebody with stuff that i have learned.

---

### Post by MG&amp;TL on 2011-11-24
Pleased you're happy. If you updated, you probably had dependency issues. You're probably better off doing a clean install. :)

---

