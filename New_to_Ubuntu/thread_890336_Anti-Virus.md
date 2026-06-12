---
title: "Anti-Virus"
date: 2008-08-14
forum: New to Ubuntu
---

### Post by richie42 on 2008-08-14
I dunno, but my computer was acting slow recently and I was wondering if there is any antivirus software/system optimizer tips for Ubuntu

Also, can viruses be sent by looking at pictures on 4chan?

---

### Post by OutOfReach on 2008-08-14
You can install ClamTK (available from the repositories), but it scans for Windows viruses. But I doubt that a Windows virus can infect you since it was made for Windows.

---

### Post by tuxxy on 2008-08-14
Theres also Clam AV, Avast etc I wouldnt worry if you havnt been sharing files regularly with a windows drive

---

### Post by WinterMadness on 2008-08-14
> **tuxxy said:**
> Theres also Clam AV, Avast etc I wouldnt worry if you havnt been sharing files regularly with a windows drive

how would a windows virus effect linux?

---

### Post by Rolcol on 2008-08-14
> **WinterMadness said:**
> how would a windows virus effect linux?

Wine?  Even then, they wouldn't start up with the computer, would they?

---

### Post by tuxxy on 2008-08-14
It wouldnt effect linux, it could effect his other windows drives or friends system if they are regularly accessing or sharing files

---

### Post by LeoSolaris on 2008-08-14
Have you added repositories or .deb's from anywhere other than the official Ubuntu repos? If so, you may have a rootkit. (Rare, but possible. Viruses that actually effect Linux are even rarer.)

Get rkhunter or chkrootkit from the Ubuntu repo and run a scan with one of them. Chkrootkit is slightly easier to use, by the way, but not by much.

Rootkits are fairly rare. The most likely cause for the slowdown was an update that didn't want to play nice with the system. I have had a couple of those.

I certainly hope that your rootkit detection returns a negitive!

(By the way, by "sluggish, do you mean that opening and closing programs seemed to take longer, or thath te internet was loading slower?)

---

### Post by richie42 on 2008-08-15
> **LeoSolaris said:**
> Have you added repositories or .deb's from anywhere other than the official Ubuntu repos? If so, you may have a rootkit. (Rare, but possible. Viruses that actually effect Linux are even rarer.)

Get rkhunter or chkrootkit from the Ubuntu repo and run a scan with one of them. Chkrootkit is slightly easier to use, by the way, but not by much.

Rootkits are fairly rare. The most likely cause for the slowdown was an update that didn't want to play nice with the system. I have had a couple of those.

I certainly hope that your rootkit detection returns a negitive!

(By the way, by "sluggish, do you mean that opening and closing programs seemed to take longer, or thath te internet was loading slower?)

The Internet seems slower. I have no Windows partition. I dunno. It was only a few seconds so I probably was just a little paranoid. LOL

---

### Post by macvr on 2008-08-15
> **LeoSolaris said:**
> 
Get rkhunter or chkrootkit from the Ubuntu repo and run a scan with one of them. Chkrootkit is slightly easier to use, by the way, but not by much.


how do u run this chkrootkit ?

---

