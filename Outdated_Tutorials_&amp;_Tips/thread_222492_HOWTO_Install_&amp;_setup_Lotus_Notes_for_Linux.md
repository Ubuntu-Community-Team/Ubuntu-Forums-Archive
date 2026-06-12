---
title: "HOWTO: Install &amp; setup Lotus Notes for Linux"
date: 2006-07-25
forum: Outdated Tutorials &amp; Tips
---

### Post by malmo on 2006-07-25
**Get package**
The best way is to get it from Partnerworld program.
Name of package is: C93D1NA.zip

**Prerequisites**
1, install mozilla package - should be >= 1.7.12 (apt-get install mozilla-browser)
2, create symlink to mozilla binary (ln -sf /usr/bin/mozilla-suite /usr/bin/mozilla)
3, edit /etc/gre.d/gre.conf to match your mozilla version (you can also add symlink /etc/gre.conf)
insert:
```

[1.7.13]
GRE_PATH=/usr/lib/mozilla

```
4, Get Gnome libraries (I'm not sure which ones - i got Gnome as alternative Desktop)

**Install**
1, unpack C93D1NA.zip (unzip -d lotus C93D1NA.zip)
2, unpack Personality.zip
3, chmod +x on lotus/setup_wct_platform.bin and setuplinux.bin
4, copy setuplinux.bin to updateSite/features/com.ibm.workplace.notesinstall.linux.feature_7.0.1.0000-0900/bin/linux/
5, run installer ./lotus/setup_wct_platform.bin as non-root user (it'll be a little bit complicated installing it as root, but it's possible)
6, as first, there will be Workplace Manged Client installed (agree to
 licenses, set install path etc. to install it - don't forget to set privileges on install dirs ;-) ) and then you will be asked to install Lotus Notes Client plug-in, so be patient. At the end launch icon will be installed to your desktop.
7, after installation, empty client will be started so don't panic ;-)
8, close client

**Setup**
To start client correctly, you have to make some environment settings:
$CLASSPATH pointing to the top-level installation directory.
Add the top-level installation directory, and jvm/bin to your path 
Set $NOTESDIR to the data subdirectory of the top-level installation directory 
Set $NOTESBIN to the top-level installation directory 
Add the subdirectories jvm/bin/classic, jvm/bin and the top-level installation directory to $LD_LIBRARY_PATH
```

example:

NOTESBIN=/home/malmo/notes
NOTESDATA=/home/malmo/notes/data
NOTESDIR=/home/malmo/notes/data

LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRARY_PATH

PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH

CLASSPATH=./:$NOTESBIN/:$CLASSPATH

export NOTESBIN NOTESDATA NOTESDIR LD_LIBRARY_PATH PATH CLASSPATH


```
The way you do it is up to you ;-)
**KDE:**
I've put those variables into file (.notesrc) & sourcing it before launch of main app. 
```

(command section in desktop file:
. /home/malmo/.notesrc;/opt/ibm/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality)

```
**Gnome:**
Create script to launch notes
e.g. /home/malmo/bin/notesstart 
```

#!/bin/sh

NOTESBIN=/home/malmo/notes
NOTESDATA=/home/malmo/notes/data
NOTESDIR=/home/malmo/notes/data
LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRARY_PATH
PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH
CLASSPATH=./:$NOTESBIN/:$CLASSPATH
export NOTESBIN NOTESDATA NOTESDIR LD_LIBRARY_PATH PATH CLASSPATH

/opt/ibm/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality

```

chmod 755 notesstart

now you can edit launcher icon to point to script

**Final:**
Then, after launching application you should be able to setup Lotus Notes common way - LotusNotes wizard will pop-up.

Enjoy ;-)

---

### Post by evilcartman on 2006-07-25
Malmo,

Excellent Howto! However, even after following this when I launched the client the way you specify, I got the empty two pane window and setup never started.  To fix this, change all of the statements in your .notesrc file to start with "export <VARIABLE> = <VALUE>".  E.g., "export NOTESBIN=/home/malmo/notes".  After making this change and then starting Notes, setup appears and now I'm up and running.  Thanks again :)

---

### Post by loupy on 2006-07-25
I followed the instructions but I get the following errors

If running the launcher as *". /home/loupy/.notesrc;/opt/ibm/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality"*

**"Details: Failed to execute child process "." (Permission denied)"**

If I run the launcher as *"./home/loupy/.notesrc;/opt/ibm/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality"* (no space in between first 2 characters)

**Details: Failed to execute child process "./home/loupy/.notesrc;/opt/ibm/Workplace Managed Client/rcp/richclient" (No such file or directory)**

If I remove the first part and do the export first from the cli I get the same empty 2 pane app and no way of setting it up ](*,)


EDIT: There is no space in "personality"  I am not sure why it's showing up that way when I post.

---

### Post by evilcartman on 2006-07-25
Loupy,

It may be that you are missing a library needed for setup?  If you run the following command:

```
. ~/.notesrc; ldd ~/notes/lnotes
```

Do you see any entries with "File not found"?  If so, then you may be missing a library or there is a problem with the environment settings in the .notesrc file.

---

### Post by malmo on 2006-07-26
Thanks for feedback. The code should be noow correct:-)

---

### Post by malmo on 2006-07-26
Loupy,

in fact, this space between "." an path to file with envs is important, as it means taht this file should be sourced. Other way how to do it, is to use "source /home/loupy/.notesrc". Maybe this'll help you.

---

### Post by loupy on 2006-07-26
I tried doing the source command from the cli and there are no missing files when I run "~/.notesrc; ldd ~/notes/lnotes" I am so lost on how to get this working. :???: 

```
loupy@ubuntu32:~$ . ~/.notesrc; ldd ~/notes/lnotes
        linux-gate.so.1 =>  (0xffffe000)
        libnotes.so => /home/loupy/notes/libnotes.so (0xb6347000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb6334000)
        libXm.so.3 => not found
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb62e6000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb6200000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb61fd000)
        libemulator.so => /home/loupy/notes/libemulator.so (0xb604b000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb6038000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb6025000)
        libjvm.so => /home/loupy/notes/jvm/bin/classic/libjvm.so (0xb5e09000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb5d4f000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb5d2d000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb5bfe000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb5bf3000)
        libndgts.so => /home/loupy/notes/libndgts.so (0xb5bf1000)
        libxmlproc.so => /home/loupy/notes/libxmlproc.so (0xb567f000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb55fb000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb55f3000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb55eb000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb55d2000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb55cf000)
        /lib/ld-linux.so.2 (0xb7fd3000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb52fa000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb527d000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb5264000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb524e000)
        libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb5248000)
        libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb523d000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb5205000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb51cd000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb51ca000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb51c5000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb51bc000)
        libcups.so.2 => /usr/lib/libcups.so.2 (0xb518f000)
        libpsprint.so => /home/loupy/notes/libpsprint.so (0xb5076000)
        libgnomeprint-2-2.so.0 => /usr/lib/libgnomeprint-2-2.so.0 (0xb5014000)
        libgnomeprintui-2-2.so.0 => /usr/lib/libgnomeprintui-2-2.so.0 (0xb4fdd000)
        libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb4f81000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb4f79000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb4f33000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb4f05000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb4ef7000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb4eef000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb4eec000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb4ee4000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb4ee1000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb4edd000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb4eb8000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb4ea6000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb4e3d000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb4e29000)
        libgnutls.so.12 => /usr/lib/libgnutls.so.12 (0xb4dc0000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb4d92000)
        libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb4d7d000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb4c6e000)
        libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb4c45000)
        libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb4c15000)
        libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb4bbd000)
        libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb4ba9000)
        libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb4b58000)
        libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0xb4b55000)
        libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0xb4b4b000)
        libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0xb4b3c000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb4b38000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb4b15000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb4af6000)
        libtasn1.so.2 => /usr/lib/libtasn1.so.2 (0xb4ae6000)
        libgcrypt.so.11 => /usr/lib/libgcrypt.so.11 (0xb4a99000)
        libgpg-error.so.0 => /usr/lib/libgpg-error.so.0 (0xb4a95000)
        libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb4a91000)
        libpopt.so.0 => /lib/libpopt.so.0 (0xb4a89000)
        libdbus-1.so.2 => /usr/lib/libdbus-1.so.2 (0xb4a51000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb4a3c000)
```

EDIT - I found the problem - I needed libmotif3 installed

---

### Post by jshein on 2006-07-26
The install worked perfectly. Thank You for this HOWTO.

One little issue..

"Set up Lotus Notes common way"

What is required for the URL ?? Normally in a windows client we point it at the domino server hostname or ip. It says "invalid url" if I do that.

Any ideas?

Is there maybe something additional that needs to be done on the server prior to using the linux client?

---

### Post by johannagnarsson on 2006-07-26
First I'd like to say Great Guide! to malmo.
I'm having some trouble with getting notes to run properly though.
I installed Notes on a RHEL WS(vmware) and got it running without too much trouble but when I try installing on my Ubuntu Dapper workstation Lotus Notes crashes immediately(sp?) and starts NSD.


This is the output:
```

ld_library_path_value -->/home/johann/notes:/home/johann/notes/jvm/bin/classic:/usr/lib:/usr/lib/mozilla
setPreload():libraryDirPath:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/
SSH_AGENT_PID=16293
TERM=xterm
DESKTOP_STARTUP_ID=
SHELL=/bin/bash
GTK_RC_FILES=/etc/gtk/gtkrc:/home/johann/.gtkrc-1.2-gnome2
WINDOWID=44078035
OLDPWD=/home/johann/bin
USER=johann
LD_LIBRARY_PATH=/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/:/home/johann/notes:/home/johann/notes/jvm/bin/classic:/usr/lib:/usr/lib/mozilla
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
GNOME_KEYRING_SOCKET=/tmp/keyring-c8DHHU/socket
SSH_AUTH_SOCK=/tmp/ssh-jcxEd16246/agent.16246
SESSION_MANAGER=local/johann-desktop:/tmp/.ICE-unix/16246
USERNAME=johann
DESKTOP_SESSION=gnome
PATH=/home/johann/notes//jvm/bin:/home/johann/notes/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
GDM_XSERVER_LOCATION=local
PWD=/home/johann
NOTESBIN=/home/johann/notes/
NOTESDIR=/home/johann/notes/data/
LANG=en_US.UTF-8
GDMSESSION=gnome
HISTCONTROL=ignoredups
HOME=/home/johann
SHLVL=1
LANGUAGE=en_US:en_GB:en
NOTESDATA=/home/johann/notes/data/
GNOME_DESKTOP_SESSION_ID=Default
LOGNAME=johann
CLASSPATH=./:/home/johann/notes//:
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-yc4SDDuOUE,guid=3baec7449cbeed842fd3c8829eb7e200
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
COLORTERM=gnome-terminal
XAUTHORITY=/home/johann/.Xauthority
_=/opt/IBM/Workplace Managed Client/rcp/richclient
JAVA_HIGH_ZIPFDS=500
MOZILLA_FIVE_HOME=/usr/../usr/lib/mozilla
/home/johann/notes:/home/johann/notes/jvm/bin/classic:/usr/lib:/usr/lib/mozilla=/home/johann/notes:/home/johann/notes/jvm/bin/classic:/usr/lib:/usr/lib/mozilla:/usr/../usr/lib/mozilla
LD_PRELOAD=libjsig.so

notes: LD_LIBRARY_PATH = /home/johann/notes:/home/johann/notes/jvm/bin/classic:/home/johann/notes/jvm/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/j9vm:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/johann/notes:/home/johann/notes/jvm/bin/classic:/usr/lib:/usr/lib/mozilla:/usr/../usr/lib/mozilla
nsdexec: notespid = 21052

(<unknown>:21052): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
DbFree: Freeing already-deallocated storage in /home/johann/notes/data/desktop6.ndk (Pos=532, Size=256)!
GetACP returns 1252

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:21052): Pango-WARNING **: Error loading GPOS table 4097
DbFree: Freeing already-deallocated storage in /home/johann/notes/data/Cache.NDK (Pos=532, Size=256)!


07/26/2006 06:45:59 PM  Lotus Notes client started
Stack base = 0xbfb83ddc, Stack size = 6348 bytes
Fatal Error signal = 0x0000000b PID/TID = 21052/-1267439936
7/26/2006 18:45:59  Running NSD

(nsdexec:21053): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
NSD is in progress .................

Please attach the following files to your bug report along with the server log:
Log file                : /home/johann/notes/data/IBM_TECHNICAL_SUPPORT/nsd_Linux_johann-desktop_2006_07_26@18_46_01.log
7/26/2006 18:46:32  Termination is in progress
7/26/2006 18:46:32  Terminating tasks
johann@johann-desktop:~$ 7/26/2006 18:46:42  Freeing resources
7/26/2006 18:46:42  Termination completed


```

Here is my ldd of ~/notes/lnotes:

```

johann@johann-desktop:~$ ldd notes/lnotes
        linux-gate.so.1 =>  (0xffffe000)
        libnotes.so => /home/johann/notes/libnotes.so (0xb630c000)
        libXp.so.6 => /usr/lib/libXp.so.6 (0xb6304000)
        libXm.so.3 => /usr/lib/libXm.so.3 (0xb60ce000)
        libXt.so.6 => /usr/lib/libXt.so.6 (0xb6080000)
        libX11.so.6 => /usr/lib/libX11.so.6 (0xb5f9a000)
        libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb5f88000)
        libemulator.so => /home/johann/notes/libemulator.so (0xb5dd6000)
        libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb5dc3000)
        libresolv.so.2 => /lib/tls/i686/cmov/libresolv.so.2 (0xb5db0000)
        libjvm.so => /home/johann/notes/jvm/bin/classic/libjvm.so (0xb5b94000)
        libstdc++.so.5 => /usr/lib/libstdc++.so.5 (0xb5ada000)
        libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb5ab8000)
        libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb5989000)
        libgcc_s.so.1 => /lib/libgcc_s.so.1 (0xb597e000)
        libndgts.so => /home/johann/notes/libndgts.so (0xb597c000)
        libxmlproc.so => /home/johann/notes/libxmlproc.so (0xb540a000)
        libglib-2.0.so.0 => /usr/lib/libglib-2.0.so.0 (0xb5386000)
        librt.so.1 => /lib/tls/i686/cmov/librt.so.1 (0xb537e000)
        libXmu.so.6 => /usr/lib/libXmu.so.6 (0xb5368000)
        libSM.so.6 => /usr/lib/libSM.so.6 (0xb5360000)
        libICE.so.6 => /usr/lib/libICE.so.6 (0xb5348000)
        libXext.so.6 => /usr/lib/libXext.so.6 (0xb533b000)
        libXau.so.6 => /usr/lib/libXau.so.6 (0xb5338000)
        /lib/ld-linux.so.2 (0xb7f98000)
        libgtk-x11-2.0.so.0 => /usr/lib/libgtk-x11-2.0.so.0 (0xb5063000)
        libgdk-x11-2.0.so.0 => /usr/lib/libgdk-x11-2.0.so.0 (0xb4fe5000)
        libatk-1.0.so.0 => /usr/lib/libatk-1.0.so.0 (0xb4fcc000)
        libgdk_pixbuf-2.0.so.0 => /usr/lib/libgdk_pixbuf-2.0.so.0 (0xb4fb7000)
        libpangoxft-1.0.so.0 => /usr/lib/libpangoxft-1.0.so.0 (0xb4fb1000)
        libpangox-1.0.so.0 => /usr/lib/libpangox-1.0.so.0 (0xb4fa6000)
        libpango-1.0.so.0 => /usr/lib/libpango-1.0.so.0 (0xb4f6e000)
        libgobject-2.0.so.0 => /usr/lib/libgobject-2.0.so.0 (0xb4f35000)
        libgmodule-2.0.so.0 => /usr/lib/libgmodule-2.0.so.0 (0xb4f32000)
        libgthread-2.0.so.0 => /usr/lib/libgthread-2.0.so.0 (0xb4f2e000)
        libXcursor.so.1 => /usr/lib/libXcursor.so.1 (0xb4f25000)
        libcups.so.2 => /usr/lib/libcups.so.2 (0xb4ef8000)
        libpsprint.so => /home/johann/notes/libpsprint.so (0xb4ddf000)
        libgnomeprint-2-2.so.0 => /usr/lib/libgnomeprint-2-2.so.0 (0xb4d7c000)
        libgnomeprintui-2-2.so.0 => /usr/lib/libgnomeprintui-2-2.so.0 (0xb4d45000)
        libgnomevfs-2.so.0 => /usr/lib/libgnomevfs-2.so.0 (0xb4cea000)
        libpangocairo-1.0.so.0 => /usr/lib/libpangocairo-1.0.so.0 (0xb4ce2000)
        libcairo.so.2 => /usr/lib/libcairo.so.2 (0xb4c80000)
        libfontconfig.so.1 => /usr/lib/libfontconfig.so.1 (0xb4c52000)
        libXrender.so.1 => /usr/lib/libXrender.so.1 (0xb4c4a000)
        libXinerama.so.1 => /usr/lib/libXinerama.so.1 (0xb4c47000)
        libXi.so.6 => /usr/lib/libXi.so.6 (0xb4c3f000)
        libXrandr.so.2 => /usr/lib/libXrandr.so.2 (0xb4c3c000)
        libXfixes.so.3 => /usr/lib/libXfixes.so.3 (0xb4c36000)
        libpangoft2-1.0.so.0 => /usr/lib/libpangoft2-1.0.so.0 (0xb4c12000)
        libXft.so.2 => /usr/lib/libXft.so.2 (0xb4c00000)
        libfreetype.so.6 => /usr/lib/libfreetype.so.6 (0xb4b97000)
        libz.so.1 => /usr/lib/libz.so.1 (0xb4b83000)
        libgnutls.so.12 => /usr/lib/libgnutls.so.12 (0xb4b19000)
        libcrypt.so.1 => /lib/tls/i686/cmov/libcrypt.so.1 (0xb4aec000)
        libart_lgpl_2.so.2 => /usr/lib/libart_lgpl_2.so.2 (0xb4ad7000)
        libxml2.so.2 => /usr/lib/libxml2.so.2 (0xb49c8000)
        libgnomecanvas-2.so.0 => /usr/lib/libgnomecanvas-2.so.0 (0xb499f000)
        libgconf-2.so.4 => /usr/lib/libgconf-2.so.4 (0xb496e000)
        libbonobo-2.so.0 => /usr/lib/libbonobo-2.so.0 (0xb4917000)
        libbonobo-activation.so.4 => /usr/lib/libbonobo-activation.so.4 (0xb4903000)
        libORBit-2.so.0 => /usr/lib/libORBit-2.so.0 (0xb48b2000)
        libavahi-glib.so.1 => /usr/lib/libavahi-glib.so.1 (0xb48af000)
        libavahi-common.so.3 => /usr/lib/libavahi-common.so.3 (0xb48a5000)
        libavahi-client.so.3 => /usr/lib/libavahi-client.so.3 (0xb4895000)
        libutil.so.1 => /lib/tls/i686/cmov/libutil.so.1 (0xb4892000)
        libpng12.so.0 => /usr/lib/libpng12.so.0 (0xb486f000)
        libglitz.so.1 => /usr/lib/libglitz.so.1 (0xb484a000)
        libexpat.so.1 => /usr/lib/libexpat.so.1 (0xb482b000)
        libtasn1.so.2 => /usr/lib/libtasn1.so.2 (0xb481a000)
        libgcrypt.so.11 => /usr/lib/libgcrypt.so.11 (0xb47ce000)
        libgpg-error.so.0 => /usr/lib/libgpg-error.so.0 (0xb47ca000)
        libORBitCosNaming-2.so.0 => /usr/lib/libORBitCosNaming-2.so.0 (0xb47c6000)
        libpopt.so.0 => /lib/libpopt.so.0 (0xb47be000)
        libdbus-1.so.2 => /usr/lib/libdbus-1.so.2 (0xb4786000)
        libnsl.so.1 => /lib/tls/i686/cmov/libnsl.so.1 (0xb4771000)

```

So if anyone has any idea about why notes crashes immediately I'd be grateful for any tips.

:edit:
p.s I should point out that I can start the WMC without problems if the environmental settings for Lotus Notes are not set.

---

### Post by evilcartman on 2006-07-26
jshein,

No URL is required.  If all the prerequisites are installed and all environment variables set correctly (particularly LD_LIBRARY_PATH), then setup should appear after you launch the Workplace client.  The setup dialogs are equivalent to the initial setup for the Windows Notes client.

---

### Post by malmo on 2006-07-27
OK, it looks like most of your troubles are my fault (mea culpa) :-)
I'm mostly kubuntu(KDE) fan.
So, now, I've started Gnome to check it.
THIS should be working:
create script to launch notes e.g. /home/user/bin/notesstart 
```

#!/bin/sh

NOTESBIN=/home/malmo/notes
NOTESDATA=/home/malmo/notes/data
NOTESDIR=/home/malmo/notes/data
LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRARY_PATH
PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH
CLASSPATH=./:$NOTESBIN/:$CLASSPATH
export NOTESBIN NOTESDATA NOTESDIR LD_LIBRARY_PATH PATH CLASSPATH

/opt/ibm/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality

```

chmod 755 notesstart

now you can edit launcher icon to point to script

I hope, that this is final ;-)

---

### Post by marinoj on 2006-07-27
I'm using Debian unstable and noticed that the Notes installer created a .bash_profile file in my home directory that sets all these environment vars ... problem is that I'm using gdm to login so the contents of .bash_profile never get executed.  However, the settings are all there for the picking - straight from the source - if anyone is interested :)

---

### Post by jan_123 on 2006-07-27
Malmo,

Thanks for the excellent HOWTO! 

I followed the guideline and installed everything on Dapper Dake 6.06 without any problems, but I get an annoying crash when starting the Application via the scipt:



[INDENT]jan@jan-ubuntu-desktop:~/bin$ ./notesstarter
ld_library_path_value -->/home/jan/notes:/home/jan/notes/jvm/bin/classic:/home/j an/notes/jvm/bin:
setPreload():libraryDirPath:/opt/IBM/Workplace Managed Client/rcp/eclipse/featur es/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/
SSH_AGENT_PID=4981
SHELL=/bin/bash
DESKTOP_STARTUP_ID=
TERM=xterm
GTK_RC_FILES=/etc/gtk/gtkrc:/home/jan/.gtkrc-1.2-gnome2
WINDOWID=62914652
USER=jan
http_proxy=http://****.******.de:3128/
LD_LIBRARY_PATH=/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.r cp.jre.linux.feature_1.3.0/jre/bin/:/home/jan/notes:/home/jan/notes/jvm/bin/clas sic:/home/jan/notes/jvm/bin:
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:c d=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.t ar=01;31:*.tgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.zip=01;31:*.z=01;31:* .Z=01;31:*.gz=01;31:*.bz2=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.jpg=01;35: *.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=0 1;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.mov=01;35:*. mpg=01;35:*.mpeg=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35 :*.xwd=01;35:*.flac=01;35:*.mp3=01;35:*.mpc=01;35:*.ogg=01;35:*.wav=01;35:
SSH_AUTH_SOCK=/tmp/ssh-TaRDVC4935/agent.4935
GNOME_KEYRING_SOCKET=/tmp/keyring-qr2PP5/socket
USERNAME=jan
SESSION_MANAGER=local/jan-ubuntu-desktop:/tmp/.ICE-unix/4935
PATH=/home/jan/notes/jvm/bin:/home/jan/notes:/usr/local/sbin:/usr/local/bin:/usr /sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games
DESKTOP_SESSION=default
GDM_XSERVER_LOCATION=local
PWD=/home/jan/bin
NOTESBIN=/home/jan/notes
NOTESDIR=/home/jan/notes/data
LANG=de_DE.UTF-8
GDMSESSION=default
HISTCONTROL=ignoredups
SHLVL=2
HOME=/home/jan
LANGUAGE=de_DE:de:en_GB:en
NOTESDATA=/home/jan/notes/data
GNOME_DESKTOP_SESSION_ID=Default
no_proxy=localhost,127.0.0.0/8,*.local,192.168.132.45
LOGNAME=jan
CLASSPATH=./:/home/jan/notes/:
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-HmANGcADgY,guid=ef98c8445611d67 edbaca01d8e153000
LESSOPEN=| /usr/bin/lesspipe %s
DISPLAY=:0.0
LESSCLOSE=/usr/bin/lesspipe %s %s
XAUTHORITY=/home/jan/.Xauthority
COLORTERM=gnome-terminal
_=/opt/IBM/Workplace Managed Client/rcp/richclient
JAVA_HIGH_ZIPFDS=500
MOZILLA_FIVE_HOME=/usr/../usr/lib/mozilla
/home/jan/notes:/home/jan/notes/jvm/bin/classic:/home/jan/notes/jvm/bin:=/home/j an/notes:/home/jan/notes/jvm/bin/classic:/home/jan/notes/jvm/bin::/usr/../usr/li b/mozilla
LD_PRELOAD=libjsig.so

notes: LD_LIBRARY_PATH = /home/jan/notes:/home/jan/notes/jvm/bin/classic:/home/j an/notes/jvm/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm. rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclips e/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Manage d Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/j9vm:/ opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feat ure_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm .rcp.jre.linux.feature_1.3.0/jre/bin:/home/jan/notes:/home/jan/notes/jvm/bin/cla ssic:/home/jan/notes/jvm/bin:/usr/../usr/lib/mozilla
nsdexec: notespid = 7805

(<unknown>:7805): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
GetACP returns 1252

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097

(<unknown>:7805): Pango-WARNING **: Error loading GPOS table 4097


27.07.2006 12:58:44 PM  Lotus Notes client started
Stack base = 0xbfd86b7c, Stack size = 6348 bytes
Fatal Error signal = 0x0000000b PID/TID = 7805/-1267161408
27/7/2006 12:58:44  Running NSD

(nsdexec:7806): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
NSD is in progress .................

Please attach the following files to your bug report along with the server log:
Log file                : /home/jan/notes/data/IBM_TECHNICAL_SUPPORT/nsd_Linux_j [email]an-ubuntu-desktop_2006_07_27@12_58_47.log[/email]
27/7/2006 12:59:16  Termination is in progress
27/7/2006 12:59:16  Terminating tasks
jan@jan-ubuntu-desktop:~/bin$ 27/7/2006 12:59:26  Freeing resources
27/7/2006 12:59:26  Termination completed
jan@jan-ubuntu-desktop:~/bin$[/INDENT]


Starting the empty "Workplace Managed Client" worked perfectly.

Has anybody the same problem or a hint for me?

Thanks
Jan

---

### Post by johannagnarsson on 2006-07-27
> **jan_123 said:**
> Malmo,

Starting the empty "Workplace Managed Client" worked perfectly.

Has anybody the same problem or a hint for me?

Thanks
Jan

Described the same problem on the first page :)

I had a Lotus expert try to help me debug this but no luck so far.
Going to try to download the package again and do a fresh install.

I'm Using Dapper Drake 6.06, fully updated.

---

### Post by jan_123 on 2006-07-27
> **johannagnarsson said:**
> Described the same problem on the first page :)

I had a Lotus expert try to help me debug this but no luck so far.
Going to try to download the package again and do a fresh install.

I'm Using Dapper Drake 6.06, fully updated.


Sorry for posting the same thing again! :oops: But now we knew, that we are not alone with our Problem. 

Im Using Dapper Drake 6.06 - fully updated -, too.

Best regards
Jan

---

### Post by treb0re on 2006-07-27
I've got exactly the same problem... installed plenty of times and still get the same output as that... I've got libmotif installed and everything else plus the libs setup in the path....

Lotus notes forum isn't sheding anything either.... Why couldn't they have just packaged it properly! Sametime 7.5 beta for linux is in an RPM (which I converted using alien to a deb) and it works flawlessly....

---

### Post by evilcartman on 2006-07-27
Do the logs in ~/notes/IBM_TECHNICAL_SUPPORT show the same crash messages as posted, or are there additional/different messages?

---

### Post by treb0re on 2006-07-27
I'm on a domino 5 server.... 
But that's not the issue as I've not even got to the config stage of notes... it crashes as it's loading the config stage (same errors as the long post above).


I've had notes r7 under windows working fine on a domino 5 server even with a r7 template, no problems, although you just can't use the new features... it's all backwards compatible.

---

### Post by treb0re on 2006-07-27
Error message at bottom and screen error message attached.... not very helpful as far as I can tell... although there a couple of file not founds at the beginning... I've got exactly the same notesstart script as posted before (but changing the home dir obviously).

It loads the blank pannels if you run it without the script...
With the script a box pops up saying "NSD is running, please wait...", then crashes and the error message pops up.

See what you can make of it... any ideas?

I've snipped a load of this as it's so looooong.
> 
INFO: New files added/deleted to/from directory '/home/trellis/notes'
INFO: Generating binary list file ./nsd.trellis/nsd_7.0.1_cache.ins.lst
INFO: Generating cache file ./nsd.trellis/nsd_7.0.1_cache.ins
Script Version  : /home/trellis/notes/nsd.sh 7.0.1
Notes Version   : Release 7.0.1 July 07, 2006             
Notes Base      : 7.01
Data Dir        : /home/trellis/notes/data
Notes Exec Dir  : /home/trellis/notes
Search Path     : /home/trellis/notes /home/trellis/notes/notesapi
Debugger        : /usr/bin/gdb
Debugger Version: GNU gdb 6.4-debian
MEMCHECK Version: 
<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>
Section: Notes Memory Analyzer (memcheck) (Time 15:20:30)
<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>

Arguments: /home/trellis/notes/memcheck -i
Script Dir      : /home/trellis/notes
Host Info       : Linux trellis-laptop 2.6.15-26-386 #1 PREEMPT Mon Jul 17 19:52:53 UTC 2006 i686 GNU/Linux
User            : trellis (trellis)
Date            : Thu Jul 27 15:20:31 BST 2006
Input arguments : -client -batch -crashpid 8022 -crashtid 2 -wrapper


ls: java: No such file or directory
ls: lnotes: No such file or directory
ls: senddiag: No such file or directory

Maybe something wrong here?! I've used the notesstart script pasted on the previous pages...
> 

<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>
Section: Summary
<@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@@>


Run /home/trellis/notes/nsd.sh -help for more info on new options/features

Script started at: Thu Jul 27 15:20:28 BST 2006
Script ended   at: Thu Jul 27 15:20:56 BST 2006


Generated Info/Warnings/Errors: 
  (1) INFO: New files added/deleted to/from directory '/home/trellis/notes'
  (2) INFO: Generating binary list file ./nsd.trellis/nsd_7.0.1_cache.ins.lst
  (3) INFO: Generating cache file ./nsd.trellis/nsd_7.0.1_cache.ins
  (4) ERROR: /usr/bin/gdb --readnever option is not supported; stack collection may take several minutes.
  (5) ERROR: /usr/bin/gdb --readnever option is not supported; stack collection may take several minutes.
  (6) ERROR: /usr/bin/gdb --readnever option is not supported; stack collection may take several minutes.
  (7) INFO: The Maximum core file size is 0 blocks



---

### Post by johannagnarsson on 2006-07-27
> **evilcartman said:**
> Do the logs in ~/notes/IBM_TECHNICAL_SUPPORT show the same crash messages as posted, or are there additional/different messages?

It's the same crash message as posted although the NSD log is a bit more detailed.

I'm in the process of reinstalling a fresh download.
If I suffer from the same crash I could post the log.(added)

---

### Post by loupy on 2006-07-27
I was having issues even after motif - what I finally did was change the launcher to point to an executable file I created and it setup fine.  Not sure if this will work for everyone, but here is the code for the file I used:

noteslauncher.sh
```

# -- Added for Lotus Notes for Linux
NOTESBIN=/home/loupy/notes
NOTESDATA=/home/loupy/notes/data
NOTESDIR=/home/loupy/notes/data

LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRARY_PATH

PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH

CLASSPATH=$NOTESBIN:$CLASSPATH

export NOTESBIN NOTESDATA NOTESDIR LD_LIBRARY_PATH PATH CLASSPATH

# run the app
/opt/ibm/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality
```

---

### Post by malmo on 2006-07-28
Johan:
If you source same variables in your terminal, what version of java you get?

---

### Post by johannagnarsson on 2006-07-28
> **malmo said:**
> Johan:
If you source same variables in your terminal, what version of java you get?

johann@johann-desktop:~$ java -version
java version "1.4.2"
Java(TM) 2 Runtime Environment, Standard Edition (build 1.4.2)
Classic VM (build 1.4.2, J2RE 1.4.2 IBM build cxia32142ifx-20041203 (142SR1+80507) (JIT enabled: jitc))

But afaik, the WMC client uses it's own JVM as does the Notes client.

---

### Post by davidwi on 2006-07-28
[QUOTE=treb0re;1306223]I've got exactly the same problem... installed plenty of times and still get the same output as that... I've got libmotif installed and everything else plus the libs setup in the path....

I was also getting NSD errors but just got it working - I deleted bookmark.nsf and log.nsf and it started working. I'm a roaming Notes user and my bookmark.nsf downloaded when I first got the wizard running, I'll try this on my other Ubuntu computer later to confirm this. 

Dsvid.

---

### Post by dankegel on 2006-07-29
For those who can't get the native version up and running,
running the Windows version under Wine is still a good alternative,
and is getting better.  See 
   [http://wiki.winehq.org/LotusNotes](http://wiki.winehq.org/LotusNotes)
for details.  As of wine-0.9.18, the client runs fairly well,
without any native DLLs.

---

### Post by supertux on 2006-07-31
anybody get notes working in dapper? I also get the errors stated above. Havent any clues anymore.. :-x

---

### Post by acascianelli on 2006-07-31
Did anybody figure out the Pango Warning problem?

---

### Post by Rever75 on 2006-07-31
I am also getting the same issue as everyone above. With the Pango error and gtk locale not supported error. I will continue to troubleshoot it and if I find a solution will post it here. If someone already found one could you please post it for the rest of us to try.

---

### Post by sigmo on 2006-07-31
I also have the problem with the "starting nsd" at work. (dapper drake)

At home (hoary->breezy->dapper) I can start lotus notes, but I also see the same pango errors. 
Maybe the pango error isn't the problem ... ?

---

### Post by themidge on 2006-07-31
Dapper 6.06 same issue with Pango errors and followed by launch of NSD...

---

### Post by skfk on 2006-07-31
Nice job..
but, please, where can i download the file 'C93D1NA.zip' faster?

I done all the register forms in parterworld but there are no answer.. :( 

Any direct link .. etc? tnks :)

---

### Post by superm1 on 2006-07-31
Your lucky you at least can log into the partner site.  I have been pestering our IT person since the day it came out, but she still hasn't gotten me a build.  If you find a direct link - I'd appreciate it too.

---

### Post by lone_marauder on 2006-07-31
I have fixed the NSD on startup problem on my machine - by removing all my printers.  (Don't ask me what made me try this - it was a total lucky guess).  If any printers are configured - NSD.  If I remove them - Notes works fine.  I am printing to an 8100 and 2200, both using the postscript driver, and to a tektronics phaser 750, also using postscript.  I tried the lj4 driver and hpijs driver on the HPs, both to no avail.  If a printer of any kind with any driver is configured, Notes will NSD crash on startup.  /var/log/cups/* provide no insight.

I hope this can at least direct effort in the right direction to get this working.

---

### Post by themidge on 2006-07-31
So I've got it running... I guess...

Basically it takes about 4 minutes to fire up, doesn't layout the interface correctly until I adjust the preview pane, runs like hell, and isn't any kind of improvement over any previous version of the notes client.

I have decided to settle for running notes 6.5 under wine as it runs at least 10x faster, fires up instantly, and actually works as expected (which I expect to be crap as every notes client is).

---

### Post by mjtg on 2006-07-31
lone_marauder is on the right track regarding printing.  I just did an strace of the notes program, and in the resulting dump the program had connected to CUPS immediately before segfaulting.  So, I shut down CUPS on my PC, and now Notes seems to be working - I'm being prompted with a config/setup box.

The connection to CUPS appears to have been successful - in the dump, I can see the data that CUPS is writing back to NOTES.  Looks like someone needs to investigate what CUPS is telling Notes that Notes doesn't like.

---

### Post by Rever75 on 2006-08-01
Well shutting down cups worked for me also. yes it takes awhile for it to start up and you need to adjust the preview pain. However at least they have created something that now they can improve on. Yes I would like it to be faster and not have the issues with cups and everything else but I like the fact that it will work natively in Linux with out wine or crossover office. yes I will most likely still use wine to run notes but will keep an eye on the improvements to the native client.

---

### Post by ultra on 2006-08-01
Yes, thanks a lot, CUPS seems to be the answer. I just did:
sudo /etc/init.d/cupsys stop

and Notes running the setup wizzard like it should be. Great and thanks a lot.

---

### Post by tnf on 2006-08-02
Hello,

installing went well for me (Breezy Badger), but when I try to open an attachment via "open with..." I get 

```
/home/tfe/notes/openwith: error while loading shared libraries: libnautilus.so.2: cannot open shared object file: No such file or directory
```

Does anyone know how to fix this?

Tobias

---

### Post by lone_marauder on 2006-08-02
For what it's worth, Gentoo does not seem to be affected by the CUPS problem.

---

### Post by acascianelli on 2006-08-04
Removing my printers worked for me.  Lotus Notes is working fine now.  Thanks.

---

### Post by jlt5 on 2006-08-10
Help!!!!! Got the darn thig to sort of come up using the notesstart script. the Panel comes up and says Notes Applications - Lotus Notes. I have the File tab and Help tab. Within the Help tab what am i connecting too? The notes server? Need help getting further. There  is not much doc past this point. Thanks Jim :confused:

---

### Post by acascianelli on 2006-08-10
Try removing any printers you have installed.

---

### Post by lone_marauder on 2006-08-11
I have a better solution to the printers thing...

Notes queries CUPS for its default printer.  Whatever Ubuntu does to keep track of your default printer, it isn't CUPS.  The NSD crash results from Notes getting an error back from CUPS - "I don't have a default printer!" (paraphrased) 

**Warning.  The advice below is to be considered experimental.  It involves directly managing your CUPS printers outside of the normal Ubuntu administrative interface.  YMMV, YRMV, IANAL, OMGWTFBBQ, etc. etc.**

To correct this problem, consult your /etc/cups/printers.conf file.  There you will find entries for your printers, in the following general format:

<Printer LaserJet-2200>

(printer stuff)

</Printer>

Find the entry for the printer you wish to use as your default printer.  Then change the header, adding the word "Default" (no spaces) before the printer name:

<DefaultPrinter LaserJet-2200>

Now CUPS has a real, honest to goodness default printer and will tell Notes so when it tries to start.  No more NSD, you can print from Notes, etc.

---

### Post by dwanders on 2006-08-24
Thanks for the great HowTo. WHen I try to use it, the following is happeneing:

I downloaded and installed the packages as instructed all went without a hitch. I created the scripts notesstart as instructed for Gnome (running Ubuntu 6 LTS). When I launch the ICON on the desktop, I get an empty client. WHen I run the script notesstart, I get a splash screen, and in the console I see:

notes: LD_LIBRARY_PATH = /home/danderson/notes:/home/danderson/notes/jvm/bin/classic:/home/danderson/notes/jvm/bin:/home/danderson/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/danderson/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/danderson/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/j9vm:/home/danderson/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/danderson/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/danderson/notes:/home/danderson/notes/jvm/bin/classic:/home/danderson/notes/jvm/bin:/home/danderson/notes:/home/danderson/notes/jvm/bin/classic:/home/danderson/notes/jvm/bin:/usr/../usr/lib/mozilla
/home/danderson/notes/notes: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
nsdexec: notespid = 5946


and I have nothing set (not of my environment) to /home/danderson/notes/notes

here is my launch script:

#!/bin/bash

NOTESBIN=/home/danderson/notes
NOTESDATA=/home/danderson/notes/data
NOTESDIR=/home/danderson/notes/data
export NOTESBIN NOTESDATA NOTESDIR 

LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRARY_PATH
PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH
CLASSPATH=./:$NOTESBIN
export LD_LIBRARY_PATH PATH CLASSPATH

/home/danderson/IBM/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality


If any one can see what I am doing wrong I would really appriciate any help. I have been running Notes in Crossover office for a few years now and have been stuck on version 5.13 for Notes.

---

### Post by kailden on 2006-08-25
Thanks lone_marauder!  Your default printer fix worked for me as well, with a  network printer even.

---

### Post by murphdog on 2006-08-25
With regards to the libX not being found, this is becuase Motif libraries are not loaded... you need to install them - NB for me this meant installing libtiff since libmotif3 was not available for Kubuntu 6.06.
If you find other shared libraries are required (as I did) then I'd recommend you get apt-file installed and then search in order to find the required packages (unless anyone else has a better idea)

---

### Post by dwanders on 2006-08-25
Outstanding, so for a quick recap, this is what worked for me:
On Ubuntu 6.06 LTS (with all the added repositories)

1) Follow the steps original set
2) add sudo apt-get install libmotif3
3) remove all printers or do lone_marauder's fix

Worked for me; during the install connecting to a R5 Domino server worked fine as well so long as the IP address is set in a /etc/hosts entry and you call it by the host name.

I would agree it is still a bit buggy - however for Big Blue to finaly get start getting their stuff together I think it is great. Right now, for me Crossover & R5.13 seem much more stable but this is well worth watching. Cant wait for the day I can apt-get install notes! I had more trouble downloading the application from IBM site with their crappy passport advantage than I did with the help from you guys. 

Thanks to all.

---

### Post by sawi on 2006-08-29
Hi folks,

I try to get notes running on Kubuntu on an AMD64 maschine. 

First thanks to all for the help, but my installation crashed very early during the progress. Normaly the graphical installation routine should install the  Workplace Manged Client and after that I should be asked to install Lotus Notes Client plug-in. This does not happen. If I try to run the script which is behind the icon "install IBM Productivity Tools" I get an error missing a lib-file:
---snipp---
"/opt/IBM/Workplace_Managed_Client/rcp/richclient" -install.deploy file:///home/frank/lotus/plugin/deploy/install.xml -install.restartpersonality com.ibm.workplace.noteswc.standalone.linux.personality -personality com.ibm.rcp.install.personality
/opt/IBM/Workplace_Managed_Client/rcp/richclient: error while loading shared libraries: libgtk-x11-2.0.so.0: cannot open shared object file: No such file or directory
---snipp---

libgtk2.0-0 and libgtk2.0-dev is installed and libgtk-x11-2.0.so.0 can be found in /usr/lib:
---snipp---
ls -l /usr/lib/libgtk-x11-2.0.so.0
lrwxrwxrwx 1 root root 26 2006-08-23 11:38 /usr/lib/libgtk-x11-2.0.so.0 -> libgtk-x11-2.0.so.0.800.20
---snipp---

In my despair I put /usr/lib in $PATH:
---snipp---
echo $PATH
/usr/lib/:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/bin/X11:/usr/games:/opt/IBM/Workplace_Managed_Client/:/usr/lib/jvm/java-1.4.2-gcj-4.1-1.4.2.0/bin/
---snipp---

Nothing helps. Does anyone have an idea?

Thx & Bye

Frank

---

### Post by mvcorrea on 2006-09-14
Finish installing on Debian etch (testing).
On an basic desktop enviroment instalation, I also installed the packages...
libmotif3(stable), mozilla, libstdc++5, gawk.

file /etc/gre.conf
--
[1.7.12]
GRE_PATH=/usr/lib/mozilla
--

disable cupsys
/etc/init.d/cupsys stop

and then install without problem....

then in the file /etc/cups/printers.conf
as already said add "Default" to one of your printers

<Printer LaserJet-4050---CUPS+Gutenprint-v5.0.0> to
<[COLOR="Red"]Default[/COLOR]Printer LaserJet-4050---CUPS+Gutenprint-v5.0.0>


and then everything seems to work...:)

Questions to solve?????

**Mime:** Does any one knows how to open a file (like an word attach) with the proper openoffice?

**Multiuser Install:** How do I build an multiuser enviroment? There is a way to pass the install folder (install dir) before installing? The installer creates an IBM folder on the user $HOME, this folder could be shared between various users?

I think I only need a notes folder in the user home to make it work. but I am in trouble when trying to install for other user (it trys to create other /opt/IBM install dir again)

regards

Marcelo

**[COLOR="Red"]Update:[/COLOR]**
I am able to make an multiuser install running this as other user
modify the "-install.deploy"!!!

/opt/IBM/WMC/rcp/richclient -install.deploy file:///home/notes/notes7/install/deploy/install.xml -install.restartpersonality com.ibm.workplace.noteswc.standalone.linux.personality -personality com.ibm.rcp.install.personality

but still creates two folders in the $HOME (IBM and notes)

---

### Post by fraoustin on 2006-09-15
Your problem is the relatoin between Lotus Notes and cups.
A "sudo vi" of "/etc/cups/printers.conf" and replace "<Printer" by "<DefaultPrinter" and restart cups service.
After reload Lotus Notes and is ok

---

### Post by Rever75 on 2006-09-20
Ok I have everything working by using the cups fix. However, when I goto print something it sends the job to the printer as format A4. Although everything says Letter. Outside of Notes I can print just fine but within the Notes client nothing I do sends it to the printer as Letter, it always goes over as A4 :confused: . I am using an supported HP LaserJet 4050N. Any help would be great.:p

---

### Post by phlegm on 2006-09-20
The CUPS trick fixed things for me. The problem now is that this Notes client is a pig. It is faster for me to open VMWare, resume an image and launch notes than it is to open this linux client. Not to mention that it run's much faster once they are both opened.

---

### Post by oo_void on 2006-10-17
I'm wondering if anyone has had any luck getting Notes installed on Edgy. I'm hitting a wall with the "Can not validate Mozilla version" message, even though I have a gre.conf file in place. Thanks ...

------
oo_void

---

### Post by jpeg on 2006-10-18
Hello,

Thanks a lot guys for this usefull thread.

For the open file problem, I just create the following links.
It's quick and dirty, but it seems to work at least for Office files.

as root:
# cd /usr/lib
# ln -s libnautilus-extension.so.1  libnautilus.so.2
# ln -s libnautilus-extension.so.1  libnautilus-private.so.2

It only resolve the library issue. If notes need some function in this it will probably hang.

---

### Post by dragonfixed on 2006-10-19
thanks for the help

i am new to installing lotus notes on linux. can you please give me step by step instructions on how to install it under ubuntu v6.0.6.1

the instructions on your post are confusing me

---

### Post by exceedhl on 2006-10-26
After I installed Lotus Notes 7 for Linux on my Ubuntu Dapper, everytime I started it, it shows two blank panes and there is no notes directory under my home directory. Does anybody know possible reason?

---

### Post by ugabriel on 2006-10-27
Hi,

i've also got the problem to install Lotus Notes for Linux on a new Edgy installation.

Did someone found a solution? The installer doesn't detect the mozilla installation.

Thanks...

---

### Post by hisloudness on 2006-10-27
I just installed Edgy and ran into an issue with how the installer validates the mozilla libs.  The installer kept failing with "Cannot validate mozilla version" message. I was getting frustrated since these instructions worked so well my Dapper systems.  I traced the installer to find it's method of validating mozilla is to create a shell script under /tmp called iwcttmp<#####>.sh that contains this --

#!/bin/sh
ldd "/usr/lib/mozilla/libgtkembedmoz.so" | grep gtk>&/tmp/iwcttmp.out

This script fails because of the ampersand (Syntax error: Bad fd number).
I corrected this by simply running the command manually --

ldd "/usr/lib/mozilla/libgtkembedmoz.so" | grep gtk > /tmp/iwcttmp.out

As long as that file is there when the installer looks for it everything works fine.

Hope this saves someone some work.

---

### Post by heintz on 2006-10-31
Thank you, thank you, thank you!!!

You just saved my day (erh, what's left of it at least ;-)

BTW, how did you trace the installer?

---

### Post by acascianelli on 2006-10-31
Has anybody gotten Notes to work in Edgy yet?  I'm installing Edgy on my computer at work later this afternoon and I'll be having a crack at getting it to work tomorrow morning.

---

### Post by saphir on 2006-11-01
I have exacly the same problem as all.

I&#8217;m running on a Fedora core 6 / Gnome

I installed the Lotus Notes package in console mode (user mode non root) because the installation doesn&#8217;t want to launch in graphic mode, I think it&#8217;s because I don&#8217;t have Mozilla 1.7.12 (I have firefox).


The Lotus notes icon on my desktop produce the empty two pane window and setup never started.

Exactly the same thing if I execute the script.

There are no errors in the terminal when I execute the script.

I stop the cups daemon to 

Question is it normal:
In my home directory I have no notes directory ??
Is mozilla mandatory ?

Any clue?

---

### Post by acascianelli on 2006-11-01
I got Notes installed on Edgy but I keep getting the 2 blank panes...

libmotif3 installed
no printers in CUPS

...I can't seem to figure it out.

---

### Post by xlnt01 on 2006-11-01
I get the following error when I try to launch notes on my kubuntu edgy:

/home/micke/notes/notes: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
nsdexec: notespid = 5202

where can I get this libXm.so.3 ?

---

### Post by hisloudness on 2006-11-01
heintz -
  In answer to your question I used the strace command to trace the installer.  There are many ways you can use this util.  I just did 'strace -f <notes installer> > /tmp/strace.notes 2>&1'.  And then reviewed the file to find out what it was doing with gre.conf.

saphir & acascianelli -
  Try making your own start script as explained in the first post in this discussion.  The installer actually puts the right stuff in your profile, it's just that your profile doesn't get sourced when you click on the icon. Here is my script:
morganma@PHXGX260:~$ cat bin/notes.sh
#!/bin/bash
#
. /home/morganma/.bash_profile
exec /opt/IBM/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality

If this works you'll get the wizard. If your still getting the blank screen you should be able to work around this by putting a working (or barebones) notes.ini file in your notes dir.

Cheers

---

### Post by acascianelli on 2006-11-01
> 
I get the following error when I try to launch notes on my kubuntu edgy:

/home/micke/notes/notes: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
nsdexec: notespid = 5202

where can I get this libXm.so.3 ?
Reply With Quote


install gsfonts and gsfonts-x11.

---

### Post by illtiss on 2006-11-02
Hi all, after the first install i got the  empty Panels, but when I try to start it again, it doesnt work any more. 
In console I can read the following:

LD_PRELOAD=libjsig.so
/home/test/IBM/Workplace Managed Client//eclipse/eclipse: error while loading shared libraries: /home/test/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/libjsig.so: cannot restore segment prot after reloc: Permission denied
[test@localhost bin]$ 


Hope somebody can help me.

---

### Post by saphir on 2006-11-02
in the file .xsession-erros in my home directory i have this :

localuser:saphir being added to access control list
SESSION_MANAGER=local/raine.css.fr:/tmp/.ICE-unix/11603
libGL warning: 3D driver claims to not support visual 0x5b
compiz: No stencil buffer. Clipping of transformed windows is not going to be correct when screen is transformed.
compiz: water: GL_ARB_fragment_program is missing

setPreload():libraryDirPath:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/
Xlib: unexpected async reply (sequence 0x9)!

---

### Post by acascianelli on 2006-11-02
> **hisloudness said:**
> heintz -
  In answer to your question I used the strace command to trace the installer.  There are many ways you can use this util.  I just did 'strace -f <notes installer> > /tmp/strace.notes 2>&1'.  And then reviewed the file to find out what it was doing with gre.conf.

saphir & acascianelli -
  Try making your own start script as explained in the first post in this discussion.  The installer actually puts the right stuff in your profile, it's just that your profile doesn't get sourced when you click on the icon. Here is my script:
morganma@PHXGX260:~$ cat bin/notes.sh
#!/bin/bash
#
. /home/morganma/.bash_profile
exec /opt/IBM/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality

If this works you'll get the wizard. If your still getting the blank screen you should be able to work around this by putting a working (or barebones) notes.ini file in your notes dir.

Cheers

I still starts up with the two blank panels, even after I put a blank notes.ini file.  I tried stopping CUPS, but nothing changes.

---

### Post by matt.fiscus on 2006-11-02
> **xlnt01 said:**
> I get the following error when I try to launch notes on my kubuntu edgy:

/home/micke/notes/notes: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
nsdexec: notespid = 5202

where can I get this libXm.so.3 ?

libXm.so.3 is part of the libmotif3 package

sudo apt-get install libmotif3

---

### Post by acascianelli on 2006-11-02
Being that I can't get the Linux client to work in Edgy, I re-installed Crossover Office and the Windows version for the time being. :(

Hopefully I can get the Linux client working soon.

---

### Post by matt.fiscus on 2006-11-02
SUCCESS!

After performing an 'strace' on my startup script, I discovered two problems...

1. It could not locate '/usr/share/locale/C/cups_C.so'

2. It was searching in directories that don't even exist on my system to locate the libraries it needs.



Problem #1 was the show stopper. To fix this, I simply created an empty 'cups_C.so' by performing the following commands...

sudo mkdir /usr/share/locale/C
sudo touch /usr/share/locale/C/cups_C.so

Problem #2 wasn't preventing Notes from starting up, it was just making my startup time incredibly slow. To solve this, I performed the following command...

sudo touch /etc/ld.so.nohwcap

This second step is optional, but it reduced my startup time to half of what it used to be.

---

### Post by acascianelli on 2006-11-02
> **matt.fiscus said:**
> SUCCESS!

After performing an 'strace' on my startup script, I discovered two problems...

1. It could not locate '/usr/share/locale/C/cups_C.so'

2. It was searching in directories that don't even exist on my system to locate the libraries it needs.



Problem #1 was the show stopper. To fix this, I simply created an empty 'cups_C.so' by performing the following commands...

sudo mkdir /usr/share/locale/C
sudo touch /usr/share/locale/C/cups_C.so

Problem #2 wasn't preventing Notes from starting up, it was just making my startup time incredibly slow. To solve this, I performed the following command...

sudo touch /etc/ld.so.nohwcap

This second step is optional, but it reduced my startup time to half of what it used to be.

Can you post your startup script please.

---

### Post by acascianelli on 2006-11-02
The only way I can even get the interface to partially come up is by using the launcher created by the installer.

Any other startup script I write either ends up with a message saying it cannot find the notes.ini(and hangs when I provide a blank notes.ini), a jvm crash, or NSD running.

---

### Post by matt.fiscus on 2006-11-02
> **acascianelli said:**
> Can you post your startup script please.

```
#!/bin/sh

NOTESBIN=/home/$USER/notes
NOTESDATA=/home/$USER/notes/data
NOTESDIR=/home/$USER/notes/data

LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRARY_PATH

PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH

CLASSPATH=./:$NOTESBIN/:$CLASSPATH

export NOTESBIN NOTESDATA NOTESDIR LD_LIBRARY_PATH PATH CLASSPATH

/opt/IBM/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality &

```

---

### Post by acascianelli on 2006-11-02
With that script, it freezes at the splash screen.  Then it pops up saying it cannot find the notes.ini.  On the console I see these messages...

> 
notes: LD_LIBRARY_PATH = /home/acascianelli/notes:/home/acascianelli/notes/jvm/bin/classic:/home/acascianelli/notes/jvm/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/j9vm:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace Managed Client/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/acascianelli/notes:/home/acascianelli/notes/jvm/bin/classic:/home/acascianelli/notes/jvm/bin:/usr/../usr/lib/mozilla
nsdexec: notespid = 6738

(<unknown>:6738): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
GetACP returns 1252

(<unknown>:6738): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:6738): GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:6738): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:6738): GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed

(<unknown>:6738): GLib-GObject-WARNING **: invalid (NULL) pointer instance

(<unknown>:6738): GLib-GObject-CRITICAL **: g_signal_emit_by_name: assertion `G_TYPE_CHECK_INSTANCE (instance)' failed


And when I create an empty notes.ini file using the touch command I get the following at the console.

> 
Unhandled exception
Type=GPF vmState=0x00000003
Target=2_20_20050124_1705_lHdSMR (Linux 2.6.17-10-generic)
CPU=x86 (2 logical CPUs) (0x7e266000 RAM)
edi=bfc274dc esi=950a64b6 eax=ffffffff ebx=94e2d458
ecx=00000000 edx=9285b004 ebp=bfc27824
eip=9349eab6 es=c010007b ds=c010007b esp=bfc26f98
eflags=00010282 cs=00000073 ss=0000007b
Module=/home/acascianelli/notes/libnotes.so
Module_base_address=9332f000 Symbol=OSAtomicDecrement
Symbol_address=9349eaad
JVMDUMP006I Processing Dump Event "gpf", detail "" - Please Wait.
JVMDUMP007I JVM Requesting System Dump using '/home/acascianelli/Desktop/core.20061102.150331.7117.dmp'
JVMDUMP006I Processing Dump Event "abort", detail "" - Please Wait.
JVMDUMP007I JVM Requesting System Dump using '/home/acascianelli/Desktop/core.20061102.150333.7117.dmp'
JVMDUMP012E Error in System Dump: cannot find core file, check "ulimit -c" is set high enough
JVMDUMP007I JVM Requesting Java Dump using '/home/acascianelli/Desktop/javacore.20061102.150333.7117.txt'
JVMDUMP010I Java Dump written to /home/acascianelli/Desktop/javacore.20061102.150333.7117.txt
JVMDUMP013I Processed Dump Event "abort", detail "".


---

### Post by matt.fiscus on 2006-11-02
> **acascianelli said:**
> With that script, it freezes at the splash screen.  Then it pops up saying it cannot find the notes.ini.  On the console I see these messages...



And when I create an empty notes.ini file using the touch command I get the following at the console.

If you don't have a notes.ini, perhaps you could try to run the Notes client installation again...


```
"/opt/IBM/Workplace Managed Client/rcp/richclient" -install.deploy file:///home/$USER/plugin/deploy/install.xml -install.restartpersonality com.ibm.workplace.noteswc.standalone.linux.personality -personality com.ibm.rcp.install.personality

```

---

### Post by acascianelli on 2006-11-02
> **matt.fiscus said:**
> If you don't have a notes.ini, perhaps you could try to run the Notes client installation again...


```
"/opt/IBM/Workplace Managed Client/rcp/richclient" -install.deploy file:///home/$USER/plugin/deploy/install.xml -install.restartpersonality com.ibm.workplace.noteswc.standalone.linux.personality -personality com.ibm.rcp.install.personality

```

I tried to do that reinstall, still gives same results.

---

### Post by saphir on 2006-11-02
where do we have to put the notes.ini ? in witch directory ?

i have no notes and notes/data directory in my /home/saphir directory ...

a notes.ini from a windows pc will be ok ?

---

### Post by TheMasterCylinder on 2006-11-02
[I]where do we have to put the notes.ini ? in witch directory ?

i have no notes and notes/data directory in my /home/saphir directory ...

a notes.ini from a windows pc will be ok ?[/I]

The notes.ini should go in /home/saphir/notes

If you do not have those directories your install did not complete correctly. A windows notes.ini will have the wrong paths, so do not do it.

---

### Post by saphir on 2006-11-03
Youpi !

So it's finaly a complete success for me.

Lotus was not completly installed .. no notesand notes/data directory. (the lotus icon was there !)
The workplace was corectly installed ... perhaps lotus was not because of my installation in console mode.

To solve my problem:

- i launch setulinux.bin in the lotus directory
- the lotus icon don't want to launch lotus even after a logout/login so i launch the your script.
- error on libXp.so.6 and libXm.so.3 not here, so i made symbolic link in the notes directory with libXpm.so.4 and libXmu.so.6

and youpi ! with the script lotus and his wizard are here :)

---

### Post by ugabriel on 2006-11-04
> **acascianelli said:**
> With that script, it freezes at the splash screen.  Then it pops up saying it cannot find the notes.ini.  On the console I see these messages...



And when I create an empty notes.ini file using the touch command I get the following at the console.

Hi,

everyone who have problems installing Lotus Notes on Edgy should try this command "sudo ln -sf /bin/bash /bin/sh" to solve the problem.

Edgy now uses /bin/dash instead of /bin/bash as the shell for sh. 

After installing Lotus Notes you can switch the link back to "sudo ln -sf /bin/dash /bin/sh". But you should change the first line in the gnome start script to /bin/bash instead of /bin/sh.

This solves the problems:

1) get the Mozilla version at the beginning of the install shield
2) create notes.ini file in your data directory...

For German users the the issue is also described at [http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29](http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29)

---

### Post by acascianelli on 2006-11-04
> **ugabriel said:**
> Hi,

everyone who have problems installing Lotus Notes on Edgy should try this command "sudo ln -sf /bin/bash /bin/sh" to solve the problem.

Edgy now uses /bin/dash instead of /bin/bash as the shell for sh. 

After installing Lotus Notes you can switch the link back to "sudo ln -sf /bin/dash /bin/sh". But you should change the first line in the gnome start script to /bin/bash instead of /bin/sh.

This solves the problems:

1) get the Mozilla version at the beginning of the install shield
2) create notes.ini file in your data directory...

For German users the the issue is also described at [http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29](http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29)

F'in right doggy, I duplicated the problems I was having on my laptop, and now using this advice I am able to start the setup wizard.  Thanks alot.

Update:  I just got Notes up and running on my system at work.

---

### Post by illtiss on 2006-11-08
Ok I`ve finished succesfully the installation on a Fedora Core 5. So I decided to give SuSe 10.1 a try. Also I got it to work. Thanks for this forum, thanks a lot.

---

### Post by xlnt01 on 2006-11-15
Yes, I've finally got lotus notes to work on both my kubuntu and my ubuntu machines.
But I got one strange problem with it. Inside lotus notes I can't type the swedish letter å. All other characters works just fine even äö but not å. I can hower type Å inside notes but I don't like to have to typ bÅt instead of båt if you know what I mean.

Does anyone have any idea of how I can get this to work?

Thanks

---

### Post by haamann on 2006-11-21
> **xlnt01 said:**
> Yes, I've finally got lotus notes to work on both my kubuntu and my ubuntu machines.
But I got one strange problem with it. Inside lotus notes I can't type the swedish letter å. All other characters works just fine even äö but not å. I can hower type Å inside notes but I don't like to have to typ bÅt instead of båt if you know what I mean.

Does anyone have any idea of how I can get this to work?

Thanks


You could try to use the crtl-key while pressing å. Works for my norwegian keyboard 8)

---

### Post by dschaefer79 on 2006-11-24
Hello I tried to run Notes 7 on Ubuntu Edgy 64 bit.

1st : I can't launch the graphical installer setup_wct_platform.bin :

current locale is not supported in X11, locale is set to CX locale modifiers are not supported, using defaultThe installer is unable to run in graphical mode. Try running the installer with the -console or -silent flag.

2nd : When I run the setup_wct_platform.bin in console mode I get this :

Can not validate Mozilla version

I've installed the mozilla suite amd64 version.

Is it possible to make notes 7 work with Ubuntu Edgy AMD64 ?

Thanks for help.
Dominique

---

### Post by giangiacomo on 2006-11-27
I have a similar problem, I'm not able to run "setup_wct_platform.bin" because it "Can not validate Mozilla version"... ](*,) ](*,) 

Did you find a solution?

Bye

---

### Post by santo on 2006-11-27
Did you try one of the workarounds mentioned before:

> **hisloudness said:**
> I just installed Edgy and ran into an issue with how the installer validates the mozilla libs.  The installer kept failing with "Cannot validate mozilla version" message. I was getting frustrated since these instructions worked so well my Dapper systems.  I traced the installer to find it's method of validating mozilla is to create a shell script under /tmp called iwcttmp<#####>.sh that contains this --

#!/bin/sh
ldd "/usr/lib/mozilla/libgtkembedmoz.so" | grep gtk>&/tmp/iwcttmp.out

This script fails because of the ampersand (Syntax error: Bad fd number).
I corrected this by simply running the command manually --

ldd "/usr/lib/mozilla/libgtkembedmoz.so" | grep gtk > /tmp/iwcttmp.out

As long as that file is there when the installer looks for it everything works fine.

Hope this saves someone some work.

> **ugabriel said:**
> Hi,

everyone who have problems installing Lotus Notes on Edgy should try this command "sudo ln -sf /bin/bash /bin/sh" to solve the problem.

Edgy now uses /bin/dash instead of /bin/bash as the shell for sh. 

After installing Lotus Notes you can switch the link back to "sudo ln -sf /bin/dash /bin/sh". But you should change the first line in the gnome start script to /bin/bash instead of /bin/sh.

This solves the problems:

1) get the Mozilla version at the beginning of the install shield
2) create notes.ini file in your data directory...

For German users the the issue is also described at [http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29](http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29)

---

### Post by dschaefer79 on 2006-11-28
I've installed notes successfully but now when I launch it, I get a window with this error message when I start my script 

notesstart :
#!/bin/sh

export XLOCALELIBDIR=/usr/lib32/X11/locale
NOTESBIN=/home/dschaefer79/notes
NOTESDATA=/home/dschaefer79/notes/data
NOTESDIR=/home/dschaefer79/data
LD_LIBRARY_PATH=$NOTESBIN:$NOTESBIN/jvm/bin/classic:$NOTESBIN/jvm/bin:$LD_LIBRA$
PATH=$NOTESBIN/jvm/bin:$NOTESBIN:$PATH
CLASSPATH=./:$NOTESBIN/:$CLASSPATH
export NOTESBIN NOTESDATA NOTESDIR LD_LIBRARY_PATH PATH CLASSPATH

$standalone.linux.personality

Error :
(process:20359): Gdk-WARNING **: locale not supported by C library

(<unknown>:20359): Gtk-WARNING **: Locale not supported by C library.
        Using the fallback 'C' locale.
notes: LD_LIBRARY_PATH = /home/dschaefer79/notes:/home/dschaefer79/notes/jvm/bin/classic:/home/dschaefer79/notes/jvm/bin:/opt/IBM/Workplace/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin/j9vm:/opt/IBM/Workplace/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/opt/IBM/Workplace/rcp/eclipse/features/com.ibm.rcp.jre.linux.feature_1.3.0/jre/bin:/home/dschaefer79/notes:/home/dschaefer79/notes/jvm/bin/classic:/home/dschaefer79/notes/jvm/bin:/usr/../usr/lib/mozilla
/home/dschaefer79/notes/notes: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
nsdexec: notespid = 20388

---

### Post by dschaefer79 on 2006-11-28
Now I've installed all the lib32 from Ubuntu 32 bit and now lotus notes starts but it complains about this :

ERROR: ld.so: object 'libjsig.so' from LD_PRELOAD cannot be preloaded: ignored.

Can you help me ?
Thanks

---

### Post by d3mia7 on 2006-12-20
Since I don't see ALL the required steps together in one post here goes...

**Get package**
The best way is to get it from Partnerworld program.
Name of package is: C93D1NA.zip

**Prerequisites**
1, install mozilla package - should be >= 1.7.12 (apt-get install mozilla-browser)
2, create symlink to mozilla binary (ln -sf /usr/bin/mozilla-suite /usr/bin/mozilla)
3, edit /etc/gre.d/gre.conf to match your mozilla version (you can also add symlink /etc/gre.conf)
insert:

```
[1.7.13] GRE_PATH=/usr/lib/mozilla
```

4. install motif3: (sudo apt-get install libmotif3)
5. create a symlink for libmotif: (ln -sf /usr/lib/libXm.so.3 /usr/lib/libXm.so.2)
6. on Edgy only create a new symlink for sh: (ln -sf /bin/bash /bin/sh)
7. edit /etc/cups/printers.conf:

```
Replace <Printer LaserJet-4250>
with
<DefaultPrinter LaserJet-4250>
```

8. not required but improves performance: ```
sudo touch /etc/ld.so.hwcap
```
[B]
Install[/B]
1, unpack C93D1NA.zip (unzip -d lotus C93D1NA.zip)
2, unpack Personality.zip
3, chmod +x on lotus/setup_wct_platform.bin and setuplinux.bin
4, copy setuplinux.bin to updateSite/features/com.ibm.workplace.notesinstall.linux.feature_7.0.1 .0000-0900/bin/linux/
5, run installer ./lotus/setup_wct_platform.bin as non-root user (it'll be a little bit complicated installing it as root, but it's possible)
6, as first, there will be Workplace Manged Client installed (agree to
licenses, set install path etc. to install it - don't forget to set privileges on install dirs ) and then you will be asked to install Lotus Notes Client plug-in, so be patient. At the end launch icon will be installed to your desktop.
7, after installation, empty client will be started so don't panic
8, close client

**To start the client:**

Create a new script with the following as its contents:

```

#!/bin/bash

. $HOME/.bash_profile

$HOME/opt/IBM/Workplace\ Managed\ Client/rcp/richclient -personality com.ibm.workplace.noteswc.standalone.linux.personality

```

Change your desktop icon to point to the script (don't forget to make it executable!)

Once you've done all of this you can make your Notes client faster by going through the 'Local Replica' steps in this document:

**[Understanding and implementing local mail replicas for Lotus Notes]("http://www-128.ibm.com/developerworks/lotus/library/local-mail-replicas/")**

---

### Post by d3mia7 on 2006-12-21
One more thing...

If your Notes client crashes for some reason you may notice that you have trouble getting it to start again.  Sometimes even quitting the client normally results in errors when trying to restart.

In order to clean everything up PROPERLY I figured out the following:

1.  Go to your notes/data directory (ie $HOME/notes/data)
2.  Run this command:

```
../nsd.sh -kill
```

This will shut down any remaining notes processes and clean everything up properly.  Sometimes you need to do this even if NSD has run on its own!  

According to some Lotus documentation for the Windows version it is important to actually be in the 'data' directory - you supposedly shouldn't just execute nsd.sh from wherever.  I haven't tried to find out!

---

### Post by bodhi.zazen on 2006-12-24
Nice How-to

This thread has been added to the UDSF wiki.

[Lotus_Notes](http://doc.gwos.org/index.php/Lotus_Notes)

---

### Post by andrea81 on 2006-12-28
Hi boys,
happy christmas to all....

I'm trying to install the lotus notes client, following your councils, but i've a problem with the version of mozilla.
I've done:
[LIST]
[*]install mozilla package - should be >= 1.7.12 (apt-get install mozilla-browser)
[*]create symlink to mozilla binary (ln -sf /usr/bin/mozilla-suite /usr/bin/mozilla)
[*]edit /etc/gre.d/gre.conf to match your mozilla version and insert code: 
    [1.7.13] 
    GRE_PATH=/usr/lib/mozilla
[/LIST]

When i run installer "setup_wct_platform.bin" as non-root user, i've the problem.

"impossible check the version of Mozilla"

and close the installer.
I've tried to install again and uninstall again mozilla and fireforx...but nothing to do. The result is always the same.

Someone you would know to help me? :confused: ](*,) ](*,) ](*,) ](*,)  :-# 

thanks....
bye bye

Andrea81

---

### Post by kbudurka on 2007-01-15
> **acascianelli said:**
> With that script, it freezes at the splash screen.  Then it pops up saying it cannot find the notes.ini.  On the console I see these messages...



And when I create an empty notes.ini file using the touch command I get the following at the console.

In the Windows world, I have solved many problems by deleting all but the first few lines of the notes.ini file. Knowing this, why not try to touch a notes.ini file, but then add these first 4 lines:

[Notes]
Directory=/home/xxxx/notes/data
DND_ENABLED=1
KitType=1

* where xxxx = your home directory.

---

### Post by lorenzo on 2007-01-19
Hi all,
I have followed the instruction but for me too:

"impossible check the version of Mozilla"

Any suggestion?

thanks, 
lorenzo

UPDATE: Solved!
I should have red the posts more carefully /bin/dash -> /bin/bash change does the trick!

---

### Post by ben42 on 2007-01-19
i followd the instructions of d3mia7 (thx a lot!!) and ended with an empty work place and missed the notes wizard for configuration the notes plugin.

to solve this issue i had to execute a 

chmod +x $HOME/notes


and after that the notes-wizard pops up after starting the workplace client

---

### Post by dvwijk on 2007-01-21
Hi,

just tried to install notes but it is stopping when it is trying to install workplace managed client...

I do get the first screen where it is telling me it will install Lotus Notes Plugin 

then after clicking next I am getting license agreement  still going strong :cool: 

then I get the question about where to install the managed client.. I choose /home/username/IBM/Workplace Managed Client. Click next again ;) 

And then the fun stops.... I have the following "empty" screen:

[ATTACH]23609[/ATTACH]

With the Next button grayed out.... 

What am I doing wrong???

---

### Post by hoppel118 on 2007-01-24
Malmo, you are the godfather of Lotus Notes 7.0.1! :D 

I got it work on ubuntu edgy!

Thanks a lot also to all the other ubuntuforum-members completed this thread!!!


Greetz from Germany, Hamburg

---

### Post by Blues- on 2007-01-29
All of you who got this working .. are you using Gnome ?
I can't get this to work on KDE ..
I get the empty window and a error about no notes.ini begin found.

Any suggestions ?

---

### Post by DFLiddle on 2007-01-29
After following the instructions posted, I still receive the error, "Cannot validate Mozilla version". Do any of you have suggestions? What information could I provide that might provide a clue about what's causing this to fail?

Edit1: Later, I saw the subsequent posts that deal with the issue and implemented them. Sorry for not being thorough in reading the whole thread. The installation proceeded without errors, but it failed to place an icon on my desktop. How do I make a proper shortcut for Notes? This installation was on a virtual machine, and I intend to try it on another instance of Edubuntu on my notebook.

Edit2: Followed ALL of the instructions (eventually) and successfully installed the client on my notebook. The last key was setting the right permissions on the WMC directory. However, I'm still facing the empty client.

---

### Post by Mallah on 2007-02-01
first of all thx for the howto..

bu i am testing it, but it doesnt work..


i get an error:

mozilla-version coult not be checked...


i have no idea...

> ii  mozilla-browser       1.7.13-0.2ubuntu1     The Mozilla Internet application suite - core and browser

> ubuntu@R51:/lotus/plugin$ echo $GRE_PATH
/usr/lib/mozilla

> ubuntu@R51:/lotus/plugin$ cat /etc/gre.d/gre.conf 
[1.7.13]
GRE_PATH=/usr/lib/mozilla

can anyone help me please???

---

### Post by mrraph on 2007-02-05
To solve the "cannot valide mozilla" problem,
I had to add some line in the gre.conf file

Btw i don't know if it will use /etc/gre.conf or /etc/gre.d/gre.conf, so i create both files.

```

[1.4]
GRE_PATH=/usr/lib/mozilla
[1.7.13]
GRE_PATH=/usr/lib/mozilla


```

---

### Post by hraposo on 2007-02-05
Can you put here the link for C93D1NA.zip

---

### Post by deadduck on 2007-02-05
Thanks for taking the time to help the rest of us out.  After I run ./lotus/setup_wct_platform.bin The install wizard launches but gives me this error. Any ideas.
Can not validate Mozilla version

---

### Post by kelboy on 2007-02-06
> **deadduck said:**
> Thanks for taking the time to help the rest of us out.  After I run ./lotus/setup_wct_platform.bin The install wizard launches but gives me this error. Any ideas.
Can not validate Mozilla version

when I got that error I didn't have Mozilla browser installed..
install the mozilla browser
try it again

---

### Post by hoppel118 on 2007-02-06
@ mallah &
@ deadduck

If u use ubuntu/kubuntu 6.10 (Edgy Eft) u have to try this:

Please, to everybody, there are always the same questions! Read this thread konsequently and you will find an answer... I got it on my IBM T40 with ubuntu 6.10 and on my PC at work with kubuntu 6.10...

Try this:

[I]>  
1.)everyone who have problems installing Lotus Notes on Edgy should try this command "sudo ln -sf /bin/bash /bin/sh" to solve the problem.

Edgy now uses /bin/dash instead of /bin/bash as the shell for sh. 

After installing Lotus Notes you can switch the link back to "sudo ln -sf /bin/dash /bin/sh". But you should change the first line in the gnome start script to /bin/bash instead of /bin/sh.

This solves the problems:

1) get the Mozilla version at the beginning of the install shield
2) create notes.ini file in your data directory...

For German users the the issue is also described at [http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29](http://wiki.ubuntuusers.de/Edgy_Eft?highlight=%28dash%29)

[/I]

and don't forget to do what "mrraph" described in post 103 and "kelboy" in post 106...

Grüße aus Hamburg

---

### Post by ianw1974 on 2007-02-14
I have kubuntu 6.10 (edgy) installed, and I cannot get this working at all no matter what I try.

I've got Lotus Notes 7.0.1 installed, but every time I launch it, I just get the Window with two panes, and no wizard starts asking me to configure Lotus Notes.

I'm out of ideas on what to try, since all the CLASSPATHS, NOTESBIN, NOTESDATA, NOTESDIR, etc, etc are all correct and yet it still doesn't work in edgy.

I've tried in the KDE environment, and I've also even installed Gnome and tried here as well - with no success.

---

### Post by fiveiron on 2007-02-15
Same thing here.  No matter what I try, I always get the 2 blank panes in the main window and that's it.  Can someone please shed some light on this?

---

### Post by ianw1974 on 2007-02-20
Incidently, it works perfectly fine in Debian 3.1 (aka sarge).  And I've done nothing different that I've done with Debian, than I've done with Ubuntu.

---

### Post by croftd on 2007-02-23
Hi guys, I'm confused as I get a setup wizard for Workplace Managed Client but NOT Lotus Notes. I'm using Edgy and followed all instructions to get to page 11 of this forum. Any suggestions? Has something not worked right? I need to get this working by Monday before my boss notices I've wiped off windows ;)

Crofty.

---

### Post by deepjoy on 2007-02-27
has anybody tried this on feisty RC. there is no mozilla package in the apt repositories

[https://launchpad.net/ubuntu/feisty/i386/mozilla-browser](https://launchpad.net/ubuntu/feisty/i386/mozilla-browser)

says it's been removed

---

### Post by ianw1974 on 2007-02-28
I've managed to get this running so far on:

CentOS
Debian 3.1 (sarge)
Debian Sid (previously etch install)
Gentoo 2006.1
Kubuntu 6.10 (edgy)
RHEL4
Ubuntu 6.10 (edgy)

I've also managed to find a lot of the dependency packages by trial and error.  You need to have the following packages:

libmotif3
mozilla 1.7.13 (although it's OK to just install seamonkey on your distro instead)
libstdc++5
gawk

If you've got printers installed, just go to localhost:631 in cups and make sure it's set as default, so you don't get nsd errors.

Sometimes the install completes but you don't have a notes directory, run setuplinux.bin manually to complete installation.

If you have /usr/lib/xulrunner, then you can use this in /etc/gre.conf or /etc/gre.d/gre.conf as all that Lotus Notes install is doing is running ldd on this libgtkembedmoz.so, so:

```
ldd /usr/lib/xulrunner/libgtkembedmoz.so | grep gtk
```

note, if you're using Mozilla, and you have ANY errors with this ldd result, you have to fix it by installing the missing package it's trying to find.

---

### Post by Darrena on 2007-03-22
This may have already been mentioned but to permit Notes to open attachments directly this worked for me:

```
sudo ln -s /usr/lib/libnautilus-extension.so.1 /lib/libnautilus-private.so.2
```

This is on the Note 8 Beta

---

### Post by td3201 on 2007-04-23
I am trying this out on 7.04.  I can't get beyond the mozilla verification.  I have done the following, not sure what is relevant and what is not:
- installed libmotif3
- installed mozilla 1.7.8 from mozilla.com and placed it in /usr/local
- created /etc/gre.conf with the following contents:
[1.7.8]
GRE_PATH=/usr/local/mozilla-1.7.8

Anyone have any additional tips?

---

### Post by Lem on 2007-04-24
I'm trying it on 7.04 too and was going to get the mozilla-browser as detailed above (it's not in feisty). Did you symlink to the binary?

I'll try the same and see how I get on!

---

### Post by ianw1974 on 2007-04-24
As per my previous message, check the ldd command against the libgtkembedmoz.so in your Mozilla directory.  If it's not working, ldd the file in the Firefox directory or even xulrunner if you have it installed on your system.  A failure in ldd will stop you going any further no matter what you try.

---

### Post by tokyoahead on 2007-04-25
> **ianw1974 said:**
> As per my previous message, check the ldd command against the libgtkembedmoz.so in your Mozilla directory.  If it's not working, ldd the file in the Firefox directory or even xulrunner if you have it installed on your system.  A failure in ldd will stop you going any further no matter what you try.


Ok think I got what you mean. I have the same file in my firefox directory, and I ran ldd on it. The problem is whay I should grep gtk on it like in your previous exaqmple?

I tried w/o and almost all libraries are found except 

        libxpcom.so => not found
        libxpcom_core.so => not found

but these are part of thunderbird, firefox etc which I have installed!
How can those be missing? Also, if I cannot install Mozilla, what version do I enter in the /etc/gre.conf? I only have a /etc/gre.d/firefox.conf ... 

after I installed xulrunner (maybe that heps, who knows?) I got another two config files there, libxul0d.conf and xulrunner.conf

do I have to create the gre.conf? Why do you grep gtk on the ldd? how do I get the libraries?

running ubuntu 7.04

thanks

---

### Post by td3201 on 2007-04-25
Still having some issues.  I have read above and hope I have consolidated everyone's suggestions:

Ubuntu 7.04
Mozilla 1.7.13 (binary from ftp.mozilla.com)

root@foo-lx:~# ls -l /bin/bash
-rwxr-xr-x 1 root root 700560 2007-04-10 18:32 /bin/bash

root@foo-lx:~# ls -l /bin/sh
lrwxrwxrwx 1 root root 4 2007-04-20 10:06 /bin/sh -> bash

root@foo-lx:~# ldd /usr/local/mozilla/libgtkembedmoz.so | grep gtk
        libgtksuperwin.so => /usr/local/mozilla/libgtksuperwin.so (0xb7dd9000)
        libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0xb7c9e000)

root@foo-lx:~# cat /etc/gre.conf 
[1.7.13]
GRE_PATH=/usr/local/mozilla

root@foo-lx:~# dpkg-query -l libmotif3 libstdc++5 gawk
||/ Name                                   Version                                Description
+++-======================================-======================================-============================================================================================
ii  gawk                                   3.1.5.dfsg-4build1                     GNU awk, a pattern scanning and processing language
ii  libmotif3                              2.2.3-1.5                              Open Motif - shared libraries
ii  libstdc++5                             3.3.6-15ubuntu1                        The GNU Standard C++ Library v3


Any ideas after all that?

Thanks!

---

### Post by td3201 on 2007-04-25
Got it working.....follow everyones lead above but be sure to get the right mozilla version with the GTK2 bindings:
[http://releases.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.12/contrib/mozilla-i686-pc-linux-gnu-1.7.12-gtk2+xft.tar.gz](http://releases.mozilla.org/pub/mozilla.org/mozilla/releases/mozilla1.7.12/contrib/mozilla-i686-pc-linux-gnu-1.7.12-gtk2+xft.tar.gz)

Also, use the startup script as already mentioned in this thread to resolve the blank screen mess.  Other than that, life is good, works great.

---

### Post by tokyoahead on 2007-04-28
that helped. I downloaded that version and then ran 

strace -f <notes installer> > /tmp/strace.notes 2>&1

I search the file created for "mozilla" and found out that it searched for /usr/local/mozilla-1.7.12/ and extraceted the the version mentioned in the prev. post to there.

it installed fine

---

### Post by ianw1974 on 2007-05-07
Sorry for late reply.  The Lotus Notes installer does an ldd based on what is configured in your /etc/gre.conf file, so if the ldd doesn't work when you run it manually due to errors, then the notes installer will always fail giving you the usual error message.

For me, on Debian, I had xulrunner installed, and so the ldd on the file in this directory worked.  I then just edited the /etc/gre.conf accordingly, and let it *think* it was Mozilla 1.7.12 when what it really was seeing was xulrunner.  The Notes installer doesn't care what it is, as long as the ldd works, the installer will work.

---

### Post by Aulden on 2007-06-14
Hi all. 

I know everyones probably moved on from this but I have a small issue.

I got it working first of all. Thanks to all those who explained over and over again for us.

But... I get all these folders and files poping up in my home directory now. What's that about? I have a hard enough time keeping it clean and orderly without all these other folders. Can anything be done?

I installed into the directory /opt/IBM as it suggests in the readme. But in Home I get IBM folders (2 I think) and a whole set of files. 

Please... if there is any way around this then great.

---

### Post by ianw1974 on 2007-06-15
It's normal, you should get:

bin
IBM
notes

it's configuration for each user.

---

### Post by Beamvr6 on 2007-07-15
Who can post a working link to C93D1NA.zip? Can't register at the IBM site and the other links are dead.

---

### Post by aNr on 2007-11-14
> **dvwijk said:**
> Hi,

just tried to install notes but it is stopping when it is trying to install workplace managed client...

I do get the first screen where it is telling me it will install Lotus Notes Plugin 

then after clicking next I am getting license agreement  still going strong :cool: 

then I get the question about where to install the managed client.. I choose /home/username/IBM/Workplace Managed Client. Click next again ;) 

And then the fun stops.... I have the following "empty" screen:

[ATTACH]23609[/ATTACH]

With the Next button grayed out.... 

What am I doing wrong???

I got the same issue here. Any solutions to this ?

I'm using Gutsy and Firefox 2.0.0.8 (Mozilla validation works with FF)

Anyone any ideas ?

[http://users.skynet.be/giorgio/IBMLN701.png]("http://users.skynet.be/giorgio/IBMLN701.png")

Many thanks in advance ...

aNr

---

### Post by aNr on 2007-11-17
Any ideas someone. I checked the IBM website, not much information there ....

---

### Post by eyad on 2008-07-08
Dear All,

i try to install lotusnotes 7 in my ubuntu 8.04 but i couldnt i still get this error message "cant validate mozilla version", while i install mozilla 1.7.12 in my system.

this is the output of  mozilla -version:
```
Mozilla 1.7.12, Copyright (c) 2003-2004 mozilla.org, build 2005092014
```

this is the output of cat /etc/gre.d/gre.conf:
```
[1.7.12]
GRE_PATH=/usr/lib/mozilla-1.7.12

```

and this is the out put of ldd "/usr/lib/mozilla-1.7.12/libgtkembedmoz.so":
```
	linux-gate.so.1 =>  (0xb7f89000)
	libxpcom.so => /usr/lib/libxpcom.so (0xb7e87000)
	libplds4.so => /usr/lib/libplds4.so (0xb7e84000)
	libplc4.so => /usr/lib/libplc4.so (0xb7e80000)
	libnspr4.so => /usr/lib/libnspr4.so (0xb7e4c000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e34000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7e30000)
	libgtksuperwin.so => /usr/lib/libgtksuperwin.so (0xb7e2b000)
	libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0xb7ce4000)
	libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0xb7caa000)
	libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0xb7ca7000)
	libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0xb7c81000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb7c79000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c6b000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7b84000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b5f000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a0f000)
	/lib/ld-linux.so.2 (0xb7f8a000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a0c000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7a0a000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb79f2000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb79ec000)

```

---

### Post by Appiah on 2008-09-30
> **eyad said:**
> Dear All,

i try to install lotusnotes 7 in my ubuntu 8.04 but i couldnt i still get this error message "cant validate mozilla version", while i install mozilla 1.7.12 in my system.

this is the output of  mozilla -version:
```
Mozilla 1.7.12, Copyright (c) 2003-2004 mozilla.org, build 2005092014
```

this is the output of cat /etc/gre.d/gre.conf:
```
[1.7.12]
GRE_PATH=/usr/lib/mozilla-1.7.12

```

and this is the out put of ldd "/usr/lib/mozilla-1.7.12/libgtkembedmoz.so":
```
	linux-gate.so.1 =>  (0xb7f89000)
	libxpcom.so => /usr/lib/libxpcom.so (0xb7e87000)
	libplds4.so => /usr/lib/libplds4.so (0xb7e84000)
	libplc4.so => /usr/lib/libplc4.so (0xb7e80000)
	libnspr4.so => /usr/lib/libnspr4.so (0xb7e4c000)
	libpthread.so.0 => /lib/tls/i686/cmov/libpthread.so.0 (0xb7e34000)
	libdl.so.2 => /lib/tls/i686/cmov/libdl.so.2 (0xb7e30000)
	libgtksuperwin.so => /usr/lib/libgtksuperwin.so (0xb7e2b000)
	libgtk-1.2.so.0 => /usr/lib/libgtk-1.2.so.0 (0xb7ce4000)
	libgdk-1.2.so.0 => /usr/lib/libgdk-1.2.so.0 (0xb7caa000)
	libgmodule-1.2.so.0 => /usr/lib/libgmodule-1.2.so.0 (0xb7ca7000)
	libglib-1.2.so.0 => /usr/lib/libglib-1.2.so.0 (0xb7c81000)
	libXi.so.6 => /usr/lib/libXi.so.6 (0xb7c79000)
	libXext.so.6 => /usr/lib/libXext.so.6 (0xb7c6b000)
	libX11.so.6 => /usr/lib/libX11.so.6 (0xb7b84000)
	libm.so.6 => /lib/tls/i686/cmov/libm.so.6 (0xb7b5f000)
	libc.so.6 => /lib/tls/i686/cmov/libc.so.6 (0xb7a0f000)
	/lib/ld-linux.so.2 (0xb7f8a000)
	libXau.so.6 => /usr/lib/libXau.so.6 (0xb7a0c000)
	libxcb-xlib.so.0 => /usr/lib/libxcb-xlib.so.0 (0xb7a0a000)
	libxcb.so.1 => /usr/lib/libxcb.so.1 (0xb79f2000)
	libXdmcp.so.6 => /usr/lib/libXdmcp.so.6 (0xb79ec000)

```

Running 8.04 too

I had to apt-get install libghc6-mozembed-dev
then ln -s /usr/lib/libgtkembedmoz.so /usr/lib/mozilla

That fixed it for me

---

### Post by mankygitt on 2008-10-21
FYI - Lotus Notes Client 8.0.1/8.0.2 for linux installs very simply and easily on Ubuntu 8.0.4
There are no required tweaks and hacks - it just works.

8.0.1 worked but was pretty sluggish.
8.0.2 is a marked improvement in speed.

The release 8 interface is a very nice overhaul of the notes interface - which one has to say was aging.

---

