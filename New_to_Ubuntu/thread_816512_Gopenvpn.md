---
title: "Gopenvpn"
date: 2008-06-02
forum: New to Ubuntu
---

### Post by kitch on 2008-06-02
Ok, I have searched the forums and tinterweb and now I am stuck.

Has anyone tried to install gopenvpn?

[http://gopenvpn.sourceforge.net/](http://gopenvpn.sourceforge.net/) 

I am a linux virgin and I just can't work out where the application is hiding, why the /etc/openvpn folder is empty and finally and possibly most embarrassingly how to "build" the programme. I have tried but am missing something fundamental. Can't go and buy a book to learn it, I am in the desert so please help!

kitch
running feisty on an acer laptop, just killed windows with gparted...

---

### Post by wolfen69 on 2008-06-02
try [THIS]("http://monkeyblog.org/ubuntu/installing/")

---

### Post by shifty_powers on 2008-06-02
go into a terminal then:

```
sudo apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libgnome-keyring-dev gksu gedit
```

then

```
svn co https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn gopenvpn
```

then

```
cd gopenvpn
```

then

```
./autogen.sh
```

then

```
./configure
```

then

```
make
```

then

```
sudo make install
```

to run it, just tupe gopenvpn in terminal ;)

---

### Post by dracayr on 2008-06-02
well first make shure you have the prerequisites:
sudo apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libgnome-keyring-dev gksu gedit

then make shure you have subversion:

sudo apt-get install subversion

then get the source:

svn co [https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn](https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn) gopenvpn

then compile and install it:

cd gopenvpn
./autogen.sh
./configure
make

EDIT: whoops someone was faster :P

dracayr

---

### Post by shifty_powers on 2008-06-02
well yes. in other words, exactly what i said ;)

---

### Post by kitch on 2008-06-02
apart from the interesting diversion into subversion this seems to leave me in approximately the same place as before:

rob@rob-laptop:~$ sudo apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libgnome-keyring-dev gksu gedit
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libglib2.0-dev is already the newest version.
libgtk2.0-dev is already the newest version.
libglade2-dev is already the newest version.
libgnome-keyring-dev is already the newest version.
gksu is already the newest version.
gedit is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
rob@rob-laptop:~$ svn co [https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn](https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn) gopenvpn
The program 'svn' is currently not installed.  You can install it by typing:
sudo apt-get install subversion
bash: svn: command not found
rob@rob-laptop:~$ sudo apt-get install subversion
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libapr1 libaprutil1 libsvn1
Suggested packages:
  subversion-tools db4.4-util patch
The following NEW packages will be installed:
  libapr1 libaprutil1 libsvn1 subversion
0 upgraded, 4 newly installed, 0 to remove and 0 not upgraded.
Need to get 1025kB of archives.
After unpacking 5325kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Get:1 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libapr1 1.2.7-8.2ubuntu1 [112kB]
Get:2 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libaprutil1 1.2.7+dfsg-2build1 [70.2kB]
Get:3 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main libsvn1 1.4.4dfsg1-1ubuntu3 [602kB]
Get:4 [http://archive.ubuntu.com](http://archive.ubuntu.com) gutsy/main subversion 1.4.4dfsg1-1ubuntu3 [241kB]
Fetched 1025kB in 24s (42.7kB/s)                                               
Selecting previously deselected package libapr1.
(Reading database ... 108884 files and directories currently installed.)
Unpacking libapr1 (from .../libapr1_1.2.7-8.2ubuntu1_i386.deb) ...
Selecting previously deselected package libaprutil1.
Unpacking libaprutil1 (from .../libaprutil1_1.2.7+dfsg-2build1_i386.deb) ...
Selecting previously deselected package libsvn1.
Unpacking libsvn1 (from .../libsvn1_1.4.4dfsg1-1ubuntu3_i386.deb) ...
Selecting previously deselected package subversion.
Unpacking subversion (from .../subversion_1.4.4dfsg1-1ubuntu3_i386.deb) ...
Setting up libapr1 (1.2.7-8.2ubuntu1) ...

Setting up libaprutil1 (1.2.7+dfsg-2build1) ...

Setting up libsvn1 (1.4.4dfsg1-1ubuntu3) ...

Setting up subversion (1.4.4dfsg1-1ubuntu3) ...
Processing triggers for libc6 ...
ldconfig deferred processing now taking place
rob@rob-laptop:~$ svn co [https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn](https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn) gopenvpn
Error validating server certificate for 'https://gopenvpn.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? t
svn: 'gopenvpn' already exists and is not a directory
rob@rob-laptop:~$ cd gopenvpn
bash: cd: gopenvpn: Not a directory

---

### Post by kitch on 2008-06-02
> **wolfen69 said:**
> try [THIS]("http://monkeyblog.org/ubuntu/installing/")
went there before I posted here but thanks anyway.

---

### Post by shifty_powers on 2008-06-02
well, no, you can't cd into gopenvpn, as svn did not finish.

try 

```
sudo svn co https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn gopenvpn
```

---

### Post by kitch on 2008-06-02
why do I keep getting the certificate error? the same thing has just happened again. I accept temporarily but no joy...

---

### Post by shifty_powers on 2008-06-02
not sure on that one. but try this. think svn is having an issue with creating the gopenvpn folder. soooo..

```
svn co https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn gopenvpn2
```

so you would then

```
cd gopenvpn2
```

and can you post the output of the first command ;)

---

### Post by kitch on 2008-06-02
Thanks,
something worked but can't take the next step

 rob@rob-laptop:~$ sudo svn co [https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn](https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn) gopenvpn2
Error validating server certificate for 'https://gopenvpn.svn.sourceforge.net:443':
 - The certificate is not issued by a trusted authority. Use the
   fingerprint to validate the certificate manually!
Certificate information:
 - Hostname: *.svn.sourceforge.net
 - Valid: from Tue, 09 Oct 2007 14:15:07 GMT until Mon, 08 Dec 2008 15:15:07 GMT
 - Issuer: Equifax Secure Certificate Authority, Equifax, US
 - Fingerprint: fb:75:6c:40:58:ae:21:8c:63:dd:1b:7b:6a:7d:bb:8c:74:36:e7:8a
(R)eject, accept (t)emporarily or accept (p)ermanently? t
A    gopenvpn2/trunk
A    gopenvpn2/trunk/gopenvpn
A    gopenvpn2/trunk/gopenvpn/pixmaps
A    gopenvpn2/trunk/gopenvpn/pixmaps/gopenvpn-connecting.png
A    gopenvpn2/trunk/gopenvpn/pixmaps/gopenvpn-closed.png
A    gopenvpn2/trunk/gopenvpn/pixmaps/Makefile.am
A    gopenvpn2/trunk/gopenvpn/pixmaps/gopenvpn-blink.png
A    gopenvpn2/trunk/gopenvpn/pixmaps/gopenvpn-open.png
A    gopenvpn2/trunk/gopenvpn/configure.ac
A    gopenvpn2/trunk/gopenvpn/AUTHORS
A    gopenvpn2/trunk/gopenvpn/TODO
A    gopenvpn2/trunk/gopenvpn/INSTALL
A    gopenvpn2/trunk/gopenvpn/ChangeLog
A    gopenvpn2/trunk/gopenvpn/src
A    gopenvpn2/trunk/gopenvpn/src/eggtrayicon.h
A    gopenvpn2/trunk/gopenvpn/src/gopenvpn.h
A    gopenvpn2/trunk/gopenvpn/src/gopenvpn.glade
A    gopenvpn2/trunk/gopenvpn/src/gopenvpn.gladep
A    gopenvpn2/trunk/gopenvpn/src/Makefile.am
A    gopenvpn2/trunk/gopenvpn/src/gopenvpnstart.c
A    gopenvpn2/trunk/gopenvpn/src/eggtrayicon.c
A    gopenvpn2/trunk/gopenvpn/src/gopenvpn.c
A    gopenvpn2/trunk/gopenvpn/.svnignore
A    gopenvpn2/trunk/gopenvpn/COPYING
A    gopenvpn2/trunk/gopenvpn/Makefile.am
A    gopenvpn2/trunk/gopenvpn/autogen.sh
A    gopenvpn2/trunk/gopenvpn/NEWS
A    gopenvpn2/trunk/gopenvpn/README
A    gopenvpn2/trunk/gopenvpn/po
A    gopenvpn2/trunk/gopenvpn/po/fr.po
A    gopenvpn2/trunk/gopenvpn/po/POTFILES.in
A    gopenvpn2/trunk/gopenvpn/po/POTFILES.skip
Checked out revision 1.
rob@rob-laptop:~$ cd gopenvpn2
rob@rob-laptop:~/gopenvpn2$ ./autogen.sh
bash: ./autogen.sh: No such file or directory

---

### Post by shifty_powers on 2008-06-02
heh, oh dear

right do

```
ls
```

when you are in gopenvpn2 ;) oh and post the contents :D

---

### Post by dracayr on 2008-06-02
or maybe try 
```
cd trunk/gopenvpn
./autogen.sh
```

because that's where autogen.sh *should* be

dracayr

---

### Post by kitch on 2008-06-02
We are gaining on it slowly... I guess I need to install automake, autoconf and intltool?

rob@rob-laptop:~/gopenvpn2$ ls
trunk
rob@rob-laptop:~/gopenvpn2$ cd trunk
rob@rob-laptop:~/gopenvpn2/trunk$ ls
gopenvpn
rob@rob-laptop:~/gopenvpn2/trunk$ cd gopenvpn
rob@rob-laptop:~/gopenvpn2/trunk/gopenvpn$ ls
AUTHORS     ChangeLog     COPYING  Makefile.am  pixmaps  README  TODO
autogen.sh  configure.ac  INSTALL  NEWS         po       src
rob@rob-laptop:~/gopenvpn2/trunk/gopenvpn$ ./autogen.sh

checking for autoconf >= 2.53...

  testing autoconf2.50... 
not found.
  testing autoconf... 
not found.
  testing autoconf-2.53... 
not found.
***Error***: You must have autoconf >= 2.53 installed
  to build Package.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/autoconf/autoconf-2.53.tar.gz](http://ftp.gnu.org/pub/gnu/autoconf/autoconf-2.53.tar.gz)


checking for automake >= 1.9...

  testing automake-1.9... 
not found.
***Error***: You must have automake >= 1.9 installed
  to build Package.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz](http://ftp.gnu.org/pub/gnu/automake/automake-1.9.tar.gz)


checking for glib-gettext >= 2.2.0...

  testing glib-gettextize... 
found 2.14.1

checking for intltool >= 0.30...

  testing intltoolize... 
not found.
***Error***: You must have intltool >= 0.30 installed
  to build Package.  Download the appropriate package for
  from your distribution or get the source tarball at
    [http://ftp.gnome.org/pub/GNOME/sources/intltool/](http://ftp.gnome.org/pub/GNOME/sources/intltool/)


checking for pkg-config >= 0.14.0...

  testing pkg-config... 
found 0.22
./autogen.sh: 347: --print-ac-dir: not found
ACLOCAL=''
AUTOHEADER=''
COLORTERM='gnome-terminal'
DBUS_SESSION_BUS_ADDRESS='unix:abstract=/tmp/dbus-HXjXrBqaFx,guid=572d4e9ca9b691c5c9974900484418ba'
DESKTOP_SESSION='default'
DESKTOP_STARTUP_ID=''
DIE='1'
DISPLAY=':0.0'
ECHO_N=''
FORBIDDEN_M4MACROS=' gnome-cxx-check.m4'
GDMSESSION='default'
GDM_LANG='en_US.UTF-8'
GDM_XSERVER_LOCATION='local'
GLIB_GETTEXTIZE='glib-gettextize'
GLIB_GETTEXTIZE_VERSION='2.14.1'
GNOME_DESKTOP_SESSION_ID='Default'
GNOME_KEYRING_PID='5210'
GNOME_KEYRING_SOCKET='/tmp/keyring-65LhYp/socket'
GTK_RC_FILES='/etc/gtk/gtkrc:/home/rob/.gtkrc-1.2-gnome2'
HISTCONTROL='ignoreboth'
HOME='/home/rob'
IFS='.'
LANG='en_US.UTF-8'
LESSCLOSE='/usr/bin/lesspipe %s %s'
LESSOPEN='| /usr/bin/lesspipe %s'
LOGNAME='rob'
LS_COLORS='no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:'
OLDPWD='/home/rob/gopenvpn2/trunk'
OPTIND='1'
PATH='/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games'
PKG_CONFIG='pkg-config'
PKG_CONFIG_VERSION='0.22'
PKG_NAME='Package'
PPID='7170'
PS1='$ '
PS2='> '
PS4='+ '
PWD='/home/rob/gopenvpn2/trunk/gopenvpn'
REQUIRED_AUTOCONF_VERSION='2.53'
REQUIRED_AUTOMAKE_VERSION='1.9'
REQUIRED_DOC_COMMON_VERSION='2.3.0'
REQUIRED_GETTEXT_VERSION='0.12'
REQUIRED_GLIB_GETTEXT_VERSION='2.2.0'
REQUIRED_GNOME_DOC_UTILS_VERSION='0.4.2'
REQUIRED_GTK_DOC_VERSION='1.0'
REQUIRED_INTLTOOL_VERSION='0.30'
REQUIRED_LIBTOOL_VERSION='1.5'
REQUIRED_M4MACROS=' glib-gettext.m4 intltool.m4 pkg.m4'
REQUIRED_PKG_CONFIG_VERSION='0.14.0'
SESSION_MANAGER='local/rob-laptop:/tmp/.ICE-unix/5213'
SHELL='/bin/bash'
SHLVL='1'
SSH_AGENT_PID='5250'
SSH_AUTH_SOCK='/tmp/ssh-eLHUod5213/agent.5213'
TERM='xterm'
USER='rob'
USERNAME='rob'
WANT_AUTOCONF_2_5='1'
WINDOWID='54526047'
WINDOWPATH='7'
XAUTHORITY='/home/rob/.Xauthority'
XDG_DATA_DIRS='/usr/local/share/:/usr/share/:/usr/share/gdm/'
XDG_SESSION_COOKIE='44b431768c51da0143fe640047ecfa00-1212422328.147447-1264280037'
_='./autogen.sh'
automake_progs='automake-1.9'
boldface=''
ch_actual_version=''
ch_cur='22'
ch_min='14'
ch_min_version='1.7'
ch_save_IFS=' 
'
ch_status='0'
cm_macrodirs=''
configure_ac='./configure.ac'
configure_files='./configure.ac'
normal=''
srcdir='.'
vc_actual_version='0.22'
vc_checkprog='pkg-config'
vc_checkprogs='pkg-config'
vc_comparator='>='
vc_min_version='0.14.0'
vc_package='pkg-config'
vc_source=''"'"'http://www.freedesktop.org/software/pkgconfig/releases/pkgconfig-0.14.0.tar.gz'
vc_status='0'
vc_variable='PKG_CONFIG'
want_gettext='false'
want_glib_gettext='true'
want_gnome_doc_utils='false'
want_gtk_doc='false'
want_intltool='true'
want_libtool='false'
want_pkg_config='true'
shift: 347: can't shift that many
rob@rob-laptop:~/gopenvpn2/trunk/gopenvpn$ ./configure
bash: ./configure: No such file or directory
rob@rob-laptop:~/gopenvpn2/trunk/gopenvpn$

---

### Post by dracayr on 2008-06-02
try 
```
./configure.ac
```
instead of
```
./configure
```

you would probably also have to do

```
make Makefile.am
```

dracayr

---

### Post by kitch on 2008-06-02
No such file or directory

will install the missing programs and see if it helps.

Kitch

---

### Post by kitch on 2008-06-04
installed the missing programs and some excitement followed. The forum went down and i went out...
currently trying to deal with this:

Running glib-gettextize... Ignore non-fatal messages.

Copying file mkinstalldirs
Copying file po/Makefile.in.in

Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
[ftp://ftp.gnu.org/pub/gnu/config/](ftp://ftp.gnu.org/pub/gnu/config/).

somewhat confused where do i put them when i find them?

---

### Post by eugen_nicoara on 2008-09-24
I tried to install gopenvpn. I had a few problems with some missing packages and I solved them by my own. That's the last one and I have absolutely no idea how to solve it:

```

./autogen.sh 
configure.ac:4: installing `./install-sh'
configure.ac:4: installing `./missing'
src/Makefile.am: installing `./depcomp'
configure.ac:5: required file `config.h.in' not found

```

autogen.sh looks like this:

```

#! /bin/sh
aclocal \
&& automake --gnu --add-missing \
&& autoconf

```

and these are the first five lines in configure.ac:

```

AC_INIT(gopenvpn, 0.1)
AC_CONFIG_SRCDIR(src/gopenvpn.c)
AC_PREREQ(2.57)
AM_INIT_AUTOMAKE
AM_CONFIG_HEADER(config.h)
.............

```

Please tell me where should I find config.h.
Thanks!

---

### Post by bretticus on 2008-09-27
Hi, I am not a c coder either and struggled for about a half hour getting this program to build. Here is what I did step-by-step

```
$ sudo apt-get install libglib2.0-dev libgtk2.0-dev libglade2-dev libgnome-keyring-dev gksu subversion build-essential autogen automake autoconf intltool
```

```
svn co https://gopenvpn.svn.sourceforge.net/svnroot/gopenvpn gopenvpn
```
```

cd gopenvpn/trunk/gopenvpn/
```

```
autoheader
```

Above got rid of that "configure.ac:5: required file `config.h.in' not found" message :)

```
autogen
```

```
intltoolize
```

Above got rid of the intltoolize configure error.

```
./configure
make
sudo make install
```

enjoy!

---

### Post by bretticus on 2008-09-27
Oh, and by the way, this is EXACTLY what I've been looking for! Works great. Now I can just right-click connect/discconnect instead of opening a terminal and running a bash script (control-z bg, etc.) A huge thanks goes out to Gary Grossman!

---

### Post by eugen_nicoara on 2008-09-29
Problem solved. Thank you bretticus!

---

### Post by franzpv on 2008-10-29
> **bretticus said:**
> Oh, and by the way, this is EXACTLY what I've been looking for! Works great. Now I can just right-click connect/discconnect instead of opening a terminal and running a bash script (control-z bg, etc.) A huge thanks goes out to Gary Grossman!

Tried using your instructions....but when I execute "autogen",nothing seems to happen.

---

### Post by TalynOne on 2008-12-26
gopenvpn with Intrepid tutorial here:

[http://ubuntuforums.org/showthread.php?t=1021592](http://ubuntuforums.org/showthread.php?t=1021592)

---

### Post by mac-duff on 2009-09-21
thx for this. Have a lot of trouble with the gnome networkmanager and disconnects. Will give this a try

Thx

---

