---
title: "update failing"
date: 2008-09-16
forum: New to Ubuntu
---

### Post by harry001 on 2008-09-16
When trying to update either via a terminal or package manager l get an error that says
 
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem. 

When l run this l get: 

admin@ks32754:~$ sudo dpkg --configure -a
Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

Can someone tell me how to fix this .....

---

### Post by vikramaditya on 2008-09-16
Hi...have a looky at [this]("http://www.linuxforums.org/forum/ubuntu-help/127343-can-not-get-updates-now-after-fouled-up-previous-update.html").  Sounds very much like a fix for ya. :)

---

### Post by anotherdisciple on 2008-09-16
It's actually just as simple as the error explained. Open a terminal and type:

```
dpkg --configure -a
```

---

### Post by harry001 on 2008-09-16
Thanks for replies but neither work. Running dpkg --configure -a results in 

Setting up initramfs-tools (0.85eubuntu39.2) ...
update-initramfs: deferring update (trigger activated)

Processing triggers for initramfs-tools ...
update-initramfs: Generating /boot/initrd.img-2.6.24-16-generic
Cannot find /lib/modules/2.6.24-16-generic
update-initramfs: failed for /boot/initrd.img-2.6.24-16-generic
dpkg: subprocess post-installation script returned error exit status 1

Going through the process vikramaditya suggested in his post results in an error to run dpkg --configure -a which means its just going in circles....

---

### Post by anotherdisciple on 2008-09-16
I don't know if it needs you to be root... try:

```
sudo dpkg --configure -a
```

---

### Post by harry001 on 2008-09-16
Yes did that from the outset result is still the same :confused:

---

### Post by phidia on 2008-09-16
Enter > sudo apt-get update && sudo dpkg --configure -a
Hope that helps.

---

### Post by harry001 on 2008-09-16
Talk about frustrating. Here is output from that.

admin@ks32754:~$ sudo apt-get update && sudo dpkg --configure -a
 
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy Release.gpg
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/main Translation-en_GB
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/restricted Translation-en_GB
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/universe Translation-en_GB
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/multiverse Translation-en_GB
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates Release.gpg
Get: 1 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main Translation-en_GB
Ign [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main Translation-en_GB    
Get: 2 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/restricted Translation-en_GB
Ign [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/restricted Translation-en_GB
Get: 3 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/universe Translation-en_GB
Ign [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/universe Translation-en_GB
Get: 4 [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/multiverse Translation-en_GB
Ign [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/multiverse Translation-en_GB
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy Release                           
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates Release
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/main Packages                          
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/restricted Packages                    
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/main Sources                   
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/restricted Sources                            
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/universe Packages                             
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/universe Sources                              
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/multiverse Packages                           
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy/multiverse Sources                            
Get: 5 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release.gpg [189B]
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Translation-en_GB
Ign [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Translation-en_GB
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main Packages
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/restricted Packages
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/main Sources
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/restricted Sources
Get: 6 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security Release [58.5kB]
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/universe Packages
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/universe Sources
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/multiverse Packages
Hit [ftp://mir1.ovh.net](ftp://mir1.ovh.net) hardy-updates/multiverse Sources
Get: 7 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Packages [58.6kB]
Get: 8 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Packages [6636B]
Get: 9 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/main Sources [13.2kB]
Get: 10 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/restricted Sources [908B]
Get: 11 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Packages [31.2kB]
Get: 12 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/universe Sources [5540B]
Get: 13 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Packages [8222B]
Get: 14 [http://security.ubuntu.com](http://security.ubuntu.com) hardy-security/multiverse Sources [14B]
Fetched 183kB in 0s (331kB/s)                         
E: dpkg was interrupted, you must manually run 'dpkg --configure -a' to correct the problem.

---

### Post by anotherdisciple on 2008-09-16
hmmm... confusing... try switching servers... I think you do this under (System > Administration > Software Sources) In the first tab there should be a "Download from" option... choose "Main Server"... or click "choose other"... and click the select best server button.

I honestly have no clue if that will help, but it can't hurt.

I just noticed that your sources list looked abnormal... maybe it's because you are in a different country... I don't know.

---

### Post by harry001 on 2008-09-16
Thank you for your time anotherdisciple. I don't have that option in the menu. I access this server via remote connection. 

I'm not quite sure what else to try as the problem does seem to be unique. Is there someway perhaps l can uninstall and reinstall the package manager? Do you think that may help?


cheers

---

