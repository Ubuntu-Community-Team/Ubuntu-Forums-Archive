---
title: "R in double dose?"
date: 2012-02-08
forum: New to Ubuntu
---

### Post by JuanNZ on 2012-02-08
Hi all,

Here is another slightly basic question. I am running Ubuntu 11.04 on my laptop. I have been meaning to use R for my work at school. I know I installed the latest binary of this package, because I went through all the process of setting up the repositories and the command line instructions  that you find in R manual.

I let that sit for a while, without using it, but then I had one of those last minute assignments. Because I was unsure how to use the terminal version of R, I just felt quickly for the temptation to install R commander (from the software manager).  While installing it, the program asked me again to choose a mirror and then installed a whole bunch of packages.

I am done with the assignment, but now (and this might seem a bit of a dumb question) I am wondering: Does the fact that I already had R binary installed in my laptop and the I installed R commander later, conflicts in any way? Does R commander takes up more space and resources? 

Thanks for your help,

---

### Post by Bodsda on 2012-02-08
> **JuanNZ said:**
> Hi all,

Here is another slightly basic question. I am running Ubuntu 11.04 on my laptop. I have been meaning to use R for my work at school. I know I installed the latest binary of this package, because I went through all the process of setting up the repositories and the command line instructions  that you find in R manual.

I let that sit for a while, without using it, but then I had one of those last minute assignments. Because I was unsure how to use the terminal version of R, I just felt quickly for the temptation to install R commander (from the software manager).  While installing it, the program asked me again to choose a mirror and then installed a whole bunch of packages.

I am done with the assignment, but now (and this might seem a bit of a dumb question) I am wondering: Does the fact that I already had R binary installed in my laptop and the I installed R commander later, conflicts in any way? Does R commander takes up more space and resources? 

Thanks for your help,

Hi,

I don't know anything about R, but this should be fairly generic. The binary install was likely to be contained to a single build directory, so this should mean that no conflicts would occur from a package installed via the software manager. However, if installing R commander removed any dependencies that R had, then this may cause a problem, but I think that is very unlikely.

Yes there will be extra space used, but not much at all, and extra resource overhead will be minimal and only experienced when actually running R commander.

Hope this helps,
Bodsda

---

### Post by JuanNZ on 2012-02-08
> **Bodsda said:**
> Hi,

I don't know anything about R, but this should be fairly generic. The binary install was likely to be contained to a single build directory, so this should mean that no conflicts would occur from a package installed via the software manager. However, if installing R commander removed any dependencies that R had, then this may cause a problem, but I think that is very unlikely.

Yes there will be extra space used, but not much at all, and extra resource overhead will be minimal and only experienced when actually running R commander.

Hope this helps,
Bodsda

Thanks Bodsda, 

This does help. I suppose if I want to check everything is working fine with the R Binary I can always remove R commander and try to run an analysis. I will pop in again and let you guys know what is the outcome of that.

Cheers,
JuanNZ

---

### Post by Bodsda on 2012-02-08
> **JuanNZ said:**
> Thanks Bodsda, 

This does help. I suppose if I want to check everything is working fine with the R Binary I can always remove R commander and try to run an analysis. I will pop in again and let you guys know what is the outcome of that.

Cheers,
JuanNZ

This may be due to my lack of knowledge about R, but can they not run side by side?

Bodsda

---

### Post by JuanNZ on 2012-02-09
> **Bodsda said:**
> This may be due to my lack of knowledge about R, but can they not run side by side?

Bodsda

R commander runs ok. At least to the extent I was using it. I have not used it for anything incredibly complicated, just summary statistics. I guess when I will have to do something more complex I will find out the full answer to your question. But for the moment, R commander its doing fine.

Many thanks.

---

