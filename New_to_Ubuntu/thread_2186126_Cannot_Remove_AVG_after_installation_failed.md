---
title: "Cannot Remove AVG after installation failed"
date: 2013-11-05
forum: New to Ubuntu
---

### Post by keatkean on 2013-11-05
Everytime I want to install or remove a program, this error msg occur:

```
Processing triggers for gnome-menus ...
Processing triggers for desktop-file-utils ...
Processing triggers for bamfdaemon ...
Rebuilding /usr/share/applications/bamf-2.index...
Processing triggers for mime-support ...
Processing triggers for man-db ...
Setting up avg2013flx (2013.3115) ...
chown: cannot access /opt/avg/av: No such file or directory
dpkg: error processing avg2013flx (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
Errors were encountered while processing:
 avg2013flx
Error in function: 

```

I had tried follow this thread:```
[http://ubuntuforums.org/showthread.php?t=426070](http://ubuntuforums.org/showthread.php?t=426070)
```
But Its Show :
```
(Reading database ... 166553 files and directories currently installed.)Removing avg2013flx ...
invoke-rc.d: unknown initscript, /etc/init.d/avgd not found.
dpkg: error processing avg2013flx (--purge):
 subprocess installed pre-removal script returned error exit status 100
Errors were encountered while processing:
 avg2013flx



```

---

### Post by DuckHook on 2013-11-06
Very sorry to hear this. I'm afraid that I will be of only limited help to you here because I don't use AV at all. Hopefully, some guru can step in to help you resolve your immediate issue.

Unfortunately, your situation is an example of why AV software simply should not be installed on Linux. At best, it is a worthless resource pig. At worst, it mangles your system with its attempt to insert hooks and calls into the guts of your kernel that resemble nothing so much as rootkits.

Is this a brand new install? If so, your best bet may simply be to reinstall to a pristine environment and this time don't touch any sort of AV with a ten-foot pole. If this is an older installation, you should at least back up your critical data *right now* so that you limit any sort of downside to yourself.

It's weird that a number of queries/issues have recently cropped up dealing with AV. Coincidence perhaps, but nonetheless, you may wish to read [this]("http://ubuntuforums.org/showthread.php?t=2184758&p=12833795#post12833795") after you straighten out your current problem.

---

### Post by warp99 on 2013-11-06
It appears that script is trying to remove a directory that doesn't exist. Try the --force option on dkpg to remove the package.

---

### Post by keatkean on 2013-11-06
The problem still persist after using --force option....

---

### Post by DuckHook on 2013-11-06
You have not answered my questions.

If this is a new install, you are better off following my suggestion to do over from scratch. By the time you wrestle this one to the ground, you will spend far more time and effort than the 20 minutes needed to re-install.

---

### Post by ian-weisser on 2013-11-06
Please describe exactly where you got the avg2013flx package from.
I'm not seeing it in the (supported) Ubuntu repositories.
Did you download it from somewhere else? If so, it's not supported by this community - you may need to contact AVG forums for support.

Your package manager will remain broken until you remove this package.

If you want our help removing it, please show us a *complete* terminal session of a failed uninstall, including the commands you used.
Also, please show us the output of the command:** dpkg -L avg2013flx**

---

### Post by sandyd on 2013-11-06
> subprocess installed pre-removal script returned error exit status 100
1.
Run this
```

sudo ln -s /bin/true /etc/init.d/avgd
```
and try to remove it again

2. Else if another error pops up, try renaming the pre/postrm script for avg

```

sudo mv /var/lib/dpkg/info/avg2013flx.postrm /var/lib/dpkg/info/avg2013flx.postrm.bak
```
prerm script should be
```

sudo mv /var/lib/dpkg/info/avg2013flx.prerm /var/lib/dpkg/info/avg2013flx.prerm.bak
```

---

### Post by keatkean on 2013-11-07
First,run this command:
```
sudo ln -s /bin/true /etc/init.d/avgd
```

Then Run This command:
```
[COLOR=#000000][FONT=Ubuntu Mono]sudo dpkg -R -P avg2013flx[/FONT][/COLOR]
```

Problem Solved.
Thank You Very Much For Helping Me

---

### Post by craig10x on 2013-11-07
Glad to hear they were able to help you solve the issue...best to avoid any anti-virus on linux....really not needed...it's nothing like windows in that regard....been on it since 2008 and never had a problem yet...
Only thing i would suggest, is (if you haven't already done so) download the program called GUFW from the software center (that is the GUI interface for the linux firewall) and just turn it ON...and that's it!

---

