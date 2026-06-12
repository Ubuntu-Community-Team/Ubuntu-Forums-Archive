---
title: "How do I install programs"
date: 2008-08-03
forum: New to Ubuntu
---

### Post by xcvcx on 2008-08-03
I've previously used Linux but failed using so I went back to Windows. Once again, I come back to Linux because there is something about it that I love. Anyways my question


How would I go by installing a

tar.gz, rpm or any other type of file? Do I have to open the terminal and type install "  "?

---

### Post by perlluver on 2008-08-03
> **xcvcx said:**
> I've previously used Linux but failed using so I went back to Windows. Once again, I come back to Linux because there is something about it that I love. Anyways my question


How would I go by installing a

tar.gz, rpm or any other type of file? Do I have to open the terminal and type install "  "?

Please read How to install anything in Ubuntu in my signature.  That should explain it better.

---

### Post by tdcdodger on 2008-08-03
In linux, I have always seen program installs referred to as packages. There are two systems of Package management (basically two different ways to install programs): 

1) RPM package based (which are those .rpm files) which is used by Red Hat Linux, and Mandrake and others. Ubuntu Does not use this type of package installation

2) Apt-get. Ubuntu is derived from Debian/GNU linux, and it uses the apt-get package manager

So in ubuntu, to install something you do: apt-get install <packagename>

Its really pretty cool, it goes to the internet, downloads, and installed the package as well as any dependencies. Google the ubuntu documentation for more information on package names.

Now for those .tar files, those are just like .zip or .rar in windows. Those can be extracted using the tar command. Here is a link to more info on how to use TAR:

[http://www.cs.duke.edu/~ola/courses/programming/tar.html]("http://www.cs.duke.edu/~ola/courses/programming/tar.html")

---

### Post by wdaniels on 2008-08-03
Ubuntu is a Debian-based Linux distribution so the preferred method is to use .deb package files (the Debian version of .rpm), many of which can be downloaded and installed automatically through package management systems like Synaptic (in the menu System->Administration->Synaptic Package Manager or Applications->Add/Remove...) or on the command line using the "apt-get" or "aptitude" commands.

It would be a good idea for you to read through the [community documentation page for installing software]("https://help.ubuntu.com/community/InstallingSoftware").

---

