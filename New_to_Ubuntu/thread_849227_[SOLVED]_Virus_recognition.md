---
title: "[SOLVED] Virus recognition"
date: 2008-07-04
forum: New to Ubuntu
---

### Post by mailtwogopal on 2008-07-04
Hi all,

    Whenever i am using my any of the removable drive (like USB, CD, DVD etc) which may contain virus unknowingly to me, Will my Ubuntu hardy heron able to recognize the virus or trojan program present in the removable drive and alert me regarding. 

    Or is there any possibility that when i was using windows with antivirus s/w installed, i select my removable drive - then right click it and can "scan" for viruses option. Will there any such options to recognize virus program if present in removable drives. I know virus written for windows programs cant infect linux file structure; but i want to ensure whether my removable drive is infected or not. Thanks in advance. Expecting reply from you guys.

---

### Post by qrwe on 2008-07-04
There is a free antivirus program available: ClamAV. Search for it in the installation manager.

---

### Post by Canis familiaris on 2008-07-04
Well I think ClamAV would do this job.

You could install it via Add/Remove.

I dunno how exactly. Never used it. But I have know it can detect Windows viruses.

EDIT: qrwe beat me! LOL!

---

### Post by mailtwogopal on 2008-07-04
hi all,

  Ok i install that and thanks.

---

### Post by Tomatz on 2008-07-04
You will probably want to install **avscan**. It's a gui for clamav.

P.s windows viruses wont run in linux

---

### Post by HermanAB on 2008-07-04
Hmm, makes me wonder what you do with your memory sticks...

The probability of ever encountering a virus is extremely remote and it won't affect Linux, so I certainly don't bother with any virus checks on my Linux machines.  The sole exception is my mail server, where I scan mail and remove viruses and spam for the benefit of the (mostly Windows) users.

---

### Post by Canis familiaris on 2008-07-04
> **HermanAB said:**
> Hmm, makes me wonder what you do with your memory sticks...

The probability of ever encountering a virus is extremely remote and it won't affect Linux, so I certainly don't bother with any virus checks on my Linux machines.  The sole exception is my mail server, where I scan mail and remove viruses and spam for the benefit of the (mostly Windows) users.
I suppose he intends to share them with his friends who use Windows. I think he is kind enough to not become a carrier of viruses to his friends PCs. I mean if he did not delete those viruses (either manually or through ClamAV) his friends PCs could get infected.

---

### Post by sydbat on 2008-07-04
AKA - Responsible computing.

---

### Post by mailtwogopal on 2008-07-04
Hi anurag,

  Exactly u r right. i used to share (from and to) photos from my teammates whenever we go team outing and as well as company's party, b'day party etc. So i try installing ClamAV to do it. Is alone sufficient?

---

### Post by tjwoosta on 2008-07-04
for me clamav works much faster and without as many errors if i use it without a GUI


the terminal commands for clamav are actually really easy to do


to update virus database
```
sudo freshclam
```

to scan only a single directory
```
sudo clamscan /path/to/directory
```

to scan a directory recursively (all directorys within will be scanned)
```
sudo clamscan -r /path/to/directory
```

to scan a directory and automatically remove viruses (be careful with this)
```
sudo clamscan --remove /path/to/directory
```

to scan a directory and list only infected files
```
sudo clamscan -i /path/to/directory
```

this is my favorite (scans entire filesystem listing only infected files and sounds a terminal bell when a virus is found)

```
sudo clamscan -i --bell /
```

and to find other arguments for clamscan do this
```
man clamscan
```

---

### Post by Canis familiaris on 2008-07-05
> **mailtwogopal said:**
> Hi anurag,

  Exactly u r right. i used to share (from and to) photos from my teammates whenever we go team outing and as well as company's party, b'day party etc. So i try installing ClamAV to do it. Is alone sufficient?

It will be good enough. But to be honest, nothing is SUFFICIENT.
Also always delete those autorun files. I dont think Antiviruses really delete the autorun files.

---

