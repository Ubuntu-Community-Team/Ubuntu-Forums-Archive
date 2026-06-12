---
title: "unable to find perl RRDs.pm"
date: 2006-11-21
forum: Programming Talk
---

### Post by mibikerguy on 2006-11-21
I currently am running Ubuntu Breezy server with Perl 5.8.7-10; rrdcollect; and rrdtool installed via Synaptic Package Manager. I have an application which uses RRD to log data and I am throwing an error message that RRDs.pm is not available. I have reindexed my files and using "locate" I have found that this module is not avaliable. Searching the Forums, I have been unable to find anyone else who has had this problem. Suggestions please regarding how to find and install this module?

Thanks everyone

Tom

---

### Post by mibikerguy on 2006-11-21
OK, After much searching, here is the answer.....

The RRDs.pm is contained in the rrdtool-1.2.15 package. I was not able to obtain a working package from the Synaptic Package Manager and needed to download it from [http://oss.oetiker.ch/rrdtool/](http://oss.oetiker.ch/rrdtool/). using ./configure, i discovered that I needed a couple of extra libs which I installed via Synaptic.

Tom

---

### Post by mibikerguy on 2006-11-21
I am still at a road block. The previoius post was not the answer for my problem. I have now installed livrdds-perl (which is said to contain RDDs.pm, however, I still do not have this module.....

Help please!

Tom

---

### Post by mibikerguy on 2006-11-22
Bump please

---

### Post by valica on 2006-11-23
> **mibikerguy said:**
> I have now installed livrdds-perl (which is said to contain RDDs.pm, however, I still do not have this module.....
Tom

try the following to test if your Perl installation find RRDs.pm:
```

perl -MRRDs -le 'print q(ok!)'

```
if Perl can't load the RRDs module it will show some error like *Can't locate RRDs.pm in @INC...*.

> 
I have an application which uses RRD to log data and I am throwing an error message that RRDs.pm is not available. 


what is this application that you are trying to install and what exactly is the error message?

---

### Post by hsoares on 2007-05-10
Hi,
i have the same problem and i'm trying to fix it. 
I'm trying to install oreon1.4.

   "Where is installed RRD perl modules (RRDs.pm) ?"

i did "locate RRDs.pm" and nothing.

If someone can help me i will be thankful.

Best reguards

Ubuntu 7.04
Nagios 2.9

---

### Post by blundr on 2007-05-12
> **hsoares said:**
> Hi,
i have the same problem and i'm trying to fix it. 
I'm trying to install oreon1.4.

   "Where is installed RRD perl modules (RRDs.pm) ?"

i did "locate RRDs.pm" and nothing.

If someone can help me i will be thankful.

Best reguards

Ubuntu 7.04
Nagios 2.9

```
apt-get install librrds-perl
```

---

### Post by hsoares on 2007-05-21
Still can not found RRds .pm


hsoares@hsoares-laptop:/$ perl -MRRDs -le 'print q(ok!)'
ok!
hsoares@hsoares-laptop:/$ locate RRDs.pm
hsoares@hsoares-laptop:/$ 

I don't know what's happening. :(
I'm recently new in this "World" so it can be probably my error.

---

### Post by crosmuller on 2007-10-16
> **hsoares said:**
> Still can not found RRds .pm


hsoares@hsoares-laptop:/$ perl -MRRDs -le 'print q(ok!)'
ok!
hsoares@hsoares-laptop:/$ locate RRDs.pm
hsoares@hsoares-laptop:/$ 

I don't know what's happening. :(
I'm recently new in this "World" so it can be probably my error.

Installing librrds-perl did the trick for me! Maybe you can't find RRDs.pm with locate beacuse you forgot updatedb?

---

### Post by Ariccanfly on 2009-03-24
Thanks did the trick for me
:popcorn:

---

### Post by Kissack on 2010-03-12
> **blundr said:**
> ```
apt-get install librrds-perl
```

Top answer.  Fixed it for me - thanks very much

---

### Post by JohnMazurka on 2012-05-07
> **blundr said:**
> ```
apt-get install librrds-perl
```
Thanks Blundr
just what I was looking for
J

---

