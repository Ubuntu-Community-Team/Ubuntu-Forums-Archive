---
title: "HOWTO: installation of E17 from CVS"
date: 2005-11-30
forum: Outdated Tutorials &amp; Tips
---

### Post by TimmyJ on 2005-11-30
This is just a quick how-to on downloading, compiling, and installing the desktop shell Enlightenment 17 from the CVS repository. E17 is still in development, so do not expect a fully stable, bug-free environment. That said: I use E17 on a daily basis and rarely run into any hiccups.

[B]READ: Before following this guide please remove any previously installed versions of E17 (aka from any repository) as they may cause errors in the process.
[/B]
A quick disclaimer: this is my first how-to, so feel free to offer any constructive criticism.

Lets Start!

1.) First we want to install all required packages for E17, and all the Enlightenment Foundation Libraries to install. This list may be a bit of overkill, but it will get the job done.

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
```


2.) Now that all that is out of the way we need to get the script that will make downloading/compiling/installing E17 very easy. All credit goes to Morlenxus for this great tool.

From your home directory, run the following command
```
wget http://omicron.homeip.net/projects/easy_e17/easy_e17.sh
```

3.) Now we need to made the script executable and then run it! This script will prompt you for your sudo password, enter it. This script will take quite some time to run, so try to be patient **NOTES: This script will install all the applications and libraries it installs into /opt/e17 so as not to interfere with other versions of enlightenment. You can change this location through scripts options. This script will install ALL the applications and libraries available in the E17 CVS tree. You may or may not want all these apps. You can easily skip any library or app using the --skip flag with the script.**

```
chmod +x easy_e17.sh
./easy_e17.sh -i
```

4.) Now we have enlightenment all installed and working. The next step it create a desktop entry so that you can log-in to enlightenment from GDM.

Create a desktop entry called e17.desktop
```
sudo gedit /usr/share/xsessions/e17.desktop
```

Copy/Paste the following into the newly created file
```
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
```

Thats all you really need to do. Now using enligthenment is as simple as logging out, selecting the E-17 session and logging back in. Any time you want to update enlightenment and related libs/apps, simply re-run the easy_e17 script. For more information on the Enlightenment Foundation Libraries, and the applications that use them, please see [http://www.get-e.org](http://www.get-e.org) and 
[http://www.enlightenment.org.au](http://www.enlightenment.org.au)
[B]
Suggestion: due to the fact that enlightenment was installed in /opt/e17 it is a good idea to add /opt/e17/bin to your PATH so that it is easier to run all those great applications you just installed.[/B]

To do this open your /etc/environment with your favorite text editor

```
sudo gedit /etc/environment
```

then add the following lines to the bottom

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```

---

### Post by bored2k on 2005-11-30
I did this about a month ago and it worked great. How stable is it now? Anything good implemented into the applications?

---

### Post by alingatong on 2005-12-01
this is great how to.its been days trying to get e17 from CVS but I am always stuck with the compilation of emotion because of xine in ubuntu.

I tried using your how to but for noobs like me, i think it would be better to add some more details like:

--how do i run the script easy_e17.sh?
--how do i add /opt/e17 in PATH?

thanks.

---

### Post by firecat53 on 2005-12-02
Well, it started working :) I got the following output (sorry for the length, but I don't know which is important) --

```
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ecore.log:
-----------------------------------------------------------------------------
ranlib .libs/libecore_dbus.a
creating libecore_dbus.la
(cd .libs && rm -f libecore_dbus.la && ln -s ../libecore_dbus.la libecore_dbus.la)
make[4]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/owner/e17_cvs/e17/libs/ecore/src/bin'
if gcc-3.4 -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include  -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -MT ecore_test-ecore_test.o -MD -MP -MF ".deps/ecore_test-ecore_test.Tpo" -c -o ecore_test-ecore_test.o `test -f 'ecore_test.c' || echo './'`ecore_test.c; \
then mv -f ".deps/ecore_test-ecore_test.Tpo" ".deps/ecore_test-ecore_test.Po"; else rm -f ".deps/ecore_test-ecore_test.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc-3.4  -I/opt/e17/include -g -O2 -Wall  -L/opt/e17/lib -o ecore_test  ecore_test-ecore_test.o ../../src/lib/ecore/libecore.la ../../src/lib/ecore_x/libecore_x.la ../../src/lib/ecore_txt/libecore_txt.la ../../src/lib/ecore_job/libecore_job.la ../../src/lib/ecore_fb/libecore_fb.la ../../src/lib/ecore_evas/libecore_evas.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore_ipc/libecore_ipc.la -lm
mkdir .libs
gcc-3.4 -I/opt/e17/include -g -O2 -Wall -o .libs/ecore_test ecore_test-ecore_test.o  -L/opt/e17/lib ../../src/lib/ecore/.libs/libecore.so ../../src/lib/ecore_x/.libs/libecore_x.so ../../src/lib/ecore_txt/.libs/libecore_txt.so ../../src/lib/ecore_job/.libs/libecore_job.so ../../src/lib/ecore_fb/.libs/libecore_fb.so ../../src/lib/ecore_evas/.libs/libecore_evas.so ../../src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_ipc/.libs/libecore_ipc.so -lm
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_get'
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_set'
collect2: ld returned 1 exit status
make[3]: *** [ecore_test] Error 1
make[3]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2

```

Any thoughts?? I'd love to get this working!! I had e17 going under Hoary, but no luck yet in Breezy. 

Thanks, Scott

---

### Post by alingatong on 2005-12-02
try this guide.

[https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php)

---

### Post by TimmyJ on 2005-12-02
> I tried using your how to but for noobs like me, i think it would be better to add some more details like:

--how do i run the script easy_e17.sh?
--how do i add /opt/e17 in PATH?

Thanks for the input! To run the script simply running the following command while in the directory you downloaded the file easy_e17.sh to:
> 
sudo ./easy_e17.sh -i --skip=emotion,eclair

for more info you can also do this:
> 
./easy_e17 --help

I will update the guide with notes on changed your $PATH

---

### Post by TimmyJ on 2005-12-02
[QUOTE=firecat53]Well, it started working :) I got the following output (sorry for the length, but I don't know which is important) --
[/QUOTE]

I updated my list of programs to install. Re-run this command and then re-run the script and see if that does it for you :) 
```

sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev
```

then

```
sudo ./easy_e17.sh -i --skip=emotion,eclair
```

hope that helps! Thanks for trying this out :)

---

### Post by crobe on 2005-12-02
mine fails on e installation with an ERROR!, this what the log shows....

LAST LOGLINES FROM /tmp/easy_e17/install_logs/e.log:

```

configure.in: installing `./missing'
src/bin/Makefile.am: installing `./depcomp'
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not exist
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not exist
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
Running aclocal...
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not exist
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used

```

I am not sure what is supposed to create src/modules/gadget_test, so I am not sure where to begin troubleshooting...

---

### Post by TimmyJ on 2005-12-02
[QUOTE=crobe]mine fails on e installation with an ERROR!, this what the log shows....

LAST LOGLINES FROM /tmp/easy_e17/install_logs/e.log:

```

configure.in: installing `./missing'
src/bin/Makefile.am: installing `./depcomp'
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not exist
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not exist
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
Running aclocal...
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
  run info '(automake)Extending aclocal'
  or see http://sources.redhat.com/automake/automake.html#Extending-aclocal
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not exist
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used

```

I am not sure what is supposed to create src/modules/gadget_test, so I am not sure where to begin troubleshooting...[/QUOTE]


This is a problem with thinktux's CVS repo, for some reason its not getting the e_gadget stuff. You can either wait it out and try again later. Or you can use [email]anonymous@cvs.sourceforge.net[/email] for the time being. Instructions on using this CVS repo can be found at [www.get-e.org](www.get-e.org)

---

### Post by foxy123 on 2005-12-02
> **firecat53]Well, it started working :) I got the following output (sorry for the length, but I don't know which is important) --

```
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ecore.log:
-----------------------------------------------------------------------------
ranlib .libs/libecore_dbus.a
creating libecore_dbus.la
(cd .libs && rm -f libecore_dbus.la && ln -s ../libecore_dbus.la libecore_dbus.la)
make[4]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/owner/e17_cvs/e17/libs/ecore/src/bin'
if gcc-3.4 -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include  -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -MT ecore_test-ecore_test.o -MD -MP -MF ".deps/ecore_test-ecore_test.Tpo" -c -o ecore_test-ecore_test.o `test -f 'ecore_test.c' || echo './'`ecore_test.c said:**
> : *** [ecore_test] Error 1
make[3]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/owner/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2

```

Any thoughts?? I'd love to get this working!! I had e17 going under Hoary, but no luck yet in Breezy. 

Thanks, Scott
I've got the same problem :(

---

### Post by TimmyJ on 2005-12-02
[QUOTE=foxy123]I've got the same problem :([/QUOTE]

OK, I think I've nailed down what causes this. It is a problem with automake versions. To fix this you should:
```
sudo apt-get remove automake1.4 automake1.6 automake1.8 automake1.9
```
then
```

sudo apt-get install automake1.7
```
then finally, run the script again
```
sudo ./easy_e17 -i --skip=eclair,emotion
```

Hopefully that'll work. Post ur results :)

---

### Post by foxy123 on 2005-12-02
[QUOTE=TimmyJ]OK, I think I've nailed down what causes this. It is a problem with automake versions. To fix this you should:
```
sudo apt-get remove automake1.4 automake1.6 automake1.8 automake1.9
```
then
```

sudo apt-get install automake1.7
```
then finally, run the script again
```
sudo ./easy_e17 -i --skip=eclair,emotion
```

Hopefully that'll work. Post ur results :)[/QUOTE]
no, still the same error...

---

### Post by TimmyJ on 2005-12-02
Bummer :( I'll keep trying to figure out whats up.

---

### Post by foxy123 on 2005-12-02
Found a similar problem here [http://edevelop.org/node/1775](http://edevelop.org/node/1775)
I also had e17 from repos but I have completely uninstalled it.:confused:

---

### Post by foxy123 on 2005-12-02
[QUOTE=foxy123]Found a similar problem here [http://edevelop.org/node/1775](http://edevelop.org/node/1775)
I also had e17 from repos but I have completely uninstalled it.:confused:[/QUOTE]
no, apparently I did not. Searched for e17 packages to uninstall by maintainer name and missed a bunch of them. It would be worth to put a note in the HOWTO to uninstall all E17 libraries, previously installed.

---

### Post by TimmyJ on 2005-12-02
Thanks for the tip, I'll do that :)

---

### Post by foxy123 on 2005-12-02
[QUOTE=TimmyJ]There is no standard repo for E17 for breezy as it is still beta software. The uninstallation of all E17 packages will vary from repo to repo. Making an universal removal HOW-TO would be very difficult. I suggest that each person should pick a method of installation and stick to it. If you want to know exactly what E17 packages you need to remove I suggest contacting the maintainer of that package.[/QUOTE]
what I meant was to tell people to make sure that they uninstalled previously installed versions of E17 before running the script...

I've got another problem now:
```
APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entice ..................... ok
- entrance ................... ok
- elicit ..................... ok
- e .......................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/e.log:
-----------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in: installing `./install-sh'
configure.in: installing `./mkinstalldirs'
configure.in: installing `./missing'
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
src/bin/Makefile.am: installing `./depcomp'
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) is used
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist

```

---

### Post by TimmyJ on 2005-12-02
Yup thats a problem with the CVS repository the script uses. There is another CVS repo at [email]anonymous@cvs.sourceforge.net[/email] (you can check [www.get-e.org](www.get-e.org) for a description on how to use this) that doesn't suffer from these issues. So you can either use that, or wait until the thintux repo (the one the script uses) is fixed. I doubt it will be a very long wait.

---

### Post by foxy123 on 2005-12-02
[QUOTE=TimmyJ]Yup thats a problem with the CVS repository the script uses. There is another CVS repo at [email]anonymous@cvs.sourceforge.net[/email] (you can check [www.get-e.org](www.get-e.org) for a description on how to use this) that doesn't suffer from these issues. So you can either use that, or wait until the thintux repo (the one the script uses) is fixed. I doubt it will be a very long wait.[/QUOTE]
Thanks a lot for you help... I guess I'll wait

---

### Post by TimmyJ on 2005-12-02
[QUOTE=foxy123]Thanks a lot for you help... I guess I'll wait[/QUOTE]

No problem :) Thx for testing this out for me, hopefully others will find it usefull

---

### Post by WanderingStar on 2005-12-02
[QUOTE=foxy123]Thanks a lot for you help... I guess I'll wait[/QUOTE]
To use the SF cvs server change line 22 (cvs_srv=...) to:

```
cvs_srv=":pserver:anonymous@cvs.sourceforge.net:/cvsroot/enlightenment";
```

and it should work.

---

### Post by foxy123 on 2005-12-03
[QUOTE=WanderingStar]To use the SF cvs server change line 22 (cvs_srv=...) to:

```
cvs_srv=":pserver:anonymous@cvs.sourceforge.net:/cvsroot/enlightenment";
```

and it should work.[/QUOTE]
I still got the same error:
```
APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entice ..................... previous installed
- entrance ................... previous installed
- elicit ..................... previous installed
- e .......................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/e.log:
-----------------------------------------------------------------------------
Running libtoolize...
Running automake...
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not e xist
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in: installing `./install-sh'
configure.in: installing `./mkinstalldirs'
configure.in: installing `./missing'
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/bin/Makefile.am: installing `./depcomp'
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
-----------------------------------------------------------------------------


```

---

### Post by WanderingStar on 2005-12-03
Thats odd, worked for me.  I would suggest deleting the e17_cvs directory and re-running the script - could be that it thinks it downloaded it somehow.

---

### Post by foxy123 on 2005-12-03
[QUOTE=WanderingStar]Thats odd, worked for me.  I would suggest deleting the e17_cvs directory and re-running the script - could be that it thinks it downloaded it somehow.[/QUOTE]
exactly what I am doing now :)

---

### Post by foxy123 on 2005-12-03
[QUOTE=WanderingStar]Thats odd, worked for me.  I would suggest deleting the e17_cvs directory and re-running the script - could be that it thinks it downloaded it somehow.[/QUOTE]
it's worked, thanks a lot! Have not tried to boot into e17 yet....

---

### Post by foxy123 on 2005-12-03
Tried it and E17 works! The thing is still buggy but astonishingly beautiful!

As I understand the script compiles only default and engage modles. What about weather and other modules? Can I add them to the script? Any other programmes like evidence? Should I list them in 24-26 lines in the script?

---

### Post by N8K99 on 2005-12-03
How do I remove gdm and run entrance from this configuration? How do I configure entrance to run both e17 and e16 on my machine? This is all on a fresh install so I want to be able to configure Entrance to be the Login Manager and I'd like to use Evidence instead of Nautilus. I guess I should probably download the elive distrobution instead if that's what I'd really want to run! But nonetheless here I am.

---

### Post by TimmyJ on 2005-12-03
I haven't configured entrance myself yet. If I do change it I'll post here how to do it.

---

### Post by TimmyJ on 2005-12-03
The modules besided the default ones and engage aren't in the CVS tree. You can find them at [www.get-e.org](www.get-e.org) with install instructions. There aren't that many right now, but expect more in the near future :)

---

### Post by benplaut on 2005-12-03
ooh, oh, pick me! i've got a new one!

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2  -L/opt/e17/lib -o libedje.la -rpath /opt/e17/lib -version-info 5:0:5 libedje_la-edje_calc.lo libedje_la-edje_callbacks.lo libedje_la-edje_data.lo libedje_la-edje_embryo.lo libedje_la-edje_load.lo libedje_la-edje_main.lo libedje_la-edje_misc.lo libedje_la-edje_program.lo libedje_la-edje_smart.lo libedje_la-edje_text.lo libedje_la-edje_util.lo libedje_la-edje_var.lo libedje_la-edje_container.lo libedje_la-edje_message_queue.lo libedje_la-edje_cache.lo libedje_la-edje_textblock_styles.lo -lm -L/opt/e17/lib -levas -L/opt/e17/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -lecore_dbus -L/usr/lib -leet -lz -ljpeg -lm -L/usr/lib -leet -lz -ljpeg -L/usr/lib -lembryo -lm
gcc -shared  .libs/libedje_la-edje_calc.o .libs/libedje_la-edje_callbacks.o .libs/libedje_la-edje_data.o .libs/libedje_la-edje_embryo.o .libs/libedje_la-edje_load.o .libs/libedje_la-edje_main.o .libs/libedje_la-edje_misc.o .libs/libedje_la-edje_program.o .libs/libedje_la-edje_smart.o .libs/libedje_la-edje_text.o .libs/libedje_la-edje_util.o .libs/libedje_la-edje_var.o .libs/libedje_la-edje_container.o .libs/libedje_la-edje_message_queue.o .libs/libedje_la-edje_cache.o .libs/libedje_la-edje_textblock_styles.o  -L/opt/e17/lib /opt/e17/lib/libevas.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_dbus.so -L/usr/lib /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so /opt/e17/lib/libembryo.so -lm  -Wl,-soname -Wl,libedje.so.0 -o .libs/libedje.so.0.5.0
(cd .libs && rm -f libedje.so.0 && ln -s libedje.so.0.5.0 libedje.so.0)
(cd .libs && rm -f libedje.so && ln -s libedje.so.0.5.0 libedje.so)
ar cru .libs/libedje.a  libedje_la-edje_calc.o libedje_la-edje_callbacks.o libedje_la-edje_data.o libedje_la-edje_embryo.o libedje_la-edje_load.o libedje_la-edje_main.o libedje_la-edje_misc.o libedje_la-edje_program.o libedje_la-edje_smart.o libedje_la-edje_text.o libedje_la-edje_util.o libedje_la-edje_var.o libedje_la-edje_container.o libedje_la-edje_message_queue.o libedje_la-edje_cache.o libedje_la-edje_textblock_styles.o
ranlib .libs/libedje.a
creating libedje.la
(cd .libs && rm -f libedje.la && ln -s ../libedje.la libedje.la)
make[3]: Leaving directory `/home/breezy/e17_cvs/e17/libs/edje/src/lib'
Making all in bin
make[3]: Entering directory `/home/breezy/e17_cvs/e17/libs/edje/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../bin -I../../src/lib -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include   -I/opt/e17/include  -g -O2 -MT edje_main.o -MD -MP -MF ".deps/edje_main.Tpo" -c -o edje_main.o edje_main.c; \
then mv -f ".deps/edje_main.Tpo" ".deps/edje_main.Po"; else rm -f ".deps/edje_main.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2  -L/opt/e17/lib -o edje edje_main.o ../../src/lib/libedje.la
mkdir .libs
gcc -g -O2 -o .libs/edje edje_main.o  -L/opt/e17/lib ../../src/lib/.libs/libedje.so
../../src/lib/.libs/libedje.so: undefined reference to `eet_data_descriptor2_new'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/breezy/e17_cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/breezy/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/breezy/e17_cvs/e17/libs/edje'
make: *** [all] Error 2

```

hopefully something simple :(

---

### Post by N8K99 on 2005-12-03
right now without gdm installed- when I call startx, the window manager that gets called is DR16. I'm needing a crash course in configuring to get DR17 to run. Also, how to I keep Nautilus from writing over the desktop? Do I have to remove it? I have run e17 before where I got rid of Nautilus and everything Gnome but that was when e17 came from Shadoi's repository and was contained within  main directory for programs not in /opt.  What do I need to do to get this sort of set up happening?  Perhaps after all this work when I get everything happening straight out of Enlightenment, then I'll work out a Ubuntu theme for e17!

---

### Post by aragorn2909 on 2005-12-03
[QUOTE=foxy123]I still got the same error:
```
APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entice ..................... previous installed
- entrance ................... previous installed
- elicit ..................... previous installed
- e .......................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/e.log:
-----------------------------------------------------------------------------
Running libtoolize...
Running automake...
configure.in:316: required file `src/modules/gadget_test/Makefile.in' not found
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/modules/Makefile.am:2: required directory src/modules/gadget_test does not e xist
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in: installing `./install-sh'
configure.in: installing `./mkinstalldirs'
configure.in: installing `./missing'
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/bin/Makefile.am: installing `./depcomp'
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
Makefile.am:1: `intl' should not be in SUBDIRS when AM_GNU_GETTEXT([external]) i s used
src/modules/Makefile.am:14: required directory src/modules/gadget_test does not exist
-----------------------------------------------------------------------------


```[/QUOTE]


Don't know if it will help now, but I was getting this exact same error the other day.  I fixed it by manually downloading the files contained in [cvs]/enlightenment/e17/apps/e/src/modules/gadget_test from [here]("http://cvs.sourceforge.net/viewcvs.py/enlightenment/e17/apps/e/src/modules/gadget_test/"),  renaming the file "Makefile.am" to "Makefile.in", inserting them in the appropriate place, and rerunning the script.  Worked like a charm.

---

### Post by penvzila on 2005-12-03
Thanks for this guide, I have been waiting for this.  Let's see if it works now.

---

### Post by ting on 2005-12-04
I first had the problem with an error on edje. I think this was due to something that was installed before. (I had used automatix, to download alot of stuff, and the shadoi method to install enlightenment, so there was probably something i did'nt remove). 

Anyway, i did a reinstall of ubuntu, upgraded the kernel (still 386), and all the other stuff(all upgrades). And it worked. This is what i did:

Follow TimmyJ's instructions, untill after i downloaded the script,
edited the script as described in wanderingstar's post, and continued following the instructions in TimmyJ' spost.

Until...
Note: you must replace **user_name** with YOUR actual user name.
Code:

sudo chown -R user:**user_name** ~/.ecore

This gave me some strange errors, but when i did it like this(i think):

sudo chown -R **user_name** ~/.ecore

said in another way:

sudo chown -R xxxxx ~/.ecore

it worked. 
I dont know what the difference is though. If anybody knows..... enlighten me:p Could be something about naming conventions in the "linux" comunity or something i guess.:confused:

---

### Post by foxy123 on 2005-12-04
[QUOTE=ting]
Until...
Note: you must replace **user_name** with YOUR actual user name.
Code:

sudo chown -R user:**user_name** ~/.ecore

This gave me some strange errors, but when i did it like this(i think):

sudo chown -R **user_name** ~/.ecore

said in another way:

sudo chown -R xxxxx ~/.ecore

it worked. 
I dont know what the difference is though. If anybody knows..... enlighten me:p Could be something about naming conventions in the "linux" comunity or something i guess.:confused:[/QUOTE]

it meant 'usermname:usergroup'. In Ubuntu a usergroup for a user is the same as the username (in SuSE as I remember usergroup is usually 'users'). For example, is a user name is 'ubuntuer', then this part of the HOWTO should look like:
```
sudo chown -R ubuntuer:ubuntuer ~/.ecore
```

---

### Post by ting on 2005-12-04
thanks! I hope i did't mess anything up.:p

---

### Post by Saiboogu on 2005-12-04
[QUOTE=N8K99]right now without gdm installed- when I call startx, the window manager that gets called is DR16. I'm needing a crash course in configuring to get DR17 to run. Also, how to I keep Nautilus from writing over the desktop? Do I have to remove it? I have run e17 before where I got rid of Nautilus and everything Gnome but that was when e17 came from Shadoi's repository and was contained within  main directory for programs not in /opt.  What do I need to do to get this sort of set up happening?  Perhaps after all this work when I get everything happening straight out of Enlightenment, then I'll work out a Ubuntu theme for e17![/QUOTE]


Try this - 
```
gconftool-2 /apps/nautilus/preferences/show_desktop -t bool -s false
```

If you make a theme, post it! I used e17 almost exclusively under Debian - when I switched to Ubuntu, it was the first time I'd spent much time in Gnome. Between the Ubuntu tweaks and 2.12 it was very impressive, but this Howto reminded me it was time to return to e17. Now I need themes.. :)

edit: Let me clarify, that solves the nautilus background problem. Other items, sorry - someone else can help!

---

### Post by anatole on 2005-12-04
thanks for the howto, i successfully installed e17 with it.. even i was surprised ;)
still, i dunno when i'll switch to e17, as the fileselector is still broken in the cvs...

---

### Post by N8K99 on 2005-12-04
I have ubuntu on a low ram machine which is why I sought out Enlightenment in the first place, so I have yanked Nautilus and all things Gnome off the machine and now it runs quite nicely. I still am wondering how to configure so that Entrance works from the /opt. When I was running it from the repository builds, just installing Entrance and removing GDM set everything up nicely, but now I have to do something else.

I have an idea for a theme beginning to be sketched out. I am calling it Enlightened Ubuntu. I could show you the graphical sketch, but I'm gonna wait until I get into the actual technical process before I start letting it slide out.:cool:

---

### Post by TimmyJ on 2005-12-04
I believe an ubuntu E17 theme is already in development.

You can get a sneak preview shot here: [http://www.get-e.org/Screenshots/User_Submitted/_images/ubuntu_theme_2.jpg](http://www.get-e.org/Screenshots/User_Submitted/_images/ubuntu_theme_2.jpg)

---

### Post by penvzila on 2005-12-04
Sort of worked.  I get segmentation faults when I try to use the configuration menu, and I can't remember how to install the thing that gives menu and background editing a gui.

---

### Post by daedalusman on 2005-12-05
I'm getting the following error when I run the script. I have tried it with the thintux repo and with the sourceforge repo, neither work and both produce the same error. I tried them both with clean directories, meaning I deleted the e17_cvs and e17 directories but that doesn't help either. 

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
(cd .libs && rm -f libedje.so && ln -s libedje.so.0.5.0 libedje.so)
ar cru .libs/libedje.a  libedje_la-edje_calc.o libedje_la-edje_callbacks.o libedje_la-edje_data.o libedje_la-edje_embryo.o libedje_la-edje_load.o libedje_la-edje_main.o libedje_la-edje_misc.o libedje_la-edje_program.o libedje_la-edje_smart.o libedje_la-edje_text.o libedje_la-edje_util.o libedje_la-edje_var.o libedje_la-edje_container.o libedje_la-edje_message_queue.o libedje_la-edje_cache.o libedje_la-edje_textblock_styles.o
ranlib .libs/libedje.a
creating libedje.la
(cd .libs && rm -f libedje.la && ln -s ../libedje.la libedje.la)
make[3]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje/src/lib'
Making all in bin
make[3]: Entering directory `/home/tyrion/e17_cvs/e17/libs/edje/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../bin -I../../src/lib -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include   -I/opt/e17/include  -g -O2 -MT edje_main.o -MD -MP -MF ".deps/edje_main.Tpo" \
  -c -o edje_main.o `test -f 'edje_main.c' || echo './'`edje_main.c; \
then mv -f ".deps/edje_main.Tpo" ".deps/edje_main.Po"; \
else rm -f ".deps/edje_main.Tpo"; exit 1; \
fi
/bin/sh ../../libtool --mode=link gcc  -g -O2  -L/opt/e17/lib -o edje  edje_main.o ../../src/lib/libedje.la
mkdir .libs
gcc -g -O2 -o .libs/edje edje_main.o  -L/opt/e17/lib ../../src/lib/.libs/libedje.so
../../src/lib/.libs/libedje.so: undefined reference to `eet_data_descriptor2_new'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje'
make: *** [all] Error 2
-----------------------------------------------------------------------------


```

---

### Post by foxy123 on 2005-12-05
> **daedalusman]I'm getting the following error when I run the script. I have tried it with the thintux repo and with the sourceforge repo, neither work and both produce the same error. I tried them both with clean directories, meaning I deleted the e17_cvs and e17 directories but that doesn't help either. 

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
(cd .libs && rm -f libedje.so && ln -s libedje.so.0.5.0 libedje.so)
ar cru .libs/libedje.a  libedje_la-edje_calc.o libedje_la-edje_callbacks.o libedje_la-edje_data.o libedje_la-edje_embryo.o libedje_la-edje_load.o libedje_la-edje_main.o libedje_la-edje_misc.o libedje_la-edje_program.o libedje_la-edje_smart.o libedje_la-edje_text.o libedje_la-edje_util.o libedje_la-edje_var.o libedje_la-edje_container.o libedje_la-edje_message_queue.o libedje_la-edje_cache.o libedje_la-edje_textblock_styles.o
ranlib .libs/libedje.a
creating libedje.la
(cd .libs && rm -f libedje.la && ln -s ../libedje.la libedje.la)
make[3]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje/src/lib'
Making all in bin
make[3]: Entering directory `/home/tyrion/e17_cvs/e17/libs/edje/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../bin -I../../src/lib -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include   -I/opt/e17/include  -g -O2 -MT edje_main.o -MD -MP -MF ".deps/edje_main.Tpo" \
  -c -o edje_main.o `test -f 'edje_main.c' || echo './'`edje_main.c said:**
> : *** [edje] Error 1
make[3]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/tyrion/e17_cvs/e17/libs/edje'
make: *** [all] Error 2
-----------------------------------------------------------------------------


```
have you got e17 installed before from repositories?

---

### Post by foxy123 on 2005-12-05
How to get engage into entangle? I remember that I had it before when used one of the repos. Now it is not there. Also I used to have entangle in Configuration menu (I guess it was called Menu Editor of Configuration) but now I have launch it from command line. Any way to put it in the menu?

In general, do you use ibar or engage for your programme launcher? What is ibox, btw. I thought it should place minimised programmes on the desktop, like iconbox in xfce, but I just have a white square and that's it.

---

### Post by TimmyJ on 2005-12-05
to add anything to engage or the ibar you need a .eap file. Refer to [www.get-e.org](www.get-e.org) for more information on making and editing .eaps. The Ibox does exactly what you thought it does. Whenever you iconofy a window, it's icon is stored in the Ibox.

---

### Post by TimmyJ on 2005-12-05
[QUOTE=penvzila]Sort of worked.  I get segmentation faults when I try to use the configuration menu, and I can't remember how to install the thing that gives menu and background editing a gui.[/QUOTE]

In the current state of CVS the configuration menu is very new and unstable, this is most likely why it segfaults. As for GUI configuration of backgrounds and menus, you are referring to the program entangle and emblem. These programs are installed in the e-utils package, which if you followed my directions sould be installed already. Simply run entangle and/or emblem from the command line.

---

### Post by foxy123 on 2005-12-05
[QUOTE=TimmyJ]to add anything to engage or the ibar you need a .eap file. Refer to [www.get-e.org](www.get-e.org) for more information on making and editing .eaps. The Ibox does exactly what you thought it does. Whenever you iconofy a window, it's icon is stored in the Ibox.[/QUOTE]
it is easier to do using e17menu and entangle... you run e17menu to generate eap files and then drag'n'drop them in entangle. However while I have ibar tab there, I do not have engage tab.

I've taken a look at /.e/e/applications. I've got all dirs there: all, bar, engage, favorite, restart, startup and trash. However, engage does not show up. Could be it because engage dir does not contain .eap.cache.cfg file, while all others have?

---

### Post by daedalusman on 2005-12-05
[QUOTE=foxy123]have you got e17 installed before from repositories?[/QUOTE]


I did have it installed from repos but as far as I know I have removed it completely. I have searched for allthings e17 and can't find anything that I didn't uninstall, I could be messing something but I don't know. Is there a list of things that I could use to uninstall it?

---

### Post by TimmyJ on 2005-12-05
[QUOTE=foxy123]it is easier to do using e17menu and entangle... you run e17menu to generate eap files and then drag'n'drop them in entangle. However while I have ibar tab there, I do not have engage tab.

I've taken a look at /.e/e/applications. I've got all dirs there: all, bar, engage, favorite, restart, startup and trash. However, engage does not show up. Could be it because engage dir does not contain .eap.cache.cfg file, while all others have?[/QUOTE]

It could be the others have the .eap.cache.cfg file, if that doesn't work out for you make sure there is a .order file in your engage directory

---

### Post by foxy123 on 2005-12-05
[QUOTE=daedalusman]I did have it installed from repos but as far as I know I have removed it completely. I have searched for allthings e17 and can't find anything that I didn't uninstall, I could be messing something but I don't know. Is there a list of things that I could use to uninstall it?[/QUOTE]
try libedje and also look for other libe* names to make sure that you have removed all e libraries.

---

### Post by foxy123 on 2005-12-05
[QUOTE=foxy123]I've taken a look at /.e/e/applications. I've got all dirs there: all, bar, engage, favorite, restart, startup and trash. However, engage does not show up. Could be it because engage dir does not contain .eap.cache.cfg file, while all others have?[/QUOTE]
yes, it was it. I have copied .eap.cache.cfg from all and engage tab has immediately appeared in entangle.

---

### Post by TimmyJ on 2005-12-05
[QUOTE=daedalusman]I did have it installed from repos but as far as I know I have removed it completely. I have searched for allthings e17 and can't find anything that I didn't uninstall, I could be messing something but I don't know. Is there a list of things that I could use to uninstall it?[/QUOTE]

It depends on the repo you installed from. You could try contacting that repo's maintainer to get a list of all the apps that can be installed from it.

---

### Post by N8K99 on 2005-12-05
[QUOTE=TimmyJ]I believe an ubuntu E17 theme is already in development.

You can get a sneak preview shot here: [http://www.get-e.org/Screenshots/User_Submitted/_images/ubuntu_theme_2.jpg](http://www.get-e.org/Screenshots/User_Submitted/_images/ubuntu_theme_2.jpg)[/QUOTE]

Oh that is so much better than what I had going on my sketchpad! Well, I will have to adjust a bit or wait. Still wondering how to get entrance to start up when I turn the computer on. Anybody know how to configure X11?

---

### Post by tuke81 on 2005-12-05
> The mostly incredible and really unbelivable has become true:
You compiled e17 sucessfully!

\O/:D :p ;) 

Heh heh works fine thanks, btw I was installed it before from there
[QUOTE=alingatong]try this guide.

[https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php)[/QUOTE] too.

So it seems to work with both how-tos. And I DIDNT uninstall it before i installed
this like is adviced in this how-to... So make sure that all those packages are installed:
```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev
```
, before you try this it should work.:cool:

---

### Post by N8K99 on 2005-12-06
ok thus far I have sort of solved my problem. Since I have completely removed anything Gnome related from my system, there was no way for me to go straight into enlightenment upon powering up. Well, now when I type [SIZE="1"]startx[/SIZE], enlightenment is started as well. I had to create my own .xinitrc file in my home directory. Well duh! you may say, bu I did not know that and it took some exploring the many rooms of the UNIX tower and discovering that the Archmages who had come before me wrote a manual for everything (or nearly everything.) 
Now, I must figure out how to put startx into the boot cycle - and also how to configure entrance to work properly.

---

### Post by foxy123 on 2005-12-06
I wonder if CVS is broken at the moment. I ran the script today and got this error:
```
evfscat.o: In function `callback':
/home/foxy/CVS/e17_cvs/e17/apps/evfs/src/bin/evfscat.c:21: undefined reference t o `evfs_client_file_read'
/home/foxy/CVS/e17_cvs/e17/apps/evfs/src/bin/evfscat.c:21: undefined reference t o `evfs_client_file_read'
evfscat.o: In function `main':
/home/foxy/CVS/e17_cvs/e17/apps/evfs/src/bin/evfscat.c:42: undefined reference t o `evfs_client_file_open'
collect2: ld returned 1 exit status
make[3]: *** [evfscat] Error 1

```

---

### Post by foxy123 on 2005-12-06
> We are ommiting the library emotion and the video player eclair because they require a newer version of a library (xinelib I believe) than the one available in the ubuntu repositories.
so there is no way to install eclair? I sort of like its design :)

---

### Post by TimmyJ on 2005-12-06
[QUOTE=foxy123]so there is no way to install eclair? I sort of like its design :)[/QUOTE]

Well, technically there is no way to install emotion...which eclair depends on. Once finals are over I plan on adding a few more things to this how-to (entrance and how to get the newest xine-lib so that emotion and eclair will work). Thanks for all the feedback guys.

---

### Post by foxy123 on 2005-12-06
[QUOTE=TimmyJ]Well, technically there is no way to install emotion...which eclair depends on. Once finals are over I plan on adding a few more things to this how-to (entrance and how to get the newest xine-lib so that emotion and eclair will work). Thanks for all the feedback guys.[/QUOTE]
you can also mentioned how to install modules and activate them:

1. Download modules you like from [http://www.get-e.org/Resources/Modules/](http://www.get-e.org/Resources/Modules/)
2. Untar them 

```
tar xfvz <source>
``` for *.tar.gz or 
```
tar xfvj <source>
``` for *tar.bz2

cd to source directory

For all modules except evolume:
```
./autogen.sh --libdir=/opt/e17/lib
make
make install
```

For evolume
Make sure that you added /opt/e17/lib in /etc/ld.so.conf and run
```
sudo ldconfig
```
```
./configure --libdir=/opt/e17/lib
make
make install
```

The mudules will be installed in ~/.e/e/modules/

If you would like to install them to /opt/e17, then you should use
--prefix=/opt/e17 and sudo with 'make install'.

To load modules use:
```
enlightenment_remote -module-load <module_name>
```

To enable it go to the menu (right-click on desktop) Modules - Module Name - Enable

I have also attached my screenshot made with 'screenshot' module with the following modules: rain, weather, evolume, engage, moon and screenshot.

---

### Post by TimmyJ on 2005-12-06
Thx for the help foxy! I shoulda added that from the get-go...I love my modules :-P. Anyways, do you think I should add this to the original how-to on the first page, or would that make it too long? Is there a way I can say "check out how to install modules here:" then just link to that specific post?

---

### Post by foxy123 on 2005-12-06
[QUOTE=TimmyJ]Thx for the help foxy! I shoulda added that from the get-go...I love my modules :-P. Anyways, do you think I should add this to the original how-to on the first page, or would that make it too long? Is there a way I can say "check out how to install modules here:" then just link to that specific post?[/QUOTE]
just put this link:
[http://ubuntuforums.org/showpost.php?p=548898&postcount=58](http://ubuntuforums.org/showpost.php?p=548898&postcount=58)

---

### Post by foxy123 on 2005-12-06
I've figured out how to install eclair. Jus installed new libxine from source with /opt/e17 prefix. After that emotion and eclair are compiled fine.

So another challenge is evidence. Not only I have to download it separately, the damned thing does not compile. Give me the error:

```
In file included from ttf.c:20:
../../../src/gui/efl/common/evas_macros.h:49: error: syntax error before '*' token
../../../src/gui/efl/common/evas_macros.h:49: error: syntax error before 'Evas'
../../../src/gui/efl/common/evas_macros.h:49: warning: type defaults to 'int' in declaration of 'evas_thumbnail_dead'
../../../src/gui/efl/common/evas_macros.h:49: warning: data definition has no type or storage class
../../../src/gui/efl/common/evas_macros.h:50: error: syntax error before '*' token
../../../src/gui/efl/common/evas_macros.h:50: error: syntax error before 'Evas'
../../../src/gui/efl/common/evas_macros.h:50: warning: type defaults to 'int' in declaration of 'evas_thumbnail_live'
../../../src/gui/efl/common/evas_macros.h:50: warning: data definition has no type or storage class
../../../src/gui/efl/common/evas_macros.h:51: error: syntax error before '*' token
../../../src/gui/efl/common/evas_macros.h:51: error: syntax error before 'Evas'
../../../src/gui/efl/common/evas_macros.h:51: warning: type defaults to 'int' in declaration of 'evas_thumbnail_dead_or_alive'
../../../src/gui/efl/common/evas_macros.h:51: warning: data definition has no type or storage class
../../../src/gui/efl/common/evas_macros.h:53: error: syntax error before '*' token
../../../src/gui/efl/common/evas_macros.h:53: error: syntax error before '*' token
../../../src/gui/efl/common/evas_macros.h:53: warning: type defaults to 'int' in declaration of 'evas_object_from_imlib_image'
../../../src/gui/efl/common/evas_macros.h:53: warning: data definition has no type or storage class
../../../src/gui/efl/common/evas_macros.h:55: error: syntax error before '*' token
../../../src/gui/efl/common/evas_macros.h:55: warning: type defaults to 'int' in declaration of 'get_evas_from_iconlist'
../../../src/gui/efl/common/evas_macros.h:55: warning: data definition has no type or storage class
ttf.c:166: error: syntax error before '*' token
ttf.c:166: warning: return type defaults to 'int'
ttf.c: In function 'live':
ttf.c:169: error: 'Evas_Object' undeclared (first use in this function)
ttf.c:169: error: (Each undeclared identifier is reported only once
ttf.c:169: error: for each function it appears in.)
ttf.c:169: error: 'o' undeclared (first use in this function)
ttf.c:276: error: 'Evas' undeclared (first use in this function)
ttf.c:276: error: syntax error before ')' token
make[4]: *** [ttf.lo] Error 1
make[4]: Leaving directory `/home/foxy/CVS/evidence/src/thumbnailer/ttf'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/foxy/CVS/evidence/src/thumbnailer'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/foxy/CVS/evidence/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/foxy/CVS/evidence'
make: *** [all] Error 2

```

---

### Post by xyz on 2005-12-07
Hi-
First of all thank you for bearing in mind this a newbie writing.
Following tutorials on the site,E17 seems to be accessible and it looks very nice but I can't choose to go Gnome,Failsafe,Enlightenment and so on.
And whatever happened to my Application - System -Places -Panel - Add to Panel,etc.....??None of those in sight on desktop.
Excuse me if this is stupid but I just had to ask someone.

---

### Post by synd7 on 2005-12-08
I've just used the script and it works greak but i noticed that theres no sign of evidence (file manager) and examine (configuration stuff).
Is there some way to add them into the script cos im sick of using an unskinned nautilus for file browsing.

I kniw that i could do them manually but then the script wouldnt update everything.

---

### Post by foxy123 on 2005-12-08
[QUOTE=synd7]I've just used the script and it works greak but i noticed that theres no sign of evidence (file manager) and examine (configuration stuff).
Is there some way to add them into the script cos im sick of using an unskinned nautilus for file browsing.

I kniw that i could do them manually but then the script wouldnt update everything.[/QUOTE]
you may try to compile it separately, though it looks like it has not being developed for a while: the last CVS commit was in July. E now has its integrated file manager EFM (Files item in the menu), it is buggy (you may need to call it twice or resize to see the files), but it provides basic features.

---

### Post by foxy123 on 2005-12-08
BTW, the script has been updated to use a new mirror and compile imlib2 library. And another thing, you do not need to run script with sudo, it will ask you for the password.

---

### Post by vaskark on 2005-12-08
Great HOWTO. But why isn't the e_modules packages built? That's where the flame module is ...

Also, in the ~/e17_cvs directory that's created I think the 'misc' folder gets downloaded twice (~/e17_cvs/misc and ~/e17_cvs/e17/misc).

---

### Post by TimmyJ on 2005-12-08
There is no longer any e_modules package in the e17 CVS tree. Seperate modules are now only available through [www.get-e.org](www.get-e.org)

---

### Post by TimmyJ on 2005-12-08
The script used in this tutorial has gone through some changed very recently (noted above by Foxy). This may require certain parts of this HOW-TO to be unneccesary or changed (namely messing with the permissions).

I suggest anyone that has used this how-to to re-download the new script due to the change in mirrors it downloads from. For this to work you must remove the /e17_cvs directory and then re-run the script (try this w/out sudo and tell me how it works :))

---

### Post by buildid on 2005-12-08
iam getting this one :

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entice ..................... ok
- entrance ................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/entrance.log:
-----------------------------------------------------------------------------
  -k <key> must be specified for all commands except -a

You need to specify a command!
Usage: ecore_config -c <file> <command> [-k key]
Modify ecore_config files

Accepted commands:
  -a          get all keys
  -g          get key
  -d          delete key
  -b <value>  set boolean
  -f <value>  set float
  -i <value>  set integer
  -n          set nil
  -r <value>  set RGBA
  -s <value>  set string
  -t <value>  set theme

  -k <key> must be specified for all commands except -a

make[2]: *** [entrance_config.cfg] Fout 2
make[2]: Leaving directory `/home/buildid/e17_cvs/e17/apps/entrance/data/config'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/buildid/e17_cvs/e17/apps/entrance/data'
make: *** [all-recursive] Fout 1
-----------------------------------------------------------------------

---

### Post by vaskark on 2005-12-08
[quote=TimmyJ]There is no longer any e_modules package in the e17 CVS tree. Seperate modules are now only available through [www.get-e.org]("http://www.get-e.org")[/quote]Okey dokey.

---

### Post by xyz on 2005-12-09
Hi-
First,thank you for the guide.It worked and installed like a charm as far as a newbie can tell...except for:
At log-in,I want to pick Session-->E17 and I get:
> Xsession unable to launch "/opt/e17/bin/enlightenment"
Xsession -- "/opt/bin/enlightenment not found;falling back to default session
What did I do wrong?Thanks for your help.

---

### Post by foxy123 on 2005-12-09
[QUOTE=buildid]iam getting this one :

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entice ..................... ok
- entrance ................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/entrance.log:
-----------------------------------------------------------------------------
  -k <key> must be specified for all commands except -a

You need to specify a command!
Usage: ecore_config -c <file> <command> [-k key]
Modify ecore_config files

Accepted commands:
  -a          get all keys
  -g          get key
  -d          delete key
  -b <value>  set boolean
  -f <value>  set float
  -i <value>  set integer
  -n          set nil
  -r <value>  set RGBA
  -s <value>  set string
  -t <value>  set theme

  -k <key> must be specified for all commands except -a

make[2]: *** [entrance_config.cfg] Fout 2
make[2]: Leaving directory `/home/buildid/e17_cvs/e17/apps/entrance/data/config'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/home/buildid/e17_cvs/e17/apps/entrance/data'
make: *** [all-recursive] Fout 1
-----------------------------------------------------------------------[/QUOTE]
it should be fixed by now...

---

### Post by buildid on 2005-12-09
thanks running enlightment now , great work ....

---

### Post by N8K99 on 2005-12-09
Just want to know, can I move the contents of /opt/e17 into my directory tree like the regular packages on my computer so that I no longer have to type /opt/e17/bin/enlightenment_remote to call eutils? I guess my question is, if I have no Gnome stuff or KDE for that matter, in fact it's only enlightenment on my machine- can it reside in my directory tree or must I leave it all in the  /opt directory?

---

### Post by TimmyJ on 2005-12-10
[QUOTE=N8K99]Just want to know, can I move the contents of /opt/e17 into my directory tree like the regular packages on my computer so that I no longer have to type /opt/e17/bin/enlightenment_remote to call eutils? I guess my question is, if I have no Gnome stuff or KDE for that matter, in fact it's only enlightenment on my machine- can it reside in my directory tree or must I leave it all in the  /opt directory?[/QUOTE]

Well, there are a couple things you can do. The easiest by far is adding /opt/e17/bin to your PATH. This means that you can type any command in the /opt/e17/bin directory w/out using the prefix '/opt/e17/bin'. There are instructions on how to do this on the first post. Another possibility is when using the script, you can change where you want it to installs, open the script with any text editor and you will find instructions there. But, to answer your question, enlightenment can reside anywhere on your system. It is completely relocatable. The reason this script uses /opt/e17 is that so it does not interfere w/ any other versions of enlightenment one may have.

---

### Post by N8K99 on 2005-12-10
It's not a weekend without me spending time re-configuring my system. Due to another crash that was self-inflicted, I had to once again reinstall the base system. No problem, but I opted to return to Shadoi's repository for it was not nearly as troublesome to set up to operational levels. I tried to follow the posted howto to add /opt/e17 to my PATH but something did not work out properly. And I had difficulty getting Entrance to operate. By returning to the repository I was able to get a good somewhat solid version running. I'm sure that in a couple of weeks when I have to do this again, there will be new options which I am willing to pursue. I do prefer Enlightenemnt over GNOME or KDE so am looking forward to the work progressing on e17.

---

### Post by bored2k on 2005-12-10
Is Entrance safe enough to use? I've been using E17 for about a week now and I havent used Entrance out of fear of it messing up.

---

### Post by TimmyJ on 2005-12-10
[QUOTE=bored2k]Is Entrance safe enough to use? I've been using E17 for about a week now and I havent used Entrance out of fear of it messing up.[/QUOTE]

Entrance is in a kind of unique position right now. Many people use and love it, I am currently not one of those people. I've used it in the past and managed to struggle through a few problems and get it working, but I've also seen many people who can't for the life of them get it working sucessfully. On top of this the development of Entrance has been very stagnant lately. I'd suggest that if you really want the extra eye candy in your login manager give it a try, you got a pretty good shot at getting it to work, but if it doesn't work for you and/or you find that its missing some features you want. Just ditch it.

---

### Post by Jona on 2005-12-12
A little late in the game (in the cutting edge world of cvs repositories, 24 hours is too late ;-) ), but I've managed to come up with yet another edje error, much like the one benplaut and daedalusman submitted, although with other error messages. I've also installed e16 and e17 before, but I've done my best to remove all e libraries, especially those related to edje. Any suggestions as to what I might be doing wrong?

```

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
edje_data.c:59: error: `EET_DATA_DESCRIPTOR_CLASS_VERSION' undeclared (first use  in this function)
edje_data.c:76: warning: assignment makes pointer from integer without a cast
edje_data.c:82: warning: assignment makes pointer from integer without a cast
edje_data.c:89: warning: assignment makes pointer from integer without a cast
edje_data.c:98: warning: assignment makes pointer from integer without a cast
edje_data.c:105: warning: assignment makes pointer from integer without a cast
edje_data.c:112: warning: assignment makes pointer from integer without a cast
edje_data.c:119: warning: assignment makes pointer from integer without a cast
edje_data.c:126: warning: assignment makes pointer from integer without a cast
edje_data.c:133: warning: assignment makes pointer from integer without a cast
edje_data.c:141: warning: assignment makes pointer from integer without a cast
edje_data.c:155: warning: assignment makes pointer from integer without a cast
edje_data.c:161: warning: assignment makes pointer from integer without a cast
edje_data.c:168: warning: assignment makes pointer from integer without a cast
edje_data.c:188: warning: assignment makes pointer from integer without a cast
edje_data.c:194: warning: assignment makes pointer from integer without a cast
edje_data.c:270: warning: assignment makes pointer from integer without a cast
edje_data.c:292: warning: assignment makes pointer from integer without a cast
make[3]: *** [libedje_la-edje_data.lo] Error 1
make[3]: Leaving directory `/home/ion/e17_cvs/e17/libs/edje/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ion/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ion/e17_cvs/e17/libs/edje'
make: *** [all] Error 2

```

---

### Post by thewayofzen on 2005-12-16
Has anyone documented exactly what needs to be done to remove all the files/changes that are made/created with the installation of e17?

any help would be appreciated.

thewayofzen

---

### Post by foxy123 on 2005-12-16
[QUOTE=thewayofzen]Has anyone documented exactly what needs to be done to remove all the files/changes that are made/created with the installation of e17?

any help would be appreciated.

thewayofzen[/QUOTE]
what do you mean by > the installation of e17? If you mean this script then all you need is to delete /opt/e17 and maybe the .desktop file in xsessions. There are other ways of installing E17 so you should be mre specific...

---

### Post by yoshic on 2005-12-19
hi!! thanks for write this how-to an the script, i've just donwloaded and installed e17, works great!!1

---

### Post by firecat53 on 2005-12-23
Do I need to do anything special to use the script to continue to update my e17 install?  When I just ran the ./easy_e17.sh -i --skip=emotion,eclair command from my working installation, it went through and appeared to update the existing CVS tree, but then stopped without compiling anything.

Do I need to delete the CVS tree each time (which would seem contrary to the purpose of CVS!) or delete the /opt/e17 directory?

By the way, it works great the first time :)

Thanks, Scott

---

### Post by foxy123 on 2005-12-23
[QUOTE=firecat53]Do I need to do anything special to use the script to continue to update my e17 install?  When I just ran the ./easy_e17.sh -i --skip=emotion,eclair command from my working installation, it went through and appeared to update the existing CVS tree, but then stopped without compiling anything.

Do I need to delete the CVS tree each time (which would seem contrary to the purpose of CVS!) or delete the /opt/e17 directory?

By the way, it works great the first time :)

Thanks, Scott[/QUOTE]
no, just run it regularly, it should update everything that has been changed...

---

### Post by venice on 2005-12-24
Followed the instructions, waited and voila. Enlightenment works beautifully. Thank you.

Quoestion - where can I find a forum about E17? Or can I ask questions on Ubuntu forum?

thanks,
venice

---

### Post by N8K99 on 2005-12-24
[QUOTE=venice]Followed the instructions, waited and voila. Enlightenment works beautifully. Thank you.

Quoestion - where can I find a forum about E17? Or can I ask questions on Ubuntu forum?

thanks,
venice[/QUOTE]
[http://edevelop.org/forum](http://edevelop.org/forum)

---

### Post by buildid on 2005-12-24
i also tried to update after 2 weeks of using e17 , it seems nothing is updated , is that correct ?

no compiling of updated parts is what i ment ...

not used to cvs so i ask to make sure iam right ...

thank you

---

### Post by foxy123 on 2005-12-24
[QUOTE=buildid]i also tried to update after 2 weeks of using e17 , it seems nothing is updated , is that correct ?

no compiling of updated parts is what i ment ...

not used to cvs so i ask to make sure iam right ...

thank you[/QUOTE]
no, CVS is updated several times almost every day. The problem could be with thinktux mirror which is used in easy_e17 script. It's been recently mentioned on the e17 mailing list that it is not updated properly. You can use get_e script from [here]("http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script")

---

### Post by buildid on 2005-12-24
have changed install pad to /opt/e17 , but get some messages , i do have a "new" trick :

=> Checking cvs presence...
=> Checking `autoconf' presence...
=> Checking `automake' presence...
=> Checking sudo access...
=> Checking /etc/ld.so.conf sanity...
| /etc/ld.so.conf paths don't contain e17 libs' path.               |
| Add /opt/e17l/lib to /etc/ld.so.conf please.
---------------------------------------------------------------------
buildid@Breezy:~$ 

i suppose i should wait till the original script is working correctly before i kill my e17,


"fixed my fault"

---

### Post by foxy123 on 2005-12-25
[QUOTE=buildid]have changed install pad to /opt/e17 , but get some messages , i do have a "new" trick :

=> Checking cvs presence...
=> Checking `autoconf' presence...
=> Checking `automake' presence...
=> Checking sudo access...
=> Checking /etc/ld.so.conf sanity...
| /etc/ld.so.conf paths don't contain e17 libs' path.               |
| Add /opt/e17l/lib to /etc/ld.so.conf please.
---------------------------------------------------------------------
buildid@Breezy:~$ 

i suppose i should wait till the original script is working correctly before i kill my e17,


"fixed my fault"[/QUOTE]
just add "/opt/e17/lib" to /etc/ld.so.conf  and run it again....

---

### Post by venice on 2005-12-25
[QUOTE=foxy123]no, CVS is updated several times almost every day. The problem could be with thinktux mirror which is used in easy_e17 script. It's been recently mentioned on the e17 mailing list that it is not updated properly. You can use get_e script from [here]("http://dev.winged.it/download/enlightened_stuff/enlightenment_updater_script")[/QUOTE]

Well I downloaded the script but it does not work. Sorry for being a noob but when i type (under gnome)

sudo ./get_e.sh

it gives me: command not found

thanks,
venice

---

### Post by foxy123 on 2005-12-25
[QUOTE=venice]Well I downloaded the script but it does not work. Sorry for being a noob but when i type (under gnome)

sudo ./get_e.sh

it gives me: command not found

thanks,
venice[/QUOTE]
first of all, do not run it as sudo, the script will ask you to enter sudo password. Then, you may want to change the prefix in the script to /opt/e17, if you want your e17 installation to go there. Otherwise it will be in /usr/local, which is also fine. The main duifference is that if you want to remove e17 in the future for some reasons it will be easier to do with /opt, because all you have to do will be to remove e17 directory from there.

BTW, the difference between easy_e17 and get_e scripts is also that get_e installs extra modules systemwide, while easy_e17 does not install them at all. So you have to follow a small howto from this thread to do it.

---

### Post by MaX on 2005-12-25
[QUOTE=venice]Well I downloaded the script but it does not work. Sorry for being a noob but when i type (under gnome)

sudo ./get_e.sh

it gives me: command not found

thanks,
venice[/QUOTE]

try ```
sh get_e.sh
```

---

### Post by venice on 2005-12-25
Thank you very much.

Also there is another thing I'd like to ask: After installing E17 I don't have the "Modules" section under the left-mouse-button menu. Is that normal? It won't apear after installing new modules (such as rain, snow etc)

thanks,
venice

---

### Post by foxy123 on 2005-12-25
[QUOTE=venice]Thank you very much.

Also there is another thing I'd like to ask: After installing E17 I don't have the "Modules" section under the left-mouse-button menu. Is that normal? It won't apear after installing new modules (such as rain, snow etc)

thanks,
venice[/QUOTE]

it's been recently changed. Now you have to go to Configuration Panel and there is a modules section there....

---

### Post by venice on 2005-12-25
I've noticed that. Thank you. I just thought there might be a chance to edit the menu under the mouse button so it could satisfy my needs

thanks again,
venice

---

### Post by toma222 on 2005-12-29
Hi,
First of all, sorry for my english (I'm French). I used this great how to and it worked well for me. But since yesterday, when I try to update my e17, I have an error on ecore's compilation. Does anybody have the same problem ? Thanks.

---

### Post by foxy123 on 2005-12-29
[QUOTE=toma222]Hi,
First of all, sorry for my english (I'm French). I used this great how to and it worked well for me. But since yesterday, when I try to update my e17, I have an error on ecore's compilation. Is anybody have the same problem ?[/QUOTE]

I've got an error with e_utils. It is quite common with CVS to break something occasionally.

---

### Post by toma222 on 2005-12-29
Ok, so I'll wait. Thank you.

---

### Post by toma222 on 2005-12-30
For my trouble with ecore, it not seem to be because of CVS, with an other script it work. But I have a trouble with some modules (engage, eloquence, evolume), I have this error : "undefined symbol : e_modapi_config" (they worked before update). Does somebody else have this ?

---

### Post by buildid on 2005-12-31
i have trouble with everything :-)

buildid@Breezy:~$ sh get_e.sh
---------------------------------------------------------------------

=> Checking cvs presence...
=> Checking `autoconf' presence...
=> Checking `automake' presence...
=> Checking sudo access...
=> Checking /etc/ld.so.conf sanity...
---------------------------------------------------------------------

Just hit enter for the cvs password!
Logging in to :pserver:anonymous@cvs.sourceforge.net:2401/cvsroot/enlightenment
CVS password: 

---------------------------------------------------------------------
  Checkout/update...
---------------------------------------------------------------------
=> Updating e17...
~/e17 ~
  ..updating CVS tree, please wait...
cvs update: warning: cannot make directory CVS in .: Permission denied
cvs update: in directory apps/evfs/autom4te.cache:
cvs update: cannot open CVS/Entries for reading: No such file or directory
cvs update: warning: cannot make directory CVS in .: Permission denied
cvs update: in directory apps/evfs/autom4te.cache:
cvs update: cannot open CVS/Entries for reading: No such file or directory
cvs update: warning: cannot make directory CVS in .: Permission denied
cvs update: in directory apps/evfs/autom4te.cache:
cvs update: cannot open CVS/Entries for reading: No such file or directory

---

### Post by drfalkor on 2005-12-31
```
sudo ./easy_e17.sh -i --skip=emotion,eclair
```

And, then:

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... SKIPPED
- ewl ........................ ok
- engrave .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engrave.log:
-----------------------------------------------------------------------------
Running aclocal...
Running autoheader...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7013: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running autoconf...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7013: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running libtoolize...
Running automake...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
-----------------------------------------------------------------------------

```

What now ? 
By the way, I'm running Kubuntu breezy .

---

### Post by foxy123 on 2005-12-31
[QUOTE=drfalkor]```
sudo ./easy_e17.sh -i --skip=emotion,eclair
```

And, then:

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... SKIPPED
- ewl ........................ ok
- engrave .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engrave.log:
-----------------------------------------------------------------------------
Running aclocal...
Running autoheader...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7013: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running autoconf...
configure.in:17: warning: AC_PROG_LEX invoked multiple times
autoconf/programs.m4:438: AC_DECL_YYTEXT is expanded from...
aclocal.m4:7013: AM_PROG_LEX is expanded from...
configure.in:17: the top level
Running libtoolize...
Running automake...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
Makefile.am:2: require version 1.5, but have 1.4-p6
src/bin/Makefile.am:1: require version 1.5, but have 1.4-p6
-----------------------------------------------------------------------------

```

What now ? 
By the way, I'm running Kubuntu breezy .[/QUOTE]
upgrade your automake to 1.7 or higher

---

### Post by drfalkor on 2006-01-01
[QUOTE=foxy123]upgrade your automake to 1.7 or higher[/QUOTE]
Thank you, that worked. But another thing:

```
falkor@ubuntu:~$ sudo chown -R user:falkor ~/.ecore
Password:
chown: «user:falkor»: ugyldig bruker // not a user or something in english
falkor@ubuntu:~$

```

huh ? hmm, I try to do this

```
falkor@ubuntu:~$ users
falkor
falkor@ubuntu:~$

```

What now ? :p

---

### Post by veloct on 2006-01-01
```
sudo chown -R falkor:falkor ~/.ecore
```

---

### Post by drfalkor on 2006-01-01
[QUOTE=veloct]```
sudo chown -R falkor:falkor ~/.ecore
```[/QUOTE]
aaah, here we go :p Got it to work, looks very nice - but its crashes alot ! :(

---

### Post by foxy123 on 2006-01-01
[QUOTE=drfalkor]aaah, here we go :p Got it to work, looks very nice - but its crashes alot ! :([/QUOTE]

it's been not in its most stable state for the last few days...

---

### Post by drfalkor on 2006-01-01
[QUOTE=foxy123]it's been not in its most stable state for the last few days...[/QUOTE]
Not for me. When I'm trying to open a folder or something it comes a message like "This is not a bug ..etc...etc..." and then I can chose to ignore, restart or exit, and then "POW"- back to the login screen again :mad:

EDIT:Wooops, did I misunderstand ?

---

### Post by synd7 on 2006-01-01
ok, got this thing working great. damn i love enlightenment:) 

what i want to know is how to select a gtk2 theme for enlightenment, im sick of having the crappy standard coloured panels in gaim etc.

---

### Post by drfalkor on 2006-01-02
I think it's working now without crashing all the time. What did I do ? Well, I deleted the cvs_dir and runned the script all over again - Wolla, here I am... :p

---

### Post by drfalkor on 2006-01-02
I'm trying to compile engage... I followed this howto
[http://ubuntuforums.org/showpost.php?p=548898&postcount=58](http://ubuntuforums.org/showpost.php?p=548898&postcount=58)

When I do a 
```
./autogen.sh --libdir=/opt/e17/lib
```

I get this little troll:mad: 
```
checking for esmart-config... no
checking for esmart - version >= 0.0.2... no
*** The esmart-config script installed by esmart could not be found
*** If esmart was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESMART_CONFIG environment variable to the
*** full path to esmart-config.
configure: error: Cannot find esmart: Is esmart-config in path?
falkor@ubuntu:~/Desktop/engage$
```
hmm, Where do I get esmart ? and how do I install it ? 

Thnx for you'r help :)

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]I'm trying to compile engage... I followed this howto
[http://ubuntuforums.org/showpost.php?p=548898&postcount=58](http://ubuntuforums.org/showpost.php?p=548898&postcount=58)

When I do a 
```
./autogen.sh --libdir=/opt/e17/lib
```

I get this little troll:mad: 
```
checking for esmart-config... no
checking for esmart - version >= 0.0.2... no
*** The esmart-config script installed by esmart could not be found
*** If esmart was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the ESMART_CONFIG environment variable to the
*** full path to esmart-config.
configure: error: Cannot find esmart: Is esmart-config in path?
falkor@ubuntu:~/Desktop/engage$
```
hmm, Where do I get esmart ? and how do I install it ? 

Thnx for you'r help :)[/QUOTE]
engage should compile fine with the script

---

### Post by drfalkor on 2006-01-02
[QUOTE=foxy123]engage should compile fine with the script[/QUOTE]
I could not see engage under the modules menu- have I done something wrong ? or do I need to config something ?

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]I could not see engage under the modules menu- have I done something wrong ? or do I need to config something ?[/QUOTE]

It was a bug I guess... try
```
enlightenment_remote -module-load engage
```

---

### Post by drfalkor on 2006-01-02
```
falkor@ubuntu:~$ enlightenment_remote -module-load engage
bash: enlightenment_remote: command not found

```

I even tryed with sudo :???:

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]```
falkor@ubuntu:~$ enlightenment_remote -module-load engage
bash: enlightenment_remote: command not found

```

I even tryed with sudo :???:[/QUOTE]

But you have e installed, have not you? enlightment_remote is a part of e as I understand...

---

### Post by drfalkor on 2006-01-02
I have followed the howto 100% :p

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]I have followed the howto 100% :p[/QUOTE]

it looks like e has not compiled for you... which is strange if you did not have any errors... what script have you used?
EDIT: what have you got if you put 'enlightenment' in the command line (without quotation marks) and hit TAB twice?

---

### Post by drfalkor on 2006-01-02
I used the script in this howto :smile:

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]I used the script in this howto :smile:[/QUOTE]
what have you got if you put 'enlightenment' in the command line (without quotation marks) and hit TAB twice?

---

### Post by drfalkor on 2006-01-02
I get nothing

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]I get nothing[/QUOTE]
it is quite strange... have you got /opt/e17/lib in /etc/ld.so.conf?

---

### Post by drfalkor on 2006-01-02
Jepp... hmmmm :confused:
I feel like the only one in the universe with this problem

---

### Post by foxy123 on 2006-01-02
[QUOTE=drfalkor]Jepp... hmmmm :confused:
I feel like the only one in the universe with this problem[/QUOTE]

try to rebuild it

---

### Post by drfalkor on 2006-01-02
Doing it right now- on the line 24: e17_apps="entrance e eclair evfs", I added e_utils to the list.. like this:

e17_apps="entrance e eclair evfs e_utils" 
(thank you Goeland86)

:p

---

### Post by TimmyJ on 2006-01-02
sry if this was already mentioned, but make SURE that '/opt/e17/bin' is in your path. If its not then none of the commands will work (unless you add the /opt/e17/bin prefix to all your enlightenment commands). If your not sure if it is in your path or not then use this command and copy/paste the results.

```
echo $PATH
```

---

### Post by drfalkor on 2006-01-03
```
falkor@ubuntu:~$ echo $PATH
/home/falkor/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games

```

---

### Post by daedalusman on 2006-01-07
Well this worked for me in the past under gnome but since then I have reinstalled and am now using KDE 3.5 and I am getting this error...

```
cvs checkout: warning: failed to open /home/aegon/.cvspass for reading: No such file or directory
can't create temporary directory /tmp/cvs-serv13074
No space left on device
FAILED! Next attempt 2 in 1 seconds
```


I am running the script as sudo. I have no idea how to get past this bit. Thanks for any help.

Oh and I most definitely have enough disk space.

---

### Post by foxy123 on 2006-01-07
[QUOTE=daedalusman]Well this worked for me in the past under gnome but since then I have reinstalled and am now using KDE 3.5 and I am getting this error...

```
cvs checkout: warning: failed to open /home/aegon/.cvspass for reading: No such file or directory
can't create temporary directory /tmp/cvs-serv13074
No space left on device
FAILED! Next attempt 2 in 1 seconds
```


I am running the script as sudo. I have no idea how to get past this bit. Thanks for any help.

Oh and I most definitely have enough disk space.[/QUOTE]
do not run it as sudo.... also it was reported today that there was a problem with cvs, so wait for some time...

btw, easy_e17 script has been updted. Advice is the same delete your previous cvs directory before running a new version....

---

### Post by malefestra on 2006-01-07
[QUOTE=foxy123]do not run it as sudo.... also it was reported today that there was a problem with cvs, so wait for some time...

btw, easy_e17 script has been updted. Advice is the same delete your previous cvs directory before running a new version....[/QUOTE]

I'll wait for a bit to see if it's a problem with CVS, but I'm receiving the same error message as daedalusman.

I've run it as sudo and not as sudo, both give the same error message.

---

### Post by foxy123 on 2006-01-08
cvs has been fixed. I recommend to update easy_e17 script and remove your source directory before running it. I guess you do not need to use any exeption as it's said in the HOWTO since xine dependency has been fixed. However, I am not sure since I installed new xine to my /opt/e17.

The script now build modules, which are in the cvs (calendar flame monitor mount rain screenshot slideshow snow tclock weather). Please not that calendar does not work at the moment. Should be fixed shortly thogh.

---

### Post by malefestra on 2006-01-08
[QUOTE=foxy123]cvs has been fixed. I recommend to update easy_e17 script and remove your source directory before running it. I guess you do not need to use any exeption as it's said in the HOWTO since xine dependency has been fixed. However, I am not sure since I installed new xine to my /opt/e17.

The script now build modules, which are in the cvs (calendar flame monitor mount rain screenshot slideshow snow tclock weather). Please not that calendar does not work at the moment. Should be fixed shortly thogh.[/QUOTE]

I have e17 up and running now, however, am clueless as to how to start entangle.  I believe it's part of the e_utils package, which looks like it installs with the script.  Also, how are those modules (rain, flame, etc.) accessed?

---

### Post by daedalusman on 2006-01-08
I'm still getting this error after downloading the new script and deleting the cvs folder...

```
CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...
cvs checkout: warning: failed to open /home/aegon/.cvspass for reading: No such file or directory
cvs [checkout aborted]: received interrupt signal
FAILED! Next attempt 2 in 3 seconds
```

---

### Post by durand on 2006-01-08
[QUOTE=foxy123]I've got the same problem :([/QUOTE]
And I have that problen as well! I just ran the script and no change since the last time i ran it 4 days ago.:mad: I tried compiling ecore separately using [https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php) but the easy_e17 script doesn't recognise that it's installed...:cry:

---

### Post by foxy123 on 2006-01-08
[QUOTE=malefestra]I have e17 up and running now, however, am clueless as to how to start entangle.  I believe it's part of the e_utils package, which looks like it installs with the script.  Also, how are those modules (rain, flame, etc.) accessed?[/QUOTE]

For entangle just type 'entangle' in terminal or in Run Command.

For modules go to Configuration/Configuraion Panel/Module Settings in the menu.

---

### Post by foxy123 on 2006-01-08
[QUOTE=daedalusman]I'm still getting this error after downloading the new script and deleting the cvs folder...

```
CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...
cvs checkout: warning: failed to open /home/aegon/.cvspass for reading: No such file or directory
cvs [checkout aborted]: received interrupt signal
FAILED! Next attempt 2 in 3 seconds
```[/QUOTE]

are you running it with sudo? anyway, just let it run, the access to cvs is patchy sometimes...

---

### Post by daedalusman on 2006-01-08
[QUOTE=foxy123]are you running it with sudo? anyway, just let it run, the access to cvs is patchy sometimes...[/QUOTE]


Ok well I let it run and it made it through but I wanted emotion and eclair so I installed the latest versions of xinelib and xine-ui from their site. Emotion installed with no problems but I got this problem when it got to eclair.

```
LAST LOGLINES FROM /tmp/easy_e17/install_logs/eclair.log:
-----------------------------------------------------------------------------
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for taglib-config... no
taglib-config  is not in your $PATH. Please ensure it is.
Read the manual page for you shell as to how to extend your path.
configure: error: Cannot find taglib-config

```


It does seem to be a xine problem but I can't find taglib-config in the repos so I'm not sure what to do. I really want to check out eclair so it would be nice to get this figured out. Thanks for all the help.

---

### Post by foxy123 on 2006-01-09
[QUOTE=daedalusman]Ok well I let it run and it made it through but I wanted emotion and eclair so I installed the latest versions of xinelib and xine-ui from their site. Emotion installed with no problems but I got this problem when it got to eclair.

```
LAST LOGLINES FROM /tmp/easy_e17/install_logs/eclair.log:
-----------------------------------------------------------------------------
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
appending configuration tag "F77" to libtool
checking for taglib-config... no
taglib-config  is not in your $PATH. Please ensure it is.
Read the manual page for you shell as to how to extend your path.
configure: error: Cannot find taglib-config

```


It does seem to be a xine problem but I can't find taglib-config in the repos so I'm not sure what to do. I really want to check out eclair so it would be nice to get this figured out. Thanks for all the help.[/QUOTE]
have you got libtag (or taglib) installed?

---

### Post by daedalusman on 2006-01-09
[QUOTE=foxy123]have you got libtag (or taglib) installed?[/QUOTE]


I've got libtag installed, is there a difference?

---

### Post by foxy123 on 2006-01-09
[QUOTE=daedalusman]I've got libtag installed, is there a difference?[/QUOTE]
I think it's the same, though I've got taglib 1.4 installed for amarok I guess. My taglib.config is in /usr/local/bin/

---

### Post by durand on 2006-01-09
I managed it get enlightenment working and it is fantastic!!:) :) :D  I just compiled the libraries and apps that didn't compile by script manually. Follow these instructions : [https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php) to compile them. use ./autogen.sh --prefix=/opt/e17/ or whatever ur install path is when compiling them. Then just use the skip "tag" in the script to skip the ones u compiled manually. Mine worked really well!

---

### Post by daedalusman on 2006-01-09
Alright, after installing taglib, sqlite3, and libxml2 from source I was able to get past package dependencies but now I am getting this error message...

```
gcc -Wall -O1 -g -O2 -o eclair eclair.o eclair_args.o eclair_utils.o eclair_callbacks.o eclair_media_file.o eclair_playlist.o eclair_playlist_container.o eclair_subtitles.o eclair_cover.o eclair_meta_tag.o eclair_config.o eclair_dialogs.o eclair_window.o eclair_database.o eclair_video.o eclair_menu.o  -L/opt/e17/lib /opt/e17/lib/libedje.so /opt/e17/lib/libemotion.so /opt/e17/lib/libevas.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_dbus.so /opt/e17/lib/libeet.so /usr/lib/libjpeg.so -ldl /opt/e17/lib/libesmart_draggies.so -L/usr/local/lib /usr/local/lib/libtag.so /usr/local/lib/libtag_c.so /usr/local/lib/libxml2.so -lz -lm /usr/local/lib/libsqlite3.so
eclair_cover.o: In function `eclair_cover_init':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_cover.c:74: undefined reference to `pthread_create'
eclair_cover.o: In function `eclair_cover_shutdown':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_cover.c:99: undefined reference to `pthread_join'
eclair_meta_tag.o: In function `eclair_meta_tag_init':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_meta_tag.c:25: undefined reference to `pthread_create'
eclair_meta_tag.o: In function `eclair_meta_tag_shutdown':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_meta_tag.c:37: undefined reference to `pthread_join'
eclair_video.o: In function `eclair_video_shutdown':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_video.c:40: undefined reference to `pthread_join'
eclair_video.o: In function `eclair_create_video_window':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_video.c:73: undefined reference to `pthread_create'
collect2: ld returned 1 exit status
make[3]: *** [eclair] Error 1
make[3]: Leaving directory `/home/aegon/e17_cvs/e17/apps/eclair/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aegon/e17_cvs/e17/apps/eclair/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aegon/e17_cvs/e17/apps/eclair'
make: *** [all] Error 2
```


Thats the end of my log file, I have no idea what it means can someone help me out here, thanks again.

---

### Post by corefile on 2006-01-21
Cool, script works perfect, and once I installed libxine 1.1.1 and taglib both emotion and eclair install with no problems

---

### Post by Juippisi on 2006-01-21
[QUOTE=daedalusman]Alright, after installing taglib, sqlite3, and libxml2 from source I was able to get past package dependencies but now I am getting this error message...

```
gcc -Wall -O1 -g -O2 -o eclair eclair.o eclair_args.o eclair_utils.o eclair_callbacks.o eclair_media_file.o eclair_playlist.o eclair_playlist_container.o eclair_subtitles.o eclair_cover.o eclair_meta_tag.o eclair_config.o eclair_dialogs.o eclair_window.o eclair_database.o eclair_video.o eclair_menu.o  -L/opt/e17/lib /opt/e17/lib/libedje.so /opt/e17/lib/libemotion.so /opt/e17/lib/libevas.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_dbus.so /opt/e17/lib/libeet.so /usr/lib/libjpeg.so -ldl /opt/e17/lib/libesmart_draggies.so -L/usr/local/lib /usr/local/lib/libtag.so /usr/local/lib/libtag_c.so /usr/local/lib/libxml2.so -lz -lm /usr/local/lib/libsqlite3.so
eclair_cover.o: In function `eclair_cover_init':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_cover.c:74: undefined reference to `pthread_create'
eclair_cover.o: In function `eclair_cover_shutdown':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_cover.c:99: undefined reference to `pthread_join'
eclair_meta_tag.o: In function `eclair_meta_tag_init':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_meta_tag.c:25: undefined reference to `pthread_create'
eclair_meta_tag.o: In function `eclair_meta_tag_shutdown':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_meta_tag.c:37: undefined reference to `pthread_join'
eclair_video.o: In function `eclair_video_shutdown':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_video.c:40: undefined reference to `pthread_join'
eclair_video.o: In function `eclair_create_video_window':
/home/aegon/e17_cvs/e17/apps/eclair/src/eclair_video.c:73: undefined reference to `pthread_create'
collect2: ld returned 1 exit status
make[3]: *** [eclair] Error 1
make[3]: Leaving directory `/home/aegon/e17_cvs/e17/apps/eclair/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/aegon/e17_cvs/e17/apps/eclair/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/aegon/e17_cvs/e17/apps/eclair'
make: *** [all] Error 2
```


Thats the end of my log file, I have no idea what it means can someone help me out here, thanks again.[/QUOTE]

Have you tried installing sqlites -dev packages? Yea, I'm, sorry I didn't read all the 15 pages and looked for your posts. 

And besides, Eclair is pretty useless currently (in my opinion). Someday it will be nice, but now it is not, because the GUI is not usable.


Yes, that morlenxuses easy_e17 has made my life a lot easier. My first Enlightenment expirement was on March 2005 and I can tell that it has changed a lot after that. To the better direction of course :-P.

Hope it will soon become stable and hit to the Ubuntu-repos, official ones.

---

### Post by durand on 2006-01-21
I had to recompile e17 but i get this error :```
cvs [checkout aborted]: end of file from server (consult above messages if any)
```Any idea what it means?There were no messages before it.

---

### Post by foxy123 on 2006-01-21
[QUOTE=durand]I had to recompile e17 but i get this error :```
cvs [checkout aborted]: end of file from server (consult above messages if any)
```Any idea what it means?There were no messages before it.[/QUOTE]
just keep trying...

---

### Post by Bavor on 2006-01-25
It was all going smooth until here:


```
Checkout repo 'e_modules' ...
cvs checkout: warning: failed to open /home/ubuntu/.cvspass for reading: No such file or directory
cvs [checkout aborted]: end of file from server (consult above messages if any)
cvs checkout: warning: failed to open /home/ubuntu/.cvspass for reading: No such file or directory
cvs [checkout aborted]: reading from server: Connection reset by peer
cvs checkout: warning: failed to open /home/ubuntu/.cvspass for reading: No such file or directory
cvs [checkout aborted]: end of file from server (consult above messages if any)
cvs checkout: warning: failed to open /home/ubuntu/.cvspass for reading: No such file or directory
cvs [checkout aborted]: end of file from server (consult above messages if any)
cvs checkout: warning: failed to open /home/ubuntu/.cvspass for reading: No such file or directory
cvs [checkout aborted]: reading from server: Connection reset by peer
FAILED! Next attempt 6 in 70 seconds
```

What happen?

---

### Post by Havoc on 2006-01-26
Yep, I was getting a *lot* of those at one time...

**1) Make sure .cvspass is writable by your user.Do a:**

```
sudo chown $USER .cvspass
```

In your home folder.If it doesn't exist do a:

```
touch .cvspass
```

**2) Move or delete the ".e17_cvs" folder.Then try the script again.**

That's all I can say right now.E17 works great, by the way.

---

### Post by thorsan on 2006-01-27
This is a great HOWTO but I do have some problems:

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally


any ideas to what might be wrong?


all help is very much appreciated.

---

### Post by foxy123 on 2006-01-27
[QUOTE=thorsan]This is a great HOWTO but I do have some problems:

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
automake: configure.in: installing `./install-sh'
automake: configure.in: installing `./mkinstalldirs'
automake: configure.in: installing `./missing'
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally


any ideas to what might be wrong?


all help is very much appreciated.[/QUOTE]
what version of automake are you using?

---

### Post by Rev. Nathan on 2006-01-28
Problem. The install seemingly returned with no errors, but when I try to log into E-17 I get an error that /opt/e17/bin/enlightenment does not exist! Help?

---

### Post by Rev. Nathan on 2006-01-29
[QUOTE=Rev. Nathan]Problem. The install seemingly returned with no errors, but when I try to log into E-17 I get an error that /opt/e17/bin/enlightenment does not exist! Help?[/QUOTE]
No one has an answer? It appears that everything else install but this. And of course I get errors when I run it through the CVS again.

---

### Post by foxy123 on 2006-01-30
[QUOTE=Rev. Nathan]Problem. The install seemingly returned with no errors, but when I try to log into E-17 I get an error that /opt/e17/bin/enlightenment does not exist! Help?[/QUOTE]
but does it exist? also did you do:

> Suggestion: due to the fact that enlightenment was installed in /opt/e17 it is a good idea to add /opt/e17/bin to your PATH so that it is easier to run all those great applications you just installed.

To do this open your /etc/environment with your favorite text editor

```
sudo gedit /etc/environment
```


then add the following lines to the bottom


```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```



---

### Post by Havoc on 2006-01-30
[QUOTE=Rev. Nathan]Problem. The install seemingly returned with no errors, but when I try to log into E-17 I get an error that /opt/e17/bin/enlightenment does not exist! Help?[/QUOTE]


Well, does it?

And, regarding the permissions, is it executable by your user?

The permissions should be 755 (or -rwxr-xr-x, depending from where you come from)
 with Owner and Group set to root.

If you don't know how to change permissions, do a...

```
sudo chmod 755 ./enlightenment
```

...in the /opt/e17/bin/ folder.

That's all.:-D

---

### Post by jaclayton on 2006-01-30
Everything went swimmingly!
Once I twigged you didn't need eclair or emotion it all compiled through first time.

But I can't get the e-utils to compile for me at all!  I'm not at my Kubuntu box at the moment so I can't post the results from autogen and make, but one of those scripts returns a list of the components of e_utils with a "no" next to each one of them.

All I wanted to do was edit some menus!  Just a little blast of Entangle (seen working perfectly on the elive CD) would be lovely!

Help!

---

### Post by Havoc on 2006-01-30
Well, you could try "e17genmenu".

It works perfectly for me.

After it auto-generates the .eap(s) and the menus, you can go down to "/home/$USER/.e/e/applications/favorite" and hack away!

Check [HERE](http://www1.get-e.org/E17_User_Guide/English/_pages/3.7.html) for more. :cool:

---

### Post by jaclayton on 2006-01-30
Thanks for a very speedy reply.

I'll try that tonight.

I'll also try posting the results from the scripts, see if anyone with more nouce than me can figure out why it isn't compiling.

---

### Post by i3dmaster on 2006-01-30
[QUOTE=TimmyJ]OK, I think I've nailed down what causes this. It is a problem with automake versions. To fix this you should:
```
sudo apt-get remove automake1.4 automake1.6 automake1.8 automake1.9
```
then
```

sudo apt-get install automake1.7
```
then finally, run the script again
```
sudo ./easy_e17 -i --skip=eclair,emotion
```

Hopefully that'll work. Post ur results :)[/QUOTE]
You really don't need to remove all other automakes, just ln -sf the 1.7 version to the /etc/alternatives/automake and it will replace the 1.9 one, which is the official way to address the multi-version apps.

---

### Post by Rev. Nathan on 2006-01-30
[QUOTE=foxy123]but does it exist? also did you do:[/QUOTE]
Yes, it looks like this:

```
LANGUAGE="en"
LANG=en_US.UTF-8
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```

[QUOTE=Havoc]Well, does it?

And, regarding the permissions, is it executable by your user?

The permissions should be 755 (or -rwxr-xr-x, depending from where you come from)
 with Owner and Group set to root.

If you don't know how to change permissions, do a...

```
sudo chmod 755 ./enlightenment
```

...in the /opt/e17/bin/ folder.

That's all.:-D[/QUOTE]
I cannot remember which step it is, but I manually changed a folder's permissions to 777 (or whatever permissions to everything is). Which would be the same, right?

Neither root user or I can see enlightenment, therefore not existing:
[IMG]http://www.bigrevmedia.com/coronets/Screenshot-owner.png[/IMG]
[IMG]http://www.bigrevmedia.com/coronets/Screenshot-root.png[/IMG]

Your suggestion did not work... :-k 
[IMG]http://www.bigrevmedia.com/coronets/Screenshot-nathan@backroom:%20-opt-e17-bin.png[/IMG]

---

### Post by louis_nichols on 2006-01-30
[COLOR="Red"]Ignore this! Silly me forgot to configure the firewall. [/COLOR]](*,)

welll. myself, I can't even download the source from cvs.

cvs [checkout aborted]: connect to cvs.sourceforge.net(66.35.250.207):2401 failed: Connection refused

And I get it A LOT.
Is it really THAT busy? Or is something else going on?

---

### Post by Havoc on 2006-01-30
Well, if it doesn't exist, you can't change it's permissions, can you now? :D 

Your best bet is to delete the whole /opt/e17 folder, possibly delete the e17_cvs folder in your home folder, and rerun the script.

This time, *don't* play around with permissions.I never had to myself.

Have a nice day! ;)

---

### Post by Rev. Nathan on 2006-01-30
[QUOTE=Havoc]Well, if it doesn't exist, you can't change it's permissions, can you now? :D 

Your best bet is to delete the whole /opt/e17 folder, possibly delete the e17_cvs folder in your home folder, and rerun the script.

This time, *don't* play around with permissions.I never had to myself.

Have a nice day! ;)[/QUOTE]
Now I get this error:

Checkout repo 'e_modules' ...
cvs checkout: [04:24:05] waiting for mej's lock in /cvsroot/enlightenment/e_modules

This error comes up every :30 :( Help?

---

### Post by benplaut on 2006-01-31
[QUOTE=Rev. Nathan]Now I get this error:

Checkout repo 'e_modules' ...
cvs checkout: [04:24:05] waiting for mej's lock in /cvsroot/enlightenment/e_modules

This error comes up every :30 :( Help?[/QUOTE]

same here... i think the CVS is down :(

---

### Post by Rev. Nathan on 2006-01-31
[QUOTE=benplaut]same here... i think the CVS is down :([/QUOTE]
But only to this point... I'm going to try this again tomorrow, I guess.

---

### Post by louis_nichols on 2006-01-31
I get the same thing. I think this happens when someone uploads new files to the cvs. But it's been 10 hours since I first got this error and it's still the same. So I'm betting some error somewhere. Weird thing is, though, that it did update some of the files. But, at e_modules it stopped.

Edits: bad, BAD english! :D

---

### Post by louis_nichols on 2006-01-31
well... I just realised that I don't need an update, cause I just downloaded the cvs yesterday, but ran into some problems when compiling. So... I used --skip-update. But... problems are still there.

```
LAST LOGLINES FROM /tmp/easy_e17/install_logs/monitor.log:
-----------------------------------------------------------------------------
/usr/share/aclocal/tcl.m4:333: warning: underquoted definition of SC_ENABLE_SHARED
/usr/share/aclocal/tcl.m4:373: warning: underquoted definition of SC_ENABLE_FRAMEWORK
/usr/share/aclocal/tcl.m4:424: warning: underquoted definition of SC_ENABLE_THREADS
/usr/share/aclocal/tcl.m4:560: warning: underquoted definition of SC_ENABLE_SYMBOLS
/usr/share/aclocal/tcl.m4:617: warning: underquoted definition of SC_ENABLE_LANGINFO
/usr/share/aclocal/tcl.m4:669: warning: underquoted definition of SC_CONFIG_MANPAGES
/usr/share/aclocal/tcl.m4:805: warning: underquoted definition of SC_CONFIG_CFLAGS
/usr/share/aclocal/tcl.m4:1901: warning: underquoted definition of SC_SERIAL_PORT
/usr/share/aclocal/tcl.m4:2030: warning: underquoted definition of SC_MISSING_POSIX_HEADERS
/usr/share/aclocal/tcl.m4:2111: warning: underquoted definition of SC_PATH_X
/usr/share/aclocal/tcl.m4:2196: warning: underquoted definition of SC_BLOCKING_STYLE
/usr/share/aclocal/tcl.m4:2261: warning: underquoted definition of SC_TIME_HANDLER
/usr/share/aclocal/tcl.m4:2338: warning: underquoted definition of SC_BUGGY_STRTOD
/usr/share/aclocal/tcl.m4:2400: warning: underquoted definition of SC_TCL_LINK_LIBS
/usr/share/aclocal/tcl.m4:2476: warning: underquoted definition of SC_TCL_EARLY_FLAG
/usr/share/aclocal/tcl.m4:2488: warning: underquoted definition of SC_TCL_EARLY_FLAGS
/usr/share/aclocal/tcl.m4:2520: warning: underquoted definition of SC_TCL_64BIT_FLAGS
/usr/share/aclocal/nspr.m4:8: warning: underquoted definition of AM_PATH_NSPR
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in:23: required file `./ABOUT-NLS' not found

```
this is the output. I have NO IDEA what it means. Tried to google, but with no luck. Any help, pls?

---

### Post by Havoc on 2006-01-31
Yup, I got that problem on mount,monitor,screenshot and slideshow.
Either create an empty file named like that in the folder, or if you're like me, jus' skip the damn thing! ;)

---

### Post by louis_nichols on 2006-01-31
Well... I just copied a file from one of the other folders (it took me a while, but then I realised it wasn't a config file, so the content wasn't important). I wanted to skip it but didn't know how.

---

### Post by Jaivaz on 2006-02-01
I got it to work earlier, but now that I try to run it again I get the following while it's making ecore

```
- ecore ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ecore.log:
-----------------------------------------------------------------------------
ranlib .libs/libecore_dbus.a
creating libecore_dbus.la
(cd .libs && rm -f libecore_dbus.la && ln -s ../libecore_dbus.la libecore_dbus.la)
make[4]: Leaving directory `/home/horace/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/horace/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/horace/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/horace/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/horace/e17_cvs/e17/libs/ecore/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/usr/X11R6/include   -I/opt/e17/include -g -O2 -Wall -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/usr/X11R6/include  -g -O2 -Wall -MT ecore_test-ecore_test.o -MD -MP -MF ".deps/ecore_test-ecore_test.Tpo" -c -o ecore_test-ecore_test.o `test -f 'ecore_test.c' || echo './'`ecore_test.c; \
        then mv -f ".deps/ecore_test-ecore_test.Tpo" ".deps/ecore_test-ecore_test.Po"; else rm -f ".deps/ecore_test-ecore_test.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2 -Wall  -L/opt/e17/lib -o ecore_test  ecore_test-ecore_test.o ../../src/lib/ecore/libecore.la ../../src/lib/ecore_x/libecore_x.la ../../src/lib/ecore_txt/libecore_txt.la ../../src/lib/ecore_job/libecore_job.la ../../src/lib/ecore_fb/libecore_fb.la ../../src/lib/ecore_evas/libecore_evas.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore_ipc/libecore_ipc.la -lm
mkdir .libs
gcc -g -O2 -Wall -o .libs/ecore_test ecore_test-ecore_test.o  -L/opt/e17/lib ../../src/lib/ecore/.libs/libecore.so ../../src/lib/ecore_x/.libs/libecore_x.so ../../src/lib/ecore_txt/.libs/libecore_txt.so ../../src/lib/ecore_job/.libs/libecore_job.so ../../src/lib/ecore_fb/.libs/libecore_fb.so ../../src/lib/ecore_evas/.libs/libecore_evas.so ../../src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_ipc/.libs/libecore_ipc.so -lm
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_get'
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_set'
collect2: ld returned 1 exit status
make[3]: *** [ecore_test] Error 1
make[3]: Leaving directory `/home/horace/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/horace/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/horace/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2

```
Any idea why?

---

### Post by Joch on 2006-02-03
Hello,

Yesterday I installed E17 from CVS and it worked with a couple of errors. But after playing a bit with the configuration I wanted to log in with Gnome back. When I try to log in with Gnome he just loads my Splash screen and it hangs after he loaded 'The Panel'.

I really don't know what caused this problem and how I can solve it. Can please somebody help me because I really would like to use Gnome again.

Thanks by advance,

Jochem

---

### Post by curtis on 2006-02-07
I am running Dapper Drake, this error is probably due to a missing libary though.

```

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Making all in modules
make[3]: Entering directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules'
Making all in engines
make[4]: Entering directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines'
Making all in buffer
make[5]: Entering directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines/buffer'
if /bin/sh ../../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I../../../../src/modules/engines -I/usr/include/freetype2  -I/opt/e17/include  -O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT evas_engine.lo -MD -MP -MF ".deps/evas_engine.Tpo" -c -o evas_engine.lo evas_engine.c; \
        then mv -f ".deps/evas_engine.Tpo" ".deps/evas_engine.Plo"; else rm -f ".deps/evas_engine.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I../../../../src/modules/engines -I/usr/include/freetype2 -I/opt/e17/include -O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT evas_engine.lo -MD -MP -MF .deps/evas_engine.Tpo -c evas_engine.c  -fPIC -DPIC -o .libs/evas_engine.o
evas_engine.c: In function 'evas_engine_buffer_output_setup':
evas_engine.c:294: error: 'EVAS_ENGINE_BUFFER_DEPTH_RGB32' undeclared (first use in this function)
evas_engine.c:294: error: (Each undeclared identifier is reported only once
evas_engine.c:294: error: for each function it appears in.)
make[5]: *** [evas_engine.lo] Error 1
make[5]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines/buffer'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas'
make: *** [all] Error 2
-----------------------------------------------------------------------------


root@laptop:~#

```

---

### Post by sebastjanp on 2006-02-08
Again problems with CVS?

```
BASIC SYSTEM CHECKS:
-----------------------------------------------------------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok
- setting compile options .... ok
-----------------------------------------------------------------------------

CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...
can't create temporary directory /tmp/cvs-serv30611
No space left on device
can't create temporary directory /tmp/cvs-serv30637
No space left on device
can't create temporary directory /tmp/cvs-serv30750
No space left on device
can't create temporary directory /tmp/cvs-serv30834
No space left on device
can't create temporary directory /tmp/cvs-serv30995
No space left on device
can't create temporary directory /tmp/cvs-serv31275
No space left on device
FAILED! Next attempt 7 in 120 seconds

```

I am running the script as sudo. 
Oh and I most definitely have enough disk space.
Any idea how to pass this or the cvs dir is not available?

Can someone help?

---

### Post by foxy123 on 2006-02-08
[QUOTE=sebastjanp]Again problems with CVS?

```
BASIC SYSTEM CHECKS:
-----------------------------------------------------------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok
- setting compile options .... ok
-----------------------------------------------------------------------------

CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...
can't create temporary directory /tmp/cvs-serv30611
No space left on device
can't create temporary directory /tmp/cvs-serv30637
No space left on device
can't create temporary directory /tmp/cvs-serv30750
No space left on device
can't create temporary directory /tmp/cvs-serv30834
No space left on device
can't create temporary directory /tmp/cvs-serv30995
No space left on device
can't create temporary directory /tmp/cvs-serv31275
No space left on device
FAILED! Next attempt 7 in 120 seconds

```

I am running the script as sudo. 
Oh and I most definitely have enough disk space.
Any idea how to pass this or the cvs dir is not available?

Can someone help?[/QUOTE]
it may be very well a CVS problem. Try again in few hours. Also you do not need run the script as a root.

---

### Post by sebastjanp on 2006-02-08
Im triing it for two days now and no difference.
I have also tryed without sudo comand and there is no difference.

---

### Post by foxy123 on 2006-02-08
[QUOTE=sebastjanp]Im triing it for two days now and no difference.
I have also tryed without sudo comand and there is no difference.[/QUOTE]
I have not built e17 for few days so I am not sure if their anonymous cvs is up. I guess it is down at the moment. Try again tomorrow.

---

### Post by brenx on 2006-02-08
[QUOTE=thewayofzen]Has anyone documented exactly what needs to be done to remove all the files/changes that are made/created with the installation of e17?

any help would be appreciated.

thewayofzen[/QUOTE]

I removed the folowing packages: 

**Completely removed the following packages**:
libeet0

**Removed the following package**s:
libeet0-dev
libembryo0
libembryo0-dev
libepeg0
libepplet0

---

### Post by newuser111 on 2006-02-09
in case anyone is interested i made a deb file for e17genmenu

[http://www.ubuntuforums.org/showthread.php?t=127820](http://www.ubuntuforums.org/showthread.php?t=127820)

---

### Post by trorion on 2006-02-16
I've seen numerous identical errors to what I have had myself (below) and I'm wondering if anyone has managed to get past it?  If so what did you actually do?

I've tried the install instructions as root and as sudo for all steps and get a repository error when I use the default CVS and then this error if I use the mirror.  Could this be a problem with the mirror CVS?

Incidentally, the problem with "/etc/e17/enlightenment" does not exist is related to this I believe (i.e. people are not getting a successful install then they go and try to log in with enlightenment...which doesn't exist).

```
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Making all in modules
make[3]: Entering directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules'
Making all in engines
make[4]: Entering directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines'
Making all in buffer
make[5]: Entering directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines/buffer'
if /bin/sh ../../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I../../../../src/modules/engines -I/usr/include/freetype2  -I/opt/e17/include  -O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT evas_engine.lo -MD -MP -MF ".deps/evas_engine.Tpo" -c -o evas_engine.lo evas_engine.c; \
        then mv -f ".deps/evas_engine.Tpo" ".deps/evas_engine.Plo"; else rm -f ".deps/evas_engine.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../../.. -I. -I../../../../src/lib -I../../../../src/lib/include -I../../../../src/modules/engines -I/usr/include/freetype2 -I/opt/e17/include -O3 -mtune=pentium4m -funroll-loops -ffast-math -fomit-frame-pointer -fno-exceptions -MT evas_engine.lo -MD -MP -MF .deps/evas_engine.Tpo -c evas_engine.c  -fPIC -DPIC -o .libs/evas_engine.o
evas_engine.c: In function 'evas_engine_buffer_output_setup':
evas_engine.c:294: error: 'EVAS_ENGINE_BUFFER_DEPTH_RGB32' undeclared (first use in this function)
evas_engine.c:294: error: (Each undeclared identifier is reported only once
evas_engine.c:294: error: for each function it appears in.)
make[5]: *** [evas_engine.lo] Error 1
make[5]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines/buffer'
make[4]: *** [all-recursive] Error 1
make[4]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules/engines'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src/modules'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/curtis/e17_cvs/e17/libs/evas'
make: *** [all] Error 2
-----------------------------------------------------------------------------

root@laptop:~#
```
edit: I did try with automake 1.7 as well as the default 1.9 so I don't think the automake is the problem.  I have not tried to download the files directly and install them manually because honestly i'm not the savvy but if someone could post a detail of how to do that I will happily try it and post my results.

Final question (probably mute) but can I do XGL and e17 at the same time?  I really want to see if the next generation of linux is going to be competitive graphically with windows and mac (especially now that I can get a mac for less than $1500).

---

### Post by loon on 2006-02-17
Just wanted to say the newest script work perfectly.  emotion and eclair wouldnt isntall because I needed xine 1.1.1 but I only have what is in the repos.  I am building from sourcing and installing.  Will let you know if it works or not, but e17 is running perfectly from home and work.  I must say, e17 has come a long way! I like the new configuration editor! e17 is the best it has ever been and I can't wait for the stable release [if ever].

\\:D/

---

### Post by loon on 2006-02-17
Can we get e_utils included into the script? :-k

---

### Post by joplass on 2006-02-19
this line: sudo ./easy_e17.sh -i --skip=emotion,eclair
gave me this:
CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Updating repo 'e17' (please wait, this won't output much) ...
cvs update: warning: failed to open /home/job/.cvspass for reading: No such file or directory
? libs/evas/stamp-h.in
Updating repo 'misc' (please wait, this won't output much) ...
cvs update: warning: failed to open /home/job/.cvspass for reading: No such file or directory
Updating repo 'e_modules' (please wait, this won't output much) ...
cvs update: warning: failed to open /home/job/.cvspass for reading: No such file or directory
-----------------------------------------------------------------------------


PREPARING FOR PHASE 2...

#############################################################################
#             easy_e17.sh (0.9.9) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#         Thanks to David 'onefang' Seikel for contributing patches!        #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/) | Contact: [email]morlenxus@gmx.net[/email] #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/job/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave
  - installable apps:     entrance e eclair evfs
  - installable misc:     engage
  - installable proto:    etk exhibit entropy
  - installable modules:  calendar flame monitor mount rain screenshot slideshow snow tclock weather
  - skipping:             emotion eclair
  - install only this:    ALL

  - script action:    install


BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Running libtoolize...
Running automake...
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
-----------------------------------------------------------------------------


job@UbuntuNotebook:~$

some help please!

---

### Post by DarkT on 2006-02-19
I just ran in to this problem myself and after a bit of searching I found the answer on a french ubuntu forum. It turns out that my install of kubuntu was using automake 1.4 even though 1.9 was installed, this can be fixed by uninstalling automake 1.4 (and installing 1.9 if it's not already installed) or running the command
```
sudo update-alternatives --config automake
```
and selecting automake 1.9 as the default automake. It seems to have gotten e17 compiling properly for me at any rate :)

**Added:**

I should also note, when you come to run the script again to finish off the install you may want to insert a -c (so sudo ./easy_e17.sh -i **-c** --skip=emotion,eclair) in to skip the CVS repository update unless you really need it, otherwise there's a lot of waiting involved ;)

---

### Post by joplass on 2006-02-19
thank to this thread enlightenment is up and running.  Very impressive but how do one go by to add apps to the lunch bar? is there a way to add gnome menu?  home?  
in other words how do you run your applications?
Thanks

---

### Post by quadomatic on 2006-02-19
Why aren't the themes i put in /opt/e17/share/enlightenment/data/themes showing up in the theme browser?

---

### Post by foxy123 on 2006-02-20
[QUOTE=joplass]thank to this thread enlightenment is up and running.  Very impressive but how do one go by to add apps to the lunch bar? is there a way to add gnome menu?  home?  
in other words how do you run your applications?
Thanks[/QUOTE]
you need e17genmenu to generate eap files. Than you can either right click for the menu of available apps or put them into you launch bar using entangle.

---

### Post by foxy123 on 2006-02-20
[QUOTE=quadomatic]Why aren't the themes i put in /opt/e17/share/enlightenment/data/themes showing up in the theme browser?[/QUOTE]
themes are to be put to ~/.e/e/themes

---

### Post by joplass on 2006-02-20
[QUOTE=foxy123]you need e17genmenu to generate eap files. Than you can either right click for the menu of available apps or put them into you launch bar using entangle.[/QUOTE]
while I am googling for e17genmenu I am wondering if a simple apt-get can give me that while running enligtement :confused: .

---

### Post by fsck0ff on 2006-02-20
[QUOTE=joplass]thank to this thread enlightenment is up and running.  Very impressive but how do one go by to add apps to the lunch bar? is there a way to add gnome menu?  home?  
in other words how do you run your applications?
Thanks[/QUOTE]

What I do is:
#cd ~/.e/e/applications/all
#e_util_eapp_edit the_name_of_the_app_u_wanna_add.eap
(here you fill App Name and Executable (the full path to the executable), also click on set icon to put some nice eyecandy in)
after that you save the eap.
Open entangle and add the newly created eap file to whatever you want (I prefer engage and Favourites, YMMV
(btw you delete eap's from entangle with a middle click on the eap that you don't want)
:>
then left click on the desktop -> restart enlightenment and your new eap is added :>

---

### Post by foxy123 on 2006-02-20
[QUOTE=joplass]while I am googling for e17genmenu I am wondering if a simple apt-get can give me that while running enligtement :confused: .[/QUOTE]
I doubt it. It is easy to compile. Also I have seen the deb somewhere, but I do not remember.

---

### Post by loon on 2006-02-20
One page over
<----

[http://www.ubuntuforums.org/showpost.php?p=720028&postcount=177](http://www.ubuntuforums.org/showpost.php?p=720028&postcount=177)

Also the e17genmenu didn't work very well for me.  Or at least the .dep version he compiled.

---

### Post by joplass on 2006-02-21
now i have directory .e in /home now what.  i tried creating links to apps no can't do

---

### Post by mrgnash on 2006-02-23
I'm tantalisingly close to having this installed, but I get this, rather inexplicable, error:

#############################################################################
#             easy_e17.sh (0.9.9) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#         Thanks to David 'onefang' Seikel for contributing patches!        #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/) | Contact: [email]morlenxus@gmx.net[/email] #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/mrgnash/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave
  - installable apps:     entrance e eclair evfs
  - installable misc:     engage
  - installable proto:    etk exhibit entropy
  - installable modules:  calendar flame monitor mount rain screenshot slideshow snow tclock weather
  - skipping:             emotion eclair
  - install only this:    ALL

  - script action:    install


BUILD PHASE: 1/3
  - running some basic system checks
  - cvs checkout/update

#############################################################################



BASIC SYSTEM CHECKS:
-----------------------------------------------------------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok
- setting compile options .... ok
-----------------------------------------------------------------------------

CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Updating repo 'e17' (please wait, this won't output much) ...
cvs update: warning: failed to open /home/mrgnash/.cvspass for reading: No such file or directory
? apps/entrance/mkinstalldirs
? apps/evfs/mkinstalldirs
? apps/evfs/src/bin/evfscopy
? libs/engrave/src/lib/libengrave_la-engrave_style.lo
? libs/epeg/epeg-uninstalled.pc
? libs/epeg/epeg.pc
? libs/evas/stamp-h.in
Updating repo 'misc' (please wait, this won't output much) ...
cvs update: warning: failed to open /home/mrgnash/.cvspass for reading: No such file or directory
Updating repo 'e_modules' (please wait, this won't output much) ...
cvs update: warning: failed to open /home/mrgnash/.cvspass for reading: No such file or directory
-----------------------------------------------------------------------------


PREPARING FOR PHASE 2...

#############################################################################
#             easy_e17.sh (0.9.9) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#         Thanks to David 'onefang' Seikel for contributing patches!        #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/) | Contact: [email]morlenxus@gmx.net[/email] #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/mrgnash/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave
  - installable apps:     entrance e eclair evfs
  - installable misc:     engage
  - installable proto:    etk exhibit entropy
  - installable modules:  calendar flame monitor mount rain screenshot slideshow snow tclock weather
  - skipping:             emotion eclair
  - install only this:    ALL

  - script action:    install


BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... previous installed
- epsilon .................... previous installed
- esmart ..................... previous installed
- emotion .................... SKIPPED
- ewl ........................ previous installed
- engrave .................... previous installed
-----------------------------------------------------------------------------

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... previous installed
- e .......................... previous installed
- eclair ..................... SKIPPED
- evfs ....................... previous installed
- engage ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/mrgnash/e17_cvs/misc/engage'
Making all in src
make[2]: Entering directory `/home/mrgnash/e17_cvs/misc/engage/src'
Making all in module
make[3]: Entering directory `/home/mrgnash/e17_cvs/misc/engage/src/module'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/mrgnash/e17_cvs/misc/engage/src/module'
make[3]: Entering directory `/home/mrgnash/e17_cvs/misc/engage/src'
/bin/sh ../libtool --tag=CC --mode=link gcc  -Wall -g -O2  -L/opt/e17/lib -o engage  engage-main.o engage-config.o engage-dock.o engage-icon.o engage-wm.o engage-window.o engage-tray.o engage-userconfig.o engage-e_object.o engage-e_file.o engage-e_user.o engage-e_apps.o -L/opt/e17/lib -levas -L/opt/e17/lib -ledje -L/opt/e17/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -lecore_dbus -L/opt/e17/lib -leet -lz -ljpeg -lm -L/usr/lib -lImlib2 -lfreetype -lz -lX11 -lXext -ldl -lm -L/opt/e17/lib -lewl -L/opt/e17/lib -ledje -L/opt/e17/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -lecore_dbus -L/opt/e17/lib -leet -lz -ljpeg -lm -L/opt/e17/lib -levas -lm -L/opt/e17/lib -lm -lesmart_trans_x11
gcc -Wall -g -O2 -o engage engage-main.o engage-config.o engage-dock.o engage-icon.o engage-wm.o engage-window.o engage-tray.o engage-userconfig.o engage-e_object.o engage-e_file.o engage-e_user.o engage-e_apps.o  -L/opt/e17/lib -L/usr/lib /opt/e17/lib/libImlib2.so /usr/lib/libfreetype.so -lX11 -lXext -ldl /opt/e17/lib/libewl.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_dbus.so /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so /opt/e17/lib/libevas.so -lm /opt/e17/lib/libesmart_trans_x11.so
engage-config.o: In function `od_config_menu_init':
/home/mrgnash/e17_cvs/misc/engage/src/config.c:260: undefined reference to `ewl_menu_item_text_set'
/home/mrgnash/e17_cvs/misc/engage/src/config.c:281: undefined reference to `ewl_menu_item_text_set'
/home/mrgnash/e17_cvs/misc/engage/src/config.c:287: undefined reference to `ewl_menu_item_text_set'
/home/mrgnash/e17_cvs/misc/engage/src/config.c:297: undefined reference to `ewl_menu_item_text_set'
collect2: ld returned 1 exit status
make[3]: *** [engage] Error 1
make[3]: Leaving directory `/home/mrgnash/e17_cvs/misc/engage/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mrgnash/e17_cvs/misc/engage/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mrgnash/e17_cvs/misc/engage'
make: *** [all] Error 2
-----------------------------------------------------------------------------


Any ideas? :-k

---

### Post by ChaKy on 2006-02-23
I have another problem with the script. This is the first time I am running the script,, and this is the output:

BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... autogen:    ./easy_e17.sh: line 238: tmp/easy_e17/install_logs/imlib2.log: No such file or directory
ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM tmp/easy_e17/install_logs/imlib2.log:
-----------------------------------------------------------------------------
tail: cannot open `tmp/easy_e17/install_logs/imlib2.log' for reading: No such file or directory

But the strange thing is, I have "imlib2.log" in that directory.

Can somebody help me here? Thanks.

---

### Post by benplaut on 2006-02-23
for those who can't get the script to work, try this:

[https://vogelweith.homeftp.net/Linux/e17_en.php](https://vogelweith.homeftp.net/Linux/e17_en.php)

be careful, though... it's made for debian. Make sure you skip emotion and eclair (unless you're in dapper, they work up here :)

---

### Post by Lucky on 2006-02-24
While executing the easy_e17.sh I got these errors
but before that it showed - 'cvs [update aborted]: end of file from server (consult above messages if any) cvs update: warning: failed to open /home/rash/.cvspass for reading: No such file or directory'   4-5 times and then it started for phase 2.

> 
APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... ok
- e .......................... ok
- eclair ..................... SKIPPED
- evfs ....................... ok
- engage ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
then mv -f ".deps/engage-userconfig.Tpo" ".deps/engage-userconfig.Po"; else rm - f ".deps/engage-userconfig.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I/usr/local/include -I../lib -I/op t/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/includ e -I/opt/e17/include -I/opt/e17/include/ewl -I/opt/e17/include -I/opt/e17/includ e/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude  -I/opt/e17/include  -Wall -g -O2 -MT engage-e_object.o -MD -MP -MF ".deps /engage-e_object.Tpo" -c -o engage-e_object.o `test -f 'e_object.c' || echo './' `e_object.c; \
then mv -f ".deps/engage-e_object.Tpo" ".deps/engage-e_object.Po"; else rm -f ". deps/engage-e_object.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I/usr/local/include -I../lib -I/op t/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/includ e -I/opt/e17/include -I/opt/e17/include/ewl -I/opt/e17/include -I/opt/e17/includ e/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude  -I/opt/e17/include  -Wall -g -O2 -MT engage-e_file.o -MD -MP -MF ".deps/e ngage-e_file.Tpo" -c -o engage-e_file.o `test -f 'e_file.c' || echo './'`e_file. c; \
then mv -f ".deps/engage-e_file.Tpo" ".deps/engage-e_file.Po"; else rm -f ".deps /engage-e_file.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I/usr/local/include -I../lib -I/op t/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/includ e -I/opt/e17/include -I/opt/e17/include/ewl -I/opt/e17/include -I/opt/e17/includ e/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude  -I/opt/e17/include  -Wall -g -O2 -MT engage-e_user.o -MD -MP -MF ".deps/e ngage-e_user.Tpo" -c -o engage-e_user.o `test -f 'e_user.c' || echo './'`e_user. c; \
then mv -f ".deps/engage-e_user.Tpo" ".deps/engage-e_user.Po"; else rm -f ".deps /engage-e_user.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I.. -I../lib -I/usr/local/include -I../lib -I/op t/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/includ e -I/opt/e17/include -I/opt/e17/include/ewl -I/opt/e17/include -I/opt/e17/includ e/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e1 7/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/in clude  -I/opt/e17/include  -Wall -g -O2 -MT engage-e_apps.o -MD -MP -MF ".deps/e ngage-e_apps.Tpo" -c -o engage-e_apps.o `test -f 'e_apps.c' || echo './'`e_apps. c; \
then mv -f ".deps/engage-e_apps.Tpo" ".deps/engage-e_apps.Po"; else rm -f ".deps /engage-e_apps.Tpo"; exit 1; fi
/bin/sh ../libtool --tag=CC --mode=link gcc  -Wall -g -O2  -L/opt/e17/lib -o eng age  engage-main.o engage-config.o engage-dock.o engage-icon.o engage-wm.o engag e-window.o engage-tray.o engage-userconfig.o engage-e_object.o engage-e_file.o e ngage-e_user.o engage-e_apps.o -L/opt/e17/lib -levas -L/opt/e17/lib -ledje -L/op t/e17/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -le core_txt -lecore_fb -lecore_config -lecore_file -lecore_dbus -L/opt/e17/lib -lee t -lz -ljpeg -lm -L/usr/lib -lImlib2 -lfreetype -lz -lX11 -lXext -ldl -lm -L/opt /e17/lib -lewl -L/opt/e17/lib -ledje -L/opt/e17/lib -lecore -lecore_job -lecore_ x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -le core_file -lecore_dbus -L/opt/e17/lib -leet -lz -ljpeg -lm -L/opt/e17/lib -levas  -lm -L/opt/e17/lib -lm -lesmart_trans_x11
mkdir .libs
gcc -Wall -g -O2 -o engage engage-main.o engage-config.o engage-dock.o engage-ic on.o engage-wm.o engage-window.o engage-tray.o engage-userconfig.o engage-e_obje ct.o engage-e_file.o engage-e_user.o engage-e_apps.o  -L/opt/e17/lib -L/usr/lib /opt/e17/lib/libImlib2.so /usr/lib/libfreetype.so -lX11 -lXext -ldl /opt/e17/lib /libewl.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore.so /opt/e17/lib/libecor e_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/l ibecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e1 7/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file. so /opt/e17/lib/libecore_dbus.so /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so /opt/e17/lib/libevas.so -lm /opt/e17/lib/libesmart_trans_x11.so
engage-config.o: In function `od_config_menu_init':
/home/rash/e17_cvs/misc/engage/src/config.c:260: undefined reference to `ewl_men u_item_text_set'
/home/rash/e17_cvs/misc/engage/src/config.c:281: undefined reference to `ewl_men u_item_text_set'
/home/rash/e17_cvs/misc/engage/src/config.c:287: undefined reference to `ewl_men u_item_text_set'
/home/rash/e17_cvs/misc/engage/src/config.c:297: undefined reference to `ewl_men u_item_text_set'
collect2: ld returned 1 exit status
make[3]: *** [engage] Error 1
make[3]: Leaving directory `/home/rash/e17_cvs/misc/engage/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rash/e17_cvs/misc/engage/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rash/e17_cvs/misc/engage'
make: *** [all] Error 2
-----------------------------------------------------------------------------



---

### Post by Lut!n on 2006-03-01
Hi all,
I was just wondering if some of you would be interested in installing e17 with a script which creates debian packages of e17, providing an easy installation, update and uninstallation (Breezy and Dapper tested). Actually, such a script is aldready aviable on the ubuntu french wiki, and I'd like to know if it useful or not to translate and make it aviable for the english-speaking community
Regards,
Lut!n

ps : french version aviable [here](http://lut1n.ifrance.com/compil-e17.py)

---

### Post by Jae686 on 2006-03-01
[QUOTE=Lut!n]Hi all,
I was just wondering if some of of you would be interested in installing e17 with a script which creates debian packages of e17, providing an easy installation, upgrade and uninstallation. Actually, a script which does this is aldready aviable on the ubuntu french wiki, and I'd like to know if it useful or not to translate and make it aviable for the english-speaking community
Regards,
Lut!n[/QUOTE]

yes it would :P

---

### Post by wushumofo on 2006-03-01
> - monitor .................... ./easy_e17.sh: line 224: cd: /home/wushumofo/e17_cvs/e_modules//monitor: No such file or directory


wha... what is it?

specifically... e_modules**//**monitor

// ???

---

### Post by Lut!n on 2006-03-02
Hi all,
for those of you who want a script creating Debian packages, a script is aviable [here](http://lut1n.ifrance.com/en/compil-e17.py)
Although I don't have translated the whole script, it's usable and you can try to compile with it
It doesn't requires anything particular but the libxine 1.1.1 if you want to compile emotion
Although it has been 'heavily' tested by the french communty, it can still be buggy, please e-mail me if it does. And sorry for the awful traduction, feel free to correct me ;)
Regards, Lut!n

---

### Post by David Valentine on 2006-03-02
> I'd like to know if it useful or not to translate and make it aviable for the english-speaking communityMais oui, naturellement. Merci beaucoup. :D

---

### Post by David Valentine on 2006-03-02
Following the HowTo, the easy_e17.sh resulted in the following error:> LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
make[4]: Entering directory `/root/e17_cvs/e17/libs/evas/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/modules/engines -I../../s rc/lib -I../..   -I/opt/e17/include -g -O2 -I/usr/X11R6/include -g -O2 -MT evas_ software_x11_test-evas_test_main.o -MD -MP -MF ".deps/evas_software_x11_test-eva s_test_main.Tpo" -c -o evas_software_x11_test-evas_test_main.o `test -f 'evas_te st_main.c' || echo './'`evas_test_main.c; \
then mv -f ".deps/evas_software_x11_test-evas_test_main.Tpo" ".deps/evas_softwar e_x11_test-evas_test_main.Po"; else rm -f ".deps/evas_software_x11_test-evas_tes t_main.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/modules/engines -I../../s rc/lib -I../..   -I/opt/e17/include -g -O2 -I/usr/X11R6/include -g -O2 -MT evas_ software_x11_test-evas_software_x11_main.o -MD -MP -MF ".deps/evas_software_x11_ test-evas_software_x11_main.Tpo" -c -o evas_software_x11_test-evas_software_x11_ main.o `test -f 'evas_software_x11_main.c' || echo './'`evas_software_x11_main.c ; \
then mv -f ".deps/evas_software_x11_test-evas_software_x11_main.Tpo" ".deps/evas _software_x11_test-evas_software_x11_main.Po"; else rm -f ".deps/evas_software_x 11_test-evas_software_x11_main.Tpo"; exit 1; fi
evas_software_x11_main.c:8:38: error: Evas_Engine_Software_X11.h: No such file o r directory
evas_software_x11_main.c: In function ‘main’:
evas_software_x11_main.c:59: error: ‘Evas_Engine_Info_Software_X11’ undeclared ( first use in this function)
evas_software_x11_main.c:59: error: (Each undeclared identifier is reported only  once
evas_software_x11_main.c:59: error: for each function it appears in.)
evas_software_x11_main.c:59: error: ‘einfo’ undeclared (first use in this functi on)
evas_software_x11_main.c:61: error: syntax error before ‘)’ token
evas_software_x11_main.c:86: error: syntax error before ‘)’ token
evas_software_x11_main.c:111: error: syntax error before ‘)’ token
evas_software_x11_main.c:136: error: syntax error before ‘)’ token
evas_software_x11_main.c:161: error: syntax error before ‘)’ token
make[4]: *** [evas_software_x11_test-evas_software_x11_main.o] Error 1
make[4]: Leaving directory `/root/e17_cvs/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/e17_cvs/e17/libs/evas/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17_cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/e17_cvs/e17/libs/evas'
make: *** [all] Error 2
-----------------------------------------------------------------------------
Looks like I'm not even getting as far as most of the other posters have.  Any ideas?  :confused: 

I'm now trying lut1n's script...(thanks, by the way):KS

---

### Post by David Valentine on 2006-03-02
Should lut1n's script be run as root?  sudo?  user?

---

### Post by Lut!n on 2006-03-02
It MUST be run as sudo ;), because it massively uses dpkg-buildpackage
But don't worry, everything's all right then for the rights on e17 folders:)

Translation is now more complete ;)

edit : I'm sorry, but you may experience problems if your previous installation was made 'manually', but you can try it :)

---

### Post by Jae686 on 2006-03-02
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/evas/src/bin/evas_software_win32'
make[4]: Entering directory `/home/jaerder/e17_cvs/e17/libs/evas/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/modules/engines -I../../src/lib -I../..   -I/opt/e17/include -g -O2 -I/usr/X11R6/include -g -O2 -MT evas_software_x11_test-evas_software_x11_main.o -MD -MP -MF ".deps/evas_software_x11_test-evas_software_x11_main.Tpo" -c -o evas_software_x11_test-evas_software_x11_main.o `test -f 'evas_software_x11_main.c' || echo './'`evas_software_x11_main.c; \
then mv -f ".deps/evas_software_x11_test-evas_software_x11_main.Tpo" ".deps/evas_software_x11_test-evas_software_x11_main.Po"; else rm -f ".deps/evas_software_x11_test-evas_software_x11_main.Tpo"; exit 1; fi
evas_software_x11_main.c:8:38: error: Evas_Engine_Software_X11.h: No such file or directory
evas_software_x11_main.c: In function ‘main’:
evas_software_x11_main.c:59: error: ‘Evas_Engine_Info_Software_X11’ undeclared (first use in this function)
evas_software_x11_main.c:59: error: (Each undeclared identifier is reported only once
evas_software_x11_main.c:59: error: for each function it appears in.)
evas_software_x11_main.c:59: error: ‘einfo’ undeclared (first use in this function)
evas_software_x11_main.c:61: error: syntax error before ‘)’ token
evas_software_x11_main.c:86: error: syntax error before ‘)’ token
evas_software_x11_main.c:111: error: syntax error before ‘)’ token
evas_software_x11_main.c:136: error: syntax error before ‘)’ token
evas_software_x11_main.c:161: error: syntax error before ‘)’ token
make[4]: *** [evas_software_x11_test-evas_software_x11_main.o] Error 1
make[4]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/evas/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/evas'
make: *** [all] Error 2
-----------------------------------------------------------------------------


any thoughts?

---

### Post by Adrian_b on 2006-03-02
You say you get permission errors when running the .sh install script as sudo..
Why not just install it as su?
[EDIT] Didn't read last pages, ignore this :p

---

### Post by Lut!n on 2006-03-02
No probleme with evas compilation, with py script and CVS from today, 12h :D

---

### Post by Adrian_b on 2006-03-02
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/modules/engines -I../../src/lib -I../..   -I/opt/e17/in clude -g -O2 -I/usr/X11R6/include -g -O2 -MT evas_software_x11_test-evas_software_x11_main.o -MD -MP -MF ".dep s/evas_software_x11_test-evas_software_x11_main.Tpo" \
  -c -o evas_software_x11_test-evas_software_x11_main.o `test -f 'evas_software_x11_main.c' || echo './'`evas_ software_x11_main.c; \
then mv -f ".deps/evas_software_x11_test-evas_software_x11_main.Tpo" ".deps/evas_software_x11_test-evas_softwa re_x11_main.Po"; \
else rm -f ".deps/evas_software_x11_test-evas_software_x11_main.Tpo"; exit 1; \
fi
evas_software_x11_main.c:8:38: error: Evas_Engine_Software_X11.h: No such file or directory
evas_software_x11_main.c: In function &#8216;main&#8217;:
evas_software_x11_main.c:59: error: &#8216;Evas_Engine_Info_Software_X11&#8217; undeclared (first use in this function)
evas_software_x11_main.c:59: error: (Each undeclared identifier is reported only once
evas_software_x11_main.c:59: error: for each function it appears in.)
evas_software_x11_main.c:59: error: &#8216;einfo&#8217; undeclared (first use in this function)
evas_software_x11_main.c:61: error: syntax error before &#8216;)&#8217; token
evas_software_x11_main.c:86: error: syntax error before &#8216;)&#8217; token
evas_software_x11_main.c:111: error: syntax error before &#8216;)&#8217; token
evas_software_x11_main.c:136: error: syntax error before &#8216;)&#8217; token
evas_software_x11_main.c:161: error: syntax error before &#8216;)&#8217; token
make[4]: *** [evas_software_x11_test-evas_software_x11_main.o] Error 1
make[4]: Leaving directory `/home/ab/e17_cvs/e17/libs/evas/src/bin'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/ab/e17_cvs/e17/libs/evas/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/ab/e17_cvs/e17/libs/evas/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/ab/e17_cvs/e17/libs/evas'
make: *** [all] Error 2


Having the same problems as all the other guys here -_-

[NOTE] Lut1n, could you list all dependencies for the script you gave?
Because the script constantly fails because of unmet packages so i need to check the execution.log about every time it compiles something and see what dependencies are unmet :s

---

### Post by Lut!n on 2006-03-02
Here are the dependancies for the script I gave : 

```
automake1.7 bison build-essential byacc checkinstall cvs cdbs debhelper fakeroot flex gettext libbz2-dev libdirectfb-dev libfreetype6-dev libglade2-dev libgstreamer0.8-dev libgtk1.2-dev libgtk2.0-dev libjpeg62-dev libltdl3-dev libncurses5-dev libpam-dev libpng3-dev libsqlite3-dev libssl-dev libtag1c2 libtagc0 libtagc0-dev libtiff4-dev libtool libttf-dev libungif4-dev libxine-dev libxml2 libxml2-dev libXxf86vm-dev pkg-config sqlite3 xlibs-dev
``` 


Note ONLY for Dapper users : you have to replace libtag1c2 by libtag1c2a, and install the latest checkinstall version aviable [here](http://asic-linux.com.mx/~izto/checkinstall/files/deb/checkinstall_1.6.0-1_i386.deb)

ONLY For Breezy users : you need to get libxine 1.1.1 in order to compile emotion. Download sources [here](http://prdownloads.sourceforge.net/xine/xine-lib-1.1.1.tar.gz) and then
```
tar -xzvf xine-lib-1.1.1.tar.gz
cd xine-lib-1.1.1
./autogen.sh && make
sudo make install
sudo gedit /etc/ld.so.conf
``` and add /usr/local/lib to the file, save and exit
Enjoy
Lut!n

---

### Post by Adrian_b on 2006-03-02
Tried again and it's giving me the same errors as the manual installation..
Kind of sucks..
I'm going to give up for a while.

---

### Post by Lut!n on 2006-03-02
I think you get the same error because you have a previous manual installation. Actually I think It should work if you could totally uninstall e17 and retrying with the script. But I don't know if there's an uninstallation option on the sh script ....

Edit : just think that removing /opt/e17 or any installation directoy you gave from your PATH would be enough to have the py script working properly (not sure, you can try)

---

### Post by wushumofo on 2006-03-02
[QUOTE=wushumofo]wha... what is it?

specifically... e_modules**//**monitor

// ???[/QUOTE]


I think I have the most retarded error on the forum...

any ideas?

---

### Post by Jae686 on 2006-03-03
and now i get

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ewl.log:
-----------------------------------------------------------------------------
ewl_border.c:153: error: 'data' undeclared (first use in this function)
ewl_border.c:153: error: 'EWL_FLAG_ALIGN_LEFT' undeclared (first use in this function)
ewl_border.c:156: error: 'EWL_FLAG_ALIGN_CENTER' undeclared (first use in this function)
ewl_border.c:159: error: 'EWL_FLAG_ALIGN_RIGHT' undeclared (first use in this function)
ewl_border.c:162: error: 'EWL_FLAG_ALIGN_TOP' undeclared (first use in this function)
ewl_border.c:165: error: 'EWL_FLAG_ALIGN_BOTTOM' undeclared (first use in this function)
ewl_border.c: At top level:
ewl_border.c:171: error: syntax error before '*' token
ewl_border.c: In function 'border_change_position':
ewl_border.c:174: error: 'w' undeclared (first use in this function)
ewl_border.c:178: warning: implicit declaration of function 'ewl_border_label_position_set'
ewl_border.c:178: error: 'data' undeclared (first use in this function)
ewl_border.c:178: error: 'EWL_POSITION_LEFT' undeclared (first use in this function)
ewl_border.c:181: error: 'EWL_POSITION_RIGHT' undeclared (first use in this function)
ewl_border.c:184: error: 'EWL_POSITION_TOP' undeclared (first use in this function)
ewl_border.c:187: error: 'EWL_POSITION_BOTTOM' undeclared (first use in this function)
make[4]: *** [ewl_border.lo] Error 1
make[4]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/ewl/src/bin/tests'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/ewl/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/ewl/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jaerder/e17_cvs/e17/libs/ewl'
make: *** [all] Error 2

is there a way to completly remove what the script installs in order to re-try?

---

### Post by Lut!n on 2006-03-03
Maybe you can go in the directory of each lib and app that the script compiles, and then "make uninstall" in xterm; you also have to remove /opt/e17 from you PATH if it's in

---

### Post by wushumofo on 2006-03-03
hahahaha... mine's partially working now...

UNABLE TO INITIALIZE IPC SUBSYSTEM...   :confused: :confused: :mad: :confused: :confused: 

so I try symlinking ~/.ecore to /tmp/mydir/ecore.....

still no dice.

it also said to go delete all the files in ~/.ecore/enlightenment
but I don't have an enlightenment directory in my /.ecore dir. :confused: :confused: 
maybe I should make one?

---

### Post by Lut!n on 2006-03-03
```
sudo chown -R 1000 ~/.ecore
sudo chown -R 1000 ~/.e
```
enjoy ;)

---

### Post by wushumofo on 2006-03-03
HOT DAMN, LUT!N

THANK YOU MAN!

you are awesome!

---

### Post by Lut!n on 2006-03-03
Hi all, I'd just like to know if some of you have tested the py script and if they got errors using it. Thanks

@wushumofo : thanks ;)

---

### Post by David Valentine on 2006-03-03
> I'd just like to know if some of you have tested the py script and if they got errors using it.Yes, I did yesterday but I don't remember what the errors were (but they were show-stoppers).  I'll try again in the next couple of days and report back what they were.

---

### Post by firecat53 on 2006-03-03
For those of you using the easy_e17.sh script, here's a few ideas to check out before posting errors here:

1. Ensure ALL previous e17 installations are completely removed!!! This happens primarily when people have used the Shadoi(?) repositories. You have to basically search your system for any files that have to do with e17. I wish I could tell you what to look for, but I just had to do multiple searches for e* things and hope I recognized the e17 files vs any other system files. (I borked a few things accidentally this way....be warned).

2. Delete your e17_cvs directory and re-run the script

3. Wait a day or two, delete your e17_cvs directory and then try again. This is CVS, so sometimes things will be broken for awhile!! Be patient....it will get fixed. It's a very active project!

Good luck and enjoy it :)

---

### Post by Lut!n on 2006-03-04
Hi all,
according to firecat53 I think you'll also have to completely uninstall your current e17 if you want the py script to work properly(you can backup your /opt/e17 directory, though). You'll also have to remove your installation directory from your PATH (in /etc/environment) if you added the directory in the PATH, and , it's important, remove the line "/opt/e17/lib" from your /etc/ld.so.conf file

you can e-mail me (or post here if it doesn't matter) bug reports, if there are some problems

Regards, Lut!n

---

### Post by Tails on 2006-03-04
[QUOTE=wushumofo]I think I have the most retarded error on the forum...

any ideas?[/QUOTE]

mmm, I also have that monitor error... i think the script isnt grabbing the monitor module from the CVS...

---

### Post by Lut!n on 2006-03-04
Hi,
It's just because monitor module no longer exists :D
the directory still exists in the CVS, but the module has been splitted into 5 new modules some days ago
Here are the name of those new modules : cpu, net, mem, wlan and uptime
Enjoy ;)

---

### Post by detyabozhye on 2006-03-04
Here's what I get, I think something's wrong on my comp, but I don't know what.
```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/imlib2.log:
-----------------------------------------------------------------------------
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking how to run the C++ preprocessor... /lib/cpp
configure: error: C++ preprocessor "/lib/cpp" fails sanity check
See `config.log' for more details.

```

---

### Post by Luzbel on 2006-03-04
Worked perfectly in Dapper here. I was just wondering which directory has the source for e17genmenu. Thanks :)

---

### Post by Lut!n on 2006-03-05
@Luzbel : Even if e17genmenu exists in the CVS(apps/e_utils), it's not compilable yet. You have to get sources [here](http://sourceforge.net/project/showfiles.php?group_id=131470) and the compile yourself```
./autogen.sh 
make
sudo make install
e17genmenu
```
You'll see some kind of weirdness running this version, but the menus are created, though.
Enjoy

---

### Post by Luzbel on 2006-03-05
Thank you, Lut!n. I'll compile it, no problem ;)

Oh! BTW, how do I change GTK apps look and feel? They're ugly now. I come from KDE, so has no idea on this topic.

Thanks!

---

### Post by s_spiff on 2006-03-11
>  CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...
cvs checkout: warning: failed to open /home/alok/.cvspass for reading: No such file or directory
cvs checkout: authorization failed: server cvs.sourceforge.net rejected access to /cvsroot/enlightenment for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
cvs checkout: warning: failed to open /home/alok/.cvspass for reading: No such file or directory
cvs checkout: authorization failed: server cvs.sourceforge.net rejected access to /cvsroot/enlightenment for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
cvs checkout: warning: failed to open /home/alok/.cvspass for reading: No such file or directory
cvs checkout: authorization failed: server cvs.sourceforge.net rejected access to /cvsroot/enlightenment for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
cvs checkout: warning: failed to open /home/alok/.cvspass for reading: No such file or directory
cvs checkout: authorization failed: server cvs.sourceforge.net rejected access to /cvsroot/enlightenment for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
cvs checkout: warning: failed to open /home/alok/.cvspass for reading: No such file or directory
cvs checkout: authorization failed: server cvs.sourceforge.net rejected access to /cvsroot/enlightenment for user anonymous
cvs checkout: used empty password; try "cvs login" with a real password
 
thats the error I get when running the script, someone help me with this.I'm a noob to linux.:P
1) never installed e17 beofre..this is a fresh installation of ubuntu itself..so e16 or 17 is out of the question...
2)on my last attempt...before i formatted the hdd and reinstalled ubuntu, I got exactly same stupid errors!
3) > U e17/apps/e/data/fonts/VeraSe.ttf
U e17/apps/e/data/fonts/VeraSeBd.ttf
U e17/apps/e/data/fonts/baekmuk.COPYING
U e17/apps/e/data/fonts/dotum.ttf
U e17/apps/e/data/fonts/fireflysung.COPYING

Its copying something..and it always gets stuck at fireflysung.copying! i mean..this is actually my fourth attempt! and it still does that! driving me crazy!

---

### Post by Lut!n on 2006-03-11
@s_spiff
1/ : look in your home directory and see if the file exists. If it does, then ```
sudo chown 1000 ~/.cvspass
chmod 755 ~/.cvspass
```
if it doesn't just create it :)

3/ : just wait, the CVS is sometimes slow, espacially for this file(it may be a large file). It can take up to half an hour to download it,  depending on your internet connection. Don't worry, it's not really stock, you just have to wait ....

@Luzbel : you have to load gnome-settings-daemon at e17 startup in order to de-uglyfy your GTK apps. If you don't have it, then you should install gtk-theme-switch and modify your GTK theme using switch2

---

### Post by btf on 2006-03-12
> LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
mkdir .libs
gcc -g -O2 -o .libs/edje edje_main.o  -L/opt/e17/lib ../../src/lib/.libs/libedje.so
edje_main.o: In function `main':
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:76: undefined reference to `ecore_evas_init'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:118: undefined reference to `ecore_evas_software_x11_new'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:127: undefined reference to `ecore_evas_callback_delete_request_set'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:128: undefined reference to `ecore_evas_callback_resize_set'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:129: undefined reference to `ecore_evas_callback_pre_render_set'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:130: undefined reference to `ecore_evas_callback_post_render_set'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:131: undefined reference to `ecore_evas_title_set'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:132: undefined reference to `ecore_evas_name_class_set'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:133: undefined reference to `ecore_evas_show'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:134: undefined reference to `ecore_evas_get'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:146: undefined reference to `ecore_evas_shutdown'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:124: undefined reference to `ecore_evas_xrender_x11_new'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:120: undefined reference to `ecore_evas_gl_x11_new'
/root/e17_cvs/e17/libs/edje/src/bin/edje_main.c:122: undefined reference to `ecore_evas_fb_new'
collect2: ld returned 1 exit status
make[3]: *** [edje] Fout 1
make[3]: Leaving directory `/root/e17_cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Fout 1
make[2]: Leaving directory `/root/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Fout 1
make[1]: Leaving directory `/root/e17_cvs/e17/libs/edje'
make: *** [all] Fout 2



Can anyone help me with this problem ?? Any help is great

---

### Post by jakeee on 2006-03-12
I get the following error when compiling ewl
> LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... previous installed
- epsilon .................... previous installed
- esmart ..................... previous installed
- emotion .................... SKIPPED
- ewl ........................ ERROR!      
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ewl.log:
-----------------------------------------------------------------------------
edje_cc: Wrote       634 bytes (   1Kb) for "collections/49" collection entry
edje_cc: Wrote       633 bytes (   1Kb) for "collections/50" collection entry
edje_cc: Wrote      1000 bytes (   1Kb) for "collections/51" collection entry
edje_cc: Wrote       726 bytes (   1Kb) for "collections/52" collection entry
edje_cc: Wrote       727 bytes (   1Kb) for "collections/53" collection entry
edje_cc: Wrote       876 bytes (   1Kb) for "collections/54" collection entry
edje_cc: Wrote       801 bytes (   1Kb) for "collections/55" collection entry
edje_cc: Wrote      1960 bytes (   2Kb) for "collections/56" collection entry
edje_cc: Wrote      2028 bytes (   2Kb) for "collections/57" collection entry
edje_cc: Wrote       727 bytes (   1Kb) for "collections/58" collection entry
edje_cc: Wrote       918 bytes (   1Kb) for "collections/59" collection entry
edje_cc: Wrote       713 bytes (   1Kb) for "collections/60" collection entry
edje_cc: Wrote       714 bytes (   1Kb) for "collections/61" collection entry
edje_cc: Wrote       829 bytes (   1Kb) for "collections/62" collection entry
edje_cc: Wrote      1098 bytes (   1Kb) for "collections/63" collection entry
edje_cc: Wrote      1055 bytes (   1Kb) for "collections/64" collection entry
edje_cc: Wrote       837 bytes (   1Kb) for "collections/65" collection entry
edje_cc: Wrote       698 bytes (   1Kb) for "collections/66" collection entry
make[3]: *** [e17.edj] Error 255
make[3]: Leaving directory `/home/jakeee/e17_cvs/e17/libs/ewl/data/themes'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jakeee/e17_cvs/e17/libs/ewl/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jakeee/e17_cvs/e17/libs/ewl'
make: *** [all] Error 2
-----------------------------------------------------------------------------


Any help is appreciated.

---

### Post by Sitarane on 2006-03-14
Hi,

Why don't you try the [manual way]("http://perso.wanadoo.fr/heliotopik/enterE17_cvs.html") ? DR 17 rocks !

Cheers

---

### Post by potrick on 2006-03-14
It took a while, and I had to switch the mirror and delete all the made files a number of times, but I managed to get it working and I'm really happy with it. Don't give up, it's worth it! nicer looking and faster. Just keep reading through this thread and you'll figure it out.

---

### Post by jakeee on 2006-03-14
I got past the ewl part and now I'm stuck again :) This time I have to compile e and now I'm not sure what's wrong with this :/
> /bin/sh ../../libtool --mode=link gcc  -g -O2   -o enlightenment -export-dynamic -L/usr/local/lib -levas -L/usr/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -lecore_dbus -L/usr/lib -leet -lz -ljpeg -lm -L/usr/lib -ledje -L/usr/local/lib -leet -lz -ljpeg -L/usr/lib -lembryo -lm    -L/usr/X11R6/lib -lX11 -lXext -ldl   e_main.o e_user.o e_manager.o e_path.o e_init.o e_ipc.o e_error.o e_container.o e_zone.o e_desk.o e_border.o e_pointer.o e_config.o e_menu.o e_object.o e_icon.o e_box.o e_int_menus.o e_module.o e_apps.o e_atoms.o e_utils.o e_canvas.o e_focus.o e_place.o e_resist.o e_startup.o e_hints.o e_gadman.o e_gadget.o e_signals.o e_xinerama.o e_table.o e_layout.o e_test.o e_font.o e_intl.o e_theme.o e_dnd.o e_bindings.o e_moveresize.o e_actions.o e_popup.o e_ipc_codec.o e_prefix.o e_datastore.o e_msg.o e_winlist.o e_alert.o e_maximize.o e_grabinput.o e_bg.o e_remember.o e_win.o e_pan.o e_dialog.o e_about.o e_theme_about.o e_apps_cache.o e_entry.o e_fileman.o e_fileman_smart.o e_fileman_file.o e_fileman_icon.o e_fileman_mime.o e_widget.o e_widget_check.o e_widget_radio.o e_widget_framelist.o e_widget_list.o e_widget_button.o e_widget_label.o e_widget_frametable.o e_widget_table.o e_widget_entry.o e_widget_image.o e_config_dialog.o e_int_config_focus.o e_icon_grid.o e_icon_canvas.o e_int_config_desks.o e_configure.o e_int_border_locks.o e_thumb.o e_int_border_remember.o e_eap_editor.o e_widget_iconsel.o e_widget_fileman.o e_scrollframe.o e_file_selector.o e_file_dialog.o e_int_border_menu.o e_ilist.o e_tlist.o e_livethumb.o e_int_border_border.o e_widget_ilist.o e_widget_tlist.o e_slider.o e_widget_slider.o e_int_config_window_manipulation.o e_int_config_window_display.o e_int_config_background.o e_int_config_background_import.o e_int_config_theme.o e_int_config_menus.o e_int_config_keybindings.o e_int_config_cursor.o e_int_config_startup.o e_int_config_performance.o e_int_config_winlist.o e_int_config_display.o e_int_config_desklock.o e_int_config_exebuf.o e_int_config_cfgdialogs.o e_int_config_hinting.o e_deskpreview.o e_exebuf.o e_desklock.o e_int_config_modules.o e_exehist.o e_color_class.o e_widget_textblock.o e_apps_error.o e_stolen.o e_gadcon.o e_shelf.o e_widget_preview.o   
gcc -g -O2 -o enlightenment e_main.o e_user.o e_manager.o e_path.o e_init.o e_ipc.o e_error.o e_container.o e_zone.o e_desk.o e_border.o e_pointer.o e_config.o e_menu.o e_object.o e_icon.o e_box.o e_int_menus.o e_module.o e_apps.o e_atoms.o e_utils.o e_canvas.o e_focus.o e_place.o e_resist.o e_startup.o e_hints.o e_gadman.o e_gadget.o e_signals.o e_xinerama.o e_table.o e_layout.o e_test.o e_font.o e_intl.o e_theme.o e_dnd.o e_bindings.o e_moveresize.o e_actions.o e_popup.o e_ipc_codec.o e_prefix.o e_datastore.o e_msg.o e_winlist.o e_alert.o e_maximize.o e_grabinput.o e_bg.o e_remember.o e_win.o e_pan.o e_dialog.o e_about.o e_theme_about.o e_apps_cache.o e_entry.o e_fileman.o e_fileman_smart.o e_fileman_file.o e_fileman_icon.o e_fileman_mime.o e_widget.o e_widget_check.o e_widget_radio.o e_widget_framelist.o e_widget_list.o e_widget_button.o e_widget_label.o e_widget_frametable.o e_widget_table.o e_widget_entry.o e_widget_image.o e_config_dialog.o e_int_config_focus.o e_icon_grid.o e_icon_canvas.o e_int_config_desks.o e_configure.o e_int_border_locks.o e_thumb.o e_int_border_remember.o e_eap_editor.o e_widget_iconsel.o e_widget_fileman.o e_scrollframe.o e_file_selector.o e_file_dialog.o e_int_border_menu.o e_ilist.o e_tlist.o e_livethumb.o e_int_border_border.o e_widget_ilist.o e_widget_tlist.o e_slider.o e_widget_slider.o e_int_config_window_manipulation.o e_int_config_window_display.o e_int_config_background.o e_int_config_background_import.o e_int_config_theme.o e_int_config_menus.o e_int_config_keybindings.o e_int_config_cursor.o e_int_config_startup.o e_int_config_performance.o e_int_config_winlist.o e_int_config_display.o e_int_config_desklock.o e_int_config_exebuf.o e_int_config_cfgdialogs.o e_int_config_hinting.o e_deskpreview.o e_exebuf.o e_desklock.o e_int_config_modules.o e_exehist.o e_color_class.o e_widget_textblock.o e_apps_error.o e_stolen.o e_gadcon.o e_shelf.o e_widget_preview.o -Wl,--export-dynamic  -L/usr/local/lib /usr/local/lib/libevas.so -L/usr/lib /usr/local/lib/libecore.so /usr/local/lib/libecore_job.so /usr/local/lib/libecore_x.so /usr/lib/libecore_evas.so /usr/local/lib/libecore_con.so /usr/local/lib/libecore_ipc.so /usr/local/lib/libecore_txt.so /usr/local/lib/libecore_fb.so /usr/lib/libecore_config.so /usr/lib/libecore_file.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -lssl -lcrypto /usr/lib/libecore_dbus.so /usr/lib/libedje.so /usr/local/lib/libeet.so -lz /usr/lib/libjpeg.so /usr/lib/libembryo.so -lm -L/usr/X11R6/lib -lX11 -lXext -ldl -Wl,--rpath -Wl,/usr/local/lib -Wl,--rpath -Wl,/usr/local/lib
e_ipc.o: In function `_e_ipc_cb_client_data':/home/jakeee/e17_cvs/e17/apps/e/src/bin/e_ipc_handlers.h:7341: undefined reference to `edje_color_class_list'
e_color_class.o: In function `e_color_class_del':/home/jakeee/e17_cvs/e17/apps/e/src/bin/e_color_class.c:77: undefined reference to `edje_color_class_del'
collect2: ld returned 1 exit status
make[3]: *** [enlightenment] Error 1
make[3]: Leaving directory `/home/jakeee/e17_cvs/e17/apps/e/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/jakeee/e17_cvs/e17/apps/e/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jakeee/e17_cvs/e17/apps/e'
make: *** [all] Error 2


---

### Post by Lut!n on 2006-03-14
I really don't know where it comes from. 
If you want to compile e17 now and if you don't mind to compile "old" sources (28th january), you should take the sources in my signature, they work fine.

Enjoy,
Lut!n

---

### Post by mrgnash on 2006-03-14
[QUOTE=Lut!n]I really don't know where it comes from. 
If you want to compile e17 now and if you don't mind to compile "old" sources (28th january), you should take the sources in my signature, they work fine.

Enjoy,
Lut!n[/QUOTE]

Downloaded and extracted... now what do I do with it? :confused:

---

### Post by Lut!n on 2006-03-14
Now, you download the script of the first page on this wiki, you just follow the instructions - be careful not to update cvs sources, because you already have them ;) - and everything's going to be fine :)

---

### Post by mrgnash on 2006-03-14
Here's what I get:

```
#############################################################################
#             easy_e17.sh (0.9.9) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#         Thanks to David 'onefang' Seikel for contributing patches!        #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: http://omicron.homeip.net/projects/ | Contact: morlenxus@gmx.net #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/mrgnash/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave
  - installable apps:     entrance e eclair evfs
  - installable misc:     engage
  - installable proto:    etk exhibit entropy
  - installable modules:  calendar flame monitor mount rain screenshot slideshow snow tclock weather
  - skipping:             emotion eclair
  - install only this:    ALL

  - script action:    install


BUILD PHASE: 1/3
  - running some basic system checks
  - cvs checkout/update

#############################################################################



BASIC SYSTEM CHECKS:
-----------------------------------------------------------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok
- setting compile options .... ok
-----------------------------------------------------------------------------

CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...
cvs [checkout aborted]: unrecognized auth response from cvs.sourceforge.net: M -!- Client or Server timeout occurred!
cvs [checkout aborted]: unrecognized auth response from cvs.sourceforge.net: M -!- Client or Server timeout occurred!
cvs [checkout aborted]: received interrupt signal
FAILED! Next attempt 4 in 9 secondss

```

---

### Post by benplaut on 2006-03-15
just so everyone knows, the CVS repo has been down for a few hours, and will probably be down for a few more.

Don't Panic.

---

### Post by Lut!n on 2006-03-15
@mrgnash : I said you NOT TO UPDATE the sources .... there's an option for that in the script, just look at it ;)

In fact, you have to run the script with the --skip-cvsupdate flag not to update your local sources. And of course the -i to install

Enjoy,
Lut!n

---

### Post by mrgnash on 2006-03-15
Thanks :)

Well it was looking pretty good for awhile... and then it screwed up on edje. Still no E17 for awhile for me then :-/

---

### Post by Lut!n on 2006-03-15
what's your errorlog ?

---

### Post by mrgnash on 2006-03-15
```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2  -L/opt/e17/lib -o libedje.la -rpath /opt/e17/lib -version-info 5:0:5 libedje_la-edje_calc.lo libedje_la-edje_callbacks.lo libedje_la-edje_data.lo libedje_la-edje_embryo.lo libedje_la-edje_load.lo libedje_la-edje_main.lo libedje_la-edje_misc.lo libedje_la-edje_program.lo libedje_la-edje_smart.lo libedje_la-edje_text.lo libedje_la-edje_util.lo libedje_la-edje_var.lo libedje_la-edje_container.lo libedje_la-edje_message_queue.lo libedje_la-edje_cache.lo libedje_la-edje_textblock_styles.lo -lm -L/opt/e17/lib -levas -L/opt/e17/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -lecore_dbus -L/opt/e17/lib -leet -lz -ljpeg -lm -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -lembryo -lm
gcc -shared  .libs/libedje_la-edje_calc.o .libs/libedje_la-edje_callbacks.o .libs/libedje_la-edje_data.o .libs/libedje_la-edje_embryo.o .libs/libedje_la-edje_load.o .libs/libedje_la-edje_main.o .libs/libedje_la-edje_misc.o .libs/libedje_la-edje_program.o .libs/libedje_la-edje_smart.o .libs/libedje_la-edje_text.o .libs/libedje_la-edje_util.o .libs/libedje_la-edje_var.o .libs/libedje_la-edje_container.o .libs/libedje_la-edje_message_queue.o .libs/libedje_la-edje_cache.o .libs/libedje_la-edje_textblock_styles.o  -L/opt/e17/lib /opt/e17/lib/libevas.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_dbus.so /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so /opt/e17/lib/libembryo.so -lm  -Wl,-soname -Wl,libedje.so.0 -o .libs/libedje.so.0.5.0
(cd .libs && rm -f libedje.so.0 && ln -s libedje.so.0.5.0 libedje.so.0)
(cd .libs && rm -f libedje.so && ln -s libedje.so.0.5.0 libedje.so)
ar cru .libs/libedje.a  libedje_la-edje_calc.o libedje_la-edje_callbacks.o libedje_la-edje_data.o libedje_la-edje_embryo.o libedje_la-edje_load.o libedje_la-edje_main.o libedje_la-edje_misc.o libedje_la-edje_program.o libedje_la-edje_smart.o libedje_la-edje_text.o libedje_la-edje_util.o libedje_la-edje_var.o libedje_la-edje_container.o libedje_la-edje_message_queue.o libedje_la-edje_cache.o libedje_la-edje_textblock_styles.o
ranlib .libs/libedje.a
creating libedje.la
(cd .libs && rm -f libedje.la && ln -s ../libedje.la libedje.la)
make[3]: Leaving directory `/home/mrgnash/e17_cvs/e17/libs/edje/src/lib'
Making all in bin
make[3]: Entering directory `/home/mrgnash/e17_cvs/e17/libs/edje/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../bin -I../../src/lib -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include  -I/opt/e17/include  -g -O2 -MT edje_main.o -MD -MP -MF ".deps/edje_main.Tpo" -c -o edje_main.o edje_main.c; \
then mv -f ".deps/edje_main.Tpo" ".deps/edje_main.Po"; else rm -f ".deps/edje_main.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2  -L/opt/e17/lib -o edje edje_main.o ../../src/lib/libedje.la
mkdir .libs
gcc -g -O2 -o .libs/edje edje_main.o  -L/opt/e17/lib ../../src/lib/.libs/libedje.so
../../src/lib/.libs/libedje.so: undefined reference to `eet_data_descriptor2_new'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/mrgnash/e17_cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/mrgnash/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/mrgnash/e17_cvs/e17/libs/edje'
make: *** [all] Error 2

```

Good luck making any sense out of that. I sure can't ;)

---

### Post by firecat53 on 2006-03-15
If you're using the easy_e17.sh script, some of the modules have changed, and need to be removed or added from the list at the beginning of the script. Monitor I know has been removed, and wlan added. It will give you an error for monitor (using recent CVS, at least) if you don't remove it from the list, since it doesn't exist anymore. I haven't gone through yet to see if there are other modules that could be changed (my laptop's at home).

Scott

---

### Post by Lut!n on 2006-03-15
Monitor has been splitted into five modules : cpu, mem, net, wlan and uptime

@mrgnash : don't see why you get this, I don't use this script. Make sure you did everything you were told to do in the first post.
If you don't mind to compile manually, you can try sitarane's guide. Make a search like installing e17 manually to find it. Otherwise, you can try the script in my signature (works for sure, I still use the sources I gave you). The dependancies list and instructions to use it were given a few posts ago.
Good luck
Lut!n

---

### Post by mrgnash on 2006-03-16
Thanks for all your help :)

I ran your script and got as far as package 14 in the libs: 'ewl' - it wants 'libemotion-dev' which I can't find in synaptic (unlike some of the other files it asked for during compilation).

---

### Post by Lut!n on 2006-03-16
Hi, 
don't know if you took the time to read my previous posts, but I said that breezy users must compile libxine 1.1.1 in order to have it working properly. :)
I gave instructions here : [http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208](http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208)
when you start the script, just restart compilation from lib. 12 and it's going to work fine (of course you have to say yes when the script asks you if you want to compile emotion)
Enjoy,
Lut!n

---

### Post by mrgnash on 2006-03-16
[QUOTE=Lut!n]Hi, 
don't know if you took the time to read my previous posts, but I said that breezy users must compile libxine 1.1.1 in order to have it working properly. :)
I gave instructions here : [http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208](http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208)
when you start the script, just restart compilation from lib. 12 and it's going to work fine (of course you have to say yes when the script asks you if you want to compile emotion)
Enjoy,
Lut!n[/QUOTE]

Yes, I went back and read through some of your posts but I missed that one - sorry :(

Anyway, it has finally installed! Thankyou very very much for your help. It really is the most beautiful window manager I have seen before, so it makes it all feel worth it \\:D/ 

The only thing that didn't install was the modules... I guess I have to install them seperately in some way?

Other than that, everything looks fine :D I can't work out where it puts my apps when I minimize them, but that's what docs are for :-k

---

### Post by Lut!n on 2006-03-16
Hi,
to see your minimized apps, enable the module iBox :) (left click => modules => then enable iBox)
for the additionnal e_modules, i'm sure there are with your sources. You just have to use the 4th choice of the script (compile e_modules), and see what modules are aviable.
As the script isn't sync with this 'old' cvs, you may have to look into your sources/e_modules directory to see what modules are really aviable.
Enjoy,
Lut!n

---

### Post by jakeee on 2006-03-17
Yeah! Another problem... This time with entropy
> LAST LOGLINES FROM /tmp/easy_e17/install_logs/entropy.log:
-----------------------------------------------------------------------------
make[1]: Entering directory `/home/jakeee/e17_cvs/e17/proto/entropy/src'
Making all in plugins
make[2]: Entering directory `/home/jakeee/e17_cvs/e17/proto/entropy/src/plugins'
if /bin/sh ../../libtool --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DCONFIGURED_WITH=\"--prefix=/opt/e17\" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_UNISTD_H=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_PTHREAD=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/home/jakeee/e17_cvs/e17/proto/entropy\"  -I. -I. -I. -I../.. -I../../src/include  -I/opt/e17/include -I/usr/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-layout_etk_simple.lo -MD -MP -MF ".deps/layout_etk_simple_la-layout_etk_simple.Tpo" \
          -c -o layout_etk_simple_la-layout_etk_simple.lo `test -f 'layout_etk_simple.c' || echo './'`layout_etk_simple.c; \
        then mv -f ".deps/layout_etk_simple_la-layout_etk_simple.Tpo" ".deps/layout_etk_simple_la-layout_etk_simple.Plo"; \
        else rm -f ".deps/layout_etk_simple_la-layout_etk_simple.Tpo"; exit 1; \
        fi
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DCONFIGURED_WITH=\"--prefix=/opt/e17\" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int "-DSELECT_TYPE_ARG234=(fd_set *)" "-DSELECT_TYPE_ARG5=(struct timeval *)" -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_UNISTD_H=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_PTHREAD=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/home/jakeee/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/usr/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-layout_etk_simple.lo -MD -MP -MF .deps/layout_etk_simple_la-layout_etk_simple.Tpo -c layout_etk_simple.c  -fPIC -DPIC -o .libs/layout_etk_simple_la-layout_etk_simple.o
layout_etk_simple.c: In function '_entropy_etk_menu_item_new':
layout_etk_simple.c:100: warning: implicit declaration of function 'etk_menu_item_image_new_with_label'
layout_etk_simple.c:100: warning: assignment makes pointer from integer without a cast
layout_etk_simple.c:103: warning: implicit declaration of function 'etk_menu_item_separator_new'
layout_etk_simple.c:103: warning: assignment makes pointer from integer without a cast
layout_etk_simple.c:113: warning: implicit declaration of function 'ETK_MENU_ITEM_IMAGE'
layout_etk_simple.c:113: warning: passing argument 1 of 'etk_menu_item_image_set' makes pointer from integer without a cast
layout_etk_simple.c: In function 'entropy_plugin_layout_create':
layout_etk_simple.c:339: error: 'ETK_STOCK_PLACES_FOLDER_SAVED_SEARCH' undeclared (first use in this function)
layout_etk_simple.c:339: error: (Each undeclared identifier is reported only once
layout_etk_simple.c:339: error: for each function it appears in.)
make[2]: *** [layout_etk_simple_la-layout_etk_simple.lo] Error 1
make[2]: Leaving directory `/home/jakeee/e17_cvs/e17/proto/entropy/src/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/jakeee/e17_cvs/e17/proto/entropy/src'
make: *** [all-recursive] Error 1
-----------------------------------------------------------------------------


---

### Post by Lut!n on 2006-03-17
cvs sources may be broken, the only thing to do is waiting ;)
When did you dowload your sources ?

---

### Post by jakeee on 2006-03-17
Hmm... I think it was a bit before the CVS repo went down.

---

### Post by Lut!n on 2006-03-18
Hi all,
sourceforge anonymous cvs server is back online
Enjoy

---

### Post by lizardking on 2006-03-18
[QUOTE=Lut!n]Hi all,
sourceforge anonymous cvs server is back online
Enjoy[/QUOTE]

Don't seem to me..
```

...
CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Checkout repo 'e17' ...

```

---

### Post by 9Digits on 2006-03-19
Sourceforge CVS has stunk every time I've ever tried to utilize it, today being the latest example.

This has been going on for me all day:

cvs [checkout aborted]: unrecognized auth response from cvs.sourceforge.net: M -!- Client or Server timeout occurred!
FAILED! Next attempt 10 in 109 seconds

---

### Post by johnnieandersson on 2006-03-22
```

- monitor .................... ./easy_e17.sh: line 224: cd: /root/e17_cvs/e_modules//monitor: File or map doesnt exists

```

What should i do to get behind/solve that problem?

---

### Post by Lut!n on 2006-03-22
You should look through the script and remove the monitor module from the list of compilable modules, because it no longer exists
Enjoy

---

### Post by donkey on 2006-03-29
How do I update E after installing?  Also, I don't seem to have the "enlightenment_remote" or "edje_decc" etc programs.  Any ideas?

---

### Post by Rui Pais on 2006-03-29
[QUOTE=Lut!n]You should look through the script and remove the monitor module from the list of compilable modules, because it no longer exists
Enjoy[/QUOTE]
hi,
or even better, replace monitor at
```
e_modules="calendar flame monitor mount ...
```with your favorite modules, like:
```
e_modules="calendar flame cpu mem net ...  mount ...
```

btw, i add embrace and e_utils to the list and the both worked good. 
i missed those.

---

### Post by Lut!n on 2006-03-30
A big update of the script will be availabe in a few hours, just two little things to fix and it's gonna be all right :D

---

### Post by Lut!n on 2006-03-30
Hi,
@Rui Pais : you didn't need to put e_utils in the list, it's compiled with the apps, just after E ;)

Now an update is available, with a big code cleanup, nice level option, re-sync with CVS and get-e, (modules, themes, etc), and a whole translation (I know the translation is bad, please e-mail me to correct the faults)

You can download it in my signature. I gave instructions here : [http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208](http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208), if you want it to work properly. DO NOT FORGET to delete your folder ~/.e/e/config and  ~/.ecore. Otherwise, you'll see some kind of weirdness such as each module enabled twice on your desktop

People who kwnows python can read through the script, there are little FIXMEs in it.

Enjoy
Lut!n

---

### Post by Rui Pais on 2006-03-30
> **Lut!n]Hi,
@Rui Pais : you didn't need to put e_utils in the list, it's compiled with the apps, just after E  said:**
> http://www.ubuntuforums.org/showpost.php?p=785386&postcount=208[/url], if you want it to work properly. DO NOT FORGET to delete your folder ~/.e/e/config and  ~/.ecore. Otherwise, you'll see some kind of weirdness such as each module enabled twice on your desktop

People who kwnows python can read through the script, there are little FIXMEs in it.

Enjoy
Lut!n

Hi,
sorry but in my case some parts of e_utils was not there.
I miss entangle among others.

Maybe we are not talk of same script... I was refering to easy_e17.sh of the howto of first post. 
Your signature points to a python file. I haven't yet try it. 

Thanks anyway, Rui.

---

### Post by klahjn on 2006-04-04
I'll really enjoy when ebuntu is released using dapper platform.   :::coos under enlightenment 17 goodness::::

---

### Post by funkenstein on 2006-04-04
hey, I've just got to step 4) where it says 
```
http://easylinux.info/wiki/Ubuntu#How_to_install_.deb_files_via_right_click_menu
``` it should say ```
sudo chown -R **user_name**:**group_name** ~/.ecore
``` shouldn't it? It was giving me "chown: `user:yonatan': invalid user" errors :( 

and while I'm on it, when I run ```
sudo chown -R yonatan:yonatan ~/.ecore
``` It tells me: ```
chown: cannot access `/home/yonatan/.ecore': No such file or directory
```

what now??? :-(

---

### Post by digdug on 2006-04-07
I know this is a bit OT, I'm trying to install euphoria on E17. I used this script to install it from CVS, because the compiled version seems much faster than any debian package I've seen. However, I've installed XMMS2 through apt.

So to install Euphoria, you have to install all these ruby bindings, and some extra XMMS2 stuff for E17 ruby clients. The ruby bindings install fine by compiling from source, but the XMMS2 stuff I was just going to grab through apt. Unfortunately, its asking for xmmsclient-ecore, which won't install because it depends on ecore0, which is installed, but apt doesn't know it is.

I've tried running apt with --ignore-dependencies... or whatever that switch is, but its still not happy. Is there any way to just inform apt that E17 is installed, or is the best option to just debianize all the compiled E17 CVS, and then install it using apt? That sounds like a real pain.

---

### Post by almahtar on 2006-04-15
Heya folks.  I was getting the "eet_data_descriptor2_new" error (undefined reference blah blah while compiling edje), and solved it.

The problem is an old version of eet, most likely installed from the Shadoi repository version of e17.

To fix it, run synaptic and search for "eet."  You should find a lot of things that don't matter, and only about 2 that do.  I'm running Dapper so if you're in Breezy it may be different for you.  I ditched libeet0 and errrr... one other package... (sorry, I forget what it was called), and edje compiles great now.

After that I got the //monitor problem a few of you were getting and followed Lut!n's advice by removing the "monitor" module in easy_e17.sh and replacing it with any modules found in my ~/e17cvs/e_modules folder that weren't already there.  That fixed the monitor issue.  It's still in the process of compiling but got farther than before.  I'll post again if I have any issues and hopefully their solutions.

*edit: It worked!!!*

---

### Post by patrick295767 on 2006-04-20
deleted ... It was solved with 1.7 automake ... 
 script running for the moment ...
 Greetz

It worked perfectly !!

Thank you very much !!

---
I did this and no problem

> apt-get update


apt-get -f -y install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev


apt-get -f -y install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev

apt-get -f -y install libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev

apt-get -f -y install libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev

apt-get -f -y install autoconf pkg-config libpng3-dev




apt-get -f -y remove automake1.4 automake1.6 automake1.8 automake1.9
apt-get -f -y install automake1.7
./easy_e17.sh -i --skip=eclair,emotion

---

### Post by syklitengutt on 2006-04-20
ok... need some help...
get this error all the time:

chris@chris:~$ sudo ./easy_e17.sh -i --skip=emotion,eclair


#############################################################################
#             easy_e17.sh (1.0.0) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#         Thanks to David 'onefang' Seikel for contributing patches!        #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/) | Contact: [email]morlenxus@gmx.net[/email] #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/chris/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave
  - installable apps:     entrance e eclair evfs e_utils
  - installable misc:     engage
  - installable proto:    etk exhibit entropy ephoto empower
  - installable modules:  calendar cpu devian flame mbar mem mount net rain screenshot slideshow snow tclock uptime weather wlan
  - skipping:             emotion eclair

  - script action:        install


BUILD PHASE: 1/3
  - running some basic system checks
  - cvs checkout/update

#############################################################################



BASIC SYSTEM CHECKS:
-----------------------------------------------------------------------------
- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. root
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf
/etc/ld.so.conf~)
- setting compile options .... ok
-----------------------------------------------------------------------------

CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Updating repo 'e17' (please wait, this won't output much) ...
Updating repo 'misc' (please wait, this won't output much) ...
Updating repo 'e_modules' (please wait, this won't output much) ...
-----------------------------------------------------------------------------


PREPARING FOR PHASE 2...

#############################################################################
#             easy_e17.sh (1.0.0) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#         Thanks to David 'onefang' Seikel for contributing patches!        #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: [http://omicron.homeip.net/projects/](http://omicron.homeip.net/projects/) | Contact: [email]morlenxus@gmx.net[/email] #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/chris/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave
  - installable apps:     entrance e eclair evfs e_utils
  - installable misc:     engage
  - installable proto:    etk exhibit entropy ephoto empower
  - installable modules:  calendar cpu devian flame mbar mem mount net rain screenshot slideshow snow tclock uptime weather wlan
  - skipping:             emotion eclair

  - script action:        install


BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ecore.log:
-----------------------------------------------------------------------------
make[4]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_file'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_file'
Making all in ecore_dbus
make[4]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/chris/e17_cvs/e17/libs/ecore/src/bin'
/bin/sh ../../libtool --mode=link gcc  -I/usr/local/include -g -O2 -Wall  -L/opt/e17/lib -o ecore_test  ecore_test-ecore_test.o ../../src/lib/ecore/libecore.la ../../src/lib/ecore_x/libecore_x.la ../../src/lib/ecore_txt/libecore_txt.la ../../src/lib/ecore_job/libecore_job.la ../../src/lib/ecore_fb/libecore_fb.la ../../src/lib/ecore_evas/libecore_evas.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore_ipc/libecore_ipc.la -lm
gcc -I/usr/local/include -g -O2 -Wall -o .libs/ecore_test ecore_test-ecore_test.o  -L/opt/e17/lib ../../src/lib/ecore/.libs/libecore.so ../../src/lib/ecore_x/.libs/libecore_x.so ../../src/lib/ecore_txt/.libs/libecore_txt.so ../../src/lib/ecore_job/.libs/libecore_job.so ../../src/lib/ecore_fb/.libs/libecore_fb.so ../../src/lib/ecore_evas/.libs/libecore_evas.so ../../src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_ipc/.libs/libecore_ipc.so -lm
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_get'
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_set'
collect2: ld returned 1 exit status
make[3]: *** [ecore_test] Error 1
make[3]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/chris/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2
-----------------------------------------------------------------------------


any ideas?

---

### Post by robfindlay on 2006-06-01
[QUOTE=TimmyJ]This is just a quick how-to on downloading, compiling, and installing the desktop shell Enlightenment 17 from the CVS repository. E17 is still in development, so do not expect a fully stable, bug-free environment. That said: I use E17 on a daily basis and rarely run into any hiccups.

[B]READ: Before following this guide please remove any previously installed versions of E17 (aka from any repository) as they may cause errors in the process.
[/B]
A quick disclaimer: this is my first how-to, so feel free to offer any constructive criticism.

Lets Start!

1.) First we want to install all required packages for E17, and all the Enlightenment Foundation Libraries to install. This list may be a bit of overkill, but it will get the job done.

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev
```


2.) Now that all that is out of the way we need to get the script that will make downloading/compiling/installing E17 a breeze! (pun intended). All credit goes to Morlenxus for this great tool.

From your home directory, run the following command
```
wget http://omicron.homeip.net/projects/easy_e17/easy_e17.sh
```

3.) Now we need to made the script executable and then run it! We are ommiting the library emotion and the video player eclair because they require a newer version of a library (xinelib I believe) than the one available in the ubuntu repositories. **NOTES: You must run this script as sudo or it will not work properly. This script will install all the applications and libraries it installs into /opt/e17 so as not to interfere with other versions of enlightenment. You can change this location through scripts options. This script will install ALL the applications and libraries (with the aforementioned exceptions) available in the E17 CVS tree. You may or may not want all these apps. You can easily skip any library or app using the --skip flag with the script.**

```
chmod +x easy_e17.sh
sudo ./easy_e17.sh -i --skip=emotion,eclair
```

4.) If you try to log-in to enlightenment now you will run into all kinds of wierdness. This is caused by some permissions problems resulting from running the script with 'sudo'. You can fix these problems by running the following command.

**Note: you must replace **user_name** with YOUR actual user name.**
```
sudo chown -R user:**user_name** ~/.ecore
```

5.) Now we have enlightenment all installed and working. The next step it create a desktop entry so that you can log-in to enlightenment from GDM.

Create a desktop entry called e17.desktop
```
sudo gedit /usr/share/xsessions/e17.desktop
```

Copy/Paste the following into the newly created file
```
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
```

Thats all you really need to do. Now using enligthenment is as simple as logging out, selecting the E-17 session and logging back in. Any time you want to update enlightenment and related libs/apps, simply re-run the easy_e17 script. For more information on the Enlightenment Foundation Libraries, and the applications that use them, please see [http://www.get-e.org](http://www.get-e.org) and 
[http://www.enlightenment.org.au](http://www.enlightenment.org.au)
[B]
Suggestion: due to the fact that enlightenment was installed in /opt/e17 it is a good idea to add /opt/e17/bin to your PATH so that it is easier to run all those great applications you just installed.[/B]

To do this open your /etc/environment with your favorite text editor

```
sudo gedit /etc/environment
```

then add the following lines to the bottom

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```

**Extra**: E17 uses little widget type things on the users desktop called modules. To learn where and how to download modules refer to this post: [http://ubuntuforums.org/showpost.php?p=548898&postcount=58](http://ubuntuforums.org/showpost.php?p=548898&postcount=58)[/QUOTE]


Help the script works untill i get an error message that reads something like glib-config not found is in your path? 

I have all the libglibs plus the dev installed so i 'm at a loss. 


Rob

---

### Post by Rui Pais on 2006-06-02
hi,
what
```
slocate glib-config
``` says?

btw, glib-config belongs to libglib1.2-dev deb package. Check if you have that installed and if so try to reinstall. 
Good luck.

---

### Post by Anagonda on 2006-06-04
I'm trying to get E17 to work on my dapper. My system is upgraded from hoary.

First I got the automake problem, but solved it. Now the script is trying to install epsilon. I get some errors about xine. I tried search etc but didn't find any help.
I found some story that there are others with the same problem, but could not find anything how to solve it.

So any help?

Here is a copy of the error:
```

- epsilon .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/epsilon.log:
-----------------------------------------------------------------------------
        then mv -f ".deps/xine_thumbnailer_la-xine_thumbnailer.Tpo" ".deps/xine_thumbnailer_la-xine_thumbnailer.Plo"; else rm -f ".deps/xine_thumbnailer_la-xine_thumbnailer.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I. -I../.. -I../../src/include -I/opt/e17/include -I/usr/include -g -O2 -Wall -MT xine_thumbnailer_la-xine_thumbnailer.lo -MD -MP -MF .deps/xine_thumbnailer_la-xine_thumbnailer.Tpo -c xine_thumbnailer.c  -fPIC -DPIC -o .libs/xine_thumbnailer_la-xine_thumbnailer.o
xine_thumbnailer.c:1:21: error: Epsilon.h: No such file or directory
In file included from xine_thumbnailer.c:2:
../../src/include/epsilon_plugin.h:4:21: error: Epsilon.h: No such file or directory
In file included from xine_thumbnailer.c:2:
../../src/include/epsilon_plugin.h:12: error: syntax error before '*' token
xine_thumbnailer.c:35: error: syntax error before '*' token
xine_thumbnailer.c:224: error: syntax error before '*' token
xine_thumbnailer.c: In function 'epsilon_generate_thumb':
xine_thumbnailer.c:267: error: 'e' undeclared (first use in this function)
xine_thumbnailer.c:267: error: (Each undeclared identifier is reported only oncexine_thumbnailer.c:267: error: for each function it appears in.)
xine_thumbnailer.c:367: warning: pointer targets in initialization differ in signedness
xine_thumbnailer.c:368: warning: pointer targets in passing argument 2 of 'i_yuy2_to_yv12' differ in signedness
xine_thumbnailer.c:370: warning: pointer targets in assignment differ in signedness
xine_thumbnailer.c:341: warning: unused variable 'v'
xine_thumbnailer.c:227: warning: unused variable 'p'
make[3]: *** [xine_thumbnailer_la-xine_thumbnailer.lo] Error 1
make[3]: Leaving directory `/root/e17_cvs/e17/libs/epsilon/src/plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17_cvs/e17/libs/epsilon/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/root/e17_cvs/e17/libs/epsilon/src'
make: *** [all-recursive] Error 1

```

---

### Post by shaders on 2006-06-04
i've got the same problem that you Anagonda!!!
Many,many xine errors...
Maybe it's just a temporary error from the cvs repository???
Indeed i have this stuff before:
CVS CHECKOUT/UPDATE:
-----------------------------------------------------------------------------
Updating repo 'e17' (please wait, this won't output much) ...
? libs/epsilon/src/plugins/.libs
? libs/epsilon/src/plugins/xine_thumbnailer_la-xine_thumbnailer.loT
Updating repo 'misc' (please wait, this won't output much) ...
Updating repo 'e_modules' (please wait, this won't output much) ...
-----------------------------------------------------------------------------

thanks

---

### Post by Rui Pais on 2006-06-04
hi,
it seems there is an error on one header file of epsilon... try:
```
sudo cp e17_cvs/e17/libs/epsilon/src/lib/Epsilon.h e17_cvs/e17/libs/epsilon/src/include/
```
and restart easy_e17.sh.

(note that if modules later on fails, then you need an cvs update, a working version was made only very recently)

good luck

---

### Post by shaders on 2006-06-04
oh! Thank you Rui Pais because thats works great!!!! (until now) I hope that the rest of the compilation will be made whitout another error.
By the way sorry for my english (i'm french).
Bye.

---

### Post by Anagonda on 2006-06-05
Thanks! That helped me get longer. But now I'm stuck at "APPS-COMPILATION AND INSTALLATION:" And when it tries to compile evfs.

```

- evfs ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evfs.log:
-----------------------------------------------------------------------------
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_debug.lo -MD -MP -MF .deps/posix_la-evfs_debug.Tpo -c ../../../src/common/evfs_debug.c -o posix_la-evfs_debug.o >/dev/null 2>&1
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include  -I/opt/e17/include  -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_event_helper.lo -MD -MP -MF ".deps/posix_la-evfs_event_helper.Tpo" -c -o posix_la-evfs_event_helper.lo `test -f '../../../src/common/evfs_event_helper.c' || echo './'`../../../src/common/evfs_event_helper.c; \
        then mv -f ".deps/posix_la-evfs_event_helper.Tpo" ".deps/posix_la-evfs_event_helper.Plo"; else rm -f ".deps/posix_la-evfs_event_helper.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_event_helper.lo -MD -MP -MF .deps/posix_la-evfs_event_helper.Tpo -c ../../../src/common/evfs_event_helper.c  -fPIC -DPIC -o .libs/posix_la-evfs_event_helper.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_event_helper.lo -MD -MP -MF .deps/posix_la-evfs_event_helper.Tpo -c ../../../src/common/evfs_event_helper.c -o posix_la-evfs_event_helper.o >/dev/null 2>&1
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include  -I/opt/e17/include  -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_misc.lo -MD -MP -MF ".deps/posix_la-evfs_misc.Tpo" -c -o posix_la-evfs_misc.lo `test -f '../../../src/common/evfs_misc.c' || echo './'`../../../src/common/evfs_misc.c; \
        then mv -f ".deps/posix_la-evfs_misc.Tpo" ".deps/posix_la-evfs_misc.Plo"; else rm -f ".deps/posix_la-evfs_misc.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_misc.lo -MD -MP -MF .deps/posix_la-evfs_misc.Tpo -c ../../../src/common/evfs_misc.c  -fPIC -DPIC -o .libs/posix_la-evfs_misc.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -g -O2 -D_FILE_OFFSET_BITS=64 -MT posix_la-evfs_misc.lo -MD -MP -MF .deps/posix_la-evfs_misc.Tpo -c ../../../src/common/evfs_misc.c -o posix_la-evfs_misc.o >/dev/null 2>&1
/bin/sh ../../../libtool --tag=CC --mode=link gcc  -g -O2 -D_FILE_OFFSET_BITS=64  -rdynamic -shared -o posix.la -rpath /opt/e17/lib/evfs/plugins/file -module -avoid-version posix_la-evfs_fs_posix.lo posix_la-evfs_debug.lo posix_la-evfs_event_helper.lo posix_la-evfs_misc.lo -L/usr/lib -lecore -lecore_job -lecore_x -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_fb -lecore_config -lecore_file -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -lecore_dbus -L/usr/lib -leet -lz -ljpeg -lm -L../../../src/lib -levfs
gcc -shared  .libs/posix_la-evfs_fs_posix.o .libs/posix_la-evfs_debug.o .libs/posix_la-evfs_event_helper.o .libs/posix_la-evfs_misc.o  -L/usr/lib /usr/lib/libecore.so /usr/lib/libecore_job.so /usr/lib/libecore_x.so /usr/lib/libecore_evas.so /usr/lib/libecore_con.so /usr/lib/libecore_ipc.so /usr/lib/libecore_txt.so /usr/lib/libecore_fb.so /usr/lib/libecore_config.so /usr/lib/libecore_file.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -ldl -lssl -lcrypto /usr/lib/libecore_dbus.so /usr/lib/libeet.so -lz /usr/lib/libjpeg.so -lm -L/root/e17_cvs/e17/apps/evfs/src/lib /usr/lib/libevfs.so  -Wl,-soname -Wl,posix.so -o .libs/posix.so
ar cru .libs/posix.a  posix_la-evfs_fs_posix.o posix_la-evfs_debug.o posix_la-evfs_event_helper.o posix_la-evfs_misc.o
ranlib .libs/posix.a
creating posix.la
/bin/sed: can't read /usr/lib/libXcursor.la: No such file or directory
libtool: link: `/usr/lib/libXcursor.la' is not a valid libtool archive
make[4]: *** [posix.la] Error 1
make[4]: Leaving directory `/root/e17_cvs/e17/apps/evfs/src/plugins/file'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/root/e17_cvs/e17/apps/evfs/src/plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/root/e17_cvs/e17/apps/evfs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/e17_cvs/e17/apps/evfs'
make: *** [all] Error 2

```

Ive had like ten missing packages etc. Why? I have installed all the packages that where listed on the first post.
For the missing packages I have searched the internet and then installed the needed package. But again I can't solve this by myself.

---

### Post by ctgray on 2006-06-05
```
- eveil ...................... ok
- evolume .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evolume.log:
-----------------------------------------------------------------------------
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for eet-config... /opt/e17/bin/eet-config
checking for eet - version >= 0.9.10... yes
checking for evas-config... /opt/e17/bin/evas-config
checking for evas - version >= 0.9.9... yes
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for embryo-config... /opt/e17/bin/embryo-config
checking for embryo - version >= 0.5.0... yes
checking for edje-config... /opt/e17/bin/edje-config
checking for edje - version >= 0.5.0... yes
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking for enlightenment - version >= 0.16.999... yes
configure: Module will be installed under /opt/e17/lib/enlightenment/modules
./configure: line 22567: syntax error near unexpected token `1.0.8'
./configure: line 22567: `AM_PATH_ALSA(1.0.8)'

```

Been good to me so far till it spewed this out.

---

### Post by Rui Pais on 2006-06-05
hi anagonda,
evfs is, as far as i know, a dependencie of entropy only and has been broken for more then a month or two (at least i can't compile it since a long time ago) 
Since entropy is in proto, not usefull at this point, (yet another file manager...) and it's development is more or less stoped, you can skip both and live happy (with thunar, pcmanfc, nautilus , konqueror, gentoo, or many others :-k )

@ ctgray
Hi. A lot of modules are broken or very unstable at this moment. 
Some even compile but do nothing (eveil and devian). 
One option is - at moment - skip those who fail, another option, try an older version, at 25 of May most of modules was made shelf compatible (slideshow and weather became a little unstable, but functional) around 19-20 of May the shelf was commited, any date before that will give a very updated e17 and much more stable. 
June as been a wild e17 month (i started to became poetic :))

Sorry if i can help more with those errors. 
Hopeful, must of them should stabilize soon.

---

### Post by Lut!n on 2006-06-05
@ctgray : you have to install libasound2-dev and automake1.9, and compile evolume with automake1.9. It just works fine

---

### Post by Anagonda on 2006-06-05
Thanks Rui! Now I got it compiled.

But one more problem. When I try to start modules, lets say like engage I get an error: 
```

Module Api Error
Error initializing Module: Engage
It requires a minimum module API version of 3
The module API advertized by Enlightenment is 2

```
So has this something to do with the apps I couldn't compile?
I had to run easy script like this: 
./easy_e17.sh -i --skip=evfs,etk_server, entropy,language
Or else I got some problems that I couldn't solve by myself.

---

### Post by Rui Pais on 2006-06-05
Hi Anagonda,

well all things you skip - evfs,etk_server, entropy - belong to proto section of cvs tree, that mean they are embrionary apps, they are not important to e17 install (most of the time they wont work or even compile...)

engage is broken since yesterday... at least i couldn't find a way to compile it.
What is strange in your case is that you compile it, but it complains about e being a lower version... well??... btw that error happen with module version or stand alone engage?
Something must have been changed in the last few hours on engage code (dev trying to make it work with recent updates of e17 api) but is not quit alright yet. Try again tomorrow or in a few days to see if it is ok. 
in mean while, ibar is more or less the same, a tittle less complicated in fact (just miss the small thing that catch apps running underground... how is call it?)

---

### Post by Anagonda on 2006-06-05
Thanks Rui for a fast answer.

I'm running the engage module. The strange thing is that allmost every module complains that same.
ibar  and pager are the only modules that I can get running. Everything else gives me that same error.

I will try again in few days.

---

### Post by Rui Pais on 2006-06-05
Hi Anagonda.

So you got the same problem with other modules... thats strange.
I compiled a few hours ago and at least ibox and pager are perfectly normal.
I can't reproduce your error messages...
Since i've got normal compilation and behaviour from source of the same date that suggests that you've got something borked with your e17 installation and not with code (so wait a few days may not solve it) :(

The advantage of easy_e17 script is that isolates completly the e17 installation allow you to have any number of versions side by side.
The advantage of cvs code is that you can choose the version you install on any base time you want. Adding those 2 and you got plenty options ;)

Try to do another installation with a sane version of e17 (as i said before all june version seems too broken) . The 30 of May are the most updated and everything works (not evfs or entropy, but that you know you can skip). 

 it's just:
```
sudo mv /opt/e17 /opt/e17_2006-jun-05
sudo rm -rf /tmp/easy_e17
sudo mv e17_cvs e17_cvs_2006-jun-05
``` (or sudo rm -rf e17_cvs/*)

and reinstall setting dates of cvs to 2006-05-30.
Its simpler to change easy_e17.sh to do the date/time you want:
Replace line 153 by this:
> backoff_loop "cvs -z3 -q update -dP $todate"
line 157 by this:
> backoff_loop "cvs -z3 -q -d $cvs_srv co $todate $repo"
and add a new line 444:
> "--date")	todate="-D $value" ;;
 
Now, just pick better times:
> sudo ./easy_e17.sh -i --skip=evfs,etk_server, entropy,language --date=2006-05-30

At least here, that day code work like a baby :)
If you feel less adventurous maybe check the date 2006-04-18. The pre-shelf days, e17 was very stable then and everything working good including all themes on get-e site.

---

### Post by oskvaz on 2006-06-06
Problems at the compilation phase:


LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... SKIPPED
- ewl ........................ ok
- engrave .................... ok
- exml ....................... ok
-----------------------------------------------------------------------------

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... ok
- e .......................... ok
- eclair ..................... SKIPPED
- evfs ....................... ok
- e_utils .................... ok
- engage ..................... ok
- scrot ...................... ok
- etk ........................ ok
- etk_server ................. ok
- exhibit .................... ok
- entropy .................... ok
- ephoto ..................... ok
- empower .................... ok
- calendar ................... ok
- cpu ........................ ok
- devian ..................... ok
- eveil ...................... ok
- evolume .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evolume.log:
-----------------------------------------------------------------------------
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for eet-config... /opt/e17/bin/eet-config
checking for eet - version >= 0.9.10... yes
checking for evas-config... /opt/e17/bin/evas-config
checking for evas - version >= 0.9.9... yes
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for embryo-config... /opt/e17/bin/embryo-config
checking for embryo - version >= 0.5.0... yes
checking for edje-config... /opt/e17/bin/edje-config
checking for edje - version >= 0.5.0... yes
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking for enlightenment - version >= 0.16.999... yes
configure: Module will be installed under /opt/e17/lib/enlightenment/modules
./configure: line 22567: syntax error near unexpected token `1.0.8'
./configure: line 22567: `AM_PATH_ALSA(1.0.8)'
-----------------------------------------------------------------------------


I need some help with this.

Thanks

---

### Post by Lut!n on 2006-06-06
install libasound2-dev ;)

---

### Post by CHUCKYCHUCK on 2006-06-06
hi, does this script work fine with the dapper release ??
thanks

---

### Post by Rui Pais on 2006-06-06
101% ;)

morlenxus script it's independent of distro or distro version. It uses direct access to cvs code and direct compilation. No deb packages or like are made. 

All you really need is some packages installed. Check the 1st post of the thread and those above from Lut!n.

good luck.

---

### Post by oskvaz on 2006-06-06
Thanks a lot, Lut!n, but now:

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... previous installed
- e .......................... previous installed
- eclair ..................... SKIPPED
- evfs ....................... previous installed
- e_utils .................... previous installed
- engage ..................... previous installed
- scrot ...................... previous installed
- etk ........................ previous installed
- etk_server ................. previous installed
- exhibit .................... previous installed
- entropy .................... previous installed
- ephoto ..................... previous installed
- empower .................... previous installed
- calendar ................... previous installed
- cpu ........................ previous installed
- devian ..................... previous installed
- eveil ...................... previous installed
- evolume .................... previous installed
- flame ...................... previous installed
- language ................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/language.log:
-----------------------------------------------------------------------------
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for edje-config... /opt/e17/bin/edje-config
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking EXML.h usability... yes
checking EXML.h presence... yes
checking for EXML.h... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking X11/extensions/XKBrules.h usability... no
checking X11/extensions/XKBrules.h presence... no
checking for X11/extensions/XKBrules.h... no
configure: error: Cannot find XKBrules.h. Make sure your CFLAGS environment variable contains include lines for the location of this file.
-----------------------------------------------------------------------------

What can I do?. I found the XKBrules.h file but not where to place it. You can help me?

---

### Post by brambles on 2006-06-07
libxkbfile-dev should sort that out:-)

Cheers

Mark

---

### Post by brambles on 2006-06-07
Built a bunch of dapper debs of e17 from CVS this afternoon. This is just a basic list of what cropped up.

Hope it's of some use to somebody:-) It's certainly not a Howto!

Used autoe.sh from [http://gefechtsdienst.de/uman/files/scripts/autoe.sh](http://gefechtsdienst.de/uman/files/scripts/autoe.sh) Many thanks Falko for this script.

apt-get install build-essential libxine-dev libextractor-dev byacc flex bison libncurses5-dev libgstreamer0.10-dev libgstreamer-plugins-base0.10-dev libid3tag0-dev automake1.9 libsqlite3-dev libid3-dev giblib-dev cvs autogen libtiff-dev  autoconf libungif4-dev libxkbfile-dev libasound-dev libxcomposite-dev

Probably missed something here but sure other posts will provide what's missing.

This should bring in a bunch of dependencies too

Edit script for where you want to install sources from cvs

control file for emotion needs to have libxine1 replaced with libxine-main1
control file for evfs needs to have automake1.7 replaced with automake1.9

debian/rules files need to be made executable

build order was
	libs :imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave exml
	apps :entrance e eclair evfs e_utils examine
	misc :engage scrot
	proto :etk etk_server exhibit entropy ephoto
	e_modules

Had to build them individually since haven't got the key-signing sussed yet, but all built peachy:-) and it's mighty pretty!

Cheers

Mark

---

### Post by oskvaz on 2006-06-07
Look at this!!!:


INSTALL NOTES:
-----------------------------------------------------------------------------
The mostly incredible and really unbelivable has become true:
You compiled e17 sucessfully!

To start e just insert 'exec /opt/e17/bin/enlightenment' in your .xinitrc,
.xsession or wherever you define that.

Note: e17 is still not released and it won't in the near future. So don't
ask for a stable release. e17 is still very buggy and only for experienced userswho know what they do...

Rasterman don't wrote this script so don't ask him for help with it.

We hope you will enjoy your trip into e17... Have fun!
-----------------------------------------------------------------------------


Thank you guys!!!

---

### Post by Rui Pais on 2006-06-07
hi oskvaz, congratulations. 
Hope you **e**njoy your e17.

Allow me to use your post just to add a smal tip to new comers to e17 using this method.

That seems to be a general tendency to people think that they only have e installed after script finish successfully with that nice message. 
[COLOR="Blue"]This is not true.[/COLOR]
As long as it finishs e or, to be more usable, e_utils one hafe a full functional enlightenment installed.

All the others are modules or extra apps, Modules are complementary stuff that you can add (one should only add as needed since they tend to be broken, broke **e** and/or eat cpu/mem for lunch and breakfast).

So the best option for a first install is just --skip==<all_things_here_that_are_not_libs_neither_e> start a e session to see if everithing is ok and then after launch e compile extas as need (or all for curiosity sake or testing)

no need to not use e just cause a module fails to compile.

hth

---

### Post by Rui Pais on 2006-06-07
A little out of topic...
Most themes on get-e site are broken since the shelf was on cvs. Right now there are only 3 (and default) that work and they are all very little generalistic. 
So i made mine:
[here they are]("http://homepage.oniduo.pt/rui.pais/projectos/") (with screenshots) if someone is interested in try them.
Simpl-Icy are finished and fully work with the shelf I'm working on 2 others, Serenity and eMacos. 
Hope you like it.

[ATTACH]10813[/ATTACH] [ATTACH]10817[/ATTACH] [ATTACH]10818[/ATTACH]

---

### Post by M@dMerC on 2006-06-09
Hi guys,
I'm having a slight problem with installing E17 i have tried the two different scripts in this thread and get the same error each time and was wondering what i can do to fix it : => Update done!
---------------------------------------------------------------------

I'm going to build the following updated modules: e17/libs/eet e17/libs/edb e17/libs/evas e17/libs/ecore e17/libs/embryo e17/libs/imlib2 e17/libs/edje e17/libs/epeg e17/libs/epsilon e17/libs/esmart e17/apps/e e17/libs/engrave e17/libs/ewl e17/apps/e_utils e17/apps/examine e17/libs/exml e_modules e17/apps/entrance e17/apps/elicit e17/apps/entice e17/libs/emotion e17/apps/eclair e17/proto/enterminus e17/apps/evfs e17/proto/etk  e17/proto/entropy e17/proto/exhibit e17/proto/enhance e17/proto/extrackt e17/proto/ephoto e17/proto/enity e17/proto/etk_server e17/proto/empower misc/enotes
..press a key to stat building=> Building...

~/Desktop/e17/libs/eet ~/Desktop
---------------------------------------------------------------------

=== Building: e17/libs/eet... ===


 => Autofoo: e17/libs/eet

Running aclocal...
./autogen.sh: line 8: aclocal: command not found
eric@Alyssa:~/Desktop$

any help would be greatly appreciated.

---

### Post by Rui Pais on 2006-06-09
hi,
you don't seems to have automake installed. 

Have you done
```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev
```
first?


Another point. You will have, probabilly, problem compiling some of those packages you list in your post. enterminus and evfs usually don't compile. 
And what about entrance, are you planning replace gdm or kdm?

---

### Post by M@dMerC on 2006-06-09
hi,
firstly thanx for replying so fast.
when i run the command u posted i get this error 
: 
The following packages have unmet dependencies:
  libimlib2-dev: Depends: libimlib2 (= 1.2.2.001-0cvs20060528) but 1.2.0-2.2ubuntu2 is to be installed
E: Broken packages

as for the other stuff i just ran the script so umm yeah lol is there a way to stop it from tryin to compile those packages and also yeah if i can get enlightenment running properly i would like to either just not use gnome or get rid of it entirely 
once again thanx for replying so quick:P

---

### Post by Rui Pais on 2006-06-09
hi, no problem, i just had come home and check my mail while the soup is get radioactive enough on microwave ;)...

you have an odd libimlib2... maybe trying to remove it, purge it and then reinstall it (and anything else it removes...) btw, are you running some version of the non-final dapper? or some "strange" repertoir on sources.list?

About get rid of gnome... well, i find e17 stable enough, at least it's core, but a lot of it's apps is far from usable. gnome-terminal, xfce4 terminal (my favorite) or eterm from e16 right now are far better choices then enterminus that is just beginning its existence... and even e, this is alpha stuff from cvs. It changes a lot and not always to good or stable things, to say it softly. 
If you want to geto a e17 only system, try to get a more stable version of e. (Repeting myself, sorry) all version of June seems very unstable and some stuff i can simply compile. Try to check my post [#281]("http://ubuntuforums.org/showpost.php?p=1099284&postcount=281") above to get a much more stable e then just plain last minute cvs :)

I don't know the script you are using. Usually they are bash scrips or python, just check for the line of compiling packages and remove those who are not fundamental. You can always compile them later, after you are running e17, to check what they or how they work. 

good luck.


*EDIT:* if you go for morlenxus script (from the 1st post) just add:
> --skip=--skip=emotion,eclair,entrance,scrot,evfs,entropy,ephoto,empower,eveil,evolume,flame,language,mbar,moon,mount,rain,snow,uptime,wlan,slideshow
you can install any of those after e is finish and running :)
A basic and full functional e17 install is: 
imlib2 edb eet evas ecore epeg embryo edje epsilon esmart ewl engrave e_utils.

---

### Post by M@dMerC on 2006-06-09
ok my dapper is as far as i know the newest version i upgraded to it last nite so yeah i assume its the stable version and the only repo i have that isnt one the upgrade has put there is  [http://gefechtsdienst.de/uman/files/](http://gefechtsdienst.de/uman/files/) unstable i cant remember what i added that one for but it was for something i needed lol you say to remove and purge libimlib2 i can remove it using synaptic but as far as purge it i dont have a clue. I have tried 2 scripts the one from the first post and also the get_e.sh script if that helps but i will try to get the stable version of E that you have suggested and let u know how i went. thanx heaps for ur time i really do appreciate it and im lookin forward to having a fuly functional e working soon lol i have what seems to be a partly functional copy going but i cant seem to be able to really do anything i have tried adding things to the ibar with no success and when i open the config panel there is nothing there so i want to do it all properly. Once again thanks heaps for your time.

---

### Post by Rui Pais on 2006-06-09
[QUOTE=M@dMerC]ok my dapper is as far as i know the newest version i upgraded to it last nite so yeah i assume its the stable version and the only repo i have that isnt one the upgrade has put there is  [http://gefechtsdienst.de/uman/files/](http://gefechtsdienst.de/uman/files/) unstable i cant remember what i added that one for but it was for something i needed lol you say to remove and purge libimlib2 i can remove it using synaptic but as far as purge it i dont have a clue.[/QUOTE]
Ok, thats a repository for sid debian packages for some stuff including e17 stuff.
 You should avoid at most mixing debian repertories with ubuntu. Ubuntu changes the places of many things and sooner or later problems appears with libs dups and things like that... And yes you faulty imlib2 came from that repository. You should clean those things.

Remove the entry for gefechtsdienst. With synaptic you could see which packages are there "local installed" that mach the repository (browse to there to check the packages they offer) 

Purge is uninstall + remove config files. It's the same as 'Mark for complete remove' at synaptics or sudo apt-get remove purge <package>

>  I have tried 2 scripts the one from the first post and also the get_e.sh script if that helps but i will try to get the stable version of E that you have suggested and let u know how i went. thanx heaps for ur time i really do appreciate it and im lookin forward to having a fuly functional e working soon lol i have what seems to be a partly functional copy going but i cant seem to be able to really do anything i have tried adding things to the ibar with no success and when i open the config panel there is nothing there so i want to do it all properly. 

I never tried get_e.sh. And i didn't realize that you have already installed e.
If your e dont crash and it's installed not mixed with system directories (installed on /opt/ or /usr/local/ are good choices) then it should be ok.
But you may prefer -better- clean imlib2, delete or backup old  e and redo a fresh one. 

In order to get your ibox or engage populate you need some icons (.eap files). 
check [those here]("http://www.clan-hash.com/gulivert/?cat=15")
You can do it by hand, editing .e/e/applications/bar/default/.order file and add your applications eap files, or using an app from e_utils called entangle (a very intuitive gui)

hth.

edit: one advantage of easy-e17.sh is that everything is installed on /opt/e17, it wont trouble with your system libraries (like its happenig now with your libimlib2); you can simple "uninstall" by rm -rf /opt/e17 and you can have any versions of e17 side by side on /op/ and link to the one you want as /opt/e17 :)

---

### Post by M@dMerC on 2006-06-09
Ok i have done everything u said and everything seemed to be going nicely when this happened 

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ecore.log:
-----------------------------------------------------------------------------
ranlib .libs/libecore_dbus.a
creating libecore_dbus.la
(cd .libs && rm -f libecore_dbus.la && ln -s ../libecore_dbus.la libecore_dbus.la)
make[4]: Leaving directory `/home/eric/e17_cvs/e17/libs/ecore/src/lib/ecore_dbus'
make[4]: Entering directory `/home/eric/e17_cvs/e17/libs/ecore/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/eric/e17_cvs/e17/libs/ecore/src/lib'
make[3]: Leaving directory `/home/eric/e17_cvs/e17/libs/ecore/src/lib'
Making all in bin
make[3]: Entering directory `/home/eric/e17_cvs/e17/libs/ecore/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include  -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I../../src/lib/ecore -I../../src/lib/ecore_evas -I../../src/lib/ecore_directfb -I../../src/lib/ecore_x -I../../src/lib/ecore_fb -I../../src/lib/ecore_job -I../../src/lib/ecore_con -I../../src/lib/ecore_ipc -I../../src/lib/ecore_txt -I../../src/lib/ecore_config -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include -I/opt/e17/include -g -O2 -Wall -MT ecore_test-ecore_test.o -MD -MP -MF ".deps/ecore_test-ecore_test.Tpo" -c -o ecore_test-ecore_test.o `test -f 'ecore_test.c' || echo './'`ecore_test.c; \
        then mv -f ".deps/ecore_test-ecore_test.Tpo" ".deps/ecore_test-ecore_test.Po"; else rm -f ".deps/ecore_test-ecore_test.Tpo"; exit 1; fi
/bin/sh ../../libtool --tag=CC --mode=link gcc  -I/opt/e17/include -g -O2 -Wall  -L/opt/e17/lib -o ecore_test  ecore_test-ecore_test.o ../../src/lib/ecore/libecore.la ../../src/lib/ecore_x/libecore_x.la ../../src/lib/ecore_txt/libecore_txt.la ../../src/lib/ecore_job/libecore_job.la ../../src/lib/ecore_fb/libecore_fb.la ../../src/lib/ecore_evas/libecore_evas.la ../../src/lib/ecore_con/libecore_con.la ../../src/lib/ecore_ipc/libecore_ipc.la -lm
mkdir .libs
gcc -I/opt/e17/include -g -O2 -Wall -o .libs/ecore_test ecore_test-ecore_test.o  -L/opt/e17/lib ../../src/lib/ecore/.libs/libecore.so ../../src/lib/ecore_x/.libs/libecore_x.so ../../src/lib/ecore_txt/.libs/libecore_txt.so ../../src/lib/ecore_job/.libs/libecore_job.so ../../src/lib/ecore_fb/.libs/libecore_fb.so ../../src/lib/ecore_evas/.libs/libecore_evas.so ../../src/lib/ecore_con/.libs/libecore_con.so ../../src/lib/ecore_ipc/.libs/libecore_ipc.so -lm
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_get'
../../src/lib/ecore_evas/.libs/libecore_evas.so: undefined reference to `evas_data_attach_set'
collect2: ld returned 1 exit status
make[3]: *** [ecore_test] Error 1
make[3]: Leaving directory `/home/eric/e17_cvs/e17/libs/ecore/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/eric/e17_cvs/e17/libs/ecore/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/eric/e17_cvs/e17/libs/ecore'
make: *** [all] Error 2
-----------------------------------------------------------------------------

can someone please decipher this for me and tell me how to fix it 
i really do appreciate the time and effort you guys go to to help us n00bs out and this time is no exception. Anyways im off to bed cause its 3am and i got some work to do 2morrow so thanx in advance to whoever can help me with this.

---

### Post by Rui Pais on 2006-06-09
3am and not in bed... e is making you suffer. 

I check those repos you mention. 
They install e17 in the the plain /usr/ so one ends up with pre-alpha packages mixed with the system :cry: (Gentoo ebuilds do the same...)

So you probabily have problems compiling cause you have old libs around in your path and ecore is trying to compile against them not the recent ones that easy_e17 build for you.

Remove any reference to that repo and look in synaptic for any package located  under Ststus -> 'Installed (local or obsolete)'. Mark for complete remove any of those that relates to e17, imlib2, edb, evas...

After do:
```
sudo updatedb
slocate libe
```and check what is in your /usr/lib/ and/or /lib/. 
If there are any e17 related, like libecore*, libeet*, libevas*,libe.*,libevas*,libesmart*, libetk*, and so..., they are you problem. Remove or mv to another location (if you have doubts).

Restart easy_e17.sh adding -s flag to skip cvsupdate.

---

### Post by M@dMerC on 2006-06-10
Rui Pais
I followed the directions you have posted and good news :D it worked i did have to skip a few apps due to missing dependencies which where:
eclair
evfs
scrot
etk_server
entropy
evolume
language
 not sure if any of these really matter but i'm just about to try my new E out thankyou soo much for your help and putting up with my n00bishness (is that a word :P) anyway you really are a legend so thanx heaps.

---

### Post by Rui Pais on 2006-06-10
Hi,
glad to know it works :)

Don't worry about evfs and entropy it very incomplete and buggy. Theres a lot file managers from light to heavy. Use your normal nautilus or konqueror, or try thunar, rox or pcmanfc. There are others even lighter.

About language you won't need except you want to change the... language. (i think, never tried)

evolume gives a module to control sound volume. If you need check last page for lut!n posts on the missing sound library. 

No need to thank, i'm happy to help :)

hope you like your e17.

---

### Post by M@dMerC on 2006-06-10
i absolutely love it thanx :P E17 rocks but im now looking for a module that displays a digital clock instead of the analog one that is there by default and also where can i get some nice themes and stuff??

---

### Post by M@dMerC on 2006-06-10
oh sorry one more thing how do i get entangled or entangle ?? thats the one that creates/edits epa files isnt it. Sorry bout making another post for this but i couldnt work out how to edit my last post lol

---

### Post by Rui Pais on 2006-06-10
hi,
entanle is the utility to manage ibox, engage, startup and Favorites (the e name for apps menu).
Is part of e_utils. Just type entangle on command line. 

To create/add/edit icons you have 2 ways: 
e_util_eapp_edit again from e_utils here an example:
```
e_util_eapp_edit .e/e/applications/all/entangle.eap
```
now add an icon of your choice and type entangle on executable entry and save.
edit with a text editor .e/e/applications/favorite/.order and add  a line with entangle.eap, save and close. 
Like magic, entangle is now in your menu applications :)

2nd way launch the app you want to change icon, in the window bar clic on little icon. On the menu there is an option named Edit Icon (guess what it does? ;))

About a digital clock, is a module called tclock. If you haven't do
easy_e17.sh -s --only=tclock

Nice themes and stuff: 
Well, icons section was removed from get-e some time ago due to some license issues...
the only set i know is that link to the site of [Gulivert]("http://www.clan-hash.com/gulivert") i give last page.

You can use an app name e17genmenu to create a series of icons like gnomes default and automaticly have the gnome menu replicated. 

Themes are few too, cause since the shelf is upon us most of the old themes don't work. 
As far as i know, you got 3 listed on themes section as working. Milky is a little incomplete and McLaren is a bit wierd and colour bizarre. Boneyfrog's blues is the one really professional that is always uptodate and work, but is a strong colour theme with a computer retro look that not appeal to every taste , besides boneyfrog eyes must be wonderfull cause he made menus with a very tinny font that is terrible hard to read unless you have an huge monitor or eyes of an eagle. Another one, Japan is listed as non-work but, at least here, works normally. And you got [mine]("http://homepage.oniduo.pt/rui.pais/projectos"), Simply-Icy fully working and some others i was working on, that are more or less functional. check my post with screenshots on last page (or here). They are quiet generalistic.

Finally to edit your posts use the red scissors icon on the post in question. 

have fun M@dMerC

---

### Post by M@dMerC on 2006-06-10
thanx once again for that lol and i think i will give your theme a go its the only one i really like besides the default one (its soo shiny :P )

---

### Post by M@dMerC on 2006-06-11
ummm can anyone tell me how to make it so entrance works ?? please :D
Edit: its ok i worked it out lol was pretty easy really. ;)

---

### Post by haani on 2006-06-16
guys i have a problem here everything was going fine till this error:

```
APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... previous installed
- e .......................... previous installed
- eclair ..................... SKIPPED
- evfs ....................... previous installed
- e_utils .................... previous installed
- engage ..................... previous installed
- scrot ...................... ok
- etk ........................ ok
- etk_server ................. ok
- exhibit .................... ok
- entropy .................... ok
- ephoto ..................... ok
- empower .................... ok
- calendar ................... ok
- cpu ........................ ok
- devian ..................... ok
- eveil ...................... ok
- evolume .................... ok
- flame ...................... ok
- language ................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/language.log:
-----------------------------------------------------------------------------
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for edje-config... /opt/e17/bin/edje-config
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking EXML.h usability... yes
checking EXML.h presence... yes
checking for EXML.h... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking X11/extensions/XKBrules.h usability... no
checking X11/extensions/XKBrules.h presence... no
checking for X11/extensions/XKBrules.h... no
configure: error: Cannot find XKBrules.h. Make sure your CFLAGS environment variable contains include lines for the location of this file.
```

any help would be appricated!!

**EDIT:** Nevermind i fixed it my self had to install xlibfile1

---

### Post by Rui Pais on 2006-06-16
Hi,
posts #286 and #287 on previous page of this thread may give you an hint ;)


@M@dMerC
Glad you managed entrance :)
Do you try it my themes? some comments? 

I have worked (just a little) and updated those i'm working at moment ([Serenity]("http://homepage.oniduo.pt/rui.pais/projectos")).

---

### Post by dlai on 2006-06-16
hello everybody i made e17 compile... pretty easy really... but what i'm wondering now is that i want entrance to run properly.. it is booting fine into entrance but when i use entrance to boot into enlightenment the applications are gone from the menu and the I can't configure anything, it is not the same problem if i do a normal startx... Anyone got any clue how to make it work?

---

### Post by haani on 2006-06-16
how can i completely uninstall e17??

---

### Post by Rui Pais on 2006-06-16
[QUOTE=haani]how can i completely uninstall e17??[/QUOTE]
if you install by using easy_e17.sh just do:
```
sudo rm -rf /opt/e17
```

If not, check the method you use (some scripts use /usr/local/ instead of /opt/, as an example)

---

### Post by Torim on 2006-06-16
Hi, I got a problem building evas:

```

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
creating libevas_imaging.la
(cd .libs && rm -f libevas_imaging.la && ln -s ../libevas_imaging.la libevas_imaging.la)
make[4]: Verlasse Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src/lib/imaging«
Making all in include
make[4]: Gehe in Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src/lib/include«
make[4]: Für das Ziel »all« ist nichts zu tun.
make[4]: Verlasse Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src/lib/include«
make[4]: Gehe in Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src/lib«
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/lib -I../../src/lib/include -I/usr/include/freetype2 -I/opt/e17/include   -I/opt/e17/include  -g -O2 -MT main.lo -MD -MP -MF ".deps/main.Tpo" -c -o main.lo main.c; \
then mv -f ".deps/main.Tpo" ".deps/main.Plo"; else rm -f ".deps/main.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/lib -I../../src/lib/include -I/usr/include/freetype2 -I/opt/e17/include -I/opt/e17/include -g -O2 -MT main.lo -MD -MP -MF .deps/main.Tpo -c main.c  -fPIC -DPIC -o .libs/main.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I. -I../../src/lib -I../../src/lib/include -I/usr/include/freetype2 -I/opt/e17/include -I/opt/e17/include -g -O2 -MT main.lo -MD -MP -MF .deps/main.Tpo -c main.c -o main.o >/dev/null 2>&1
/bin/sh ../../libtool --tag=CC --mode=link gcc  -g -O2  -L/opt/e17/lib -o libevas.la -rpath /opt/e17/lib -version-info 1:0:0 main.lo canvas/libevas_canvas.la data/libevas_data.la file/libevas_file.la imaging/libevas_imaging.la engines/common/libevas_engine_common.la -lm -ldl -lfreetype -lz -L/opt/e17/lib -leet -lz -ljpeg -lfontconfig
gcc -shared  .libs/main.o -Wl,--whole-archive canvas/.libs/libevas_canvas.a data/.libs/libevas_data.a file/.libs/libevas_file.a imaging/.libs/libevas_imaging.a engines/common/.libs/libevas_engine_common.a -Wl,--no-whole-archive  -Wl,--rpath -Wl,/opt/e17/lib -Wl,--rpath -Wl,/opt/e17/lib -L/opt/e17/lib -lm -ldl /usr/lib/libfreetype.so /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so -lfontconfig  -Wl,-soname -Wl,libevas.so.1 -o .libs/libevas.so.1.0.0
**gcc: /opt/e17/lib/libeet.so: No such file or directory**
make[4]: *** [libevas.la] Fehler 1
make[4]: Verlasse Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src/lib«
make[3]: *** [all-recursive] Fehler 1
make[3]: Verlasse Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src/lib«
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis »/home/moe/e17_cvs/e17/libs/evas/src«
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis »/home/moe/e17_cvs/e17/libs/evas«
make: *** [all] Fehler 2
-----------------------------------------------------------------------------

```
(Sorry for the output being in German, don't know how to change it)

Using Kubuntu 5.10. 
All the packages according to the wiki page are installed. 
Automake is version 1.9.5 (same error with 1.7).
CVS (from today) and the script are saved under $HOME and the script is run from the root console.

Any suggestions?

---

### Post by Rui Pais on 2006-06-16
hi,
the line
> gcc: /opt/e17/lib/libeet.so: No such file or directory
suggest that you have installed e17 before (or tried at least) with some other method and you got some lost old librarys on your PATH.

try
```
slocate libeet.so
```
and see how many libeet exist and where they are.
(Specially there **should not** exist a /lib/libeet.so)

---

### Post by dlai on 2006-06-16
[QUOTE=dlai]hello everybody i made e17 compile... pretty easy really... but what i'm wondering now is that i want entrance to run properly.. it is booting fine into entrance but when i use entrance to boot into enlightenment the applications are gone from the menu and the I can't configure anything, it is not the same problem if i do a normal startx... Anyone got any clue how to make it work?[/QUOTE]

Come on! Somebody must have had this problem!! or is it just the easy_e17.sh script? I have the problem everytime i have installed e17 from cvs...

---

### Post by Torim on 2006-06-16
[QUOTE=Rui Pais]hi,
the line

suggest that you have installed e17 before (or tried at least) with some other method and you got some lost old librarys on your PATH.

try
```
slocate libeet.so
```
and see how many libeet exist and where they are.
(Specially there **should not** exist a /lib/libeet.so)[/QUOTE]

I tried the script a couple of times yesterday. Is running the script with the "-c" argument and removing the /opt/e17/ folder enough to get rid of any old burdens?

slocate returns:
```

root@ubuntu:~# slocate libeet.so
/opt/e17/lib/libeet.so.0.9.10

```

and just in case:
```

root@ubuntu:~# find / -name libeet*
/home/moe/e17_cvs/e17/libs/eet/debian/libeet0-dev.install
/home/moe/e17_cvs/e17/libs/eet/debian/libeet0.install
/home/moe/e17_cvs/e17/libs/eet/src/lib/.libs/libeet.so.0.9.10
/home/moe/e17_cvs/e17/libs/eet/src/lib/.libs/libeet.so.0
/home/moe/e17_cvs/e17/libs/eet/src/lib/.libs/libeet.so
/home/moe/e17_cvs/e17/libs/eet/src/lib/.libs/libeet.a
/home/moe/e17_cvs/e17/libs/eet/src/lib/.libs/libeet.lai
/home/moe/e17_cvs/e17/libs/eet/src/lib/.libs/libeet.la
/home/moe/e17_cvs/e17/libs/eet/src/lib/libeet.la
/opt/e17/lib/libeet.so.0.9.10
/opt/e17/lib/libeet.la
/opt/e17/lib/libeet.a


```

---

### Post by Rui Pais on 2006-06-16
well Torim in that case is not a lost library.
Aparently something seems to be wrong with libeet.

I will try to update now and see if mine compiles well and will post the results.

@dlai
entrance is very outdated, and dev page has as last news the date of 2005 of May... It miss some features too (that at least to me are essencial), seems a little lost of time try to make it work when gdm or kdm are working so well (Dapper gdm is amazing fast) 
Anyway seems that M@dMerC had recently make it work so why not wait and see if he shares is solution with you?

---

### Post by Rui Pais on 2006-06-16
Well, here either eet as evas compiled normally...

Have you tried to repeat the process after complete remove the /opt/e17 and ~/e17_cvs and /tmp/easy_e17?


(my bed time)

---

### Post by dlai on 2006-06-16
[QUOTE=Rui Pais]
@dlai
entrance is very outdated, and dev page has as last news the date of 2005 of May... It miss some features too (that at least to me are essencial), seems a little lost of time try to make it work when gdm or kdm are working so well (Dapper gdm is amazing fast) 
Anyway seems that M@dMerC had recently make it work so why not wait and see if he shares is solution with you?[/QUOTE]

Thank you very much... strange though that they made it work in elive...

---

### Post by Torim on 2006-06-16
[QUOTE=Rui Pais]Well, here either eet as evas compiled normally...

Have you tried to repeat the process after complete remove the /opt/e17 and ~/e17_cvs and /tmp/easy_e17?


(my bed time)[/QUOTE]

Tried that, still the same problem. I will try and build it manually tomorrow and see if that has any effect. Thanks for your help

Good night ;)

---

### Post by Sukie on 2006-06-22
Hi,

I've been trying to install e17 for almost a week  now, using various methods in the forums, and I still can't get it to work :(  I ended up wiping my hard drive & re-installing Breezy.  I ran the first script in this thread again a few times, and got dependency errors.  (I ran it as root as per the advice in the Ubuntu wiki.)  I managed to fix those, but now it's throwing up another error with ewl and I have no idea what it means. I'd be grateful if anyone can help, as I **really** want the pretty shinyness of e17!  

(I also found a link explaining how to do a manual install of each individual component in order, but the cvs source it specified no longer exists.  Does anyone know of a step-by-step guide to installing it all manually?)

Here's the error log:

CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /root/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave exml
  - installable apps:     entrance e eclair evfs e_utils
  - installable misc:     engage scrot
  - installable proto:    etk etk_server exhibit entropy ephoto empower
  - installable modules:  calendar cpu devian eveil evolume flame language mbar mem moon mount net rain screenshot slideshow snow tclock uptime weather wlan
  - skipping:             -

  - script action:        install


BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... ok
- ewl ........................ ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/ewl.log:
-----------------------------------------------------------------------------
config.status: creating src/engines/evas_software_x11/Makefile
config.status: creating src/engines/evas_gl_x11/Makefile
config.status: creating src/engines/evas_fb/Makefile
config.status: creating data/Makefile
config.status: creating data/images/Makefile
config.status: creating data/themes/Makefile
config.status: creating debian/changelog
config.status: creating ewl-config.h
config.status: executing depfiles commands
config.status: executing default commands
make: Warning: File `configure.in' has modification time 1.4e+04 s in the futurecd . && /bin/sh /root/e17_cvs/e17/libs/ewl/missing --run aclocal-1.9
/usr/share/aclocal/gtk.m4:7: warning: underquoted definition of AM_PATH_GTK
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
 cd . && /bin/sh /root/e17_cvs/e17/libs/ewl/missing --run automake-1.9 --gnu
cd . && /bin/sh /root/e17_cvs/e17/libs/ewl/missing --run autoconf
configure.in:16: error: possibly undefined macro: AC_C___ATTRIBUTE__
      If this token and others are legitimate, please use m4_pattern_allow.
      See the Autoconf documentation.
configure.in:21: error: possibly undefined macro: AC_DEFINE
configure.in:67: error: possibly undefined macro: AC_PATH_GENERIC
configure.in:70: error: possibly undefined macro: AC_MSG_ERROR
make: *** [configure] Error 1
-----------------------------------------------------------------------------


root@linux:/home/sukie# aclocal-1.9
aclocal-1.9: `configure.ac' or `configure.in' is required
root@linux:/home/sukie#
---------------------

Thanks very much.

---

### Post by PoisoN2003 on 2006-06-23
some help would be nice

```
LAST LOGLINES FROM /tmp/easy_e17/install_logs/scrot.log:
-----------------------------------------------------------------------------
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables...
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking for style of include used by make... GNU
checking dependency style of gcc... gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for an ANSI C-conforming const... yes
checking for a BSD-compatible install... /usr/bin/install -c
checking whether make sets $(MAKE)... (cached) yes
checking whether to enable maintainer-specific portions of Makefiles... no
checking for giblib-config... no
checking for giblib - version >= 1.2.3... no
*** The giblib-config script installed by giblib could not be found
*** If giblib was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the GIBLIB_CONFIG environment variable to the
*** full path to giblib-config.
configure: error: Cannot find giblib: Is giblib-config in the path?

```

---

### Post by thunderduck3141 on 2006-06-24
i hade the same exact problem
what u do is download giblib-dev
then make sure u have pkg-config
then run

pkg-config giblib-config

---

### Post by thunderduck3141 on 2006-06-24
- evolume .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evolume.log:
-----------------------------------------------------------------------------
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for eet-config... /opt/e17/bin/eet-config
checking for eet - version >= 0.9.10... yes
checking for evas-config... /opt/e17/bin/evas-config
checking for evas - version >= 0.9.9... yes
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for embryo-config... /opt/e17/bin/embryo-config
checking for embryo - version >= 0.5.0... yes
checking for edje-config... /opt/e17/bin/edje-config
checking for edje - version >= 0.5.0... yes
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking for enlightenment - version >= 0.16.999... yes
configure: Module will be installed under /opt/e17/lib/enlightenment/modules
./configure: line 22567: syntax error near unexpected token `1.0.8'
./configure: line 22567: `AM_PATH_ALSA(1.0.8)'
-----------------------------------------------------------------------------




any ideas?

---

### Post by JMO707 on 2006-06-24
Anyone with a clue for this?
[I]
BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################


LIB-COMPILATION AND INSTALLATION:
------------------------------------------------------------------------------ imlib2 ..................... ERROR!
-----------------------------------------------------------------------------
LAST LOGLINES FROM /tmp/easy_e17/install_logs/imlib2.log:
-----------------------------------------------------------------------------Running aclocal...
aclocal: configure.in: 32: macro `AM_ENABLE_SHARED' not found in library
aclocal: configure.in: 40: macro `AM_PROG_LIBTOOL' not found in library
-----------------------------------------------------------------------------[/I]

---

### Post by thunderduck3141 on 2006-06-24
no idea mate, make sure you have all the libs u need installed

any idea what happened to all my other apps (mplayer, xine, vlc, opne office, etc.)

---

### Post by PoisoN2003 on 2006-06-24
well now i get this
```
LAST LOGLINES FROM /tmp/easy_e17/install_logs/evfs.log:
-----------------------------------------------------------------------------
config.status: executing default commands
cd . && /bin/sh /home/poison/e17_cvs/e17/apps/evfs/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-recursive
make[1]: Entering directory `/home/poison/e17_cvs/e17/apps/evfs'
Making all in src
make[2]: Entering directory `/home/poison/e17_cvs/e17/apps/evfs/src'
Making all in lib
make[3]: Entering directory `/home/poison/e17_cvs/e17/apps/evfs/src/lib'
if /bin/sh ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/include/libxml2  -I. -I../.. -DBINDIR=\""/opt/e17/bin"\"  -I/opt/e17/include -DLIB  -g -O2 -D_FILE_OFFSET_BITS=64 -MT libevfs_la-libevfs.lo -MD -MP -MF ".deps/libevfs_la-libevfs.Tpo" -c -o libevfs_la-libevfs.lo `test -f 'libevfs.c' || echo './'`libevfs.c; \
        then mv -f ".deps/libevfs_la-libevfs.Tpo" ".deps/libevfs_la-libevfs.Plo"; else rm -f ".deps/libevfs_la-libevfs.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/include/libxml2 -I. -I../.. -DBINDIR=\"/opt/e17/bin\" -I/opt/e17/include -DLIB -g -O2 -D_FILE_OFFSET_BITS=64 -MT libevfs_la-libevfs.lo -MD -MP -MF .deps/libevfs_la-libevfs.Tpo -c libevfs.c  -fPIC -DPIC -o .libs/libevfs_la-libevfs.o
In file included from libevfs.c:1:
../../src/include/evfs.h:103:27: error: evfs_metadata.h: No such file or directory
make[3]: *** [libevfs_la-libevfs.lo] Error 1
make[3]: Leaving directory `/home/poison/e17_cvs/e17/apps/evfs/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/poison/e17_cvs/e17/apps/evfs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/poison/e17_cvs/e17/apps/evfs'
make: *** [all] Error 2

```
any idea what i can do

---

### Post by Erik Trybom on 2006-06-26
Thanks for an excellent guide! I ran into some dependency trouble, but all I had to do was install the missing dep with Synaptic and it worked (on Dapper).

Just a quick question... The "e17_cvs" folder that appeared in my home directory, is that something I need or can I delete it after the install?

---

### Post by Rui Pais on 2006-06-26
[QUOTE=Erik Trybom]Just a quick question... The "e17_cvs" folder that appeared in my home directory, is that something I need or can I delete it after the install?[/QUOTE]

You shouldn't delete it, or next time you update you have to download all again. A boring, time consuming task that will only put an extra stress on e cvs servers.

Altough i find very annoying have it visible on my home folder so i rename it to .e17_cvs and create a file ~/.easy_e17.conf with the line:
--cvspath=/home/<user_name_here>/.e17_cvs 
(must be a full path, ~/.e17_cvs don't work!)
Besides, i will not easilly deleted by mistake :)

---

### Post by Erik Trybom on 2006-06-26
OK, thanks. It's the disk space I'm after though, so I guess I'll burn it to a CD or something until I need it next time.

---

### Post by Raavea on 2006-07-01
```
- evolume .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evolume.log:
-----------------------------------------------------------------------------
checking for ld used by GCC... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for shared library run path origin... /bin/sh: ./config.rpath: No such file or directory
done
checking for CFPreferencesCopyAppValue... no
checking for CFLocaleCopyCurrent... no
checking whether NLS is requested... yes
checking for GNU gettext in libc... yes
checking whether to use NLS... yes
checking where the gettext function comes from... libc
checking for eet-config... /opt/e17/bin/eet-config
checking for eet - version >= 0.9.10... yes
checking for evas-config... /opt/e17/bin/evas-config
checking for evas - version >= 0.9.9... yes
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for embryo-config... /opt/e17/bin/embryo-config
checking for embryo - version >= 0.5.0... yes
checking for edje-config... /opt/e17/bin/edje-config
checking for edje - version >= 0.5.0... yes
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking for enlightenment - version >= 0.16.999... yes
configure: Module will be installed under /opt/e17/lib/enlightenment/modules
./configure: line 22567: syntax error near unexpected token `1.0.8'
./configure: line 22567: `AM_PATH_ALSA(1.0.8)'
-----------------------------------------------------------------------------
```I have this error, after a problem with giblib, which I corrected by using synaptic to install giblib-dev, and entering pkg-config giblib-config (which showed nothing..)

 Can anyone help?

---

### Post by Rui Pais on 2006-07-02
[QUOTE=thunderduck3141]- evolume .................... ERROR!

...

./configure: line 22567: syntax error near unexpected token `1.0.8'
./configure: line 22567: `AM_PATH_ALSA(1.0.8)'
[/QUOTE]


[QUOTE=Raavea]- evolume .................... ERROR!

...

./configure: line 22567: syntax error near unexpected token `1.0.8'
./configure: line 22567: `AM_PATH_ALSA(1.0.8)'
-----------------------------------------------------------------------------[/code]I have this error, after a problem with giblib, which I corrected by using synaptic to install giblib-dev, and entering pkg-config giblib-config (which showed nothing..)[/QUOTE]

Hi,
Have you check previous page, [this post]("http://ubuntuforums.org/showpost.php?p=1095977&postcount=277")?
.

---

### Post by Neo40 on 2006-07-03
I have problem to install "language" app:

>Skip<
checking for edje-config... /opt/e17/bin/edje-config
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking EXML.h usability... yes
checking EXML.h presence... yes
checking for EXML.h... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking X11/extensions/XKBrules.h usability... no
checking X11/extensions/XKBrules.h presence... no
checking for X11/extensions/XKBrules.h... no
configure: error: Cannot find XKBrules.h. Make sure your CFLAGS environment variable contains include lines for the location of this file.


I did a search with synaptic for word "XKBrules" but it found none package. Any idea?
Thanks.

EDIT: Nevermid! THe file missing was libxkbfile-dev. BTW, How can I delete my message? I know I can edit it but how to cancel it?

---

### Post by Rui Pais on 2006-07-03
[QUOTE=Neo40]I have problem to install "language" app:

>Skip<
checking for edje-config... /opt/e17/bin/edje-config
checking for enlightenment-config... /opt/e17/bin/enlightenment-config
checking EXML.h usability... yes
checking EXML.h presence... yes
checking for EXML.h... yes
checking X11/XKBlib.h usability... yes
checking X11/XKBlib.h presence... yes
checking for X11/XKBlib.h... yes
checking X11/extensions/XKBrules.h usability... no
checking X11/extensions/XKBrules.h presence... no
checking for X11/extensions/XKBrules.h... no
configure: error: Cannot find XKBrules.h. Make sure your CFLAGS environment variable contains include lines for the location of this file.


I did a search with synaptic for word "XKBrules" but it found none package. Any idea?
Thanks.[/QUOTE]


Hi, a quick search give me post [#307]("http://ubuntuforums.org/showpost.php?p=1143999&postcount=307")

edit:
to search for a file inside a package, use dpkg -S:
```
dpkg -S XKBrules.h
```
and i got, 
> libxkbfile-dev: /usr/include/X11/extensions/XKBrules.h


so i think that is the one that should be installed for that problem.

---

### Post by Raavea on 2006-07-07
Thanks very much for the help. Now I am having difficulties with CHOWN.

 ```
sudo chown -R user:**user_name** ~/.ecore
```
 I changed to
 ```
sudo chown -R user:raavea ~/.ecore
```
 and it said
 ```
chown: `user:raavea': invalid user
```
What do I do? :-? I feel like an idiot, so I'm probably missing something incredibly obvious... Gonna have a search, but felt posting this meant I could share my solution with anyone else with the same difficulty in reference directly with this.

 ..Did that make sense? It did to me. XD

---

### Post by Rui Pais on 2006-07-07
Hi,
just do 
```
sudo rm ~/.ecore
```

next time you start e17 a new .ecore will be made with correct permissions.

I think that point of how-to refers to some old problem.

---

### Post by Raavea on 2006-07-07
```
 Have you tried this? sudo chown -R polloz:polloz /home/polloz This assumes, of course, that your username is polloz.
```
 After lots of searching the different terms (and trying in vain to get it to search invalid user, not invalid, user) I found the above.

 Thanks for your quick reply, I shall try what you suggest.

---

### Post by UJM on 2006-07-08
thanks for this "How To for E17" finally got it up & running!

---

### Post by Traldan on 2006-07-14
Hi

I've got Dapper, and I've been trying to get E17 installed.  I messed around a little with the files on my own, but never got it to work right.  Ran instructions as according to the first post in this thread, and got this far:

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evas.log:
-----------------------------------------------------------------------------
Running aclocal...
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
automake: src/modules/engines/software_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/fb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/buffer/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/software_qtopia/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/directfb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/gl_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/cairo_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_x11/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
automake: src/modules/engines/xrender_xcb/Makefile.am: warning: automake does not support module_la_LDFLAGS being defined conditionally
-----------------------------------------------------------------------------


```

Any suggestions?  I read through as much of this thread as I could, and didn't see anything specific about this, so my apologies if this has already been addressed.

EDIT: Nevermind, got it fixed.  I installed an older version of automake (1.7) and it got through that step fine.  Now to hope it makes it the rest of the way without error.:???:

---

### Post by daedalusman on 2006-07-20
I'm getting this error on a fresh dapper install...

```
- bling ...................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/bling.log:
-----------------------------------------------------------------------------
cd . && /bin/sh /home/aegon/e17_cvs/e_modules/bling/missing --run autoheader
rm -f stamp-h1
touch config.h.in
cd . && /bin/sh ./config.status config.h
config.status: creating config.h
config.status: config.h is unchanged
make  all-am
make[1]: Entering directory `/home/aegon/e17_cvs/e_modules/bling'
if /bin/sh ./libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I. -I. -I. -I/opt/e17/include -I/opt/e17/include/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/X11R6/include  -I/opt/e17/include  -g -O2 -MT compmgr.lo -MD -MP -MF ".deps/compmgr.Tpo" -c -o compmgr.lo compmgr.c; \
        then mv -f ".deps/compmgr.Tpo" ".deps/compmgr.Plo"; else rm -f ".deps/compmgr.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I. -I. -I. -I/opt/e17/include -I/opt/e17/include/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/X11R6/include -I/opt/e17/include -g -O2 -MT compmgr.lo -MD -MP -MF .deps/compmgr.Tpo -c compmgr.c  -fPIC -DPIC -o .libs/compmgr.o
compmgr.c:39:39: error: X11/extensions/Xcomposite.h: No such file or directory
compmgr.c:40:36: error: X11/extensions/Xdamage.h: No such file or directory
compmgr.c: In function 'composite_init':
compmgr.c:2053: error: 'COMPOSITE_NAME' undeclared (first use in this function)
compmgr.c:2053: error: (Each undeclared identifier is reported only once
compmgr.c:2053: error: for each function it appears in.)
compmgr.c:2094: error: 'CompositeRedirectAutomatic' undeclared (first use in this function)
compmgr.c:2098: error: 'CompositeRedirectManual' undeclared (first use in this function)
compmgr.c: In function 'composite_shutdown':
compmgr.c:2153: error: 'CompositeRedirectManual' undeclared (first use in this function)
make[1]: *** [compmgr.lo] Error 1
make[1]: Leaving directory `/home/aegon/e17_cvs/e_modules/bling'
make: *** [all] Error 2
-----------------------------------------------------------------------------
```

Does anyone have any ideas here, Thanks.

---

### Post by danderson3 on 2006-07-20
I had to install the following packages to make this work:
libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libxkbfile-dev

---

### Post by danderson3 on 2006-07-20
building evolume on dapper produced these errors:
LAST LOGLINES FROM /tmp/easy_e17/install_logs/evolume.log:
-----------------------------------------------------------------------------
configure.ac: no proper invocation of AM_INIT_AUTOMAKE was found.
configure.ac: You should verify that configure.ac invokes AM_INIT_AUTOMAKE,
configure.ac: that aclocal.m4 is present in the top-level directory,
configure.ac: and that aclocal.m4 was recently regenerated (using aclocal).
configure.ac: installing `./install-sh'
configure.ac: installing `./mkinstalldirs'
configure.ac: installing `./missing'
src/lib/Makefile.am:7: Libtool library used but `LIBTOOL' is undefined
src/lib/Makefile.am:7:
src/lib/Makefile.am:7: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/lib/Makefile.am:7: to `configure.ac' and run `aclocal' and `autoconf' again.
src/lib/Makefile.am: installing `./compile'
src/lib/Makefile.am: installing `./depcomp'
/usr/share/automake-1.7/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.7/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
src/module/Makefile.am:15: Libtool library used but `LIBTOOL' is undefined
src/module/Makefile.am:15:
src/module/Makefile.am:15: The usual way to define `LIBTOOL' is to add `AC_PROG_LIBTOOL'
src/module/Makefile.am:15: to `configure.ac' and run `aclocal' and `autoconf' again.
/usr/share/automake-1.7/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.7/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.7/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.7/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL
/usr/share/automake-1.7/am/depend2.am: am__fastdepCC does not appear in AM_CONDITIONAL
/usr/share/automake-1.7/am/depend2.am: AMDEP does not appear in AM_CONDITIONAL

---

### Post by Don_DiZzLe on 2006-07-20
I get this the whole time:

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evfs.log:
-----------------------------------------------------------------------------
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/include/taglib -g -O2 -D_FILE_OFFSET_BITS=64 -MT audio_tagger_la-evfs_meta_audio.lo -MD -MP -MF ".deps/audio_tagger_la-evfs_meta_audio.Tpo" -c -o audio_tagger_la-evfs_meta_audio.lo `test -f 'evfs_meta_audio.c' || echo './'`evfs_meta_audio.c; \
        then mv -f ".deps/audio_tagger_la-evfs_meta_audio.Tpo" ".deps/audio_tagger_la-evfs_meta_audio.Plo"; else rm -f ".deps/audio_tagger_la-evfs_meta_audio.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/include/taglib -g -O2 -D_FILE_OFFSET_BITS=64 -MT audio_tagger_la-evfs_meta_audio.lo -MD -MP -MF .deps/audio_tagger_la-evfs_meta_audio.Tpo -c evfs_meta_audio.c  -fPIC -DPIC -o .libs/audio_tagger_la-evfs_meta_audio.o
evfs_meta_audio.c:44:19: error: tag_c.h: No such file or directory
evfs_meta_audio.c: In function 'evfs_file_meta_retrieve':
evfs_meta_audio.c:70: error: 'TagLib_File' undeclared (first use in this function)
evfs_meta_audio.c:70: error: (Each undeclared identifier is reported only once
evfs_meta_audio.c:70: error: for each function it appears in.)
evfs_meta_audio.c:70: error: 'taglib_file' undeclared (first use in this function)
evfs_meta_audio.c:71: error: 'TagLib_Tag' undeclared (first use in this function)
evfs_meta_audio.c:71: error: 'taglib_tag' undeclared (first use in this function)
evfs_meta_audio.c:72: error: syntax error before '*' token
evfs_meta_audio.c:88: warning: assignment makes pointer from integer without a cast
evfs_meta_audio.c:102: warning: assignment makes pointer from integer without a cast
evfs_meta_audio.c:115: error: 'taglib_props' undeclared (first use in this function)
make[4]: *** [audio_tagger_la-evfs_meta_audio.lo] Error 1
make[4]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs/src/plugins/meta'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs/src/plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs'
make: *** [all] Error 2
-----------------------------------------------------------------------------

What gives?

---

### Post by daedalusman on 2006-07-20
> **Don_DiZzLe said:**
> I get this the whole time:

LAST LOGLINES FROM /tmp/easy_e17/install_logs/evfs.log:
-----------------------------------------------------------------------------
if /bin/sh ../../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/include/taglib -g -O2 -D_FILE_OFFSET_BITS=64 -MT audio_tagger_la-evfs_meta_audio.lo -MD -MP -MF ".deps/audio_tagger_la-evfs_meta_audio.Tpo" -c -o audio_tagger_la-evfs_meta_audio.lo `test -f 'evfs_meta_audio.c' || echo './'`evfs_meta_audio.c; \
        then mv -f ".deps/audio_tagger_la-evfs_meta_audio.Tpo" ".deps/audio_tagger_la-evfs_meta_audio.Plo"; else rm -f ".deps/audio_tagger_la-evfs_meta_audio.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../.. -I. -I../../.. -I../../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/usr/include/taglib -g -O2 -D_FILE_OFFSET_BITS=64 -MT audio_tagger_la-evfs_meta_audio.lo -MD -MP -MF .deps/audio_tagger_la-evfs_meta_audio.Tpo -c evfs_meta_audio.c  -fPIC -DPIC -o .libs/audio_tagger_la-evfs_meta_audio.o
evfs_meta_audio.c:44:19: error: tag_c.h: No such file or directory
evfs_meta_audio.c: In function 'evfs_file_meta_retrieve':
evfs_meta_audio.c:70: error: 'TagLib_File' undeclared (first use in this function)
evfs_meta_audio.c:70: error: (Each undeclared identifier is reported only once
evfs_meta_audio.c:70: error: for each function it appears in.)
evfs_meta_audio.c:70: error: 'taglib_file' undeclared (first use in this function)
evfs_meta_audio.c:71: error: 'TagLib_Tag' undeclared (first use in this function)
evfs_meta_audio.c:71: error: 'taglib_tag' undeclared (first use in this function)
evfs_meta_audio.c:72: error: syntax error before '*' token
evfs_meta_audio.c:88: warning: assignment makes pointer from integer without a cast
evfs_meta_audio.c:102: warning: assignment makes pointer from integer without a cast
evfs_meta_audio.c:115: error: 'taglib_props' undeclared (first use in this function)
make[4]: *** [audio_tagger_la-evfs_meta_audio.lo] Error 1
make[4]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs/src/plugins/meta'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs/src/plugins'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dazkrlauwste/e17_cvs/e17/apps/evfs'
make: *** [all] Error 2
-----------------------------------------------------------------------------

What gives?


You need to download and install taglib from this site [http://developer.kde.org/~wheeler/taglib.html](http://developer.kde.org/~wheeler/taglib.html) 
also if you have libxine 1.1.1 (dapper repo's version) than you should be able to install emotion and eclair aswell. Just today I used this script to install e17 without skipping anything and that was really the only major problem I came across.

---

### Post by Don_DiZzLe on 2006-07-21
Ok thnx for your reply but I fixed the problem already. It was indeed the taglib package that I needed to install.

---

### Post by Don_DiZzLe on 2006-07-21
Why aren't all the xtra packages that have come up throughout this thread not been included with the dependacies on the first page?

It would be a lot easier to have all the dependacies installed first insted of lookin through this thread for all the extra requirden packages

---

### Post by TimmyJ on 2006-07-21
> **Don_DiZzLe said:**
> Why aren't all the xtra packages that have come up throughout this thread not been included with the dependacies on the first page?

It would be a lot easier to have all the dependacies installed first insted of lookin through this thread for all the extra requirden packages

I'm sorry, that would be my mistake. I wrote this how-to for breezy  badget some time ago and have unfortunately neglected it since then. I'll do my best to look through this how-to and update the original guide as neccesary.

---

### Post by Don_DiZzLe on 2006-07-21
OK Cool!

---

### Post by TimmyJ on 2006-07-21
I have updated the guide with the changes I saw in a quick look-over of this thread. If anyone finds any errors or has a suggestion about how to improve this guide, please PM me.

Also, I have one question: daedalusman mentioned that you need to get taglib to be installed from [http://developer.kde.org/~wheeler/taglib.html](http://developer.kde.org/~wheeler/taglib.html). Is there a version of taglib in the repositories that will suffice? I have left this out of my how-to until I hear back. I'd test this myself but I'm not at home.

---

### Post by Don_DiZzLe on 2006-07-21
I just installed all the packages listed in synaptic after searching for "taglib" 

That did the trick for and I was able to install E17 after that.

---

### Post by daedalusman on 2006-07-21
> **Don_DiZzLe said:**
> I just installed all the packages listed in synaptic after searching for "taglib" 

That did the trick for and I was able to install E17 after that.

Taglib packages did you install from synaptic, the ones I installed didn't seem to do the trick for me, thats why I compiled from source? Thanks.

---

### Post by Don_DiZzLe on 2006-07-21
The last dependancy that you have listed is taglig-dev, I think this should be " libtag1-dev" ( and maybe or maybe not this one "libtag0-dev" too).

---

### Post by Adrian_b on 2006-07-27
Can anyone tell me what i exactly need on this point?
Since it probably changed since i tried it in December...

---

### Post by vuitton on 2006-07-27
Hi Adrian,  
'Last edited by TimmyJ : 3 Days Ago at 07:31 PM. Reason: update'
The How-to should be up to date

---

### Post by TimmyJ on 2006-07-27
Yes, I've tried to keep this how-to up to date recently. If you notice/experience any problems please don't hesitate to post on this forum or PM me.

-TimmyJ

---

### Post by deen on 2006-07-28
hi timmy
do you have .deb package of E17 ? for intel 386 architecture.

Thank you.

---

### Post by TimmyJ on 2006-07-28
> **deen said:**
> hi timmy
do you have .deb package of E17 ? for intel 386 architecture.

Thank you.

No, I download and install E17 from CVS so as to always have the latest code. There are however some packages out there for dapper. I have not used these packages and cannot vouch for them in any way. 

To add the repository containing these deb packages simply add the following line to /etc/apt/sources.list file:

deb [http://edevelop.org/ubuntu](http://edevelop.org/ubuntu) dapper e17

-TimmyJ

---

### Post by juancaman80 on 2006-07-29
Hey folks...I'm a Ubuntu newbie...trying to get E17 to work, and I'm just out of ideas on this one:


```


LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/edje.log:
-----------------------------------------------------------------------------
make[3]: Leaving directory `/home/juanca/e17_cvs/e17/libs/edje/src/lib'
Making all in bin
make[3]: Entering directory `/home/juanca/e17_cvs/e17/libs/edje/src/bin'
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../bin -I../../src/lib -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -DPACKAGE_BIN_DIR=\"/opt/e17/bin\" -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/edje\"   -I/opt/e17/include  -g -O2 -MT edje_main.o -MD -MP -MF ".deps/edje_main.Tpo" \
          -c -o edje_main.o `test -f 'edje_main.c' || echo './'`edje_main.c; \
        then mv -f ".deps/edje_main.Tpo" ".deps/edje_main.Po"; \
        else rm -f ".deps/edje_main.Tpo"; exit 1; \
        fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../.. -I../.. -I../../bin -I../../src/lib -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -DPACKAGE_BIN_DIR=\"/opt/e17/bin\" -DPACKAGE_LIB_DIR=\"/opt/e17/lib\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/edje\"   -I/opt/e17/include  -g -O2 -MT edje_prefix.o -MD -MP -MF ".deps/edje_prefix.Tpo" \
          -c -o edje_prefix.o `test -f 'edje_prefix.c' || echo './'`edje_prefix.c; \
        then mv -f ".deps/edje_prefix.Tpo" ".deps/edje_prefix.Po"; \
        else rm -f ".deps/edje_prefix.Tpo"; exit 1; \
        fi
/bin/sh ../../libtool --mode=link gcc  -g -O2  -L/opt/e17/lib -o edje  edje_main.o edje_prefix.o ../../src/lib/libedje.la
mkdir .libs
gcc -g -O2 -o .libs/edje edje_main.o edje_prefix.o  -L/opt/e17/lib ../../src/lib/.libs/libedje.so
../../src/lib/.libs/libedje.so: undefined reference to `eet_data_descriptor2_new'
collect2: ld returned 1 exit status
make[3]: *** [edje] Error 1
make[3]: Leaving directory `/home/juanca/e17_cvs/e17/libs/edje/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/juanca/e17_cvs/e17/libs/edje/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/juanca/e17_cvs/e17/libs/edje'
make: *** [all] Error 2


```

I've been kinda having issues with every other package when compiling, and I've made it this far, I've tried quite a few things mentioned in earlier posts from this thread, any ideas on what else I could do for this one.
Any help will be greatly appreciated :)

-JC

---

### Post by Metroid48 on 2006-07-30
Hey, error:

./easy_e17.sh: line 150: cvs: command not found

it just keeps retrying that line. This happens when I execute the script.

---

### Post by Rui Pais on 2006-08-01
> **Metroid48 said:**
> Hey, error:

./easy_e17.sh: line 150: cvs: command not found

it just keeps retrying that line. This happens when I execute the script.

Hi, 
You need cvs installed.
```
sudo apt-get install cvs
```
should solve it.

---

### Post by PascalGR on 2006-08-05
If anyone has still problems with installing e17 under Ubuntu, you may try this How-To: [http://www.pascal.gr/articles/ubuntu_e17.php](http://www.pascal.gr/articles/ubuntu_e17.php)

I've wrotten it while I was trying to install e17 by myself and was tracking down all the steps.

Hope will help you :)

---

### Post by Nightblade on 2006-08-12
- e_utils .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/e_utils.log:
-----------------------------------------------------------------------------
:/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/main.c:225: undefined reference to `ecore_desktop_paths_shutdown'
global.o: In function `backup_eaps':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/global.c:159: undefined reference to `ecore_desktop_get_home'
:/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/global.c:182: undefined reference to `ecore_desktop_get_home'
:/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/global.c:190: undefined reference to `ecore_desktop_get_home'
global.o: In function `write_mapping_file':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/global.c:209: undefined reference to `ecore_desktop_get_home'
menus.o: In function `make_menus':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/menus.c:50: undefined reference to `ecore_desktop_paths_search_for_file':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/menus.c:61: undefined reference to `ecore_desktop_menus_get'
:/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/menus.c:65: undefined reference to `ecore_desktop_tree_foreach'
parse.o: In function `_parse_process_file':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/parse.c:201: undefined reference to `ecore_desktop_get_home'
:/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/parse.c:210: undefined reference to `ecore_desktop_find_icon'
parse.o: In function `parse_desktop_file':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/parse.c:114: undefined reference to `ecore_desktop_get_home'
:/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/parse.c:123: undefined reference to `ecore_desktop_parse_file'
sort.o: In function `sort_menu':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/sort.c:69: undefined reference to `ecore_desktop_get_home'
sort.o: In function `sort_menus':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/sort.c:139: undefined reference to `ecore_desktop_get_home'
sort.o: In function `sort_favorites':/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu/sort.c:172: undefined reference to `ecore_desktop_get_home'
collect2: ld returned 1 exit status
make[4]: *** [e17genmenu] Error 1
make[4]: Leaving directory `/home/zth/e17_cvs/e17/apps/e_utils/src/bin/e17genmenu'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/zth/e17_cvs/e17/apps/e_utils/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/zth/e17_cvs/e17/apps/e_utils/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/zth/e17_cvs/e17/apps/e_utils'
make: *** [all] Error 2
-----------------------------------------------------------------------------


That's what I get... help? :)

---

### Post by gordho on 2006-08-16
I was not able to complete step one because apt-get could not find libtag0-dev. I removed this one package from the install and of course had problems further down the road. Once Easy_e17.sh would get to eclair it would bomb. I tried skipping eclair but then it bombed again on evfs. On page 35 of this thread Don_Dizzle recommended installing taglib from synaptic. I installed libtagc0-dev which also required libtagc0 from synaptic and then was able to succesfully compile/install eclair and the rest of the apps using the Easy_e17.sh script. Should it be changed in step one to be libtagc0-dev and not libtag0-dev? 

I also had a problem compiling evolume and had to install libasound2-dev. Should this be in step one as well?

---

### Post by TimmyJ on 2006-08-21
> **gordho said:**
> I was not able to complete step one because apt-get could not find libtag0-dev. I removed this one package from the install and of course had problems further down the road. Once Easy_e17.sh would get to eclair it would bomb. I tried skipping eclair but then it bombed again on evfs. On page 35 of this thread Don_Dizzle recommended installing taglib from synaptic. I installed libtagc0-dev which also required libtagc0 from synaptic and then was able to succesfully compile/install eclair and the rest of the apps using the Easy_e17.sh script. Should it be changed in step one to be libtagc0-dev and not libtag0-dev? 

I also had a problem compiling evolume and had to install libasound2-dev. Should this be in step one as well?

I added libasound2-dev to the requirements and fixed the libtag requirement. Thanks for the fix.

---

### Post by gordho on 2006-08-21
I also needed libxslt1-dev otherwise when building exml it would die and give a "configure: error: Make sure that xslt-config is in your PATH or that Xslt is correctly installed"

Also, I went to install e17 on a fresh install of Ubuntu today and am not able to build engage, empower, extrackt, calendar, cpu, devian, evolume, mbar, and wlan. This is probably due to the recent change in cvs, see [http://www5.get-e.org/Main/News/_articles/318.html](http://www5.get-e.org/Main/News/_articles/318.html).

---

### Post by Goemon4 on 2006-08-21
how do i dl all those apps that they took off the cvs? (cause im on e17 and want those apps!)


btw great tut, e17 rules!!

thanks
-Goemon4


EDIT: also how would you delete e17 after using this tut?

---

### Post by DigiNeT on 2006-08-23
hi guys, i need some help here, all the libs are compiled but one app called "Engage" has this error.

```
LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... ok
- ewl ........................ ok
- engrave .................... ok
- exml ....................... ok
-----------------------------------------------------------------------------

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... ok
- e .......................... ok
- eclair ..................... ok
- evfs ....................... ok
- e_utils .................... ok
- engage ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
e_mod_main.c:2550: error: dereferencing pointer to incomplete type
e_mod_main.c: In function '_engage_zoom_function':
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2634: error: dereferencing pointer to incomplete type
e_mod_main.c:2635: error: dereferencing pointer to incomplete type
e_mod_main.c:2651: error: dereferencing pointer to incomplete type
e_mod_main.c:2653: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2663: error: dereferencing pointer to incomplete type
e_mod_main.c:2665: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2672: error: dereferencing pointer to incomplete type
e_mod_main.c:2674: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
make[3]: *** [e_mod_main.lo] Error 1
make[3]: se sale del directorio `/home/diginet/e17_cvs/misc/engage/src/module'
make[2]: *** [all-recursive] Error 1
make[2]: se sale del directorio `/home/diginet/e17_cvs/misc/engage/src'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/diginet/e17_cvs/misc/engage'
make: *** [all] Error 2
-----------------------------------------------------------------------------

```

---

### Post by TimmyJ on 2006-08-23
The following modules will NOT install under current E17 code due to recent CVS changes: calendar, cpu, eloquence, engage, devian, evolume, wlan. When running the script you must choose to skip over these applications.
```

./easy_e17.sh -i --skip=calendar,cpu,eloquence,engage,devian,evolume,wlan

```

---

### Post by tzulberti on 2006-08-23
I recommend you take a look at: [www.get-e.org](www.get-e.org), where it says in the news that is not useful to install/update e17 this days because of the great working they are doing.

---

### Post by Rui Pais on 2006-08-24
Hi,
i have been working on a modified version of morlenxus' easy_e17.sh that deals better with updates and intallations of specific dates (to hold darkest times when e17 is broken :().
Specially i wanted that the script only check/download cvs tree that i want to install (not all code!) and that only rebuild/update the needed libs/apps. 

That make it much faster, on updates, to the user and much lighter on e17 servers. :-\" 

The  latest version of easy_e17.sh, 1.0.3, already include same of my desired features (not download all cvs sources),
but unfortunantely just for --only flag (!?)

I made a patch to apply to that version with some add-ons and extras.

----------------------------
Here are the changes:
----------------------------
**--date=<DATE>** (optional new flag)
**Logs of updates** (on /opt/e17)
**Ask for confirmation, after it shows what will be done.**
**Only outputs information header report once** (3 times on the original!)
**Only do CVS updates of the chosen e17 libs/apps/modules.**
**Only compiles libs/apps/modules that have been updated on cvs.**

You can get the original [here]("http://omicron.homeip.net/projects/easy_e17/easy_e17.sh") and patch [here]("http://homepage.oniduo.pt/rui.pais/projectos/easy_e17.patch.txt").

Apply it with:
```
patch easy_e17.sh easy_e17.patch.txt
```

And use it with the normal syntax or to specify a certain date with the new flag, 
```
sudo ./easy_e17.sh -i --date=2006-08-19
```

Hope some of you find it usefull. 
Is not very well tested, but i'm work it with it for some time and it's been ok.

-----------------------------

[QUOTE=]how do i dl all those apps that they took off the cvs? (cause im on e17 and want those apps!)[/QUOTE]
The example above with --date=2006-08-19 will give the latest working version of e17 (before the removal of the old gadman code). 
If you already compiled a broken version please remove it first!!
> how would you delete e17
simply do:
```
sudo rm -rf /opt/e17
```
or if you want to make a backup:
```
sudo mv /opt/e17 /opt/e17_BACKUP
```

---

### Post by Gylu on 2006-08-25
Something is not working for me I did everything that is in the first post but I do not have /opt/e17/bin/enlightenment I have /opt/e17/bin/ but there is no enlightenment in that dir.  I may have something wrong but I don't see anything that I missed.  I am really new to Linux so it may be something that I am doing wrong.

---

### Post by rko618 on 2006-08-25
I'm getting a syntax error when I attempt to build

```
make[4]: Entering directory `/home/rob/e17_cvs/e17/proto/empower/src/bin/etk'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../../src/bin   -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -MT empower_etk-empower.o -MD -MP -MF ".deps/empower_etk-empower.Tpo" -c -o empower_etk-empower.o `test -f 'empower.c' || echo './'`empower.c; \
        then mv -f ".deps/empower_etk-empower.Tpo" ".deps/empower_etk-empower.Po"; else rm -f ".deps/empower_etk-empower.Tpo"; exit 1; fi
In file included from empower.c:1:
Empower.h:32: error: syntax error before ‘Etk_Event_Key_Up_Down’

```


I will try again tonight hopefully they will have fixed this by then.

---

### Post by kimusabi on 2006-08-25
Not to sure if this has been reported or not. But I felt it worth a go.

```

- engage ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
e_mod_main.c:2550: error: dereferencing pointer to incomplete type
e_mod_main.c: In function '_engage_zoom_function':
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2634: error: dereferencing pointer to incomplete type
e_mod_main.c:2635: error: dereferencing pointer to incomplete type
e_mod_main.c:2651: error: dereferencing pointer to incomplete type
e_mod_main.c:2653: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2663: error: dereferencing pointer to incomplete type
e_mod_main.c:2665: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2672: error: dereferencing pointer to incomplete type
e_mod_main.c:2674: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
make[3]: *** [e_mod_main.lo] Error 1
make[3]: Leaving directory `/home/kimusabi/e17_cvs/misc/engage/src/module'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/kimusabi/e17_cvs/misc/engage/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/kimusabi/e17_cvs/misc/engage'
make: *** [all] Error 2
-----------------------------------------------------------------------------

```

I tried deleting the CVS dir but still the same problem.

EDIT: I think I have it resolved, just looked at TimmyJ's post, hopefully this should fix it.

---

### Post by r00tzz on 2006-08-26
libxslt1-dev is now required.

---

### Post by rko618 on 2006-08-26
Awesome! Your modification worked wonderfully for me Rui Pais.  E17 didn't compile until I tried your modification.  I recommend everyone use this instead of the script in its original state.

---

### Post by Rui Pais on 2006-08-27
> **rko618 said:**
> Awesome! Your modification worked wonderfully for me Rui Pais.  E17 didn't compile until I tried your modification.  I recommend everyone use this instead of the script in its original state.

Hi, 
glad to hear it :)

---

### Post by _savior_ on 2006-08-27
> **TimmyJ said:**
> 
1.) First we want to install all required packages for E17, and all the Enlightenment Foundation Libraries to install. This list may be a bit of overkill, but it will get the job done.

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
```


I must say that it is not overkill. Because of exml, libxslt-dev should be added too. :) 

Anyway, thanks for the nice tutorial! =D> 

Savior

---

### Post by carney1979 on 2006-08-29
```
#############################################################################
#             easy_e17.sh (1.0.3) by Brian 'morlenxus' Miculcy              #
#                                                                           #
#                       Thanks for supplying patches:                       #
#                           David 'onefang' Seikel                          #
#                           Tim 'wtfoo' Zebulla                             #
#                                                                           #
#    This is the result of the ideas from the people of #e.de - join us.    #
# Updates: http://omicron.homeip.net/projects/ | Contact: morlenxus@gmx.net #
#############################################################################


CURRENT CONFIGURATION:
  - install-path:     /opt/e17
  - cvs-path:         /home/david/e17_cvs
  - logs-path:        /tmp/easy_e17/install_logs
  - nice level:       0

  - installable libs:     imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion ewl engrave exml
  - installable apps:     entrance e eclair evfs e_utils
  - installable misc:     engage scrot
  - installable proto:    etk etk_server edje_viewer enhance empower entropy ephoto exhibit extrackt
  - installable modules:  bling calendar cpu deskshow devian emu eveil evolume flame language mail mbar mem moon net rain screenshot slideshow snow taskbar tclock uptime weather wlan
  - skipping:             -

  - script action:        install


BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... previous installed
- epsilon .................... previous installed
- esmart ..................... previous installed
- emotion .................... previous installed
- ewl ........................ previous installed
- engrave .................... previous installed
- exml ....................... previous installed
-----------------------------------------------------------------------------

APPS-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- entrance ................... previous installed
- e .......................... previous installed
- eclair ..................... previous installed
- evfs ....................... previous installed
- e_utils .................... previous installed
- engage ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
e_mod_main.c:2550: error: dereferencing pointer to incomplete type
e_mod_main.c: In function '_engage_zoom_function':
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2634: error: dereferencing pointer to incomplete type
e_mod_main.c:2635: error: dereferencing pointer to incomplete type
e_mod_main.c:2651: error: dereferencing pointer to incomplete type
e_mod_main.c:2653: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2663: error: dereferencing pointer to incomplete type
e_mod_main.c:2665: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2672: error: dereferencing pointer to incomplete type
e_mod_main.c:2674: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
make[3]: *** [e_mod_main.lo] Error 1
make[3]: Leaving directory `/home/david/e17_cvs/misc/engage/src/module'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/david/e17_cvs/misc/engage/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/david/e17_cvs/misc/engage'
make: *** [all] Error 2
-----------------------------------------------------------------------------


david@n1zhe:~$

``` 
Ooops!

What now?

David

---

### Post by Rui Pais on 2006-08-29
For me, i'm not even remember when was the last time i could compile engage. Month now. 
I always got "dereferencing pointer to incomplete type" errors. 

Don't know why. Don't seems to be a dependency problem... i suspect it is the gcc version (4.0.3 on Dapper, instead of 4.1 series), because on my gentoo it compiled fine with the later gcc. But don't really know.


Just skip engage. ibar it's fine. Better in most opinions.

---

### Post by mikkelk on 2006-08-31
Hi

I got it to work using Rui Pais's patch.

But why are my "all applications" menu empty?
I have tried the  "regenerate 'all applications'menu" feature but I still don't get any applications.

/Mikkel Kaas

---

### Post by r00tzz on 2006-08-31
Okay people.. Just recompiled CVS and gues what? EVERYTHING is working again!! Well, not everything, have to skip empower and extrackt, but its great!

mikkelk: try e17genmenu to generate the menu for you. HTH

---

### Post by Rui Pais on 2006-09-01
> **mikkelk said:**
> Hi

I got it to work using Rui Pais's patch.

But why are my "all applications" menu empty?
I have tried the  "regenerate 'all applications'menu" feature but I still don't get any applications.

/Mikkel Kaas

thanks for give my patch a try.
i don't know how this new `Regenerate "All Applications" Menu' works since i'm still using a e17 from 19 Aug that don't have it.
Have you checked for correct folders as indicated [here]("http://www5.get-e.org/Main/News/_articles/323.html")?
Anyway e17genmenu, that mikkelk have point it, usually gives enough good results (not perfect but functional at least). 
Most of the times failures occurs when deal with apps that have svg instead of png as icons... 

> **r00tzz said:**
> Okay people.. Just recompiled CVS and gues what? EVERYTHING is working again!! Well, not everything, have to skip empower and extrackt, but its great!
Hi 
get-e.org mention that cpu is now working but don't mention none of the others of the failure modules. 
Have you got calendar, evolume or wlan already working?

---

### Post by ramasdf123 on 2006-09-02
i am getting this

[HTML]engage ..................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/engage.log:
-----------------------------------------------------------------------------
e_mod_main.c:2550: error: dereferencing pointer to incomplete type
e_mod_main.c: In function '_engage_zoom_function':
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2633: error: dereferencing pointer to incomplete type
e_mod_main.c:2634: error: dereferencing pointer to incomplete type
e_mod_main.c:2635: error: dereferencing pointer to incomplete type
e_mod_main.c:2651: error: dereferencing pointer to incomplete type
e_mod_main.c:2653: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2660: error: dereferencing pointer to incomplete type
e_mod_main.c:2663: error: dereferencing pointer to incomplete type
e_mod_main.c:2665: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2666: error: dereferencing pointer to incomplete type
e_mod_main.c:2672: error: dereferencing pointer to incomplete type
e_mod_main.c:2674: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
e_mod_main.c:2675: error: dereferencing pointer to incomplete type
make[3]: *** [e_mod_main.lo] Error 1
make[3]: Leaving directory `/home/rama/e17_cvs/misc/engage/src/module'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rama/e17_cvs/misc/engage/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rama/e17_cvs/misc/engage'
make: *** [all] Error 2
-----------------------------------------------------------------------------
[/HTML]

any1 know how to fix this?

and 

[HTML]empower .................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/empower.log:
-----------------------------------------------------------------------------
if gcc -DHAVE_CONFIG_H -I. -I. -I../../../src/bin   -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/ewl -g -O2 -MT empower_ewl-empower.o -MD -MP -MF ".deps/empower_ewl-empower.Tpo" -c -o empower_ewl-empower.o `test -f 'empower.c' || echo './'`empower.c; \
        then mv -f ".deps/empower_ewl-empower.Tpo" ".deps/empower_ewl-empower.Po"; else rm -f ".deps/empower_ewl-empower.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../../src/bin   -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/ewl -g -O2 -MT empower_ewl-empower_cb_ewl.o -MD -MP -MF ".deps/empower_ewl-empower_cb_ewl.Tpo" -c -o empower_ewl-empower_cb_ewl.o `test -f 'empower_cb_ewl.c' || echo './'`empower_cb_ewl.c; \
        then mv -f ".deps/empower_ewl-empower_cb_ewl.Tpo" ".deps/empower_ewl-empower_cb_ewl.Po"; else rm -f ".deps/empower_ewl-empower_cb_ewl.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../../src/bin   -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/ewl -g -O2 -MT empower_ewl-empower_gui_ewl.o -MD -MP -MF ".deps/empower_ewl-empower_gui_ewl.Tpo" -c -o empower_ewl-empower_gui_ewl.o `test -f 'empower_gui_ewl.c' || echo './'`empower_gui_ewl.c; \
        then mv -f ".deps/empower_ewl-empower_gui_ewl.Tpo" ".deps/empower_ewl-empower_gui_ewl.Po"; else rm -f ".deps/empower_ewl-empower_gui_ewl.Tpo"; exit 1; fi
/bin/sh ../../../libtool --tag=CC --mode=link gcc  -g -O2  -L/opt/e17/lib -o empower_ewl  empower_ewl-empower.o empower_ewl-empower_cb_ewl.o empower_ewl-empower_gui_ewl.o  -L/opt/e17/lib -lewl -L/opt/e17/lib -lemotion -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/opt/e17/lib -lecore -lecore_job -lecore_x -L/usr/X11R6/lib -lX11 -lXext -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_config -lecore_file -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -lecore_desktop -lecore_dbus -lssl -lcrypto -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/usr/X11R6/lib -lX11 -lXext -lXcursor -lXrender -lXinerama -lXrandr -lXfixes -lXdamage -lm -ldl -L/opt/e17/lib -ledje -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/opt/e17/lib -lecore -lecore_job -lecore_x -L/usr/X11R6/lib -lX11 -lXext -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_config -lecore_file -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -lecore_desktop -lecore_dbus -lssl -lcrypto -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/usr/X11R6/lib -lX11 -lXext -lXcursor -lXrender -lXinerama -lXrandr -lXfixes -lXdamage -lm -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -lembryo -lm -lm -L/opt/e17/lib -lecore -lecore_job -lecore_x -L/usr/X11R6/lib -lX11 -lXext -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_config -lecore_file -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -lecore_desktop -lecore_dbus -lssl -lcrypto -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/usr/X11R6/lib -lX11 -lXext -lXcursor -lXrender -lXinerama -lXrandr -lXfixes -lXdamage -lm -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/opt/e17/lib -lepsilon -L/usr/lib -lImlib2 -lfreetype -lz -lX11 -lXext -ldl -lm -L/opt/e17/lib -lepeg -ljpeg -L/opt/e17/lib -ledje -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/opt/e17/lib -lecore -lecore_job -lecore_x -L/usr/X11R6/lib -lX11 -lXext -lecore_evas -lecore_con -lecore_ipc -lecore_txt -lecore_config -lecore_file -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -lecore_desktop -lecore_dbus -lssl -lcrypto -L/usr/lib -lcurl -L/usr/lib -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -lssl -lcrypto -ldl -lssl -lcrypto -lz -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -levas -ldl -L/opt/e17/lib -leet -lz -ljpeg -lfreetype -lz -L/usr/X11R6/lib -lX11 -lXext -lXcursor -lXrender -lXinerama -lXrandr -lXfixes -lXdamage -lm -L/opt/e17/lib -leet -lz -ljpeg -L/opt/e17/lib -lembryo -lm -lm -lpng12 -lm
mkdir .libs
gcc -g -O2 -o empower_ewl empower_ewl-empower.o empower_ewl-empower_cb_ewl.o empower_ewl-empower_gui_ewl.o  -L/opt/e17/lib /opt/e17/lib/libewl.so /opt/e17/lib/libemotion.so -L/usr/X11R6/lib -L/usr/lib /opt/e17/lib/libepsilon.so /opt/e17/lib/libImlib2.so /opt/e17/lib/libepeg.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_desktop.so /opt/e17/lib/libecore_dbus.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -lssl -lcrypto /opt/e17/lib/libevas.so -ldl /usr/lib/libfreetype.so -lX11 -lXext -lXcursor -lXrender -lXinerama -lXrandr -lXfixes -lXdamage /opt/e17/lib/libeet.so -lz /usr/lib/libjpeg.so /opt/e17/lib/libembryo.so -lpng12 -lm
make[4]: Leaving directory `/home/rama/e17_cvs/e17/proto/empower/src/bin/ewl'
Making all in etk
make[4]: Entering directory `/home/rama/e17_cvs/e17/proto/empower/src/bin/etk'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../../src/bin   -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -MT empower_etk-empower.o -MD -MP -MF ".deps/empower_etk-empower.Tpo" -c -o empower_etk-empower.o `test -f 'empower.c' || echo './'`empower.c; \
        then mv -f ".deps/empower_etk-empower.Tpo" ".deps/empower_etk-empower.Po"; else rm -f ".deps/empower_etk-empower.Tpo"; exit 1; fi
In file included from empower.c:1:
Empower.h:32: error: syntax error before ‘Etk_Event_Key_Up_Down’
make[4]: *** [empower_etk-empower.o] Error 1
make[4]: Leaving directory `/home/rama/e17_cvs/e17/proto/empower/src/bin/etk'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/rama/e17_cvs/e17/proto/empower/src/bin'
make[2]: *** [all] Error 2
make[2]: Leaving directory `/home/rama/e17_cvs/e17/proto/empower/src/bin'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rama/e17_cvs/e17/proto/empower/src'
make: *** [all-recursive] Error 1
-----------------------------------------------------------------------------
[/HTML]

---

### Post by thelanlegend on 2006-09-02
I just tried this How-To on a fresh install of ubuntu and everything appeared to work fine until I got to here:

```
BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... previous installed
- epsilon .................... previous installed
- esmart ..................... previous installed
- emotion .................... previous installed
- ewl ........................ previous installed
- engrave .................... previous installed
- exml ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/exml.log:
-----------------------------------------------------------------------------
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld -m elf_x86_64
checking if the linker (/usr/bin/ld -m elf_x86_64) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld -m elf_x86_64) supports shared libr aries... yes
```

I searched and didn't see anyone getting this besides me. Any ideas?

---

### Post by gordho on 2006-09-02
> **thelanlegend said:**
> I just tried this How-To on a fresh install of ubuntu and everything appeared to work fine until I got to here:

```
BUILD PHASE: 2/3
  - lib-compilation and installation
  - apps-compilation and installation

#############################################################################



LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... previous installed
- epsilon .................... previous installed
- esmart ..................... previous installed
- emotion .................... previous installed
- ewl ........................ previous installed
- engrave .................... previous installed
- exml ....................... ERROR!
-----------------------------------------------------------------------------

```

I searched and didn't see anyone getting this besides me. Any ideas?

the import part you need is actually at the end of the log. If you are getting a message that says "configure: error: Make sure that xslt-config is in your PATH or that Xslt is correctly installed" then you need to install libxslt1-dev.

---

### Post by r00tzz on 2006-09-03
> **Rui Pais said:**
> 
Hi 
get-e.org mention that cpu is now working but don't mention none of the others of the failure modules. 
Have you got calendar, evolume or wlan already working?

wlan adn calendar are working, evolume, at least in my conf, isn't. Aparentely, no mixer found.

---

### Post by Rui Pais on 2006-09-03
Thanks for the info.
I'll try an update soon...


-------------------------------------------------------------------------------

Edit:
> **r00tzz said:**
> wlan adn calendar are working
Hi again, 
are you sure you are not using some version from pre 20 August? cause i still got gadman references with latest calendar code...
>  gcc -DHAVE_CONFIG_H -I. -I. -I.. -I. -I.. -I/opt/e17/include -I/opt/e17/include/enlightenment -DUSE_E_CONFIG_H -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -Os -march=pentium4 -mtune=pentium4 -pipe -fomit-frame-pointer -MT add_event_dialog.lo -MD -MP -MF .deps/add_event_dialog.Tpo -c add_event_dialog.c  -fPIC -DPIC -o .libs/add_event_dialog.o
In file included from add_event_dialog.c:2:
e_mod_main.h:218: error: syntax error before 'E_Gadman_Client'
e_mod_main.h:218: warning: no semicolon at end of struct or union
e_mod_main.h:257: error: syntax error before '}' token
In file included from e_mod_main.h:329,
                 from add_event_dialog.c:2:
cal_face_func.h:16: error: syntax error before 'E_Gadman_Client'
add_event_dialog.c: In function '_add_event_basic_create_widgets':
add_event_dialog.c:130: warning: passing argument 2 of 'e_widget_entry_add' from incompatible pointer type
make[3]: *** [add_event_dialog.lo] Error 1
make[3]: Leaving directory `/home/rui/.e17_cvs/e_modules/calendar/src'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/rui/.e17_cvs/e_modules/calendar/src'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/rui/.e17_cvs/e_modules/calendar'
make: *** [all] Error 2

---

### Post by Rui Pais on 2006-09-04
:arrow: **[COLOR="SeaGreen"]To those using my patch[/COLOR]**

I found 2 annoying things. 
Sometimes after using a patched version of script cvs update is not done it without delete cvs tree 
and --only flag is being overwhelmed by patch behavior :(. 
I made an [update of patch]("http://homepage.oniduo.pt/rui.pais/projectos/easy_e17.patch.txt") that correct that. 

PLEASE APPLY TO AN ORIGINAL/UNPATCHED [easy_e17.sh]("http://omicron.homeip.net/projects/easy_e17/easy_e17.sh")!!

---

### Post by Rui Pais on 2006-09-08
Hi again,
for those who have problems installing using this method seems to be now, according to e-news, an constantly updated Ubuntu repository for e17.

[Check it here]("http://www4.get-e.org/Main/News/_articles/334.html").

---

### Post by pvphaneuf on 2006-09-10
I'm getting an error similar to what you have displayed, could anyone help me with this?

LIB-COMPILATION AND INSTALLATION:
-----------------------------------------------------------------------------
- imlib2 ..................... previous installed
- edb ........................ previous installed
- eet ........................ previous installed
- evas ....................... previous installed
- ecore ...................... previous installed
- epeg ....................... previous installed
- embryo ..................... previous installed
- edje ....................... previous installed
- epsilon .................... previous installed
- esmart ..................... previous installed
- emotion .................... previous installed
- ewl ........................ previous installed
- engrave .................... previous installed
- exml ....................... ERROR!
-----------------------------------------------------------------------------

LAST LOGLINES FROM /tmp/easy_e17/install_logs/exml.log:
-----------------------------------------------------------------------------
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for xml2-config... /usr/bin/xml2-config
checking for xml2 - version >= 2.6.13... yes
checking for xslt-config... no
checking for xslt - version >= 1.1.10... no
*** The xslt-config script installed by xslt could not be found
*** If xslt was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XSLT_CONFIG environment variable to the
*** full path to xslt-config.
configure: error: Make sure that xslt-config is in your PATH or that Xslt is correctly installed
-----------------------------------------------------------------------------

---

### Post by Rui Pais on 2006-09-11
check post #384 in this page.

---

### Post by AcesAndEights on 2006-09-11
Hows everyone doing?

I just finished installing using the instructions from the first post to the dot, with the exception of changing the automake version. I get this error though when I try to log into a new session with enlightenment.

> Xsession:unable to launch "/opt/e17/bin/enlightenment" X
session ---"/opt/e17/bin/enlightenment" not found; falling back 
to default session.

I'm pretty new to linux, so I have no idea where to even start looking for the file. I thinking that I was supposed to change the path in the desktop location file that was created, but i don't know what Im supposed to change it to. Any help would be much apperciated.

Edit: I think I may have found a small part of the problem. In the path file I replaced the orginal code with the code provided instead of simply adding it. Could anyone provide me with the orginal path from the etc/environment/ file?

Edit: Upon further examination, I've determined that I do not have the file /opt/e17/bin/enlightenment. There are a great deal of other exec files in that extension, but I dont have the file "enlightenment" that the desktop file references. Can anyone help me out? Im kind of lost now.

---

### Post by ting on 2006-09-15
to acesandeights.


I tried installing e17 a few weeks ago, and as far as I remember this happened to me too. The problem as far as I remember was that the process had errors which I overlooked. In essence, I never really completed the Install. After becoming annoyed I just excluded the elements which gave me errors. And in the end it worked.

---

### Post by jrock08 on 2006-11-24
I am having a problem with exml on installation.  I looked through and found someone that i think gave a solution to the problem, but I didn't understand what his suggestion was.

---

### Post by BrowneR on 2006-12-02
> **jrock08 said:**
> I am having a problem with exml on installation.  I looked through and found someone that i think gave a solution to the problem, but I didn't understand what his suggestion was.

i had this problem also.
to fix it you need to install libxslt1-dev as follows:
```

sudo apt-get install libxslt1-dev

```

then rerun the script.

---

### Post by Steff81 on 2006-12-03
hi,
i tried install e17 with the easy_e17 script. but i get follow error message
```
---------------------------- Installing applications ---------------------------
- entrance ................... ok          
- e .......................... ok          
- eclair ..................... ok          
- evfs ....................... ok          
- e_utils .................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
../../../libtool: line 1872: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
../../../libtool: line 1872: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
../../../libtool: line 1872: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
../../../libtool: line 1872: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
../../../libtool: line 1872: cd: NONE: No such file or directory
libtool: link: cannot determine absolute directory name of `NONE'
mkdir .libs
gcc -g -O2 -o eap_edit eapp_edit_main.o  -L/opt/e17/lib /opt/e17/lib/libewl.so /opt/e17/lib/libemotion.so -L/usr/lib -LNONE /opt/e17/lib/libepsilon.so /opt/e17/lib/libImlib2.so /opt/e17/lib/libepeg.so /opt/e17/lib/libedje.so /opt/e17/lib/libembryo.so -lpng12 /opt/e17/lib/libengrave.so /opt/e17/lib/libecore.so /opt/e17/lib/libecore_job.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_txt.so /usr/lib/libecore_fb.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_desktop.so /opt/e17/lib/libecore_dbus.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -lssl -lcrypto -lX11 -lXext -lXcursor -lXrender -lXp -lXinerama -lXrandr -lXfixes -lXss /opt/e17/lib/libevas.so -lpthread -ldl /opt/e17/lib/libeet.so /usr/lib/libjpeg.so /usr/lib/libfreetype.so -lz -lfontconfig -lm
eapp_edit_main.o: In function `eapp_ui_init':
/home/steffen/e17_cvs/e17/apps/e_utils/src/bin/eapp_edit/eapp_edit_main.c:208: undefined reference to `ewl_button_stock_type_set'
/home/steffen/e17_cvs/e17/apps/e_utils/src/bin/eapp_edit/eapp_edit_main.c:218: undefined reference to `ewl_button_stock_type_set'
collect2: ld returned 1 exit status
make[4]: *** [eap_edit] Fehler 1
make[4]: Verlasse Verzeichnis '/home/steffen/e17_cvs/e17/apps/e_utils/src/bin/eapp_edit'
make[3]: *** [all-recursive] Fehler 1
make[3]: Verlasse Verzeichnis '/home/steffen/e17_cvs/e17/apps/e_utils/src/bin'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/steffen/e17_cvs/e17/apps/e_utils/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/steffen/e17_cvs/e17/apps/e_utils'
make: *** [all] Fehler 2

```

can anybody help me to fix this error?
libtool is installed
thanks in advance
regards steff

---

### Post by Jorcelangelo on 2007-01-03
I did the five original steps to install the E17. 
but when I finished to run script to install I got an error:

 Script action:   install
--------------------------------------------------------------------------------

-------------------------------- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


--------------------------- Installing libaries (EFL) --------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... ok
- ewl ........................ ok
- engrave .................... ok
- [COLOR="Red"]exml ....................... ERROR![/COLOR]
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for xml2-config... /usr/bin/xml2-config
checking for xml2 - version >= 2.6.13... yes
checking for xslt-config... no
checking for xslt - version >= 1.1.10... no
*** The xslt-config script installed by xslt could not be found
*** If xslt was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XSLT_CONFIG environment variable to the
*** full path to xslt-config.
configure: error: Make sure that xslt-config is in your PATH or that Xslt is correctly installed
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/exml.log'!

musa@musa-desktop:/home$  


**************

the content of the file exml.log is:
Running aclocal...
/usr/share/aclocal/snacc.m4:24: warning: underquoted definition of AM_PATH_SNACC
  run info '(automake)Extending aclocal'
  or see [http://sources.redhat.com/automake/automake.html#Extending-aclocal](http://sources.redhat.com/automake/automake.html#Extending-aclocal)
/usr/share/aclocal/glib.m4:8: warning: underquoted definition of AM_PATH_GLIB
Running autoheader...
Running autoconf...
Running libtoolize...
Running automake...
configure.in: installing `./install-sh'
configure.in: installing `./missing'
checking for a BSD-compatible install... /usr/bin/install -c
checking whether build environment is sane... yes
checking for gawk... no
checking for mawk... mawk
checking whether make sets $(MAKE)... yes
checking for style of include used by make... GNU
checking for gcc... gcc
checking for C compiler default output file name... a.out
checking whether the C compiler works... yes
checking whether we are cross compiling... no
checking for suffix of executables... 
checking for suffix of object files... o
checking whether we are using the GNU C compiler... yes
checking whether gcc accepts -g... yes
checking for gcc option to accept ANSI C... none needed
checking dependency style of gcc... gcc3
checking for library containing strerror... none required
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking for gcc... (cached) gcc
checking whether we are using the GNU C compiler... (cached) yes
checking whether gcc accepts -g... (cached) yes
checking for gcc option to accept ANSI C... (cached) none needed
checking dependency style of gcc... (cached) gcc3
checking how to run the C preprocessor... gcc -E
checking for egrep... grep -E
checking for ANSI C header files... yes
checking for an ANSI C-conforming const... yes
checking build system type... i686-pc-linux-gnu
checking host system type... i686-pc-linux-gnu
checking for a sed that does not truncate output... /bin/sed
checking for ld used by gcc... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking for /usr/bin/ld option to reload object files... -r
checking for BSD-compatible nm... /usr/bin/nm -B
checking whether ln -s works... yes
checking how to recognise dependent libraries... pass_all
checking for sys/types.h... yes
checking for sys/stat.h... yes
checking for stdlib.h... yes
checking for string.h... yes
checking for memory.h... yes
checking for strings.h... yes
checking for inttypes.h... yes
checking for stdint.h... yes
checking for unistd.h... yes
checking dlfcn.h usability... yes
checking dlfcn.h presence... yes
checking for dlfcn.h... yes
checking for g++... g++
checking whether we are using the GNU C++ compiler... yes
checking whether g++ accepts -g... yes
checking dependency style of g++... gcc3
checking how to run the C++ preprocessor... g++ -E
checking for g77... no
checking for f77... no
checking for xlf... no
checking for frt... no
checking for pgf77... no
checking for fort77... no
checking for fl32... no
checking for af77... no
checking for f90... no
checking for xlf90... no
checking for pgf90... no
checking for epcf90... no
checking for f95... no
checking for fort... no
checking for xlf95... no
checking for ifc... no
checking for efc... no
checking for pgf95... no
checking for lf95... no
checking for gfortran... no
checking whether we are using the GNU Fortran 77 compiler... no
checking whether  accepts -g... no
checking the maximum length of command line arguments... 32768
checking command to parse /usr/bin/nm -B output from gcc object... ok
checking for objdir... .libs
checking for ar... ar
checking for ranlib... ranlib
checking for strip... strip
checking if gcc supports -fno-rtti -fno-exceptions... no
checking for gcc option to produce PIC... -fPIC
checking if gcc PIC flag -fPIC works... yes
checking if gcc static flag -static works... yes
checking if gcc supports -c -o file.o... yes
checking whether the gcc linker (/usr/bin/ld) supports shared libraries... yes
checking whether -lc should be explicitly linked in... no
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
checking whether stripping libraries is possible... yes
checking if libtool supports shared libraries... yes
checking whether to build shared libraries... yes
checking whether to build static libraries... yes
configure: creating libtool
appending configuration tag "CXX" to libtool
checking for ld used by g++... /usr/bin/ld
checking if the linker (/usr/bin/ld) is GNU ld... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for ecore-config... /opt/e17/bin/ecore-config
checking for ecore - version >= 0.9.9... yes
checking for xml2-config... /usr/bin/xml2-config
checking for xml2 - version >= 2.6.13... yes
checking for xslt-config... no
checking for xslt - version >= 1.1.10... no
*** The xslt-config script installed by xslt could not be found
*** If xslt was installed in PREFIX, make sure PREFIX/bin is in
*** your path, or set the XSLT_CONFIG environment variable to the
*** full path to xslt-config.
configure: error: Make sure that xslt-config is in your PATH or that Xslt is correctly installed



*************



OK, But anyway, I did try to login to the E17 and I got the follow msg:

Xsession: unable to launch " opt/e17/bin/enlightenment" X session --- "/opt/e17/bin/enlightenment" not found; falling back to default session.  
<Okay>

****************


I did a search for on the this forum to find out the any essue about XSLT but I can't find nothing about it.

What I did wrong?
Do you have any tip for me?

Thanks !!!

---

### Post by Rui Pais on 2007-01-03
hi,
it's at least the second time i answer that on this now almost 400 post long thread.
Others answer the same, so as a simple exercise...
Go to the top of the page, click on: **search this thread** and type: xslt-config. ;) 
(easy isn't it?)

to your 2nd question, you didn't go till the compilation of "e" package, so you don't have /opt/e17/bin/enlightenment installed (yet) :)

---

### Post by Simimi on 2007-01-23
Hey all. I am working on the installing of e17, from the original script on the first post. I looked through all 40 pages of this thread and did not see my problem, but I found some similar ones. I assume this error is a dependency thing or maybe just because it is not working properly in the CVS.

```
make[2]: Leaving directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/data'
make[1]: Leaving directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/data'
Making all in src
make[1]: Entering directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/src'
make  all-recursive
make[2]: Entering directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/src'
Making all in widgets
make[3]: Entering directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/src/widgets'
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src   -I/opt/e17/include -I../../src/smarts -I../../src/widgets -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -MT libentrance_widgets_la-ew.lo -MD -MP -MF ".deps/libentrance_widgets_la-ew.Tpo" -c -o libentrance_widgets_la-ew.lo `test -f 'ew.c' || echo './'`ew.c; \
	then mv -f ".deps/libentrance_widgets_la-ew.Tpo" ".deps/libentrance_widgets_la-ew.Plo"; else rm -f ".deps/libentrance_widgets_la-ew.Tpo"; exit 1; fi
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DHAVE_CONFIG_H -I. -I. -I../../src   -I/opt/e17/include -I../../src/smarts -I../../src/widgets -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -MT libentrance_widgets_la-ew_dialog.lo -MD -MP -MF ".deps/libentrance_widgets_la-ew_dialog.Tpo" -c -o libentrance_widgets_la-ew_dialog.lo `test -f 'ew_dialog.c' || echo './'`ew_dialog.c; \
	then mv -f ".deps/libentrance_widgets_la-ew_dialog.Tpo" ".deps/libentrance_widgets_la-ew_dialog.Plo"; else rm -f ".deps/libentrance_widgets_la-ew_dialog.Tpo"; exit 1; fi
mkdir .libs
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include -I../../src/smarts -I../../src/widgets -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -MT libentrance_widgets_la-ew_dialog.lo -MD -MP -MF .deps/libentrance_widgets_la-ew_dialog.Tpo -c ew_dialog.c  -fPIC -DPIC -o .libs/libentrance_widgets_la-ew_dialog.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include -I../../src/smarts -I../../src/widgets -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -MT libentrance_widgets_la-ew.lo -MD -MP -MF .deps/libentrance_widgets_la-ew.Tpo -c ew.c  -fPIC -DPIC -o .libs/libentrance_widgets_la-ew.o
In file included from ew_textlist.h:4,
                 from Entrance_Widgets.h:9,
                 from ew_dialog.c:2:
_ew_list.h:14: error: expected specifier-qualifier-list before 'Etk_Tree2_Col'
In file included from ew_textlist.h:4,
                 from Entrance_Widgets.h:9,
                 from ew.c:3:
_ew_list.h:14: error: expected specifier-qualifier-list before 'Etk_Tree2_Col'
make[3]: *** [libentrance_widgets_la-ew.lo] Error 1
make[3]: *** Waiting for unfinished jobs....
make[3]: *** [libentrance_widgets_la-ew_dialog.lo] Error 1
make[3]: Leaving directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/src/widgets'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/citan/e17_cvs/e17/proto/entrance_edit_gui/src'
make: *** [all-recursive] Error 1

```

No idea here... I do not recognize a recursive error...

Any ideas?

Yours, Mimi

---

### Post by Rui Pais on 2007-01-23
hi simimi,
i don't use entrance or any related so you don't know, but maybe it's just a temporarily cvs broke one (note that entrance_edit_gui is on proto... not in main tree where apps tend to be more stable). 

You could skip that one - you probably will never use it anyway... the script try to download a lot of stuff not need, extras, experimental stuff... it's based on morlenxus (it's author) preferences or needs and anyone who use it should adapt it to his/her one needs :)

hth

---

### Post by Simimi on 2007-01-23
Hmm, thanks a lot!  So the proto repo is for things that are very very bleeding edge, and still in the "test" stages, even for CVS stuff?

I'll try to keep excluding things until I get it to compile then, thanks for the help!

---

### Post by Rui Pais on 2007-01-23
> **Simimi said:**
> Hmm, thanks a lot!  So the proto repo is for things that are very very bleeding edge, and still in the "test" stages, even for CVS stuff?

I'll try to keep excluding things until I get it to compile then, thanks for the help!

yes, proto is where the stuff that is yet at very beginning or even only as a prototypes (so the name... i think).

entrance is the replace for gdm/kdm, it's optional and a much less powerful/configurable then gdm/kdm... entrance_gui_edit must be some app to edit the theme and/or background images on entrance. They are not a direct or fundamental part of the desktop environment.

**Just a note (maybe useful to anyone reading this):**
This is an old (unmaintained?) how-to. And in certain points outdated.
when you make the .desktop file at the present it's not:
> Exec=/opt/e17/bin/enlightenment 
**but this:**
> Exec=/opt/e17/bin/enlightenment_start

In order to start for the first time i needed one time (fail to see why!) to reboot my box.
It give me a message saying that /opt/e17/bin/enlightenment_start was not found even when it was on $PATH (](*,))

---

### Post by Rui Pais on 2007-01-27
Hi,
just another small thing i find my self dealing with today... 

One must definitely check the list of apps installed with the script. 
That not only a question of what is unneed but, on the opposite, it will not use all available on cvs server.

e_utils, as an example, is not on the original list of apps and so it's not compiled even if its absent from the skip list. I use a script to make backgrounds/wallpapers that make use of e17setroot and took me a while before i understand why it did exist in my new installation. It's part of e_utils :) 

If someone it's interested in this (set of) app, you have to add it manually to the script list app="..." section. And then do a sudo ./easy_e17.sh --only=e_utils

have fun all.

---

### Post by bajanpoet on 2007-02-07
In my attempt to install enlightenment (e17) I started to do the steps set out in this thread, but after doing the first sudo apt-get... statement, this is the result:

```
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/g/glib1.2/libglib1.2-dev_1.2.10-10.1build1_i386.deb  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
Failed to fetch http://archive.ubuntu.com/ubuntu/pool/main/x/x11proto-fixes/x11proto-fixes-dev_4.0-0.1ubuntu1_all.deb  Error reading from server - read (104 Connection reset by peer) [IP: 195.248.90.38 80]
E: Unable to fetch some archives, maybe run apt-get update or try with --fix-missing?

```

When I tried to run 
```
wget http://omicron.homeip.net/projects/easy_e17/easy_e17.sh
```

this is what I get
```

--22:37:19--  http://omicron.homeip.net/projects/easy_e17/easy_e17.sh
           => `easy_e17.sh'
Resolving omicron.homeip.net... 88.72.195.81
Connecting to omicron.homeip.net|88.72.195.81|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: unspecified [text/html]
easy_e17.sh: Permission denied

```

What is this - and how do I fix it? (Sorry, I'm a complete Newbie to Linux and Englightenment...

---

### Post by MiD-AwE on 2007-03-04
I did everything like it says but when I change sessions into E17, I get message that /etc/opt/e17/bin/enlightenment cannot be found.

How can I fix this?

---

### Post by Rui Pais on 2007-03-05
> **MiD-AwE said:**
> I did everything like it says but when I change sessions into E17, I get message that /etc/opt/e17/bin/enlightenment cannot be found.

How can I fix this?

this instructions are becoming obsolete.
see my post above, [#401]("http://ubuntuforums.org/showthread.php?p=2054941").

---

### Post by Lajexander on 2007-03-25
yay! errors!!

this might be a little long but here goes nothing:

```
---------------------------- Installing applications ---------------------------
- e .......................... ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for E... configure: error: Package requirements (
  evas
  ecore
  ecore-evas
  ecore-config
  ecore-dbus
  ecore-file
  ecore-desktop
  edje
  eet
  embryo
  efreet
) were not met:

No package 'efreet' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables E_CFLAGS
and E_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.
```

btw, what is efreet?

---

### Post by Rui Pais on 2007-03-25
efreet is a new dependency for e. It appeared yesterday.
Morlenxus has not yet update his script.

You can do it by yourself changing the line:
> efl="imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion engrave etk ewl exml enhance"
to:
> efl="imlib2 edb eet evas ecore epeg embryo edje epsilon esmart emotion engrave etk ewl exml enhance efreet"

If you are updating, and not installing, i would advise you to wait one or two days till things stabilize a little.

hth

---

### Post by huwbie on 2007-04-06
Ok the install went fine with the script not a problem.

However im using e17 now and i can't seem to create icons at all, it also seems i dont have e_utils_eapp_edit installed.. any ideas why?

---

### Post by Rui Pais on 2007-04-08
> **huwbie said:**
> Ok the install went fine with the script not a problem.

However im using e17 now and i can't seem to create icons at all, it also seems i dont have e_utils_eapp_edit installed.. any ideas why?

hi,
e17 stop use/support eaps for icons menus for at least a month or two. 
Thats why you can't find e_utils_eap. It's been deprecated. Same for e17setroot, entangle, exige and a few others. 
They are part of the old e_utils. It's still there, at .e17_cvs/e17/apps/e_utils and you still can build them (you may need to add the entry to morlenxus script list...). 

Another thing.
Right now icons stuff are going for a deep changes and most of the things related are broken or incomplete... same for themes (or at least most of the old themes wont work with the new api).

If you want a stable working e17 you must use the 20070323  version. It's the latest Ok.

hth.

---

### Post by Kiwi-Hawk on 2007-04-09
Hi

Thanks this is great,.. jus a wee bug or two but hey easyer than bu hand
Is this realted to cvs or is cause I'm running Mepis 6.5 which is Ubuntu based anyway


--------------------------- Installing libaries (EFL) --------------------------
- imlib2 ..................... ok
- edb ........................ ok
- eet ........................ ok
- evas ....................... ok
- ecore ...................... ok
- efreet ..................... ok
- epeg ....................... ok
- embryo ..................... ok
- edje ....................... ok
- epsilon .................... ok
- esmart ..................... ok
- emotion .................... ok
- engrave .................... ok
- etk ........................ ok
- ewl ........................ ok
- exml ....................... ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EXML... configure: error: Package requirements (
  ecore
  libxml-2.0
  libxslt
) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EXML_CFLAGS
and EXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

was doing so well to,.. LOL teach me to blow my mouth off to my mate saying how easy it is


found my own answer I did a search in snaptic for libxslt and installed the dev all good to go it looks

If I might make a wee suggestion as a passing thought,..  I have had another fall over but fixed the same way,

My thought is to put somit like a mini howto cut and paste the missing file name into synaptic's search and see if they can
find the missing files that provide what they need then rerun the script, this might save a few posts that maybe don't need posting
and will help thy learning curve for some ya think?

this one might have stumped me tho,:No package 'libmpd' found
I did the search and install a couple of libs but still no find it

running updatedb and will run ldconfig -v and see if I can find it 

No good I did fix it:
-------------------------------------------------------------------------------------------------------------------------------------
 e .......................... previously installed
- entrance ................... previously installed
- eclair ..................... previously installed
- evfs ....................... previously installed
- edje_viewer ................ previously installed
- edje_editor ................ previously installed
- elicit ..................... previously installed
- emphasis ................... ERROR!
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for strndup... yes
checking for pthread_create in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EMPHASIS... configure: error: Package requirements (
  ecore >= 0.9.9.022
  ecore-config
  etk >= 0.1.0.002
  enhance >= 0.0.1
  libxml-2.0 >= 2.6.0
  libmpd >= 0.12.0
) were not met:

No package 'libmpd' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMPHASIS_CFLAGS
and EMPHASIS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

Don't know what I'm missing

messy I found the sound and compiled it to get right version

Cheers
Kiwi-Hawk

---

### Post by Rui Pais on 2007-04-09
> **Kiwi-Hawk said:**
> ...
checking for EXML... configure: error: Package requirements (
  ecore
  libxml-2.0
  libxslt
) were not met:

No package 'libxslt' found
...


Try:
```
sudo apt-get install libxslt-dev
```

---

### Post by Kiwi-Hawk on 2007-04-09
Hi this truly stumped me

#
layout_etk_simple.c: In function 'entropy_etk_layout_trackback_show':
#
layout_etk_simple.c:385: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
#
layout_etk_simple.c:385: error: too many arguments to function 'etk_container_remove'
#
layout_etk_simple.c: In function 'entropy_etk_layout_tree_show':
#
layout_etk_simple.c:412: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
#
layout_etk_simple.c:412: error: too many arguments to function 'etk_container_remove'
#
layout_etk_simple.c: In function 'entropy_layout_etk_simple_local_view_set':
#
layout_etk_simple.c:447: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
#
layout_etk_simple.c:447: error: too many arguments to function 'etk_container_remove'
#
make[2]: *** [layout_etk_simple_la-layout_etk_simple.lo] Error 1
#
make[2]: *** Waiting for unfinished jobs....
#
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DCONFIGURED_WITH=\"--prefix=/opt/e17\" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int "-DSELECT_TYPE_ARG234=(fd_set *)" "-DSELECT_TYPE_ARG5=(struct timeval *)" -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_UNISTD_H=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/root/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-entropy_debug.lo -MD -MP -MF .deps/layout_etk_simple_la-entropy_debug.Tpo -c ../../src/entropy_debug.c  -fPIC -DPIC -o .libs/layout_etk_simple_la-entropy_debug.o
#
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DCONFIGURED_WITH=\"--prefix=/opt/e17\" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int "-DSELECT_TYPE_ARG234=(fd_set *)" "-DSELECT_TYPE_ARG5=(struct timeval *)" -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_UNISTD_H=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/root/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-entropy_debug.lo -MD -MP -MF .deps/layout_etk_simple_la-entropy_debug.Tpo -c ../../src/entropy_debug.c -o layout_etk_simple_la-entropy_debug.o >/dev/null 2>&1
#
make[2]: Leaving directory `/root/e17_cvs/e17/proto/entropy/src/plugins'
#
make[1]: *** [all-recursive] Error 1
#
make[1]: Leaving directory `/root/e17_cvs/e17/proto/entropy/src'
#
make: *** [all-recursive] Error 1 

any thoughts please?

Cheers
Kiwi-Hawk

---

### Post by Kiwi-Hawk on 2007-04-09
> **Rui Pais said:**
> Try:
```
sudo apt-get install libxslt-dev
```

thanks for that found that one

---

### Post by Kiwi-Hawk on 2007-04-09
Hi

I have three apps broken now says cant find eet_config and I look back eet is supposedly install but I can't find it can I force a reinstall of it?
entropy, estickies, extrackt

Cheers
Kiwi-Hawk

BTW I guess it'll need the enviroment changed to suit the prefixed install right how I do that

---

### Post by Kiwi-Hawk on 2007-04-09
Hi

Got the crash thing on startup say you access enlightenment directly thats bad
need to know how to edit this to use the luncher they're on about and I guess less three programs we're good to go


-------------------------------------------------------------
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
-----------------------------------------------------------------------

Cheers
Kiwi-Hawk

---

### Post by Rui Pais on 2007-04-09
hi again.

About your questions:

Entropy is broken and i think is not maintained anymore. 
You can use something like xfe, pcmanfm, rox or thunar if you need a light file manager.

Broken things with eet_config are related with recent changes of happy (after 24/03), usually related with edje files that are being dropped (for desktop files). 
You can safety skip them or rollback to a working previous date.

About the launcher for the startup, see my post [#401]("http://ubuntuforums.org/showthread.php?p=2054941") 

hth

---

### Post by Leeniez on 2007-04-09
I have an error with the installation!! (really this is the third but I solve the others):

```
- entropy .................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
creating system_thumbnailer.la
(cd .libs && rm -f system_thumbnailer.la && ln -s ../system_thumbnailer.la system_thumbnailer.la)
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DCONFIGURED_WITH=\"/opt/e17/share/config.site\ /opt/e17/etc/config.site\" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/home/leno/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-layout_etk_simple.lo -MD -MP -MF ".deps/layout_etk_simple_la-layout_etk_simple.Tpo" -c -o layout_etk_simple_la-layout_etk_simple.lo `test -f 'layout_etk_simple.c' || echo './'`layout_etk_simple.c; \
        then mv -f ".deps/layout_etk_simple_la-layout_etk_simple.Tpo" ".deps/layout_etk_simple_la-layout_etk_simple.Plo"; else rm -f ".deps/layout_etk_simple_la-layout_etk_simple.Tpo"; exit 1; fi
gcc -shared  .libs/action_simple_la-entropy_gui.o .libs/action_simple_la-action_simple.o .libs/action_simple_la-entropy_debug.o  -L/opt/e17/lib /opt/e17/lib/libewl.so /opt/e17/lib/libemotion.so /opt/e17/lib/libepsilon.so /opt/e17/lib/libImlib2.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_txt.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -ldl -lz /opt/e17/lib/libecore.so -lssl -lcrypto /opt/e17/lib/libevas.so -lm  -Wl,-soname -Wl,action_simple.so -o .libs/action_simple.so
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" "-DCONFIGURED_WITH=\"/opt/e17/share/config.site /opt/e17/etc/config.site\"" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int "-DSELECT_TYPE_ARG234=(fd_set *)" "-DSELECT_TYPE_ARG5=(struct timeval *)" -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/home/leno/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-layout_etk_simple.lo -MD -MP -MF .deps/layout_etk_simple_la-layout_etk_simple.Tpo -c layout_etk_simple.c  -fPIC -DPIC -o .libs/layout_etk_simple_la-layout_etk_simple.o
layout_etk_simple.c: In function 'entropy_etk_layout_trackback_show':
layout_etk_simple.c:385: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
layout_etk_simple.c:385: error: too many arguments to function 'etk_container_remove'
layout_etk_simple.c: In function 'entropy_etk_layout_tree_show':
layout_etk_simple.c:412: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
layout_etk_simple.c:412: error: too many arguments to function 'etk_container_remove'
layout_etk_simple.c: In function 'entropy_layout_etk_simple_local_view_set':
layout_etk_simple.c:447: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
layout_etk_simple.c:447: error: too many arguments to function 'etk_container_remove'
make[2]: *** [layout_etk_simple_la-layout_etk_simple.lo] Error 1
make[2]: *** Se espera a que terminen otras tareas....
ar cru .libs/action_simple.a  action_simple_la-entropy_gui.o action_simple_la-action_simple.o action_simple_la-entropy_debug.o
ranlib .libs/action_simple.a
creating action_simple.la
(cd .libs && rm -f action_simple.la && ln -s ../action_simple.la action_simple.la)
make[2]: se sale del directorio `/home/leno/e17_cvs/e17/proto/entropy/src/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/leno/e17_cvs/e17/proto/entropy/src'
make: *** [all-recursive] Error 1
--------------------------------------------------------------------------------

```
What can I do? Any idea? (Note that my Ubuntu 6.10 is spanish version, and even I'm spanish heh)

Thanks!

---

### Post by Rui Pais on 2007-04-09
> **Leeniez said:**
> I have an error with the installation!! (really this is the third but I solve the others):

```
- entropy .................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
creating system_thumbnailer.la
(cd .libs && rm -f system_thumbnailer.la && ln -s ../system_thumbnailer.la system_thumbnailer.la)
if /bin/bash ../../libtool --tag=CC --mode=compile gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" -DCONFIGURED_WITH=\"/opt/e17/share/config.site\ /opt/e17/etc/config.site\" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int -DSELECT_TYPE_ARG234=\(fd_set\ \*\) -DSELECT_TYPE_ARG5=\(struct\ timeval\ \*\) -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/home/leno/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-layout_etk_simple.lo -MD -MP -MF ".deps/layout_etk_simple_la-layout_etk_simple.Tpo" -c -o layout_etk_simple_la-layout_etk_simple.lo `test -f 'layout_etk_simple.c' || echo './'`layout_etk_simple.c; \
        then mv -f ".deps/layout_etk_simple_la-layout_etk_simple.Tpo" ".deps/layout_etk_simple_la-layout_etk_simple.Plo"; else rm -f ".deps/layout_etk_simple_la-layout_etk_simple.Tpo"; exit 1; fi
gcc -shared  .libs/action_simple_la-entropy_gui.o .libs/action_simple_la-action_simple.o .libs/action_simple_la-entropy_debug.o  -L/opt/e17/lib /opt/e17/lib/libewl.so /opt/e17/lib/libemotion.so /opt/e17/lib/libepsilon.so /opt/e17/lib/libImlib2.so /opt/e17/lib/libecore_evas.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libedje.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_txt.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -ldl -lz /opt/e17/lib/libecore.so -lssl -lcrypto /opt/e17/lib/libevas.so -lm  -Wl,-soname -Wl,action_simple.so -o .libs/action_simple.so
 gcc -DPACKAGE_NAME=\"\" -DPACKAGE_TARNAME=\"\" -DPACKAGE_VERSION=\"\" -DPACKAGE_STRING=\"\" -DPACKAGE_BUGREPORT=\"\" "-DCONFIGURED_WITH=\"/opt/e17/share/config.site /opt/e17/etc/config.site\"" -DPACKAGE=\"entropy\" -DVERSION=\"0.0.1\" -DSTDC_HEADERS=1 -DHAVE_SYS_TYPES_H=1 -DHAVE_SYS_STAT_H=1 -DHAVE_STDLIB_H=1 -DHAVE_STRING_H=1 -DHAVE_MEMORY_H=1 -DHAVE_STRINGS_H=1 -DHAVE_INTTYPES_H=1 -DHAVE_STDINT_H=1 -DHAVE_UNISTD_H=1 -DHAVE_DLFCN_H=1 -DHAVE_STRUCT_STAT_ST_BLKSIZE=1 -DHAVE_ST_BLKSIZE=1 -DHAVE_STRUCT_STAT_ST_BLOCKS=1 -DHAVE_ST_BLOCKS=1 -DRETSIGTYPE=void -DHAVE_LIMITS_H=1 -DTIME_WITH_SYS_TIME=1 -DHAVE_LOCALTIME_R=1 -DHAVE_NL_LANGINFO=1 -DHAVE_MEMSET=1 -DHAVE_MEMMOVE=1 -DHAVE_STRCASECMP=1 -DHAVE_STRNCASECMP=1 -DHAVE_STRTOL=1 -DHAVE_STRSTR=1 -DHAVE_STRRCHR=1 -DHAVE_STRCHR=1 -DHAVE_STRDUP=1 -DHAVE_SELECT=1 -DHAVE_FTELLO=1 -DHAVE_FSEEKO=1 -DHAVE_STRTOUL=1 -DHAVE_STRTOULL=1 -DHAVE_STATFS=1 -DHAVE_STATVFS=1 -DHAVE_SYS_SELECT_H=1 -DHAVE_SYS_SOCKET_H=1 -DSELECT_TYPE_ARG1=int "-DSELECT_TYPE_ARG234=(fd_set *)" "-DSELECT_TYPE_ARG5=(struct timeval *)" -DLSTAT_FOLLOWS_SLASHED_SYMLINK=1 -DHAVE_STDLIB_H=1 -DHAVE_MALLOC=1 -DHAVE_FORK=1 -DHAVE_VFORK=1 -DHAVE_WORKING_VFORK=1 -DHAVE_WORKING_FORK=1 -DHAVE_STDLIB_H=1 -DHAVE_SYS_TIME_H=1 -DHAVE_UNISTD_H=1 -DHAVE_ALARM=1 -DHAVE_DIRENT_H=1 -DHAVE_LANGINFO_CODESET=1 -DHAVE_WORDEXP=1 -DHAVE_ECORE=1 -DHAVE_EWL=1 -DHAVE_ETK=1 -DHAVE_EVFS=1 -DHAVE_IMLIB2=1 -DHAVE_LIBPNG=1 -DPACKAGE_PREFIX=\"/opt/e17\" -DPACKAGE_LOCALE_DIR=\"/opt/e17//locale\" -DPACKAGE_DATA_DIR=\"/opt/e17/share/entropy\" -DPACKAGE_SOURCE_DIR=\"/home/leno/e17_cvs/e17/proto/entropy\" -I. -I. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -D_FILE_OFFSET_BITS=64 -Wall -MT layout_etk_simple_la-layout_etk_simple.lo -MD -MP -MF .deps/layout_etk_simple_la-layout_etk_simple.Tpo -c layout_etk_simple.c  -fPIC -DPIC -o .libs/layout_etk_simple_la-layout_etk_simple.o
layout_etk_simple.c: In function 'entropy_etk_layout_trackback_show':
layout_etk_simple.c:385: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
layout_etk_simple.c:385: error: too many arguments to function 'etk_container_remove'
layout_etk_simple.c: In function 'entropy_etk_layout_tree_show':
layout_etk_simple.c:412: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
layout_etk_simple.c:412: error: too many arguments to function 'etk_container_remove'
layout_etk_simple.c: In function 'entropy_layout_etk_simple_local_view_set':
layout_etk_simple.c:447: warning: passing argument 1 of 'etk_container_remove' from incompatible pointer type
layout_etk_simple.c:447: error: too many arguments to function 'etk_container_remove'
make[2]: *** [layout_etk_simple_la-layout_etk_simple.lo] Error 1
make[2]: *** Se espera a que terminen otras tareas....
ar cru .libs/action_simple.a  action_simple_la-entropy_gui.o action_simple_la-action_simple.o action_simple_la-entropy_debug.o
ranlib .libs/action_simple.a
creating action_simple.la
(cd .libs && rm -f action_simple.la && ln -s ../action_simple.la action_simple.la)
make[2]: se sale del directorio `/home/leno/e17_cvs/e17/proto/entropy/src/plugins'
make[1]: *** [all-recursive] Error 1
make[1]: se sale del directorio `/home/leno/e17_cvs/e17/proto/entropy/src'
make: *** [all-recursive] Error 1
--------------------------------------------------------------------------------

```
What can I do? Any idea? (Note that my Ubuntu 6.10 is spanish version, and even I'm spanish heh)

Thanks!

hi, see my [previous post]("http://ubuntuforums.org/showpost.php?p=2426134&postcount=416").

---

### Post by Kiwi-Hawk on 2007-04-09
Hi

heres a thought for those start E17 via kdm

------------------------------------------------------------
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
-----------------------------------------------------------------------

needs to be as follows"
---------------------------------------------------------------------
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment_start
Icon=
Type=Application
-----------------------------------------------------------------------
or E will crash at startup it does not like being started direct

Cheers
Kiwi-Hawk

---

### Post by stylesuxx on 2007-04-10
Hi!
First I want to say that this thread really helped allot while installing E17 :-)
Well i just started my first E17 Session and i fell in love.


BUT

While installing with this script i had to skip some stuff:
[LIST]
[*]exhibit
[*]extrackt
[*]emphasis
[*]engage
[*]emu
[*]language
[*]moon
[*]taskbar
[/LIST]
I just wanted to ask what`s going on with this packages, are they not maintained anymore?

regards Chris

---

### Post by stylesuxx on 2007-04-11
Ok, just installed the rest of the stuff, the problem was, that i had automake1.10 installed, with 1.9 it worked like a charm :-)

---

### Post by dOkTOR_dO on 2007-04-13
this error:

```

- exml ....................... ok          
- enhance .................... ok          
--------------------------------------------------------------------------------

---------------------------- Installing applications ---------------------------
- e .......................... ok          
- entrance ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include    -I/opt/e17/include  -g -O2 -Wall -MT spawner.o -MD -MP -MF ".deps/spawner.Tpo" -c -o spawner.o spawner.c; \
        then mv -f ".deps/spawner.Tpo" ".deps/spawner.Po"; else rm -f ".deps/spawner.Tpo"; exit 1; fi
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include    -I/opt/e17/include  -g -O2 -Wall -MT entranced_display.o -MD -MP -MF ".deps/entranced_display.Tpo" -c -o entranced_display.o entranced_display.c; \
        then mv -f ".deps/entranced_display.Tpo" ".deps/entranced_display.Po"; else rm -f ".deps/entranced_display.Tpo"; exit 1; fi
spawner.c:443: warning: ‘_cb_atexit’ defined but not used
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2 -Wall  -L/opt/e17/lib -o entranced  auth.o ipc.o md5.o util.o spawner.o entranced_display.o -lXau -L/opt/e17/lib -lecore_evas -levas -lecore_x -lecore_txt -lecore_ipc -lecore_con -lecore_config -leet -lecore_desktop -lecore_file -lecore -lcurl -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -ldl -lssl -lcrypto -lz   -lcrypt
mkdir .libs
gcc -g -O2 -Wall -o entranced auth.o ipc.o md5.o util.o spawner.o entranced_display.o  -L/opt/e17/lib -lXau /opt/e17/lib/libecore_evas.so /opt/e17/lib/libevas.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libeet.so /opt/e17/lib/libecore_desktop.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -ldl -lssl -lcrypto -lz -lcrypt
make[3]: Leaving directory `/home/dok/e17_cvs/e17/apps/entrance/src/daemon'
Making all in config
make[3]: Entering directory `/home/dok/e17_cvs/e17/apps/entrance/src/config'
if gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include   -I./../lib  -I/opt/e17/include -I/opt/e17/include   -g -O2 -Wall -MT entrance_edit-entrance_edit_main.o -MD -MP -MF ".deps/entrance_edit-entrance_edit_main.Tpo" -c -o entrance_edit-entrance_edit_main.o `test -f 'entrance_edit_main.c' || echo './'`entrance_edit_main.c; \
        then mv -f ".deps/entrance_edit-entrance_edit_main.Tpo" ".deps/entrance_edit-entrance_edit_main.Po"; else rm -f ".deps/entrance_edit-entrance_edit_main.Tpo"; exit 1; fi
/bin/bash ../../libtool --tag=CC --mode=link gcc  -g -O2 -Wall  -L/opt/e17/lib -o entrance_edit -L../lib entrance_edit-entrance_edit_main.o -L/opt/e17/lib -lecore_evas -levas -lecore_x -lecore_txt -lecore_ipc -lecore_con -lecore_config -leet -lecore_desktop -lecore_file -lecore -lcurl -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv -lidn -ldl -lssl -lcrypto -lz   -lentrance_edit -lcrypt
mkdir .libs
gcc -g -O2 -Wall -o .libs/entrance_edit entrance_edit-entrance_edit_main.o  -L/opt/e17/lib -L/home/dok/e17_cvs/e17/apps/entrance/src/lib /opt/e17/lib/libecore_evas.so /opt/e17/lib/libevas.so /opt/e17/lib/libecore_x.so /opt/e17/lib/libecore_txt.so /opt/e17/lib/libecore_ipc.so /opt/e17/lib/libecore_con.so /opt/e17/lib/libecore_config.so /opt/e17/lib/libeet.so /opt/e17/lib/libecore_desktop.so /opt/e17/lib/libecore_file.so /opt/e17/lib/libecore.so /usr/lib/libcurl.so -lgssapi_krb5 -lkrb5 -lk5crypto -lkrb5support -lcom_err -lresolv /usr/lib/libidn.so -ldl -lssl -lcrypto -lz /home/dok/e17_cvs/e17/apps/entrance/src/lib/.libs/libentrance_edit.so -lcrypt
built in linker script:10 nonconstant expression for fill value
collect2: ld returned 1 exit status
make[3]: *** [entrance_edit] Error 1
make[3]: Leaving directory `/home/dok/e17_cvs/e17/apps/entrance/src/config'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/dok/e17_cvs/e17/apps/entrance/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/dok/e17_cvs/e17/apps/entrance/src'
make: *** [all-recursive] Error 1


```
any solution?:confused:

---

### Post by worldwithoutgurus on 2007-04-14
Yes.
Don't use entrance.
Don't even think about using entrance.

Or use Elive... :D

---

### Post by Anagonda on 2007-04-14
I have used E16 for a while now, over a year atleast. I like it alot. So I have tried E17 few times. 6-12 months ago I tried E17 and then it was so full of bugs I couldnt use it. Crashed once in every hour etc. I had once before tried E17 and then it was a big thing if I got it even started before it crashed.

Last night I build it again from cvs with this threads script(last time I did it with this script and worked fine). I had to install 3 new packages with apt-get, just googled when got a error that script can't find something. So I could find the three missing packages and it did go fine. Last time I did the install with this script I needed to find about 10 packages.
I skipped evfs,entropy,engage and bling. I don't need them so it was a easy solution when I got an error...

But the biggest thing is that the E17 haven't crashed once in about 4 hours. And this is almoust as fast as E16! 
Only thing that isn't so fine is the "loading of wallpaper" when changing desktop. I have a different wallpaper on each desktop. This problem is more(or I think so) because of my hardware. So slow (GF6600) graphics card that it needs to be loaded. But ofcourse if I use only one wallpaper I don't get this loading thing.
Ok, got a another thing... There just isn't any nice themes for E17 yet. get-e.org has four? And thats about all. Or maybe I haven't found any nice sites.

The best thing (still with enlightenment as with E16) that theese are much faster than gnome or kde. And I like that my friends can't use my computer(winxp geeks). Maybe this E17 is easier to use because of the icons I have set on the bar...

---

### Post by gauteh on 2007-04-15
in case cvs fails to checkout, try to login first:

```
cvs -d:pserver:anoncvs@anoncvs.enlightenment.org:/var/cvs/e login
```

---

### Post by gauteh on 2007-04-17
and you need: libxslt1-dev for **exml**

```
sudo apt-get install libxslt1-dev
```

---

### Post by gauteh on 2007-04-17
not to speak about: 

libmpd0
libmpd-dev

for **emphasis**

---

### Post by john_spiral on 2007-04-17
Hi,

Is the HOWTO on the first page complete or do I need to make any adjustments?

I see it was last edited on:

August 21st, 2006 at 09:54 AM

John

---

### Post by gauteh on 2007-04-17
and put enlightenment_start in the xsessions e17.desktop file

---

### Post by gauteh on 2007-04-17
> **john_spiral said:**
> Hi,

Is the HOWTO on the first page complete or do I need to make any adjustments?

I see it was last edited on:

August 21st, 2006 at 09:54 AM

John

with the latest posts from me you see  here plus skipping: exhibit,extrackt,engage,moon because of a bug in the configure scripts it works for me.

---

### Post by foxy123 on 2007-05-11
I've got no applications in the Application menu. How to get them there?

---

### Post by honeydew on 2007-05-11
try typing in console


e17genmenu

---

### Post by foxy123 on 2007-05-12
> **honeydew said:**
> try typing in console


e17genmenu

I do not think that e17genmenu works anymore. E17 now uses .desktop files. In any case I do not have e17genmenu.

I read that I need to install xdg-menu and xdg-utils, what I did but there is some bug there, so I do not have any apps :(

---

### Post by Rui Pais on 2007-05-12
> **foxy123 said:**
> I do not think that e17genmenu works anymore. E17 now uses .desktop files. In any case I do not have e17genmenu.

I read that I need to install xdg-menu and xdg-utils, what I did but there is some bug there, so I do not have any apps :(

yes, you are right. e17genmenu is obsolete a long time ago (it was a very buggy hack anyway).

e17 now uses desktop files. They are not so easily manageable :(. 
[Here]("http://wiki.enlightenment.org/index.php/E17_and_Efreet") is a link to some useful reference.

You can generate an Gnome like menu by moving your .e/e/ folder to .e/e_BAK/ and then start e17.

Or copying .desktop files from /usr/share/applications to ~/.e/e/applications/all and editing ~/.e/e/applications/bar/default/.order manually. 

hth

---

### Post by foxy123 on 2007-05-12
oh, thanks. I had to install also a package called just 'menu' and it works now. 

Another question: how do people manage without systray? engage is obsolete and itask is buggy. What about apps, which usually sit in the system tray like gaim?

---

### Post by Rui Pais on 2007-05-12
> **foxy123 said:**
> oh, thanks. I had to install also a package called just 'menu' and it works now. 

Another question: how do people manage without systray? engage is obsolete and itask is buggy. What about apps, which usually sit in the system tray like gaim?

well, in my case i don't have one or the need for it. So i can't talk for my experience... but usually people use some DE independent systray manager, like trayer (on repos) or stalonetray ([check here]("http://stalonetray.sourceforge.net/")).

---

### Post by bestial on 2007-05-12
Is there any easy way to uninstall EVERYTHING this howto installed? Everything went wrong, and I tried to install e17 the way I hade it before I updated to fiesty, but then I couldn't click on anything.

So... please, a simple line to undo this whole hellish thing? :) Or should I just to a new clean install of fiesty?

---

### Post by Rui Pais on 2007-05-13
> **bestial said:**
> Is there any easy way to uninstall EVERYTHING this howto installed? Everything went wrong, and I tried to install e17 the way I hade it before I updated to fiesty, but then I couldn't click on anything.

So... please, a simple line to undo this whole hellish thing? :) Or should I just to a new clean install of fiesty?

"Hellish"? damn, you deserve the hell for the blafesmy ;)

Anyway simple. If you haven't change default paths it's just:
```
sudo rm -rf /opt/e17 ~/e17_cvs ~/.e /tmp/easy_e17 /tmp/enlightenment* 
```
:)

---

### Post by bestial on 2007-05-13
> **Rui Pais said:**
> "Hellish"? damn, you deserve the hell for the blafesmy ;)

Anyway simple. If you haven't change default paths it's just:
```
sudo rm -rf /opt/e17 ~/e17_cvs
```
:)

Hah, that's pretty obvious, but I'm not always sure if everything will be removed. But thanks!

And I guess that this howto is awesome, I was just som tired so I removed everything. Cause my computer just shutted down during the install (or maybe the install did that? I didn't see). And when I tried to start E17 it complained about X-sessions (I think) and turned back into Gnome.

---

### Post by Rui Pais on 2007-05-13
> **bestial said:**
> Hah, that's pretty obvious, but I'm not always sure if everything will be removed. But thanks!
yes, one of the advantages of this method is that it installs everything on opt, not mixing alpha stuff with your system, and make backups or clean ups very easy.
btw i forget to a full clean you need to remove too from your home .e/ folder and check /tmp/ for  any temporary stuff that may be there from install process. (i will edit my previous post)

> 
And I guess that this howto is awesome, I was just som tired so I removed everything. Cause my computer just shutted down during the install (or maybe the install did that? I didn't see). And when I tried to start E17 it complained about X-sessions (I think) and turned back into Gnome.

i wonder if you followed the how-to exactly or if you have done the changes need for the new starter mentioned early here. These days you need: Exec=/opt/e17/bin/enlightenment_start, and not what is said on 1st. post.

Anyway if your computer shut down during compilation/install maybe rm /opt/e17 and reinstall again would be a good idea (no need to rm ~/e17_cvs in this case) or at least run easy_e17 again to see if it says everything is done it or skipped.

---

### Post by bestial on 2007-05-13
> i wonder if you followed the how-to exactly or if you have done the changes need for the new starter mentioned early here. These days you need: Exec=/opt/e17/bin/enlightenment_start, and not what is said on 1st. post.

Anyway if your computer shut down during compilation/install maybe rm /opt/e17 and reinstall again would be a good idea (no need to rm ~/e17_cvs in this case) or at least run easy_e17 again to see if it says everything is done it or skipped.

Ah, that could've been the problem, cause I did everything from the 1st post. But now everything is deleted so to just run easy_e17 wouldn't show me anything I guess. 

But maybe I should give it a try, cause the apt-get install e17 just gets crappier and crappier for every time I upgrade Ubuntu. :)

---

### Post by Rui Pais on 2007-05-13
> **bestial said:**
> Ah, that could've been the problem, cause I did everything from the 1st post. But now everything is deleted so to just run easy_e17 wouldn't show me anything I guess. 

But maybe I should give it a try, cause the apt-get install e17 just gets crappier and crappier for every time I upgrade Ubuntu. :)

Well, thats a boring problem... the 1st post is outdated in several points. The person who made it stop updated for long...

for me e17 (an alpha) product as been very stable (more stable then the edgy gnome, btw) the only issues are related with the endless and sudden  changes of APIsi introduced constantly and the move for .desktop instead of .eap. 
I decided to stay for a while on the 20070323 version, since it's very stable and i can edit my menu as i used to...

Anyway, maybe you wanted to check the e17 version precompiled and  save the trouble of do it yourself.
[Here a thread on how-to do it]("http://ubuntuforums.org/showthread.php?t=319336").

---

### Post by bestial on 2007-05-13
It's starting to come together again, it's just that everytime I update and installs e17 again new problems come forth and old ones disappear. It's pretty nagging. 

.order for favourites doesn't work anymore (don't ask me why) but the application-apt does the trick anyway.. but, I want what I'm used to! :)

EDIT: And that's the howto I always use, I only wanted to try something different this time.. but I ended up with that one again.

---

### Post by raul_ on 2007-05-17
Sorry, I d'idnt go through all the thread. I suppose that updating is just running the script again, since it downloads everything from the cvs repository...right? Like, you guys commit a change, and when I run the script again, that change will be updated?

---

### Post by Rui Pais on 2007-05-17
> **raul_ said:**
> Sorry, I d'idnt go through all the thread. I suppose that updating is just running the script again, since it downloads everything from the cvs repository...right? Like, you guys commit a change, and when I run the script again, that change will be updated?

to update (without a full reinstall) just run it passing --update or use -u flag:
```
sudo ./easy_e17.sh -u
``` 
it will download all changes committed and compile/install only what needs to be upgraded :)

---

### Post by raul_ on 2007-05-17
```
- engrave .................... ok          
- etk ........................ ok          
- ewl ........................ ok          
- exml ....................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EXML... configure: error: Package requirements (
  ecore
  libxml-2.0
  libxslt
) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EXML_CFLAGS
and EXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/exml.log'!

```

ups... :rolleyes:

---

### Post by Rui Pais on 2007-05-18
that issue is asked once in any page and answered one in each page of this thread.

```
sudo apt-get install libxslt1-dev
```

i wish 1 st post was updated...

---

### Post by foxy123 on 2007-05-18
> **raul_ said:**
> ```
- engrave .................... ok          
- etk ........................ ok          
- ewl ........................ ok          
- exml ....................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EXML... configure: error: [B][COLOR="Red"]Package requirements (
  ecore
  libxml-2.0
  libxslt
) were not met:

No package 'libxslt' found
[/COLOR][/B]
Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EXML_CFLAGS
and EXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/exml.log'!

```

ups... :rolleyes:

it is quite clear from the error you had (see above). And usually compiling errors refer to dev packages.

---

### Post by raul_ on 2007-05-18
I know, it's just another thing to add in the dependencies

---

### Post by foxy123 on 2007-05-25
For last few days I've got this error:
```
M apps/e/po/bg.po
M apps/e/po/ca.po
C apps/e/po/de.po
M apps/e/po/eo.po
M apps/e/po/fr.po
M apps/e/po/hu.po
C apps/e/po/it.po
M apps/e/po/ja.po
M apps/e/po/ko.po
M apps/e/po/pt_BR.po
M apps/e/po/ru.po
M apps/e/po/sl.po
FAILED! Next attempt 6 in 30 seconds
```

---

### Post by Rui Pais on 2007-05-25
if you have the latest version of the script, try run it with -f lag (--fix-cvs-conflicts)

or manually remove apps/e/po

---

### Post by ark on 2007-06-01
i got this error:


--------------------------- Installing libaries (EFL) --------------------------
- imlib2 ..................... ok          
- edb ........................ ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- epeg ....................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... ok          
- emotion .................... ok          
- engrave .................... ok          
- etk ........................ ok          
- ewl ........................ ok          
- exml ....................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EXML... configure: error: Package requirements (
  ecore
  libxml-2.0
  libxslt
) were not met:

No package 'libxslt' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EXML_CFLAGS
and EXML_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.


----------------edit------------------

nvm , i found the answer

---

### Post by bricke on 2007-07-02
Hi, I've got some problem using easy_e17.sh script.
I've already installed e17 from cvs, but now I've formatted my HD and so...

Here is the log
```

checking for struct stat.st_blocks... yes
checking for statfs... yes
before test, samba_includes: 
checking libsmbclient.h usability... no
checking libsmbclient.h presence... no
checking for libsmbclient.h... no
have_samba_includes: no
checking for Samba 3.0 libraries... no
checking for xml2-config... /usr/bin/xml2-config
checking for xml2 - version >= 2.3.10... yes
checking for perl... /usr/bin/perl
checking for ecore-config... no
ecore-config  is not in your $PATH. Please ensure it is.
Read the manual page for you shell as to how to extend your path.
configure: error: Cannot find ecore-config

```

But ecore is installed!! The script install ecore at the beginning!!
I use the script with no module skip, and emotion, eclair install without any problems.

I've search in the web for this problem but i cannot find anything useful.

Have you any ideas?

Sorry for my english

---

### Post by Rui Pais on 2007-07-02
> **bricke said:**
> Hi, I've got some problem using easy_e17.sh script.
I've already installed e17 from cvs, but now I've formatted my HD and so...

...

But ecore is installed!! The script install ecore at the beginning!!
I use the script with no module skip, and emotion, eclair install without any problems.

Hi,
usually that means that its looking for ecore on the wrong place.

Do you still have you old e17/ on /opt/? Or do you use an cvs tree previously installed?

Try:
```
sudo rm -rf /opt/e17
sudo mv $HOME/e17_cvs $HOME/e17_cvs_OLD
sudo rm -rf /tmp/easy_e17*
```

and redo the easy_e17 -i to see if it works.

---

### Post by bricke on 2007-07-03
Ok I'll try it.

But I remenber that I  cancelled all things related to old e17 installation...

...No, the same problem...
```

---------------------------- Installing applications ---------------------------
- e .......................... ok          
- entrance ................... ok          
- eclair ..................... ok          
- evfs ....................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether byte ordering is bigendian... no
checking for struct stat.st_blksize... yes
checking for struct stat.st_blocks... yes
checking for statfs... yes
before test, samba_includes: 
checking libsmbclient.h usability... no
checking libsmbclient.h presence... no
checking for libsmbclient.h... no
have_samba_includes: no
checking for Samba 3.0 libraries... no
checking for xml2-config... /usr/bin/xml2-config
checking for xml2 - version >= 2.3.10... yes
checking for perl... /usr/bin/perl
checking for ecore-config... no
ecore-config  is not in your $PATH. Please ensure it is.
Read the manual page for you shell as to how to extend your path.
configure: error: Cannot find ecore-config
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/evfs.log'!

```

Later I'll try to search if there is some old deb package of E17.

Thanks

---

### Post by PuppyFromHell on 2007-07-03
> **bricke said:**
> Ok I'll try it.

But I remenber that I  cancelled all things related to old e17 installation...

...No, the same problem...
```

---------------------------- Installing applications ---------------------------
- e .......................... ok          
- entrance ................... ok          
- eclair ..................... ok          
- evfs ....................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking for g++ option to produce PIC... -fPIC
checking if g++ PIC flag -fPIC works... yes
checking if g++ static flag -static works... yes
checking if g++ supports -c -o file.o... yes
checking whether the g++ linker (/usr/bin/ld) supports shared libraries... yes
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking whether byte ordering is bigendian... no
checking for struct stat.st_blksize... yes
checking for struct stat.st_blocks... yes
checking for statfs... yes
before test, samba_includes: 
checking libsmbclient.h usability... no
checking libsmbclient.h presence... no
checking for libsmbclient.h... no
have_samba_includes: no
checking for Samba 3.0 libraries... no
checking for xml2-config... /usr/bin/xml2-config
checking for xml2 - version >= 2.3.10... yes
checking for perl... /usr/bin/perl
checking for ecore-config... no
ecore-config  is not in your $PATH. Please ensure it is.
Read the manual page for you shell as to how to extend your path.
configure: error: Cannot find ecore-config
--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/evfs.log'!

```

Later I'll try to search if there is some old deb package of E17.

Thanks

I've got the same problem.

---

### Post by bricke on 2007-07-04
Maybe in this moment the cvs has some problem?

---

### Post by Rui Pais on 2007-07-04
> **bricke said:**
> Maybe in this moment the cvs has some problem?

I've been upgrade daily and find no problems... i have done a clean install 2 or 3 days ago, with Arch Linux, i run it ok too.

Have you done already the step of adding /opt/e17/bin to your /etc/environment?
If not try to add, then redo:```

sudo rm -rf /opt/e17
sudo mv $HOME/e17_cvs $HOME/e17_cvs_OLD
sudo rm -rf /tmp/easy_e17*
```

then run too:
```
sudo ldconfig
```

and then try again the installation from the beginning.

Best of luck.

---

### Post by acoc on 2007-07-04
Ecore-config is no longer used.  The packages need to be updated that require it.  Using the easy_e17 script you can skip these apps by using the --skip=<app> option.

If you are inclined you can search around the cvsview ([http://e.kevb.net/cgi-bin/viewvc.cgi/](http://e.kevb.net/cgi-bin/viewvc.cgi/)) and find the authors and ask them to update their projects.  None of the apps that need ecore-config are required to use e17.

evfs and entropy are involved it an addon file manager (besides the default one)
entrance_edit_gui has been dead for about 6 months and was never maintained by the entrance developer
engage is temporarily out of commission due to a change in the way e stores menus 

John

---

### Post by PuppyFromHell on 2007-07-04
Now I'm getting this error:
```
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/data/etc'
Making all in icons
make[3]: Entering directory `/home/dw/e17_cvs/e17/apps/e/data/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/data/icons'
make[3]: Entering directory `/home/dw/e17_cvs/e17/apps/e/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/data'
make[2]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/data'
Making all in doc
make[2]: Entering directory `/home/dw/e17_cvs/e17/apps/e/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/doc'
Making all in po
make[2]: Entering directory `/home/dw/e17_cvs/e17/apps/e/po'
make enlightenment.pot-update
make[3]: Entering directory `/home/dw/e17_cvs/e17/apps/e/po'
make[3]: *** No rule to make target `../src/bin/e_int_config_wallpaper.c', needed by `enlightenment.pot-update'.  Stop.
make[3]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/po'
make[2]: *** [enlightenment.pot] Error 2
make[2]: Leaving directory `/home/dw/e17_cvs/e17/apps/e/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/dw/e17_cvs/e17/apps/e'
make: *** [all] Error 2

```
and it stops at "Installing Applications: e-ERROR"

---

### Post by Rui Pais on 2007-07-05
hi. 
[COLOR="Gray"]Bad luck :(
cvs tree is broken on last few hours. Seems that wallpaper configuration will be turn into an internal module...[/COLOR]

[COLOR="Blue"]
THIS GIVES e17 WITH ALL THEMES WORKING:[/COLOR]

(I'll keep this for future reference... )
Well you got 2 ways of deal with that. Either you clean all and install the yesterday tree, or you keep what you have and just install e code from yesterday (and you got no GUI for configure wallpaper until they fix it).

Just do: 
(i'll assume you have you e17_cvs on defaults path, change it for your case if you have change this)

CLEAN INSTALL OF 2007/07/04:
```
cd e17_cvs/
mv e17 e17_20070705
sudo cvs -z3 -d :pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e co -D 20070704 e17
sudo rm -rf /opt/e17 /rmp/easy_e17

```

Then go back to where you have easy_e17.sh and do:
```
sudo ./easy_e17.sh --skip-cvsupdate -i
```

[COLOR="Blue"]The above gives the last stable, all themes working, e17.[/COLOR]

---

### Post by bricke on 2007-07-05
Ok i'll try this out

---

### Post by Rui Pais on 2007-07-05
ok 
e_int_config_wallpaper.c issue on cvs tree it's fixed:
[http://cia.vc/stats/project/e](http://cia.vc/stats/project/e) ([enlightenment.pot-update]("http://cia.vc/stats/project/e/.message/db44dc"))
:)

---

### Post by PuppyFromHell on 2007-07-08
Yay everything works now!
I just had to skip some stuff.  I'm really impressed with the invisible shelf style now, When I tried e17 before it was buggy.

---

### Post by PuppyFromHell on 2007-07-09
When I tried to change themes to one I downloaded from edevelop.org all of the menu entries disappeared.  I don't know why and they all worked on my other comp but  Ithink I got e17 from the repos on that one.

---

### Post by Rui Pais on 2007-07-10
> **PuppyFromHell said:**
> When I tried to change themes to one I downloaded from edevelop.org all of the menu entries disappeared.  I don't know why and they all worked on my other comp but  Ithink I got e17 from the repos on that one.

Another change of API.
All themes, except default, are borked since 05 of July.
I would, for now, stay on day 4, where at least everything seems to work. 
And only update when section themes of get-e.org has new versions of thems.

To roll back to day see my previous post [#461]("http://ubuntuforums.org/showpost.php?p=2965800&postcount=461").

---

### Post by adil_uk on 2007-07-12
Guys every time the script easy_e17.sh  try to compile esmart I get this error any idea why this is happening?

Making all in esmart_thumb
make[4]: Entering directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib/esmart_thumb'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib/esmart_thumb'
Making all in esmart_trans_x11
make[4]: Entering directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib/esmart_trans_x11'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib/esmart_trans_x11'
Making all in esmart_resize
make[4]: Entering directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib/esmart_resize'
make[4]: Nothing to be done for `all'.
make[4]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib/esmart_resize'
make[4]: Entering directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib'
make[4]: Nothing to be done for `all-am'.
make[4]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib'
make[3]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src/lib'
Making all in bin
make[3]: Entering directory `/home/adil/e17_cvs/e17/libs/esmart/src/bin'
make[3]: *** No rule to make target `../../src/lib/esmart_file_dialog/libesmart_file_dialog.la', needed by `esmart_file_dialog_test'.  Stop.
make[3]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src/bin'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src'
make[1]: *** [all] Error 2
make[1]: Leaving directory `/home/adil/e17_cvs/e17/libs/esmart/src'
make: *** [all-recursive] Error 1
--------------------------------------------------------------------------------

thanks

---

### Post by Rui Pais on 2007-07-12
Hi,
They are making changes on e17 API again... those "** No rule to make target `something_file_dialog need" has neen pretty frequent lately. 
I wouldn't trust cvs tree for some days (and probably resources like themes would take longer to get up-to-date by they devs).

You can try to delete your cvs tree (i find that some times update seems not made correctly to some config files...) and try again, maybe waiting some hours to see if problem is solved.

You can check development and changes here:
[http://cia.vc/stats/project/e](http://cia.vc/stats/project/e)

Or you can get the 20070704 version that it's very stable and had all themes on get-e.org working.

---

### Post by adil_uk on 2007-07-12
Hi

I thought it was a missing library that caused this error, but anyway thanks for the reply.

---

### Post by Rui Pais on 2007-07-12
> **adil_uk said:**
> Hi

I thought it was a missing library that caused this error, but anyway thanks for the reply.

> 
make[3]: *** No rule to make target `../../src/lib/esmart_file_dialog/libesmart_file_dialog.la', needed by `esmart_file_dialog_test'. Stop.
well it seems that make couldn't find how to make that lib. No rule on some POTFILES.in file.

But if you really want try the latest up to the last minutes version, try to remove e17_cvs and restart again. As i said it happen to a few days ago that for some reason one of the POTFILES failed to be updated (that time for wallpaper_config rule i think, that was available and on-line). I downloaded manually and compare with the file in my cvs tree after run the script with -u flag and the differences was not merged... don't know why... maybe it was the case. 

Btw, with the recent API only 3 themes seems to work.

---

### Post by adil_uk on 2007-07-12
Hi

I have deleted the the e17_cvs and started fresh download but the problem still seems to be there. I do believe its to do with the cvstree and certain update are failing.

---

### Post by Rui Pais on 2007-07-12
> **adil_uk said:**
> Hi

I have deleted the the e17_cvs and started fresh download but the problem still seems to be there. I do believe its to do with the cvstree and certain update are failing.

hi, if you deleted your cvs_tree and run the easy17.sh script it must get it a fresh a correct cvs tree. Thats a bug or an incomplete change on code. Thats all. It's been very common on last few days.

As i said there is no real advantage in going to some environment that is going through internal changes. 
Check [my post above]("http://ubuntuforums.org/showpost.php?p=2965800&postcount=461") to install the stable from 4 of July.



*edit:*
seems to be solved ([cvs report]("http://cia.vc/stats/project/e/.message/de20ff"))

---

### Post by PuppyFromHell on 2007-07-22
Okay I was trying to decompile the Blue_Sky_Tree.edj file to get at the actual picture inside but when I tried to using edje_decc it gave me this
```

Output Image: Blue_Sky_Tree/base.png
ERROR: cannot write file Blue_Sky_Tree/base.png. Perhaps missing JPEG or PNG saver modules for Evas.

```
so yeah I'm thinking something went wrong while I was installing it.

---

### Post by aGit on 2007-07-23
hi

I did everything said in the first post, the how-to, everything went well, apart from me geting a EXML error in the scripting part, what does that mean?

also, when i logged off and chose the e17 to login on, it said that /opt/e17/bin/englightenment not found...that cant be right? help would be much appriciated. Thanks.

ps. i'm running edgy on a Via epia ms10000e, 1ghz cpu, i read from the interwebz that enlightenment should work on older and less powerfull setups too, hope it runs with mine. need something to replace beryl as it i cannot run with this and i like my eyecandy.

-aGit

---

### Post by Rui Pais on 2007-07-23
> **aGit said:**
> hi

I did everything said in the first post, the how-to, everything went well, apart from me geting a EXML error in the scripting part, what does that mean?

also, when i logged off and chose the e17 to login on, it said that /opt/e17/bin/englightenment not found...that cant be right? help would be much appriciated. Thanks.

ps. i'm running edgy on a Via epia ms10000e, 1ghz cpu, i read from the interwebz that enlightenment should work on older and less powerfull setups too, hope it runs with mine. need something to replace beryl as it i cannot run with this and i like my eyecandy.

-aGit

[#401]("http://ubuntuforums.org/showpost.php?p=2054941&postcount=401")

---

### Post by aGit on 2007-07-23
Thanks for the quick reply, but that didnt work for me, i changed the opt/e17/bin/englighenment to ...englightenment_start and booted the 'puter, and it still gave me the same error; /opt/e17/bin/enlightenment_start was not found , i checked and the file really aint there, duh =). Could this be a result of the exml error i got eariler on in the scripting?


-aGit

---

### Post by Rui Pais on 2007-07-24
> **aGit said:**
> Thanks for the quick reply, but that didnt work for me, i changed the opt/e17/bin/englighenment to ...englightenment_start and booted the 'puter, and it still gave me the same error; /opt/e17/bin/enlightenment_start was not found , i checked and the file really aint there, duh =). Could this be a result of the exml error i got eariler on in the scripting?

hi,
the error in exml is not important. It's not a fundamental package.

check first for typos:
```
ls /opt/e17/bin/enlightenment_start 
```
(start with / and it's enlightenment_start, not englightenment)

and don't forget to add the path on /etc/environment. Check with:
```
echo $PATH
```
it should say /opt/e17/bin at the end of line.

---

### Post by elninom on 2007-07-24
i tried a few command but still get this error:
```

--------------------------- Installing libaries (EFL) --------------------------
- imlib2 ..................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
Running aclocal...
./autogen.sh: 8: aclocal: not found

```

where i was doing wrong?

---

### Post by godora102192 on 2007-07-25
hey i enter the FIRST code into the TERMINAL and it gives me the following error or just it can't continue!!! any help?? thanks 

sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
pkg-config is already the newest version.
Package libpng3-dev is a virtual package provided by:
  libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation candidate

---

### Post by godora102192 on 2007-07-25
> **TimmyJ said:**
> I updated my list of programs to install. Re-run this command and then re-run the script and see if that does it for you :) 
```

sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev
```

then

```
sudo ./easy_e17.sh -i --skip=emotion,eclair
```

hope that helps! Thanks for trying this out :)


hey i enter the FIRST code into the TERMINAL and it gives me the following error or just it can't continue!!! any help?? any comments & suggestions?

sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
pkg-config is already the newest version.
Package libpng3-dev is a virtual package provided by:
libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation candidate

---

### Post by Rui Pais on 2007-07-26
> **godora102192 said:**
> hey i enter the FIRST code into the TERMINAL and it gives me the following error or just it can't continue!!! any help?? any comments & suggestions?

sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
Reading package lists... Done
Building dependency tree
Reading state information... Done
pkg-config is already the newest version.
Package libpng3-dev is a virtual package provided by:
libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation candidate

Hi, this instructions are getting older :(

That package, libpng3, is superseded by libpng12-dev. There is too a missing package, libxslt1-dev.

A package list now could be: 
```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng12-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev libxslt1-dev

```

Another obsolete instruction is the part:
> Exec=/opt/e17/bin/enlightenment
that should now be:
> Exec=/opt/e17/bin/enlightenment_start
good luck

---

### Post by godora102192 on 2007-07-26
ohhh everything was going perfectly UNTIL  this pooped up!!!!! WHAT should i do???

-- Build phase 2/3 -------------------------------
- lib-compilation and installation
- apps-compilation and installation
--------------------------------------------------------------------------------


--------------------------- Installing libaries (EFL) --------------------------
- imlib2 ..................... ok          
- edb ........................ ok          
- eet ........................ ok          
- evas ....................... ok          
- ecore ...................... ok          
- efreet ..................... ok          
- epeg ....................... ok          
- embryo ..................... ok          
- edje ....................... ok          
- epsilon .................... ok          
- esmart ..................... ok          
- emotion .................... ok          
- engrave .................... ok          
- etk ........................ ok          
- ewl ........................ ok          
- exml ....................... ok          
- enhance .................... ok          
--------------------------------------------------------------------------------

---------------------------- Installing applications ---------------------------
- e .......................... ok          
- entrance ................... ok          
- eclair ..................... ok          
- evfs ....................... ok          
- edje_viewer ................ ok          
- edje_editor ................ ok          
- elicit ..................... ok          
- emphasis ................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
checking dynamic linker characteristics... GNU/Linux ld.so
checking how to hardcode library paths into programs... immediate
appending configuration tag "F77" to libtool
checking for strndup... yes
checking for pthread_create in -lpthread... yes
checking for pkg-config... /usr/bin/pkg-config
checking pkg-config is at least version 0.9.0... yes
checking for EMPHASIS... configure: error: Package requirements (
  ecore >= 0.9.9.022
  ecore-config
  etk >= 0.1.0.002
  enhance >= 0.0.1
  libxml-2.0 >= 2.6.0
  libmpd >= 0.12.0
) were not met:

No package 'libmpd' found

Consider adjusting the PKG_CONFIG_PATH environment variable if you
installed software in a non-standard prefix.

Alternatively, you may set the environment variables EMPHASIS_CFLAGS
and EMPHASIS_LIBS to avoid the need to call pkg-config.
See the pkg-config man page for more details.

--------------------------------------------------------------------------------

-> Get more informations by checking the log file '/tmp/easy_e17/install_logs/emphasis.log'!

---

### Post by Rui Pais on 2007-07-27
hi godora102192,
congratulations on your ***working*** e17. Hope you like it.
You only need some modules to make it more comfortable. ;)

About emphasis. Are you sure you really need emphasis? (do you what it does?)
Anyway, if you are sure you reallly need it you need first:
```
sudo apt-get install libmpd-dev
```
But probably the best choice is just skip that one and run the script again
```
sudo ./easy_e17.sh --skip=emphasis
```
to get the modules installation part. 
You can do it from e17 if you want it to try your e now :)

hth

---

### Post by godora102192 on 2007-07-27
ok!! i duon't know what EMPESIS IS!!! and btw its already working????

i mean if its installed and WORKING how do run  it??? is it like an app???? i did not continue AFTER i ran the LAST script!!!!

i was about to enter SCRIPT number 4 !!! i think its about a DESKTOP icon or something!!!

THE last post that u replied to is WERE I COMPLETELY STOPPED!!!! i did not do anything after that!!!

so can u tell me WHAT to do now??? like am i done ?? or i need some more little things to do???

thanks !! your the best

---

### Post by Rui Pais on 2007-07-27
> **godora102192 said:**
> ok!! i duon't know what EMPESIS IS!!! and btw its already working????

i mean if its installed and WORKING how do run  it??? is it like an app???? i did not continue AFTER i ran the LAST script!!!!

i was about to enter SCRIPT number 4 !!! i think its about a DESKTOP icon or something!!!

THE last post that u replied to is WERE I COMPLETELY STOPPED!!!! i did not do anything after that!!!

so can u tell me WHAT to do now??? like am i done ?? or i need some more little things to do???

thanks !! your the best

uff, you use a lot of punctuation signs :)

Yes you have compiled and installed e17. Congratulations! 
e17 is a (almost) Desktop Environment (it's a extended window manager with a toolkit, to be more precise). 
Like Gnome it has things like applets, called modules. When the script stoped it didn't compile/installed those. And they are very useful. Thats what you need to finish. But you can load e17 now. 
Just do the other steps of the 1st post, creating a /usr/share/xsessions/e17.desktop file with:
```
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment_start
Icon=
Type=Application
```
logout gnome (or the one you use) and on login manager, under "Session", choose E-17, and enjoy :D

To finish, do in a terminal:
```
sudo ./easy_e17.sh --skip=emphasis
``` 
and that will finish scrip install building the missing modules.
emphasis is a music player daemon.

hth

---

### Post by godora102192 on 2007-07-27
i entered the CODE u told me to enter in the terminal but it does not continue!!!!!!!

 after i enter the code it shows me the following!

 sudo ./easy_e17.sh --skip=emphasis

------------------------------- Easy_e17.sh 1.1.3 ------------------------------
  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'wtfoo' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
--------------------------------------------------------------------------------
  Updates:         [http://omicron.homeip.net/projects/#easy_e17.sh](http://omicron.homeip.net/projects/#easy_e17.sh)
  Support:         #e.de, #get-e (irc.freenode.net)
                   [email]morlenxus@gmx.net[/email]
  Patches:         Generally accepted, please contact me!
--------------------------------------------------------------------------------


----------------------------- Current Configuration ----------------------------
  Install path:    /opt/e17
  CVS path:        /home/irakli/e17_cvs
  CVS server:      :pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux

  Libaries:        imlib2 edb eet evas ecore efreet epeg embryo edje epsilon esmart emotion engrave etk ewl exml enhance
  Applications:    e entrance eclair evfs edje_viewer edje_editor elicit emphasis empower entrance_edit_gui entropy ephoto estickies exhibit extrackt
  Miscellaneous:   engage scrot
  Modules:         alarm bling cpu deskshow emu flame forecasts language mail mem mixer moon net photo rain screenshot slideshow snow taskbar tclock uptime weather winselector wlan
  Skipping:        emphasis 

  Script action:   MISSING!
--------------------------------------------------------------------------------

----------------- Short help 'easy_e17.sh <ACTION> <OPTIONS...>' ---------------
  -i, --install    = action: compile and install ALL of e17
  -u, --update     = action: update your installed e17
      --help       = full help



and when i try to update it or install it  ! it does not continue, it just shows "command not found", i tried entering it in ANY way it just would not do it!! any suggestions?

---

### Post by Rui Pais on 2007-07-28
oops. 
Sorry forget the -i flag:
```
sudo ./easy_e17.sh --skip=emphasis -i
```

that should continue from the last time where it stops.

---

### Post by godora102192 on 2007-07-28
hey 

i got  the MASSAGE that i installed everything correctly !!!! i created the DESKTOP thing that you told me to do, and i saved it !! now how do i actually USE it??

the massage was similar to this !!! you successfully installed the E17!!!! then i created the DESKTOP entry u asked me and saved it, now what do i do to actually use it??

thank you for your help! and if there is any way i can help your RANK, in ubuntu forums just tell me  and i WILLLLLLLL fill it out i promise!

thank you once again

---

### Post by godora102192 on 2007-07-28
hey i got how to LOG in into the e17!!! but there is a problem, when i  select e-17 in the sessions when i am logging in it gives me the following error and then i click exit cause i don't wanna ruin everything!


                                                                 Enlightenment error

you are executing enlightenment directly. this is bad. please do not execute the "enlightenment " binary. Use the "enlightenment_start" launcher. it will handle setting up environment variables, paths, and launching any other required services etc. Before enlightenment itself begins running.

so did i do something wrong? how do i use the "enlightenment_start" ?? please help me 

thank you

---

### Post by Rui Pais on 2007-07-28
Hi again. 
You must have something wrong.
type:
```
gksudo gedit /usr/share/xsessions/e17.desktop
```
and ensure that the line started with Exec says:
```
Exec=/opt/e17/bin/enlightenment_start
```

then type:
gksudo gedit  /etc/environment
and ensure that line started with PATH contains /opt/e17/bin. Should be something like:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/e17/bin"
```

then it should work.
:)

---

### Post by godora102192 on 2007-07-28
well that seems to be the problem!!  when i typed the """"gksudo gedit /usr/share/xsessions/e17.desktop""""" it gave the following output


/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename

and when i typed the """"""gksudo gedit /etc/environment"""""" it gave the following output!!

/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:21: Unable to locate image file in pixmap_path: "Toolbar/toolbar-black.png"
/home/irakli/.themes/aero-clone/gtk-2.0/toolbar-custom.rc:24: Background image options specified without filename
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:187: Unable to locate image file in pixmap_path: "Arrows/arrow-up.png"
/home/irakli/.themes/aero-clone/gtk-2.0/gtkrc:191: Overlay image options specified without filename
(gedit:5544): GnomeUI-WARNING **: While connecting to session manager:
Authentication Rejected, reason : None of the authentication protocols specified are supported and host-based authentication failed.

ohh and the PATH was the following--------  PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
LANG="en_US.UTF-8"-----


so what should i do?????

---

### Post by Rui Pais on 2007-07-28
hmmm, that seems to be an issue with your gnome theme. Nothing to do with e17...

If you have E-17 avaliable on Login Manager Sessions then you have already made the /usr/share/xsessions/e17.desktop file. Just edit that the same way to ensure that it uses **enlightenment_start**.

About the second part, just replace at /etc/environment:
> PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games"
by:
```
PATH="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/e17/bin"
```
thats all.

good luck

---

### Post by godora102192 on 2007-07-28
hey 

i am kinda confused about what you actually want me to do! i don't get what to enter and were. can you make it little more understandable please?? 

thank you man you are a GREAT help

---

### Post by godora102192 on 2007-07-29
ohhh i got it!! i have not actually tried it but i will try it tomorrow cause i need to go to sleep right now but i think i got what you are saying!! 

by the way dude if u need any help with your rank or something i can help you with if thats possible just send me a massage ok???

thanks man your are the best

---

### Post by godora102192 on 2007-07-29
hey i did what you told me to do but it still gave me the same error! why?? any suggestions what to do next???

---

### Post by Rui Pais on 2007-07-29
> **godora102192 said:**
> hey i did what you told me to do but it still gave me the same error! why?? any suggestions what to do next???

Sorry the late answer, today i was out...

Do you that you still got the same error at start of E-17 that you mention at your [post #489]("http://ubuntuforums.org/showpost.php?p=3096533&postcount=489")?

can you copy paste here the output of:
```
cat /usr/share/xsessions/e17.desktop
```
```
echo $PATH
```
and
```
ls  ls /opt/e17/bin/
```
please?

---

### Post by godora102192 on 2007-07-29
yes i still get the SAME error as i mentioned in post 489!! here are the outputs u wanted to see

 cat /usr/share/xsessions/e17.desktop 

[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application

 echo $PATH

/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games:/opt/e17/bin


ls  ls /opt/e17/bin/

ls: ls: No such file or directory
/opt/e17/bin/:
eclair               enhance-config          etk_test
eclair_wsz2edj       enlightenment           evfs
ecore_config         enlightenment-config    evfscat
edb_ed               enlightenment_fm        evfscopy
edb_gtk_ed           enlightenment_imc       evfsdemo
edje_cc              enlightenment_remote    ewl_config
edje_decc            enlightenment_start     ewl_embed_test
edje_editor          enlightenment_sys       ewl_simple_test
edje_recc            enlightenment_thumb     ewl_test
edje_viewer          entrance                exhibit
efreet_alloc         entrance_edit           exml-config
efreet_cache_test    entrance_edit-config    extrackt
efreet_menu_alloc    entrance_edit_gui       imlib2-config
efreet_spec_test     entrance_wrapper        imlib2_bumpmap
efreet_test          entropy                 imlib2_colorspace
elicit               epeg                    imlib2_conv
embryo_cc            ephoto                  imlib2_grab
emotion_test         epsilon                 imlib2_poly
empower              epsilon_thumb_test      imlib2_show
empower-askpass      epsilon_thumbd          imlib2_test
emu_client           esmart_test             imlib2_view
engage               esmart_text_entry_test  scrot
engrave_canvas_test  estickies
engrave_test         etk_prefs

---

### Post by godora102192 on 2007-07-29
ohh and in the LAST code u asked me for the LONG one in the TERMINAL this is HIGHLIGHTED RED!!!

enlightenment_sys   <--- that is highlighted red when i enter the 3rd code u asked me for!!

---

### Post by Rui Pais on 2007-07-29
> **godora102192 said:**
> yes i still get the SAME error as i mentioned in post 489!! here are the outputs u wanted to see

 cat /usr/share/xsessions/e17.desktop 

[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
**Exec=/opt/e17/bin/enlightenment**
Icon=
Type=Application
...

ok, thats the problem, the line in bold from your quote.
you need todo:
```
gksudo gedit /usr/share/xsessions/e17.desktop
```
and replace
```
Exec=/opt/e17/bin/enlightenment
```
by:
```
Exec=/opt/e17/bin/enlightenment_start
```

don't worry with the red in ls command. Thats normal.

---

### Post by godora102192 on 2007-07-29
OMG dude!!! 

thank you so much, thank you, thank you, thank you, thank you,thank you, thank you, thank you, thank you thank you, thank you, thank you, thank you thank you, thank you, thank you, thank you

dude you are the BEST !!! its SOOOOO beautiful!!!! thank you sooooo much!!!!!

if there is ANYTHING i can help you with, i will certainly TRY . thank you 


just e-mail me at godora102192@aol,com  your are the best!!

if there is anything e-mail me at that e-mail!!

thank you

---

### Post by Rui Pais on 2007-07-30
no prob, glad i could help :)

check [www.get-e.org](www.get-e.org) too for more eyecandy stuff like themes and animated backgrounds.

have fun
:)

---

### Post by godora102192 on 2007-07-30
hey 

once again thanks for helping me out! :)

the site you gave me is great and easy to use but when i download the file it does not get "recognized" by any kind of software. so how can i open up the animated backgrounds and set them as my wallpapers?

---

### Post by Freddy on 2007-07-30
> **godora102192 said:**
> hey 

once again thanks for helping me out! :)

the site you gave me is great and easy to use but when i download the file it does not get "recognized" by any kind of software. so how can i open up the animated backgrounds and set them as my wallpapers?
Download them to ~/.e/e/backgrounds load up your wallpaper chooser and select personal, select the background and voila.

---

### Post by godora102192 on 2007-07-30
> **Freddy said:**
> Download them to ~/.e/e/backgrounds load up your wallpaper chooser and select personal, select the background and voila.


when i use firefox the default place it saves is on a desktop!! i can't find the path you told me to save into !!

how do i find it??? i am a TOTAL noob at this man so u gotta help me out!

thanks

---

### Post by godora102192 on 2007-07-30
Never mind i got it lol!!

thank you for posting anyways!!

thanks:lolflag:

---

### Post by godora102192 on 2007-07-31
hey guys i have a little problem !!

i applied new theme to my e-17 but its seems that it has a BUG!!!

i have a black theme but when i click on my desktop the menu pops up but i CANT see the writing !!!!

can one of u guys UPLOAD a video for me that slow and shows how to change a theme so i can follow your steps and do it?? cause remember i can use the e-17 theme but i can't see the writing !!!!!

or does this thing have like "system restore"?????? so i can change it back to the original time that it was installed???

any help would be great!!

thank you :confused::confused:

---

### Post by raul_ on 2007-07-31
Because E17 is under heavy development, some older themes don't work in the latest CVS version. You could try to remove the .edj file and restart, so E17 reverts back to the default theme

---

### Post by Freddy on 2007-07-31
> **raul_ said:**
> Because E17 is under heavy development, some older themes don't work in the latest CVS version. You could try to remove the .edj file and restart, so E17 reverts back to the default theme
Don't use any other themes found it the repository than the default "bling, bling) theme, instead download the working themes at [get-e]("http://www4.get-e.org/Themes/E17/"), Put them inside ~/.e/e/themes and choose them from the "personal themes" tab.
/Freddan

---

### Post by godora102192 on 2007-07-31
> **raul_ said:**
> Because E17 is under heavy development, some older themes don't work in the latest CVS version. You could try to remove the .edj file and restart, so E17 reverts back to the default theme

i did what you told me but it still shows me the SAME theme!!!!

and i downloaded that theme from [www.get.e.org](www.get.e.org) or it was from [www.e17-stuff.org](www.e17-stuff.org) i am not sure!!

but how can i invert it to the DEFAULT theme again?? because i can't see ANY kind of writings EXCEPT when i am on the internet!!!!!

HELP:confused::confused::confused::(:(:(:(

---

### Post by raul_ on 2007-07-31
Lol

don't worry. that happened to me a couple of times. You can change themes with the terminal. 

enlightenment_remote -theme-set theme default.edj -restart

---

### Post by godora102192 on 2007-07-31
thank you very much man!!!

it worked!!:)

---

### Post by fifthecho on 2007-08-01
I'm attempting to install through this method as the package feed appears to be from older snapshots and am getting the following error:
```

---------------------------- Installing applications ---------------------------
- e .......................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/e17_cvs/e17/apps/e/data/etc'
Making all in icons
make[3]: Entering directory `/root/e17_cvs/e17/apps/e/data/icons'
make[3]: Nothing to be done for `all'.
make[3]: Leaving directory `/root/e17_cvs/e17/apps/e/data/icons'
make[3]: Entering directory `/root/e17_cvs/e17/apps/e/data'
make[3]: Nothing to be done for `all-am'.
make[3]: Leaving directory `/root/e17_cvs/e17/apps/e/data'
make[2]: Leaving directory `/root/e17_cvs/e17/apps/e/data'
Making all in doc
make[2]: Entering directory `/root/e17_cvs/e17/apps/e/doc'
make[2]: Nothing to be done for `all'.
make[2]: Leaving directory `/root/e17_cvs/e17/apps/e/doc'
Making all in po
make[2]: Entering directory `/root/e17_cvs/e17/apps/e/po'
make enlightenment.pot-update
make[3]: Entering directory `/root/e17_cvs/e17/apps/e/po'
make[3]: *** No rule to make target `../src/modules/exebuf/e_mod_config.c', needed by `enlightenment.pot-update'.  Stop.
make[3]: Leaving directory `/root/e17_cvs/e17/apps/e/po'
make[2]: *** [enlightenment.pot] Error 2
make[2]: Leaving directory `/root/e17_cvs/e17/apps/e/po'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/root/e17_cvs/e17/apps/e'
make: *** [all] Error 2
--------------------------------------------------------------------------------

```
Any ideas?

---

### Post by 4KvRMU7Nnv on 2007-08-01
I have same problem as fifthecho.

---

### Post by godora102192 on 2007-08-01
how do i update e17???? how do i get the new updates???

---

### Post by fifthecho on 2007-08-02
Edit the "e17_cvs/e17/apps/e/po/POTFILES.in" file
Delete line #212 which contains "src/modules/exebuf/e_mod_config.c"
Then run "sudo ./easy_e17.sh -s -i"

Source: [http://forums.gentoo.org/viewtopic-t-573610-highlight-.html]("http://forums.gentoo.org/viewtopic-t-573610-highlight-.html")

E then compiles fine. I'm not sure what functionality this may remove, but at least until we have a working CVS again, this works.

---

### Post by 4KvRMU7Nnv on 2007-08-02
thanks im trying it now

EDIT:: sweet it worked...now for the rest of them...

---

### Post by Jem777 on 2007-08-06
I got following error when trying to install e17:
> --------------------------- Installing libaries (EFL) --------------------------
- imlib2 ..................... previously installed
- edb ........................ previously installed
- eet ........................ previously installed
- evas ....................... previously installed
- ecore ...................... previously installed
- efreet ..................... previously installed
- epeg ....................... previously installed
- embryo ..................... previously installed
- edje ....................... previously installed
- epsilon .................... previously installed
- esmart ..................... previously installed
- emotion .................... previously installed
- engrave .................... previously installed
- etk ........................ previously installed
- ewl ........................ previously installed
- exml ....................... previously installed
- enhance .................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
make[3]: Betrete Verzeichnis '/home/satriani/e17_cvs/e17/libs/enhance/src/lib'
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I. -I../.. -I../../src/include  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk   -g -O2 -Wall -MT libenhance_la-enhance.lo -MD -MP -MF .deps/libenhance_la-enhance.Tpo -c -o libenhance_la-enhance.lo `test -f 'enhance.c' || echo './'`enhance.c
/bin/bash ../../libtool --tag=CC   --mode=compile gcc -DHAVE_CONFIG_H -I. -I../.. -I. -I../.. -I../../src/include  -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk   -g -O2 -Wall -MT libenhance_la-enhance_widget.lo -MD -MP -MF .deps/libenhance_la-enhance_widget.Tpo -c -o libenhance_la-enhance_widget.lo `test -f 'enhance_widget.c' || echo './'`enhance_widget.c
 gcc -DHAVE_CONFIG_H -I. -I../.. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -Wall -MT libenhance_la-enhance.lo -MD -MP -MF .deps/libenhance_la-enhance.Tpo -c enhance.c  -fPIC -DPIC -o .libs/libenhance_la-enhance.o
In file included from /opt/e17/include/etk/Etk.h:35,
                 from enhance_private.h:13,
                 from enhance.c:1:
/opt/e17/include/etk/etk_dialog.h:69: error: expected declaration specifiers or '...' before 'Etk_Uidget'
 gcc -DHAVE_CONFIG_H -I. -I../.. -I. -I../.. -I../../src/include -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -g -O2 -Wall -MT libenhance_la-enhance_widget.lo -MD -MP -MF .deps/libenhance_la-enhance_widget.Tpo -c enhance_widget.c  -fPIC -DPIC -o .libs/libenhance_la-enhance_widget.o
make[3]: *** [libenhance_la-enhance.lo] Fehler 1
make[3]: *** Warte auf noch nicht beendete Prozesse...
In file included from /opt/e17/include/etk/Etk.h:35,
                 from enhance_private.h:13,
                 from enhance_widget.c:1:
/opt/e17/include/etk/etk_dialog.h:69: error: expected declaration specifiers or '...' before 'Etk_Uidget'
enhance_widget.c: In function '_e_widget_parent_add':
enhance_widget.c:979: error: incompatible type for argument 2 of 'etk_dialog_pack_widget_in_action_area'
enhance_widget.c:979: error: too many arguments to function 'etk_dialog_pack_widget_in_action_area'
make[3]: *** [libenhance_la-enhance_widget.lo] Fehler 1
make[3]: Verlasse Verzeichnis '/home/satriani/e17_cvs/e17/libs/enhance/src/lib'
make[2]: *** [all-recursive] Fehler 1
make[2]: Verlasse Verzeichnis '/home/satriani/e17_cvs/e17/libs/enhance/src'
make[1]: *** [all-recursive] Fehler 1
make[1]: Verlasse Verzeichnis '/home/satriani/e17_cvs/e17/libs/enhance'
make: *** [all] Fehler 2


---

### Post by fifthecho on 2007-08-09
Are you still getting the same error?
I completed a -u upgrade with no errors (or need to change code) yesterday, so CVS may have stabled out some.

---

### Post by Metacarpal on 2007-08-09
For those who wonder: giving easy_e17.sh your sudo password does not present any security risk.  I went through the code to make sure that information never leaves the script.  It's friendly.

Nothing personal, TimmyJ - just my personal brand of paranoia at work. :)
Nicely written script, by the way.  This is my first try with e17, and I'm looking forward to seeing how it looks.

---

### Post by thelostsoul on 2007-08-16
Wow I've officially moved into e17 and am loving it.  I've tried just about everything - GNOME, KDE, KDE4, Openbox, Fluxbox, XFCE, so many different things, but e17 is just the best!

Thanks for this script!!  I run it almost every morning to get updates!


Only problem I have is with entropy - it when I run it, my computer starts going real slow, and even when I close it, it keeps going slow.  I have to actually reboot (restart gdm doesn't help) to get it to run at normal speeds.

---

### Post by risenphoenix on 2007-08-18
> mathangi@mathangi-desktop:~$ sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
Password:
Reading package lists... Done
Building dependency tree... Done
gettext is already the newest version.
pkg-config is already the newest version.
Package libpng3-dev is a virtual package provided by:
  libpng12-dev 1.2.8rel-5ubuntu0.2
You should explicitly select one to install.
E: Package libpng3-dev has no installation candidate
mathangi@mathangi-desktop:~$ wget [http://omicron.homeip.net/projects/easy_e17/easy_e17.sh](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh)
--15:38:03--  [http://omicron.homeip.net/projects/easy_e17/easy_e17.sh](http://omicron.homeip.net/projects/easy_e17/easy_e17.sh)
           => `easy_e17.sh.3'
Resolving omicron.homeip.net... 85.178.62.13
Connecting to omicron.homeip.net|85.178.62.13|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 39,112 (38K) [application/x-sh]

100%[====================================>] 39,112         5.75K/s    ETA 00:00

15:38:12 (5.75 KB/s) - `easy_e17.sh.3' saved [39112/39112]

mathangi@mathangi-desktop:~$ chmod +x easy_e17.sh
mathangi@mathangi-desktop:~$ ./easy_e17.sh -i

------------------------------- Easy_e17.sh 1.1.4 ------------------------------  Developers:      Brian 'morlenxus' Miculcy
                   David 'onefang' Seikel
  Contributors:    Tim 'wtfoo' Zebulla
                   Daniel G. '_ke' Siegel
                   Stefan 'slax' Langner
                   Massimiliano 'Massi' Calamelli
                   Thomas 'thomasg' Gstaedtner
--------------------------------------------------------------------------------  Updates:         [http://omicron.homeip.net/projects/#easy_e17.sh](http://omicron.homeip.net/projects/#easy_e17.sh)
  Support:         #e.de, #get-e (irc.freenode.net)
                   [email]morlenxus@gmx.net[/email]
  Patches:         Generally accepted, please contact me!
--------------------------------------------------------------------------------

----------------------------- Current Configuration ----------------------------  Install path:    /opt/e17
  CVS path:        /home/mathangi/e17_cvs
  CVS server:      :pserver:anonymous@anoncvs.enlightenment.org:/var/cvs/e
  Logs path:       /tmp/easy_e17/install_logs
  OS:              Linux (Distribution: debian)

  Libraries:       imlib2 edb eet evas ecore efreet epeg embryo edje epsilon esmart emotion engrave etk etk_extra evolve ewl exml enhance e_dbus
  Applications:    e entrance eclair evfs edje_viewer edje_editor elicit elitaire emphasis empower engycad entrance_edit_gui entropy ephoto estickies exhibit expedite extrackt
  Miscellaneous:   engage enthrall rage scrot
  Modules:         alarm bling cpu deskshow emu flame forecasts language mail mem mixer moon net news photo rain screenshot slideshow snow taskbar tclock uptime weather winselector wlan

  Script action:   install
--------------------------------------------------------------------------------
-------------------------------- Build phase 1/3 -------------------------------- running some basic system checks
- pre cleaning
- cvs checkout/update
--------------------------------------------------------------------------------

------------------------------- Basic system checks ----------------------------- cvs-dir .................... ok
- creating script dirs ....... ok
- build-user ................. mathangi (non-root)
- sudo available ............. enter sudo-password:
- adding path to env ......... ok
- checking lib-path in ldc ... ok (/etc/ld.so.conf)
- setting compile options .... ok
--------------------------------------------------------------------------------
------------------------------- CVS checkout/update ----------------------------- checkout source of repo 'e17' ...
./easy_e17.sh: line 302: cvs: command not found
./easy_e17.sh: line 302: cvs: command not found
./easy_e17.sh: line 302: cvs: command not found
./easy_e17.sh: line 302: cvs: command not found
./easy_e17.sh: line 302: cvs: command not found
./easy_e17.sh: line 302: cvs: command not found
./easy_e17.sh: line 302: cvs: command not found


This is the error I got. What did I do wrong?

---

### Post by Rui Pais on 2007-08-18
> **risenphoenix said:**
> This is the error I got. What did I do wrong?

Hi,
the problem is that the instructions on the 1st post are outdated and are incorrect for feisty. 
You did not acted according to the error output but gone ahead on instructions when the 1st one was not finished and you still don't had your compilations and dependencies all installed and configured.

[Try use this ones instead.]("http://ubuntuforums.org/showpost.php?p=3082892&postcount=481")

Good luck.

---

### Post by natty on 2007-08-25
hi ,
am trying to install e17 and having some problems

dies on installing e itself, not something i guess i can skip, with -e on the install script

heres the end of the log

---------------------------- Installing applications ---------------------------
- e .......................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
/opt/e17/bin/edje_cc: Wrote      1157 bytes (   1Kb) for "images/504" image entry "e17_slider_bt0.png" compress: [raw: 71.8%] [real: 6.2%]
/opt/e17/bin/edje_cc: Wrote      1082 bytes (   1Kb) for "images/505" image entry "e17_slider_bt1.png" compress: [raw: 73.6%] [real: 7.8%]
/opt/e17/bin/edje_cc: Wrote      1631 bytes (   2Kb) for "images/506" image entry "e17_slider_bt_glow.png" compress: [raw: 60.2%] [real: 19.9%]
/opt/e17/bin/edje_cc: Wrote       260 bytes (   0Kb) for "images/507" i/opt/e17/bin/edje_cc: Error. unable to load image for image "e17_wiz_b1.png" part entry to ../../data/themes/default.edj. Missing PNG or JPEG loader modules for Evas or file does not exist, or is not readable.
mage entry "e17_entry_cursor.png" compress: [raw: 79.9%] [real: 39.3%]
/opt/e17/bin/edje_cc: Wrote      1310 bytes (   1Kb) for "images/508" image entry "e17_desklock_error.png" compress: [raw: 98.9%] [real: -90.4%]
/opt/e17/bin/edje_cc: Wrote      7647 bytes (   7Kb) for "images/509" image entry "e17_shelf_bg_h.png" compress: [raw: 77.5%] [real: -23.8%]
/opt/e17/bin/edje_cc: Wrote     10039 bytes (  10Kb) for "images/510" image entry "e17_shelf_bg_v.png" compress: [raw: 70.5%] [real: -59.4%]
/opt/e17/bin/edje_cc: Wrote     17796 bytes (  17Kb) for "images/511" image entry "e17_shelf_bg2_h.png" compress: [raw: 47.7%] [real: -126.6%]
/opt/e17/bin/edje_cc: Wrote     19642 bytes (  19Kb) for "images/512" image entry "e17_shelf_bg2_v.png" compress: [raw: 42.3%] [real: -143.8%]
/opt/e17/bin/edje_cc: Wrote       840 bytes (   1Kb) for "images/513" image entry "e17_preview_bg.png" compress: [raw: 98.0%] [real: -62.5%]
/opt/e17/bin/edje_cc: Wrote       960 bytes (   1Kb) for "images/514" image entry "e17_preview_bg_over.png" compress: [raw: 95.5%] [real: -15.7%]
/opt/e17/bin/edje_cc: Wrote      1332 bytes (   1Kb) for "images/515" image entry "e17_well_overlay.png" compress: [raw: 89.2%] [real: -42.6%]
/opt/e17/bin/edje_cc: Wrote     54920 bytes (  54Kb) for "images/516" image entry "e17_tl_corner_logo.png" compress: [raw: 91.4%] [real: -36.5%]
/opt/e17/bin/edje_cc: Wrote     13964 bytes (  14Kb) for "images/517" image entry "e17_tl_corner_logo_shadow.png" compress: [raw: 97.8%] [real: 49.5%]
/opt/e17/bin/edje_cc: Wrote     48520 bytes (  47Kb) for "images/518" image entry "e17_whitev.png" compress: [raw: 81.5%] [real: -23.9%]
make[4]: *** [default.edj] Error 255
make[4]: Leaving directory `/home/nat/e17_cvs/e17/apps/e/data/themes'
make[3]: *** [all-recursive] Error 1
make[3]: Leaving directory `/home/nat/e17_cvs/e17/apps/e/data/themes'
make[2]: *** [all-recursive] Error 1
make[2]: Leaving directory `/home/nat/e17_cvs/e17/apps/e/data'
make[1]: *** [all-recursive] Error 1
make[1]: Leaving directory `/home/nat/e17_cvs/e17/apps/e'
make: *** [all] Error 2


any help much appreciated

cheers

n

---

### Post by Rui Pais on 2007-08-26
> **natty said:**
> hi ,
am trying to install e17 and having some problems

dies on installing e itself, not something i guess i can skip, with -e on the install script

heres the end of the log

---------------------------- Installing applications ---------------------------
- e .......................... ERROR!      

...

any help much appreciated

cheers

n

hi,
just a temporary cvs bork.
try install again, is working now.

---

### Post by godora102192 on 2007-08-26
hey rui 

how can i update my e17????  i have not run any kind of UPDATE for e17 since i installed it because i dunno how to update it.

thanx

---

### Post by Rui Pais on 2007-08-26
> **godora102192 said:**
> hey rui 

how can i update my e17????  i have not run any kind of UPDATE for e17 since i installed it because i dunno how to update it.

thanx

easy, just use the flag -u:
>  sudo ./easy_e17.sh -u
:)

---

### Post by Metacarpal on 2007-08-27
I'm trying to update my e17 using easy_e17.sh -u
but encountering errors when the script attempts to update the repos:
```
<snip>
? libs/engrave/src/bin/.deps/engrave_test_main.Po
? libs/etk_extra/etk_extra_tree_model_wobbly.pc
? libs/etk_extra/etk_extra_video.pc
? proto/e_dbus/src/lib/nm/e_nm_network.lo
C apps/e/po/bg.po
C apps/e/po/ca.po
C apps/e/po/de.po
C apps/e/po/eo.po
C apps/e/po/fr.po
C apps/e/po/hu.po
C apps/e/po/it.po
C apps/e/po/ja.po
C apps/e/po/ko.po
C apps/e/po/pt_BR.po
C apps/e/po/ru.po
C apps/e/po/sl.po
M apps/elitaire/po/de.po
FAILED! Next attempt 7 in 40 seconds
```

---

### Post by MikeNet on 2007-09-01
When I install Enlightenment I become this error:

> 
- evolve ..................... ERROR!      
--------------------------------------------------------------------------------

----------------------------------- Last loglines ------------------------------
        then mv -f ".deps/libevolve_la-evolve_signal.Tpo" ".deps/libevolve_la-evolve_signal.Plo"; else rm -f ".deps/libevolve_la-evolve_signal.Tpo"; exit 1; fi
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -I/opt/e17/include -I/opt/e17/include -Wall -MT libevolve_la-evolve_signal.lo -MD -MP -MF .deps/libevolve_la-evolve_signal.Tpo -c evolve_signal.c  -fPIC -DPIC -o .libs/libevolve_la-evolve_signal.o
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -I/opt/e17/include -I/opt/e17/include -Wall -MT libevolve_la-evolve_lib.lo -MD -MP -MF .deps/libevolve_la-evolve_lib.Tpo -c evolve_lib.c  -fPIC -DPIC -o .libs/libevolve_la-evolve_lib.o
evolve_lib.c: In function 'evolve_init':
evolve_lib.c:91: error: 'Etk_Property_Value_Value' undeclared (first use in this function)
evolve_lib.c:91: error: (Each undeclared identifier is reported only once
evolve_lib.c:91: error: for each function it appears in.)
evolve_lib.c:92: error: expected ';' before '___ett'
evolve_lib.c:92: error: '___ett' undeclared (first use in this function)
evolve_lib.c:93: error: expected ';' before '___ett'
evolve_lib.c:94: error: expected ';' before '___ett'
evolve_lib.c:95: error: expected ';' before '___ett'
evolve_lib.c:96: error: expected ';' before '___ett'
evolve_lib.c:97: error: expected ';' before '___ett'
evolve_lib.c:98: error: expected ';' before '___ett'
evolve_lib.c:99: error: expected ';' before '___ett'
make[3]: *** [libevolve_la-evolve_lib.lo] Error 1
make[3]: *** Wait for end....
 gcc -DHAVE_CONFIG_H -I. -I. -I../../src -I/opt/e17/include -I/opt/e17/include -I/opt/e17/include/etk -I/opt/e17/include -I/opt/e17/include -Wall -MT libevolve_la-evolve_signal.lo -MD -MP -MF .deps/libevolve_la-evolve_signal.Tpo -c evolve_signal.c -o libevolve_la-evolve_signal.o >/dev/null 2>&1
make[3]: Quitting `/root/e17_cvs/e17/libs/evolve/src/lib'
make[2]: *** [all-recursive] Error 1
make[2]: Quitting `/root/e17_cvs/e17/libs/evolve/src'
make[1]: *** [all] Error 2
make[1]: Quitting `/root/e17_cvs/e17/libs/evolve/src'
make: *** [all-recursive] Error 1

---

### Post by guidop on 2007-09-02
I can confirm the evolve library compile error seen by MikeNet.
Attempting to compile on iMac DV400 (G3 ppc).  
Tried on 2007 Sep 1 & Sep 2.

---

### Post by KingArthur10 on 2007-09-02
> **guidop said:**
> I can confirm the evolve library compile error seen by MikeNet.
Attempting to compile on iMac DV400 (G3 ppc).  
Tried on 2007 Sep 1 & Sep 2.

I, too am receiving an evolve compilation error.  Inspiron 6000D.  The newest CVS must have broken something.

---

### Post by braynyac on 2007-09-03
Same here as well...Any ideas?

~braynyac

---

### Post by Rui Pais on 2007-09-03
And you need evolve for?...


Listen this thread suggest an installation from CVS using a script.
Thats ok. Simplify the job and offers options like update or partial installation etc.

But you can't use it blindly and without a though on what its going on. 
It's a script of one of **e** developers and tuned for his use. 
You are not a developer. Don't need to install every single e app and any pre-alpha, prototype, testing, developer tools ,etc. OK?
 Why download code and compile stuff that you don't use or is highly pre-alpha? 

It's not the cvs that it's broken, it's the new script that add some extra apps to the list, that may or may not compile. 

Again, **If you are not a DEVELOPER you don't need to track every single app that appears one17 CVS server**. 

The last version of script adds elitaire, engycad, enthrall, evolve, expedite and rage. Neither it's fundamental for e17. 
you need to do a file name .easy_e17.conf with something like (thats my list):
```
--skip=edb,evfs,entropy,edje_editor,emotion,eclair,emphasis,empower,engage,entrance,entrance_edit_gui,ephoto,estickies,extrackt,deskshow,emu,flame,language,mixer,moon,photo,winselector,snow,rain,taskbar
```
Just add evolve (or better, all the new entries) to --skip list.

Thats all.

---

### Post by RAV TUX on 2007-09-08
> **TimmyJ said:**
> This is just a quick how-to on downloading, compiling, and installing the desktop shell Enlightenment 17 from the CVS repository. E17 is still in development, so do not expect a fully stable, bug-free environment. That said: I use E17 on a daily basis and rarely run into any hiccups.

[B]READ: Before following this guide please remove any previously installed versions of E17 (aka from any repository) as they may cause errors in the process.
[/B]
A quick disclaimer: this is my first how-to, so feel free to offer any constructive criticism.

Lets Start!

1.) First we want to install all required packages for E17, and all the Enlightenment Foundation Libraries to install. This list may be a bit of overkill, but it will get the job done.

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
```2.) Now that all that is out of the way we need to get the script that will make downloading/compiling/installing E17 very easy. All credit goes to Morlenxus for this great tool.

From your home directory, run the following command
```
wget http://omicron.homeip.net/projects/easy_e17/easy_e17.sh
```3.) Now we need to made the script executable and then run it! This script will prompt you for your sudo password, enter it. This script will take quite some time to run, so try to be patient **NOTES: This script will install all the applications and libraries it installs into /opt/e17 so as not to interfere with other versions of enlightenment. You can change this location through scripts options. This script will install ALL the applications and libraries available in the E17 CVS tree. You may or may not want all these apps. You can easily skip any library or app using the --skip flag with the script.**

```
chmod +x easy_e17.sh
./easy_e17.sh -i
```4.) Now we have enlightenment all installed and working. The next step it create a desktop entry so that you can log-in to enlightenment from GDM.

Create a desktop entry called e17.desktop
```
sudo gedit /usr/share/xsessions/e17.desktop
```Copy/Paste the following into the newly created file
```
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
```Thats all you really need to do. Now using enligthenment is as simple as logging out, selecting the E-17 session and logging back in. Any time you want to update enlightenment and related libs/apps, simply re-run the easy_e17 script. For more information on the Enlightenment Foundation Libraries, and the applications that use them, please see [http://www.get-e.org](http://www.get-e.org) and 
[http://www.enlightenment.org.au](http://www.enlightenment.org.au)
[B]
Suggestion: due to the fact that enlightenment was installed in /opt/e17 it is a good idea to add /opt/e17/bin to your PATH so that it is easier to run all those great applications you just installed.[/B]

To do this open your /etc/environment with your favorite text editor

```
sudo gedit /etc/environment
```then add the following lines to the bottom

```
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/bin
```

following step one I get this:

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cvs is already the newest version.
cvs set to manual installed.
gettext is already the newest version.
gettext set to manual installed.
Package libpng3-dev is a virtual package provided by:
  libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation candidate
```what should I do about these packages?

Package libpng3-dev is a virtual package provided by:
  libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation

---

### Post by gundumfx on 2007-09-08
[QUOTE=TimmyJ;533202]This is just a quick how-to on downloading, compiling, and installing the desktop shell Enlightenment 17 from the CVS repository. E17 is still in development, so do not expect a fully stable, bug-free environment. That said: I use E17 on a daily basis and rarely run into any hiccups.

[B]READ: Before following this guide please remove any previously installed versions of E17 (aka from any repository) as they may cause errors in the process.
[/B]
A quick disclaimer: this is my first how-to, so feel free to offer any constructive criticism.

Lets Start!

1.) First we want to install all required packages for E17, and all the Enlightenment Foundation Libraries to install. This list may be a bit of overkill, but it will get the job done.

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
```


2.) Now that all that is out of the way we need to get the script that will make downloading/compiling/installing E17 very easy. All credit goes to Morlenxus for this great tool.

From your home directory, run the following command
```
wget http://omicron.homeip.net/projects/easy_e17/easy_e17.sh
```

3.) Now we need to made the script executable and then run it! This script will prompt you for your sudo password, enter it. This script will take quite some time to run, so try to be patient **NOTES: This script will install all the applications and libraries it installs into /opt/e17 so as not to interfere with other versions of enlightenment. You can change this location through scripts options. This script will install ALL the applications and libraries available in the E17 CVS tree. You may or may not want all these apps. You can easily skip any library or app using the --skip flag with the script.**

```
chmod +x easy_e17.sh
./easy_e17.sh -i
```

4.) Now we have enlightenment all installed and working. The next step it create a desktop entry so that you can log-in to enlightenment from GDM.

Create a desktop entry called e17.desktop
```
sudo gedit /usr/share/xsessions/e17.desktop
```

Copy/Paste the following into the newly created file
```
[Desktop Entry]
Encoding=UTF-8
Name=E-17
Comment=
Exec=/opt/e17/bin/enlightenment
Icon=
Type=Application
```

Thats all you really need to do. Now using enligthenment is as simple as logging out, selecting the E-17 session and logging back in. Any time you want to update enlightenment and related libs/apps, simply re-run the easy_e17 script. For more information on the Enlightenment Foundation Libraries, and the applications that use them, please see [http://www.get-e.org](http://www.get-e.org) and 
[http://www.enlightenment.org.au](http://www.enlightenment.org.au)
[B]
Suggestion: due to the fact that enlightenment was installed in /opt/e17 it is a good idea to add /opt/e17/bin to your PATH so that it is easier to run all those great applications you just installed.[/B]

To do this open your /etc/environment with your favorite text editor

```
sudo gedit /etc/environment
```

then add the following lines to the bottom

[CODE]PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/opt/e17/
dude does this take a long time this command  
./easy_e17.sh -i

---

### Post by Rui Pais on 2007-09-08
> **RAV TUX said:**
> following step one I get this:

```
sudo apt-get install build-essential cvs libtool libltdl3-dev automake1.9 autotools-dev libpopt-dev libcurl3-dev libx11-dev x11proto-xext-dev libbz2-dev libid3tag0-dev libpng12-dev libtiff4-dev libungif4-dev libjpeg62-dev libssl-dev libfreetype6-dev bison flex xlibs-dev gettext libimlib2-dev libxml2-dev libxcursor-dev libgtk1.2-dev autoconf pkg-config libpng3-dev libxine-dev libxkbfile-dev libsqlite3-dev giblib-dev libxmu-dev libxdamage-dev libxcomposite-dev libtag1-dev libtagc0-dev giblib-dev libasound2-dev
Reading package lists... Done
Building dependency tree       
Reading state information... Done
cvs is already the newest version.
cvs set to manual installed.
gettext is already the newest version.
gettext set to manual installed.
Package libpng3-dev is a virtual package provided by:
  libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation candidate
```what should I do about these packages?

Package libpng3-dev is a virtual package provided by:
  libpng12-dev 1.2.15~beta5-1ubuntu1
You should explicitly select one to install.
E: Package libpng3-dev has no installation

Hi RAV TUX,
do you mind to give a look at my [post #481]("http://ubuntuforums.org/showpost.php?p=3082892&postcount=481"), please.

---

### Post by RAV TUX on 2007-09-08
> **Rui Pais said:**
> Hi RAV TUX,
do you mind to give a look at my [post #481]("http://ubuntuforums.org/showpost.php?p=3082892&postcount=481"), please.

Thanks this Rui Pais, it would be really helpful if this thread could be closed and if you could start a new updated thread.

If you could start a updated thread anyway even if this thread isn't closed it would be greatly appreciated.

I'm looking at your directive now.

also please refer to this thread in general help:
[http://ubuntuforums.org/showthread.php?t=546079](http://ubuntuforums.org/showthread.php?t=546079)

---

### Post by Perfect Storm on 2007-09-08
Closed due to very outdated guide.

---

### Post by Perfect Storm on 2007-09-14
New guide check: [http://ubuntuforums.org/showthread.php?t=546746](http://ubuntuforums.org/showthread.php?t=546746)

---

