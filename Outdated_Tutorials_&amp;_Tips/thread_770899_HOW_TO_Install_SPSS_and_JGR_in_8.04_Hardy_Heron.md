---
title: "HOW TO: Install SPSS and JGR in 8.04 Hardy Heron"
date: 2008-04-27
forum: Outdated Tutorials &amp; Tips
---

### Post by SendDerek on 2008-04-27
This guide is intended to help users install and configure "R", a great, free alternative to SPSS.  The instructions that I outline here are tailored to Ubuntu 8.04 (Hardy Heron), but can be alternated to fit any Linux distribution.  I also have these instructions available on [ my blog](http://derekhildreth.com/blog) [ located here]("http://derekhildreth.com/blog/index.php/2008/04/spss-alternative-for-linux-ubuntu-tutorial").

[SIZE="4"][COLOR="DarkRed"]What is "R"?[/COLOR][/SIZE]
This is right from the [R homepage]("http://www.r-project.org/"):
[indent]*R is a language and environment for statistical computing and graphics.  It is a <a href="http://www.gnu.org/" target="_top">GNU project</a> which is similar to the S language and environment which was developed at Bell Laboratories (formerly AT&amp;T, now Lucent Technologies) by John Chambers and colleagues.  R can be considered as a different implementation of S. There are some important differences, but much code written for S runs unaltered under R.*

*R provides a wide variety of statistical (linear and nonlinear modelling, classical statistical tests, time-series analysis, classification, clustering, ...) and graphical techniques, and is highly extensible.  The S language is often the vehicle of choice for research in statistical methodology, and R provides an Open Source route to participation in that activity.*[/indent]

[SIZE="4"][COLOR="DarkRed"]What is JGR?[/COLOR][/SIZE]
Fortunately or unfortunately, R is based on Command Line Interface (CLI).  This is where JGR comes into play.  JGR is a Graphical User Interface (GUI) for the R program. This is from the [ JGR homepage]("http://rosuda.org/JGR/index.shtml"):
[indent][i]**JGR **(speak 'Jaguar') is a universal and unified Graphical User Interface for R (it actually abbreviates **J**ava **G**ui for **R**). JGR was introduced at the [useR!]("http://www.ci.tuwien.ac.at/Conferences/useR-2006/") meeting in [2004](http://www.ci.tuwien.ac.at/Conferences/useR-2004/) and there is an introductory article in the [Statistical Computing and Graphics Newsletter Vol 16 nr 2]("http://www.statcomputing.org/newsletter/v162.pdf") p9-12[/indent]

[SIZE="4"][COLOR="DarkRed"]Installation:[/COLOR][/SIZE]
**We begin by simply installing R, Java, and all dependencies in one command:**
[COLOR="Gray"][In Terminal][/COLOR]```
sudo apt-get install -y r-base-dev r-recommended sun-java6-jdk
```

When everything is finished downloading and is about to install, you will be prompted to accept the End User License Agreement (EULA) from Sun Java:
[IMG]http://derekhildreth.com/blog/wp-content/uploads/screenshot-debconf-on-vaio.thumbnail.png[/IMG]

Check the "Do you agree with the DLJ license terms?" and hit "Forward".  Allow the installer to finish before continuing.

**Enable support for Java in R:**
[COLOR="Gray"][In Terminal][/COLOR] ```
sudo update-java-alternatives -s java-6-sun
```
[COLOR="Gray"][In Terminal][/COLOR] ```
sudo R CMD javareconf
```

**Now, installing JGR:**
[COLOR="Gray"][In Terminal][/COLOR] ```
sudo R
```
[COLOR="Gray"][In R][/COLOR] ```
install.packages('JGR')
```
After entering the above command, a prompt to select the closest mirror will appear:

[img]http://derekhildreth.com/blog/wp-content/uploads/screenshot-cran-mirror.png[/img]

Select the closest mirror to you and continue by running this command within R:
[COLOR="Gray"][In R][/COLOR] ```
library(JGR)
```

[COLOR="DarkRed"][SIZE="4"]Running it:
[/SIZE][/COLOR]
**Run JGR from inside R:**
[COLOR="Gray"][In R][/COLOR] ```
JGR()
```

**Run JGR from the terminal:**
[COLOR="Gray"][In Terminal][/COLOR] ```
/usr/local/lib/R/site-library/JGR/scripts/run
```

You should then be pleasantly greeted with the JGR interface:
[img]http://derekhildreth.com/blog/wp-content/uploads/screenshot-console.thumbnail.png[/img]

Thank you for using my tutorial.  If you thought this was useful, you may want to consider subscribing to my [Linux RSS Feed](http://feeds.feedburner.com/DerekHildrethsBlogLinux") to get updates for more Linux tips and tricks.  Don't forget to comment on [my blog](http://derekhildreth.com/blog/index.php/2008/04/spss-alternative-for-linux-ubuntu-tutorial) as well!

[COLOR="DarkRed"][SIZE="4"]Basic Troubleshooting:[/SIZE][/COLOR]
This section will be expanded upon as I receive input from the comments below.

If you get an error message while trying to load the JGR library (or at the end of the "install.packages('JGR') command that looks like, or contains the following:
[i]"installation of package 'maps' had non-zero exit status"
"installation of package 'CarbonEL' had non-zero exit status"
"installation of package 'rJava' had non-zero exit status"
"installation of package 'JavaGD' had non-zero exit status"
"installation of package 'mapproj' had non-zero exit status"
"installation of package 'iplots' had non-zero exit status in"[/i]

Then you will need to make sure that (1) you in fact have the package *sun-java6-jdk* installed, and (2) you have also run the two commands in the "Enable Java in R" section of this tutorial.

**[SIZE="1"]Sources**: [JGR Installation Guide for Feisty](http://rosuda.org/JGR/linux.shtml#faisty)[/SIZE]

---

### Post by superzorro on 2008-06-02
Thanks a lot, it worked perfectly!!!

---

### Post by samden on 2008-06-16
I received three errors:

```
Warning messages:
1: In install.packages("JGR") :
  installation of package 'rJava' had non-zero exit status
2: In install.packages("JGR") :
  installation of package 'JavaGD' had non-zero exit status
3: In install.packages("JGR") :
  installation of package 'iplots' had non-zero exit status

```

I have checked the code and have entered everything exactly as you said (except that I had already installed R). I believe Sun Java6 installed correctly and I configured R to use it correctly too. If anyone has any suggestions I would be very grateful.

---

### Post by orduek on 2008-06-19
Thank you for the this how to.
I have another question, how can I open an excel file with R (on JGR ofcourse)??

---

### Post by samden on 2008-06-19
I don't know that you can open an Excel file with R. Save the file as a .csv instead, then you can import it using the read.table function. An example of mine is:

```
nitrate <- read.table("leachna.csv",header=T,sep=",")

```

This means import the file "leachna.csv", the first line of which contains column titles (header=T), it is a csv file (separated by commas) (sep=","), and is to be saved in R as "nitrate".

I gave up on installing JGR and installed RKward instead - loving it, great program, even better than the R interface for Mac OS X, which is really saying a lot. I haven't managed to get JGR running to compare, but can highly recommend RKward.

---

### Post by orduek on 2008-06-19
how can you open those .csv files with RKward?
or do I have to use the command line?

---

### Post by samden on 2008-06-19
In any version of R (or any statistical program like SAS or SPSS) you should be using the command line (within R, the R command line) to do virtually everything. This is because R is a command-line language. The great advantage of the command line is that you can type your commands once, save them as a script file, run them as often as you like, modify them and run them again - far simpler than going through menus each time you want to do something.

So, to import a .csv file using RKward or ANY implementation of R, you would use the following code (modified of course for your own file):
```

# Set working directory
setwd("/home/samuel/Documents/Work/Statistics/Leachate")

# Import datfile Tot nitrate.csv
nitrate <- read.table("Tot nitrate.csv",header=T,sep=",")
```

The first line sets the working directory, the folder where you want R to find files to work with. The second line I explained earlier (lines starting with a # are comments).

This code can be entered directly into the console in RKward, or (better) into a script file (File-New-Script File). You can then highlight it in the script file, press F8 and the code will be run in the console.

You can then continue to enter code for the rest of your analysis into the script file and save it, and easily rerun the analysis at a later date or modify it slightly for a new dataset.

The beauty of RKward (and I don't know if this is true about JGR too) is that you can use the menus to do something that you don't know the code for. Then just look in the command log, and it will show you the actual code that the menu used. You can then copy this code, and save it in a script file for future use as is or modified. The best of both worlds!

Enjoy R. For further help do a google search for documentation, there is a lot of free documentation for R on the net.

---

### Post by orduek on 2008-08-20
How do I use this GUI to do statistic manipulations?

---

### Post by samden on 2008-08-20
That is a very broad question! You'll need to learn to use R - well worth the effort, it is an extremely good statistical package. The best place to start is with the documentation on R at the official homepage. There is a mailing list there for specific questions that you can't find an answer for in the documentation.

cran.r-project.org

You will get assistance installing the software here, but for help actually doing analysis you'd be better off going to the cran website (above) or talk to a friendly statistician. Good luck!

---

### Post by a3qp on 2008-08-30
Hi Samden,
you probably solved your problem post on June 16th, 2008 10:26 PM. However, I was having the same problems and I missed the solution.
So what I did was:

add

```
deb http://cran.r-project.org/bin/linux/ubuntu hardy/
```

to the file /etc/apt/source.list

then I did again the same steps that SendDerek said, and I copy again:

[in terminal]
```

sudo update-java-alternatives -s java-6-sun
sudo R CMD javareconf
sudo R

```

[and in R]
```

install.packages('JGR')
library(JGR)

```

Then, to get it running 

[in R]
```

library(JGR)
JGR()

```

I haven't been able to run it on Terminal (welcome suggestions!).

---

### Post by samden on 2008-08-30
Thanks for that. I gave up on it in the end and installed RKward (which is great by the way), sorry I forgot to post this earlier. Hopefully your post will help others.

---

### Post by Nordic on 2008-10-20
I initially could not get these instructions to work on my machine - several of the required packages would not install in R.

The fix was to install the packages "build-essentials" and "gfortan" from synaptic, and then repeat the steps from: sudo R forward.

Hopefully this helps someone!

---

### Post by Acradon on 2009-11-20
I can't install JGR. It keeps giving me an error that suggests that I am missing a library. How do I get around this.

Warning in install.packages("JGR") :
  argument 'lib' is missing: using '/usr/local/lib/R/site-library'
--- Please select a CRAN mirror for use in this session ---
Loading Tcl/Tk interface ... done
Warning message:
In getDependencies(pkgs, dependencies, available, lib) :
  package ‘JGR’ is not available
> library(JGR)
Error in library(JGR) : there is no package called 'JGR'


I tried to ignore the first error as the mirror interface opened anyway. But that did not work

Greets

Acradon

---

### Post by slowtrain on 2009-12-13
I have spent way too much time struggling to get JGR to work w/ R.  a3qp above is on the right track to a solution but doesn't explain fully why what he does is important.  (Am cross posting here a bit so this info gets out to people.)

Turns out that the version of R in the standard repositories is not generally up to date.  If you then try to use install.packages("JGR") in R to install JGR, the CRAN repository may tell you there is no JGR package--if there is no current JGR package in the repository that is consistent with your out of date version of R (or you could get errors).  When you try to install JGR directly by downloading it and using "R CMD INSTALL", you may well run into incompatibility problems between the different components needed to run JGR.

My solution is to a) purge r-base, r-base-core, and r-base-dev in Synaptic, b) update my "System > Administration > Software Sources" so they include an up to date R repository and gpg key for the repository (look here for instructions: [http://cran.r-project.org/bin/linux/ubuntu/](http://cran.r-project.org/bin/linux/ubuntu/)), and c) use Synaptic to install the now up-to-date version of r-base and r-base-core.  After this, you can do the usual JGR installation with install.packages.

The Ubuntu team should either include up-to-date repositories for R or make it very clear that JGR might not install w/o a 3rd party repository.  Many people use JGR.  R is not very useful for them w/o JGR.

---

### Post by silvioskk on 2010-05-20
[FONT=-moz-fixed]Good morning, 
I installed R and JGR following your guide.  Everything works but I noticed that my cpu is completely used by a  process called "java" (which is JGR) even if I am doing nothing.. 

In the JGRError.log it continues to add the same lines. See the file  attached herewith. 

Someone can help me? Thank's a lot. Silvio 
[/FONT]
>> 15:43

[FONT=-moz-fixed]I found this[FONT=Verdana]:[/FONT][/FONT]
[http://www.mail-archive.com/r-sig-debian@r-project.org/msg00779.html](http://www.mail-archive.com/r-sig-debian@r-project.org/msg00779.html)

*Help > About* solve the problem.

---

### Post by IeU on 2010-10-24
I managed to install everything, but when i try to run JGR, i get this:

```
> library(JGR)
Loading required package: rJava
Loading required package: JavaGD
Loading required package: iplots

Please use the corresponding JGR launcher to start JGR.
Run JGR() for details. You can also use JGR(update=TRUE) to update JGR.

> JGR()
Error in .generate.run.script() : 
  JRI is required but missing! Make sure R was configured with --enable-R-shlib and rJava was compiled with JRI support.
> 

```

Please help me out!

Need this for my Statistics classes.

---

