---
title: "VMware Problem...."
date: 2007-07-19
forum: Other OS Talk
---

### Post by hockey97 on 2007-07-19
I  tried installing VMware on my sister's labtop, the installation faild at the end, now it locked up my package manager and update manager, I get error's when I try using them, it say's VMware didn't install properly, please reinstall.

When I tried the updates, it say's that VMware didn't install properly, try to reinstall, can't find the archive.

like update trie's to repair the problem but couldn't find the archive. When I try to download VMware and install it, it say's that I don't haver permissions for this file or the file is currpted, please reinstall.

I tried to delete it with ```
sudo apt-get remove VMware-player
```

but that didn't work becuse the termanial tried to it said done but then after it said done, has an error and tells me that I need to reinstall VMware..

I really need help.

I am trying to make it possible to install programs that  only install on a windows platform, and want to connect the labtop to a windows network, so it can use the shared printers on my other computers that are running windows xp pro..

---

### Post by KyleBrandt on 2007-07-19
This is not a fix but rather an alternative.  I would try using VirtualBox, it has worked better for me than and is in the repositories.  If you chose this option, you will probably want to use NAT for networking in the options for the Guest system (Your windows box).  When using nat for your printer shares note the following:

"Two limitations of NAT networking are that finding Windows shares by browsing is not possible in the default configuration (although they can still be accessed if you know the name or the IP address of the machine that is sharing them) and that the ping utility will not get a response from the host or other machines outside of the private network."

Thats is from the virtualbox help file, you will probably want to read the whole section about NAT.

As far as fixing that vmware install goes, I would try some of those options using -f (force switch).  I also might try deleting the cached packages.  But there are probably people here with more experience dealing with broken apt packages.  Hope this helps a little.

---

### Post by hockey97 on 2007-07-20
well I can't download anything nor update or use package manager, all becuse VMware didn't install properly, How would I clear that cahe??

the updater tries to fix the problem, but then the error window pops up saying to reinstall. 

here is the true error,  : E: The package vmware-player needs to be reinstalled, but I can't find an archive for it.  that's what it say's in terminal and also with the update manager, the package manager just say's to reinstall VMware

This is what I get in terminal...    Reading extended state information      
Initializing package states... Done
Writing extended state information... Done
Building tag database... Done             
Couldn't find package "VMware-Player".  However, the following
packages contain "VMware-Player" in their name:
  vmware-player vmware-player-kernel-modules-2.6.20-15 
  vmware-player-kernel-modules-2.6.20-16 
  vmware-player-kernel-modules-2.6.15-28 vmware-player-kernel-modules 
The following packages are unused and will be REMOVED:
  gettext intltool-debian libbtctl4 libglib1.2 libgnomebt0 libjpeg-progs 
  libmeanwhile1 libmono-data-tds1.0-cil libmono-security1.0-cil 
  libmono-sharpzip0.84-cil libmono-sqlite1.0-cil libmono-system-data1.0-cil 
  libmono-system-web1.0-cil libmono1.0-cil libmyspell3c2 libtimedate-perl 
  libxml-perl libxmlsec1 libxmlsec1-nss libxmlsec1-openssl libxt-java 
  miscfiles myspell-en-us openoffice.org-style-default pmount po-debconf 
0 packages upgraded, 0 newly installed, 26 to remove and 0 not upgraded.
Need to get 0B of archives. After unpacking 21.3MB will be freed.
Do you want to continue? [Y/n/?] y
Writing extended state information... Error!
E: I wasn't able to locate a file for the vmware-player package. This might mean you need to manually fix this package. (due to missing arch)
E: Couldn't lock list directory..are you root?

Yes I was in root.

---

### Post by smoker on 2007-07-20
hi, if you open synaptic package manager, click on custom filters on the bottom left, and highlight the 'broken' option above.then opt for complete removal of anything in the right hand view. hopefully that will fix the problem,

or you could try > sudo apt-get check in the terminal, though i am not sure if this will remove any problems!

best of luck

---

