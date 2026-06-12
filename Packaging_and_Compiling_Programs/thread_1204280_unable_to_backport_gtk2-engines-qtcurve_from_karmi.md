---
title: "unable to backport gtk2-engines-qtcurve from karmic to jaunty"
date: 2009-07-04
forum: Packaging and Compiling Programs
---

### Post by jamadagni on 2009-07-04
I downloaded the source files for gtk2-engines-qtcurve (0.65.1-1ubuntu1):

gtk2-engines-qtcurve_0.65.1-1ubuntu1.dsc
gtk2-engines-qtcurve_0.65.1.orig.tar.gz
gtk2-engines-qtcurve_0.65.1-1ubuntu1.diff.gz

from [http://packages.ubuntu.com/source/karmic/gtk2-engines-qtcurve](http://packages.ubuntu.com/source/karmic/gtk2-engines-qtcurve). I have all the dependencies installed:

debhelper
cmake
libgtk2.0-dev 

I did:

dpkg-source -x gtk2-engines-qtcurve_0.65.1-1ubuntu1.dsc
cd gtk2-engines-qtcurve-0.65.1
dpkg-buildpackage -rfakeroot

I got:

dpkg-buildpackage: set CFLAGS to default value: -g -O2                             
dpkg-buildpackage: set CPPFLAGS to default value:                                  
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions          
dpkg-buildpackage: set FFLAGS to default value: -g -O2                             
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2                           
dpkg-buildpackage: source package gtk2-engines-qtcurve                             
dpkg-buildpackage: source version 0.65.1-1ubuntu1                                  
dpkg-buildpackage: source changed by Jonathan Thomas <echidnaman@kubuntu.org>      
dpkg-buildpackage: host architecture i386                                          
 fakeroot debian/rules clean                                                       
dh clean                                                                           
   dh_testdir                                                                      
   dh_auto_clean                                                                   
   dh_clean                                                                        
 dpkg-source -b gtk2-engines-qtcurve-0.65.1                                        
dpkg-source: info: using source format `1.0'                                       
dpkg-source: info: building gtk2-engines-qtcurve using existing gtk2-engines-qtcurve_0.65.1.orig.tar.gz
dpkg-source: info: building gtk2-engines-qtcurve in gtk2-engines-qtcurve_0.65.1-1ubuntu1.diff.gz       
dpkg-source: info: building gtk2-engines-qtcurve in gtk2-engines-qtcurve_0.65.1-1ubuntu1.dsc           
 debian/rules build                                                                                    
dh build                                                                                               
   dh_testdir                                                                                          
   dh_auto_configure                                                                                   
   dh_auto_build                                                                                       
   dh_auto_test                                                                                        
 fakeroot debian/rules binary                                                                          
dh binary                                                                                              
   dh_testroot                                                                                         
   dh_prep                                                                                             
   dh_installdirs                                                                                      
   dh_auto_install                                                                                     
   dh_install                                                                                          
   dh_installdocs                                                                                      
   dh_installchangelogs                                                                                
   dh_installexamples                                                                                  
   dh_installman                                                                                       
   dh_installcatalogs                                                                                  
   dh_installcron                                                                                      
   dh_installdebconf                                                                                   
   dh_installcatalogs                                                                                  
   dh_installemacsen                                                                                   
   dh_installifupdown                                                                                  
   dh_installinfo                                                                                      
   dh_installinit                                                                                      
   dh_installmenu                                                                                      
   dh_installmime                                                                                      
   dh_installmodules                                                                                   
   dh_installlogcheck                                                                                  
   dh_installlogrotate                                                                                 
   dh_installpam                                                                                       
   dh_installppp                                                                                       
   dh_installudev                                                                                      
   dh_installwm                                                                                        
   dh_installxfonts
   dh_lintian
   dh_desktop
   dh_gconf
   dh_icons
   dh_perl
   dh_pysupport
   dh_scrollkeeper
   dh_usrlocal
   dh_link
   dh_compress
   dh_fixperms
   dh_strip
   dh_makeshlibs
   dh_shlibdeps
   dh_installdeb
   dh_gencontrol
dpkg-gencontrol: warning: unknown substitution variable ${misc:Depends}
   dh_md5sums
   dh_builddeb
warning, `debian/gtk2-engines-qtcurve/DEBIAN/control' contains user-defined field `Original-Maintainer'
dpkg-deb: building package `gtk2-engines-qtcurve' in `../gtk2-engines-qtcurve_0.65.1-1ubuntu1_i386.deb'.
dpkg-deb: ignoring 1 warnings about the control file(s)
 signfile gtk2-engines-qtcurve_0.65.1-1ubuntu1.dsc
gpg: skipped "Jonathan Thomas <echidnaman@kubuntu.org>": secret key not available
gpg: [stdin]: clearsign failed: secret key not available

 dpkg-genchanges  >../gtk2-engines-qtcurve_0.65.1-1ubuntu1_i386.changes
dpkg-genchanges: not including original source code in upload
dpkg-buildpackage: binary and diff upload (original source NOT included)
dpkg-buildpackage: warning: Failed to sign .dsc and .changes file

And then when I examine the contents of the archive:

$ dpkg-deb -c ../gtk2-engines-qtcurve_0.65.1-1ubuntu1_i386.deb | grep -v drwx | cut -c50-
/usr/share/doc/gtk2-engines-qtcurve/copyright
/usr/share/doc/gtk2-engines-qtcurve/TODO
/usr/share/doc/gtk2-engines-qtcurve/changelog.Debian.gz
/usr/share/doc/gtk2-engines-qtcurve/README
/usr/share/doc/gtk2-engines-qtcurve/changelog.gz

Comparing with the DEB from Jaunty whose file list shown at [http://packages.ubuntu.com/karmic/i386/gtk2-engines-qtcurve/filelist](http://packages.ubuntu.com/karmic/i386/gtk2-engines-qtcurve/filelist) is:

/usr/lib/gtk-2.0/2.10.0/engines/libqtcurve.so
/usr/share/doc/gtk2-engines-qtcurve/README
/usr/share/doc/gtk2-engines-qtcurve/TODO
/usr/share/doc/gtk2-engines-qtcurve/changelog.Debian.gz
/usr/share/doc/gtk2-engines-qtcurve/changelog.gz
/usr/share/doc/gtk2-engines-qtcurve/copyright
/usr/share/themes/QtCurve/gtk-2.0/gtkrc
/usr/share/themes/QtCurve/gtk-2.0/icons3
/usr/share/themes/QtCurve/gtk-2.0/icons4
/usr/share/themes/QtCurve/gtk-2.0/map_kde_icons.pl
/usr/share/themes/QtCurve/mozilla/QtCurve-KDEButtonOrder.css
/usr/share/themes/QtCurve/mozilla/QtCurve.css
/usr/share/themes/QtCurve/mozilla/preferences-rev.xml

---

