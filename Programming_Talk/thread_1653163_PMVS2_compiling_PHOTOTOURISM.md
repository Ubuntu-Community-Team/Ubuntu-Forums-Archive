---
title: "PMVS2 compiling PHOTOTOURISM"
date: 2010-12-26
forum: Programming Talk
---

### Post by mojo_aden on 2010-12-26
Hello all,

I am trying to implement photo-tourism project. As a first step I am trying to compile what is already available online. There are some packages available from Washington University called 
1. bundler([http://phototour.cs.washington.edu/bundler/](http://phototour.cs.washington.edu/bundler/)), 
2. pmvs2([http://grail.cs.washington.edu/software/pmvs/](http://grail.cs.washington.edu/software/pmvs/)) and 
3. cmvs ([http://grail.cs.washington.edu/software/cmvs/](http://grail.cs.washington.edu/software/cmvs/)).

These have to be compiled and implemented sequentially as given above. I am trying to implement them on a Ubuntu based 64-bit machine.

I was successful with bundler but run into a problem with pmvs. The package does not seem to have any binary files which I could execute and the documentation seems to indicate that it does. The CMVS package seems to be the next step in implementing photo-tourism which needs PMVS2 installed. I tried using the CMVS package which according to documentation is supposed to contain pmvs2 package along with some other essentials. This was'nt very successful either. 

Could someone please help me in this regard? I would greatly appreciate any tips as well.

Thanks and Cheers

---

### Post by drstupid_1999 on 2011-10-11
Interested to know how you got bundler to compile, as it errors continually for me, including the SVN version.

---

### Post by bigblob on 2011-10-17
I'm also trying to get Bundler + CMVS + PMVS running.

After some work Bundler and PMVS is compiling fine.

CMVS is also compiling without errors except for linking to the multilevel library, where I'm getting the following message:

```

g++ -L/home/bigblob/DATA/BUILD/lib -lXext -lX11 -ljpeg -lm -lpthread -llapack -fopenmp -lmultilevel -lmetis -lm  -o cmvs cmvs.o patch.o camera.o image.o photo.o photoSetS.o bundle.o graclus.o -L/home/bigblob/DATA/BUILD/lib -lXext -lX11 -ljpeg -lm -lpthread -llapack -fopenmp -lmultilevel -lmetis -lm 
graclus.o: In function `CMVS::Cgraclus::runSub(graphdef&, int, int, int, std::vector<long long, std::allocator<long long> >&)':
graclus.cc:(.text+0x272): undefined reference to `MLKKM_PartGraphKway(int*, long long*, long long*, long long*, long long*, int*, int*, int*, int*, int*, int*, long long*, int)'
graclus.cc:(.text+0x291): undefined reference to `__ComputePartitionBalance(graphdef*, int, long long*, float*)'
graclus.cc:(.text+0x2ad): undefined reference to `ComputeRAsso(graphdef*, long long*, int)'
graclus.cc:(.text+0x2e9): undefined reference to `ComputeNCut(graphdef*, long long*, int)'
collect2: ld returned 1 exit status
make: *** [cmvs] Error 1

```
I don't know, the function can be found in graclus (multilevelLib/mlkkm.c) and graclus is compiling fine. I copied the generated files (libmetis.a,libmultilevel.a) into /home/bigblob/BUILD/lib and there is NO message by the linker that the libs cannot be found.

Maybe there is some type-mismatch in MLKKM_PartGraphKway's argument list, couldn't yet figure out where idxtype and adjwgt, etc is defined.
```

void MLKKM_PartGraphKway(int *nvtxs, idxtype *xadj, idxtype *adjncy, idxtype *vwgt,
                         idxtype *adjwgt, int *wgtflag, int *numflag, int *nparts, int *chainlength,
                         int *options, int *edgecut, idxtype *part, int levels)

```

@drstupid_1999,

maybe I could give you some advices, please post your error messages.

Cheers

---

