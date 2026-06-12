---
title: "MPICH - Clustering in wiki"
date: 2007-07-29
forum: Outdated Tutorials &amp; Tips
---

### Post by omid on 2007-07-29
Hi all,
I've prepared a wiki page for setting up a mpich cluster in ubuntu.
Hope it will be usefull.
any comments will be appreciated.
 
[https://wiki.ubuntu.com/MpichCluster]("https://wiki.ubuntu.com/MpichCluster")

---

### Post by christian18 on 2009-11-21
hello omid i've read your article in [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster)
and i've a problem here :
[FONT=tahoma,arial,sans-serif][SIZE=-1][COLOR=#000000]suhendra18@cluster3:~$ mpirun -np 1 cpi
Process 0 on cluster3
pi is approximately 3.1416009869231254, Error is 0.0000083333333323
wall clock time = 0.000080

suhendra18@cluster3:~$ mpirun -np 2 cpi
Process 1 on cluster3
[/COLOR][/SIZE][/FONT][FONT=tahoma,arial,sans-serif][SIZE=-1][COLOR=#000000]Process 0 on cluster3[/COLOR][/SIZE][/FONT]
[FONT=tahoma,arial,sans-serif][SIZE=-1][COLOR=#000000]pi is approximately 3.1416009869231254, Error is 0.0000083333333323
 wall clock time = 0.000080

suhendra18@cluster3:~$ mpirun -np 3 cpi
Process 2 on cluster3
[/COLOR][/SIZE][/FONT][FONT=tahoma,arial,sans-serif][SIZE=-1][COLOR=#000000]Process 1 on cluster3
[/COLOR][/SIZE][/FONT][FONT=tahoma,arial,sans-serif][SIZE=-1][COLOR=#000000]Process 0 on cluster3[/COLOR][/SIZE][/FONT]
[FONT=tahoma,arial,sans-serif][SIZE=-1][COLOR=#000000]pi is approximately 3.1416009869231254, Error is 0.0000083333333323
wall clock time = 0.000080

i've tree node cluster1.cluster2,cluster3..but the cpi only running in cluster3..
 i've configured the rsh..i can connect other node with ssh no pass...[/COLOR][/SIZE][/FONT]
i use mpich-1.2.7p1

---

