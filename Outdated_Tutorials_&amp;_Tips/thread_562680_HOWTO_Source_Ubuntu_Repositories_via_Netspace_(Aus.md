---
title: "HOWTO: Source Ubuntu Repositories via Netspace (Australia)"
date: 2007-09-29
forum: Outdated Tutorials &amp; Tips
---

### Post by lonoy on 2007-09-29
Sourcing Ubuntu Repositories via Netspace (Australia)

Regarding using Netspace's mirror for software, there are a few ways to set it up. You can do it with Synaptic (System > Admin > Synaptic Package Manager > Settings > Repositories) or another GUI, but it's easiest for me to explain and quicker for you to do most of it via the terminal. When in the terminal, you can just copy and paste my uncommented commands.

Applications > Accessories > Terminal.

Backup your current software sources

```
sudo cp /etc/apt/sources.list /etc/apt/sources/list.original
```

Use the text editor to make changes, gksudo is like sudo but for opening GUI apps:

```
gksudo gedit /etc/apt/sources.list
```

Search > Replace

[http://au.archive.ubuntu.com/ubuntu/](http://au.archive.ubuntu.com/ubuntu/) 

with...(ensure to add a space after last / or it will not work)

[ftp://ftp.netspace.net.au/pub/ubuntu/](ftp://ftp.netspace.net.au/pub/ubuntu/)

So if you're using Ubuntu 7.04, your lines would look something like:

deb [ftp://ftp.netspace.net.au/pub/ubuntu/](ftp://ftp.netspace.net.au/pub/ubuntu/) feisty main restricted universe multiverse

Then save and close Gedit. 

Now any software you install or any updates you do won't count towards your monthly download quota.

If you ever need to change back to the original sources keep up a backup of the sources.list with Netspace's mirror.

```
sudo cp /etc/apt/sources.list /etc/apt/sources.list.netspace
```

Overwrite sources.list with the original:

```
sudo cp /etc/apt/sources.list.original /etc/apt/sources.list
```

Cheers
Lonoy

---

### Post by real.aussie on 2008-08-02
Hi,
This works just fine... 

But, I've found that Netspace usually throttle their 'free' ftp download stuff to approx 45 kB/s (i.e., the 'free' stuff that is not added to your download traffic).

If:
(1) you are a Netspace user
(2) you don't mind it running a little slowly, and
(3) you want it 'free'
then this is OK for you.

Regards,
Alf Lacis
GDipApSci
[http://alfredo4570.customer.netspace.net.au](http://alfredo4570.customer.netspace.net.au)

---

### Post by mrgnash on 2008-09-25
Thanks for this -- I'm always going over my cap, so anything I can do to reduce my bandwidth usage is great :D

---

