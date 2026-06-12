---
title: "Rolling distribution like Debian VS. 6 month release like Ubuntu in Linux"
date: 2010-11-09
forum: Recurring Discussions
---

### Post by COKEDUDE on 2010-11-09
I am curious about everyone's opinion on a Rolling distribution like Debian VS. a 6 month release like Ubuntu. What are some previous problems that have occurred with one type over the other? Why do you prefer one over the other? I am trying to decide if I want to use Linux Mint Debian or Linux Mint Julia (the newest version of Mint being released in November). I have been using Linux Mint Isadora since May and like it a lot. I wanna try something new.

---

### Post by overdrank on 2010-11-09
Moved to Recurring Discussions

---

### Post by NightwishFan on 2010-11-09
I am not personally fond of using a rolling release. In some cases you are not guaranteed to have a package be supported for any amount of time. Such as if you update a certain library and your desktop can no longer use the gnome shell until the packages are synced to be compatible again.

A solid time based release offers much more predictability and sometimes stability (as in the repositories stay constant) and fixes (such as in-place backports). You might not have everything bleeding edge; Though usually it is best to know what you want and what is tested than to use something that is simply new. (Though that does not mean it will not be in working order etc). For example, I like Banshee, so I easily add a ppa to backport it to Lucid rather than have to roll my whole distribution to have the newest stuff. Everything else is predictable and constant, though I have a newer Banshee.

I say, it depends. However a time based release wins for me on flexibility.

---

### Post by dummy910 on 2010-11-09
To me any software that is updated, is rolling(as in progess), especially that of open-source as its rpms are a bit faster than most...

Great thread btw :biggrin:

---

### Post by TBABill on 2010-11-09
It's almost a "pick your poison" decision for me. I have used distros on a rolling release and they were no less stable than the distros on a fixed release with security and some app updates. One would tend to think the rolling release would leave a distro more susceptible to breakage and incompatibilities or missing dependencies, but those of us using Ubuntu realize we see breakages for similar and other reasons here as well during an update cycle. Fortunately it is not frequently in my experience, but it happens. And so too did it happen with rolling release. 
 
The experience, however, is different. I was on a KDE system and the KDE upgrades came in a flurry over a period of a month or two. They were very rapid and some were quite drastic. For users accustomed to doing things a certain way there was a new, but short, learning curve. 
 
If you like consistency with pretty up to date software, the 6 month cycle works but causes you more install and download work. If you like truly cutting edge stuff, rolling release in some cases can provide that. If you just like rock solid with up to date software for the first year or two, then sticking with the LTS is a safe bet.
 
There's no right or wrong, just different. I got off the rolling release distro, but not because of the rolling release system. I had video issues that were not supported yet. So, pick your poison and enjoy.

---

### Post by mobilediesel on 2010-11-09
When did Debian become a rolling release?

---

### Post by NightwishFan on 2010-11-09
Debian testing and unstable are constantly updated.

---

### Post by mobilediesel on 2010-11-09
> **NightwishFan said:**
> Debian testing and unstable are constantly updated.

Ah, I was thinking "officially released" but those two versions can definitely be considered rolling releases. That's what I get for running out of caffeine.

---

### Post by slackthumbz on 2010-11-09
Rolling releases can be nice but the obvious advantage to a timed release that I can see is that it makes much easier to make large scale changes to the core system in a single fell swoop (however that makes upgrading via apt a real pain) so pros and cons either way, find the distro that works for you and enjoy :)

---

### Post by Shining Arcanine on 2010-11-11
> **mobilediesel said:**
> When did Debian become a rolling release?

Debian is on a two-year release cycle.

> **NightwishFan said:**
> Debian testing and unstable are constantly updated.

Ubuntu's development branch is constantly updated too, but that is not a rolling distribution in and of itself. You need something like aptosid on top of that to produce a rolling distribution:

[http://www.aptosid.com/](http://www.aptosid.com/)

---

### Post by NightwishFan on 2010-11-11
Yes, I am obviously aware they are not true rolling distributions. Though in all practical aspects they work fine.

---

### Post by cascade9 on 2010-11-12
> **Shining Arcanine said:**
> Debian is on a two-year release cycle.

Ubuntu's development branch is constantly updated too, but that is not a rolling distribution in and of itself. You need something like aptosid on top of that to produce a rolling distribution:


No, debian is on a two year freeze cyctle now. It will still be unfrozen to 'stable' 'when its ready' in the classic debian style.

Umm....ubuntu developmenty branch with aptosid 'on top'? I dont think thats possible....

---

### Post by handy on 2010-11-12
I use Arch because I'm lazy. :)

System upgrades everyday (usually not many files) suits me. If on a rare occasion the upgrade brings trouble, you just roll back the troublesome file(s), which thankfully is a quick & easy proposition, once you know how. You then watch the Arch forum & News page & upgrade the broken bit(s) when they have been fixed. Which is usually pretty quickly.

The Arch install I'm using now, is 2 years & pushing 8 months old. I just about live on this system; trouble rarely comes, even though I've chosen to be using the testing kernels & the FOSS -git packages that my AMD GPU uses, for most of the last 15 months.

Though I do understand that systems like Arch could drive many people mad, as they don't want to be using the Terminal to do things, & don't like the way they have to initially build their system.

Horses for courses. 

It truly is great that there exist so many FOSS choices for us to mess around in until we find just what we like. :)

---

