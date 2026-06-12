---
title: "So I just installed ubuntu/lubuntu for the first time"
date: 2013-08-13
forum: New to Ubuntu
---

### Post by yesveryfunny666 on 2013-08-13
As my laptop's windows 7 installation is fairly slow and has been getting a few bugs recently, I decided to try a different operating system. Hardly knew anything about ubuntu when I installed it, apart from that it's linux based so should be faster. On installing ubuntu I was underwhelmed that it seemed even slower than my windows installation, and can't get used to the interface. After reading that lubuntu was less resource intensive I installed the lubuntu environment for ubuntu. It runs faster than ubuntu and about the same as windows 7, maybe slightly faster. However it's full of bugs- I can't install programs, can't watch videos, the administrator password doesn't work even though it's correct, and my keyboard volume control shortcuts don't work. 

Would a clean install of straight lubuntu be less buggy?

Secondly shouldn't lubuntu be a _lot_ faster than windows 7? Lubuntu is meant to run on very old, low spec machines well; my laptop/netbook with an AMD C60 processor and 2GB RAM isn't powerful by today's standards but surely it should run lubuntu really fast?

Thanks for any help! I'm enjoying trying out linux

---

### Post by Gilad_Pellaeon on 2013-08-13
Sound's to me like a fresh install of Lubuntu would be better for your system.

---

### Post by ibjsb4 on 2013-08-13
You can't install programs probably because you haven't updated yet and you can't play videos because you haven't installed the necessary restricted extras.

I agree with a fresh install of lubuntu.  That will remove all unnecessary ubuntu packages.  I believe there is the option to install on top of the excising install.  If not you will have to use windows to delete the ubuntu partition and then install.  If you end up deleting the ubuntu partition, your computer will not boot until you have installed lubuntu.  So now is a good time to ask any other questions you can think of.

---

### Post by vasa1 on 2013-08-13
Just a minor point ... As you are new to Linux, what may seem bugs to you may just be a different way of working which takes a bit of getting used to.

It would help if you post a separate thread on each of your issues so that you get help specific to your situation.

You've written that "I can't install programs, can't watch videos, the administrator password doesn't work even though it's correct, and my keyboard volume control shortcuts don't work. "

We can help you with each of those issues. Rest assured of that :)

---

### Post by Hylas de Niall on 2013-08-14
> **ibjsb4 said:**
> You can't install programs probably because you haven't updated yet and you can't play videos because you haven't installed the necessary restricted extras.

I agree with a fresh install of lubuntu.  That will remove all unnecessary ubuntu packages.  I believe there is the option to install on top of the excising install.  **If not you will have to use windows to delete the ubuntu partition and then install.**  If you end up deleting the ubuntu partition, your computer will not boot until you have installed lubuntu.  So now is a good time to ask any other questions you can think of.


Better surely to use the ubuntu live-cd and Gparted which can actually see the ubuntu partition?
MS Windows can't see linux partitions by default.

HTH

---

### Post by Paqman on 2013-08-14
The main reason people see poor performance from a fresh install of Ubuntu is that they haven't installed their graphics drivers. Before sorting that we need to fix your "can't install programs" issue. Are you connected to the internet?

---

### Post by yesveryfunny666 on 2013-08-14
Thanks for the responses. I'm going to go with a fresh install of lubuntu and then see what problems remain. I'd have thought the best way would be to put the lubuntu install onto a USB and write over the ubuntu partition?

---

### Post by yesveryfunny666 on 2013-08-14
I think graphics drivers have installed, I downloaded and installed a 3D game on ubuntu which runs fine. I'll see if the problem's still there on the new install and get back to you.

---

### Post by vasa1 on 2013-08-14
> **yesveryfunny666 said:**
> Thanks for the responses. I'm going to go with a fresh install of lubuntu and then see what problems remain. I'd have thought the best way would be to put the lubuntu install onto a USB and write over the ubuntu partition?
Yes, you should get that option to replace the existing Ubuntu OS (including or excluding your home folder) quite early on in the installation process. I'd get rid of the existing home folder as well, assuming you have backed up your actual data.

---

### Post by vasa1 on 2013-08-14
> **yesveryfunny666 said:**
> I think graphics drivers have installed, I downloaded and installed a 3D game on ubuntu which runs fine. I'll see if the problem's still there on the new install and get back to you.
But you said you couldn't install programs? ???

---

### Post by yesveryfunny666 on 2013-08-14
I can on ubuntu, just not on the lubuntu environment. Videos and everything else works on ubuntu, it's just too slow

---

### Post by Paqman on 2013-08-15
> **yesveryfunny666 said:**
> I think graphics drivers have installed, I downloaded and installed a 3D game on ubuntu which runs fine.

Ubuntu comes with some basic open source drivers that do give some 3D performance. If you've got an Nvidia or AMD card you'll almost certainly want to install the proprietary drivers for it. Open Software Sources and check the other drivers tab.

---

### Post by newb85 on 2013-08-15
> **vasa1 said:**
> But you said you couldn't install programs? ???

I would imagine not, given that the administrator password isn't working...

When you installed, did you choose to encrypt the partition or the /home directory?  If so, resetting the administrator password will do no good, and your best bet is probably to simply reinstall (which is probably not a bad idea, anyway).

If you didn't, you should be able to reset the administrator password following this tutorial:  [http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

After that, bring your system up-to-date by running the following in a terminal:
```
sudo apt-get update
sudo apt-get upgrade
```
answering yes to prompts.  You will have to be logged in as an administrator to do this, and the password it asks for is the administrator's login password.  You won't receive any feedback as you enter the password.

---

### Post by newb85 on 2013-08-15
> **yesveryfunny666 said:**
> I can on ubuntu, just not on the lubuntu environment. Videos and everything else works on ubuntu, it's just too slow

If you have two desktop environments set up on one system, programs you install should be accessible from both.  When you log into Lubuntu, are you still logging in as an administrator?

---

