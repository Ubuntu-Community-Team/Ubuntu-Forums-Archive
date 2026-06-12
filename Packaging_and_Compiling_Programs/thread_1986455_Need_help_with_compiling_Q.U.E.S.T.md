---
title: "Need help with compiling Q.U.E.S.T"
date: 2012-05-24
forum: Packaging and Compiling Programs
---

### Post by an0001wa on 2012-05-24
I just started doing a simulation project that requires me to use the following package. QUEST DQMC PACKAGE: [http://www.cs.ucdavis.edu/~bai/QUEST_public/](http://www.cs.ucdavis.edu/~bai/QUEST_public/)

I followed the given manual up to the :
cd EXAMPLE
./verify
and it was unresponsive, so I assumed something went wrong on the way. 

So here were the steps I did:
1. attempting to configure /QUEST/make.inc
- FC = gfortran
- FC_FLAGS = -O0 -c   
- HOME = /home/admin/QUEST
- LIBHOME   = /home/admin/LAPACK
- BLASLIB   = /home/admin/LAPACK/librefblas.a
- LAPACKLIB = /home/admin/LAPACK/liblapack.a
- DQMCLIB   = /home/admin/QUEST/libdqmc.a
2. attempting to 'make', which would then produce "libdqmc.a" under QUEST folder:
cd QUEST
make
3. attempting to 'verify'
under QUEST
make example
(now here's where I noticed the problem. there is supposed to have a "verify.out" file under /QUEST/EXAMPLE/verify, but all I got was just "verify")

Then I noticed again, I might be building the wrong libdqmc.a in the first place. 
So I was wondering if someone could help me? By following the manual (not mine) to see if we get the same libdqmc.a, mine has a size of 294532.

Of course I would be really grateful if we can go steps by steps, because I'm really wrecking my brain over the initial steps of this package D:


A linux newbie seeking help.

---

