---
title: "installing blas on ubuntu"
date: 2008-06-22
forum: New to Ubuntu
---

### Post by vak002 on 2008-06-22
hi all,

i'm pretty new to ubuntu, and trying to switch from windows.
I'm attempting to use rblas, but it turns out to be much more challenging to do than under windows. After experimenting with a set of instruction found on the author's website (given here; [http://oldmill.uchicago.edu/~wilder/Code/rblas/](http://oldmill.uchicago.edu/~wilder/Code/rblas/))

i obtained the following error messages:

root@kaveh:~# R CMD INSTALL rblas
* Installing to library '/home/kaveh/R/i486-pc-linux-gnu-library/2.7'
* Installing *source* package 'rblas' ...
** libs
gcc -std=gnu99 -I/usr/share/R/include      -fpic  -g -O2 -c rblas1.c -o rblas1.o
rblas1.c:9: error: conflicting types for &#8216;drotm_&#8217;
/usr/share/R/include/R_ext/BLAS.h:59: error: previous declaration of &#8216;drotm_&#8217; was here
rblas1.c:11: error: conflicting types for &#8216;drotmg_&#8217;
/usr/share/R/include/R_ext/BLAS.h:62: error: previous declaration of &#8216;drotmg_&#8217; was here
rblas1.c:14: error: conflicting types for &#8216;zaxpy_&#8217;
/usr/share/R/include/R_ext/BLAS.h:243: error: previous declaration of &#8216;zaxpy_&#8217; was here
rblas1.c:16: error: conflicting types for &#8216;zcopy_&#8217;
/usr/share/R/include/R_ext/BLAS.h:246: error: previous declaration of &#8216;zcopy_&#8217; was here
rblas1.c:18: error: conflicting types for &#8216;zdotu_&#8217;
/usr/share/R/include/R_ext/BLAS.h:252: error: previous declaration of &#8216;zdotu_&#8217; was here
rblas1.c:20: error: conflicting types for &#8216;zdotc_&#8217;
/usr/share/R/include/R_ext/BLAS.h:249: error: previous declaration of &#8216;zdotc_&#8217; was here
rblas1.c:22: error: conflicting types for &#8216;zdrot_&#8217;
/usr/share/R/include/R_ext/BLAS.h:255: error: previous declaration of &#8216;zdrot_&#8217; was here
rblas1.c:24: error: conflicting types for &#8216;zrotg_&#8217;
/usr/share/R/include/R_ext/BLAS.h:316: error: previous declaration of &#8216;zrotg_&#8217; was here
rblas1.c:26: error: conflicting types for &#8216;zscal_&#8217;
/usr/share/R/include/R_ext/BLAS.h:318: error: previous declaration of &#8216;zscal_&#8217; was here
rblas1.c:28: error: conflicting types for &#8216;zswap_&#8217;
/usr/share/R/include/R_ext/BLAS.h:320: error: previous declaration of &#8216;zswap_&#8217; was here
rblas1.c:30: error: conflicting types for &#8216;izamax_&#8217;
/usr/share/R/include/R_ext/BLAS.h:240: error: previous declaration of &#8216;izamax_&#8217; was here
rblas1.c:32: error: conflicting types for &#8216;dzasum_&#8217;
/usr/share/R/include/R_ext/BLAS.h:236: error: previous declaration of &#8216;dzasum_&#8217; was here
rblas1.c:33: error: conflicting types for &#8216;dznrm2_&#8217;
/usr/share/R/include/R_ext/BLAS.h:238: error: previous declaration of &#8216;dznrm2_&#8217; was here
rblas1.c:34: error: conflicting types for &#8216;dcabs1_&#8217;
/usr/share/R/include/R_ext/BLAS.h:234: error: previous declaration of &#8216;dcabs1_&#8217; was here
make: *** [rblas1.o] Error 1
ERROR: compilation failed for package 'rblas'
** Removing '/home/kaveh/R/i486-pc-linux-gnu-library/2.7/rblas'


What am i doing wrong ? Doees anyone know a work arround ?

thanks in advance,

---

### Post by ZabiGG on 2008-07-04
Hello,

Is the file you downloaded from the author's site either very old or very new?

It looks like it is not compatible with the compiler (gcc) version you're using.

Sorry I couldn't be more helpful.

---

### Post by vak002 on 2008-07-04
> **ZabiGG said:**
> Hello,

Is the file you downloaded from the author's site either very old or very new?

It looks like it is not compatible with the compiler (gcc) version you're using.

Sorry I couldn't be more helpful.

Thanks...i think the file is very old indeed.

Since then i tried different options:

I (think i have) installed (the right ?) Atlas packages using the package manager....although performance has increased markedly it still suffers a 40% performance gap with the windows box (same machine, other partition).

if anyone has been through this before...feel free to comment,...

PS i use a T7500 box...i installed the following packages from the repository:

atlas3-base
atlas3-SSE
atlas3-SSE2
lapack3-pic
libatlas3gf-SSE
libatlas3gf-SSE2

again, feel free to comment: i'm am not a computer literate.


*inverting a big matrix used to take 30+ secs, now down to 14
(windows+Rblas does the same on 10 sec)

---

### Post by vak002 on 2008-07-04
;

---

### Post by drexell0680 on 2008-07-06
Any luck with this?  I can confirm this problem on Hardy...

---

### Post by vak002 on 2008-07-10
i think i've found out.

the version of atlas used in windows is 3.7.34
the version of atlas available in the rep is 3.6.

only the 3.7. onwards fully support core 2 duo.

i guess we're now looking for a way to install a newer atlas version/

---

### Post by drexell0680 on 2008-07-10
Have you tried compiling from source?  The install instructions appear to be pretty clear at sourceforge (install tab)...

[http://math-atlas.sourceforge.net/](http://math-atlas.sourceforge.net/)

---

### Post by vak002 on 2008-07-13
> **drexell0680 said:**
> Have you tried compiling from source?  The install instructions appear to be pretty clear at sourceforge (install tab)...

[http://math-atlas.sourceforge.net/](http://math-atlas.sourceforge.net/)

sure. still i wonder why it isn't simply in the reps...

---

