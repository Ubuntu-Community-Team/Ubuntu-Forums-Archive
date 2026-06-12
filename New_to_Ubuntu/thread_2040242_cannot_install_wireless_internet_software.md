---
title: "cannot install wireless internet software"
date: 2012-08-10
forum: New to Ubuntu
---

### Post by vipul2world on 2012-08-10
Hi,
I'm using Ubuntu 10.04 (Lucid Lynx). I want to use wireless Internet on Ubuntu and thus need to install Idea Net Setter(ISP) for the same.  In the USB drive I can find some files, one of the files read as below..:

[I]--How to Install---------------------- 
* You need login as root *

1. Run "tar jxvf linux_install.tar.bz2"[/I]  [I]

2. Run "./install" in TERMINAL to install MobilePartner [/I] [I]
   eg: # bash /<path>/install 

3. If you had installed this software in your system before, you will get a prompt: "The software is exist, do you want overwrites? ([Y]/[N])", enter "y" to overwrites or "n" to exit. [/I]     [I]

4. If you do not had installed this software in your system before, you will get a prompt: "Please input the install path[/usr/local/Mobile_Partner]:". Then you can input install path(fullpath), or you may using the default path(/usr/local/Mobile_Partner) by press ENTER direct [/I]  [I]

5. Finish installing [/I]  [I]

--How to run-------------------------- [/I]  [I]
* From shortcut in desktop 

* Run MobilePartner in your install path [/I]  [I]
   eg: # /<install path>/MobilePartner 

* Plug in your device, it will run automatically (Not supported in Xandros)[/I]  

But when I run '**tar jxvf linux_install.tar.bz2**' in terminal I get this message:
[B]tar: linux_install.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors[/B]

Please help. I'm clueless and don't know what to do ? :(

---

### Post by johnathansmith on 2012-08-10
Post here what you exactly get from terminal. Are you in same directory where tar files are?

---

### Post by Bashing-om on 2012-08-10
Johnathan;
  Not to confuse the issue.... but are you new to ubuntu? Why are you having to build the driver package? Can you not find/get the wireless module from the ubuntu repository ?
   we await to help!

---

### Post by vipul2world on 2012-08-11
Thanks for your reply _**[johnathansmith]("http://ubuntuforums.org/member.php?u=1582842")**_.

I inserted the USB and tried to change my directory but it didn't work:

[I]vipul@vipul-desktop:~$ cd /
vipul@vipul-desktop:/$ cd media
vipul@vipul-desktop:/media$ ls
Idea Net Setter
vipul@vipul-desktop:/media$ cd Idea Net Setter
bash: cd: Idea: No such file or directory[/I]

Then I directly pasted **tar jxvf linux_install.tar.bz2 **in the terminal and it didn't work:

[I]vipul@vipul-desktop:/media$ tar jxvf linux_install.tar.bz2
tar: linux_install.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors[/I]

Then I copied the whole installation program into my home folder, changed directories, ran it again and still nothing happened:

[I]vipul@vipul-desktop:~$ cd Idea Net Setter
vipul@vipul-desktop:~/Idea$ ls
AutoRun.exe  autorun.sh       install_linux  Startup.ico
AUTORUN.INF  Idea Net Setter  Linux          SysConfig.dat
vipul@vipul-desktop:~/Idea$ tar jxvf linux_install.tar.bz2
tar: linux_install.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
vipul@vipul-desktop:~/Idea$ cd Linux
vipul@vipul-desktop:~/Idea/Linux$ tar jxvf linux_install.tar.bz2
tar: linux_install.tar.bz2: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now
tar: Child returned status 2
tar: Exiting with failure status due to previous errors
vipul@vipul-desktop:~/Idea/Linux$ ls
7zr       DataCard_Verify  MobilePartner.bin  SysConfig.dat
data.bin  install          readme.txt

----------------------------------------------------------------------------------------------------

Thanks [/I]_**[Bashing-om]("http://ubuntuforums.org/member.php?u=1111508")**_ for your interest,
[I]
Why are you having to build the driver package? Can you not find/get the wireless module from the ubuntu repository ?[/I]

I m used to installing software in windows, so according to me when I have to get my hardware working i have to install it's driver. 

*Wireless module ? *
how can they help me? Please suggest anyone such module I can try.

*but are you new to ubuntu?*
Very complicated question. Not too new but still not familiar with Ubuntu.

---

