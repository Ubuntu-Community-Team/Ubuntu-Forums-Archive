---
title: "HowTo: Installing VMware Tools 5.5.2 on Ubuntu 6.10"
date: 2006-10-27
forum: Outdated Tutorials &amp; Tips
---

### Post by mtnbike on 2006-10-27
I recently investigated the use of Ubuntu and worked through the process of installing VMware Tools and developed this guide. All comments and feedback welcome as this is my first experience with Ubuntu.

Host OS: Windows XP SP2
VMware Workstation: 5.5.2 build-29772
Guest OS: Ubuntu-6.10.1-desktop-i386 (Edgy Eft)

The VMware Tools installer (for 5.5.2) does not install drivers for Xorg 7.1, only up to 7.0 is supported. The method outlined below updates the installer to install the 7.0 vmmouse driver and leaves the vmware video driver that exists on a default 6.10 install in place. The existing 6.10 vmware_drv.so is 39332 bytes, 2006-09-11 19:55.

The full text is available here: [http://mtnbike.org/blog/?p=26](http://mtnbike.org/blog/?p=26)

---

### Post by domino on 2006-10-28
Hi mtnbike. Thanks for the info. On edgy host, do you have full network support using bridged network for both Windows guest and Edgy guest? I have no bridge support on edgy guest and only Host-only network support for Winodws guest. I mount the same two .vmx on a windows host and I have full network support for both guest OS.

VMware workstation worked 100% while Edgy was in beta 4 days ago. I think upgrading to Final release broke something.

---

### Post by gasoya on 2006-10-29
I'm totally new to anything that isn't Microsoft, but, this is what happened to me:

After I did
```
sudo /usr/bin/vmware-config-tools.pl
```

I got
```
syntax error at /usr/bin/vmware-config-tools.pl line 4491, near "elsif"
Execution of /usr/bin/vmware-config-tools.pl abored due to compilation errors.
```

---

### Post by lech@ibcl.at on 2006-10-29
> **domino said:**
> VMware workstation worked 100% while Edgy was in beta 4 days ago. I think upgrading to Final release broke something.

I must agree, vmware workstation 5.5.2 does not work any more since I upgraded my laptop from dapper to edgy.

Furthermore, on most of my machines Firefox crashes with certain sites (about 99% of the web) due to some X11+ATI related problem, and quite some legacy C software refuses to even configure ...

I am not gonna update my servers for now ...

---

### Post by mtnbike on 2006-10-29
> **domino said:**
> Hi mtnbike. Thanks for the info. On edgy host, do you have full network support using bridged network for both Windows guest and Edgy guest? I have no bridge support on edgy guest and only Host-only network support for Winodws guest. I mount the same two .vmx on a windows host and I have full network support for both guest OS.

VMware workstation worked 100% while Edgy was in beta 4 days ago. I think upgrading to Final release broke something.

I've not run Edgy as Host, only as a VM.  Sorry I could not provide any details.

---

### Post by soul814 on 2006-10-29
I just set up vmware w/ ubuntu today on my notebook and I hate the fact that i dont have widescreen support =( vmware creates its own virtual video card and i didnt know about that so i spent an hr trying to install atis driver o well

---

### Post by domino on 2006-10-30
That's okay. I'm here to confirm that on Edgy desktop host, vmware bridge networking does not work. i have both winxp guest and 6.10 server guest and neither can connect to the network or browse using bridged network. The only way for the windows guest to be able to browse the network/Internet is to set the the network to NAT or Host Only. IMO, that's totally useless for a server guest because I needs a static IP and it must be bridged. Btw, both guest OS work 100% on a windows host.

I heard that there was to be a service release for VMware WS to add 6.10 support. only then will we be able to run guest OS with static IP.

[email]lech@ibcl.at[/email], I've read many things breaking while upgrading from dapper to Edgy. I'm sorry about your troubles. I did a fresh install from Edgy beta to edgy final. As far as I know, VMware WS networking is the only thing broke.

---

### Post by mtnbike on 2006-10-30
> **gasoya said:**
> I'm totally new to anything that isn't Microsoft, but, this is what happened to me:

After I did
```
sudo /usr/bin/vmware-config-tools.pl
```

I got
```
syntax error at /usr/bin/vmware-config-tools.pl line 4491, near "elsif"
Execution of /usr/bin/vmware-config-tools.pl abored due to compilation errors.
```

Be aware that this patch is only for VMware Tools 5.5.2.  Also, the line was wrapped in my post so it may have confused you.

```

wget http://mtnbike.org/vmware/vmware-config-tools-5.5.2-patch-diff.txt
sudo chmod u+w /usr/bin/vmware-config-tools.pl
sudo patch /usr/bin/vmware-config-tools.pl vmware-config-tools-5.5.2-patch-diff.txt
sudo /usr/bin/vmware-config-tools.pl

```

---

### Post by chris-at on 2006-10-30
After installing VMware tools (with and without your patch) I get the following error when the X server starts:

*** VMware Workstation internal monitor error ***
vcpu-0:ASSERT devices/vide/vide.c:2264 bugNr=12190
...

Any ideas?

---

### Post by saracen on 2006-11-03
I get this error after patching the file:

```
sudo /usr/bin/vmware-config-tools.pl
"my" variable $xorg_modules_dir masks earlier declaration in same scope at /usr/bin/vmware-config-tools.pl line 4493.
"my" variable $gXMouseDriverFile masks earlier declaration in same scope at /usr/bin/vmware-config-tools.pl line 4501.
syntax error at /usr/bin/vmware-config-tools.pl line 4491, near "elsif"
syntax error at /usr/bin/vmware-config-tools.pl line 4512, near "1)"
syntax error at /usr/bin/vmware-config-tools.pl line 4527, near "} elsif"
Execution of /usr/bin/vmware-config-tools.pl aborted due to compilation errors.
```

---

### Post by gorth on 2006-11-05
mtnbike, I've followed your howto and everything seems to work fine with the exception of synchronized clipboard.

---

### Post by Nickolay on 2006-11-06
I was getting the "Failed to load module "vmware" (module requirement mismatch" error after multiple attempts to get this working. Turned out I had a wrong version of vmware_drv.so in xorg's input/ (?!) folder in addition to the right one installed by the script. Once I deleted that one, everything worked fine. Hope that helps other with this problem.

Thanks for the instructions, much appreciated.

---

### Post by xunshirine on 2006-11-13
Hi. I am on Xp home SP2. I downloaded and saved 6.10 iso file into a directory and used this iso file by creating an extra vmrave cdrom drive. After booting ubuntu on vmware, I choose to install the vmware tools from the vmware menu , then iso file of vmware tools implement into cdrom. But I can't find any tar file to ectract in this cdrom file. The image is below. What to do now?

[[IMG]http://img228.imageshack.us/img228/6726/ekrangrnts1pu3.th.png[/IMG]](http://img228.imageshack.us/my.php?image=ekrangrnts1pu3.png)

---

