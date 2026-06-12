---
title: "How to start R"
date: 2010-08-07
forum: Programming Talk
---

### Post by satimis on 2010-08-07
Hi folks,


Just finished installing R on Ubuntu 10.04, running on a VM, download following packages on repo;

r-base
littler
r-cran-plotrix
r-cran-qtl
r-cran-rggobi

But I could not get R started. r is on /usr/bin/r

On console evoking it just hanging there.  Any additional packages I need to install?  Thanks

B.R.
satimis

---

### Post by ronnielsen1 on 2010-08-07
> You need to have installed *r-base-dev* for this to work in Ubuntu.

Do you have this installed?

[http://www.keittlab.org/node/158](http://www.keittlab.org/node/158)

---

### Post by satimis on 2010-08-07
> **ronnielsen1 said:**
> Do you have this installed?

[http://www.keittlab.org/node/158](http://www.keittlab.org/node/158)

Hi,

I got it. It should be R (capital letter) NOT r


$ R```


R version 2.10.1 (2009-12-14)
Copyright (C) 2009 The R Foundation for Statistical Computing
ISBN 3-900051-07-0

R is free software and comes with ABSOLUTELY NO WARRANTY.
You are welcome to redistribute it under certain conditions.
Type 'license()' or 'licence()' for distribution details.

  Natural language support but running in an English locale

R is a collaborative project with many contributors.
Type 'contributors()' for more information and
'citation()' on how to cite R or R packages in publications.

Type 'demo()' for some demos, 'help()' for on-line help, or
'help.start()' for an HTML browser interface to help.
Type 'q()' to quit R.

```

I haven't installed r-base-dev.  Is it for compiling package?  Thanks


B.R.
satimis

---

### Post by ronnielsen1 on 2010-08-07
> (Actually, you will almost certainly want to compile add-on R packages locally, so install *r-base-dev* instead.)

[http://www.keittlab.org/node/158](http://www.keittlab.org/node/158)
I read it wrong but it sounds like you might need it

---

### Post by Tibuda on 2010-08-07
You'll need r-base-dev to install some CRAN packages that need compiling.

---

### Post by satimis on 2010-08-07
> **danielrmt said:**
> You'll need r-base-dev to install some CRAN packages that need compiling.

Hi danielrmt,

Thanks for your advice.  I got r-base-dev installed.

B.R.
satimis

---

### Post by satimis on 2010-08-07
> **ronnielsen1 said:**
> [http://www.keittlab.org/node/158](http://www.keittlab.org/node/158)
I read it wrong but it sounds like you might need it

Thanks

B.R.
satimis

---

### Post by satimis on 2010-08-09
Editted.

---

