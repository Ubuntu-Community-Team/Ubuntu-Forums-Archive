---
title: "Boot up windows threw VM?"
date: 2012-07-23
forum: New to Ubuntu
---

### Post by cosmoshell on 2012-07-23
I know its possible with VMware, want to boot windows directly from hardive within ubuntu using something free. Any suggestions?

---

### Post by Bucky Ball on 2012-07-23
Yea, install Virtualbox, (or VM but I don't know anything about that), launch it, and install your flavour of Windows. Bout that simple.

Be reminded: You need to share the RAM with both OSs. If you have 4Gb, 2Gb each, or 1Gb for one and 3Gb the other, or whatever. You allocate this at install.

In other words; if you have 512kbs of RAM don't bother (and if you have 1Gb I wouldn't bother either; 512kbs each?) ... 

Good luck. ;)

---

### Post by stmiller on 2012-07-23
Yes VirtualBox can do raw disk access, but this is pretty risky or experimental....

---

### Post by Old_Grey_Wolf on 2012-07-23
> **cosmoshell said:**
> I know its possible with VMware, want to boot windows directly from hardive within ubuntu using something free. Any suggestions?

You can install Microsoft Windows in a VM with open source VirtualBox, Xen, QEMU, or KVM.

---

### Post by Big Dan on 2012-07-23
I don't think it would be possible as the windows install on your hard drive is loaded with drivers and such for your computer and not Virtual Box.

---

### Post by Old_Grey_Wolf on 2012-07-23
@cosmoshell,

Are you wanting to boot an existing Microsoft Windows installed on a partition as a VM in a hypervisor?

:confused:

---

### Post by cosmoshell on 2012-07-23
> **Old_Gray_Wolf said:**
> @cosmoshell,

Are you wanting to boot an existing Microsoft Windows installed on a partition as a VM in a hypervisor?

:confused:

&#9653;I want to boot an existing Microsoft Windows installed on a partition as a VM. I Just dont know how. 
                                                                                                       &#9653;&#9653;

---

### Post by Bucky Ball on 2012-07-23
> **Big Dan said:**
> I don't think it would be possible as the windows install on your hard drive is loaded with drivers and such for your computer and not Virtual Box.

To clarify: A virtual install is just that. You don't actually have 'a windows install on the hard drive', even though all the files are there. You install Ubuntu, then Virtualbox (or whatever you're using), then launch VB and install Windows inside the already running Ubuntu install. It runs virtually. 

To install Windows you are not actually booting from the Windows hard drive and putting it on a separate partition. It is on the same partition as Ubuntu and needs to share the RAM with it. You also have a full range of Linux flavours in VB which it can install as guests inside the Ubuntu host.

As far as I understand it, the drivers of the host operating system run the show and support the guest (in this case, Windows). Someone correct me if I'm wrong ... ;)

---

### Post by cosmoshell on 2012-07-23
> **stmiller said:**
> Yes VirtualBox can do raw disk access, but this is pretty risky or experimental....

how do i do this?

---

### Post by cosmoshell on 2012-07-23
> **Bucky Ball said:**
> To clarify: A virtual install is just that. You don't actually have 'a windows install on the hard drive', even though all the files are there. You install Ubuntu, then Virtualbox (or whatever you're using), then launch VB and install Windows inside the already running Ubuntu install. It runs virtually. 

To install Windows you are not actually booting from the Windows hard drive and putting it on a separate partition. It is on the same partition as Ubuntu and needs to share the RAM with it. You also have a full range of Linux flavours in VB which it can install as guests inside the Ubuntu host.

As far as I understand it, the drivers of the host operating system run the show and support the guest (in this case, Windows). Someone correct me if I'm wrong ... ;)
 Acutually you can do this with some soft, actually off the partition. I cant get the vmware to run and existing windows off its partition anymore and would prefer to use free vs VMware. Ive done this before years ago just doesent work with VMware any more for me, and I just thought there would be a free alternative by now. It wasent a file it was a live off other partition run.

---

### Post by yuvraj23 on 2012-07-23
Also what can you do is that you can make an vdi image of existing system partion i.e c:/ and use it in virtualbox. This way you will retain all your previous windows settings

---

### Post by wildmanne39 on 2012-07-23
Hi, here is a link on migrating an existing operating system to virtualbox.
[https://www.virtualbox.org/wiki/User_HOWTOS](https://www.virtualbox.org/wiki/User_HOWTOS)

I do not recommend this it will not run quite as well in virtualbox as it does by itself, when I had windows installed I dual booted then put windows inside virtualbox so I would not need to boot windows very often.

Also here is a link to the forums CoC.
[http://ubuntuforums.org/index.php?page=policy](http://ubuntuforums.org/index.php?page=policy)
> Trolling, Attacks and Flaming: These are always forbidden.

    Trolling is posting in a way that provokes emotional responses.
    Attacks and derogatory terms of any kind are not welcome. This includes references to other operating systems and the companies that produce them.
    Flames are messages that personally attack or call any people names or otherwise harass. These, along with any generally condescending posts will be edited or removed at the moderators discretion.
    If a thread is flame-bait (appears to be intended to start an argument or is likely to cause an argument rather than enhance discussion, as in trolling), it will be locked or removed without notice. Individual flame-bait comments in a post may be deleted or edited at the moderators' discretion.
    If the thread turns into an argument, it can be closed to further comment or removed without notice. Sometimes a moderator may split the thread or delete certain portions in order to keep the discussion going, but that is not always possible since we are a staff of volunteers with limited time and numbers.
Notice that bad comments or in your case changing the name of microsoft is not allowed, please read the CoC.

I will edit your post.
Thanks

---

