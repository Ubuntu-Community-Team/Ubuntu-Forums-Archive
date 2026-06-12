---
title: "Arbitrary precision in C with GMP and MPFR"
date: 2007-10-29
forum: Programming Talk
---

### Post by Badenn on 2007-10-29
Does someone know how to install GMP [**http://gmplib.org/**]("http://gmplib.org/") and MPFR [**http://www.mpfr.org/**]("http://www.mpfr.org/") ? Could you give me some advices step by step?
I work in Physics and need to do some calculations with arbitrary precision using C. I use Ubuntu 6.06, but I'm not very experimented on Linux, so not sure how to install those libraries, and make them work.
Thanks in advance.

---

### Post by hod139 on 2007-10-29
GMP:
sudo apt-get install libgmp3-dev

MPFR
sudo apt-get install libmpfr-dev

---

### Post by Badenn on 2007-10-29
Thank you. It works now! Before, I had tried to install only libmpfr1. 
Cheers.

---

