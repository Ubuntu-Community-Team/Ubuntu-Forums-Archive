---
title: "Keeping linux tiptop"
date: 2008-05-18
forum: New to Ubuntu
---

### Post by philipluna66 on 2008-05-18
I am experimenting with ubuntu 8.04 on a very old machine I have 8gig hard drive, Pentium 111 Mem 375mb and 384 swap.I am VERY impressed with the speed and ubuntu in general. When I put win xp on this machine it would barely operate. I am so impressed i am going to upgrade this computer What I am asking is coming from a windows background i feel like I am neglecting my ubuntu not defraging cleaning etc. Is there anything I should be doing and can I improve the performance in any way till I get my upgrade. Once again THANKYOU Linux for a GREAT product

---

### Post by HotShotDJ on 2008-05-18
> **philipluna66 said:**
> i feel like I am neglecting my ubuntu not defraging cleaning etcNo defraging necessary.  From a terminal, you might want to run the following commands occasionally:```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```But don't get too obsessive about those... just once in awhile is enough. :)

---

### Post by bryncoles on 2008-05-18
dont worry about defragging - the default file-type (Ext3) effectively defrags itself on the fly, from what i understand, so it wont suffer from windows-esque fragmentation issues. if you keep some NTFS or Fat32 systems around, you'll need to keep windows too to defrag those though, as im not aware of any linux defrag tools (as linux systems such as ubuntu) arent prone to fragmentation. 

and as for viruses etc - the usual rule apply. dont download suspicious files from dodgey sources, and you should be ok. for some reason, malware seems not to affect linux-based systems. i think (disclaimer) its due to the different architecture of linux. and the fact that its designed to be a multi-user envionment, so you actually have to go out of your way to find viruses. 

ask about installing antivirus software though, and watch the sparks fly! it seems to be an emotive subject!

you might want a firewall (they're good practice, i still think). Firestarter is what id use - its a way of editing your 'IP tables', which are basically the rules your computer uses to moderate traffic to and fro form the internet. 

note: you dont need firestarter to run all the time. once youve set a  rule with it, that rule will be in effect whether you boot firestarter or not.

---

### Post by bryncoles on 2008-05-18
> **HotShotDJ said:**
> No defraging necessary.  From a terminal, you might want to run the following commands occasionally:```
sudo apt-get autoremove
sudo apt-get clean
sudo apt-get autoclean
```But don't get too obsessive about those... just once in awhile is enough. :)

+1! am i right in my understanding, that these commands clean up left overs from programs that you install and uninstall? its basically like tidying up after yourself, rather than leaving a trail of debris in your wake!

---

### Post by HotShotDJ on 2008-05-18
> **bryncoles said:**
> +1! am i right in my understanding, that these commands clean up left overs from programs that you install and uninstall?Sort of.  autoremove gets rid of dependencies that are no longer needed after the removal of a package.  clean and autoclean clean up the package cache (I'm not fully clear how the two are different, other than they are different)

I should have also mentioned that when you remove packages, you can use the --purge option on the command line (ie sudo apt-get autoremove packagename --purge) which will get rid of configuration files as well as the software itself.  The same thing can be accomplished in Synaptic Package Manager by choosing "Complete Removal" rather than just "Removal"

---

### Post by bryncoles on 2008-05-18
nice! thankyou! also, i just spotted this link 

[http://ubuntuforums.org/showthread.php?t=140920](http://ubuntuforums.org/showthread.php?t=140920)

in this thread about cleaning your system

[http://ubuntuforums.org/showthread.php?t=798137](http://ubuntuforums.org/showthread.php?t=798137). 

its like a hugely elaborated version of your post!

---

### Post by mapes12 on 2008-05-18
Hi

This is also a good resource for making sure you keep your Linux box secure:

[http://www.psychocats.net/ubuntu/security](http://www.psychocats.net/ubuntu/security)

Best wishes.

Mark

---

