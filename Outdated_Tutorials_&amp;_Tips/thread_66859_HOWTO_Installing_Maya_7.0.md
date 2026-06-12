---
title: "HOWTO: Installing Maya 7.0"
date: 2005-09-18
forum: Outdated Tutorials &amp; Tips
---

### Post by szr4321 on 2005-09-18
This thread is about installing Alias Wavefront Maya 7.0 on Ubuntu, tested on Hoary 5.04.

It's based on johannes' thread about [Maya 6.5](http://ubuntuforums.org/showthread.php?t=45748).

The instructions are very similar for Autodesk Maya 8.0 and 8.5 (tested on Feisty 7.04). Thanks to ZombieAcademy for providing these hints.
You only need to adjust the filenames when installing the packages.

Install the following programs, in case you don't already have them:
```
apt-get install csh alien
```Copy over all rpm installation files to a local directory.
We need to convert the rpm-packages to debian format using alien. Change to the directory that holds your rpms and run:
```
for i in *.rpm; do sudo alien -cv $i; done
```This will take some time.
(fragmental reported that he had problems running alien on a FAT filesystem, so better don't try that.)
To make Maya install without problems later, we need to create the following link, even though /usr/aw doesn't exist yet:
```
sudo ln -s /usr/aw /aw
```
For Maya 8.0 / 8.5, you also need to run
```

sudo ln -s /usr/autodesk /autodesk

```
Now we're ready to install the Maya packages:
(Change the filenames according to your version. Also have a look at the update at the end of this howto.)
```
sudo dpkg -i awcommon-server_9.5-2_i386.deb
```
For Maya 8.0 / 8.5, you can *ignore* the warning about chkconfig not being found. Now, run
```

sudo dpkg -i awcommon_9.5-2_i386.deb
sudo dpkg -i maya7-0_7.0-375_i386.deb
```Now you need to install your license file (aw.dat).
Copy it over to /var/flexlm (create this directory if it doesn't exist):
```
sudo cp aw.dat /var/flexlm
```Make sure Maya has read-access to this file.
I *didn't* need to install aksusbd*.deb.
To stop Maya from complaining at startup about not being able to create a log file, run
```

sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp

```
You should be able to run Maya now by running:
```
maya
```
DinoeL noted that to fix the error
```

/aw/maya7.0/bin/maya.bin: /aw/maya7.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

```
you need to create some symlinks (only if you get the error above!):
```

sudo ln -sf /usr/lib/libstdc++.so.5 /usr/aw/maya/lib/libstdc++.so.5
sudo ln -sf /lib/libgcc_s.so.1 /usr/aw/maya/lib/libgcc_s.so.1

```
In case you get the error *"Can't Find libXp.so.6"*, you need to install libxp6 (thanks to *Rixeh* for this):```
apt-get install libxp6
```
Should you get the error *"/aw/COM/bin/installKey: error while loading shared libraries: libXm.so.2: cannot open shared object file: No such file or directory"*:```
apt-get install libmotif3
```
To install the documentation files (optional step), run:
```
sudo dpkg -i maya7-0-docs-en-us_7.0-381_i386.deb
sudo dpkg -i maya7-0-docserver_7.0-381_i386.deb
```You can start up and shut down the documentation server using
```
/usr/aw/maya/docs/startDocServer.sh
/usr/aw/maya/docs/shutdownDocServer.sh
```To make the documentation server start up at boot time, create the script /etc/init.d/maya-doc-server (as root) with the following content:
```
#! /bin/sh
#
# maya-doc-server
#
# Starts and stops the Maya Documentation Server
#
set -e
PATH=/usr/local/sbin:/usr/local/bin:/sbin:/bin:/usr/sbin:/usr/bin
PATH=$PATH:/usr/aw/maya/docs
DESC="Maya Documentation Server"
NAME=maya-doc-server
SCRIPTNAME=/etc/init.d/$NAME
case "$1" in
start)
echo -n "Starting $DESC"
startDocServer.sh
echo "."
;;
stop)
echo -n "Stopping $DESC"
shutdownDocServer.sh
echo "."
;;
restart|force-reload)
echo -n "Restarting $DESC"
shutdownDocServer.sh
startDocServer.sh
echo "."
;;
*)
echo "Usage: $SCRIPTNAME {start|stop|restart|force-reload}" >&2
exit 1
;;
esac
exit 0
```Now run```
sudo chmod +x /etc/init.d/maya-doc-server
sudo update-rc.d maya-doc-server defaults
```That should basically be all you need for a proper Maya installation on Ubuntu. Let me know if it worked for you!

I had big trouble running Maya and having the X composite extension enabled at the same time (using an nVidia card and current drivers): all titlebars disappeared. Apparently I'm not the only one with this [problem](http://ubuntuforums.org/showthread.php?p=106703&highlight=maya#post106703), so better disable compositing when using Maya. There's [another post](http://discussion.autodesk.com/thread.jspa?messageID=5499540) on the Autodesk forum that might be helpful (thanks, Bart Simpson 18 ).
Additionally, my window display got garbled when scrolling. For me it worked to add the following section to /etc/X11/xorg.conf:
```

Section "Extensions"
  Option "Composite" "Disable"
EndSection

```
You need to restart your X server to use these new settings. Compiz / Beryl probably won't work anymore because of this.

By default, [Alt] + mouse moves windows in Gnome. However, for Maya you need the Alt-key for rotation, zooming etc.
You can change the key binding to move windows in the Gnome settings. For example, set it to the Super-key, which corresponds to the Windows-key.

If you get font errors (e.g. "Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-"), you might want to check your xorg.conf; especially if you've got an ATI driver installed: some users reported that this driver messes up the font paths.

If Maya segfaults on startup, you should double-check your license file.

mattb reported a problem using the TextCurve tool (Create -> Text) in the [Maya 6.5](http://ubuntuforums.org/showthread.php?t=45748) thread (Maya doesn't find the font files). I'm not aware of a solution to this right now.

Alias provides a set of ["Bonus Tools"](http://www.alias.com/glb/eng/community/downloads/bonus_tools/index.jsp) which might be interesting for some of you. Just convert and install the rpm in the same way as above.

Meanwhile, Alias released an update, [Maya 7.01](http://www.alias.com/glb/eng/support/product_support.jsp?itemId=5200001). You'll need a bronze account to download, but that only means you'll have to register there (for free). This update includes all the rpms to install Maya.

There is also a download for [Maya 8.5 Service Pack 1](http://www.alias.com/glb/eng/support/product_support.jsp?itemId=9000001).

A cursor issue can be fixed by running
```

export MAYA_MMSET_DEFAULT_XCURSOR=1

```
(Thanks to endymon for this hint.)

---

### Post by simoncullen on 2005-09-29
it's okay now! cheers

---

### Post by Rixeh on 2005-10-03
Works like a charm.  An FYI, if anyone gets an error saying "Can't Find libXp.so.6", just apt-get install libxp6.  ;)

---

### Post by szr4321 on 2005-10-04
@Rixeh: Glad to hear that it worked for you!
Thanks a lot for the libxp6 hint, I've added it to the HowTo.

---

### Post by SecondMan on 2005-10-17
Hi all, 

I am a complete and utter newbie to Linux, but got my machine up and running on Ubuntu and now trying to install Maya 7. I am converting the rpm's to .deb files (or at least I am trying, but instead of building .deb files, alien creates directories which all contain a /debian and a /usr dir. Got no idea why and how to use them... any thoughts?

Thanks!

---

### Post by SecondMan on 2005-10-17
This is the output I get for one of them:

dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
        xargs -0 -r -i cp -a {} debian/awcommon
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dpkg-shlibdeps: warning: could not find path for libXm.so.2
dpkg-shlibdeps: warning: could not find path for libXp.so.6
dpkg-shlibdeps: warning: unable to find dependency information for shared library libstdc++ (soname 5, path /usr/lib32/libstdc+ +.so.5, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXt (soname 6, path /usr/lib32/libXt.so.6, dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libX11 (soname 6, path /usr/lib32/libX11.so.6 , dependency field Depends)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXmu (soname 6, path /usr/lib32/libXmu.so.6 , dependency field Depends)
dpkg-shlibdeps: warning: could not find any packages for  (libXp.so.6)
dpkg-shlibdeps: warning: unable to find dependency information for shared library libXp (soname 6, path , dependency field Depe nds)
dh_gencontrol
sh: gcc: command not found
dpkg-architecture: warning: Couldn't determine gcc system type, falling back to default (native compilation)
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find: AWCommon-9.5: No such file or directory


Looks like the fact that I am running this on an AMD64 system is an issue as well. Might not be possible at all to convert then... :(

---

### Post by szr4321 on 2005-10-19
You might want to try to install the build-essential package using apt-get / synaptic. This will include gcc for example. I'm not sure though if that'll help or if it's a AMD64 related issue.

---

### Post by DaveA on 2005-10-19
Hi,
I'm trying to get Maya 6 running on Breezy (sorry I couldn't find a more pertinent thread) but when I start Maya the output window continously shows this error message (a continous cascade):

> // Error: Failed trying to load font : -*-helvetica-bold-r-normal--14-*-*-*-p-82-iso8859-1 //
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-1 //
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-1 //
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-1 //
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-1 //
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-1 //
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--14-*-*-*-p-82-iso8859-1 //

Part of Maya interface is obviously missing fonts (timeline, rangeslider etc)

What shall I do/install to get this missing helvetica?

A friend has the same problem with Maya 7 / Breezy, so at least it's not only Maya 6 related

---

### Post by chadwick359 on 2005-10-20
Nice Howto, thanks for it. But whenever i just try to run the command maya, bash outputs this

> bash: /usr/local/bin/maya: /bin/csh: bad interpreter: No such file or directory

Any suggestions?

---

### Post by szr4321 on 2005-10-20
[QUOTE=chadwick359] bash: /usr/local/bin/maya: /bin/csh: bad interpreter: No such file or directory[/QUOTE]
Could it be possible that you haven't installed csh (at the very beginning of the HowTo)?
Try to run```
sudo apt-get install csh
```

---

### Post by szr4321 on 2005-10-20
[QUOTE=DaveA]
What shall I do/install to get this missing helvetica?
[/QUOTE]You might want to try to install appropriate xfonts-* packages, e.g. **xfonts-100dpi** provides */usr/X11R6/lib/X11/fonts/100dpi/helvBO14-ISO8859-1.pcf.gz* which seems what you're looking for. You can check what fonts are installed by running something like```
xlsfonts -fn "*helvetica-bold*"
```

---

### Post by chadwick359 on 2005-10-20
Yes, I had installed csh, and a reinstall fixed it. However, I still have a problem. The UI doesn't seem to be rendering properly. Parts or menus and buttons don't seem to be refreshing, and I get choppy lines across rarley used parts of the UI. It isn't usually a problem, but it does get annoying when I can't see all of the options. Is there any way to fix this?

---

### Post by MR.T on 2005-10-20
when trying to run maya I get the error "Segmentation fault" in terminal.

Eh I just notest the main maya file is i686...and I have a athlon xp CPU,is that why I got the error?,and if so  can I simply go into synaptic and remove all the maya DEBs Ive installed and  then get the i386 version of maya and install them? or can I do something with my existing i686 files?

thanks

---

### Post by groblus on 2005-10-21
considering fonts, i've encountered a problem with fonts (it gave me a problem with hud in viewports making damaging them), i had the fonts installed but maya still gave me the missing helvetica error, it turned out that i had my xorg.conf made by ati driver installer and it had font paths mixed up - i've fixed that and everything works fine now - no font missing error nor bad  viewports (ubuntu 5.10)

---

### Post by DaveA on 2005-10-21
Thanks for your help szr4321 and groblus! :) :) :) 

I already had xfonts-100dpi installed (I think they come as default in Ubuntu) so after reading fontconfig help I started messing with folders but couldn't think of the xorg.conf by ati :???: (I'm using Ubuntu/Linux in general since last week) Damn driver! Besides being a pain to install (have you read the how-to for latest ati 6.18.6? ;) ), a slow performer, is also a big troublemaker (garbled res etc..). Thanks again! :KS

---

### Post by szr4321 on 2005-10-22
[QUOTE=groblus]it turned out that i had my xorg.conf made by ati driver installer and it had font paths mixed up[/QUOTE]Thanks for the hint, I've updated the HowTo! :)

---

### Post by szr4321 on 2005-10-22
[QUOTE=chadwick359]Yes, I had installed csh, and a reinstall fixed it. However, I still have a problem. The UI doesn't seem to be rendering properly. Parts or menus and buttons don't seem to be refreshing, and I get choppy lines across rarley used parts of the UI. It isn't usually a problem, but it does get annoying when I can't see all of the options. Is there any way to fix this?[/QUOTE]Did you try to update your graphics driver?

---

### Post by szr4321 on 2005-10-22
[QUOTE=MR.T]when trying to run maya I get the error "Segmentation fault" in terminal.

Eh I just notest the main maya file is i686...and I have a athlon xp CPU,is that why I got the error?[/QUOTE]Hm, i686 should be just fine with an Athlon XP.

---

### Post by MR.T on 2005-10-22
^^^so then whats the whole "Segmentation fault" thing,I mean I know it has something to do with memory allocation,is there some kind of log or something I can post so someone can deduce my problem?

thanks

---

### Post by szr4321 on 2005-10-23
[QUOTE=MR.T]so then whats the whole "Segmentation fault" thing,I mean I know it has something to do with memory allocation,is there some kind of log or something I can post so someone can deduce my problem?[/QUOTE]You could use the GNU debugger to see where it crashes:```
maya -d gdb
```Enter *run* on the gdb command line to start maya. When it crashes, you might be able to use the backtrace command *bt* to see what went wrong.  This might give some hint where to look at.

Of course you might want to try to install the i386-version of Maya if the above doesn't help.

---

### Post by MR.T on 2005-10-23
^^^^^^^thanks for the advice,heres what I got:

Starting program: /usr/aw/maya7.0/bin/maya.bin
[Thread debugging using libthread_db enabled]
[New Thread -1313652608 (LWP 9943)]
[New Thread -1315165264 (LWP 9948)]

Program received signal SIGSEGV, Segmentation fault.
[Switching to Thread -1313652608 (LWP 9943)]
0xb66b0cd2 in deselect__12TstkEnvGv () from /aw/maya7.0/lib/libFoundation.so

using the bt command I get this:

#0  0xb66b0cd2 in deselect__12TstkEnvGv ()
   from /aw/maya7.0/lib/libFoundation.so
#1  0xb66b0bec in deselect__12TstkEnvGv ()
   from /aw/maya7.0/lib/libFoundation.so
#2  0xb66c6cbf in afj5iW () from /aw/maya7.0/lib/libFoundation.so
#3  0xb66c652e in l_checkout () from /aw/maya7.0/lib/libFoundation.so
#4  0xb66c6062 in l_checkout () from /aw/maya7.0/lib/libFoundation.so
#5  0xb66c5e58 in lc_checkout () from /aw/maya7.0/lib/libFoundation.so
#6  0xb66b1540 in secCheckoutLicenseByProcess ()
   from /aw/maya7.0/lib/libFoundation.so
#7  0xb66b0b43 in select__12TstkEnvGv () from /aw/maya7.0/lib/libFoundation.so
#8  0xb66af4bf in secReadVersion () from /aw/maya7.0/lib/libFoundation.so
#9  0xb66af774 in TregSelectGv::value () from /aw/maya7.0/lib/libFoundation.so
#10 0xb66aeca0 in sAttrVerify__10TvarSetGv ()
   from /aw/maya7.0/lib/libFoundation.so
#11 0x080520a8 in appmain ()
#12 0x0806a5cb in main ()

what does that mean?

thanks for the help so far

---

### Post by szr4321 on 2005-10-24
[QUOTE=MR.T]
#0  0xb66b0cd2 in deselect__12TstkEnvGv ()
   from /aw/maya7.0/lib/libFoundation.so
#1  0xb66b0bec in deselect__12TstkEnvGv ()
   from /aw/maya7.0/lib/libFoundation.so
#2  0xb66c6cbf in afj5iW () from /aw/maya7.0/lib/libFoundation.so
#3  0xb66c652e in l_checkout () from /aw/maya7.0/lib/libFoundation.so
#4  0xb66c6062 in l_checkout () from /aw/maya7.0/lib/libFoundation.so
#5  0xb66c5e58 in lc_checkout () from /aw/maya7.0/lib/libFoundation.so
#6  0xb66b1540 in secCheckoutLicenseByProcess ()
   from /aw/maya7.0/lib/libFoundation.so
#7  0xb66b0b43 in select__12TstkEnvGv () from /aw/maya7.0/lib/libFoundation.so
#8  0xb66af4bf in secReadVersion () from /aw/maya7.0/lib/libFoundation.so
#9  0xb66af774 in TregSelectGv::value () from /aw/maya7.0/lib/libFoundation.so
#10 0xb66aeca0 in sAttrVerify__10TvarSetGv ()
   from /aw/maya7.0/lib/libFoundation.so
#11 0x080520a8 in appmain ()
#12 0x0806a5cb in main ()[/QUOTE]Sorry, I'm stumped here :( . Unfortunately the crippled debug output isn't that much help without the source code. Did you check your license file (because of secCheckoutLicenseByProcess)? Maybe the official Maya support is able to help you more provided this backtrace.

Did you already try the i386 version?

---

### Post by lucas on 2005-11-04
Yes, that error is related to the license file. i got the same error before i had checked the license file properly. i did that and now it works. i only need to fix the "Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-" error. :)

---

### Post by szr4321 on 2005-11-05
[QUOTE=lucas]Yes, that error is related to the license file. i got the same error before i had checked the license file properly. i did that and now it works.[/QUOTE]Thanks for this hint![QUOTE=lucas]i only need to fix the "Error: Failed trying to load font : -*-helvetica-bold-r-normal--10-*-*-*-*-*-iso8859-" error. :)[/QUOTE]You should check your xorg.conf file:[QUOTE=groblus]considering fonts, i've encountered a problem with fonts (it gave me a problem with hud in viewports making damaging them), i had the fonts installed but maya still gave me the missing helvetica error, it turned out that i had my xorg.conf made by ati driver installer and it had font paths mixed up - i've fixed that and everything works fine now - no font missing error nor bad  viewports (ubuntu 5.10)[/QUOTE]

---

### Post by fragmental on 2006-01-12
I get this error when I try to install:

for i in *.rpm; do sudo alien -cv $i; done
      ```
  LANG=C rpm -qp --queryformat %{SUMMARY} aksusbd-redhat-1.5-1.i386.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} aksusbd-redhat-1.5-1.i386.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
        LANG=C rpm -qp --queryformat %{SUMMARY} aksusbd-suse-1.7-2.i386.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} aksusbd-suse-1.7-2.i386.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
        LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-9.5-1.i686.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-9.5-1.i686.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
        LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-server-9.5-1.i686.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-server-9.5-1.i686.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
        LANG=C rpm -qp --queryformat %{SUMMARY} Maya7_0-7.0-374.i686.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} Maya7_0-7.0-374.i686.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
        LANG=C rpm -qp --queryformat %{SUMMARY} Maya7_0-docs_en_US-7.0-380.i686.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} Maya7_0-docs_en_US-7.0-380.i686.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.
        LANG=C rpm -qp --queryformat %{SUMMARY} Maya7_0-docserver-7.0-380.i686.rpm
Error executing "LANG=C rpm -qp --queryformat %{SUMMARY} Maya7_0-docserver-7.0-380.i686.rpm":  at /usr/share/perl5/Alien/Package.pm line 449.

```

Any ideas?

---

### Post by fragmental on 2006-01-13
Must have been my copies of the rpms.  Seems to be working now.  It hasn't finished yet, so something could still go wrong.

---

### Post by apoclypse on 2006-01-13
Everything is working fine but it seems  that mental ray does't want to render at all. it keeps saying contour.mi and whole bunch of other things are not found.

---

### Post by szr4321 on 2006-01-15
[QUOTE=apoclypse]Everything is working fine but it seems  that mental ray does't want to render at all. it keeps saying contour.mi and whole bunch of other things are not found.[/QUOTE]Does */aw/maya7.0/mentalray/include/contour.mi* exist on your system?

---

### Post by fragmental on 2006-01-25
I had more trouble installing maya.  I used two different copies of the rpms and both of them  had errors when alien tried to install them.

Then I got another copy, but when I was trying to transfer them from the cd they had IO errors, but they seemed to be the same size so I went ahead and used alien on them and they worked.  After installing maya would start up and complain about how the temporary directory "/usr/tmp" wasn't accessible and how the maya couldn't create the directory, but it started anyway.  

Then, if I try to do anything in maya like click on any buttons or anything everything will freeze up and the only thing I can do is move the mouse and I have to hard reboot.   The keyboard does not respond or anything.  I had music playing once and the song finished and then the music did not continue on to the next song.

After it froze once I tried adding the /tmp/usr/ directory and made it read/write for my user account, but it didn't help.

Edit: I just realised that one of the copies had errors because it was on a FAT file system.  Apparently alien doesn't like FAT filesystems.  Good thing to note.

---

### Post by szr4321 on 2006-02-05
[QUOTE=fragmental]I just realised that one of the copies had errors because it was on a FAT file system.  Apparently alien doesn't like FAT filesystems.  Good thing to note.[/QUOTE]Thanks for the hint! I'll update the howto.

---

### Post by Eden on 2006-02-13
Thanks for the guide, works ok in 5.10 as well. 
One problem I did have was running the following line to convert the packages.
```
for i in *.rpm; do sudo alien -cv $i; done
```
I was getting the same error as fragmental, I c&p'd so that my have been why but copying the same line from fragmental's post worked.

---

### Post by Eden on 2006-02-13
ok im getting a small problem when trying to run maya.
```
Error: default temp directory /usr/tmp does not have write permissions.
Segmentation fault

```

any ideas?

---

### Post by Eden on 2006-02-13
3 posts ion a row sorry.

I thought id post a little update, ive got everything working perfectly.

```
Error: default temp directory /usr/tmp does not have write permissions.
```
this came up becuase there was no tmp directory in the usr folder, so i just created one with rw access.

second one was the licence, check it, fixed it and it now works.

---

### Post by tauil on 2006-02-14
Hello there !

I've installed Maya 7 like tutorial said but I got this erro:

"The 'Maya' application resource file cannot be found. Maya canno proceed without it."

Does Anyone know what is that ? ( see the erro screenshot [http://ubuntuforums.org/attachment.php?attachmentid=6138&stc=1&d=1139966477](http://ubuntuforums.org/attachment.php?attachmentid=6138&stc=1&d=1139966477) )

Thanks,
Tauil

---

### Post by aroticoz on 2006-03-09
I have the exact same problem as **tauil**.

If someone knows how to fix this please say, I have to get Maya working fast :neutral:

---

### Post by aden on 2006-03-13
Hm i installing maya.. running and everything goes fine but.. when i trying rotate screen or zoom in it don't work.. i pressing alt + left mouse and trying to move it but it did nothing. Someone know what could be wrong or had that problem before?

[sorry for my english :P]

---

### Post by Bubs on 2006-03-16
ok I can't get it to run!!

I installed it all the way up to the license but when I type "maya" in the terminal nothing happens. (without quotes):cry: 

I get this message:  bash: maya: command not found

whats up I'm a complete noob at linux so any help is appreciated.

---

### Post by aden on 2006-03-18
sudo apt-get install csh

and then make ur rpm files to deb using:

for i in *.rpm; do sudo alien -cv $i; done

should be ok after that

---

### Post by Bubs on 2006-03-19
ok don't flame me.  but has anyone gotten the maya crack to work in linux.  i've got the rpm's and the crack but I just don't know how to run the crack.

---

### Post by aden on 2006-03-19
Crack should has "install.txt" file. If he doesn't:

[quote=]
WINDOWS:
--------
1.  First Create a directory on the c: drive (even if you install maya on different drive) called
    FLEXLM
2.  Copy the aw.dat and awkeygen.exe file to this directory.
3.  Install Maya
4.  Goto start-->all programs-->AliasWavefront-->common utilities-->FlexLM license utilities
5.  Under system settings copy Ethernet address
6.  Open the file (from the directory FLEXLM) aw.dat with Wordpad and replace the words "your host"
    with the copied Ethernet address. Save and close wordpad
7.  Using the run utility and type: awkeygen.exe aw.dat
8.  Goto start-->all programs-->AliasWavefront-->common utilities-->Install license
10. Under the path of the file aw.dat
11. Click install
12. Restart computer


LINUX:
------
Start at Step 3.

Your license (default) dir is /var/flexlm
so copy the generated aw.dat (you did that on a windows machine in dos)
into that directory.
[/quote]

---

### Post by Bubs on 2006-03-19
yea but how do I use the keygen it's an exe and comes out as an unrecognized format.

i think I got everything else 
i installed the rpm's using alien ( ididn't convert to debs I just installed the rpms themselves)
I found my ehternet address and replaced "your host"
but I don't know how to run the keygen.exe

or if i even have to, which in that case i messed up somewhere else

---

### Post by aden on 2006-03-19
U have to did this on ur windows.. if u don't have it well.. u've got a problem :P 
btw. maybe u should make rpms to deb before installing cos if i aliened them without csh maya wasn't run so there's can be a problem when u wrote that maya doesn't starta by writing "maya" 

ps. Yes! i know! my english sux ;]

---

### Post by Bubs on 2006-03-19
ok one last question.  I saw this ealier but they were running an athlon xp chip 

does it matter that I have the i686 rpm's

I'm running a hp laptop with a pentium 4.  I'm having a dificult time finding the i386 rpm's

---

### Post by aden on 2006-03-20
i've got i686 package running on p4 also and everything is ok

---

### Post by Bubs on 2006-03-21
ok I converted all the rpm's to debs but then I get this when trying to dpkg maya

License installation failed
A detailed license installation report may be found at: /tmp/alias_rpt_1wprCl
There may be a more recent license for this workstation available on the Alias
web site. Please visit the following URL to check for updated licenses:
[http://www.alias.com/en/Community/Special/keys/maya/](http://www.alias.com/en/Community/Special/keys/maya/)



this is what the /tmp/alias.... file has in it.

<b><u>License Installation Report</u></b><br>
Installing from license file /usr/aw/maya/license_data/prekey.dat.
Input license contains 0 license(s) matching this computer.<br>
End of license installation report.

anyone know what this means and how I can fix this?

---

### Post by Bubs on 2006-03-21
ok despite the last post maya works now !!!!!! \\:D/ 

thank you aden.

buy the way did you fix the alt+mouse problem?

---

### Post by aden on 2006-03-21
in gnome u have to go system -> preferences -> windows [or sth like that] and there u can change alt for other button and rotate will work

---

### Post by notor on 2006-03-23
hi all:KS 

i just got Maya7 working on ubuntu :p 


anyways, it seems to work, but when i try to render it doesn't render anything,](*,) 
any suggestions?:confused: 



A default light has been created, modify defaultRenderGlobals.enableDefaultLight to change this behavior.
Automatic near/far clipping values: 36.6003, 40.1247.
Starting Rendering /home/jason/maya/projects/default/images/tmp/untitled.iff.
Constructing shading groups.

Rendering current frame.
Frame triangle count: 760

====================================
Resource Usage At End Of Frame
====================================
1 Page faults
164.500 Mb Peak total size(Estimated)
37.938 Mb Peak arena size
====================================
66.957 Mb Heap
0.125 Mb Transforms
30.078 Mb MEL
0.007 Mb Render Geometry Arena
0.750 Mb NURBS AG
0.312 Mb Data Blocks
6.672 Mb Render Cache
====================================
Postprocessing rendering result.
Time For Tessellation (hh:mm:ss): 00:00:00
Time For Shadow Map (hh:mm:ss): 00:00:00
Time For Post Process (hh:mm:ss): 00:00:00
Time For Frame Render (hh:mm:ss): 00:00:00
Finished Rendering /home/jason/maya/projects/default/images/tmp/untitled.iff.

---

### Post by ibabob on 2006-04-03
Great guide! got maya 7 working on 5.10 in no time! thanks a lot.

Coming from windows, I'm wondering if there is any way to make maya look a little better, like having menus and text that looks and acts more like a gnome program, cause by default it looks like linux 8 years ago :( Also, tapping the spacebar seems to work only sometimes when trying to go from full view to four view in the panels. Another thing is that X mouse pointer... it not that bad to have it for some tools in maya, but why doesn't it goes back to the normal mouse pointer outside of Maya?

Thank you

---

### Post by smudge on 2006-04-08
Hi guys,

I'm generally a pretty good linux hacker and have no problem installing maya and it's licence it and found this post very good. One thing I do have problems with however is when I load Maya, I cannot alt+mousebutton to scroll around. I'm using KDE, and alt+mousebutton moves the whole screen around, not the camera! Anyone have this problem, or know a fix?

Keep up the good work! :KS

---

### Post by Bubs on 2006-04-09
you can download a pdf manual with all kinds of install info on the alias website.  so when I read it it says this

"open the kde control center.  
select desktop then select window behavior
open the actions tab
in the inner window, title bar and frame section, for modifier key alt, set all mouse action combonations to nothing."

---

### Post by smudge on 2006-04-09
Thank you Bubs, a very helpful tip that works a treat. I am now playing with window specific settings to see if I can enable this only on one desktop, a Maya desktop. Thanks again.

---

### Post by animax_forever on 2006-04-14
Hi guyz,

i successfully installed maya 7.0 on my ubuntu 5.10.it is working but in startup it shows some errors,

file -f -new;
[COLOR="red"]// Warning: Unable to get OpenGL visual with a depth buffer, trying without //
// Warning: Unable to get OpenGL visual with a depth buffer, trying without //
// Warning: Unable to get OpenGL visual with a depth buffer, trying without //
// Warning: Unable to get OpenGL visual with a depth buffer, trying without //[/COLOR]
// Result: ./untitled //
docServer -start;
// mental ray for Maya 7.0 
// mental ray for Maya: using startup file /aw/maya7.0/mentalray/maya.rayrc
// mental ray for Maya: setup
// mental ray for Maya: initialize
// mental ray for Maya: using 1 license
// mental ray for Maya: register extensions
// mental ray Node Factory: loaded
// parsing /aw/maya7.0/mentalray/include/base.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/contour.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/paint.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/physics.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/subsurface.mi
// generating Maya nodes...
// mental ray for Maya: successfully registered
// MayaLive version 7.0updateRendererUI;
// Saving runtime commands to : /root/maya/7.0/prefs/userRunTimeCommands.mel
// Saving hotkeys to : /root/maya/7.0/prefs/userHotkeys.mel
// Saving named commands to : /root/maya/7.0/prefs/userNamedCommands.mel
// Preferences saved. See Script Editor for details.
[COLOR="Red"]// Warning: Unable to get OpenGL visual with a depth buffer, trying without //[/COLOR]

i have ATI Radeon 9200 graphics card.How to install it's driver.I downloaded the setup from it's site.
I then generated the source pakage for ubuntu 5.10, then i don't know how to compile it.{lease help me.](*,)

---

### Post by Mike_48 on 2006-04-17
Potreste dirmi cosa è il Run Utility e dove si trova in Maya .
Grazie mille
Mike

---

### Post by Bubs on 2006-04-17
Ho usato i pesci de Babele per tradurre questo in modo da può essere un po'divertente. il programma di utilità di funzionamento è il terminale. dopo voi installi il maya aprono il terminale ed il tipo "maya" ed esso dovrebbe funzionare. per trovare lo sguardo terminale sotto la finestra di applicazioni.

---

### Post by arash on 2006-04-22
I managed to install Maya 7 on ubuntu, without any problem, following this HowTo, but I can't get maya to start on "dapper" following the same HowTo.
I get this 
bash: maya: command not found

I think it's a permission-problem. But I am newbie linux user and I don't know where to begin.
 
Anyone can help?

---

### Post by sergio_dos_bonecos on 2006-05-03
Hello

Is there anyone that could send me the activation code for MAYA7.0 ??
please.
thank

---

### Post by Bubs on 2006-05-03
you have to have a crack... and you can easily find it on the internet, just google maya 7 crack and you'll find it.  it's a little tough to figure out at first but it works

---

### Post by abs on 2006-05-04
dudes, just a quick NOTE: I strongly advise against using any direct links to cracks/keygens, so for all you future poster please bare this in mind.

thanks.


also if your working in Maya try the maximise window mode and you can have a little extra space for editing/modelling.


Abs

---

### Post by MistaED on 2006-05-05
Hey, so far I've got maya up and running in ubuntu. Just a few problems though:

* The cursor turns into the default "X" all the time, often permanently. This happens only in gnome though, and not KDE. Is there a way to just use default X11 cursors and disable the gnome way? This is the biggest problem I have at the moment.

* Mental Ray just crashes the program when used. No idea on how to fix this one.

* I hate motif widgets! I hope they change to Qt/Gtk in the next version! Fair enough this one is a gripe :)

It would be great if these problems can be solved as I am in a maya course at the moment and will be living and breathing in this program, and I don't want to use windows or suse/fedora. I was hoping dapper solved the cursor issue but it still does it.

-MistaED

---

### Post by abs on 2006-05-05
[QUOTE=MistaED]Hey, so far I've got maya up and running in ubuntu. Just a few problems though:

* The cursor turns into the default "X" all the time, often permanently. This happens only in gnome though, and not KDE. Is there a way to just use default X11 cursors and disable the gnome way? This is the biggest problem I have at the moment.

* Mental Ray just crashes the program when used. No idea on how to fix this one.

* I hate motif widgets! I hope they change to Qt/Gtk in the next version! Fair enough this one is a gripe :)

It would be great if these problems can be solved as I am in a maya course at the moment and will be living and breathing in this program, and I don't want to use windows or suse/fedora. I was hoping dapper solved the cursor issue but it still does it.

-MistaED[/QUOTE]


mentalray is a problem and yes, that X corser is a problem, Mybe now they are woned by autodesk they will have more funds to create a better linux port, however, Autodesk has close ties with M$, so not sure where that will lead too.

---

### Post by atrus123 on 2006-05-06
[QUOTE=arash]I managed to install Maya 7 on ubuntu, without any problem, following this HowTo, but I can't get maya to start on "dapper" following the same HowTo.
I get this 
bash: maya: command not found

I think it's a permission-problem. But I am newbie linux user and I don't know where to begin.
 
Anyone can help?[/QUOTE]


I am running into this exact same problem.  For some reason, Maya7 doesn't want to work with Dapper.  I can't figure it out for now, which means I'm stuck downgrading.  Anyone have any ideas?

J.

---

### Post by jujoje on 2006-05-07
Hi,

I'm running maya 7 on dapper and mental ray and the 'maya' and 'Render' commands are all working from the terminal. 

Given that the commands aren't working in the terminal for you I'm guessing that there may be some problem with converting the rpms in dapper. The ones I used to install maya (following this guide) were made in breezy, and I vaguely remember having some difficulty with ones that I'd made in dapper.

If you look in /usr/local/bin there should be 3 files which are put there by mayaL: "maya" "Render" and "fcheck". If they are not there then something has cocked up somewhere along the line.

Unfortunately, beeing something of a newbie myself, I can't really suggest anything other then trying to convert the rpms again or going to breezy, converting the rpms, saving them, reinstalling dapper and trying again. Not the best of solutions I'm afraid :(. Perhaps someone who knows a bit more can provide a better solution.

In relation to mental ray freaking out, I found that after installing mental ray was looking for the shaders in the wrong place. This can be fixed by editing  /usr/aw/maya7.0/mentalray/maya.rayrc file and changing the first line to:

> 
registry "{MAYABASE}"	value	"/usr/aw/maya7.0//mentalray"

Sorry about the somewhat speculative reply. Hope something in there helps :)

---

### Post by jujoje on 2006-05-07
That should have been: 

> registry "{MAYABASE}" value "/usr/aw/maya7.0/mentalray"

Oddly enough I did originally have two //s in there but oddly enough it still worked :)

---

### Post by Mike_48 on 2006-05-22
[QUOTE=aden]Crack should has "install.txt" file. If he doesn't:[/QUOTE]
Using the run utility and type: awkeygen.exe aw.dat, What does mean this! What exactly is the run utility and where I can find it.

Many thanks

---

### Post by Bubs on 2006-05-22
the "run" Utility is you console the Dos Prompt looking thingy  and the awkeygen should be in the folder with the crack

---

### Post by MistaED on 2006-05-27
I wouldn't be duscussing keygens and cracks in here for maya.....

I found an awesome solution for the mouse arrow always turning into the default X, you've got to run:
```
export MAYA_MMSET_DEFAULT_XCURSOR=1
```
before starting maya in the terminal, then the cursor shouldn't revert to X under maya (for an example, click the shelf-tab button to add/remove/modify shelves without that export, then try it again with the export option).

Now, I want to ask how can I just make a script for this, or have the maya in my gnome menu doing this everytime I run it. I've tried a basic bash script with
```
export MAYA_MMSET_DEFAULT_XCURSOR=1 & maya
```
but it never seems to work, and I also put it into my $HOME/.bashrc which works with gnome SUSE, but not for dapper. Can anyone tell me a way to fix this?

I Hope this helps, oh and mental ray works fine now for me, odd. I think I just made the whole /usr/aw directory chmod -R 777 or something. That should solve some permission problems people have been having (there's probably a more secure number config but this just worked for me and I'm the only one using this computer anyway).

---

### Post by apatris on 2006-06-04
Hi guys, 

Great guide. I have followed it and have installed (or at least believe so, being a newbie) maya 7 on dapper. Though it does not seem to start properly. I get the following error :

```

Warning: Color name "black" is not defined

```

and then something called a "script editor" starts. You can see a screenshot of it [IMG]http://firstwebdev.net/screen.png[/IMG]

EDIT :
ok , got it fixed. It was a bug. It seems that a file called rgb.txt is missing or mislocated

Creating a symbolic link to where the file seems to be physically residing solved the problem for me. see below :

```


sudo ln -s /etc/X11/rgb.txt /usr/share/X11/rgb.txt

```


You can find further info on this issue in this thread :

[http://www.ubuntuforums.org/showthread.php?t=90751&page=2&highlight=rgb.txt](http://www.ubuntuforums.org/showthread.php?t=90751&page=2&highlight=rgb.txt)

Thanks again for an understandable guide

---

### Post by lethal_falcon on 2006-06-09
I'm having a problem similar to the above poster, but I'm not getting any warnings.  I installed Maya as per the instructions on page 1.  When I run it (as any user), the splash screen comes up, and then it loads the script editor, but I don't get the main Maya window.  The script editor's output is this:

> // Error: File not found: newLayerSelected.xpm //
// mental ray for Maya 7.0
// mental ray for Maya: using startup file /aw/maya7.0/mentalray/maya.rayrc
// mental ray for Maya: setup
// mental ray for Maya: initialize
// mental ray for Maya: using 1 license
// mental ray for Maya: register extensions
// mental ray Node Factory: loaded
// parsing /aw/maya7.0/mentalray/include/base.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/contour.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/paint.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/physics.mi
// generating Maya nodes...
// parsing /aw/maya7.0/mentalray/include/subsurface.mi
// generating Maya nodes...
// mental ray for Maya: successfully registered
// MayaLive version 7.0.1// Error: Object not found:  //
updateRendererUI;
// Error: Object not found: mainRenderMenu //
// Error: Object not found:  //

All of the "object not found" messages bother me a bit, but I have no idea what objects it's looking for.  Has anyone else had this issue?

Note: I'm using X.org 7.0 modular, with nvidia driver version 87.62. I have turned off composite.

Any help would be appreciated. Thanks.

UPDATE: Well, I figured out the problem. Apparently when I'd let nvidia change my xorg.conf file, it hosed all of my font paths. So, if you're ever in this same boat, make sure your font paths are set.

---

### Post by lethal_falcon on 2006-06-10
[QUOTE=MistaED]I wouldn't be duscussing keygens and cracks in here for maya.....

I found an awesome solution for the mouse arrow always turning into the default X, you've got to run:
```
export MAYA_MMSET_DEFAULT_XCURSOR=1
```
before starting maya in the terminal, then the cursor shouldn't revert to X under maya (for an example, click the shelf-tab button to add/remove/modify shelves without that export, then try it again with the export option).

Now, I want to ask how can I just make a script for this, or have the maya in my gnome menu doing this everytime I run it. I've tried a basic bash script with
```
export MAYA_MMSET_DEFAULT_XCURSOR=1 & maya
```
but it never seems to work, and I also put it into my $HOME/.bashrc which works with gnome SUSE, but not for dapper. Can anyone tell me a way to fix this?

I Hope this helps, oh and mental ray works fine now for me, odd. I think I just made the whole /usr/aw directory chmod -R 777 or something. That should solve some permission problems people have been having (there's probably a more secure number config but this just worked for me and I'm the only one using this computer anyway).[/QUOTE]

The setting works great! If you want to add it to a menu, do this instead:

```
export MAYA_MMSET_DEFAULT_XCURSOR=1; maya
```

I did this in fluxbox and it worked, but other menu systems should work the same way.  Hope this helps!

---

### Post by JakobWelner on 2006-06-16
I've installe Maya 7.01 on Dapper and everything seems to work ok apart from the sound. When I loaded a wave file, Maya said that it couldn't load libaudiofile.so, with a quick search and by linking libaudiofile.so to libaudiofile.so.1 I fixed this error. When I load a maya file already including audio, it dosn't complain and the name showup by RMB on the timeline -> sound, but the sound dosn't show on the timeline itself and no sound gets played when I playback the animation or scrub.
When I start af new scene and try to import the soundfile it dosn't show wave files, so there is no way of importing them then. 
I guess it could be some wave support for maya that I havn't installed yet, but it plays flawlessly in all other players I have installed.
Anyone who have any idea how this could be sorted out? It's quite important that I get this to work as I usually animate to music and I would hate to be forced to use windows :(
Thanks in advance

---

### Post by honolulu on 2006-06-21
hi folks i´m trying to install maya 7.0 on ubuntu 6.06
but it doesn´t work...
converting of files went fine
installing of the following files 
 awcommon-server_9.5-2_i386.deb
 awcommon_9.5-2_i386.deb
went fine too but when i try to install maya7-0_7.0-375_i386.deb
i get the following message:


nobody@nowhere:~/MayaL$ sudo dpkg -i maya7-0_7.0-375_i386.deb
(Reading database ... 110023 files and directories currently installed.)
Preparing to replace maya7-0 7.0-375 (using maya7-0_7.0-375_i386.deb) ...
/var/lib/dpkg/info/maya7-0.prerm: line 8: test: upgrade: integer expression expected
Unpacking replacement maya7-0 ...
Setting up maya7-0 (7.0-375) ...
License installation failed
A detailed license installation report may be found at: /tmp/alias_rpt_Mk8YFB
There may be a more recent license for this workstation available on the Alias
web site. Please visit the following URL to check for updated licenses:
[http://www.alias.com/en/Community/Special/keys/maya/](http://www.alias.com/en/Community/Special/keys/maya/)

can anybody help me?

---

### Post by ephemeros on 2006-06-25
hello,
i have some experience using maya on linux, the last time i installed it on ubuntu 6.06 and kubuntu 6.06 (my GF). it works fine, like what i call "fine" on linux.
  -on **KDE** maya has a conflict with **[COLOR="Red"]Klipper[/COLOR]**, so it must be closed, else maya could crash while switching viewports;
  -on **Gnome**, about that cursor problem, it is enough to add the line: **[COLOR="Red"]MAYA_MMSET_DEFAULT_XCURSOR=1[/COLOR]** in the **[COLOR="Red"]/home/user/maya/7.0/Maya.env[/COLOR]** file;
  about the installation:
 -be sure to have **[COLOR="Red"]csh[/COLOR]** or **[COLOR="Red"]tchs[/COLOR]** installed before installing maya (maya uses csh shell language scripts);
 -i installed it with **[COLOR="Red"]alien[/COLOR]** directly (alien -c -i *.rpm) or just converted it (alien -c -d *.rpm) and installed the debs normally. i read about using the flag "-c" to allow maya scripts to be run;
  -in the console i get the following errors:
```
ln: creating symbolic link `/aw/maya' to `maya7.0': No such file or directory
ln: creating symbolic link `/aw/maya7.0/bin/maya' to `Maya7.0': No such file or directory
ln: creating symbolic link `/aw/maya7.0/bin/plug-ins/Mayatomr.sog' to `Mayatomr.so': No such file or directory
ln: creating symbolic link `/aw/maya7.0/lib/libgcc_s.so' to `libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/aw/maya7.0/lib/libstdc++.so.5' to `libstdc++.so.5.0.6': No such file or directory
ln: creating symbolic link `/aw/maya7.0/lib/libstdc++.so' to `libstdc++.so.5.0.6': No such file or directory
sed: can't read /aw/maya7.0/mentalray/maya.rayrc: No such file or directory
sed: can't read /aw/maya7.0/bin/unsupported/mayarender_with_mr: No such file or directory
sed: can't read /aw/maya7.0/bin/unsupported/mayaexport_with_mr: No such file or directory
mv: cannot move `/tmp/maya.rayrc' to `/aw/maya7.0/mentalray/maya.rayrc': No such file or directory
mv: cannot move `/tmp/mayarender_with_mr' to `/aw/maya7.0/bin/unsupported/mayarender_with_mr': No such file or directory
mv: cannot move `/tmp/mayaexport_with_mr' to `/aw/maya7.0/bin/unsupported/mayaexport_with_mr': No such file or directory
```

  so: 
 -i must create a symbolic link **[COLOR="Red"]'/usr/aw/maya'[/COLOR]** for the existing folder **[COLOR="Red"]'/usr/aw/maya7.0'[/COLOR]**;
 -create a symbolic link **[COLOR="Red"]'/usr/aw/maya7.0/bin/maya'[/COLOR]** for the existing C shell script **[COLOR="Red"]'/usr/aw/maya7.0/bin/Maya7.0'[/COLOR]**;
 -create a symbolic link **[COLOR="Red"]'/usr/aw/maya7.0/bin/plug-ins/Mayatomr.sog'[/COLOR]** for the existing lib **[COLOR="Red"]'/usr/aw/maya7.0/bin/plug-ins/Mayatomr.so'[/COLOR]**;
 -create a link **[COLOR="Red"]`/aw/maya7.0/lib/libgcc_s.so'[/COLOR]** for the existing lib **[COLOR="Red"]`/aw/maya7.0/lib/libgcc_s.so.1'[/COLOR]**;
 -the following links were allready made (on my comp) in the installation: **[COLOR="Blue"]`/aw/maya7.0/lib/libstdc++.so.5'[/COLOR]** for **[COLOR="Blue"]`/aw/maya7.0/lib/libstdc++.so.5.0.6'[/COLOR]** and **[COLOR="Blue"]`/aw/maya7.0/lib/libstdc++.so'[/COLOR]** for **[COLOR="Blue"]`/aw/maya7.0/lib/libstdc++.so.5.0.6'[/COLOR]**.

---for the other 6 errors i didnt do anything.
  next i just added symbolic links with the same names in **'/usr/local/bin'** for the following files: **[COLOR="Red"]'/usr/aw/maya7.0/bin/fcheck'[/COLOR]**, **[COLOR="Red"]'/usr/aw/maya7.0/bin/imgcvt'[/COLOR]**, **[COLOR="Red"]'/usr/aw/maya7.0/bin/maya'[/COLOR]** and **[COLOR="Red"]'/usr/aw/maya7.0/bin/Render'[/COLOR]**.
 -- that was all about the installation.
  ---about the licence activation, you must have instructions from Alias/Autodesk. the **'aw.dat'** file must be copied in **'/usr/aw'** folder. you can see the HOSTID/HWaddr typing '**[COLOR="Red"]ifconfig[/COLOR]**' in the console (12 digits code). for the poorer people: the crack is made for Windoze and should work with wine, but i won't discuss about that. in a better world, anyone would have the possibility to buy **Maya** ;)
**Maya** rullz! \m/

---

### Post by Victor.Barna on 2006-07-04
Hi guys, i'm having a slight problem with my installation...i installed maya, everything was ok, i installed the licence but now, when i try to run maya, i keep getting the "maya 7.0 requires an activation key" window, please help me.
thanks in advance.

---

### Post by BIGtrouble77 on 2006-07-09
Has anyone tried to do a forced install with a 64bit system?  I have a feeling it might work as long as I have the 32 nvidia libraries installed, but just wanted to check first.

---

### Post by }{yBr!D^ on 2006-07-15
I'm actually having problems with step 7 in the install.txt...

"Using the run utility and type: awkeygen.exe aw.dat"

When I type in "awkeygen.exe aw.dat" in window's run utility i get this error message...

"Windows cannot find 'awkeygen.exe'. Make sure you typed the name correctly, and then try again. To search for a file, click the start button, and then click Search."

What am I doing wrong...? there is no typo's and I copy/paste it... wtf?

---

### Post by mech7 on 2006-07-16
lol plz no crack replies here.. go elsewhere for illegal software..

Btw.. does anybody also has a black cross issue.. and a bit slow performance, and also I have lost all animtion when for example i frame something up?

---

### Post by mech7 on 2006-07-16
When I run this in the terminal it works.. but not when i use this in the menu with alacarte? how can i fix this ?

[RIGHT][/RIGHT]

> **lethal_falcon said:**
> The setting works great! If you want to add it to a menu, do this instead:

```
export MAYA_MMSET_DEFAULT_XCURSOR=1; maya
```

I did this in fluxbox and it worked, but other menu systems should work the same way.  Hope this helps!

---

### Post by Ashur on 2006-07-20
> **szr4321 said:**
> *mattb* reported a problem using the TextCurve tool (Create -> Text) in the [Maya 6.5]("http://ubuntuforums.org/showthread.php?t=45748") thread (Maya doesn't find the font files). I'm not aware of a solution to this right now.

Maya looks in the following paths for postscript fonts:
[B]/usr/share/fonts/default/ghostscript
/usr/X11R6/lib/X11/fonts/Type1[/B]

Just link some fonts to any of this locations and the TextCurve tool
shoud work.

---

### Post by jujoje on 2006-07-22
Has anyone managed to get a wacom tablet working with maya? 

I found a post on [Highend3d]("http://www.highend3d.com/boards/lofiversion/index.php/t215925.html") suggesting that changing the mode for the tablet in xorg from "absolute" to "relative" would make maya detect the tablet properly. Unfortunately that doesn't appear to work for me since the pressure options in the artisan based tools are still grayed out, although the tablet is now working in relative mode. 

The wacom tablet is an Intuos3, and works fine in the GIMP and other apps.

---

### Post by pgatrick on 2006-07-26
After getting everything installed, I'm having a problem with meshes getting really screwed up after only one or two subdivides or smooths.. Anyone else have this problem? I'm on 64 bit ubuntu, so it's installed on a chroot, would that make any difference in it?

---

### Post by sunkari on 2006-07-28
Guys i installed Maya 7.01 in Ubuntu 6.06.When i run Maya I am unable to see workspace(views).The error shown by the application is opengl is not configured properly.Wat i have to do now?

---

### Post by draka on 2006-07-30
Hi all

I've installed maya , but when I wrote in the terminal
 
"$ maya"

I got this:

"/aw/maya7.0/bin/maya.bin: error while loading shared libraries: /aw/maya7.0/lib/libPolyEngine.so: unexpected reloc type 0x0a"

does anybody has any idea?

---

### Post by ephemeros on 2006-07-31
@mech7: write MAYA_MMSET_DEFAULT_XCURSOR=1 in your /home/user/maya/7.0/maya.env file. start maya as usual;
@sunkari: you must configure the video drivers for your video card. check the threads about configuring the video card with hardware acceleration, this is not a maya issue (i hope ;) );
@draka: what version of ubuntu do you use? that souns weird, i never heard about that problem.
@pgatrick: what do you mean by "screwd up", can you post a screenshot?

---

### Post by draka on 2006-07-31
I'm using 6.06.
It's wired, yes. I read many forums and there was nothing about that:confused:

---

### Post by pgatrick on 2006-08-03
> **ephemeros said:**
> @pgatrick: what do you mean by "screwd up", can you post a screenshot?
Here's the screenshot. Trying to smooth or subdivide on anything more than just a simple model and it does that. Polys are the only thing I'm having problems with, everything else works flawlessly.

---

### Post by MistaED on 2006-08-04
pgatrick: running 32-bit dapper here and I can smooth/subdivide fine on a basic cube over and over. What video chip do you use? Try uploading the .ma/.mb file and I'll take a look if it's video card related or it really is maya/ubuntu stuffing up. Does the object have any history? Try clearing it first maybe and then smooth/subd.

Maya 8 just came out a few days ago and there's a 64-bit port, so maybe you could test that out (granted you have enough money to get the next version :P).

---

### Post by CyaNox on 2006-08-11
Installing Maya 8 using this guide was a success. Everything works here on my Dell Inspiron 9400 with Ubuntu 6.06.

I had one minor problem and that was that Maya could not write to /usr/tmp ... a simple chmod 777 did the trick.

---

### Post by calford on 2006-08-14
I managed to install maya 8 with the instructions and everything worked fine.
i did notice that the time line had the numbers missing and the fonts looked quite crappy.
I am using xgl (eye candy) and have noticed that it messes the graphics up.
this topic will fix most of those problems:
[http://www.ubuntuforums.org/showthread.php?t=176636](http://www.ubuntuforums.org/showthread.php?t=176636)

but now maya stays on top of every other window on any desktop. and it doesnt have a window border so it cant be resized or closed.

any ideas how to fix that

---

### Post by danny b on 2006-08-15
Has any one installed D2's nuke on ubuntu? [www.d2software.com](www.d2software.com)

I know this isnt the right discussion board but i couldn't find any more sutible.

Cheers

---

### Post by redx666 on 2006-08-21
Has anyone been able to install Maya 8 64-bit using this method?

---

### Post by xxxx on 2006-08-27
hi,
so im following the instructions below, but no.7 looks like a typo to me? :( Can anyone tell me what its meant to say? Im not sure what it means, I dont even know how to use the run utility in this case!!

thx
all

xxxx

WINDOWS:
--------
1. First Create a directory on the c: drive (even if you install maya on different drive) called
FLEXLM
2. Copy the aw.dat and awkeygen.exe file to this directory.
3. Install Maya
4. Goto start-->all programs-->AliasWavefront-->common utilities-->FlexLM license utilities
5. Under system settings copy Ethernet address
6. Open the file (from the directory FLEXLM) aw.dat with Wordpad and replace the words "your host"
with the copied Ethernet address. Save and close wordpad
7. Using the run utility and type: awkeygen.exe aw.dat
8. Goto start-->all programs-->AliasWavefront-->common utilities-->Install license
10. Under the path of the file aw.dat
11. Click install
12. Restart computer

---

### Post by westie on 2006-08-28
when I run this....
sudo dpkg -i awcommon-server_10.80-8_amd64.deb

I get a this:
Warning:  Unable to locate the chkconfig utility!

and it halts any ideas?

---

### Post by Madley on 2006-08-31
Hi all, its my first post in this community..!

I'm new ubuntu user, and I'm trying to install Maya on my laptop. Well, i think i installed it correctly, but when I launch it from terminal typing "maya" i get:

```
bash: maya: command not found
```

So i type "./maya.bin" and it seem to start... but it isn't so. I get a little window, empty, called "MayaStartupWnd" and a little black square. 
If I click the bar i see in the window, the window shut down and so i'm at the starting point....

Anyone can help me?

Thanks

---

### Post by eagle0691 on 2006-09-03
To #94

That is "$alien -c #(includ scripts)" to convert rpms,check this out, may be help.

---

### Post by eagle0691 on 2006-09-03
either for # 94

sometimes maya 8 need "csh" to startup, then  "apt-get install csh", this might fix your problem

---

### Post by jankubjan on 2006-09-04
i tried installing maya on kubuntu, everything went on well, until
i tried to install the licence, whatever you do to aw.dat file, the maya licence manager says.. its not a valid host id..., can anyone help me on this...

---

### Post by Madley on 2006-09-08
Thanks for your help, now I try and see what happen...

I'll told you if so it works.

Thanks.

---

### Post by iyeo on 2006-09-17
How did you people who got this working get past the server installer wanting chkconfig?  Chkconfig is only available in fedora/redhat.

---

### Post by iyeo on 2006-09-19
Nevermind about chkconfig.  I got Maya 8 x64 working with ubuntu 6.06 x64.  The font rendering is a bit funky, but it works.  Thank you all.

---

### Post by leif3d on 2006-09-22
> **iyeo said:**
> Nevermind about chkconfig.  I got Maya 8 x64 working with ubuntu 6.06 x64.  The font rendering is a bit funky, but it works.  Thank you all.
Did you get Maya 8 running with the same steps? or you had to do something different (to solve your problem)?...and how stable is Maya 8 x64 on Ubuntu?

By the way...I tried installing Maya 7.0.1 on Ubuntu amd64...I couldn't get past the 2nd step...is this because it's a 32 bit package and not a 64 bit one? Thanks;)

---

### Post by strattonbrazil on 2006-09-23
Has anyone tried Maya 8.0 with success?  I seem to be getting some kind of error in alien that doesn't give me any debian files.  

Here's the output when I try alien on the server rpm:

dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dh_md5sums
dh_builddeb
dpkg-deb: control directory has bad permissions 700 (must be >=0755 and <=0775)
dpkg-deb: building package `awcommon-server' in `../awcommon-server_10.80-13_i386.deb'.
dh_builddeb: command returned error code 512
make: *** [binary-arch] Error 1
        find AWCommon-server-10.80 -type d -exec chmod 755 {} ;
find: AWCommon-server-10.80: No such file or directory
        rm -rf AWCommon-server-10.80

---

### Post by leif3d on 2006-09-28
If anyone is interested, I solved the Mental Ray not rendering problem by creating a "tmp" folder in "usr" and giving it read and write permissions. I also gave this permission to all "aw" folders and "var" folders...now mental ray workd fine.

---

### Post by leif3d on 2006-09-28
NEW PROBLEM! Fcheck wont load images...I can get the application to run fine...but it wont display anything...anyone out there!](*,)

---

### Post by tempo500 on 2006-09-29
anybody having problems switching the viewports from fullscreen to a 4 pane view with the spacebar? i have to hit it really fast, so it only works every 10 time... + how do i link the libsoundfile corectly? thanx phil

---

### Post by uno_the_great on 2006-09-30
Great walkthrough! I used it to install maya 8 without any problems what so ever. It runs great so far, without any issues.

---

### Post by leif3d on 2006-10-06
Just so everyone knows!!!

Do not upgrade Driver 8762 If you have an Nvidia Card...the new drivers do not work well with Fcheck!...only use drivers 8762!

---

### Post by jujoje on 2006-10-07
I'm using the new beta drivers (1.0-9625) and fcheck is running fine for me, so maybe it's not related to the drivers. 

However, in edgy the swatches in hypershade become corrupted if you scroll them up or down. Relatively easy to work around (open and close the attribute editor), and they refresh, but it is relatively annoying.

---

### Post by v8YKxgHe on 2006-10-08
Hey,

I'm having some trouble installing Maya 8. I convert all the packages to .deb files and install them fine - but when I type "maya" in terminal i get "command not found" - there is no trace of any Maya files on my Ubuntu install, even though I did Install it. 

Any help would be great as I can then be free of Windows for ever!

---

### Post by v8YKxgHe on 2006-10-08
Now I'm getting this error:

```
alex@alex-ubuntu:~/Maya-install$ maya
*** Fatal Error: Failed creating directory: /home/alex/maya
Maya could not create the necessary startup directories.
Please check for sufficient disk space and necessary write permissions.
```

I'm so close! someone please help =)

Edit: Fixed it by removing the maya link that was broken in my home folder. Now Maya loads but it looks HORRIBLE, is it suppose to be like that?

---

### Post by jujoje on 2006-10-08
If you mean the lovely ugly bold fonts and the boxy grey menus and stuff, I'm afraid that it is meant to look like that. I did look into this a while back and it's apparently due to Maya using a custom version of an old library for the rendering the menus and fonts and stuff. Was a while ago when I looked into it, and there were a couple of things what were meant to fix it and force maya to use a more up-to-date library, but I couldn't get them working.

---

### Post by v8YKxgHe on 2006-10-08
oh right that sucks, I hope they make a native GTK for the next version, but now Autodesk took over I doubt it!

Does anyone know why I can't use the Mouse navigation controls aswell, like the ALT combinations.

---

### Post by jujoje on 2006-10-08
Had a look into the font issue, and it might be possible to make the fonts look a bit better (although the windows will look the same), by changing the maya scheme.

Here's what the manual has to say:

> 
(Linux) Changing system font display settings

You cannot edit the font display in Maya Linux using the system font settings.

Workaround

You can edit the MayaScheme file in /usr/aw/maya/app-defaults/ to modify the additional X resources used by Maya to change the system font display settings. This file is searched in the following location order:

$HOME/app-defaults/MayaScheme

/usr/lib/X11/app-defaults/MayaScheme

$MAYA_LOCATION/app-defaults/MayaScheme

To list available fonts, use the xlsfonts command. Alternatively, you can use the xfontsel command to generate a font string.

See also “Using the MayaScheme file to set fonts, font sizes, and colors” in the Linux chapter of the Installation and Licensing guide.



The file appears to be located in /usr/aw/maya8.0/app-default/MayaScheme so I guess that's the one that should be changed. I'm not sure how fonts work but at the moment the entery in the MayaScheme file looks like this:

> -*-helvetica-bold-r-normal-*-17-*-*-*-*-*-iso8859-1

I'm really not sure what all the * marks are for and am unsure how to go about changing it, particularly since the fonts listed by the xlsfonts command are listed like this:

> -urw-nimbus mono l-bold-o-normal--0-0-0-0-p-0-iso8859-1 

Could someone point me in this right direction on this? It'd be really good to get maya to use some nice fonts.

---

### Post by jujoje on 2006-10-08
Had a quick play with it. It still ain't pretty, but a lot better than is was before. Basically what you want to do is:

1) Backup the original file:

```
sudo cp /usr/aw/maya8.0/app-defaults/MayaScheme /usr/aw/maya8.0/app-defaults/MayaScheme.back
```

2) Open the font selector tool:

```
xfontsel
```

3) Open the MayaScheme files:

```
gksudo gedit /usr/aw/maya8.0/app-defaults/MayaScheme
```

4) Look at the MayaScheme file and the xfontsel windows and generate the code for the fonts that you want to use and paste them into the MayaScheme file.

That's all there is to it. Can be kinda fiddly since some fonts don't support some functions and certainly none of the fonts are pretty. I've attached a screenshot and my MayaScheme file. If anyone comes up with better looking fonts could they post their MayaScheme file.

[I added .zip to the MayaScheme file, since I couldn'y upload it as it was. Just get rid of the extention.]

---

### Post by luap56 on 2006-10-10
hi i have just installed maya and i keep getting this problem when i go to open maya in the terminal *****@****:~#maya it wont open but when i open it like this *****@****:~#/usr/aw/maya8.0/bin/maya.bin
 it will open but then this is the real problem it comes up with a box that has a line that you can click and a little black box:confused:  i will send a pic so if any one out there know what there doing plz make a post ty

---

### Post by v8YKxgHe on 2006-10-12
Which one is the font size then out of this?

```
-bitstream-bitstream vera sans-medium-r-normal--17-120-100-100-p-0-iso8859-15
```

Thats the exact font I want ( It looks great ) but the font is huge. Also I have found out how to change the main UI color with this:

```
*basicBackground: #373737
Maya*Background: #373737
```

in the MayaScheme file

---

### Post by ilbozo on 2006-10-16
Today i installed Maya 8 on my edgy distribution. (Absolutely standard/updated with no other fonts installed except for standard windows ttf fonts).
Maya now has no more huge font!!!

---

### Post by ilbozo on 2006-10-17
Today i updated my edgy and maya turned back to bad fonts...

---

### Post by apoclypse on 2006-10-25
For some reason flexlm doesn't seemto recognize the hostid and is giving me errors when I try to start maya. It keeps asking for the license file eventhough its already in the /var/flexlm folder and the file worked perfectly in dapper. Any ideas?

---

### Post by labradorg13 on 2006-10-26
thanks for this all information....

---

### Post by leif3d on 2006-10-28
> **apoclypse said:**
> For some reason flexlm doesn't seemto recognize the hostid and is giving me errors when I try to start maya. It keeps asking for the license file eventhough its already in the /var/flexlm folder and the file worked perfectly in dapper. Any ideas?

Enable executing rights on the folder and file.

---

### Post by leif3d on 2006-10-28
I updated to Edgy and the bad fonts problem happened. Maya also got very buggy with the new drivers...to the point where it's unworkable. This sucks...

---

### Post by iyeo on 2006-11-08
Ok, I had to reinstall this with a fresh install of edgy and there were some complications.  First, I was getting an error about libXm.so.2.  You need the 32bit version of it if you're running 64bit.  The file is in the lesstif2 package.  Download it.  Open the package with the archive manager and extract out libXm.so.2 and 2.0.1 into /usr/lib32/.  You probably already have 64bit versions in /usr/lib, but apparently they don't work for some function in installKey.

For those of you having problems with the license install, you need to run /aw/COM/bin/getid to get the host address (ethernet address) of the machine you're trying to install this on, copy that address in the aw.dat file, take the aw.dat file to a windows box (or dos), then run "aw_keygen aw.dat" from the prompt which will change the series of #s preceeding the host id.  Copy this file into /var/flexlm/ on your linux box and maya should work.  There's a link in the forums to fix the fonts so they're not as horrible, but I can't remember exactly where.

---

### Post by iyeo on 2006-11-08
The link for fixing fonts is on the page before this.  I finally have maya8_x64 running on edgy_x64 with a nice looking ui with mental ray fully working.  Mine seems to even run fine (minus some transparent menu bars) with beryl/emerald running (so with compositing on) so no need to create different sessions.  Compared to 3DS Max 8/Mental Ray on windows on the same box, render times are nearly identical.  If I can switch to Maya from 3DS, no need for windows!

---

### Post by jujoje on 2006-11-10
iyeo,

I was wondering if you could tell me how you've got beryl working with maya. I'm running beryl with AIGLX on the new nvidia drivers and everytime I press space and bring up the hotbox my computer hard locks and I have to hit the reset switch.  

Any information relating to how you set up beryl or tweaked maya to work with it would be appreciated. It's kinda anoying to have to switch between beryl and metacity.

---

### Post by gu1tarfreak on 2006-11-11
when i put in the first code, it gives me

E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?

---

### Post by jujoje on 2006-11-11
You need run the command as root, so the command should be:

sudo apt-get install csh alien

Then just enter your password and it start downloading and installing the files.

---

### Post by iyeo on 2006-11-19
I actually do switch from beryl to metacity when I run maya.  Besides the spacebar locking up thing you noticed, I also get transparency on the time slider and some of the windows (like the render window).  I run maya fullscreen so I don't really need cool transparency for my window frames.  I do find the lack of Alt-Tab annoying.

I did encounter another oddity recently.  I don't get an option for high quality rendering on the shading panel.  Obviously, I can render stuff in HQ, but I can't view it in the panel in HQ.  I have no idea where to even begin looking for that one.  Google wasn't very helpful, nor was Maya help.  Anyone?

---

### Post by jujoje on 2006-11-20
Thanks for reply on maya & beryl. I'm hoping that sometime beryl and maya will actually work properly togther. It's certainly got a lot better than it used to be with compiz (which was pretty much load maya and watch it crash :)

Getting the high quality shading should be straightforward:
[INDENT]1) Make sure the viewport is in shaded mode (press 5 on the viewport or go *shading->smooth shade all*).
2) In the viewport menu go *renderer->high quality rendering*
3) To turn textures on go *shading->hardware texturing*[/INDENT]
This applies to maya 8.0. Seems autodesk felt like moving some of the options around just to confuse people :) 

You can also enable shadows and stuff should you want to by turning on *lighting ->use all lights* and then going *lighting->shadows*. Which is nice in theory but will most likely cause your graphics card to keel over if the scene is at all complex.

---

### Post by presdec on 2006-11-20
the getid gives me ```
localhost bin]$ ./getid 
lmutil - Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""
```

a little more searching revealed that the hostid is 000000.

My windows HOSTID though is a much different number. what do i do?

---

### Post by HEMOglobina on 2006-11-22
After following the tutorial, I tried to run maya and got the following error:
```
/aw/maya7.0/bin/maya.bin: /aw/maya7.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```
Is there a way to fix this or is my maya broken forever? :)
Thank you for your help,
HEMOglobina

---

### Post by J-Rod on 2006-11-23
do you have GCC installed?

---

### Post by tempo500 on 2006-11-24
does anyone have experience with DrQueue? i could use some help with one last remaining issue... slave has problems finding the drqueue script... master render fine. thanks, philip[http://www.ubuntuforums.org/showthread.php?t=305994]("http://www.ubuntuforums.org/showthread.php?t=305994")

---

### Post by HEMOglobina on 2006-11-24
> **J-Rod said:**
> do you have GCC installed?
Hello J-Rod. Yes I do, but when I typed the following command
```
gcc -v
```
I got the following result
```
Using built-in specs.
Target: i486-linux-gnu
Configured with: ../src/configure -v --enable-languages=c,c++,fortran,objc,obj-c++,treelang --prefix=/usr --enable-shared --with-system-zlib --libexecdir=/usr/lib --without-included-gettext --enable-threads=posix --enable-nls --program-suffix=-4.1 --enable-__cxa_atexit --enable-clocale=gnu --enable-libstdcxx-debug --enable-mpfr --enable-checking=release i486-linux-gnu
Thread model: posix
gcc version 4.1.2 20060928 (prerelease) (Ubuntu 4.1.1-13ubuntu5)

```

From what I can tell, my GCC is older than the one needed by Maya?
I tried to get a newer version by doing:
```
sudo apt-get install gcc
```
But the answer was that I already had the newest package.
What would you suggest? Please remember that I'm very new to linux so please "speak slowly" :)
Thank you very much for your help,
HEMOglobina

---

### Post by WiredAnim on 2006-11-27
I'm following the instructions above trying to install Maya 7 on Ubuntu but I can't get past converting the rpm to deb file it goes fine for awhile but it stops for a minute and then spits out 

"dpkg-shlibdeps.orig: warning: could not find any packages for libc.so.6 dpkg-shlibdeps.orig: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)dpkg-shlibdeps.orig: warning: could not find any packages for libdl.so.2dpkg-shlibdeps.orig: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps.orig: " 


and that goes on for awhlie and it ends like 


"library libc (soname 6, path libc.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture powerpc does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
        find Maya8_0-8.0 -type d -exec chmod 755 {} ;
find: Maya8_0-8.0: No such file or directory
        rm -rf Maya8_0-8.0"

I don't know what to do I have tried installing the files listed that are missing but most of them I can't find.  Can anyone help??? 

Wired

---

### Post by phyllit on 2006-12-01
hi everyone!

i managed to install maya 7 and it seems to work just fine. i fixed the cursor problem with your given suggestions, but there is still one big problem: mental ray doesnt work at all. i corrected the first line of the maya.rayrc file to have only one "/", but that did't help...

when i switch the render globals to mental ray and the hit "render current frame", maya just closes down...

i also have to say, that i'm a complete newbie to linux, so i would appreciate any ideas you might have to solve this problem...

thx

---

### Post by J-Rod on 2006-12-06
sudo ln -s /usr/aw /aw

I got a little antsy when I reinstalled Ubuntu/Maya, and I forgot to make the link before installing the converted .deb packages. I am now getting an error that i have seen others get, what I think I need to do is destroy the old link, uninstall all three packages and reinstall in the proper order. Can anyone enlighten me as to what I need to do to get rid of the link that was made with this command?

Meh, disregard this, I don't think I installed csh. :)

---

### Post by tyfius on 2006-12-12
> **iyeo said:**
> Nevermind about chkconfig.  I got Maya 8 x64 working with ubuntu 6.06 x64.  The font rendering is a bit funky, but it works.  Thank you all.
How did you get past this ?
I've looked at different ways to install chkconfig, but none worked.

---

### Post by tempo500 on 2006-12-12
forget chkconfig, its a warning not an error

---

### Post by tyfius on 2006-12-14
It seems so.
I think it installed everything pretty well, I can create cubes and move them around. Only the combination with Beryl is a bit forked, but that's something I'll look into next week, when I have the time.

---

### Post by sargosis on 2006-12-15
hey, i can't seem to find anything about my particular error in this forum. I'm trying to install maya from this tutorial and i keep getting this error when i try to run maya:

apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64

i have virtually no linux experience, so i have no idea what this is or what it's about. if you could help me out i'd be greatful.

---

### Post by pgatrick on 2006-12-15
I really have no clue, but I'm going to guess you're on a 64bit system and running the 32bit maya? Maybe do "linux32 maya"? If you've already done that, then I don't kow..

---

### Post by pgatrick on 2006-12-15
> **WiredAnim said:**
> I'm following the instructions above trying to install Maya 7 on Ubuntu but I can't get past converting the rpm to deb file it goes fine for awhile but it stops for a minute and then spits out 

"dpkg-shlibdeps.orig: warning: could not find any packages for libc.so.6 dpkg-shlibdeps.orig: warning: unable to find dependency information for shared library libc (soname 6, path libc.so.6, dependency field Depends)dpkg-shlibdeps.orig: warning: could not find any packages for libdl.so.2dpkg-shlibdeps.orig: warning: unable to find dependency information for shared library libdl (soname 2, path libdl.so.2, dependency field Depends)
dpkg-shlibdeps.orig: " 


and that goes on for awhlie and it ends like 


"library libc (soname 6, path libc.so.6, dependency field Depends)
dh_gencontrol
dpkg-gencontrol: error: current build architecture powerpc does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
        find Maya8_0-8.0 -type d -exec chmod 755 {} ;
find: Maya8_0-8.0: No such file or directory
        rm -rf Maya8_0-8.0"

I don't know what to do I have tried installing the files listed that are missing but most of them I can't find.  Can anyone help??? 

Wired

I don't know about the first problem, but the second one is easy enough, it can't make the debs, but the rpms are unpacked already, just go dig the files out of the folder it created and install them by hand.

---

### Post by sargosis on 2006-12-16
actually, i've got a 64 bit system and i'm trying to run the 64 bit maya. i'm still completely new to linux so "simply installing the 32 bit version" is pretty much beyond my capabilities.

---

### Post by pgatrick on 2006-12-16
> **sargosis said:**
> actually, i've got a 64 bit system and i'm trying to run the 64 bit maya. i'm still completely new to linux so "simply installing the 32 bit version" is pretty much beyond my capabilities.
In that case I really have no idea :-| I'm about to be getting 64bit maya though, I'll see if I get a similar error.. :-k

---

### Post by Nosiburger on 2006-12-16
> **HEMOglobina said:**
> After following the tutorial, I tried to run maya and got the following error:
```
/aw/maya7.0/bin/maya.bin: /aw/maya7.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```
Is there a way to fix this or is my maya broken forever? :)
Thank you for your help,
HEMOglobina

I have the same problem........](*,)

---

### Post by snovak on 2006-12-19
I too have the same error.. anyone with a fix would be greatly appreciated.

---

### Post by 3dimentia on 2006-12-24
I have an interesting problem.  I have maya 8 installed and working.  It is an odd error.  Basically, I cannot open up my synaptic package monitor or update anymore, because the awcommon_10.80-13_i386.deb file, which was converted just fine with alien, seems to have a problem.  It will not install correctly, and I can't remove it without re installing it (or so the package manager tells me).  When I try to re install it with dpkg it spits this out:


```
Ubuntu:~/Desktop/maya_convert$ sudo dpkg -i awcommon_10.80-13_i386.deb
(Reading database ... 117677 files and directories currently installed.)
Preparing to replace awcommon 10.80-13 (using awcommon_10.80-13_i386.deb) ...
Unpacking replacement awcommon ...
/usr/bin/test: invalid integer `upgrade'
exit: 26: Illegal number: -0
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/usr/bin/test: invalid integer `failed-upgrade'
exit: 26: Illegal number: -0
dpkg: error processing awcommon_10.80-13_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
/usr/bin/test: invalid integer `abort-upgrade'
exit: 26: Illegal number: -0
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon_10.80-13_i386.deb

```


any thoughts or suggestions on how to get this silly thing working correctly or fix the file?  It doesn't spit out any errors when it creates the DEB so im not really sure whats going on.

Thanks in advance

---

### Post by 3dimentia on 2006-12-24
I actually, after a bit more playing around (thought I exhausted all my options there!) managed to get rid of the package and re install it.  I had to manually remove the info from /var/lib/dpkg/status for awcommon, and the purged it.  After that, the re install of it worked like a charm.  I find it strange that it wouldn't even let me re install the silly thing!  Oh well alls well that ends well, and my comp is HAPPY SLAPPY with ubuntu!

thx!

---

### Post by v8YKxgHe on 2006-12-24
Hum I've got a problem with aw.dat - when I start Maya it says there is no license found, then if I go to choose it from a location and select 'var/flexlm/aw.dat' it says:

> The file contains invalid data. ERROR: FEATURE MayaUnltd has invalid host identifier of 00508d9719dd. (line 1)

The license file works fine on Windows, but not on Ubuntu - why is this?

---

### Post by 3dimentia on 2006-12-24
probably cause ubuntu is seeing a different hardware address then your windows box is.  There are some utilities you can use in the aw/bin folder where you can check the hardware address.  I cant remember the name of it at the moment though.

cheers

---

### Post by v8YKxgHe on 2006-12-24
do you mean the mac address? If so it is the same as on my Windows PC.

---

### Post by DinoeL on 2006-12-25
If you get this error:
```
/aw/maya7.0/bin/maya.bin: /aw/maya7.0/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)
```

You need to link your libstdc++.so.5, and libgcc_s.so.1 into /usr/aw/maya/lib

```
 sudo ln -sf /usr/lib/libstdc++.so.5 /usr/aw/maya/lib/libstdc++.so.5
sudo ln -sf /lib/libgcc_s.so.1 /usr/aw/maya/lib/libgcc_s.so.1
```

Worked for me.

---

### Post by 3dimentia on 2006-12-25
> **AlexC_ said:**
> do you mean the mac address? If so it is the same as on my Windows PC.

Yah i did mean your mac address.  I thought the same thing, but on my machine in windows, vs machine in ubuntu, its using different mac addresses ( I assume windows/maya is just fine using say a wireless, where as ubuntu and maya were looking at the ethernet card).  

I didn't know for sure if this would fix your problem, but it is what my problem was (with that same error) and now everything works just dandy.

cheers

---

### Post by v8YKxgHe on 2006-12-25
Ok so I shall fiddle around with the mac address. Could you give an example of the aw.dat file please? I think I've played around with it to much now and want to check if it's all correct apart from the mac address.

Merry Christmas!

---

### Post by 3dimentia on 2006-12-25
FEATURE MayaUnltd sgiawd 8.000 permanent uncounted XXXXXXXXXXXX \
	HOSTID=XXXXXXXXXXXX

obviously I removed my info, but basic aw.dat file.  

To get the right host ID:

open up a terminal
cd to aw/COM/bin
type ./lmhostid press enter.

It'll spit out the host id that maya/linux want and away you go.

cheers m8

---

### Post by v8YKxgHe on 2006-12-26
Wooohoo! Thanks so much 3dimentia, now I can be Windows free :mrgreen:

---

### Post by v8YKxgHe on 2006-12-29
Hey,

I'm having some trouble with the Maya open/save dialog, see the attachments. In the Maya dialog all I can see is 2 distorted items, yet in the Nautilus screenshot that is the real contents of the dir I am looking in. Why is it doing this? 

Please, Autodesk make a GTK/QT version!! :p

---

### Post by v8YKxgHe on 2006-12-31
anyone?

---

### Post by v8YKxgHe on 2006-12-31
Ahh, the problem was because of my font settings, here is my MayaScheme file that works perfectly and looks good.

```
*extraLargeBoldLabelFont:          -*-helvetica-medium-r-normal-*-14-*-*-*-*-*-iso8859-1
*largeBoldLabelFont:               -*-lucida-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*boldLabelFont:                    -*-helvetica-medium-r-normal-*-13-*-*-*-*-*-iso8859-1
*smallBoldLabelFont:               -*-helvetica-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*tinyBoldLabelFont:                -*-helvetica-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*plainLabelFont:                   -*-lucida-medium-r-normal-*-12-*-*-*-*-*-iso8859-1
*smallPlainLabelFont:              -*-lucida-medium-r-normal-*-10-*-*-*-*-*-iso8859-1
*FontList:                         -*-lucida-medium-r-normal-*-12-*-*-*-*-*-iso8859-1
*obliqueLabelFont:                 -*-helvetica-bold-o-normal-*-12-*-*-*-*-*-iso8859-1
*smallObliqueLabelFont:            -*-helvetica-bold-o-normal-*-12-*-*-*-*-*-iso8859-1
*fixedWidthFont:                   -*-clean-medium-r-normal--12-*-*-*-*-*-iso8859-1
*smallFixedWidthFont:              -*-clean-medium-r-normal--12-*-*-*-*-*-*-*
*XmLabel.fontList:                 -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*XmLabelGadget.fontList:           -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*XmScale*fontList:                 -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*SgColumn.fontList:                -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*XmRowColumn.OptionLabel.fontList: -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*Label*font:                       -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*LabelFont:                        -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*
*Label*fontlist:                   -*-lucida-bold-r-normal-*-10-*-*-*-*-*-*-*

*basicBackground:            #e7e7e7
Maya*Background:             #e7e7e7
*textForeground:             #000000
*textFieldBackground:        #eeeeee
*readOnlyBackground:         #bdbdbd
*buttonBackground:           #bdbdbd
*scrollBarTroughColor:       #bdbdbd
*scrollBarControlBackground: #bdbdbd
*indicatorBackground:        #cbcbcb
*radioColor:                 #0000ff
*checkColor:                 #ff0000
*blueSelectBackgroundColor1: #3884c4
*blueSelectBackgroundColor2: #81a7c1
*drawingAreaBackground:      #90abb1
*drawingAreaContrastColor1:  #b86b6b
*drawingAreaContrastColor2:  #7894bf
*drawingAreaContrastColor3:  #7ba988
*drawingAreaContrastColor4:  #ab7ec8
*scrolledListBackground:     #bdbdbd
*textBackground:             #b5b5b5
*highlightColor1:            #ff0000
*highlightColor2:	#0000ff
*highlightColor3:	#00ff00
*highlightColor4:	#a01ef0
*highlightColor5:	#ffa500
*highlightColor6:	#00ffff
*highlightColor7:	#ff00ff
*HighlightColor8:	#ffff00
*wMBackground:	#aaaaaa
*wMForeground:	#000000
*wMActiveBackground:	#c6c1aa
*wMActiveForeground:	#000000
*textSelectedBackground:	#e6e6e6
*textSelectedForeground:	#000000
*indicatorLightColor:	#ffff00
*selectFillColor:	#ffff00
*redColor:	#ff0000
*orangeColor:	#ff7e00
*yellowColor:	#ffff00
*greenColor:	#4fe44f
*blueColor:	#0000ff
*brownColor:	#743f3f
*purpleColor:	#ae00ff
*errorColor:	#ff0000
*warningColor:	#0000ff
*informationColor:	#00ff00
*alternateBackground1:	#c1adad
*alternateBackground2:	#a7b7a7
*alternateBackground3:	#bbbbcd
*alternateBackground4:	#9fbfbf
*alternateBackground5:	#87aaca
*alternateBackground6:	#d1d1c9
*disabledTextForeground:	#aaaaaa
*layerAdjustmentTextForeground:	#e56929
*lightRadioFillColor:	#9e9edc
*disabledCheckColor:	#dc9e9e

```

---

### Post by tempo500 on 2007-01-14
did anybody notice a reproducable crash in maya when one uses the hotkey "w"? holding this button and clicking the left mouse button gives one a marking menu with the transformation axis, global, local etc... the same with the rotate and scale tool. so using this marking menu and releasing the keyboard before one releases the mouse button , produceses a crash. first i blamed all on ubuntu, installed fedora, - the same bug. then i thought it must be the crappy ati drivers... well...the same on ubuntu/nvidia. 

the next thing i hate is that switching a viewport to fullscreen with the spacebar. on an ati this works, lets say 50 to 50. on a nvidia 90 to 10, besides the cheap nvidia 5200 can display the menu much faster than a firegl x1.

maybe someone of you have insight to this.

---

### Post by tauil on 2007-01-14
tempo500,

Nvdia do supports on Linux so it works better than ATI. 

I think that ATI video boards are really better than Nvidia, but as I am a Linux user, I would buy a Nvidia board. :-D 

I've tried to use W key + LMB and it worked just fine here. I'm using Maya 7 running on an Ubuntu Dapper (6.06) with Fluxbox 1.0 rc2. Probably it is a problem of yours video card. 8) 

I'm having problem using Mental Ray of Maya Software Render. I dont Know what happens but the log tells me that the Erro: :-? 

-------------------------------------------
maya encountered a fatal error

Signal: 11 (Unknown Signal)
------------------------------------------- 

I've found some people that ad the same Error but there is no solution for it, if you do know an answare, plz help me! :confused: 

Best Regards!
Tauil

---

### Post by jujoje on 2007-01-15
I can confirm that the w+LMB does indeed crash maya, although this is on Debain not Ubuntu. I guess it might be common to all versions of linux if it also happens in Fedora. Looks like it must be a bug with maya 8.0.  (For what it's worth my graphics card is a GeForce 7900)

Tauil:
From what I've read Signal 11 is just a catch all error message: it doesn't indicate that something specific has gone wrong, just that something has gone wrong making the programme crash. Do you get any related errors in the script editor when maya boots up? When exactly does it occur?

---

### Post by tempo500 on 2007-01-15
interresting that the w+lmb works on maya7... mental ray works just fine with maya 8. dont know anything about signal11...sorry... i recently installed the latest ati drivers and used the aticonfig wich has a few options for the xorg.conf file. the maya profile is interresting + the opengl overlays. just my gnome-profile wont start with opengl-overlays on. so it seems that i am running a workstation card with video overlay planes... wasnt  that the reason that i got myself a firegl?:-k  anyway... i should get a new computer this week... and guess.... its not going to be an ati... phil

---

### Post by tauil on 2007-01-15
jujoje,

Check out my full error report trying to render my scene on Linux:

tauil@tux:~$ export MAYA_DEBUG_ENABLE_CRASH_REPORTING=1 

tauil@tux:~$ Render /media/hda5/maya/projects/default/scenes/_Freela_Fabio/caixaAtash/caixaRenderFinal.mb

Starting "/usr/aw/maya7.0/bin/maya"

File read in 1 seconds.
Result: /media/hda5/maya/projects/default/scenes/_Freela_Fabio/caixaAtash/caixaRenderFinal.mb
Total Elapsed Time Since Start Of Maya (hh:mm:ss): 00:00:06
====================================
Resource Usage At Start Of Rendering
====================================
     774        Page faults
  93.031 Mb     Peak total size(Estimated)
   6.727 Mb     Peak arena size
====================================
  37.559 Mb     Heap
   0.938 Mb     Data Blocks
   2.555 Mb     Arrays
   0.375 Mb     Transforms
   0.125 Mb     Keys
   2.734 Mb     MEL
====================================
A default light has been created, modify defaultRenderGlobals.enableDefaultLight to change this behavior.
Automatic near/far clipping values: 20.8551, 54.8266.
Starting Rendering /media/hda5/maya/projects/TesteAlpha.png.
Constructing shading groups.

Rendering current frame.
Warning: Texture file E:/caixaADMA.jpg doesn't exist, node file1
Warning: Texture file E:/caixa.jpg doesn't exist, node file2
Frame triangle count: 2740958

====================================
Resource Usage At End Of Frame
====================================
      23        Page faults
 863.434 Mb     Peak total size(Estimated)
 708.617 Mb     Peak arena size
====================================
 105.817 Mb     Heap
 701.891 Mb     Render Cache
   0.375 Mb     Transforms
   2.555 Mb     Arrays
   0.938 Mb     Data Blocks
   0.065 Mb     Render Geometry Arena
   2.734 Mb     MEL
   0.125 Mb     Keys
====================================
Postprocessing rendering result.

maya encountered a fatal error

Signal: 11 (Unknown Signal)
Stack trace:
  [0xffffe420]
  bcopy
  FLbufferedWrite
  FLwrite
  FLbgnput
  FLbgnwgroup
  /usr/aw/maya7.0/lib/libImage.so [0xb5e7204e]
  ILopen
  TiffImageFile::open(char const*, char const*)
  TrenderFrame::postProcess()
  TrenderFrame::cleanUp(bool)
  TrenderFrame::render(TrenderCamera&, TgeoManager*, Trect&, bool, Trect&, Tstring&, Tstring&, Tstring&, Tstring&, bool, bool, Tstring&, TcameraTypes::TfieldType, bool, bool, bool, short)
  TrenderFrames::render(TdagPath&, bool)
  TrenderItemCmd::doIt()
  renderBatchMode(Tmodel*, TrenderGlobalsOverrides&)
  TrenderAction::doCommand(TargList&)
  Mel_Command_Dispatch(SphNode*)
  node_exec
  sophia_call_executable
  SophiaExecutable::evaluate(void*)
  TcommandEngine::executeCommand(SophiaExecutable*, void*)
  TelfEvalCmd::doCommand(TargList&)
  Mel_Command_Dispatch(SphNode*)
  node_exec
  f_function_entry_node
  node_exec
  sophia_call_executable
  SophiaExecutable::evaluate(void*)
  TcommandEngine::executeCommand(SophiaExecutable*, void*)
  TelfEvalCmd::doCommand(TargList&)

Result: /media/hda5/maya/projects/default/scenes/_Freela_Fabio/caixaAtash/caixaRenderFinal.ma
Attempting to save in
        /usr/tmp/tauil.20070115.1224.ma
Writing crash report in /usr/tmp/tauil.20070115.1224.crash
tauil@tux:~$

---

### Post by tempo500 on 2007-01-15
sorry, i dont know... if you can render a simple qube with mr - try minimizing your scene, file/optimize scene, reduce the features in the renderglobal, shading nodes, geometry. the last resort i can think of is exporting your selected objects to ma. phil

---

### Post by apoclypse on 2007-01-21
> **3dimentia said:**
> FEATURE MayaUnltd sgiawd 8.000 permanent uncounted XXXXXXXXXXXX \
	HOSTID=XXXXXXXXXXXX

obviously I removed my info, but basic aw.dat file.  

To get the right host ID:

open up a terminal
cd to aw/COM/bin
type ./lmhostid press enter.

It'll spit out the host id that maya/linux want and away you go.

cheers m8


I wish that were the case but everytime I run that command or getid I get this 

```
lmutil - Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""

```

There have been acouple of people here with the same issue and yet no fix. Is there something we are doing wrong? Someone said that thir should be execute rights on the folder and file, can they elaborate. I you mean execute rights on the aw,dat file, then that won't o any good cause flexlm itself doesn't seem to be reading a hostid. I didn't have this problem at all in Dapper.

---

### Post by EvanPMeth on 2007-02-07
I found this tutorial on installing maya 8 on kubuntu hope it helps!

[http://www.wouz.dk/alias-maya-misc/maya-8-installation-under-kubuntu-6061-lts/]("http://www.wouz.dk/alias-maya-misc/maya-8-installation-under-kubuntu-6061-lts/")

-EvanPMeth

---

### Post by kreme-karamel on 2007-02-08
I tried to install Maya8.5-x64  on my system (an AMD Quad Opetron running Edgy 6.10) following the procedure suggested here and I get the following error message:

```
apcw: error while loading shared libraries: 
```

Like other users in this thread, despite diligently following the instructions and installing csh,  typing "maya" would not load the application. I figured out that this is because the symbolic links in /usr/bin were pointing to /autodesk/maya8.5-x64/bin/<application> (fckeck, maya, imgcvt, Render) whereas the installer placed the autodesk directory under /usr/autodesk.

Rather than moving the autodesk directory to root and risk breaking something, I added a symbolic link in root with:
 
```
sudo ln -s /usr/autodesk  /autodesk
```

That took care of the launch problem, however now I'm getting the following error:

> apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64

Operating under the assumption that perhaps the libstdc++.so.6 library packaged with Maya was incompatible with my system, I linked maya's to the system's with: 

```
sudo ln -s /usr/lib/libstdc++.so.6.0.8 /usr/aw/maya/lib/libstdc++.so.6.0.6 
```

This generated a different error message:
> 
usr/aw/maya8.5/lib/libgcc_s.so.1: version `GCC_4.2.0' not found (required by /usr/lib/libstdc++.so.6)

I figured, I'd relink libgcc_s.so.1 as above with:

```
sudo ln -s /lib/libgcc_s.so.1  /usr/aw/maya/lib/libgcc_.so.1 
```

This brought me right back where I started from with:

> apcw: error while loading shared libraries: libstdc++.so.6: wrong ELF class: ELFCLASS64

I'm stumped - any ideas?

---

### Post by kreme-karamel on 2007-02-08
On Autodesk's [ _site_]("http://www.alias.com/eng/support/maya/qualified_hardware/QUAL/maya_85_linux.html") it says:

 > Maya 8.54 was compiled using gcc 4.0.2.  on a RHEL 4 system. gcc 4.0.2 source code is available from [http://gcc.gnu.org/gcc-4.0/](http://gcc.gnu.org/gcc-4.0/)
The options to build the gcc 4.0.2. compiler used for Maya are:
     
gcc402 -v

 Using built-in specs.
 Target: x86_64-unknown-linux-gnu
 Configured with: ../gcc-4.0.2/configure --prefix=/opt/gcc402 --program-suffix=402  --enable-shared  --enable-threads=posix  --enable-checking=release  --with-system-zlib  --enable-__cxa_atexit  --disable-libunwind-exceptions  --enable-languages=c,c++ Thread model: posix gcc version 4.0.2
Plugin developers should use the same configuration.

Why in the world, then, is libstdc++.so.6 looking for gcc 4.2.0? Edgy's version of gcc on my machine is 4.1.2 so I should be covered for the above compile, no?

---

### Post by number_six on 2007-02-11
My problem has me buffaloed - Maya 8.0 - Installs just fine as per
the 7.0 instructions, but when I run it, the machine locks up,
still have cursor movement, but that is it.

So I tried it on my wife's machine.

Works fine, no problems.

My machine is a a dual PIII with 1gb ram
and ATI FireGl T2 video card.
(Using the fglrx drivers out of synaptic)
Running Edgy.

Wife's machine is an amd 64bit machine
but running 32 bit Ubuntu.
512Mb ram
Nvidia graphics card.

I originally had Maya 6.0, which ran under Dapper
with no issues. So out of curiosity,
I tried installing 6.0 under edgy
on this box. Same issue, machine
locks up, except I have cursor movement.

Any ideas?

---

### Post by vakont on 2007-02-25
Hello friends,

My Maya so far works correctly except two parts: The fonts and Mental Ray. The font list is completely empty, nore can I select any font to create curves or polygons on nurbs... generally anything. But that is not what interests me right now.

As a professional 3D Artist, my main concern is Mental Ray. I use various versions of it, but we still have projects on version 7 that we wish to keep that way. I also adore the memory management of Linux that can make a big difference.

Ok, I am trying to utilize Maya 7 on my laptop, which has:
Pentium Core 2 Duo 2.16GHz
2GB RAM
nVidia 7950, 512MB Video RAM
Ubuntu Edgy Eft (6.10)

I have added permissions in /usr/aw folder and I have created a full permission tmp folder. I also checked the maya.rayrc file and all the paths point correctly. Just to make sure that the permissions were not the issue, I sudo ran Maya, but I got the very same results:

```
// Error: (Mayatomr.Export) : mental ray startup failed with errors //
// Info (Mayatomr): Aborted //
// Error: (mental ray) : failed to load library /usr/aw/maya7.0/mentalray/lib/mayahair.so (original name {MAYABASE}/lib/mayahair.{DSO}): /usr/aw/maya7.0/mentalray/lib/mayahair.so: undefined symbol: mi_db_access //
// Error: (mental ray) : failed to load library /usr/aw/maya7.0/mentalray/lib/subsurface.so (original name {MAYABASE}/lib/subsurface.{DSO}): /usr/aw/maya7.0/mentalray/lib/subsurface.so: undefined symbol: mi_img_get_depth //
// Error: (mental ray) : failed to load library /usr/aw/maya7.0/mentalray/lib/mayabase.so (original name {MAYABASE}/lib/mayabase.{DSO}): /usr/aw/maya7.0/mentalray/lib/mayabase.so: undefined symbol: mi_shaderstate_get //
```

Are there any suggestions on this?

Thanx for your time!

---

### Post by LorenzoChomp on 2007-02-25
vakont, I've solved that problem just creating an empty file named Mayatomr.sog in the plugings folder. The exact path on my system is :

/usr/aw/maya7.0/bin/plug-ins/Mayatomr.sog

Just create it in complete blank (i.e. using Vim), and then launch Maya again. Looks like when Maya finds this file empty, then it just fills the file with default settings.

By the way, also make sure of having the dir /usr/tmp with read/write permmisions for your user.

Almost forgot... Nice laptop!!

---

### Post by kobalatse on 2007-02-25
after installing nvidia drivers on my system the fontpaths are apperently mangled. Maya worked fine before that but I don't have a clue how to set font paths

sounds simple enough, how to go about it

---

### Post by outtony on 2007-03-01
if you have maya 8.5, you should do this before

sudo ln -s /usr/autodesk  /autodesk

:guitar:

---

### Post by gga73 on 2007-03-01
Running any version of maya, I get the problem that floating subwindows (outliner, hypergraph, etc) are incorrectly handled and loose focus, whenever you click on the main maya window.

Also, minimizing maya does not minimize maya's subwindows.  This looks as maya's subwindows are being created incorrectly and not as child of the main maya window.

I know that there is an obscure fix for this in the .Xresources/.Xdefaults file (due to having worked at a company that had settings that fixed this), but I don't know what it is.

Does anyone know?

---

### Post by aphex_666 on 2007-03-04
.

---

### Post by aphex_666 on 2007-03-04
For the Signal 11 problem: 

Had the same problem with Debian Etch after upgrading some packages for the latest version of Beryl.
For me it seems as though it was caused by /usr/lib/libGL.so pointing to /usr/lib/nvidia/libGL.so.1.2.xlibmesa.
I removed that symlink and made a new one pointing /usr/lib/libGL.so to /usr/lib/libGL.so.1.0.8776.
Then Maya started ok again.

You can see the command issued below.

For problem with libstdc and GCC,
I deleted the symlink libstdc++.so.6 -> libstdc++.so.6.0.8
and replaced it with
libstdc++.so.6 -> libstdc++.so.6.0.7

This made the libstdc/GCC error go away for me. I found the libstdc++.so.6.0.7 on my Ubuntu machine in the lib directory and copied it over to my Debian Etch box.
This works amazingly, although I often have to remake the symlink after rebooting. 

-P 

websol:/usr/X11R6/lib# ls -la /usr/lib/ | grep libGL
lrwxrwxrwx   1 root     root           21 2007-01-14 02:15 libGLcore.so.1 -> libGLcore.so.1.0.8776
-rw-r--r--   1 root     root      8161228 2006-12-03 20:04 libGLcore.so.1.0.8776
-rw-r--r--   1 root     root        92120 2006-10-24 13:27 libGLEW.a
lrwxrwxrwx   1 root     root           16 2007-02-18 18:09 libGLEW.so -> libGLEW.so.1.3.4
lrwxrwxrwx   1 root     root           16 2007-02-18 18:09 libGLEW.so.1.3 -> libGLEW.so.1.3.4
-rw-r--r--   1 root     root       195624 2006-10-24 13:27 libGLEW.so.1.3.4
lrwxrwxrwx   1 root     root           37 2007-03-03 12:25 libGL.so -> /usr/lib/nvidia/libGL.so.1.2.xlibmesa
lrwxrwxrwx   1 root     root           17 2007-01-14 02:15 libGL.so.1 -> libGL.so.1.0.8776
-rw-r--r--   1 root     root       543724 2006-12-03 20:04 libGL.so.1.0.8776
-rw-r--r--   1 root     root       688008 2007-01-03 08:42 libGLU.a
lrwxrwxrwx   1 root     root           11 2007-02-14 16:32 libGLU.so -> libGLU.so.1
lrwxrwxrwx   1 root     root           20 2007-02-17 04:14 libGLU.so.1 -> libGLU.so.1.3.060501
-rw-r--r--   1 root     root       479244 2007-02-15 02:16 libGLU.so.1.3.060401
-rw-r--r--   1 root     root       519844 2007-01-03 08:42 libGLU.so.1.3.060501
websol:/usr/X11R6/lib# rm /usr/lib/libGL.so
websol:/usr/X11R6/lib# ln -s /usr/lib/libGL.so.1.0.8776 /usr/lib/libGL.so

---

### Post by aphex_666 on 2007-03-04
.

---

### Post by kiaran on 2007-03-25
3dimensia- after install Maya 8.5, synaptic package manager was throwing an error regarding the awcommon package, saying it had to be removed but couldn't find the package.

 Obvisously, synaptic is very important so I had to fix it. Your recommendation worked perfectly. I used sudo nano /var/lib/dpkg/status to open the file in root mode. Then I removed the section about the awcommon package and saved the file (ctrl+o).

Then I re-installed the awcommon_10.80-14_i386.deb (which I aliened from the rpm) and this time the installation worked perfectly and I can use the Maya help again!! Thanks for the advice, it really saved my ***. :)

---

### Post by tehquickness on 2007-03-29
Did anyone find an answer as to why  ./lmhostid can not see what the host id?
here is my output:

lmhostid - Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""

There must be a way to solve this problem. Is there a way to see what settings the lmhostid is checking? I would love to solve this problem as I really need this for architecture studio class.

---

### Post by mech7 on 2007-04-02
:) This works good for maya 8.5 the interface is damn ugly though under Linux:confused:

---

### Post by Engnome on 2007-04-08
> **mech7 said:**
> :) This works good for maya 8.5 the interface is damn ugly though under Linux:confused:

Yup, maya uses openmotif which doesn't blend very well with GNOME (havent tried kde)

Does anyone get the "The main window is black after a menu has been closed" It's very annoying to have to pan or rotate to get rid of the black artifacts.

---

### Post by dagooze on 2007-04-09
I got the same stupit window problem as gga73 described. 
The outliner, hypershade, ... always go away when working in the maya main window. Would be really kewl if some1 would come up with a solution for that so the child windows stay on top of the main window.

cheers

dagooze

---

### Post by tempo500 on 2007-04-09
i still haven't entirely got used to the window focus thing... but i got used to it and it has some benefits too... anyway... i put a shortcut on fullscreen and "always on top" which can be found under the program icon on the left side of the window bar. phil

---

### Post by dagooze on 2007-04-09
This On Top thing is a good thing that helps ... but I don't get it with this shortcut.
when I restart maya I always have to go to the outliner, hypershade for a new round to make em stay on to of the viewport/main window.

thx

dagoose

---

### Post by pgatrick on 2007-04-10
Anyone have a problem with window contents being all messed up after scrolling? Any ideas how to fix it? Other parts of the display are sort of scrambled as well.. :confused:

---

### Post by pgatrick on 2007-04-10
> **pgatrick said:**
> Anyone have a problem with window contents being all messed up after scrolling? Any ideas how to fix it? Other parts of the display are sort of scrambled as well.. :confused:

Nevermind I got it fixed. :D Just had to disable compositing in my xorg.conf. :)

---

### Post by affected on 2007-04-29
Anyone else have an issue where pressing space a number of times in quick succession crashes maya 7.0? This is easy to do by accident since sometimes maya does not respond when pressing space to switch between views. Wonder if there's anything to be done about it...

---

### Post by jujoje on 2007-04-29
> **affected said:**
> Anyone else have an issue where pressing space a number of times in quick succession crashes maya 7.0? This is easy to do by accident since sometimes maya does not respond when pressing space to switch between views. Wonder if there's anything to be done about it...

Have you got beryl or compiz enabled? With either of these pressing space will cause ubuntu to hard crash, although it should work fine if you disable desktop-effects\compiz temporarily. If your not using them I'm not sure what could be causing it.

On a related note has anyone found a workaround for the crash that occurs when you hold down one of the transform keys (qwer) to bring up the local/world transform menu? I found this also caused ubuntu to hard crash even without have desktop acceleration on (or installed). Seems like it's a bug with Maya since the same thing happens in SUSE 10.2, Fedora and Debian.

---

### Post by thedaemon on 2007-04-30
I don't have that crashing problem. I can bring up the menu just fine. Running Maya 8.5 and Feisty. Only problems I have so far is that the time slider doesn't get updated unless I click in its window.

---

### Post by ZombieAcademy on 2007-05-06
Thanks for the tutorial. Got Maya 8.5 working in Feisty just fine.
A few things that confused me that I will reiterate for anyone else in a similar situation:

- When installing the first package in the tutorial with dpkg you can safely **IGNORE the chkconfig warning.**

- To get camera movement working properly you must change the default "move window" hotkey in Ubuntu from ALT to something else. This is in System->Preferences->Windows. Then you must RESTART maya if it is already running. This one got me for a minute.

- In addition to the 'sudo ln -s /usr/aw /aw' before installing, **also run 'sudo ln -s /usr/autodesk /autodesk'**
[update: apparently this is a necessary step, thanks dagooze!]

- You might have to make a directory in your /usr called 'tmp'. Then do a 'sudo chmod 777 /usr/tmp'
This allows all read and write permissions to this  directory, and will stop maya complaining about writing a log file when it starts.

- When making a new launcher for maya, in order to get it to let me pick the Maya icon (in the /desktop directory of your maya install) I had to copy the icon file to /usr/share/pixmaps. At first I thought maybe it was a file type issue, so I used GIMP to convert it to a .xpm, but it should work as the default png file.

---

### Post by drfalkor on 2007-05-08
Hi, 
thnx for this great howto, but when i try to install it I get this error: 

> falkor@ubuntu:~/Desktop$ sudo dpkg -i awcommon-server_10.80-14_i386.deb 
(Leser database ... 126675 filer og kataloger er installerte.)
Gjør klar til å bytte ut awcommon-server 10.80-14 (ved bruk av awcommon-server_10.80-14_i386.deb) ...
Pakker ut erstatningen awcommon-server ...
/usr/bin/test: invalid integer «upgrade»
Setter opp awcommon-server (10.80-14) ...
Warning:  Unable to locate the chkconfig utility!
          This is required to add or remove the License Server as an automatically started
          system daemon.
          You can manually set this up or run the utility that came with you linux distribution.


What can be wrong ?:O

---

### Post by dagooze on 2007-05-08
Hey all.
drfalkor I run into the same problem but maya8.5 runs fine with this install errors!

You can be sure that the sudo ln -s /usr/autodesk /autodesk  does matter like hell !!! BIG THANKS ZombieAcademy, I was going crazy about the ln failures I got during maya setup. You saved my day!

cheers

dagoose

---

### Post by Bart Simpson 18 on 2007-05-09
Hi guys,

I also encountered some refresh errors in Maya 8.5.

My errors were the following:
**- when starting Maya 8.5 the screen elements didnt show up**
**- when scrolling in the Attribute editor menu, all the fonts got messed up because of refresh draw error**
**- also the swatches in the Attrib editor -> refresh draw error**

I was really dissapointed and almost gave up.... wanted to return to Maya on Windows when I found this site

[http://discussion.autodesk.com/thread.jspa?messageID=5499540](http://discussion.autodesk.com/thread.jspa?messageID=5499540)

They write that you have to do these steps to get Maya running:
> I solved this with an option in xorg.conf

I put my relevant config here (I don't remember exactly what option was)

Section "Screen"
...
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
Option "DamageEvents" "True"
Option "RenderAccel" "on"
Option "NvAGP" "1"
Option "XAANoOffscreenPixmaps"

Hope this Info helps some of you guys :popcorn:

---

### Post by fakie_flip on 2007-05-09
What is Maya? Is it a game or something like blender?

---

### Post by dagooze on 2007-05-09
Hey,

Maya is something like Blender!

Does anyone of you guys know how to get the ctrl+shift+click combination to work to drag functions onto the shelf. I don't want to do that all manually ... will take ages.

Thanks a lot

---

### Post by jujoje on 2007-05-11
If I can remember correctly in linux the key combo is <alt>+<shift> + <lmb>

---

### Post by jujoje on 2007-05-11
Hi,

I'm trying to install maya 8.5 x64 and I'm getting the
**sh: apcw: not found**
error message. I notice that earlier in this thread a few people have come across it before. Does any one have any idea of how I can get around this error, or what is causing it?

---

### Post by jujoje on 2007-05-11
What do you know: I post and immediately afterwards get it working :) 

All I did was copy the aw.dat to the /var/flexlm directory and all worked. the apcw is just the "install license" dialogue box so if the licence is already there it works fine.

---

### Post by mikebelanger on 2007-05-25
Ok I did this tutorial as well.
I'm running Kubuntu 7.04.
I'm getting some errors 
> mike@mike:~/Desktop/linux$ sudo dpkg -i maya_8.5-112_i386.deb
Selecting previously deselected package maya.
(Reading database ... 90104 files and directories currently installed.)
Unpacking maya (from maya_8.5-112_i386.deb) ...
Setting up maya (8.5-112) ...
ln: creating symbolic link `/autodesk/maya' to `maya8.5': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/bin/maya' to `Maya8.5': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libgcc_s.so' to `libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libstdc++.so.6' to `libstdc++.so.6.0.6': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libstdc++.so' to `libstdc++.so.6.0.6': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libGLU.so.1' to `libGLU.so.1.3': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libpython2.4.so' to `libpython2.4.so.1.0': No such file or directory
sed: can't read /autodesk/maya8.5/mentalray/maya.rayrc: No such file or directory
sed: can't read /autodesk/maya8.5/bin/unsupported/mayarender_with_mr: No such file or directory
sed: can't read /autodesk/maya8.5/bin/unsupported/mayaexport_with_mr: No such file or directory
mv: cannot move `/tmp/maya.rayrc' to `/autodesk/maya8.5/mentalray/maya.rayrc': No such file or directory
mv: cannot move `/tmp/mayarender_with_mr' to `/autodesk/maya8.5/bin/unsupported/mayarender_with_mr': No such file or directory
mv: cannot move `/tmp/mayaexport_with_mr' to `/autodesk/maya8.5/bin/unsupported/mayaexport_with_mr': No such file or directory
There may be a more recent license for this workstation available on the Autodesk
web site. Please visit the following URL to check for updated licenses:
[http://www.autodesk.com/Maya-webkey](http://www.autodesk.com/Maya-webkey)


Now I just ignored this message and went ahead, installed the docs.  They seemed to install fine.
So I create a link to the file Maya.bin.  When I click on it, absolutely nothing happens. 
When I try and execute 'Maya' in that same subdirectory I get a bouncing icon, that's it.
When I go in the consol and type it in, bash doesn't even recognize it.

But all the files appear to be there, so I'm a little confused.

HELP!

---

### Post by mikebelanger on 2007-06-01
oops!  Spoke too soon!

I made the silly mistake of not having csh.
For those having the problem above,  just run a 

sudo apt-get csh

Hehe Maya worked fine after that.
So yeah just do what was mentioned a few pages before and make sure csh is installed if you had my problem.

---

### Post by mech7 on 2007-06-01
does anybody know how to install sp1 for ubuntu?

[http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=9627807&linkID=9242259](http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=9627807&linkID=9242259)

---

### Post by unlotto on 2007-06-09
> **mech7 said:**
> does anybody know how to install sp1 for ubuntu?

[http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=9627807&linkID=9242259](http://usa.autodesk.com/adsk/servlet/ps/dl/item?siteID=123112&id=9627807&linkID=9242259)

I've install sp1 on a 64bit ubuntu, using much the same approach as explained here. AWCommon will most likely fail on first install attempt. Remove its status from nano /var/lib/dpkg/status and you should succeed. I don't remember where I read this. Remember sp1 is not an update per se. It's a whole new full-rpm

---

### Post by steigleitung on 2007-06-11
I installed Maya 8.5. It works fine so far, I am wondering however how to use command line batch rendering. On Windows, it's just entering "render file.mb". There is a "Render" binary (?) in Maya's /bin directory, but I can't get it to work ("bash: Render: command not found"). I'm really not much of a Linux user, can anybody tell me how to do this?

---

### Post by mayamaniac on 2007-06-14
I'm getting these errors with maya8.5, does any one know how to fix this? please help

> :~/Desktop/maya85$ sudo dpkg -i maya_8.5-112_i386.deb
Selecting previously deselected package maya.
(Reading database ... 122542 files and directories currently installed.)
Unpacking maya (from maya_8.5-112_i386.deb) ...
Setting up maya (8.5-112) ...
ln: creating symbolic link `/autodesk/maya' to `maya8.5': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/bin/maya' to `Maya8.5': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libgcc_s.so' to `libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libstdc++.so.6' to `libstdc++.so.6.0.6': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libstdc++.so' to `libstdc++.so.6.0.6': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libGLU.so.1' to `libGLU.so.1.3': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libpython2.4.so' to `libpython2.4.so.1.0': No such file or directory
sed: can't read /autodesk/maya8.5/mentalray/maya.rayrc: No such file or directory
sed: can't read /autodesk/maya8.5/bin/unsupported/mayarender_with_mr: No such file or directory
sed: can't read /autodesk/maya8.5/bin/unsupported/mayaexport_with_mr: No such file or directory
mv: cannot move `/tmp/maya.rayrc' to `/autodesk/maya8.5/mentalray/maya.rayrc': No such file or directory
mv: cannot move `/tmp/mayarender_with_mr' to `/autodesk/maya8.5/bin/unsupported/mayarender_with_mr': No such file or directory
mv: cannot move `/tmp/mayaexport_with_mr' to `/autodesk/maya8.5/bin/unsupported/mayaexport_with_mr': No such file or directory
There may be a more recent license for this workstation available on the Autodesk
web site. Please visit the following URL to check for updated licenses:
[http://www.autodesk.com/Maya-webkey](http://www.autodesk.com/Maya-webkey)

Edit; just posted and saw mikebelanger's post on top with the same error, so I'm trying that fix he posted. I did an "sudo apt-get install csh" and it said I already have the newest one. I ran the maya install command again and it still gave the same error. Any other ideas?

---

### Post by mikebelanger on 2007-06-14
Hey mayamaniac,

It looks like your directories were created.  
I'm new to ubuntu, but it might be that you need to set your tmp directory with proper permissions.  Did you try and execute the maya file with csh?
I had those errors, but was able to execute it anyway.  

If it doesn't work, it might be permissions on your /tmp folder aren't open ( even though you ran it with sudo ).

Zombie Academy said:
> 
- You might have to make a directory in your /usr called 'tmp'. Then do a 'sudo chmod 777 /usr/tmp'
This allows all read and write permissions to this directory, and will stop maya complaining about writing a log file when it starts.
.

---

### Post by unlotto on 2007-06-16
Are any of you having issues with Maya and importing wav files? I got it to work in i386, (by system linking libaudiofile.so)

on amd64 (and 64bit maya) it imports, but the sound is all scrambled and won't playback properly.

Same thing happens on a variety of other distro's like Fedora Core 7 and CentOS 5 and OpenSuse 10.2

without sound, maya is useless to our animators.

---

### Post by mayamaniac on 2007-06-18
I'm still getting the error with Maya 8.5:
> :~/Desktop/maya85$ sudo dpkg -i maya_8.5-112_i386.deb
Password:
(Reading database ... 138854 files and directories currently installed.)
Preparing to replace maya 8.5-112 (using maya_8.5-112_i386.deb) ...
test: 45: upgrade: bad number
Unpacking replacement maya ...
Setting up maya (8.5-112) ...
ln: creating symbolic link `/autodesk/maya' to `maya8.5': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/bin/maya' to `Maya8.5': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libgcc_s.so' to `libgcc_s.so.1': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libstdc++.so.6' to `libstdc++.so.6.0.6': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libstdc++.so' to `libstdc++.so.6.0.6': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libGLU.so.1' to `libGLU.so.1.3': No such file or directory
ln: creating symbolic link `/autodesk/maya8.5/lib/libpython2.4.so' to `libpython2.4.so.1.0': No such file or directory
sed: can't read /autodesk/maya8.5/mentalray/maya.rayrc: No such file or directory
sed: can't read /autodesk/maya8.5/bin/unsupported/mayarender_with_mr: No such file or directory
sed: can't read /autodesk/maya8.5/bin/unsupported/mayaexport_with_mr: No such file or directory
mv: cannot move `/tmp/maya.rayrc' to `/autodesk/maya8.5/mentalray/maya.rayrc': No such file or directory
mv: cannot move `/tmp/mayarender_with_mr' to `/autodesk/maya8.5/bin/unsupported/mayarender_with_mr': No such file or directory
mv: cannot move `/tmp/mayaexport_with_mr' to `/autodesk/maya8.5/bin/unsupported/mayaexport_with_mr': No such file or directory
There may be a more recent license for this workstation available on the Autodesk
web site. Please visit the following URL to check for updated licenses:
[http://www.autodesk.com/Maya-webkey](http://www.autodesk.com/Maya-webkey)

When I try to run maya.bin from csh, I get this:
> % ./maya.bin
./maya.bin: error while loading shared libraries: libirc.so: cannot open shared object file: No such file or directory

I tried the permission thing for /usr/tmp, but it doesn't seem to help. Any ideas why it is not working?

---

### Post by mayamaniac on 2007-06-18
It's working now. Instead of running maya.bin, I ran ./Maya8.5 and that works. Now to test if everything is working like the Windows version.

First difference is the camera keys, the alt key just drags the window around (ubuntu default key to move windows), so to get the camera dolly, pan, and zoom tools, I have to hold down both the windows key and alt.

---

### Post by arsui on 2007-06-23
befor, i had install the maya8.5, it can use but not steady, often quit  automatic itself. So i anstall maya7 without uninstall maya8.5, then not successful, so i use  'sudo rm -r ' to remove the directory of maya7. 
and now , when i open the  update manager. it tips
--------------------------------------------------------------------------------
Password:Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package awcommon needs to be reinstalled, but I can't find an archive for it.'
-------------------------------------------------------------------------------------------------------------------
and in termial
---------------------------------------------------------
sudo apt-get check

Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: The package awcommon needs to be reinstalled, but I can't find an archive for it.
---------------------------------------------------------------------------------------------------------

and then i reinstall 
-------------------------------------
 sudo dpkg -i awcommon_10.80-2_i386.deb
Selecting previously deselected package awcommon.
(Reading database ... 151303 files and directories currently installed.)
Preparing to replace awcommon 10.80-2 (using awcommon_10.80-2_i386.deb) ...
Unpacking replacement awcommon ...
test: 7: upgrade: bad number
exit: 8: Illegal number: -0
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
test: 7: failed-upgrade: bad number
exit: 8: Illegal number: -0
dpkg: error processing awcommon_10.80-2_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
test: 7: abort-upgrade: bad number
exit: 8: Illegal number: -0
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon_10.80-2_i386.deb
--------------------------------------------------

I do not kown how to fix the problem. i found hard to uninstall the deb software, PS: i can't found maya8.5 in Synptic package manager .
anybody can tell me what happen and how to fix ?
Thanks 
(&#35874;&#35874;)

---

### Post by szr4321 on 2007-06-23
> **arsui said:**
> 
dpkg: error processing awcommon_10.80-2_i386.deb (--install):
 subprocess new post-removal script returned error exit status 2
(&#35874;&#35874;)
Try ```
sudo rm /var/lib/dpkg/info/awcommon.postrm
```and then remove / reinstall the awcommon package.

---

### Post by arsui on 2007-06-24
> **szr4321 said:**
> Try ```
sudo rm /var/lib/dpkg/info/awcommon.postrm
```and then remove / reinstall the awcommon package.
[COLOR="Red"]Thanks very much, szr4321, you reply is useful. but  now  when open then update manage, it tips : [/COLOR]

-------------------------------------------------------------
Software index is broken

It is impossible to install or remove any software. Please use the package manager "Synaptic" or run "sudo apt-get install -f" in a terminal to fix this issue at first.
------------------------------------------------------------------
[COLOR="Red"]so I try 'sudo apt-get install -f ' [/COLOR]

------------------------------------------------
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libsm-dev libarts1c2a kdelibs4c2a libice-dev
  x11proto-xext-dev libatk1.0-dev x11proto-kb-dev libglib2.0-dev
  x11proto-xinerama-dev libpango1.0-dev g++-4.1 x11proto-render-dev
  kdelibs-data libxi-dev libxrender-dev liblualib50 libpcre3 libcairo2-dev
  libxdmcp-dev libpng12-dev libstdc++6-4.1-dev libfontconfig1-dev xtrans-dev
  x11proto-core-dev libxcursor-dev libavahi-qt3-1 x11proto-randr-dev
  libxext-dev zlib1g-dev x11proto-input-dev libfreetype6-dev
  x11proto-fixes-dev libxau-dev libxrandr-dev libexpat1-dev libxft-dev
  libx11-dev libqt3-mt liblua50 libxfixes-dev libxinerama-dev
  libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  awcommon
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3957kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 151311 files and directories currently installed.)
Removing awcommon ...
test: 7: remove: bad number
exit: 8: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
-----------------------------------------------------------------------------------

[COLOR="Red"]and in the Synaptic,  i can open and mark the awcommon and awcommon-server as remove, but when apply, it told me [/COLOR]

------------------------------
 sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libopenexr2c2a libsm-dev libarts1c2a kdelibs4c2a libice-dev
  x11proto-xext-dev libatk1.0-dev x11proto-kb-dev libglib2.0-dev
  x11proto-xinerama-dev libpango1.0-dev g++-4.1 x11proto-render-dev
  kdelibs-data libxi-dev libxrender-dev liblualib50 libpcre3 libcairo2-dev
  libxdmcp-dev libpng12-dev libstdc++6-4.1-dev libfontconfig1-dev xtrans-dev
  x11proto-core-dev libxcursor-dev libavahi-qt3-1 x11proto-randr-dev
  libxext-dev zlib1g-dev x11proto-input-dev libfreetype6-dev
  x11proto-fixes-dev libxau-dev libxrandr-dev libexpat1-dev libxft-dev
  libx11-dev libqt3-mt liblua50 libxfixes-dev libxinerama-dev
  libid3-3.8.3c2a
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED:
  awcommon
0 upgraded, 0 newly installed, 1 to remove and 14 not upgraded.
2 not fully installed or removed.
Need to get 0B of archives.
After unpacking 3957kB disk space will be freed.
Do you want to continue [Y/n]? Y
(Reading database ... 151311 files and directories currently installed.)
Removing awcommon ...
test: 7: remove: bad number
exit: 8: Illegal number: -0
dpkg: error processing awcommon (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon
E: Sub-process /usr/bin/dpkg returned an error code (1)
----------------------------------------------------------------------
i sorry, i don't know which message is the key, so i past all. :D


[COLOR="Red"]add: sorry, now the 'awcommon' had remove, but the  when i try 'sudo apt-get auto remove' it tips :
--------------------------------------[/COLOR]
 sudo apt-get autoremove
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up aksusbd-suse (1.7-3) ...
cat: /etc/SuSE-release: No such file or directory
[: 31: 8: unexpected operator
[: 31: 8: unexpected operator
/var/lib/dpkg/info/aksusbd-suse.postinst: 35: insserv: not found
.: 13: Can't open /etc/rc.status
dpkg: error processing aksusbd-suse (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 aksusbd-suse
E: Sub-process /usr/bin/dpkg returned an error code (1)

---------------------------------------------------------------------------
[COLOR="Red"]i can install maya7 again now?[/COLOR]

add info : i had install, but not very good, often quit it self. i think maybe conflict with other software

---

### Post by szr4321 on 2007-06-24
> **arsui said:**
> /var/lib/dpkg/info/aksusbd-suse.postinst: 35: insserv: not found
.: 13: Can't open /etc/rc.status
dpkg: error processing aksusbd-suse (--configure):
 subprocess post-installation script returned error exit status 2
Errors were encountered while processing:
 aksusbd-suse
E: Sub-process /usr/bin/dpkg returned an error code (1)

Usually you don't need to install the aksusbd-suse package at all, it's for SuSE Linux distributions. Unfortunately the removal script doesn't work on Ubuntu, because the insserv application isn't there. So, try
```
sudo rm /var/lib/dpkg/info/aksusbd-suse.postinst /var/lib/dpkg/info/aksusbd-suse.postrm
```
And then run
```

sudo apt-get autoremove
sudo apt-get install -f

```
> **arsui said:**
> i can install maya7 again now?
You should first make sure that no packages are broken anymore. Then only install the three packages given in the HowTo.

---

### Post by arsui on 2007-06-25
> **szr4321 said:**
> Usually you don't need to install the aksusbd-suse package at all, it's for SuSE Linux distributions. Unfortunately the removal script doesn't work on Ubuntu, because the insserv application isn't there. So, try
```
sudo rm /var/lib/dpkg/info/aksusbd-suse.postinst /var/lib/dpkg/info/aksusbd-suse.postrm
```
And then run
```

sudo apt-get autoremove
sudo apt-get install -f

```

You should first make sure that no packages are broken anymore. Then only install the three packages given in the HowTo.

thanks all !

I had in stall maya 7.0  , and it run well after i edit the xorg.conf , [COLOR="Red"]but some time when i click the button "render current frame", the maya quit it self without any alarm or tips[/COLOR]

---

### Post by thedaemon on 2007-06-25
> **mayamaniac said:**
> It's working now. Instead of running maya.bin, I ran ./Maya8.5 and that works. Now to test if everything is working like the Windows version.

First difference is the camera keys, the alt key just drags the window around (ubuntu default key to move windows), so to get the camera dolly, pan, and zoom tools, I have to hold down both the windows key and alt.

Change the settings for gnome to move windows. I changed it to Super+mouse button. Super is the windows key.

---

### Post by szr4321 on 2007-06-26
> **arsui said:**
> 
I had in stall maya 7.0  , and it run well after i edit the xorg.conf , [COLOR="Red"]but some time when i click the button "render current frame", the maya quit it self without any alarm or tips[/COLOR]
Did you start Maya from the console? If yes, are there any error displayed after Maya quits?

Did you try to render using mental ray?

---

### Post by arsui on 2007-06-27
> **szr4321 said:**
> Did you start Maya from the console? If yes, are there any error displayed after Maya quits?

Did you try to render using mental ray?
not from console, I creat a desktop file in applications menu, point to the  [/usr/aw/maya/bin/Maya7.0] , it is ok.

I use mental ray, but i don't think it is the cause; for it also have same problem when only use maya software render.   however i found the way: not click the render current frame, just select  the area and click the render region; it will always ok.

but i also want to kown the problem and solution.

and thks again szr4321

---

### Post by szr4321 on 2007-06-27
> **arsui said:**
> not from console, I creat a desktop file in applications menu, point to the  [/usr/aw/maya/bin/Maya7.0] , it is ok.
I asked because Maya sometimes displays error messages on the console when it quits because of an error. You won't see these if you start Maya using a desktop link.
> **arsui said:**
> 
but i also want to kown the problem and solution.

Maya creates the log file *maya/mayaLog* in your home directory. Maybe you can find some hints there.

Finally, you should install the [Maya 7.01 update](http://www.alias.com/glb/eng/support/product_support.jsp?itemId=5200001) if you haven't already.

---

### Post by arsui on 2007-06-28
> **szr4321 said:**
> I asked because Maya sometimes displays error messages on the console when it quits because of an error. You won't see these if you start Maya using a desktop link.

Maya creates the log file *maya/mayaLog* in your home directory. Maybe you can find some hints there.

Finally, you should install the [Maya 7.01 update](http://www.alias.com/glb/eng/support/product_support.jsp?itemId=5200001) if you haven't already.

thanks all, i will do it!

---

### Post by alanf on 2007-07-02
I got Maya 8.5 up and running. Thanks for the great how-to! :D

Now, I realised that I needed to free the Alt key hotkeys (like to move/resize windows) and so I did, switching it to my Winkey. However, I missed one, but I can't seem to find where to change its setting... and that is when you Alt+rightclick on a window.

Where do I get rid of that or change it to something else?? :confused:

---

### Post by alanf on 2007-07-02
Found it!

In gconf-editor, at /apps/compiz/general/allscreens/options/window_menu_button

Woohoo! :D

---

### Post by svigno on 2007-07-02
Use WindowMaker ten times faster than gnome ...

---

### Post by wntrmt on 2007-07-03
Hello,

I've been trying to install Maya 64 on a fresh installation of Ubuntu Feisty 64 without success. I've read this thread over and over and it seems there's no problem to my solution (this has been posted by some around pages 8 to 16 I think). First I was having problems like this:

> 
$ ./findkey
./findkey: error while loading shared libraries: libstdc++.so.5: cannot open shared object file: No such file or directory


Then, doing this linking like some suggested:
```

sudo ln -sf /lib/libgcc_s.so.1 /usr/aw/COM/lib/libgcc_s.so.1
sudo ln -sf /usr/lib/libstdc++.so.5 /usr/aw/COM/lib/libstdc++.so.5

```

Got me to this error (mentioned before):
> 
$ ./findkey
./findkey: error while loading shared libraries: libstdc++.so.5: wrong ELF class: ELFCLASS64


The aw.dat is on /var/flexlm, with permissions set, etc etc. I don't know if it's really necessary to run findkey and/or installkey, nobody mentioned it here. Anyway trying to run maya I get:
> 
$ maya
apcw: error while loading shared libraries: libXrender.so.1: cannot open shared object file: No such file or directory


So I made:
```

$ sudo ln -sf /usr/lib/libXrender.so.1  /usr/autodesk/maya/lib/libXrender.so.1

```

Then I get:
> 
$ maya
apcw: error while loading shared libraries: libXrender.so.1: wrong ELF class: ELFCLASS64


And yes, I installed 64 bit version of Maya.

From the Italian [forum]("http://forum.ubuntu-it.org/index.php?topic=15503.0") and [Wiki,]("http://forum.ubuntu-it.org/index.php?topic=15503.0") they say you need **i386 versions** of libraries **libXp.so.6 libuuid.so.1 libfam.so.0**. So I downloaded them from [http://packages.ubuntu.com/](http://packages.ubuntu.com/) and placed on /usr/autodesk/maya/lib. Still the same. So I look for i386 version of libXrender, place it on /usr/autodesk/maya/lib and have:
> 
$ maya
apcw: error while loading shared libraries: libXrandr.so.2: cannot open shared object file: No such file or directory


But I'm not in the mood to get ALL i386 version of maya libs to run the 64 bit version. Something is wrong, but I have no idea of what.

Would anyone have any light?


Wntrmt

---

### Post by wntrmt on 2007-07-04
No one??

There are some people on this thread that are running Maya 64 on amd64, did you find any of this problems I mentioned? I was trying the latest Maya 8.5... 

I wonder, if I install it on Fedora will it run out of the box?

---

### Post by P4VV37 on 2007-07-09
Maya crashes on startup :[
I had a problem with  /usr/lib/libGLU.so so I did:
```
cp libGLU.so.1.3 /usr/lib/libGLU.so
```
 and  
```
cp libGLU.so.1.3 /autodesk/maya8.5/lib/libGLU.so
```
now I've got other problem:
```

/autodesk/maya8.5/bin/maya.bin: symbol lookup error: /autodesk/maya8.5/lib/libHWRenderMaya.so: undefined symbol: _ZN18GLParticleDrawBase21setMaterialPropertiesEfRN7awColor5ColorES2_S2_S2_
```


;(

What can I do? :confused:


Maya 8.5 and Kubuntu 7.04

---

### Post by ydiaz on 2007-07-16
Hi guys, I managed to install Maya 8.5 on a Feisty AMD64 correctly but as other people have stated in this thread it's impossible to import and work with sounds correctly. I had to move to windows because of this only detail. I've tried to link the library and Maya does not complain but I can't hear the sound on playblasts or scrubbing.

Anyone, please, has any idea how to sort this last hurdle?

Thanks.

---

### Post by Nisroc on 2007-07-26
I'm getting this error message when trying to run Maya 8.5 after following the instructions in the tutorial (64 bit system):

> apcw: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory

I've checked if it is installed and everything seams to be in working order.
I really hope some one can help me!

Thanks in advance :)
-Ian

---

### Post by Nisroc on 2007-07-26
bump.

Please. I really need help with this

---

### Post by qzr on 2007-07-31
Great work!! Install worked as a charm for me on my Ubuntu Feisty system with Maya 8.5.
Only problem was with that old dusty graphics card in that system (Radeon 9600). 
This gave me some crappy graphics. But even that was quickly fixed by disabling the composite option in xorg.conf:

Section "Extensions"
  Option "Composite" "Disable"
EndSection

and adding a GARTsize option under my device section in xorg.conf:
Option          "GARTSize" "64"

This option gets rid of the  GARTSize allocation error with older ATI cards. 


I also upgraded my X.org to 7.2 as described in [http://ubuntuforums.org/showthread.php?t=373087](http://ubuntuforums.org/showthread.php?t=373087)
for better 3d performance

And all of the wacky graphics are gone.
Thx m8!
I am now getting rid of window$ :))

---

### Post by tempo500 on 2007-08-15
> apcw: error while loading shared libraries: libXcursor.so.1: cannot open shared object file: No such file or directory

hi,

i had this problem at work, and right now dont have acces to this information... but i know you are missing a package and my guess would be:ia32-libs

so now to my problem.... i have been using maya in production now for a year, and everything was good untill a few days ago... maya works, render window works, just batch rendering gives me a signal 11 error. couldnt fix it - installed a fresh ubuntu system(i dared to install gutsy...) batch rendering worked again, finished my scene, and the same thing again... maybe someone knows how to fix this...

ok...update.... i am middle in a production so it was quicker to reinstall ubuntu... so now i know its not a new package cause i updated gutsy with all new packages and maya is rendering just fine. so i am not sure what causes maya to crash in batch mode, the first time it happend on feisty, i was just working with the usual progs no updates no new progs, no messing around... batch crash...reinstalled ubuntu renderd fine, installed the remaining progs, same thing... third reinstall, clean system updated packages. maya and shake... everything good.. i will pay attention to the batch render after i install something new... my feeling tells me i will be posting again tomorrow.... :-/ my next try would be to install a 32bit ubuntu? i never had this problem just appeard a few days ago, there is a similar thread at autodesk. [http://discussion.autodesk.com/thread.jspa?threadID=591260]("http://discussion.autodesk.com/thread.jspa?threadID=591260")

thanks for _any_ info, phil

here is the feedback

```
export MAYA_DEBUG_ENABLE_CRASH_REPORTING=1 
phil@workstation:~/maya/projects/3d_coffee/scenes$ ./rnd.sh
// Using temp file "/usr/tmp/ASTMP7iijl2.mel"

////////////////////////////////////////////////////////////////////////////
// Starting Mel program

proc renderIt(string $name) {

string $opt=""; string $rl=""; string $rp=""; int $renderThreads = 2; float $resize=-1.; miLoadMayatomr; miCreateDefaultNodes(); select defaultRenderGlobals; setAttr .renderAll 1; // Before all flags

workspace -rt "images" "/home/phil/maya/projects/3d_coffee/images";workspace -rt "depth" "/home/phil/maya/projects/3d_coffee/images";; // For flag -rd

makeCameraRenderable("cam16_9E"); // For flag -cam

removeRenderLayerAdjustmentAndUnlock .animation; setAttr .animation 1; removeRenderLayerAdjustmentAndUnlock .startFrame; setAttr .startFrame 1; // For flag -s

removeRenderLayerAdjustmentAndUnlock .animation; setAttr .animation 1; removeRenderLayerAdjustmentAndUnlock .endFrame; setAttr .endFrame 175; // For flag -e

setMayaSoftwareLayers($rl, $rp); miCreateMentalJobs(); setImageSizePercent($resize); mayaBatchRenderProcedure(0, "", "", "mentalRay", $opt); ; // After all flags

}

//
// Main part
//

string $sceneName = "master008.mb";

string $checkScene = `file -q -sn`;
if ($checkScene=="") {
    quit -abort -force -exitCode 209;
    error ("Cannot load scene \""+$sceneName+"\". Please check the scene name.");
} else if (catch(`renderIt($sceneName)`)) {
    quit -abort -force -exitCode 210;
    error ("Scene "+$sceneName+" failed to render.\n");
} else {
    print ("Scene "+$sceneName+" completed.\n");
    quit -abort -force -exitCode 0; // Exit Maya
}

// Ending Mel program
// Maya file is "master008.mb"

Starting "/usr/autodesk/maya8.5-x64/bin/maya"
Arg[1]="-batch"
Arg[2]="-file"
Arg[3]="master008.mb"
Arg[4]="-script"
Arg[5]="/usr/tmp/ASTMP7iijl2.mel"
Arg[6]="-proj"
Arg[7]="/home/phil/maya/projects/3d_coffee"


maya encountered a fatal error

Signal: 11 (Unknown Signal)
Stack trace:
  /lib/libc.so.6 [0x2aade5e2f760]
  XtAppAddWorkProc
  TeventHandler::addIdleEventTimer()
  TeventHandler::addIdleCommand(Taction*, TidleCommandPriority, unsigned short)
  TeventHandler::addIdleCommand(Taction*, TidleCommandPriority)
  TidleTrigger::addClientHook(Tclient*, Tmetaclass*)
  TclientServer::addClient(Tclient*, Tmetaclass*, void (*)(Tclient*, TclientServer*, TserverMsg const&))
  MEventMessage::addEventCallback(MString const&, void (*)(void*), void*, MStatus*)
  initializePlugin(MObject)
  Tplugin::load(Tstring const&, Tstring*)
  TloadPluginAction::loadPlugin(TfilePath const&, Tstring const&, bool, Tstring&)
  TloadPluginAction::execute(TargList&)
  TloadPluginAction::doCommand(TargList&)
  Mel_Command_Dispatch(SphNode*)
  node_exec
  f_catch
  f_not
  fc_if
  node_exec
  fc_ifelse
  node_exec
  f_function_entry_node
  node_exec
  sophia_call_executable
  SophiaExecutable::evaluate(void*)
  TcommandEngine::executeCommand(Tstring const&, bool, bool, TmelCmdResult*, unsigned int)
  TscriptAction::doIt(Tevent const&)
  TevalDeferredAction::doCommand(TargList&)
  Mel_Command_Dispatch(SphNode*)
  node_exec

Fatal Error. Attempting to save in /usr/tmp/phil.20070815.1730.ma
Writing crash report in /usr/tmp/phil.20070815.1730.crash
// Maya exited with status 1

```

---

### Post by sciclone on 2007-08-16
we are facing wiered problem hope there is the solution for missing paths and text inside render globals script editor file open dialogue etc almost every creation menu rest everything is fine

---

### Post by boob11 on 2007-08-16
Thank you man

---

### Post by tempo500 on 2007-08-18
hi!

i found the problem! i recently bought myself a spacenavigator from 3dconexxion. they have linux drivers and linux maya plugins. well... the maya plugin caused the problem. for more details got to [http://www.3dconnexion.com/forum/viewtopic.php?p=5844#5844]("http://http://www.3dconnexion.com/forum/viewtopic.php?p=5844#5844")
once again.... it wasnt linux... phil

---

### Post by jorosy on 2007-08-26
I just installed maya 8.5 sp1. With add composite disable to xorg.conf. I got some maya disaply problems fixed.
However, in Hypershade, while I creat a node by MMB drag from create bar into workarea,
the system seems to freeze for about a while like a minute before it is shown in the workarea
same problem happens when connecting a node's attribut to other node in workarea. 
but they works fine when I drag n drop a node into attribute editor for connection.
Would any body know why is this happen?? I am running feisty with gefore 8600gt and the driver form nvidia site.
I am new to linux and ubuntn, and Thanks for help in advanced.

---

### Post by jorosy on 2007-08-26
I had lots of gnome keyboard shortcut that is conflicting with maya, and I dont feel like to reassign the shortcut in either maya or gnome. 
is there any way that I could do those??
like when maya get started, I could temporary disable all gnome keyboard shortcut, and restore it when I exit maya.
or, I could put maya into a gnome desktop workspace, then in that workspace, all the gnome keyboard shortcut is disable.
or, disable gnome shortcut just for maya window, or something that detects mouse hover point to do the temporary disable.

---

### Post by P4VV37 on 2007-08-26
I can't update maya 8.5  to service pack 1
I've downloaded file and used alien.
I've got this error:
(sorry, I can't translate it to English)
 sudo dpkg -i maya8-5_8.5-145_i386.deb
Password:
(Odczytywanie bazy danych ... 176521 plików i katalogów obecnie zainstalowanych.)
Rozpakowanie maya8-5 (z maya8-5_8.5-145_i386.deb) ...
dpkg: b&#322;&#261;d przetwarzania maya8-5_8.5-145_i386.deb (--install):
 próba nadpisania `/usr/autodesk/maya8.5/ExternalWebBrowser/MacOS/McpPlugIn.plugin/Contents/MacOS/McpPlugIn', który istnieje tak&#380;e w pakiecie maya
dpkg-deb: podproces paste zosta&#322; zabity sygna&#322;em (Broken pipe)
Wyst&#261;pi&#322;y b&#322;&#281;dy podczas przetwarzania:
 maya8-5_8.5-145_i386.deb


Translated to English:
```
[...]
dpkg error when transforming  maya8-5_8.5-145_i386.deb (--install):
trying to overwrite `/usr/autodesk/maya8.5/ExternalWebBrowser/MacOS/McpPlugIn.plugin/Contents/MacOS/McpPlugIn', Witch exist also in package maya
dpkg-deb: subprocess paste was killed by signal (Broken pipe)
there was errors when transforming
 maya8-5_8.5-145_i386.deb

```

wtf is wrong??

Sorry for my English :mad:

---

### Post by HuitZiloP on 2007-09-11
> **Ashur said:**
> Maya looks in the following paths for postscript fonts:
[B]/usr/share/fonts/default/ghostscript
/usr/X11R6/lib/X11/fonts/Type1[/B]

Just link some fonts to any of this locations and the TextCurve tool
shoud work.

Could you please elaborate? I'm having this problem and haven't found a way to solve it. Some thread at autodesk (only one on the entire web to take on the subject) suggest the same solution, but it's very vague. I tried copying all my fonts from fonts:/// to the specified paths, but to no avail, so my guess is I MUST create some symlinks. Only question is how do I do that?

Thanks a lot in advance.

EDIT:
Original thread at autodesk:

[http://discussion.autodesk.com/thread.jspa?threadID=508762](http://discussion.autodesk.com/thread.jspa?threadID=508762)

Check last two posts. They seem to give the solution, but they're not very specific, could someone please elaborate a little bit more into this?

---

### Post by SreckoMicic on 2007-09-12
I installed Maya 8 without any problem thanks to this thread.
Now I want to install SP1. 
How can I, or do I need at all, to uninstall previous version of Maya and awcommon?
Will this do the trick?
```
sudo dpkg -r package_name
```

EDIT: Solved it, using Synaptic :), now can use latest edition, yeah.
BTW if you ran on awcommon uninstall problem just modify status file, and manually remove awcommon entry, as stated [here]("http://ubuntuforums.org/showthread.php?t=545055&highlight=maya+install")

---

### Post by skullmunky on 2007-09-13
MMB drag freeze

I have the same problem as jorosy - MMB drag in hypershade freezes when you release.  Alt-Tab to another window and back unfreezes it.

maya 8.5, kubuntu feisty, quadrofx 1400.  CIOVerlay is on and Composite is Disable.  everything else works fine - even sound scrubbing :)

---

### Post by tempo500 on 2007-09-14
> MMB drag in hypershade freezes when you release
strange.... maya 8.5, quadro 1500 ubuntu feisty.... works  fine.... maybe try to put this in your maya.env file under home/maya

```
MAYA_MMSET_DEFAULT_XCURSOR=1
```

so i also have a problem... posted this on a few maya scripting forums but no reply untill now... maybe there is someone with mel knowledge... this script works great under windows but wont work under linux, my guess is this callback funktion which opens the filebrowser to select a directory. this would be great if someone comes up with a solution. this script should write blendshape information into a file to be imported as animated blendshapes. please.... thanks, phil

error: DSO <libSharedUI.so> faild to load properly or perhaps commandList is incorrect.

i dont have any mel experience but it looks like somethings wrong with the fileBrowserDialog function...

```
 global proc exportBlends (){
    fileBrowserDialog -mode 4 -fc "exportCallback" -an "Pick Your Blend Shape Directory";
    return;
    }

global proc exportCallback(string $path, string $mode){
    print ("this is the dir path: " + $path + "\n");
    string $objs[] = `ls -sl`;
    for ($obj in $objs){
        select $obj;
        file -es -type "mayaAscii" ($path + "/" + $obj);
        delete $obj;
        print "successfully exported objects! \n";
        }
    }
```

---

### Post by Asparatame on 2007-09-20
When I try to install awcommon it only get half-installed... 

This is the error message i get when installing awcommon

```
xxxx@xxxx-desktop:~/maya rpm$ sudo dpkg -i awcommon_10.80-13_i386.deb
Selecting previously deselected package awcommon.
(Reading database ... 116386 files and directories currently installed.)
Unpacking awcommon (from awcommon_10.80-13_i386.deb) ...
Setting up awcommon (10.80-13) ...
cd: 13: can't cd to /aw/COM/bin
cd: 14: can't cd to /aw/COM/bin
cd: 15: can't cd to /aw/COM/bin
cd: 16: can't cd to /aw/COM/bin
cd: 17: can't cd to /aw/COM/bin
cd: 18: can't cd to /aw/COM/bin
cd: 19: can't cd to /aw/COM/bin
cd: 20: can't cd to /aw/COM/bin
cd: 21: can't cd to /aw/COM/lib
cd: 22: can't cd to /aw/COM/lib
cd: 26: can't cd to /aw
```

---

### Post by fktt on 2007-09-23
hmm.. did you make the symbolic links before installing?

---

### Post by Asparatame on 2007-09-24
Yeah I did...

Though I have another error when installing awcommon-server that may have something to do with the previous error

```
martin@martin-desktop:~$ sudo dpkg -i awcommon-server_10.80-13_i386.deb
Selecting previously deselected package awcommon-server.
(Reading database ... 116588 files and directories currently installed.)
Unpacking awcommon-server (from awcommon-server_10.80-13_i386.deb) ...
Setting up awcommon-server (10.80-13) ...
cp: cannot stat `/aw/COM/etc/aw_flexlm': No such file or directory
chmod: cannot access `/etc/init.d/aw_flexlm': No such file or directory
Warning:  Unable to locate the chkconfig utility!
          This is required to add or remove the License Server as an automatically started
          system daemon.
          You can manually set this up or run the utility that came with you linux distribution.

```

The thing with chkconfig I know i don't have to care about but what's up with the cp: cannot stat stuff?

I'm a beginner with ubuntu and linux on the whole so I don't really understand all those error messages yet

---

### Post by fktt on 2007-09-26
ahh, you need to create and 'sudo chmod 777' the flexlm folder before installing(iirc) ;)

allso:

```
Warning:  Unable to locate the chkconfig utility!
```

perhaps you should allso check on that one.. :)

edit: oh, and are you trying to install 8.0/8.5?

---

### Post by Asparatame on 2007-09-27
Yeah I'm trying to install maya 8.0.

And you did mean create and use sudo chmod 777 on /var/flexlm right?
Because if you did it's still not working... getting the same issues as before :(

---

### Post by fktt on 2007-09-29
yes, thats what i meant, hmmh.. 

did you make sure that you have that chkconfig utility? thats the only thing i can think of right now, but will try to come up with more ideas ;)

btw. i my self too have 8.0 installed, and i didnt get those errors.. so, its really hard to guess whats wrong.. i guess it must be some packages you have not installed, witch  i probably had, as ive been on this install for since i got my 7.04 cd's after the version was released.. hmmh..


EDIT: do you have coreutils installed from synaptic?

[ATTACH]44683[/ATTACH]

to check it out open synaptic from "System > Administration > Synaptic Package Manager" enter your root pasword when it asks it

then use the search function.. and either enter "chk" or "coreutils" into the search :)

now see if you have coreutils installed, if not.. install it! :)

---

### Post by tempo500 on 2007-09-29
[QUOTE=did you make sure that you have that chkconfig utility?[/QUOTE]

well... this chkconfig is a warning not an error... i did not install those packages manually...
this is my tomboy note, worked now allready several times on ubuntu 32/64bit feisty and gutsy

hope this helps... besides maya 2008 linux has several important bug fixes... this is a mayor update for linux in my eyes... stuck menu, crash with the shortcut w if you release the mouse early etc... 
i found out that it is saver for me to install the maya deb in the same order as in tomboy note blow, with the graphical package manager. hope this helps....

```
 setup - maya

----------------------------------------------#stupid libXm error

/aw/COM/bin/installKey error libXm.so.2

->/lib/libc.so.6

----------------------------------------------#crash report
• export MAYA_DEBUG_ENABLE_CRASH_REPORTING=1
• maya -d gdb
----------------------------------------------#convert rpm
sudo apt-get install csh alien
for i in *.rpm; do sudo alien -cv $i; done
----------------------------------------------#symlink
sudo ln -s /usr/aw /aw
sudo ln -s /usr/autodesk /autodesk
----------------------------------------------#install - !!IGNORE CHKCONFIG WARNING!!
sudo dpkg -i awcommon-server_
sudo dpkg -i awcommon_
sudo dpkg -i maya
sudo dpkg -i maya-docs-en-us_
----------------------------------------------#install license
sudo cp aw.dat /var/flexlm
sudo mkdir /usr/tmp
sudo chmod 777 /usr/tmp
-------------------------------------------------------------------------------------maya mental ray satellite setup
/etc/services
port:7054
--------------------------------------------------------------------------------------CURSOR PROBLEM
add the line: MAYA_MMSET_DEFAULT_XCURSOR=1 in the /home/user/maya/7.0/Maya.env file
--------------------------------------------------------------------------------------MAYA BG COLOR
sudo gedit /usr/autodesk/maya/app-defaults/MayaScheme
*basicBackground:            #525252
Maya*Background:             #525252
*textForeground:             #bfbfbf
textFieldBackground:         #4b4b57
*readOnlyBackground:         #666666
*textBackground:             #666666


/media/ohdb/SYSTEM/maya_stuff/linux_admin/MayaScheme
------------------------------------------------------------------------------------MAYA FONT ISSUE
sudo gedit /usr/autodesk/maya/app-defaults/MayaScheme
*extraLargeBoldLabelFont:    -*-clean-medium-r-normal-*-16-*-*-*-*-*-*-*
*largeBoldLabelFont:         -*-clean-medium-r-normal-*-14-*-*-*-*-*-*-*
*boldLabelFont:              -*-clean-medium-r-normal-*-12-*-*-*-*-*-*-*
*smallBoldLabelFont:         -*-clean-medium-r-normal-*-12-*-*-*-*-*-*-*
*tinyBoldLabelFont:          -*-clean-medium-r-normal-*-8-*-*-*-*-*-*-*
*plainLabelFont:             -*-clean-medium-r-normal-*-12-*-*-*-*-*-*-*
*smallPlainLabelFont:        -*-clean-medium-r-normal-*-10-*-*-*-*-*-*-*
*obliqueLabelFont:           -*-clean-medium-i-normal-*-12-*-*-*-*-*-*-*
*smallObliqueLabelFont:      -*-clean-medium-i-normal-*-8-*-*-*-*-*-*-*
*fixedWidthFont:             -*-fixed-medium-r-normal--13-*-*-*-*-*-iso8859-1
*smallFixedWidthFont:        -*-clean-medium-r-normal--12-*-*-*-*-*-*-*

*extraLargeBoldLabelFont:    -*-helvetica-bold-r-normal-*-17-*-*-*-*-*-iso8859-1
*largeBoldLabelFont:         -*-helvetica-bold-r-normal-*-14-*-*-*-*-*-iso8859-1
*boldLabelFont:              -*-helvetica-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*smallBoldLabelFont:         -*-helvetica-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*tinyBoldLabelFont:          -*-helvetica-bold-r-normal-*-10-*-*-*-*-*-iso8859-1
*plainLabelFont:             -*-helvetica-medium-r-normal-*-12-*-*-*-*-*-iso8859-1
*smallPlainLabelFont:        -*-helvetica-medium-r-normal-*-10-*-*-*-*-*-iso8859-1
*obliqueLabelFont:           -*-helvetica-bold-o-normal-*-12-*-*-*-*-*-iso8859-1
*smallObliqueLabelFont:      -*-helvetica-bold-o-normal-*-10-*-*-*-*-*-iso8859-1
*fixedWidthFont:             -*-fixed-medium-r-normal--13-*-*-*-*-*-iso8859-1
*smallFixedWidthFont:        -*-clean-medium-r-normal--12-*-*-*-*-*-*-*
--------------------------------------------------------------------------------------WINDOW STAY ON TOP
gconf-editor
/apps/metacity/window_keybindings/toggle_above - toggle_fullscreen

--------------------------------------------------------------------------------------create text issue
 sudo apt-get install t1-xfree86-nonfree 
-------------------------------------------------------------------------------------xorg composite off!!
Section "Extensions"
	Option		"Composite" "Disable"
EndSection

----------------------------------------------#scrabbled window content
Section "Screen" -> xorg.conf
...
Option "AddARGBGLXVisuals" "True"
Option "DisableGLXRootClipping" "True"
Option "DamageEvents" "True"
Option "RenderAccel" "on"
Option "NvAGP" "1"
Option "XAANoOffscreenPixmaps" 
```

---

### Post by banda on 2007-10-03
i have installed **maya 2008** here on my system .. and it is working without a hitch.. no crashes.. rendering proper.... w+lmb fixed

thanks for the great howto... even let a linux noob like me do it... Thanks!

---

### Post by banda on 2007-10-04
ooops... i hit a road block
although the installation had gone smoothly .. never produced any errors.. and i can use maya now ... every tool i tried is working perfectly....
but the problem is that i can't type !!!

i can't type in the open file dialog so i haven't been able to open any files
i've tried copy-pasting characters in the dialog but its not working...
i can type in the channel box but not in open/save dialog baxes and the mel command line
someone help!!!


(i can open files by double clicking on them but then i have to overwrite the original while saving cuz i can't give a new name....)

---

### Post by fktt on 2007-10-04
well, before saving, make a copy and rename the the copied file! as a temporary fix, will probably do, but ofc. i can understand why it can allso be a bit annoying.. allso, why not see if someone might have brought it up on the autodesk's boards.. and if not ask about it there, your self.. ;)

---

### Post by Ryokukitsune on 2007-10-06
well I have a bit of a weird problem with this install, I haven't gotten maya to work just yet though I suspect it will once my license is accepted.

on windows my license works just fine but when i try to use it under linux my MAC address seems to change and I cant figure out what to do.

I have 3 nic cards installed, a wireless and 2 wired (1 not installed) I'm wondering if the wireless is somehow conflicting though the Mac address is similar to my windows license it just seems to change by a few digits. I've tried to reactivate it with the MAC address i grabbed from my linux installation though I'm stuck because nothing is working. anyone got any ideas?

EDIT: after diving threw the thread in its entirety i found the Linux identifier and managed to get a working key. now i just have to fix that "X" mouse pointer and the middle mouse functions though thankfully those are also listed in the forum.

---

### Post by chunkified on 2007-10-07
> **Ryokukitsune said:**
> well I have a bit of a weird problem with this install, I haven't gotten maya to work just yet though I suspect it will once my license is accepted.

on windows my license works just fine but when i try to use it under linux my MAC address seems to change and I cant figure out what to do.

I have 3 nic cards installed, a wireless and 2 wired (1 not installed) I'm wondering if the wireless is somehow conflicting though the Mac address is similar to my windows license it just seems to change by a few digits. I've tried to reactivate it with the MAC address i grabbed from my linux installation though I'm stuck because nothing is working. anyone got any ideas?

EDIT: after diving threw the thread in its entirety i found the Linux identifier and managed to get a working key. now i just have to fix that "X" mouse pointer and the middle mouse functions though thankfully those are also listed in the forum.

I'm having the exact same problem. I've got 1 wireless NIC (Netgear WG311Ts) and 2 on board NIC's and Maya isn't accepting any of the MAC addresses as a valid host. I've done a lmhostid and i get the following:

> lmhostid - Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""

How did you fix this problem Ryokukitsune??

Thanks in advance

---

### Post by overlord.gaurav on 2007-10-13
I installed Maya 8.0 (64 bit)according to this HowTO.
The installation went fine for me. But when I start using Maya, I'm unable to see most the fonts.

The text isn't visible in New Project inspite I type it.

[[IMG]http://maxupload.com/thumb/EBBB3B0B.png[/IMG]](http://maxupload.com/img/EBBB3B0B.png)

The attributes of the objects are visible when the object is created but they disappear if I move the object.

[[IMG]http://maxupload.com/thumb/C57A92CE.png[/IMG]](http://maxupload.com/img/C57A92CE.png)
[[IMG]http://maxupload.com/thumb/AECEC4F4.jpg[/IMG]](http://maxupload.com/img/AECEC4F4.jpg)

Need help.

---

### Post by overlord.gaurav on 2007-10-14
Need help, anyone...!

---

### Post by MistaED on 2007-10-15
overlord.gaurav, put:

```
XLIB_SKIP_ARGB_VISUALS=1
```

In your $HOME/maya/8.0-x64/Maya.env

Maya needs all of opengl and a compositing desktop takes away the alpha channel, and that xorg variable fixes this just for maya. Also I recommend you disable compiz when using maya, it isn't stable with that running because of how openmotif works with the opengl windows (do a few middle-click drag & drops in the hypershade, it'll cause a *one minute lock-up, followed by maya crashing*)

This is a gripe of mine, it's 2007, IRIX and the indigo desktop is DEAD, we've all moved onto Qt and GTK which actually are stable and up to date, why are you living in the past autodesk? It might be more stable to run the windows version of maya in linux, now with the new wine fixing up that opengl child window bug.

-MistaED

---

### Post by overlord.gaurav on 2007-10-15
This fixed the attributes problem, but the save/load(new project) prompt is still messed up.
And thanks for your advice. But, exactly which alternative should I use for Maya? *which is potentially equal to maya*

---

### Post by Ryokukitsune on 2007-10-16
can someone help me out with the redraw problem,

when i scroll a menu (such as the attributes box) the text becomes garbled and I have to close and reopen the panel to view the information.

---

### Post by DrumBum on 2007-10-21
like some other people I was having trouble with tapping the spacebar and not being able to switch from one view to 4. Searching google I found the reason.

You can't move the mouse and hit the spacebar at the same time. I let go of the mouse and hit the spacebar and it worked fine.

[http://www.highend2d.com/boards/lofiversion/index.php/t88520.html]("http://www.highend2d.com/boards/lofiversion/index.php/t88520.html")
Looks like this has been a problem since Maya 4.

Now if anyone can find a solution . . .

---

### Post by endymon on 2007-10-24
I'm not able to: "Create - Text (option) - create" 

The only font I get listed is "Courier" and when I hit "create" I get "***Error: Unable to open postscript font file for Courier***r"

In which directory is Maya looking for those fonts ? I was thinking about creating a symlink to the actual font directory.

Tested on: Ubuntu 7.10 x64, Maya 2008 x64 but I'm pretty sure it happens in other releases as well.

Thanks for any help !

---

### Post by Yes on 2007-10-24
You do need to still buy Maya, correct?

---

### Post by squidward_tentacels on 2007-10-27
I followed this tutorial exactly as written (though I'm using Debian etch, many of the Ubuntu How-to's seem to work fine) However when I attempt to launch, I get;

$ maya 
bash: maya: command not found

$ /usr/aw/maya7.0/bin/maya.bin
 error while loading shared libraries: libMaya.so: cannot open shared object file: No such file or directory

Any thoughts would be appreciated, Thanks.

---

### Post by Engnome on 2007-11-04
Haven't checked this thread for a while (haven't used Maya for a while either) But it seems everyone keeps doing this:

> **squidward_tentacels said:**
> I followed this tutorial exactly as written (though I'm using Debian etch, many of the Ubuntu How-to's seem to work fine) However when I attempt to launch, I get;

$ maya 
bash: maya: command not found

$ /usr/aw/maya7.0/bin/maya.bin
 error while loading shared libraries: libMaya.so: cannot open shared object file: No such file or directory

Any thoughts would be appreciated, Thanks.

IIRC it was Maya not maya.bin that you launched. Check previous pages, probably been answered before.

---

### Post by yasman07 on 2007-11-12
Hello,
i have a problem with the installation... well licensing. I managed to get Maya 8.5 installed and have the correct aw.dat.

When i launch maya, the license box pops up, so i navigate it to find the aw.dat. i get green tick, then says installation complete. Once i click finish and reopen maya, the same license box appears. Tried it over and over again.

Help Please???

p.s the host id is different from my Windows and Linux. but i found the correct one (hence the little green tick)

---

### Post by yasman07 on 2007-11-13
Its ok, i sorted it out. needed to drag and drop on to the keygen.

HOwever i face another problem. When i try and navigate in maya (Alt and drag) the screen wobbles. how do make maya use these controls not the gnome package

---

### Post by yasman07 on 2007-11-13
AHA sorted it out again. Sorry for the useless thread replies. Yay maya working..

---

### Post by yasman07 on 2007-11-16
Hello again. i have a new problem. When i have a transparent object in maya, it will show me the desktop. so actually make the window transparent. Any thoughts?

---

### Post by tempo500 on 2007-11-22
did anyone notice a change from edgy to gutsy using opengl apps? i did... opengl windows regulary freeze untill i switch again to the already activated window with alt+tab... typical refresh error... i guess this has something todo with compiz... i turned it off in the xorg file... maybe someone has a tip....

---

### Post by Madj on 2007-12-01
Hi maya don't find my aw.dat wich i ve installed in the folder /var/flexlm .

when i do maya on the terminal i obtain :
~$ maya
sh: apcw: not found
madjid@ubuntu:~$ 


How i can  make sure Maya has read-access to this file.

should i ve  to use aksusbd*.deb.

If yes can someone give me the command i m suppose to do thanks

---

### Post by summerredflame on 2007-12-08
Hello,I am new to Ubuntu ,am using gutsy with Kubuntu.I have the alt+LMB problem ...No matter what keyboard style I choose ,it still moves the window  and doesnt work in maya.I have changed the radio button for starting new session in Session manager.I have tried to remove all alt key combos in keyboard shortcuts as well.

I dont know what to do?

Please help.

---

### Post by summerredflame on 2007-12-09
Found it atlast...
Heres what I did
Changed Keyboard shortcut scheme to Winkey
and in window behaviour changed Modifier key to Meta...
So now alt keys work in Maya for navigation and Win key (Meta) works for moving and resizing windows as alt used to before.

Cool.

---

### Post by pgatrick on 2007-12-27
After upgrading to gutsy maya no longer works for me. :confused: It doesn't recognize any hostid for my computer now:

> lmutil - Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""


Has anyone ever found a fix for this, or at least have some idea why it's doing this? The only thing I've changed on my computer is upgrading to kubuntu 7.10, everything else is the same as it was before when maya worked..

---

### Post by Feureau on 2008-01-03
Hi, I tried installing maya 2008 x64 on Ubuntu Gutsy x64 per guide, but I think there's a problem with the awcommon. Now, everytime I try to go to Synaptic or download ubuntu updates, I'm getting:

```
Could not initialize the package information

A unresolvable problem occurred while initializing the package information.

Please report this bug against the 'update-manager' package and include the following error message:

'E:The package awcommon needs to be reinstalled, but I can't find an archive for it.'
```

I think I need to remove and reinstall awcommon. Any Ideas how to remove it manually? (or via terminal?)

Thanks a bunch.

---

### Post by pgatrick on 2008-01-04
Maya doesn't ever seem to be removed easily, this thread should help: [http://ubuntuforums.org/showthread.php?t=462135/]("http://ubuntuforums.org/showthread.php?t=462135/")

---

### Post by fghj. on 2008-01-12
ocmask(SIG_BLOCK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [INT], 8 ) = 0
vfork()                                 = 8550
gettimeofday({1200182816, 540666}, NULL) = 0
rt_sigprocmask(SIG_SETMASK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [INT], 8 ) = 0
rt_sigprocmask(SIG_SETMASK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [INT], 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], NULL, 8 ) = 0
rt_sigsuspend([INT]

maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/robin.20080113.0107.ma
)                    = ? ERESTARTNOHAND (To be restarted)
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, {ru_utime={6, 716419}, ru_stime={0, 460028}, ...}) = 8550
wait4(-1, 0xbfed42e8, WNOHANG, 0xbfed42a0) = -1 ECHILD (No child processes)
sigreturn()                             = ? (mask now [INT CHLD])
rt_sigprocmask(SIG_BLOCK, [CHLD], NULL, 8 ) = 0
rt_sigprocmask(SIG_SETMASK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8 ) = 0
close(3)                                = 0
close(4)                                = 0
close(5)                                = 0
close(0)                                = 0
close(1)                                = 0
close(2)                                = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [INT], NULL, 8) = 0
close(0)                                = -1 EBADF (Bad file descriptor)
dup(19)                                 = 0
ioctl(0, FIONCLEX)                      = 0
close(1)                                = -1 EBADF (Bad file descriptor)
dup(17)                                 = 1
ioctl(1, FIONCLEX)                      = 0
close(2)                                = -1 EBADF (Bad file descriptor)
dup(18)                                 = 2
ioctl(2, FIONCLEX)                      = 0
lseek(16, 0, SEEK_END)                  = 7269
close(0)                                = 0
close(1)                                = 0
close(2)                                = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
read(16, "", 1024)                      = 0
ioctl(16, SNDCTL_TMR_TIMEBASE or TCGETS, 0xbfed7d58) = -1 ENOTTY (Inappropriate ioctl for device)
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
exit_group(1)                           = ?
Process 8538 detached

i get that message when i run "strace maya".
Maya loads and when it starts the 3d view is just black and the program shuts down. I got a ati mobility x300 with 8.44.3 drivers, and maya works well in windows :( anyone knows what the problem is?

---

### Post by jujoje on 2008-01-13
I'm not sure, but I reckon that your problem might well stem from the x300 and the graphics card drivers. The x300 is somewhat underpowered for maya and the ati drivers linux have always been somewhat dodgy. You could try reinstalling the drivers and seeing what happens. Unfortunately I'm not sure what the strace output means (rather beyond me), but generally speaking I've found that problems with graphics card drivers tend to lead to a signal 11 with maya.

---

### Post by fghj. on 2008-01-13
Okey, the drivers is the problem!
I unistalled the ati drivers with envy and then restarted ubuntu (without reinstalling the drivers.)
And ubuntu starts in 800x600, and i cant activate compiz :P BUT somehow i can start maya and it works fine :S without any drivers lol. I'll try to install the drivers again because i want compiz :P

---

### Post by fghj. on 2008-01-14
Anyone got any ideas of what I can do? Do I need to install windows ( =( ) again  or does anyone know how to make maya work with a Ati mobility x300 card?

---

### Post by Feureau on 2008-01-15
Thanks for the tip, I managed to "disable" awcommons and reinstall it (correctically, I think).

However, when I launch maya, it gives me: 
```
Failed to execute child process "/usr/autodesk/maya/bin/maya" (No such file or directory)
```

The thing is, I can find /usr/autodesk/maya/bin/maya alright in the file browser. Has this happen to anyone? Any ideas what to do?

PS: Installing maya 2008 x64 to Gutsy x64

---

### Post by umarali on 2008-01-16
hi this is probably an extremely stupid question, but im a newbie :P
i really really NEED maya for a uni project. im using ubuntu 7.10 (gutsy) and i tried lookin for a linux version of maya but couldnt find any so i bought the windows version.
but...all i have is a single .exe setup file...
how do i install it? :confused: :oops: do i need to install wine or something? 
any help would be appreciated

edit: i got maya 8

---

### Post by azexian on 2008-01-16
> **umarali said:**
> hi this is probably an extremely stupid question, but im a newbie :P
i really really NEED maya for a uni project. im using ubuntu 7.10 (gutsy) and i tried lookin for a linux version of maya but couldnt find any so i bought the windows version.
but...all i have is a single .exe setup file...
how do i install it? :confused: :oops: do i need to install wine or something? 
any help would be appreciated

edit: i got maya 8

umarali are you sure that autodesk don't offer installation of any once you have payed for a licence, at least between the oses?, if there's no link, you could try emailing them, I'm guessing once you've payed the huge cost for this, they'd be more then happy to help :d

I just managed to install following this guide, very nice thankyou :)

---

### Post by sglider12 on 2008-01-26
Alright..
I haven't been keeping up with this thread (as I just found it today :P) but I was wondering..

I just installed Maya 2008 on my Ubuntu Gutsy Gibbon laptop..
I'm trying to run the FlexLM License Tools application but I can't seem to find it...

Anyone know how?

In Windows I know you go to Start -> All Programs -> Autodesk -> Common Utilities -> FlexLM License Utilities 

Thx

---

### Post by azexian on 2008-01-26
> **sglider12 said:**
> Alright..
I haven't been keeping up with this thread (as I just found it today :P) but I was wondering..

I just installed Maya 2008 on my Ubuntu Gutsy Gibbon laptop..
I'm trying to run the FlexLM License Tools application but I can't seem to find it...

Anyone know how?

In Windows I know you go to Start -> All Programs -> Autodesk -> Common Utilities -> FlexLM License Utilities 

Thx

sglider12, you need to copy your licence file into /var/flexlm/ if it doesn't already exist, create it, you should then be able to run maya.

---

### Post by sglider12 on 2008-01-26
Well, I can already run Maya. I just want to know how to get to the FlexLM License Utilities app....thx tho

---

### Post by 3shirtlessmen on 2008-01-30
This might sound very noobish,

but where do you get the RPMs? I found some maya 2008 rpm numbers but when using them in the rpm command the terminal spits out that the directory or file doesn't exist.

Now, the autodesk website has a download for windows and mac, I could install and run through wine... bad idea?

This is the demo speaking...

---

### Post by ewg118 on 2008-01-31
> **fghj. said:**
> Okey, the drivers is the problem!
I unistalled the ati drivers with envy and then restarted ubuntu (without reinstalling the drivers.)
And ubuntu starts in 800x600, and i cant activate compiz :P BUT somehow i can start maya and it works fine :S without any drivers lol. I'll try to install the drivers again because i want compiz :P

I'm also getting the same error you ran into.  Arg, must be an ATI thing, which is too bad considering how much better their drivers have gotten in the last two months.  Unless anyone knows anything more, I might just have to wait it out until the issue is resolved.

I'm running ubuntu x64 with a Radeon HD3850 with the most recent ATI drivers (last week).

---

### Post by antonyant11 on 2008-02-14
at the end of converting the rpms i get this

Package build failed. Here's the log:
dh_testdir
dh_testdir
dh_testroot
dh_clean -k -d
dh_installdirs
dh_installdocs
dh_installchangelogs
find . -maxdepth 1 -mindepth 1 -not -name debian -print0 | \
                xargs -0 -r -i cp -a {} debian/maya8-0-docs-en-us
dh_compress
dh_makeshlibs
dh_installdeb
dh_shlibdeps
dh_gencontrol
dpkg-gencontrol: error: current build architecture amd64 does not appear in package's list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
        find Maya8_0-docs_en_US-8.0 -type d -exec chmod 755 {} ;
find: Maya8_0-docs_en_US-8.0: No such file or directory
        rm -rf Maya8_0-docs_en_US-8.0

Is there any way around this?

---

### Post by recallfx on 2008-02-17
```
Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""
```

It appears, that flexlm specifically needs eth0. If your network card has some different number e.g. eth1, then you must change it.

Edit file **/etc/udev/rules.d/70-persistent-net.rules ** so the line which contains NAME="eth0", is surely your default working network device.

In my case, it was assigned to an old nic, that I even dont have anymore.

Now restart ubuntu, and now it should work.

---

### Post by Wisp2006 on 2008-02-17
Hy all,
I have managed to install Maya 8 SP1 on my Gutsy x64 machine... I had solved a small problem with the licence (which i think it is exactly the problem written above by recallfx). But now I've run in another issue.
It happens to get serious artifact problems with or without compiz, but surprisingly are more severe with compiz deactivated. 
[[IMG]http://img518.imageshack.us/img518/2425/compizofflg0.th.png[/IMG]](http://img518.imageshack.us/my.php?image=compizofflg0.png)
Any ideas why this is happening?... I can work somewhat by maximizing/minimizing the window while compiz is enabled, but it's getting on my nerves since new window frames will invariably corrupt the display... I have an Ati 3850, drivers are installed properly. The most interesting issue is that the same effect occurs when I run certain screensavers, which means that it is a driver issue; but the driver seem to work fine, fglrxinfo and glxinfo output the normal, expected results. Is something that needs specified in xorg.conf and I didn't find out?...

---

### Post by endymon on 2008-02-21
I finally found the solution to the TextCurve tool.

1) Make sure you have the MS fonts installed.  Applications - add/remove - "Microsoft Core Fonts"

2) I setup my xorg.conf like this:
Section "Files"
FontPath "/usr/share/fonts/"
FontPath "/usr/share/fonts/truetype"
FontPath "/usr/share/fonts/type1"
FontPath "/usr/share/fonts/X11"
EndSection

I'm sure that section for xorg.conf can be trimmed but I'm really happy that it works now. 

Enjoy a working TextCurve tool for the first time ;-)

---

### Post by &#1052;&#1080;&#1093;&#1072;&#1080;&#1083; &#1053;&#1072;&#1081;&#1076;&#1077;&#1085;&#1086;&#1074; on 2008-02-24
> **endymon said:**
> 
...

1) Make sure you have the MS fonts installed.  Applications - add/remove - "Microsoft Core Fonts"

2) I setup my xorg.conf like this:
Section "Files"
FontPath "/usr/share/fonts/"
FontPath "/usr/share/fonts/truetype"
FontPath "/usr/share/fonts/type1"
FontPath "/usr/share/fonts/X11"
EndSection

...


It does not work for me!:(

I also tried all symbolic links combos I have found on the net - no luck!

Does anyone know for sure in which dir **maya 2008** is looking for those fonts???

pls, HELP
10x

sorry for my english

---

### Post by Repgahroll on 2008-02-27
I was thinking about sometime in the future buy a Maya license...

But i'd seen the 2008 version at my friend's house (FC8), and can say that it runs very slow on Linux compared to the other OS versions... specially the rendering... it's more than twice slower!

I think that compared to the price of the Maya License, is better to buy also a Windows (XP, or other cheaper.. dunno) License, so you'll can use everything that the app offers in performance terms... it's better to dual boot to Windows than buy a 3 times faster hardware to run it on Linux with the same performance that it could run on Windows without any upgrades...

Maya is good, but there's no respect from Autodesk to Linux users.

For now i'm happy using Blender, wich runs blazing fast on Linux.

Sorry my englsih.

---

### Post by wawarren on 2008-02-28
I can't copy or paste any text in Maya 8.5 x64.  Does anyone else have this problem?  

To clarify, I can't copy + paste from the attribute editor, channel editor, script editor, etc.  using Ctrl+c / Ctrl+v.  

Any ideas?

---

### Post by luckyluca on 2008-02-28
Exactly the same problem!
maya 8.5 64bit on ubuntu7.1 64bit.

I've checked at work somebody else has the same problem too.

Any idea?

very frustrating...

---

### Post by wawarren on 2008-02-29
> **luckyluca said:**
> Exactly the same problem!
maya 8.5 64bit on ubuntu7.1 64bit.

I've checked at work somebody else has the same problem too.

Any idea?

very frustrating...

Hey Luca.  I thought it was probably best we concluded this somewhere besides the sidefx forums since it strayed a bit off topic.  :)

Anyhow, this is very frustrating and I'm sure others have experienced it as well.  

I've tried changing my hotkeys and everything.  Maya won't even copy if I Right-click and choose to copy (where available) It doesn't seem to have access to the clipboard for some reason.  

Any takers?  

Thanks,
Alan

---

### Post by luckyluca on 2008-03-03
Solved!

It is a problem with gnome. I've solved it by installing Kubuntu.
If you fancy you could simply add kde to your existing ubuntu installation as well, but I preferred starting clean.

So cut copy and paste now work fine.

However I get a small annoying problem in the hypershade.
when I drag and drop a connection to a node the pop up menu (with the list of avail. inputs) flickers and is redrawn underneath the node.
This happens when I move the mouse cursor. By appearing under the material node it becomes unusable. This is not a showstopper problem but nevertheless annoying. Do you encounter the same?

Thanks
Luca

---

### Post by wawarren on 2008-03-06
> **luckyluca said:**
> Solved!

It is a problem with gnome. I've solved it by installing Kubuntu.
If you fancy you could simply add kde to your existing ubuntu installation as well, but I preferred starting clean.

So cut copy and paste now work fine.

However I get a small annoying problem in the hypershade.
when I drag and drop a connection to a node the pop up menu (with the list of avail. inputs) flickers and is redrawn underneath the node.
This happens when I move the mouse cursor. By appearing under the material node it becomes unusable. This is not a showstopper problem but nevertheless annoying. Do you encounter the same?

Thanks
Luca

Strange, I tried Maya in KDE and copy + paste still didn't work for me.  

Oh well, I would rather avoid KDE anyways.

---

### Post by dandixon on 2008-03-07
Thanks for the help.
I was wounder if someone can help with how I might go about installing bonus tools for 2008 lunix.
As I'm a new user to lunix.

Any help would be great.
Dan

---

### Post by wawarren on 2008-03-07
> **dandixon said:**
> Thanks for the help.
I was wounder if someone can help with how I might go about installing bonus tools for 2008 lunix.
As I'm a new user to lunix.

Any help would be great.
Dan

You should be able to convert the RPM to a .deb with alien and type sudo dpkg -i mayabonustools2008-i386.deb (whatever it's called)

---

### Post by dandixon on 2008-03-08
I got it. Something to do with the fold i had the file in.
Thanks



when i use (for i in *.rpm; do sudo alien -cv $i; done)
to unpack the rpm file, it creates a folder for MayaBonusTools2008_0_x64-2008.0 and then I run your text (sudo dpkg -i MayaBonusTools2008_0_x64-2008.0) I get an error. Am I using the right command to unpack the .rpm file
Thanks

---

### Post by wawarren on 2008-03-08
dpkg is for files ending with the .DEB file extension. The command I listed (sudo dpkg -i) will only work on .DEB files.  

When using Alien to convert your RPM you don't need to use a for loop unless you're converting multiple .RPM files.  In this case you should only have 1 .RPM file, so this command will work. 

sudo alien -i /path/to/file.rpm

It should make one .DEB file in the same directory as your .RPM.  Then, you can just double-click the .DEB file to install.

---

### Post by dandixon on 2008-03-08
Hey wawarren
Thanks for the help so far.
I thought I had it. I got it to unpack the file in the right dir . But when I launch Maya the bonus tools don't load, So I run the bonusToolsMenus.mel script and the tool bar loads but the tools won't run because the plug ins aren't sourcing.

I can't copy the userSetup.mel to the right fold because i don't have root and I don't now the command to change the folder permissions.
Can you help me out?
Do I need to set up some env variable?

Dan

---

### Post by wawarren on 2008-03-10
The only thing I can think of is $MAYA_PLUGIN_PATH.  You can add this to your Maya.env file, which should be in your Maya folder inside HOME.  You could also define it in /etc/profile (sudo gedit /etc/profile)

syntax for environment var's 

export MAYA_PLUGIN_PATH=/usr/autodesk/Maya/some/folder

to change permissions on a file.  sudo chmod 777 /path/to/file/filename.mel

---

### Post by dandixon on 2008-03-17
Install problems now.
Had it running great before but Now no go.

After I install it and try to run Maya I get this error
**Could not launch menu item**
Failed to execute child process "/usr/autodesk/maya/bin/maya" (No such file or directory)

The install goes good until I install the awcommon_10.80-16_amd64.deb
> ddixon@ddixon-LINUX:~/Desktop/linux-amd64$ sudo dpkg -i awcommon_10.80-16_amd64.deb 
(Reading database ... 118358 files and directories currently installed.)
Preparing to replace awcommon 10.80-16 (using awcommon_10.80-16_amd64.deb) ...
Unpacking replacement awcommon ...
/usr/bin/test: invalid integer `upgrade'
exit: 26: Illegal number: -0
dpkg: warning - old post-removal script returned error exit status 2
dpkg - trying script from the new package instead ...
/usr/bin/test: invalid integer `failed-upgrade'
exit: 26: Illegal number: -0
dpkg: error processing awcommon_10.80-16_amd64.deb (--install):
 subprocess new post-removal script returned error exit status 2
/usr/bin/test: invalid integer `abort-upgrade'
exit: 26: Illegal number: -0
dpkg: error while cleaning up:
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 awcommon_10.80-16_amd64.deb


And last but lease When I got to Synaptic Package Manager to uninstall what I have did to try to redo the process I get
**An error occured**
> E: The package awcommon needs to be reinstalled, but I can't find an archive for it.
E: Internal error opening cache (1). Please report.
Just as I thought I hand the upper hand with Linux
SOLVED

---

### Post by jlindbergh on 2008-03-18
> **&#1052 said:**
> It does not work for me!:(

I also tried all symbolic links combos I have found on the net - no luck!

Does anyone know for sure in which dir **maya 2008** is looking for those fonts???

pls, HELP
10x

sorry for my english

Same for me. Although I'm running Maya 8.5, I've also tried both adding /usr/share/fonts/truetype, type1 and X11as FontPath in xorg.conf and linking from /usr/X11R6/lib/X11->/usr/share/fonts but I still get following output from Maya:
// Error: Unable to open postscript font file for Courier // 
// Error: Command textCurves failed. Open Script Editor for details. //
when trying Create->Text

---

### Post by falkaholic on 2008-03-26
For me this procedure worked as described on my 7.10 i386.

Maya seems to act a little weird so far. Could just be the way it acts on *unix, this is my first time using it on linux.

---

### Post by aeacides on 2008-03-31
Hi guys,

I don't know if it has been reported yet (didn't read the 30 post pages, only a couple of them), hehe.

So, I Installed/Updated Alien, and other needed packages. Then I copy/paste  
```

for i in *.rpm; do sudo alien -cv $i; done
```

And got this:

```
        LANG=C rpm -qp --queryformat %{SUMMARY} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{POSTIN} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{NAME} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{POSTUN} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{PREUN} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{RELEASE} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{PREFIXES} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{COPYRIGHT} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{DESCRIPTION} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{ARCH} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{VERSION} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qp --queryformat %{PREIN} awcommon-1080-15x86_64.rpm
        LANG=C rpm -qcp awcommon-1080-15x86_64.rpm
        rpm -qpi awcommon-1080-15x86_64.rpm
        LANG=C rpm -qpl awcommon-1080-15x86_64.rpm
        mkdir AWCommon-10.80
[B][COLOR="Red"]mkdir: ne peut créer le répertoire `AWCommon-10.80': Système de fichiers accessible en lecture seulement
unable to mkdir AWCommon-10.80:  at /usr/share/perl5/Alien/Package.pm line 257.[/COLOR][/B]
        LANG=C rpm -qp --queryformat %{SUMMARY} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{POSTIN} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{NAME} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{POSTUN} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{PREUN} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{RELEASE} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{PREFIXES} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{COPYRIGHT} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{DESCRIPTION} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{ARCH} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{VERSION} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qp --queryformat %{PREIN} awcommon-server-1080-15x86.rpm
        LANG=C rpm -qcp awcommon-server-1080-15x86.rpm
        rpm -qpi awcommon-server-1080-15x86.rpm
        LANG=C rpm -qpl awcommon-server-1080-15x86.rpm
        mkdir AWCommon-server-10.80
[B][COLOR="Red"]mkdir: ne peut créer le répertoire `AWCommon-server-10.80': Système de fichiers accessible en lecture seulement
unable to mkdir AWCommon-server-10.80:  at /usr/share/perl5/Alien/Package.pm line 257.[/COLOR][/B]
        LANG=C rpm -qp --queryformat %{SUMMARY} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{POSTIN} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{NAME} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{POSTUN} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{PREUN} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{RELEASE} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{PREFIXES} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{COPYRIGHT} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{DESCRIPTION} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{ARCH} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{VERSION} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qp --queryformat %{PREIN} maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qcp maya2008_0_64-20080-134x86.rpm
        rpm -qpi maya2008_0_64-20080-134x86.rpm
        LANG=C rpm -qpl maya2008_0_64-20080-134x86.rpm
        mkdir Maya2008_0_64-2008.0
[B][COLOR="Red"]mkdir: ne peut créer le répertoire `Maya2008_0_64-2008.0': Système de fichiers accessible en lecture seulement
unable to mkdir Maya2008_0_64-2008.0:  at /usr/share/perl5/Alien/Package.pm line 257.[/COLOR][/B]
        LANG=C rpm -qp --queryformat %{SUMMARY} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{POSTIN} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{NAME} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{POSTUN} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{PREUN} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{RELEASE} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{PREFIXES} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{COPYRIGHT} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{DESCRIPTION} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{ARCH} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{VERSION} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qp --queryformat %{PREIN} maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qcp maya2008_0_64-docs_en_us-2.rpm
        rpm -qpi maya2008_0_64-docs_en_us-2.rpm
        LANG=C rpm -qpl maya2008_0_64-docs_en_us-2.rpm
        mkdir Maya2008_0_64-docs_en_US-2008.0
[COLOR="Red"]
[B]mkdir: ne peut créer le répertoire `Maya2008_0_64-docs_en_US-2008.0': Système de fichiers accessible en lecture seulement
unable to mkdir Maya2008_0_64-docs_en_US-2008.0:  at /usr/share/perl5/Alien/Package.pm line 257.[/B][/COLOR]


```

Any idea how to fix this? I tryed chmod 777 on Package.pm, without result. Basically, the error message says that package.pm is accessible in read only. I just don't understand why it's trying to create a directory on a .pm file?!

Thanks for your help,

have a nice day :- )

edit::

I've forget this tiny line: Copy over all rpm installation files to a local directory. 

Works fine now. Sorry about that.

---

### Post by samjcarter on 2008-04-02
> **smudge said:**
> Hi guys,

I'm generally a pretty good linux hacker and have no problem installing maya and it's licence it and found this post very good. One thing I do have problems with however is when I load Maya, I cannot alt+mousebutton to scroll around. I'm using KDE, and alt+mousebutton moves the whole screen around, not the camera! Anyone have this problem, or know a fix?

Keep up the good work! :KS

The default key binding in K maps the ALT key to the move window function... thats why maya's camera isnt responding. you need to change the key binding to allow maya to work (eg swap it with the windows/super key). I'm not 100% on where that setting is in KDE but have a funny feeling if you go into your control panel its in the window manager preferences. You just gotta free that ALT key up and maya should cooperate.

---

### Post by warby on 2008-04-05
hi guys i am trieng to install maya 7 under ubuntu 7.10 with gnome. 
i AM a complete linux noob i have linux running on my machine for a total of 2 days now so please go easy on me.
however i am not new to 3d art at all i have been using maya commercially for over 6 years now. one of my linux using friends recommended this forum ... i believe he used the words "the most helpful place on the internet" so here i am :D


this is the problem:
- i dont know how to launch maya  ?
- i mean like where is the .exe ... is the maya.bin the equivalent ?
- when i double click the maya.bin absolutely nothing happens ?!
- am i even in the right folder ?! filesystem/aw/maya7.0/bin/maya.bin  is that right ?!



this is what i did
-i got the rpms on the hd
-i used somethign (alien ?!) to install the rpms but it really just extracted the files to the wrong place and deleted the stuff afterwards
-than i converted the rpms to deb files
- i used the terminal to dpkg all the deb files
- i also did the sudo ln -s /usr/aw /aw as described in the tutorial on the front page ...i am not sure what that does though 
-i copied my aw.dat to the flexlm folder under /var

shouldn't that be it ?! in the package manager all packages awcommon /server maya and even the doc stuff is installed fine !
but something that i can see allready that cant be right is that i have like 100.000 aw folders stacked into each other filesystem/aw/aw/aw/aw/aw/aw/aw/aw/aw/aw/aw/aw/aw ... and so on i don't even know how many there are. that is wrong right ? you guys don't have that ???

---

### Post by milly77 on 2008-04-15
Got this problem?

Copyright (c) 1989-2006 Macrovision Europe Ltd. and/or Macrovision Corporation. All Rights Reserved.
The FLEXlm host ID of this machine is ""


The problem seems to stem from a bug in Ununtu Gutsy 7.10! I think it has to do something with adapter changing on each reboot..

1. Go to /etc/udev/rules.d and create a backup of 70-persistent-net.rules


2. Open  70-persistent-net.rules

(my looked something like this)

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:ee:a9:16", NAME="eth0"

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:fb:e3:7c", NAME="eth1"

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:ca:68:0f", NAME="eth2"

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:44:f1:a8", NAME="eth3"

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:92:c4:e1", NAME="eth4"

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="?*", ATTRS{address}=="00:00:6c:ae:6b:c3", NAME="eth5"


3. Rremove the entries and add this line)

SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"

(my file looked like this afterwords)

# This file maintains persistent names for network interfaces.
# See udev(7) for syntax.
#
# Entries are automatically added by the 75-persistent-net-generator.rules
# file; however you are also free to add your own entries.

# PCI device 0x10de:0x07dc (forcedeth)
SUBSYSTEM=="net", DRIVERS=="forcedeth", NAME="eth0"


4. Save the file..

5. Reboot the system..

6. Now either type:

sudo ifconfig

to find out your host ID address, or go to /usr/aw/COM/bin and type in:

./lmhostid

7. That's it!

Sources

[http://ubuntuforums.org/showthread.php?t=66859&page=29](http://ubuntuforums.org/showthread.php?t=66859&page=29) thanks to recallfx!

[https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382](https://bugs.launchpad.net/ubuntu/+source/udev/+bug/145382)

---

### Post by milly77 on 2008-04-15
This is a scheme I use for Maya 2008, combustion/shake like.. I will have to update it sometime though.. either way enjoy.

Maya 2008 scheme location /usr/autodesk/maya2008/app-defaults

Backup original and replace entries with this:

*extraLargeBoldLabelFont:    -*-helvetica-bold-r-normal-*-17-*-*-*-*-*-iso8859-1
*largeBoldLabelFont:         -*-helvetica-bold-r-normal-*-14-*-*-*-*-*-iso8859-1
*boldLabelFont:              -*-helvetica-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*smallBoldLabelFont:         -*-helvetica-bold-r-normal-*-12-*-*-*-*-*-iso8859-1
*tinyBoldLabelFont:          -*-helvetica-bold-r-normal-*-10-*-*-*-*-*-iso8859-1
*plainLabelFont:             -*-helvetica-medium-r-normal-*-12-*-*-*-*-*-iso8859-1
*smallPlainLabelFont:        -*-helvetica-medium-r-normal-*-10-*-*-*-*-*-iso8859-1
*obliqueLabelFont:           -*-helvetica-bold-o-normal-*-12-*-*-*-*-*-iso8859-1
*smallObliqueLabelFont:      -*-helvetica-bold-o-normal-*-10-*-*-*-*-*-iso8859-1
*fixedWidthFont:             -*-fixed-medium-r-normal--13-*-*-*-*-*-iso8859-1
*smallFixedWidthFont:        -*-clean-medium-r-normal--12-*-*-*-*-*-*-*
*basicBackground: #585858
Maya*Background:             #585858
*textForeground: #cbcbcb
*textFieldBackground: #787878
*readOnlyBackground: #686868
*buttonBackground: #2c2c2c
*scrollBarTroughColor: #3e3e3e
*scrollBarControlBackground: #a9aabd
*indicatorBackground: #2a2a2a
*radioColor: #000000
*checkColor: #ffff1e
*blueSelectBackgroundColor1: #3884c4
*blueSelectBackgroundColor2: #81a7c1
*drawingAreaBackground: #2e344b
*drawingAreaContrastColor1: #872020
*drawingAreaContrastColor2: #221578
*drawingAreaContrastColor3: #005600
*drawingAreaContrastColor4: #4c167a
*scrolledListBackground: #3c3c3c
*textBackground: #585858
*highlightColor1: #ff0000
*highlightColor2: #5554ff
*highlightColor3: #00ff00
*highlightColor4: #850eea
*highlightColor5: #ff8b00
*highlightColor6: #00ffff
*highlightColor7: #ff00ff
*HighlightColor8: #ffff00
*wMBackground: #ffffff
*wMForeground: #000000
*wMActiveBackground: #ffffff
*wMActiveForeground: #000000
*textSelectedBackground: #373737
*textSelectedForeground: #ffef6c
*indicatorLightColor: #000000
*selectFillColor: #ffff00
*redColor: #ef001c
*orangeColor: #e46800
*yellowColor: #d9b000
*greenColor: #169612
*blueColor: #924c39
*brownColor: #743f3f
*purpleColor: #924f95
*errorColor: #c60000
*warningColor: #0067a8
*informationColor: #218719
*alternateBackground1: #84677c
*alternateBackground2: #6d758b
*alternateBackground3: #6d758b
*alternateBackground4: #286165
*alternateBackground5: #59598a
*alternateBackground6: #d1d1c9
*disabledTextForeground: #e2e2e2
*layerAdjustmentTextForeground:	#e56929
*lightRadioFillColor: #e2e2e2
*disabledCheckColor: #949494

---

### Post by Guy Gizmo on 2008-04-16
> **jlindbergh said:**
> Same for me. Although I'm running Maya 8.5, I've also tried both adding /usr/share/fonts/truetype, type1 and X11as FontPath in xorg.conf and linking from /usr/X11R6/lib/X11->/usr/share/fonts but I still get following output from Maya:
// Error: Unable to open postscript font file for Courier // 
// Error: Command textCurves failed. Open Script Editor for details. //
when trying Create->Text
I've got exactly the same problem.  I've tried all of the suggestions in this thread for fixing it to no avail.  If someone knows a way of fixing this, I'd be very appreciative!

---

### Post by zeal0t on 2008-04-30
> **endymon said:**
> I'm not able to: "Create - Text (option) - create" 

The only font I get listed is "Courier" and when I hit "create" I get "***Error: Unable to open postscript font file for Courier***r"

In which directory is Maya looking for those fonts ? I was thinking about creating a symlink to the actual font directory.

Tested on: Ubuntu 7.10 x64, Maya 2008 x64 but I'm pretty sure it happens in other releases as well.

Thanks for any help !

I got the same problem, Please help me, I appreciate your help.

---

### Post by Qrikko on 2008-05-08
Hi, I just want to add some information that caused me a lot of problems, to this (wonderful I might add) Installation howto.

To save you time you kind of aren't interested in this post if you don't have a problem with corrupt files and maya crashing on load/import of your saved work.

If however you do have these problems I hope this can help you.

Namely a problem I had for a long while, first of all I would recommend everyone to keep .ma files at least for backup, because well it is so annoying loosing a lot of work (which I did).

(I save like this but I am paranoid after the problems I had..
1) save as: tmp.ma
2) open tmp.ma
3) save as cleanWorkingCopy.ma
)

To the PROBLEM!
The problem I had was that sometimes when I saved a file I couldn't open it and Maya would crash with a segmentation fault (if I don't remember wrong). BUT be able to save a backup in /usr/tmp you know that kind of .ma files that it save to try to not completely kill your work?) So I was able to retrieve my work from it after gedit:ing it into life again.. *phew*.

So I figured out that if I took away all Lamberts (and sometimes some raw in the end) I could get life in the file again, so I knew that it was something in my model and less interesting what I did was that I cleaned up the model in outliner and hypergraph (or what they are called) so I only had polygons left deleted history and saved again. And now I got a working file! :D

and after this I saved very much and was very careful AND I am not 100% sure but everything point toward my files getting corrupt from using the extrude tool (not to extrude but if I use the tool that can transform/rotate and scale) so I have to extrude and at once change to for example the translation tool (w) and I get rid of corrupt files.

I don't mind too much it's a nice tool but since everything else work wonder I just avoid using this tool.

Hope anyone that run into this problem just saved some time running maya in gdb, reading forums and what not.

---

### Post by TaintedFungus on 2008-05-10
> **unlotto said:**
> Are any of you having issues with Maya and importing wav files? I got it to work in i386, (by system linking libaudiofile.so)

on amd64 (and 64bit maya) it imports, but the sound is all scrambled and won't playback properly.

Same thing happens on a variety of other distro's like Fedora Core 7 and CentOS 5 and OpenSuse 10.2

without sound, maya is useless to our animators.

Hi guys. I'm running the 64-bit version of Maya2008 on gutsy and ran into this same issue. After reading a thread on the autodesk forums, ([http://area.autodesk.com/index.php/forums/viewthread/1475/#4995](http://area.autodesk.com/index.php/forums/viewthread/1475/#4995)) I installed libaudiofile-dev using synaptic, and so far it seems to have fixed the problem. 

I'm pretty much a linux newb, hence I'm not sure why it works or if it works in every scenario, but I do know that immediately after installing the package, I was able to import wav files into Maya. I hope this helps a bit.

---

### Post by tadeusz666 on 2008-06-03
Hey Im running Hardy amd64 and installed Maya 64bit and did what
**TaintedFungus** suggested and also did the linking of the **libaudiofile.so**,
but maya still dosent even wanna let me add the sound. It says [B]No sound 
available[/B] when i click the timeline. !?

Does anyone have an idea as to why it dosent work !? My sound has been
working like a dream since I installed it so I have no clue what so ever.

Really need sound in maya and dont want to go back to windows

---

### Post by TaintedFungus on 2008-06-07
> **tadeusz666 said:**
> Hey Im running Hardy amd64 and installed Maya 64bit and did what
**TaintedFungus** suggested and also did the linking of the **libaudiofile.so**,
but maya still dosent even wanna let me add the sound. It says [B]No sound 
available[/B] when i click the timeline. !?

Does anyone have an idea as to why it dosent work !? My sound has been
working like a dream since I installed it so I have no clue what so ever.

Really need sound in maya and dont want to go back to windows


Does it say '**No Sound Available**' in the script editor or in the menu box when you right click the timeline? If it's in the menu box (and your script editor is error-free), then try re-importing your sound file via the **File>Import** method. It also wont recognize it if it's anything other than a .wav file.

---

### Post by tadeusz666 on 2008-06-07
> **TaintedFungus said:**
> Does it say '**No Sound Available**' in the script editor or in the menu box when you right click the timeline? If it's in the menu box (and your script editor is error-free), then try re-importing your sound file via the **File>Import** method. It also wont recognize it if it's anything other than a .wav file.

Thanks for replying, yes when i right-clicked the timeline and choose sound then it would be grayed out but saying **No sound Available** And the script editor was error-free as well.

Then I imported it via file > Import and found that I could now choose it when I right click the timeline. Also it played just fine no problems what so ever. 

Anyways works fine now ! thanks :)

---

### Post by spiritsmoke on 2008-06-16
when I try to copy my aw.dat files to my Flexlm dir. my pc said that the file
aw.dat does not exist. Where Do I find the file aw.dat. I'v got an ISO image file of Maya8 5.
running a XPS M1530
GeForce 8400 mGS

Maya starts up when I typ Maya in the console, but It states that their is 
no license and prompts me for a license. I'v got windows xp student edition 
as a Dual boot on my pc. If their is a way to port a licence for one OS to another OS that would be effective too.

thanks in advance for your help
   

a windows addict screaming for help 
             Ubuntu makes an intervention, and all was right with the world

---

### Post by TaintedFungus on 2008-06-26
> **spiritsmoke said:**
> when I try to copy my aw.dat files to my Flexlm dir. my pc said that the file
aw.dat does not exist. Where Do I find the file aw.dat. I'v got an ISO image file of Maya8 5.
running a XPS M1530
GeForce 8400 mGS

Maya starts up when I typ Maya in the console, but It states that their is 
no license and prompts me for a license. I'v got windows xp student edition 
as a Dual boot on my pc. If their is a way to port a licence for one OS to another OS that would be effective too.

thanks in advance for your help
   

a windows addict screaming for help 
             Ubuntu makes an intervention, and all was right with the world

There should be a .exe file somewhere on the install dvd (It's called linux_webkey2008.exe on Maya 2008 ). Run it windows and you'll get the aw.dat file to copy over.

---

### Post by dcbc on 2008-07-02
i get this error.please help

[b] License Installation Report

Installing from license file /var/flexlm/aw.dat.
Input license contains 1 license(s) matching this computer.

License #1

Attempting Installation to license file: /var/flexlm/aw2.dat
Source file /var/flexlm/aw.dat contains errors and/or warnings. Please see below for detailed information.

Successful Operations:
(none)


Warnings:
(none)


Errors:
Data on line 1 is not recognized as FLEXlm data. Source: /var/flexlm/aw.dat


End of license installation report.[/b]

---

### Post by eternal_sage on 2008-09-06
has anyone else had trouble installing the license file? i am getting stuck in a repeating loop asking me to install the license (which i do) then it asks me again (and i do it again) etc etc etc.

this is really odd, and i've never had this issue before on windows.

---

### Post by sorwrith on 2008-09-10
In Maya 2008 im getting the same problems as the poster above me... i installed fine following the directions but im stuck in a license loop in ubuntu.. on vista i had no problems with it...

---

### Post by dubacik22 on 2008-10-02
i have similar issue an after spending some time with google i have found this.. the main difference betwen other howtos is that youre hardware ID or wtf it is contains two groups of numbers. and to aw.dat you got to copy just one group.. its up on you which group you choose.. and paste it to aw.dat without -> "" <-(i dont know what is its name:) [http://crmgen.com/2008/autodesk-maya-2008-unlimited-tested-working-rs.html]("http://crmgen.com/2008/autodesk-maya-2008-unlimited-tested-working-rs.html")

---

### Post by tortiman on 2008-10-07
I have maya in rpm format and need convert to deb for installing, but when it's converting with alien show this message error:

Unpacking of 'Maya2008_0-2008.0-142.i686.rpm' failed at /usr/share/perl5/Alien/Package/Rpm.pm line 153.

What happen?

---

### Post by kougaru on 2008-10-11
Hello, I successfully installed Maya 2008 using this guide. It runs pretty well, but I only have one problem, whenever I try to use the sculpt geometry tool Maya crashes. I tried to google the problem with no luck. Would anyone have any ideas on this subject?

I'm running Hardy with Nvidia drivers from envy.

---

### Post by krystian75 on 2008-10-26
kougaru have you install maya on ubuntu 64bit?

---

### Post by kougaru on 2008-10-29
I've installed it both on a 32bit and a 64bit system. The 64bit system was actually working for a while but then it started having the same errors.

Edit: It seems to happen with any tool using a brush. Ex: Paint Effects, Sculpt Tool, 3D Paint Tool etc. Any time I select any of these tools Maya crashes.

---

### Post by cgwabbit on 2008-11-03
Anyone have any luck installing 64-bit Maya 2009 under Ubuntu 8.10?
I can get the Maya package converted to .deb and installed fine, but no such luck with the AWCommon package.
I get the errors:

dpkg-shlibdeps: failure: couldn't find library libXm.so.2 needed by debian/awcommon/usr/aw/COM/bin/installKey (its RPATH is '').

and

dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)

I've tried installing lesstif2 and libmotif3, but looking at the unpacked directories that alien leaves laying around, I think the libXm.so.2 that it is looking for is in its own /aw/COM/lib directory.
I don't know exactly how to set LD_LIBRARY_PATH to make this look in its own package.  I tried: "export LD_LIBRARY_PATH=/aw/COM/lib/" but it didn't help.

The error I get when trying to run maya is the license file error, "can't find acpw".  My challenge I believe is due to the fact that I have a HASP key dongle.  I gathered that I didn't need the HASP tools as Maya handles this somehow in the AWCommon package, but perhaps I'm mistaken.  I did try installing the HASP aksusbd packages, but couldn't get those to work either.

thanks in advance for any help! :)

---

### Post by derby_sv on 2008-11-05
Try to install by using the RPM Package Manager:

sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

cd linux-amd64/
sudo rpm -ivh --nodeps AWCommon-****.rpm Maya2009_****.rpm

---

### Post by alegria071 on 2008-11-06
> **zeal0t said:**
> I got the same problem, Please help me, I appreciate your help.


Hi,

 I got the same problem in ubuntu 8.04 x86_64 + maya2008.

 Anyone know where maya 2008 is looking for the fonts???

 any idea??

thanks,

---

### Post by alegria071 on 2008-11-06
hi,

I have de same problem. do you find the solution?

thanks,

marcela alegria

---

### Post by cgwabbit on 2008-11-09
> **derby_sv said:**
> Try to install by using the RPM Package Manager:

sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

cd linux-amd64/
sudo rpm -ivh --nodeps AWCommon-****.rpm Maya2009_****.rpm

I had kinda tried this before, but I went back and uninstalled the .deb package and followed these steps with the same result.
There seems to be some package/requirement in the lmdiag and other license tools that I don't have from a fresh install of Ubuntu.  I tried linking sh to dash, but that didn't make any difference.
The only program in the common files directories that will run is AWinfo, but I think that's a shell script.
I tried to do a search to figure out how one determines what library or sub-program is generating the "not found" error when trying to run these programs, but I can't figure that out.  Is there some way to make the shell verbose about its error messages?  "not found" when the main executable is most definitely there and has the correct permissions is not tremendously helpful.

any other ideas?

---

### Post by daviebasite on 2008-11-13
> **derby_sv said:**
> Try to install by using the RPM Package Manager:

sudo apt-get install rpm
sudo mkdir -p /var/lib/rpm

cd linux-amd64/
sudo rpm -ivh --nodeps AWCommon-****.rpm Maya2009_****.rpm

for me this do the work, all packages where installed
there was a warning message, which is not a problem regarding the install guide for maya7
I'm using fresh installed ubuntu8.10


Thanks!

---

### Post by Neon612 on 2008-11-22
Hi,
Everything works fine, until Maya 2008 (in my case) tries to load the shelves then I get an error saying:

"The shelf "PaintEffects" has an item that cannot be read. The shelf will only display th eitems before the first unreadable item it finds. If you start Maya and save this shelf then you will lose the unreadable items. This will happen automatically if you have your preferences set to save the shelves on exit"

and buttons with Continue and Quit Maya.

Not matter which button I hit the Script editor starts up saying:
// Error: Plug-in, "RealflowMesher.so", was not found on MAYA_PLUG_IN_PATH. // 
// Error: Plug-in, "RealflowParticler.so", was not found on MAYA_PLUG_IN_PATH. // 
updateRendererUI;
// Error: Object not found: mainRenderMenu // 
// Error: Object not found: mainRenderMenu // 
// Error: Object is not a child: Polygons // "

And when I exit out of it nothing else happens. When I go look in System Monitor, on the Precesses tab it shows Maya and Maya-bin as loaded but Sleeping.

How can I get this to work?

---

### Post by kougaru on 2008-12-01
Try installing all of the RPM files with RPM instead of converting some of them to DEB. I've had success with this method.

---

### Post by Bubs on 2008-12-14
It tried the RPM way for maya 2009 and I installed AWCommon, maya2009, and the docs.  but when I try to run it just says
```
Failed to execute child process "/usr/autodesk/maya/bin/maya" (No such file or directory)
```

Any clues?

And I looked around and the file does exist.  I tried running it as sudo and still the same message

---

### Post by Bubs on 2008-12-14
Never Mind!  I didn't have csh installed.  I forgot.  installed it and everything is working tip top!  I happy :)  Real HAPPY

---

### Post by tazbo28 on 2008-12-21
hello, 

i am a super newb, and i have a problem with my new ubuntu8.10 install. I have tried to do the csh alien install, but after i type this command, i get this error message...

vince@vince-desktop:~$ apt-get install csh alien
E: Could not open lock file /var/lib/dpkg/lock - open (13 Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
vince@vince-desktop:~$ 


what does that mean? what should i type or do now? also i have the rpm packages on my desktop. is this ok? i also wanted to create my flexlm file in the /var folder however it wont allow me to do this. how can i get the permissions? 

thanks in advance

---

### Post by tad1073 on 2008-12-21
you need to sudo the commmand.
```
sudo apt-get install csh alien
```

---

### Post by danlutz on 2008-12-25
Hey  can't seem to get maya 2009 running. I get this when I run it.sh: > apcw: not found

Some people seem to think it's got to do with  lic file. I have it running fine on my windows side and copied the Flexlm folder to var/FlexLm and no go.
Any help would be nice. 

had maya running fine before not sure why its not running now.

---

### Post by danlutz on 2008-12-25
got it

---

### Post by phuziun on 2009-01-08
> **kougaru said:**
> I've installed it both on a 32bit and a 64bit system. The 64bit system was actually working for a while but then it started having the same errors.

Edit: It seems to happen with any tool using a brush. Ex: Paint Effects, Sculpt Tool, 3D Paint Tool etc. Any time I select any of these tools Maya crashes.

Have you had any progress with this issue.  Here's my post from the Autodesk Area forums.



I’m a systems administrator for the flagship lab at the Savannah College of Art and Design.  We currently host two installs of Maya, Maya 2008 Ext2 x64 and Maya 2009 x64, running on Hardy Heron 8.04.1 64bit.

We’re encountering the exact same issue, any time a brush tool is invoked (via 3d Sculpt, Paint Follicles) it instantly crashes returning the dreaded and horribly terse error:

```

maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/dahale20.20090108.2107.ma
```

I tried disabling our CiOverlay “True” and Composite Disabled sections of our xorg configuration, which did nothing.  I’m not really sure what other angles to hit this from…

Have you made any progress on this issue, or does anyone have a suggestion of where to look to resolve this issue.  I did a bit of searching and it’s seemingly non-existent.

NOTE: Paint selection works fine.

---

### Post by SadaraX on 2009-01-10
I can confirm that Maya 8.5 works under Ubuntu 8.04.1.

---

### Post by YouUbu on 2009-01-10
delete post

---

### Post by kougaru on 2009-01-10
@Phuziun

To try and remedy the problem I tried Maya on the New Ubuntu 8.10 Intrepid Ibex 64bit. So far I've been able to use any brush tool I want without crashing Maya. So far so good. Hopefully I won't encounter the problem again.

Hopefully this helps a least a little bit.

---

### Post by YouUbu on 2009-01-10
I am trying to install Maya 8.5 on Ubuntu

when typing the for i in *.rpm; do sudo alien -cv $i; done

I get that the File "*.rpm" not found

I have the rpm files in a folder called Maya on my Desktop.

Any advice how to solve?

Also when I try the dpkg line

I get the errors
requested operation requires superuser privelege

---

### Post by 1jackjack on 2009-01-10
Just to say thanks very much for the great guide. Got Maya 8.5 working perfectly in hardy!

As for YouUbu, make sure you're in the right directory before you try that first command (i.e. probably try cd ~/Desktop/Maya). And if it requires superuser privelege, simply use the sudo prefix i.e. start the command with the word sudo (will require password).

---

### Post by YouUbu on 2009-01-10
I am beginning to give up on installing Maya on Ubuntu.  I have sought help and read through this thread several times without luck.

I don't understand how everyone is installing maya successfully.  I have gotten as far as the 

for i in *.rpm; do sudo alien -cv $i; done

And for some reason it keeps coming up with the error: File "*.rpm" not found

or now a new one

[sudo] password for: 

to which it won't even take my password!

I have right on my Ubuntu screen/desktop a folder called Maya containing the following folders: Eula, aksusbd-redhat-1.8.l-3.i386.rpm, aksusbd-suse-1.8.1-3.i386.rpm, AWCommon-10.18013.i686.rpm, AWCommon-server-10.80-13i686.rpm, Maya2008_0-2008.0-116.i686.rpm, Maya2008_0-docs_en_US-2008.0-745.i686.rpm

Tell me if I am missing any other files???

I have been searching the internet for a step by step, literally a beginners guide to doing this but apparently everyone has taken classes in linux so I am definitely stuck and will try one more day on it, but I don't know what to do.

---

### Post by 1jackjack on 2009-01-11
try these commands in this order:

cd ~/Desktop/Maya

for i in *.rpm; do sudo alien -cv $i; done

If you can't remember your sudo password, try this thread to reset it:
[http://ubuntuforums.org/showthread.php?t=154841](http://ubuntuforums.org/showthread.php?t=154841)

---

### Post by YouUbu on 2009-01-11
Yes I tried your cd from your previous post and it didn't work.  I do remember my password it's just that ubuntu is not letting me.  It gives me 3 tries to try to enter it. But it's not allowing.

---

### Post by Phoenix777 on 2009-01-28
Problem: Converting rpm to deb
I have three rpm files that I need to convert to deb files:

Maya2009_0_64-docs_en_US-2009.0-63.x86_64.rpm
AWCommon-server-11.5-19.i686.rpm
AWCommon-11.5-19.i686.rpm

So I type the command sudo alien -cv *.rpm

this produces 1 deb file:

maya2009-0-64_2009.0-102_amd64.deb

which is all good, BUT it creates 2 directories that are not deb files:

AWCommon-server-11.5
AWCommon-11.5

on creating these there is an error in terminal:


dpkg-shlibdeps: failure: couldn't find library libXm.so.2 needed by debian/awcommon/usr/aw/COM/bin/installKey (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find AWCommon-11.5 -type d -exec chmod 755 {} ;
find: `AWCommon-11.5': No such file or directory
rm -rf AWCommon-11.5

So how do I either fix these errors or go about creating deb files from these directories.

---

### Post by aeacides on 2009-01-28
Yeah it's normal, I had the same issue yesterday. Maya 2009 (via alien) generate only 2 deb files. So I installed both (the 2 debs), and it worked. Just start Maya after the installation and go over the license installation process.

:-)

EDIT: 

Oh, I just saw that line:
"dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)" ... maya 2009 for linux **is only in x64** .. **no 32 bits version**. So you need a 64bit OS to install it.



> **Phoenix777 said:**
> Problem: Converting rpm to deb
I have three rpm files that I need to convert to deb files:

Maya2009_0_64-docs_en_US-2009.0-63.x86_64.rpm
AWCommon-server-11.5-19.i686.rpm
AWCommon-11.5-19.i686.rpm

So I type the command sudo alien -cv *.rpm

this produces 1 deb file:

maya2009-0-64_2009.0-102_amd64.deb

which is all good, BUT it creates 2 directories that are not deb files:

AWCommon-server-11.5
AWCommon-11.5

on creating these there is an error in terminal:


dpkg-shlibdeps: failure: couldn't find library libXm.so.2 needed by debian/awcommon/usr/aw/COM/bin/installKey (its RPATH is '').
Note: libraries are not searched in other binary packages that do not have any shlibs or symbols file.
To help dpkg-shlibdeps find private libraries, you might need to set LD_LIBRARY_PATH.
dh_shlibdeps: command returned error code 512
make: [binary-arch] Error 1 (ignored)
dh_gencontrol
dpkg-gencontrol: error: current host architecture 'amd64' does not appear in package's architecture list (i386)
dh_gencontrol: command returned error code 65280
make: *** [binary-arch] Error 1
find AWCommon-11.5 -type d -exec chmod 755 {} ;
find: `AWCommon-11.5': No such file or directory
rm -rf AWCommon-11.5

So how do I either fix these errors or go about creating deb files from these directories.

---

### Post by Phoenix777 on 2009-01-28
Well thats strange as I installed 64 bit linux. Could alien be 32 bit?

---

### Post by aeacides on 2009-01-28
Ok, I'm probably wrong (with my interpretation)... anyway, have you tried installing the 2 debs ? And it seems that you need some libraries ... (dpkg-shlibdeps: failure: couldn't find library **libXm.so.2**)

> **Phoenix777 said:**
> Well thats strange as I installed 64 bit linux. Could alien be 32 bit?

---

### Post by kougaru on 2009-02-01
Has anyone had any luck with running Maya with Compiz enabled?

---

### Post by Phoenix777 on 2009-02-03
**Fonts**

I have successfully installed Maya 2009 on ubuntu 8.10, 64 bit. Horay!

But when I go to create text ( in the text curves option) Maya cannot find the fonts.  I noticed others have had this problem, has anyone solved it. Or does anyone know where Maya looks for fonts?

---

### Post by FrostBlue on 2009-02-03
Could u please explain , did u get to convert the other two debs or not.If not did the licensing work,for me it doesn't.

Pleas help.

The license manager shows me this Ethernet address E0003253E06183,while ifconf give me this 00:03:25:3e:06:18 .

What is the problem here.

Please help,I need this I cant live without maya.

---

### Post by Phoenix777 on 2009-02-04
I never managed to convert the other 2 rpm files, so I installed the main Maya file, and like most things with Ubuntu, it just worked. 

The only problem I'm having is that Maya cannot find the font files.

---

### Post by FrostBlue on 2009-02-04
Thanks man.I managed to get it working,I was doing something wrong with licensing.I think there is a way to get the fonts working earlier in this thread or if not just do a search for it,I am sure I saw it somewhere.

peace.

---

### Post by GeneralCody on 2009-02-24
> **Phoenix777 said:**
> **Fonts**

I have successfully installed Maya 2009 on ubuntu 8.10, 64 bit. Horay!

But when I go to create text ( in the text curves option) Maya cannot find the fonts.  I noticed others have had this problem, has anyone solved it. Or does anyone know where Maya looks for fonts?

non-free Postscript Type 1 fonts from XFree86

Maya looks in the following paths for postscript fonts:
/usr/share/fonts/default/ghostscript
/usr/X11R6/lib/X11/fonts/Type1

Just link some fonts to any of these locations

---

### Post by AmbientOcclusion on 2009-02-26
> **GeneralCody said:**
> non-free Postscript Type 1 fonts from XFree86

Maya looks in the following paths for postscript fonts:
/usr/share/fonts/default/ghostscript
/usr/X11R6/lib/X11/fonts/Type1

Just link some fonts to any of these locationsSorry for the noob question. I am having the same problem. What would be the best way to go about linking the fonts to those locations?

---

### Post by kougaru on 2009-03-05
I think found the solution to the font problem!

Install the package "t1-xfree86-nonfree"

It only gives you a few fonts but at least it worked for me. Hopefully it will work for everyone having this problem.

---

### Post by greenbean119 on 2009-03-13
I have this problem when I trying to install, can any one help?

hanwwu20@hanwwu20-desktop:~/Desktop$ for i in *.rpm; do sudo alien -cv $i; done	LANG=C rpm -qp --queryformat %{NAME} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{VERSION} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{ARCH} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{COPYRIGHT} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{PREUN} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{PREIN} AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qcp AWCommon-11.5-19.i686.rpm
	rpm -qpi AWCommon-11.5-19.i686.rpm
	LANG=C rpm -qpl AWCommon-11.5-19.i686.rpm
	mkdir AWCommon-11.5
mkdir: cannot create directory `AWCommon-11.5': File exists
unable to mkdir AWCommon-11.5:  at /usr/share/perl5/Alien/Package.pm line 257.
	LANG=C rpm -qp --queryformat %{NAME} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{VERSION} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{RELEASE} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{ARCH} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{CHANGELOGTEXT} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{SUMMARY} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{DESCRIPTION} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{COPYRIGHT} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{PREFIXES} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{POSTIN} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{POSTUN} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{PREUN} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qp --queryformat %{PREIN} AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qcp AWCommon-server-11.5-19.i686.rpm
	rpm -qpi AWCommon-server-11.5-19.i686.rpm
	LANG=C rpm -qpl AWCommon-server-11.5-19.i686.rpm
	mkdir AWCommon-server-11.5
mkdir: cannot create directory `AWCommon-server-11.5': File exists
unable to mkdir AWCommon-server-11.5:  at /usr/share/perl5/Alien/Package.pm line 257.




so here is where I got stoped....Plz help.....

---

### Post by killpotts on 2009-03-19
Thanks for the awesome tutorial ! I was lost at first when I looked through my maya CD's directory to find rpm's. 


I managed to Maya working great, just one problem: The font color for the gui text is almost the same as the gui itself, making it practically unreadable.

Here is what I mean ( screenshot from my desktop )

[http://img403.imageshack.us/img403/1040/mayafail.jpg]("http://img403.imageshack.us/img403/1040/mayafail.jpg")

Changing Ubuntu font colors has no effect on it either. Does anyone know of any way to change this ? if there are alternative skins for maya that can be installed then that would work just the same.

---

### Post by GeneralCody on 2009-03-19
Check out the tips on my blog to get Maya installed correctly on Linux:

[http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/](http://baltazaar.wordpress.com/2009/03/19/installing-maya-2009-64-bit-on-linux/)

---

### Post by vitaliks777 on 2009-03-28
Tnx guys for all your efforts! *buntus rock! :)

I have some new, I think, not bad link:
[http://www2.bk.tudelft.nl/help/mayahelp/ReleaseNotes/ReleaseNotesMisc10.html](http://www2.bk.tudelft.nl/help/mayahelp/ReleaseNotes/ReleaseNotesMisc10.html)

---

### Post by kougaru on 2009-04-28
I've encountered a weird problem. Whenever I try to enter anything in the channel box and then press enter to finish it, it seems to go on a loop of enter key presses. If I open of gnome terminal I get an endless loop of enter until I press backspace which makes it stop. 

Right now I'm avoiding the problem by not pressing enter at all in maya, but would really like to fix the problem instead of ignoring it.

Anyone have any insight into this problem?

---

### Post by mickie.kext on 2009-05-12
I have problem with Maya 2009 on Ubuntu Jaunty 64-bit. Alien cant convert those two AWCOMON files so i cant install them. So I cant install licnece either. But maya is installed. Here is the tread

[http://ubuntuforums.org/showthread.php?t=1153363](http://ubuntuforums.org/showthread.php?t=1153363)

Please someone give tutorial for this.

---

### Post by mickie.kext on 2009-05-15
Anybody please.

---

### Post by kougaru on 2009-05-15
mickie.kext,

I've been using Maya successfully for the last couple weeks without installing the AWCOMMON packages. If you start Maya, the license utility should still pop up and ask for the license without those packages.

---

### Post by omkrasu on 2009-07-01
> **fghj. said:**
> ocmask(SIG_BLOCK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [INT CHLD], [INT], 8 ) = 0
vfork()                                 = 8550
gettimeofday({1200182816, 540666}, NULL) = 0
rt_sigprocmask(SIG_SETMASK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [INT], 8 ) = 0
rt_sigprocmask(SIG_SETMASK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], [INT], 8 ) = 0
rt_sigprocmask(SIG_BLOCK, [CHLD], NULL, 8 ) = 0
rt_sigsuspend([INT]

maya encountered a fatal error

Signal: 11 (Unknown Signal)
Fatal Error. Attempting to save in /usr/tmp/robin.20080113.0107.ma
)                    = ? ERESTARTNOHAND (To be restarted)
--- SIGCHLD (Child exited) @ 0 (0) ---
wait4(-1, [{WIFEXITED(s) && WEXITSTATUS(s) == 1}], WNOHANG, {ru_utime={6, 716419}, ru_stime={0, 460028}, ...}) = 8550
wait4(-1, 0xbfed42e8, WNOHANG, 0xbfed42a0) = -1 ECHILD (No child processes)
sigreturn()                             = ? (mask now [INT CHLD])
rt_sigprocmask(SIG_BLOCK, [CHLD], NULL, 8 ) = 0
rt_sigprocmask(SIG_SETMASK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8 ) = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8 ) = 0
close(3)                                = 0
close(4)                                = 0
close(5)                                = 0
close(0)                                = 0
close(1)                                = 0
close(2)                                = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
rt_sigprocmask(SIG_BLOCK, [INT], NULL, 8) = 0
close(0)                                = -1 EBADF (Bad file descriptor)
dup(19)                                 = 0
ioctl(0, FIONCLEX)                      = 0
close(1)                                = -1 EBADF (Bad file descriptor)
dup(17)                                 = 1
ioctl(1, FIONCLEX)                      = 0
close(2)                                = -1 EBADF (Bad file descriptor)
dup(18)                                 = 2
ioctl(2, FIONCLEX)                      = 0
lseek(16, 0, SEEK_END)                  = 7269
close(0)                                = 0
close(1)                                = 0
close(2)                                = 0
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
read(16, "", 1024)                      = 0
ioctl(16, SNDCTL_TMR_TIMEBASE or TCGETS, 0xbfed7d58) = -1 ENOTTY (Inappropriate ioctl for device)
rt_sigprocmask(SIG_UNBLOCK, [INT], NULL, 8) = 0
exit_group(1)                           = ?
Process 8538 detached

i get that message when i run "strace maya".
Maya loads and when it starts the 3d view is just black and the program shuts down. I got a ati mobility x300 with 8.44.3 drivers, and maya works well in windows :( anyone knows what the problem is?

Hi there! It took me so long to find this thing. I even use Maya 8.5, and this signal problem occurs only for me when i plug in another monitor so two servers running won't accept the "export XLIB_SKIP_ARGB_VISUALS=1" command which is needed for some acceleration stuff.

Now it works.

I have an Nvidia Quadro NVS card, and it's from the 8000 series. So it might just be a driver issue, or worse, but i hope you get the idea.

---

### Post by eyeJ on 2009-07-03
I have a problem with paint effects brush strokes. They will not render as i paint them with my intuos, they only show up when i open and close a menu from the panel. It happens when painting on the canvas and on the scene.

Anyone know how to fix this?

I'm using maya 2009 on ubuntu 9.04 with nvidia drivers version 180 i installed from the hardware drivers utility.

Thanks for reading and your help in advance!

---

### Post by eyeJ on 2009-07-18
> **kougaru said:**
> I've encountered a weird problem. Whenever I try to enter anything in the channel box and then press enter to finish it, it seems to go on a loop of enter key presses. If I open of gnome terminal I get an endless loop of enter until I press backspace which makes it stop. 

Right now I'm avoiding the problem by not pressing enter at all in maya, but would really like to fix the problem instead of ignoring it.

Anyone have any insight into this problem?

I have the same problem and in adition to it wierd stuff also happens if i try to switch desktops with shortcuts on the keyboard. From what I've tested it seems that the numpad enter key will not cause the same problem. This makes some sense since the main enter key is used for completing input and the numpad enter will only apply the current setting so that you can inspect your changes.

If anyone has some more information please share :)

By the way do you have some devices like an Wacom tablet or 3dconnexion mice connected to your pc for use with maya? I previously thought it's related to those devices but it now seems that it is not.
I'l also test this in suse because I also want to see if paint effects will work there as they should. my problem with paint effects -> [http://ubuntuforums.org/showpost.php?p=7556987&postcount=373](http://ubuntuforums.org/showpost.php?p=7556987&postcount=373)

here is my xorg.conf:

```


# nvidia-settings: X configuration file generated by nvidia-settings
# nvidia-settings:  version 1.0  (buildmeister@builder62)  Wed May 27 01:59:40 PDT 2009

# nvidia-xconfig: X configuration file generated by nvidia-xconfig
# nvidia-xconfig:  version 1.0  (buildmeister@builder62)  Wed May 27 01:58:49 PDT 2009

Section "ServerLayout"
    Identifier     "Layout0"
    Screen      0  "Screen0" 0 0
    InputDevice    "Keyboard0" "CoreKeyboard"
    #InputDevice    "Mouse0" "CorePointer"
  InputDevice   "stylus"  "SendCoreEvents"
  InputDevice   "eraser"  "SendCoreEvents"
  InputDevice   "cursor"  "SendCoreEvents" # For non-LCD tablets only
  InputDevice   "pad"                      # For Intuos3/CintiqV5/Graphire4/Bamboo tablets
# InputDevice   "touch"   "SendCoreEvents" # Only a few TabletPCs support this type
EndSection

Section "Files"
EndSection

Section "ServerFlags"
    Option         "Xinerama" "0"
EndSection

#INTUOS3 START

Section "InputDevice"
  Driver        "wacom"
  Identifier    "stylus"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "stylus"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
  Option          "TopX"        "0"     
  Option          "TopY"        "13503"      
  Option          "BottomX"     "61010"
  Option          "BottomY"     "60960"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "eraser"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "eraser"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB 
  Option          "TopX"        "0"     
  Option          "TopY"        "13503"      
  Option          "BottomX"     "61010"
  Option          "BottomY"     "60960"
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "cursor"
  Option        "Device"        "/dev/input/wacom" # USB ONLY?
#  Option        "Device"        "/dev/ttyS0"      # SERIAL ONLY
  Option        "Type"          "cursor"
#  Option        "ForceDevice"   "ISDV4"           # Tablet PC ONLY
  Option        "USB"           "on"               # USB ONLY
EndSection

Section "InputDevice"
  Driver        "wacom"
  Identifier    "pad"
  Option        "Device"        "/dev/input/wacom"    # USB ONLY
#  Option        "Device"        "/dev/ttyS0"         # SERIAL ONLY
  Option        "Type"          "pad"
  Option        "USB"           "on"                  # USB ONLY
EndSection

# Uncomment the following section if you you have a TabletPC that supports touch
# Section "InputDevice"
#  Driver        "wacom"
#  Identifier    "touch"
#  Option        "Device"        "/dev/ttyS0"       # SERIAL ONLY
#  Option        "Device"        "/dev/input/wacom" # USB ONLY
#  Option        "Type"          "touch"
#  Option        "ForceDevice"   "ISDV4"            # Serial Tablet PC ONLY
#  Option        "USB"           "on"               # USB ONLY
# EndSection

#INTUOS3 END

Section "InputDevice"
    # generated from default
    Identifier     "Mouse0"
    Driver         "mouse"
    Option         "Protocol" "auto"
    Option         "Device" "/dev/psaux"
    Option         "Emulate3Buttons" "no"
    Option         "ZAxisMapping" "4 5"
EndSection

Section "InputDevice"

    # generated from default
    Identifier     "Keyboard0"
    Driver         "kbd"
EndSection

Section "Monitor"
    Identifier     "Monitor0"
    VendorName     "Unknown"
    ModelName      "Samsung SyncMaster"
    HorizSync       30.0 - 96.0
    VertRefresh     50.0 - 160.0
    Option         "DPMS"
EndSection

Section "Device"
    Identifier     "Device0"
    Driver         "nvidia"
    VendorName     "NVIDIA Corporation"
    BoardName      "GeForce 9800 GTX+"
EndSection

Section "Screen"
    Identifier     "Screen0"
    Device         "Device0"
    Monitor        "Monitor0"
    DefaultDepth    24
    Option         "TwinView" "0"
    Option         "metamodes" "1280x1024_85 +0+0"
    SubSection     "Display"
        Depth       24
    EndSubSection
EndSection

Section "Extensions"
  Option "Composite" "Disable"
EndSection


```

and here is output from 'xinput list' command:
note that i removed my SpacePilot from there.

```


"Virtual core pointer"	id=0	[XPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 0
"Virtual core keyboard"	id=1	[XKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"stylus"	id=2	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 61010
		Resolution is 5080
	Axis 1 :
		Min_value is 13503
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
"eraser"	id=3	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 61010
		Resolution is 5080
	Axis 1 :
		Min_value is 13503
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"cursor"	id=4	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 97536
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"pad"	id=5	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 15
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 97536
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"AT Translated Set 2 keyboard"	id=6	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
"Macintosh mouse button emulation"	id=7	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
"Wacom Intuos3 12x19"	id=8	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 97536
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
"Wacom Intuos3 12x19 pad"	id=9	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 15
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 97536
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 4 :
		Min_value is 0
		Max_value is 4096
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Intuos3 12x19 cursor"	id=10	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 97536
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -900
		Max_value is 899
		Resolution is 1
	Axis 4 :
		Min_value is -1023
		Max_value is 1023
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Wacom Intuos3 12x19 eraser"	id=11	[XExtensionKeyboard]
	Num_keys is 248
	Min_keycode is 8
	Max_keycode is 255
	Num_buttons is 7
	Num_axes is 6
	Mode is Absolute
	Motion_buffer is 256
	Axis 0 :
		Min_value is 0
		Max_value is 97536
		Resolution is 5080
	Axis 1 :
		Min_value is 0
		Max_value is 60960
		Resolution is 5080
	Axis 2 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
	Axis 3 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 4 :
		Min_value is -64
		Max_value is 63
		Resolution is 1
	Axis 5 :
		Min_value is 0
		Max_value is 1023
		Resolution is 1
"Microsoft Microsoft Trackball Optical?"	id=12	[XExtensionPointer]
	Num_buttons is 32
	Num_axes is 2
	Mode is Relative
	Motion_buffer is 256
	Axis 0 :
		Min_value is -1
		Max_value is -1
		Resolution is 1
	Axis 1 :
		Min_value is -1
		Max_value is -1
		Resolution is 1

```

---

### Post by eyeJ on 2009-08-06
> **kougaru said:**
> I've encountered a weird problem. Whenever I try to enter anything in the channel box and then press enter to finish it, it seems to go on a loop of enter key presses. If I open of gnome terminal I get an endless loop of enter until I press backspace which makes it stop. 

Right now I'm avoiding the problem by not pressing enter at all in maya, but would really like to fix the problem instead of ignoring it.

Anyone have any insight into this problem?

I think I fixed the problem but I'll have to test it some more to be absolutely sure. Seems that the last time I cleaned my keyboard I misaligned something inside and because of that keyboard was causing the trouble.

Now pressing the enter key on the letter part of the keyboard while changing values in the channel box doesn't make Maya go mad... so far so good...

I will report back when I'm sure the problem is fixed. :D

To see more info about what my problem was see my previews post above.
Oh and one last thing my keyboard is PS/2 connector Microsoft Natural Keyboard Elite

---

### Post by Saxcore on 2009-08-18
Awesome! Thanks alot for this thread, i never would have been able to do it otherwise!

...now, all i have to do is get 3D supported on my graphics card. Bah..

---

### Post by mentarm on 2009-09-12
Has anybody succeeded at install Maya 2010 in Ubuntu?

The installation processes seems simple, but the 'adlmreg' tool does not work as explained in the manual.

I would appreciate if somebody gets it working and shares her tricks with all of us.

Thanks!

Mentar

---

### Post by penguinv on 2009-10-23
> **}{yBr!D^ said:**
> I'm actually having problems with step 7 in the install.txt...

"Using the run utility and type: awkeygen.exe aw.dat"

When I type in "awkeygen.exe aw.dat" in window's run utility i get this error message...

"Windows cannot find 'awkeygen.exe'. Make sure you typed the name correctly, and then try again. To search for a file, click the start button, and then click Search."

What am I doing wrong...? there is no typo's and I copy/paste it... wtf?

Hello, You need to put the FULL PATH in the run command.
I did it. I got the same. I solved it this way.

---

### Post by wentzr on 2009-11-12
> **szr4321 said:**
> Did you try to update your graphics driver?

also be sure you have your visual effects set to normal or minimal. compiz screws with the hotbox in maya, at least it does on my intel mac (running ubuntu) with a NVIDIA 6500.

---

### Post by stallion151 on 2009-11-15
[FONT=monospace]hey everyone,

first of all, I've never used ubuntu 9.10 before and don't know what i'm missing here. But I've run through this tutorial and the one at the baltazaar website but I keep getting stuck or something. 
I run the alien convert rpm files to deb files, but i cannot find where the deb files are converted. I change directory to where the rpm files are but the converter doesn't leave the newly created deb files there. I did a search for *.deb and still can't find it. 

So when I try sudo dpkg....it can't find the deb files and neither can I. 
Is there something simple i'm unaware of. 

Please help
Thanks in Advance
[/FONT]

---

### Post by kougaru on 2009-11-18
wentzr,

Have you been able to use the Maya hotbox with compiz turned on at all? Every time I've tried it just freezes my whole desktop. Even with minimal settings.

---

### Post by misterbk on 2009-12-06
> **penguinv said:**
> Hello, You need to put the FULL PATH in the run command.
I did it. I got the same. I solved it this way.

Or just drag the aw.dat onto the keygen.exe.

---

### Post by antrozous812 on 2009-12-12
I seem to have a problem no one else had.... 
When I execute this command:

```

for i in *.rpm; do sudo alien -cv $i; done

```I don't have any .deb files created, but Folders instead...? (with root permissions)

does any one knows why, and what to do so I can have .deb files? 

thanks in advance! 
-C

EDIT: I also have this error message in the console: "error: incorrect format: unknown tag"

---

### Post by kiran001 on 2010-03-17
Hi friends 
i'm trying to install maya 2009 on ubuntu 9.10 i converted the .rpm to .deb files but i cannot find maya package for example (sudo dpkg -i maya7-0_7.0-375_i386.deb) please help me regarding this one more over if any one has maya 8/ 8.5 packages please can any upload for me 

Thanks in advance [IMG]file:///home/manu/Desktop/Screenshot.png[/IMG]

---

### Post by etoia on 2010-04-27
Hello all,

I had a little time yesterday and I wrote a little tutorial on How to install Maya 2011 as there have been some modifications since the 2010 version on the activation part (so it should be Maya 2010 compatible).
I have done this tutorial for Debian Sid (wich I run), but I think it should also work on Ubuntu.Can anybody who run Ubutnu and test it can tell me if it work on Ubuntu (especially the 10.04 since it will be a LTS one).

Here is the address to the tutorial : [http://etoia.free.fr/?p=1611](http://etoia.free.fr/?p=1611)

And a preview:

---------------------------------------------------------------------------------------------------
**6.Fix Maya UI launching bug**

 Here is the part that is specific to Maya 2011 (I have encountered it on the Betas versions and it&#8217;s still here).It may be a bug with non-US Debian installations (French in my case).If you don&#8217;t do it, a bug with one of the startup mel prevent the Maya UI to be launched.We will had a variable in the maya launcher to avoid that.Using nano (or your favorite editor), insert this : setenv LC_ALL en_US.UTF-8 In this file* /usr/autodesk/maya2011-x64/bin/maya2011*
You can also use this command:
 sudo sh -c "echo 'setenv LC_ALL en_US.UTF-8' >> /usr/autodesk/maya2011-x64/bin/maya2011"



---------------------------------------------------------------------------------------------------


Thank you in advance, and thank you to all the people who have answered this thread, it have been a great source of information in the past.

---

### Post by niallcd on 2010-05-27
etoia: I've got some time and will give your tutorial a try. I'm really trying to get 2011 to work in Ubuntu. So far I've been using this as a guide post 

[http://area.autodesk.com/forum/autodesk-maya/autodesk-maya-2011/maya-2011-on-ubuntux64-40solved41/](http://area.autodesk.com/forum/autodesk-maya/autodesk-maya-2011/maya-2011-on-ubuntux64-40solved41/)

I'll abandon that for now and give your tutorial a shot. 

I'll let you know how it turns out. If I get stuck can I email you? If we get it sorted I know many users would be thrilled. 

Thanks.

---

### Post by elf128 on 2010-06-13
> **etoia said:**
> Hello all,

I had a little time yesterday and I wrote a little tutorial on How to install Maya 2011 as there have been some modifications since the 2010 version on the activation part (so it should be Maya 2010 compatible).
I have done this tutorial for Debian Sid (wich I run), but I think it should also work on Ubuntu.Can anybody who run Ubutnu and test it can tell me if it work on Ubuntu (especially the 10.04 since it will be a LTS one).

Here is the address to the tutorial : [http://etoia.free.fr/?p=1611](http://etoia.free.fr/?p=1611)

And a preview:

------------------------------------------------------------------------


Thank you in advance, and thank you to all the people who have answered this thread, it have been a great source of information in the past.

I've read your tutorial. Nice trick with "fake rpm". Thanks for idea. :)

---

### Post by eks on 2011-05-08
With Maya 2012 and a clean install of Kubuntu 11.04 I'm getting the helvetica problem...

```
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
(...)
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--14-*-*-*-p-82-iso8859-1 // 
// Error: Failed trying to load font : -*-helvetica-bold-r-normal--14-*-*-*-p-82-iso8859-1 // 
(...)
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
// Error: Failed trying to load font : -*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 // 
```

The problem is, I've installed all font packages from everywhere, t1-xfree86-nonfree, msttcorefonts, but none of them installed Helvetica. I found it online and tried both installing through Kubuntu Font Installer and copying manually, but still no deal.

What am I doing wrong??

If I have to link the font to some place, WHERE in /usr/autodesk/?

---

### Post by eks on 2011-05-08
I found out that xlsfonts doesn't list any EXACT match for the helvetica Maya is looking for. There are these:


```
-rfx-helvetica-bold-o-normal--0-0-0-0-p-0-iso10646-1
-rfx-helvetica-bold-o-normal--0-0-0-0-p-0-iso8859-5
-rfx-helvetica-bold-o-normal--0-0-0-0-p-0-koi8-r
-rfx-helvetica-bold-o-normal--0-0-0-0-p-0-koi8-u
-rfx-helvetica-bold-o-normal--0-0-0-0-p-0-microsoft-cp1251
-rfx-helvetica-bold-r-normal--0-0-0-0-p-0-iso10646-1
-rfx-helvetica-bold-r-normal--0-0-0-0-p-0-iso8859-5
-rfx-helvetica-bold-r-normal--0-0-0-0-p-0-koi8-r
-rfx-helvetica-bold-r-normal--0-0-0-0-p-0-koi8-u
-rfx-helvetica-bold-r-normal--0-0-0-0-p-0-microsoft-cp1251
-rfx-helvetica-medium-o-normal--0-0-0-0-p-0-iso10646-1
-rfx-helvetica-medium-o-normal--0-0-0-0-p-0-iso8859-5
-rfx-helvetica-medium-o-normal--0-0-0-0-p-0-koi8-r
-rfx-helvetica-medium-o-normal--0-0-0-0-p-0-koi8-u
-rfx-helvetica-medium-o-normal--0-0-0-0-p-0-microsoft-cp1251
-rfx-helvetica-medium-r-normal--0-0-0-0-p-0-iso10646-1
-rfx-helvetica-medium-r-normal--0-0-0-0-p-0-iso8859-5
-rfx-helvetica-medium-r-normal--0-0-0-0-p-0-koi8-r
-rfx-helvetica-medium-r-normal--0-0-0-0-p-0-koi8-u
-rfx-helvetica-medium-r-normal--0-0-0-0-p-0-microsoft-cp1251
```

and

```
-cronyx-helvetica-bold-o-normal--0-0-0-0-p-0-iso10646-1
-cronyx-helvetica-bold-o-normal--0-0-0-0-p-0-iso8859-5
-cronyx-helvetica-bold-o-normal--0-0-0-0-p-0-koi8-r
-cronyx-helvetica-bold-o-normal--0-0-0-0-p-0-koi8-u
-cronyx-helvetica-bold-o-normal--0-0-0-0-p-0-microsoft-cp1251
-cronyx-helvetica-bold-r-normal--0-0-0-0-p-0-iso10646-1
-cronyx-helvetica-bold-r-normal--0-0-0-0-p-0-iso8859-5
-cronyx-helvetica-bold-r-normal--0-0-0-0-p-0-koi8-r
-cronyx-helvetica-bold-r-normal--0-0-0-0-p-0-koi8-u
-cronyx-helvetica-bold-r-normal--0-0-0-0-p-0-microsoft-cp1251
-cronyx-helvetica-medium-o-normal--0-0-0-0-p-0-iso10646-1
-cronyx-helvetica-medium-o-normal--0-0-0-0-p-0-iso8859-5
-cronyx-helvetica-medium-o-normal--0-0-0-0-p-0-koi8-r
-cronyx-helvetica-medium-o-normal--0-0-0-0-p-0-koi8-u
-cronyx-helvetica-medium-o-normal--0-0-0-0-p-0-microsoft-cp1251
-cronyx-helvetica-medium-r-normal--0-0-0-0-p-0-iso10646-1
-cronyx-helvetica-medium-r-normal--0-0-0-0-p-0-iso8859-5
-cronyx-helvetica-medium-r-normal--0-0-0-0-p-0-koi8-r
-cronyx-helvetica-medium-r-normal--0-0-0-0-p-0-koi8-u
-cronyx-helvetica-medium-r-normal--0-0-0-0-p-0-microsoft-cp1251
```

None of them match

```
-*-helvetica-bold-r-normal--14-*-*-*-p-82-iso8859-1
-*-helvetica-bold-r-normal-*-11-*-*-*-*-*-iso8859-1 

```

Scourging the net I see people just installing t1-xfree86-nonfree or msttcorefonts do solve this issue. Would the font be updated on these packs (iso8859-5 instead of iso8859-1 like maya wants) be the cause of this issue?

Where do I find (or convert) a size 11 and 14 iso8859-1 helvetica?

---

### Post by eks on 2011-05-08
So I'm really blocked with this........... :(

No matter what type of font I try to install, Maya NEVER finds the 11 and 14 size of helvetica. And no matter what change I do to MayaScheme file, or where I place it, Maya is ALWAYS looking for helvetica. It seems it's just not reading it.

I tried leaving it at /usr/autodesk/maya/app-defaults but also at /home/eks/app-defaults, /home/eks/.app-defaults and /home/eks/maya/app-defaults, it did not made any difference...

I have no idea what else I could try...

---

### Post by eks on 2011-05-15
Btw, for those coming here with the same problem (Maya 2012 and *Ubuntu 11.04), I was able to solve the font problem only reinstalling Kubuntu 10.10, which had the font packages installed by default, then upgrading.

The packages which seem to be unavailable from a 11.04 install are: **xfonts-100dpi** and/or **xfonts-75dpi**. And thus, I leave a salute and good luck for future people that might come here with 11.04, 11.10 and so on. :)  (me included...)

---

