---
title: "Help installing GNU Octave"
date: 2011-12-08
forum: New to Ubuntu
---

### Post by spamanon on 2011-12-08
I downloaded GNU Octave and extracted the files.  I do not understand what the directions are talking about.  Here are the first two steps:


The simplest way to compile this package is:

  1. `cd' to the directory containing the package's source code and type
     `./configure' to configure the package for your system.

     Running `configure' might take a while.  While running, it prints
     some messages telling which features it is checking for.

  2. Type `make' to compile the package.



So, on a Windows system, I would 'cd' using DOS or the Run to get to a command prompt.  But on my brand new Ubuntu installation I do not see anything like this.  How can I get to where I can 'cd' to the location of the files?

Thanks

---

### Post by beew on 2011-12-08
Octave is in the repository. You can choose which tool boxes to install from synaptic or the software center too.

---

### Post by spamanon on 2011-12-08
Thank you beew!

However, what you just said means about as much to me as: "octave sdlfj sdiuoa sdoiua as"

What is a repository?  I already downloaded and extracted the files.  I am trying to follow directions but I guess I need to open a "terminal".  So I did a search and found this:

[https://help.ubuntu.com/community/UsingTheTerminal](https://help.ubuntu.com/community/UsingTheTerminal)

> The easiest way to open the Terminal is to use the 'search' function on the dash.

Which would be even easier if I knew what a dash was!

Man, I am missing Windows already - but I want to learn!

---

### Post by spamanon on 2011-12-08
O.k., so I have gotten a little further along.  I found the dash after looking around on google for 15 minutes.  But now I am stuck again.  It seems that to install octave one must first have gcc and gnu make installed.  So I got gnu make installed but now gcc is NOT so simple to install.

According to the instructions found here:

[http://gcc.gnu.org/install/configure.html](http://gcc.gnu.org/install/configure.html)

I just type:

makedir objdir

then:
[FONT=monospace]
[/FONT]cd objdir

then:
[FONT=monospace]
[/FONT]srcdir/configure

but when I typed makedir objdir I get "No command 'makedir' found"

So what have I done wrong? 

Thanks again.

---

### Post by beew on 2011-12-08
Ok, in Ubuntu (and many other distros as well) installation and update of programs are managed centrally in software repositories so that you don't have to go on random sites to download installers like in Windows. 

In Ubuntu, you can access these repositories through several means : the Software center, Synaptic package manager (you have to install this yourself if you are using Ubuntu 11.10) and the good old command line.  So the repos are like Apple's app store, except all the software is free.

Besides the official repositories maintained by Ubuntu, you can add many ppas (personal program archives, something like that. :)) if you want programs not available from the official repos, or want versions which are more up to date. Since you appear to be quite new I will skip this, you will find out later as you learn more. 

Other than installing through repositories (official or ppas) You can also download installers for some programs to do right click install like in Windows, but they have to have the .deb extension ( or .rpm sometimes, you can convert some rpms to debs with a tool called alien and then install the debs, it may not work sometimes though,  but I will skip that), they are kind of like the .exe files for installation in windows. I would suggest ppas over downloading .debs if ppas are available because once you add a ppa it is managed by the software managing system like programs in the official repos and you will get regular upgrades, whereas sofwtare installed with .deb are static. 

Finally you can compile software from source, which is what you are trying to do here. It is a good learning experience and for bleeding edge features but not necessary for most things.

Ok, now to install from the repositories, you can always go to the Software center and search for the package (say Octave) and then just click. The SC is very nice looking but it is slow and buggy and it doesn't have many options so I would recommend synaptic instead. Like I said, in 11.10 synaptic is not installed by default so you have to install it first. You can do it with the software center, or simply with command line. Open the terminal and type
```

sudo apt-get install synaptic
```Now you have installed synaptic you can find it in the dash. Every time when you start synaptic you should click the "Reload" button to update repo information. The advantage of synaptic over the command line is you can browse applications by categories and install programs even when you don't know the exact names. In synaptic you can find the base octave package and other tool boxes, just click to install whatever you want (see screenshot) If you decide that you don't want some tool boxes later you can just click to uninstall them. It is that simple, no need to compile anything. :) 

Hope that helps.

---

### Post by beew on 2011-12-08
Oh to answer your question, the dash shows the installed programs (if they have a .desktop file)  and if your compile has failed your program wouldn't show up. Also programs that don't have a .desktop file (launcher) will not show up. Octave is a command line application (unless you install a GUI, there is one called qtoctave) so I am not sure if it will show up on the dash even if it compiled and installed successfully. In my dash I have an icon for GNU Octave but I might have created it myself (couldn't remember as I installed it a while back)

---

### Post by spamanon on 2011-12-08
beew,

Thanks so much!  Indeed that does help.  

I installed synaptic, searched for Octave, found it!  I also see that some other stuff was needed, which synaptic marked out for me.  So it is downloading packages right now!  I hope to be able to manage the rest of this on my own, but I truly appreciate your time.  Thanks again!

---

