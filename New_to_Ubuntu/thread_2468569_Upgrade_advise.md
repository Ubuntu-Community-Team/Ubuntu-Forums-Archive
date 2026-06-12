---
title: "Upgrade advise"
date: 2021-11-03
forum: New to Ubuntu
---

### Post by foggybrain on 2021-11-03
Currently installed Xubuntu 20.04....(I've moved from Mint where i had no choice!). But unsure which is best - 

1) Stick to LTS path or move to regular releases - what are advantages / disadvantages?
2) If I move to regular release path when can I do it now or wait till after 22.04?

---

### Post by grahammechanical on 2021-11-03
Be careful what you wish for. You just might get it.

The latest standard Ubuntu release is 21.10. To get that installed through online upgrades you will have to upgrade 20.04 to 20.10 and then to 21.04 and then to 21.10. But 21.10 only has nine months support which means you will have to upgrade to 22.04 next April/May. On the other hand, if you stay with 20.04 until May or June 2022 you will be able to do a direct online upgrade from 20.04 to 22.04.

Or, you could simply download the 21.10 ISO image and install that instead of 20.04. Personally, I would dual boot with the 20.04 LTS and the 21.10 release. I will upgrade the 21.10 release to the 22.04 release and see how it runs before I upgrade my 20.04 to 22.04. And when I have done that I will upgrade one 22.04 to 22.10. And so it goes.

Regards

---

### Post by ajgreeny on 2021-11-03
Personally I always use the LTS only as my main system but I look at many other intermediate versions using all the DE versions available using virtual machines in KVM/QEMU, just to see what is happening in the Ubuntu (and other distros) world.

For stability I think the LTS versions win hands down, and see no good reason to use the intermediate versions long term; in fact you can not safely do so as they have supported life of 9 months only, meaning another distro version upgrade or another clean install must be carried out before support disappears. In real life this means every six months you have to upgrade or move by clean install to the next version with all the potential for problems that upgrading always gives.

Your Xubuntu 20.04 has another year and a half of support but you can not upgrade easily from that version to the current supported versions (21.04 or 21.10) as I think you can still only move either from one LTS to the next, ie 20.04 to 22.04, or from one intermediate version to the next version, ie from 21.04 to 21.10, or when available, from 22.10 to 22.04.  For this reason I don't think you can now upgrade from 20.04 to either of the currently supported intermediate versions.

I have always clean installed, never upgraded, so I am probably not the right person to give advice on upgrading, apart from repeating that it makes most sense for most people to use the LTS versions only.

---

### Post by rsteinmetz70112 on 2021-11-03
Wait for the next LTS then upgrade to that. Your life will be simpler. Only use the regular releases if you need them for something special, like new hardware.

---

### Post by ActionParsnip on 2021-11-03
I like the LTS releases due to stability. If you want the newest and shiniest toys then go for the in between releases

---

### Post by Impavidus on 2021-11-04
I used to be on the LTS releases (6.06–12.04), but from 13.10 on I switched to the interim releases. The reason is that the software on the LTS releases gets quite old after 12–18 months. There are bugs that don't get fixed in the versions in the repos, although they have been fixed upstream, and add-ons/macro-packages etc. available from the web no longer work on the version in the Ubuntu repos. I encountered this problem with Flightgear, TeX, heard others complain about Gimp. So if you find the software on the LTS release outdated and a better version is available on de interim release, don't hesitate to switch. If you keep your system clean and you've got easy hardware, upgrades are quite reliable. I've never had any problems, but keep backups and prepare for fresh install anyway. Upgrades from an LTS release to the next supported release are available (currently 20.04 to 21.04), although less rigorously tested than upgrades to the immediate successor or LTS to LTS.

---

### Post by monkeybrain20122 on 2021-11-04
Just stick with the LTS if it is working and when you want to upgrade to the next LTS, do a clean install instead of "upgrade", it is much faster and problem free. I can't see any pro of upgrading your OS every 9 months.  Interim releases used to be supported for 1.5 years so in those days it made more sense to go for an interim releases. 

Now there are more ways to mitigate old software problem. There are now many ways to install up to date versions on Ubuntu: ppas' snap and flatpak, for examples (you can always install from source too though that is not beginner friendly) e.g Gimp, VLC and Flightgear all have up to date versions in Flatpak (probably snaps too but I have removed snapd so don't know)

---

### Post by mIk3_08 on 2021-11-04
> **foggybrain said:**
> Currently installed Xubuntu 20.04....(I've moved from Mint where i had no choice!). But unsure which is best - 

1) Stick to LTS path or move to regular releases - what are advantages / disadvantages?
2) If I move to regular release path when can I do it now or wait till after 22.04?
In my opinion, If your current Linux Ubuntu Operating System is working smoothly then just stay but If you really want a new and shiny then choose carefully. Be careful of what you choose. As what "ActionParsnip" says
> **ActionParsnip said:**
> I like the LTS releases due to stability.  If you want the newest and shiniest toys then go for the in between  releases
So Good Luck and Regards.

---

### Post by foggybrain on 2021-11-04
Thanks for advice folks......I'll stick with LTS its working well.  A clean install sounds good  when next LTS arrives, but it does mean I have to reinstall printer drivers and reinstall other software etc and tweak settings so might try
1) Back up user files 2) in place update if all ok - fine else 3) Clean install

---

### Post by mrdc76 on 2021-11-04
I hope the OP realizes that the stability of LTS releases does not mean that the interim releases crash more often, because they don't. LTS releases are stable by definition: their stability means that they don't change and thereby introduce new bugs. However, as time passes by, more and more (old) bugs are discovered and remain unfixed.

---

### Post by Tadaen_Sylvermane on 2021-11-04
For me LTS means the few ppa's that I use always work. They don't all get interim releases done. Is something to consider as well.

---

