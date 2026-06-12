---
title: "Unable to open ns / nam after moving the installation folder (back and forth)"
date: 2015-03-25
forum: New to Ubuntu
---

### Post by Nachiketkumar on 2015-03-25
Hello,
I installed ns2 (Network Simulator) and nam(network animator) in ubuntu (wubi) 14.04LTS
at /home/nachiket/Documents/ns-allinone-2.35   
nachiket is my username
Due to space crunch I moved the installation folder to other drive and expanded (Resized the wubi disk from 10Gb to 15Gb)
and then I copied the ns-allinone-2.35 back to its original position.

But now


> 
nachiket@ubuntu:~$ ns
bash: /home/nachiket/Documents/ns-allinone-2.35/bin/ns: Permission denied

 
However I can manually open the folder

I tried 

sudo chmod 777 /home/nachiket/Documents/ns-allinone-2.35/

and 

sudo chown nachiket:nachiket /home/nachiket/Documents/ns-allinone-2.35/

but both did not work,what should I do ?

---

### Post by Holger_Gehrke on 2015-03-25
Is there a good reason you installed it from source (and into such an unusual location) ? ns2 and nam are in the repositories. A short search in synaptic or an 'apt-cache policy ns2' could have shown you this. If I were you, I'd back up my data and get rid of the self compiled ... thing ... and install the one in the repositories ('sudo apt-get install ns2 nam').
Oh, and 'wubi' ? That's decidedly a bad idea with anything newer than Windows XP ...

---

### Post by Vladlenin5000 on 2015-03-25
> **Holger_Gehrke said:**
> Oh, and 'wubi' ? That's decidedly a bad idea with anything newer than Windows XP ...

+1

---

### Post by Impavidus on 2015-03-25
Make that +2, and +1 to installing from the repositories if possible. And both Windows XP and any Ubuntu later than 12.04 via wubi usually are bad ideas too. See [http://ubuntuforums.org/showthread.php?t=2229766](http://ubuntuforums.org/showthread.php?t=2229766)

But to come to your problem, copying an executable from a Linux partition (or virtual partition, like wubi is) to a Windows partition and back to Linux may cause it to lose execute permissions, as Windows partitions don't support Linux style permissions. So you have to restore execute permissions to the executable file. You only gave execute permissions to the directory, not the files inside. (The directory needs execute permissions too, but I don't think they were gone in the first place.)

---

