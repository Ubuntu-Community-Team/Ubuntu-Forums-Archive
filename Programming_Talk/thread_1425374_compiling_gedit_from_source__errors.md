---
title: "compiling gedit from source :: errors"
date: 2010-03-09
forum: Programming Talk
---

### Post by kaligus on 2010-03-09
I have been trying (and the key word here is TRYING) to compile gedit as both an exercise in learning for me and to help someone else out (but that is already posted elsewhere).

I have 2 versions of everything:
gedit 2.28.0 from packages.ubuntu.com
gedit 2.29.8 from git.gnome.org

glib /usr/lib (default) 2.22.3 from repo
glib /usr/local/lib from git

gtksourceview 2.8.1-1 /usr/lib from repo
gtksourceview 2.9.8 /usr/local/lib from archive

I *think* I understand how to specify which library to use but since the same error2, same files, etc. happens whether I try to compile gedit 2.28 or 2.29 I can only assume that there is something else outside of these libraries that is broken.

Here is the output of "make" and "apt-get build-dep gedit" in the 2.28 directory

```

bigwill:[20100308.2247]will@/tz/computer/development/compile/gedit-2.28.0 :: make
make  all-recursive                                                              
make[1]: Entering directory `/tz/computer/development/compile/gedit-2.28.0'      
Making all in gedit                                                              
make[2]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
  GEN    gedit-enum-types.c                                                      
  GEN    gedit-enum-types.h                                                      
  GEN    gedit-marshal.c                                                         
  GEN    gedit-marshal.h                                                         
make  all-recursive                                                              
make[3]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
Making all in dialogs                                                            
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit/dialogs'
  CC     gedit-preferences-dialog.lo                                                     
  CC     gedit-close-confirmation-dialog.lo                                              
  CC     gedit-encodings-dialog.lo                                                       
  CC     gedit-search-dialog.lo                                                          
  CCLD   libdialogs.la                                                                   
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit/dialogs' 
Making all in smclient                                                                   
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit/smclient'
  CC     eggsmclient.lo                                                                   
  CC     eggsmclient-xsmp.lo                                                              
  CC     eggdesktopfile.lo                                                                
  CCLD   libeggdesktopfile.la                                                             
  CCLD   libeggsmclient.la                                                                
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit/smclient' 
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit'         
  CC     gedit-enum-types.lo                                                              
  CC     gedit-marshal.lo                                                                 
  CC     bacon-message-connection.lo                                                      
  CC     gedit-local-document-saver.lo                                                    
  CC     gedit-app.lo                                                                     
  CC     gedit-commands-documents.lo                                                      
  CC     gedit-commands-edit.lo                                                           
  CC     gedit-commands-file.lo                                                           
  CC     gedit-commands-file-print.lo                                                     
  CC     gedit-commands-help.lo                                                           
  CC     gedit-commands-search.lo                                                         
  CC     gedit-commands-view.lo                                                           
  CC     gedit-convert.lo                                                                 
  CC     gedit-debug.lo                                                                   
  CC     gedit-dirs.lo                                                                    
  CC     gedit-document.lo                                                                
  CC     gedit-document-loader.lo                                                         
  CC     gedit-gio-document-loader.lo                                                     
  CC     gedit-document-saver.lo                                                          
  CC     gedit-gio-document-saver.lo                                                      
  CC     gedit-documents-panel.lo                                                         
  CC     gedit-encodings.lo                                                               
  CC     gedit-encodings-option-menu.lo                                                   
  CC     gedit-file-chooser-dialog.lo                                                     
  CC     gedit-help.lo                                                                    
  CC     gedit-history-entry.lo                                                           
  CC     gedit-io-error-message-area.lo                                                   
  CC     gedit-language-manager.lo                                                        
  CC     gedit-message-bus.lo                                                             
  CC     gedit-message-type.lo                                                            
  CC     gedit-message.lo                                                                 
  CC     gedit-metadata-manager.lo                                                        
  CC     gedit-object-module.lo                                                           
  CC     gedit-notebook.lo
  CC     gedit-panel.lo
  CC     gedit-plugin-info.lo
  CC     gedit-plugin.lo
  CC     gedit-plugin-loader.lo
  CC     gedit-plugin-manager.lo
  CC     gedit-plugins-engine.lo
  CC     gedit-prefs-manager-app.lo
  CC     gedit-prefs-manager.lo
  CC     gedit-print-job.lo
  CC     gedit-print-preview.lo
  CC     gedit-progress-message-area.lo
  CC     gedit-session.lo
  CC     gedit-spinner.lo
  CC     gedit-statusbar.lo
  CC     gedit-status-combo-box.lo
  CC     gedit-style-scheme-manager.lo
  CC     gedit-tab.lo
  CC     gedit-utils.lo
  CC     gedit-view.lo
  CC     gedit-window.lo
  CC     gedittextregion.lo
  CCLD   libgedit.la
  CC     gedit.o
  CCLD   gedit
./.libs/libgedit.a(gedit-utils.o): In function `gedit_utils_drop_get_uris':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-utils.c:1376: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(eggsmclient-xsmp.o): In function `sm_client_xsmp_set_restart_command':
/tz/computer/development/compile/gedit-2.28.0/gedit/smclient/eggsmclient-xsmp.c:398: undefined reference to `g_malloc_n'
./.libs/libgedit.a(gedit-message-type.o): In function `gedit_message_type_set_valist':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-message-type.c:338: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(gedit-spinner.o): In function `gedit_spinner_images_load':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-spinner.c:340: undefined reference to `g_malloc_n'
collect2: ld returned 1 exit status
make[4]: *** [gedit] Error 1
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0'
make: *** [all] Error 2
bigwill:[20100308.2248]will@/tz/computer/development/compile/gedit-2.28.0 :: sudo apt-get build-dep gedit
[sudo] password for will:
Reading package lists... Done
Building dependency tree
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
bigwill:[20100308.2249]will@/tz/computer/development/compile/gedit-2.28.0 ::

```Does anyone have any idea what vital piece I am missing in my understanding of the world?

---

### Post by heikaman on 2010-03-09
Hi, I think you need to link with glib, try -lglib

---

### Post by gmargo on 2010-03-09
I had no trouble compiling gedit 2.28.0 from the Ubuntu source, on 9.10 Karmic.  I'm not sure why your's went wrong but here's how I did it:
```

# Get gedit source code
apt-get source gedit
cd gedit-2.28.0

# Get build dependencies
sudo aptitude -V -R build-depends gedit

# Try to build, round 1
dpkg-buildpackage -b -us -uc

# First try failed, due to a couple of build dependencies
# that the build-depends missed.  Install the others.
sudo aptitude -V -R install libglib2.0-doc libgtk2.0-doc libgtksourceview2.0-doc

# Try to build, round 2
dpkg-buildpackage -b -us -uc

# Success!
```The files created:
```

$ cd .. ; ls -lGg *.deb
-rw-r--r-- 1 4355654 Mar  9 06:13 gedit-common_2.28.0-0ubuntu2_all.deb
-rw-r--r-- 1  123998 Mar  9 06:13 gedit-dev_2.28.0-0ubuntu2_all.deb
-rw-r--r-- 1  566058 Mar  9 06:14 gedit_2.28.0-0ubuntu2_i386.deb

```

---

### Post by kaligus on 2010-03-13
> **heikaman said:**
> Hi, I think you need to link with glib, try -lglib

Still no joy, in fact somewhat less joy

```
bigwill:[20100313.0601]will@/tz/computer/development/compile/gedit-2.28.0 :: make -lglib
make  all-recursive
make[1]: Entering directory `/tz/computer/development/compile/gedit-2.28.0'
Making all in gedit
make[2]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make  all-recursive
make[3]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
Making all in dialogs
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit/dialogs'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit/dialogs'
Making all in smclient
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit/smclient'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit/smclient'
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
  CCLD   gedit
./.libs/libgedit.a(gedit-utils.o): In function `gedit_utils_drop_get_uris':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-utils.c:1376: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(eggsmclient-xsmp.o): In function `sm_client_xsmp_set_restart_command':
/tz/computer/development/compile/gedit-2.28.0/gedit/smclient/eggsmclient-xsmp.c:398: undefined reference to `g_malloc_n'
./.libs/libgedit.a(gedit-message-type.o): In function `gedit_message_type_set_valist':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-message-type.c:338: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(gedit-spinner.o): In function `gedit_spinner_images_load':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-spinner.c:340: undefined reference to `g_malloc_n'
collect2: ld returned 1 exit status
make[4]: *** [gedit] Error 1
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0'
make: *** [all] Error 2
bigwill:[20100313.0601]will@/tz/computer/development/compile/gedit-2.28.0 :: 

```

---

### Post by kaligus on 2010-03-13
> **gmargo said:**
> I had no trouble compiling gedit 2.28.0 from the Ubuntu source, on 9.10 Karmic.  I'm not sure why your's went wrong but here's how I did it:
```

# Get gedit source code
apt-get source gedit
cd gedit-2.28.0

# Get build dependencies
sudo aptitude -V -R build-depends gedit

# Try to build, round 1
dpkg-buildpackage -b -us -uc
[ deletia]


```

no joy here either.

```

bigwill:[20100313.0601]will@/tz/computer/development/compile/gedit-2.28.0 :: dpkg-buildpackage -b -us -uc
dpkg-buildpackage: set CFLAGS to default value: -g -O2
dpkg-buildpackage: set CPPFLAGS to default value:
dpkg-buildpackage: set LDFLAGS to default value: -Wl,-Bsymbolic-functions
dpkg-buildpackage: set FFLAGS to default value: -g -O2
dpkg-buildpackage: set CXXFLAGS to default value: -g -O2
tail: cannot open `debian/changelog' for reading: No such file or directory
dpkg-buildpackage: error: tail of debian/changelog gave error exit status 1
bigwill:[20100313.0602]will@/tz/computer/development/compile/gedit-2.28.0 ::

```

---

### Post by gmargo on 2010-03-13
> **kaligus said:**
> no joy here either.
```
**tail: cannot open `debian/changelog' for reading: No such file or directory**

```

You are attempting to compile the original **gedit-2.28.0** source code without the Ubuntu differences patch.  Probably you downloaded the source code manually and forgot the patch. The Ubuntu source consists of three files:

[LIST=1]
[*]gedit_2.28.0-0ubuntu2.diff.gz
[*]gedit_2.28.0-0ubuntu2.dsc
[*]gedit_2.28.0.orig.tar.gz
[/LIST]
The ".diff.gz" file is a patch that must be applied to the original source.  Try that and the dpkg-buildpackage should work.

"apt-get source" will fetch the source files, extract the  original, and apply the patch, all in one step.

---

### Post by kaligus on 2010-03-13
> **gmargo said:**
> You are attempting to compile the original **gedit-2.28.0** source code without the Ubuntu differences patch.  Probably you downloaded the source code manually and forgot the patch. The Ubuntu source consists of three files:

[LIST=1]
[*]gedit_2.28.0-0ubuntu2.diff.gz
[*]gedit_2.28.0-0ubuntu2.dsc
[*]gedit_2.28.0.orig.tar.gz
[/LIST]
The ".diff.gz" file is a patch that must be applied to the original source.  Try that and the dpkg-buildpackage should work.

"apt-get source" will fetch the source files, extract the  original, and apply the patch, all in one step.

I did download the diff.gz and used "patch" to in my limited theory apply the patch but I will try the full apt-get way in a moment and see what that offers :)

---

### Post by kaligus on 2010-03-13
> **gmargo said:**
> You are attempting to compile the original **gedit-2.28.0** source code without the Ubuntu differences patch.  Probably you downloaded the source code manually and forgot the patch. The Ubuntu source consists of three files:

[LIST=1]
[*]gedit_2.28.0-0ubuntu2.diff.gz
[*]gedit_2.28.0-0ubuntu2.dsc
[*]gedit_2.28.0.orig.tar.gz
[/LIST]
The ".diff.gz" file is a patch that must be applied to the original source.  Try that and the dpkg-buildpackage should work.

"apt-get source" will fetch the source files, extract the  original, and apply the patch, all in one step.

Still denied :| same thing and there are almost 50 new files in the apt-get directory over the gz and patched directory.

EDIT:  hang on I think I did a make and it will be a while before I get back to this project as the #$%^# phone rang with immediate projects.

```

./.libs/libgedit.a(gedit-utils.o): In function `gedit_utils_drop_get_uris':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-utils.c:1376: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(eggsmclient-xsmp.o): In function `sm_client_xsmp_set_restart_command':
/tz/computer/development/compile/gedit-2.28.0/gedit/smclient/eggsmclient-xsmp.c:398: undefined reference to `g_malloc_n'
./.libs/libgedit.a(gedit-message-type.o): In function `gedit_message_type_set_valist':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-message-type.c:338: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(gedit-spinner.o): In function `gedit_spinner_images_load':
/tz/computer/development/compile/gedit-2.28.0/gedit/gedit-spinner.c:340: undefined reference to `g_malloc_n'
collect2: ld returned 1 exit status
make[4]: *** [gedit] Error 1
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0/gedit'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0'
make: *** [all] Error 2
bigwill:[20100313.0956]will@/tz/computer/development/compile/gedit-2.28.0 ::

```

---

### Post by cubeist on 2010-03-13
--- nevermind, useless advice!

---

### Post by heikaman on 2010-03-14
>  make -l glib

I don't this has any effect, you may have to edit the makefile manually.

g_malloc0_n and similar symbols are defined in glib that's why I think you should link with it, good luck.

EDIT: I installed gedit-2.28.0 from [ftp://ftp.gnome.org/mirror/gnome.org/sources/gedit/2.28/gedit-2.28.0.tar.gz]("ftp://ftp.gnome.org/mirror/gnome.org/sources/gedit/2.28/gedit-2.28.0.tar.gz") installed a few dependencies and ./configure && make and I can build successfully.

---

### Post by kaligus on 2010-03-14
at this point I am thinking it is time to boot from a CD and delete /var /usr /etc and start over ... 

Is it possible that somehow I have a wonked up version/flavour/settings/etc. of make?  

Some setting that other languages would find but not gcc?

I have -dev version of all of the files synaptic shows installed in a search for "glib" (where one is available)

What about other libraries that possibly need a -dev?

```

bigwill:[20100314.0619]will@/tz/computer/development/compile/gedit-2.28.0-apt_get :: make -l glib
make: *** No rule to make target `glib'.  Stop.
bigwill:[20100314.0621]will@/tz/computer/development/compile/gedit-2.28.0-apt_get :: make -lglib
make  all-recursive
make[1]: Entering directory `/tz/computer/development/compile/gedit-2.28.0-apt_get'
Making all in gedit
make[2]: Entering directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit'
make  all-recursive
make[3]: Entering directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit'
Making all in dialogs
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/dialogs'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/dialogs'
Making all in smclient
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/smclient'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/smclient'
make[4]: Entering directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit'
  CCLD   gedit
./.libs/libgedit.a(gedit-utils.o): In function `gedit_utils_drop_get_uris':
/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/gedit-utils.c:1376: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(eggsmclient-xsmp.o): In function `sm_client_xsmp_set_restart_command':
/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/smclient/eggsmclient-xsmp.c:398: undefined reference to `g_malloc_n'
./.libs/libgedit.a(gedit-message-type.o): In function `gedit_message_type_set_valist':
/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/gedit-message-type.c:338: undefined reference to `g_malloc0_n'
./.libs/libgedit.a(gedit-spinner.o): In function `gedit_spinner_images_load':
/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit/gedit-spinner.c:340: undefined reference to `g_malloc_n'
collect2: ld returned 1 exit status
make[4]: *** [gedit] Error 1
make[4]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0-apt_get/gedit'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/tz/computer/development/compile/gedit-2.28.0-apt_get'
make: *** [all] Error 2
bigwill:[20100314.0622]will@/tz/computer/development/compile/gedit-2.28.0-apt_get ::

```

---

### Post by kaligus on 2010-03-14
something is certainly wonked... today when I get the build deps with apt-get it gives me an error and wants to remove half of the things which seem important to me.

```

bigwill:[20100314.0637]will@/tz/computer/development/compile/gedit-2.28.0-apt_get :: sudo aptitude -V -R build-depends gedit
Reading package lists... Done
Building dependency tree
Reading state information... Done
Reading extended state information
Initializing package states... Done
Writing extended state information... Done
Unable to satisfy the build-depends: Build-Dependsscrollkeeper.Unable to satisfy the build-depends: Build-Dependsscrollkeeper.The following packages will be REMOVED:
  libjline-java{u} [0.9.94-5~ubuntu1]  libmcrypt4{u} [2.5.8-3]  libmhash2{u} [0.9.9-1build1]  libmikmod2{u} [3.1.11-a-6ubuntu4]
  libpolkit-gnome0{u} [0.9-1ubuntu3]  libsdl-mixer1.2{u} [1.2.8-6build1]  libsmpeg0{u} [0.4.5+cvs20030824-2.2]
  nvidia-190-modaliases{u} [190.53-karmic~ppa3]  pidgin-libnotify{u} [0.14-1ubuntu11]  policykit-gnome{u} [0.9-1ubuntu3]
  python-libtorrent{u} [0.14.9-2~karmic~ppa1]  python-numpy{u} [1:1.3.0-3]  python-pygame{u} [1.8.1release-1ubuntu1]  python-twisted{u} [8.2.0-3]
  python-twisted-conch{u} [1:8.2.0-2ubuntu1]  python-twisted-lore{u} [8.2.0-1ubuntu1]  python-twisted-mail{u} [8.2.0-2ubuntu2]
  python-twisted-news{u} [8.2.0-2]  python-twisted-runner{u} [8.2.0-1]  python-twisted-words{u} [8.2.0-2ubuntu1]  rhino{u} [1.7R2-1ubuntu1]
0 packages upgraded, 0 newly installed, 21 to remove and 1 not upgraded.
Need to get 0B of archives. After unpacking 22.7MB will be freed.
Do you want to continue? [Y/n/?] n
Abort.
bigwill:[20100314.0638]will@/tz/computer/development/compile/gedit-2.28.0-apt_get ::

```

---

### Post by kaligus on 2010-03-27
A reinstall (and actually switched to Kubuntu but that is another story) of the OS and everything starts working like magic.

Not sure what was confused as I still have the same apps from the same sources... but life is much better now!

---

