---
title: "How do you install a tarball?"
date: 2013-07-11
forum: New to Ubuntu
---

### Post by Jonathan Precise on 2013-07-11
Hello!

I have ubuntu 13.04, and there are a large number of programs out there on the internet not included in synaptic. Most of the ones out there come in the form of tarballs (ending in .tar.gz or in tar.bz2). However, I usually have a hard time installing them.

I run the following commands:

```
./configure
make
sudo make install
```

Sometimes they work. Sometimes they don't. Is there any advice?

---

### Post by BreezyBrooke on 2013-07-11
It's usually suggested to never do this. This will cause problems later down the line as this installation method dosen't convey to Apt that it was installed. So at anypoint, apt can corrupt the program by installing a library the tar program provided, but since apt didn't know it's already installed, it will install over it and cause issues. 

Also, installing by tar, usually means you will have to pull dev packages through apt in order to build against something. Like an app for gnome will need gnome-dev packages and will usualy result in hundreds of megabytes of dev packages just to install something that may just be a few megabytes. 

So please, I urge you, stick to apt and synaptic. They know MUCH BETTER than you about your own system and what's installed and what can be removed.

---

### Post by BBQdave on 2013-07-11
> **BreezyBrooke said:**
> So please, I urge you, stick to apt and synaptic.

+1

Trusted repos, trusted packages, sorted - installed - updated by apt. Safe and Secure for you and your system :D

---

### Post by oldos2er on 2013-07-11
> **BreezyBrooke said:**
> It's usually suggested to never do this. This will cause problems later down the line as this installation method dosen't convey to Apt that it was installed. So at anypoint, apt can corrupt the program by installing a library the tar program provided, but since apt didn't know it's already installed, it will install over it and cause issues. 

I think you're overstating the case somewhat; I've compiled quite a few (usually small) programs and have never experienced the issues you're describing here.

Jonathon Precise, can you name some of the programs you don't find in the repositories? There may be PPAs for them, or *.deb files. If you just want to compile for the sake of learning, it's best to post questions in the Packaging & Compiling Programs subforum.

Also see [https://help.ubuntu.com/community/CompilingEasyHowTo](https://help.ubuntu.com/community/CompilingEasyHowTo) and [https://help.ubuntu.com/community/CompilingSoftware](https://help.ubuntu.com/community/CompilingSoftware)

---

### Post by lisati on 2013-07-11
As others have suggested, there's sometimes ways of installing software that makes it easier to use tools based around the *apt* system of installing from repositories.

Another thing to look for is a "read me" file in the extracted archive: these often have additional information that can be helpful if you change your mind and want to remove or change something about the program you've installed.

---

### Post by mc4man on 2013-07-11
> **Jonathan Precise said:**
> Hello!

I have ubuntu 13.04, and there are a large number of programs out there on the internet not included in synaptic. Most of the ones out there come in the form of tarballs (ending in .tar.gz or in tar.bz2). However, I usually have a hard time installing them.

I run the following commands:

```
./configure
make
sudo make install
```

Sometimes they work. Sometimes they don't. Is there any advice?
The 1st.thing you should do after extracting is open the extracted folder & have a look around. Many times there will be a text file or 2 that will provide you with some info. (A file named install or readme will usually be useful.

Not all sources need to built, of those that do not all use ./configure & make,  so again having a look around can make that apparent.

With those that do use a ./configure it's generally best to first run ./configure --help to see what configure options are available, what is enabled by default & what may need to be specially enabled or disabled in the ./ configure line.

In other words there's never any guarantee that "./configure make" will work or if it does produce the most useful of builds.

---

### Post by Paqman on 2013-07-12
> **Jonathan Precise said:**
> However, I usually have a hard time installing them.


Good, tarballs are awful. I avoid them like the plague myself.

One of Ubuntu's good points is that a lot of software is available in PPAs (Personal Package Archives), where an individual (often the actual developer of the software) has taken the time to package up their code into a nice Ubuntu-friendly format. If something isn't available in the official repos, a third party repo (eg: Google) or as a .deb file then plugging "name-of-app PPA" into a search engine should be your next step. 

Obviously when enabling a PPA on your system you're implicitly trusting the individual who's maintaining it. But you're doing the same when you install a tarball anyway.

---

### Post by su:bhatta on 2013-07-12
Hi, 
if you have gone through the links provided by oldos2er, you have already found out a lot and it should make it easy for you to install tarballs...

Basically, you have to get rid of the dependencies which  once resolved will allow you to 'make' and then 'make install'. Also 'check install' is a more preferred method...

& as for this is not the suggested method, yes it may not be, but sometimes you get tarballs specifically for your use which you cannot get in apt resources, but they don't necessarily give you any problems after installation...

use 'apt-get autoremove' to remove packages downloaded as dependencies once install is done, this will clear up your system partially....

Check the website(from where you got the tarball) for pages like 'documentation', which sometimes list all the dev packages you need for installing the tarball, also as suggested by mc4man, generally a guide is given along with the tarball...

Just ensure that the tarball is genuine, difficult to do, but check if people have used it and given any reviews...
Also, I have found some programs that come with a 'install.sh' file in a zip, those need to be installed using './install.sh'

Enough of my runt, use it cautiously is all i can say....

---

### Post by newb85 on 2013-07-12
First thing you should know is this: a tarball is just a container, and it could have anything in it.  I could send you a tarball containing only a text file detailing what I had for lunch yesterday.  And there would be nothing to install.  A tarball could contain a .deb file, which would not need to be compiled (because it has already been compiled).  Or it could contain the source code, which *would* need to be compiled.

As it has been said, using PPAs is usually better than installing from a tarball.  A couple great sites to search for PPAs:
[www.omgubuntu.co.uk]("http://www.omgubuntu.co.uk")
[www.webupd8.org]("http://www.webupd8.org")


> **bhattabhishek said:**
> Hi, 
Basically, you have to get rid of the dependencies which  once resolved will allow you to 'make' and then 'make install'. Also 'check install' is a more preferred method...


"get rid of the dependencies" is probably not the clearest way of stating this.  What (I think) bhattabhishek is trying to say is that the packages you're trying to install often depend on other packages to work, and when installing from a tarball, you have to manually make sure those dependencies are installed.  (This is one of the advantages of a PPA.)

> **bhattabhishek said:**
> 
use 'apt-get autoremove' to remove packages downloaded as dependencies once install is done, this will clear up your system partially....
I don't know what they're trying to say here.  If packages are dependencies of the package you want to install, then you don't want to uninstall them.

---

### Post by Zill on 2013-07-12
> **Jonathan Precise said:**
> ...Sometimes they work. Sometimes they don't. Is there any advice?
Welcome to "[Dependency hell]("http://en.wikipedia.org/wiki/Dependency_hell")".  I suggest you read this: "[Installing Software in Ubuntu]("http://www.psychocats.net/ubuntu/installingsoftware")"

---

### Post by su:bhatta on 2013-07-12
> **newb85 said:**
> 


I don't know what they're trying to say here.  If packages are dependencies of the package you want to install, then you don't want to uninstall them.

Hey ! Thanks for pointing out, my bad.

'sudo apt-get autoremove ' is used to remove packages that were automatically installed to satisfy  dependencies for some package and that are no more needed.

I should have made that clear, in the first place.

---

