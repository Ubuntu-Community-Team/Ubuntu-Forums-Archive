---
title: "Why isn't my CUPS spooler starting?"
date: 2013-09-13
forum: New to Ubuntu
---

### Post by kristen2 on 2013-09-13
Will someone help me with this please? I'm trying to install CUPS so I can connect my computer to a printer, but it isn't happening... I've installed CUPS, but when I try to connect I get this error, in my printing settings :


    There was an error during the CUPS operation: 'failed to connect to server'.


The troubleshoot says:


    The CUPS print spooler does not appear to be running. To correct this, choose System->Administration->Services from the main menu and look for the 'cups' service


I have "System" in my menu but I do not have an "Administration" menu; therefore, I don't have the Services menu either, so I can't do anything that way. And... I get this error when I use terminal


    sudo /etc/init.d/cups start
    [sudo] password for kristenxoxox: 
    Rather than invoking init scripts through /etc/init.d, use the service(8)
    utility, e.g. service cups start
    initctl: Unknown job: cups


    Since the script you are attempting to invoke has been converted to an
    Upstart job, you may also use the start(8) utility, e.g. start cups
    (precise)kristenxoxox@localhost:~$ sudo start cups
    start: Unknown job: cups
    (precise)kristenxoxox@localhost:~$ start cups
    bash: start: command not found
    (precise)kristenxoxox@localhost:~$ service cups start
    /usr/bin/service: 123: exec: start: not found


Help??

---

### Post by kristen2 on 2013-09-13
Someone please tell me why I can't connect:?:

---

### Post by kristen2 on 2013-09-13
I found this: 
[COLOR=#333333][FONT=Helvetica]I'm[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica] using lxde (raring) on a Samsung series 3, but the process should be the same.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]1. Install the needed packages: cups, system-config-printer-gnome, and hplip (if it's an HP printer).[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]2. init scripts don't work right in crouton so we need to start cups somehow. One way is to edit /etc/rc.local[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica] and add:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]/usr/sbi[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]n/cupsd[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]3. Add your username to the lpadmin group:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]sudo adduser [/FONT][/COLOR]*username*[COLOR=#333333][FONT=Helvetica] lpadmin[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]4. Finally, log out and back in for these settings to take effect.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]You should now be able to go into Preferences / Printers and set up your network printer. I had to point it at the ip address of the printer host (I haven't gotten smb browsing to work yet but that's another issue), but from there everything just worked.

from [/FONT][/COLOR][https://github.com/dnschneid/crouton/issues/143](https://github.com/dnschneid/crouton/issues/143)

How do I do #2: "edit" and "add"

Please tell me! Thank you

---

### Post by kristen2 on 2013-09-13
Is anyone seeing this...?

---

### Post by tgalati4 on 2013-09-13
Have you performed all of your updates?  There is a bug that causes cups to shut down if it doesn't see avahi (Bonjour, publishing service).  Make sure either avahi is installed and running, or perform the updates and it should fix it for you.

---

### Post by kristen2 on 2013-09-13
Thank you.

I'm wondering if it's a problem that I'm trying to install/use CUPS in Crouton via Chromebook? 

I did "sudo apt-get update" but it didn't solve anything. I don't know what avahi is... you think I need that installed?

What about this, "[I][COLOR=#333333][FONT=Helvetica]2. init scripts don't work right in crouton so we need to start cups somehow. One way is to edit /etc/rc.local[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica] and add:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]/usr/sbi[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]n/cupsd[/FONT][/COLOR][/I]"
That looks promising... I just don't know how to "edit" /etc/rc.local and "add" /usr/sbin/cupsd

---

### Post by bweinel on 2013-09-13
> **kristen2 said:**
> I found this: 
[COLOR=#333333][FONT=Helvetica]I'm[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica] using lxde (raring) on a Samsung series 3, but the process should be the same.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]1. Install the needed packages: cups, system-config-printer-gnome, and hplip (if it's an HP printer).[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]2. init scripts don't work right in crouton so we need to start cups somehow. One way is to edit /etc/rc.local[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica] and add:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]/usr/sbi[/FONT][/COLOR][COLOR=#333333][FONT=Helvetica]n/cupsd[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]3. Add your username to the lpadmin group:[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]sudo adduser [/FONT][/COLOR]*username*[COLOR=#333333][FONT=Helvetica] lpadmin[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]4. Finally, log out and back in for these settings to take effect.[/FONT][/COLOR]
[COLOR=#333333][FONT=Helvetica]You should now be able to go into Preferences / Printers and set up your network printer. I had to point it at the ip address of the printer host (I haven't gotten smb browsing to work yet but that's another issue), but from there everything just worked.

from [/FONT][/COLOR][https://github.com/dnschneid/crouton/issues/143](https://github.com/dnschneid/crouton/issues/143)

How do I do #2: "edit" and "add"


rc.local is just a txt file. So you need to open a terminal window and edit the file '/etc/rc.local' with a text editor. 

I like to use the 'nano' editor from the terminal. So to edit with nano, start it like this:

```

bweinel@excalibur:~$ sudo nano /etc/rc.local

```

(use 'sudo' to start nano as you need to edit the file as 'root'.)

Once in the nano editor, you will see a number of lines displayed beginning with '#' marks. These are comment lines... Just arrow down until you get to the blank line immediatly above the 'exit 0' line. On that line type ' /usr/sbin/cupsd' (without the quotes) and press enter. Then press control-O to save your work and then control-X to exit back to the command prompt. This will add the /usr/sbin/cupsd start command to your rc.local script. Once you do that you can make sure its there by listing the file like this:

```

bweinel@excalibur:~$ cat /etc/rc.local
#!/bin/sh -e
#
# rc.local
#
# This script is executed at the end of each multiuser runlevel.
# Make sure that the script will "exit 0" on success or any other
# value on error.
#
# In order to enable or disable this script just change the execution
# bits.
#
# By default this script does nothing.
/usr/sbin/cupsd
exit 0

```

Now... before you do all of this editing, you might want to verify first that cupsd isn't running on your system already (or crashing when starting.) 
Check it like this from a terminal window:

```

bweinel@excalibur:~$ sudo ps -ae | grep cups
  716 ?        00:00:00 cupsd
  879 ?        00:00:00 cups-browsed

```
 
Note in the example above, both cupsd and cups-browsed are running on my system. If your search returns with nothing.. its not running. 

You can also search /var/log/dmesg to find out if cupsd is starting and if not, why not:

```

bweinel@excalibur:~$ sudo cat /var/log/dmesg | grep 'cups'
[   12.424104] init: avahi-cups-reload main process (655) terminated with status 1
[   12.707337] type=1400 audit(1379079003.165:8): apparmor="STATUS" operation="profile_load" name="/usr/lib/cups/backend/cups-pdf" pid=704 comm="apparmor_parser"
[   12.727573] type=1400 audit(1379079003.185:9): apparmor="STATUS" operation="profile_load" name="/usr/sbin/cupsd" pid=704 comm="apparmor_parser"
```

Hopefully this helps you determine if your cupsd is running or not. 

cheers,
bill

---

### Post by kristen2 on 2013-09-13
Thanks Bill. I was able to edit the rc.local file in nano and added [COLOR=#333333]*[FONT=Helvetica]/usr/sbi[/FONT]*[/COLOR][COLOR=#333333]*[FONT=Helvetica]n/cupsd[/FONT]*[/COLOR] where you said to, but CUPS is still not starting.

Before I edited the file I did look to see if CUPS was running, which it wasn't.

[B](precise)kristenxoxox@localhost:~$ sudo ps -ae | grep cups
(precise)kristenxoxox@localhost:~$ sudo cat /var/log/dmesg | grep 'cups'
(precise)kristenxoxox@localhost:~$ [/B]

As you can see, there is no output either time.

I tried starting CUPS in terminal and still have the same message.

[B](precise)kristenxoxox@localhost:~$ sudo /etc/init.d/cups start
 Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service cups start
initctl: Unknown job: cups


Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start cups
[/B]

Soooooo... I haven't an idea how to solve this :/

---

### Post by steeldriver on 2013-09-13
I don't know anything about crouton, but if /etc/init.d thinks cups should be started by upstart, but initctl says it's unknown, then that suggests it wasn't installed correctly - is there a /etc/init/cups.conf file? do you have a /var/log/cups/error_log file and if so does it record any startup attempts? What other cups packages are installed? You can use

```
dpkg -l | grep cups
```

 to list them

---

### Post by tgalati4 on 2013-09-14
Go through /var/log/cups and look for errors.  I'm guessing it's the same avahi issue that others have experienced.  You need to install avahi and start it, then cups should load properly.  I don't know anything about Crouton or how it is packaged for Chromebook.

tgalati4@Mint14-Extensa ~ $ apt-cache policy avahi-daemon
avahi-daemon:
  Installed: 0.6.31-1ubuntu2
  Candidate: 0.6.31-1ubuntu2
  Version table:
 *** 0.6.31-1ubuntu2 0
        500 [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) quantal/main amd64 Packages
        100 /var/lib/dpkg/status
tgalati4@Mint14-Extensa ~ $ ps -ef | grep avahi
avahi      538     1  0 Sep09 ?        00:00:00 avahi-daemon: running [Mint14-Extensa.local]
avahi      543   538  0 Sep09 ?        00:00:00 avahi-daemon: chroot helper
tgalati4  7475  3819  0 21:33 pts/0    00:00:00 grep --colour=auto avahi

---

### Post by kristen2 on 2013-09-14
Hi steeldriver,

Thanks for your answer. You're right, it must have been installed incorrectly. I am clueeelesss. I've looked through my files and have found that 1) yes, there is a /etc/init/cups.conf file and 2) There is not a /var/log/cups/error_log file. I have a /var/log/cups directory but it's empty.

I ran the dpkg -l | grep cups command, so here's the list of cups packages that are installed:
dpkg -l | grep cups
**ii  cups                                 1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - server**
**ii  cups-client                          1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - client programs (SysV)**
**ii  cups-common                          1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - common files**
**ii  cups-filters                         1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters**
**ii  cups-ppdc                            1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - PPD manipulation utilities**
**ii  ghostscript-cups                     9.05~dfsg-0ubuntu4.2                    interpreter for the PostScript language and for PDF - CUPS filters**
**ii  libcups2                             1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - Core library**
**ii  libcupscgi1                          1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - CGI library**
**ii  libcupsfilters1                      1.0.18-0ubuntu0.1                       OpenPrinting CUPS Filters - Shared library**
**ii  libcupsimage2                        1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - Raster image library**
**ii  libcupsmime1                         1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - MIME library**
**ii  libcupsppdc1                         1.5.3-0ubuntu8                          Common UNIX Printing System(tm) - PPD manipulation library**
**ii  python-cups                          1.9.61-0ubuntu2                         Python bindings for CUPS**
**ii  python-cupshelpers                   1.3.8+20120201-0ubuntu8.1               Python modules for printer configuration with CUPS**

I hope that from this information you can kind of see what's going on, what needs to be done, because I don't know anything. 

Please please continue to help me. Thank you.

---

### Post by kristen2 on 2013-09-14
[COLOR=#000000]Hi tgalati4, 

Thanks for your answer also. All I understand from what you're telling me is that I need to install avahi. I don't understand the [/COLOR][COLOR=#000000]apt-cache policy avahi-daemon [/COLOR][COLOR=#000000]command you pasted or anything else following it. Sorry :/ I know so little about what I'm doing

Oh, and also there is no error log. That's weird, right?[/COLOR]

---

### Post by kristen2 on 2013-09-14
bump..

---

### Post by kristen2 on 2013-09-15
hello.....

---

### Post by bweinel on 2013-09-16
Hi Kirsten2,

Check to see that avahi isn't already installed like this:

```

bweinel@excalibur:~$ ps -ae | grep avahi-daemon
  723 ?        00:00:00 avahi-daemon
  725 ?        00:00:00 avahi-daemon

```

As you can see on my system it is installed. If it returns nothing, then install it:

```

bweinel@excalibur:~$ sudo apt-get install avahi-daemon

```

Then try to start up cups and verify its running:

```

bweinel@excalibur:~$ sudo start cups
cups start/running, process 5177
bweinel@excalibur:~$ ps -ae | grep cups
  864 ?        00:00:00 cups-browsed
 5177 ?        00:00:00 cupsd

```

I'm not a cups expert.. but my system shows that cups also requires ghostscript, colord, and a few other things. So if you don't have those installed you'll probably need them as well. You should be able to see the status of the installation in dpkg status listing after you install. Here's a listing of my systems dpkg status and all the cups related stuff. As you can see below (and also if you examine the depends in the listing) there are some additional packages recommended (and required) as listed below. (You can put a larger number for the -A command to seem more lines in each section if needed) :

```

bweinel@excalibur:~$ cat /var/lib/dpkg/status | grep -A 20 'Package: cups'
Package: cups-ppdc
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 228
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Depends: libc6 (>= 2.4), libcups2 (>= 1.6.2), libcupsppdc1 (>= 1.4.0), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), cups-common
Description: Common UNIX Printing System(tm) - PPD manipulation utilities
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides utilities to generate and manipulate PPD files.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.cups.org

--
Package: cups-client
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 578
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Depends: libc6 (>= 2.14), libcups2 (= 1.6.2-1ubuntu5), libcupsimage2 (>= 1.4.0), cups-common (>= 1.6.2), adduser
Recommends: smbclient
Suggests: cups, xpp, cups-bsd
Conflicts: lprng
Description: Common UNIX Printing System(tm) - client programs (SysV)
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the System V style print client programs.
--
Package: cups-common
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 1123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Description: Common UNIX Printing System(tm) - common files
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides common files for CUPS server and client packages.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.cups.org

Package: kcalc
--
Package: cups-filters
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 901
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.0.34-0ubuntu1.1
Replaces: cups (<< 1.5.0-16), cups-common (<< 1.5.0-16), ghostscript-cups (<< 9.02~)
Depends: libc6 (>= 2.15), libcups2 (>= 1.4.0), libcupsfilters1 (>= 1.0~b1), libcupsimage2 (>= 1.4.0), libfontconfig1 (>= 2.9.0), libfontembed1 (>= 1.0.31), libgcc1 (>= 1:4.1.1), libijs-0.35 (>= 0.35), liblcms2-2 (>= 2.2+git20110628), libpoppler28 (>= 0.20.5), libqpdf10 (>> 4.0.0~), libstdc++6 (>= 4.1.1), bc, ghostscript (>= 9.02~), fonts-freefont-ttf | fonts-liberation | ttf-dejavu
Recommends: colord, foomatic-filters (>= 4.0), ghostscript-cups (>= 9.02~)
Suggests: foomatic-db-compressed-ppds | foomatic-db
Breaks: cups (<< 1.5.0-16), cups-common (<< 1.5.0-16), ghostscript-cups (<< 9.02~)
Conffiles:
 /etc/fonts/conf.d/99pdftoopvp.conf a5221cfad70a981c80864229ef56586d
Description: OpenPrinting CUPS Filters
 This package provides additional CUPS filters which are not provided
 by the CUPS project itself. This includes filters for a PDF based
 printing workflow.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.openprinting.org/
--
Package: cups-daemon
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 929
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Replaces: cups (<< 1.6.1-1~)
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.15), libcups2 (= 1.6.2-1ubuntu5), libcupsmime1 (>= 1.5.0), libdbus-1-3 (>= 1.0.2), libgnutls26 (>= 2.12.17-0), libgssapi-krb5-2 (>= 1.10+dfsg~), libpam0g (>= 0.99.7.1), libpaper1, upstart-job, procps, lsb-base (>= 3), ssl-cert (>= 1.0.11), adduser, bc
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: avahi-daemon, colord, cups-browsed
Suggests: cups, cups-bsd, cups-common (>= 1.6.2), cups-client (>= 1.6.2-1ubuntu5), cups-ppdc, cups-filters, poppler-utils (>= 0.12), ghostscript (>= 9.02~), ghostscript-cups (>= 9.02~), foomatic-filters (>= 4.0), foomatic-db-compressed-ppds | foomatic-db, printer-driver-gutenprint, printer-driver-hpcups, hplip, cups-pdf, udev, smbclient
Breaks: cups (<< 1.6.1-1~)
Conffiles:
 /etc/apparmor.d/usr.sbin.cupsd c1309855cf3aeaf16daf485b28fc94a8
 /etc/ufw/applications.d/cups 29e98a6d850da251e180c3d68dec2bd3
 /etc/pam.d/cups-daemon ff2488324854f7b1e892bb0df062d5f0
 /etc/default/cups 2b436fbb1a32b82b6aba45a76a1d7e40
--
Package: cups-bsd
Status: install ok installed
Priority: extra
Section: net
Installed-Size: 120
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Replaces: lpr
Provides: lpr
Depends: libc6 (>= 2.4), libcups2 (>= 1.6.2), debconf (>= 0.5) | debconf-2.0, cups-client (= 1.6.2-1ubuntu5), update-inetd, cups-common
Suggests: cups
Conflicts: lpr, lprng
Description: Common UNIX Printing System(tm) - BSD commands
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpr, lpd and the like.  It supports the
 Internet Printing Protocol (IPP), and has its own filtering driver
 model for handling various document types.
 .
--
Package: cups-browsed
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 127
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: cups-filters
Version: 1.0.34-0ubuntu1.1
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.4), libcups2 (>= 1.6.0), libglib2.0-0 (>= 2.14.0), upstart-job, cups
Conffiles:
 /etc/init/cups-browsed.conf f5e832d72b464bd17247f30c728fa3fb
 /etc/cups/cups-browsed.conf f4b89864b48e4f2f3f62667ca5145122
Description: OpenPrinting CUPS Filters - cups-browsed
 This package provides cups-browsed, a daemon which browses the Bonjour
 broadcasts of shared remote CUPS printers and makes the printers
 available locally, replacing the CUPS broadcasting/browsing which was
 dropped in CUPS 1.6.x. This way the old behavior of having the remote
 printers available automatically is now re-implemented with Bonjour.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.openprinting.org/
--
Package: cups
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 3331
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 1.6.2-1ubuntu5
Replaces: ghostscript-cups (<< 9.02~)
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.16), libcups2 (= 1.6.2-1ubuntu5), libcupscgi1 (>= 1.4.2), libcupsimage2 (>= 1.4.0), libcupsmime1 (>= 1.4.0), libcupsppdc1 (>= 1.4.0), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libusb-1.0-0 (>= 2:1.0.8), debconf (>= 1.2.9) | debconf-2.0, libc-bin (>= 2.13), cups-daemon (>= 1.6.2-1ubuntu5), poppler-utils (>= 0.12), procps, ghostscript (>= 9.02~), lsb-base (>= 3), cups-common (>= 1.6.2), cups-client (>= 1.6.2-1ubuntu5), cups-ppdc, cups-filters (>= 1.0.24-3~), libp11-kit-gnome-keyring
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: avahi-daemon, colord, foomatic-filters (>= 4.0), printer-driver-gutenprint, ghostscript-cups (>= 9.02~)
Suggests: cups-bsd, foomatic-db-compressed-ppds | foomatic-db, printer-driver-hpcups, hplip, cups-pdf, udev, smbclient
Breaks: foomatic-filters (<< 4.0), ghostscript-cups (<< 9.02~)
Conffiles:
 /etc/cups/snmp.conf 55baa060a50f48f9dbb99c6eb60dc04c
 /etc/init/cups.conf 43d2d4234cff969f03c48484e985deed obsolete
 /etc/cups/cups-files.conf 2d5c3341837e2dabeaa16cf90582fd6c obsolete
 /etc/cups/cupsd.conf 330ccbff0f945529855a5f274ee3579b obsolete
 /etc/cups/cupsd.conf.default bedd8fafef3a16ccd1f52d9b0d01772c obsolete
bweinel@excalibur:/var/lib/dpkg$ clear
bweinel@excalibur:/var/lib/dpkg$ cat status | grep -A 20 'Package: cups'
Package: cups-ppdc
Status: install ok installed
Priority: optional
Section: utils
Installed-Size: 228
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Depends: libc6 (>= 2.4), libcups2 (>= 1.6.2), libcupsppdc1 (>= 1.4.0), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), cups-common
Description: Common UNIX Printing System(tm) - PPD manipulation utilities
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides utilities to generate and manipulate PPD files.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.cups.org

--
Package: cups-client
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 578
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Depends: libc6 (>= 2.14), libcups2 (= 1.6.2-1ubuntu5), libcupsimage2 (>= 1.4.0), cups-common (>= 1.6.2), adduser
Recommends: smbclient
Suggests: cups, xpp, cups-bsd
Conflicts: lprng
Description: Common UNIX Printing System(tm) - client programs (SysV)
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides the System V style print client programs.
--
Package: cups-common
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 1123
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Description: Common UNIX Printing System(tm) - common files
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpd and the like.  It supports the Internet
 Printing Protocol (IPP), and has its own filtering driver model for
 handling various document types.
 .
 This package provides common files for CUPS server and client packages.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.cups.org

Package: kcalc
--
Package: cups-filters
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 901
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Version: 1.0.34-0ubuntu1.1
Replaces: cups (<< 1.5.0-16), cups-common (<< 1.5.0-16), ghostscript-cups (<< 9.02~)
Depends: libc6 (>= 2.15), libcups2 (>= 1.4.0), libcupsfilters1 (>= 1.0~b1), libcupsimage2 (>= 1.4.0), libfontconfig1 (>= 2.9.0), libfontembed1 (>= 1.0.31), libgcc1 (>= 1:4.1.1), libijs-0.35 (>= 0.35), liblcms2-2 (>= 2.2+git20110628), libpoppler28 (>= 0.20.5), libqpdf10 (>> 4.0.0~), libstdc++6 (>= 4.1.1), bc, ghostscript (>= 9.02~), fonts-freefont-ttf | fonts-liberation | ttf-dejavu
Recommends: colord, foomatic-filters (>= 4.0), ghostscript-cups (>= 9.02~)
Suggests: foomatic-db-compressed-ppds | foomatic-db
Breaks: cups (<< 1.5.0-16), cups-common (<< 1.5.0-16), ghostscript-cups (<< 9.02~)
Conffiles:
 /etc/fonts/conf.d/99pdftoopvp.conf a5221cfad70a981c80864229ef56586d
Description: OpenPrinting CUPS Filters
 This package provides additional CUPS filters which are not provided
 by the CUPS project itself. This includes filters for a PDF based
 printing workflow.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.openprinting.org/
--
Package: cups-daemon
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 929
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Replaces: cups (<< 1.6.1-1~)
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.15), libcups2 (= 1.6.2-1ubuntu5), libcupsmime1 (>= 1.5.0), libdbus-1-3 (>= 1.0.2), libgnutls26 (>= 2.12.17-0), libgssapi-krb5-2 (>= 1.10+dfsg~), libpam0g (>= 0.99.7.1), libpaper1, upstart-job, procps, lsb-base (>= 3), ssl-cert (>= 1.0.11), adduser, bc
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: avahi-daemon, colord, cups-browsed
Suggests: cups, cups-bsd, cups-common (>= 1.6.2), cups-client (>= 1.6.2-1ubuntu5), cups-ppdc, cups-filters, poppler-utils (>= 0.12), ghostscript (>= 9.02~), ghostscript-cups (>= 9.02~), foomatic-filters (>= 4.0), foomatic-db-compressed-ppds | foomatic-db, printer-driver-gutenprint, printer-driver-hpcups, hplip, cups-pdf, udev, smbclient
Breaks: cups (<< 1.6.1-1~)
Conffiles:
 /etc/apparmor.d/usr.sbin.cupsd c1309855cf3aeaf16daf485b28fc94a8
 /etc/ufw/applications.d/cups 29e98a6d850da251e180c3d68dec2bd3
 /etc/pam.d/cups-daemon ff2488324854f7b1e892bb0df062d5f0
 /etc/default/cups 2b436fbb1a32b82b6aba45a76a1d7e40
--
Package: cups-bsd
Status: install ok installed
Priority: extra
Section: net
Installed-Size: 120
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Source: cups
Version: 1.6.2-1ubuntu5
Replaces: lpr
Provides: lpr
Depends: libc6 (>= 2.4), libcups2 (>= 1.6.2), debconf (>= 0.5) | debconf-2.0, cups-client (= 1.6.2-1ubuntu5), update-inetd, cups-common
Suggests: cups
Conflicts: lpr, lprng
Description: Common UNIX Printing System(tm) - BSD commands
 The Common UNIX Printing System (or CUPS(tm)) is a printing system and
 general replacement for lpr, lpd and the like.  It supports the
 Internet Printing Protocol (IPP), and has its own filtering driver
 model for handling various document types.
 .
--
Package: cups-browsed
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 127
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Source: cups-filters
Version: 1.0.34-0ubuntu1.1
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libavahi-glib1 (>= 0.6.16), libc6 (>= 2.4), libcups2 (>= 1.6.0), libglib2.0-0 (>= 2.14.0), upstart-job, cups
Conffiles:
 /etc/init/cups-browsed.conf f5e832d72b464bd17247f30c728fa3fb
 /etc/cups/cups-browsed.conf f4b89864b48e4f2f3f62667ca5145122
Description: OpenPrinting CUPS Filters - cups-browsed
 This package provides cups-browsed, a daemon which browses the Bonjour
 broadcasts of shared remote CUPS printers and makes the printers
 available locally, replacing the CUPS broadcasting/browsing which was
 dropped in CUPS 1.6.x. This way the old behavior of having the remote
 printers available automatically is now re-implemented with Bonjour.
Original-Maintainer: Debian Printing Team <debian-printing@lists.debian.org>
Homepage: http://www.openprinting.org/
--
Package: cups
Status: install ok installed
Priority: optional
Section: net
Installed-Size: 3331
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: amd64
Multi-Arch: foreign
Version: 1.6.2-1ubuntu5
Replaces: ghostscript-cups (<< 9.02~)
Depends: libavahi-client3 (>= 0.6.16), libavahi-common3 (>= 0.6.16), libc6 (>= 2.16), libcups2 (= 1.6.2-1ubuntu5), libcupscgi1 (>= 1.4.2), libcupsimage2 (>= 1.4.0), libcupsmime1 (>= 1.4.0), libcupsppdc1 (>= 1.4.0), libgcc1 (>= 1:4.1.1), libstdc++6 (>= 4.1.1), libusb-1.0-0 (>= 2:1.0.8), debconf (>= 1.2.9) | debconf-2.0, libc-bin (>= 2.13), cups-daemon (>= 1.6.2-1ubuntu5), poppler-utils (>= 0.12), procps, ghostscript (>= 9.02~), lsb-base (>= 3), cups-common (>= 1.6.2), cups-client (>= 1.6.2-1ubuntu5), cups-ppdc, cups-filters (>= 1.0.24-3~), libp11-kit-gnome-keyring
Pre-Depends: dpkg (>= 1.15.7.2)
Recommends: avahi-daemon, colord, foomatic-filters (>= 4.0), printer-driver-gutenprint, ghostscript-cups (>= 9.02~)
Suggests: cups-bsd, foomatic-db-compressed-ppds | foomatic-db, printer-driver-hpcups, hplip, cups-pdf, udev, smbclient
Breaks: foomatic-filters (<< 4.0), ghostscript-cups (<< 9.02~)
Conffiles:
 /etc/cups/snmp.conf 55baa060a50f48f9dbb99c6eb60dc04c
 /etc/init/cups.conf 43d2d4234cff969f03c48484e985deed obsolete
 /etc/cups/cups-files.conf 2d5c3341837e2dabeaa16cf90582fd6c obsolete
 /etc/cups/cupsd.conf 330ccbff0f945529855a5f274ee3579b obsolete
 /etc/cups/cupsd.conf.default bedd8fafef3a16ccd1f52d9b0d01772c obsolete

```

I am running kubuntu, so my requirements might differ from yours... but this should at least let you see what you need (and also the installation status. :)

cheers,
bill

---

### Post by tgalati4 on 2013-09-16
It takes a few years to get linux under your belt.  Just keep plodding along and you will get it.  Try installing avahi-daemon and reboot.

---

