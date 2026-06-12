---
title: "New POSSIBLE NTR Project"
date: 2008-09-06
forum: Pennsylvania Team - US
---

### Post by jedijf on 2008-09-06
[Kevin Valentine]("https://launchpad.net/%7Ekejava") was recently contacted by [NTR]("http://ntronline.org/") about a possible new project with them.

The original specifications were unsatisfactory, but after some negotiation, Kevin and NTR have come up with a suitable project.

Basically, NTR installs and supports Windows installs.  They feel that much of their support time is wasted re-installing that operating system.  They are looking to the LoCo to create an automated re-install process for Windows, that the user themselves can implement.

The negotiations ended up being, along with that functionality, the boxes would have to be dual boot; Windows as primary and auto-boot, with the option to boot an Ubuntu flavor.

The Ubuntu flavor, the Windows re-install image, and the re-install scripts will reside on a separate 6 gb  HD.

Kevin and I like the challenge, but this will require ongoing support.  This is a call to arms!!!

If you are interested, let us know.  This is a Philadelphia area project, so people outside can help with logistics and scripting and such.  We will setup a wiki page for those efforts.  

Locals will be needed to physically go to NTR and assist with the imaging process once all the scripting is done.  

This physical assistance may be an ongoing job, as more imaging and/or tweaks to the Ubuntu installs are needed.

We need bodies.  These imaging sessions will try to be scheduled on Saturdays.  All your input and support is welcomed and required.

Let us know what you think.

---

### Post by InHisName on 2008-09-06
Ok, I'll byte.   I have only 25% of my sat's avail all others are obligated so far....     Doing a bazillion installs in one day could be very interesting.

---

### Post by OneIdle on 2008-09-07
Unless I am mistaken the ubuntu-us-pa teams primary goal is to promote Ubuntu and not to install Ubuntu on dual boot systems that will auto-boot Windows.
the Ubuntu philosophy is to help each other but does that mean we have to help at the possible detrement of the teams main objective? 

Installing ubuntu as a secondary OS that will most likely be overlooked by the average Windows user is not promoting or perpetuating the Ubuntu philosphy. IMHO

---

### Post by jedijf on 2008-09-07
The fact is according to market share that Gnu/Linux is 0.93% desktop market share.

This is at least a way to get Ubuntu into some users homes and give them the opportunity to use it if they choose.

As far as the work.  I personally look forward to the challenge of the task, and to the furthering of my own knowledge.  I don't have the outlet resources that NTR does, so doing this myself isn't as good an option to get Ubuntu dual booted machines to the public.

Keeping this existing relationship going can only lead to more opportunities.

We have done the same, under the guise of an installfest for thirty people at the same location.  This is the same thing, except it gets done for EVERY machine that they give away to organizations and sell via their thrift store and ebay site.

Hmm, a PERPETUAL installfest.  Seems like promotion to me.

---

### Post by OneIdle on 2008-09-07
I don't want to repeat myself. sufficite to say that I have a different opinion on the matter.

I will of course try and help out with this project as much as I can if the powers that be decide to go forward with it.

jedijf: of course getting ubuntu onto as many computers as possible is always a good thing. My only concern is that with this project it is as a secondary ( almost invisible ) option to the user.

---

### Post by jedijf on 2008-09-07
The reply was not argumentative, it was meant to be clarifying.

I was unfortunately privileged to receive their first request, which had me infuriated. 

Given time to calm down, and offer the dual boot option, which we didn't think they would accept, it was gratifying to see that they did accept that option.

Had there had been no Ubuntu option, this wouldn't have even made it to the LoCo.

All help is appreciated.  Always.

I expected many to have the same reaction as I did initially.

---

### Post by kejava on 2008-09-08
[QUOTE=OneIdle]Unless I am mistaken the ubuntu-us-pa teams primary goal is to promote Ubuntu and not to install Ubuntu on dual boot systems that will auto-boot Windows.[/QUOTE]

I'm glad you brought this up.  For now, let's remove "auto-boot Windows" part from you comment.  AFAIC, that part is still under negotiation.  I don't like it either.

Jim mentioned the install-fests that we've done as a follow-up.  If the LoCo can't do dual boot systems, then we may have to discontinue any install-fests.  Is your primary concern the timeout?

[QUOTE=OneIdle]the Ubuntu philosophy is to help each other but does that mean we have to help at the possible detrement of the teams main objective?[/QUOTE] 

The only thing that *could* be considered detrimental to our groups objectives is the part where we provide the Windows restore feature.  Yes, that part sucks but it's the only way we're ever going to get Ubuntu onto any PCs at NTR.  We don't get many opportunities like this.  It's possible we won't for a while.

The end result is that people on the other side of the digital divide are getting PCs with Ubuntu on them.  I'm willing to bend my own rules to do that :)  Based on your follow-up post, it seems you may be willing also.  We can't get around the dual-boot but if there's anything else you think should be changed, let us know.

[QUOTE=OneIdle]Installing ubuntu as a secondary OS that will most likely be overlooked by the average Windows user is not promoting or perpetuating the Ubuntu philosphy. IMHO[/QUOTE]
There's no way of knowing if it will be overlooked.  If we draw enough attention to it in the Grub splashimage, there's a good chance people may actually press the up/down arrows and select it.  The splashimage is something I'm going to work on ;)

---

### Post by kejava on 2008-09-08
For those interested in a visual representation, attached is a simple block diagram (OO Draw) that describes the process.  Had to zip it so it would be just below the 20kB bar for attachments.
[ATTACH]84625[/ATTACH]

---

### Post by OneIdle on 2008-09-08
Don't get me wrong here. I am not one of those anti-windows people. My wife uses windows and I jump on there every now and then also. I have no problem with other OS'es.

 I just would like to see an offer something like " Hey Ubuntu guys we just got 1000 pc's we want you to install Ubuntu on!" 

but you both make valid points about getting Ubuntu out there and if it means we need to comprimize a little well then...

Grub Splash: a nice 7 to 10 second splahs would be great with the obvious choice of starting up Ubuntu :)

---

### Post by jedijf on 2008-09-09
I can testify that Kevin LOVES splash images.

Every project has had one (or two).  :-)

I am certain that when these machines boot, they will know they bought it from NTR and that the **Ubuntu PA LoCo **set them up!!

Wiki Page started:

[https://wiki.ubuntu.com/PennsylvaniaTeam/CommunityOutreachTeam/NTRDualBootImage](https://wiki.ubuntu.com/PennsylvaniaTeam/CommunityOutreachTeam/NTRDualBootImage)

---

### Post by jedijf on 2008-09-14
Looking for the best set of Grub boot options, so if you have installed a Gnu/Linux Distro on an older desktop, and have had to use any special boot options, please let us know what special options you have used, and for what machine specs (processor/video etc.) it helped boot.

Donated pc's come in many different configurations and we are trying to come up with a scenario that will just work.

Thanks for your help.

---

### Post by OneIdle on 2008-09-14
all_generic_ide always helped me as a boot option

---

