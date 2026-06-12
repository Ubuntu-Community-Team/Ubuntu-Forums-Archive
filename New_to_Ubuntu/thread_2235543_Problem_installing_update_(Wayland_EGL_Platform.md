---
title: "Problem installing update (Wayland EGL Platform"
date: 2014-07-21
forum: New to Ubuntu
---

### Post by dtlongrifles on 2014-07-21
After installing updates today I got a message saying that my Hardware would lose support in August, giving me the option to upgrade now which I selected. I got an error message before upgrade was completed which gave me new instructions to follow. My experience level is very low but I followed the instructions, Following are screen shots (I hope) of what happened:

---

### Post by grahammechanical on 2014-07-21
An hour or so ago I put in an install of Ubuntu 12.04.4 specifically to test this offer of a hardware upgrade as some have been reporting that running the update caused problems. In my case everthing went fine. But then again I was doing this on a default installation.

The update to the Wayland EGl platform was that part of the hardware upgrade or was it offered afterwards? You need to run that apt-get install -f command using sudo.

```
sudo apt-get install -f
```

Have you tried it that way? And are you using third party repositories - PPAs? They should be disabled once we have used them to install the software.

Regards.

---

### Post by dtlongrifles on 2014-07-22
I don't know what this sudo is and I don't know what third party repositories are. It's taken me 20 minutes to post this because Firefox keeps crashing and when I try Chromium I get "Aw Snap" crashes constantly.
 I tried adding "sudo" to command in terminal and got this: 
```
bmacbn@bmacbn-Latitude-D520:~$ sudo apt-get install -f[sudo] password for bmacbn: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Correcting dependencies... Done
The following packages were automatically installed and are no longer required:
  thunderbird-globalmenu language-pack-kde-en gir1.2-ubuntuoneui-3.0
  language-pack-kde-en-base kde-l10n-engb libubuntuoneui-3.0-1
  linux-headers-3.5.0-23 linux-headers-3.5.0-23-generic amarok-help-en
Use 'apt-get autoremove' to remove them.
The following extra packages will be installed:
  libwayland-egl1-mesa-lts-trusty
The following NEW packages will be installed:
  libwayland-egl1-mesa-lts-trusty
0 upgraded, 1 newly installed, 0 to remove and 0 not upgraded.
1 not fully installed or removed.
Need to get 0 B/6,508 B of archives.
After this operation, 92.2 kB of additional disk space will be used.
Do you want to continue [Y/n]? y
(Reading database ... 313212 files and directories currently installed.)
Unpacking libwayland-egl1-mesa-lts-trusty (from .../libwayland-egl1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_i386.deb) ...
xz: (stdin): Compressed data is corrupt
dpkg-deb (subprocess): subprocess data returned error exit status 1
dpkg-deb: error: subprocess <decompress> returned error exit status 2
dpkg: error processing /var/cache/apt/archives/libwayland-egl1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_i386.deb (--unpack):
 short read on buffer copy for backend dpkg-deb during `./usr/share/doc/libwayland-egl1-mesa-lts-trusty/copyright'
No apport report written because MaxReports is reached already
                                                              Errors were encountered while processing:
 /var/cache/apt/archives/libwayland-egl1-mesa-lts-trusty_10.1.3-0ubuntu0.1~precise1_i386.deb
E: Sub-process /usr/bin/dpkg returned an error code (1)
bmacbn@bmacbn-Latitude-D520:~$
```

---

### Post by dtlongrifles on 2014-07-22
When I open up the Ubuntu Software Center I get a message saying that  nothing can be added or removed until the package manager is repaired  and it asks if I want to repair it now. When I click to repair, it tries  for about 30 seconds and then I got this message:

---

