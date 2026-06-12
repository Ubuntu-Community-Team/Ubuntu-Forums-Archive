---
title: "Is there a firewall with Ubuntu 11.10?"
date: 2012-01-08
forum: New to Ubuntu
---

### Post by Zoot 10+six on 2012-01-08
Hi Everyone this is my first post, I installed Ubuntu 11.10 on my laptop a few days ago.

My question is: when you install Ubuntu from a CD is there a firewall added with the installation? A student on the Open University website forum said that 'A firewall is not added to the installation with Ubuntu'. But I read in a book that it is, can anyone put me right on this?

Also if there is indeed a firewall included could you tell me how to find it in the GUI? To check that it is turned on.

I did download the Firestarter firewall but I could not find out how to switch it on, then I found out it had disabled my wireless broadband connection. So I re-inserted the Ubuntu mirror image CD and did a clean installation over the first one and got my broadband connection back.

I have got a Virgin broadband connection if that helps.

                      Thanks, Paul.

---

### Post by Derek Karpinski on 2012-01-08
There is a firewall installed by default, but it's not on.  'ufw' is a command line only firewall.

If you want to install the GUI frontend for it, install 'gufw' from the software center or in terminal:

```
sudo apt-get update

sudo apt-get install gufw
```

Here is the documentation for it:

[https://help.ubuntu.com/community/Gufw](https://help.ubuntu.com/community/Gufw)

---

### Post by jjex22 on 2012-01-08
Hello, welcome to the forums... the answer is yes and no!

A simple firewall is installed, but disabled, it's enabled and configured through a command called ufw, to enable and learn more, have a look [here.]("https://help.ubuntu.com/8.04/serverguide/C/firewall.html") (to get into the terminal press ctrl+alt+T)

If you'd like a list of common tcp ports to enable or close, have a look [here]("http://www.chebucto.ns.ca/~rakerman/port-table.html")

And for general advice on how to harden your Linux system this is a good one [here]("http://www.ibm.com/developerworks/linux/tutorials/l-harden-desktop/")

for more information on anti virus, have a look [here]("https://help.ubuntu.com/community/Antivirus") (from this list, to the best of my knowledge bit defender isn't free? but gets good reviews, I've read a lot of conflicting reviews about avg - from good to often targeted?

If you are dual booting with windows, it's best to also scan your linux partitions so that it doesn't become a "carrier" for infections - after all if you downloaded something in linx it may not run but you may accidentally move it into a Windows partition and then it's allready past your firewall and on your machine.

In general when it comes to malware, I don't wish to depress you as a new user, but you're not technically safer yet on linux - its just there just isn't anything "in the wild" at the moment to worry about - it's still important to stay safe online even with Linux :)

---

### Post by oldos2er on 2012-01-12
> **Zoot 10+six said:**
> My question is: when you install Ubuntu from a CD is there a firewall added with the installation? A student on the Open University website forum said that 'A firewall is not added to the installation with Ubuntu'. But I read in a book that it is, can anyone put me right on this?

See [http://ubuntuforums.org/showthread.php?t=510812](http://ubuntuforums.org/showthread.php?t=510812) and [http://ubuntuforums.org/showthread.php?t=1871177](http://ubuntuforums.org/showthread.php?t=1871177)

---

