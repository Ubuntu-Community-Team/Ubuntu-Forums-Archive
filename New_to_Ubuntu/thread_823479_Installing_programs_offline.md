---
title: "Installing programs offline"
date: 2008-06-09
forum: New to Ubuntu
---

### Post by fruitsofherwomb on 2008-06-09
Ok, I wanted to install some programs off a flash drive to my friends Ubuntu installation. 

Myth TV tbh. 

Though I don't know how to do it :/ . He can't get online. Just wondering if you guys knew. Someone said to just drop it in terminal, sounds wrong :mad:

---

### Post by arckeda on 2008-06-09
The easy way would be to download MythTv in a .deb file and then transfer it over to his Desktop to install.  But remember, you need to have all the dependencies for MythTv which may require you to download them off the net if they don't come in the package, I am afraid I do not use MythTv, at least not yet. :)


     -ARCKEDA

---

### Post by inter-m on 2008-06-09
i think u should check out this link... [https://help.ubuntu.com/community/AptGet/Offline/Repository](https://help.ubuntu.com/community/AptGet/Offline/Repository)
i hope it helps...

Khalaf

---

### Post by aeiah on 2008-06-09
all the stuff that you install via apt-get or synaptic gets stored in the apt cache. if you havent cleared it out you should be able to install what you want then copy the apt cache to a cd and use that in his system.

your cache is at /var/cache/apt/archives/ i do believe.

that way you'll have all the dependencies that are needed etc. you'll also have a lot of stuff your friend doesnt need, but if it all fits on a disk there's not really any need to sift through it

---

### Post by fruitsofherwomb on 2008-06-09
I have the mythtv-0.21.tar file. Thats the one on myth's site. I just want to know if there was a way to have that file on the desktop and install it. Like is there a command line for terminal to do it?

---

### Post by Cypher on 2008-06-09
You don't want to use the .tar file, as that would most likely have to be compiled and you might need lots of other dependencies. Ideally you should grab the .DEB file from the Ubuntu repository and any other dependencies from there and use that.

So if you go the Mythtv [repository entry]("http://packages.ubuntu.com/hardy/mythtv"), you will find that there are a few dependencies like mythtv-backend, mythtv-database and so on. So you'd follow all those links and grab the .DEB file for each of those entries..

---

### Post by Hospadar on 2008-06-09
You can install offline with deb files, although you need to make sure you grab all the dependancies.  There is something called aptoncd which basically lets you make a little software repo on a cd, then install stuff through synaptic.  you might want to do some googling and find out about that.

If you want to install mythtv though, I'd highly suggest you install fresh with mythbuntu.  If it's not a dedicated mythtv box, then that might not be a good option, but it's a lot easier to do it that way.

---

### Post by fruitsofherwomb on 2008-06-09
This sound all so confusing, i'll just try to get it online and install :/ 

Ubuntu needs a easier way of installing progs offline tbh. 

Its not a myth box, just going to be a desktop with myth on it :)

---

