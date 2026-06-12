---
title: "How do I burn ISO in XP (at work)?"
date: 2008-05-19
forum: New to Ubuntu
---

### Post by marcelo danico on 2008-05-19
I need to burn a live CD for 8.04. I'm at work and can use Roxio or Explorer to burn it. I burned one last week using Roxio (and slow speed ~8-12X)but it had 1 error that killed the installation during reformatting. 
I can't install any other programs at work, so which do I use?

Thanks

---

### Post by philinux on 2008-05-19
[http://onlinepubs.trb.org/Onlinepubs/burning_iso.html](http://onlinepubs.trb.org/Onlinepubs/burning_iso.html)

You need to burn at 4x

When you boot it and get the menu screen choose "check cd for errors" it take a while but well worth it.

---

### Post by rbc on 2008-05-19
Try this:
[http://burncdcc.en.softonic.com/](http://burncdcc.en.softonic.com/)
It is just a downloaded .zip file, with an .exe file inside. I have  used it many times, and never had a problem

---

### Post by .nedberg on 2008-05-19
I don't think Explorer will burn an iso. Roxio should do it just fine!

Also check your downloaded iso for errors if you can.

You could also try this one: [http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable)

It does not need an install!

---

### Post by Joeb454 on 2008-05-19
If you want something that is installable, I'd recommend [ImgBurn]("http://www.imgburn.com") though if not Roxio will be fine.

And burn at 1-4x rather than 8-12x to reduce the possibility of burn errors :)

---

### Post by alienexplorers on 2008-05-19
> **philinux said:**
> [http://onlinepubs.trb.org/Onlinepubs/burning_iso.html](http://onlinepubs.trb.org/Onlinepubs/burning_iso.html)

You need to burn at 4x

When you boot it and get the menu screen choose "check cd for errors" it take a while but well worth it.

When I try to burn a CD at 4x my burner program tells me after the CD is burnt that it was burnt at 12x.  How do I get it to stay at 4x?

---

### Post by philinux on 2008-05-19
Not really sure, have no windows to test on. 

If cd burned at 12x then boot it and use "check cd for defects" option from the initial boot menu.

If it works no problems.

---

### Post by marcelo danico on 2008-05-19
> **alienexplorers said:**
> When I try to burn a CD at 4x my burner program tells me after the CD is burnt that it was burnt at 12x.  How do I get it to stay at 4x?

Using roxio creator (classic or silver) I don't have the option of 4X. 12X is the slowest. This is weird, If I remove the CD the 4X is available under burn options, but when it recognizes the CD it makes 12X the slowest speed and the other slower speeds disappear.

I'll try to get 4X and do the CD defect check.

---

### Post by yogo on 2008-05-19
Get imgburn, it is less than 2mb and a great burner for iso's.

---

### Post by marcelo danico on 2008-05-19
> **yogo said:**
> Get imgburn, it is less than 2mb and a great burner for iso's.

Thanks I'm going to do this.

---

### Post by Xerp on 2008-05-19
[https://help.ubuntu.com/community/BurningIsoHowto](https://help.ubuntu.com/community/BurningIsoHowto)

---

### Post by mjitkop on 2008-05-19
> **.nedberg said:**
> I don't think Explorer will burn an iso. Roxio should do it just fine!

Also check your downloaded iso for errors if you can.

You could also try this one: [http://portableapps.com/apps/utilities/infrarecorder_portable](http://portableapps.com/apps/utilities/infrarecorder_portable)

It does not need an install!

+1!  :guitar:

I love PortableApps and InfraRecorder is great. Note that InfraRecorder is also open source just as Ubuntu is. ;-)

---

### Post by marcelo danico on 2008-05-19
Couldn't get imageburn to work, Admin rules lock up program installation, even when I had it installed in my thumb drive (access denied to the burner).

I accidentally burned another cd using roxio silver and the burn rate was at 48X.  
I checked the cd, using option from the livecd (no md5sum) and it said no cd defects, is this possible? 
Should I burn an extra copy at the slower speed (slowest I can get with roxio is 12X)?

---

### Post by .nedberg on 2008-05-19
> **marcelo danico said:**
> Couldn't get imageburn to work, Admin rules lock up program installation, even when I had it installed in my thumb drive (access denied to the burner).

I accidentally burned another cd using roxio silver and the burn rate was at 48X.  
I checked the cd, using option from the livecd (no md5sum) and it said no cd defects, is this possible? 
Should I burn an extra copy at the slower speed (slowest I can get with roxio is 12X)?

If the test states that the CD is OK, then it is! Go ahead and install!

---

### Post by philinux on 2008-05-19
> **marcelo danico said:**
> Couldn't get imageburn to work, Admin rules lock up program installation, even when I had it installed in my thumb drive (access denied to the burner).

I accidentally burned another cd using roxio silver and the burn rate was at 48X.  
I checked the cd, using option from the livecd (no md5sum) and it said no cd defects, is this possible? 
Should I burn an extra copy at the slower speed (slowest I can get with roxio is 12X)?
I would burn one at 12x if that's the slowest speed. As long as you check for defects from the initial menu when you boot the live cd, and it comes up clean it should be good to go.

---

### Post by marcelo danico on 2008-05-19
Thanks again, I'm going to burn another one at 12X. That way I'll take both home today and one better work.

---

### Post by stchman on 2008-05-19
> **marcelo danico said:**
> I need to burn a live CD for 8.04. I'm at work and can use Roxio or Explorer to burn it. I burned one last week using Roxio (and slow speed ~8-12X)but it had 1 error that killed the installation during reformatting. 
I can't install any other programs at work, so which do I use?

Thanks

I have Roxio 7.5 and in Creator Classic go to File--->Burn from Disc Image File...

Burn as slow as you can, preferably < 16X.

What version of Roxio do you have?

---

### Post by marcelo danico on 2008-05-19
> **stchman said:**
> I have Roxio 7.5 and in Creator Classic go to File--->Burn from Disc Image File...

Burn as slow as you can, preferably < 16X.

What version of Roxio do you have?

I have Roxio silver 10 (work pc).

But the issue is resolved, the computer is pretty locked up by the administrators, so I was stuck burning 16X using roxio classic.

But I just finished my install and am up and running:)

I'm sure I'll be referencing your website stchman, thanks a ton everyone!:KS

---

