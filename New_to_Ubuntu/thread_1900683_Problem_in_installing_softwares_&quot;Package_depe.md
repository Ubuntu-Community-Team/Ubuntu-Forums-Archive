---
title: "Problem in installing softwares &quot;Package dependencies cannot be resolved&quot;"
date: 2011-12-26
forum: New to Ubuntu
---

### Post by kevincmaker on 2011-12-26
Hello,
I am a new ubuntu user who recently switched on to ubuntu 11.10 from windows7 ..

Whenever I try to install any software (many except a few), via the Ubuntu software center, it gives an error message as follows : 
```
**Package dependencies cannot be resolved:**
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.

```

:( Can any one help in giving a solution to this problem?

Thanks in advance!

---

### Post by snowpine on 2011-12-26
You should never get this error, assuming 1) you are installing supported software from the Ubuntu repositories; and 2) you have not altered/modified your software sources.

Please give us the specific name of the application you are trying to install and the specific dependencies it's complaining about. If the Software Center isn't giving you enough detail then try installing from the Terminal:

```
sudo apt-get update
sudo apt-get install foo
```

Replace "foo" with the actual name of the software you are trying to install. :)

---

### Post by kevincmaker on 2011-12-26
Yes! I tried in the terminal way too! 

It gives an error message as follows:

> Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main Sources                              
  404  Not Found
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main amd64 Packages                       
  404  Not Found
.
.
.
.
Err [http://ppa.launchpad.net](http://ppa.launchpad.net) oneiric/main i386 Packages                        
  404  Not Found
.
.
.
.
W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages](http://ppa.launchpad.net/mozillateam/firefox-stable/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

The above errors are displayed when i try to update the packages.

When I try to install **vlc **media player by typing ```
sudo apt-get install vlc
```,
I get the following error message:
> Reading package lists... Done
Building dependency tree       
Reading state information... Done
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:

The following packages have unmet dependencies:
 vlc : Depends: vlc-nox (= 1.2.0~~git20111110+r996-0~r47~oneiric1) but it is not going to be installed
       Depends: libavcodec53 (>= 4:0.7-1) but it is not going to be installed or
                libavcodec-extra-53 (>= 4:0.7-1) but it is not going to be installed
       Depends: libegl1-mesa (>= 7.8.1) but it is not installable or
                libegl1-x11 but it is not installable
       Depends: libva-x11-1 (> 1.0.12~) but it is not installable
       Depends: libva1 (> 1.0.12~) but it is not installable
       Depends: libxcb-composite0 but it is not installable
       Depends: libxcb-randr0 (>= 1.1) but it is not installable
       Depends: libxcb-xv0 (>= 1.2) but it is not installable
       Recommends: vlc-plugin-notify (= 1.2.0~~git20111110+r996-0~r47~oneiric1) but it is not going to be installed
       Recommends: vlc-plugin-pulse (= 1.2.0~~git20111110+r996-0~r47~oneiric1) but it is not going to be installed
E: Unable to correct problems, you have held broken packages.
BTW, I'm using AMD Athlon 64 bit processor.

Any further suggestions? :confused:

---

### Post by snowpine on 2011-12-26
You have modified your software sources by adding unofficial 3rd party repositories for some reason you haven't explained to us. You're now stuck in what's called "dependency hell."

The obvious solution is to remove these unsupported software sources and install vlc from the official Ubuntu repositories.

Other solutions may require a little more effort...

---

### Post by lolpenguin on 2011-12-26
You have probably added sources with packages that conflict with the official repositories. Firstly, try this
```
sudo apt-get install -f
```
If that does not work, launch Software Sources (if you don't see it, run "software-properties-gtk", (enter password), click on the Other Software tab, uncheck everything, then run```
sudo apt-get update
``` and install whatever you need.

---

### Post by Arif_9804 on 2011-12-28
after type sudo apt-get update in tarminl, i found some eror...Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/main Sources     
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/restricted Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/universe Sources 
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/multiverse Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/main amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/restricted amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/universe amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/multiverse amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/main i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/restricted i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/universe i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric/multiverse i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/main Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/restricted Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/universe Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/multiverse Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/main amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/restricted amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/universe amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/multiverse amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/main i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/restricted i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/universe i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-updates/multiverse i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/main Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/restricted Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/universe Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/multiverse Sources
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/main amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/restricted amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/universe amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/multiverse amd64 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/main i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/restricted i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/universe i386 Packages
  404  Not Found
Err [http://bd.archive.ubuntu.com](http://bd.archive.ubuntu.com) oneiric-backports/multiverse i386 Packages
  404  Not Found
W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/main/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-updates/multiverse/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/source/Sources)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-amd64/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/main/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/restricted/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/universe/binary-i386/Packages)  404  Not Found

W: Failed to fetch [http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages](http://bd.archive.ubuntu.com/ubuntu/dists/oneiric-backports/multiverse/binary-i386/Packages)  404  Not Found

E: Some index files failed to download. They have been ignored, or old ones used instead.

and when i try to install skype or flash player then this error message ...
This error could be caused by required additional software packages which are missing or not installable. Furthermore there could be a conflict between software packages which are not allowed to be installed at the same time.
...now wt can i do..tell me plz..:(:(:(:(:(:(

---

### Post by oldos2er on 2011-12-28
Try changing to different servers (I'm assuming you have a working internet connection on the computer in question): [https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server](https://help.ubuntu.com/community/Repositories/Ubuntu#Download_Server)

---

### Post by lolpenguin on 2011-12-28
Go back to Software Sources and change entry "Download from" to Main server, not server for country and try [FONT="Courier New"]sudo apt-get update[/FONT] again.

---

### Post by kevincmaker on 2011-12-28
The problem is solved for me now.... I just reinstalled my system.

It seems that the package was not well saved in my system...

So, try burning the image file to a new CD and then install ubuntu 11.10 again... Hope it will solve ur problem....

---

