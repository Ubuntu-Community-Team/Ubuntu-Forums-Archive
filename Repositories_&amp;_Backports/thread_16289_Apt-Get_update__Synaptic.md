---
title: "Apt-Get update / Synaptic"
date: 2005-02-20
forum: Repositories &amp; Backports
---

### Post by qa1433 on 2005-02-20
Hi all, 
Last night I upgraded from warty to hoary with apt-get update and upgrade. All went well and the system feels real responsive. However, I cannot get apt-get or synaptic to update. Just so you know I am presently listening to Pete Tong's BBC Radio One's Essential Selection broadcast. I am also using the browser to author this memo. So I have broadband connection.
~~~~~~~~~~~~~~~~~~~~~~~~~~
The CMI error I am getting is below: 
qa1433@ubuntu:~ $ sudo apt-get update
0%  Connecting to archive.ubuntu.com (82.211.81.138)   Connecting to security.ubuntu.com (82.211.81.138) 
Err  url [http://archive.ubuntu.com](http://archive.ubuntu.com) url hoary Release.gpg
  Could not connect to archive.ubuntu.com:80 (82.211.81.138), connection timed out
~~~~~~~~~~~~~~~~~~~~~~~~~~
Now if I try to upgrade this is the error I get below:
qa1433@ubuntu:~ $ sudo apt-get upgrade
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list  [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list http://archive.ubuntu.com[/url] hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
qa1433@ubuntu:~ $
~~~~~~~~~~~~~~~~~~~~~~~~~~
I tried apt-get -f install:
qa1433@ubuntu:~ $ sudo apt-get -f install
Reading Package Lists... Done
Building Dependency Tree... Done
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/main Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/restricted Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/universe Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_universe_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://archive.ubuntu.com](http://archive.ubuntu.com) hoary/multiverse Packages (/var/lib/apt/lists/archive.ubuntu.com_ubuntu_dists_hoary_multiverse_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) hoary-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) /hoary-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_hoary-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
qa1433@ubuntu:~ $
~~~~~~~~~~~~~~~~~~~~~~~~~~
I also ran dpkg --configure -a:
qa1433@ubuntu:~ $ sudo dpkg --configure -a
qa1433@ubuntu:~ $ 
~~~~~~~~~~~~~~~~~~~~~~~~~~
So here i am. What do I do next? Oh below is my source file:
#deb cdrom: Ubuntu 4.10 _Warty Warthog_ - Preview i386 Binary-1 (20041020)]/ unstable main restricted  
#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted  
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty main restricted  

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

#deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  
#deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) warty universe  

#deb [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted  
#deb-src [http://security.ubuntu.com/ubuntu/](http://security.ubuntu.com/ubuntu/) warty-security main restricted  

# This is the latest HOARYrealease. May cause problems.
#Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary main restricted

deb [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
deb-src [http://archive.ubuntu.com/ubuntu/](http://archive.ubuntu.com/ubuntu/) hoary universe
~~~~~~~~~~~~~~~~~~~~~~~~~~~~
Any help would be appriciated,
paul

---

### Post by WW on 2005-02-20
[http://www.ubuntuforums.org/showthread.php?t=16218](http://www.ubuntuforums.org/showthread.php?t=16218)

---

### Post by qa1433 on 2005-02-20
WW,
Thanks! Sorry for not knowing that tidbit of info.

I was so excited that this upgrade whent off with out a hitch that I did not check for maintance news.

Again thanks,
paul

---

### Post by WW on 2005-02-20
No need to be sorry.  The only announcement that I could find was in the ubuntu-devel mailing list.

---

