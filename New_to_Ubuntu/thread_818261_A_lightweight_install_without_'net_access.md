---
title: "A lightweight install without 'net access?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Graphite on 2008-06-04
Hi all,

My rather technophobic dad has decided that he wants to enter the digital age and learn to use a computer. He has acquired an aging desktop computer with a bloatware-laden Windows ME install, and has no clue how to use it. I'm trying to decide whether to a) do a new 'though still slightly bloated install of Windows ME using the recovery disk or b) do a clean install of (k)(x)ubuntu.

I don't know the computer specs exactly; it's something like a 1.5GHz Celeron with maybe 512MB RAM. It was happy running Windows ME before all the bloat found its way in.

**His requirements:**
Internet access (this will be via an internal dial-up modem for the forseeable future)
Simple email client
Basic word processing
Use of an Epson USB printer

**My requirements:**
An OS I'm sufficiently familiar with to teach and do basic troubleshooting (so: windows, ubuntu, kubuntu, xubuntu if it's easy)
Something I can get set up without using an internet connection.

My gut feeling is that I should go for Ubuntu. My reasoning:
With the compiz visual effects turned off, it should be lightweight enough for this computer
It's easy to use; My dad has to learn a new system whether we pick Windows or Linux, so there's no *extra* learning curve associated with Linux.
The word processor, Firefox, pdf viewer etc. are all there out of the box.
No viruses, spyware or bloatware. My dad has effectively no experience of the Internet, so he's a prime target for this stuff.
Overall, once I have everything set up and working for him I imagine that he'll have an easier experience with Linux.

**My concerns about giving him Ubuntu:**
Installation without net access:
My dad won't need bleeding-edge software for what he wants, but we *will* need some stuff from repositries when I install: Non-free codecs, possibly Flash player (although I can't exactly see him trolling the YouTube boards, especially on dial-up) etc. Is there a way to put these files on a CD and take them with me?

Printing and dial-up internet:
I'll need to find drivers for his printer and, presumably, his internal dial-up modem. Again, assuming they're in the repositories can I install them from a CD?

Support:
I live in a different city, so if something does go wrong that I can't fix over the phone I can't help him. If he's running Ubuntu, I doubt any of his friends will be able to help him out.

.....

So, what are your thoughts? Should I unleash my technophobic dad on a fresh Ubuntu install or would Windows be better? (I realise there might be a slight bias in this crowd :)). If we and he decide on Ubuntu, can I install it and some extras without internet access?

---

### Post by bumanie on 2008-06-04
On older architecture, xubuntu or you could go for something smaller like puppy linux or damn small linux. Never used DSL, but puppy will install from a live cd and run from ram so it is quick. It can of course be installed to a hard drive too. Although small it has full functionality.

---

### Post by Joeb454 on 2008-06-04
Windows ME may be easier to use (I'll probably get flamed for that). But I'd imagine the internal modem will give you issues otherwise.

Also like you said, you can't always help him out, which could be an issue. And if his friends use Windows, you can bet they'll be stuck in the "Windows **is** the computer" mindset, which could become an issue if he's not running Windows.

---

### Post by Duck2006 on 2008-06-04
> his internal dial-up modem

If it is a win modem you may not even get drivers for it in linux.

---

### Post by mikewhatever on 2008-06-04
Ubuntu or Xubuntu should be a desent choice for that PC (provided the hardware is supported), not lightning fast, but easy to use.
The no-net part is tricky. You can use [http://nonetdebs.unixpod.com/](http://nonetdebs.unixpod.com/) to get whatever is needed from the repositories.

---

### Post by Inxsible on 2008-06-04
I agree with the above posters....The modem may be the only problem you might face.

You should still try a Xubuntu Live CD -- with 512 MB Ram..i would say that's your best bet unless you want to try out other distros like DSL or puppy. I am not sure how familiar you are to them. but DSL is debian based.

Fluxbuntu would also be great...but its not a full featured DE and you will have to manually set almost everything using config files.

---

### Post by Joeb454 on 2008-06-04
If somebody is new to computers - period. Then I don't think Fluxbox would be the best DE to start them off with, it can be a little confusing :)

---

### Post by jeffus_il on 2008-06-04
> **bumanie said:**
> On older architecture, xubuntu or you could go for something smaller like puppy linux or damn small linux. Never used DSL, but puppy will install from a live cd and run from ram so it is quick. It can of course be installed to a hard drive too. Although small it has full functionality.
Puppy is much user friendlier than DSL.

---

### Post by jeffus_il on 2008-06-04
> **Duck2006 said:**
> If it is a win modem you may not even get drivers for it in linux.
There is slmodem including slamr and slusb modules, the install is definitely not trivial, best to buy a full modem.

---

### Post by jeffus_il on 2008-06-04
Consider giving him GMail and Google Docs which make the system smaller and requires less maintenance. so all he needs is a browser!

---

### Post by mikewhatever on 2008-06-04
> **jeffus_il said:**
> Consider giving him GMail and Google Docs which make the system smaller and requires less maintenance. so all he needs is a browser!

There is limited access to the web, remember?

---

