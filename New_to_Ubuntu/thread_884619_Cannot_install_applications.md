---
title: "Cannot install applications"
date: 2008-08-09
forum: New to Ubuntu
---

### Post by Aldtjaom on 2008-08-09
Whenever I go to enable/install an application a message appears saying 

"Application Name" cannot be installed on your computer (i386)

Other errors come up saying 

         
failed to fetch file http://www......etc[/url]
invalid Hash sum mismatch 

Also when I tried to install Wine, a message appeared saying something from Synaptic Package Manager was conflicting with it. Only problem I don't know what the file the is conflicting with it is.

I know this is a lot but please help me!

---

### Post by brian_p on 2008-08-09
> **Aldtjaom said:**
> Whenever I go to enable/install an application a message appears saying 

"Application Name" cannot be installed on your computer (i386)

Other errors come up saying 

         
failed to fetch file http://www......etc[/url]
invalid Hash sum mismatch 

Please give us the exact command you are using to install the application.

> Also when I tried to install Wine, a message appeared saying something from Synaptic Package Manager was conflicting with it. Only problem I don't know what the file the is conflicting with it is.


Please give us the exact error message.

---

### Post by sharks on 2008-08-09
go to system---administration---software sources and check whether the download is from main server.

---

### Post by billgoldberg on 2008-08-09
Also, post your sources.list file

```
sudo gedit /etc/apt/sources.list
```

What version of Ubuntu do you have installed?

---

### Post by Aldtjaom on 2008-08-09
This is what came up when I tried to enable NVidia binary X.Org driver ('new' driver) in add/remove applications 

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb](http://archive.ubuntu.com/ubuntu/pool/restricted/l/linux-restricted-modules-2.6.24/nvidia-glx-new_169.12+2.6.24.13-19.45_i386.deb)
  Hash Sum mismatch



This is what came up when I tried to enable Wine

Cannot install 'wine'

This application conflicts with other installed software. To install 'wine' the conflicting software must be removed first.

Switch to the 'synaptic' package manager to resolve this conflict.



This is what came up when ad/remove applications tried update its list

W: A error occurred during the signature verification. The repository is not updated and the previous index files will be used.GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>

W: GPG error: [http://archive.ubuntu.com](http://archive.ubuntu.com) hardy-security Release: The following signatures were invalid: BADSIG 40976EAF437D05B5 Ubuntu Archive Automatic Signing Key <ftpmaster@ubuntu.com>
W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy/Release](http://archive.ubuntu.com/ubuntu/dists/hardy/Release)  

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/binary-i386/Packages.bz2)  Sub-process bzip2 returned an error code (2)

W: Failed to fetch [http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2](http://archive.ubuntu.com/ubuntu/dists/hardy-updates/main/source/Sources.bz2)  Sub-process bzip2 returned an error code (2)

W: Some index files failed to download, they have been ignored, or old ones used instead.



And when I try to install other software (eg Warzone 2100) this is what comes up

Warzone 2100 cannot be installed on your computer type (i386)

Either the application requires special hardware features or the vendor decided to not support your computer type.

Any help on this wil lbe greatly appreciated.

---

### Post by Aldtjaom on 2008-08-09
> **billgoldberg said:**
> Also, post your sources.list file

```
sudo gedit /etc/apt/sources.list
```

What version of Ubuntu do you have installed?


I have Ubuntu Hardy 8.04

---

### Post by Aldtjaom on 2008-08-09
> **sharks said:**
> go to system---administration---software sources and check whether the download is from main server.

I checked this and downloads are from main server.

---

### Post by sharks on 2008-08-09
its a bug:
**[http://ubuntuforums.org/showthread.php?t=794957](http://ubuntuforums.org/showthread.php?t=794957)**

---

### Post by Aldtjaom on 2008-08-09
> **sharks said:**
> its a bug:
**[http://ubuntuforums.org/showthread.php?t=794957](http://ubuntuforums.org/showthread.php?t=794957)**

If its a bug, how do you fix it? I read through these other posts but there's nothing saying how to fix it.

---

### Post by brian_p on 2008-08-09
> **Aldtjaom said:**
> If its a bug, how do you fix it? I read through these other posts but there's nothing saying how to fix it.

I hope you followed and read the links in those posts before coming to that conclusion.

---

### Post by Aldtjaom on 2008-08-09
I did, but some of the links didn't work. Browser kept saying something about secure connection error, so I just assumed the page didn't exist anymore.

---

### Post by brian_p on 2008-08-09
> **Aldtjaom said:**
> I did, but some of the links didn't work. Browser kept saying something about server connection troubles, so I just assumed the page didn't exist anymore.

The pages do exist and may help you.

---

### Post by Aldtjaom on 2008-08-09
> **brian_p said:**
> The pages do exist and may help you.

But one problem, the pages never show in my browser, it keeps on displaying this instead.

Secure Connection Failed

      

      
      
      

      
        
        

          

An error occurred during a connection to bugs.launchpad.net.

SSL received a record with an incorrect Message Authentication Code.

(Error code: ssl_error_bad_mac_read)

        


        
        

The page you are trying to view can not be shown because the authenticity of the received data could not be verified.

    * Please contact the web site owners to inform them of this problem.

---

### Post by brian_p on 2008-08-09
> **Aldtjaom said:**
> But one problem, the pages never show in my browser, it keeps on displaying this instead.

Secure Connection Failed



A network problem? Browser problem?

The links are

[http://ubuntuforums.org/showthread.php?t=824738](http://ubuntuforums.org/showthread.php?t=824738)

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)

Only one is [https://.](https://.)

---

### Post by Aldtjaom on 2008-08-09
> **brian_p said:**
> A network problem? Browser problem?

The links are

[http://ubuntuforums.org/showthread.php?t=824738](http://ubuntuforums.org/showthread.php?t=824738)

[https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061](https://bugs.launchpad.net/ubuntu/+source/apt/+bug/24061)

Only one is [https://.](https://.)

Thanks, the links worked. Only thing is nothing in the link is working for me. I tried all the terminal commands but nothing seems to work. Whats more another error appears when I tried to download/install stuff from add/remove applications. The error says something about "Unable to obtain repertory indexes".

---

### Post by xzaverax on 2008-08-09
You might want to make sure that all other instances of synaptic are fully closed.  I had a few problems with that also but as long as you only have one instance running I think that will solve your problem.

---

### Post by tinker312 on 2008-08-09
What I would try is to open your terminal and gain root privileges.  Then type: 

[B]cp /etc/apt/sources.list /etc/apt/sources.list.backup 
gedit /etc/apt/sources.list [/B]

Now, delete everything that is in this file and paste in this sources list quoted below.  Finally close gedit and the sources lists and run 

**apt-get update **

If you get an error message post it here and we can try something else. And remember your original source list is backed up so you can revert to your old repositories if you feel the need. 

> 
#deb cdrom:[Ubuntu 8.04.1 _Hardy Heron_ - Release i386 (20080702.1)]/ hardy main restricted
# See [http://help.ubuntu.com/community/UpgradeNotes](http://help.ubuntu.com/community/UpgradeNotes) for how to upgrade to
# newer versions of the distribution.

deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates main restricted

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy universe
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates universe

## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy multiverse
deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse
deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-updates multiverse

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu/](http://us.archive.ubuntu.com/ubuntu/) hardy-backports main restricted universe multiverse

## Uncomment the following two lines to add software from Canonical's
## 'partner' repository. This software is not part of Ubuntu, but is
## offered by Canonical and the respective vendors as a service to Ubuntu
## users.
# deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner
# deb-src [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) hardy partner

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security main restricted
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security universe
deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) hardy-security multiverse


---

