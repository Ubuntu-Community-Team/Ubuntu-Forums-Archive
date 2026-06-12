---
title: "How UBuntu installation process works - Does it download and install automatically?"
date: 2012-12-19
forum: New to Ubuntu
---

### Post by bs19 on 2012-12-19
I just started migrating from Windows to Ubuntu 10.04
I have big question regarding installing new softwares.
--
I want to install a software "ABC12" which is on the web (Let us assume it is Ubuntu version).

What are the ways to install - I am very confused.

1. By typing - sudo apt-get install ABC12.
What will happen - Will Ubuntu search in the whole WWW and -  i)  Download  and  - ii).Install ???


2. What is the use of Ubuntu Software Center? Can I install the above ABC12 using this tool?

3. When I type 'sudo apt-get install SOME SOFTWARE NAME', I see message like "Could not find package  SOME SOFTWARE NAME'". 

What is package ? A software already COPIED (Ubuntu has the EXE / dump) on this machine???

4. I know apt stands for Advanced Packaging Tool . What does this do exactly?

5. How does Ubuntu knows if a new software is released in to the Web (and it has Ubuntu version)

Regards,
BS19

---

### Post by offgridguy on 2012-12-19
Just another thought here, have you considered ubuntu 12.04 which is a newer version
and has long term support?
  The software center is a great tool, essentially a catalog of available software for
ubuntu.
       You can use the search bar in the software center if you know the name of what you are looking for.

You can use the update manager to see what new software or updates are available.

---

### Post by Wim Sturkenboom on 2012-12-19
Ubuntu uses a so-called repositories that are located on the web. Any packages that Ubuntu made available for Ubuntu are in those repositories. When you run apt-get or synaptic or software center, it will look in those repositories (not the whole web). Synaptic and software center are GUI versions of apt-get; it does not matter which one you use (but on a server there's usually no GUI); there are two other commandline programs, dpkg and one of which I've forgotten the name; apt-get however seems to be the most used.

'apt-get' (as well as the other repository tools mentioned above) downloads the software from the repositories on the web, installs it and applies a default configuration.

Note that Ubuntu does not necessarily has the latest versions of software in the repositories. If Firefox e.g. goes to version 18, you might be stuck with version 17; as long as security patches are made available by firefox for version 17, Ubuntu will provide theme well (a little later).

I think this basically addresses all questions except for '3' to which I don't have an answer.

I also suggest to use 12.04 instead of 10.04; 10.04 for the desktop reaches end-of-life in april 2013 after which you have to upgrade; 12.04 is supported till april 2017.
The server version of 10.04 is supported till april 2015; if you're after a server, that will still be fine.

---

### Post by arpanaut on 2012-12-20
> 3. When I type 'sudo apt-get install SOME SOFTWARE NAME', I see message like "Could not find package  SOME SOFTWARE NAME'". That means that the software is not available in the repositories that you have enabled for your installation.  The package may be available through a PPA, or from other sources from the web, but not by default.

[https://help.ubuntu.com/community/InstallingSoftware](https://help.ubuntu.com/community/InstallingSoftware)

---

### Post by oldfred on 2012-12-20
The repositories are maintained by Ubuntu and the software will work with Ubuntu. As a new user you should only install software from the repository.

If using the command line you have to know the exact name of the package or software. Package name may not be the common name or even the name it shows in the applications menu, but usually is related.

Alternatives are Software Center or Synaptic and synaptic is not now included by default. Synaptic package name is synaptic.
```
sudo apt-get install synaptic
```

Software Center will give you the applications with some search on similar names. Synaptic gives a bit more detail but is a bit harder to work with.

Alternative ways to install include downloading a .deb which is software compiled for Debian and usually works with Ubuntu. Similar to an .exe in Windows.
Or you can download software that needs compiling. Usually not required and may have issues of supporting packages missing which you have to resolve.

       Linux alternatives to windows apps
[http://www.osalt.com/](http://www.osalt.com/)
[http://www.linuxappfinder.com/](http://www.linuxappfinder.com/)
[http://www.linuxalt.com/](http://www.linuxalt.com/)

---

### Post by Wim Sturkenboom on 2012-12-20
Just saw that I forgot to mention that 10.04 does not provide 'software center'; it has earlier mentioned 'synaptic' instead.

And to answer what a package is (I also seem to have forgotten that :():
It contains the software (e.g. firefox) plus everything that is needed for it to be configured and run. It will also indicate possible other packages that are required by this software and those will also be installed (if not installed yet).

---

### Post by zombifier25 on 2012-12-20
> **Wim Sturkenboom said:**
> Just saw that I forgot to mention that 10.04 does not provide 'software center'; it has earlier mentioned 'synaptic' instead.
10.04 DOES have a Software Center.

---

### Post by Wim Sturkenboom on 2012-12-20
> **zombifier25 said:**
> 10.04 DOES have a Software Center.
Duh? Never seen it ;) And as I don't like changes, I have been using synaptic all the time so did not bother to look for it.

Thanks for the correction.

---

### Post by bs19 on 2012-12-21
Thanks for everyone for your help and your time!
I learned good points from your answers.

Best Regards,
Suresh

---

