---
title: "ubuntu installer error after typing sh ubuntu.sh"
date: 2012-02-23
forum: New to Ubuntu
---

### Post by Delta1992 on 2012-02-23
I keep having an error after typing "sh ubuntu.sh" on my terminal. The result is :

app_125@android:/ $ export PATH=/data/local/bin:$PATH
app_125@android:/ $ su
app_125@android:/ #  cd sdcard/ubuntu
app_125@android:/sdcard/ubuntu #  sh ubuntu.sh
mkdir failed for /data/local/mnt, File exists
Loop device exists
mount: Invalid argument
mount: No such file or directory
mount: No such file or directory
mount: No such file or directory
mount: mounting /sdcard on /data/local/mnt/sdcard failed: No such file or directory
mount: mounting /sdcard/external_sd on /data/local/mnt/external_sd failed: No such file or directory
net.ipv4.ip_forward = 1
ubuntu.sh[31]: cannot create /data/local/mnt/etc/resolv.conf: No such file or directory
ubuntu.sh[32]: cannot create /data/local/mnt/etc/resolv.conf: No such file or directory
ubuntu.sh[33]: cannot create /data/local/mnt/etc/hosts: No such file or directory
Ubuntu is configured with SSH and VNC servers that can be accessed from the IP:
eth0: ip 192.168.1.103 mask 255.255.255.0 flags [up broadcast running multicast]

chroot: can't execute '/root/init.sh': No such file or directory
Shutting down Ubuntu ARM
failed.
failed.
failed.
failed.
failed.
failed.
app_125@android:/sdcard/ubuntu #

The device I am using is a galaxy tablet 10.1. Ubuntu does work on it. Was working just fine, but when running it for the third time; the error keeps appearing. The method I am using to run ubuntu is from an app called ubuntu installer (paid) version from the android market. Followed all the steps given. At first I choose the small image option, but actually wanted the large image (choose small first just to see if it worked on my tablet). Thats about it, from there I am stuck. Have tried to re-install all files and apps, but same error results keep popping up.

---

### Post by jtarin on 2012-02-23
When you reinstalled did you wipe the drive before re-installation? You might have some leftover config files affecting the new install.

---

### Post by Delta1992 on 2012-02-23
> **jtarin said:**
> When you reinstalled did you wipe the drive before re-installation? You might have some leftover config files affecting the new install.
 
Very good point. I am checking my drive for any files that may be affecting the program script. I have deleted all evidence known to me of ubuntu files and re-installed the program. The error is still there. Just to note, the installation requires the apps: "Android Terminal Emulator" by Jack Palevich, and "android-vnc-viewer" by Andriodvnc Team + Antlersoft. Could these apps contain any past existing data that might cause the terminal error? I have uninstalled these apps before and the error is still occurring.

---

### Post by matbluvenger on 2012-02-23
I am actually having the exact same problems with the same error message in the Terminal Emulator.

I'll post if I make any progress... I'd like very much to get this working.


I'm trying to do this on my Samsung Continuum (it's a part of the galaxy series)

---

### Post by Delta1992 on 2012-02-23
> **matbluvenger said:**
> I am actually having the exact same problems with the same error message in the Terminal Emulator.

I'll post if I make any progress... I'd like very much to get this working.


I'm trying to do this on my Samsung Continuum (it's a part of the galaxy series)

Really? Did it work before like me or did the error occur the first time you ran the terminal? By the way, yes please let me know if you made any process.

---

### Post by matbluvenger on 2012-02-23
Yeah, first time I tried installing it through Terminal and got the same error.

I did as such:
```
su
cd /sdcard/ubuntu
sh ubuntu.sh
```

The ubuntu directory is where my ubuntu .sh and image files are.

---

### Post by Delta1992 on 2012-02-23
> **matbluvenger said:**
> Yeah, first time I tried installing it through Terminal and got the same error.

I did as such:
```
su
cd /sdcard/ubuntu
sh ubuntu.sh
```

The ubuntu directory is where my ubuntu .sh and image files are.

When you were installing ubuntu, which image did you put into your ubuntu file? I started with the small image first, and it worked like a charm. I did this as only as a test to see if it worked out, which it did. Then i decide to replace the small image with the large. If i make progress with this error I will let you know too.

---

### Post by matbluvenger on 2012-02-23
Hmm, tried the small image this time and still no dice....

---

### Post by Delta1992 on 2012-02-23
> **matbluvenger said:**
> Hmm, tried the small image this time and still no dice....

I see. I send an email to the developer of the ubuntu installer guide, and he told me to try to reboot my system. This did not work for me, but you should try it becuase you never know unless you try it. So far, I am using Astro file manager and choose to view the cdcard files and the hidden ones but I am not seeing any files left behind from my first installation. Plus, I have been reading what the terminal writes out and found that the "/data/local/mnt" fails becuase it exists already. Perhaps this has something to do with the error. If you have the same error, that script in the terminal I quoted should be around right after you type "sh ubuntu.sh".

---

