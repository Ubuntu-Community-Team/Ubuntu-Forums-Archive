---
title: "Software updater warns of need to download from unverified sources"
date: 2016-03-18
forum: New to Ubuntu
---

### Post by AbleTassie on 2016-03-18
I went to update my system using the Software Updater and was warned that the download required downloading from unverified sources. I am using Ubuntu 14.04.4 LTS (Lubuntu). I believe that the unverified sources may be because I installed the JAVA plugin using WebUpd8, but I am not sure. The JAVA plugin was not available through the official Ubuntu Software Center.

Does anybody have any comments about the safety of downloading from unverified sources like this?

Thank you,

A.

---

### Post by v3.xx on 2016-03-18
Probably just need to add the key.

```
sudo apt-get update && sudo apt-get upgrade
```

Please post any errors

---

### Post by DuckHook on 2016-03-18
> **AbleTassie said:**
> ...Does anybody have any comments about the safety of downloading from unverified sources like this?.WebUpd8 is an awesome site. Nonetheless, adding PPAs is a seriously dangerous exercise and should be used sparingly and ultra-cautiously. Having said that, I do use two PPAs: Virtualbox and Wine, so it's not like I avoid them as an article of faith either. But I make sure to fence both in with apparmour profiles&#8213;which are admittedly a real pain in the neck.

Your bigger worry is not the site, which as v3.xx indicates, is probably just a signing key issue, but Java itself. Any time you add a scripting language to your system, you open up a huge attack vector for the scumbags out there. I admit to being more paranoid than most, but the idea of running Java just gives me the willies. However, if you have to install it, Webupd8 is a good site. Just make sure that you get the proper key. Instructions [here]("http://www.webupd8.org/2014/10/how-to-add-launchpad-ppas-in-debian-via.html").

---

### Post by AbleTassie on 2016-03-22
Thanks DuckHook and v3.xx,

I am aware that JAVA is a security risk, but I have to have it for one specific task. No way around that. I have it disabled unless I need it, at which point I enable it. 

I will try adding "sudo apt-get update && sudo apt-get upgrade" but it may take a while as the internet connection to the computer is very erratic--I am presently using a friend's PC to respond on this forum.

Thanks again,

A.

---

### Post by DuckHook on 2016-03-22
> **AbleTassie said:**
> ...I will try adding "sudo apt-get update && sudo apt-get upgrade"...This won't add the key. You need to follow my linked instructions to add the key.

Re: Java

Running java inside a VM will close a lot of the security exposure.

---

### Post by AbleTassie on 2016-03-26
Thanks DuckHook,

I have Windows XP running as a VM in Virtualbox. Do you mean that 1) installing Firefox in this VM and 2) then installing the JAVA plugin in the VM installed Firefox, then 3) accessing the internet through the VM would be more secure? 

A.

---

### Post by DuckHook on 2016-03-26
> **AbleTassie said:**
> Thanks DuckHook,

I have Windows XP running as a VM in Virtualbox. Do you mean that 1) installing Firefox in this VM and 2) then installing the JAVA plugin in the VM installed Firefox, then 3) accessing the internet through the VM would be more secure? 

A.You can do as you describe, or you can run another Lubuntu/Xubuntu in VirtualBox and install Java inside that. Personally, I would avoid doing anything further in XP because it is end-of-life and a huge security hole. I suggest Lubuntu or Xubuntu only because they are lightweight and will run faster in a VM. Since you are already familiar with VMs, you know about their snapshot capabilities and how they are sandboxed from the rest of your system. By rolling back to a known good snapshot, you can get rid of lots of bad stuff that may infect you. Of course, if you are accessing data that resides outside the sandbox, then all bets are off.

---

### Post by AbleTassie on 2016-03-26
Thanks DuckHook, I have not been able to figure out how to access my ports (USB, wireless connections, CD/DVD drives, ethernet) while in the VM. All I can presently do is communicate (transfer files) between the Windows XP VM and Lubuntu via a shared folder. I never access the internet while using Windows XP; too risky as you said and also I just cannot do it.

If I can figure out how to access the internet with a Lubuntu VM, I will do that.

A.

---

### Post by DuckHook on 2016-03-26
You may need to install Extension Pack from VirtualBox site to access USB devices. Network should work right out of the box for both XP and any flavour of 'buntu.

Extension Pack download [here]("http://download.virtualbox.org/virtualbox/5.0.16/Oracle_VM_VirtualBox_Extension_Pack-5.0.16-105871.vbox-extpack"). Instructions [here]("https://www.virtualbox.org/manual/ch01.html#intro-installing").

This thread is starting to morph into a VM thread. But you would be better starting a new thread in the VM forum to help you with that because that's where all the VM gurus are.

The idea is that once you have your devices and network running, you can then confine your Java app inside that VM. Since VMs can take snapshots of their system state, and roll back to that snapshot at any time, you would take a snapshot of your system before Java is installed, perhaps another immediately after Java is installed (but before you install the Java app), and then be able to roll back to those pristine system states if anything should later go wrong. You can take as many snapshots as you want. It only takes up HDD space and adds a little complexity trying to keep track of all your different snapshots.

I highly recommend starting a thread in the VM forum to straighten out the networking issues. I'm not sure it's a good idea to enable networking with XP anymore (I've purposefully disabled mine due to XP security holes after end of life), but lack of a network would be very limiting with any L/Xubuntu VM.

---

### Post by AbleTassie on 2016-03-28
OK thanks DuckHook. I will consult the Virtual forum. 

A.

---

