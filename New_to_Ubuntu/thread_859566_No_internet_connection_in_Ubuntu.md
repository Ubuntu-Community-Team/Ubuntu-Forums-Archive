---
title: "No internet connection in Ubuntu"
date: 2008-07-14
forum: New to Ubuntu
---

### Post by jcbeta730 on 2008-07-14
Hey, this is my first time using Linux and I need some help connecting to the internet.

I set up my computer to dual boot with windows xp and Ubuntu 8.04.  The install worked fine, but when I try to connect to the internet with firefox the page doesn't come up, I tried using the network manager to connect, but it appears to do nothing. I also installed Ubuntu on another old computer and the internet works, which makes me wonder whether or not this might have to do with dual booting? 

I'm sure this has been asked before but there are so many different topics and guides that I'm not sure which fits my problem, if someone could just link me to the proper thread that would be fine.

To connect I use an ethernet cable with the on-board network ports on my nvidia 680i motherboard and a linksys WRT54G ver. 6 router. Also, the internet works fine in windows. I hope I included enough info in this post. 
Thanks.

---

### Post by Jim! on 2008-07-14
What type of Internet connection is it? e.g. PPPoE, DSL, etc.

---

### Post by jcbeta730 on 2008-07-14
I use broadband.

---

### Post by ImThatNerd on 2008-07-14
In firefox url bar type: about:config

Search for: network.dns.disableIPv6;false

Mine is currently false and my internet works fine, but I remember when I was in LiveCD I think I had to set it to true or false.

---

### Post by jcbeta730 on 2008-07-14
It was already set to false, but it is not only firefox, I can't download updates either.

---

### Post by Jim! on 2008-07-14
If you can't get access to updates either then it means you haven't configured your modem for use with Ubuntu correctly, if your using wireless then you may also need to configure your router.

---

### Post by jcbeta730 on 2008-07-14
But my other computer that is totally linux not dual boot works fine with the same connections.  But, anyway for some reason now when I try to boot Ubuntu it brings me to a DOS-like prompt. It's called like busybox or something and says to type 'help' for command list and something.  So right now I can't even really  try to fix the internet because I can't even get there. :p If anyone has any ideas for that I would appreciate it.

---

### Post by Xerp on 2008-07-14
Can you post the output from

```
ifconfig -a
```

---

### Post by jcbeta730 on 2008-07-14
Xerp is that from the terminal or the busybox shell, because right now that's all I can get to when I try to boot Ubuntu.

---

### Post by Xerp on 2008-07-14
If it used to boot normally and now only boots into busybox, then something has changed. You possibly have a failing hard disk, a wireless keyboard with interference or something similar.

---

### Post by Jim! on 2008-07-14
> **jcbeta730 said:**
> But my other computer that is totally linux not dual boot works fine with the same connections.  But, anyway for some reason now when I try to boot Ubuntu it brings me to a DOS-like prompt. It's called like busybox or something and says to type 'help' for command list and something.  So right now I can't even really  try to fix the internet because I can't even get there. :p If anyone has any ideas for that I would appreciate it.

Not really sure what happened there! Maybe try pressing "Ctrl + Alt F7", It's worth a try.....

---

### Post by jcbeta730 on 2008-07-14
I'm not sure what could have changed, but anyway, I chose the second option on the boot disc, install in windows, how do I go about uninstalling without deleting other data on the drive.  I'm thinking about trying again on another drive.

---

### Post by Jim! on 2008-07-14
OK, Be very careful when uninstalling Ubuntu! Very, very careful. The first time I tried uninstalling Ubuntu I deleted the Windows partition by mistake and ended up being stuck with Ubuntu (Which I'm greatful for:)) I don't know how to go about deleting 'uninstalling' Ubuntu since I'm not dual booting but I recommend you know the name of the Windows partition so that you don't delete it by mistake;)

I think it should be as easy as just deleting the Ubuntu partition but you should search google and the forums for more information or wait for better replies to this thread before you try doing anything.

---

### Post by jcbeta730 on 2008-07-15
That's what has me worried and confused, I don't think a Linux partition was ever made because I installed it through Windows like an application, I looked in partition magic and there doesn't appear to be a partition, there is a 30GB 'ubuntu' file on my harddrive which appears to be where it was installed. In the folder there is an Uninstall exe that doesn't do anything, and when I goto Add/Remove programs and click remove Ubuntu nothing happens either.  I know that this isn't really the right thread to be asking about this stuff since it was originally about internet, but anyways yeah.

---

### Post by Jim! on 2008-07-15
You installed it like an application? Do you mean you used the Wubi installer? That's what it sounds like, if thats the case do a quick search of "Uninstall Wubi" or something similar and if you can't find an answer then post a thread in the Wubi section of this forum;)

---

### Post by jcbeta730 on 2008-07-15
Yeah I was having trouble partitioning the drive with regular install and that said I didn't have to partition it so I decided to use that.

---

