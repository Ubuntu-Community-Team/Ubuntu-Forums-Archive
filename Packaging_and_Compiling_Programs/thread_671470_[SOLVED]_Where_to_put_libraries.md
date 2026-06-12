---
title: "[SOLVED] Where to put libraries?"
date: 2008-01-18
forum: Packaging and Compiling Programs
---

### Post by dmitrijledkov on 2008-01-18
I'm trying to compile libjingle.
```

checking speex.h usability... no
checking speex.h presence... no
checking for speex.h... no
checking speex/speex.h usability... yes
checking speex/speex.h presence... yes
checking for speex/speex.h... yes
checking for speex_encode_int in -lspeex... yes
checking iLBC_decode.h usability... no
checking iLBC_decode.h presence... no
checking for iLBC_decode.h... no
configure: WARNING: Could not find ilbc headers or libs. Please install ilbc package from http://www.linphone.org if you want iLBC codec support in libjingle.

```

But I did put them in include folder
```
dmitrij@xubuntu:~$ locate iLCB
dmitrij@xubuntu:~$ cd /usr/include/iLBC/
dmitrij@xubuntu:/usr/include/iLBC$ ls
anaFilter.c  filter.c         hpInput.c       iLBC_define.h  packing.c
anaFilter.h  filter.h         hpInput.h       iLBC_encode.c  packing.h
constants.c  FrameClassify.c  hpOutput.c      iLBC_encode.h  StateConstructW.c
constants.h  FrameClassify.h  hpOutput.h      iLBC_test.c    StateConstructW.h
createCB.c   gainquant.c      iCBConstruct.c  LPCdecode.c    StateSearchW.c
createCB.h   gainquant.h      iCBConstruct.h  LPCdecode.h    StateSearchW.h
doCPLC.c     getCBvec.c       iCBSearch.c     LPCencode.c    syntFilter.c
doCPLC.h     getCBvec.h       iCBSearch.h     LPCencode.h    syntFilter.h
enhancer.c   helpfun.c        iLBC_decode.c   lsf.c
enhancer.h   helpfun.h        iLBC_decode.h   lsf.h
dmitrij@xubuntu:/usr/include/iLBC$ 

```

But strange enough can't locate them.

I'm begginer at programming and linux. Please help.

---

### Post by dmitrijledkov on 2008-01-18
I did manage to get one yes! Folders are case sensetive i have rename include/iLBC into include/ilbc and i got this:
```
checking for iLBC_decode.h... yes
checking for iLBC_decode in -lilbc... no

```

Now gonna work on the second one.

---

### Post by Borbus on 2008-01-18
Why are you trying to compile it? You can get it from the ubuntu repos.

---

### Post by dmitrijledkov on 2008-01-18
Didn't know that =D. Cool

Well compiling because there is 0,4 version available. Repositories only have 0.3.

I did check on iLBC, it wasn't there so I assumed libjingle won't be there.

I still don't understand why does it say iLBC_decode yes iLBC_decode -lilbc no.

---

### Post by dmitrijledkov on 2008-01-19
Well I realised that I accutially in addition to header and source files have to compile and link shared library and put it in libs before hand =D. This is why it wasn't working =D. Solved.

---

