---
title: "Integrating KDevelop w/ gcc and g++"
date: 2007-04-01
forum: Programming Talk
---

### Post by se2131 on 2007-04-01
I recently installed KDevelop because I saw a number of recommendations for it as far as an IDE goes.  However, after installing, I realized that there is no clear way to compile the programs (C++).  Is there a way to integrate gcc and g++ into the IDE so that I can run it all from KDevelop, and don't have to use the terminal?

Thanks in advance

---

### Post by cold_fu5ion on 2007-04-02
I'm also looking for an answer to this problem, possibly I have automake and auto configure installed wrong but I can't seem to be able to compile and run any programs using any IDE in Ubuntu. 

I wrote a simple hello world program using KDevelop but I can't work out how to compile  0_o

---

### Post by Asix on 2007-04-02
Have you installed build-essential package before deploying KDevelop? Similiar situation happened to me a year ago and I fixed it by installing this package. It doesn't matter if KDevelop is already installed, as long as you have build-essential package installed, it should work... Also, look if you have all KDE and Qt related development packages and libraries installed on your system, that caused me lots of problems and frustrations in the past, too... Good luck.

---

### Post by se2131 on 2007-04-02
I have build-essential installed already, so that's not it unfortunately.

As for the KDE and QT development packages, which ones should I install?  There seem to be a lot of choices, so should I just go ahead and install them all (e.g. qt4-dev-tools, qt3-dev-tools, kde-devel, kde-devel-extras, etc. etc)

Thanks

---

### Post by cold_fu5ion on 2007-04-04
I've also installed build-essentials so its not that.
This is really annoying me, I don't want to have to dual boot just to write some c programs for uni.

---

### Post by se2131 on 2007-04-04
To cold_fu5ion:

There's no need to dual boot, even though we can't get the IDE to compile, you can still use gcc or g++ (I think one works in some situations, and the other works in others) to compile your .c file.  It's temporary, but at least it prevents you from the major hassle of dual booting when it's not necessary.

g++ myprogram.c --> creates an a.out file which you can execute (you can also name it something else w/ the -o option)

---

### Post by GeneralZod on 2007-04-04
> **se2131 said:**
> I recently installed KDevelop because I saw a number of recommendations for it as far as an IDE goes.  However, after installing, I realized that there is no clear way to compile the programs (C++).  Is there a way to integrate gcc and g++ into the IDE so that I can run it all from KDevelop, and don't have to use the terminal?


Of course - otherwise, it wouldn't be an *I*DE ;)

What version of KDevelop do you have, what have you tried so far, and what problems are you having?

---

### Post by cold_fu5ion on 2007-04-04
Thanks for the terminal commands :-)
Im using KDev version 3.5.5. I just can't work out how to compile, I read a guide that said ............. "From the build menu; choose ‘Run automake and friends’. After this is successfull; run ‘Build->Run Configure’. Now your project is ready to ‘Build’. Choose ‘Build->Build Project’ and then you can execute it by doing ‘Build->Execute Program’. Congrats! You have just built your first KDE application."

When I click on build the only thing is a greyed out stop button, there just is nothing else in that menu.

---

### Post by GeneralZod on 2007-04-04
> **cold_fu5ion said:**
> Thanks for the terminal commands :-)
Im using KDev version 3.5.5. I just can't work out how to compile, I read a guide that said ............. "From the build menu; choose ‘Run automake and friends’. After this is successfull; run ‘Build->Run Configure’. Now your project is ready to ‘Build’. Choose ‘Build->Build Project’ and then you can execute it by doing ‘Build->Execute Program’. Congrats! You have just built your first KDE application."

When I click on build the only thing is a greyed out stop button, there just is nothing else in that menu.

I'm pretty sure 3.4.0 is the latest stable release of kdevelop ;) 

What version of (K)Ubuntu are you using? I'll see if I can try this out in a blank VM when I get home tonight.  I seem to recall that the "Automake and Friends" always ends with an error or a warning on a stock (K)Ubuntu install, which is why the build cycle is failing, but can't recall offhand what the fix was.

---

### Post by se2131 on 2007-04-04
I'm using KDevelop version 3.3.4, w/ KDE version 3.5.5.  I just installed it a few days ago, so I think that it's the latest version (I think cold_fu5ion was referring to his KDE version).  I'm running this on Ubuntu 6.10

I also only have the greyed out "Stop" item under the Build menu.


Thanks for looking into this, hopefully we can get this to work

---

### Post by GeneralZod on 2007-04-05
> **se2131 said:**
> I'm using KDevelop version 3.3.4, w/ KDE version 3.5.5.  I just installed it a few days ago, so I think that it's the latest version (I think cold_fu5ion was referring to his KDE version).  I'm running this on Ubuntu 6.10

I also only have the greyed out "Stop" item under the Build menu.


Thanks for looking into this, hopefully we can get this to work


Ok, I had a blank Kubuntu 6.10 .img lying around, and got it all to work.

The steps were roughly this (I'm going from memory, here):

```

sudo apt-get install build-essential automake1.7 autoconf libtool

```

Start up KDevelop.

I went with a KDE project (New Project -> C++ -> KDE -> Simple KDE application -> Give it a name and a place) so had to install the KDE headers, etc (this is pretty easy).

Once I've gone though the Wizard successfully, do Build -> Build Project.  It should complain about having no Makefile, and offer to run "Automake and Friends" - do this.  When it completes successfully, you should be able to run/ debug your project.

In 3.4, you can set breakpoints  by clicking in the margin to the left of the text area, but I'm not sure if this feature is in 3.3.4; you can toggle breakpoints from the right-click menu, or the Debug menu.  You might want a keyboard shortcut for this.

When your breakpoints are set, Debug ->Start.

Any problems, let me know :)

---

### Post by cold_fu5ion on 2007-04-05
Fantastic! Thats solved the problem. 
I'm not sure if it was the packages that I was missing or that I wasn't going though the wizard to make a project (I was just clicking new file) in KDevelop, but it works great now.

Thanks for all the help :-) Hopefuly se2131 has the same result as me.

---

### Post by se2131 on 2007-04-05
oh wow, so that was the problem: I guess I need to create the project, instead of just writing the .c file and trying to compile it.

Thanks for the help, it's been much appreciated

---

### Post by GeneralZod on 2007-04-05
Great; glad it worked out for you both :)

---

