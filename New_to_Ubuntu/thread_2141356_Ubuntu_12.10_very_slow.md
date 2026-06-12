---
title: "Ubuntu 12.10 very slow"
date: 2013-05-02
forum: New to Ubuntu
---

### Post by wim12 on 2013-05-02
Hi Ubuntu forum for beginners,

I installed ubuntu 12.10 on my pc as a dual bootable  with windows XP. I startet with installing windows XP and with that errasing all the old data that lied on the harddisk. Afterwards I downloaded Ubuntu from the internet, and everyting went smooth
Now windows XP works quite fast, but ubuntu is very slow.
What could be the problem?

My pc: desktop, fujitsu-siemens, 7 years old, intell pentium 4 cpu, 2,6 ghz, 1,5 gb ram, radeon 9200 sec

---

### Post by Elect GMax on 2013-05-02
Ubuntu has the same bloat problem as Windows Vista/7/8. A lot of this is allegedly the interface. Try using Lubuntu instead. If that's still too resource-hungry, you might need to switch to a different flavor of Linux altogether, like Fedora.

---

### Post by wim12 on 2013-05-02
Hi Elect GMax,
Do you know a smart way of installing Lubuntu without having to format the whole harddisk again?
What could be the disadvantages of Fedora compared to Lubuntu?

---

### Post by AndyOpie150 on 2013-05-02
I have a ten year old SONY VAIO with Windows XP. 120GB hard drive. 1GB RAM.
I tried at least 2 dozen Distros. Xubuntu is working the best for my computer. Dual booted it with Windows XP. Shrunk the XP partition to just 25GB (that's with giving it 10GB over what was actually used on the partition). Gave the rest to Xubuntu.

I totally didn't even try it until the last. Would have saved me a lot of hassle. I really like the layout of the desktop. It has an auto-hide app bar at the bottom that is really handy as well.
Wouldn't trade it for nothing.

EDIT: Ninja'd by the OP.

All you need to do is use the advanced section in the installer. Install in the same partition as the Ubuntu install. Format to ext.4 which will delete the Ubuntu distro. You will need to have it boot to /

---

### Post by wim12 on 2013-05-02
Where can I find the installer?

---

### Post by sandyd on 2013-05-02
If you already have ubuntu installed
```

sudo apt-get install lubuntu-desktop
```
should get lubuntu installed :)

You can select Lubuntu at the login screen.

---

### Post by wim12 on 2013-05-03
Thank you very much, [Elect GM]("http://ubuntuforums.org/member.php?u=1761265") , [sandyd]("http://ubuntuforums.org/member.php?u=717412"), and Andieopie !    
Lubuntu was installed overnight, and this morning the sun is shining and Lubuntu rules :p
Problem solved.
[COLOR=#000000][/COLOR]

---

### Post by 3rdalbum on 2013-05-03
That's a rather extreme solution! He didn't need to change his whole desktop environment, all he needed to do was set the dconf key to disable transparency in Unity and the performance would have improved quite a bit. Oh well, at least he is happy, but now he thinks Ubuntu is bloated and slow whereas it's just that his graphics card has only rudimentary drivers.

---

### Post by wim12 on 2013-05-03
Ubuntu is not deleted. I had to choose between several linux versions when I started my pc.
What are the disadvantages of Lubuntu compared to Ubuntu?

---

### Post by snowpine on 2013-05-03
> **wim12 said:**
> Ubuntu is not deleted. I had to choose between several linux versions when I started my pc.


Nothing wrong with that, but if you **choose** to delete Ubuntu and only have Lubuntu, read here: [http://www.psychocats.net/ubuntu/purelubuntu](http://www.psychocats.net/ubuntu/purelubuntu)

> **wim12 said:**
> 
What are the disadvantages of Lubuntu compared to Ubuntu?

None.

---

