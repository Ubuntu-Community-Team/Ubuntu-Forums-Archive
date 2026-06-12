---
title: "endian.h - file not found, broken packages"
date: 2015-01-25
forum: New to Ubuntu
---

### Post by Josh_Hopps on 2015-01-25
Hi guys!

I'm attempting to compile android source code on my xubuntu installation. I've done it a lot with no issues, until now. The build required me to update libstdc++.so.6, so first I used terminal, where it was already up to date. I then used Synaptic package manager to update most things I could find that contained the word libstdc++. Now, if I try to update libstdc++.so.6, this is what I get:

```
hopper@hopper:~$ sudo apt-get install libstdc++
[sudo] password for hopper: 
Reading package lists... Done
Building dependency tree       
Reading state information... Done
Note, selecting 'libstdc++6-4.7-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.8-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-powerpc-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-arm64-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.8-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-arm64-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-ppc64el-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-pic-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-doc' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-dev-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-pic-armhf-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-arm-none-eabi-newlib' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.9-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-dev' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-powerpc-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-pic-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-ppc64el-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-powerpc-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-pic-powerpc-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-dev-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-dev-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-ppc64el-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-pic-ppc64el-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-pic-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'pd-libstdcpp' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-pic-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++3.0-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.9-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-doc' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-dev-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armhf-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dev-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-pic-arm64-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-pic-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.8-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.8-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.9-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-dev-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.8-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-pic' for regex 'libstdc+'
Note, selecting 'libstdc++-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-armhf-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-pic-armhf-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armhf-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-pic-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++2.8-dev' for regex 'libstdc+'
Note, selecting 'libstdc++5-doc' for regex 'libstdc+'
Note, selecting 'libstdc++5-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.9-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-dev-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++2.10-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-pic-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-armel-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-pic-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5-3.3-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-pic-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.5-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-dev-arm64-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-pic-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-pic' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dbg' for regex 'libstdc+'
Note, selecting 'libstdc++-4.8-dev-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.9-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-dev-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++5' for regex 'libstdc+'
Note, selecting 'libstdc++6' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-dbg-ppc64el-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.0-dbg-arm64-cross' for regex 'libstdc+'
Note, selecting 'libstdc++2.9-glibc2.1-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.1-dbg-armhf-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.7-dev-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.4-dev' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-armel-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.2-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.3-doc' for regex 'libstdc+'
Note, selecting 'libstdc++6-4.6-pic' for regex 'libstdc+'
Note, selecting 'libstdc++-4.9-pic-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-dev-armhf-dcv1' for regex 'libstdc+'
Note, selecting 'libstdc++6-dbg-powerpc-cross' for regex 'libstdc+'
Note, selecting 'libstdc++6-arm64-cross' instead of 'libstdc++6-arm64-dcv1'
Note, selecting 'libstdc++6-armhf-cross' instead of 'libstdc++6-armhf-dcv1'
Note, selecting 'libstdc++6-powerpc-cross' instead of 'libstdc++6-powerpc-dcv1'
Note, selecting 'libstdc++6-ppc64el-cross' instead of 'libstdc++6-ppc64el-dcv1'
Note, selecting 'libstdc++6-4.7-dbg-armel-cross' instead of 'libstdc++6-dbg-armel-dcv1'
Note, selecting 'libstdc++6-4.7-dev-armel-cross' instead of 'libstdc++-dev-armel-cross'
Note, selecting 'libstdc++6-4.7-dev-armel-cross' instead of 'libstdc++-dev-armel-dcv1'
Note, selecting 'libstdc++6-4.7-dev-armel-cross' instead of 'libstdc++6-dev-armel-dcv1'
Note, selecting 'libstdc++6-4.7-dev-armhf-cross' instead of 'libstdc++6-dev-armhf-dcv1'
Note, selecting 'libstdc++6-4.7-pic-armel-cross' instead of 'libstdc++6-pic-armel-dcv1'
Note, selecting 'libstdc++6-4.7-pic-armhf-cross' instead of 'libstdc++6-pic-armhf-dcv1'
Note, selecting 'libstdc++6-armel-cross' instead of 'libstdc++6-armel-dcv1'
libstdc++-4.8-dev is already the newest version.
libstdc++-4.9-dev is already the newest version.
libstdc++-4.9-dev set to manually installed.
libstdc++6 is already the newest version.
Some packages could not be installed. This may mean that you have
requested an impossible situation or if you are using the unstable
distribution that some required packages have not yet been created
or been moved out of Incoming.
The following information may help to resolve the situation:


The following packages have unmet dependencies:
 libstdc++-4.8-doc : Conflicts: libstdc++6-4.4-doc but 4.4.7-8ubuntu1 is to be installed
                     Conflicts: libstdc++6-4.6-doc but 4.6.4-6ubuntu2 is to be installed
                     Conflicts: libstdc++6-4.7-doc but 4.7.4-2ubuntu1 is to be installed
 libstdc++-4.9-doc : Conflicts: libstdc++-4.8-doc but 4.8.3-12ubuntu3 is to be installed
                     Conflicts: libstdc++6-4.4-doc but 4.4.7-8ubuntu1 is to be installed
                     Conflicts: libstdc++6-4.6-doc but 4.6.4-6ubuntu2 is to be installed
                     Conflicts: libstdc++6-4.7-doc but 4.7.4-2ubuntu1 is to be installed
 libstdc++-4.9-pic : Depends: gcc-4.9-base (= 4.9.1-16ubuntu6) but 4.9.2-0ubuntu1~14.04 is to be installed
                     Depends: libstdc++-4.9-dev (= 4.9.1-16ubuntu6) but 4.9.2-0ubuntu1~14.04 is to be installed
 libstdc++6-4.4-dbg : Depends: libgcc1-dbg but it is not going to be installed
 libstdc++6-4.6-dbg : Depends: libgcc1-dbg but it is not going to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.7-8ubuntu1 is to be installed
 libstdc++6-4.6-doc : Conflicts: libstdc++6-4.4-doc but 4.4.7-8ubuntu1 is to be installed
 libstdc++6-4.7-dbg : Depends: libgcc1-dbg (>= 1:4.7.4-2ubuntu1) but it is not going to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.7-8ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.6-dbg but 4.6.4-6ubuntu2 is to be installed
 libstdc++6-4.7-doc : Conflicts: libstdc++6-4.4-doc but 4.4.7-8ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.6-doc but 4.6.4-6ubuntu2 is to be installed
 libstdc++6-4.8-dbg : Depends: libgcc1-dbg (>= 1:4.8.3-12ubuntu3) but it is not going to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.7-8ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.6-dbg but 4.6.4-6ubuntu2 is to be installed
                      Conflicts: libstdc++6-4.7-dbg but 4.7.4-2ubuntu1 is to be installed
 libstdc++6-4.8-dbg-armhf-cross : Conflicts: libstdc++6-4.7-dbg-armhf-cross but 4.7.4-2ubuntu1cross1.86 is to be installed
 libstdc++6-4.9-dbg : Depends: gcc-4.9-base (= 4.9.1-16ubuntu6) but 4.9.2-0ubuntu1~14.04 is to be installed
                      Depends: libgcc1-dbg (>= 1:4.9.1-16ubuntu6) but it is not going to be installed
                      Recommends: libstdc++-4.9-dev (= 4.9.1-16ubuntu6) but 4.9.2-0ubuntu1~14.04 is to be installed
                      Conflicts: libstdc++6-4.4-dbg but 4.4.7-8ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.6-dbg but 4.6.4-6ubuntu2 is to be installed
                      Conflicts: libstdc++6-4.7-dbg but 4.7.4-2ubuntu1 is to be installed
                      Conflicts: libstdc++6-4.8-dbg but 4.8.3-12ubuntu3 is to be installed
 libstdc++6-4.9-dbg-arm64-cross : Conflicts: libstdc++6-4.8-dbg-arm64-cross but 4.8.3-12ubuntu3cross0.12 is to be installed
 libstdc++6-4.9-dbg-armhf-cross : Conflicts: libstdc++6-4.7-dbg-armhf-cross but 4.7.4-2ubuntu1cross1.86 is to be installed
                                  Conflicts: libstdc++6-4.8-dbg-armhf-cross but 4.8.3-12ubuntu3cross0.13 is to be installed
 libstdc++6-4.9-dbg-powerpc-cross : Conflicts: libstdc++6-4.8-dbg-powerpc-cross but 4.8.3-12ubuntu3cross0.14 is to be installed
 libstdc++6-4.9-dbg-ppc64el-cross : Conflicts: libstdc++6-4.8-dbg-ppc64el-cross but 4.8.3-12ubuntu3cross0.5 is to be installed
E: Unable to correct problems, you have held broken packages.
hopper@hopper:~$ 



```

Which seems I have a huge number of broken packages. I think it's related to the next lot of errors: When I try to compile as I always have, I get this:

```
host C: libunwind_32 <= external/libunwind/src/mi/Gdestroy_addr_space.c
host C: libunwind_32 <= external/libunwind/src/mi/Gget_reg.c
host C: libunwind_32 <= external/libunwind/src/mi/Gset_reg.c
host C: libunwind_32 <= external/libunwind/src/mi/Gget_fpreg.c
host C: libunwind_32 <= external/libunwind/src/mi/Gset_fpreg.c
host C: libunwind_32 <= external/libunwind/src/mi/Gset_caching_policy.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lexpr.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lfde.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lparser.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lpe.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lstep_dwarf.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lfind_proc_info-lsb.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Lfind_unwind_table.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gexpr.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gfde.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gfind_proc_info-lsb.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gfind_unwind_table.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gparser.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gpe.c
host C: libunwind_32 <= external/libunwind/src/dwarf/Gstep_dwarf.c
host C: libunwind_32 <= external/libunwind/src/dwarf/global.c
host C: libunwind_32 <= external/libunwind/src/os-common.c
host C: libunwind_32 <= external/libunwind/src/os-linux.c
host C: libunwind_32 <= external/libunwind/src/Los-common.c
host C: libunwind_32 <= external/libunwind/src/x86/is_fpreg.c
host C: libunwind_32 <= external/libunwind/src/x86/regname.c
host C: libunwind_32 <= external/libunwind/src/x86/Gcreate_addr_space.c
host C: libunwind_32 <= external/libunwind/src/x86/Gget_proc_info.c
host C: libunwind_32 <= external/libunwind/src/x86/Gget_save_loc.c
host C: libunwind_32 <= external/libunwind/src/x86/Gglobal.c
host C: libunwind_32 <= external/libunwind/src/x86/Ginit.c
host C: libunwind_32 <= external/libunwind/src/x86/Ginit_local.c
host C: libunwind_32 <= external/libunwind/src/x86/Ginit_remote.c
host C: libunwind_32 <= external/libunwind/src/x86/Gregs.c
host C: libunwind_32 <= external/libunwind/src/x86/Gresume.c
host C: libunwind_32 <= external/libunwind/src/x86/Gstep.c
host C: libunwind_32 <= external/libunwind/src/x86/Lcreate_addr_space.c
host C: libunwind_32 <= external/libunwind/src/x86/Lget_proc_info.c
host C: libunwind_32 <= external/libunwind/src/x86/Lget_save_loc.c
host C: libunwind_32 <= external/libunwind/src/x86/Lglobal.c
host C: libunwind_32 <= external/libunwind/src/x86/Linit.c
host C: libunwind_32 <= external/libunwind/src/x86/Linit_local.c
host C: libunwind_32 <= external/libunwind/src/x86/Linit_remote.c
host C: libunwind_32 <= external/libunwind/src/x86/Lregs.c
host C: libunwind_32 <= external/libunwind/src/x86/Lresume.c
host C: libunwind_32 <= external/libunwind/src/x86/Lstep.c
host C: libunwind_32 <= external/libunwind/src/x86/Gos-linux.c
host C: libunwind_32 <= external/libunwind/src/x86/Los-linux.c
host C: libunwind_32 <= external/libunwind/src/elf32.c
host asm: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/x86_64/floatundixf.S
host asm: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/x86_64/floatundisf.S
host asm: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/x86_64/floatundidf.S
host C: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/absvdi2.c
host C: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/absvsi2.c
host C: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/absvti2.c
host C: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/adddf3.c
host C: libcompiler_rt_32 <= external/compiler-rt/lib/builtins/addsf3.c
In file included from In file included from external/compiler-rt/lib/builtins/absvsi2.c:15:
In file included from external/compiler-rt/lib/builtins/int_lib.h:57:
In file included from external/compiler-rt/lib/builtins/int_types.h:21external/compiler-rt/lib/builtins/absvdi2.c:15:
In file included from external/compiler-rt/lib/builtins/int_lib.h:
external/compiler-rt/lib/builtins/int_endianness.h:57:
:In file included from external/compiler-rt/lib/builtins/int_types.h:86:1021:
external/compiler-rt/lib/builtins/int_endianness.h: fatal error:86:: 'endian.h' file not found10: 
fatal error: 'endian.h' file not found
#include <endian.h>
#include <endian.h>
         ^         ^


11 error generated.
 error generated.
build/core/binary.mk:747: recipe for target '/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/absvdi2.o' failed
make: *** [/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/absvdi2.o] Error 1
make: *** Waiting for unfinished jobs....
build/core/binary.mk:747: recipe for target '/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/absvsi2.o' failed
make: *** [/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/absvsi2.o] Error 1
In file included from external/compiler-rt/lib/builtins/absvti2.c:15:
In file included from external/compiler-rt/lib/builtins/int_lib.h:57:
In file included from external/compiler-rt/lib/builtins/int_types.h:21:
external/compiler-rt/lib/builtins/int_endianness.h:86:10: fatal error: 'endian.h' file not found
#include <endian.h>
         ^
1 error generated.
build/core/binary.mk:747: recipe for target '/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/absvti2.o' failed
make: *** [/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/absvti2.o] Error 1
In file included from external/compiler-rt/lib/builtins/adddf3.c:16:
In file included from external/compiler-rt/lib/builtins/fp_add_impl.inc:15:
In file included from external/compiler-rt/lib/builtins/fp_lib.h:27:
In file included from external/compiler-rt/lib/builtins/int_lib.h:57:
In file included from external/compiler-rt/lib/builtins/int_types.h:21:
external/compiler-rt/lib/builtins/int_endianness.h:86:10: fatal error: 'endian.h' file not found
#include <endian.h>
         ^
1 error generated.
build/core/binary.mk:747: recipe for target '/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/adddf3.o' failed
make: *** [/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/adddf3.o] Error 1
In file included from external/compiler-rt/lib/builtins/addsf3.c:16:
In file included from external/compiler-rt/lib/builtins/fp_add_impl.inc:15:
In file included from external/compiler-rt/lib/builtins/fp_lib.h:27:
In file included from external/compiler-rt/lib/builtins/int_lib.h:57:
In file included from external/compiler-rt/lib/builtins/int_types.h:21:
external/compiler-rt/lib/builtins/int_endianness.h:86:10: fatal error: 'endian.h' file not found
#include <endian.h>
         ^
1 error generated.
build/core/binary.mk:747: recipe for target '/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/addsf3.o' failed
make: *** [/home/hopper/android/slimlp/out/host/linux-x86/obj32/STATIC_LIBRARIES/libcompiler_rt_intermediates/lib/builtins/addsf3.o] Error 1
make: *** wait: No child processes.  Stop.


real    7m7.026s
user    11m44.346s
sys    6m57.334s
hopper@hopper:~/android/slimlp$ 

```

I can't compile due to missing 'endian.h', and I have broken packages. I'm not a Linux guru, I just use it so that I can tweak with android. In saying that, to try and fix my issue, so far I've:

- used Synaptic package manager to 'fix broken packages' - doesn't seem to do anything
- update all software through built in software updater - some packages seem to error out due to 'ELF - wrong magic bytes', although it scrolls past too fast to read
- update from Xubuntu 14.04 to 14.10. This was successful but didn't fix my compilation error or broken packages, even though 45 packages were removed during installation.
- scour the internet for solutions to similar errors. I can't find anything that relates, a lot of the errors seem to be on MacOSX. 

Ideally, I'd like to fix the broken packages and compilation error from missing endian.h as I assume they're related. I'm posting in an ubuntu forum as the error isn't in the source code I'm compiling, but the packages and compiler itself. 

Thanks in advance!

---

### Post by GalaticStryder on 2015-02-06
Hello, have you figured this out? I have been facing the same error, with the same log, and every research drives me to MacOS forums. I'm on Mint 17 Rebecca.

---

### Post by Josh_Hopps on 2015-02-06
Hi! 

I'm sorry to say, I never figured it out. I had to format my Linux partition and start over. I did try re-installing xubuntu over its existing installation without formatting, but that didn't work. So I had to start again from a fresh partition  :( I wish you all the best for your situation though.

---

