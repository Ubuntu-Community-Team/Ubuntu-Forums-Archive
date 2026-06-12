---
title: "Gparted installation problems"
date: 2016-02-02
forum: New to Ubuntu
---

### Post by incurablegeek on 2016-02-02
Some of you may recall me as a bit of a dabbler with Linux - no more. Because of my business with partners in India, for whom Windows is a dirty word, I must migrate everything from Win 7 to Kubuntu 14.04. So, for better or worse guys, I am here to stay - the proverbial "pain in the behind".

Ages ago I mentioned that after (in this case) a successful Kubuntu installation, I was unable to see all the hdd's (OS installed on SSD); and Gparted was suggested to me by someone with infinite patience and toleration of newbie questions.

OK, I burned Gparted as an ISO (burning done on Win 7), but when I boot from the ISO I am asked a bunch of seemingly unrelated questions. Qwerty keyboard selection of course was easy, but then it goes on to ask me about video card and screen resolution. After answering all of those (for me) inane questions, I come to THE END - meaning no exit, no save, just ends. When I take the DVD out of the optical drive and boot into Kubuntu, Gparted is Nowhere To Be Seen.

What am I doing wrong - and please feel free to tell me what an idiot I am. :lolflag:

---

### Post by buzzingrobot on 2016-02-02
Gparted is a package that can be installed from the repos, if it is not already installed.

A bootable Live CD is also available under the Gparted name.  It is live version of Debian Linux that includes Gparted and a range of other disk and rescue tools.  From your description, I suspect you tried to use this Live CD. It needed answers to the questions it asked to set up the live session correctly. Since it's intended as a technician's tool, I'd guess they didn't spend much time making it user friendly (or, perhaps, have room on the image).

Partitions need to be unmounted -- they need to be unattached from the file system -- before you use a partitioner. They won't be mounted when you boot the live image.  

I'd recommend just installing gparted on your system and running it.  Use it to unmount the parttions (most options will be greyed-out until you do), then proceed. Reboot when you're finished so the kernel picks up the changes.

---

### Post by Vladlenin5000 on 2016-02-02
Welcome back :-)

Well... First of all you don't need a different media for GParted. The GParted bootable image you used is intended for using GParted alone but you can also run it from any Ubuntu live session. Kubuntu, the Ubuntu variant with KDE doesn't come with Gparted but with KDE Partition Manager instead.

Now, it begs two questions:
1. Is **K**ubuntu really a requirement? Can't you use standard Ubuntu or any other Ubuntu flavor? 
2. Why do you think you need GParted (or KDE Partition Manager) now? For what purpose exactly? Also please read again (and try to understand this answer to an old thread of yours: [http://ubuntuforums.org/showthread.php?t=2292715&p=13347350#post13347350](http://ubuntuforums.org/showthread.php?t=2292715&p=13347350#post13347350)
It pretty much explains what I did in the first paragraph.

---

### Post by incurablegeek on 2016-02-02
> ***Partitions need to be unmounted*** -- they need to be unattached from the  file system -- before you use a partitioner. They won't be mounted when  you boot the live image.  

I'd recommend ***just installing gparted on your system and running it.***

1) The first bolded I knew from many years (25) with Windows.
2) The second bolded is the real problem. Should I reboot from the ISO, and if so what default selections (which I'm sure can be changed later, e.g. screen resolution, etc.) should I choose?

At present, installing via the ISO does not make Gparted a visible program in Kubuntu 14.04 for me. So I must have made some "improper" choices during setup.

Next silly question: Whenever I attempt to update Kubuntu or any of the included programs, I am being asked for an authentication password. As a rule I never set up a password when I am installing an OS, and sure didn't in this case either. So what is the "secret handshake" desired here.

And thanks so much for your patience.

---

### Post by Vladlenin5000 on 2016-02-02
Again, please re-read and understand the link I posted before which is an answer to the same questions you have now.
[B]The Gparted live CD isn't meant to be installed anywhere; it's meant to be run as a live session only.

[/B]And please consider the questions I asked, especially why do you think you need Gparted anyway? Or KDE Partition Manager for that matter?

---

### Post by incurablegeek on 2016-02-02
> **The Gparted live CD isn't meant to be installed anywhere; it's meant to be run as a live session only.**

My misunderstanding of the Gparted.org site. I see now that it can only be installed on the SSD by using GRUB or LILO - both of which are of course new to me.

> why do you think you need Gparted anyway? Or KDE Partition Manager for that matter?

Now that's an easy one. I develop educational materials for publication and for the different levels there are many iterations of development. I therefore always partition my hdd's - with the occasional need to resize them.

As to why I want gparted on my ssd, well in Windows we have *Computer Management* where I can change MBR to GPT, for example - and so much more. In the past, I asked on this forum why my 2 X 3TB hdd's were not visible and hence not partitionable. I was told I needed Gparted for that.

---

### Post by ajgreeny on 2016-02-02
If you really want to install gparted in your running OS just do it as you would for any other package, ie, use software-center, synaptic, or run command **sudo apt-get install gparted**

Just be aware, however, that when installed in your OS you are very limited in the ways in which you can use it as a result of the need to have partitions unmounted.

As to your post #6, I would still simply recommend that you use one of the most recent *ubuntu live systems and use gparted from that; it will be much easier than using gparted-live.  I do not know the KDE Partition manager so can not comment on that.

---

### Post by Vladlenin5000 on 2016-02-02
> **incurablegeek said:**
> My misunderstanding of the Gparted.org site. I see now that it can only be installed on the SSD by using GRUB or LILO - both of which are of course new to me..

No, nothing to do with it. The live CD is a tool, just a tool intended to be used "as is". How you can install GParted in an already installed OS was explained to you many times before, namely in the previous post.
Additionally, as expected, you don't really need it. If you're running Kubuntu then KDE Partition Manager or Disks (installed by default in any Ubuntu variant, I think) can be used for the exact same purpose. People here often mention GParted because that is what most people use (or are used to).

And regarding...
> Whenever I attempt to update Kubuntu or any of the included programs, I  am being asked for an authentication password. As a rule I never set up a  password when I am installing an OS, and sure didn't in this case  either. So what is the "secret handshake" desired here.

I wasn't aware that Kubuntu would let you install without defining a user's password but if it does you shouldn't do that anyway. Understandably that stems directly from the **old** 'Windows mentality' which results in an additional layer of insecurity. All new Windows now require user accounts pretty much the same way Linux has always been so you better get used to those 'best practices' ASAP. That's the same password you need to do some updates and/or install software.

---

### Post by incurablegeek on 2016-02-02
> I wasn't aware that Kubuntu would let you install without defining a  user's password but if it does you shouldn't do that anyway.  Understandably that stems directly from the **old** 'Windows  mentality' which results in an additional layer of insecurity. All new  Windows now require user accounts pretty much the same way Linux has  always been so you better get used to those 'best practices' ASAP.  That's the same password you need to do some updates and/or install  software.

I see here that lengthy Windows experience is not something to be touted. ;)

> All new  Windows now require user accounts pretty much the same way Linux has  always been so you better get used to those 'best practices' ASAP.  That's the same password you need to do some updates and/or install  software.

When installing Kubuntu, I was ***never*** asked for a password, so as I mentioned before I never set one upon installation because it is just a senseless hurdle that slows down the installation of programs, updates to the OS, etc.

So should I reinstall Kubuntu and hope that this time it asks me for a password?

As for getting used to something ASAP, rest assured I have quite a solid reputation for acclimating to new things quickly. As of now, I am only 2 hours into Kubuntu as opposed to thousands of hours in every iteration of Windows - and before that DOS. Doing my best, that I can assure you.

---

### Post by Vladlenin5000 on 2016-02-02
> **incurablegeek said:**
> When installing Kubuntu, I was ***never*** asked for a password, 

Actually you were, in this exact step, along with the username and computer's name: [https://userbase.kde.org/Kubuntu/Installation#User_Info](https://userbase.kde.org/Kubuntu/Installation#User_Info)
Now, in this same dialog you have the option to select "automatic login". That doesn't mean it has no password, it means it isn't asked when starting the session but will be asked anyway any action requiring elevated privileges.

---

### Post by incurablegeek on 2016-02-02
----------------
Back to the subject at hand. There is nothing in [https://userbase.kde.org/Kubuntu/Installation#User_Info](https://userbase.kde.org/Kubuntu/Installation#User_Info)
that I am not familiar with. 

When it asked for a password, I simply hit "Enter" and then checked the box "log in automatically". Without some "authentication password that I am not privy to, my hands are tied.

---

### Post by Rocky_Bennett on 2016-02-02
> **incurablegeek said:**
> ----------------
Back to the subject at hand. There is nothing in [https://userbase.kde.org/Kubuntu/Installation#User_Info](https://userbase.kde.org/Kubuntu/Installation#User_Info)
that I am not familiar with. 

When it asked for a password, I simply hit "Enter" and then checked the box "log in automatically". Without some "authentication password that I am not privy to, my hands are tied.



Then re-install Kubuntu and this time enter a password. You will not regret it. Try Kubuntu 15.10 for a newer version.

---

### Post by furtom on 2016-02-02
This thread is making my head hurt.

To the OP: Stop a minute. Take a breath. Vladlenin and the others are trying to explain to you that you have a fundamental misunderstanding somewhere, but you're not getting that.

1. You probably already have KDE partition manager installed, therefore you don't really need gparted. The two applications have the same functionality.

2. If you need to change the partition that you have mounted and cannot be unmounted, i.e. "/" (root) or /home or some such, then it doesn't matter which one you have installed, if any. You can't change a mounted partition while running your normal booted system. If you need to partition empty space or reparation other partitions that only contain data, then you can unmount these partitions and use KDE partition manager that you already have.

But I'm assuming, since you are fooling around with bootable media, you need to repartion an otherwise mounted partition as mentioned above. Therefore:

3. In that case, yes, you need bootable media. But you do NOT NEED to install anything from that. You just boot it up and then repartition with gparted (or whatever), while you are running the live session. No need to worry about GRUB (not to mention LiLO, which I doubt you are running anyway).

If you do not understand all I have written above. Stop and ask questions about it. You need to understand these points before you can proceed.

The password thing is a separate issue. We can talk about that in another thread.

I don't mean to be pedantic here, I'm just trying to save you some headache.

---

### Post by incurablegeek on 2016-02-02
> use KDE partition manager that you already have.

This was hugely helpful. What derailed me was a while ago, several members said I needed to use Gparted to do all this. It appears I do not, though I need to see what limitations KDE Partition Mgr. has before I can really say that.

As for > you have a fundamental misunderstanding somewhere, but you're not getting that.

Ah, but yes, I am really, truly getting that.

As for a password, I actually (unconsciously) entered one - a quite inane one just to pacify the installation. For those of you who wish to break into my system it is 1-0. 
My usual passwords normally look something like this:
K?y72aD!s$9L8X}d{f

Thank you, furtom, so very much. As to "making your head hurt", I can personally empathize. Mine does as well; because I have given myself until Friday to understand Kubunu thoroughly. "The difficult I do immediately; the impossible takes a bit longer". Been doing both for a long time and sure as heck do not give up easily.

[CENTER]A Huge Thank You to All!  ):P
[/CENTER]

---

### Post by oldfred on 2016-02-02
I use simple passwords for my home system, but for anything else passwords are more complex.

       Forum rules on root vs. sudo
[http://ubuntuforums.org/showthread.php?t=1486138](http://ubuntuforums.org/showthread.php?t=1486138)
[https://wiki.ubuntu.com/RootSudo](https://wiki.ubuntu.com/RootSudo)
[http://xkcd.com/149/](http://xkcd.com/149/)

But as above I also have had issues with sudo. I still have to make my own sandwiches. :)

---

### Post by furtom on 2016-02-03
> **incurablegeek said:**
> This was hugely helpful. What derailed me was a while ago, several members said I needed to use Gparted to do all this. It appears I do not, though I need to see what limitations KDE Partition Mgr. has before I can really say that.

No "limitations." basically, it's the KDE version of the same software. You will find, running a KDE desktop, that there are many alternate applications as contrasted with "standard" Ubuntu and most varients like Xubuntu, etc. KDE has it's own ecosystem. Most other variants of Ubuntu are in the GTK mold, but KDE uses QT libraries. So it's nice to have native applications. It keeps the user experience more consistent. Actually, I like some of the KDE applications better than their GTK counterparts, but in this case, there is little difference besides the UI.

> Ah, but yes, I am really, truly getting that.

Perhaps. 

So, let's start this over. Please give more information about what you are trying to do.

Start by posting the output of:

```
sudo fdisk -l
```

This will list all your partitions. The please tell me exactly what you want to do with what partition.

Thanks.

---

### Post by incurablegeek on 2016-02-03
Tom, thanks for the helpful push up the learning curve. One thing about me is that I am extremely stubborn. Last night I was up until 4:00 am trying to learn Kubuntu and woke at 7:00 am ready to go again. In short, ignorance frustrates and annoys me.

With KDE Partition Mgr. everything is stupidly simple - as it should be. So I'm OK.

You did mention something very interesting and for me quite timely.
> KDE has it's own ecosystem. Most other variants of Ubuntu are in the GTK  mold, but KDE uses QT libraries. So it's nice to have native  applications. It keeps the user experience more consistent. Actually, I  like some of the KDE applications better than their GTK counterparts

***What do you think of the LibreOffice included in Kubuntu vs the LibreOffice downloaded from*** [https://www.libreoffice.org/](https://www.libreoffice.org/)

My associates are quite adamant that I remove the one in Kubuntu and use the one from the LibreOffice site.

---

### Post by furtom on 2016-02-03
> **incurablegeek said:**
> ***What do you think of the LibreOffice included in Kubuntu vs the LibreOffice downloaded from*** [https://www.libreoffice.org/](https://www.libreoffice.org/)

My associates are quite adamant that I remove the one in Kubuntu and use the one from the LibreOffice site.

This is another misperception. In Linux in general, and certainly Ubuntu in particular, the way to obtain and install software is substantially different than that in Windows. You **do not** go to Websites and download software to install it unless that is the very last option available. This is, generally speaking, a bad way to go about things.

OK, that being said, why exactly do your associates say you need to do anything. LibreOffice is LibreOffice and has nothing to do with the Kubuntu/Ubuntu, KDE/GTK discussion above. The only thing may be that the version you have installed is less up-to-date than the current version. Perhaps your associates are telling you that you need to update your software.

If so, you can start a thread about how to update LibreOffice, but let's not confuse this thread with too many tangents. 

> With KDE Partition Mgr. everything is stupidly simple - as it should be. So I'm OK.

Glad to hear it. I think this thread should probably be marked solved.

---

### Post by incurablegeek on 2016-02-03
> I think this thread should probably be marked solved.

Just did so. Btw, so that you fellows do not feel your contributions are in vain, I make it a habit to copy every post from every thread I start.

Much appreciate all of you.  :popcorn:

---

### Post by vasa1 on 2016-02-03
> **furtom said:**
> ...
If so, you can start a thread about how to update LibreOffice, but let's not confuse this thread with too many tangents. ...
Here: [http://ubuntuforums.org/showthread.php?t=2312205](http://ubuntuforums.org/showthread.php?t=2312205)

---

### Post by furtom on 2016-02-03
> **incurablegeek said:**
> Just did so. Btw, so that you fellows do not feel your contributions are in vain, I make it a habit to copy every post from every thread I start.

Much appreciate all of you.  :popcorn:

I hate to tell you this, but it is not easy to help you or have a conversation with you. I, along with several other people, have asked you several simple, clear and direct questions, but you ignore them and go on to something else instead.

This forum works in two directions. Certainly, you may ask questions, but then, when you are questioned, you have to answer.

There are several unresolved questions in this thread. For example, what partions you needed to change and why? what was the problem with the libreoffice you had installed and what were you trying to accomplish by installing from downloaded deb files?

These are just a few off the top of my head. there are others.

In order to help you, we need more information, especially as you are new. You may be asking the wrong question, but we can't figure out what the right question is until we have more information.

As far as the world of Linux forums goes, this one is extremely liberal and easy going. In other forums, your initial posts, or your first or second follow up posts would be uniformly ignored -- or flamed. Here, we take the time to ask questions so we can help you. Please answer them in the future.

And finally, please stop changing the subject so much. A little back and forth is OK, and sometimes minor problems do arise and get handled as tangents to a thread. But generally speaking, you should keep a single thread on a single subject. You started this thread about gparted, but we've got two major tangents that I can recall off the top of my head: Passwords and now LibreOffice! Both of those were major enough to warrant their own thread.

There is nothing wrong with mentioning things in passing, but you hijacked your own thread twice!

---

