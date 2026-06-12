---
title: "Ubuntu Software Center Malfunction"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by kman0420 on 2013-06-22
Hi guys!   ):P (first post)

I have a problem with the Ubuntu Software Center. I don't know if this is the appropriate spot to post a question about that, but seeing as how I'm an absolute beginner, I thought I'd give it a try.

I downloaded Ubuntu a few days ago and I've been having trouble with the Software Center since the first day. It opened fine when I was testing it out on the live CD (although it was a bit slow) but when I fully installed Ubuntu I couldn't get it open again.

Generally, this wouldn't be a problem for me. I know the software center is loaded with awesome stuff to download, but I could do without it. But I'm trying to download the codeblocks compiler so I can learn programming, and I think I can only install it with the Software Center.

Help!

I searched online and saw that a few other people were having similar problems (but not identical). One answer said that I should update the Software Center with the updater, but I have done all of the updates (excluding a few python updates that I won't work for some reason).

I'm a real newb, guys, so if you could give me your professional advice (and maybe hold my hand until mi problema is resolved) that would be swell. Or if you know a compiler I can download that doesn't require the Software Center or knowledge of compiling, that works too.

 Thanks guys! :D

P.S. I'm running Ubuntu 12.04

---

### Post by Dennis N on 2013-06-22
> **kman0420 said:**
> Hi guys!   ):P (first post)

 But I'm trying to download the codeblocks compiler so I can learn programming, and I think I can only install it with the Software Center.



You have other options for installing software packages. Here are two:

1) Use the terminal:

**sudo apt-get install codeblocks**

2) Install and use the Synaptic Package Manager which has a GUI and powerful features.

**sudo apt-get install synaptic**

Then search for and install your package with it.

---

### Post by kman0420 on 2013-06-22
> **Dennis N said:**
> You have other options for installing software packages. Here are two:

1) Use the terminal:

**sudo apt-get install codeblocks**

2) Install and use the Synaptic Package Manager which has a GUI and powerful features.

**sudo apt-get install synaptic**

Then search for and install your package with it.

Thank you so much, Dennis!

I now have Codeblocks installed and I'm in the process of trying to figure out how to use it. (A long process, I would imagine, but I've got nothing if not time. :) )

I used the first command you posted and it took less than five minutes for it to install completely. Thanks again!

Is there any reason I should keep trying to fix the Software Manager right now, or can I keep installing any applications I need by using terminal commands?

---

### Post by fantab on 2013-06-22
As suggested, Install 'Synaptic Package Manager, as a more powerful alternative to 'Software Center'.

sudo apt-get install synaptic

Command Line will always be there. But to install packages from CLI we must know the exact package name. So GUI package manager always comes in handy.

---

