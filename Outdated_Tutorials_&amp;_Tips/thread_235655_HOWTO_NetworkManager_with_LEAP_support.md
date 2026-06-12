---
title: "HOWTO: NetworkManager with LEAP support"
date: 2006-08-13
forum: Outdated Tutorials &amp; Tips
---

### Post by misha680 on 2006-08-13
** !!! THIS IS REALLY OUTDATED. nm-applet 0.6.5 and later on has LEAP support (this is the version in gutsy) !!!**

** Feisty debs are [http://ubuntuforums.org/showthread.php?p=2663064#post2663064](http://ubuntuforums.org/showthread.php?p=2663064#post2663064) **

Hi, these are debs I have made of the CVS version of NetworkManager. This includes LEAP support and also one checkinstalled deb that is included is the VPNC plugin. To install these debs simply click on the attachment that starts with dapper for Dapper Drake 6.06 systems or the one that starts with Edgy for Edgy Eft 6.10 systems, open with Archive Manager (this should be an option from firefox), and extract the files somewhere (e.g., /tmp). Then, either  type:

```
cd /tmp
sudo dpkg -i *.deb
```

or find /tmp in Nautilus (Places->Filesystem->tmp) and double click on each .deb file to install with the GDebi installer. Then log out, log in and you should see the network manager applet in your top right-hand corner. That is all you need to do. To create a new LEAP wireless network, click on the network manager icon, click on "Create a new Wirless network" and you will see LEAP as an allowed network protocol. Enjoy!

Misha

p.s. In order for the vpnc plug-in to work correctly you must have the vpnc package installed. Either type:

```
sudo aptitude install vpnc
```

or "Search" for the vpnc plugin in Synaptic Pacakage Manager, right click on it, and select "Mark for Installation" then Apply.

p.p.s If you'd like to compile it yourself, it is very easy too. To get the CVS repositories, just type these commands:

```
sudo apt-get remove network-manager.*
sudo apt-get remove libnm.*
sudo apt-get install automake1.9
sudo apt-get build-dep network-manager
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome login
cvs -d :pserver:anonymous@anoncvs.gnome.org:/cvs/gnome co NetworkManager
cd NetworkManager
gedit configure.in
```

Now, find the line that says:

```
        CFLAGS="-Wall -Werror -std=gnu89 $CFLAGS"

```

and change it to read:

```
        CFLAGS="-Wall -std=gnu89 $CFLAGS"

```

Great, now to compile and install it (I am using the checkinstall utility to make the debs and install it, if you just want to install it without it also making debs just use "sudo make install" instead):

```
./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var
make
sudo checkinstall --pkgname=network-manager
```

Only catch here, checkinstall (and debian packages) don't like certain things in the version numbers, so you must change it. I use something like cvs20060914 to indicate the date when I made the package.

That's it. You will still need the two files in network-manager-scripts.tar.bz2 that are attached. You can try getting them off the old network-manager debs from the repositories too if you want (they are both in /etc/dbus-1/system.d).

---

### Post by dave_abrahams on 2006-08-18
Some obstacles I ran into here:

1. building from CVS requires automake-1.9.  No need to download the automake sources as I discovered after much flailing.  Simply

```
sudo apt-get install automake1.9
```

2. In addition to removing network-manager before starting this process, I had to 

```
sudo apt-get remove libnm-util0
```

3. The icon nm-vpn-lock is not present in my theme, which causes problems for nm-applet.

> The NetworkManager applet could not find some required resources.  It cannot continue.

The fix, from elsewhere on this forum, is:

```
sudo gtk-update-icon-cache -f /usr/share/icons/hicolor
```

I hope this helps someone.  Maybe this HOWTO should be copied off the forums to some Wiki?

---

### Post by misha680 on 2006-08-18
Deleted

---

### Post by deception1 on 2006-08-27
Is this the normal dialoge when connecting to a vpn?

Memory status: size: 18178048 vsize: 0 resident: 18178048 share: 0 rss: 6520832 rss_rlim: 0
CPU usage: start_time: 1156658273 rtime: 0 utime: 19 stime: 0 cutime:16 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/nm-vpnc-auth-dialog'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1224554832 (LWP 6328)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb74982e3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f2bed5 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7536da2 in gnome_keyring_find_network_password_sync ()
   from /usr/lib/libgnome-keyring.so.0
#5  0x0804a10c in ?? ()
#6  0x08063618 in ?? ()
#7  0x00000000 in ?? ()

Thread 1 (Thread -1224554832 (LWP 6328)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74982e3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f2bed5 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7536da2 in gnome_keyring_find_network_password_sync ()
   from /usr/lib/libgnome-keyring.so.0
No symbol table info available.
#5  0x0804a10c in ?? ()
No symbol table info available.
#6  0x08063618 in ?? ()
No symbol table info available.
#7  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
#-o 

Pascal.:-\"

---

### Post by misha680 on 2006-08-27
Hmm... doesn't seem like it is for me. Does the VPN connection still work? If not, I'd suggest joining the network-manager developer list (see the NetworkManager web site, the developers subsection) and sending it to them. I'm sure they'd be more than likely to help.

Misha

> **deception1 said:**
> Is this the normal dialoge when connecting to a vpn?

Memory status: size: 18178048 vsize: 0 resident: 18178048 share: 0 rss: 6520832 rss_rlim: 0
CPU usage: start_time: 1156658273 rtime: 0 utime: 19 stime: 0 cutime:16 cstime: 0 timeout: 3 it_real_value: 0 frequency: 0

Backtrace was generated from '/usr/libexec/nm-vpnc-auth-dialog'

(no debugging symbols found)
Using host libthread_db library "/lib/tls/i686/cmov/libthread_db.so.1".
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
(no debugging symbols found)
[Thread debugging using libthread_db enabled]
[New Thread -1224554832 (LWP 6328)]
0xffffe410 in __kernel_vsyscall ()
#0  0xffffe410 in __kernel_vsyscall ()
#1  0xb74982e3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
#2  0xb7f2bed5 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
#3  <signal handler called>
#4  0xb7536da2 in gnome_keyring_find_network_password_sync ()
   from /usr/lib/libgnome-keyring.so.0
#5  0x0804a10c in ?? ()
#6  0x08063618 in ?? ()
#7  0x00000000 in ?? ()

Thread 1 (Thread -1224554832 (LWP 6328)):
#0  0xffffe410 in __kernel_vsyscall ()
No symbol table info available.
#1  0xb74982e3 in __waitpid_nocancel ()
   from /lib/tls/i686/cmov/libpthread.so.0
No symbol table info available.
#2  0xb7f2bed5 in gnome_gtk_module_info_get () from /usr/lib/libgnomeui-2.so.0
No symbol table info available.
#3  <signal handler called>
No symbol table info available.
#4  0xb7536da2 in gnome_keyring_find_network_password_sync ()
   from /usr/lib/libgnome-keyring.so.0
No symbol table info available.
#5  0x0804a10c in ?? ()
No symbol table info available.
#6  0x08063618 in ?? ()
No symbol table info available.
#7  0x00000000 in ?? ()
No symbol table info available.
#0  0xffffe410 in __kernel_vsyscall ()
#-o 

Pascal.:-\"

---

### Post by TheAngryPenguin on 2006-09-12
Upon trying to compile Network Manager from CVS, I receive the following errors:

During ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var:

```
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.
```

...and then during sudo checkinstall --pkgname=network-manager:

```
Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]:
```

log file:

```
dpkg-deb: parse error, in file `/var/tmp/cAMpnBAUkEkrlSgLMdBba/package/DEBIAN/control' near line 8 package `network-manager':
 newline in field name `0.7.0'
```

Any ideas?

---

### Post by minchina on 2006-09-14
It looks like a new knetworkmanager package just came online in adept.  Is this the same package that you are talking about manually installing?  If so, I am still having problems finding LEAP support in the options.  There are three WEP options and two WPA options, but none of them seem to have metion LEAP anywhere.  If this new update is not the one that you have been manually updating, is there anything that I should change in the instructions when installing on Kubuntu?

Thanks

---

### Post by misha680 on 2006-09-14
Ok, I think the first one may be solved by
doing

```
sudo apt-get install gnome-common
```

maybe also try 

```
sudo apt-get automake1.9
```

But if you're getting to the make install part, it's probably not a problem.

As for the checkinstall problem, you just have
to remember to change the version number
(the package system doesn't like a bunch of
them, I don't remember the exact rules,
I use something like cvs20060914 to keep
track of mine as version numbers).

Misha

> **TheAngryPenguin said:**
> Upon trying to compile Network Manager from CVS, I receive the following errors:

During ./autogen.sh --prefix=/usr --sysconfdir=/etc --localstatedir=/var:

```
Please add the files
  codeset.m4 gettext.m4 glibc21.m4 iconv.m4 isc-posix.m4 lcmessage.m4
  progtest.m4
from the /usr/share/aclocal directory to your autoconf macro directory
or directly to your aclocal.m4 file.
You will also need config.guess and config.sub, which you can get from
ftp://ftp.gnu.org/pub/gnu/config/.
```

...and then during sudo checkinstall --pkgname=network-manager:

```
Striping ELF binaries and libraries...OK

Compressing man pages...OK

Building file list...OK

Building Debian package... FAILED!

*** Failed to build the package

Do you want to see the log file?  [y]:
```

log file:

```
dpkg-deb: parse error, in file `/var/tmp/cAMpnBAUkEkrlSgLMdBba/package/DEBIAN/control' near line 8 package `network-manager':
 newline in field name `0.7.0'
```

Any ideas?

---

### Post by misha680 on 2006-09-14
I would guess that they would not be putting up
the CVS versions, but probably 0.64 (or is it
0.6.4?). CVS is pretty much the most up-to-date
development version, and I think they are 
slating LEAP support for 0.7. In any case,
if you don't see it it is not there. I am not
sure if you need to do anything different for
KDE. How do you run network-manager on KDE
(I assume it is not using nm-applet)?

Misha

> **minchina said:**
> It looks like a new knetworkmanager package just came online in adept.  Is this the same package that you are talking about manually installing?  If so, I am still having problems finding LEAP support in the options.  There are three WEP options and two WPA options, but none of them seem to have metion LEAP anywhere.  If this new update is not the one that you have been manually updating, is there anything that I should change in the instructions when installing on Kubuntu?

Thanks

---

### Post by minchina on 2006-09-14
I just start knetworkmanager from the K menu.  I can also do wireless with the wireless assistant application, but knetworkmanager seems like a more sophisticated option.  I want to have this LEAP capability, but I am far from a linux ninja and I am worried that if I remove knetworkmanager and something goes wrong on the installation I will be totallly without wireless.  
I will try and find some information about dealing with deb packages in kubuntu so that I can do it this way.  This may be a question that you can't answer, but do you have any sense as to the kind of time frame this version would be released indo adept?

thanks

---

### Post by misha680 on 2006-09-15
I am guessing it is going to be a looong time before it is up on the main packages, as they only even added code to do this to the CVS version a month or so ago, although on the other hand it works quite well (I was really proud of the fact that LEAP works with ndiswrappers on my friends cheap Compaq computer that doesn't even support LEAP in Windows :) ) so maybe sooner.

What I would do if it was me would be just to try it. I think you can keep the knetworkmanager package around (although it might not let you do that if you delete the network-manager packages). Maybe you could also try reinstalling it after you follow my installation procedures. However, it could very well give some dependency errors. I would have to investigate this further.

However, since with my instructions you are using checkinstall to install it, that creates a "deb" package and installs it, so if it doesn't work you should just be able to remove it with your favorite package manager (adept, I am not too familiar with it as I use synaptic).

Especially since you have wireless network support with wireless ninja as well, it should be pretty straightforward if something goes wrong to just remove the network-manager packages that following the HOWTO will install and reinstall the default Kubuntu ones. However, on the other hand, I don't know how likely it is to work, as knetworkmanager probably wants a specific version of the network manager packages. Hmm... Anyhow, I say it is worth a try, but only if you feel comfortable removing the packages for network-manage rCVS after they have been installed and then reinstalling knetworkamanger.

Misha

> **minchina said:**
> I just start knetworkmanager from the K menu.  I can also do wireless with the wireless assistant application, but knetworkmanager seems like a more sophisticated option.  I want to have this LEAP capability, but I am far from a linux ninja and I am worried that if I remove knetworkmanager and something goes wrong on the installation I will be totallly without wireless.  
I will try and find some information about dealing with deb packages in kubuntu so that I can do it this way.  This may be a question that you can't answer, but do you have any sense as to the kind of time frame this version would be released indo adept?

thanks

---

### Post by minchina on 2006-09-17
I gave it a shot.  The good news is that I can still get online wirelesly with the kde wireless assistant, so nothing is broken.  Unfortunately I can't get network manager to start.  I tried to use the non-vpnc package first and got this:

dpkg -i '///home/micha
(Reading database ... 135416 files and directories currently installed.)
Preparing to replace network-manager 0.6.2-0ubuntu7 (using .../network-manager_cvs20060815-1_i386.deb) ...
Unpacking replacement network-manager ...
dpkg: error processing ///home/michael/Download/Network manager files/network-manager_cvs20060815-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libnm-util.so.0.0.0', which is also in package libnm-util0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ///home/michael/Download/Network manager files/network-manager_cvs20060815-1_i386.deb
RESULT=1


I did not know how to fix that, so I just tried to use the vpnc package.  That gave me this:

<iles/network-manager-vpnc_cvs20060815-1_i386.deb' ;echo RESULT=$?
Selecting previously deselected package network-manager-vpnc.
(Reading database ... 135416 files and directories currently installed.)
Unpacking network-manager-vpnc (from .../network-manager-vpnc_cvs20060815-1_i386.deb) ...
Setting up network-manager-vpnc (cvs20060815-1) ...
RESULT=0

Not seeing any error messages, I followed the rest of the directions to install the scrips.  That went off until I tried the last line (which I assume launches the program) and I got a 'command not found' response.

Any ideas?  The program show up as installed in adept.  Is there any additional information I can give you?

Thanks for the work that you put into the howto and sorry to have to keep asking you questions.

---

### Post by misha680 on 2006-09-17
No prob. For that first error you just need to remove the libnm-util0 package. You can just do

```
sudo aptitude remove libnm-util0
```

or

```
sudo apt-get remove libnm-util0
```

(the first one is usually smarter about removing packages). The VPNC package is just an
add on to network manager base so it would not do anything unless the other package is
installed too. Hope that helps.

Misha

> **minchina said:**
> I gave it a shot.  The good news is that I can still get online wirelesly with the kde wireless assistant, so nothing is broken.  Unfortunately I can't get network manager to start.  I tried to use the non-vpnc package first and got this:

dpkg -i '///home/micha
(Reading database ... 135416 files and directories currently installed.)
Preparing to replace network-manager 0.6.2-0ubuntu7 (using .../network-manager_cvs20060815-1_i386.deb) ...
Unpacking replacement network-manager ...
dpkg: error processing ///home/michael/Download/Network manager files/network-manager_cvs20060815-1_i386.deb (--install):
 trying to overwrite `/usr/lib/libnm-util.so.0.0.0', which is also in package libnm-util0
dpkg-deb: subprocess paste killed by signal (Broken pipe)
Errors were encountered while processing:
 ///home/michael/Download/Network manager files/network-manager_cvs20060815-1_i386.deb
RESULT=1


I did not know how to fix that, so I just tried to use the vpnc package.  That gave me this:

<iles/network-manager-vpnc_cvs20060815-1_i386.deb' ;echo RESULT=$?
Selecting previously deselected package network-manager-vpnc.
(Reading database ... 135416 files and directories currently installed.)
Unpacking network-manager-vpnc (from .../network-manager-vpnc_cvs20060815-1_i386.deb) ...
Setting up network-manager-vpnc (cvs20060815-1) ...
RESULT=0

Not seeing any error messages, I followed the rest of the directions to install the scrips.  That went off until I tried the last line (which I assume launches the program) and I got a 'command not found' response.

Any ideas?  The program show up as installed in adept.  Is there any additional information I can give you?

Thanks for the work that you put into the howto and sorry to have to keep asking you questions.

---

### Post by minchina on 2006-09-17
Of course.  That worked great and everything seemed to be cooking until I got to the nm-applet --sm-disable command.  That gave me this:

nm-applet: error while loading shared libraries: libpanel-applet-2.so.0: cannot open shared object file: No such file or directory


I tried to reboot, but still the same thing.  What is my next step?

thanks

---

### Post by misha680 on 2006-09-17
Ok, try this. I did a google search on knetworkmanager and found the homepage. They have a compilation script on there. Just
download the script from this link:

[http://nouse.net/projects/KNetworkManager/build-knm-svn-head.sh](http://nouse.net/projects/KNetworkManager/build-knm-svn-head.sh)

Save it somewhere (say in your home folder). Now open your home folder, right click on the file, go to the permissions tab, click on execute. Close the permissions dialog. Now right click, "open with other application," select "gedit," change the line that says "sudo make install" to "sudo checkinstall" (or if you want you can just leave it too, but this will not create a package). Now double click on the script to run it, when you get to checkinstall make sure to put in some options like a version number, and then hopefully it will work when it is done compiling and installing.

Also, before you run the script, you might want to make sure it has all the dependencies to compile by typing the following command in a terminal:

```
sudo apt-get build-dep knetworkmanager
```

Anyhow, those are just my guesses as I have no way to actually try it out with no KDE system handy.

Misha

> **minchina said:**
> Of course.  That worked great and everything seemed to be cooking until I got to the nm-applet --sm-disable command.  That gave me this:

nm-applet: error while loading shared libraries: libpanel-applet-2.so.0: cannot open shared object file: No such file or directory


I tried to reboot, but still the same thing.  What is my next step?

thanks

---

### Post by minchina on 2006-09-18
Thanks for all of the help.  I think that I may have to take a pass on this one for now.  The script was very unhappy when I ran it, so I tried to track down my missing libpanel-applet2-0.  It turns out that it is a library for GNOME applets. I installed it and started to run nm-applet but got a bunch of error messages about things failing, culminating in a message about failing to find resources.   I guess I will just have to wait until it comes out in adept.


Thanks again

---

### Post by misha680 on 2006-10-27
In case anyone is using Edgy and wants NetworkManager CVS, I made debs (real debs this time, not checkinstalled  - except vpnc deb) attached.

Misha

---

### Post by TrumpetMan258 on 2006-10-27
Hi.  I followed your guide exactly, by just copying and pasting the commands into the terminal.  Everything seemed to work fine, up until I entered "sudo /etc/init.d/dbus restart", at which point I got this:

```
* Stopping System Tools Backends system-tools-backends                  [ ok ] 
 * Stopping NetworkManager dispatcher                                    [ ok ] 
 * Stopping Avahi mDNS/DNS-SD Daemon: avahi-daemon                       [fail] 
 * Stopping NetworkManager daemon                                        [ ok ] 
 * Stopping Hardware abstraction layer hald                              [ ok ] 
 * Stopping system message bus dbus                                      [ ok ] 
 * Starting system message bus dbus                                      [ ok ] 
 * Starting Hardware abstraction layer hald                              [ ok ] 
 * Starting NetworkManager daemon                                               /usr/sbin/NetworkManager: error while loading shared libraries: libnl.so.1: cannot open shared object file: No such file or directory
run-parts: /etc/dbus-1/event.d/25NetworkManager exited with return code 127
 * Starting NetworkManager dispatcher                                           /usr/sbin/NetworkManagerDispatcher: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory
run-parts: /etc/dbus-1/event.d/26NetworkManagerDispatcher exited with return code 127
 * Starting System Tools Backends system-tools-backends                  [ ok ] 
```

I then tried to enter "nm-applet --sm-disable", but that just gave me the same complaint about libdbus-1.so.2.

Does anyone have any ideas as to what I need to do?

---

### Post by misha680 on 2006-10-27
Are you on edgy? If so you might need to do:

```
sudo aptitude install libdbus-1-2
```

or you could just try to install the debs I made two posts up which are actually real debs so should work better I think. If you're on dapper, I might try just installing network-manager from the repositories first (use Synaptic Package Manager), then removing it, and try the procedure again, as perhaps you are missing some dependencies that that should take care of (thus the problem making checkinstalled debs).

Misha

---

### Post by FrankL on 2006-10-28
I updated to Edgy and lost my networkmanager in the process. Now I'm trying to reinstall it, but get the same errors as some others:

frank@frank-laptop:~/Downloads$ nm-applet --sm-disable
nm-applet: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

This happens when I installed it using Synaptic, with the guide from the first posts and with the debs. If I try to install libdbus, the result is the following:

frank@frank-laptop:~/Downloads$ sudo aptitude install libdbus-1-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for libdbus-1-2
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

And Synaptic doesn't want to install it either. Anyone any idea how to fix this? Would be great, thanks in advance!

---

### Post by misha680 on 2006-10-28
You used the debs from post #17?

Misha

> **FrankL said:**
> I updated to Edgy and lost my networkmanager in the process. Now I'm trying to reinstall it, but get the same errors as some others:

frank@frank-laptop:~/Downloads$ nm-applet --sm-disable
nm-applet: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

This happens when I installed it using Synaptic, with the guide from the first posts and with the debs. If I try to install libdbus, the result is the following:

frank@frank-laptop:~/Downloads$ sudo aptitude install libdbus-1-2
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Reading extended state information      
Initializing package states... Done
Building tag database... Done      
No candidate version found for libdbus-1-2
No packages will be installed, upgraded, or removed.
0 packages upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 0B will be used.
Writing extended state information... Done

And Synaptic doesn't want to install it either. Anyone any idea how to fix this? Would be great, thanks in advance!

---

### Post by plush2 on 2006-10-28
> **misha680 said:**
> Ok, I think the first one may be solved by
doing

```
sudo apt-get install gnome-common
```

maybe also try 

```
sudo apt-get automake1.9
```

But if you're getting to the make install part, it's probably not a problem.

As for the checkinstall problem, you just have
to remember to change the version number
(the package system doesn't like a bunch of
them, I don't remember the exact rules,
I use something like cvs20060914 to keep
track of mine as version numbers).

Misha

I had the same error.  When the details of the build package came up mine had a strange list for 
item 3 that had a list of repeating "0.7.0" with carriage returns between them. I simply hit #3 at that point to edit that entry, changed it to a single instance of "0.7.0" and hit return.  This allowed the package to build and install without issue.

I hope this helps.

---

### Post by FrankL on 2006-10-30
Yup, I used the debs. Same result though.

---

### Post by TrumpetMan258 on 2006-10-30
Okay, I used those debs and got everything working.  The wireless card is being recognized and network-manager is seeing the network signal.  But network-manager won't connect to the network (using leap, of course).  I know I'm putting in the right username and password.  Any ideas?

---

### Post by misha680 on 2006-10-30
For FrankL, try the new debs in post #17, I updated them with the latest Edgy network manager debs and latest CVS. As for TrumpetMan, I will think about your problem, but for me the nice thing was that I didn't have problems with LEAP at all. Since the LEAP feature is still in development, I would join the networkmanager-list for development (you don't have to stay joined forever, just for a while, I think it's better that way when you post problems, but even if you don't join I think it should be okay):

[http://mail.gnome.org/mailman/listinfo/networkmanager-list](http://mail.gnome.org/mailman/listinfo/networkmanager-list)

and post your exact set-up & stuff on there, as people on there are more networkmanager savvy than I am. 

The only other thing I would suggest is to try using wpa supplicant to connect to your network. To do that all you have to do is edit /etc/network/interfaces (as sudo of course). This is what worked for me with my LEAP network in that file:

```

iface eth1 inet dhcp
wpa-ssid ssid
wpa-scan-ssid 1
wpa-auth-alg OPEN
wpa-key-mgmt IEEE8021X
wpa-eap LEAP
wpa-ap-scan 2
wpa-identity login
wpa-password password

```

Make sure to change eth1 to your network interfaces and login and password to your login and password (yes they will have to be in that file, that is why I don't like wpa_supplicant, you can do a few tricks to put it in another file that's not world readable). But if you can get it to work with wpa_supplicant and it doesn't work with NetworkManager, I bet they could help you real quick on that mailing list.

Misha

---

### Post by jjhart on 2006-11-01
I have the same problem as Trumpetman.  I don't know if it makes a difference, but the network that I want to join, the SSID is hidden.  I know the SSID and I enter that in, along with my username and password for the network, it has 802.1x LEAP authentication and I have to logon to a certain domain.  I didn't know where to enter the domain so I put domain/username in the username box.  It tried to connect for a few minutes and then gave up.  So now I am back to WINXP so that I can connect and ask you guys questions.  It is really a pain having to get an answer, reboot, try it out, it doesn't work, reboot to WinXp for the internet and start all over again.
To make sure everything was clean, I did a fresh install of edgy and then installed the debs from post 17.  I could connect to an unsecured network at home, just not the leap network here at school.

---

### Post by misha680 on 2006-11-01
The network I use has a hidden SSID too, but it works just fine. Also, I noticed that we have a domain for ours, but i just ignore it (my username i s just username, I don't use the domain anywhere). Ours also uses IEEE 80211x authentication. Our network works on my computer (ipw2100) and also on my coworkers computer (Broadcom something with CVS ndiswrapper on Dapper). So I am not sure hwat the problem is. I would suggest doing what I suggested in my previous post, trying to get it to work with wpa_supplicant by putting the lines I described in /etc/network/interfaces. If that works email the network manager devel list, if it doesn't still probably email them if you can't figure it out and they'll have some suggestions for you I'm sure. Just to clarify I'm just a happy end user and in no way have contributed any code to networkmanager to make the LEAP support work, however, since the LEAP (and all networkmanger WPA) works through wpa_supplicant, if you can get it working with wpa_supplicant settings it should be easy to fix in networkmanager.

Misha

> **jjhart said:**
> I have the same problem as Trumpetman.  I don't know if it makes a difference, but the network that I want to join, the SSID is hidden.  I know the SSID and I enter that in, along with my username and password for the network, it has 802.1x LEAP authentication and I have to logon to a certain domain.  I didn't know where to enter the domain so I put domain/username in the username box.  It tried to connect for a few minutes and then gave up.  So now I am back to WINXP so that I can connect and ask you guys questions.  It is really a pain having to get an answer, reboot, try it out, it doesn't work, reboot to WinXp for the internet and start all over again.
To make sure everything was clean, I did a fresh install of edgy and then installed the debs from post 17.  I could connect to an unsecured network at home, just not the leap network here at school.

---

### Post by jjhart on 2006-11-01
ok so I tried to add that code that you had in an earlier post.  After I save the file, then what?  I restarted the system, now networkmanager didn't even know I had a wireless card.  It only bring up an option for wired network.  Now, in that file there was a bunch of other listings for network settings, I am guessing those were for loopback and my ethernet.  But there was one for wlan and ath0 both.  My card is an internal atheros a/b/g card.  Whenever I had connected previously, it had connected using ath0, so that is the one that edited.  You said to put this in:
[I]iface eth1 inet dhcp
wpa-ssid ssid
wpa-scan-ssid 1
wpa-auth-alg OPEN
wpa-key-mgmt IEEE8021X
wpa-eap LEAP
wpa-ap-scan 2
wpa-identity login
wpa-password password[/I]
I assume that wpa-ssid ssid meant, wpa-ssid "my ssid" right?
also, there was a:[I]
auto ath0
iface ath0 inet dhcp[/I]
was I supposed to add to that or delete it?  after it is edited, am I supposed to restart it?  how do I get it to work?  I am sorry, I am really new and I guess that this is a little bit advanced, but this is a major hurdle I have to get past before I can fully convert to ubuntu

---

### Post by misha680 on 2006-11-01
Ok, sorry, those instructions weren't very good and actually I hadn't even done it like that in quite some time so let me give you something else. Change that file back to the way it was, now make a new file in your home directory called wpa_supplicant.conf and put the following lines in there:

```

ap_scan=2

network={
        ssid="yourssid"
        scan_ssid=1
        auth_alg=OPEN
        key_mgmt=IEEE8021X
        eap=LEAP
        identity="yourusername"
        password="yourpassword"
}

```

Now, to connect you need to try the following commands at a terminal:

```

sudo wpa_supplicant -c~/wpa_supplicant.conf -iath0 -Dwext -B
sudo dhclient ath0

```

Note these are the only commands you will need to connect, by doing this you are keeping networkmanager out of the equation. If this works, and the last command (dhclient) says you have a lease, you're connected, but I expect it won't work because you can't connect through NetworkManger. If it doesn't then you can try playing with the settings in wpa_supplicant.conf. If I remember correctly you can look up info on the file by typing:

```
man wpa_supplicant.conf
```

and also there is a sample file with lots of examples on your system that is reference by this manual page. Also you can play with the wpa_supplicant options (specifically add -d or -dd to show more info which might help diagnose the problem) to get more info about what's going on. This is how I was able to get the wpa_supplicant.conf file above in the first place, which works for me. Anyhow, just worth a shot.

Misha

p.s. The big example configuration file is found at /usr/share/doc/wpasupplicant/examples/wpa_supplicant.conf.gz. It is a gzipped file so you should probably just copy that file to your home directory and gunzip it so you can browse it easier.

> **jjhart said:**
> ok so I tried to add that code that you had in an earlier post.  After I save the file, then what?  I restarted the system, now networkmanager didn't even know I had a wireless card.  It only bring up an option for wired network.  Now, in that file there was a bunch of other listings for network settings, I am guessing those were for loopback and my ethernet.  But there was one for wlan and ath0 both.  My card is an internal atheros a/b/g card.  Whenever I had connected previously, it had connected using ath0, so that is the one that edited.  You said to put this in:
[I]iface eth1 inet dhcp
wpa-ssid ssid
wpa-scan-ssid 1
wpa-auth-alg OPEN
wpa-key-mgmt IEEE8021X
wpa-eap LEAP
wpa-ap-scan 2
wpa-identity login
wpa-password password[/I]
I assume that wpa-ssid ssid meant, wpa-ssid "my ssid" right?
also, there was a:[I]
auto ath0
iface ath0 inet dhcp[/I]
was I supposed to add to that or delete it?  after it is edited, am I supposed to restart it?  how do I get it to work?  I am sorry, I am really new and I guess that this is a little bit advanced, but this is a major hurdle I have to get past before I can fully convert to ubuntu

---

### Post by TrumpetMan258 on 2006-11-01
```
sudo wpa_supplicant -c~/wpa_supplicant.conf -iath0 -Dwext -B
sudo dhclient ath0
```

I am going to try this wpa-supplicant method too and see if it works.  I have a Dell Wireless 1370 card.  Is there anything I need to change in the instructions at the top of my post because I have a different card?

---

### Post by jjhart on 2006-11-01
ok, I will try it.  Any idea when the new stable version of network manager will come out so that those of us with these types of networks won't have to mess with settings just to get something to work?  For the most part I have been very impressed with Ubuntu and so far "it just works" but this is a major hurdle to me.

---

### Post by misha680 on 2006-11-01
Just change ath0 in these commands to your card, mine is eth1 (if you run iwconfig it will list all your cards).

Misha

> **TrumpetMan258 said:**
> ```
sudo wpa_supplicant -c~/wpa_supplicant.conf -iath0 -Dwext -B
sudo dhclient ath0
```

I am going to try this wpa-supplicant method too and see if it works.  I have a Dell Wireless 1370 card.  Is there anything I need to change in the instructions at the top of my post because I have a different card?

---

### Post by FrankL on 2006-11-03
Still the same result I'm afraid, even with the new debs:

frank@frank-laptop:~/Downloads/Wireless$ sudo dpkg -i *.deb
(Reading database ... 165490 files and directories currently installed.)
Preparing to replace libnm-glib0 0.7.0-cvs20061010 (using libnm-glib0_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement libnm-glib0 ...
Preparing to replace libnm-util0 0.7.0-cvs20061010 (using libnm-util0_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement libnm-util0 ...
Preparing to replace network-manager 0.7.0-cvs20061010 (using network-manager_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement network-manager ...
Preparing to replace network-manager-gnome 0.7.0-cvs20061010 (using network-manager-gnome_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement network-manager-gnome ...
Preparing to replace network-manager-vpnc cvs20060815-1 (using network-manager-vpnc_cvs20061030-1_i386.deb) ...
Unpacking replacement network-manager-vpnc ...
Setting up libnm-glib0 (0.7.0-cvs20061030) ...

Setting up libnm-util0 (0.7.0-cvs20061030) ...

Setting up network-manager (0.7.0-cvs20061030) ...
 * Reloading system message bus config                                                                                                                                    [ ok ] 
 * Stopping NetworkManager daemon                                                                                                                                         [ ok ] 
 * Starting NetworkManager daemon                                                                                                                                         [ ok ] 
 * Stopping NetworkManager dispatcher                                                                                                                                     [ ok ] 
 * Starting NetworkManager dispatcher                                                                                                                                     [ ok ] 

Setting up network-manager-gnome (0.7.0-cvs20061030) ...

Setting up network-manager-vpnc (cvs20061030-1) ...

Looking good...

But then:frank@frank-laptop:~/Downloads/Wireless$ nm-applet --sm-disable
nm-applet: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

Anyone got any ideas? Would be great, thanks in advance!

---

### Post by misha680 on 2006-11-03
Hmm... that is so weird... I don't have that file anywhere on my computer (although I did at some point as I updated from Dapper, did you install Edgy directly from CD?) and I don't get any errors. Could you post your output of 

```
dpkg -l | grep dbus
```

Here is mine:

```
ii  dbus                                       0.93-0ubuntu3                            simple interprocess messaging system
ii  dbus-1-utils                               0.93-0ubuntu3                            simple interprocess messaging system (utilit
ii  dhcdbd                                     1.14-2ubuntu2                            dbus interface to the ISC DHCP client
ii  libdbus-1-3                                0.93-0ubuntu3                            simple interprocess messaging system
ii  libdbus-1-cil                              0.63.git.20060719-2ubuntu1               CLI binding for D-BUS interprocess messaging
ii  libdbus-1-dev                              0.93-0ubuntu3                            simple interprocess messaging system (develo
ii  libdbus-glib-1-2                           0.71-1ubuntu1                            simple interprocess messaging system (GLib-b
ii  libdbus-glib-1-dev                         0.71-1ubuntu1                            simple interprocess messaging system (GLib i
ii  libdbus-qt-1-1c2                           0.62.git.20060814-1                      simple interprocess messaging system (Qt-bas
ii  libnet-dbus-perl                           0.33.2-0ubuntu3                          Perl XS API to the dbus inter-application me
ii  python-dbus                                0.71-2ubuntu1                            simple interprocess messaging system (Python

```

Misha

> **FrankL said:**
> Still the same result I'm afraid, even with the new debs:

frank@frank-laptop:~/Downloads/Wireless$ sudo dpkg -i *.deb
(Reading database ... 165490 files and directories currently installed.)
Preparing to replace libnm-glib0 0.7.0-cvs20061010 (using libnm-glib0_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement libnm-glib0 ...
Preparing to replace libnm-util0 0.7.0-cvs20061010 (using libnm-util0_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement libnm-util0 ...
Preparing to replace network-manager 0.7.0-cvs20061010 (using network-manager_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement network-manager ...
Preparing to replace network-manager-gnome 0.7.0-cvs20061010 (using network-manager-gnome_0.7.0-cvs20061030_i386.deb) ...
Unpacking replacement network-manager-gnome ...
Preparing to replace network-manager-vpnc cvs20060815-1 (using network-manager-vpnc_cvs20061030-1_i386.deb) ...
Unpacking replacement network-manager-vpnc ...
Setting up libnm-glib0 (0.7.0-cvs20061030) ...

Setting up libnm-util0 (0.7.0-cvs20061030) ...

Setting up network-manager (0.7.0-cvs20061030) ...
 * Reloading system message bus config                                                                                                                                    [ ok ] 
 * Stopping NetworkManager daemon                                                                                                                                         [ ok ] 
 * Starting NetworkManager daemon                                                                                                                                         [ ok ] 
 * Stopping NetworkManager dispatcher                                                                                                                                     [ ok ] 
 * Starting NetworkManager dispatcher                                                                                                                                     [ ok ] 

Setting up network-manager-gnome (0.7.0-cvs20061030) ...

Setting up network-manager-vpnc (cvs20061030-1) ...

Looking good...

But then:frank@frank-laptop:~/Downloads/Wireless$ nm-applet --sm-disable
nm-applet: error while loading shared libraries: libdbus-1.so.2: cannot open shared object file: No such file or directory

Anyone got any ideas? Would be great, thanks in advance!

---

### Post by jjhart on 2006-11-04
I tried, I really don't know what I am doing.  I think I am little bit too much of a newbie to figure this out.  I will have to stick to using XP at school until "out of the box" LEAP is supported.  Everything else work pretty well so far though.

---

### Post by FrankL on 2006-11-04
Sure I can, here it is:

```

frank@frank-laptop:~$ dpkg -l | grep dbus
ii  dbus                                       0.93-0ubuntu3           simple interprocess messaging system
ii  dbus-1-utils                               0.93-0ubuntu3                 simple interprocess messaging system (utilit
ii  dhcdbd                                     1.14-2ubuntu2                 dbus interface to the ISC DHCP client
rc  libdbus-1-2                                0.60-6ubuntu8                 simple interprocess messaging system
ii  libdbus-1-3                                0.93-0ubuntu3                 simple interprocess messaging system
ii  libdbus-1-cil                              0.63.git.20060719-2ubuntu1    CLI binding for D-BUS interprocess messaging
ii  libdbus-1-dev                              0.93-0ubuntu3                 simple interprocess messaging system (develo
ii  libdbus-glib-1-2                           0.71-1ubuntu1                 simple interprocess messaging system (GLib-b
ii  libdbus-glib-1-dev                         0.71-1ubuntu1                 simple interprocess messaging system (GLib i
ii  libnet-dbus-perl                           0.33.2-0ubuntu3               Perl XS API to the dbus inter-application me
ii  python-dbus                                0.71-2ubuntu1                 simple interprocess messaging system (Python



```

I hope it is of any help .

---

### Post by FrankL on 2006-11-04
Quite interesting to see that I actually have two versions of libd installed... :) Would that be the cause?

---

### Post by misha680 on 2006-11-04
> **FrankL said:**
> Quite interesting to see that I actually have two versions of libd installed... :) Would that be the cause?

Yes I think so. What I would do is use the command:

```
sudo aptitude remove --purge packagename
```

replacing packagename with the name of the libdbus 1.2 package. Aptitude will tell you if it finds any dependencies and will try to resolve them, but you might need to find newer versions of a package if it depends on libdbus 1.2 and aptitude doesn't suggest any good ways to resolve the dependency.

Good luck.

Misha

p.s. Hmm... actually looking further at your post you don't actually have 1.2 installed, it just has residual configuration files installed. This might not fix it. You might also try sudo aptitude install libdbus-qt-1-1c2. Not sure if this will help.

---

### Post by shaungc on 2006-11-06
OK, I have all of the packages from 10302006 installed and nm-applet comes up fine.  But when I try to do "connect to other wireless" and look for EAP protocol LEAP, I only show PEAP, TLS and TTLS.  Am I missing something?  Using a IPW2200 by the way.

---

### Post by misha680 on 2006-11-06
> **shaungc said:**
> OK, I have all of the packages from 10302006 installed and nm-applet comes up fine.  But when I try to do "connect to other wireless" and look for EAP protocol LEAP, I only show PEAP, TLS and TTLS.  Am I missing something?  Using a IPW2200 by the way.

When you click on connect to other wireless network under wireless security you should have a LEAP option. Btw with ipw2200 if you are using Dapper you might have to download updated drivers at ipw2200.sourceforge.net (I know I had to for ipw2100, also needed ieee80211.sourceforge.net drivers).

Misha

---

### Post by shaungc on 2006-11-06
> **misha680 said:**
> When you click on connect to other wireless network under wireless security you should have a LEAP option. Btw with ipw2200 if you are using Dapper you might have to download updated drivers at ipw2200.sourceforge.net (I know I had to for ipw2100, also needed ieee80211.sourceforge.net drivers).

Misha

Strange after a forced reboot (laptop didn't suspend when I closed it, battery died before it overheated in my backpack thankfully) LEAP now shows under wireless security.  I'll check it out at work in the morning.

edit: confirmed to be working, thanks!

---

### Post by mariner09 on 2006-11-10
Misha,

I'm using your packages and when I try to connect to an open AP, it never connects and I get the following in /var/log/messages:

dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason

I have all the dbus packages installed from a previous post.

Any ideas?

---

### Post by misha680 on 2006-11-10
Hi, actually I checked my /var/log/messages and I also have a bunch of these types of messages including the same one as you (except eth1 instead of ath0) so this is probably not the cause of the actual problem you are having. Are you using Edgy or Dapper? 

Misha

> **mariner09 said:**
> Misha,

I'm using your packages and when I try to connect to an open AP, it never connects and I get the following in /var/log/messages:

dhcdbd: message_handler: message handler not found under /com/redhat/dhcp/ath0 for sub-path ath0.dbus.get.reason

I have all the dbus packages installed from a previous post.

Any ideas?

---

### Post by mariner09 on 2006-11-10
It's Edgy.  I've never had any issues until I added this sources.list and NM just stopped.  It would just die and restart when I selected the AP.  Upgrading to your 0.7.0 NM only makes it sit there.  When I try to select the AP, that message appears. 

Is there any logging I can examine, /var/log/messages doesn't show much.

[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

Manual connectivity works, so it doesn't seem to be a driver issue.

---

### Post by misha680 on 2006-11-11
Hmm, well your problem might be deeper as from what you are saying it seems like your standard edgy networkmanager doesn't work when adding the sources.list. I might try to do this, kill off your network manager processes:

```

sudo killall NetworkManager
sudo killall NetworkManagerDispatcher

```

now just run NetworkManager in a terminal:
```

sudo NetworkManager

```

and you will be able to observe all the messages in the terminal (at least this is how I remember it, it's been a while since I've done this).

Misha

> **mariner09 said:**
> It's Edgy.  I've never had any issues until I added this sources.list and NM just stopped.  It would just die and restart when I selected the AP.  Upgrading to your 0.7.0 NM only makes it sit there.  When I try to select the AP, that message appears. 

Is there any logging I can examine, /var/log/messages doesn't show much.

[http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html](http://www.debianadmin.com/ubuntu-edgy-eft-complete-sourceslist-repository-list-file.html)

Manual connectivity works, so it doesn't seem to be a driver issue.

---

### Post by mariner09 on 2006-11-12
Thanks for the pointer...

Here's what I found.  To see the stdout for NetworkManager, it's this:

sudo NetworkManager --no-daemon

This allowed me to see what was happening.  NM was calling /sbin/wpa_supplicant.  In fact, the Ubuntu wpa_supplicant installs /usr/sbin/wpa_supplicant.

I created a symbolic link for /sbin/wpa_supplicant and all is well.

I like the leap support as that's what my company uses, though I haven't had to use it in the office as yet.

I also had something change the permissions on my /etc/resolv.conf so that only root had rw.  It's been a strange weekend.

---

### Post by misha680 on 2006-11-12
I am glad things worked for you. It seems like on my edgy install the wpasupplicant package created /sbin/wpa_supplicant (I ran dpkg -S /sbin/wpa_supplicant to tell me what package owns it).

Misha

> **mariner09 said:**
> Thanks for the pointer...

Here's what I found.  To see the stdout for NetworkManager, it's this:

sudo NetworkManager --no-daemon

This allowed me to see what was happening.  NM was calling /sbin/wpa_supplicant.  In fact, the Ubuntu wpa_supplicant installs /usr/sbin/wpa_supplicant.

I created a symbolic link for /sbin/wpa_supplicant and all is well.

I like the leap support as that's what my company uses, though I haven't had to use it in the office as yet.

I also had something change the permissions on my /etc/resolv.conf so that only root had rw.  It's been a strange weekend.

---

### Post by mariner09 on 2006-11-13
Aahhh, looks like the wpasupplicant I have came from the Trevino repo and it's version 0.5.5-3v1ubuntu1 while the currtent Edgy release is 0.5.4-5.

That could explain the difference....

---

### Post by growse on 2006-11-18
Hi all, just jumping on this bandwagon of trying to get LEAP working on Ubuntu. I've a fresh install of Edgy on a Thinkpad T40 with a Cisco Aironet card (not sure which, doesn't appear to do WPA and is 801.11b only).

I'm not sure if this is supported by wpa_supplicant - am I right that thinking that wpa_supplicant can be used on a non-wpa NIC just to get LEAP capability?

Currently just trying to get it up and running with WEP at the moment. Hopefully, if all goes to plan, the office will let me run Winxp inside a VM on ubuntu, so that I can revert back to a "just installed" snapshot every time it gets really slow.

---

### Post by misha680 on 2006-11-18
I am not really sure what exactly it means that a network card does or does not do WPA, but I think that a lot of times a network card does in fact support WPA, this is just not supported by the Windows drivers for that card (especially LEAP). Specifically, I know this because one of my friends with some Broadcom (I think) card could not use LEAP in Windows but it works fine with NetworkManager (wpa_supplicant as a backend) in Ubuntu.

Misha

> **growse said:**
> Hi all, just jumping on this bandwagon of trying to get LEAP working on Ubuntu. I've a fresh install of Edgy on a Thinkpad T40 with a Cisco Aironet card (not sure which, doesn't appear to do WPA and is 801.11b only).

I'm not sure if this is supported by wpa_supplicant - am I right that thinking that wpa_supplicant can be used on a non-wpa NIC just to get LEAP capability?

Currently just trying to get it up and running with WEP at the moment. Hopefully, if all goes to plan, the office will let me run Winxp inside a VM on ubuntu, so that I can revert back to a "just installed" snapshot every time it gets really slow.

---

### Post by growse on 2006-11-19
> **misha680 said:**
> I am not really sure what exactly it means that a network card does or does not do WPA, but I think that a lot of times a network card does in fact support WPA, this is just not supported by the Windows drivers for that card (especially LEAP). Specifically, I know this because one of my friends with some Broadcom (I think) card could not use LEAP in Windows but it works fine with NetworkManager (wpa_supplicant as a backend) in Ubuntu.

Misha

Agreed, I've seen that sometimes. I think it's about whether the nic has the hardware capability of negotiating natively with an AP using traffic encrypted with WPA. You can probably emulate it in software, which I imagine is what wpa_supplicant does.

Seems the aironet isn't supported by wpa_supplicant for using WPA though :(

---

### Post by Frem on 2006-11-22
I've got an integrated Atheros wifi card in this Toshiba M55-S139 laptop.
I'm running Eft. I can see my school's LEAP network in NetworkManager and use it in XP, but I can't connect to it using the packages posted in this thread. (Though NetworkManager does fine with normal WEP networks. Not sure about WAP)
For some reason, the network in question does not have a shield next to it until after a failed connection attempt.
I'm using the madwifi *ath_pci* modules.

edit: Switched to ndiswrapper, and was able to browse for forty-five glorious seconds before the connection was dropped.

---

### Post by FrankL on 2006-11-25
After some while I tried it again, with the new hints (thanks!), but no luck. Then I looked at what files I have and I saw a libdbus-1.so.3, but no libdbus-1.so.2, as the error was telling me. Next I tried to fool the system by a symbolic link called libdbus-1.so.2 to libdbus-1.so.3 and it fell for it :) So I am now posting this with my wireless working. It gives some warnings in the background, but nothing serious, so I'm happy. Thanks again for all the help!

---

### Post by misha680 on 2006-11-28
I am glad it worked for you.

Misha

> **FrankL said:**
> After some while I tried it again, with the new hints (thanks!), but no luck. Then I looked at what files I have and I saw a libdbus-1.so.3, but no libdbus-1.so.2, as the error was telling me. Next I tried to fool the system by a symbolic link called libdbus-1.so.2 to libdbus-1.so.3 and it fell for it :) So I am now posting this with my wireless working. It gives some warnings in the background, but nothing serious, so I'm happy. Thanks again for all the help!

---

### Post by cpsalvestrini on 2007-01-19
In regards to this latest incarnation of NetworkManager, which I have installed successfully, there are three small details for it to work "automagically" :

1. libpam_keyring needs to be 0.0.8, it can be found in these forums as a.deb package or built from source code. 

2. the file /etc/pam.d/gdm needs to be edited as follows (Assuming you have already installed NetworkManager and that NetworkManager constantly asks you for a keyring password, which has to be **the same** as your login password):

```


#%PAM-1.0
auth	requisite	pam_nologin.so
auth	required	pam_env.so
@include common-auth
@include common-account
session	required	pam_limits.so
@include common-session
@include common-password
## Added so that NetworkManager doesn't keep asking for Keyring password.
## relies on having same password to keyring as login password.
auth optional pam_keyring.so try_first_pass
session optional pam_keyring.so


```

the above modification is needed in order to avoid NetworkManager to constantly ask for the keyring password.

3. If the computer is going to be used across different wireless networks that use encryption, there is a small procedure to follow for NetworkManager to successfully connect  to the network automatically:

1. Connect to the encrypted network.
2. Comment out the last two lines of the code in section 2.
3. reboot your machine.
4. Upon login, the Gnome keyring manager will ask for a keyring password. **Make sure it is set as the same password that you use for your login** or this procedure will not work.
5. Upon successfully connecting, uncomment the last two lines of /etc/pam.d/gdm.
6. Check the Gnome Keyring Manager for a new key for the network you are connecting to. It should be there.
7. Reboot, and enjoy NetworkManager.

As usual, YMMV, read the HOWTOS, FAQ's, manpages, etc., and spread the knowledge. Cheers!

---

### Post by usererror on 2007-02-05
Has this been testing using LEAP with a hidden SSID environment?

---

### Post by misha680 on 2007-02-05
> **usererror said:**
> Has this been testing using LEAP with a hidden SSID environment?

Yes, this is how I use it.

Misha

---

### Post by usererror on 2007-02-05
> **misha680 said:**
> Yes, this is how I use it.

Misha

Fantastic!  I just installed it from the files you posted on page one.  I'll give it a try at work tomorrow.  Thank you!

---

### Post by misha680 on 2007-02-05
> **usererror said:**
> Fantastic!  I just installed it from the files you posted on page one.  I'll give it a try at work tomorrow.  Thank you!

Sure, hope it works for you.

Misha

---

### Post by usererror on 2007-02-06
> **misha680 said:**
> Sure, hope it works for you.

Misha

I'm giving this thread two thumbs up!  WORKS PERFECTLY! (with hidden SSID &  LEAP)  ):P  :guitar:

so when are network manager & friends going to support EAP-FAST ;)

---

### Post by Rogers on 2007-02-21
Ok, Mishna.... AWESOME JOB!  I've compiled your stuff into a kit.....

Just download this file I've attached to the post and run the install.  



tar xvfz  Rogers-Leap-Kit.tar.gz

cd  Rogers-Leap-Kit

./install.sh
[B]


Say yes to all the prompts...... log off.... log on... pick LEAP![/B]:guitar: :guitar:

---

### Post by misha680 on 2007-02-24
Hi, looks nice. Just make sure you mention that it is for edgy and also automake1.9 shouldn't be strictly necessary if you're not compiling networkmanager from source but it's not going to hurt anything.

Misha

> **Rogers said:**
> Ok, Mishna.... AWESOME JOB!  I've compiled your stuff into a kit.....

Just download this file I've attached to the post and run the install.  



tar xvfz  Rogers-Leap-Kit.tar.gz

cd  Rogers-Leap-Kit

./install.sh
[B]


Say yes to all the prompts...... log off.... log on... pick LEAP![/B]:guitar: :guitar:

---

### Post by mephisto1982 on 2007-02-26
i'd like to build some debs myself, but i dont really know how to make debs from scratch. could you post the files you used to build these debs, so i can make new ones with the latest cvs code?

---

### Post by misha680 on 2007-02-28
> **mephisto1982 said:**
> i'd like to build some debs myself, but i dont really know how to make debs from scratch. could you post the files you used to build these debs, so i can make new ones with the latest cvs code?

Hi, I just used the network-manager source debs available in the ubuntu repositories as a base for mine do:

```
apt-get source network-manager
```

somewhere (say in tmp), get the CVS repository into another directory using my instructions in the HOWTO, get rid of the -Werror as it describes, and then just do a:

```
cp -a directory_where_you_got_deb_src/debian directory_where_you_got_cvs/debian
```

Also, there is a file in debian/rules that references the man files for network manager. I think in the repos it was NetworkManager.8 but now it is .1 (or vice versa) so you need to do that, and also comment out the stuff in rules about patches as they will no longer apply. Then dch -vyourversion number and dpkg-buildpackage -rfakeroot -us -uc. Sorry to be brief about this but I am assuming you are familiar with building debs. The source debs I have are 2.5 MBs or so and I don't think this forum will allow me to attach a file that large.

Misha

---

### Post by theonlyrealperson on 2007-03-02
I'm a complete Noob, and although i'm learning, I'm still having a bit of trouble.

I was using Wifi-Radar from the repositories (and still am, until I get Network Manager working), but I need LEAP to access my school's wifi. I'm currently on a unencrypted wifi.

I installed your .debs (THANK YOU) and everything went well. I know have the network manager in the top right corner, and when I click on it I can create a LEAP connection.

However, it doesn't seem to be picking up any wireless signals. It always has a ! mark on it, and when I try to manually connect it logs me off whatever wifi I was on. It never connects to anything, but breaks whatever connection I have. It doesn't even read any networks around me.

Help! Why is it not reading any Wifi signals, and why can't I connect using it? :confused: 

Thanks!

P.S. I'm on Dapper Drake, and I did try uninstalling Wifi-Radar and then using NetworkManager. It still didn't work. (I restarted in-between as well. Old Windoze habit.)

---

### Post by theonlyrealperson on 2007-03-02
I saw the earlier threads on commenting out /etc/network/interfaces, and I did that as well. Still a no-go. It doesn't seem to want to connect to my eth1. 

Could it be that NetworkManager is conflicting with Wifi-Radar or NetworkMonitor? That's what I'm starting to think.

Thanks again!
> 
# This file describes the network interfaces available on your system
# and how to activate them. For more information, see interfaces(5).

# The loopback network interface
auto lo
iface lo inet loopback


---

### Post by theonlyrealperson on 2007-03-02
Ahh, yes. Me again...  Sorry!

I upgraded to Edgy, and I uninstalled/reinstalled the .debs using the Edgy ones. Still the same problem. Any ideas, anyone?

---

### Post by misha680 on 2007-03-04
Sorry to not have replied sooner, I've been pretty busy lately and will be for some time. The big question is do you see your wireless interface in the plain vanilla NetworkManager (without LEAP support) that is available from the repositories. If not, then it is probably a configuration problem with your NetworkManager that may be due, for example, to having WifiRadar also installed. If this is the case, you should be able to use all the help forums and follow instructions you find with regular NetworkManager to resolve this and then just install the LEAP one.

The other possibility is if you _can_ see the wireless interface in NetworkManager that is in the repositories but not with the packages in my HOWTO. In this case I think there are some versioning problems (e.g., if you are using ndiswrapper I have noticed that on some more recent NetworkManager CVS version I think there might be some problems), and I am not sure there is an easy way to resolve the problems other than trying to install a bunch of other things from CVS (but if this is the case I would go with wpasupplicant).

Anyway, sorry I can't help more right now but I have a big deadline I am working on.

Misha

**p.s. reading some of your other posts I noticed in another forum, the key thing I would do is to try the plain vanilla networkmanager from the repository. If this works with your wireless card but my debs don't, I think you might be out of luck with your wireless card for now. If it doesn't work as well, then I think there are a lot more resources for troubleshooting this, and once you troubleshoot it so NetworkManager from the repositories can see your wireless card, you should just be able to install my debs and it should work. **

---

### Post by theonlyrealperson on 2007-03-05
Hmm, ok. I broke a lot of things when I upgraded to Edgy, for some reason - so I went back to Dapper (clean re-install).

I definitely see your point, and when I get some time I'll give it a shot. I'll install the vanilla-NM and try to get that working first (if it doesn't work), then try yours.

Thanks a lot, good luck on your deadline!

---

### Post by kevinsun on 2007-03-15
> **Rogers said:**
> Ok, Mishna.... AWESOME JOB!  I've compiled your stuff into a kit.....

Just download this file I've attached to the post and run the install.  



tar xvfz  Rogers-Leap-Kit.tar.gz

cd  Rogers-Leap-Kit

./install.sh
[B]


Say yes to all the prompts...... log off.... log on... pick LEAP![/B]:guitar: :guitar:

It works!!!!!  There are something unstable but it works!  I'm using IBM X60 and ubutnu edgy.

Thanks a lot,

Kevin.

---

### Post by bezibaerchen on 2007-03-17
Trying to compile as the actual version crashes (seems something to do with dbus).

Running into an error:

```

Requested 'dbus-glib-1 >= 0.72' but version of dbus-glib is 0.71

```

What to do?

---

### Post by misha680 on 2007-03-17
> **bezibaerchen said:**
> Trying to compile as the actual version crashes (seems something to do with dbus).

Running into an error:

```

Requested 'dbus-glib-1 >= 0.72' but version of dbus-glib is 0.71

```

What to do?

Well if you are on Dapper (which it seems like to me) and you need a new version of dbus I would use prevu - it is a cool tool that allows you to pretty easily "backport" newer version of packages from new Ubuntu distributions (edgy). You should just search the forums for prevu (and the wiki too I think there's very easy instructions on there) - I actually had to do this for my mom's computer b/c for some reason (non-LEAP) NetworkManager version that comes with dapper did not work for the newest ndiswrapper version, so I had to prevu NetworkManager, dbus, and I think wpasupplicant from edgy. Hope that helps, let me know if you need more help.

Misha

---

### Post by bezibaerchen on 2007-03-17
I'm on Edgy, not on dapper.

```

dpkg -l | grep libdbus-glib
ii  libdbus-glib-1-2                      0.71-1ubuntu1                        simple interprocess messaging system (GLib-based share
ii  libdbus-glib-1-dev                    0.71-1ubuntu1                        simple interprocess messaging system (GLib interface)

```

---

### Post by misha680 on 2007-03-17
Oh oops. I guess you could prevu from feisty or just use the -D option when getting the code from CVS to get an older version that doesn't require that version of dbus-glib (if you look at the ones I packaged I didn't actually use the latest ones b/c I noticed some of the resume from suspend features are better in the version I had gotten).

Hope that helps.

Misha

> **bezibaerchen said:**
> I'm on Edgy, not on dapper.

```

dpkg -l | grep libdbus-glib
ii  libdbus-glib-1-2                      0.71-1ubuntu1                        simple interprocess messaging system (GLib-based share
ii  libdbus-glib-1-dev                    0.71-1ubuntu1                        simple interprocess messaging system (GLib interface)

```

---

### Post by bezibaerchen on 2007-03-17
Well, as a matter of fact, it isn't CVS anymore, but SVN, so what's the corresponding switch for

```

svn co http://svn.gnome.org/svn/NetworkManager/trunk NetworkManager

```

That's how i checked it out.

---

### Post by misha680 on 2007-03-17
```

svn co -r {2007-02-01} http://svn.gnome.org/svn/NetworkManager/trunk NetworkManager

```

I just used a random date. Hope that helps.

Misha

> **bezibaerchen said:**
> Well, as a matter of fact, it isn't CVS anymore, but SVN, so what's the corresponding switch for

```

svn co http://svn.gnome.org/svn/NetworkManager/trunk NetworkManager

```

That's how i checked it out.

---

### Post by zerocool83 on 2007-03-22
Hi there,
I'm trying to connect my feisty herd 5 with the network of my school, using NetworkManager v 0.70!
The wifi network have an hidden SSID and use the Leap protocol, I follow all your suggestions but when I try to connect always ask me username and password, I insert them but after little time it ask me again! I can't connect!!
Can you help me in some way?!?!?!?

Second answer, I follow the guide of the user cpsalvestrini, but at any login the OS ask me the keyring, why?!?!?!?

:confused: 

I need Your help.

Thx & goodbye

---

### Post by theonlyrealperson on 2007-03-22
Hey, Mishna, I just wanted to let you know that I switched to Edgy (well, actually Linux Mint Bianca) and .7 works great. Thank you very much!!!! :guitar: 

Zerocool83: I noticed that if you wait too long to put in your credentials it doesn't connect. I don't know exactly how long you have, but if you have to type in a long key it may time-out.

---

### Post by navsx on 2007-04-02
I have compiled code from svn and installed it. It all went fine except that it doesn't seem to install nm-applet. So, I installed network-manager-gnome from the feisty repository. However, this version doesn't seem to work with the newer NetworkManager.

What am I missing?

---

### Post by navsx on 2007-04-02
nm-applet shows some warnings and the icon loads, but it doesn't list any interface at all. NM is running fine - I tried running with --no-daemon and I don't see any errors. Just seems to be an incompatibility between nm-applet 0.6.4 and nm 0.7.

---

### Post by navsx on 2007-04-03
Well, nm-applet is not part of the NetworkManager svn repository anymore. It needs to be checked out seperately:

svn co [http://svn.gnome.org/svn/network-manager-applet/trunk](http://svn.gnome.org/svn/network-manager-applet/trunk) network-manager-applet

Unfortunately, the latest code doesn't support wireless yet. While NetworkManager itself seems to work fine, the applet doesn't have code to get wireless working.

I tried a few older revisions (Feb 1st cvs and then the binaries by misha) on feisty, but just couldn't get LEAP working. I guess I'll wait for the cvs code to support wireless.

---

### Post by misha680 on 2007-04-08
> **navsx said:**
> Well, nm-applet is not part of the NetworkManager svn repository anymore. It needs to be checked out seperately:

svn co [http://svn.gnome.org/svn/network-manager-applet/trunk](http://svn.gnome.org/svn/network-manager-applet/trunk) network-manager-applet

Unfortunately, the latest code doesn't support wireless yet. While NetworkManager itself seems to work fine, the applet doesn't have code to get wireless working.

I tried a few older revisions (Feb 1st cvs and then the binaries by misha) on feisty, but just couldn't get LEAP working. I guess I'll wait for the cvs code to support wireless.

I am sorry you are having trouble. I am not switching to Feisty yet but when I do (not 100% sure when that will be as I remember having a fair number of problems switching from Dapper -> Edgy Beta) when I do will figure out how to get LEAP+NM to work and post here.

Misha

---

### Post by rasputin84 on 2007-05-08
there is package for feisty? i can use same tar of edgy?

---

### Post by misha680 on 2007-05-08
> **rasputin84 said:**
> there is package for feisty? i can use same tar of edgy?

I woulds strongly encourage everyone to sign on here:

[https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/108369](https://bugs.launchpad.net/ubuntu/+source/network-manager/+bug/108369)

requesting an update of Feisty's NetworkManager to 0.6.5. 0.6.5
includes LEAP, but packaging it is not straightforward as the applet
is separated from the rest of networkmanager unlike in previous version.

For now you can use wpa_supplicant. Just make a wpa_supplicant.conf file somewhere (I like in /etc and make it read-write for root, no read or write for everyone else since it will contain your network password in cleartext):

```

ap_scan=2

network={
        ssid="your ssid"
        scan_ssid=1
        auth_alg=OPEN
        key_mgmt=IEEE8021X
        eap=LEAP
        identity="username"
        password="pass"
}

```

And then start the connection with the following commands (using your interface name instead of eth0):

```

sudo wpa_supplicant -c/etc/wpa_supplicant.conf -ieth0 -Dwext -B
sudo dhclient eth0

```

Sorry I don't have more at the moment.

Misha

---

### Post by robbie75 on 2007-05-14
Hi Misha,
I was just managing to build Feisty package of nm-0.7 from svn,
everything seems fine except for the fact that I don't know how to get
separeted debs for lib-nm, nm, nm applet... actually all I get is one big
package for nm/libnm-glib/libnm-utils and one for the applet....

Hints?

thank you
Rob

---

### Post by misha680 on 2007-05-14
> **robbie75 said:**
> Hi Misha,
I was just managing to build Feisty package of nm-0.7 from svn,
everything seems fine except for the fact that I don't know how to get
separeted debs for lib-nm, nm, nm applet... actually all I get is one big
package for nm/libnm-glib/libnm-utils and one for the applet....

Hints?

thank you
Rob

hmm... well are you using checkinstall to build these debs or how are you doing it?

Usually for a "proper" deb, you need a debian directory with all sorts of things like a rules file that tells debian (or Ubuntu) how to build the package. An easy way to do this, and how I did this for my CVS packages, is simply to get the source for the existing package:

```
apt-get source network-manager
```

(note this is done _without_ using sudo, as it just retrieves the source code and unpacks it into a directory). Then, you can copy the whole debian directory to the network manager SVN directory, tweak the rules file (mainly in terms of patches applied as most of the patches in the package won't apply to SVN, and some of the file names changed too like some of the manual pages). However, for this new split applet approach that network manager 0.6.5 and svn are using, much more tweaking is needed of the debian/rules files, and although I have figured out a lot of things about these files I have not yet delved in deeply enough to make these significant changes yet (and plus since LEAP support is now in an "official" release 0.6.5 it is only a matter of time before this version becomes the Ubuntu "official" version anyhow, and I would rather have someone who is a MOTU and really knows what they are doing package it anyhow). 

But in any case, once you are done tweaking debian/rules and other files in the debian directory, you can compile with the dpkg-buildpackage utility, usually the following command is used:

```
dpkg-buildpackage -rfakeroot -us -uc
```

Hope that helped and was not things you already knew. Let me know if you have any more questions and I'll try to answer them if I am able to.

Misha

---

### Post by robbie75 on 2007-05-15
Hi misha!
Thank you for you detailed info!

> **misha680 said:**
> hmm... well are you using checkinstall to build these debs or how are you doing it?
I'm using dh_make along with dpkg-buildpackage as explained in the first post of this thread and
in another guide about debian packaging I've found in this forum.

> **misha680 said:**
> 
Usually for a "proper" deb, you need a debian directory with all sorts of things like a rules file that tells debian (or Ubuntu) how to build the package. An easy way to do this, and how I did this for my CVS packages, is simply to get the source for the existing package:

```
apt-get source network-manager
```

great hint!
I'll try that asap ;)

> **misha680 said:**
> 
(note this is done _without_ using sudo, as it just retrieves the source code and unpacks it into a directory). Then, you can copy the whole debian directory to the network manager SVN directory, tweak the rules file (mainly in terms of patches applied as most of the patches in the package won't apply to SVN, and some of the file names changed too like some of the manual pages). However, for this new split applet approach that network manager 0.6.5 and svn are using, much more tweaking is needed of the debian/rules files, and although I have figured out a lot of things about these files I have not yet delved in deeply enough to make these significant changes yet (and plus since LEAP support is now in an "official" release 0.6.5 it is only a matter of time before this version becomes the Ubuntu "official" version anyhow, and I would rather have someone who is a MOTU and really knows what they are doing package it anyhow).  
I'd really like to have the latest nm-0.7 as an official package since in that version seems to be full
support for dial-up connections which I use very often...

> **misha680 said:**
> 
But in any case, once you are done tweaking debian/rules and other files in the debian directory, you can compile with the dpkg-buildpackage utility, usually the following command is used:

```
dpkg-buildpackage -rfakeroot -us -uc
```

Hope that helped and was not things you already knew. Let me know if you have any more questions and I'll try to answer them if I am able to.

Misha

Your hints are very useful to me and now I think it should be easier building the package:
I'll let you know ;)
thank you again!
Rob

---

### Post by misha680 on 2007-05-15
**New packages with all the patches from the 0.6.4 included except 10, 12, 13, 14, and 16, which don't seem to apply cleanly b/c of actualy changes in the underlying code b/w 0.6.4 & 0.6.5. **

Feisty debs.

Ok, here y'all go. These are feisty debs for 0.6.5 that I made after seeing so much demand, works for me with LEAP.

*The debs are in the file nm-0.6.5-feisty.tar.bz2. The rest of the files are source debs for ppl who need to recompile.*

Misha

p.s. You might have to do 
```
sudo dpkg -i *.deb
```
twice as I had to move some stuff from network-manager-gnome in 0.6.4 to network-manager in 0.6.5 (now network-manager-gnome is just the applet).

---

### Post by robbie75 on 2007-05-16
Great job Misha ;-)

Apart from leap, have you tried to connect via dial-up?
With nm-0.6.4 I was able to do that but nm did not inform
dbus about the dial-up connection so several apps stayed
in disconnected mode.

On launchpad, bug 108369 I've found a nm-0.7 package 
[http://librarian.launchpad.net/7652460/nm0.7.0.cvs20061010.tar.bz2](http://librarian.launchpad.net/7652460/nm0.7.0.cvs20061010.tar.bz2)
which seems a little bit more recent than the one  I'm using now; 
I think I'll give it a try and let you know ;-)

Best
Robert

---

### Post by misha680 on 2007-05-16
> **robbie75 said:**
> Great job Misha ;-)

Apart from leap, have you tried to connect via dial-up?
With nm-0.6.4 I was able to do that but nm did not inform
dbus about the dial-up connection so several apps stayed
in disconnected mode.

On launchpad, bug 108369 I've found a nm-0.7 package 
[http://librarian.launchpad.net/7652460/nm0.7.0.cvs20061010.tar.bz2](http://librarian.launchpad.net/7652460/nm0.7.0.cvs20061010.tar.bz2)
which seems a little bit more recent than the one  I'm using now; 
I think I'll give it a try and let you know ;-)

Best
Robert

I think the one on launchpad is my edge debs from the very top of this thread. Don't use dialup so I'm not sure, sorry.

Misha

p.s. Just to save anyone else time, I first tried making debs of the current svn version, but that version of the applet currently doesn't
allow any connections to wireless networks (and prints a FIXME message to let you know that functionality is not implemented yet).

---

### Post by zerocool83 on 2007-05-16
> **misha680 said:**
> Feisty debs.

Ok, here y'all go. These are feisty debs for 0.6.5 that I made after seeing so much demand, seem to work although I still have to test LEAP at work (but it shows up in the Connect to other wireless network menu so I'm pretty confident about it).

*The debs are in the file nm-0.6.5-feisty.tar.bz2. The rest of the files are source debs for ppl who need to recompile.*

Misha

p.s. You might have to do 
```
sudo dpkg -i *.deb
```
twice as I had to move some stuff from network-manager-gnome in 0.6.4 to network-manager in 0.6.5 (now network-manager-gnome is just the applet).

I have installed your debs, but the nm ask me the username and password for the leap connection continuously, it's impossible to connect with this hateful network?
I do not know what to think!!!!

---

### Post by misha680 on 2007-05-16
> **zerocool83 said:**
> I have installed your debs, but the nm ask me the username and password for the leap connection continuously, it's impossible to connect with this hateful network?
I do not know what to think!!!!

I am sorry you are having problems. I just tried my LEAP at work with the nm 0.6.5 feisty debs I made and it worked beautifully (I am on an IEEE 802.1X). 

Perhaps you might try playing with the settings in the LEAP login dialog box, or alternately I would recommend emailing the network-manager developer's forum if you are confident that all nm 0.6.5 debs are installed (do a:
```
dpkg -l | grep libnm
```
and 
```
dpkg -l | grep network-manager
```
and make sure all debs except network-manager-vpnc if you have that installed say 0.6.5; also try rebootting your system first if you have not already) as they may be able to help you troubleshoot your specific LEAP network and how it is different than mine.

Misha

p.s. btw I am connecting the first time by clicking on Connect to other wireless network... and then typing in all the LEAP settings, not by clicking on the ESSID in the dropdown (my network has an invisible ESSID anyhow). Are you doing this too? If not, try doing it that way.

---

### Post by psyke83 on 2007-05-16
Misha,

Thanks a million, your 0.6.5 debs are working excellently so far, I haven't noticed any problems yet. 

zerocool83,

It connects perfectly to my WPA/WPA2 network, and I was able to choose my ESSID via the drop-down menu without being asked for the password (although there may still be a bug connecting to a LEAP protected network).

Try installing libpam-keyring and adding this to the end of /etc/pam.d/gdm:

```
@include common-pamkeyring
```

This prevents Network Manger from asking for your keyring password upon login.

---

### Post by zerocool83 on 2007-05-16
> **misha680 said:**
> 
p.s. btw I am connecting the first time by clicking on Connect to other wireless network... and then typing in all the LEAP settings, not by clicking on the ESSID in the dropdown (my network has an invisible ESSID anyhow). Are you doing this too? If not, try doing it that way.

I have made your same things, the network have an Hidden ESSID, encryption I'm not sure if is wep or 802.1x, authentication Leap, do you think that the problem is the wep encryption mode?

to psyke83:

already made thanks equally

---

### Post by misha680 on 2007-05-16
> **zerocool83 said:**
> I have made your same things, the network have an Hidden ESSID, encryption I'm not sure if is wep or 802.1x, authentication Leap, do you think that the problem is the wep encryption mode?

to psyke83:

already made thanks equally

Hmm... I am not sure. You could also try doing my wpa_supplicant stuff on the previous page and see if that works for you at least. Either way you should email the network manager developer list (ideally after figuring out how to get it to work on wpa_supplicant so they know what specific settings are affecting your network) as it seems they are responsive to this soft of thing (I think given that you can describe technically succinctly what is wrong, i.e., figured out how to connect with wpa_supplicant)

Misha

---

### Post by robbie75 on 2007-05-17
Misha thank you for you effort! ;-)

Now I've had to go back to nm-0.6.4 because it's the only
that works properly after hibernate/suspend (which
I do very often) and it has the ability to show the name
of your peers as in your /etc/network/interfaces.
But, the ugly thing is that nm-0.6.4 doesn't inform
dbus that the state is "connected" while on dial-up
:-(

Your last package for feisty could be the final
solution but I've found that it messes with resolvconf
which I have to use (it overwrites the resolv.conf symlink)

Regards
Rob

---

### Post by theonlyrealperson on 2007-05-17
[QUOTE=robbie75;2673621]Misha thank you for you effort! ;-)
[QUOTE]

I want to second that. Thank you very much - you've made my new Linux experience much much easier on the wireless network end. 

Thanks!

---

### Post by j7899 on 2007-05-17
Does network-manager-vpnc need to be installed along with vpnc?  If so the only version I could find of it is 0.6.4svn2422-0ubuntu2.

Thanks, hopefully this will allow me to access my universities LEAP network.

---

### Post by misha680 on 2007-05-18
> **j7899 said:**
> Does network-manager-vpnc need to be installed along with vpnc?  If so the only version I could find of it is 0.6.4svn2422-0ubuntu2.

Thanks, hopefully this will allow me to access my universities LEAP network.

Glad I could help btw with these packages; hopefully in the next version of Ubuntu 6.5 or later will be official.

I am using that 0.6.4svn network-manager-vpnc package here with the 0.6.5 network-manager and it works great.

Misha

---

### Post by j7899 on 2007-05-21
....Nevermind automagically is working now.

---

### Post by robbie75 on 2007-05-22
Misha, are you using resolvconf on your machine?

I've noticed that your package 0.6.5 for feisty overwrites
the resolvconf symlink....

I was trying to recompile by myself and I'm also trying to
manually apply rejected debian patches but it's a hard work...
Which patches you managed to apply?
I've found that 01-02 and 04 get applied automatically...
I've only applied some stuff from the 05...

---

### Post by misha680 on 2007-05-26
> **robbie75 said:**
> Misha, are you using resolvconf on your machine?

I've noticed that your package 0.6.5 for feisty overwrites
the resolvconf symlink....

I was trying to recompile by myself and I'm also trying to
manually apply rejected debian patches but it's a hard work...
Which patches you managed to apply?
I've found that 01-02 and 04 get applied automatically...
I've only applied some stuff from the 05...

Ok, I uploaded new debs & source debs (replaced them in my old post 
with them) to which I applied all the patches except the ones that look like they are due to actual code changes (and not just filename changes or splits into the applet), so everything except 10, 12, 13, 14, and 16.

As far as I know I am not using resolvconf (dpkg -l | grep resolv doesn't reveal anything; ideally these packages should be built with pbuilder I guess). Do you know which package modifies the resolvconf symlink? If you still have this problem with the new packages I can try compiling with pbuilder next...

Let me know if the new packages work better. Sorry I haven't been so responsive on this thread lately, I've been busy with work/school stuff and also some wine patches I was working on.

Misha

---

### Post by robbie75 on 2007-05-26
> **misha680 said:**
> Ok, I uploaded new debs & source debs (replaced them in my old post 
with them) to which I applied all the patches except the ones that look like they are due to actual code changes (and not just filename changes or splits into the applet), so everything except 10, 12, 13, 14, and 16.

As far as I know I am not using resolvconf (dpkg -l | grep resolv doesn't reveal anything; ideally these packages should be built with pbuilder I guess). Do you know which package modifies the resolvconf symlink? If you still have this problem with the new packages I can try compiling with pbuilder next...

Let me know if the new packages work better. Sorry I haven't been so responsive on this thread lately, I've been busy with work/school stuff and also some wine patches I was working on.

Misha

Hi Misha!
Now I've got almost all patches (manually) applied ;) except for the one about the hostap drivers,
but my package doesn't build because of the applet stuff which isn't anymore included
into the nm daemon sources, and, even if I tried to merge the two tarball (applying debian
patches to the the applet stuff too) obviusly there is the configure file to be updated/merged.

Regarding the resolvconf thing I've found that the debian patch is
applied to the debian backend files (patch 05).

I can send you my patched source if you want to try to build from them.

Ok, now I'm going to try your new debs and let you know soon. ;)
Robbie

---

### Post by misha680 on 2007-05-26
> **robbie75 said:**
> Hi Misha!
Now I've got almost all patches (manually) applied ;) except for the one about the hostap drivers,
but my package doesn't build because of the applet stuff which isn't anymore included
into the nm daemon sources, and, even if I tried to merge the two tarball (applying debian
patches to the the applet stuff too) obviusly there is the configure file to be updated/merged.

Regarding the resolvconf thing I've found that the debian patch is
applied to the debian backend files (patch 05).

I can send you my patched source if you want to try to build from them.

Ok, now I'm going to try your new debs and let you know soon. ;)
Robbie

Yes, pls let me know about the debs. I'm pretty sure all patches don't actually need to be applied, esp look at patch #12 for example. It looks like in 0.6.4 dbus_connection_disconnect was called in two places, and the patch wanted to change it to dbus_connection_unref, but now instead of dbus_connection_disconnect, _close and then _unref are already called in 0.6.5. So in that case, the patch wouldn't make any sense to apply, even manually.

#5 is applied on mine, so let me know if this fixes your problems.

EDIT: Oh, and I did apply all the applet patcbes, check out my source debs if you'd like to see how to do this.

Misha

---

### Post by robbie75 on 2007-05-26
> **misha680 said:**
> Yes, pls let me know about the debs. I'm pretty sure all patches don't actually need to be applied, esp look at patch #12 for example. It looks like in 0.6.4 dbus_connection_disconnect was called in two places, and the patch wanted to change it to dbus_connection_unref, but now instead of dbus_connection_disconnect, _close and then _unref are already called in 0.6.5. So in that case, the patch wouldn't make any sense to apply, even manually.

#5 is applied on mine, so let me know if this fixes your problems.

EDIT: Oh, and I did apply all the applet patcbes, check out my source debs if you'd like to see how to do this.

Misha

Ok, I've tried your latest debs and tey seems stable enough... the only weird thing is that
sometimes nm resumes from suspend/hibernate saying it's connected via ethernet :D and,
unlike the debs from upstream, here nm doesn't auto-connect to a wifi lan if the link becoms
available. But it's ok.

So I could be happy now but one big (to me) problem remains: when I connect to my bluetooth
umts smartphone nm does not inform dbus that a connection is available so many apps stay
in disconnected mode :-|

Now I'm tryng your package posted in the beginning of this thread (0.7 cvs for edgy...) since
on the nm-ml I was told that starting from the 0.7 nm is able to correctly manage modem cnnections.

It could be interesting to apply the latest debian patches to nm-07 sources...

Thank you very much for your time Misha!

---

### Post by misha680 on 2007-05-28
> **robbie75 said:**
> Ok, I've tried your latest debs and tey seems stable enough... the only weird thing is that
sometimes nm resumes from suspend/hibernate saying it's connected via ethernet :D and,
unlike the debs from upstream, here nm doesn't auto-connect to a wifi lan if the link becoms
available. But it's ok.

So I could be happy now but one big (to me) problem remains: when I connect to my bluetooth
umts smartphone nm does not inform dbus that a connection is available so many apps stay
in disconnected mode :-|

Now I'm tryng your package posted in the beginning of this thread (0.7 cvs for edgy...) since
on the nm-ml I was told that starting from the 0.7 nm is able to correctly manage modem cnnections.

It could be interesting to apply the latest debian patches to nm-07 sources...

Thank you very much for your time Misha!

No prob. The sources that were used for the 0.7 debs aren't available anymore (since cvs is no longer being used) and I don't personally have them on my computer anymore. The svn version right now is not functional at all (applet can't connect to wireless networks at the moment).

I'll let you know if I am able to apply any more patches to 0.6.5.

Misha

---

### Post by robbie75 on 2007-05-28
> **misha680 said:**
> No prob. The sources that were used for the 0.7 debs aren't available anymore (since cvs is no longer being used) and I don't personally have them on my computer anymore. The svn version right now is not functional at all (applet can't connect to wireless networks at the moment).

I'll let you know if I am able to apply any more patches to 0.6.5.

Misha

Now I'm using the 0.7 edgy debs and, finally I'm able to get connected by my umts smartphone
and dbus gets informed about that ;) (even if the applet is sayng "no network connection" but
I can live with that)

BTW, the problem about the wired connection or gnome-keyring at startup/resume seems a common
issue for all the non official packages....but I've found that, if I place a restart script for nm into
the acpi scripts directory the problem seems to disappear, so my next move is to find where to place and
when to execute a restart script to solve that strange issue even at startup time.

I'll let you know ;)
Robbie

---

### Post by mystuff on 2007-05-31
I too had problems with 0.6.4 so I used Misha's packages found here:
[http://ubuntuforums.org/showthread.php?p=2663064#post2663064](http://ubuntuforums.org/showthread.php?p=2663064#post2663064)

However installing wasn't completely without problem. First I tried
```
sudo dpkg -i *.deb
```
twice (2) but I kept getting an error regarding libnm-util-dev. I found the solution to be executing:
```
sudo aptitude remove libnm-util0
```

And then executing again:
```
sudo dpkg -i *.deb
```

After a reboot it worked! I was connected through WPA2 Enterprise, EAP-TTLS, AES using "phase2 type: PAP. And I was even using server and client certificates. At least I think I was, because there was one problem, I didn't get a network address and thus couldn't do anything. When I tried to reconnect it stopped working. I can't even connect with the same settings any more.

Any idea what's wrong? This is the information on the network (as far as I know).

ssid: VU-Campusnet
WPA with TKIP or WPA2 with AES
Type: EAP-TTLS
Phase2: PAP
verification: username + password
certificates: CA certificate + personal radius certificate

The access point are all Cisco btw and I'm using Intel 3945 ABG card (using ipw3945 drivers) to connect. WEP and WPA-PSK work without problems.

---

### Post by misha680 on 2007-05-31
Well one thing I've noticed with 0.6.5 vs the cvs 0.7.0 package I used in edgy (very first message in this thread) is that for some reason 0.6.5 doesn't remember my LEAP network is LEAP and thus every time I connect so far I've been using "Connect to other wireless network...", otherwise it detects it & tries to connect but nothing happens. Have you tried doing "Connect to other wireless network..." again?

Misha

> **mystuff said:**
> I too had problems with 0.6.4 so I used Misha's packages found here:
[http://ubuntuforums.org/showthread.php?p=2663064#post2663064](http://ubuntuforums.org/showthread.php?p=2663064#post2663064)

However installing wasn't completely without problem. First I tried
```
sudo dpkg -i *.deb
```
twice (2) but I kept getting an error regarding libnm-util-dev. I found the solution to be executing:
```
sudo aptitude remove libnm-util0
```

And then executing again:
```
sudo dpkg -i *.deb
```

After a reboot it worked! I was connected through WPA2 Enterprise, EAP-TTLS, AES using "phase2 type: PAP. And I was even using server and client certificates. At least I think I was, because there was one problem, I didn't get a network address and thus couldn't do anything. When I tried to reconnect it stopped working. I can't even connect with the same settings any more.

Any idea what's wrong? This is the information on the network (as far as I know).

ssid: VU-Campusnet
WPA with TKIP or WPA2 with AES
Type: EAP-TTLS
Phase2: PAP
verification: username + password
certificates: CA certificate + personal radius certificate

The access point are all Cisco btw and I'm using Intel 3945 ABG card (using ipw3945 drivers) to connect. WEP and WPA-PSK work without problems.

---

### Post by soro2005 on 2007-06-09
Thanks Misha. I just "downgraded" from your edgy 0.7.0 pack to your feisty 0.6.5 debs. The Edgy stuff worked on my Feisty, but it lost the LEAP network all the time, and I had to try typing in the details ten or twenty times before I would get a new connection. The 0.6.5 version has just connected on the first attempt. :-) Hope that wasn't an exceptional case.

In any case: Thanks for sharing this with us!

---

### Post by misha680 on 2007-06-10
> **soro2005 said:**
> Thanks Misha. I just "downgraded" from your edgy 0.7.0 pack to your feisty 0.6.5 debs. The Edgy stuff worked on my Feisty, but it lost the LEAP network all the time, and I had to try typing in the details ten or twenty times before I would get a new connection. The 0.6.5 version has just connected on the first attempt. :-) Hope that wasn't an exceptional case.

In any case: Thanks for sharing this with us!

No prob, glad to help out.

Misha

---

### Post by growse on 2007-07-07
I just want to echo those who are saying that the 0.65 version seems to forget the settings for LEAP networks. I have about 3 different WPA network keys in the keymanager fine, and network manager can connect to them great without prompting, but despite the details for my work's LEAP network being in the keyring, it always just says "Waiting for network key" when I click on the SSID in the menu. The only way to successfully connect is to select "Connect to wireless network.." and fill all the SSID and credentials manually.

I'm sure this didn't used to happen with 0.7 on edgy. Seeing as it successfully puts the credentials in the keyring, it seems to just be a bug in fetching them back out again....

---

### Post by Roo on 2007-07-10
I've been trying to get my Fiesty install to connect to a wireless (LEAP) network - this is using a Thinkpad T43p.

Using the .deb's provided in this thread - I can get a connection - it does work.  However, once connected properly - attempting to reboot (or it seems anything else that causes a loss of connection) results in the following cycle being entered by the NetworkManager.

NetworkManager: <info>  Activation (eth1) New wireless user key for network 'XXX' received.
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) starting...
NetworkManager: <info>  Activation (eth1/wireless): access point 'XXX' is encrypted, but NO valid key exists.  New key needed.
NetworkManager: <info>  Activation (eth1) New wireless user key requested for network 'XXX'.
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) complete.
NetworkManager: <info>  Activation (eth1) New wireless user key for network 'XXX' received.
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) started...
NetworkManager: <info>  Activation (eth1) Stage 2 of 5 (Device Configure) scheduled...
NetworkManager: <info>  Activation (eth1) Stage 1 of 5 (Device Prepare) complete.
[...repeated many, many times..]

So to be clear.  If I use "Connect to Other Wireless Network.." and fill in my leap details - I will connect.  However,  if I do anything that causes a loss of connection - I end up back in the same bad loop shown above.

---

### Post by Roo on 2007-07-10
So ignoring the NetworkManager and using wpa_supplicant directly I can get things to work.  This really isn't news since I was able to get the NetworkManager to work if I was willing to configure a new wireless network each time.

I used the instructions in post: [http://ubuntuforums.org/showthread.php?p=1701331](http://ubuntuforums.org/showthread.php?p=1701331)

This allows me to use an effectively "stock" Fiesty with some scripts to get wifi LEAP working.

Roo

---

### Post by misha680 on 2007-07-10
> **Roo said:**
> So ignoring the NetworkManager and using wpa_supplicant directly I can get things to work.  This really isn't news since I was able to get the NetworkManager to work if I was willing to configure a new wireless network each time.

I used the instructions in post: [http://ubuntuforums.org/showthread.php?p=1701331](http://ubuntuforums.org/showthread.php?p=1701331)

This allows me to use an effectively "stock" Fiesty with some scripts to get wifi LEAP working.

Roo

For a very simple solution with wpa_supplicant see my post here:

[http://ubuntuforums.org/showpost.php?p=2617985&postcount=84](http://ubuntuforums.org/showpost.php?p=2617985&postcount=84)

Misha

---

### Post by mattengstrom on 2007-07-12
Thanks for putting this together.  I've just installed Feisty on an IBM t60p with an atheros wireless adapter,  I followed the guide and installed the NetworkManager 0.6.5 packages, but still can't get connected to LEAP with NetworkManager.  The first NetworkManager light turns green, which I understand means that I'm authenticated, but the second one never lights up indicating that I've gotten an address.

Using wpa_supplicant, per the instructions in this forum, works fine.

Any suggestions?  Are there logs from NetworkManager someplace on the machine, or do I need to activate some debug level?

---

### Post by misha680 on 2007-07-12
> **mattengstrom said:**
> Thanks for putting this together.  I've just installed Feisty on an IBM t60p with an atheros wireless adapter,  I followed the guide and installed the NetworkManager 0.6.5 packages, but still can't get connected to LEAP with NetworkManager.  The first NetworkManager light turns green, which I understand means that I'm authenticated, but the second one never lights up indicating that I've gotten an address.

Using wpa_supplicant, per the instructions in this forum, works fine.

Any suggestions?  Are there logs from NetworkManager someplace on the machine, or do I need to activate some debug level?

No prob. For logs I usually kill NetworkManager and then run:

```

sudo NetworkManager --no-daemon

```

which will print everything out to the command line, or you could redirect to a file:

```

sudo NetworkManager --no-daemon > filename 2>&1

```

Not sure the 2>&1 is needed but it will redirect stderr into the file too (normally it is
just stdout that gets redirected).

Misha

---

### Post by mattengstrom on 2007-07-13
OK, I did that and captured everything to a log file, which is attached.  To me, it looks like it's timing out on the DHCP request.  Do you agree?  Is there a way to increase the timeout parameter?  Or is something else going on?

---

### Post by chadjohnson on 2008-02-08
FYI for anyone out there:

To authenticate against LEAP via wpa_supplicant using hte madwifi drivers...

edit /etc/wpa_supplicant/wpa_supplicant.conf as follows:
```

network={
        scan_ssid=1
        ssid="MYNETWORK"
        key_mgmt=WPA-EAP
        eap=LEAP
        identity="MYIDENTITY"
        password="MYPASSWORD"
}

```

run the following commands (replacing ath0 with your wireless interface):
```

wpa_supplicant -D madwifi -c /etc/wpa_supplicant/wpa_supplicant.conf -i ath0
dhclient ath0

```

---

### Post by joeschmit123 on 2008-05-05
steps provided in the original start of the thread don't work.  As soon as you remove Networkmanager 'sudo apt-get remove network-manager', your network connection is basically dead and you get an error running 'sudo apt-get .... ' commands from there on.   Thanks for messing up my machine.

---

### Post by misha680 on 2008-05-05
> **joeschmit123 said:**
> steps provided in the original start of the thread don't work.  As soon as you remove Networkmanager 'sudo apt-get remove network-manager', your network connection is basically dead and you get an error running 'sudo apt-get .... ' commands from there on.   Thanks for messing up my machine.

Sorry this howto is actually quite old (you can see my last edit to my first post was in May of 07 a year ago, although now I just changed it to say it was outdated). In any case NM 0.6.5 (included with gutsy) and later have LEAP support by default.

You should be able to reinstall from your CD if you have it (let me know if you need more instructions I believe when you install from CD it actually is a package repository and plus if you insert an Ubuntu CD at least on my computer I get asked whether to use it as a repository, but if this doesn't work let me know and I can lead you through more complex step by step instructions).

Sorry
Misha

---

