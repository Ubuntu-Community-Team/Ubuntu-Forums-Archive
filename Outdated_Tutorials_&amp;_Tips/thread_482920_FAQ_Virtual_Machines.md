---
title: "FAQ: Virtual Machines"
date: 2007-06-24
forum: Outdated Tutorials &amp; Tips
---

### Post by maddot on 2007-06-24
Here is a small faq, after asking various questions in the newbie area i can conclude, so in case you are a new Virtual Machine user looking into installing one, you'll probably not find a guide in this post. This post will address some concerns i think many people who are interested in getting into virtual machines have.

**What is a virtual machine?** 
Virtual machines are OSes that operate of your host system. 

**Why do i need a virtual machine?**
For countless reasons to list. Games in Windows, softwares not supported in linux yet... For more productive environments, development testing, networking, website design and stuff. etc.etc.

**How many Virtual systems software are available?**
Currently there is only 3 i know off.

Xen - Free & Paid 
VMware - Paid & Free Available
Virtual Box - Currently Free & open source

**What are the differences?**
Xen - Supposed to be the best which has top performance. I can't confirm that as i have yet to use it. Apparently it uses technology that streamlines dual core system users.

VMware - A more advanced program however, it requires a more powerful system to get it to run nicely. Minimum i would say, is 512 ram. However less would prolly work, but not optimum. Wouldn't say it's very user friendly.

VirtualBox - To me is the best. So far i have it installed on my ubuntu system, which has about 512 ram and my windows laptop, with only 265 ram and it works like a charm. It is so far to me the easiest to use(Wizards FTW).

**Can I use this to boot off an already existing partition?**
Yes and no. If your intention is to boot off a windows partition, then you will run into some problems. One of erm is that you will need to reactivate it everytime you intend to use it. It is the cause of windows XP's hardware protection thingy. A walk around is to use a corporate edition of XP, but that is your choice.

Yes, if you intend to boot off linux, but however be forewarned that if you are booting off the current host system partition, then your in a world of trouble. Seriously. (Besides WTF would you want to do that?)

**Since Linux/Ubuntu is virus-proof do i still need to install security/anti-virus/spyware on it?**
Yes, Yes and Yes. Windows is windows, linux is linux. It can still catch a virus if you're not careful. However, chances are lesser if you intend for it to never leave the confines of your PC. If it does, install some basic forms of protection.

**What about defragging?**
Like windows, windows will die if it isn't defragged. So i suggest you do so, depending on how often you use the virtual machine.

**A virtual machine is slower than my real machine! How do i make it go faster?**
Delete your system and install that OS! lmao. That's the only way, either that, or get a crap load of more ram. Oh yeah, but if you seriously want to try, you can set the limit of the amount of ram used, play around till you break it and get the best amount.

**Which Virtual Machine software is best?**
IF you ask anyone or everyone, they will tell you according to personal preference. It has ben discussed countless times. So, i suggest you search for these argument posts or, research and try yourself.

**Where can i find them?**
[http://vmware.com/](http://vmware.com/)
[http://www.xensource.com](http://www.xensource.com)
[http://www.virtualbox.org/](http://www.virtualbox.org/)

**How do i install them?**
Look around the forums, it isn't hard to find a guide....though..finding a guide for VMware is a bit difficult :P..or xen. I don't think xen works in ubuntu yet.

**I disagree with your FAQS!**
Well..too bad :P take it up with me in my pms.

**I have questions reguarding installing the VMs**
Post it in one of the forums... lmao.

---

### Post by Computer-Geek on 2007-06-27
Thanks Dude!!

---

### Post by smartboyathome on 2007-07-09
You forgot QEMU. It is (to me) the most flexible VM software out there.

---

### Post by MozartlovesUbun2 on 2007-09-16
===============================================================
quote:
Why do i need a virtual machine?
For countless reasons to list. Games in Windows, softwares not supported in linux yet... For more productive environments, development testing, networking, website design and stuff. etc.etc.
===============================================================

You talk about playing games inside the (windowsXP) virtual machine, I'm not so sure that would work coz the guest OS doesn't have direct access to the graphic card, right? (only emulated, right?)

It's only the host OS (which in our case is Linux) that has access to the graphic card.

So question, what kind of games are you talking about and have you tested it out yourself?

Can someone please answer this, thx.

I'm talking about heavy duty 3D games

===============================================================
I started a New Thread:
Virtual Machiens & Gaming (does it really work?) 

[http://ubuntuforums.org/showthread.php?p=3372869#post3372869](http://ubuntuforums.org/showthread.php?p=3372869#post3372869)

---

### Post by stephanecharette on 2007-09-16
> **maddot said:**
> 
[http://vmware.com/](http://vmware.com/)
[http://www.xensource.com](http://www.xensource.com)
[http://www.virtualbox.org/](http://www.virtualbox.org/)


If that isn't enough, take a look at:
[http://en.wikipedia.org/wiki/Comparison_of_virtual_machines](http://en.wikipedia.org/wiki/Comparison_of_virtual_machines)

Would be nice to know what virtualization software product is recommended and/or supported specifically when using Ubuntu as the host OS.  I took a quick look in Synaptic, but didn't see anything stand out.

I've been using VMWare until now, but I'd like to move to something "free".

--------------

Update, one year later:  I've been using 64-bit VirtualBox for the past year on Ubuntu 7.04, 7.10, and 8.04-64bit, and it works like a charm!  If anyone is looking for a solution that works well on Ubuntu, look no further.  Go to [http://virtualbox.org/](http://virtualbox.org/) to download the 32-bit or 64-bit Ubuntu package, as the one in Synaptic is somewhat out-of-date.

Stéphane

---

