---
title: "dpkg-buildpackage error"
date: 2009-03-09
forum: Packaging and Compiling Programs
---

### Post by woodenbrick on 2009-03-09
I'm trying to create a .deb package from some python source code using the guide [here.]("http://showmedo.com/videos/video?name=linuxJensMakingDeb") I keep getting an error: must specify package since control info has many ()

I included the whole output in case it is of use finding the problem.  Attached my control file as well, since it gave warnings about it.
```

dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value: 
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
dpkg-buildpackage: source package mtp-lastfm
dpkg-buildpackage: source version 0.5-1
dpkg-buildpackage: source changed by Daniel Woodhouse <wodemoneke@gmail.com>
dpkg-buildpackage: host architecture i386
 debian/rules clean
dh_testdir
dh_testroot
rm -f build-stamp configure-stamp
dh_clean 
 dpkg-source -b mtp-lastfm-0.5
dpkg-source: warning: unknown information field 'Package' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Version' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Architecture' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Installed-Size' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Depends' in input data in general section of control info file
dpkg-source: warning: unknown information field 'Description' in input data in general section of control info file
dpkg-source: info: using source format `1.0'
dpkg-source: info: building mtp-lastfm in mtp-lastfm_0.5-1.tar.gz
dpkg-source: info: building mtp-lastfm in mtp-lastfm_0.5-1.dsc
dpkg-source: warning: missing information for output field Architecture
dpkg-source: warning: missing information for output field Standards-Version
 debian/rules build
dh_testdir
# Add here commands to configure the package.
touch configure-stamp
dh_testdir
touch build-stamp
 debian/rules binary
dh_testdir
dh_testroot
dh_clean -k 
dh_installdirs
#install for python progs	
mkdir -p /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm
mkdir -p /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp COPYING /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp dbClass.py /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp logger.py /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp mtp-lastfm-gtk /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp scrobbler.py /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp songdata.py /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp songview.py /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp webservices.py /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp mtp-lastfm.png /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
cp -r glade/ /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/mtp-lastfm
mkdir -p /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/applications
cp mtp-lastfm.desktop /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/applications
mkdir -p /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/doc/mtp-lastfm
cp README.textile /home/wode/programming/current/builds/mtp-lastfm-0.5/debian/mtp-lastfm/usr/share/doc/mtp-lastfm
dh_testdir
dh_testroot
dh_installchangelogs 
dh_installdocs
dh_installexamples
dh_installman
dh_link
dh_strip
dh_compress
dh_fixperms
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: must specify package since control info has many ()
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
dpkg-buildpackage: failure: debian/rules binary gave error exit status 2

```

---

### Post by InfinityCircuit on 2009-03-09
That control file is rather strange.

The canonical description lists the source package first, followed by the binary name. You shouldn't have installed-size or version or any of those in the control file.

I don't maintain any python packages but you can see the basic structure for some other packages I maintain here:

[http://git.debian.org/?p=collab-maint/ypsilon.git;a=blob;f=debian/control;h=13ab8fe7ca9e22b275af64f15cee3b6451f5700c;hb=HEAD](http://git.debian.org/?p=collab-maint/ypsilon.git;a=blob;f=debian/control;h=13ab8fe7ca9e22b275af64f15cee3b6451f5700c;hb=HEAD)

[http://git.debian.org/?p=collab-maint/pekwm.git;a=blob;f=debian/control;h=ef81daeee986399d5056304ad6395f0606afaf57;hb=HEAD](http://git.debian.org/?p=collab-maint/pekwm.git;a=blob;f=debian/control;h=ef81daeee986399d5056304ad6395f0606afaf57;hb=HEAD)

dpkg-source gives you those warnings precisely because your control file should include none of that.

Also, that guide has some errors. You should use "dh_install" to install files if there is no file renaming involved. You should use a debian/dirs file to create directories, not mkdir -p.

---

### Post by woodenbrick on 2009-03-10
Great thanks for your help, I have a working deb file now.

I got confused with the control file because I opened one up and used that as a basis for mine, but I see that it gets changed in the build process.

---

### Post by InfinityCircuit on 2009-03-10
I think you were confusing the output of apt-cache policy with the control file.

Control files that are changed during the build process (not control.in files used in some packages though) are rejected from the Debian (and by proxy) Ubuntu archives.

[http://ftp-master.debian.org/REJECT-FAQ.html](http://ftp-master.debian.org/REJECT-FAQ.html)

[http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=311724](http://bugs.debian.org/cgi-bin/bugreport.cgi?bug=311724)

---

