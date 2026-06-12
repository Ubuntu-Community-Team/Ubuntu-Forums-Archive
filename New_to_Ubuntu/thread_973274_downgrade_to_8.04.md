---
title: "downgrade to 8.04"
date: 2008-11-06
forum: New to Ubuntu
---

### Post by Zopiac on 2008-11-06
i really hate 8.10, how do i switch back to 8.04? thanks

---

### Post by coolbrook on 2008-11-06
What is it you dislike about Intrepid?

Backup your important data and do a clean install from the 8.04 CD.

---

### Post by bobbob1016 on 2008-11-06
1)  Download 8.04
2)  Burn it the same way you did for 8.10
3)  Boot from the 8.04 CD

That is the best way.  I'd think an actual downgrade would be very messy, since you have settings leftover from 8.10, and 8.04 versions of those programs would get confused.

---

### Post by Cypher on 2008-11-06
As with every other Ubuntu release, there is no downgrade path. The only way to downgrade is to re-install the previous version from scartch and preferably after formatted the partitions. 

So if you have your /home directory on a seperate partition, you can safely format the remainder parititons and isntall Ubuntu 8.04. You MIGHT still have some issues with some of your configuration files that might have been converted to the newer versions of the applications that came with Intrepid..

---

### Post by lovinglinux on 2008-11-06
I have a separated /home partition and I simply did a fresh 8.04 install, keeping the /home partition. Everything is working fine here after the downgrade.

But if you did an upgrade to 8.10 instead of a fresh install, then things can get messy.

---

### Post by drakeman007 on 2008-11-06
> **Zopiac said:**
> i really hate 8.10, how do i switch back to 8.04? thanks

Dont say that, i love it.!

---

### Post by blazercist on 2008-11-06
There is no way to "downgrade".  You have to do a clean install.  You can try and backup your /home directory to some external media and just plop it back in 8.04 once you've installed it again, there's no garantee it'll work properly but there's a chance.

---

### Post by Bölvaður on 2008-11-06
My post will be useless:

There is no "downgrade". If it works, it works, it if doesn't... then it probably works for someone else :)
There is actually no real reason to "upgrade" each time when ubuntu makes new release.

Perhaps something which is good to keep in mind

---

### Post by richg on 2008-11-06
I found some features of 8.10 I did not like so I went back to 8.04. I use removable hard drives, one drive one OS. I still have a couple drives with 8.10. I might try it again in a couple months to see if anything has improved.
I back up my files to an external drive so no issue there.
One real annoying issue is when I click on Places then documents, K3B opens and I see a message that says, File not found.
I have to click Places, Computer to get to my files.

Gimp now has a tool box that stays in your face. Could not figure out how to hide that one.
Gimp in 8.04 has something like the Tool box but it hides when I click the photo.

Rich

---

### Post by Zopiac on 2008-11-07
> **coolbrook said:**
> What is it you dislike about Intrepid?

Backup your important data and do a clean install from the 8.04 CD.

mainly , so far, the remmoval of a certain tab in the Sessions prefs that allowed me to take out the last gnome-panel in Hardy...there were other things, but i cant remember them

---

### Post by nagolchi on 2008-11-10
gotta agree. 8.10 has been a disaster for me.  many things stopped working that worked fine in 8.04. can't seem to get them working again even with heavy tinkering.  everything seems to run slower.  just seems really buggy without any benefit.  wish i hadn't upgraded

---

### Post by fozzya on 2008-12-26
[https://help.ubuntu.com/community/DowngradeHowto](https://help.ubuntu.com/community/DowngradeHowto)

---

### Post by shankhs on 2008-12-26
> **nagolchi said:**
> gotta agree. 8.10 has been a disaster for me.  many things stopped working that worked fine in 8.04. can't seem to get them working again even with heavy tinkering.  everything seems to run slower.  just seems really buggy without any benefit.  wish i hadn't upgraded
I agree dude , my Ubuntu System has become very slow I thought that its because of low empty space for / and /home partition and only 512 MB swap space but I found a lot of users are having the same problem. I wonder if I can get rid of this!!!!

---

### Post by xyepblra on 2009-03-15
Guys, I clearly see from the posts above that there is no downgrade. At the same time, I really regret I did an upgrade from Hardy to Intrepid, because now I have my obex not workibg, Evolution being unable to process my mail, Firefox glitching and a lot of other bigger and smaller things to increase my regret. Anyway, the reason why I upgraded was, I did not know how to "install from a scratch", as people on this forum often say. Can anybody please give me an instruction on how to install Intrepid from a scratch instead (and over) axisting Intrepid I got by upgrade?

---

### Post by hyper_ch on 2009-03-15
> **nagolchi said:**
> gotta agree. 8.10 has been a disaster for me.  many things stopped working that worked fine in 8.04. can't seem to get them working again even with heavy tinkering.  everything seems to run slower.  just seems really buggy without any benefit.  wish i hadn't upgraded

How many of those things have you reported or asked for help?

---

### Post by terrox on 2009-06-24
I think for anyone who relies on the 71.86.xx legacy nvidia drivers, the 8.10 and 9.04 is a dead end for 3D acceleration. Nvidia legacy driver still does not support xorg 1.6.0 and that is what 9.04 has (8.10 has 1.5.1 I think?). 

If there was a way to downgrade xorg-server to a version which legacy 71.86.10 driver worked with, then I would stay with 9.04 but I don't think that is possible.

So for Anyone on a GPU listed below, no more 3D with ubuntu 8.10 or ubuntu 9.04 ... why would you have this GPU? for developer testing when making low-poly games and trying to support old hardware. Old laptop, backup GPU incase current one explodes.. I dunno.

```
The 71.86.xx driver supports the following set of GPUs:
RIVA TNT	
RIVA TNT2/TNT2 Pro	
RIVA TNT2 Ultra	
Vanta/Vanta LT	
RIVA TNT2 Model 64/Model 64 Pro	
Aladdin TNT2	
GeForce 256	
GeForce DDR	
Quadro	
GeForce2 GTS/GeForce2 Pro	
GeForce2 Ti	
GeForce2 Ultra	
Quadro2 Pro
```

---

### Post by cjv8888 on 2009-06-24
> **richg said:**
> 
One real annoying issue is when I click on Places then documents, K3B opens and I see a message that says, File not found.
I have to click Places, Computer to get to my files.



same thing happened to me on 9.04 with k3b coming out blinking wildly whenever Places/Home was clicked.
I went back to 8.04 also.

---

### Post by mcurtiss1970 on 2009-10-27
> **terrox said:**
> I think for anyone who relies on the 71.86.xx legacy nvidia drivers, the 8.10 and 9.04 is a dead end for 3D acceleration. Nvidia legacy driver still does not support xorg 1.6.0 and that is what 9.04 has (8.10 has 1.5.1 I think?). 

If there was a way to downgrade xorg-server to a version which legacy 71.86.10 driver worked with, then I would stay with 9.04 but I don't think that is possible.

So for Anyone on a GPU listed below, no more 3D with ubuntu 8.10 or ubuntu 9.04 ... why would you have this GPU? for developer testing when making low-poly games and trying to support old hardware. Old laptop, backup GPU incase current one explodes.. I dunno.

```
The 71.86.xx driver supports the following set of GPUs:
RIVA TNT	
RIVA TNT2/TNT2 Pro	
RIVA TNT2 Ultra	
Vanta/Vanta LT	
RIVA TNT2 Model 64/Model 64 Pro	
Aladdin TNT2	
GeForce 256	
GeForce DDR	
Quadro	
GeForce2 GTS/GeForce2 Pro	
GeForce2 Ti	
GeForce2 Ultra	
Quadro2 Pro
```

Any word if 9.10 will rectify this issue?  (not that I expect it will)

---

