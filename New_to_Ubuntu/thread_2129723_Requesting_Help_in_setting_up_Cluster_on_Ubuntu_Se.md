---
title: "Requesting Help in setting up Cluster on Ubuntu Server"
date: 2013-03-27
forum: New to Ubuntu
---

### Post by shridhar.s.i on 2013-03-27
Hello, 
I am a newbie to the world of cluster computing, 
I am a student pursuing my Masters in Engineering and as part of my  project, i have taken up the topic which involves MPICH2 libraries,  capturing the performance of MPI etc 
I have been using Ubuntu for almost 6 years now and have basic knowledge on UNIX as well (from my Job) but i am a rookie yet coz this is an ocean
I want to setup a cluster at home to support my research and the project
Initially i was inclined towards the Pelican HPC but once i found out that our friendly Distro UBUNTU also supports MPICH2 implementation over a server, the choice was obvious - [https://help.ubuntu.com/community/MpichCluster](https://help.ubuntu.com/community/MpichCluster)

But before i do that i have a few queries

1. Hardware: 
Currently i have  
a. 1 Desktop running AMD Phenom Quadcore with 4GB DDR3 RAM, 1 network card and one Wifi Adapter,  
b. 1 Laptop - AMD A6 Quadcore with 4GB DDR3 RAM
c. 1 laptop running on celeron 1.6 Ghz with 1 GB DDR RAM
d. 1 desktop running Pentium 4 HT with 1 GB DDR RAM
e. I am planning to add one more machine (AMD FX 8-Core with 16 GB DDR3 RAM)
f. There will be a dedicated 8 port Gigabit Lan Switch to support the networking requirements of a cluster

Hence, first i want to know whether the cluster will optimally  perform in such a heterogeneous hardware combination
Is there any link to understand load balancing in Ubuntu and how we can configure it

2. Which machine to be taken as Front-Node ?
Once the above hardware issue is sorted out, please advise which  machine (a/b/c/d/e) can be taken as the primary node,

3. Software
I have already downloaded the Ubuntu 12.04 LTS Server as i plan to keep this setup for a while
All the machines except (b) will run  dual boot setup between Ubuntu and Win 7
For machine (b) i have a challenge as it is Windows 8, the HP laptop came preinstalled with Win 7 (July 2012), which I  later upgraded to Win 8 ad if i understand correctly, it does not use UEFI so i believe we are fine for a dual boot setup here as well (though i read may threads here still complaining about dual boot issues with Win 8)
For Machine (e), it will have a UEFI setup and hence installation will be challenging to setup dual boot configuration, links to any threads are most welcome which will help me in this case

As of now i have these queries which will help me decide if i can go ahead with the implementation 

Thanks, 
Shri

---

