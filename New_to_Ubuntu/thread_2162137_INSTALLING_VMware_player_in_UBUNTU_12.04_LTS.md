---
title: "INSTALLING VMware player in UBUNTU 12.04 LTS"
date: 2013-07-13
forum: New to Ubuntu
---

### Post by karanbpathak on 2013-07-13
Like Vmware player is freely available for Windows 7 can i also get it for Ubuntu, I tried installing Vmware player.exe in ubuntu using wine software but i cannot install it.When i open the Vmware.exe file
with wine a blank window appears and then i have to forcefully quit?please help

---

### Post by Paqman on 2013-07-13
Does it have to be VMWare? There's a good Linux VM package called Virtualbox that's available in the Software Centre. It can run VMWare disk images, although IIRC they need to be converted first.

If it absolutely has to be VMWare then you will need a Linux version from [here]("https://my.vmware.com/web/vmware/free#desktop_end_user_computing/vmware_player/5_0|PLAYER-502|product_downloads").

---

### Post by jimingkui on 2013-07-13
There are a lot of good tutorials about how to install VMware Player on Ubuntu. Search on Google.

Here's a short:

1.) Download the VMware Player for Linux 32-bit or 64-bit (bundle) from the link (Pagman's rely). You may check 32-bit or 64-bit under <b>System Setting -> Details</b>.

2.) After downloaded, change the package file extension from FILENAME.txt to FILENAME.bundle.

3.) Right click on file and go to its Properties window, and set to "Allow execute as program" at second tab.

4.) Run in terminal:

<pre>sudo apt-get install build-essential linux-headers-$(uname -r)</pre>

<pre>sudo bash ~/Downloads/FILENAME.bundle</pre>


Here's my tutorial for Ubuntu 13.10, which also works for Ubuntu 12.04
[http://ubuntuhandbook.org/index.php/2013/07/install-vmware-player-on-ubuntu-13-10/](http://ubuntuhandbook.org/index.php/2013/07/install-vmware-player-on-ubuntu-13-10/)

---

