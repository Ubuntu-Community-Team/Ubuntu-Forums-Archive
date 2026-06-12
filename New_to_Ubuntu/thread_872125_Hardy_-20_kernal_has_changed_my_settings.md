---
title: "Hardy -20 kernal has changed my settings"
date: 2008-07-27
forum: New to Ubuntu
---

### Post by bwallum on 2008-07-27
Hi, My Ubuntu has done strange things following a motherboard transplant. It has upgraded to a -20 kernal. Software Sources now prevents me from ticking the hardy-security tick box under the updates tab. Instead I have numerous listings relating to hardy-security in my third party software tab.

Anybody else get this? What's happened with the -20 kernel that changes the security to third party?

Rgds
Bob

---

### Post by gjoellee on 2008-07-27
you should actually not use kernel 2.6.26-20 because it is so much wrong with it....uninstall from synaptec is my advice. use kernel 2.6.26-19 instead

fact:
kernel 2.6.26-20 is a pre-release, and for many computers it don't even boot

---

### Post by Elfy on 2008-07-27
> Anybody else get this? What's happened with the -20 kernel that changes the security to third party?Mine changed some time ago for some reason - it wasn't the -20 kernel.

I think that there is a bug report for it - I'm loathe to look myself as it is taking me ages to load launchpad bug pages at the moment :)

Edit - have to say I have no problems with it at all.

---

### Post by gjoellee on 2008-07-27
you are the first one I have ever heard about that have no problems with that kernel!!!!:lolflag:

---

### Post by markbuntu on 2008-07-27
Well, I just looked in Synaptic and you are correct about that. As long as the security updates show up, I don't care about a little cosmetic change.

I had only a small problem with the -20 kernel and the kernel modules for my video driver. I had to load them manually. But, the kernel told me that when it was installing itself.

Anyway, I still have all the kernels back to -16 so I don't worry too much.

---

### Post by Liakath on 2008-07-27
Dear Bob,

> **bwallum said:**
> Hi, My Ubuntu has done strange things following a motherboard transplant. It has upgraded to a -20 kernal. Software Sources now prevents me from ticking the hardy-security tick box under the updates tab. Instead I have numerous listings relating to hardy-security in my third party software tab.

Anybody else get this? What's happened with the -20 kernel that changes the security to third party?

Rgds
Bob

I have also updated to Hardy -20 Kernel (generic & rt). My software sources still remain the same as before. I did not find any problem under Hardy 8.04.1 on this count. See the Screen shots of my "Software Sources"

Of course what you had described happened with me on my Intrepid Ibex 8.10 Alpha 2 which I had on my Desktop; I do not have any clue why it is so in your case.

May be some of our learned friends will throw some light on this.

Liakath

---

### Post by steveneddy on 2008-07-27
I recently turned off Proposed updates.

I have the -20 kernel and so far it's ok, but I would like to see the stable version of -20 come along fairly quickly.

---

### Post by Nepherte on 2008-07-28
Most people need to realize that the proposed repository is very different to other repositories, i.e. they rather offer beta, unstable packages than stable ones. It is therefore recommended you disable the hardy-proposed repository unless you have an interest in testing updates and providing feedback.

---

### Post by northern lights on 2008-07-28
> **Nepherte said:**
> Most people need to realize that the proposed repository is very different to other repositories, i.e. they rather offer beta, unstable packages than stable ones. It is therefore recommended you disable the hardy-proposed repository unless you have an interest in testing updates and providing feedback.
+1

I'd recommend leaving backports and proposed disabled on your primary working machine.

---

### Post by stevoo on 2008-07-28
interesting ... nothing changed on mine. But i tried un clicking the security update and i couldnt re enable it. The only way to to click revert instead. 

So perhaps it wasnt even enabled from before ? 

But it seems .20 does screw a few thinks here and there

---

### Post by ibuclaw on 2008-07-28
Yes, backports and proposed cause no end of trouble if you don't know what your doing.
Infact, I never add them unless I pin the stable hardy repos first.
Then I just install newer versions of packages/new packages that are in the ubuntu testing repo when I require them.
compiz-0.7-git, 2.6.26-4-kernel and codeblocks are some examples of packages I've pin-installed.

[https://help.ubuntu.com/community/PinningHowto](https://help.ubuntu.com/community/PinningHowto)

Someting, such as this in both preferences files would have prevented this entirely...
```
Package: *
Pin: release a=**releasename**
Pin-Priority: 900

```
where "releasename" would be **hardy**, **hardy-updates** and **hardy-security**.

Regards
Iain

---

### Post by waspbr on 2008-07-28
I have mixed feeling about the new kernel, My oldish desktop (athlonXP 3000+) did not like it, it freezes during boot, but no worries, I can just boot from 19.

though newish laptop (hp tx1320us) didn't mind it at all, though it seemed to have 'misconfigured' my cpu frequency scaling, I think it is fixed now, I am saying I think because I have been using intrepid more and more lately. asided from the lack of  3rd party repos, it runs really well... something to look foward too... though until release a lot can change...

---

