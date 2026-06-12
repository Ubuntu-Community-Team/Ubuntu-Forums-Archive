---
title: "debian/rules install"
date: 2007-07-05
forum: Packaging and Compiling Programs
---

### Post by Hendrixski on 2007-07-05
I made a .deb of my own helloworld program but after I run dpkg -i I can't seem to run the program!  Ideally if i type helloworld into the command prompt I should get my program to pop up. is there some modification I should be making to the debian/rules file.

Also, is there a way to get your programs to appear in the applications-->accessories menu?  Is that done in packaging/install-scripts or in the program itself?

---

### Post by Hendrixski on 2007-07-05
This is the current instal... i assume that there's some voodoo stuff i could add to the part where it says #add commands to install the package
But I'm still kind of new to all of this... and was hoping someone could point me in a direction where I'd understand it better.

```

$ ls
debian  form1.ui  helloworld-0.1.pro  helloworld.cpp  images
[code]

[code]
install: build
        dh_testdir
        dh_testroot
        dh_clean -k 
        dh_installdirs

        # Add here commands to install the package into debian/hellonurse.
        $(MAKE) DESTDIR=$(CURDIR)/debian/hellonurse install

```

---

### Post by Hendrixski on 2007-07-11
I GOT IT!!!!

Ok, so sometimes I go looking around these forums and I see someone post a problem but never the solution, and I get mad... so here I'll post the solution.

Sometimes you need to replace DESTDIR with INSTALL_ROOT, that is for cases not covered by automake... which I guess Qt was one of them.  Don't know when else one may need to do this but it works.


The symptom is that when you run dpkg -i mypackage the package doesn't install... therefor you can't run myprogram from commandline.  Try changing that line in debian/rules and TADA!!!!!!!!!

---

