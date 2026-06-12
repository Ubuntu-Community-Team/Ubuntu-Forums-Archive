---
title: "I don't know what's wrong with my computer."
date: 2015-09-19
forum: New to Ubuntu
---

### Post by tisho2 on 2015-09-19
Ok, I don't know what's wrong with my computer. I ran that command and this is what I got: > trt@trt-HP:~$ dpkg -l 'linux-*' | sed  '/^ii/!d;/'"$(uname -r | sed "s/\(.*\)-\([^0-9]\+\)/\1/")"'/d;s/^[^ ]*  [^ ]* \([^ ]*\).*/\1/;/[0-9]/!d' | xargs sudo apt-get -y purgeReading package lists... Done
Building dependency tree       
Reading state information... Done
E: Unable to locate package 3.13.0-37.64
E: Couldn't find any package by regex '3.13.0-37.64'
E: Unable to locate package 3.16.0-24.32
E: Couldn't find any package by regex '3.16.0-24.32'
E: Unable to locate package 3.16.0-25.33
E: Couldn't find any package by regex '3.16.0-25.33'

---

### Post by Bucky Ball on 2015-09-19
*Thread moved to **New to Ubuntu**.*

... and post moved from [here]("http://ubuntuforums.org/showthread.php?t=2283287") to own thread to improve chances of support.

Welcome. Please run these commands one after the other hitting enter between each. Post any and all errors:

```

sudo apt-get clean
sudo apt-get autoremove
sudo apt-get update
sudo apt-get upgrade
sudo apt-get dist-upgrade

```	

Thanks. Post errors back here between code tags (see last link in my signature). Also, which release of Ubuntu are you using? The one in question on the thread you posted on was 14.10 which is no longer supported. If you are using 14.10, please upgrade to a supported release, 14.04 LTS or 15.04.

---

### Post by Sweet_Baby_Jamie on 2015-09-19
I always recommend and use the Long Term Support versions.  A large number of the complaints about updates not working are because the user is using a previous, unsupported version.

---

### Post by monkeybrain20122 on 2015-09-19
> **Sweet_Baby_Jamie said:**
> I always recommend and use the Long Term Support versions.  A large number of the complaints about updates not working are because the user is using a previous, unsupported version.

No, it has nothing to do with LTS or not. In this instance OP copied and pasted a long command that contain a lot regular expressions without knowing what it does. It is always a bad idea to copy and paste these very long and cryptic commands without understanding. They may work only for some special configurations or particular Ubuntu releases. Without knowing what they do you can't make modifications if you have to.

Purging old kernels can be done easily with synaptic (or better, not to make a /boot partition when install, it has no use for most users but since it is tiny old kernels got accumulated and eventually will run out of space)

---

