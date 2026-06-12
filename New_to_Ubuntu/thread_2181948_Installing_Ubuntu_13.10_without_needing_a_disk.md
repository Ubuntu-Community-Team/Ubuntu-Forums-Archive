---
title: "Installing Ubuntu 13.10 without needing a disk?"
date: 2013-10-19
forum: New to Ubuntu
---

### Post by CodemonkeyAlx on 2013-10-19
I am thinking a Wubi like app that would allow the user to upgrade to the latest and greatest with out killing all of their files or am I better off sticking to 13.04 for the time being and upgrading at the next LTS? 
- I'm kind of OCD about keeping up with things except iPhones <.< >.>


I have actually been on the forums once or twice before back when I first started using ubuntu about 3 - 4 years ago now I think. I have returned to it after the idea to start a game company took over my head so here I am rocking ubuntu 13.04 wondering if maybe it would have been better to wait a few days. Right now I am low on DVD's and for some reason my computer (UEFI) is not letting me install from flash drive.

Well here I am for the time being :3 

And remember: no matter where you go - there you are!

---

### Post by Frogs Hair on 2013-10-19
Hello and Welcome

Upgrading via the update manager is possible. 13.04 ends life in January and 14.04 comes out in April , so you have time to let 13.10 become more stable before making a decision . UEFI presents installation challenges and searching the forum would produce helpful results.    

[http://askubuntu.com/questions/203301/how-to-safely-upgrade-from-an-older-ubuntu-version-to-a-newer-one](http://askubuntu.com/questions/203301/how-to-safely-upgrade-from-an-older-ubuntu-version-to-a-newer-one)

---

### Post by grahammechanical on 2013-10-19
When was the last time you ran Update Manager? If you are on 13.04 then you should be able to upgrade to 13.10 with just an internet connection. If Update Manager is set to notify you of the next Ubuntu release, then Update Manager will already be offering a button to run the upgrade. Always back up.

Because you are using 13.04 you cannot directly upgrade to 14.04 (when it is released). You will have to upgrade to 13.10 and then upgrade again to get 14.04. That is the way it works. And remember, Ubuntu 13.04 has about 3 months support left to it.

If you do decide to upgrade and not fresh install, then revert the OS to the default OS as much as possible and switch to the Nouveau open source video driver if you are using a proprietary video driver. And do not leave the upgrade unattended. If you are using software that required acceptance of licence conditions, then you will be asked to confirm. If this does not happen the upgrade will pause. 

I cannot provide any scientific evidence for this advice but there has to be a logical reason why some people have trouble when they upgrade and others do not.

Regards.

---

### Post by kurt18947 on 2013-10-19
> **grahammechanical said:**
> When was the last time you ran Update Manager? If you are on 13.04 then you should be able to upgrade to 13.10 with just an internet connection. If Update Manager is set to notify you of the next Ubuntu release, then Update Manager will already be offering a button to run the upgrade. Always back up.

Because you are using 13.04 you cannot directly upgrade to 14.04 (when it is released). You will have to upgrade to 13.10 and then upgrade again to get 14.04. That is the way it works. And remember, Ubuntu 13.04 has about 3 months support left to it.
[B]
If you do decide to upgrade and not fresh install, then revert the OS to the default OS as much as possible and switch to the Nouveau open source video driver if you are using a proprietary video driver.[/B] And do not leave the upgrade unattended. If you are using software that required acceptance of licence conditions, then you will be asked to confirm. If this does not happen the upgrade will pause. 

I cannot provide any scientific evidence for this advice but there has to be a logical reason why some people have trouble when they upgrade and others do not.

Regards.

In addition to disabling proprietary drivers, it seems a good idea to disable ppa s temporarily as well.  Personally I back up my data and do fresh installs most of the time.  I've done an upgrade or two but it's just too simple with *buntu to do a fresh install and eliminate the chance that some forgotten leftover will cause grief down the road.

---

### Post by CodemonkeyAlx on 2013-10-20
Aye, thanks for the reply guys. I forgot ubuntu had that feature! I am from #! / Win7 Land. They don't have nifty features like that yet.

---

