---
title: "Howto: Install and run vwmare-server from repositories"
date: 2007-06-14
forum: Outdated Tutorials &amp; Tips
---

### Post by eentonig on 2007-06-14
The [old and existing howto]("http://ubuntuforums.org/showthread.php?t=183209&highlight=howto+vmware") still does a more then decent job on explaining how to install vmware-server from source. It does not explain how to install it from the official 'commercial' repositories.

Another good howto with extensive use of pictures can be found [here]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html"). You might be better off using that, but it doesn't include the patch mentioned at the end of this post. So in case of problems, check back here.

**_[COLOR="Red"][SIZE="4"]Prerequisites:[/SIZE][/COLOR]_**

A pc with enough processing power and ram to run 2 Operating Systems.

**_[COLOR="Red"][SIZE="4"]HOWTO[/SIZE][/COLOR]_**

_**1. Enable the required repo**_
Open **Synaptic **and open **Settings\Software Sources**
Open the "**Third-Party Software**" tab. click on "**+ Add..**." and enter
**deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main**
'**Close**' and '**Reload**'

*Alternative: *
Open terminal
> gksudo gedit /etc/sources.list
and put the following line at the bottom of the file.
> deb [http://archive.canonical.com/ubuntu](http://archive.canonical.com/ubuntu) feisty-commercial main

update the repo info
> sudo apt-get update

**_2. Install vmware-server_**

Still in Synaptic, search for **vmware-server** and mark it for installation.
You should also see **vmware-server-kernel-modules**, mark for installation as well
Click on '**Apply**'

_*Alternative*_
> sudo apt-get install vmware-server vmware-server-kernel-modules

When this is done, you have vmware-server installed, but it could still be that you can't run the VM's yet. This is because the kernel-modules apparently aren't updated everytime they update the kernel.
***The solution:***
download tthe vmware-any-any-update patch from
[http://knihovny.cvut.cz/ftp/pub/vmware/](http://knihovny.cvut.cz/ftp/pub/vmware/) 

Unpack the archive to a folder to your liking. Open a terminal in this extracted folder and enter

> chmod +x runme.pl
sudo ./runme.pl

---

### Post by jamaas on 2007-06-14
Why might I be getting this error?

Thanks

Jim

0$ sudo apt-get install vmware-server vmware-server-kernel-modules 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
vmware-server is already the newest version.
vmware-server-kernel-modules is already the newest version.
0 upgraded, 0 newly installed, 0 to remove and 1 not upgraded.
1 not fully installed or removed.
Need to get 0B of archives.
After unpacking 0B of additional disk space will be used.
Setting up vmware-server (1.0.3-1) ...
/etc/init.d/vmware-server: 176: vmware_product_name: not found
Warning: Unable to find 's main database /etc/vmware/locations.

invoke-rc.d: initscript vmware-server, action "start" failed.
dpkg: error processing vmware-server (--configure):
 subprocess post-installation script returned error exit status 1
Errors were encountered while processing:
 vmware-server
E: Sub-process /usr/bin/dpkg returned an error code (1)

---

### Post by gg234 on 2007-06-14
this is very detailed [installation guide ]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html") with screenshots

---

### Post by eentonig on 2007-06-14
> **gg234 said:**
> this is very detailed [installation guide ]("http://www.ubuntugeek.com/how-to-install-vmware-server-from-canonical-commercial-repository-in-ubuntu-feisty.html") with screenshots

That one is indeed very detailed and clear. It misses two thing though.

1. It's not on ubuntuforums.org, so people might miss it when searching. I know I didn't find it when searching. But it's good you referenced it. I'll add it to my first post.
2. It doesn't include the patch I mentioned. And you need that when the modules aren't in sync with the server. 


jamaas,
Did you already tried installing vmware before using another howto? 
> vmware-server is already the newest version.
vmware-server-kernel-modules is already the newest version.

I think the previous install is screwing you up.

---

### Post by limaunion on 2007-07-06
Hi! I've followed this howto but due that I'm using a self compiled kernel (latest vanilla) I'm having some problem while trying to install the modules. 

I've downloaded the vmware-any-any-update patch but it gives me the following error: 
sh: /usr/bin/vmware-config.pl: not found

It seems that this command is needed in order to compile the modules but it doesn't exist in any of the vmware packages. 

Any idea how to solve this ?
Thanks!

---

