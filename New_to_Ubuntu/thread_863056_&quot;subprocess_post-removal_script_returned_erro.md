---
title: "&quot;subprocess post-removal script returned error exit status 2&quot;. erk."
date: 2008-07-18
forum: New to Ubuntu
---

### Post by fraser_m on 2008-07-18
I recently installed KDE, to try to use thinliquidfilm, but decided that HandBrake would work better.

 So I tried to remove KDE, but had some problems as I apt-get'd it, rather that synaptic'ing or aptitude'ing, like I should have. I followed the guide on [this site]("http://www.psychocats.net/ubuntu/puregnome.php"), but now when I apt-get, aptitude, synaptic, or dpkg anything, it does a lovely...

```
fraser@laptop:~$ sudo apt-get install kazehakase
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libatk1-ruby1.8 libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8 libgettext-ruby1.8
  libglib2-ruby1.8 libgtk2-ruby libgtk2-ruby1.8 libpango1-ruby1.8 libruby1.8
  ruby1.8
Suggested packages:
  migemo rdoc1.8 ri1.8 ruby1.8-examples
Recommended packages:
  hyperestraier libgettext-ruby-util
The following packages will be REMOVED
  kio-umountwrapper
The following NEW packages will be installed
  kazehakase libatk1-ruby1.8 libcairo-ruby1.8 libgdk-pixbuf2-ruby1.8
  libgettext-ruby1.8 libglib2-ruby1.8 libgtk2-ruby libgtk2-ruby1.8
  libpango1-ruby1.8 libruby1.8 ruby1.8
0 upgraded, 11 newly installed, 1 to remove and 178 not upgraded.
1 not fully installed or removed.
Need to get 0B/3155kB of archives.
After this operation, 14.3MB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 111245 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--remove):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper
E: Sub-process /usr/bin/dpkg returned an error code (1)

```

Ouch. I have no idea what to do... Any help would be nice...

I need kazehakase!

---

### Post by PmDematagoda on 2008-07-18
Try doing:-
```
sudo dpkg -P kio-umountwrapper
```

Post the output of the command here.

---

### Post by fraser_m on 2008-07-18
```
fraser@laptop:~$ sudo dpkg -P kio-umountwrapper
(Reading database ... 111245 files and directories currently installed.)
Removing kio-umountwrapper ...
No diversion `diversion of /usr/share/apps/konqueror/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
No diversion `diversion of /usr/share/apps/dolphin/servicemenus/media_safelyremove.desktop by kio-umountwrapper', none removed
Removing `diversion of /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop to /usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop.distrib by kio-umountwrapper'
dpkg-divert: error checking `/usr/share/apps/d3lphin/servicemenus/media_safelyremove.desktop': No such file or directory
dpkg: error processing kio-umountwrapper (--purge):
 subprocess post-removal script returned error exit status 2
Errors were encountered while processing:
 kio-umountwrapper

```

Herey you go.

Thanks for the reply, I didn't think it would get one because of the scary title...

EDIT: I see you have skype. I have a skypephone so Im always online. I should put my details.

EDIT2: Or I could just reinstall. My ~/ is safe.

---

### Post by Toon Macharis on 2009-01-15
Hi there,

I recently had a similar problem as described in [http://ubuntuforums.org/showthread.php?t=668097](http://ubuntuforums.org/showthread.php?t=668097)

The previous post was closed for posting, so I will post my solution here, as it probably is the same problem.

first go to a command line and execute the command

[FONT="Courier New"]dpkg-divert --list[/FONT]

The package I was having problems with was xorg-driver-fglrx.  The output of the previous command was

[FONT="Courier New"]...
diversion of /usr/X11R6/lib/libGL.so.1.2 to /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/X11R6/lib32/libGL.so.1 to /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1.2 to /usr/lib32/fglrx/libGL.so.1.2.xlibmesa by xorg-driver-fglrx
diversion of /usr/lib32/libGL.so.1 to /usr/lib32/fglrx/libGL.so.1.xlibmesa by xorg-driver-fglrx
...
[/FONT]

The lines in the output take the form

[FONT="Courier New"]**diversion of** XXX **to** YYY **by** package[/FONT]

in this, package is the of your package.  In my case, this was xorg-driver-fglrx, in your case this would be kio-unmountwrapper

Look for the file /var/lib/dpkg/info/package.postrm
I had to look for /var/lib/dpkg/info/xorg-driver-fglrx.postrm
You will have to look for /var/lib/dpkg/info/kio-unmountwrapper.postrm

Before you make any changes to the file, it could be smart to make a back up copy.

When I opened the file xorg-driver-fglrx.postrm, it contained the lines:

[FONT="Courier New"]...
	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib/fglrx/libGL.so.1.2.xlibmesa /usr/lib/libGL.so.1.2 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1.2 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib32/libGL.so.1 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib/libGL.so.1.2 > /dev/null
...
[/FONT]

These lines are of the form:

[FONT="Courier New"]**dpkg-diver --remove --rename --package $PKGNAME --divert** YYY XXX **> /dev/null**
[/FONT]

The lines in this file have to be in synch with the lines that are shown after you execute the [FONT="Courier New"]dpkg-divert --list[/FONT] command.  They were not, so I fixed the file /var/lib/dpkg/info/xorg-driver-fglrx.postrm to look like:

[FONT="Courier New"]...
	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib/fglrx/libGL.so.1.2.xlibmesa /usr/X11R6/lib/libGL.so.1.2 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/X11R6/lib32/fglrx/libGL.so.1.xlibmesa /usr/X11R6/lib32/libGL.so.1 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.2.xlibmesa /usr/lib32/libGL.so.1.2 > /dev/null

	dpkg-divert --remove --rename --package $PKGNAME --divert /usr/lib32/fglrx/libGL.so.1.xlibmesa /usr/lib32/libGL.so.1 > /dev/null
...[/FONT]

After I had fixed the postrm file, I could remove my package without any problem.  I hope this will work for you as well.

---

### Post by Crabdude on 2010-05-13
I had a similar problem, "post-removal script returned error exit status 2" error came up every time I tried to remove or install a program.

I found a simple solution on [The _khAttAm_ blog]("http://www.khattam.info/2009/08/04/solved-subprocess-pre-removal-script-returned-error-exit-status-2-error/") where the first solution worked fine.

If you go to terminal and type in the following:
```
sudo aptitude update
sudo aptitude -f install
```


and it should everything worked again. If this doesn't work, click on the hyperlink above because he has a couple more solutions on the blog!

(^_^)

---

### Post by vinay_wagh on 2011-11-04
I have a the same problem on Ubuntu 11.10, the only change is the exist status is 1 instead of 2 being discussed. None of the solutions mentioned above have worked for me. 

Further if I try to enable the driver via jockey, then  nothing happens for hours, it just keeps saying "installing drivers". (The status of the process is "sleeping").

-- VInay

---

### Post by oldos2er on 2011-11-04
Closed. Please start a new thread for your question.

---

