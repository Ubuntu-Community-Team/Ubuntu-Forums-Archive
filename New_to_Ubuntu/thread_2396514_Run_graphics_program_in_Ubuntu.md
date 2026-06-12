---
title: "Run graphics program in Ubuntu"
date: 2018-07-17
forum: New to Ubuntu
---

### Post by pailan on 2018-07-17
To All

I am trying to [FONT=arial]Run graphics program in Ubuntu, so I am trying to install 

[/FONT]sudo apt-get install libsdl-image1.2 libsdl-image1.2-dev guile-1.8 \
  guile-1.8-dev libsdl1.2debian libart-2.0-dev libaudiofile-dev \
  libesd0-dev libdirectfb-dev libdirectfb-extra libfreetype6-dev \
  libxext-dev x11proto-xext-dev libfreetype6 libaa1 libaa1-dev \
  libslang2-dev libasound2 libasound2-dev

getting errors

1. failed to fetch [http://in.archive](http://in.archive).....

2. hash sum mismatched

3. bad headers line bad headers data

4. file not found

Please help.

---

### Post by TheFu on 2018-07-17
Dependencies should be handled automatically.  

Rather than describing the output, show the actual output.  Please use *code tags*.
Also, start by ensuring the OS is fully patched before trying to install new programs.

The Guile project says: > Try installing Guile from your system packages first. It is likely that Guile is already packaged for the operating system you are using.   I see v2 of guile in my repos. Is there a reason you don't want the newer release?

When I force v1.8, I see:
```
$ sudo apt install guile-1.8
Reading package lists... Done
Building dependency tree       
Reading state information... Done
The following additional packages will be installed:
  guile-1.8-libs
Suggested packages:
  guile-1.8-doc
The following NEW packages will be installed:
  guile-1.8 guile-1.8-libs
0 upgraded, 2 newly installed, 0 to remove and 0 not upgraded.
Need to get 609 kB of archives.
After this operation, 2,707 kB of additional disk space will be used.
Do you want to continue? [Y/n] 

```
Looks like it would install fine, if I continue.

Welcome to the forums.

---

