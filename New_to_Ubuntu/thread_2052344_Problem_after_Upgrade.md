---
title: "Problem after Upgrade"
date: 2012-09-03
forum: New to Ubuntu
---

### Post by 3dmatrix on 2012-09-03
I recently upgraded my Ubuntu from 11.10 to 12.04. Since then i am facing a few problems.

The first problem was of Grub. It worked well till i tried to boot in to the windows partition. And then it could not boot any more. Just the screen kept flickering. I had to reinstall grub from a live cd and then it worked fine. But i am still afraid to boot in to the windows partition fearing that the problem will come up again. How can i check that ?

IBus is not working properly. I can type in the other language but the pop-up menu that comes up showing the list of character options is not being displayed. So it gets difficult to select the right character.

The keyboard shortcut that is used (Fn+PrtSc) to take a snaphot is not working well. When i use it, it seems somthing happening (like a glow for a fraction of a second) but the Screenshot application finally does not works. But when i directly execute the Screenshot application it works fine.

The clock in the screenlets application is not working well. Every time i logout and re login, its config gets back to default setting. But if i do not logout and just suspend then it remains fine.

The new Ubuntu 12.04-1 that has been released can be upgraded from 12.04 or is there any other procedure to do that ?

Thanx !

---

### Post by 3dmatrix on 2012-09-05
Is there anyone who could help !

---

### Post by NikTh on 2012-09-05
Hello , 
this is a Thread with multiple problems. Difficult for someone to answer completely. 

Do you know what I suggest ? 

Fresh Install of Ubuntu 12.04.1 . It is quick  and I am almost sure , all of your problems will gone.

Ubuntu 12.04.1 : [http://releases.ubuntu.com/12.04/](http://releases.ubuntu.com/12.04/)

Thanks

---

### Post by 3dmatrix on 2012-09-06
Does it makes sense to instal every thing from scratch every 6 months ?
Many would say "Then dont upgrade"  :) funny !

When i tried to help one of my friend to migrate to lubuntu on a very old notebook, many on this forum offered this same advise - install again. And i ended up fresh installing 6 times :) but the problem remained. Finally some guys here were good enuf to spot the 'real' problem and i could get out of the chain of fresh installs.

Its so similar to the windows environment where often ppl advise to reinstall.

Anyway i have a feeling the problems are not too diverse. For example the ibus and screenshot prob seems to be related. And its been long time since 12.04 has been released and many would have faced similar problems. As i could not find those threads here so it would be nice if atleast any one could forward the links to such threads.

---

### Post by Wim Sturkenboom on 2012-09-06
> 
The new Ubuntu 12.04-1 that has been released can be upgraded from 12.04 or is there any other procedure to do that ?
12.04-1 is just a version with the latest updates (at the time that it is created). So if you started with 12.04 and applied all updates, you have 12.04-1 (and probably more).

> 
The keyboard shortcut that is used (Fn+PrtSc) to take a snaphot is not working well.
I have always used <alt><prtscr> (active window) and <prtscr> (whole screen); did you try those? I did not know that <Fn><prtscr> was an option.

> 
Does it makes sense to instal every thing from scratch every 6 months ?
Many would say "Then dont upgrade" funny !

No, it does not make sense to install every 6 months ;) It's only if you want to run the latest and the (maybe maybe maybe) greatest. Run LTS versions and it's only every 4 years :D

Sometimes upgrades do not work properly and the only way to make sure that there is not an old leftover from the previous version interfering with the upgrade is by doing a new install.

And that's how far I'm able to help.

---

### Post by NikTh on 2012-09-06
Hello , 

Ubuntu 12.04 LTS has support for 5 years now (Desktop - Servers) . So you will do a clean installation and at April 2017(where support will end)  , will see :) 

Thanks

---

### Post by 3dmatrix on 2012-09-07
> **Wim Sturkenboom said:**
> 

I have always used <alt><prtscr> (active window) and <prtscr> (whole screen); did you try those? I did not know that <Fn><prtscr> was an option.



In my keyboard prtscr = fn + prtscr

---

### Post by Epodx64 on 2012-09-07
If you have a seperate /home partition I'd honestly recommend doing a fresh install I never understood why Ubuntu made upgrading seem like a point and click operation. If anything if your going to upgrade you should killx and do it from a console I think anyway.

---

### Post by Wim Sturkenboom on 2012-09-07
> 
In my keyboard prtscr = fn + prtscr

Must have had a blackout; on my laptop as well ;)

---

