---
title: "Creating a Documentation Package"
date: 2010-07-04
forum: Packaging and Compiling Programs
---

### Post by igb on 2010-07-04
I want to create a package that is essentially just documentation for an Emacs package. I am reading the various package guides, but these are really aimed at creating packages for binary apps or libraries.

Is there any tutorial that is more specifically directed towards creating packages for documentation?

Thanks,

Ian.

---

### Post by SevenMachines on 2010-07-05
if you look at the packaging guide, but dont use the cdbs stuff for compiling, ie only use the debhelper stuff
debian/rules:
> #!/usr/bin/make -f
                                
include /usr/share/cdbs/1/rules/debhelper.mkthen look at 'man dh_installdocs'. all you would need is a file called
debian/<mypackagename>.docs:
> somefile.txt
docs/*this automatically installs the files named into the 
/usr/share/doc/<mypackagename> directory

---

### Post by Umang on 2010-07-06
Or use the tiny rules file with dh7 and use the dh_installdocs as mentioned above.
debian/rules:
```
#!/usr/bin/make -f
%:
        dh $@
```
You should also register the documents with doc-base.

[http://www.debian.org/doc/debian-policy/ch-opersys.html#s-doc-base](http://www.debian.org/doc/debian-policy/ch-opersys.html#s-doc-base)
[http://www.debian.org/doc/manuals/maint-guide/ch-dother.en.html#s-doc-base](http://www.debian.org/doc/manuals/maint-guide/ch-dother.en.html#s-doc-base)

---

### Post by igb on 2010-07-07
Thanks both, that is very helpful.

Ian.

---

