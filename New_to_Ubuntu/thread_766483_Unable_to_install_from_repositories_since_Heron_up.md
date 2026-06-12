---
title: "Unable to install from repositories since Heron upgrade"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by Her Ghost on 2008-04-25
I upgraded to Hardy Heron last night and everything went well.

Now though, when I try to install _any_ application from the Add/Remove programs menu, I get this error:

E: /var/cache/apt/archives/libhiglayout-java_1.0-2ubuntu1_all.deb: files list file for package `transmission-common' is missing final newline

Does anyone know how to fix this?

Thanks!


edit:

more detailed error

[[IMG]http://img174.imageshack.us/img174/2508/screenshotchangesapplienm0.th.png[/IMG]](http://img174.imageshack.us/my.php?image=screenshotchangesapplienm0.png)

---

### Post by SunnyRabbiera on 2008-04-25
well this could be in part to the server overload, with everyone wanting to try hardy it is causing issues with the repositories.

---

### Post by PmDematagoda on 2008-04-25
Do:-
```
sudo apt-get clean
```
and then:-
```
sudo apt-get install -f
```
followed by:- 
```
sudo dpkg --configure -a
```

See if the error persists after it is done.

---

### Post by Her Ghost on 2008-04-25
> **PmDematagoda said:**
> Do:-
```
sudo apt-get clean
```
and then:-
```
sudo apt-get install -f
```
followed by:- 
```
sudo dpkg --configure -a
```

See if the error persists after it is done.

hi, thanks for the advice.  after these steps I get the same error message...

---

### Post by Tatty on 2008-04-25
It might be worth checking your ram for any failures.  Reboot then at grub it should give you an option to do a memtest.

---

### Post by Her Ghost on 2008-04-25
more detail:

**sudo apt-get clean**

returns no result.

**sudo apt-get install -f**

returns:```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libstdc++5 gnome-bin libgtk1.2 libgnome32 gnome-libs-data
  libart2 libgnorbagtk0 gdk-imlib1 python-qt3 libsdl-ttf2.0-0 libgif4
  python-sip4 libgnomeui32 libxml1 libdb3 libgtk1.2-common imlib-base
  python-setuptools liborbit0 gdk-imlib11 python-pkg-resources
  libgnomesupport0 gcc-3.3-base libgnorba27 libsmpeg0 libungif4g
Use 'apt-get autoremove' to remove them.
0 upgraded, 0 newly installed, 0 to remove and 0 not upgraded.

```
**sudo dpkg --configure -a**

returns no result


if, as apt-get install -f suggests, I run apt-get autoremove, this happens:
```

Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libstdc++5 gnome-bin libgtk1.2 libgnome32 gnome-libs-data
  libart2 libgnorbagtk0 gdk-imlib1 python-qt3 libsdl-ttf2.0-0 libgif4
  python-sip4 libgnomeui32 libxml1 libdb3 libgtk1.2-common imlib-base
  python-setuptools liborbit0 gdk-imlib11 python-pkg-resources
  libgnomesupport0 gcc-3.3-base libgnorba27 libsmpeg0 libungif4g
The following packages will be REMOVED
  gcc-3.3-base gdk-imlib1 gdk-imlib11 gnome-bin gnome-libs-data imlib-base
  libart2 libdb3 libgif4 libglib1.2ldbl libgnome32 libgnomesupport0
  libgnomeui32 libgnorba27 libgnorbagtk0 libgtk1.2 libgtk1.2-common liborbit0
  libsdl-ttf2.0-0 libsmpeg0 libstdc++5 libungif4g libxml1 python-pkg-resources
  python-qt3 python-setuptools python-sip4
0 upgraded, 0 newly installed, 27 to remove and 0 not upgraded.
After this operation, 32.8MB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing libstdc++5 (--remove):
 files list file for package `transmission-common' is missing final newline
dpkg: ../../src/packages.c:252: process_queue: Assertion `!queuelen' failed.
E: Sub-process /usr/bin/dpkg exited unexpectedly 
```

---

### Post by Her Ghost on 2008-04-25
> **Tatty said:**
> It might be worth checking your ram for any failures.  Reboot then at grub it should give you an option to do a memtest.

I will try that now - thanks

---

### Post by PmDematagoda on 2008-04-25
Could you post the output of:-
```
cat /var/lib/dpkg/available | grep transmission-common
```

---

### Post by Her Ghost on 2008-04-25
> **PmDematagoda said:**
> Could you post the output of:-
```
cat /var/lib/dpkg/available | grep transmission-common
```

memtest was fine.

output from above command:

```

Package: transmission-common
Depends: libatk1.0-0 (>= 1.20.0), libc6 (>= 2.7-1), libcairo2 (>= 1.5.14), libfontconfig1 (>= 2.4.0), libfreetype6 (>= 2.3.5), libglib2.0-0 (>= 2.16.0), libgtk2.0-0 (>= 2.12.0), libpango1.0-0 (>= 1.20.0), libpixman-1-0 (>= 0.9.4-2), libpng12-0 (>= 1.2.13-4), libssl0.9.8 (>= 0.9.8f-1), libx11-6, libxrender1, transmission-common (= 1.06-0ubuntu4), zlib1g (>= 1:1.2.3.3.dfsg-1)

```

---

### Post by zvacet on 2008-04-25
Did you in synaptic mark for install transmission or transmission-common?if you selected transmission-common then delete it from synaptic and install package transmission.If you alleady did that and still have problems then try 

```
sudo apt-get install  libatk1.0-0 libc6 libcairo2 libfontconfig1 libfreetype6 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libpixman-1-0 libpng12-0 libssl0.9.8 libx11-6 libxrender1 transmission-common  zlib1g
```

---

### Post by tom56 on 2008-04-25
As above, the servers are overloaded at the moment. I expect a sudo apt-get update will fix your problem once the servers are back to normal.

---

### Post by Her Ghost on 2008-04-25
> **zvacet said:**
> Did you in synaptic mark for install transmission or transmission-common?if you selected transmission-common then delete it from synaptic and install package transmission.If you alleady did that and still have problems then try 

```
sudo apt-get install  libatk1.0-0 libc6 libcairo2 libfontconfig1 libfreetype6 libglib2.0-0 libgtk2.0-0 libpango1.0-0 libpixman-1-0 libpng12-0 libssl0.9.8 libx11-6 libxrender1 transmission-common  zlib1g
```

I think the problem lies in the actual transmission installation, like you said.  The problem that I have is that trying to remove transmission through either synaptics, apt-get or dpkg returns an error that I can't get past.

The error is that "transmission-common" is missing final new line - I don't really know what that means!

Is there a way of forcing an uninstallation because it seems that this package being on my system is ruining everything!

---

### Post by Her Ghost on 2008-04-25
does anyone know how to force the uninstallation of a piece of software?

in this case transmission-control, which was installed as part of the Heron upgrade appears to be corrupt and it is preventing all apt-get installations.

if there is a way of forcing an uninstall is this likely to create problems for other packages and dependencies?  does anyone have any general advice about this?

thanks!

---

### Post by zvacet on 2008-04-25
```
sudo dpkg --remove --force-remove-reinstreq package_name
```

---

### Post by Her Ghost on 2008-04-25
```
sudo dpkg --remove --force-remove-reinstreq transmission-common
dpkg: dependency problems prevent removal of transmission-common:
 transmission-gtk depends on transmission-common (= 1.06-0ubuntu4).
dpkg: error processing transmission-common (--remove):
 dependency problems - not removing
Errors were encountered while processing:
 transmission-common

```


grrrr!

---

### Post by xhero0 on 2008-04-25
Thanx for the help!

it worked for me!

joe

---

### Post by Her Ghost on 2008-04-26
does anyone else know how I could solve this problem?

I can't perform any installations with apt-get because transmission-common appears to be corrupt.  This also means that I can't remove transmission-common!

---

### Post by zvacet on 2008-04-26
Try to remove transmission-gtk and then transmossion-common.

---

### Post by Her Ghost on 2008-04-26
> **zvacet said:**
> Try to remove transmission-gtk and then transmossion-common.

no joy - looks like the error with transmission-common is stopping ALL apt-get commands.

```

 sudo apt-get remove transmission-gtk
[sudo] password for herghost: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following packages were automatically installed and are no longer required:
  libglib1.2ldbl libstdc++5 gnome-bin libgtk1.2 libgnome32 gnome-libs-data
  libart2 libgnorbagtk0 gdk-imlib1 python-qt3 libsdl-ttf2.0-0 libgif4
  python-sip4 libgnomeui32 libxml1 libdb3 libgtk1.2-common imlib-base
  python-setuptools liborbit0 gdk-imlib11 python-pkg-resources
  libgnomesupport0 gcc-3.3-base libgnorba27 libsmpeg0 libungif4g
Use 'apt-get autoremove' to remove them.
The following packages will be REMOVED
  transmission-gtk
0 upgraded, 0 newly installed, 1 to remove and 0 not upgraded.
After this operation, 946kB disk space will be freed.
Do you want to continue [Y/n]? y
(Reading database ... dpkg: error processing transmission-gtk (--remove):
 files list file for package `transmission-common' is missing final newline
Errors were encountered while processing:
 transmission-gtk
Processing was halted because there were too many errors.
E: Sub-process /usr/bin/dpkg returned an error code (1)


```

---

### Post by Her Ghost on 2008-04-26
thanks to "ompaul" in the ubuntu IRC, the solution is detailed here:

[https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html](https://lists.ubuntu.com/archives/ubuntu-users/2007-January/104520.html)

in brief:

performing the steps:
a) cd /var/lib/dpkg
(all other commands from within this directory)

1) sudo mv info info.bak
2) sudo mkdir info
3) sudo apt-get --reinstall install package_name
4) sudo mv info/* info.bak/
5) sudo rm -rf info
6) sudo mv info.bak info

I had to perform this several times for various package_name files.

It appears that my problem was that the installation didn't complete as successfully as I thought and several files were corrupt.

Each time I stepped through these instructions I tried to install anything through apt-get install package_name (for example, "freecol") and then the error message that popped up told me the name of the package that was corrupt.  Replacing package_name in step 3 with the name of the corrupt package fixed it.

hope this helps anyone else who is having this problem.

herghost.

(p.s. if anyone knows how to change the title to include "solved" please let me know!)

---

### Post by zvacet on 2008-04-27
@ [B]Her Ghost
[/B]
> p.s. if anyone knows how to change the title to include "solved" please let me know!


**Thread tools>mark as solved**.You can do that if you started thread.

---

