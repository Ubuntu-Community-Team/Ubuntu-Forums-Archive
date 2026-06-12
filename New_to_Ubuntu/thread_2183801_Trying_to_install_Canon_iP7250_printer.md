---
title: "Trying to install Canon iP7250 printer"
date: 2013-10-26
forum: New to Ubuntu
---

### Post by chris-burmajster on 2013-10-26
Hello Everybody,

I'm trying to install my Canon iP7250 printer on a fresh install of 13:10 64bit. Last time I installed it successfully via [http://handytutorial.com/install-canon-printer-driver-for-ubuntu-13-04-12-10-12-04]("http://handytutorial.com/install-canon-printer-driver-for-ubuntu-13-04-12-10-12-04/#comment-7478") which entailed adding a repository via the terminal and then updating it. I then opened Synaptic and searched for my printer model and Synaptic then installed everything. 

This time round I added the repositories but the update failed with the following error: 

[I]Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon-stable/ubuntu/dists/saucy/main/binary-amd64/Packages](http://ppa.launchpad.net/michael-gruz/canon-stable/ubuntu/dists/saucy/main/binary-amd64/Packages)  404  Not Found
Failed to fetch [http://ppa.launchpad.net/michael-gruz/canon-stable/ubuntu/dists/saucy/main/binary-i386/Packages](http://ppa.launchpad.net/michael-gruz/canon-stable/ubuntu/dists/saucy/main/binary-i386/Packages)  404  Not Found
Some index files failed to download. They have been ignored, or old ones used instead.[/I]

An internet search failed to find another way of installing this printer so I'm stuck. My laptop also runs 64 bit 13:10 and the printer works, as I installed it months ago. Is there any way I can take something off that to use on this new machine?

Thank you all in advance

Chris

P.S. I have just found and downloaded the official Canon driver from the Canon website and extracted it, but I don't know how to install it.

---

### Post by Isamu715 on 2013-10-26
The repository was probably not updated to support 13.10 yet, if it's an active one it should get updated soon.

---

### Post by chris-burmajster on 2013-10-27
Thanks for your reply. So presumably I just need to wait? It's a shame that there appears to be no other easy way of installing this printer on Ubuntu. I notice that the Handy Tutorial website doesn't appear to have been updated since August.

---

### Post by chris-burmajster on 2013-11-02
A search on Duck Duck Go brought me to [answers.launchpad.net/ubuntu/+source/cups/+question/226171]("https://answers.launchpad.net/ubuntu/+source/cups/+question/226171")  where I managed to add another repository and managed to install the  printer driver that way. Thank you to all of you for your help

---

