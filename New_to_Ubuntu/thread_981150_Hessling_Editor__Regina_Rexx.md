---
title: "Hessling Editor / Regina Rexx"
date: 2008-11-13
forum: New to Ubuntu
---

### Post by w0ipl on 2008-11-13
I am running Ubuntu 8.04 and have downloaded/installed THE (Hessling editor) and Rexx (Regina Rexx). When I look through the system I see the packages and everything seems fine - except - that I cannot find the place to install the "profile.the" to have it run at invocation of THE, and I see no way to invoke Rexx.

Anyone running either of these packages? Anyone with ideas? 

I ran individual searches in this forum for Regina and Hessling and received a "not found" for both, thus this thread.

---

### Post by quirks on 2008-11-13
First of: what the heck are those tools? I have never ever even heard of them.

To your questions:
1. The documentation of THE ([http://hessling-editor.sourceforge.net/doc/misc/app1.html#APPENDIX1](http://hessling-editor.sourceforge.net/doc/misc/app1.html#APPENDIX1)) says, you have to set an environment variable named THE_PROFILE_FILE, which points to the profile.the.
2. According to the package details of Regina REXX ([http://packages.ubuntu.com/intrepid/i386/regina-rexx/filelist](http://packages.ubuntu.com/intrepid/i386/regina-rexx/filelist)), there sould be two executables /usr/bin/regina and /usr/bin/rexx. You can invoke those from a terminal.

Let me know, if you encounter any problems.

---

### Post by w0ipl on 2008-11-13
THE (The Hessling Editor) is the PC version of the IBM mainframe XEDIT. Regina Rexx is the PC version of REXX written by Mike Colishaw for the mainframe VM/CMS operating system that IBM runs.

The Hessling editor uses macros that can be written in Rexx. Rexx can run by itself as an interpreted language or it can be compiled. The nice part is that you can set up Linux to execute Rexx programs from the command line, much as you would run Linux commands.

I "grew up" on IBM-OS, then MFT, then MVT, then MVS then the last ten years before retirement on VM/CMS. Having Rexx and THE is like going back home to the mainframes (but using a LOT less electricity :) ).

I'm not finding the file referenced in the web page, but it has me going in (hopefully) the right direction. Thanks.

---

### Post by quirks on 2008-11-14
According to the manual, THE uses /home/your_username/.therc as the profile by default. If the file does not exist, just create it with gedit or any other plain text editor of your choice. If you do not want this file to be your profile, set the environment variable THE_PROFILE_FILE to whatever file you want, e.g.:
```
export THE_PROFILE_FILE=/home/your_username/profile.the
```
In order to make this environment variable permanent, you must add the above command to your .bashrc file (to be found in your home directory).

---

### Post by w0ipl on 2008-11-14
BINGO!  Placing it as the /home/my_username/.therc fixed the problem.
It now looks/feels like I want it to.

Thank you, thank you. - Problem fixed.

---

