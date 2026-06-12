---
title: "[SOLVED] Help Picking Webserver distro!"
date: 2008-07-22
forum: Other OS Talk
---

### Post by El Conquistador on 2008-07-22
Hi, well i use ubuntu as my main operating system around the house so i kinda know how to work with it, however ive also had some expirience with Fedora and Red Hat. now as i have been doing some googling on "the best webserver OS" ive found that many people like red hat and fedora for their webservers(what makes them better than ubuntu?). i also found that CentOS might be a good option. so my question is (i guess it would be in your opinion) 

what is the best webserver distro for ME to use? and what are the benefits of using that particular OS?

it would have to work well with apache and Samba. preferably with a package manager and if you want go ahead and throw in some advice on some 'not do obvious' security setup. All help is appreciated! sorry in advance for the broad question.

---

### Post by cariboo on 2008-07-22
If you want to try out apache2 on Ubuntu you can install the LAMP server package and try it out to see you it works for you. FYI Redhat and Fedora are based on the same core. Fedora is the desktop version of Redhat. I used Redhat v 6.0 as my first stab at linux and to this day I still don't like RPM based distributions.

To install the LAMP server package you can use tasksel to install it. in a terminal type:

```
tasksel
```

Select LAMP and let it inatall Apache2, Mysql and PHP.

Jim

---

### Post by El Conquistador on 2008-07-22
ok well thank you very much that LAMP install will save me some time. i guess i will just install it in ubuntu and see how that works out i just wondered why there wasnt many people who used it as their webserver, according to the pages and forums i read at. But thanks again!

---

### Post by dca on 2008-07-22
> **cariboo907 said:**
>  FYI Redhat and Fedora are based on the same core. Fedora is the desktop version of Redhat. 


  
No, Fedora grows up to become RHEL...  It's a test-bed for it.  RHEL has its own enterprise (not for personal desktop use I guess) desktop edition...  CentOS is a free binary-compatible vers of RHEL.  Basically same packages as RHEL w/o any branding...

---

### Post by Bachstelze on 2008-07-22
> **dca said:**
> No, Fedora grows up to become RHEL...  It's a test-bed for it.  RHEL has its own enterprise (not for personal desktop use I guess) desktop edition...  CentOS is a free binary-compatible vers of RHEL.  Basically same packages as RHEL w/o any branding...

You are both wrong. Fedora is a community-maintained distribution sponsorized by RedHat, and RHEL is developed and maintained by RH. They are distict project, each with its own developers and roadmap.

---

### Post by volkswagner on 2008-07-22
Not sure if this means anything.  GoDaddy provides dedicated Linux servers in CentOS and Red Hat F7 flavors.  You may be onto some good choices.  You may want to poke around the servers and security forums to get other opinions.

HowToForge has some useful howto's.  I followed this one...

[http://howtoforge.com/perfect-server-ubuntu8.04-lts]("http://howtoforge.com/perfect-server-ubuntu8.04-lts")

I had one issue which I posted in "servers and Security".  Other than that it went without a hitch.  Better than the 6.06 howto.

I must say, IspConfig was not for me.  It seems to be geared toward resellers.  I had better results just using webmin.

---

### Post by cardinals_fan on 2008-07-22
CentOS/Red Hat, Slackware, or FreeBSD.

---

### Post by El Conquistador on 2008-07-22
well i appreciate all your help guys. since i started this thread ive been doing some reading and now i think ive decided im gonna go with CentOS. however they just released a CentOS live CD now i havent downloaded it yet so i dont know if it has a install option like the ubuntu cd's have. would any of you know the answer to that question. and if it does infact have an install option would that be enough to run my webserver or would i still need to download the install DVD? Thanks again everyone!

---

### Post by cardinals_fan on 2008-07-23
> **El Conquistador said:**
> well i appreciate all your help guys. since i started this thread ive been doing some reading and now i think ive decided im gonna go with CentOS. however they just released a CentOS live CD now i havent downloaded it yet so i dont know if it has a install option like the ubuntu cd's have. would any of you know the answer to that question. and if it does infact have an install option would that be enough to run my webserver or would i still need to download the install DVD? Thanks again everyone!
The CentOS live CD does not include an installer like Ubuntu's, but it does allow you to run a network installation.

---

### Post by dca on 2008-07-23
> **HymnToLife said:**
> You are both wrong. Fedora is a community-maintained distribution sponsorized by RedHat, and RHEL is developed and maintained by RH. They are distict project, each with its own developers and roadmap.

So then the guts of FC5 or 6 did not become RHEL5? Hmm, the only difference I see are ports made (by RH) to other archs outside x86 & 64 and the red hat trademarks...
 
The above explanation (IMHO) is the diplomatic or political explanation given on the Fedora website not what people should know when choosing a distribution used outside of plinking around on a laptop or three year old PC...
 
I'd still stick with either CentOS 5.x or Ubuntu Server Ed 8.04.x depending on your comfort zone between apt & yum.

---

### Post by El Conquistador on 2008-07-24
thanks cardinals_fan for letting me know about the no install feature. and thanks you dca for recommending ubuntu server edition. i cant believe it never even came to mind! however i think im going to try CentOS this way i get to have new expiriences and learn some more. however i am curious to find out something that maybe you guys could shed some light on. ive read that ubuntu server edition is commad line only with NO GUI. but ive also read that you can just as easily install it afterword by using apt and installing a desktop. is this true? and if so does it behave like regualar ubuntu box but with just added capabilities? does the gnome desktop let you access the server versions features through some kinda of front-end?  or are they built in to the desktop? finally i also read that you could take a regular ubuntu desktop and install LAMP and it would function just as the server version is this true? as far as programs go, because i cant imagine that just installing LAMP would magically turn it into a server. well i hope you guys can help THANKS AGAIN!

---

### Post by Bachstelze on 2008-07-24
> **El Conquistador said:**
> ive read that ubuntu server edition is commad line only with NO GUI. but ive also read that you can just as easily install it afterword by using apt and installing a desktop. is this true?

Yes.

> **El Conquistador said:**
> and if so does it behave like regualar ubuntu box but with just added capabilities? does the gnome desktop let you access the server versions features through some kinda of front-end?  or are they built in to the desktop?

No, there is no GUI administration tool (that I know of). Overall, while instaling a GUI on a server is technically possible, it is to me prett pointless, and I therefore don't recommend it.

> **El Conquistador said:**
> finally i also read that you could take a regular ubuntu desktop and install LAMP and it would function just as the server version is this true?

Yes.

> **El Conquistador said:**
> as far as programs go, because i cant imagine that just installing LAMP would magically turn it into a server.

Why not? Of course, it does. Having Apache installed makes your machine a Web server, regardless of everything else that is installed on it.

---

### Post by dca on 2008-07-24
> **HymnToLife said:**
> 

No, there is no GUI administration tool (that I know of). Overall, while instaling a GUI on a server is technically possible, it is to me prett pointless, and I therefore don't recommend it.


Exactly, you can still do a text install for CentOS...  From a support standpoint I think you get better responses on the Ubuntu forums, though.

---

### Post by El Conquistador on 2008-07-24
Ok Well I would like to thank you all very much for all your help. i think ive gotten all my questions answered for now. ok so now i have to figure out how to mark this as solved. Thanks again!

---

### Post by cardinals_fan on 2008-07-24
> **El Conquistador said:**
> Ok Well I would like to thank you all very much for all your help. i think ive gotten all my questions answered for now. ok so now i have to figure out how to mark this as solved. Thanks again!
Thread Tools -> Mark as Solved

---

### Post by david_lynch on 2008-07-24
It seems odd that you wouldn't just go with ubuntu, since you are already familiar with it - as for the abundance of redhat and the redhat clone centos, the fact is that in the 90s, redhat was pretty much it, and gained a big market share during those days, but debian has a healthy and growing web presence and the debian-based ubuntu, although a latecomer, is gaining ground fast.

ubuntu comes with all the software and package management utilities you need for setting up web services. I moved my maia mailguard system from suse to ubuntu and was amazed at how easy and trouble-free the move was.

---

