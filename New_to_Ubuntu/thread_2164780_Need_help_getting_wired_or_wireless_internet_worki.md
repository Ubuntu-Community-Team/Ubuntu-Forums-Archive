---
title: "Need help getting wired or wireless internet working!"
date: 2013-08-01
forum: New to Ubuntu
---

### Post by ryan4 on 2013-08-01
I am completely new to Ubuntu and linux. I installed it on my new laptop, an ASUS X75A, but I cannot get online, either wired or wireless. I have been reading forums for the last several ours and have not been able to find a solution to my problem. Ifconfig returns only an "lo" but not an "eth0". When I try "auto eth0" I get:

No command 'auto' found...

What do I need to do to get the internet going? I would like to get the wireless going eventually but the wired would be a start.  Thanks.

---

### Post by ryan4 on 2013-08-01
I might add that I installed 12.04.2 (does it have a name? I thought they had names like 'Jaunty Jackal')... I wanted to install the small version, I think it is called LUBUNTU, but I was never asked what version I wanted to install during the installation.

---

### Post by ryan4 on 2013-08-01
I discovered the Ubuntu software center, which shows "Network (network-manager-gnome)". I think I need to reinstall this, but I can't figure out how. If I click on it, it shows: "Available from the 'main' source", and the USE THIS SOURCE button is grayed out.

---

### Post by TheFu on 2013-08-01
It seems the OS doesn't know which driver to load for your specific ethernet card.  

[http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware](http://blog.jdpfu.com/2013/04/27/linux-troubleshooting-101-knowing-your-hardware) explains how to determine the network card information so you can look for a driver.

I would not work on the wireless at this point. Concentrate only on the wired connection.  Wifi can be much harder to get working - and may never work on some models.

---

### Post by ryan4 on 2013-08-01
Thanks, I am reading the content in the link right now. Will post any results.

---

### Post by ryan4 on 2013-08-01
What am I looking for? Network controller? Ethernet controller?

---

### Post by ryan4 on 2013-08-01
I ran

sudo lshw

---

### Post by ryan4 on 2013-08-01
Okay, the ethernet controller is an AR8161, the network controller shows (under product) "Ralink corp."

---

### Post by ryan4 on 2013-08-01
when I run "sudo lshw -short -C network" the device column is empty for both Ralink and AR8161

---

### Post by ryan4 on 2013-08-01
So do I need drivers? How do I get them?

---

### Post by TheFu on 2013-08-01
> **ryan4 said:**
> So do I need drivers? How do I get them?

I googled "ubuntu ar8161" and this was the first result: 
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Seems you are on the bleeding edge of hardware.

---

### Post by ryan4 on 2013-08-02
Thanks, I followed the link and tried the suggestions, but I always get a result of "Unable to locate package..." or "Couldn't find any package by..."

---

### Post by ryan4 on 2013-08-02
I downloaded the package here:
[http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-amd64/linux-backports-modules-cw-3.4-3.2.0-48-generic_3.2.0-48.36_amd64.deb/download/](http://pkgs.org/ubuntu-12.04/ubuntu-updates-main-amd64/linux-backports-modules-cw-3.4-3.2.0-48-generic_3.2.0-48.36_amd64.deb/download/)

And now have it on the new computer. Where do I put it so that Ubuntu will find it?

---

### Post by ryan4 on 2013-08-02
I was going to try this with the package:
[http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/](http://www.cyberciti.biz/faq/ubuntu-linux-how-do-i-install-deb-packages/)

But I am not sure where I should put it.

---

### Post by ryan4 on 2013-08-02
I put it in my 'downloads' directory, and used Ubuntu Software Centre to attempt installation. I am told that there is an error, that I should use the backports 'meta-package'
I cannot find the right package/meta-package. Another I tried gave me another error: "Dependency is not satisfiable..."

Where can I find the package I need?

---

### Post by ryan4 on 2013-08-02
Well, I tried installing 'linux-backports-modules-cw-3.4-3.2.0-29-generic' but I am told "Dependency is not satisfiable: linux-image-3.2.0-29-generic". When I try to install that, I am told to use "linux-generic", but when I try installing that I get the message: "Dependency is not satisfiable: linux-image-generic (=3.2.0.40.48)"

Can anybody please help me out here?

---

### Post by TheFu on 2013-08-02
I don't know.

It is best that you work with 1 set of instructions and follow them completely. If you get stuck, post the exact command AND all the output here, so someone else can try to help. Often, if you read the output carefully, you will understand the issue.  Copy and paste is your friend here.  Also, please use the "Adv Reply" with "code" tags here so it is all easier to read.

I get that you are frustrated. I'd be too, but at least there seems to be a possible solution.  Plus you are learning a bunch.

I know this is a little late, but if you haven't wiped Windows, you might consider running Ubuntu inside a virtual machine.  The virtual hardware will be supported by Ubuntu and the real hardware has Windows drivers.  Just a thought.  I ran Ubuntu inside a VM for the last 5 yrs.  For everything that I did, when I was full screen, I'd forget it was inside a VM. It was very stable and performed fine.  Anyway, just a thought.

---

### Post by ryan4 on 2013-08-02
I suspect that I need to install drivers, per:
[http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller](http://askubuntu.com/questions/165192/how-do-i-install-drivers-for-the-atheros-ar8161-ethernet-controller)

Which you suggested I read. 

Installing the package for the driver seems like a possible solution. So what I am specifically seeking help with is how to install the package, given that I have no internet on the computer. I have tried copying over various .deb files, but have had little success, in part because there are so many different .deb files and I do not know which one to use. 

I have tried 7 different .deb files and all return a "dependency is not satisfiable" error. But I might just be installing the wrong file. Is it that, or is it something else?

---

### Post by ryan4 on 2013-08-04
I solved the issue, [see my post here]("http://ubuntuforums.org/showthread.php?t=2165295").

---

### Post by TheFu on 2013-08-04
> **ryan4 said:**
> I solved the issue, [see my post here]("http://ubuntuforums.org/showthread.php?t=2165295").

Thanks for posting your solution. It will probably help others ... however, I fear that at the next kernel upgrade, your wifi will stop working again. See, installing the exact kernel headers was needed, but using a meta-package for "current-kernel-headers" will have the next kernel headers installed automatically and rebuilding the drivers again will be easier.

One of three kernel header packages is required. Run
```
$ uname -r
```
and based on the returned string, install one of these:

{}-generic-pae = **apt-get install linux-headers-generic-pae**
{}-generic = **apt-get install linux-headers-generic**
{}-server = **apt-get install linux-headers-server**

I hope that's clear. Whenever we install packages using .deb files, we risk future dependency issues. It is always best to install using the Canonical repositories. You didn't have any choice this time, but if you install the meta-package for headers now, it should make life a little easier, if not completely automatic, in the future.

---

### Post by ryan4 on 2013-08-20
Sure enough, I ran some updates today and it bumped my kernel up, so I had to roll it back. I fixed it and tried your suggestion to install a kernel headers package, but this is what I got:

ryan@ryan-X75A:~$ sudo apt-get install linux-headers-generic
[sudo] password for ryan: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
linux-headers-generic is already the newest version.
The following package was automatically installed and is no longer required:
  firefox-globalmenu
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.
ryan@ryan-X75A:~$ 

It didn't seem to install anything, so I am afraid I may have the same problem next kernel update.

---

### Post by TheFu on 2013-08-20
Well, if you are running the old kernel, then you aren't using the new drivers or headers. 
Why did you install "linux-headers-generic"?  Was that the specific need from the **uname -r** output?  Afterwhich you'll need to boot into the new kernel and rebuild whatever drivers you custom built again.  This will be a way of life with every new kernel until you can find a PPA or repository for the needed drivers.

I'm not certain if this is clear, but installing things from .DEB files is almost worse than installing from source.  It can force your system to keep packages and dependencies that you don't want .... leading to "APT Hell" where nothing can be installed or remove because the apt DB has gotten too confused.  I have a system in APT-Hell now. It sucks.

---

### Post by ryan4 on 2013-08-20
> **TheFu said:**
> Well, if you are running the old kernel, then you aren't using the new drivers or headers. 
Why did you install "linux-headers-generic"?  Was that the specific need from the **uname -r** output?  Afterwhich you'll need to boot into the new kernel and rebuild whatever drivers you custom built again.  This will be a way of life with every new kernel until you can find a PPA or repository for the needed drivers.

I'm not certain if this is clear, but installing things from .DEB files is almost worse than installing from source.  It can force your system to keep packages and dependencies that you don't want .... leading to "APT Hell" where nothing can be installed or remove because the apt DB has gotten too confused.  I have a system in APT-Hell now. It sucks.

Here is the output:

ryan@ryan-X75A:~$ uname -r
3.2.0-51-generic
ryan@ryan-X75A:~$ 


So I installed the generic headers. I do not want to go to APT Hell, that's why I am trying to sort this out now.

---

