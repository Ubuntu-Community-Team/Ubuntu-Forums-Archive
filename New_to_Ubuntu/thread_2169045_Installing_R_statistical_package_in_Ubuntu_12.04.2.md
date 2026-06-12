---
title: "Installing R statistical package in Ubuntu 12.04.2"
date: 2013-08-20
forum: New to Ubuntu
---

### Post by havtrouble on 2013-08-20
Hello all. I am in need of help to install R statistical package. I have googled and read some and copy pasted some of the terminal commands. But it ended nowhere and I still have no "R". If somebody can point me towards a place where simple explanations are given, that will be awesome. Thanks

---

### Post by bapoumba on 2013-08-20
Which ubuntu release are you using ?
[http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README) :
> As of March 25, 2013, the supported releases are Raring
Ringtail (13.04), Quantal Quetzal (12.10), Precise Pangolin (12.04; LTS),
and  Lucid Lynx (10.04; LTS).

Edit :
Doh, ignore, it's in your title >.<

r-base packages are in universe, do you have this repo enabled ?

[http://www.r-project.org/](http://www.r-project.org/)

---

### Post by havtrouble on 2013-08-20
You wrote,
> [COLOR=#000000]r-base packages are in universe, do you have this repo enabled ?[/COLOR]

[http://www.r-project.org]("http://www.r-project.org/")
 
That is exactly the trouble. How do I have this repo enabled?

---

### Post by steeldriver on 2013-08-21
Instructions for adding repositories here --> [https://help.ubuntu.com/community/Repositories/Ubuntu](https://help.ubuntu.com/community/Repositories/Ubuntu)

It's a little tricky to search for a package called 'R' but you can list the available packages from the command line using

```
apt-cache search --names-only ^r-
```

---

### Post by monkeybrain20122 on 2013-08-21
Install synaptic.

```
sudo apt-get install synaptic

```
Then open it and search "r-cran"
It is an outdated version though, if you want R 3.0.1 add this ppa
[https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)

Open synaptic, go to Settings > Repositories > Other software, press Add and enter in the box
```
ppa:marutter/rrutter 
```
Then reload synaptic (click the "Reload" button)

You need actually only install r-base and r-recommended and the dependencies, the rest I would install from within R.

---

### Post by bapoumba on 2013-08-21
Just to make sure, please post your sources.list:
**cat etc/apt/sources.list**

---

### Post by havtrouble on 2013-08-21
Thanks monkeybrain20122. I have done> sudo apt-get install synaptic

 and then opened the synaptic and done
> ppa:marutter/rrutter
What happens next? Sorry for being so dumb.

---

### Post by drmrgd on 2013-08-21
> **monkeybrain20122 said:**
> Install synaptic.

```
sudo apt-get install synaptic

```
Then open it and search "r-cran"
It is an outdated version though, if you want R 3.0.1 add this ppa
[https://launchpad.net/~marutter/+archive/rrutter](https://launchpad.net/~marutter/+archive/rrutter)

Open synaptic, go to Settings > Repositories > Other software, press Add and enter in the box
```
ppa:marutter/rrutter 
```
Then reload synaptic (click the "Reload" button)

You need actually only install r-base and r-recommended and the dependencies, the rest I would install from within R.

That's nice!  I usually just follow the instructions here to install:
 
[http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)

I didn't think to look for Michael Rutter's Launchpad page, and I usually have to go through the extra PGP key signing step listed in there.  I'm going to have to remember this Lauchpad page for future reference!

To the OP: once you've added that PPA to the list in Synaptic, just refresh the software cache, look for r-base, and then you should be able to install it.

---

### Post by havtrouble on 2013-08-21
Thank you all I have it now.

---

### Post by monkeybrain20122 on 2013-08-21
> **drmrgd said:**
> That's nice!  I usually just follow the instructions here to install:
 
[http://cran.r-project.org/bin/linux/ubuntu/README](http://cran.r-project.org/bin/linux/ubuntu/README)

I didn't think to look for Michael Rutter's Launchpad page, and I usually have to go through the extra PGP key signing step listed in there.  I'm going to have to remember this Lauchpad page for future reference!

To the OP: once you've added that PPA to the list in Synaptic, just refresh the software cache, look for r-base, and then you should be able to install it.

Yeah Michael told me that all packages in Cran's Ubuntu repository are from his ppa except they are older builds, so unless for some reasons you want an older version he recommends using the ppa.

---

### Post by texaswriter on 2013-08-22
If the thread is solved, does the OP know how to change status to "SOLVED"?

---

### Post by havtrouble on 2013-08-22
I have subsequently installed R studio which is much more "friendly" than R. But this application seems to hang. I havent been able to spend as much time with R studio as I would have liked to, so I am unable to provide more details 
texaswriter, your mild rebuke is well taken. Yes the OP does know how to mark this thread as solved and indeed, has done so.

---

### Post by texaswriter on 2013-08-23
> **havtrouble said:**
> I have subsequently installed R studio which is much more "friendly" than R. But this application seems to hang. I havent been able to spend as much time with R studio as I would have liked to, so I am unable to provide more details 

R Studio is a front end to R, so it should have pulled everything in. 

Can you be more specific about "hanging". I'd run it from a terminal, use project files and save often. You can report any bugs you have. 

> **havtrouble said:**
>  texaswriter, your mild rebuke is well taken. Yes the OP does know how to mark this thread as solved and indeed, has done so.

I didn't mean that as a rebuke of any kind. If people are searching for solutions, they can use the past solutions. Obviously threads marked as solved more clearly state that this is a possible solution.

---

