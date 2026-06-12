---
title: "virtual box error"
date: 2011-10-16
forum: New to Ubuntu
---

### Post by cmcanulty on 2011-10-16
My virtualbox running XP has developed an error and the fix suggested which I am showing in output doesn.t work. I need some help on this.
```
cmcanulty@HP:~$ /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                              /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied
                                                                         [ OK ]
 * Trying to register the VirtualBox kernel modules using DKMS                  /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        /etc/init.d/vboxdrv: 415: cannot create /var/log/vbox-install.log: Permission denied

 * Look at /var/log/vbox-install.log to find out what went wrong
cmcanulty@HP:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.35-27-generic-pae cannot be found at
/lib/modules/2.6.35-27-generic-pae/build or /lib/modules/2.6.35-27-generic-pae/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
cmcanulty@HP:~$
```

---

### Post by mister_playboy on 2011-10-16
```
sudo /etc/init.d/vboxdrv setup
```

Root is required for this since it's modifying the kernel.

---

### Post by cmcanulty on 2011-10-16
same error with sudo
```
cmcanulty@HP:~$ sudo /etc/init.d/vboxdrv setup
 * Stopping VirtualBox kernel modules                                    [ OK ] 
 * Uninstalling old VirtualBox DKMS kernel modules                       [ OK ] 
 * Trying to register the VirtualBox kernel modules using DKMS                  
Error! Your kernel headers for kernel 2.6.35-27-generic-pae cannot be found at
/lib/modules/2.6.35-27-generic-pae/build or /lib/modules/2.6.35-27-generic-pae/source.

 * Failed, trying without DKMS
 * Recompiling VirtualBox kernel modules                                        
 * Look at /var/log/vbox-install.log to find out what went wrong
cmcanulty@HP:~$ 

```

---

### Post by wildmanne39 on 2011-10-16
Hi, make sure your kernel headers are installed for 2.6.35-27-generic-pae.
Thank you

---

### Post by cmcanulty on 2011-10-17
How do I do that synaptic doesn't have headers for that number

---

### Post by wildmanne39 on 2011-10-17
Hi, I do not know for sure then but you might make sure backports is checked in synaptic then reload synaptic and see if it shows up.
Thank you

---

### Post by cmcanulty on 2011-10-18
I looked through all the synaptic menus and software sources and don't see any setting for backports. Sorry to be so dumb.

---

### Post by sadaruwan12 on 2011-10-18
For any reason did you removed those headers or did you do an upgrade of your system ?

I got this ERROR once but after a upgrade and I ran the same command it solved it buy recompiling the modules to the new kernel.

I think your old kernel headers are missing.

Or you could backup your .VDI files and do a reinstall of the software.

---

### Post by wildmanne39 on 2011-10-18
Hi, this should install the headers, run the command for virtualbox again.
```
sudo apt-get install --reinstall linux-headers-$(uname -r)
```

---

### Post by cmcanulty on 2011-10-18
Here is the error I get now. I didn't do any upgrading
```

cmcanulty@HP:~$ sudo apt-get install --reinstall linux-headers-$(uname -r)
Reading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package linux-headers-2.6.35-27-generic-pae
E: Couldn't find any package by regex 'linux-headers-2.6.35-27-generic-pae'
cmcanulty@HP:
```~$

---

### Post by wildmanne39 on 2011-10-18
Hi let&#347; check backports then run the linux kernel header command again.

Open synaptic click on settings, repositories, updates, make sure a check is by backports, then click reload in synaptic then close.

If that does not work then I am out of ideas.
Thank you

---

### Post by cmcanulty on 2011-10-18
yes it is checked, I missed that. Thanks for your help. I will try reinstalling VB as I can't use it now anyway.

---

### Post by wildmanne39 on 2011-10-18
Hi, okay I have no more ideas, but if it can not find your kernel headers I think you are still going to have problems when you reinstall virtualbox.
Thank you

---

### Post by cmcanulty on 2011-10-18
thank you!

---

### Post by anewguy on 2011-10-18
You DID install the build-essential package, right?

Dave ;)

---

### Post by cmcanulty on 2011-10-19
yes

---

### Post by anewguy on 2011-10-20
Have you tried following the link for downloading the headers in the following link?  I tried it and it links to another page where there is a link that has the word "security" in it.  Clicking on that link starts the download of the headers.

[http://packages.ubuntu.com/maverick/linux-headers-2.6.35-27-generic-pae]("http://packages.ubuntu.com/maverick/linux-headers-2.6.35-27-generic-pae")

Hope that works some how for you.

Dave ;)

---

### Post by cmcanulty on 2011-11-05
I finally got the deb header file but when I try to install I get dependency not satisfyable but no detail as to what I need

---

