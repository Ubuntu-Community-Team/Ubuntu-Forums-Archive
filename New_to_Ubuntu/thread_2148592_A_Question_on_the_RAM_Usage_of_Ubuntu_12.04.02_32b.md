---
title: "A Question on the RAM Usage of Ubuntu 12.04.02 32bit Desktop"
date: 2013-05-25
forum: New to Ubuntu
---

### Post by hangpan on 2013-05-25
Based on my "old" experience, 32bit OS should be only support RAM less than 3.5~4GB, but why ubuntu 32bit supports RAM over 4GB. I didn't install any 3rd party software, or anything to do with PAE tools.

Environment:
[LIST=1]
[*]VMWare Workstation 9
[*][COLOR=#000000][FONT=Lucida Grande]Ubuntu 12.04.02 32bit Desktop Version[/FONT][/COLOR]
[/LIST]

Please refer to the image below:
[ATTACH=CONFIG]243042[/ATTACH]

It would be appreciated for any comments on this.

Thanks,
Hang

---

### Post by HiImTye on 2013-05-25
what kernel are you using?

---

### Post by deadflowr on 2013-05-25
I'st called a PAE kernel.

---

### Post by mörgæs on 2013-05-25
Ubuntu 12.04 comes by default with PAE.

---

### Post by sanderj on 2013-05-26
> **hangpan said:**
> Based on my "old" experience, 32bit OS should be only support RAM less than 3.5~4GB, but why ubuntu 32bit supports RAM over 4GB. I didn't install any 3rd party software, or anything to do with PAE tools.



Correct: in the *old* days, 32-bit kernel meant no more than 3.5GB RAM usage.
However, current Ubuntu versions install the PAE kernel by default, and thus will access all the RAM you have got.


So ... boom ... there goes an advantage of 64-bit. ;-)
The only advantage of 64-bit I now know, is: no rollover of the TX/RX byte counter in ifconfig ... 

HTH

---

### Post by Paqman on 2013-05-26
> **sanderj said:**
> 
So ... boom ... there goes an advantage of 64-bit. ;-)
The only advantage of 64-bit I now know, is: no rollover of the TX/RX byte counter in ifconfig ... 


Not really. A 64-bit kernel supports large amounts of RAM natively, without having to run hacky PAE in userspace.

The main advantage of 64-bit remains the same; it's significantly faster for any kind of serious number crunching (eg: video or audio re-encoding, encryption, compression, etc). PAE is cool, but it's really just a bridging solution while we complete the switch to the new standard of 64-bit.

---

### Post by Cheesemill on 2013-05-26
Although a PAE kernel can address more than 4GB of RAM, it doesn't do it very well.
You may want to read what Linus thinks of the PAE kernel...

[Linus on PAE]("http://cl4ssic4l.wordpress.com/2011/05/24/linus-torvalds-about-pae/")

---

### Post by hangpan on 2013-05-26
Many thanks guys, learn a lot. The kernel version I used is: [B][I]Ubuntu 12.04.02 LTS
[/I][/B]
You guys are right, the 32bit 12.04.02 ubuntu came up with pae-enabled, I found it here as well: [http://ubuntuforums.org/showthread.php?t=1919647](http://ubuntuforums.org/showthread.php?t=1919647)
I know little about PAE, now it's time to pick it up. ;)

Thanks everyone again.

---

### Post by sanderj on 2013-05-26
> **hangpan said:**
> Many thanks guys, learn a lot. The kernel version I used is: [B][I]Ubuntu 12.04.02 LTS
[/I][/B]
You guys are right, the 32bit 12.04.02 ubuntu came up with pae-enabled, I found it here as well: [http://ubuntuforums.org/showthread.php?t=1919647](http://ubuntuforums.org/showthread.php?t=1919647)
I know little about PAE, now it's time to pick it up. ;)

Thanks everyone again.

Why not use 64-bit?

---

### Post by KdotJ on 2013-05-26
> **sanderj said:**
> Why not use 64-bit?

+1 to this. If its not too much inconvenience, start again with the proper architecture rather than add on a workaround.

---

### Post by hangpan on 2013-05-26
Thanks for your reply, [COLOR=#000000]sanderj and KdotJ, I am a pure newbie to Ubuntu, usually, I take CentOS 6 as my web app server with no GUI, and my workstation is always on Windows, at least, in 95% of cases.
I am thinking if I can do some development on Linux desktop, and see Ubuntu is so popular and even propagated by some of my colleagues, so, want to give it try. :)
I downloaded and installed this 32bit version is all because "Recommended" on download page. If I didn't see this word, I believe I had 64bit desktop version played.[/COLOR][COLOR=#000000][/COLOR]

---

### Post by hangpan on 2013-05-27
what's the heck, now the "recommended" is gone...
I am quite, absolutely, positively sure that it shows me "32bit (Recommended)" while I am downloading the desktop version.
Now it's showing 64bit (for newer machine)... hmm...slick...:rolleyes:

---

### Post by deadflowr on 2013-05-27
> **hangpan said:**
> what's the heck, now the "recommended" is gone...
I am quite, absolutely, positively sure that it shows me "32bit (Recommended)" while I am downloading the desktop version.
Now it's showing 64bit (for newer machine)... hmm...slick...:rolleyes:

I notice that too.
Nice change, but I still don't like the dropdown.
I'd rather see both listed with a checkbox to choose from.
But beggars can't be choosers.

---

