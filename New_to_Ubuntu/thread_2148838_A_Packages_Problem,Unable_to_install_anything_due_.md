---
title: "A Packages Problem,Unable to install anything due to unconfigured and depandesies"
date: 2013-05-26
forum: New to Ubuntu
---

### Post by thekoalover on 2013-05-26
Hi, I've had 12.10 for four months now, problem for 3 :P its an amazing OS, but my problem i think is when i left it updating and installing packages and in the middle the electricity went off, i've tried every single command and way on every thread and site, nothing worked.. this is the Line.. please help,Thank you so very much.

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 183 not upgraded.
17 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lsb-release (4.0-0ubuntu26.1) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/lsb-release.postinst): Input/output error
dpkg: error processing lsb-release (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not coNo apport report written because the error message indicates its a followup error from a previous failure.
                                                                 No apport report written because MaxReports is reached already
                                               No apport report written because MaxReports is reached already
                             No apport report written because MaxReports is reached already
           No apport report written because MaxReports is reached already
                                                                         No apport report written because MaxReports is reached already
                                                       No apport report written because MaxReports is reached already
                                     No apport report written because MaxReports is reached already
                   No apport report written because MaxReports is reached already
 No apport report written because MaxReports is reached already
                                                               No apport report written because MaxReports is reached already
                                             nfigured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3-update-manager (= 1:0.174.4); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends oNo apport report written because MaxReports is reached already
                                                                               No apport report written because MaxReports is reached already
                                                             No apport report written because MaxReports is reached already
                                           No apport report written because MaxReports is reached already
                         n python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.

dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-unity:
 xul-ext-unity depends on firefox (>= 10.0); however:
  Package firefox is not configured yet.

dpkg: error processing xul-ext-unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 19.0+build1-0ubuntu0.12.10.2); however:
  Package firefox is not configured yet.

dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.

dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.174.4); however:
  Package update-manager-core is not configured yet.

dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:0.190.5); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xdiagnose:
 xdiagnose depends on python3-apport; however:
  Package python3-apport is not configured yet.

dpkg: error processing xdiagnose (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-drivers-common
 lsb-release
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 update-manager-core
 python3-apport
 apport
 apport-gtk
 firefox
 xul-ext-unity
 firefox-globalmenu
 firefox-gnome-support
 python-apport
 update-manager
 ubuntu-release-upgrader-gtk
 xdiagnose
```

---

### Post by thekoalover on 2013-05-29
bump

---

### Post by oldrocker99 on 2013-05-29
I saw your request for help. Try this:

sudo apt-get -f install


and see what happens

---

### Post by thekoalover on 2013-05-29
kl

---

### Post by thekoalover on 2013-05-29
@Oldrocker99 This Happens, Same Thing


```
thekoalover@Batman:~$ sudo apt-get -f install
[sudo] password for thekoalover: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 183 not upgraded.
17 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lsb-release (4.0-0ubuntu26.1) ...
dpkg (subprocess): unable to execute installed post-installation script  (/var/lib/dpkg/info/lsb-release.postinst): Input/output error
dpkg: error processing lsb-release (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of  ubuntu-release-upgradNo apport report written because the error message  indicates its a followup error from a previous failure.
                  No apport report written because MaxReports is reached already
No apport report written because MaxReports is reached already
                                                              No apport report written because MaxReports is reached already
                                            No apport report written because MaxReports is reached already
                          No apport report written because MaxReports is reached already
        No apport report written because MaxReports is reached already
                                                                      No  apport report written because MaxReports is reached already
                                                    No apport report written because MaxReports is reached already
                                  No apport report written because MaxReports is reached already
                No apport report written because MaxReports is reached already
                                                                              er-core:
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3-update-manager (= 1:0.174.4); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-apport (--No apport report written because MaxReports is reached already
                       No apport report written because MaxReports is reached already
     No apport report written because MaxReports is reached already
                                                                   No  apport report written because MaxReports is reached already
                                                 configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.

dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-unity:
 xul-ext-unity depends on firefox (>= 10.0); however:
  Package firefox is not configured yet.

dpkg: error processing xul-ext-unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 19.0+build1-0ubuntu0.12.10.2); however:
  Package firefox is not configured yet.

dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.

dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.174.4); however:
  Package update-manager-core is not configured yet.

dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:0.190.5); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xdiagnose:
 xdiagnose depends on python3-apport; however:
  Package python3-apport is not configured yet.

dpkg: error processing xdiagnose (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-drivers-common
 lsb-release
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 update-manager-core
 python3-apport
 apport
 apport-gtk
 firefox
 xul-ext-unity
 firefox-globalmenu
 firefox-gnome-support
 python-apport
 update-manager
 ubuntu-release-upgrader-gtk
 xdiagnose
E: Sub-process /usr/bin/dpkg returned an error code (1)
```

---

### Post by oldrocker99 on 2013-05-29
Well, it looks like your system may be hosed beyond my ability to help. It it had happened to me, I would simply reinstall the system. This is a LOT faster if your /home is on another partition, otherwise you should back up your /home folder and reinstall.


Sorry to be the bearer of bad news...

---

### Post by thekoalover on 2013-05-29
nah it's okay thank you very much, ill keep this thread and spreading around till i get an answer, reinstalling is not an option right now :P thanks a lot,Friend :D

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]thekoalover;

What ya got here 'pears to be what is termed "dependency hell" ! As (re-)installing is not an option, perhaps with time and patience we can work through it, For starters, get rid of obsolete files and related dunnage :
[/COLOR]```
 sudo apt-get autoclean
sudo apt-get autoremove
sudo apt-get clean 
```
And now to start the descent, do some pok'n at "apport-gtk" :
Post the output of terminal code:
```
dpkg - L apport-gtk
```, try'n to get down to the base of one dependency, work our way around. Tackle these things - one thing-at-a-time ....

Looks like if we can fix "apport-gtk" may make a lot of packages happy.[INDENT]
wont know 'till we try

[/INDENT]
[COLOR=#000000]
[/COLOR]

---

### Post by thekoalover on 2013-05-30
Bashing-om;
So I Tried All The Codes, And This Happens, Now What,And Thank You For The Reply
```
 thekoalover@Batman:~$ dpkg -L apport-gtk
/.
/usr
/usr/share
/usr/share/doc
/usr/share/doc/apport-gtk
/usr/share/doc/apport-gtk/copyright
/usr/share/apport
/usr/share/apport/apport-gtk.ui
/usr/share/apport/apport-gtk
/usr/share/applications
/usr/share/applications/apport-gtk-mime.desktop
/usr/share/doc/apport-gtk/changelog.Debian.gz 
```

---

### Post by matt_symes on 2013-05-30
Hi

> dpkg (subprocess): unable to execute installed post-installation script  (/var/lib/dpkg/info/lsb-release.postinst): Input/output error

This is your main problem and is the reason why you are having most of the dependencies problems you are having.

We need to take a look at this file.

Please post the output of 

```
stat /var/lib/dpkg/info/lsb-release.postinst
```

```
ls -li /var/lib/dpkg/info/lsb-release.postinst
```

```
file /var/lib/dpkg/info/lsb-release.postinst
```

```
df -h | grep /$
```

Have you tried to run fsck on the partition from a LiveCD/USB or from recovery mode yet ?

Kind regards

---

### Post by thekoalover on 2013-05-30
matt_symes;
so this is by order 
```
 thekoalover@Batman:~$ stat /var/lib/dpkg/info/lsb-release.postinst
  File: `/var/lib/dpkg/info/lsb-release.postinst'
  Size: 871           Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d    Inode: 20713729    Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2013-05-30 01:13:07.541153986 +0200
Modify: 2012-10-24 02:34:42.000000000 +0200
Change: 2013-03-05 03:42:49.647701053 +0200
 Birth: -

 
```

second:  ```
 thekoalover@Batman:~$ ls -li /var/lib/dpkg/info/lsb-release.postinst
20713729 -rwxr-xr-x 1 root root 871 Oct 24  2012 /var/lib/dpkg/info/lsb-release.postinst

 
```

Third: ```
 thekoalover@Batman:~$ file /var/lib/dpkg/info/lsb-release.postinst
/var/lib/dpkg/info/lsb-release.postinst: ERROR: cannot read `/var/lib/dpkg/info/lsb-release.postinst' (Input/output error)

 
```

Fourth : ```
 thekoalover@Batman:~$ df -h | grep /$
/dev/sda1       457G  214G  220G  50% /

 
```

And No I Haven't Tried Running fsck on the partition

---

### Post by Bashing-om on 2013-05-30
@ Matt ... As always, thanks ! I seem to be in a learning mode once again.

My "stat" output for comparison:
> File: &#8216;/var/lib/dpkg/info/lsb-release.postinst&#8217;  Size: 871           Blocks: 8          IO Block: 4096   regular file
Device: 808h/2056d    Inode: 128856      Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2013-05-19 10:55:21.600505048 -0500
Modify: 2012-10-23 19:32:46.000000000 -0500
Change: 2013-05-19 10:54:54.616844279 -0500
 Birth: -
What is the significance of [COLOR=#000000]thekoalover's output "+0200" as opposed to mine "-500" mean ?

@ thekoalover; Following Matt's lead; what does the "lsb-release.postinst" script file look like ?
post the output of:
[/COLOR] ```
cat /[COLOR=#000000][FONT=Ubuntu Mono]var/lib/dpkg/info/lsb-release.postinst [/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR][INDENT=2][COLOR=#000000]
as I continue to play catch-up

[/COLOR][/INDENT]

---

### Post by westie457 on 2013-05-30
> **Bashing-om said:**
> @ Matt ... As always, thanks ! I seem to be in a learning mode once again.

My "stat" output for comparison:

What is the significance of [COLOR=#000000]thekoalover's output "+0200" as opposed to mine "-500" mean ?

@ thekoalover; Following Matt's lead; what does the "lsb-release.postinst" script file look like ?
post the output of:
```
 /
```[/COLOR]```
[COLOR=#000000][FONT=Ubuntu Mono]var/lib/dpkg/info/lsb-release.postinst[/FONT][/COLOR]
```[COLOR=#000000]
[/COLOR][COLOR=#000000]
[/COLOR][INDENT=2][COLOR=#000000]
as I continue to play catch-up

[/COLOR][/INDENT]



It looks like a time-stamp. In your case Bashing-om UTC minus 5 hours. in the OPs case, UTC plus 2 hours.


Purely for comparison purposes here is mine, I am in the UK.

```
graham@graham-Aspire-5755G:~$ stat /var/lib/dpkg/info/lsb-release.postinst  File: `/var/lib/dpkg/info/lsb-release.postinst'
  Size: 871       	Blocks: 8          IO Block: 4096   regular file
Device: 816h/2070d	Inode: 2231710     Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2013-04-30 12:45:44.595490455 +0100
Modify: 2012-10-24 01:38:33.000000000 +0100
Change: 2012-10-29 14:53:05.559253464 +0000



```
Other that this I have no ideas about the OPs issue or how to fix it.

---

### Post by thekoalover on 2013-05-30
@Bashing-Om this happen 
```
 thekoalover@Batman:~$ /var/lib/dpkg/info/lsb-release.postinst
bash: /var/lib/dpkg/info/lsb-release.postinst: Input/output error

 
```

---

### Post by Bashing-om on 2013-05-30
[COLOR=#000000]thekoalover; OOppss -> thought I had fixed that "messed up code tags" lemme try again.
```
 cat /var/lib/dpkg/info/lsb-release.postinst
```
Don't know what is happening within my browser that "additional" code tags are being added. happened on this post also--- so maually typed the above - carefully check the path for errors in my typing.
[/COLOR][COLOR=#000000][FONT=Ubuntu Mono]

@ [/FONT][/COLOR][COLOR=#000000]westie457 , thanks ,for the "time stamp" info advisement, honestly I did not want to take the time at this time to read the manual, had no idea it would be such !
[/COLOR][INDENT][COLOR=#000000]
nothing better to do ? Let's read some code ! [/COLOR][/INDENT]

---

### Post by thekoalover on 2013-05-30
@Bashing-om This 
```
thekoalover@Batman:~$ cat /var/lib/dpkg/info/lsb-release-postinst
cat: /var/lib/dpkg/info/lsb-release-postinst: No such file or directory
  
```

---

### Post by Bashing-om on 2013-05-31
[COLOR=#000000]thekoalover;

Regret the delay in getting back with you, storms and power outages here on my end, one of them caught me big time too - fixed it all up and back in business ...
The missing file we may be able to overcome. Verify though that it is no longer in existence.

Oopsie again on my part, var is correct, no such file exist. Correct sequence - I will correct my post-

[/COLOR]```
cat /var/lib/dpkg/info/lsb-release.postinst
``` from the typeo
[COLOR=#000000][FONT=Ubuntu Mono][INDENT]
and then we will take off again

[/INDENT]


[/FONT][/COLOR]

---

### Post by mc4man on 2013-05-31
A couple of things for possible use - 
Do you have the lsb-release package available (maybe dpkg can configure or install
```
ls /var/cache/apt/archives |grep lsb
```

You mentioned trying all sorts of commands, did you try to configure lsb-release or all unconfigured packages?

```
sudo dpkg --configure lsb-release
```
```
sudo dpkg --configure --pending
```

This is just a simulation - want to see if apt is willing to/can purge lsb-release

```
sudo apt-get -s purge lsb-release
```

---

### Post by thekoalover on 2013-06-01
@Bashing-om Still :/ ```
 thekoalover@Batman:~$ cat /var/lib/dpkg/info/lsb-release.postinst
cat: /var/lib/dpkg/info/lsb-release.postinst: Input/output error

 
```


@mc4man thanks for replying, by order
```
 thekoalover@Batman:~$ ls /var/cache/apt/archives |grep lsb
thekoalover@Batman:~$ 


 
```[**[COLOR=#000000][/COLOR]**]("http://ubuntuforums.org/member.php?u=320715")

```
 thekoalover@Batman:~$ sudo dpkg --configure lsb-release
[sudo] password for thekoalover: 
Setting up lsb-release (4.0-0ubuntu26.1) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/lsb-release.postinst): Input/output error
dpkg: error processing lsb-release (--configure):
 subprocess installed post-installation script returned error exit status 2
Errors were encountered while processing:
 lsb-release

 
```

```
 thekoalover@Batman:~$ sudo dpkg --configure --pending
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3-update-manager; however:
  Package python3-update-manager is not configured yet.
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-apport (--configure):
 dependency problems - leaving unconfigured
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.174.4); however:
  Package update-manager-core is not configured yet.

dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 19.0+build1-0ubuntu0.12.10.2); however:
  Package firefox is not configured yet.

dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-core:
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-unity:
 xul-ext-unity depends on firefox (>= 10.0); however:
  Package firefox is not configured yet.

dpkg: error processing xul-ext-unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.

dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python-apport
 update-manager-core
 python3-update-manager
 python3-distupgrade
 python3-apport
 ubuntu-drivers-common
 firefox
 update-manager
 ubuntu-release-upgrader-gtk
 firefox-globalmenu
 ubuntu-release-upgrader-core
 xul-ext-unity
 firefox-gnome-support
 
```

```
 thekoalover@Batman:~$ sudo apt-get -s purge lsb-release
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libufe-xidgetter0
The following packages will be REMOVED:
  apport* apport-gtk* apturl* apturl-common* command-not-found* firefox*
  firefox-globalmenu* firefox-gnome-support* gir1.2-ubuntuoneui-3.0*
  libsyncdaemon-1.0-1* libubuntuoneui-3.0-1*
  lightdm-remote-session-uccsconfigure* lsb-release* nautilus-share*
  python-apport* python3-apport* python3-distupgrade*
  python3-software-properties* python3-update-manager* rhythmbox-ubuntuone*
  software-properties-common* software-properties-gtk* ubuntu-desktop*
  ubuntu-minimal* ubuntu-release-upgrader-core* ubuntu-release-upgrader-gtk*
  ubuntuone-client* ubuntuone-client-gnome* ubuntuone-control-panel*
  ubuntuone-control-panel-qt* unattended-upgrades* unity-scope-musicstores*
  update-manager* update-manager-core* update-notifier* xdiagnose*
  xul-ext-unity* xul-ext-websites-integration*
The following packages will be upgraded:
  libufe-xidgetter0
1 upgraded, 0 newly installed, 38 to remove and 175 not upgraded.
17 not fully installed or removed.
Purg apport-gtk [2.6.1-0ubuntu10]
Purg apport [2.6.1-0ubuntu10]
Purg firefox-gnome-support [19.0+build1-0ubuntu0.12.10.2]
Purg firefox-globalmenu [19.0+build1-0ubuntu0.12.10.2]
Purg xul-ext-unity [2.4.1-0ubuntu1.2]
Purg xul-ext-websites-integration [2.3.5-0ubuntu1]
Purg lightdm-remote-session-uccsconfigure [1.1-0ubuntu2]
Purg firefox [19.0+build1-0ubuntu0.12.10.2]
Purg ubuntu-desktop [1.287]
Purg ubuntu-release-upgrader-gtk [1:0.190.5] [update-manager:i386 update-notifier:i386 ]
Purg update-manager [1:0.174.4] [update-notifier:i386 ]
Purg update-notifier [0.126]
Purg update-manager-core [1:0.174.4]
Purg ubuntu-release-upgrader-core [1:0.190.5]
Purg nautilus-share [0.7.3-1ubuntu3]
Purg apturl [0.5.1ubuntu6]
Purg apturl-common [0.5.1ubuntu6]
Purg python3-distupgrade [1:0.190.5] [python3-update-manager:i386 ]
Purg python3-update-manager [1:0.174.4]
Purg xdiagnose [3.2.2]
Purg python3-apport [2.6.1-0ubuntu10]
Purg ubuntuone-control-panel-qt [4.0.0-0ubuntu1]
Purg ubuntuone-control-panel [4.0.0-0ubuntu1]
Purg ubuntuone-client-gnome [4.0.0-0ubuntu1]
Purg unity-scope-musicstores [6.8.1-0ubuntu1]
Purg rhythmbox-ubuntuone [4.0.0-0ubuntu1]
Purg gir1.2-ubuntuoneui-3.0 [4.0.0-0ubuntu1]
Purg libubuntuoneui-3.0-1 [4.0.0-0ubuntu1]
Purg libsyncdaemon-1.0-1 [4.0.0-0ubuntu1]
Purg ubuntuone-client [4.0.0-0ubuntu1]
Purg python-apport [2.6.1-0ubuntu10]
Purg software-properties-gtk [0.92.9]
Purg software-properties-common [0.92.9]
Purg python3-software-properties [0.92.9]
Purg unattended-upgrades [0.79.3ubuntu4]
Purg ubuntu-minimal [1.287]
Purg command-not-found [0.3ubuntu5]
Purg lsb-release [4.0-0ubuntu26.1]
Inst libufe-xidgetter0 [2.4.1-0ubuntu1.2] (2.4.4-0ubuntu0.2 Ubuntu:12.10/quantal-updates [i386])
Conf ubuntu-drivers-common (1:0.2.71.1 Ubuntu:12.10/quantal-updates [i386])
Conf libufe-xidgetter0 (2.4.4-0ubuntu0.2 Ubuntu:12.10/quantal-updates [i386]) 
```

---

### Post by Bashing-om on 2013-06-01
@ [COLOR=#000000]thekoalover; Making progress !

But, that last leaves me hanging .... did you enter "y" to do it ???
Let's look at what the package manager thinks now:
```
 sudo dpkg -C
```
That is an uppercase 'c' ... consult the manual for full details:
```
man dpkg
``` long read, then might want to follow the advise given and consult the "shorter" docs.
[/COLOR][INDENT=2][COLOR=#000000]
we be stepp'n

[/COLOR][/INDENT]

---

### Post by mc4man on 2013-06-01
**If it was me** I'd run the purge command for real, then update sources & re-install ubuntu-desktop which would pull most if not all the removed packages 
(none of the removed are critical, the most important would be firefox if you currently have no other browser installed. 
So I wouldn't suggest doing that yet, only if all other attempts fail

You don't have lsb-release package in the archives, now noticed you likely ran sudo apt-get  clean

Maybe try this, can't hurt - 
```
mkdir -p test1 && cd test1 && \
wget http://mirror.pnl.gov/ubuntu//pool/main/l/lsb/lsb-release_4.0-0ubuntu26.1_all.deb
```
In same terminal (@ ~/test1$ prompt
```
sudo dpkg -i  lsb-release_4.0-0ubuntu26.1_all.deb
```

---

### Post by Cheesehead on 2013-06-01
> **thekoalover said:**
>  the electricity went off

Two things probably occurred on an unexpected poweroff.
1) Your filesystem was left in an unstable state. Easy enough to fix using fsck. Normally the system will detect this upon reboot and run fsck automatically.

2) Packages in process of download are broken, and must be removed manually. Trying to install a broken package won't work, as you have seen...

> **thekoalover said:**
>  
```
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1

Setting up lsb-release (4.0-0ubuntu26.1) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/lsb-release.postinst): Input/output error

```

Downloaded (and patially-downloaded) packages are in /var/cache/apt/archives/. You will need to use sudo to delete them. Or you can use this command to wipe all downloaded packages. It will have *not* uninstall any software, it will merely delete the .deb files from your local archive. If you need to reinstall anything, apt will need to re-download it. For most users, that's not a big problem.

```
sudo apt-get clean
```

---

### Post by thekoalover on 2013-06-02
@mac4man this what came out 
```
 thekoalover@Batman:~$ mkdir -p test1 && cd test1 && \
> wget http://mirror.pnl.gov/ubuntu//pool/main/l/lsb/lsb-release_4.0-0ubuntu26.1_all.deb
--2013-06-02 22:03:47--  http://mirror.pnl.gov/ubuntu//pool/main/l/lsb/lsb-release_4.0-0ubuntu26.1_all.deb
Resolving mirror.pnl.gov (mirror.pnl.gov)... 192.101.102.2
Connecting to mirror.pnl.gov (mirror.pnl.gov)|192.101.102.2|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 10742 (10K) [text/plain]
Saving to: `lsb-release_4.0-0ubuntu26.1_all.deb'

100%[======================================>] 10,742      36.9K/s   in 0.3s    

2013-06-02 22:03:51 (36.9 KB/s) - `lsb-release_4.0-0ubuntu26.1_all.deb' saved [10742/10742]

thekoalover@Batman:~/test1$ sudo dpkg -i  lsb-release_4.0-0ubuntu26.1_all.deb
Selecting previously unselected package lsb-release.
dpkg: warning: files list file for package 'python-gst0.10' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'vim-tiny': Input/output error

 
```

@cheesehead still the same thing :/

@bashing-om well,friend...this..

```
 thekoalover@Batman:~/test1$  sudo dpkg -C
The following packages have been unpacked but not yet configured.
They must be configured using dpkg --configure or the configure
menu option in dselect for them to work:
 ubuntu-release-upgrader-gtk manage release upgrades
 firefox-globalmenu   Unity appmenu integration for Firefox
 apport-gtk           GTK+ frontend for the apport crash report system
 python-apport        Python library for Apport crash report handling
 update-manager-core  manage release upgrades
 python3-update-manager python 3.x module for update-manager
 ubuntu-release-upgrader-core manage release upgrades
 xul-ext-unity        Firefox extension: Unity Integration
 python3-distupgrade  manage release upgrades
 firefox-gnome-support Safe and easy web browser from Mozilla - GNOME support
 python3-apport       Python 3 library for Apport crash report handling
 firefox              Safe and easy web browser from Mozilla
 xdiagnose            X.org diagnosis tool
 update-manager       GNOME application that manages apt updates
 apport               automatically generate crash reports for debugging

The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 lsb-release          Linux Standard Base version reporting utility
 ubuntu-drivers-common Detect and install additional Ubuntu driver packages

The following packages are missing the list control file in the
database, they need to be reinstalled:
 libgnome-keyring-common GNOME keyring services library - data files
 python-gst0.10       generic media-playing framework (Python bindings)

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 python-gst0.10       generic media-playing framework (Python bindings)

 
```
I Feel We're Getting Real Close..Now What?

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]thekoalover; 

Lemme put it like this, the package manager is smart, smarter about managing packages than I will ever be. I would literally take dpkg's advise and comply with the directives. In the event (that does happen) that the package manager gets confused and does not know what to do, we can take matters into our own hands and try to resolve the dependencies... one at a time and very small steps at that. What often happens in this circumstance is following a trail of dependencies and getting to the bottom of them, then working our way back up, installing as we go. Very tedious and time consuming... with care and attention it can be done !

Starting with lsb-release dependencies "python-gst0.10" and "libgnome-keyring-common //see what "apt-get install <package_name>" has to say.

Now with that said, there is not a thing wrong with waiting on cheesehead or mc4man or others with a greater amount of experience with linux to respond and advise............ there may be a much simpler solution than piecemeal (re)constrction.

As to what I would do........ piecemeal construction !! ..... might learn a whole lot in general and even more in particular.
[/COLOR][INDENT][COLOR=#000000]
given the options, only you can decide [/COLOR][/INDENT]

---

### Post by thekoalover on 2013-06-02
Bashing-om; Whatever Way That Gets It Done,Mate :P
and this is what it has to say 
It tells me both the python-gst and the libgnome are installed and configured yet wont work..
```
thekoalover@Batman:~$ apt-get install python-gst0.10 libgnome-keyring-common
E: Could not open lock file /var/lib/dpkg/lock - open (13: Permission denied)
E: Unable to lock the administration directory (/var/lib/dpkg/), are you root?
thekoalover@Batman:~$ sudo apt-get install python-gst0.10 libgnome-keyring-common
[sudo] password for thekoalover: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
libgnome-keyring-common is already the newest version.
python-gst0.10 is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic
  ttf-droid ttf-umefont ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 194 not upgraded.
17 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lsb-release (4.0-0ubuntu26.1) ...
dpkg (subprocess): unable to execute installed post-installation script (/var/lib/dpkg/info/lsb-release.postinst): Input/output error
dpkg: error processing lsb-release (--configure):
 subprocess installed post-installation script returned error exit status 2
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgradNo apport report written because the error message indicates its a followup error from a previous failure.
                                                No apport report written because MaxReports is reached already
                                             No apport report written because MaxReports is reached already
                                          No apport report written because MaxReports is reached already
                                       No apport report written because MaxReports is reached already
                                    No apport report written because MaxReports is reached already
                                 No apport report written because MaxReports is reached already
                              No apport report written because MaxReports is reached already
                           No apport report written because MaxReports is reached already
                        No apport report written because MaxReports is reached already
                     No apport report written because MaxReports is reached already
                  er-core:
 ubuntu-release-upgrader-core depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager-core:
 update-manager-core depends on python3-update-manager (= 1:0.174.4); however:
  Package python3-update-manager is not configured yet.
 update-manager-core depends on lsb-release; however:
  Package lsb-release is not configured yet.
 update-manager-core depends on ubuntu-release-upgrader-core; however:
  Package ubuntu-release-upgrader-core is not configured yet.

dpkg: error processing update-manager-core (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python3-apport:
 python3-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-apport (--No apport report written because MaxReports is reached already
                                      No apport report written because MaxReports is reached already
                                   No apport report written because MaxReports is reached already
                                No apport report written because MaxReports is reached already
                             configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport:
 apport depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.

dpkg: error processing apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of apport-gtk:
 apport-gtk depends on python3-apport (>= 2.6.1-0ubuntu10); however:
  Package python3-apport is not configured yet.
 apport-gtk depends on apport (>= 0.41); however:
  Package apport is not configured yet.

dpkg: error processing apport-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox:
 firefox depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing firefox (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xul-ext-unity:
 xul-ext-unity depends on firefox (>= 10.0); however:
  Package firefox is not configured yet.

dpkg: error processing xul-ext-unity (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-globalmenu:
 firefox-globalmenu depends on firefox (= 19.0+build1-0ubuntu0.12.10.2); however:
  Package firefox is not configured yet.

dpkg: error processing firefox-globalmenu (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of firefox-gnome-support:
 firefox-gnome-support depends on firefox; however:
  Package firefox is not configured yet.

dpkg: error processing firefox-gnome-support (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of python-apport:
 python-apport depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python-apport (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of update-manager:
 update-manager depends on update-manager-core (= 1:0.174.4); however:
  Package update-manager-core is not configured yet.

dpkg: error processing update-manager (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of ubuntu-release-upgrader-gtk:
 ubuntu-release-upgrader-gtk depends on ubuntu-release-upgrader-core (= 1:0.190.5); however:
  Package ubuntu-release-upgrader-core is not configured yet.
 ubuntu-release-upgrader-gtk depends on update-manager; however:
  Package update-manager is not configured yet.
 ubuntu-release-upgrader-gtk depends on python3-distupgrade (= 1:0.190.5); however:
  Package python3-distupgrade is not configured yet.

dpkg: error processing ubuntu-release-upgrader-gtk (--configure):
 dependency problems - leaving unconfigured
dpkg: dependency problems prevent configuration of xdiagnose:
 xdiagnose depends on python3-apport; however:
  Package python3-apport is not configured yet.

dpkg: error processing xdiagnose (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 ubuntu-drivers-common
 lsb-release
 python3-distupgrade
 python3-update-manager
 ubuntu-release-upgrader-core
 update-manager-core
 python3-apport
 apport
 apport-gtk
 firefox
 xul-ext-unity
 firefox-globalmenu
 firefox-gnome-support
 python-apport
 update-manager
 ubuntu-release-upgrader-gtk
 xdiagnose
E: Sub-process /usr/bin/dpkg returned an error code (1)
thekoalover@Batman:~$ sudo dpkg --configure python-gst0.10
dpkg: error processing python-gst0.10 (--configure):
 package python-gst0.10 is already installed and configured
Errors were encountered while processing:
 python-gst0.10
  
```

---

### Post by Bashing-om on 2013-06-02
thekoalover;

Try this and see if it gives us any better hints as to what dpkg wants:
```
 sudo dpkg --configure lsb-release_4.0-0ubuntu26.1
```

Once again, after that (re)install, this might force it to configure (?). If and when lsb-release is stable, will go a long way to resolving the other issues.

[INDENT]worth a shot[/INDENT]

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]thekoalover;
I be drilling down and looking...
when ya get done with --reconfigure //
lets look at 
```
dpkg -l lsb-release
``` for a status
now next what are it's dependencies (my system says python3);
```
apt-cache show lsb-release
```
Now, what state is python(?) in ?
```
dpkg -l python3
``` python3 is on my system, your version may be different.

now we can either try and configure python, or, (re-)install python and see what results.
[/COLOR][INDENT][COLOR=#000000]
little steps, but we be stepp'n

[/COLOR][/INDENT]

---

### Post by thekoalover on 2013-06-02
```
thekoalover@Batman:~$ sudo dpkg --configure lsb-release_4.0-0ubuntu26.1
dpkg: error processing lsb-release_4.0-0ubuntu26.1 (--configure):
 no package named `lsb-release_4.0-0ubuntu26.1' is installed, cannot configure
Errors were encountered while processing:
 lsb-release_4.0-0ubuntu26.1

```

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]thekoalover; Yuk, but not surprised;

Lets start building from the bottom up with what is presently known.
```
dpkg -l python3
dpkg -l python3-update-manager
dpkg -l python3-distupgrade
dpkg -l python3-apt
work'n to try and get lsb-release installed.

```
[/COLOR][INDENT=2][COLOR=#000000]
where there is a will there is a way

[/COLOR][/INDENT]

---

### Post by thekoalover on 2013-06-02
@Bashing-om Lead The Way Cap'n!

```
thekoalover@Batman:~$ sudo dpkg -l python3
[sudo] password for thekoalover: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python3        3.2.3-5ubunt all          interactive high-level object-ori
thekoalover@Batman:~$ sudo dpkg -l python3-update-manager
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  python3-update 1:0.174.4    all          python 3.x module for update-mana
thekoalover@Batman:~$ sudo dpkg -l python3-distupgrade
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  python3-distup 1:0.190.5    all          manage release upgrades
thekoalover@Batman:~$ sudo dpkg -l python3-apt
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python3-apt    0.8.7ubuntu4 i386         Python 3 interface to libapt-pkg
```

---

### Post by Bashing-om on 2013-06-02
[COLOR=#000000]thekoalover;
OK --here we go... 
looking good --of the three last, only 1 shows a problem and it says it is fixable as it is installed, but not configured - python3-update-manager -

While I am lookin about for next step go ahead and configure that one..
```
dpkg --configure python3-update-manager
```

and I be putting it together for next.[/COLOR]

---

### Post by thekoalover on 2013-06-03
@Bashing-om The Lsb-release again :/
```
thekoalover@Batman:~$ sudo dpkg --configure python3-update-manager
[sudo] password for thekoalover: 
dpkg: dependency problems prevent configuration of python3-update-manager:
 python3-update-manager depends on python3-distupgrade; however:
  Package python3-distupgrade is not configured yet.
 python3-update-manager depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-update-manager (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-update-manager
```

---

### Post by Bashing-om on 2013-06-03
thekoalover; My afternonn to ya !

I playing catch ya as I can...
To situation at hand. we will put "my next step on hold" and direct our attention to python3-update-manager, as around and around we go with these dependencies...
```
apt-cache show python3-update-manager
```
In that output are it's dependencies, and we want to know their install status:
```
 dpkg -l python3-apt
dpkg -l python3-distupgrade

```
depending on that output is what we do next.
[INDENT]still look'n to get to the bottom of "dependencies"[/INDENT]

---

### Post by thekoalover on 2013-06-03
@Bashing-om Aiight This Is it..
```
  thekoalover@Batman:~$ apt-get show python3-update-manager
E: Invalid operation show
thekoalover@Batman:~$ sudo apt-get show python3-update-manager
[sudo] password for thekoalover: 
E: Invalid operation show
thekoalover@Batman:~$ sudo dpkg -l python3-apt
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  python3-apt    0.8.7ubuntu4 i386         Python 3 interface to libapt-pkg
thekoalover@Batman:~$ sudo dpkg -l python3-distupgrade 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  python3-distup 1:0.190.5    all          manage release upgrades
 
```

---

### Post by Bashing-om on 2013-06-03
[COLOR=#000000]thekoalover; Sorry bout that, getting scattered brained with many working threads dancing within my mind,
command should have been
```
apt-cache show python3-update-manager
``` I will correct the erroronnious (sp) entry.


sheeshh

[/COLOR]

---

### Post by thekoalover on 2013-06-03
@Bashing-om Aiight
```
  thekoalover@Batman:~$ apt-cache show python3-update-manager
Package: python3-update-manager
Priority: standard
Section: python
Installed-Size: 221
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: update-manager
Version: 1:0.174.4
Replaces: update-manager-core (<< 1:0.163)
Depends: python3 (>= 3.2.3-3~), python3-apt (>= 0.8.5~), python3-distupgrade, lsb-release
Breaks: update-manager-core (<< 1:0.163)
Filename: pool/main/u/update-manager/python3-update-manager_0.174.4_all.deb
Size: 30808
MD5sum: 3a7d7c123b5788ce51a444dafde4d6ca
SHA1: 798ffd750f2b156dbf6a731b5c2295b4a7efe481
SHA256: 7d303c22c9058bb217c2e838869c6355ddce1d92a1c0a77fbb24e8ff0ecaf593
Description-en: python 3.x module for update-manager
 Python module for update-manager (UpdateManager).
 .
 This package contains the python 3.x version of this module.
Description-md5: ecfb930b93b3c3391fc6ad445be08cee
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: standard, kubuntu-active, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master

Package: python3-update-manager
Priority: standard
Section: python
Installed-Size: 221
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Source: update-manager
Version: 1:0.174.3
Replaces: update-manager-core (<< 1:0.163)
Depends: python3 (>= 3.2.3-3~), python3-apt (>= 0.8.5~), python3-distupgrade, lsb-release
Breaks: update-manager-core (<< 1:0.163)
Filename: pool/main/u/update-manager/python3-update-manager_0.174.3_all.deb
Size: 30880
MD5sum: 2b13bca77551f44c4b865e480ecd4f3c
SHA1: af3f9fef599b70f38dea7d07939fad94c8cf9e3f
SHA256: dbcef58da590c6e49cd336beb2fcd258f2d373470c35482ee45ee0aa2c2dec7f
Description-en: python 3.x module for update-manager
 Python module for update-manager (UpdateManager).
 .
 This package contains the python 3.x version of this module.
Description-md5: ecfb930b93b3c3391fc6ad445be08cee
Bugs: https://bugs.launchpad.net/ubuntu/+filebug
Origin: Ubuntu
Supported: 18m
Task: standard, kubuntu-active, mythbuntu-frontend, mythbuntu-desktop, mythbuntu-backend-slave, mythbuntu-backend-master, mythbuntu-backend-master


```

---

### Post by Bashing-om on 2013-06-03
-lover, OK, moving along, we are looking now at python3-distupgrade, says it is installed but not configured(that "iu" notation);
what results when we try and get it "configured" ?
```
sudo dpkg --configure python3-distupgrade
```[INDENT]
just one small step in one small chain

[/INDENT]

---

### Post by thekoalover on 2013-06-03
Dude If We Just Find A Sulotion To lsb-release it'll fix all....its the one that ruining it all cuz its not right and all has dependancies...
```
thekoalover@Batman:~$ sudo dpkg --configure python3-distupgrade
[sudo] password for thekoalover: 
dpkg: dependency problems prevent configuration of python3-distupgrade:
 python3-distupgrade depends on python3-update-manager; however:
  Package python3-update-manager is not configured yet.
 python3-distupgrade depends on lsb-release; however:
  Package lsb-release is not configured yet.

dpkg: error processing python3-distupgrade (--configure):
 dependency problems - leaving unconfigured
Errors were encountered while processing:
 python3-distupgrade

```

---

### Post by Bashing-om on 2013-06-03
--lover,
Unless I have lost track of the chain, we are working to get lsb-release resolved... that is the intent // and we go around and around until all the base dependencies are dealt with, one chain at a time. Now these dependencies with in the chains are intertwined and the output of "dpkg -C"  is directive on what we are working toward.
To that end -> python3-update-manager ;
```
dpkg -l python3-update-manager
``` To get an idea for what to do, to resolve that dependency issue.

As advised this is a tedious and frustrating experience, not to be entered into lightly.
If one is willing to take the risk can always take alternate advise and wholesale uninstall/reinstall, But, if upon the rebuild
FireFox does not get installed properly.... up a creek and the broken paddle; here is "wget" and on us to find the files on the net where ever and hope that we can find the correct versions// I much prefer the package manager manage all this.

Then if one gets really frustrated and/or out of time //back up data and (re-)install ! 

The process is not real bad if one is at the "broke" terminal and following the chains on that terminal in a timely manner.
The communications lag here is what seems to make the process laborious. and going round and around and around trying to get to the bottom of dependencies.... aptly termed "DEPENDENCY HELL"[INDENT=2]
that is where we are at

[/INDENT]

---

### Post by thekoalover on 2013-06-03
@Bashing-om so i did some snooping in the "status" file on our rotten apple "lsb-release"
and this is what it sayd,any ideas? "not from terminal"
```
 Package: lsb-release
Status: install ok half-configured
Priority: extra
Section: misc
Installed-Size: 111
Maintainer: Ubuntu Developers <ubuntu-devel-discuss@lists.ubuntu.com>
Architecture: all
Multi-Arch: foreign
Source: lsb
Version: 4.0-0ubuntu26.1
Config-Version: 4.0-0ubuntu26
Depends: python3 (>= 3.2.3-3~)
Recommends: apt
Suggests: lsb
Description: Linux Standard Base version reporting utility
 The Linux Standard Base (http://www.linuxbase.org/) is a standard
 core system that third-party applications written for Linux can
 depend upon.
 .
 The lsb-release command is a simple tool to help identify the Linux
 distribution being used and its compliance with the Linux Standard Base.
 LSB conformance will not be reported unless the required metapackages are
 installed.
 .
 While it is intended for use by LSB packages, this command may also
 be useful for programmatically distinguishing between a pure Debian
 installation and derived distributions.
Homepage: http://www.linux-foundation.org/en/LSB
Original-Maintainer: Chris Lawrence <lawrencc@debian.org> 
```

As for the code you posted  ```
 thekoalover@Batman:~$ sudo dpkg -l python3-update-maneger
[sudo] password for thekoalover: 
dpkg-query: no packages found matching python3-update-maneger 
```

---

### Post by Bashing-om on 2013-06-03
--lover, sheesshh, I am making more than my share of typing errors ..once again (and I did double checked my last. shhessh)

As to what I think: We already know the lsb-release is installed and has configuration problems (half configured); continue to work on it. I am pleased you are taking some initiative and delving deeper into the operating system.
 
My typo: change the"maneger" in update-maneger" to manager -e to a- ;;; i'll fix it in my prior post.

Your delayed response caused me concern that I might have caused offense in some means; I only mean to help in any way I can.

[INDENT]I ramble on a lot, but I try to be effective[/INDENT]

---

### Post by Bashing-om on 2013-06-04
--lover;

I am done for the night.. I have a busy day outside tomorrow, but I will catch up with you as I can.
[INDENT=2]
see ya
 [/INDENT]

---

### Post by Bashing-om on 2013-06-04
--lover; checking back in,,,

I am also still considering if there may be an advantage if those "status" files were removed. Will do some research in that respect, get caught up on some other things -> and I will be back.
 regards

---

### Post by thekoalover on 2013-06-04
@Bashing-om first of all man thank you for standing by me helping me with this endless circle :P
i really appreciate it,maan!
```
 thekoalover@Batman:~$ sudo dpkg -l python3-update-manager
[sudo] password for thekoalover: 
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
iU  python3-update 1:0.174.4    all          python 3.x module for update-mana

 
```

---

### Post by Bashing-om on 2013-06-04
--lover, as we continue to go round and round trying to get to the bottom ->
I did the  "dpkg -l show python3-update-manager" points to the next dependency -> "python3-apt (maybe again ?) anyway do on your system:
```
dpkg -l python3-apt
```
to get an idea where we stand and where to look else;
Hopeful that that is the end of this chain and python3-apt will configure !(or install)[INDENT]
work'n to study 'bout the "status" file ..in my craw for some reason.[/INDENT]

---

### Post by matt_symes on 2013-06-04
Hi

> **thekoalover said:**
> matt_symes;
so this is by order 
```
 thekoalover@Batman:~$ stat /var/lib/dpkg/info/lsb-release.postinst
  File: `/var/lib/dpkg/info/lsb-release.postinst'
  Size: 871           Blocks: 8          IO Block: 4096   regular file
Device: 801h/2049d    Inode: 20713729    Links: 1
Access: (0755/-rwxr-xr-x)  Uid: (    0/    root)   Gid: (    0/    root)
Access: 2013-05-30 01:13:07.541153986 +0200
Modify: 2012-10-24 02:34:42.000000000 +0200
Change: 2013-03-05 03:42:49.647701053 +0200
 Birth: -

 
```

second:  ```
 thekoalover@Batman:~$ ls -li /var/lib/dpkg/info/lsb-release.postinst
20713729 -rwxr-xr-x 1 root root 871 Oct 24  2012 /var/lib/dpkg/info/lsb-release.postinst

 
```

Third: ```
 thekoalover@Batman:~$ file /var/lib/dpkg/info/lsb-release.postinst
/var/lib/dpkg/info/lsb-release.postinst: ERROR: cannot read `/var/lib/dpkg/info/lsb-release.postinst' (Input/output error)

 
```

Fourth : ```
 thekoalover@Batman:~$ df -h | grep /$
/dev/sda1       457G  214G  220G  50% /

 
```

And No I Haven't Tried Running fsck on the partition

I hope you don't find if i step in again.

Fisrt try running fsck from a LiveCD/USB and forcing a check.

Booting into a LiveCD/USB, open a terminal and type

```
sudo fsck -f -y /dev/sda1
```

When it's finished, reboot into your hard drive installation and run...

```
sudo apt-get install -f
```

If that does not work then try deleting the file

```
sudo rm -f /var/lib/dpkg/info/lsb-release.postinst
```

Then reinstall it as you did before.

```
sudo apt-get install -f lsb-release
```

or 

```
sudo dpkg -i --force-remove-reinstreq lsb-release_4.0-0ubuntu26.1
```

If that does not work, what does this return ?

```
echo "" | sudo tee /var/lib/dpkg/info/lsb-release.postinst
```

If you cannot delete the file, you can try to delete it using its inode and debugfs but let's see how the above options pan out first.

Kind regards

---

### Post by Bashing-om on 2013-06-04
@ [COLOR=#000000]matt_symes, I appreciate your "stepping in" //glad you continue to watch....


Presently I have a concern that there are two versions of "lsb-release" installed and I am unsure how to differentiate them. I have the thought that running "dpkg -l grep lsb-release" will show if 2 versions are installed. Try and remove the older version ... and at that time try your install procedure ....(???)
[/COLOR][INDENT=2][COLOR=#000000]
I have been look'n and try'n to think this through

[/COLOR][/INDENT]

---

### Post by matt_symes on 2013-06-04
Hi basming-om,

> **Bashing-om said:**
> @ [COLOR=#000000]matt_symes, I appreciate your "stepping in" //glad you continue to watch....

Presently I have a concern that there are two versions of "lsb-release" installed and I am unsure how to differentiate them. I have the thought that running "dpkg -l grep lsb-release" will show if 2 versions are installed. Try and remove the older version ... and at that time try your install procedure ....(???)
[/COLOR][INDENT=2][COLOR=#000000]
I have been look'n and try'n to think this throug
[/COLOR][/INDENT]


I hope you're well. To be honest, this is the first time i have spent  any time on the forums for a week or so. Real life has been calling me [IMG]http://ubuntuforums.org/images/smilies/icon_smile.gif[/IMG]

It is worth looking ast what dpkg thinks is installed for the package lsb-release.

```
[COLOR=#000000]dpkg -l | grep lsb-release[/COLOR]
```

I have to say that i could only see one lsb-package installed though.

The problem is that postinst file for the package lsb-release.

It looks to me like the directory entry has been created and the inode allocated but it is pointing to rubbish, hence the input/output error.

fsck needs to be run on the partition sda1 from a LiveCD/USB.

If that and deleing the file using 'rm' does not fix it then freeing/clearing/rm'ing the inode using debugsfs may be the way forward.

All the other packages are dependent upon the package being installed correctly, so fixing that should allow the other packages to be fixed.

Kind regards

---

### Post by thekoalover on 2013-06-05
@Matt_symes Matt Man You're A Genius! 
Your Command Code Worked! 
```
 thekoalover@Batman:~$ sudo apt-get install -f lsb-release
Reading package lists... Done
Building dependency tree       
Reading state information... Done
lsb-release is already the newest version.
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 194 not upgraded.
17 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Do you want to continue [Y/n]? y
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Setting up lsb-release (4.0-0ubuntu26.1) ...
No apport report written because MaxReports is reached already
                                                              Setting up python3-apport (2.6.1-0ubuntu10) ...
Setting up apport (2.6.1-0ubuntu10) ...
Setting up apport-gtk (2.6.1-0ubuntu10) ...
Setting up firefox (19.0+build1-0ubuntu0.12.10.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up xul-ext-unity (2.4.1-0ubuntu1.2) ...
Please restart all running instances of firefox, or you will experience problems.
Setting up firefox-globalmenu (19.0+build1-0ubuntu0.12.10.2) ...
Setting up firefox-gnome-support (19.0+build1-0ubuntu0.12.10.2) ...
Setting up python-apport (2.6.1-0ubuntu10) ...
Setting up xdiagnose (3.2.2) ...
Setting up python3-distupgrade (1:0.190.5) ...
Setting up python3-update-manager (1:0.174.4) ...
Setting up ubuntu-release-upgrader-core (1:0.190.5) ...
Setting up update-manager-core (1:0.174.4) ...
Setting up ubuntu-release-upgrader-gtk (1:0.190.5) ...
Setting up update-manager (1:0.174.4) ...
Errors were encountered while processing:
 ubuntu-drivers-common

 
```
All Are Configured And Working Except Ubuntu-drivers-common Tried the same command line on it,tried force remove it didnt work,even configuration didnt.... @Bashing-om @Matt-symes Any Thoughts? 
Again Thank You Both So Very Much!!

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]thekoalover;  

Matt does indeed have a deep comprehension of what is happening "under the hood" ! Deeply relieved that the situation is this close to being resolved. Thanks Matt !

ubuntu-drivers-common :
See how fares this:
[/COLOR]```
sudo apt-get install --reinstall ubuntu-drivers-common[COLOR=#000000]
[/COLOR]
```[COLOR=#000000]
[/COLOR][INDENT=2][COLOR=#000000]
ain't nuth'n but a thing

[/COLOR][/INDENT]

---

### Post by thekoalover on 2013-06-05
@Bashing-om Nope :P 
```
 thekoalover@Batman:~$ sudo apt-get install --reinstall ubuntu-drivers-common
[sudo] password for thekoalover: 
Sorry, try again.
[sudo] password for thekoalover: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 1 reinstalled, 0 to remove and 236 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
E: Internal Error, No file name for ubuntu-drivers-common:i386

 
```

---

### Post by Bashing-om on 2013-06-05
[COLOR=#000000]thekoalover'

That error generally is a result of a package not completely installed in the upgrade process;
Try:

[/COLOR]```

sudo apt-get autoremove
sudo apt-get --fix-broken install
sudo dpkg --configure --pending
sudo apt-get update
sudo apt-get upgrade
``` before we take drastic measures.[INDENT=2]
my fingers are crossed

[/INDENT]

---

### Post by thekoalover on 2013-06-06
@Bashing-om No Again,It Seems There's No Files For It At All As Terminal Says...Im gonna keep trying different commands on it...hit me up if you got something.
```
 thekoalover@Batman:~$ sudo apt-get autoremove
[sudo] password for thekoalover: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
0 upgraded, 0 newly installed, 6 to remove and 236 not upgraded.
1 not fully installed or removed.
After this operation, 84.7 MB disk space will be freed.
Do you want to continue [Y/n]? y
dpkg: warning: files list file for package 'python-gst0.10' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'unity': Input/output error
E: Sub-process /usr/bin/dpkg returned an error code (2)
thekoalover@Batman:~$ sudo apt-get --fix-broken install
E: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem. 
thekoalover@Batman:~$ sudo dpkg --configure -a
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntu-drivers-common
thekoalover@Batman:~$ sudo dpkg --configure --pending
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntu-drivers-common
thekoalover@Batman:~$ sudo apt-get --fix-broken install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 236 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntu-drivers-common
E: Sub-process /usr/bin/dpkg returned an error code (1)

 
```

---

### Post by Bashing-om on 2013-06-06
[COLOR=#000000]thekoalover;
Somewhat disappointed, but not real surprised.... I am burned out for the eve, will sleep on this and get a fresh start in my AM.

I will let ya know ![/COLOR][INDENT=3][COLOR=#000000]
regards

[/COLOR][/INDENT]

---

### Post by thekoalover on 2013-06-06
Adios Man,So Close :P

---

### Post by Irihapeti on 2013-06-06
I found this: [http://www.piprime.fr/1480/manually-remove-broken-package-debian-ubuntu/](http://www.piprime.fr/1480/manually-remove-broken-package-debian-ubuntu/) which might be helpful.

It, or something very similar, got me out of difficulty when I first started on Ubuntu and got stuck with a half-installed package. Once I'd removed it, I could install it again properly.

But wait until one of your helpers has had a look at it first. It could do real damage if it was the wrong thing to do.

---

### Post by matt_symes on 2013-06-06
Hi

That's quite a messed up package system you have there.

You have an input/output error on the Unity file list file as well.

Let's look at this package first though.

```
sudo dpkg -i --force-remove-reinstreq ubuntu-drivers-common
```

after that

```
sudo dpkg --configure -a
```

Keep forcing the reinstall on the broken packages until you can go no further.

After that

```
sudo apt-get -f install
```

I expect the last command to fail on the unity input/output error.

Kind regards

---

### Post by thekoalover on 2013-06-06
@irihapeti Thank You Very Much I'll Try The Command..
@matt_symes it was turned off for a w2hile now after trying your command lines no unity nor the python-gst-.10 or the libgnome-keyring-common error shows...
But,,
```
thekoalover@Batman:~$ sudo dpkg -i --force-remove-reinstreq ubuntu-drivers-common
dpkg: error processing ubuntu-drivers-common (--install):
 cannot access archive: No such file or directory
Errors were encountered while processing:
 ubuntu-drivers-common
thekoalover@Batman:~$ sudo dpkg --configure -a
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
Errors were encountered while processing:
 ubuntu-drivers-common
thekoalover@Batman:~$ sudo apt-get -f install
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  linux-headers-3.5.0-17 linux-headers-3.5.0-17-generic ttf-droid ttf-umefont
  ttf-unfonts-core wine-gecko1.4
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 236 not upgraded.
1 not fully installed or removed.
After this operation, 0 B of additional disk space will be used.
Setting up ubuntu-drivers-common (1:0.2.71.1) ...
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/sl-modem.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/arm-gles.py'
[Errno 2] No such file or directory: '/usr/share/ubuntu-drivers-common/detect/open-vm-dkms.py'
dpkg: error processing ubuntu-drivers-common (--configure):
 subprocess installed post-installation script returned error exit status 1
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 ubuntu-drivers-common
E: Sub-process /usr/bin/dpkg returned an error code (1)
  
```

---

### Post by thekoalover on 2013-06-06
@irihapet didnt work, the desktop and another package depands on it... @matt_symes
```
thekoalover@Batman:~$ sudo dpkg --remove --force-remove-reinstreq ubuntu-drivers-common
dpkg: dependency problems prevent removal of ubuntu-drivers-common:
 software-properties-gtk depends on ubuntu-drivers-common (>= 1:0.2.67).
 ubuntu-desktop depends on ubuntu-drivers-common.

dpkg: error processing ubuntu-drivers-common (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 ubuntu-drivers-common

```

---

### Post by Irihapeti on 2013-06-06
What if you try a variation on that: 
```
sudo dpkg --install --force-remove-reinstreq ubuntu-drivers-common
```

---

### Post by matt_symes on 2013-06-07
Hi

> thekoalover@Batman:~$ sudo dpkg -i --force-remove-reinstreq ubuntu-drivers-common 
dpkg: error processing ubuntu-drivers-common (--install):  cannot access archive: No such file or directory 
Errors were encountered while processing:  ubuntu-drivers-common thekoalover@Batman:~$ 

This is not good. You have over 200 packages that need to be upgraded and each of them may have problems as well.

Having a powercut while updating a system can hose it pretty badly. This goes for other operating systems as well.

You may find it quicker and easier to backup your data and reinstall.

If you do want to try and continue fixing it the we will need to know if your system is 32 or 64 bit.

```
uname -a
```

I would then consider *wget* ing the deb file from the internet anf installing it manually.

The other option is to try sudo dpkg -i --force-remove-reinstreq ubuntu-drivers-common using the full path to ubuntu-drivers-common.

Kind regards

---

### Post by thekoalover on 2013-06-07
@matt_symes 
```
thekoalover@Batman:~$ uname -a
Linux Batman 3.5.0-25-generic #39-Ubuntu SMP Mon Feb 25 19:02:34 UTC 2013 i686 i686 i686 GNU/Linux

```

How Can I wget A Deb??

---

### Post by matt_symes on 2013-06-07
Hi

I take it you don't have it cached then. So to download it using wget...

```
cd && wget http://launchpadlibrarian.net/121724534/ubuntu-drivers-common_0.2.71.1_i386.deb && sudo dpkg -i ubuntu-drivers-common_0.2.71.1_i386.deb
```

Then continue as before.

Kind regards

---

### Post by thekoalover on 2013-06-07
@matt_symes no man, python-gst0.10 and libgnome and unity stepped again!!
```
 thekoalover@Batman:~$ cd && wget http://launchpadlibrarian.net/121724534/ubuntu-drivers-common_0.2.71.1_i386.deb && sudo dpkg -i ubuntu-drivers-common_0.2.71.1_i386.deb
--2013-06-07 17:15:56--  http://launchpadlibrarian.net/121724534/ubuntu-drivers-common_0.2.71.1_i386.deb
Resolving launchpadlibrarian.net (launchpadlibrarian.net)... 91.189.89.229, 91.189.89.228
Connecting to launchpadlibrarian.net (launchpadlibrarian.net)|91.189.89.229|:80... connected.
HTTP request sent, awaiting response... 200 OK
Length: 34268 (33K) [application/x-debian-package]
Saving to: `ubuntu-drivers-common_0.2.71.1_i386.deb'

100%[======================================>] 34,268       134K/s   in 0.2s    

2013-06-07 17:15:58 (134 KB/s) - `ubuntu-drivers-common_0.2.71.1_i386.deb' saved [34268/34268]

[sudo] password for thekoalover: 
Sorry, try again.
[sudo] password for thekoalover: 
Selecting previously unselected package ubuntu-drivers-common.
dpkg: warning: files list file for package 'python-gst0.10' missing; assuming package has no files currently installed
dpkg: warning: files list file for package 'libgnome-keyring-common' missing; assuming package has no files currently installed
dpkg: unrecoverable fatal error, aborting:
 reading files list for package 'unity': Input/output error

 
```
Peace Ya Man!

---

### Post by thekoalover on 2013-06-07
bump

---

### Post by matt_symes on 2013-06-07
Hi

> reading files list for package 'unity': Input/output error

I was wondering when that would come back to bite us. That input/ouput error on a different file (unity).

Let's look where the file is and then we can delete it as we did the other one and then try to install ubuntu-drivers-common again.

Please post the output of

```
ls -l /var/lib/dpkg/info/*unity*.list
```

Also let's have a look at the other files in that directory to see if they produce input/output errors.

Please post the output of (*if there is any* * we are hoping there isn't - apart from the unity file we know about*). This command will take a moment to complete.

```
cat /var/lib/dpkg/info/* 1> /dev/null
```

Kind regards

---

### Post by Bashing-om on 2013-06-07
I am back,  - others things do preclude on occasion -  and most happy that Matt is taking the lead on this. Awaiting compliance with Matt's last.
[INDENT]
still learning even after all these years

[/INDENT]

---

### Post by thekoalover on 2013-06-08
@matt_symes First Input.. 
```
 thekoalover@Batman:~$ ls -l /var/lib/dpkg/info/*unity*.list
-rw-r--r-- 1 root root  546 Mar  5 03:42 /var/lib/dpkg/info/gir1.2-unity-5.0:i386.list
-rw-r--r-- 1 root root  367 Mar  5 03:38 /var/lib/dpkg/info/libunity9:i386.list
-rw-r--r-- 1 root root  343 Mar  5 03:42 /var/lib/dpkg/info/libunity-core-6.0-5.list
-rw-r--r-- 1 root root  333 Oct 17  2012 /var/lib/dpkg/info/libunity-misc4.list
-rw-r--r-- 1 root root  388 Mar  5 03:38 /var/lib/dpkg/info/libunity-protocol-private0:i386.list
-rw-r--r-- 1 root root  410 Mar  5 03:39 /var/lib/dpkg/info/libunity-webapps0.list
-rw-r--r-- 1 root root 4469 Oct 17  2012 /var/lib/dpkg/info/unity-asset-pool.list
-rw-r--r-- 1 root root 7113 Mar  5 03:42 /var/lib/dpkg/info/unity-common.list
-rw-r--r-- 1 root root 1157 Mar  8 01:42 /var/lib/dpkg/info/unity-greeter.list
-rw-r--r-- 1 root root 1045 Mar  5 03:42 /var/lib/dpkg/info/unity-lens-applications.list
-rw-r--r-- 1 root root  705 Oct 17  2012 /var/lib/dpkg/info/unity-lens-files.list
-rw-r--r-- 1 root root 1135 Oct 17  2012 /var/lib/dpkg/info/unity-lens-gwibber.list
-rw-r--r-- 1 root root  546 Oct 17  2012 /var/lib/dpkg/info/unity-lens-music.list
-rw-r--r-- 1 root root 1103 Mar  8 01:42 /var/lib/dpkg/info/unity-lens-photos.list
-rw-r--r-- 1 root root  469 Oct 17  2012 /var/lib/dpkg/info/unity-lens-shopping.list
-rw-r--r-- 1 root root  770 Mar  5 03:42 /var/lib/dpkg/info/unity-lens-video.list
-rw-r--r-- 1 root root 1215 Mar  5 03:42 /var/lib/dpkg/info/unity.list
-rw-r--r-- 1 root root  920 Oct 17  2012 /var/lib/dpkg/info/unity-scope-gdocs.list
-rw-r--r-- 1 root root  477 Oct 17  2012 /var/lib/dpkg/info/unity-scope-musicstores.list
-rw-r--r-- 1 root root  718 Mar  8 01:42 /var/lib/dpkg/info/unity-scope-video-remote.list
-rw-r--r-- 1 root root  407 Mar  5 03:42 /var/lib/dpkg/info/unity-services.list
-rw-r--r-- 1 root root 2244 Mar  8 01:42 /var/lib/dpkg/info/unity-webapps-common.list
-rw-r--r-- 1 root root  867 Mar  5 03:39 /var/lib/dpkg/info/unity-webapps-service.list
-rw-r--r-- 1 root root 6818 Mar  5 03:43 /var/lib/dpkg/info/xul-ext-unity.list 
```

Second Input.. 
```
 thekoalover@Batman:~$ cat /var/lib/dpkg/info/* 1> /dev/null
cat: /var/lib/dpkg/info/apt-utils.list: Input/output error
cat: /var/lib/dpkg/info/gnome-screensaver.list: Input/output error
cat: /var/lib/dpkg/info/gstreamer0.10-gconf:i386.list: Input/output error
cat: /var/lib/dpkg/info/gstreamer0.10-plugins-base:i386.md5sums: Input/output error
cat: /var/lib/dpkg/info/isc-dhcp-client.postrm: Input/output error
cat: /var/lib/dpkg/info/libboost-date-time1.49.0.shlibs: Input/output error
cat: /var/lib/dpkg/info/libnux-3.0-0.postrm: Input/output error
cat: /var/lib/dpkg/info/libnux-3.0-common.md5sums: Input/output error
cat: /var/lib/dpkg/info/libqjson0:i386.postinst: Input/output error
cat: /var/lib/dpkg/info/libreoffice-math.postrm: Input/output error
cat: /var/lib/dpkg/info/libunity-core-6.0-5.postinst: Input/output error
cat: /var/lib/dpkg/info/libunity-webapps0.symbols: Input/output error
cat: /var/lib/dpkg/info/lsb-release.postrm: Input/output error
cat: /var/lib/dpkg/info/python-uno.prerm: Input/output error
cat: /var/lib/dpkg/info/unity-webapps-service.md5sums: Input/output error
cat: /var/lib/dpkg/info/vim-common.preinst: Input/output error

 
```
@Bashing-om Yeah Man Catching And Learning From That Matt Dev Wisdom :D

---

### Post by Bashing-om on 2013-06-08
@ [COLOR=#000000]thekoalover/[/COLOR][COLOR=#000000]matt_symes...
I am being pulled away, I will be back asap ...
[/COLOR][INDENT=2][COLOR=#000000]

[/COLOR][/INDENT]

---

### Post by matt_symes on 2013-06-08
Hi

> 
 thekoalover@Batman:~$ cat /var/lib/dpkg/info/* 1> /dev/null cat: /var/lib/dpkg/info/apt-utils.list: Input/output error cat: /var/lib/dpkg/info/gnome-screensaver.list: Input/output error cat: /var/lib/dpkg/info/gstreamer0.10-gconf:i386.list: Input/output error cat: /var/lib/dpkg/info/gstreamer0.10-plugins-base:i386.md5sums: Input/output error cat: /var/lib/dpkg/info/isc-dhcp-client.postrm: Input/output error cat: /var/lib/dpkg/info/libboost-date-time1.49.0.shlibs: Input/output error cat: /var/lib/dpkg/info/libnux-3.0-0.postrm: Input/output error cat: /var/lib/dpkg/info/libnux-3.0-common.md5sums: Input/output error cat: /var/lib/dpkg/info/libqjson0:i386.postinst: Input/output error cat: /var/lib/dpkg/info/libreoffice-math.postrm: Input/output error cat: /var/lib/dpkg/info/libunity-core-6.0-5.postinst: Input/output error cat: /var/lib/dpkg/info/libunity-webapps0.symbols: Input/output error cat: /var/lib/dpkg/info/lsb-release.postrm: Input/output error cat: /var/lib/dpkg/info/python-uno.prerm: Input/output error cat: /var/lib/dpkg/info/unity-webapps-service.md5sums: Input/output error cat: /var/lib/dpkg/info/vim-common.preinst: Input/output error

My advice ? Backup your data and reinstall.

EDIT;

That above copy and paste when a bit wrong there but basically you have a whole world of pain with those files.

You have a whole bunch of input/output errors and that is only on the list files. You could well have it in other files as well.

Restore from a backup and if you don't have one then backup your data and reinstall.

Then make a backup.

I would not even consider trying to fix this :)

Kind regards

---

### Post by Bashing-om on 2013-06-08
never mind ...see Matt's last...

---

### Post by matt_symes on 2013-06-08
Hi

> **Bashing-om said:**
> never mind ...see Matt's last...

It may be fixable bashing-om and if you want to continue then please do :)

One technique would be to delete the files with input/output errors and trying to reinstall the packages with the problems

The thing that concerns is it may go on and on. It may just be quicker to restore from backup or backup and reinstall.

However if the OP wants to go on then please help him.

OP. run a SMART test on the drive just in case it's damaged, but i suspect the power failure just damaged the filing system and not the hardware itself.

Kind regards

---

### Post by Bashing-om on 2013-06-08
[COLOR=#000000]@ matt_symes & [/COLOR][COLOR=#000000]thekoalover ....

Well, I have no heart burn ..trying to fix the system... all know just from the little trial in this thread how tedious just working one chain to determine it's dependencies was, imagine that times 100 !

--[/COLOR][COLOR=#000000]thekoalover-- I have in mind a means to start this //but please back up your data anyway, just in case //
I have in mind to wipe out dpkg's current "info" state and regenerate a new data base, take the status from this new database as a foundation to build from/on. If we are to proceed with this - and believe me I expect to learn from this too - let's establish a reference point from the "broken" install in order to know what effects we accomplish in the rebuild process.
one of the references is a hard copy printout of:
```
dpkg -l ucf
```
and another baseline:
```
sudo dpkg -C
```

and we take off again ///very time consuming in a long process. There will then always remain the doubt that all the snakes have been stomped out !

The sure thing is (re-)install .![/COLOR]

---

### Post by thekoalover on 2013-06-09
@Bashing-om ```
[COLOR=#000000]thekoalover@Batman:~$ dpkg -l ucf
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  ucf            3.0025+nmu3  all          Update Configuration File: preser[/COLOR]
```

```
thekoalover@Batman:~$ sudo dpkg -C
[sudo] password for thekoalover: 
The following packages are only half configured, probably due to problems
configuring them the first time.  The configuration should be retried using
dpkg --configure <package> or the configure menu option in dselect:
 ubuntu-drivers-common Detect and install additional Ubuntu driver packages

The following packages are missing the list control file in the
database, they need to be reinstalled:
 libgnome-keyring-common GNOME keyring services library - data files
 python-gst0.10       generic media-playing framework (Python bindings)

The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 python-gst0.10       generic media-playing framework (Python bindings)

```
These Packages =_='

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]thekoalover' Well glory be !

Things look a lot brighter... 
OK, Lets clear out the old databases and rebuild.
[/COLOR]```
sudo fuser -vvv /var/lib/dpkg/lock[COLOR=#000000]
[/COLOR]sudo rm /var/lib/apt/lists/lock
sudo cp -arf /var/lib/dpkg /var/lib/dpkg.backup
sudo cp /var/lib/dpkg/status-old /var/lib/dpkg/status
sudo cp /var/lib/dpkg/available-old /var/lib/dpkg/available
sudo rm -rf /var/lib/dpkg/updates/*
sudo rm -rf /var/lib/apt/lists
sudo rm /var/cache/apt/*.bin
sudo mkdir /var/lib/apt/lists
sudo mkdir /var/lib/apt/lists/partial
LANG=C;sudo apt-get clean
LANG=C;sudo apt-get autoclean
LANG=C;sudo apt-get --purge autoremove
LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824
sudo dpkg --clear-avail
sudo dpkg --configure -a
LANG=C;sudo apt-get -f install
LANG=C;sudo apt-get --fix-missing install
LANG=C;sudo apt-get update -o APT::Cache-Limit=25165824 && sudo apt-get dist-upgrade

``` one line at a time and with feeling ![INDENT=2]And need I say --copy and paste -- this is no time for an error ... space, letter, function, line perfect !
good things can happen

[/INDENT]

---

### Post by Bashing-om on 2013-06-09
[COLOR=#000000]thekoalover;
I am done for the eve...will check on your status my next.
[/COLOR][INDENT=2][COLOR=#000000]
regards

[/COLOR][/INDENT]

---

### Post by thekoalover on 2013-06-11
Hi Everyone Sorry Didnt Respond These Couple Of Days,It's That Ubuntu Didnt Wanna Boot,And It Gives Me That System Files are Missing New Ones Every Time I Try As If Its Eating Itself.....So I Gave Up After Lots of Livecd boots And Attempts Of Lots Of Things.....So Here I Am With A Fresh,Clean 12.10 Ubuntu Copy,Thank God My Things Are Still In Place,Thank You All Who Worked With Me...
@Bashing-om @matt_symes Thanks Mates For Sticking With Me Till The Big Boom :P
I Hope What These Brilliant Men Posted In my Aid Helps Whoever Is Viewing This Threade Under The Same Prob..

---

### Post by Bashing-om on 2013-06-11
[COLOR=#000000]thekoalover; Good deal.

Ain't ubuntu wonderful ... with care and attention even fatalities can be overcome !... (re-)install is always a means of last resort, but it is sure and effective !

Please mark this thread as "solved" - even though had to resort to (re-)installation - It workie now; this aids others seeking a solution as well as keeping the forum tidy.
[/COLOR]Interim method:
> Go to the first post in your thread. Click on "Edit Post". Now click on the orange "Go Advanced" button. In the advanced editor change the prefix to "SOLVED". Now click on the orange "Save Changes" button.

[INDENT=2]
I trust things go well with you and your ubuntu[/INDENT]

---

### Post by thekoalover on 2013-06-11
Thanks To You All,Now i Have A Tiny Piece Of Info To Get A Start...Will Do,Mate

---

