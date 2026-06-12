---
title: "A problem occurred when checking for the updates."
date: 2014-04-11
forum: New to Ubuntu
---

### Post by Rednibia on 2014-04-11
Any ideas what to do to fix this? Thanks in advance.

---

### Post by slickymaster on 2014-04-11
Hi Rednibia, welcome to the forums.

Can you please provide the forums with some more information regarding what happened. Can you please open a terminal window an run the following commands:```
sudo apt-get update && sudo apt-get upgrade
```and post the results here using the code tags for the effect.

---

### Post by Rednibia on 2014-04-11
```
E: Malformed line 1 in source list /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list (dist parse)
E: The list of sources could not be read.
```

---

### Post by slickymaster on 2014-04-11
Please post the content of your _sources.list_ file, runnig the following command in a terminal window and post back the results:```
cat /etc/apt/sources.list
```

---

### Post by Rednibia on 2014-04-11
```
# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)]/ dists/precise/main/binary-i386/

# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)]/ dists/precise/restricted/binary-i386/
# deb cdrom:[Ubuntu 12.04.4 LTS _Precise Pangolin_ - Release amd64 (20140204)]/ precise main restricted


# See http://help.ubuntu.com/community/UpgradeNotes for how to upgrade to
# newer versions of the distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise main restricted


## Major bug fix updates produced after the final release of the
## distribution.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates main restricted


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team. Also, please note that software in universe WILL NOT receive any
## review or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates universe


## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu 
## team, and may not be under a free licence. Please satisfy yourself as to 
## your rights to use the software. Also, please note that software in 
## multiverse WILL NOT receive any review or updates from the Ubuntu
## security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise multiverse
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-updates multiverse


## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main restricted universe multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-backports main restricted universe multiverse


deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security main restricted
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security universe
deb http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security multiverse
deb-src http://mirror.cc.columbia.edu/pub/linux/ubuntu/archive/ precise-security multiverse


## Uncomment the following two lines to add software from Canonical's
## 'partner' repository.
## This software is not part of Ubuntu, but is offered by Canonical and the
## respective vendors as a service to Ubuntu users.
deb http://archive.canonical.com/ubuntu precise partner
deb-src http://archive.canonical.com/ubuntu precise partner


## This software is not part of Ubuntu, but is offered by third-party
## developers who want to ship their latest software.
deb http://extras.ubuntu.com/ubuntu precise main
deb-src http://extras.ubuntu.com/ubuntu precise main



```

---

### Post by Bashing-om on 2014-04-11
Rednibia; Hello,

Passing by,- slickymaster -  allow me to assist, the indication:
> 
 source list /etc/apt/sources.list.d/ 

says also we need to look a bit further.

 @ Rednibia; Post back the output of terminal commands:
```

ls -la /etc/apt/sources.list.d
cat /etc/apt/sources.list.d/*.list

```

And let's see where that leads to for the next step.

[INDENT][INDENT]my little bit to try and help
[/INDENT][/INDENT]

---

### Post by slickymaster on 2014-04-11
> **Bashing-om said:**
> Rednibia; Hello,

Passing by,- slickymaster -  allow me to assist, the indication:

says also we need to look a bit further.

 @ Rednibia; Post back the output of terminal commands:
```

ls -la /etc/apt/sources.list.d
cat /etc/apt/sources.list.d/*.list

```

And let's see where that leads to for the next step.
[INDENT][INDENT]my little bit to try and help
[/INDENT]
[/INDENT]


No problem, Bashing-om. Got caught with something else and didn't get to the thread on time. Besides an extra pair of eyes is always welcome.

But you're right in your observation and I was going to suggest the OP to run```
find /etc/apt  -name '*.list' -exec bash -c 'echo -e "\n$1\n"; cat -n "$1"' _ '{}' \;
```for a thorough search.

---

### Post by SeijiSensei on 2014-04-11
> **Rednibia said:**
> ```
E: Malformed line 1 in source list /etc/apt/sources.list.d/private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list (dist parse)
E: The list of sources could not be read.
```

If it were me, I'd remove that entry from sources.list.d/, then run update/upgrade as suggested.  

Alternatively you can post the contents of that file here (in [noparse]```
[/noparse] tags please), so we can see what line 1 of that file looks like.  It should consist of one or more additional "deb" or "deb-src" entries like these on my system for the libreoffice PPA:
[code]deb http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
# deb-src http://ppa.launchpad.net/libreoffice/ppa/ubuntu trusty main
```
Lines beginning with a hash mark like the second one above are ignored.

---

### Post by Rednibia on 2014-04-15
ls -la /etc/apt/sources.list.d
[COLOR=#000000][FONT=Ubuntu Mono]gives me...
```
[/FONT][/COLOR]total 36
drwxr-xr-x 2 root root 4096 Apr 11 09:51 .
drwxr-xr-x 6 root root 4096 Apr  3 11:03 ..
-rw-r--r-- 1 root root  176 Apr 11 09:57 google-chrome.list
-rw-r--r-- 1 root root  176 Apr 11 09:57 google-chrome.list.save
-rw-r--r-- 1 root root   41 Apr 11 09:57 heroku.list
-rw-r--r-- 1 root root   41 Apr 11 09:57 heroku.list.save
-rw-r--r-- 1 root root    0 Apr 11 09:56 plexmediaserver.list
-rw-r--r-- 1 root root   70 Apr 11 09:56 plexmediaserver.list.save
-rw-r--r-- 1 root root  162 Apr 11 09:57 private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list
-rw-r--r-- 1 root root  162 Apr 11 09:57 private-ppa.launchpad.net_commercial-ppa-uploaders_plexmediaserver_ubuntu.list.save
[COLOR=#000000][FONT=Ubuntu Mono]
```


[/FONT][/COLOR]cat /etc/apt/sources.list.d/*.list[COLOR=#000000][FONT=Ubuntu Mono]
```
[/FONT][/COLOR]### THIS FILE IS AUTOMATICALLY CONFIGURED #### You may comment out this entry, but any other modifications may be lost.
deb http://dl.google.com/linux/chrome/deb/ stable main
deb http://toolbelt.heroku.com/ubuntu ./
deb https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu precise #Added by software-center; credentials stored in /etc/apt/auth.conf
[COLOR=#000000][FONT=Ubuntu Mono]
```[/FONT][/COLOR]
[COLOR=#000000][FONT=Ubuntu Mono]

Sorry for the delay, I've been traveling the last few days.[/FONT][/COLOR]

---

### Post by Bashing-om on 2014-04-15
Rednibia & et all; sheesshh;

Getting a bit out of my depth here, but I do not see the error. However, when I try and access the server, I get:
> 
The server [https://private-ppa-launchpad.net:443](https://private-ppa-launchpad.net:443) requires a username and pass word 
<snip>
----------------
That leads to this ->
----------------
Authorization Required

This server could not verify that you are authorized to access the document requested. Either you supplied the wrong credentials (e.g., bad password), or your browser doesn't understand how to supply the credentials required.


Which from the info provided :
> 
deb [https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu](https://private-ppa.launchpad.net/commercial-ppa-uploaders/plexmediaserver/ubuntu) precise #Added by software-center; credentials stored in [color=blue]/etc/apt/auth.conf[/color]

leads me to inquire does the file 'auth.conf' exist, and if so can we access it, and if so what info does it contain and is the credential valid ?

Hey
[INDENT][INDENT]going where I have never been before
[/INDENT][/INDENT]

---

### Post by slickymaster on 2014-04-15
> **Bashing-om said:**
> Rednibia & et all; sheesshh;

Getting a bit out of my depth here, but I do not see the error. However, when I try and access the server, I get:


Which from the info provided :

leads me to inquire does the file 'auth.conf' exist, and if so can we access it, and if so what info does it contain and is the credential valid ?

Hey[INDENT][INDENT]going where I have never been before
[/INDENT]
[/INDENT]


Besides what Bashing-om pointed, there's also the fact that the second url in that file resolves into an encrypted connection with a page not found error.

---

### Post by Rednibia on 2014-04-16
Looks like this problem is solved, thanks a lot for all the help!

---

