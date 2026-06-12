---
title: "Elusive file connections"
date: 2011-10-05
forum: New to Ubuntu
---

### Post by BEEDO on 2011-10-05
OK, I'm an Absolute Beginner with 11.04 Desktop w/LAMP in VirtualBox on XP. I want to share files between XP and Ubuntu, but somehow it eludes me. I've played with this for days. I think there must be something simple right under my nose. I think there must be a half dozen different ways... still...](*,)    HELP!

---

### Post by hyper2hottie on 2011-10-05
If your ubuntu is installed in a virtual box in win xp then I don't think you will be able to share files.  I could be wrong(if I am I hope someone corrects me) but my understanding of a virtual box is that it emulates hardware.  Ubuntu does not even know that win xp exists. 

If you need to share files then you will probably need to install ubuntu on a separate partition or through wubi.

---

### Post by BEEDO on 2011-10-05
Fortunately, I am sure you are mistaken about sharing files. VB emulates hardware so Ubuntu being software, is a legitimate OS. For instance: I can write files in Terminal and keep them in /var/www and access them via Apache (port 80) via a browser on the host XP and the other Windows PC on my home network. (This is very cool, though I am not sure what I did to achieve it, since I have tried many things to achieve file sharing and only noticed the server was working after many changes).

Still, most of my file generating pastiche comes from programs running on Windows so naturally I want to share that with the Ubuntu OS. I could use a FTP program, but if I am truly to embrace Ubuntu beyond being a Server, I need to be able to work on files in either OS.

I have Samba installed and think it looks promising, but I haven't grasped it well enough, despite tutorials aplenty. My lack is probably so fundamental as to be taken as a given!   :-k

---

### Post by 4llf0rn0t on 2011-10-05
Am I getting it right? You want to share your Windows files to your Ubuntu VM?
I assume you already enabled Files/Folders sharing under your WinXP. 
From your Ubuntu VM, how do you access the shares?
You could use Nautilus. Press Ctrl+L and from the Location bar type:```
smb://ipaddressofWinXP/shares
```

Regarding your Ubuntu VM, what did you use for network adapter? NAT or bridged? As long as either one was used, your webserver under ubuntu will be seen by other computers (including your host Windows XP) in your network.

---

### Post by hyper2hottie on 2011-10-05
Ok I think I misunderstood.  You will definitely be able to share files between the ubuntu and win xp across a network. 

What I am saying is that the ubuntu will not be able to copy files directly into the win xp machine and vice versa(with no network).  Of course, I could still be wrong.

As for copying across the network, you could try using nautilus.  When you open nautilus Click File->Connect to Server.  If you have windows set up with a server then you should be able to access your entire windows file system from ubuntu.

---

### Post by wildmanne39 on 2011-10-05
Hi, the best place to learn about virtualbox is here.
[https://www.virtualbox.org/](https://www.virtualbox.org/)

Also you will need bidirectional checked, plus you must set up the folder you are going to share, then everything in that folder will be accessible.

Make sure you installed guest additions and extension packs.
Thank you

---

