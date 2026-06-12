---
title: "Swap help"
date: 2008-06-12
forum: New to Ubuntu
---

### Post by slimboarder003 on 2008-06-12
Hi, I started using Ubuntu Monday and got most everything working but the swap. It sees the swap but wont use any of it. I tried and search for it but can't find anything on it to get it going.

heres what I see always
        total       used       free     shared    buffers     cached
Mem:       2075736     595636    1480100          0      28956     359480
-/+ buffers/cache:     207200    1868536
Swap:      3229024          0    3229024

Thanks if anyone can help.

---

### Post by sdennie on 2008-06-12
With 2G of memory, you will probably never use swap at all unless you are doing things that are very memory intensive.  You could probably open every app on your machine and it wouldn't touch swap.  Welcome to Linux.

---

### Post by slimboarder003 on 2008-06-12
Thanks for the help. I've been enjoying using Linux this whole week so far and no more windows. Say do you need to use a antivirus with Linux?

---

### Post by FAJALOU on 2008-06-12
I personally use 'sudo swapon /dev/hda4'  in my rc.local to turn swap on.  And viruses???

[http://simplyubuntu.wordpress.com/2006/08/16/maintenance/](http://simplyubuntu.wordpress.com/2006/08/16/maintenance/)

That will tell you all you need for the virus problem and a little more.  I use Aegis Virus Scanner, but maybe once o every year.  :grin:  Welcome to Ubuntu.

---

### Post by slimboarder003 on 2008-06-12
Thanks

I had Ubuntu setup that. It give me a Linux, Extended, Linux swap.

I'll put on a antivirus for safety. Thanks again.

---

### Post by Xiong Chiamiov on 2008-06-12
There really is [no need]("http://www.psychocats.net/ubuntu/security#firewallantivirus") for an antivirus.  Essentially, virus scanners for Linux are not looking for Linux viruses; rather, they scan files that you've received for Windows viruses.  This means that you are only going to benefit from an anti-virus if you a) receive a file that is virus-infected and b) pass said file on to someone on an unsecured Windows box.  I hardly receive files, send only files that I create, and make sure that anyone near me has at least a semblance of protection on their machines, so it's a waste of resources for me.

Regarding swap, I have 2 gigs and almost never use my swap space (all the better, since RAM's faster).  If you wish, you can alter the "swapiness", though I am unsure of how to do so.

---

### Post by slimboarder003 on 2008-06-12
Thanks.

What's a good firewall to use?

---

### Post by Xiong Chiamiov on 2008-06-12
There is one built-in to Ubuntu called iptables.  If you're planning on actually doing some sort of configuration with it, Firestarter is popular for GNOME, and Guarddog for KDE.  If you're behind a router, it almost certainly acts as a hardware firewall and blocks incoming nastiness.  Since (as long as you don't go installing crap from random shady-looking places) you probably won't have any sort of trojan horses, eliminating the need for outgoing connection checking.

Essentially, you can eliminate several of the security applications that you have been trained to never go without in Windows.  If you would like to manage a firewall, though, check out those two applications.

---

### Post by slimboarder003 on 2008-06-12
I got firestarter just to be safe because I use facebook. I don't get how to get it to startup with ubuntu.

---

