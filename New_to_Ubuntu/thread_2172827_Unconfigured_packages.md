---
title: "Unconfigured packages"
date: 2013-09-06
forum: New to Ubuntu
---

### Post by Paun_Remus on 2013-09-06
Hello to all,

I have recently installed UBUNTu 13.04 and started to install packages from the Ubuntu software center. After each installation I get this message (posted below). Could anyone please tell me how to configure these packages:

 [B]libcrystalhd3:amd64 
 vlc-nox 
 vlc-plugin-pulse 
 vlc 
 vlc-plugin-notify[/B]

I mention that these packages are allready installed. 
Thanks in advance!

```
installArchives() failed: Selecting previously unselected package vlc. 
(Reading database ...  (Reading database ... 5% (Reading database ... 10% (Reading database ... 15% (Reading database ... 20% (Reading database ... 25% (Reading database ... 30% (Reading database ... 35% (Reading database ... 40% (Reading database ... 45% (Reading database ... 50% (Reading database ... 55% (Reading database ... 60% (Reading database ... 65% (Reading database ... 70% (Reading database ... 75% (Reading database ... 80% (Reading database ... 85% (Reading database ... 90% (Reading database ... 95% (Reading database ... 100% (Reading database ... 187240 files and directories currently installed.) 
Unpacking vlc (from .../vlc_2.0.8-0ubuntu0.13.04.1_amd64.deb) ... 
Selecting previously unselected package vlc-plugin-notify. 
Unpacking vlc-plugin-notify (from .../vlc-plugin-notify_2.0.8-0ubuntu0.13.04.1_amd64.deb) ... 
Processing triggers for mime-support ... 
Processing triggers for bamfdaemon ... 
Rebuilding /usr/share/applications/bamf-2.index... 
Processing triggers for desktop-file-utils ... 
Processing triggers for gnome-menus ... 
Processing triggers for man-db ... 
dpkg: error processing libcrystalhd3:amd64 (--configure): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting configuration. 
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libcrystalhd3; however: 
  Package libcrystalhd3:amd64 is not configured yet. 
 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 2.0.8-0ubuntu0.13.04.1); however: 
  Package vlc-nox is not configured yet. 
 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfiguredNo apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 2.0.8-0ubuntu0.13.04.1); however: 
  Package vlc-nox is not configured yet. 
 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-notify: 
 vlc-plugin-notify depends on vlc-nox (= 2.0.8-0ubuntu0.13.04.1); however: 
  Package vlc-nox is not configured yet. 
 
dpkg: error processing vlc-plugin-notify (--configure): 
 dependency problems - leaving unconfigured 
No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
Errors were encountered while processing: 
 libcrystalhd3:amd64 
 vlc-nox 
 vlc-plugin-pulse 
 vlc 
 vlc-plugin-notify 
dpkg: error processing libcrystalhd3:amd64 (--configure): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting configuration. 
dpkg: dependency problems prevent configuration of vlc-nox: 
 vlc-nox depends on libcrystalhd3; however: 
  Package libcrystalhd3:amd64 is not configured yet. 
 
dpkg: error processing vlc-nox (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc: 
 vlc depends on vlc-nox (= 2.0.8-0ubuntu0.13.04.1); however: 
  Package vlc-nox is not configured yet. 
 
dpkg: error processing vlc (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-notify: 
 vlc-plugin-notify depends on vlc-nox (= 2.0.8-0ubuntu0.13.04.1); however: 
  Package vlc-nox is not configured yet. 
 
dpkg: error processing vlc-plugin-notify (--configure): 
 dependency problems - leaving unconfigured 
dpkg: dependency problems prevent configuration of vlc-plugin-pulse: 
 vlc-plugin-pulse depends on vlc-nox (= 2.0.8-0ubuntu0.13.04.1); however: 
  Package vlc-nox is not configured yet. 
 
dpkg: error processing vlc-plugin-pulse (--configure): 
 dependency problems - leaving unconfigured 
```

---

### Post by newb85 on 2013-09-06
Try this:
```
sudo dpkg-reconfigure vlc-nox
sudo apt-get -f install
```

---

### Post by ian-weisser on 2013-09-07
> **Paun_Remus said:**
> 
```
[...]

dpkg: error processing libcrystalhd3:amd64 (--configure): 
 Package is in a very bad inconsistent state - you should 
 reinstall it before attempting configuration. 

[...]

```

Remove the damaged package from your cache with **sudo apt-get clean libcrystalhd3:amd64 **
Redownload and reinstall with **sudo apt-get install --reinstall libcrystalhd3:amd64 **

---

### Post by newb85 on 2013-09-07
Good catch, ian-weisser.  I missed that part.

It seems to me the OP has installed the 64-bit version of libcrystalhd3 on a 32-bit system, and that may be the source of the problem.

Edit: on second thought, it looks like the 64-bit version is a a dependency of the 32-bit version.  Odd...

---

### Post by ian-weisser on 2013-09-07
Well, if the reinstall fails due to an architecture incompatibility, then we will know....
Seen quite a few of those after people install Skype.

---

### Post by Paun_Remus on 2013-09-07
Tried this and got the following message:

E: Could not get lock /var/lib/dpkg/lock - open (11: Resource temporarily unavailable)
E: Unable to lock the administration directory (/var/lib/dpkg/), is another process using it?

Am I doing somethig wrong?

---

### Post by bapoumba on 2013-09-07
@Paun_Remus : please close any other package manager that may be open.

---

### Post by Paun_Remus on 2013-09-09
I did this and there was no package manager that was preventing me from reinstalling [B]libcrystalhd3:amd64

[/B]I also restarted my notebook and got the same answer. Clearly there is something odd here. Any more sugestions?

---

### Post by bapoumba on 2013-09-09
**sudo rm /var/lib/dpkg/lock**
For some reason, the lock file that prevent 2 packages managers to run at the same time may not have been deleted.

---

