---
title: "Package Error"
date: 2008-07-01
forum: New to Ubuntu
---

### Post by Cront on 2008-07-01
I was trying to install the plugins required for facebook and after some messing around here is the error I'm getting on Ubuntu 8.04 2.6.24-19

daniel@daniel-laptop:~$ sudo apt-get -f install
[sudo] password for daniel: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-jdk (6-06-0ubuntu1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing sun-java6-jdk (--configure):
 subprocess post-installation script returned error exit status 2
Setting up cacao (0.97-4) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing cacao (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xulrunner-1.9 (1.9+nobinonly-0ubuntu0.8.04.1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9~rc); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9+nobinonly-0ubuntu0.8.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up opera (9.50) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing opera (--configure):
 subprocess post-installation script returned error exit status 2
Setting up sun-java5-bin (1.5.0-15-0ubuntu1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-15-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
 sun-java5-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jdk
 cacao
 xulrunner-1.9
 firefox-3.0
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
 opera
 sun-java5-bin
 sun-java5-plugin
 sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ChameleonDave on 2008-07-01
You do seem to be rather screwed.  You will not be able to install or remove anything until this is manually fixed.

Try this and see what happens:

```

cd /usr/sbin
sudo mv -T  update-alternatives  update-alternatives.backup
sudo apt-get install -f

```

---

### Post by benfindlay on 2008-07-01
Not too sure, but give ```
dpkg --configure --pending

``` and ```
apt-get install -f
```a try

Hope this helps!

---

### Post by Cront on 2008-07-01
daniel@daniel-laptop:~$ sudo dpkg --configure --pending
[sudo] password for daniel: 
Setting up xulrunner-1.9 (1.9+nobinonly-0ubuntu0.8.04.1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 2
Setting up sun-java5-bin (1.5.0-15-0ubuntu1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
Setting up cacao (0.97-4) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing cacao (--configure):
 subprocess post-installation script returned error exit status 2
Setting up opera (9.50) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing opera (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-15-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
 sun-java5-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9+nobinonly-0ubuntu0.8.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up sun-java6-jdk (6-06-0ubuntu1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing sun-java6-jdk (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9~rc); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 xulrunner-1.9
 sun-java5-bin
 cacao
 opera
 sun-java5-plugin
 xulrunner-1.9-gnome-support
 sun-java6-jdk
 firefox-3.0
 sun-java6-plugin
 firefox-3.0-gnome-support
 firefox-gnome-support
 firefox
daniel@daniel-laptop:~$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-jdk (6-06-0ubuntu1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing sun-java6-jdk (--configure):
 subprocess post-installation script returned error exit status 2
Setting up cacao (0.97-4) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing cacao (--configure):
 subprocess post-installation script returned error exit status 2
Setting up xulrunner-1.9 (1.9+nobinonly-0ubuntu0.8.04.1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9~rc); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9+nobinonly-0ubuntu0.8.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up opera (9.50) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing opera (--configure):
 subprocess post-installation script returned error exit status 2
Setting up sun-java5-bin (1.5.0-15-0ubuntu1) ...
Can't locate Dpkg/Gettext.pm in @INC (@INC contains: /etc/perl /usr/local/lib/perl/5.8.8 /usr/local/share/perl/5.8.8 /usr/lib/perl5 /usr/share/perl5 /usr/lib/perl/5.8 /usr/share/perl/5.8 /usr/local/lib/site_perl .) at /usr/sbin/update-alternatives line 8.
BEGIN failed--compilation aborted at /usr/sbin/update-alternatives line 8.
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-15-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
 sun-java5-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jdk
 cacao
 xulrunner-1.9
 firefox-3.0
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
 opera
 sun-java5-bin
 sun-java5-plugin
 sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)
daniel@daniel-laptop:~$ cd /usr/sbin
daniel@daniel-laptop:/usr/sbin$ sudo mv -T  update-alternatives  update-alternatives.backup
daniel@daniel-laptop:/usr/sbin$ sudo apt-get install -f
Reading package lists... Done
Building dependency tree       
Reading state information... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
12 not fully installed or removed.
After this operation, 0B of additional disk space will be used.
Setting up sun-java6-jdk (6-06-0ubuntu1) ...
/var/lib/dpkg/info/sun-java6-jdk.postinst: 54: update-alternatives: not found
dpkg: error processing sun-java6-jdk (--configure):
 subprocess post-installation script returned error exit status 127
Setting up cacao (0.97-4) ...
/var/lib/dpkg/info/cacao.postinst: 10: update-alternatives: not found
dpkg: error processing cacao (--configure):
 subprocess post-installation script returned error exit status 127
Setting up xulrunner-1.9 (1.9+nobinonly-0ubuntu0.8.04.1) ...
/var/lib/dpkg/info/xulrunner-1.9.postinst: 12: /usr/sbin/update-alternatives: not found
dpkg: error processing xulrunner-1.9 (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of firefox-3.0:
 firefox-3.0 depends on xulrunner-1.9 (>= 1.9~rc); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing firefox-3.0 (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on firefox-3.0; however:
  Package firefox-3.0 is not configured yet.
dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xulrunner-1.9-gnome-support:
 xulrunner-1.9-gnome-support depends on xulrunner-1.9 (= 1.9+nobinonly-0ubuntu0.8.04.1); however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing xulrunner-1.9-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-3.0-gnome-support:
 firefox-3.0-gnome-support depends on firefox-3.0 (= 3.0+nobinonly-0ubuntu0.8.04.1); however:
  Package firefox-3.0 is not configured yet.
 firefox-3.0-gnome-support depends on xulrunner-1.9-gnome-support (>= 1.9~b4~); however:
  Package xulrunner-1.9-gnome-support is not configured yet.
dpkg: error processing firefox-3.0-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox-3.0-gnome-support; however:
  Package firefox-3.0-gnome-support is not configured yet.
dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Setting up opera (9.50) ...
/var/lib/dpkg/info/opera.postinst: 31: update-alternatives: not found
dpkg: error processing opera (--configure):
 subprocess post-installation script returned error exit status 127
Setting up sun-java5-bin (1.5.0-15-0ubuntu1) ...
/var/lib/dpkg/info/sun-java5-bin.postinst: 80: update-alternatives: not found
dpkg: error processing sun-java5-bin (--configure):
 subprocess post-installation script returned error exit status 127
dpkg: dependency problems prevent configuration of sun-java5-plugin:
 sun-java5-plugin depends on sun-java5-bin (= 1.5.0-15-0ubuntu1); however:
  Package sun-java5-bin is not configured yet.
 sun-java5-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java5-plugin (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of sun-java6-plugin:
 sun-java6-plugin depends on xulrunner-1.9; however:
  Package xulrunner-1.9 is not configured yet.
dpkg: error processing sun-java6-plugin (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 sun-java6-jdk
 cacao
 xulrunner-1.9
 firefox-3.0
 firefox
 xulrunner-1.9-gnome-support
 firefox-3.0-gnome-support
 firefox-gnome-support
 opera
 sun-java5-bin
 sun-java5-plugin
 sun-java6-plugin
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by ChameleonDave on 2008-07-01
That's a very difficult-to-read mess.  When quoting stuff like that, it can be helpful to select it and then click on the "#" icon to format it as code.

It seems that moving "update-alternatives" out of the way did help to some extent.  Let's try to repair that file.

```
cd /usr/sbin
sudo cp update-alternatives.backup  update-alternatives

```

That will put the file back as it was.  Now, open the file for editing:

```
sudo nano update-alternatives
```

You can replace "nano" with your favourite text editor.

Here is the first section of that file on my computer:

```

#!/usr/bin/perl --

use strict;
use warnings;

use POSIX qw(:errno_h);
use Dpkg;
use Dpkg::Gettext;

textdomain("dpkg");

```

Compare it with yours, and edit yours to make it similar.  I know mine works for me, at least.  Is yours very different?

You can then try "sudo dpkg --configure --pending" again and see if it's any better.

---

### Post by Cront on 2008-07-01
Hmm I have exactly that at the top of my file

---

