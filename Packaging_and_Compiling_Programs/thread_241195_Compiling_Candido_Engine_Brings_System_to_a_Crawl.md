---
title: "Compiling Candido Engine Brings System to a Crawl"
date: 2006-08-22
forum: Packaging and Compiling Programs
---

### Post by igutekunst on 2006-08-22
Before I say anything else, I am quite new to Linux, and Ubuntu. I appologise if my problem is obvious. Thanks in advanced.
I tried to compile Candido ([Website]("http://candido.berlios.de/")) by following the instructions.
```
./autogen.sh  
make   
make install
```
After typing make, it began compiling (as far is I know).

```
make[1]: Entering directory '/home/isaac/Candido-Engine'
cd. && make am refresh
```
After a while, as the numbers incremented, the my computer slowed to a crawl.
At this point, the terminal output read as follows:
```
[2246.889861] Out of Memory: Killed process 13677 (make).
[####.######] Out of Memory: Killed process ##### (make).
```

It proceeded to do this until gdm restarted.

If it helps here are my specs. 
Ubuntu Dapper Drake (6.06 LTS)
AMB 64X2 4200
NVIDIA 7800 gt
1GB Corsair PC3200 ram
300 GB HD.

---

