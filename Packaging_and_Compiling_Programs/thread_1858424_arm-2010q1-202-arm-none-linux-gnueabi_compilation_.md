---
title: "arm-2010q1-202-arm-none-linux-gnueabi compilation and installation on ubuntu"
date: 2011-10-12
forum: Packaging and Compiling Programs
---

### Post by chandra_bhanu on 2011-10-12
Please, do tell me the procedure to compile and install the GNU arm Toolchain "arm-2010q1-202-arm-none-linux-gnueabi" which I downloaded from codesourcey website. 
I couldnot find the deb packages.

---

### Post by SevenMachines on 2011-10-13
Are you using ubuntu maverick, natty or oneiric? In which case you want
```
 $ sudo apt-get install gcc-arm-linux-gnueabi g++-arm-linux-gnueabi
```I've used codesourcey (now renamed) stuff a while back, its commercially leaning though, although you can download
[https://sourcery.mentor.com/sgpp/lite/arm/portal/release1802](https://sourcery.mentor.com/sgpp/lite/arm/portal/release1802) for the moment, it would be the least favoured option in my opinion though. 

Depending on what you're trying to do you could also set up a qemu arm environment, see
[https://wiki.ubuntu.com/ARM/BuildArmPackages](https://wiki.ubuntu.com/ARM/BuildArmPackages). I've used this myself a few months back for testing armel builds, I *think* I used that wiki for it. Setting up a pbuilder arm environment also works if you're looking to test build arm packages. It's been several months since I've done either qemubuilder or pbuilder stuff for armel so I'm not entirely sure what the state of these methods and guides are.

---

### Post by chandra_bhanu on 2011-10-13
> **SevenMachines said:**
> Are you using ubuntu maverick, natty or oneiric? In which case you want
```
 $ sudo apt-get install gcc-arm-linux-gnueabi g++-arm-linux-gnueabi
```I've used codesourcey (now renamed) stuff a while back, its commercially leaning though, although you can download
[https://sourcery.mentor.com/sgpp/lite/arm/portal/release1802](https://sourcery.mentor.com/sgpp/lite/arm/portal/release1802) for the moment, it would be the least favoured option in my opinion though. 

Depending on what you're trying to do you could also set up a qemu arm environment, see
[https://wiki.ubuntu.com/ARM/BuildArmPackages](https://wiki.ubuntu.com/ARM/BuildArmPackages). I've used this myself a few months back for testing armel builds, I *think* I used that wiki for it. Setting up a pbuilder arm environment also works if you're looking to test build arm packages. It's been several months since I've done either qemubuilder or pbuilder stuff for armel so I'm not entirely sure what the state of these methods and guides are.
Thanks for all the information.
Actually I downloaded the arm-2010q1-202-arm-none-linux-gnueabi.src.tar.bz2. So my question was how do I compile and install this. Any documentation etc. may help.

---

### Post by SevenMachines on 2011-10-13
If you're absolutely set on codesourcey and not repository...
To compile from source seems to be difficult if not impossible, you can give
```
$ chmod 755 arm-2011.03-42-arm-none-eabi.sh
$ ./arm-2011.03-42-arm-none-eabi.sh
```in the untarred  source directory, the version name will be different but the script still exists.
But note the warning, building yourself instead of using  the installer may well be impossible, or will at least require manual editing of the build script and general messing about. A warning to get gnueabi from  somewhere else I'd say :*)

> # This file contains the complete sequence of commands
# CodeSourcery used to build this version of Sourcery G++.
# 
# For each free or open-source component of Sourcery G++, the
# source code provided includes all of the configuration
# scripts and makefiles for that component, including any and
# all modifications made by CodeSourcery.  From this list of
# commands, you can see every configuration option used by
# CodeSourcery during the build process.
# 
# This file is provided as a guideline for users who wish to
# modify and rebuild a free or open-source component of
# Sourcery G++ from source. For a number of reasons, though,
# you may not be able to successfully run this script directly
# on your system. Certain aspects of the CodeSourcery build
# environment (such as directory names) are included in these
# commands. CodeSourcery uses Canadian cross compilers so you
# may need to modify various configuration options and paths
# if you are building natively. This sequence of commands
# includes those used to build proprietary components of
# Sourcery G++ for which source code is not provided.
# 
# Please note that Sourcery G++ support covers only your use
# of the original, validated binaries provided as part of
# Sourcery G++ -- and specifically does not cover either the
# process of rebuilding a component or the use of any binaries
# you may build.  In addition, if you rebuild any component,
# you must not use the --with-pkgversion and --with-bugurl
# configuration options that embed CodeSourcery trademarks in
# the resulting binary; see the "CodeSourcery Trademarks"
# section in the Sourcery G++ Software License Agreement.

There are set instructions for using the installer which seem to work
[http://fun-tech.se/stm32/CodeSourceryInstall/index.php](http://fun-tech.se/stm32/CodeSourceryInstall/index.php)

Note, if you want the latest version you should be able to just change the 
```
wget [http://www.codesourcery.com/sgpp/lite/arm/portal/package6495/public/arm-none-eabi/arm-2010q1-188-arm-none-eabi.bin](http://www.codesourcery.com/sgpp/lite/arm/portal/package6495/public/arm-none-eabi/arm-2010q1-188-arm-none-eabi.bin)
```to
 ```
wget [https://sourcery.mentor.com/sgpp/lite/arm/portal/package8736/public/arm-none-eabi/arm-2011.03-42-arm-none-eabi.bin](https://sourcery.mentor.com/sgpp/lite/arm/portal/package8736/public/arm-none-eabi/arm-2011.03-42-arm-none-eabi.bin)
```

In short, if you must use codesourcey, you're very likely going to *have* to use the pre built binary installer. But to be honest, I'd be avoiding it like the plague! Good luck though :)

---

