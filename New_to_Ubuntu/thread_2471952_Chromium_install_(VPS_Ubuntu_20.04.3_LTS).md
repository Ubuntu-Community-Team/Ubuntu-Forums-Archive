---
title: "Chromium install (VPS: Ubuntu 20.04.3 LTS)"
date: 2022-02-14
forum: New to Ubuntu
---

### Post by dantsi on 2022-02-14
Hello,

I'm sorry, I speak a little English.

My new VPS:

```
hostnamectl
Virtualization: openvz
Operating System: Ubuntu 20.04.3 LTS
Kernel: Linux 5.4.0
Architecture: x86-64
```

I try:

```
apt install chromium-browser
Reading package lists... Done
Building dependency tree
Reading state information... Done
The following NEW packages will be installed:
  chromium-browser
0 upgraded, 1 newly installed, 0 to remove and 37 not upgraded.
Need to get 0 B/48.3 kB of archives.
After this operation, 164 kB of additional disk space will be used.
Preconfiguring packages ...
(Reading database ... 27527 files and directories currently installed.)
Preparing to unpack .../chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd64.deb ...
=> Installing the chromium snap
==> Checking connectivity with the snap store
==> Installing the chromium snap
error: system does not fully support snapd: cannot mount squashfs image using "squashfs": mount:
       /tmp/sanity-mountpoint-002613914: mount failed: Operation not permitted.
dpkg: error processing archive /var/cache/apt/archives/chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd64.deb (--unpack):
 new chromium-browser package pre-installation script subprocess returned error exit status 1
Errors were encountered while processing:
 /var/cache/apt/archives/chromium-browser_1%3a85.0.4183.83-0ubuntu0.20.04.2_amd64.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
```


What is the problem?

I would like use run this command:

```
chromium  --headless --disable-gpu --dump-dom https://tezfiles.com
```

I tried with Lynx, but the Lynx not supported the JavaScript. I need text browser, I would like open a tezfiles.com and need the cookies.

---

### Post by ActionParsnip on 2022-02-14
Prefix with sudo
```

sudo apt install chromium-browser

```

Should do it

---

### Post by cerdtmann on 2022-09-23
Could you solve it ?
I get the same error on the same system, but i already try it with 
sudo apt install chromium-browser

---

### Post by ajgreeny on 2022-09-23
Usually there is no chromium-browser .deb package in the Ubuntu repos and the only way to get a chromium-browser package to install as a .deb package is to enable a PPA which you do not mention at all.

Where did you get the chromium-browser from, ie, which PPA, as by default in 20.04 chromium is installed as a snap even if you use command ***sudo apt install chromium***

---

