---
title: "WAR files packaged as source DEBs for Tomcat container +/- source from SVN?"
date: 2010-09-27
forum: Packaging and Compiling Programs
---

### Post by misha680 on 2010-09-27
Dear All:

I have researched this quite a bit, and have not found a lot of examples, but it does not hurt to ask.

I am working on packaging OpenMRS ([www.openmrs.org](www.openmrs.org)) for Debian Med and/or Ubuntu.

You can see my current progress/discussion to date here:
[http://old.nabble.com/Correction-to-web-site-information%3A-OpenMRS-has-debian-packages-available-for-download-ts29724635.html](http://old.nabble.com/Correction-to-web-site-information%3A-OpenMRS-has-debian-packages-available-for-download-ts29724635.html)

It seems like there are not a lot of wars packaged as source debs - at least not a lot that I could find (this is versus binary debs that are created via the dpkg-deb command rather than the full debuild or dpkg-buildpackage - sorry if you already knew all this :) ).

In any case, it never hurts to ask...

Any good examples?

Thank you
Misha

---

### Post by misha680 on 2010-09-28
Ok, here is one:

Application -> Accessories -> Terminal, type:
```

cd /tmp
sudo aptitude install openjdk-6-jdk ant debhelper quilt svn-buildpackage devscripts -y
alias svn-b='svn-buildpackage -us -uc -rfakeroot --svn-ignore'
svn checkout svn://cvs.alioth.debian.org/svn/debian-med/trunk/packages/openmrs/trunk
cd trunk
./debian/rules get-orig-source
echo "origDir=.." >> .svn/deb-layout
svn-b

```

You should have the debs built in the folder /tmp/build-area

For more info, see this very helpful Wiki page:
[http://wiki.debian.org/DebianMed](http://wiki.debian.org/DebianMed)

Thank you
Misha

---

### Post by SevenMachines on 2010-09-29
I'm not sure how much war files are used in debian but packaging them in a standard way seems to be a recent 'work-in-progress'. see [http://dep.debian.net/deps/dep7/](http://dep.debian.net/deps/dep7/)

It highlights a few ways people debianise .war stuff. Can't see many examples but
$ apt-file search ".war " shows a few, i dont know if they're worth looking at or not with 'apt-get source', tomcat just copies across a pre-built war archive as far as i can see

> jets3t: /usr/share/jets3t/servlets/gatekeeper/gatekeeper-0.7.3.war 
libsitemesh-java-doc: /usr/share/doc/libsitemesh-java/examples/sitemesh-blank.war 
sun-javadb-core: /usr/share/javadb/lib/derby.war
tomcat6-docs: /usr/share/tomcat6-docs/docs/appdev/sample/sample.war
I know nothing about war archives but theres some distinctively named file they need then you might find a few examples of the 'Install the web application files as an exploded archive' option mentioned in dep7 using apt-file search

---

