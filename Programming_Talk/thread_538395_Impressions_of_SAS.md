---
title: "Impressions of SAS?"
date: 2007-08-29
forum: Programming Talk
---

### Post by gnuman on 2007-08-29
Hi all,

I've taught myself some programming here and there.  Anyway, I just signed up for a class that will do some "programming" in SAS 9.1.2.  It looks pretty easy to me, except I can't help but want to say, "What a crappy, expensive language."  

Or maybe I'm just so used to open-source software that I'm just having culture shock or something.  I mean, every 5 minutes it says something along the line of "This version will expire in 30 days...."  It prints that right to the output file!  Now, I'm using this at a campus comp lab that pays a $10,000 license just so we get a "good deal" (actual quote from the instructor) on the software.  I haven't finished my installation yet on my seldom-used XP computer simply because I have to wait for the proper install code to be emailed to me from the university (they had no Linux version).

Opinions of SAS, anyone?

:confused:

---

### Post by gnuman on 2007-08-29
I did find this not-so-helpful site:

[http://www.sas-sucks.com/index.php?pr=Home_Page](http://www.sas-sucks.com/index.php?pr=Home_Page)

:-k

---

### Post by pmasiar on 2007-08-30
Yes, SAS is mighty expensive. Looks like you are stuck. :-(

University where I work (and it is expensive private research uni) uses extensively R (but not exclusively). As professor explained, R is  as powerful as SPSS/SAS when used properly, and once you learn it, you can use it anywhere, without asking permission.  Also, there are loads of modules to analyze biologic/genetics data - when scientist analyzes data, wants to share not only data but also methods and algorithms for peer review, so again R makes more sense. 

He is also young and kind of hacker, he created his own extension (way to graph data).

But exactly as you found out, smaller cheaper state uni close by uses SPSS, because they don't have experts who want to do something in it, just teach - and R comes with only community support, noone to choke :-)

R has also RPy - Python bindings.

I try to avoid learning proprietary software if I can get away with it.

I don't think that you can convert them to R, but it never hurts to try (OK it **does** hurt, but not too much :-) )- and explain why it is better for learning.

Good luck!

---

### Post by gnuman on 2007-08-30
> **pmasiar said:**
> 

---snip-----

R has also RPy - Python bindings.

I try to avoid learning proprietary software if I can get away with it.

I don't think that you can convert them to R, but it never hurts to try (OK it **does** hurt, but not too much :-) )- and explain why it is better for learning.

Good luck!

**Thanks** for the info.  You read my mind.  My original thought was to hand in all the work done in SAS and then hand it in in another form.  I've got to check out R, as RPy would be a cool way to do it.

:)

---

### Post by nanotube on 2007-08-30
> **gnuman said:**
> **Thanks** for the info.  You read my mind.  My original thought was to hand in all the work done in SAS and then hand it in in another form.  I've got to check out R, as RPy would be a cool way to do it.

:)

here's a note from another R devotee:
yea, forget SAS, and use R instead. :) there are /some/ things that are not built into R but are into SAS, and depending on your area they may be a lot - but then again, the same thing applies in reverse to R.

plus, R is like a real programming language, whereas SAS looks just like a bunch of magic incantations strung together. :)

for a person with a programming background, SAS is generally a painful experience.

---

### Post by gnuman on 2007-08-30
Having trouble getting R installed from:

[http://cran.fhcrc.org/](http://cran.fhcrc.org/)

Any advice?  I'm a n00b with installs like this.  
In my etc/apt/sources.list I added:
```
http://cran.cnr.berkeley.edu/R/CRAN/bin/linux/ubuntu feisty
```

and get the message:
```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

Well, I've been in places like this before.  I guess some READMEs will help.  I'll keep at it....

---

### Post by pmasiar on 2007-08-30
Are you using ubuntu? It is in repository: r-cran-* IIRC, I installed with no problems - nothing what I remember a year later :-)

---

### Post by nanotube on 2007-08-30
> **gnuman said:**
> Having trouble getting R installed from:

[http://cran.fhcrc.org/](http://cran.fhcrc.org/)

Any advice?  I'm a n00b with installs like this.  
In my etc/apt/sources.list I added:
```
http://cran.cnr.berkeley.edu/R/CRAN/bin/linux/ubuntu feisty
```

and get the message:
```
Could not download all repository indexes

The repository might be no longer available or could not be contacted because of network problems. If available an older version of the failed index will be used. Otherwise the repository will be ignored. Check your network connection and the correct writing of the repository address in the preferences.
```

Well, I've been in places like this before.  I guess some READMEs will help.  I'll keep at it....

you seem to have the repo incorrectly specified. this is what i have, and it works just fine:

```
# R packages repositories
# gpg --keyserver subkeys.pgp.net --recv-key E2A11821
# gpg -a --export E2A11821 | sudo apt-key add -
# let's use the berkeley mirror
deb http://cran.cnr.berkeley.edu/bin/linux/ubuntu feisty/

```

give that a try. :)

---

### Post by nanotube on 2007-08-30
> **pmasiar said:**
> Are you using ubuntu? It is in repository: r-cran-* IIRC, I installed with no problems - nothing what I remember a year later :-)

yea, but the repos directly from the r-project have newer versions. :)
(2.4.1 in the ubuntu repos, and 2.5.1 in the r-project repos)

---

### Post by pmasiar on 2007-08-30
> **nanotube said:**
> but the repos directly from the r-project have newer versions. :)


I prefer old version which works after install to newer version which does not :-) That's why I prefer debian - someone solved all boring installations problems for me, what is left are interesting applications to code!

---

### Post by nanotube on 2007-08-30
> **pmasiar said:**
> I prefer old version which works after install to newer version which does not :-) That's why I prefer debian - someone solved all boring installations problems for me, what is left are interesting applications to code!

i'm not sure i understand what you're saying - version 2.5.1 works for me just fine after i installed it... did it not work for you?

---

### Post by pmasiar on 2007-08-30
It did not worked for OP, IIUC. 

I don't want even **bother** with trying new version, unless it has some new crucial functionality. Current ubuntu usually works just fine for me.

One exception was recently Turbogears - development is very rapid, so repository version is obsolete, and I had to install eggs. But that was easy. :-)

---

### Post by slavik on 2007-08-30
if you think SAS/SPSS are expensive, lookup SciFinder ... I've been told it is 50k per license per year ... yay!

---

### Post by gnuman on 2007-08-31
> **slavik said:**
> if you think SAS/SPSS are expensive, lookup SciFinder ... I've been told it is 50k per license per year ... yay!

OMFG!:shock:

Hey, just wanted to say thanks for all the help from everyone so far.
I'll get back to the installation attempts tomorrow  :)

---

### Post by gnuman on 2007-08-31
> **nanotube said:**
> you seem to have the repo incorrectly specified. this is what i have, and it works just fine:

```
# R packages repositories
# gpg --keyserver subkeys.pgp.net --recv-key E2A11821
# gpg -a --export E2A11821 | sudo apt-key add -
# let's use the berkeley mirror
deb http://cran.cnr.berkeley.edu/bin/linux/ubuntu feisty/

```

give that a try. :)

Bam! Got it!  Thanks!

Now to start learning how to use R to avoid SAS :)

Thanks to all--another happy customer....

---

### Post by nanotube on 2007-08-31
> **pmasiar said:**
> It did not worked for OP, IIUC. 

I don't want even **bother** with trying new version, unless it has some new crucial functionality. Current ubuntu usually works just fine for me.

One exception was recently Turbogears - development is very rapid, so repository version is obsolete, and I had to install eggs. But that was easy. :-)

well, it didn't work because he specified the repo incorrectly. :)

but i agree with your general point about sticking with the official repos unless there's a good reason.

i started using the r-project repos back when i was using dapper and there actually was a good reason (dapper's version was even older than feisty's), and i kinda stuck with it through my feisty upgrade. :)

---

### Post by pAt84 on 2007-09-06
Hello gnuman,

did you manage to get SAS running under Ubuntu? If yes, you had any problems installing it?

Pat

---

### Post by gnuman on 2007-09-07
Pat,

Sorry for the delay.  I never really considered putting SAS on my pride and joy (my Ubuntu laptop).  I installed it on my old XP box that I don't have connected to the net.

I did however, install R and several other R components on my Ubuntu laptop.  I so seldom use Windows anymore, and this class looks like something I'm going to breeze through and then not really use later in life (that's sad, but true).  

Just today I helped a student of mine get a donated 1 Ghz HP up and running with Ubuntu.  I have a pretty loyal computer programming club and the kids are very interested in OS, Python, and Ubuntu :-)

Cheers.

---

