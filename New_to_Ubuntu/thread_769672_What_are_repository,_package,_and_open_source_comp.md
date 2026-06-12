---
title: "What are repository, package, and open source compiling, library, etc.?"
date: 2008-04-26
forum: New to Ubuntu
---

### Post by puifais on 2008-04-26
So I get the idea that when I select an application to be added to my Ubuntu, the computer downloads "something" onto my computer and make it work automatically.  So what exactly is downloaded?  Is it the library, the package, the source code, etc.?  What are the stuff being downloaded externally and what are the existing stuff that my OS already has that's being used?  What is the "thing" that make these downloaded information works as an application on my computer?  I'm guessing it's some sort of compiler but I don't know if that's what it's called because the only time I have to do with a compiler is when I work on my assignment in CS101 (C++) class :)

---

### Post by frup on 2008-04-26
When using the repositories are .deb file is downloaded and any other required dependencies which are in .deb files too. These .deb files have default configurations and are then installed. I think dpkg is the system which handles this.

Source is available in the repos but installations are done via binaries. A distribution like Gentoo installs from source all the time.

To install from source on Ubuntu you need to install the build-essential package first which have the required compilers and libraries etc.

---

### Post by LaRoza on 2008-04-26
> **puifais said:**
> So I get the idea that when I select an application to be added to my Ubuntu, the computer downloads "something" onto my computer and make it work automatically.  So what exactly is downloaded?  Is it the library, the package, the source code, etc.?  What are the stuff being downloaded externally and what are the existing stuff that my OS already has that's being used?  What is the "thing" that make these downloaded information works as an application on my computer?  I'm guessing it's some sort of compiler but I don't know if that's what it's called because the only time I have to do with a compiler is when I work on my assignment in CS101 (C++) class :)

Windows uses .msi or .exe installers. Ubuntu uses .deb (other formats exist, but Debian based distros use .deb)

You can download a bunch of them here: [http://www.getdeb.net/](http://www.getdeb.net/) [http://www.opera.com](http://www.opera.com) has a .deb for Ubuntu and installers for other OS's.

This is what is downloaded. A repository is just a collection of .debs and source code archives. The package manager has a list of what is available. It just downloads and installs them and finds other files needed to work.

You can add or remove repositories also. Remember, only use sources you trust.

You can get the source code, but normally this is not downloaded.

---

