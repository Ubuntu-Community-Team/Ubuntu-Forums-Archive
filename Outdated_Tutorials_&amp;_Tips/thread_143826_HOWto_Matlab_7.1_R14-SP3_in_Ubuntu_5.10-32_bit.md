---
title: "HOWto: Matlab 7.1 R14-SP3 in Ubuntu 5.10-32 bit"
date: 2006-03-13
forum: Outdated Tutorials &amp; Tips
---

### Post by neoflight on 2006-03-13
Hi,

Here is an attempt to give you some tips to install and run matlab on *breezy* running on 32bit. 

Note: This is for original licensed full version which requires a license file to start and run Matlab. Installing Matlab is not 'sooo' complicated if you follow the instructions from mathworks. 

[I]Then what is this HOWTO for? Well, there is a very high probability that one will run into various problems (like me!!!). SO this HOWTO explains dealing with some specific problems like the ones I ran into while installing it in Breezy.
[/I]
*I acknowledge the [howto]("http://ubuntuforums.org/showthread.php?t=74708") by hangfire and people posted in that thread. You may find my comments there too. Thanks to n0ah420 for helping me to nail this thing down. Please consider this as a supplement to the above howto*

I. Install matlab. Follow these [instructions]("http://www.mathworks.com/access/helpdesk/help/base/install/unix/") from mathworks.

* Be sure to check the license file for carriage returns. See that all lines are separated as explained in the instruction procedure. If there is some problem perfectly reading the license.dat file then quit the installation and restart. 

* Do not skip the 'create link' option. be sure to check the box before proceeding. 

II. Post installation-several problems I ran into, during the post installation phase. 

1. Installation was OK. but I couldn't start matlab. There was simply no matlab command ! No link was made in /usr/local/bin.
2. No lmstart script file or matlab executable in $matlab/etc. So nothing was working with just the matlab folder sitting there doing nothing...!

So re-did the whole installation after emptying the matlab folder in /usr/local.  This time it was successful. The problem was with the license.dat file. Careful when you copy-paste to an editor. There were no proper separation between the lines...as given below (sample from mathworks modified to reflect the problem I had...)

Note: Here $matlab refers to the matlab home directory. In my case it was \usr\local\matlab71

Open up and edit license.dat file in /etc .. not the one we copied initially..

```
sudo gedit $matlab/etc/license.dat
```
If it is like this....
> # BEGIN-------cut here-------CUT HERE-------BEGIN
# MATLAB license passcode file.
# LicenseNo: 12345       HostID: ID=12345
INCREMENT TMW_Archive MLM 15 01-mar-2006 0 BC9GDE7743A77D15A1F8 \
	VENDOR_STRING=83 HOSTID=DEMO SN=12345 INCREMENT MATLAB MLM 15 01-mar-2006 1 4C9DB3348561DBE97E3B \
	USER_BASED DUP_GROUP=U SN=12345 INCREMENT SIMULINK MLM 15 01-mar-2006 1 1CD71484665EF583DF8B \
	USER_BASED DUP_GROUP=U SN=12345 

see how the 'INCREMENT' follows SN = 12345 in the same line

then change it to....
> # BEGIN-------cut here-------CUT HERE-------BEGIN
# MATLAB license passcode file.
# LicenseNo: 12345       HostID: ID=12345
INCREMENT TMW_Archive MLM 15 01-mar-2006 0 BC9GDE7743A77D15A1F8 \
	VENDOR_STRING=83 HOSTID=DEMO SN=12345 
INCREMENT MATLAB MLM 15 01-mar-2006 1 4C9DB3348561DBE97E3B \
	USER_BASED DUP_GROUP=U SN=12345


Use 'enter' btw. This time a proper link was created and matlab was launching from the terminal.

If not, and getting some license file error then check 
$matlab\etc  and see if you have the lmstart, lmstat, lmboot etc. are present. If not look for them at 

```
$matlab/etc/scripts
```
If you find them then copy all the 'script files' into $matlab/etc folder. 
for e.g.,
```
sudo cp $matlab/etc/scripts/lmstart $matlab/etc
```

[Now you will be able to start matlab without any problems. Solutions when encountered with lib permission issues could be solved by
issuing proper chmod commands. (I used chmod 755). Missing gcc lib files could easily be obtained from synaptic.]

3. Then there were other problems. No command could be executed. Could not even change the directory location. No file could be opened. No commands like plot etc could be used. Was experiencing "segmentation violation error". All this pain and what I have now is a simple calculator!

Then [n0ah420]("http://ubuntuforums.org/member.php?u=35455") pointed this out. (also provided in mathworks helpdesk somewhere)

execute in matlab window:
```
>> restoredefaultpath; matlabrc
>> savepath
>> rehash toolboxcache

```

4. Now - no rehash command found, savepath was not working, matlabrc not found. What the ....!!!

Reason? 

matlabrc.m and pathdef.m were not in $matlab/toolbox/local. Here is what the  installation guide and so does matlab expected them to be found.

4 Actually they were in  
```
$matlab/toolbox/local/template
```
Surprising. I dont know why it was like this. May be some incombatibility with breezy? No idea.

So the solution was to copy all those files to the place where matlab searches, which is
```
$matlab/toolbox/local
```

5. Again, there was nothing in pathdef.m file. Matlab would expect to get some paths using which it can load all the necessary stuff at launch. "restoredefaultpath" writes the necessary paths to this file. Since I was getting permission denied error when running that command, login as root using 'su' and start matlab and issue these commands in matlab,

```
>> restoredefaultpath ; matlabrc
>> savepath 

```

6. Exit and relogin as normal user and lauch matlab.

Note[edited content from mathworks somewhere]: Warnings related to toolbox cache happens when a new verison is installed and at its first launch. Data from this launch will be saved automatically for future sessions until a new version is installed.

OR use the matlab command

```
>> rehash toolboxcache
```
along with step 5. 

7. Restart matlab and bingo !!! it should be working, with no segmentation violation error, no permission denied error, no lib files missing, no problem with license stuff, no matlabrc not found etc...


**To launch matlab without an associated command window**...
[credit: n0ah420] create  a launcher with the command...

```
$matlab/bin/matlab -desktop &
```

Moral of the story : Locate all the needed files and put them in the place where matlab searches them.

Thanks and good luck people. Please let me know how it went for you and feel free to discuss.

---

### Post by Lemons. on 2006-03-28
Thanks for the launcher tip -- couldn't figure out why it wasn't working.

I have the Student version of R14SP3... there's no license file, but each installation must be activated online.  This requires some extra tweaks to the online activation script to get it running (found these in another thread here).

Note also that it appears that the "computer ID" given to mathworks when you activate is tied to the machine... so in my dual-boot, I have it installed in both XP and Linux, and this counts as one installation as far as the activation is concerned (you only get two installations in their student license)...

---

### Post by S!ian on 2006-10-14
Hi, 

I'm in the process of installing MATLAB 7 on my System (Ubuntu 6.06). I was able to install it following the instructions and i was able to start MATLAB after executing install_matlab from the $MATLAB/ directory. Unfortunately my MATLAB seems to be a "simple calculator" as neoflight described it.
Unfortunately is the above described solution not working on my system, since the files matlabrc.m and pathdef.m are in the right place. Just to be sure I renamed them and used the files from $MATLAB/toolbox/local/template. However, still no difference. When I start MATLAB I get the following error message on startup: ```

                              < M A T L A B >
                  Copyright 1984-2004 The MathWorks, Inc.
                         Version 7.0.0.19901 (R14)
                                May 06, 2004

Warning: MATLAB Toolbox Path Cache is out of date and is not being used.
Type 'help toolbox_path_cache' for more info.
Warning: MATLAB did not appear to successfully set the search path. To avoid this
warning the next time you start MATLAB, use
http://www.mathworks.com/access/helpdesk/help/techdoc/ref/pathdef.shtml
to help troubleshoot the "pathdef.m" file. To recover for this session
of MATLAB, type "restoredefaultpath;matlabrc".
Warning: Duplicate directory name: /home/sebastian/matlab.
??? Undefined function or variable "cname".

Error in ==> matlabrc at 82
if strncmp(cname,'GLNX',4)

Error parsing dbstack: value is:
??? Undefined command/function 'dbstack'.


>> 
```

when i type >> restoredefaultpath I get:
```
Warning: Duplicate directory name: /usr/local/matlab7/toolbox/stateflow/stateflow.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7/toolbox/rtw/rtw.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7/toolbox/shared/optimlib.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7/toolbox/shared/optimlib.
> In restoredefaultpath at 50
Warning: Duplicate directory name: /usr/local/matlab7/toolbox/shared/optimlib.
> In restoredefaultpath at 50
>> 
```
 and for any further command I will receive something similar to this:
```
??? Undefined function or variable 'matlabrc'.
```

Did anyone experience that and was able to solve this problem?

Thank you.

---

### Post by daou on 2006-10-15
I had trouble using Simulink in Matlab 7.1. It gave an error about missing libXft.so.1, but I was able to fix it by installing the depracated libXft1 package from the repository. Just in case anyone else runs into this as well.

---

### Post by ozancihangir on 2006-11-11
I have exactly same error with S!ian !!! (I have Ubuntu 6.06 and matlab 7,too)

---

### Post by neoflight on 2006-11-15
what i observed after these days was the problem lies in mounting the cdrom. there are some files in it which need to have some executing permissions...

so when you insert the disc and the system mounts the cdrom automatically then umount it and mount it using

```
mount -t iso9660 CD-device /cdrom
```

then the installation is straight forward and all the files (including matlabrc) are installed in their proper locations...

all you have to be careful is to get the license file correct. it needs carriage returns and breaks at the proper places....

hope this helps...

---

### Post by michaelsharman on 2007-11-22
Hi daou,

Where did you get 'libXft.so.1' from? I can't find it in any of the repositories.

Thanks

---

### Post by daou on 2007-11-23
> **michaelsharman said:**
> Hi daou,

Where did you get 'libXft.so.1' from? I can't find it in any of the repositories.

Thanks

I think I was running Dapper at the time. It is still available in the Feisty repository. You can try to get it on Gutsy with "sudo apt-get install libxft1"

If it doesn't work, do a search for libxft and look for a deprecated v. 1 of the library: "apt-cache search libxft"

---

