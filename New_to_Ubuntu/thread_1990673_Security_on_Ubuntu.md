---
title: "Security on Ubuntu"
date: 2012-05-29
forum: New to Ubuntu
---

### Post by TheMTtakeover on 2012-05-29
What are some security programs I should get set up? I have done a good bit of reading and understand that there aren't wild Linux viruses running around and that programs from the software center are safe, but what firewall and making sure that there aren't ports open on my computer than someone could gain access to? I saw something called app armor is that any good? What kind of set-ups do you guys have?

---

### Post by sffvba[e0rt on 2012-05-29
For a little bit more reassurance I open up a terminal and enable Uncomplicated Firewall:
**sudo ufw enable**

Then I use common sense when using the Net.


404

---

### Post by gnusci on 2012-05-29
I use to install Firestarter and gufw. I find both good. They are very easy to set up.

---

### Post by TheMTtakeover on 2012-05-29
Thanks I do have ufw enabled. I do have common sense so I should be fine there. Any other tips?

---

### Post by DingusFett on 2012-05-29
I tend to just use GUFW. I'm usually careful on what I visit/download so haven't felt the need for a virus scanner for years, even on Windows.

---

### Post by Cheesemill on 2012-05-29
> **gnusci said:**
> I use to install Firestarter and gufw. I find both good. They are very easy to set up.
Bad idea. You shouldn't install both because they end up conflicting with each other as they are both front ends for iptables, which is the firewall built into the kernel.

Also firestarter hasn't been developed for many years now so shouldn't really be used at all.

---

### Post by mutap on 2012-05-29
> **TheMTtakeover said:**
> Thanks I do have ufw enabled. I do have common sense so I should be fine there. Any other tips?

Install antivirus for Linux, just in case if you are downloading or copying files in Linux and later you move them to Windows(they can't harm your Linux OS but they could harm Windows).
Also, check out sticky threads on this forum about security issues ;) 
[http://ubuntuforums.org/forumdisplay.php?f=338](http://ubuntuforums.org/forumdisplay.php?f=338)

---

### Post by kevdog on 2012-05-29
A firewall IMO is really only useful if you are running listening services on the machine.  In this case you really need to harden your model and try to limit access to as few people as possible. One model is using a firewall, other methods such as access control lists, user jails, specific server setup options are others.  If you are really paranoid there is a tutorial on SE Linux.

---

