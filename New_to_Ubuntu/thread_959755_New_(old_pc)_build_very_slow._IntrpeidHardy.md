---
title: "New (old pc) build very slow. Intrpeid/Hardy"
date: 2008-10-26
forum: New to Ubuntu
---

### Post by iamdavid on 2008-10-26
Just finished putting together an older PC to run as secondary PC in the home. I can't believe how poorly the machine runs. :( I used the same PC to run Feisty on a while back and don't remember having any issues. Are the newer releases going to require more and more hardware recourses? I hope not since that's a huge reason I switched from MS. 


System specs:
AMD XP3000
512 MB DDR333 Ram 
ATI 9600Pro
150 Barracuda HDD

By poorly I mean it lags quite a bit when doing simple task like internet browsing and text office work. Takes about 10 seconds to start playing an MP3 or movie.

---

### Post by teaker1s on 2008-10-26
xp2200 in our office pc flys on 6.06lts, i'm guessing either boot options may be required or something is swallowing vast amounts of system resources. Do either syslogs or ```
top
``` provide any  clues

---

### Post by iamdavid on 2008-10-26
Thanks teaker1s but no. Nothing I can see. No programs using a large amount of resources. Just every-time a new program is started it takes around 7-10 seconds to load and shows ~100% CPU usage. Multitasking is completely out of he question. I'm going to add another stick of 512 ram but I don't think a Linux box should require that to run smoothly.

---

### Post by Xiong Chiamiov on 2008-10-26
Although this may not be an answer you like, I'd try using something other than Ubuntu.  If you'd like to stay with something similar, you can use Debian.  If you want a lot of control over what's running on your system, you can give Arch Linux a try.  It'll take a little bit of effort to get started, though, so don't do it if you need a point-and-click system installer.  I find that [The Arch Way]("http://wiki.archlinux.org/index.php/The_Arch_Way") often requires a small investment of time getting things setup compared to the time I save by not having unneeded things running (or even installed) on my machine.

---

### Post by ukera on 2008-10-26
well, since you just installed I'm guessing your have the minimum setup and the minimum setup is supposed to require very little.  about 250MB of your ram.  thats about half your RAM, so for your other programs like firefox, or whatever you use to watch your movies, you only have 262MB Of RAM to do other stuff.  i'm going to have to say no.  newer versions don't require more, you just need to upgrade your stuff man.  

[//www.newegg.com/Product/Product.aspx?Item=N82E16820231166]("http://www.newegg.com/Product/Product.aspx?Item=N82E16820231166")

check that out bro 4GB ram, for 79 bucks.  thats a good deal.  i just bookmarked it.  perhaps you should buy it and put it in your main computer, and take your other ram and put it in your "old pc".  good luck.

-ukera

---

### Post by teaker1s on 2008-10-26
I disagree with the ram suggestion for 2 reasons.
1) We have a 6.06lts system which flew on 512mb
2) Have atom 1.6ghz 512mb running intrepid flawlessly

Suggesting other distro's unless the issue is unresolvable could be considered un-helpful. I still believe that boot options may help or looking through logs for errors.

---

### Post by Miljet on 2008-10-26
I also disagree with the RAM suggestion because the RAM you suggested won't even fit in the machine in question. DDR2 won't fir DDR slots.

---

### Post by Xiong Chiamiov on 2008-10-26
> **teaker1s said:**
> I disagree with the ram suggestion for 2 reasons.
1) We have a 6.06lts system which flew on 512mb
2) Have atom 1.6ghz 512mb running intrepid flawlessly

Suggesting other distro's unless the issue is unresolvable could be considered un-helpful. I still believe that boot options may help or looking through logs for errors.
I agree with both of these.  Suggesting the purchase of new hardware is bad, unless actually needed.  Suggesting a different distro as a solution is also bad, although my intent was to provide another option for him to know about.

I think taking a look at what daemons are running might help.

---

### Post by bumanie on 2008-10-27
Distributions after feisty need 384mb ram to run. 512mb should be enough, unless you have a shared graphics card that takes some of your system ram.

---

