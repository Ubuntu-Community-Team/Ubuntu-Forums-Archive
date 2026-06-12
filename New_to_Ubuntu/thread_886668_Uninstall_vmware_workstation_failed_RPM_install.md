---
title: "Uninstall vmware workstation failed RPM install"
date: 2008-08-11
forum: New to Ubuntu
---

### Post by wtfbrb on 2008-08-11
I installed vmware workstation trial unsuccessfully, I thought I had removed it so I removed all the old installation files now I am trying to install vmware server via synaptic package manager, but to no avail.  I have removed every reference to vmware in the package manager but I believe some files are still staying around and blocking me from installing vmware server.  Here are a couple screen shots of the errors I am getting.  I have tried both adding the vm repo and using package manager and using the tar ball from the vmware website and followed the online guides to installing each respectively but I get errors.  The problem is related to the previous installation of vm workstation.  As I am a noob I don't know where to even look for the scraps workstation has left.


I am running 64 bit hardy.

---

### Post by ajgreeny on 2008-08-11
Is this because the kernel needed is 2.6.22 and hardy uses 2.6.24?  I have no knowledge of vmware but that does seem a possible reason to me.  Also, how did you install the rpm version in the first place?  Ubuntu used .deb packages not rpm, unless you use alien to perform the rpm conversion/installation.

---

### Post by Ryadt on 2008-08-11
You can try virtualbox which is a great alternative to vmware and it is in the repos.```
sudo apt-get install virtualbox-ose
```
or you can download and install the one on their website, which is better. Try this tutorial [http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox](http://ubuntuforums.org/showthread.php?t=770745&highlight=virtualbox)

---

### Post by Thelasko on 2008-08-11
> As I am a noob I don't know where to even look for the scraps workstation has left.
This is exactly why you shouldn't install RPM files in Ubuntu.  It makes a mess of your system.  Let this be a lesson learned, and an example of what not to do for other users.  (honestly, I don't intend to sound mean)

Lecture aside, the original RPM file you installed should have a list of files it installed, including the directories.  I don't know how to access it in Ubuntu, but I know it exists from my days of using SUSE. (if you provide a link to what you installed, perhaps someone else can find it)  If you can find that list, you should be able to hunt down your problem files and delete them.  Be careful you don't delete any important system files in the process.

It would be safer to leave the files on your machine and continue to use it as is, or reinstall Ubuntu.

---

### Post by Thelasko on 2008-08-11
Ok, I did some more work on figuring out the RPM.  The RPM is likely just a .cpio.gz file.  Fileroller should uncompress the .gz just fine and 7zip should open the .cpio, leaving you with the a bunch of folders.  (I'm on a Windows machine right now, fileroller might be able to decompress the rpm in one step.)  The folders you see once the file is uncompressed represent the install location of each file.  (so if a file is located in usr/lib in the rpm, that's where it is on your system.)

Hope that helps.

---

### Post by Thelasko on 2008-08-11
Also, did you read [this page]("https://help.ubuntu.com/community/VMware/Server") and [this page]("https://help.ubuntu.com/community/VMware/Server/AMD64") before you installed?  I guess VMware server isn't straight forward to install.  Upon reading this, I don't think your problem is with old files left over from your other install.

---

### Post by wtfbrb on 2008-08-11
I believe aj was correct about the problem being 2.6.24.  I did convert the rpm to deb with alien...so I reinstalled and uninstalled and this time it removed icons and seemed much cleaner.  Don't know what happened the first time, but I guess that is why noobs shouldn't use rpm files.

As for virtualbox while I should probably start a new thread to see if any of you geniuses out there can solve my problem with it.  Which is vmware (on windows) can run a machine in the background and when I use remote desktop in full screen mode it actually works virtualbox seems to be limited to the aspect ratio of the connected monitor.  But I do agree virtualbox is very good, and faster than vmware.  I just always remote in from my widescreen laptop.

Thanks for the link for installing on 8.04, I had only found the 7.10 guide which didn't work, the new one still didn't work for the vmware server 1.06, but I will try 2.0 RC1 and see how that goes.

---

