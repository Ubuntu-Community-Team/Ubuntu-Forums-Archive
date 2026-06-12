---
title: "dpkg: unrecoverable fatal error, aborting:  files list file for package 'nautilus-sen"
date: 2013-03-29
forum: New to Ubuntu
---

### Post by celfletch on 2013-03-29
I am getting the error message: dpkg: unrecoverable fatal error, aborting:
 files list file for package 'nautilus-sendto-empathy' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2), when I try to upgrade, or download software.  Since I upgraded from 12.04 to 12.10, I have continually received system error messages on-screen when I log in, though this is after I go on Firefox, and it may be a Firefox error.  But I am unable to update any software ever since the upgrade.  I have fiddled about a bit, and unticked some items in the software system settings.  Now the error message I get is the one you see above.
Would it be better if I reinstalled my good old 12.04?  I am not very good with technology and need to be 'led'.
Thanks for your thoughts.

C.

---

### Post by schragge on 2013-03-29
The error message indicates that file */var/lib/dpkg/info/nautilus-sendto-empathy.list* is corrupt (missing final newline). [This]("http://packages.ubuntu.com/quantal/amd64/nautilus-sendto-empathy/filelist") is how the file should look like. Besides the files listed on the linked page, it also should contains folders they are in and all directories above those in the path, i.e. */usr/share/doc*, */usr/share*, */usr*, /*usr/lib*, */usr/lib/nautilus-sendto*, etc. Compare this with what in the file on your system.

---

### Post by celfletch on 2013-03-29
Thanks.  But just HOW do I do this please?

---

### Post by schragge on 2013-03-29
Open a terminal window (press **Ctrl**+**Alt**+**t**, or see [uhelp]community/UsingTheTerminal[/uhelp] for detailed instructions), and run the commands below, then post their output here:
```

dpkg -l nautilus-sendto-empathy
cat /var/lib/dpkg/info/nautilus-sendto-empathy.list

```

---

### Post by celfletch on 2013-03-29
dpkg -l nautilus-sendto-empathy
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nautilus-sendt 3.6.0.3-0ubu i386         GNOME multi-protocol chat and cal
******************************:~$ cat /var/log/dpkg/info/nautilus-sendto-empathy.list
cat: /var/log/dpkg/info/nautilus-sendto-empathy.list: No such file or directory
******************************dpkg -l nautilus-sendto-empathy
Desired=Unknown/Install/Remove/Purge/Hold
| Status=Not/Inst/Conf-files/Unpacked/halF-conf/Half-inst/trig-aWait/Trig-pend
|/ Err?=(none)/Reinst-required (Status,Err: uppercase=bad)
||/ Name           Version      Architecture Description
+++-==============-============-============-=================================
ii  nautilus-sendt 3.6.0.3-0ubu i386         GNOME multi-protocol chat and cal
******************************~$ cat /var/log/dpkg/info/nautilus-sendto-empathy.list

---

### Post by schragge on 2013-03-29
> **celfletch said:**
> 
```
~$ cat /var/log/dpkg/info/nautilus-sendto-empathy.list
cat: /var/log/dpkg/info/nautilus-sendto-empathy.list: No such file or directory
```

Oops. The package is listed as installed, but an important configuration file is missing. Please open a terminal, run
```

sudo dpkg -C

``` and post the output here.

When posting, please wrap the output of terminal commands in [noparse][[/noparse]code][noparse][[/noparse]/code] tags to make it more readable. The **#** button above the text input area in **Adv Reply** allows you to insert them.

---

### Post by celfletch on 2013-03-29
> **schragge said:**
> Oops. The package is listed as installed, but an important configuration file is missing. Please open a terminal, run
```

sudo dpkg -C

``` and post the output here.

When posting, please wrap the output of terminal commands in [noparse][[/noparse]code][noparse][[/noparse]/code] tags to make it more readable. The **#** button above the text input area in **Adv Reply** allows you to insert them.

[The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 adobeair             Adobe AIR 2
 medibuntu-keyring    GnuPG key of the Medibuntu repository]









[/HTML]

---

### Post by celfletch on 2013-03-29
```
The following packages are missing the md5sums control file in the
database, they need to be reinstalled:
 adobeair             Adobe AIR 2
 medibuntu-keyring    GnuPG key of the Medibuntu repository


```

---

### Post by celfletch on 2013-03-29
Just tried reinstalling AdobeAir with these results:

```
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following extra packages will be installed:
  libhal1
The following NEW packages will be installed
  libhal1
The following packages will be upgraded:
  adobeair
1 upgraded, 1 newly installed, 0 to remove and 338 not upgraded.
Need to get 0 B/16.2 MB of archives.
After this operation, 239 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
Selecting previously unselected package libhal1.
dpkg: unrecoverable fatal error, aborting:
 files list file for package 'nautilus-sendto-empathy' is missing final newline
E: Sub-process /usr/bin/dpkg returned an error code (2)

```

---

### Post by schragge on 2013-03-29
:oops: Oops, sorry. I made a typo, that's why the file couldn't be found. The right command is:
```
cat /var/[COLOR=red]lib[/COLOR]/dpkg/info/nautilus-sendto-empathy.list
```. Please post the output of it.

[size=-1]*Also editing my post above.*[/size]

---

### Post by celfletch on 2013-03-29
```
cat /var/lib/dpkg/info/nautilus-sendto-empathy.list
&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;
```

---

### Post by schragge on 2013-03-29
Ouch. Looks not good. Well, let's try to make the file from scratch. Run these commands:
```

wget http://packages.ubuntu.com/quantal/amd64/nautilus-sendto-empathy/filelist
awk -vRS='</?pre>' NR==2 filelist|sed '$s:.*:/usr/share/doc/nautilus-sendto-empathy:' >nautilus-sendto-empathy.list
sudo cp -fv nautilus-sendto-empathy.list /var/lib/dpkg/info/
sudo dpkg -P nautilus-sendto-empathy
sudo apt-get install nautilus-sendto-empathy

```

---

### Post by celfletch on 2013-03-30
This is what i got (but not sure how to manually configure anything - see end comment):```
   ********************************:~$ wget http://packages.ubuntu.com/quantal/amd64/nautilus-sendto-empathy/filelist 
 --2013-03-30 11:34:52--  http://packages.ubuntu.com/quantal/amd64/nautilus-sendto-empathy/filelist 
 Resolving packages.ubuntu.com (packages.ubuntu.com)... 91.189.94.203 
 Connecting to packages.ubuntu.com (packages.ubuntu.com)|91.189.94.203|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: unspecified [text/html] 
 Saving to: `filelist' 
  
     [ <=>                                   ] 4,948       --.-K/s   in 0s       
  
 2013-03-30 11:34:52 (42.9 MB/s) - `filelist' saved [4948] 
  
 ********************************:~$ awk -vRS='</?pre>' NR==2 filelist|sed '$s:.*:/usr/share/doc/nautilus-sendto-empathy:' >nautilus-sendto-empathy.list 
 ********************************:~$ sudo cp -fv nautilus-sendto-empathy.list /var/lib/dpkg/info/ 
 [sudo] password for celia:  
 `nautilus-sendto-empathy.list' -> `/var/lib/dpkg/info/nautilus-sendto-empathy.list' 
 ********************************:~$ sudo dpkg -P nautilus-sendto-empathy 
 dpkg: unrecoverable fatal error, aborting: 
  files list file for package `nautilus-sendto' contains empty filename 
 ********************************:~$ sudo apt-get install nautilus-sendto-empathyE: dpkg was interrupted, you must manually run 'sudo dpkg --configure -a' to correct the problem.  
 ********************************:~$ ^C 
 ********************************:~$ sudo dpkg --configure -a 


```

---

### Post by schragge on 2013-03-30
Could you please again post the output of
```
cat /var/lib/dpkg/info/nautilus-sendto-empathy.list
```
and also the output of
```
cat /var/lib/dpkg/info/nautilus-sendto-empathy.md5sums
```

I don't think *sudo dpkg --configure -a* would help here as this command doesn't change the contents of the .list file in question. But it won't hurt either.

Now, I think the approach I suggested was overengineered quite a bit. If the md5sums file is intact, the file list for the package could have been derived from it like this:
```

f=/var/lib/dpkg/info/nautilus-sendto-empathy
sudo sed "s:.* :/:w$f.list" $f.md5sums

```

---

### Post by celfletch on 2013-03-30
FIRST ONE:

```
uk:~$ cat /var/lib/dpkg/info/nautilus-sendto-empathy.list
/usr/lib/nautilus-sendto/plugins/libnstempathy.so
/usr/share/doc/nautilus-sendto-empathy/AUTHORS
/usr/share/doc/nautilus-sendto-empathy/NEWS.gz
/usr/share/doc/nautilus-sendto-empathy/README
/usr/share/doc/nautilus-sendto-empathy/TODO
/usr/share/doc/nautilus-sendto-empathy/changelog.Debian.gz
/usr/share/doc/nautilus-sendto-empathy/copyright
/usr/share/doc/nautilus-sendto-empathy


```

2ND ONE:

```
uk:~$ cat /var/lib/dpkg/info/nautilus-sendto-empathy.md5sums
&#65533;&#65533;m
    &#65533;&#65533;&#65533;g&#65533;=&#65533;&#65533;&#65533;&#65533;=&#65533;&#65533;&#65533;&#65533;-&#65533;f&#65533;&#65533;&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;4&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;$&#65533;&#65533;&#65533;p&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;op&#65533;l&#65533;
A&#65533;&#65533;*&#65533;&#65533;&#65533;,&#65533;&&#65533;80&#65533;&#65533;\&#65533;&#65533;&#65533;&#65533;&#65533;&#65533; &#65533;&#65533;&#65533;"&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;,\8&#65533;&&#65533;&#65533;&#65533;&#65533;&#65533;&#65533;"&#65533;&#65533;&#65533;&#65533;0&#65533;&#65533;&#65533;B&#65533;&#65533;-&#65533;H&#65533;=
```

---

### Post by schragge on 2013-03-30
Well, the .md5sums is also damaged. Let's download the package and re-install it by hand.
```

sudo rm -fv /var/lib/dpkg/info/nautilus-sendto-empathy.*
a=$(dpkg --print-architecture)
wget http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.6.0.3-0ubuntu1_$a.deb
sudo dpkg -i nautilus-*.deb

```

---

### Post by celfletch on 2013-03-30
Thank you for all your help!  Not sure if it worked. It seemed to, then came up with the same message.
This is what I get, after entering each line separately:

```
   ********************-uk:~$  
 ********************-uk:~$  
 ********************-uk:~$ sudo rm -fv /var/lib/dpkg/info/nautilus-sendto-empathy.* 
 [sudo] password for celia:  
 removed `/var/lib/dpkg/info/nautilus-sendto-empathy.list' 
 removed `/var/lib/dpkg/info/nautilus-sendto-empathy.md5sums' 
 ********************-uk:~$ a=$(dpkg --print-architecture) 
 ********************-uk:~$ wget http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.6.0.3-0ubuntu1_$a.deb 
 --2013-03-30 17:33:53--  http://archive.ubuntu.com/ubuntu/pool/main/e/empathy/nautilus-sendto-empathy_3.6.0.3-0ubuntu1_i386.deb 
 Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.92.200, 91.189.92.201, 91.189.92.202, ... 
 Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.92.200|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 13318 (13K) [application/x-debian-package] 
 Saving to: `nautilus-sendto-empathy_3.6.0.3-0ubuntu1_i386.deb' 
  
 100%[======================================>] 13,318      --.-K/s   in 0.001s   
  
 2013-03-30 17:33:53 (13.5 MB/s) - `nautilus-sendto-empathy_3.6.0.3-0ubuntu1_i386.deb' saved [13318/13318] 
  
 ********************-uk:~$ sudo dpkg -i nautilus-*.deb 
 Selecting previously unselected package nautilus-sendto-empathy. 
 dpkg: warning: files list file for package 'nautilus-sendto-empathy' missing; assuming package has no files currently installed 
 dpkg: unrecoverable fatal error, aborting: 
  files list file for package `nautilus-sendto' contains empty filename 


```

---

### Post by celfletch on 2013-03-30
I think I should reinstall 12.04, and leave 12.10 alone for now.  It has had error messages ever since the upgrade to 12.10. I installed 12.04 from disk and will use that again, but upgraded without disk to 12.10.

I thought the message re nautilus and empathy must refer to the empathy application, which I have installed.  I have tried to remove this, but it will not uninstall.  I have tried installing other apps and they won't install.  Before, on 12.04, I used to be able to update the software, with reminders when I logged on.  Now I never see that.

I really think that the only fix is a reinstall, and it won't be 12.10!!!

Thank you so very much for all your help.  I really appreciate it, but will reinstall 12.04 tomorrow - and leave 12.10 firmly alone!

C.:popcorn:

---

### Post by schragge on 2013-03-30
Looks like you've got more problematic packages at your hands than *nautilus-sendto-empathy* alone. This particular error is about *nautilus-sendto*. To check what other packages may need to be re-installed, please post the output of
```

file /var/lib/dpkg/info/*.list|grep -vw text

```

---

### Post by celfletch on 2013-03-30
```
   ********************uk:~$  
 ********************-uk:~$ file /var/lib/dpkg/info/*.list|grep -vw text/var/lib/dpkg/info/gnome-bluetooth.list:                                data 
 /var/lib/dpkg/info/libavcodec53:i386.list:                              empty 
 /var/lib/dpkg/info/libavformat53:i386.list:                             empty 
 /var/lib/dpkg/info/nautilus-sendto.list:                                data 
 ********************uk:~$  
  


```

---

### Post by schragge on 2013-03-30
Please, Celia, don't give up so easy. Just one last attempt. Empty files are no problem, so it looks like the only other package that got corrupted is *nautilus-sendto*. Let's re-install it, too.
```

sudo rm -fv /var/lib/dpkg/info/nautilus-sendto.*
wget http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus-sendto/nautilus-sendto_3.6.0-0ubuntu1_i386.deb
sudo dpkg -i nautilus-*.deb

```

If this doesn't help then go ahead and reinstall Ubuntu

---

### Post by celfletch on 2013-03-30
Hi. Thanks again.
These are the results:

```
   ********************uk:~$ sudo rm -fv /var/lib/dpkg/info/nautilus-sendto.* 
 [sudo] password for celia:  
 removed `/var/lib/dpkg/info/nautilus-sendto.list' 
 removed `/var/lib/dpkg/info/nautilus-sendto.md5sums' 
 ********************-uk:~$ wget http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus-sendto/nautilus-sendto_3.6.0-0ubuntu1_i386.deb 
 --2013-03-30 22:41:37--  http://archive.ubuntu.com/ubuntu/pool/main/n/nautilus-sendto/nautilus-sendto_3.6.0-0ubuntu1_i386.deb 
 Resolving archive.ubuntu.com (archive.ubuntu.com)... 91.189.92.202, 91.189.92.200, 91.189.92.201, ... 
 Connecting to archive.ubuntu.com (archive.ubuntu.com)|91.189.92.202|:80... connected. 
 HTTP request sent, awaiting response... 200 OK 
 Length: 62996 (62K) [application/x-debian-package] 
 Saving to: `nautilus-sendto_3.6.0-0ubuntu1_i386.deb' 
  
 100%[======================================>] 62,996      --.-K/s   in 0.06s    
  
 2013-03-30 22:41:37 (995 KB/s) - `nautilus-sendto_3.6.0-0ubuntu1_i386.deb' saved [62996/62996] 
  
 ********************uk:~$ sudo dpkg -i nautilus-*.deb 
 dpkg: warning: files list file for package 'nautilus-sendto' missing; assuming package has no files currently installed 
 dpkg: warning: files list file for package 'nautilus-sendto-empathy' missing; assuming package has no files currently installed 
 dpkg: unrecoverable fatal error, aborting: 
  files list file for package 'gnome-bluetooth' is missing final newline 


```

---

### Post by schragge on 2013-03-31
Well, I guess at this point reinstalling the whole system is going to be easier than hunting down all damaged packages one by one. Sorry for taking your time.

---

### Post by celfletch on 2013-03-31
No. It's ok.  Thank you for trying.  The odd thing is that the system still seems to work well, apart from an on-screen error message from time to time, and, of course, when I try to update software.  Will use my 12.04 disk and go back to that.

Would you say it's better to use discs for installing an os on ubuntu?  I upgraded without one to 12.10.  Maybe I should just buy a 12.10 disc.  Will see how it goes.

Thank you so much for all your time and effort.  Very, very much appreciated.

HAPPY EASTER!

Celia

---

