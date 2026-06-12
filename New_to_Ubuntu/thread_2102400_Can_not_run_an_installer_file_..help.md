---
title: "Can not run an installer file ..help"
date: 2013-01-07
forum: New to Ubuntu
---

### Post by dokha on 2013-01-07
```
/home/administrator/Desktop
bash: /home/administrator/Desktop: Is a directory
administrator@administrator ~ $ chmod +x NVIDIA-Linux-x86-310.19.run
chmod: cannot access `NVIDIA-Linux-x86-310.19.run': No such file or directory
```this is literally driving me nuts

---

### Post by mlentink on 2013-01-07
Assuming the file is indeed on your desktop: first change to the approriate directory:
```
cd /home/administrator/Desktop
```
then execute the chmod:
```
chmod +x NVIDIA-Linux-x86-310.19.run
```
Seeing as how you're logged in as "administrator" I assume you do have the priviliges to chmod the file? Otherwise precede the chmod with 'sudo'.

---

### Post by dokha on 2013-01-07
ok so everything seemed to be working until nvidia told me installation has failed and gave me a log file, here it is:```
 PATH: /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin

nvidia-installer command line:
    ./nvidia-installer

Using: nvidia-installer ncurses user interface
-> The file '/tmp/.X0-lock' exists and appears to contain the process ID '1226' of a runnning X server.
ERROR: You appear to be running an X server; please exit X before installing.  For further details, please see the section INSTALLING THE NVIDIA DRIVER in the README available on the Linux driver download page at www.nvidia.com.
ERROR: Installation has failed.  Please see the file '/var/log/nvidia-installer.log' for details.  You may find suggestions on fixing installation problems in the README available on the Linux driver download page at www.nvidia.com.
```

---

### Post by 3rdalbum on 2013-01-07
**STOP.**

Before doing a manual install of an Nvidia driver, go to Ubuntu Software Center and use the Edit menu to open the Software Sources program.

From there, you can easily install Nvidia drivers. (That's for 12.10 - if you're using 12.04 you need the Additional Drivers program, available from the Dash or from System Settings). It's much easier than doing it manually, and there are other benefits too, namely that you don't have to keep reinstalling the driver each time you install a kernel update. The version Ubuntu can help you install is the safer option, basically.

ONLY if you know you need the version from the Nvidia website, which is sometimes newer and sometimes supports newer hardware, should you attempt a manual installation of the driver from the Nvidia website.

Your problem is that you're still running the graphical display. The Nvidia driver from the Nvidia website doesn't like to be installed with your graphical desktop still active. You need to temporarily turn it off:

```
sudo service lightdm stop
```

You'll be dropped back to a text-only terminal where you can do the Nvidia driver installation. When done, type:

```
sudo reboot
```

You need to do this every time you install a kernel update. Every. Single. Time.

Please, unless you have no other option, just use the version that Ubuntu helps you install, as you can simply install it once and it will work forever.

---

### Post by dokha on 2013-01-07
> **mlentink said:**
> Assuming the file is indeed on your desktop: first change to the approriate directory:
```
cd /home/administrator/Desktop
```then execute the chmod:
```
chmod +x NVIDIA-Linux-x86-310.19.run
```Seeing as how you're logged in as "administrator" I assume you do have the priviliges to chmod the file? Otherwise precede the chmod with 'sudo'.

following the steps without sudo, nvidia gave me installer should be run in root, so i put sudo in the 2nd and 3rd command and it proceeded. unless i login as superuser which is not recommended?

---

### Post by dokha on 2013-01-07
Additional drivers is stuck on "applying changes"
EDIT
closed synaptic and it works now

---

### Post by 3rdalbum on 2013-01-07
I'm glad everything is sorted now.

---

