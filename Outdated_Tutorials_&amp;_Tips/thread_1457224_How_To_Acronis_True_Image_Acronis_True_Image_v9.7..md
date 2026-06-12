---
title: "How To: Acronis True Image Acronis True Image v9.7.8206 Snapapi Ubuntu 9.10"
date: 2010-04-18
forum: Outdated Tutorials &amp; Tips
---

### Post by lightenup on 2010-04-18
Ive had success installing Acronis True Image on Ubuntu 8.04 - 9.10 32bit (64bit can be done but it involves installing some 32bit PAM modules). The main issue everyone will run into at one point or another is the fact that the Acronis SNAPAPI module will not compile and install. 

Acronis has provided a script for this however in some cases finding the latest source of the SNAPAPI code can prove difficult or you will find the latest version but it will be an RPM format. I will cover how to work around these issues. 

Lets get started. Install the Acronis True Image agent:

sudo ./AcronisTrueImageAgentLinuxEnterprise.i686

The above will fail at the part where the SNAPAPI modules are being compiled, no worries we will manually install them.

At this point we need to get a copy of the latest SNAPAPI modules that match our newer kernel on Ubuntu 9.10. Those who have got to this point soon realize that there is nothing out there but some .rpm files which obviously don't work well on Ubuntu. I found out that a RPM file is nothing more than some sort of compressed archive. The easiest way to extract these is with File Roller (Archive Manager).

Here is the most recent version of SNAPAPI I could find:

[http://kb.acronis.com/sites/default/files/content/2010/03/9317/snapapi26_modules-0.7.51-1.noarch.rpm](http://kb.acronis.com/sites/default/files/content/2010/03/9317/snapapi26_modules-0.7.51-1.noarch.rpm)

Open the file with Archvie Manager, dig down and pull out the file snapapi26-0.7.51-all.tar.gz .

Extract the snapapi archive:

$ tar xvfz snapapi26-0.7.51-all.tar.gz
dkms_main_tree/
dkms_source_tree/
dkms_source_tree/dkms.conf
dkms_source_tree/Makefile
dkms_source_tree/snapapi.h
dkms_source_tree/snapapi26.c
dkms_source_tree/snumbd.h
dkms_source_tree/snumbd26.c
dkms_source_tree/sn_huge_ptr.h

Now lets rename the dkms_source_tree folder and place it where it needs to be for the script to operate:

$ mv dkms_source_tree snapapi26-0.7.51
$ sudo mv snapapi26-0.7.51 /usr/src/
$ sudo chown -R root:src /usr/src/snapapi26-0.7.51/

With everything is in place we now need to download and make a change to the build script to reference the new version of snapapi. Head on over to the Acronis site and download the Ubuntu build script:

[http://kb.acronis.com/sites/default/files/content/2008/12/1813/ubuntu_build.tar](http://kb.acronis.com/sites/default/files/content/2008/12/1813/ubuntu_build.tar)

Extract ubuntu_build.tar:

$tar xvfz ubuntu_build.tar
$ vi ubuntu_build.sh

Edit the following line to match the version of snapapi we have placed in the /usr/src folder:

Change this line from:
snapapi_ver=0.7.45

To:
snapapi_ver=0.7.51

Save the file and exit. Now kick off the ubuntu_build.sh script:

$ sudo ./ubuntu_build.sh

If everything goes well you should get the following:

Modules were built successfully.
Running depmod...
Trying to load built module...
The installation is completed sucessfully.

Lastly we need to set a password on the root account b/c the management console needs to connect as root in order to function:

sudo passwd

Finally start up the Acronis services:

$ sudo /etc/init.d/acronis_agent start

I hope this helps some of you out there.

---

