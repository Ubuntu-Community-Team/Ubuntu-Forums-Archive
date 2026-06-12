---
title: "Opening ega/cga graphics file ?"
date: 2010-02-14
forum: Programming Talk
---

### Post by WitchCraft on 2010-02-14
Is there any way to open CGA or EGA graphics files on Linux ?
(I want to extract some images from an old dos program).

---

### Post by iponeverything on 2010-02-14
ega and cga are not file formats, but graphics specifications. 

Whether or not your able to view the files is going to depend on the file format. More than likely you will be view them just fine, as they were probably .gif's . If you have issues post the file extension and the name of program that created them, if you have it.

---

### Post by WitchCraft on 2010-02-14
Unfortunately, I'm not seeing them well.

```

[root@assmunch ~]# cd /root/.dosemu/drive_c/northandsouth
[root@assmunch northandsouth]# ls
BA1CGA.1  CAREGA.2    ECREGA.2  NSPXI.1   SFOCGA.1   TRACGA.1
BA1EGA.2  CHOCGA.1    FORCGA.1  PERCGA.2  SFOEGA.2   TRAEGA.2
BA2CGA.1  CHOEGA.2    FOREGA.2  PEREGA.2  TATCGA.1   VIGCGA.1
BA2EGA.2  CONFIG.TAT  GAGCGA.2  PRECGA.1  TATEGA.2   VIGEGA.2
CARCGA.1  ECRCGA.1    GAGEGA.2  PREEGA.2  TATOU.COM
[root@assmunch northandsouth]# 


```


And the file tool doesn't help much
```

[root@assmunch northandsouth]# file ./*
./BA1CGA.1:   data
./BA1EGA.2:   data
./BA2CGA.1:   data
./BA2EGA.2:   data
./CARCGA.1:   data
./CAREGA.2:   data
./CHOCGA.1:   data
./CHOEGA.2:   data
./CONFIG.TAT: data
./ECRCGA.1:   data
./ECREGA.2:   data
./FORCGA.1:   data
./FOREGA.2:   data
./GAGCGA.2:   data
./GAGEGA.2:   data
./NSPXI.1:    Maple help database
./PERCGA.2:   data
./PEREGA.2:   data
./PRECGA.1:   data
./PREEGA.2:   data
./SFOCGA.1:   data
./SFOEGA.2:   data
./TATCGA.1:   data
./TATEGA.2:   data
./TATOU.COM:  DOS executable (COM)
./TRACGA.1:   data
./TRAEGA.2:   data
./VIGCGA.1:   data
./VIGEGA.2:   data

```

---

### Post by iponeverything on 2010-02-14
I think those are just data files for the application, not images.

doing "strings BA1CGA.1" might give an idea what it is used for.

The application should be runnable under emulation.

---

### Post by wmcbrine on 2010-02-14
Well clearly those are man pages. ;)

Back in the EGA/CGA days, I think PCX was the most common image format used in games and such, to the extent that there was a standard format. (GIF was popular for trading images on BBSes, but it was too CPU-intensive for games!) If they aren't PCX, then you may have to resort to running the program in DOSEMU or DOSBox and doing screen captures.

---

### Post by WitchCraft on 2010-02-16
> **wmcbrine said:**
> Well clearly those are man pages. ;)

Back in the EGA/CGA days, I think PCX was the most common image format used in games and such, to the extent that there was a standard format. (GIF was popular for trading images on BBSes, but it was too CPU-intensive for games!) If they aren't PCX, then you may have to resort to running the program in DOSEMU or DOSBox and doing screen captures.

That's exactly what I'm trying to avoid ;-)))
I've done an example capture, but i have to remove the overlay manually (merging together several different screenshots).
Not necessary to say that this consumes time and the outcome is of dubious quality ;-)

Btw, is there any way to extract sound?
From the quality, I'd assume midi, but I'm not sure, did midi run on DOS? Sound doesn't work on Fedora, it worked on Ubuntu.

---

### Post by WitchCraft on 2010-02-16
bump.

---

### Post by WitchCraft on 2010-02-20
bump

---

### Post by WitchCraft on 2010-02-26
bump.

---

