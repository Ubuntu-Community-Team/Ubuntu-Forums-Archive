---
title: "Ubuntu and old laptops"
date: 2008-09-17
forum: New to Ubuntu
---

### Post by jskeys on 2008-09-17
Folks,
  I work in Southern Sudan and travel every few months back to the U.S.  I often try to pick up some of the old laptops (as far back as 133 Mhz processors.  I bring them back and give them to students who have nothing (and I do mean nothing).  In the past I have tried to load Win 95 so they did not have to learn DOS.  I'm getting ready to return to the U.S. again.  I am not real experienced with Ubuntu,so can anyone tell me if I can load Ubuntu (which versions) on those old machines to give them another life with a student?

Thanks in advance,  John

---

### Post by Patrick793 on 2008-09-17
You could give Xubuntu a try, since that is made for more low spec systems. If that doesn't work, give DSL a try.

---

### Post by Alien.col on 2008-09-17
There is a light version of Ubuntu called Xubuntu. It is a very light installation of Ubuntu but has all the modern features that the latest OS's have. You would have to check for the stability of the particular laptop first though. You can find more info here: [http://www.xubuntu.org/](http://www.xubuntu.org/)

Ubuntu is "lighter" than Windows Vista and somewhat similar in terms of cpu load to a clean windows xp installation. In an old laptop it will be slow I think, it is best if you give xubuntu a try first i think.

---

### Post by LowSky on 2008-09-17
[https://help.ubuntu.com/community/Installation/SystemRequirements](https://help.ubuntu.com/community/Installation/SystemRequirements)

your better of trying puppy linux or DSL, maybe even Debian (which Ubuntu is based)

---

### Post by linuxlizard on 2008-09-17
Forget ubuntu or any spinoff like fluxbuntu if you are using systems that old- it's too heavy and will run like a slug. I know because I've tried them all and most recently a couple of weeks ago.

PCFluxboxOS will run nicely on older laptops (I've got a p3 700 lapto with 192 mb ram and pcfluxboxos feels just as fast as ubuntu on my amd 3200+ with 756 mb ram and set up all my hardware on install including my belkin wireless card- pcfluxboxos feels very comfortable on an old 333mhz with 128 mb ram desktop that I use sometimes for website development as well)

fluxbox can take a little getting used to- for icons wbar and for start menu fbpanel work nicely.

Otherwise try TinyMe which has the same performance but an easier to use desktop manager than fluxbox (well at least fluxbox without wbar and fbpanel) for new users.

If it has just a little more horsepower (more than 128 mb ram) Sam linux has an even easier desktop (xfce).

All 3 of these are based on pclinuxos and are absolutely wonderful for older hardware. And your users can use synaptic to install thousands of the latest software packages with a couple of clicks of the mouse. The latest firefox3, gimp, open office, bluefish, etc- all run very comfortably on my old 333mhz with 128 mb ram computer running pcfluxboxos.


Other alternatives include puppy and damn small linux- I have fun with those, but they aren't standard linux in structure so users can't necessarily transfer what they learn with these OS to other linux systems and users can't get the thousands of packages like these that I recommend, and performance and system requirements are the same so why choose one that isn't full featured?

---

### Post by snowpine on 2008-09-17
> **jskeys said:**
> Folks,
  I work in Southern Sudan and travel every few months back to the U.S.  I often try to pick up some of the old laptops (as far back as 133 Mhz processors.  I bring them back and give them to students who have nothing (and I do mean nothing).  In the past I have tried to load Win 95 so they did not have to learn DOS.  I'm getting ready to return to the U.S. again.  I am not real experienced with Ubuntu,so can anyone tell me if I can load Ubuntu (which versions) on those old machines to give them another life with a student?

Thanks in advance,  John

Hi John, good for you, I am a big believer in recycling old hardware and putting it to good use.

The following is just my opinion: 
Ubuntu is designed to run well on most new computers being sold today. With a decent processor and 512mb-2gb of ram, it gives good performance. The oldest system I've been able to install it on was a 650mz Pentium 3 with 256mb. I had to use the Alternate CD to install, and performance was mediocre. I have since switched to a lighter OS on that machine because speed is important to me. 

Xubuntu is the "official" variant of Ubuntu for older hardware. I tried it on the 650mz P3 w/256mb that I mentioned above. My impression is that it was *slightly* faster than Ubuntu. There was a noticeable difference, but it was not night-and-day. In my opinion, Canonical needs to develop a *truly* lightweight Ubuntu variant. Which leads me to...

"Unofficial" Ubuntu variants/remixes. Fluxbuntu, Crunchbang, Ubuntulite, Boxbuntu, etc. The best thing you can do to boost Ubuntu performance is to switch to a lightweight windows manager such as Openbox or Fluxbox. I'm currently using Crunchbang (which uses Openbox) on the P3 computer mentioned above, and it's quite a bit faster than Xubuntu ever was. The downside to these variants is they do not have the same level of community and support as an official Ubuntu release. 

To conclude, Ubuntu is arguably the most modern and user-friendly desktop Linux available. However, this comes at the price of performance. Any variant that uses Ubuntu as its base is going to be heavy--128mb of ram *minimum*. To get truly good performance on ancient hardware, you should look outside the Ubuntu family. Debian is quite similar, yet has lighter system requirements. Then, there are ultra-light distros such as DSL, Puppy, and SliTaz. These will run circles around Ubuntu on old hardware.

Hope that helps you out! Kudos for undertaking that project.

---

### Post by starcannon on 2008-09-17
Fluxbuntu and Damn Small Linux are going to be 2 very excellent choices for that old pii 133mhz iron. If you are working with 366mhz or faster xubuntu works pretty good if you have 128mb or more ram.

GL and have fun.

---

### Post by viltrio on 2008-09-17
> **jskeys said:**
> Folks,
  I work in Southern Sudan and travel every few months back to the U.S.  I often try to pick up some of the old laptops (as far back as 133 Mhz processors.  I bring them back and give them to students who have nothing (and I do mean nothing).  In the past I have tried to load Win 95 so they did not have to learn DOS.  I'm getting ready to return to the U.S. again.  I am not real experienced with Ubuntu,so can anyone tell me if I can load Ubuntu (which versions) on those old machines to give them another life with a student?

Thanks in advance,  John

I think that you should, at least, try a minimal installation with ubuntu-server edition.

If you succeed, you could try to install graphical server and a lightweight desktop-manager like fluxbox.

> sudo apt-get install xserver-xorg fluxbox

---

