---
title: "error no such partition. gub rescue&gt;"
date: 2013-02-26
forum: New to Ubuntu
---

### Post by busarap on 2013-02-26
Before this happened, I have both window7 and Ubuntu 12.04 on my notebook. I have some problem about Ubuntu update. So I choose to move to Ubuntu 12.10. Then I install Ubuntu 12.10. But I forget to install alongside window. So my window recovery partition was gone. I'm usuing Toshiba protege R835-p56x that have window license on it and I need that recovery partition back. So I tried "testdisk" to restore that partition. I did a deep search then I load "HDDRECOVERY" partition that I think it is what i need back. After I finish it and restart. Then my computer cannot boot. It shows "error no such partition. Grub rescue>". Please help me to solve it. I want the recovery partition back. I want to install window 7 and then Ubuntu alongside it. 

Please help me :(

---

### Post by carl4926 on 2013-02-27
[https://help.ubuntu.com/community/Boot-Repair](https://help.ubuntu.com/community/Boot-Repair)

---

### Post by busarap on 2013-02-27
Thank you very much. I will try that.
I have a question, will I get my window recovery back ?

---

### Post by carl4926 on 2013-02-27
> **busarap said:**
> Thank you very much. I will try that.
I have a question, will I get my window recovery back ?

The above will help get your machine booting both OS's. Assuming they are both intact.

You might also want to look at this info
[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

---

### Post by busarap on 2013-02-27
Now it shows "missing operating system. Insert system disk in drive" on boot Manu :(

---

### Post by carl4926 on 2013-02-27
Boot the ubuntu live cd
Open Gparted
Take a screenshot of what you see
Post it here

also of
```
sudo fdisk -l
```

---

### Post by busarap on 2013-02-27
This is what I saw on the screen after using boot-repair and restart

[IMG]https://fbcdn-sphotos-e-a.akamaihd.net/hphotos-ak-prn1/72377_10151465099224630_2103949968_n.jpg[/IMG]

Here the file that came out,
[http://paste.ubuntu.com/5569822/](http://paste.ubuntu.com/5569822/)

---

### Post by busarap on 2013-02-27
Here it is.

[IMG]https://fbcdn-sphotos-h-a.akamaihd.net/hphotos-ak-ash3/69652_10151465111564630_1029151726_n.jpg[/IMG]

Thank you for your help :)

---

### Post by carl4926 on 2013-02-27
Just re-install ubuntu and let it use the whole drive

Option : Erase everything and re-install

---

### Post by busarap on 2013-02-27
So that the window7 recovery partition will be lost, right? 
I also want to keep it because it have the window license :(

---

### Post by carl4926 on 2013-02-27
> **busarap said:**
> So that the window7 recovery partition will be lost, right? 
I also want to keep it because it have the window license :(

The windows licence should be on the machine in the for of a Label.
That is all you need + a windows DVD
Those recovery partitions are next to useless, especially in the situation you are in.

---

