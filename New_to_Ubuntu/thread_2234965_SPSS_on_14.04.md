---
title: "SPSS on 14.04"
date: 2014-07-18
forum: New to Ubuntu
---

### Post by mithun6 on 2014-07-18
Hey, I need to install SPSS on my ubuntu 14.04, 64 bit, please help

---

### Post by claracc on 2014-07-18
I think, this link: [http://www-01.ibm.com/support/docview.wss?uid=swg24029274](http://www-01.ibm.com/support/docview.wss?uid=swg24029274) can help you.

Remark that if you install in 64 bits system (which is not oficially compatible), you have to install ia32-libs software package.

---

### Post by monkeybrain20122 on 2014-07-18
There is no more ia-32libs package since 13.10

From this link [https://www.ibm.com/developerworks/community/forums/html/topic?id=189eeb9d-b5bd-43b9-a325-ccceea61fd66](https://www.ibm.com/developerworks/community/forums/html/topic?id=189eeb9d-b5bd-43b9-a325-ccceea61fd66)
```
sudo apt-get install lib32z1 lib32ncurses5 lib32bz2-1.0
```
But they seem to get into some other problems..

---

### Post by SeijiSensei on 2014-07-18
If you just need rather simple statistics like frequencies, descriptives, crosstabs and regression, I suggest you give [PSPP]("http://www.gnu.org/software/pspp/"), the GNU open-source SPSS clone, a try.  You can install it from the repositories with "sudo apt-get install pspp".  It will read and write SPSS system files.

Here's a list of supported statistical calculations from the [manual]("http://www.gnu.org/software/pspp/manual/pspp.html"):
```

    15.1 DESCRIPTIVES
    15.2 FREQUENCIES
    15.3 EXAMINE
    15.4 CORRELATIONS
    15.5 CROSSTABS
    15.6 FACTOR
    15.7 LOGISTIC REGRESSION
    15.8 MEANS
    15.9 NPAR TESTS
        15.9.1 Binomial test
        15.9.2 Chisquare Test
        15.9.3 Cochran Q Test
        15.9.4 Friedman Test
        15.9.5 Kendall's W Test
        15.9.6 Kolmogorov-Smirnov Test
        15.9.7 Kruskal-Wallis Test
        15.9.8 Mann-Whitney U Test
        15.9.9 McNemar Test
        15.9.10 Median Test
        15.9.11 Runs Test
        15.9.12 Sign Test
        15.9.13 Wilcoxon Matched Pairs Signed Ranks Test 
    15.10 T-TEST
        15.10.1 One Sample Mode
        15.10.2 Independent Samples Mode
        15.10.3 Paired Samples Mode 
    15.11 ONEWAY
    15.12 QUICK CLUSTER
    15.13 RANK
    15.14 REGRESSION
        15.14.1 Syntax
        15.14.2 Examples 
    15.15 RELIABILITY
    15.16 ROC 

```
No n-way analysis of variance I'm sorry to say.

---

### Post by monkeybrain20122 on 2014-07-19
> **SeijiSensei said:**
> If you just need rather simple statistics like frequencies, descriptives, crosstabs and regression, I suggest you give [PSPP]("http://www.gnu.org/software/pspp/"), the GNU open-source SPSS clone, a try.  You can install it from the repositories with "sudo apt-get install pspp".  It will read and write SPSS system files.

Here's a list of supported statistical calculations from the [manual]("http://www.gnu.org/software/pspp/manual/pspp.html") ...

You won't get all of those supported features from the version in the repo (0.7.9) e.g  you need 0.8+ for logistic regression. The absence of logit is a show stopper for many students in social sciences who would have used PSPP instead of SPSS. 

OP can install 0.8.1 from ppa if he/she is interested (or at least checing it out)

[https://launchpad.net/~adamzammit/+archive/ubuntu/pspp](https://launchpad.net/~adamzammit/+archive/ubuntu/pspp)

---

### Post by SeijiSensei on 2014-07-20
Or you can use [gretl]("http://gretl.sourceforge.net/") which has every sort of limited dependent variable method you might want including binomial and multinomial probit and logit.  It's also in the repositories.  The analyses presented in my blog (below) were all conducted in PSPP or gretl.

---

