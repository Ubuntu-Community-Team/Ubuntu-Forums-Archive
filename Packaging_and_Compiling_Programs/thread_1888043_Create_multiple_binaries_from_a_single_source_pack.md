---
title: "Create multiple binaries from a single source package"
date: 2011-11-28
forum: Packaging and Compiling Programs
---

### Post by djsephiroth on 2011-11-28
Trying to create two binary packages from a single source package. The source includes both a driver for a device and several tools for the device. I want to separate the driver and tools into two separate .deb files (foo-driver and foo-admin). 

I have gone over the instructions in the Packaging Guide, and followed it to the letter.
[https://wiki.ubuntu.com/PackagingGuide/Complete#PackagingGuide.2BAC8-Howtos.2BAC8-Advanced.Creating_More_Than_One_Binary_Package](https://wiki.ubuntu.com/PackagingGuide/Complete#PackagingGuide.2BAC8-Howtos.2BAC8-Advanced.Creating_More_Than_One_Binary_Package)

However, I get this error when running dpkg-buildpackage:
```
make[1]: Leaving directory `/usr/src/derp/foo-4.28'
   dh_install
dh_install: foo-driver missing files (lib/*), aborting
make: *** [binary] Error 2
dpkg-buildpackage: error: debian/rules binary gave error exit status 2

```

---

### Post by Bachstelze on 2011-11-28
It would help if you gave us the source packagage (.orig.tar.gz, .debian.tar.gz and .dsc).

---

### Post by djsephiroth on 2011-11-28
The source is not debianized. It can be found at
[ftp://ftp.comtrol.com/dev_mstr/rts/drivers/linux/devicemaster-linux-4.28.tar.gz](ftp://ftp.comtrol.com/dev_mstr/rts/drivers/linux/devicemaster-linux-4.28.tar.gz)

I have debianized it. Please let me know of any relevant files and their contents that I should post.

However, I believe that the issue lies in my following the instructions here:
[https://wiki.ubuntu.com/PackagingGuide/Complete#PackagingGuide.2BAC8-Howtos.2BAC8-Advanced.Creating_More_Than_One_Binary_Package](https://wiki.ubuntu.com/PackagingGuide/Complete#PackagingGuide.2BAC8-Howtos.2BAC8-Advanced.Creating_More_Than_One_Binary_Package)
... and in looking at how already-debianized packages are set up.

In my foopackage1.install, for example, I have
```

/usr/* usr/
/etc/*.bin etc/

```

What am I doing incorrectly here?

---

### Post by SevenMachines on 2011-11-28
If you can just post the debian/ directory that makes it a lot easier to see the problems

---

### Post by djsephiroth on 2011-11-28
changelog  
control    
nslink-admin.debhelper.log  
nslink-driver.debhelper.log  
rules
compat     
copyright  
nslink-admin.install       
nslink-driver.install        
source/

---

### Post by SevenMachines on 2011-11-28
In the sense of a zipped archive of the actual debian directory that you're using with the source you've linked to above

---

### Post by djsephiroth on 2011-11-29
debian dir attached.

---

### Post by SevenMachines on 2011-11-29
You've got quite a complicated package there. The Makefile crams quite a lot into the install rule. If you want to use debhelper in debian rules then you're going to need to override dh_auto_install and do some sort of fixed up equivalent of the sources own install rule does, which will be fairly complicated but, you can add a rule to debian/rules
```

override_dh_auto_install:
    # Do some install things in here instead of relying on 'make install'
```You could also create a nslink-dkms package in debian/control and have dh_dkms install the driver source and a dkms.conf file, allowing for proper external kernel module building. But thats yet more work!

---

### Post by djsephiroth on 2011-11-30
What is "proper external kernel module building"?

How should I go about separating the kernel module stuff from the tools and/or the daemon? Would I mess with the Makefile/rules, or would I do something else after everything is compiled?

Also, any reason not to just rip stunnel out of the Makefile and have the rest of the package depend on stunnel (and thus get it from the Ubuntu repo)?

---

### Post by SevenMachines on 2011-11-30
I meant using dh_dkms so that you install the driver source code and have it automatically rebuilt on each kernel. Generally something like..
* add a nslink-dkms package to debian/control
* add a debian/nslink-dkms.dkms as your dkms.conf equivalent
* probably(?) add a debian/nslink-dkms.install to install driver source
As I say, theres a lot of work in packaging this particular source, thats just one aspect. Theres firmware in there and init.d stuff. You might be as well ditching debhelper altogether and building a custom debian/rules instead. Either way it seems like a lot of work to me.

---

### Post by djsephiroth on 2011-11-30
Thanks for the explanations; my path seems much more clear now. Thank you for bearing with my ignorance, as I seem to have taken on a difficult project as my first foray into packaging. 

The amount of effort involved is no issue - if it's not an "if", but a "when", I shall declare it a satisfactory situation.

I'll read up on dh_dkms. Thanks for pointing me in that direction.

For my own edification: is this source exceptionally klugey or complicated; or is this sort of thing (e.g., stunnel in the Makefile, putting the tools and kernel module and daemon in one package) not uncommon?

Regarding debian/rules and Makefiles, would it be best - not just in this case, but generally - to have multiple Makefiles, or to have a single Makefile that creates binaries that will end up in separate packages?

---

### Post by SevenMachines on 2011-12-01
> For my own edification: is this source exceptionally klugey or  complicated; or is this sort of thing (e.g., stunnel in the Makefile,  putting the tools and kernel module and daemon in one package) not  uncommon?It's a more complicated thing to package than many due to it just using a bare Makefile instead of something like autotools, and kernel drivers. The only obvious problematic area to me is the install section of the makefile though, which you can override as mentioned above. dh_dkms seems like the obvious solution to me for the driver. Theres also dh_installinit which I imagine would be useful for the rc.d stuff in there. Theres a dh_ version for most things,
```
$ man -k dh_
dh_apparmor (1)      - reload AppArmor profile and create local include
dh_apport (1)        - install apport package hooks
dh_auto_build (1)    - automatically builds a package
dh_auto_clean (1)    - automatically cleans up after a build
dh_auto_configure (1) - automatically configure a package prior to building
dh_auto_install (1)  - automatically runs make install or similar
dh_auto_test (1)     - automatically runs a package's test suites
dh_autoreconf (1)    - Call autoreconf - f - i and keep track of the changed files.
dh_autoreconf_clean (1) - Clean all changes made by dh_autoreconf
dh_autotools-dev_restoreconfig (1) - restore config.sub and config.guess
dh_autotools-dev_updateconfig (1) - update config.sub and config.guess
dh_bash-completion (1) - install bash completions for package
dh_bugfiles (1)      - install bug reporting customization files into package build directories
dh_builddeb (1)      - build Debian binary packages
dh_clean (1)         - clean up package build directories
dh_clideps (1)       - calculates CLI (.NET) dependencies
dh_clifixperms (1)   - fix permissions of files in CLI package build directories
dh_cligacpolicy (1)  - creates and installs a CLI policy file for a package
dh_clistrip (1)      - strips CLI debug symbols from package build directories
dh_compress (1)      - compress files and fix symlinks in package build directories
dh_desktop (1)       - deprecated no-op
dh_dkms (1)          - correctly handle DKMS usage by a kernel module package
dh_fixperms (1)      - fix permissions of files in package build directories
dh_gconf (1)         - install GConf defaults files and register schemas
dh_gencontrol (1)    - generate and install control file
dh_girepository (1)  - compute dependencies for GObject introspection packages
dh_gnome (1)         - tools for the Debian GNOME Packaging Team
dh_gnome_clean (1)   - tools for the Debian GNOME Packaging Team
dh_gtkmodules (1)    - create Gtk module files for Gtk modules
dh_icons (1)         - Update Freedesktop icon caches
dh_install (1)       - install files into package build directories
dh_installcatalogs (1) - install and register SGML Catalogs
dh_installchangelogs (1) - install changelogs into package build directories
dh_installcligac (1) - register assemblies to be late installed into a GAC
dh_installcron (1)   - install cron scripts into etc/cron.*
dh_installdeb (1)    - install files into the DEBIAN directory
dh_installdebconf (1) - install files used by debconf in package build directories
dh_installdefoma (1) - install a defoma related scripts
dh_installdirs (1)   - create subdirectories in package build directories
dh_installdocs (1)   - install documentation into package build directories
dh_installemacsen (1) - register an Emacs add on package
dh_installexamples (1) - install example files into package build directories
dh_installgsettings (1) - install GSettings overrides and set dependencies
dh_installifupdown (1) - install if-up and if-down hooks
dh_installinfo (1)   - install info files
dh_installinit (1)   - install upstart jobs or init scripts into package build directories
dh_installlogcheck (1) - install logcheck rulefiles into etc/logcheck/
dh_installlogrotate (1) - install logrotate config files
dh_installman (1)    - install man pages into package build directories
dh_installmanpages (1) - old-style man page installer (deprecated)
dh_installmenu (1)   - install Debian menu files into package build directories
dh_installmime (1)   - install mime files into package build directories
dh_installmodules (1) - register modules with modutils
dh_installpam (1)    - install pam support files
dh_installppp (1)    - install ppp ip-up and ip-down files
dh_installtex (1)    - register Type 1 fonts, hyphenation patterns, or formats with TeX
dh_installudev (1)   - install udev rules files
dh_installwm (1)     - register a window manager
dh_installxfonts (1) - register X fonts
dh_installxmlcatalogs (1) - install and register XML catalog files
dh_link (1)          - create symlinks in package build directories
dh_lintian (1)       - install lintian override files into package build directories
dh_listpackages (1)  - list binary packages debhelper will act on
dh_make (8)          - prepare Debian packaging for an original source archive
dh_makeclilibs (1)   - automatically create clilibs file
dh_makeshlibs (1)    - automatically create shlibs file and call dpkg-gensymbols
dh_md5sums (1)       - generate DEBIAN/md5sums file
dh_movefiles (1)     - move files out of debian/tmp into subpackages
dh_numpy (1)         - adds to python:Depends the Numpy versioned depends
dh_pangomodules (1)  - create a Pango Module file for all Pango modules
dh_perl (1)          - calculates Perl dependencies and cleans up after MakeMaker
dh_perl_dbi (1)      - add dependencies required for DBI modules
dh_prep (1)          - perform cleanups in preparation for building a binary package
dh_pycentral (1)     - use the python-central framework to handle Python modules and extensions
dh_pysupport (1)     - use the python-support framework to handle Python modules
dh_python (1)        - calculates Python dependencies and adds postinst and prerm Python scripts (deprecated)
dh_python2 (1)       - calculates Python dependencies, adds maintainer scripts to byte compile files, etc.
dh_python3 (1)       - calculates Python 3 dependencies, adds maintainer scripts to byte compile files, etc.
dh_quilt_patch (1)   - apply patches listed in debian/patches/series
dh_quilt_unpatch (1) - unapply patches listed in debian/patches/series
dh_rdoc (1)          - generates and installs Ruby documentation
dh_scour (1)         - run scour optimizer on shipped SVG files
dh_scrollkeeper (1)  - deprecated no-op
dh_shlibdeps (1)     - calculate shared library dependencies
dh_sip (1)           - set the correct dependencies for Python packages using sip
dh_strip (1)         - strip executables, shared libraries, and some static libraries
dh_suidregister (1)  - suid registration program (deprecated)
dh_testdir (1)       - test directory before building Debian package
dh_testroot (1)      - ensure that a package is built as root
dh_translations (1)  - perform common translation related operations
dh_ucf (1)           - register configuration files with ucf
dh_undocumented (1)  - undocumented.7 symlink program (deprecated no-op)
dh_usrlocal (1)      - migrate usr/local directories to maintainer scripts

```On the other hand, you might want to do it differently, a look for packages ending -dkms will show you how other people have done similar things,
```
$ apt-cache search -n dkms
dkms - Dynamic Kernel Module Support Framework
open-vm-dkms - Source for VMware guest systems driver (DKMS)
backfire-dkms - kernel module for signal benchmarking (DKMS)
blcr-dkms - DKMS support for BLCR kernel module
dahdi-dkms - DAHDI telephony interface (dkms kernel driver)
iscsitarget-dkms - iSCSI Enterprise Target kernel module source - dkms version
lttng-modules-dkms - Kernel modules for LTTng (DKMS)
ndiswrapper-dkms - Source for the ndiswrapper Linux kernel module (DKMS)
openafs-modules-dkms - AFS distributed filesystem kernel module DKMS source
openswan-modules-dkms - Internet Key Exchange daemon - DKMS source
openvswitch-datapath-dkms - Source code for Open vSwitch datapath Linux module - dkms version
oss4-dkms - Open Sound System - DKMS module sources
tp-smapi-dkms - ThinkPad hardware/firmware access modules source - dkms version
v4l2loopback-dkms - Source for the v4l2loopback driver (DKMS)
virtualbox-dkms - x86 virtualization solution - kernel module sources for dkms
virtualbox-guest-dkms - x86 virtualization solution - guest addition module source for dkms
virtualbox-ose-dkms - transitional package for virtualbox-dkms
virtualbox-ose-guest-dkms - transitional package for virtualbox-guest-dkms
west-chamber-dkms - iptable extension for bypassing content filtering firewall (dkms)
xtables-addons-dkms - Extensions targets and matches for iptables

```Then 
```
$ apt-get source <pkgname>
```to have a look at what they've done, it'll likely be a multiple binary package with the dkms driver being one of them, similar to what you have here.

---

### Post by djsephiroth on 2011-12-01
Thanks, that is exactly what I needed!

---

### Post by djsephiroth on 2011-12-02
I can't seem to find any definitive guides for creating dkms packages from un-debianized source. The ones I have found are either quite rudimentary, out of date, or seemingly conflicting.

Where would be the best sources of information on this topic?

---

### Post by SevenMachines on 2011-12-02
I haven't seen any myself, the best way might be to look at an example. There arent many of them either but the first one I found using dh_dkms is
```
 $ apt-get source backfire-dkms
```
Apart from that you might just need to go for 'man dh_dkms' and 'man dkms'. There isnt too much to do really though...

* add a binary to the debian/control file called <package>-dkms
* add a file debian/<package>-dkms.dkms containing your dkms.conf
* add --with dkms to the dh command in debian/rules
* install driver source to /usr/src

Quite how its supposed to be done I don't know but I very quickly had a working version. looking at backfire-dkms should be a sounder idea to do it properly

---

