---
title: "Virtual Box"
date: 2014-05-01
forum: New to Ubuntu
---

### Post by Chant_Gras on 2014-05-01
Hi Folks,

I'm on a Dell M4600 (Intel® Core&#8482; i5-2540M CPU @ 2.60GHz × 4) with 32-bit Ubuntu 13.10. Never ever had problems with Ubuntu before.

I'm really stuck here. I'm having trouble getting VBox to start (this never happened before either). I know that there are plenty of previous posts on this, but I can make neither head nor tail of them. In any case, anything I've tried following instructions from other posts doesn't work.

Windows 7 has always run very well for me in VBox. When I try to start Windows 7 in VBox now, I get this message:
FIRST:
Failed to open a session for the virtual machine W7.
The virtual machine 'W7' has terminated unexpectedly during startup with exit code 1.
Details
Result Code: NS_ERROR_FAILURE (0x80004005)
Component: Machine
Interface: IMachine {22781af3-1c96-4126-9edf-67a020e0e858}

THEN:
 The VirtualBox Linux kernel driver (vboxdrv) is either not loaded or there is a permission problem with /dev/vboxdrv. Please reinstall the kernel module by executing

  [COLOR=#0000ff]'/etc/init.d/vboxdrv setup'[/COLOR]
  as root. If it is available in your distribution, you should install the DKMS package first. This package keeps track of Linux kernel changes and recompiles the vboxdrv kernel module if necessary.

 
I have tried the following solutions in several different orders:

1 apt-get install linux-headers-3.5.0-17-generic (didn't work)

2 wget [http://www.cisgendered.com/~keyvin/v...mods-3.4.0.deb](http://www.cisgendered.com/~keyvin/v...mods-3.4.0.deb) (and got 404 Not Found as a response)

3 apt-get remove virtualbox-dkms
  apt-get install virtualbox-dkms - didn't work, but generated the following:

Setting up virtualbox-dkms (4.2.16-dfsg-3ubuntu0.1) ...
Loading new virtualbox-4.2.16 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-31-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]

4 Also tried:
sudo /etc/init.d/vboxdrv setup
and got as a response:
sudo: /etc/init.d/vboxdrv: command not found

I'm really lost right now and don't know what else to try.

If I reinstall VBox, will it erase my Windows 7 already installed? Problem is I don't have a CD to reinstall Windows.

Thanks in advance for any help you can suggest.

Hope to hear from you soon,
CG

---

### Post by jdeca57 on 2014-05-01
First of all, what happened in order to make Virtualbox fail? My guess is that there was a new kernel installed. Now I don't have 13.10 running here anymore but things like sudo apt-get install linux-headers-$(uname -r) installs the headers of the installed kernel and that seems to be 3.8.0-31-generic. uname -r on a command line gives this info.
installing virtualbox-dkms should work then.

---

### Post by Chant_Gras on 2014-05-01
Hi jdeca57

Many thanks for the speedy reply.

This is what i've tried since:
```

xx:~$  uname -r
3.8.0-31-generic
xx:~$ sudo apt-get install linux-headers-generic
[sudo] password for xx: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
linux-headers-generic set to manually installed.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
xx:~$ sudo apt-get remove virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages will be REMOVED:
  virtualbox-dkms
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 4 141 kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... 387844 files and directories currently installed.)
Removing virtualbox-dkms ...

------------------------------
Deleting module version: 4.2.16
completely from the DKMS tree.
------------------------------
Done.
xx:~$ sudo apt-get install virtualbox-dkms
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following NEW packages will be installed:
  virtualbox-dkms
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
Need to get 0 B/514 kB of archives.
After this operation, 4 141 kB of additional disk space will be used.
Selecting previously unselected package virtualbox-dkms.
(Reading database ... 387575 files and directories currently installed.)
Unpacking virtualbox-dkms (from .../virtualbox-dkms_4.2.16-dfsg-3ubuntu0.1_all.deb) ...
Setting up virtualbox-dkms (4.2.16-dfsg-3ubuntu0.1) ...
Loading new virtualbox-4.2.16 DKMS files...
First Installation: checking all kernels...
Building only for 3.8.0-31-generic
Module build for the currently running kernel was skipped since the
kernel source for this kernel does not seem to be installed.
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Starting VirtualBox kernel modules                                            * No suitable module for running kernel found
                                                                         [fail]
invoke-rc.d: initscript virtualbox, action "restart" failed.
xx:~$ 
xx:~$ 

```
So still not working ...
CG

---

### Post by SeijiSensei on 2014-05-01
First, no, you won't lose your virtual machine images if you blow away your current VB instance.  They are simply large files on your hard drive, usually stored in your home directory under "VirtualBox VMs".  (If you're running an older version of VB, they might be in a hidden directory called .VirtualBox.)

Next, I recommend that you remove any current copies of VirtualBox from your machine, then follow the instructions on the VB site for [Debian-based distributions]("https://www.virtualbox.org/wiki/Linux_Downloads#Debian-basedLinuxdistributions") to add the Oracle repository.  Now your copy of VB will survive kernel changes and be automatically maintained along with the other software on your system.

Remember to install the Extension Pack as well.

You might want to plan to upgrade your version of Ubuntu to 14.04LTS as well.  13.10 won't be supported [past July]("https://wiki.ubuntu.com/Releases").

---

### Post by Chant_Gras on 2014-05-02
Hi SeijiSensei,

Thanks for your advice. Clearly, you know what you're doing. The problem is, I don't. Looking at the VBox download page you suggest above, I don't even know where to start. Wouldn't a reinstall of VB mess up my current settings (shared folders, device filters, etc)? I wouldn't know how to set those up again.

As for moving on to 14.04LTS, in view of what is said here ([http://www.theregister.co.uk/2014/04/28/ubuntu_power_user_crash/](http://www.theregister.co.uk/2014/04/28/ubuntu_power_user_crash/)) I think I'll give it a miss for a while.

Many thanks for your suggestions,
CG

---

### Post by SeijiSensei on 2014-05-02
> **Chant_Gras said:**
> Hi SeijiSensei,

Thanks for your advice. Clearly, you know what you're doing. The problem is, I don't. Looking at the VBox download page you suggest above, I don't even know where to start. Wouldn't a reinstall of VB mess up my current settings (shared folders, device filters, etc)? I wouldn't know how to set those up again.

You configure shared folders and device filters in the VB Manager.  Choose a VM, click Settings, and pick USB for device filters and Shared Folders for, well, shared folders.  I don't usually have many of these at all.  I have one shared folder.  For most purposes, I write files to a server that both the host and guest can use.  I have only two USB filters.

I suspect all these settings are stored with the VM image, though I haven't tested that to be sure.  If so, they are invulnerable to changes in VirtualBox itself.

Here's a quick overview of the upgrading process.

1)  Use sudo and a text editor to create the file /etc/apt/sources.list.d/virtualbox.list and put this one line into it:
```
deb http://download.virtualbox.org/virtualbox/debian saucy contrib
```

2)  Next, you need to add the signing key for the Oracle repository so that your system can verify that packages from the repository are legitimate.  Run the command:
```
wget -q http://download.virtualbox.org/virtualbox/debian/oracle_vbox.asc -O- | sudo apt-key add -
```

3)  Update your software sources by running
```
sudo apt-get update
```

Now you have a couple of choices.  It looks like you have version 4.2 of VirtualBox.  You can update that installation by running the command:
```
sudo apt-get install virtualbox-4.2
```

If that works, and you'd like to upgrade to 4.3, then run
```
sudo apt-get install virtualbox-4.3
```
at some future time.

> As for moving on to 14.04LTS, in view of what is said here ([http://www.theregister.co.uk/2014/04/28/ubuntu_power_user_crash/](http://www.theregister.co.uk/2014/04/28/ubuntu_power_user_crash/)) I think I'll give it a miss for a while.

Does your system use [UEFI]("http://www.farstone.com/articles/what-is-uefi.php")?  Mine doesn't.  The [problem]("http://ubuntuforums.org/showthread.php?t=2217894") described in that article concerns upgrading on systems with UEFI enabled. In true "TheReg" style, their article doesn't even mention what the problem is but just relies on a garish headline to drive more traffic to their site.  I would never make decisions based on a single article in TheReg.

I had no problems upgrading from 12.04 -> 13.04 -> 13.10 -> 14.04.  In fact I started running the alpha version of 14.04 in January.  I had only one problem using the alpha/beta versions of Trusty Tahr which was resolved by updates in a day or two.

It looks like the M4600 has support for UEFI in the BIOS, but it is [disabled]("http://superuser.com/questions/383079/what-are-the-advantages-to-install-windows-7-with-uefi") by default.  On a machine that boots only Linux, I see no advantages to UEFI and would leave it disabled.

---

