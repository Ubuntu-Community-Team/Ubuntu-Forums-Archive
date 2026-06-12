---
title: "gfortran: type mismatch in argument 'foo' at (1); passed COMPLEX(8) to REAL(8)"
date: 2015-03-21
forum: Packaging and Compiling Programs
---

### Post by phorminx on 2015-03-21
With some program, gfortran 4.6.3 gives me a bunch of warnings
> Type mismatch in argument 'foo' at (1); passed COMPLEX(8) to REAL(8)
I assume that with fortran it is always possible to interpret complex numbers as two consecutive real numbers, so that this warning is harmless.  How can I suppress these warnings?  The option -w works, but I'd prefer to suppress these warnings more specifically so that I do not miss more important warnings.
Thanks.

---

### Post by bardo2 on 2015-03-23
WOW, i havent seen Fortran in... what? 40 years?
Back on topic: if nothing else, you can pass the output through awk (or grep - for that matter) to filter out undesired lines - or make more meaningful ones out of them.
more information is necessary: does you output appear on stderr or stdout? is ALL output appearing there? and so on...

---

### Post by phorminx on 2015-03-23
> **bardo2 said:**
> if nothing else, you can pass the output through awk (or grep - for that matter) to filter out undesired lines - or make more meaningful ones out of them.
sure, but that's not quite my point.
> **bardo2 said:**
> more information is necessary: does you output appear on stderr or stdout? is ALL output appearing there? and so on...
gfortran (like any gcc compiler) comes with zillions of options to enable / disable various warnings. The option -w disables all warnings, which also suppresses the warnings about mismatched types.  But I'd like to be more specific and suppress / disable only these "type mismatch" warnings.  Among the gfortran-specific options I could not find this option.  So I believe the relevant option applies to various gcc compilers (and it might apply also to some other scenarios than just mismatched types).  But there are rather many of these options and I could not yet find the right one.

---

### Post by phorminx on 2015-03-23
> **bardo2 said:**
> if nothing else, you can pass the output through awk (or grep - for that matter) to filter out undesired lines - or make more meaningful ones out of them.
sure, but that's not quite my point.
> **bardo2 said:**
> more information is necessary: does you output appear on stderr or stdout? is ALL output appearing there? and so on...
gfortran (like any gcc compiler) comes with zillions of options to enable / disable various warnings. The option -w disables all warnings, which also suppresses the warnings about mismatched types.  But I'd like to be more specific and suppress / disable only these "type mismatch" warnings.  Among the gfortran-specific options I could not find this option.  So I believe the relevant option applies to various gcc compilers (and it might apply also to some other scenarios than just mismatched types).  But there are rather many of these options and I could not yet find the right one.

---

