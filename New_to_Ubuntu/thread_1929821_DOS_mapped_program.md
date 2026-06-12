---
title: "DOS mapped program"
date: 2012-02-22
forum: New to Ubuntu
---

### Post by jjerry76 on 2012-02-22
Hi
 
Can ubuntu run an old DOS mapped program? i.e. a fox DB program. I want to know because I liked Ubuntu so much that I want to apply it on my workplace, thanks for readding and more thanks if you answer/help me, good day!:KS

---

### Post by lisati on 2012-02-22
Among your options is [DosBOX]("https://help.ubuntu.com/community/DOSBox")

---

### Post by jjerry76 on 2012-02-22
> **lisati said:**
> Among your options is [DosBOX]("https://help.ubuntu.com/community/DOSBox")
 
Hi Lisati, thanks for answering ...
 
I've downloaded DOSbox but i can't get it to work and I know it has to be with the mapping, my Fox DB program has to be mapped in G:/ ...

---

### Post by jjerry76 on 2012-02-22
> **jjerry76 said:**
> Hi Lisati, thanks for answering ...
 
I've downloaded DOSbox but i can't get it to work and I know it has to be with the mapping, my Fox DB program has to be mapped in G:/ ...
 
 
Ok, will look into that DosBOX link you posted, didn't saw that lol :oops:

---

### Post by jjerry76 on 2012-02-22
Will it change everything if my DOS Fox DB program is a network share? .... mean the mounting and all ...

---

### Post by jjerry76 on 2012-02-24
So far and no good, can anyone help me?
 
I've downloaded DOSBox so I can run my DOS DB there and SMBFS so I can map a network drive from the network which has the old DOS DB in it ..... I can map that drive with the letter needed (G: I've mounted C: on DOSBox .... but still can't get to run (tipical "MASTER does not exist" error) .... anyone?

---

### Post by iponeverything on 2012-02-24
patience and google are your friends. 

What you are trying to do has been done many times before.

---

### Post by jjerry76 on 2012-02-24
> **iponeverything said:**
> patience and google are your friends. 
 
What you are trying to do has been done many times before.
 
 
Did not find any info on that, but you're right found the info needed here & google as well, this is what I did (dunno if it's necessary but hope helps someone and if you see something wrong, please, do tell)
 
1.- Downloaded DosBox
 
sudo apptitude install dosbox
 
2.- Made C: which I believe is necessary on any Windows program
 
On terminal:
mkdir ~/dos
mkdir ~/dos/c
 
On DosBox
mount c /home/*userhome*/dos/c
 
3.- Installed SMBFS for "mapping"
 
sudo aptitude install smbfs
 
Updates as well: 
sudo update-rc.d -f umountnfs.sh remove
sudo update-rc.d umountnfs.sh stop 15 0 6 4
Edit with NANO /etc/fstab, added the next line:

//servername/sharename /media/mountname smbfs guest,uid=1000,iocharset=utf8,codepage=unicode,unicode 0 0

Mount the map letter:
 
sudo mkdir /media/mountname
sudo mount -a
 
4.- Mount it on DosBox that drive letter which is diferent from C:
 
What do you think?

---

### Post by forrestcupp on 2012-02-24
If it works, thank you for posting your findings.

---

