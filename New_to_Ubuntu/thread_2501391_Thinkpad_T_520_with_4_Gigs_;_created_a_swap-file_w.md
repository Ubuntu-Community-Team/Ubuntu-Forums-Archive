---
title: "Thinkpad T 520 with 4 Gigs ; created a swap-file: what do you say to this performance"
date: 2024-10-05
forum: New to Ubuntu
---

### Post by alsacien on 2024-10-05
dear community 

i  run a thinkpad with a linux 

the notebook has got 4 g of ram 

i have created a SWAP file: see below what i have done:; 



```
[martin@martin-4243f53 ~]$ sudo swapon --show
[sudo] Passwort für martin: 
NAME      TYPE SIZE USED PRIO
/swapfile file 1,9G   0B   -2

```


**question**;  How to adjust the swappiness value: do i need to use the swappiness-option: 

**note**: Swappiness is a Linux kernel property - a option that may help here: swapiness  defines how often the system will use the swap space. 
well do you think that i need Swappiness to improve the behavior: 

swapiness - friends told me that it can have a value between 0 and 100.  A low value will make the kernel to try to avoid swapping whenever possible,
 while a higher value will make the kernel to use the swap space more aggressively.
The default swappiness value is told to be somewhat like 60. Friends told me that i  can check the current swappiness value by typing the following command:


```

[martin@martin-4243f53 ~]$ cat /proc/sys/vm/swappiness
60

Für weitere Einzelheiten siehe free(1).
[martin@martin-4243f53 ~]$ sudo free -h
[sudo] Passwort für martin: 
              gesamt       benutzt     frei      gemns.  Puffer/Cache verfügbar
Speicher:      3,7Gi       2,3Gi       560Mi       316Mi       1,4Gi       1,4Gi
Swap:          1,9Gi          0B       1,9Gi
[martin@martin-4243f53 ~]$ 



```

well over all - what do  you say - what can i do to get a good performance!?

any and all idas are wellcome

look forward !

---

### Post by Holger_Gehrke on 2024-10-06
Swapping always impacts performance negatively because no matter how fast a drive is it is slower than RAM by orders of magnitude. 4 GB of RAM are enough for a lot of things, with the important exception of web browsers which have developed over the last two decades into RAM-devouring monstrosities. I know from experience that running Firefox on a system with 4 GB is horribly slow and - if you open too many tabs or pages which use especially memory hungry features - potentially unstable. Your best option is to get more RAM. A quick search tells me that the T520 can take up to 16 GB of RAM.

Holger

---

### Post by oldfred on 2024-10-06
Besides more RAM, faster drive also helps. And a lighter weight flavor.

I have used my external SSD with Kubuntu on my 2006 laptop with only 1.5GGB. With full install to old slow internal HDD, it would go gray for 2 sec while it swapped to HDD if I loaded too many programs at once. With SSD, it was very quick, but I still only tried to load a minimal set of applications at once.
Laptop would not even install Ubuntu. It installed server & I was able to add a lightweight gui. I was a bit surprised that Kbuntu installed and worked reasonably well. But SSD made it even better. Kubuntu is more of a mid-weight flavor.

[https://ubuntu.com/download/flavours](https://ubuntu.com/download/flavours)
Light weight flavors:
Lubuntu, Xubuntu, Ubuntu MATE, Budgie
Flavors of Ubuntu only come with three years of supported life (five years applies to Ubuntu Desktop, Ubuntu Server but not flavors)

---

### Post by jimmyrus on 2024-10-06
> **alsacien said:**
> dear community 

i  run a thinkpad with a linux 

the notebook has got 4 g of ram 

i have created a SWAP file: see below what i have done:; 



```
[martin@martin-4243f53 ~]$ sudo swapon --show
[sudo] Passwort für martin: 
NAME      TYPE SIZE USED PRIO
/swapfile file 1,9G   0B   -2

```


**question**;  How to adjust the swappiness value: do i need to use the swappiness-option: 

**note**: Swappiness is a Linux kernel property - a option that may help here: swapiness  defines how often the system will use the swap space. 
well do you think that i need Swappiness to improve the behavior: 

swapiness - friends told me that it can have a value between 0 and 100.  A low value will make the kernel to try to avoid swapping whenever possible,
 while a higher value will make the kernel to use the swap space more aggressively.
The default swappiness value is told to be somewhat like 60. Friends told me that i  can check the current swappiness value by typing the following command:


```

[martin@martin-4243f53 ~]$ cat /proc/sys/vm/swappiness
60

Für weitere Einzelheiten siehe free(1).
[martin@martin-4243f53 ~]$ sudo free -h
[sudo] Passwort für martin: 
              gesamt       benutzt     frei      gemns.  Puffer/Cache verfügbar
Speicher:      3,7Gi       2,3Gi       560Mi       316Mi       1,4Gi       1,4Gi
Swap:          1,9Gi          0B       1,9Gi
[martin@martin-4243f53 ~]$ 



```

well over all - what do  you say - what can i do to get a good performance!?

any and all idas are wellcome

look forward !
How come you can't ask your 'friends' who told you about this for information? And haven't you asked about swap many many many times over the 10+yrs you've been using linux?
[https://forums.opensuse.org/t/setting-up-optimizing-the-partition-table-on-a-notebook-that-will-run-opensuse-leap-42-1/118206](https://forums.opensuse.org/t/setting-up-optimizing-the-partition-table-on-a-notebook-that-will-run-opensuse-leap-42-1/118206)

---

