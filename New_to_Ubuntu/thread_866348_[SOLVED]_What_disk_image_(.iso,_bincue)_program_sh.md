---
title: "[SOLVED] What disk image (.iso, bin/cue) program should I use?"
date: 2008-07-21
forum: New to Ubuntu
---

### Post by DOS4dinner on 2008-07-21
I need something that can make a bin/cue of a CD for one of my DOS games. Actually, a complete CD burning program would be good too. Any recommendations? 

(sorry if this is the wrong spot to post this)

---

### Post by Joeb454 on 2008-07-21
Perhaps these will help: ```
:~$ apt-cache search bin/cue
cdrdao - records CDs in Disk-At-Once (DAO) mode
libcdio-dev - library to read and control CD-ROM (development files)
libcdio7 - library to read and control CD-ROM
bchunk - CD image format conversion from bin/cue to iso/cdr
mybashburn - Burn data and create songs with interactive dialog box

```

---

### Post by DOS4dinner on 2008-07-21
> **Joeb454 said:**
> Perhaps these will help: ```
:~$ apt-cache search bin/cue
cdrdao - records CDs in Disk-At-Once (DAO) mode
libcdio-dev - library to read and control CD-ROM (development files)
libcdio7 - library to read and control CD-ROM
bchunk - CD image format conversion from bin/cue to iso/cdr
mybashburn - Burn data and create songs with interactive dialog box

```

Ummm...this may sound dumb....Are those terminal commands or programs? If they are commands, how do I use them?
Nevermind, they are programs. However, I don't think that is quite what I need. I need something more like Roxio or Nero.

---

### Post by cariboo on 2008-07-21
I don't know of any gui burning programs that can create bin/cue files, but any burning program can burn then. K3b is my favourite, but gnomebaker and brassero will do what you need. Brassero is installed by default and k3b and gnomebaker can be installed using Add/Remove Programs or Synaptic Package Manager.

Jim

---

### Post by DOS4dinner on 2008-07-21
> **cariboo907 said:**
> I don't know of any gui burning programs that can create bin/cue files, but any burning program can burn then. K3b is my favourite, but gnomebaker and brassero will do what you need. Brassero is installed by default and k3b and gnomebaker can be installed using Add/Remove Programs or Synaptic Package Manager.

Jim

This is the problem: I need the bin/cue itself, as the CD (Rayman to be exact) is a mixed mode music/game CD that an .iso can't handle.

I guess I can just boot up Windows and use roxio, but that is a pain.

---

### Post by jbrown96 on 2008-07-21
Check out this guide. It looks a little dated, but it will still work. As far as a replacement to Nero. I really like K3B, which is a KDE app. If you use Gnome, you might want to try Brasero (installed by default in 8.04). Brasero has a few less options, but both are great.

---

### Post by DOS4dinner on 2008-07-21
> **jbrown96 said:**
> Check out this guide. It looks a little dated, but it will still work. As far as a replacement to Nero. I really like K3B, which is a KDE app. If you use Gnome, you might want to try Brasero (installed by default in 8.04). Brasero has a few less options, but both are great.

Tried brasero. Unless I am missing something, it cannot make bin/cue or .iso. It can only make a .toc or a .raw from what I can tell (I am using 8.04)
Oh, and where is this guide?

---

### Post by Joeb454 on 2008-07-21
You *can* get nero for Linux, but you need to pay. For now it might be worth just booting Windows (it depends how urgently you need the disc)

---

### Post by DOS4dinner on 2008-07-21
> **Joeb454 said:**
> You *can* get nero for Linux, but you need to pay. For now it might be worth just booting Windows (it depends how urgently you need the disc)

They make nero for Linux? cool. Anywho, I will just boot up Windows. Thanks! I will put solved a little later in case someone knows of a program that can.

---

### Post by cariboo on 2008-07-21
It turns out that k3b can make mixed mode CD's. I'd never needed to do it, so I never looked for that function. I am burning a mixed mode cd as I type.

Jim.

---

### Post by tm0054 on 2008-07-24
For the record Brasero can make cue/bin files. I made one last night.

---

