---
title: "Downloading without apt-get?"
date: 2006-03-22
forum: Repositories &amp; Backports
---

### Post by p221072 on 2006-03-22
I installed Ubuntu Breezy on my pc at home where I've got a slow dial-up internet connection.:( 
I would like to know if it's possible to download packages with my (win2k) laptop at work and install them later at home.
If it's so, where can I find the packs and all the libraries or dependancies needed?
Thank you for the help

---

### Post by markr on 2006-03-22
You can download them manually.  If you go to packages.ubuntu.com you can manually download the deb files there.  Each deb file will tell you what it depends on; sorry but it's a matter of manually checking the dependancies (and the dependancies of the dependancies) to ensure you have all the files.

You can then use dpkg to install them.

I have a similar problem, my ubuntu is not connected to the internet.  What I've done is install vmware and install ubuntu as a virtual machine under windows.  I can then use my windows connection to download all the updates (via synpatic) and then just copy all the debs to my ubuntu box later (I think instructions exist to create a local respository which you copy the debs into, and then you can point synaptic on your non-internet nachine to that repository) - search the forum for "local repository"

---

### Post by p221072 on 2006-03-22
Thank you very much
quick and accurate!

---

### Post by p221072 on 2006-03-24
I started downloading from web but it's very hard following all the dependencies of the dependencies of the dependencies...
so i installed vmware and the ubuntu5.10 virtual machine... and IT WORKS!
but big problem: though network and internet work, apt-get cannot connect to repos, i think because of the company's firewall
so it seems all useless :-(
any ideas?

---

### Post by markr on 2006-03-24
I believe that synaptic and apt-get use http, so in theory if you can connect to the internet (from within the vmware system), it should work.

Can you provide more details:

1. In Ubuntu (vmware) can you browse the internet?
2. What network settings are you using in vmware, I'm using the NAT option which should just use the same IP Address that your WinXP host system uses.
3. If you do a 'sudo apt-get update', what is the output.
4. Can you post your sources.lst

Mark.

---

### Post by p221072 on 2006-03-24
Thank you for your help, so:
1. I'm writing from Firefox on ubuntu5.10 in vmware under win2k, so browsing works. I had to set the proxy options;
2. I'm using th NAT option too;
3. with 'sudo apt-get update' connection goes in timeout, this is the output:
> ubuntu@ubuntu:~$ sudo apt-get update
Err [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security Release.gpg
  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Err [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates Release.gpg
  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Failed to fetch [http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg](http://us.archive.ubuntu.com/ubuntu/dists/breezy-updates/Release.gpg)  Could not connect to us.archive.ubuntu.com:80 (216.165.129.138), connection timed out
Failed to fetch [http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg](http://security.ubuntu.com/ubuntu/dists/breezy-security/Release.gpg)  Could not connect to security.ubuntu.com:80 (82.211.81.138), connection timed out
Reading package lists... Done
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/main Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_main_binary-i386_Packages) - stat (2 No such file or directory)W: Couldn't stat source package list [http://us.archive.ubuntu.com](http://us.archive.ubuntu.com) breezy-updates/restricted Packages (/var/lib/apt/lists/us.archive.ubuntu.com_ubuntu_dists_breezy-updates_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/main Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_main_binary-i386_Packages) - stat (2 No such file or directory)
W: Couldn't stat source package list [http://security.ubuntu.com](http://security.ubuntu.com) breezy-security/restricted Packages (/var/lib/apt/lists/security.ubuntu.com_ubuntu_dists_breezy-security_restricted_binary-i386_Packages) - stat (2 No such file or directory)
W: You may want to run apt-get update to correct these problems
E: Some index files failed to download, they have been ignored, or old ones used instead.

4. Here is my sources.lst ( the default one)
> deb cdrom:[Ubuntu 5.10 _Breezy Badger_ - Release i386 (20051012)]/ breezy main restricted


deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy main restricted

## Major bug fix updates produced after the final release of the
## distribution.
deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted
deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-updates main restricted

## Uncomment the following two lines to add software from the 'universe'
## repository.
## N.B. software from this repository is ENTIRELY UNSUPPORTED by the Ubuntu
## team, and may not be under a free licence. Please satisfy yourself as to
## your rights to use the software. Also, please note that software in
## universe WILL NOT receive any review or updates from the Ubuntu security
## team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy universe

## Uncomment the following two lines to add software from the 'backports'
## repository.
## N.B. software from this repository may not have been tested as
## extensively as that contained in the main release, although it includes
## newer versions of some applications which may provide useful features.
## Also, please note that software in backports WILL NOT receive any review
## or updates from the Ubuntu security team.
# deb [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse
# deb-src [http://us.archive.ubuntu.com/ubuntu](http://us.archive.ubuntu.com/ubuntu) breezy-backports main restricted universe multiverse

deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted
deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security main restricted

# deb [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe
# deb-src [http://security.ubuntu.com/ubuntu](http://security.ubuntu.com/ubuntu) breezy-security universe

5. I made a file apt.conf with the proxy settings, I post it  without the true data (login, passwd and proxy name) but are the same of Firefox settings. This is the file:
> 
Acquire
{
 
  http 
  {


	Proxy::[http://login:passwd@proxy..mycompany.root.it:8080/;](http://login:passwd@proxy..mycompany.root.it:8080/;)
  
  };

};


I'm sure the problem is in the proxy configuration but I'm not finding out the solution
thanx
Paolo

---

