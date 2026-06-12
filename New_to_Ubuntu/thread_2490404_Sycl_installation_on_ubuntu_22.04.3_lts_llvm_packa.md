---
title: "Sycl installation on ubuntu 22.04.3 lts llvm package installation"
date: 2023-09-02
forum: New to Ubuntu
---

### Post by bryancantero on 2023-09-02
Hi guys, 

I'm trying to install the install-llvm.sh package on Ubuntu, this is one of a 5 series of packages to run Gromacs under a RDNA AMD GPU over Gromacs, for molecular dynamics,

1st. I tried with sudo sh install-llvm.sh getting, 

CMake Error at cmake/modules/CheckCompilerVersion.cmake:97 (message):
  libstdc++ version must be at least 5.1.
Call Stack (most recent call first):
  cmake/config-ix.cmake:13 (include)
  CMakeLists.txt:655 (include)

2nd. When using sudo sh install-llvm.sh I get install-llvm.sh: 16: read: Illegal option -n, now I'm trying with bash instead of sh after "install", like "install bash ...", and is letting me run the commands.

Can anyone help me with the 1st item on the list?

---

### Post by raja.genupula on 2023-09-05
Did you tried installing `[FONT=system]libstdc++6`
[/FONT]```
[FONT=system]sudo apt-get install libstdc++6[/FONT]
```[FONT=&amp][SIZE=2][FONT=system]
[/FONT][/SIZE][/FONT]

---

### Post by mIk3_08 on 2023-09-06
The error message "libstdc++ version must be at least 5.1" means that the version of libstdc++ that is installed on your system is not new enough to support the build of LLVM. libstdc++ is a C++ standard library, and it provides the basic building blocks for C++ programs. The version 5.1 of libstdc++ was released in 2010 and it's quite old.

There are a few things you can do to fix this error:

Update your system's libstdc++ package. You can do this by running the following command:
sudo apt update && sudo apt upgrade
Install a newer version of libstdc++ manually. You can download the latest version of libstdc++ from the GNU website.

Use a different C++ compiler that does not require a newer version of libstdc++. For example, you could use the Clang compiler.

I would recommend trying to update your system's libstdc++ package first. If that does not work, then you can try installing a newer version of libstdc++ manually. If you are still having problems, then you can try using a different C++ compiler.

As for the second item on your list, the error message "install-llvm.sh: 16: read: Illegal option -n" means that the install-llvm.sh script does not understand the option -n. This option is not documented in the script, so it is likely a typo. You can try removing the option -n from the command line and see if that fixes the problem.

---

