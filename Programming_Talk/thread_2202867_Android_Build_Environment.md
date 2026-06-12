---
title: "Android Build Environment"
date: 2014-01-31
forum: Programming Talk
---

### Post by shahin on 2014-01-31
Greetings-
I am looking for procedures for downloading the source for the Android. I tried to follow the procedures at [http://source.android.com/source/initializing.html]("http://source.android.com/source/initializing.html") to build an Ubuntu development environment for the Android platform. I installed Ubuntu 10.04 as a VM on VMware workstation. But I had some trouble with the section of the Android Source procedures: setting up cache. I put in the command "export USE_CCACHE=1", but not the other two commands they suggested. Someone online stated that they are only required if you are on NFS. I think I should not have put in the export statement. I downloaded the source just fine. But I am stuck at the building stage; when I issue the command "source build/envsetup.sh" I get "no such file directory ...". This community is always very friendly, and they are known ( I mean Ubuntu Forums ) for helpful advice. I wonder if there are procedures that may be a little more detailed? My other question is if I can salvage what I have done, or should I just rebuild this using Ubuntu 12.04. I am on 10.04 right now. Thanks in Advance. 
P.S. I have also attached the result of debug-all when I run avd of a Kitkat api.

---

### Post by TheFu on 2014-01-31
[https://wiki.ubuntu.com/Releases](https://wiki.ubuntu.com/Releases) says that 10.04 desktop support ended last May. I wouldn't touch anything on that release.

Those instructions seem extremely out of date ... a few years if they are still referencing 10.04.

I setup an Android development environment a few years ago. It required Eclipse and there were extensions to get everything working together "just so." I wasn't enough of a java dev to stick with it - plus my Core i5 machine only had 8G of RAM, which wasn't enough CPU or RAM. I never built Android, just a few trivial apps. Still, my machine was W-A-Y under powered.  Everything was slow. I can't imagine doing this inside a VM - ok - actually I can, since I do almost everything inside a VM these days.

If you enable the CCACHE, but don't tell it where to put the files ... that seems like a bad idea to me. Having a correct environment is critical.

So you are stuck on "**repo**"?  That was NOT part of the installation I did.  So using git is too complex for Android developers? Scary. I find git very easy to use and understand.

I'm not seeing any attachments to your post - and I will not look at images.

So ... I probably haven't helped at all. To get better help, 
* use "Adv Reply"
* copy/paste the commands AND output into "code" tags in the forums. Seeing the exact command and output is key.

Do you really need to rebuild android, the OS?  I never did.  Have you setup an Android app environment already?  To create Android apps, you don't need all the android source or need to build android [https://developer.android.com/training/basics/firstapp/index.html](https://developer.android.com/training/basics/firstapp/index.html) explains.

---

### Post by shahin on 2014-02-01
@TheFu
I hear you about the resource limitations for the VM. I have 4G of ram and a i3dual core machine, so it seems to run ok. I allocated about 2G to the VM. Let me just say I am not a programmer by trade; I am sure Android developers are very talented. I have however setup the andorid development on a windows machine a number of times. I need to get this going on Linux because I need a functionality that needs modifying the source with a patch. My plan is to then run it on the emulator. I have run a number of sample apps for Android. I even played around with the RPC-like functions and did make some progress. My main problem right now is that I don't know which directory to issue the "source build/envsetup.sh" command from. I don't know what "build" means. I don't have this specific directory, and if it is a generic name for one's build environment, I have tried running the script from various directories with no luck. I thought it may be the directory I have the andoid sdk and eclipse, but I can not run envsetup.sh from anywhere. Is it a script that I need to download from somewhere? The procedures don't say anything about that or maybe I missed it. I don't know. I kind a know where the Android sources I downloaded are, since I know the master branch I downloaded from Git is about 8G. I have attached a script session of my attempt in finding the right directory. Here is an output of my session:
[INDENT]sansari@ubuntu:~$ source build/envsetup.sh
bash: build/envsetup.sh: No such file or directory
sansari@ubuntu:~$ ls
Desktop  Development  Documents  Downloads  examples.desktop  Music  Pictures  Public  T
emplates  typescript  Videos  WORKING_DIRECTORY  workspace
sansari@ubuntu:~$ cd WORKING_DIRECTORY/
sansari@ubuntu:~/WORKING_DIRECTORY$ ls
git-1.8.5.3  git-1.8.5.3.tar.gz  git-1.9.rc1
sansari@ubuntu:~/WORKING_DIRECTORY$ cd git-1.8.5.3/
sansari@ubuntu:~/WORKING_DIRECTORY/git-1.8.5.3$ cd ..
sansari@ubuntu:~/WORKING_DIRECTORY$ ls -al
total 4716
drwxr-xr-x  5 root    root       4096 2014-01-29 08:34 .
drwxr-xr-x 31 sansari sansari    4096 2014-02-01 07:48 ..
drwxrwxr-x 20 root    root      28672 2014-01-29 08:38 git-1.8.5.3
-rw-r--r--  1 sansari sansari 4757215 2014-01-29 08:32 git-1.8.5.3.tar.gz
drwxrwxr-x 20 root    root      24576 2014-01-29 08:26 git-1.9.rc1
drwxr-xr-x  6 root    root       4096 2014-01-29 08:45 .repo
sansari@ubuntu:~/WORKING_DIRECTORY$ cd .repo/
sansari@ubuntu:~/WORKING_DIRECTORY/.repo$ ls
manifests  manifests.git  manifest.xml  projects  repo
sansari@ubuntu:~/WORKING_DIRECTORY/.repo$ source build/envsetup.sh
bash: build/envsetup.sh: No such file or directory
sansari@ubuntu:~/WORKING_DIRECTORY/.repo$ cd repo/
sansari@ubuntu:~/WORKING_DIRECTORY/.repo/repo$ ls
color.py     COPYING     error.py         git_config.py   git_ssh   manifest_xml.py   progress.py   pyversion.py   subcmds             trace.pyc
color.pyc    docs        error.pyc        git_config.pyc  hooks     manifest_xml.pyc  progress.pyc  pyversion.pyc  SUBMITTING_PATCHES
command.py   editor.py   git_command.py   git_refs.py     main.py   pager.py          project.py    repo           tests
command.pyc  editor.pyc  git_command.pyc  git_refs.pyc    main.pyc  pager.pyc         project.pyc   repoc          trace.py
sansari@ubuntu:~/WORKING_DIRECTORY/.repo/repo$ source build/envsetup.sh
bash: build/envsetup.sh: No such file or directory
ansari@ubuntu:~/WORKING_DIRECTORY/.repo/repo$ history 
command.py   editor.py   git_command.py   git_refs.py     main.py   pager.py          project.py    repo           tests
command.pyc  editor.pyc  git_command.pyc  git_refs.pyc    main.pyc  pager.pyc         project.pyc   repoc          trace.py
sansari@ubuntu:~/WORKING_DIRECTORY/.repo/projects$ cd device/
sansari@ubuntu:~/WORKING_DIRECTORY/.repo/projects/device$ ls
asus  common.git  generic  google  lge  sample.git  samsung
sansari@ubuntu:~/WORKING_DIRECTORY/.repo/projects/device$ source build/envsetup.sh
bash: build/envsetup.sh: No such file or directory
sansari@ubuntu:~/WORKING_DIRECTORY/.repo/projects/device$ cd
sansari@ubuntu:~$ ls
Desktop  Development  Documents  Downloads  examples.desktop  Music  Pictures  Public  T

emplates  typescript  Videos  WORKING_DIRECTORY  workspace
sansari@ubuntu:~$ cd Development/
sansari@ubuntu:~/Development$ ls
adt-bundle-linux-x86_64-20131030
sansari@ubuntu:~/Development$ cd adt-bundle-linux-x86_64-20131030/
sansari@ubuntu:~/Development/adt-bundle-linux-x86_64-20131030$ ls
eclipse  sdk
sansari@ubuntu:~/Development/adt-bundle-linux-x86_64-20131030$ cd eclipse/
sansari@ubuntu:~/Development/adt-bundle-linux-x86_64-20131030/eclipse$ ls
about_files  artifacts.xml  dropins  eclipse.ini   features  libcairo-swt.so  p2       readme
about.html   configuration  eclipse  epl-v10.html  icon.xpm  notice.html      plugins
sansari@ubuntu:~/Development/adt-bundle-linux-x86_64-20131030/eclipse$ source build/envsetup.

sh
bash: build/envsetup.sh: No such file or directory
sansari@ubuntu:~/Development/adt-bundle-linux-x86_64-20131030/eclipse$ exit
Script done, file is typescript
sansari@ubuntu:~$ ls
Desktop  Development  Documents  Downloads  examples.desktop  Music  Pictures  Public  T

emplates  typescript  Videos  WORKING_DIRECTORY  workspace
sansari@ubuntu:~$ more typescript 
Script started on Sat 01 Feb 2014 07:48:22 AM PST
sansari@ubuntu:~$ script
Script started, file is typescript
sansari@ubuntu:~$ source build/envsetup.sh
bash: build/envsetup.sh: No such file or directory
sansari@ubuntu:~$ ls
Desktop  Development  Documents  Downloads  examples.desktop  Music  Pictures  Public  T


emplates  typescript  Videos  WORKING_DIRECTORY  workspace
sansari@ubuntu:~$ cd WORKING_DIRECTORY/
sansari@ubuntu:~/WORKING_DIRECTORY$ ls
git-1.8.5.3  git-1.8.5.3.tar.gz  git-1.9.rc1
sansari@ubuntu:~/WORKING_DIRECTORY$ cd git-1.8.5.3/
[/INDENT]

---

