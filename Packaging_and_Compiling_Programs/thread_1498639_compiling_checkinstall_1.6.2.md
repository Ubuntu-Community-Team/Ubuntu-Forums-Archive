---
title: "compiling checkinstall 1.6.2"
date: 2010-06-01
forum: Packaging and Compiling Programs
---

### Post by PGScooter on 2010-06-01
I would like to install the newest checkinstall 1.6.2. I downloaded it from here [http://www.asic-linux.com.mx/~izto/checkinstall/](http://www.asic-linux.com.mx/~izto/checkinstall/)

I've searched a lot and have found that others came up with a similar error and I saw no solution.

I'm on Ubuntu 64-bit 10.04.

```

jeremy:~/source-builds/checkinstall-1.6.2$ make
for file in locale/checkinstall-*.po ; do \
		case ${file} in \
			locale/checkinstall-template.po)  ;; \
			*) \
				out=`echo $file | sed -s 's/po/mo/'` ; \
				msgfmt -o ${out} ${file} ; \
				if [ $? != 0 ] ; then \
					exit 1 ; \
				fi ; \
			;; \
		esac ; \
	done	
make -C installwatch
make[1]: Entering directory `/home/scott/source-builds/checkinstall-1.6.2/installwatch'
gcc -Wall -c -D_GNU_SOURCE -DPIC -fPIC -D_REENTRANT -DVERSION=\"0.7.0beta7\" installwatch.c
installwatch.c:2942: error: conflicting types for &#8216;readlink&#8217;
/usr/include/unistd.h:825: note: previous declaration of &#8216;readlink&#8217; was here
installwatch.c:3080: error: conflicting types for &#8216;scandir&#8217;
/usr/include/dirent.h:252: note: previous declaration of &#8216;scandir&#8217; was here
installwatch.c:3692: error: conflicting types for &#8216;scandir64&#8217;
/usr/include/dirent.h:275: note: previous declaration of &#8216;scandir64&#8217; was here
make[1]: *** [installwatch.o] Error 1
make[1]: Leaving directory `/home/scott/source-builds/checkinstall-1.6.2/installwatch'
make: *** [all] Error 2
jeremy:~/source-builds/checkinstall-1.6.2$ 

```

any ideas?

Thanks

---

### Post by SevenMachines on 2010-06-01
hi, 2 problems. 

* scandir and scandir64 headers have changes in later glibc's (>2.9-10? xsomething like that?)
you'd need to replace the bits in installwatch.c where scandir (and true_scandir) is defined. the last argument part has gone from 
(const void *,const void *) -> (const struct             dirent **, const struct dirent             **)
i think the scandir64/true_scandir64 equivalent is now
(const struct             dirent64 **, const struct dirent64             **)

* checkinstall doesnt detect the glibc minor version properly so assumes its 2.1
you would need to edit installwatch/create-localdecls
and add entries for newer versions of glibc, ie after
7)
                        echo '#define GLIBC_MINOR 7' >> $OUTFILE
                        SUBVERSION='glibc-2.7' ;;

you could add entries replacing 7 with 10, 11 , etc

or just remove the #if (GLIBC_MINOR <= 4) ->#endif entries in the code

All that said you might be better just getting the package source from maverick,
[https://launchpad.net/ubuntu/maverick/+source/checkinstall](https://launchpad.net/ubuntu/maverick/+source/checkinstall)
 it has all these patches included, perhaps the version in lucid does too, i dont know

---

### Post by PGScooter on 2010-06-01
Thanks SevenMachines, I will remember to check Maverick in the future.

I downloaded and extracted these two files:
checkinstall_1.6.2-1.debian.tar.gz
checkinstall_1.6.2.orig.tar.gz
but I am unsure what to do now. Do I just have to apply the patches? How do I do that? What does the rules script do?

I am learning a lot from this experience, thanks!

---

### Post by SevenMachines on 2010-06-01
hi, although you could probably just use the pre-built deb files from the link above, if you want to build your own from the source....

1. Download the 3 files below, no need to extract them
[checkinstall_1.6.2-1.dsc]("https://launchpad.net/ubuntu/maverick/+source/checkinstall/1.6.2-1/+files/checkinstall_1.6.2-1.dsc") 
checkinstall_1.6.2-1.debian.tar.gz
checkinstall_1.6.2.orig.tar.gz

2. then use dpkg-source to extract them, this automatically applies the packaging and such
$ dpkg-source -x checkinstall_1.6.2-1.dsc

3. get any missing build dependencies
$ sudo apt-get build-dep checkinstall

4. now build the binary packages (the necessary patches in debian/patches will be automatically applied by debuild)
$ cd checkinstall-1.6.2/
$ debuild -b -us -uc

All being well you should now have the binary debs built in the parent directory ( cd .. )

---

### Post by SevenMachines on 2010-06-01
just to add a couple of quick links, an explanation to the rules file can be found [here]("https://wiki.ubuntu.com/PackagingGuide/Complete#rules") as part of the very useful [URL="https://wiki.ubuntu.com/PackagingGuide/Complete"]Ubuntu Packaging Guide
[/URL]

---

### Post by PGScooter on 2010-06-02
Thank you SevenMachines!!! I have learned a lot from going through this. Your instructions worked perfectly. I've been reading the Packaging Guide. I am making progress, but still have a long way to go. Thanks!

---

### Post by SevenMachines on 2010-06-02
Its a good guide, stick with it! theres also the [debian new maintainers guide]("http://www.debian.org/doc/maint-guide/"), its less of a tutorial and more of a reference but you might want to look at some of it once you're comfortable with the stuff in the ubuntu packaging guide. And of course feel free to ask any questions here, someone around will give it a stab i'm sure :)

---

### Post by PGScooter on 2010-06-02
great, thanks for the other guide and encouragement.

---

