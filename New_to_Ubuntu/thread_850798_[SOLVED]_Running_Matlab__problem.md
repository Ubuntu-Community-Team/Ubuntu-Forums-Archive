---
title: "[SOLVED] Running Matlab  problem"
date: 2008-07-06
forum: New to Ubuntu
---

### Post by link- on 2008-07-06
Hi guys,
I recently installed matlab2008a but I'm having this problem, after I install the program it appear a window asking me if I want to run matlab where I accept to run it. Run smoothly, no terminal window around, just matlab and that's it.
I created an icon in the menu bar for the matlab and found the bin on /usr/local/bin/matlab. The problem is that when I click on the matlab icon on the menu bar appear the splash screen but then it goes off and matlab never start. I run it on the terminal with the command $ matlab, it opens but the terminal window stay around, the matlab layout can't be edited and also have problem to specify the work path in matlab. 
I the tried in the terminal window $sudo matlab which make matlab work well, but the terminal windows stay always around. Also I can't still use the icon I made in the menu bar.

Any Help

Thanks a lot
-link

---

### Post by link- on 2008-07-06
:(
Nobody know the solution to my problem?

---

### Post by tramir on 2008-07-06
What happens when you type
```
which matlab
```

---

### Post by link- on 2008-07-06
> **tramir said:**
> What happens when you type
```
which matlab
```

```

chris@chris-laptop:~$ which matlab
/home/chris/bin/matlab
chris@chris-laptop:~$ 
```

---

### Post by link- on 2008-07-07
Didn't help?

---

### Post by tramir on 2008-07-07
Sorry, forgot to check your answer :) Apparently, what gets run is not "/usr/local/bin/matlab", but "/home/chris/bin/matlab", which is probably a script optimized for matlab. Try to open a terminal window and type "matlab". If that works, then just change the properties of the icon in the menu bar so that it runs "/home/chris/bin/matlab" and not "/usr/local/bin/matlab". Let me know if this works (I'll subscribe to the post so that I don't miss your answer again).

---

### Post by link- on 2008-07-07
> **tramir said:**
> Sorry, forgot to check your answer :) Apparently, what gets run is not "/usr/local/bin/matlab", but "/home/chris/bin/matlab", which is probably a script optimized for matlab. Try to open a terminal window and type "matlab". If that works, then just change the properties of the icon in the menu bar so that it runs "/home/chris/bin/matlab" and not "/usr/local/bin/matlab". Let me know if this works (I'll subscribe to the post so that I don't miss your answer again).

> **link- said:**
>  I run it on the terminal with the command $ matlab, it opens but the terminal window stay around, the matlab layout can't be edited and also have problem to specify the work path in matlab. 

The matlab command doesn't work.:(

---

### Post by tramir on 2008-07-08
OK, I think I got confused. When does/did it work? Or how, better said?

---

### Post by link- on 2008-07-08
The $ matlab command in the terminal runs matlab but the problem is that the terminal window still around and I can't save the matlab documents and I can't save the layout with a message that sometimes appears that says something about some permissions. 

But the $ sudo matlab make it work great, with no problem (still the terminal window on the background) it let me save the documents and the layout.

---

### Post by tramir on 2008-07-08
OK, then it seems the issue are those permissions. Can you try to copy-paste the error message about the permissions?

---

### Post by link- on 2008-07-08
> **tramir said:**
> OK, then it seems the issue are those permissions. Can you try to copy-paste the error message about the permissions?

Cannot write to preference file "matlab.prf" in "/home/chris/.matlab/R2008a".
Check file permissions.
The desktop configuration was not saved successfully
The desktop configuration was not saved successfully

This lines appear in the matlab command window.

---

### Post by tramir on 2008-07-08
Good. Type this in a terminal:

```
sudo chown chris /home/chris/.matlab/R2008a/matlab.prf
```

This should make you the "owner" of the file and thus allow you to write to it. After this, try to run matlab again (without sudo).

---

### Post by renzokuken on 2008-07-08
an alternative, but not really ideal, (if you dont mind running it as root, but i guess not really a very good idea at all for something like matlab) is to hit Alt+F2, then run "gksudo matlab"

this will give you matlab in the same as running $sudo matlab from the terminal, but you wont have the terminal hanging about

---

### Post by tramir on 2008-07-08
I don't think the issue was running Matlab as root, but rather why it only works when run as root. Here's what I think happened: during the installation (which was done as root), Matlab created the .matlab folder and/or some files in it. Which means that, when you try to run it as user "chris" and overwrite those files, you're going to get errors because you're not allowed to write over files owned by root. So the idea is to "reclaim" those files to yourself - there's no reason I can think of that "root" should have files in your .matlab folder. The one file you identified is that matlab.prf file, that's why I told you to chown it to yourself. Alternatively, you could try to chown the folder and everything in it, that might be an even safer way to go:
```
sudo chown -R chris /home/chris/.matlab
```
Let us know if it worked.

---

### Post by carrarin on 2008-07-08
on a rather unrelated note, did you use wine to install matlab.
im taking Differential Eq, and my prof wants me to use matLab for extra credit.

---

### Post by link- on 2008-07-09
No, apparently don't work. Now matlab gives this error 
```

Attempt to execute SCRIPT pathdef as a function:
/home/chris/pathdef.m
Warning: MATLAB did not appear to successfully set the search
path. To avoid this
warning the next time you start MATLAB, use
http://www.mathworks.com/access/helpdesk/help/techdoc/ref/pathdef.shtml
to help troubleshoot the "pathdef.m" file. To recover for this
session
of MATLAB, type "restoredefaultpath;matlabrc".
Warning: Duplicate directory name: /home/chris/toolbox/local.
Warning: Initializing Handle Graphics failed in matlabrc.
This indicates a potentially serious problem in your MATLAB
setup,
which should be resolved as soon as possible.  Error detected
was:
MATLAB:UndefinedFunction
Undefined function or method 'colordef' for input arguments of
type 'double'.
> In matlabrc at 104
Warning: Initializing Java preferences failed in matlabrc.
This indicates a potentially serious problem in your MATLAB
setup,
which should be resolved as soon as possible.  Error detected
was:
MATLAB:UndefinedFunction
Undefined function or method 'usejava' for input arguments of
type 'char'.
> In matlabrc at 129
Warning: Failed to add default profiler filters.
> In matlabrc at 224
??? Undefined function or variable 'ispc'.

Error in ==> reporterrorlogs>isComputeServer at 337
if ispc

Error in ==> reporterrorlogs at 14
if isdeployed || ~isInteractive || isComputeServer  ||
~isJavaAvailable || ~getCheckForLogFiles

Error in ==> matlabrc at 286
reporterrorlogs

The desktop configuration was not saved successfully
```

I think the sudo chown -R chris /home/chris/.matlab command made it worse. :(

-link

PS No, I didn't use wine to install matlab.

---

### Post by tramir on 2008-07-09
Hmmm, the weird thing is that the first error is related to a matlab file located directly in your home folder (which, if I guess right, should not be the case). Is there a pathdef.m directly in your home folder?
In the meantime, I'll check some of those references to see if there's anything that would point to a solution. Which would not require running matlab as root...

---

### Post by link- on 2008-07-09
I un-installed Matlab and then Re-install it. Doesn't work, I still have the problem.

---

### Post by link- on 2008-07-09
> **tramir said:**
> Hmmm, the weird thing is that the first error is related to a matlab file located directly in your home folder (which, if I guess right, should not be the case). Is there a pathdef.m directly in your home folder?
In the meantime, I'll check some of those references to see if there's anything that would point to a solution. Which would not require running matlab as root...

Actually matlab installed in the home folder by default. The install wizard asked me where to install it but the home folder was  already in the path so I just ignored it.

---

### Post by tramir on 2008-07-09
Directly in home? I kind of doubt that. OK, how did you install it? Did you do something like "sudo install"?

---

### Post by link- on 2008-07-10
> **tramir said:**
> Directly in home? I kind of doubt that. OK, how did you install it? Did you do something like "sudo install"?

```
sudo sh /media/cdrom/install
```
Found on [https://wiki.ubuntu.com/MATLAB](https://wiki.ubuntu.com/MATLAB)
-link

---

### Post by tramir on 2008-07-11
That's what I thought. So now Matlab created a whole bunch of files in your home folder. After installing, can you give us the output of

```
ls -lR .matlab* | more
```

I don't know if you ran "sudo matlab" after installation yet, but I would suggest not doing it.

---

### Post by link- on 2008-07-11
```
chris@chris-laptop:~$ ls -lR .matlab* | more
.matlab:
total 4
drwxr-xr-x 2 root root 4096 2008-07-10 09:56 R2008a

.matlab/R2008a:
total 2868
-rw-r--r-- 1 root  root     59 2008-07-10 09:56 cwdhistory.m
-rw-r--r-- 1 root  root    305 2008-07-10 09:56 history.m
-rw-r--r-- 1 root  root   6646 2008-07-10 09:56 MATLABDesktop.xml
-rw-r--r-- 1 root  root   6591 2008-07-09 18:59 MATLABDesktop.xml.prev
-rw-r--r-- 1 root  root    220 2008-07-10 09:56 MATLAB_Editor_State.xml
-rw-r--r-- 1 chris root    742 2008-07-10 09:53 matlab.prf
-rw-r--r-- 1 root  root     38 2008-06-19 20:45 MLintDefaultSettings.txt
-rw-r--r-- 1 root  root      0 2008-07-10 09:54 MLintFailureFiles
-rw-r--r-- 1 root  root   1233 2008-07-10 09:55 publish_configurations.m
-rw-r--r-- 1 root  root    242 2008-07-10 09:55 run_configurations.m
-rw-r--r-- 1 root  root   1263 2008-06-19 20:45 shortcuts.xml
-rw-r--r-- 1 root  root 956540 2008-06-21 17:25 toolbox_cache-7.6.0-1151091188-g
lnx86.xml
-rw-r--r-- 1 root  root 956540 2008-07-06 22:07 toolbox_cache-7.6.0-160177829-gl
nx86.xml
-rw-r--r-- 1 root  root 956540 2008-07-10 09:56 toolbox_cache-7.6.0-4099763003-g
lnx86.xml
```

---

### Post by link- on 2008-07-11
> **link- said:**
> ```
chris@chris-laptop:~$ ls -lR .matlab* | more
.matlab:
total 4
drwxr-xr-x 2 root root 4096 2008-07-10 09:56 R2008a

.matlab/R2008a:
total 2868
-rw-r--r-- 1 root  root     59 2008-07-10 09:56 cwdhistory.m
-rw-r--r-- 1 root  root    305 2008-07-10 09:56 history.m
-rw-r--r-- 1 root  root   6646 2008-07-10 09:56 MATLABDesktop.xml
-rw-r--r-- 1 root  root   6591 2008-07-09 18:59 MATLABDesktop.xml.prev
-rw-r--r-- 1 root  root    220 2008-07-10 09:56 MATLAB_Editor_State.xml
-rw-r--r-- 1 chris root    742 2008-07-10 09:53 matlab.prf
-rw-r--r-- 1 root  root     38 2008-06-19 20:45 MLintDefaultSettings.txt
-rw-r--r-- 1 root  root      0 2008-07-10 09:54 MLintFailureFiles
-rw-r--r-- 1 root  root   1233 2008-07-10 09:55 publish_configurations.m
-rw-r--r-- 1 root  root    242 2008-07-10 09:55 run_configurations.m
-rw-r--r-- 1 root  root   1263 2008-06-19 20:45 shortcuts.xml
-rw-r--r-- 1 root  root 956540 2008-06-21 17:25 toolbox_cache-7.6.0-1151091188-g
lnx86.xml
-rw-r--r-- 1 root  root 956540 2008-07-06 22:07 toolbox_cache-7.6.0-160177829-gl
nx86.xml
-rw-r--r-- 1 root  root 956540 2008-07-10 09:56 toolbox_cache-7.6.0-4099763003-g
lnx86.xml
```

I already did ran "sudo matlab" after installation... SORRY!! If you think is useful I can uninstall matlab and reinstall it again.

---

### Post by tramir on 2008-07-11
That's ok. See, in the list of files, all of them are listed as owned by the user root (the first "root" in each line) in the group root (the second "root" in each line), except for matlab.prf, which we explicitly changed earlier. Let's try this:

```
cd ~/.matlab
sudo chown chris: `ls -a`
cd R2008a
sudo chown chris: `ls -a`
```

Check if chown reports any errors - this would happen if there are files with spaces in their names, but that didn't seem the case in the list you posted. If everything works fine, do another

```
ls -lR ~/.matlab* | more
```

and check that you only see "chris" as owner and group. If that worked, then try to run matlab again (without sudo). Let me know of the results, hopefully this will solve it. If not, post the errors and we'll give it another shot.

---

### Post by link- on 2008-07-11
```
chris@chris-laptop:~$ matlab
---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------
/home/chris/bin/glnx86/MATLAB: error while loading shared libraries: libXm.so.3: cannot open shared object file: No such file or directory
chris@chris-laptop:~$ 
```

---

### Post by tramir on 2008-07-12
Making progress. Try this now:

```
sudo apt-get install sun-java6-jre
```

Then matlab again. If it gives the same error message, then

```
matlab -n
```

If it still complains about libXm.so.3, then you might also need to do

```
sudo apt-get install libmotif3
```

---

### Post by link- on 2008-07-12
Still getting the same message as before when try to run "matlab".

Also when I type "matlab -n" it enters in a kind of menu where I'm supposed to choose something to fix.
:) The MATLAB_JAVA is empty...
-link

PS. By the way, thanks for the help.

---

### Post by tramir on 2008-07-12
More things to try... Just to be on the safe side, do this now:

```
sudo apt-get install sun-java6-bin sun-java6-jre
```

This should make sure you have all the required java stuff. To check if everything went ok, type

```
cd /usr/lib/jvm/
```

You should see a "java-6-sun" there, which is a link to your actual java installation (which should show up there to as "java-6-sun-bunch_of_numbers"). Now we need to tell matlab to use this version of java instead of the one it ships with and which seems to give problems. So now try this:

```
sudo chown chris: ~/bin/matlab
gedit ~/bin/matlab
```

It'll open a text editor with some code inside. The first line should be
```
#!/bin/bash
```
or something like that. Add the following line between this line and the line below it:

```
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
```

Save and try to run matlab again.

PS: Thank me when we've figured it out ;)

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ matlab
/home/chris/bin/glnx86/MATLAB: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

```
:(

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ sudo matlab
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb54ab767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_unlock+0x31) [0xb54ab8b1]
#2 /usr/lib/libX11.so.6(_XReply+0xfd) [0xb57701bd]
#3 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xae8662be]
#4 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xae844ed7]
#5 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xae845188]
#6 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xae84548f]
#7 [0xafb2d68e]
#8 [0xafb25e9d]
#9 [0xafb25e9d]
#10 [0xafb23207]
#11 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
#12 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6305bc8]
#13 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x62098e0]
#14 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f77b]
#15 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1bd296d]
#16 [0xafb2d68e]
#17 [0xafb25d37]
#18 [0xafb23207]
#19 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
Locking assertion failure.  Backtrace:
#0 /usr/lib/libxcb-xlib.so.0 [0xb54ab767]
#1 /usr/lib/libxcb-xlib.so.0(xcb_xlib_lock+0x2e) [0xb54ab81e]
#2 /usr/lib/libX11.so.6 [0xb576f518]
#3 /usr/lib/libX11.so.6(XGetVisualInfo+0x26) [0xb57660a6]
#4 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xae844189]
#5 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xae8443d5]
#6 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so [0xae845239]
#7 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/xawt/libmawt.so(Java_sun_awt_X11GraphicsEnvironment_initDisplay+0x2f) [0xae84548f]
#8 [0xafb2d68e]
#9 [0xafb25e9d]
#10 [0xafb25e9d]
#11 [0xafb23207]
#12 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6209a4d]
#13 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x6305bc8]
#14 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so [0x62098e0]
#15 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/client/libjvm.so(JVM_DoPrivileged+0x34b) [0x625f77b]
#16 /home/chris/matlab2008a/sys/java/jre/glnx86/jre1.6.0/lib/i386/libjava.so(Java_java_security_AccessController_doPrivileged__Ljava_security_PrivilegedAction_2+0x3d) [0xb1bd296d]
#17 [0xafb2d68e]
#18 [0xafb25d37]
#19 [0xafb23207]

```
Maybe this would help to figure out what's wrong.

---

### Post by tramir on 2008-07-12
The file "libgfortran.so.1" is in the package "ppu-gfortran". So what you need to do is:

```
sudo apt-get install ppu-gfortran
```

---

### Post by tramir on 2008-07-12
I didn't see the new list of errors. What might help is if you type 
```
gedit ~/bin/matlab
```
and add the following line below the "export MATLAB_JAVA" line:
```
export LIBXCB_ALLOW_SLOPPY_LOCK=1
```

Try to run matlba now. If it still gives errors, run this

```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so
```

And try matlab again.

PS: These suggestions come from [this Launchpad entry]("https://answers.launchpad.net/ubuntu/+question/26562").

---

### Post by link- on 2008-07-12
> **tramir said:**
> The file "libgfortran.so.1" is in the package "ppu-gfortran". So what you need to do is:

```
sudo apt-get install ppu-gfortran
```

```
chris@chris-laptop:~$ matlab
/home/chris/bin/glnx86/MATLAB: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory
chris@chris-laptop:~$ 
```

Still having the same error.

---

### Post by link- on 2008-07-12
> **tramir said:**
> I didn't see the new list of errors. What might help is if you type 
```
gedit ~/bin/matlab
```
and add the following line below the "export MATLAB_JAVA" line:
```
export LIBXCB_ALLOW_SLOPPY_LOCK=1
```

Try to run matlba now. If it still gives errors, run this

```
sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so
```

And try matlab again.

PS: These suggestions come from [this Launchpad entry]("https://answers.launchpad.net/ubuntu/+question/26562").
```

chris@chris-laptop:~$ gedit ~/bin/matlab
chris@chris-laptop:~$ matlab
/home/chris/bin/glnx86/MATLAB: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory
chris@chris-laptop:~$ sudo sed -i 's/XINERAMA/FAKEEXTN/g' /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so
sed: can't read /usr/lib/jvm/java-6-sun-1.6.0.04/jre/lib/i386/xawt/libmawt.so: No such file or directory
chris@chris-laptop:~$ matlab
/home/chris/bin/glnx86/MATLAB: error while loading shared libraries: libgfortran.so.1: cannot open shared object file: No such file or directory

```

---

### Post by tramir on 2008-07-12
So it seems like the only error left is the one about libgfortran.so.1. Can you post the output of

```
sudo updatedb
locate libgfortran.so.1
```

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ sudo updatedb
chris@chris-laptop:~$ locate libgfortran.so.1
/home/chris/matlab2008a/sys/os/glnx86/libgfortran.so.1
/home/chris/matlab2008a/sys/os/glnx86/libgfortran.so.1.0.0
/usr/lib/cell/toolchain/lib/gcc/ppu/4.1.1/libgfortran.so.1
/usr/lib/cell/toolchain/lib/gcc/ppu/4.1.1/libgfortran.so.1.0.0
/usr/lib/cell/toolchain/lib/gcc/ppu/4.1.1/32/libgfortran.so.1
/usr/lib/cell/toolchain/lib/gcc/ppu/4.1.1/32/libgfortran.so.1.0.0

```

---

### Post by tramir on 2008-07-12
It looks like I told you to install a package for nothing. So let's uninstall it before we do more damage :)

```
sudo apt-get purge ppu-gfortran
sudo apt-get autoremove -purge
```

Now we need to check if matlab looks for these shared libraries where it should:

```
gedit ~/bin/matlab
```

And search for "LD_LIBRARY_PATH". If it finds it, it should have a list of paths separated by colons. Check if "/home/chris/matlab2008a/sys/os/glnx86/" is included in the list. If it's not in the list, then add it in the very beginning:

```
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86/:the_rest_of_the_list
```

If you can't find "LD_LIBRARY_PATH", then add the following line:

```
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86/:$LD_LIBRARY_PATH
```

And try to run matlab again...

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ matlab
chris@chris-laptop:~$ ---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /home/chris/sys/java/jre/glnx86/jre does not exist.
---------------------------------------------------------------------------

```
```

chris@chris-laptop:~$ sudo apt-get autoremove -purge
E: Command line option 'p' [from -purge] is not known.
chris@chris-laptop:~$ 
```

---

### Post by tramir on 2008-07-12
Sorry for the typo, it should have been "--purge" (two dashes).

Can you copy/paste the file "/home/chris/bin/matlab"? You can do it from "Text Editor". I wonder what caused the JRE error, we had moved past that...

---

### Post by link- on 2008-07-12
```
#!/bin/sh
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86/:$LD_LIBRARY_PATH
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
export LIBXCB_ALLOW_SLOPPY_LOCK=1
#
#  Name:
#     matlab    script file for invoking MATLAB
#
#  Usage:
#     matlab [-h|-help] | [-n | -e]
#	     [-arch | v=variant | v=arch/variant]
#	     [-c licensefile] [-display Xdisplay | -nodisplay]
#	     [-nosplash] [-mwvisual visualid] [-debug]
#            [-softwareopengl]
#	     [-desktop | -nodesktop | -nojvm]
#	     [-memmgr manager | -check_malloc]
#	     [-r MATLAB_command] [-logfile logfile] [-timing]
#	     [-Ddebugger [options]]
#
#  Description:
#     This Bourne Shell script sets MATLAB environment variables,
#     determines the machine architecture, and starts the appropriate
#     executable.
#
#  Options:
#
#     -h,-help
#
#           Help. Show command usage
#
#     -n
#
#	    Print out the values of the environment variables and
#	    arguments passed to the MATLAB executable as well as
#	    other diagnostic information. MATLAB is not run.
#
#     -e
#
#	    Print ALL environment variables and their values to
#           standard output just prior to exiting. This argument
#	    must have been parsed before exiting for anything to
#	    be printed. MATLAB is not run. The last possible exiting
#           point is just before the MATLAB image would have been
#           executed and a status of 0 is returned. If the exit
#           status is not 0 on return then the variables and values
#           may not be correct.
#
#     -arch
#
#	    Run MATLAB assuming this architecture rather than the
#	    actual machine architecture.
#
#     v=variant
#
#           Execute the version of MATLAB found in the directory
#	    bin/$ARCH/variant instead of bin/$ARCH.
#
#     v=arch/variant
#
#           Execute the version of MATLAB found in the directory
#	    bin/arch/variant instead of bin/$ARCH.
#
#
#     -c licensefile 
#
#           Set location of the license file that MATLAB should use. 
#           It can have the form port@host or be a colon separated
#           list of license files.  This option will cause the
#           LM_LICENSE_FILE and MLM_LICENSE_FILE environment variables
#           to be ignored.
#
#     -display Xdisplay
#
#	    Send X commands to X Window Server display, Xdisplay. This
#	    supersedes the value of the DISPLAY environment variable.
#
#     -nodisplay
#
#	    Do not display any X commands. The DISPLAY environment
#	    variable is ignored. The MATLAB desktop will not be started.
#	    However, unless -nojvm is also provided the Java virtual
#	    machine will be started.
#
#     -nosplash  
#
#           Do not display the splash screen during startup.
#
#     -mwvisual visualid
#
#           The default X visual to use for figure windows.
#           The visualid is a hex number which can be found using
#           xdpyinfo.
#
#     -softwareopengl
#
#           On unix platforms (excluding MAC) this option selects
#           between hardware and software opengl implementations.
#           When used, this forces MATLAB to link in Mesa software
#           opengl libraries.
#
#     -debug
#
#           Provides debugging information especially for X based
#	    problems. Should be used only in conjunction with a
#	    Technical Support Representative from The MathWorks, Inc.
#
#     -desktop
#
#           Allow the MATLAB desktop to be started by a process
#           without a controlling terminal. This is usually a required
#           command line argument when attempting to start MATLAB
#           from a window manager menu or desktop icon.
#           
#     -nodesktop	
#
#	    Do not start the MATLAB desktop. Use the current window
#	    for commands. The Java virtual machine will be started.
#
#     -nojvm
#
#	    Shut off all Java support by not starting the Java virtual
#	    machine. In particular the MATLAB desktop will not be
#	    started.
#
#     -memmgr manager
#
#	    Set environment variable MATLAB_MEM_MGR to manager.
#	    manager can have one of the following values:
#
#	    cache    - Default.
#	    compact  - (32-bit addressing only) For large models or
#		       MATLAB code that uses many structure or object
#		       variables. It is not helpful for large arrays.
#	    debug    - Does memory integrity checking. Useful for
#		       debugging memory problems caused by user mex
#		       files.
#
#     -check_malloc
#
#           Same as '-memmgr debug'.
#
#     -r MATLAB_command
#
#	    Start MATLAB and execute the MATLAB command.
#
#     -logfile log
#
#	    Make a copy of any output to the command window in file log.
#	    This includes all crash reports.
#
#     -timing
#
#	    Print a summary of startup time to the command window. It is
#	    also recorded in a timing log, the name of which is printed
#           to the shell window that started up MATLAB. Should be used
#           only in conjunction with a Technical Support Representative
#           from The MathWorks, Inc.
#
#     -Ddebugger [options]
#
#	    Start MATLAB with debugger (e.g. dbx, gdb, dde, xdb, cvd).
#	    A full path can be specified for debugger. The options
#	    cover ONLY those that go after the executable to be debugged
#	    in the syntax of the actual debug command and for most
#	    debuggers this is very limited. To customize your debugging
#	    session use a startup file. See your debugger documentation
#	    for details. Options above that would normally be passed to
#	    the MATLAB executable should be used as parameters of
#	    a command inside the debugger like 'run' and not used
#	    when running the matlab script. If any of the options are
#	    placed before the -Ddebugger argument they will be
#	    handled as if they were part of the options after the
#	    -Ddebugger argument and will be treated as illegal
#	    options by most debuggers. The MATLAB_DEBUG environment
#	    variable is set to the filename part of the debugger argument.
#
#	    NOTE: For certain debuggers like gdb, the SHELL environment
#		  variable is ALWAYS set to /bin/sh.
#
# Copyright 1984-2007 The MathWorks, Inc.
# $Revision: 1.100.4.47 $  $Date: 2007/11/12 22:52:38 $
#__________________________________________________________________________
#
# Enable proper operation on Windows when using a UNIX-compatible shell
#
    if [ "$OS" = "Windows_NT" ]; then
        arglist=
        while [ $# -gt 0 ]; do
            # Quote arguments so that single quotes inside double quoted
            # strings are preserved, e.g., -r "disp('hello'); quit"
            arglist="$arglist \"\\\"$1\\\"\""
            shift
        done
        eval exec "$0.exe $arglist"
    fi
#
    arg0_=$0
#
# Temporary file that hold MATLABPATH code from .matlab7rc.sh file.
#
    temp_file=/tmp/matlab.$LOGNAME.$$.a
#
    trap "rm -f $temp_file; exit 1" 1 2 3 15
#
#========================= archlist.sh (start) ============================
#
# usage:        archlist.sh
#
# abstract:     This Bourne Shell script creates the variable ARCH_LIST.
#
# note(s):      1. This file is always imbedded in another script
#
# Copyright 1997-2007 The MathWorks, Inc.
# $Revision: 1.1.6.3 $  $Date: 2007/11/12 22:52:47 $
#----------------------------------------------------------------------------
#
    ARCH_LIST='glnx86 glnxa64 mac maci maci64 sol2 sol64'
#=======================================================================
# Functions:
#   check_archlist ()
#=======================================================================
    check_archlist () { # Sets ARCH. If first argument contains a valid
			# arch then ARCH is set to that value else
		        # an empty string. If there is a second argument
			# do not output any warning message. The most
			# common forms of the first argument are:
			#
			#     ARCH=arch
			#     MATLAB_ARCH=arch
			#     argument=-arch
			#
                        # Always returns a 0 status.
                        #
                        # usage: check_archlist arch=[-]value [noprint]
                        #
	if [ $# -gt 0 ]; then
	    arch_in=`expr "$1" : '.*=\(.*\)'`
	    if [ "$arch_in" != "" ]; then
	        ARCH=`echo "$ARCH_LIST EOF $arch_in" | awk '
#-----------------------------------------------------------------------
	{ for (i = 1; i <= NF; i = i + 1)
	      if ($i == "EOF")
		  narch = i - 1
	  for (i = 1; i <= narch; i = i + 1)
		if ($i == $NF || "-" $i == $NF) {
		    print $i
		    exit
		}
	}'`
#-----------------------------------------------------------------------
	       if [ "$ARCH" = "" -a $# -eq 1 ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
echo ' '
echo "    Warning: $1 does not specify a valid architecture - ignored . . ."
echo ' '
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	       fi
	    else
		ARCH=""
	    fi
	else
	    ARCH=""
	fi
#
	return 0
    }
#=======================================================================
#========================= archlist.sh (end) ==============================
#
#=======================================================================
# Functions:
#   check_rc_file ()
#   build_cmd ()
#=======================================================================
    check_rc_file () { # Checks rc_file file for minimal features.
                       # Currently the only thing it checks for is:
                       # 
                       #    .matlab7rc.sh in the file
                       # 
                       # If it fails the check print a warning message.
                       # The rc_file is assumed to exist.
                       # 
                       # Always returns a zero status.
                       # 
                       # usage: check_rc_file rc_file
                       # 
        grep '\.matlab7rc.sh' $1 > /dev/null 2>&1
        if [ $? -ne 0 ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
echo "---------------------------------------------------------------------------"
echo "Warning: The .matlab7rc.sh file that was sourced is old . . ."
echo "         --> file = $1"
echo " "
echo '         Please use $MATLAB/bin/.matlab7rc.sh to update this file.'
echo "         --> MATLAB = $MATLAB"
echo "---------------------------------------------------------------------------"
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
        fi
        return 0
    }
#=======================================================================
    build_cmd () { # Takes the cmd input string and outputs the same
                   # string correctly quoted to be evaluated again.
                   #
                   # Always returns a 0
                   #
                   # usage: build_cmd
                   #
        echo "$cmd" | awk '
#----------------------------------------------------------------------------
        BEGIN { squote = sprintf ("%c", 39)   # set single quote
                dquote = sprintf ("%c", 34)   # set double quote
              }
NF != 0 { newarg=dquote                 # initialize output string to
                                        # double quote
          lookquote=dquote              # look for double quote
          oldarg = $0
          while ((i = index (oldarg, lookquote))) {
             newarg = newarg substr (oldarg, 1, i - 1) lookquote
             oldarg = substr (oldarg, i, length (oldarg) - i + 1)
             if (lookquote == dquote)
                lookquote = squote
             else
                lookquote = dquote
             newarg = newarg lookquote
          }
          printf " %s", newarg oldarg lookquote }'
#----------------------------------------------------------------------------
        return 0
    }
#=======================================================================
#
#**************************************************************************
# Determine the path of the MATLAB root directory - always one directory
# up from the path to this command.
#**************************************************************************
#
    filename=$arg0_
#
# Now it is either a file or a link to a file.
#
    cpath=`pwd`

#
# Use it to find the top of the tree
# Skip this if someone wants to override the default
#
    if [ "$SOURCE_MATLAB_ENV_FROM" = "" ]; then

#
# Follow up to 8 links before giving up. Same as BSD 4.3
#
      n=1
      maxlinks=8
      while [ $n -le $maxlinks ]
      do
#
# Get directory correctly!
#
	newdir=`echo "$filename" | awk '
                        { tail = $0
                          np = index (tail, "/")
                          while ( np != 0 ) {
                             tail = substr (tail, np + 1, length (tail) - np)
                             if (tail == "" ) break
                             np = index (tail, "/")
                          }
                          head = substr ($0, 1, length ($0) - length (tail))
                          if ( tail == "." || tail == "..")
                             print $0
                          else
                             print head
                        }'`
	if [ ! "$newdir" ]; then
	    newdir="."
	fi
	(cd $newdir) > /dev/null 2>&1
	if [ $? -ne 0 ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ''
    echo 'Internal error 1: We could not determine the path of the'
    echo '                  MATLAB root directory.'
    echo ''
    echo "                  original command path = $arg0_"
    echo "                  current  command path = $filename"
    echo ''
    echo '                  Please contact:'
    echo '' 
    echo '                      MathWorks Technical Support'
    echo ''
    echo '                  for further assistance.'
    echo ''
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	    exit 1
	fi
	cd $newdir
#
# Need the function pwd - not the built in one
#
	newdir=`/bin/pwd`
#
	newbase=`expr //$filename : '.*/\(.*\)' \| $filename`
        lscmd=`ls -l $newbase 2>/dev/null`
	if [ ! "$lscmd" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ''
    echo 'Internal error 2: Could not determine the path of the'
    echo '                  MATLAB root directory.'
    echo ''
    echo "                  original command path = $filename"
    echo "                  current  command path = $filename"
    echo ''
    echo '                  Please contact:'
    echo '' 
    echo '                      MathWorks Technical Support'
    echo ''
    echo '                  for further assistance.'
    echo ''
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	    exit 1
	fi
#
# Check for link portably
#
	if [ `expr "$lscmd" : '.*->.*'` -ne 0 ]; then
	    filename=`echo "$lscmd" | awk '{ print $NF }'`
	else
#
# It's a file
#
	    dir="$newdir"
	    command="$newbase"
#
	    cd $dir/..
	    MATLABdefault=`/bin/pwd`
	    break
	fi
	n=`expr $n + 1`
      done
      if [ $n -gt $maxlinks ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ''
    echo 'Internal error 3: More than $maxlinks links in path to'
    echo "                  this script. That's too many!"
    echo ''
    echo "                  original command path = $filename"
    echo "                  current  command path = $filename"
    echo ''
    echo '                  Please contact:'
    echo '' 
    echo '                      MathWorks Technical Support'
    echo ''
    echo '                  for further assistance.'
    echo ''
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	exit 1
      fi
    else 
        MATLABdefault="$SOURCE_MATLAB_ENV_FROM"
    fi

    cd "$cpath"
#
#**************************************************************************
#
# Do not use ARCH if it exists in the environment
#
    ARCH=""
#
    RCSHEADER='$Revision: 1.100.4.47 $  $Date: 2007/11/12 22:52:38 $'
#
    USAGE1="${command} [-h|-help] | [-n | -e]"
    USAGE2="       [-arch | v=variant | v=arch/variant]"
    USAGE3="       [-c licensefile] [-display Xdisplay | -nodisplay]"
    USAGE4="       [-nosplash] [-mwvisual visualid] [-debug] [-softwareopengl]"
    USAGE5="       [-desktop | -nodesktop | -nojvm]"
    USAGE6="       [-memmgr manager | -check_malloc]"
    USAGE7="       [-r MATLAB_command] [-logfile log] [-timing]" 
    USAGE8="       [-Ddebugger [options]]" 
#
# Parse the arguments
#
    stat="OK"
    showenv=0
    showenv_all=0
    VARIANT=""
    VARIANTmatlab="MATLAB"
    arglist=""
    arglist2=
    memmgr=""
    desktopflag=1
    jvmflag=1
    nodisplay=0
    usemesa=0
    usemesalinux=0
    while [ "$stat" = "OK" -a  $# -gt 0 ]; do
	case "$1" in
	    -h|-help)
		stat=""
		;;
            -n)
                showenv=1
                ;;
	    -e)
    		showenv_all=1
		;;
	    #-c)
            #   This now is handled by the * case.
            #   ;;
	    -display)
		if [ $# -eq 1 ]; then
		    stat=""
		else
		    arglist="$arglist $1"
		    shift
		    isoption=`expr "/$1" : '/\(-.*\)'`
		    if [ "$isoption" != "" ]; then
		        stat=""
		    else
		        arglist="$arglist $1"
			display="$1"
		    fi
		fi
 		;;
	    -nodisplay)
		arglist="$arglist $1"
		nodisplay=1
		;;
	    -softwareopengl)
		usemesa=1;
		;;
	    -softwareopengllinux)
		usemesalinux=1;
		;;
	    -memmgr)
		if [ $# -eq 1 ]; then
		    stat=""
		else
		    shift
		    memmgr=$1
		fi
 		;;
	    -check_malloc)
		memmgr="debug"
		;;
	    -D*)
		debugger=`expr "$1" : '-D\(.*\)'`
		if [ "$debugger" = "" ]; then
		    stat=""
		else
		    MATLAB_DEBUG=`expr "//$debugger" : ".*/\(.*\)"`
		fi
		;;
	    -jdb)
		arglist="$arglist $1"
		;;
	    -nodesktop)
		desktopflag=0
		;;
	    -nojvm)
		jvmflag=0
		;;
	    -r)
		if [ $# -eq 1 ]; then
		    stat=""
		else
		    arglist="$arglist $1"
		    shift
		    cmd="$1"
		    quoted_cmd=`build_cmd`
		    arglist="$arglist `echo $quoted_cmd`"
		fi
 		;;
	    -timing)
		if [ "$ARCH" = "" ]; then
                    . $MATLABdefault/bin/util/arch.sh
                fi
                if [ -f $MATLABdefault/bin/$ARCH/cpucount ]; then
                    MATLAB_CPUCOUNT=`$MATLABdefault/bin/$ARCH/cpucount`
                fi
		;;
	    -logfile)
		if [ $# -eq 1 ]; then
#
# The MATLAB executable will check that there is no logfile
#
		    arglist="$arglist $1"
		else
#
# The MATLAB executable will check if the file can be opened for writing
#		
		    arglist="$arglist $1 $2"
		    shift
		fi
 		;;
	    v=*/*)
                foundVariant=0
#
# Test options if no debugger.
#
                if [ "$debugger" = "" ]; then
#
# Check for variant
#
                    value=`expr "$1" : 'v=\(.*\)/.*'`
                    value2=`expr "$1" : 'v=.*/\(.*\)'`
		    arch=$ARCH
		    check_archlist argument=$value noprint
		    if [ "$ARCH" != "" -a -f $MATLABdefault/bin/$value/$value2/MATLAB ]; then
			VARIANT=$value2
			VARIANTmatlab=$VARIANT/MATLAB
                        foundVariant=1
		    else
			ARCH=$arch
		    fi
		fi
		if [ "$foundVariant" = "0" ]; then
                    arglist="$arglist $1"
		fi
		;;
	    v=*)
                foundVariant=0
#
# Test options if no debugger.
#
                if [ "$debugger" = "" ]; then
		    value=`expr "$1" : 'v=\(.*\)'`
#
# Check for variant
#
		    if [ "$ARCH" = "" ]; then
  			. $MATLABdefault/bin/util/arch.sh
		    fi
  		    if [ -f $MATLABdefault/bin/$ARCH/$value/MATLAB ]; then
  			VARIANT=$value
			VARIANTmatlab=$VARIANT/MATLAB
  			foundVariant=1
		    fi
                fi
		if [ "$foundVariant" = "0" ]; then
                    arglist="$arglist $1"
		fi
		;;
	    -*)
		found=0
#
# Test options if no debugger.
#
                if [ "$debugger" = "" ]; then
#
# Check for -arch
#
		    arch=$ARCH
		    check_archlist argument=$1 noprint
		    if [ "$ARCH" != "" ]; then
			found=1
		    else
			ARCH=$arch
		    fi
                fi
		if [ "$found" = "0" ]; then
                    arglist="$arglist $1"
		fi
                ;;
	    *)
		arglist="$arglist $1"
		;;
	esac
	shift
    done
#
# Check for errors
#
    if [ "$stat" != "OK" -a "$showenv" != "1" ]; then	# An error occurred.
#
        RCSREVISION=`echo "$RCSHEADER" | awk '{ print $2 }'`
#
        if [ "$stat" != "" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ""
    echo "    ${command}:  $stat"
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
        fi
	if [ "$ARCH" = "" ]; then
  	    . $MATLABdefault/bin/util/arch.sh
	fi
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ""
    echo "    Usage:  $USAGE1"
    echo "            $USAGE2"
    echo "            $USAGE3"
    echo "            $USAGE4"
    echo "            $USAGE5"
    echo "            $USAGE6"
    echo "            $USAGE7"
    echo "            $USAGE8"
    echo ""
    echo "    -h|-help             - Display arguments." 
    echo "    -n                   - Display final environment variables,"
    echo "                           arguments, and other diagnostic"
    echo "                           information. MATLAB is not run."
    echo "    -e                   - Display ALL the environment variables and"
    echo "                           their values to standard output. MATLAB"
    echo "                           is not run. If the exit status is not"
    echo "                           0 on return then the variables and values"
    echo "                           may not be correct."
    echo "    -arch                - Start MATLAB assuming architecture arch."
    echo "    v=variant            - Start the version of MATLAB found"
    echo "                           in bin/$ARCH/variant instead of bin/$ARCH."
    echo "    v=arch/variant       - Start the version of MATLAB found"
    echo "                           in bin/arch/variant instead of bin/$ARCH."
    echo "    -c licensefile       - Set location of the license file that MATLAB" 
    echo "                           should use.  It can have the form port@host or"
    echo "                           be a colon separated list of license files."
    echo "                           The LM_LICENSE_FILE and MLM_LICENSE_FILE"
    echo "                           environment variables will be ignored."
    echo "    -display Xdisplay    - Send X commands to X server display, Xdisplay."
    echo "    -nodisplay           - Do not display any X commands. The MATLAB"
    echo "                           desktop will not be started. However, unless"
    echo "                           -nojvm is also provided the Java virtual machine"
    echo "                           will be started."
    echo "    -nosplash            - Do not display the splash screen during startup."
    echo "    -mwvisual visualid   - The default X visual to use for figure windows."
    echo "    -debug               - Provide debugging information especially for X"
    echo "                           based problems."
    echo "    -desktop             - Allow the MATLAB desktop to be started by a"
    echo "                           process without a controlling terminal. This is"
    echo "                           usually a required command line argument when"
    echo "                           attempting to start MATLAB from a window manager"
    echo "                           menu or desktop icon."
    echo "    -nodesktop           - Do not start the MATLAB desktop. Use the current"
    echo "                           terminal for commands. The Java virtual machine"
    echo "                           will be started."
    echo "    -nojvm               - Shut off all Java support by not starting the"
    echo "                           Java virtual machine. In particular the MATLAB"
    echo "                           desktop will not be started."
    echo "    -memmgr manager      - Set environment variable MATLAB_MEM_MGR to"
    echo "                           manager. manager can have one of the following"
    echo "                           values:"
    echo "                           cache   - Default."
    echo "                           compact - (32-bit addressing only) For large"
    echo "                                     models or MATLAB code that uses many"
    echo "                                     structure or object variables. It is"
    echo "                                     not helpful for large arrays."
    echo "                           debug   - Does memory integrity checking. Useful"
    echo "                                     for debugging memory problems caused by"
    echo "                                     user mex files."
    echo "    -check_malloc        - Same as '-memmgr debug'."
    echo "    -r MATLAB_command    - Start MATLAB and execute the MATLAB_command."
    echo "    -logfile log         - Make a copy of any output to the command window"
    echo "                           in file log. This includes all crash reports."
    echo "    -timing              - Print a summary of startup time to the command"
    echo "                           window. It is also recorded in a timing log, the"
    echo "                           name of which is printed to the shell window that"
    echo "                           started up MATLAB."
    echo "    -Ddebugger [options] - Start debugger to debug MATLAB."
    echo ""
    echo "    Revision #: $RCSREVISION"
    echo ""
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	if [ "$showenv_all" = "1" ]; then
	   env
	fi
        exit 1
    fi
#
# Determine what is set in the environment
#
    AUTOMOUNT_MAPenv="$AUTOMOUNT_MAP"
    DISPLAYenv="$DISPLAY"
    TOOLBOXenv="$TOOLBOX"
    MATLABPATHenv="$MATLABPATH"
    XAPPLRESDIRenv="$XAPPLRESDIR"
    XKEYSYMDBenv="$XKEYSYMDB"
    MATLAB_MEM_MGRenv="$MATLAB_MEM_MGR"
    SHELLenv="$SHELL"
#
# Set the defaults - MATLABdefault is determined above.
#
    AUTOMOUNT_MAPdefault=''
    DISPLAYdefault=''
    ARCHdefault=''
    TOOLBOXdefault='$MATLAB/toolbox'
    MATLABPATHdefault=''
#
    XAPPLRESDIRdefault='$MATLAB/X11/app-defaults'
    XKEYSYMDBdefault='$MATLAB/X11/app-defaults/XKeysymDB'
#
    MATLAB_MEM_MGRdefault=''
#
    SHELLdefault='$SHELL'
#
    MATLAB_UTIL_DIRdefault=$MATLABdefault/bin/util
#
# Feature state variables
#
#--------------------------------------------------------------------------
#
# Source file .matlab7rc.sh and get values for the following environment
# variables
#
#       ARCH                    (machine architecture)
#       AUTOMOUNT_MAP           (Path prefix map for automounting)
#       DISPLAY                 (DISPLAY variable for X Window System)
#       LDPATH_PREFIX           (path(s) that appear at the start of
#       			 LD_LIBRARY_PATH)
#       LDPATH_SUFFIX           (path(s) that appear at the end of
#       			 LD_LIBRARY_PATH)
#       LD_LIBRARY_PATH         (load library path - the name
#       			 LD_LIBRARY_PATH is platform dependent)
#       MATLAB                  (MATLAB root directory)
#       MATLABPATH              (MATLAB search path)
#       SHELL                   (which shell to use for ! and unix
#       			 command in MATLAB)
#       TOOLBOX                 (toolbox path)
#       XAPPLRESDIR             (X Application Resource Directory)
#       XKEYSYMDB               (X keysym Database file)
#
# The search order for .matlab7rc.sh is:
#
#       .               (current directory)
#       $HOME           (users home directory)
#       $MATLAB/bin     (MATLAB bin directory)
#
    if [ -f .matlab7rc.sh ]; then
        SOURCED_DIR='.'
        SOURCED_DIReval=`pwd`
        . "$cpath"/.matlab7rc.sh
    elif [ -f "$HOME"/.matlab7rc.sh ]; then
        SOURCED_DIR='$HOME'
        SOURCED_DIReval=$HOME
        . "$HOME"/.matlab7rc.sh
    elif [ -f $MATLABdefault/bin/.matlab7rc.sh ]; then
#
# NOTE: At this point we will use the MATLAB determined earlier to
#       source the file. After that the value in that file if not
#       null will be used.
#
        SOURCED_DIR='$MATLAB/bin'
        SOURCED_DIReval=$MATLABdefault/bin
        . $MATLABdefault/bin/.matlab7rc.sh
    else
        SOURCED_DIR=
        MATLAB_UTIL_DIR=$MATLAB_UTIL_DIRdefault
#
# arch.sh requires MATLAB - save temporarily
#
        MATLABsave="$MATLAB"
        MATLAB="$MATLABdefault"
#
        . $MATLAB_UTIL_DIR/arch.sh
        if [ "$ARCH" = "unknown" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ''
    echo '^G    Sorry! We could not determine the machine architecture for your'
    echo '           host. Please contact:'
    echo ''
    echo '               MathWorks Technical Support'
    echo ''
    echo '           for further assistance.'
    echo ''
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
            exit 1
        fi
        MATLAB="$MATLABsave"
#
	ARCHdefault=$ARCH
    fi
#
#--------------------------------------------------------------------------
#
# Determine the final values for the following variables
#
#       ARCH                    (machine architecture)
#       AUTOMOUNT_MAP           (Path prefix map for automounting)
#       DISPLAY                 (DISPLAY variable for X Window System)
#       MATLAB                  (MATLAB root directory)
#       MATLAB_MEM_MGR          (Type of memory manager)
#       MATLAB_DEBUG		(name of the debugger from -Ddebugger argument)
#       MATLABPATH              (MATLAB search path)
#       SHELL                   (which shell to use for ! and unix
#       			 command in MATLAB)
#       TOOLBOX                 (toolbox path)
#       XAPPLRESDIR             (X Application Resource Directory)
#       XKEYSYMDB               (X keysym Database file)
#
    rcfile='r '
    environ='e '
    script='s '
    argument='a '
    rcfilep='rs'
    environp='es'
#
# Sourced a .matlab7rc.sh file
#
    if [ "$SOURCED_DIR" != "" ]; then
	if [ "$AUTOMOUNT_MAP" != "" ]; then
	    if [ "$MATLAB" != "$MATLABdefault" -a "$AUTOMOUNT_MAPenv" != "" ]; then
                AUTOMOUNT_MAPmode="$environ"
	    else
                AUTOMOUNT_MAPmode="$rcfile"
	    fi
	else
            AUTOMOUNT_MAPmode="$script"
	    AUTOMOUNT_MAP="$AUTOMOUNT_MAPdefault"
	fi
#
        if [ "$MATLAB" != "" ]; then
            MATLABmode="$rcfile"
        else
            MATLABmode="$script"
            MATLAB="$MATLABdefault"
        fi
        if [ "$AUTOMOUNT_MAP" != "" ]; then
            MATLAB=`echo $MATLAB $AUTOMOUNT_MAP | awk '
                {if (substr($1,1,length($2)) == $2)
                     if (NF == 4)                               # a -> b
                         print $NF substr($1,length($2) + 1)
                     else                                       # a ->
                         print substr($1,length($2) + 1)
                     else
                         print $1}'`
        fi
#
	if [ "$display" != "" ]; then
            DISPLAYmode="$argument"
	    DISPLAY="$display"
	elif [ "$DISPLAY" != "" ]; then
	    if [ "$DISPLAYenv" = "$DISPLAY" ]; then
                DISPLAYmode="$environ"
	    else
                DISPLAYmode="$rcfile"
	    fi
	else
            DISPLAYmode="$script"
	    DISPLAY="`eval echo $DISPLAYdefault`"
	fi
#
	if [ "$ARCH" != "" ]; then
            ARCHmode="$rcfile"
	else
            ARCHmode="$script"
	    ARCH="$ARCHdefault"	
	fi
#
	if [ "$TOOLBOX" != "" ]; then
	    if [ "$TOOLBOXenv" = "$TOOLBOX" ]; then
                TOOLBOXmode="$environ"
	    else
                TOOLBOXmode="$rcfile"
	    fi
	else
            TOOLBOXmode="$script"
	    TOOLBOX="`eval echo $TOOLBOXdefault`"
	fi
#
	if [ "$XAPPLRESDIR" != "" ]; then
	    XAPPLRESDIR="`eval echo $XAPPLRESDIR`"
	    if [ "$XAPPLRESDIRenv" = "$XAPPLRESDIR" ]; then
                XAPPLRESDIRmode="$environ"
	    else
                XAPPLRESDIRmode="$rcfile"
	    fi
	else
            XAPPLRESDIRmode="$script"
	    XAPPLRESDIR="`eval echo $XAPPLRESDIRdefault`"
	fi
#
	if [ "$XKEYSYMDB" != "" ]; then
	    XKEYSYMDB="`eval echo $XKEYSYMDB`"
	    if [ "$XKEYSYMDBenv" = "$XKEYSYMDB" ]; then
                XKEYSYMDBmode="$environ"
	    else
                XKEYSYMDBmode="$rcfile"
	    fi
	else
            XKEYSYMDBmode="$script"
	    XKEYSYMDB="`eval echo $XKEYSYMDBdefault`"
	fi
#
        if [ "$MATLABPATH" != "" ]; then
	    if [ "$MATLABPATHenv" = "$MATLABPATH" ]; then
                MATLABPATHmode="$environp"
	    else
                MATLABPATHmode="$rcfilep"
	    fi
        else
            MATLABPATHmode="$script"
	    MATLABPATH="`eval echo $MATLABPATHdefault`"
        fi
#
# For MATLAB_MEM_MGR:
#
#        1. memmgr manager argument
#	 2. check_malloc argument
#        3. rcfile (not currently set)
#	 4. environment
#	 5. default (empty)
#
	if [ "$memmgr" != "" ]; then
	    MATLAB_MEM_MGRmode="$argument"
	    MATLAB_MEM_MGR=$memmgr
	elif [ "$MATLAB_MEM_MGR" != "" ]; then
	    if [ "$MATLAB_MEM_MGRenv" = "$MATLAB_MEM_MGR" ]; then
	        MATLAB_MEM_MGRmode="$environ"
	    else
	        MATLAB_MEM_MGRmode="$rcfile"
	    fi
	else
	    MATLAB_MEM_MGRmode="$script"
	    MATLAB_MEM_MGR="$MATLAB_MEM_MGRdefault"
	fi
#
	if [ "$MATLAB_DEBUG" = "" ]; then
            MATLAB_DEBUGmode="$script"
	else
            MATLAB_DEBUGmode="$argument"
	fi
#
	if [ "$SHELL" != "" ]; then
	    if [ "$SHELLenv" = "$SHELL" ]; then
                SHELLmode="$environ"
	    else
                SHELLmode="$rcfile"
	    fi
	else
            SHELLmode="$script"
	    SHELL="`eval echo $SHELLdefault`"
	fi
    else
	if [ "$AUTOMOUNT_MAPenv" != "" ]; then
    	    AUTOMOUNT_MAPmode="$environ"
	    AUTOMOUNT_MAP="$AUTOMOUNT_MAPenv"
	else
    	    AUTOMOUNT_MAPmode="$script"
	    AUTOMOUNT_MAP="$AUTOMOUNT_MAPdefault"
	fi
	MATLABmode="$script"
        if [ "$AUTOMOUNT_MAP" != "" ]; then
            MATLAB=`echo $MATLABdefault $AUTOMOUNT_MAP | awk '
                {if (substr($1,1,length($2)) == $2)
                     if (NF == 4)                               # a -> b
                         print $NF substr($1,length($2) + 1)
                     else                                       # a ->
                         print substr($1,length($2) + 1)
                     else
                         print $1}'`
	else
	    MATLAB="$MATLABdefault"
        fi
	if [ "$display" != "" ]; then
            DISPLAYmode="$argument"
	    DISPLAY="$display"
	else
            DISPLAYmode="$environ"
	    DISPLAY="$DISPLAYenv"
	fi
        ARCHmode="$script"
	ARCH="$ARCHdefault"
	TOOLBOXmode="$script"
	TOOLBOX="`eval echo $TOOLBOXdefault`"
        XAPPLRESDIRmode="$script"
	XAPPLRESDIR="`eval echo $XAPPLRESDIRdefault`"
        XKEYSYMDBmode="$script"
	XKEYSYMDB="`eval echo $XKEYSYMDBdefault`"
        if [ "$MATLABPATHenv" != "" ]; then
            MATLABPATHmode="$environp"
	    MATLABPATH="$MATLABPATHenv"
	else
            MATLABPATHmode="$script"
	    MATLABPATH="`eval echo $MATLABPATHdefault`"
	fi
	if [ "$check_malloc" = "1" ]; then
	    MATLAB_MEM_MGRmode="$argument"
	    MATLAB_MEM_MGR='debug'
	elif [ "$MATLAB_MEM_MGR" != "" ]; then
	    MATLAB_MEM_MGRmode="$environ"
	else
	    MATLAB_MEM_MGRmode="$script"
	    MATLAB_MEM_MGR="$MATLAB_MEM_MGRdefault"
        fi
	if [ "$MATLAB_DEBUG" = "" ]; then
            MATLAB_DEBUGmode="$script"
	else
            MATLAB_DEBUGmode="$argument"
	fi
        SHELLmode="$environ"
	SHELL="$SHELLenv"
    fi
#
#--------------------------------------------------------------------------
#
# Check rc_file
#
    if [ "$SOURCED_DIR" = '.' ]; then
	check_rc_file "$cpath"/.matlab7rc.sh
    elif [ "$SOURCED_DIR" = '$HOME' ]; then
	check_rc_file "$HOME"/.matlab7rc.sh
    fi

#
# Use MATLAB instead of matlab for the executable
# A more invasive change (to be made long-term) involves setmwe
#
VARIANTmatlab=`echo "$VARIANTmatlab" | sed 's|matlab$|MATLAB|'`

#
# Determine the final values for the following variables
#
#       LD_LIBRARY_PATH         (load library path - the name
#       			 LD_LIBRARY_PATH is platform dependent)
#	_JVM_THREADS_TYPE	(type of Java virtual machine threads)
#
#--------------------------------------------------------------------------

#
# Decide whether to put -nojvm or -nodesktop back on the argument list.
# Check the mac first.
#
if [ "$ARCH" = 'mac' -o "$ARCH" = 'maci' -o "$ARCH" = 'maci64' ]; then
#
# If the user did not explicitly set v=arch or v=arch/variant,
# then launch the executable via the Mac OS X package by default, so that
# resources and executable icons can be automatically found by the system.
#
    if [ "$foundVariant" = "" ]; then
        VARIANT=MATLAB.app/Contents/MacOS
        VARIANTmatlab=$VARIANT/MATLAB
    fi
fi
if [ "$jvmflag" = "0" ]; then
    arglist="$arglist -nojvm"
elif [ "$desktopflag" = "0" ]; then
    arglist="$arglist -nodesktop"
fi

#
# Determine the java vm path for each platform.
#
    case "$ARCH" in
	sol2)
	    JARCH="sparc"
	    ;;
	sol64)
	    JARCH="sparcv9"
	    ;;
	glnx86)
	    JARCH="i386"
	    ;;
	glnxa64)
	    JARCH="amd64"
	    ;;
	*)
	    JARCH=$ARCH
	    ;;
    esac
#
    if [ "$ARCH" = 'mac' -o "$ARCH" = 'maci' -o "$ARCH" = 'maci64' ]; then
        DEFAULT_JRE_LOC=/System/Library/Frameworks/JavaVM.framework
    else
        DEFAULT_JRE_LOC=$MATLAB/sys/java/jre/$ARCH/jre
    fi

    # No more symlinks to jre
    if [ "X$MATLAB_JAVA" = "X" ]; then
	MATLAB_JAVA_CFG=`head -n 1 ${DEFAULT_JRE_LOC}.cfg 2>/dev/null`
    else
	MATLAB_JAVA_CFG=$MATLAB_JAVA
    fi
    JRE_LOC=$DEFAULT_JRE_LOC${MATLAB_JAVA_CFG:-}
    if [ ! -d "$JRE_LOC" ]; then
	JRE_LOC=$MATLAB_JAVA_CFG
    fi
#
# Threads
#
    case "$ARCH" in
       *)
            JLIB=lib
            ;;
    esac
    JAVA_VM_PATH="$JRE_LOC/$JLIB/$JARCH/native_threads"
#
# JVM
#
    JVM_LIB_ARCH="$JRE_LOC/$JLIB/$JARCH"
    if [ "$ARCH" = "glnxa64" -o "$ARCH" = "sol64" ]; then
        VM_FLAVOR=server
    else
        VM_FLAVOR=client
    fi
    if [ -d $JVM_LIB_ARCH/$VM_FLAVOR ]; then
	JAVA_VM_PATH="$JAVA_VM_PATH:$JVM_LIB_ARCH/$VM_FLAVOR"
    elif [ -d $JVM_LIB_ARCH/hotspot ]; then
	JAVA_VM_PATH="$JAVA_VM_PATH:$JVM_LIB_ARCH/hotspot"
    elif [ -d $JVM_LIB_ARCH/classic ]; then
	JAVA_VM_PATH="$JAVA_VM_PATH:$JVM_LIB_ARCH/classic"
	_JVM_THREADS_TYPE=native_threads; export _JVM_THREADS_TYPE
    fi
    JAVA_VM_PATH="$JAVA_VM_PATH:$JRE_LOC/$JLIB/$JARCH"

#
#--------------------------------------------------------------------------
#
# Check for FVWM window manager on Linux

  # or in a glnx86) switch case
  if [ "$ARCH" = "glnx86" -o "$ARCH" = "glnxi64"  ] ; then
    if [ -f $MATLAB/bin/$ARCH/fvwmfix ]; then
      $MATLAB/bin/$ARCH/fvwmfix -quiet
    fi

  fi


#
# Augment with AWT Motif default locale resource files
#
    XFILESEARCHPATH="$JRE_LOC/lib/locale/%L/%T/%N%S:$XFILESEARCHPATH"
    export XFILESEARCHPATH
#
# Initialize LDPATH_MATLAB to include any VARIANT directory
#
    if [ "$VARIANT" != "" ]; then
        BIN_DIRS=$MATLAB/bin/$ARCH/$VARIANT:$MATLAB/bin/$ARCH
    else
        BIN_DIRS=$MATLAB/bin/$ARCH
    fi

    LDPATH_MATLAB=$MATLAB/sys/os/$ARCH:$BIN_DIRS:$MATLAB/extern/lib/$ARCH

#
# Determine how to interpret the $usemesa variable.
#
# First version: we tested for GLX, and guessed in this startup script.
# Second version: we tested at runtime, and used RPATH in glren.so
# Third version: Too many 3rd party libraries, use command line
#                option to select.

    case "$ARCH" in
	mac)
	    # MAC does not have this option
	    if [ "$usemesa" = "1" ]; then
		echo "Option -softwareopengl does not apply on MAC."
	    fi
	    ;;
	maci)
	    # MAC does not have this option
	    if [ "$usemesa" = "1" ]; then
		echo "Option -softwareopengl does not apply on MAC."
	    fi
	    ;;
	*)
	    # Look for usemesalinux startup option.
	    if [ "$usemesalinux" = "1" ]; then
		case "$ARCH" in
		    glnx86)
			usemesa=1;
			;;
		    glnxa64)
			usemesa=1;
			;;
		esac
	    fi
            # test if we have no GLX extension, and set usemesa to 1
            # we used to use 'xdpyinfo', but that would sometimes hang.
            # We can't query for glxinfo because that is also unreliable.

	    if [ "$usemesa" = "1" ]; then
		LDPATH_MATLAB=$MATLAB/sys/opengl/lib/$ARCH:$LDPATH_MATLAB
		echo "MATLAB is selecting SOFTWARE OPENGL rendering."
#	    else
#		echo "MATLAB will try and use hardware opengl."
	    fi
    esac

#
#-------------------------------------------------------------------------
#
# Determine the osg library path
#
# Note: Must come before LD_LIBRARY_PATH so MAC can add it to it library path
# as it does not support RPATH yet.

    osg="$MATLAB/sys/openscenegraph/lib/$ARCH"

    OSG_LD_LIBRARY_PATH=$osg
    export OSG_LD_LIBRARY_PATH

#
#--------------------------------------------------------------------------
#
# Determine <final_load_library_path> for each platform
#
    case "$ARCH" in
	sol*|glnx*)
	    LD_LIBRARY_PATH="`eval echo $LD_LIBRARY_PATH`"
	    LDPATH_MATLAB=$LDPATH_MATLAB:$JAVA_VM_PATH
	    if [ "$LD_LIBRARY_PATH" != "" ]; then
		LD_LIBRARY_PATH=$LDPATH_MATLAB:$LD_LIBRARY_PATH
                LD_LIB_PATHmode="$rcfilep"
	    else
		LD_LIBRARY_PATH=$LDPATH_MATLAB
                LD_LIB_PATHmode="$script"
	    fi
	    if [ "$LDPATH_PREFIX" != "" ]; then
	        LDPATH_PREFIX="`eval echo $LDPATH_PREFIX`"
	        if [ "$LDPATH_PREFIX" != "" ]; then
                    LD_LIBRARY_PATH=$LDPATH_PREFIX:$LD_LIBRARY_PATH
                    LD_LIB_PATHmode="$rcfilep"
		fi
	    fi
	    if [ "$LDPATH_SUFFIX" != "" ]; then
	        LDPATH_SUFFIX="`eval echo $LDPATH_SUFFIX`"
	        if [ "$LDPATH_SUFFIX" != "" ]; then
                    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$LDPATH_SUFFIX
                    LD_LIB_PATHmode="$rcfilep"
		fi
	    fi
            # Fix for Sun BugID 4663077
            if [ "`uname -r`" = "5.8" ]; then
                LD_LIBRARY_PATH=/usr/lib/lwp:$LD_LIBRARY_PATH
            fi
	    export LD_LIBRARY_PATH
	    ;;
	mac*)
	    # DYLD_BIND_AT_LAUNCH=1
            # export DYLD_BIND_AT_LAUNCH
	    DYLD_LIBRARY_PATH="`eval echo $DYLD_LIBRARY_PATH`"
	    LDPATH_MATLAB=$LDPATH_MATLAB
	    if [ "$DYLD_LIBRARY_PATH" != "" ]; then
		DYLD_LIBRARY_PATH=$LDPATH_MATLAB:$DYLD_LIBRARY_PATH
                LD_LIB_PATHmode="$rcfilep"
	    else
		DYLD_LIBRARY_PATH=$LDPATH_MATLAB
                LD_LIB_PATHmode="$script"
	    fi
	    if [ "$LDPATH_PREFIX" != "" ]; then
	        LDPATH_PREFIX="`eval echo $LDPATH_PREFIX`"
	        if [ "$LDPATH_PREFIX" != "" ]; then
                    DYLD_LIBRARY_PATH=$LDPATH_PREFIX:$DYLD_LIBRARY_PATH
                    LD_LIB_PATHmode="$rcfilep"
		fi
	    fi
	    if [ "$LDPATH_SUFFIX" != "" ]; then
	        LDPATH_SUFFIX="`eval echo $LDPATH_SUFFIX`"
	        if [ "$LDPATH_SUFFIX" != "" ]; then
                    DYLD_LIBRARY_PATH=$DYLD_LIBRARY_PATH:$LDPATH_SUFFIX
                    LD_LIB_PATHmode="$rcfilep"
		fi
	    fi
	    if [ -d $osg ]; then
		 DYLD_LIBRARY_PATH=$DYLD_LIBRARY_PATH:$osg
	    fi
	    export DYLD_LIBRARY_PATH
	    ;;
	*)
	    LD_LIBRARY_PATH="`eval echo $LD_LIBRARY_PATH`"
	    LDPATH_MATLAB=$LDPATH_MATLAB
	    if [ "$LD_LIBRARY_PATH" != "" ]; then
		LD_LIBRARY_PATH=$LDPATH_MATLAB:$LD_LIBRARY_PATH
                LD_LIB_PATHmode="$rcfilep"
	    else
		LD_LIBRARY_PATH=$LDPATH_MATLAB
                LD_LIB_PATHmode="$script"
	    fi
	    if [ "$LDPATH_PREFIX" != "" ]; then
	        LDPATH_PREFIX="`eval echo $LDPATH_PREFIX`"
	        if [ "$LDPATH_PREFIX" != "" ]; then
                    LD_LIBRARY_PATH=$LDPATH_PREFIX:$LD_LIBRARY_PATH
                    LD_LIB_PATHmode="$rcfilep"
		fi
	    fi
	    if [ "$LDPATH_SUFFIX" != "" ]; then
	        LDPATH_SUFFIX="`eval echo $LDPATH_SUFFIX`"
	        if [ "$LDPATH_SUFFIX" != "" ]; then
                    LD_LIBRARY_PATH=$LD_LIBRARY_PATH:$LDPATH_SUFFIX
                    LD_LIB_PATHmode="$rcfilep"
		fi
	    fi
	    export LD_LIBRARY_PATH
	    ;;
    esac

#--------------------------------------------------------------------------
#
# Increase the data segment size to unlimited for Maple libraries.
#
    if [ "$ARCH" = "mac" -o "$ARCH" = "maci" -o "$ARCH" = "maci64" ]; then
        ulimit -d unlimited
    fi

#
#--------------------------------------------------------------------------
#
# SHELL must currently be defined. (problem showed up on Solaris)
#
    if [ "$SHELL" = "" ]; then 
        SHELLmode="$script"
	SHELL="/bin/sh"
    fi
#
#--------------------------------------------------------------------------
#
# Be sure that X sees the Matlab Resource Database (X11/R5).
#
# The critical thing that can block access to the $XAPPLRESDIR/Matlab
# database is the existence of the XUSERFILESEARCHPATH variable. If
# it exists then it does NOT automatically use $XAPPLRESDIR/Matlab even if
# it is not part of the XUSERFILESEARCHPATH path variable.
#
    if [ "$XUSERFILESEARCHPATH" != "" ]; then
        XAPPLRESDIRmode="$environp"
	XUSERFILESEARCHPATH=$XUSERFILESEARCHPATH:$XAPPLRESDIR/%N
	export XUSERFILESEARCHPATH
    fi
#
    BASEMATLABPATH=$MATLABPATH; export BASEMATLABPATH
#
#--------------------------------------------------------------------------
#
# Add on $HOME/matlab if available and $MATLAB/toolbox/local
#

    if [ -d "$HOME"/matlab ]; then
	MATLABPATH=$MATLABPATH:"$HOME"/matlab
    fi
    MATLABPATH=$MATLABPATH:$MATLAB/toolbox/local
#
# Remove any leading ":" character from the path. Can't use awk
# here because it fails on very long paths.
#
    MATLABPATH=`echo $MATLABPATH | sed 's/^://'`
#
#--------------------------------------------------------------------------
#
# Check OS version
#
    if [ -f $MATLAB_UTIL_DIR/oscheck.sh ]; then
	. $MATLAB_UTIL_DIR/oscheck.sh
	if [ "$oscheck_status" = "1" ]; then
	    exit 1
	fi
    fi
#
#--------------------------------------------------------------------------
#
# Set a floor on the maximum number of file descriptors that can be opened.
# The user can always set something higher before calling MATLAB.
#
    FLOOR_OPEN_FILES=256
    MAX_OPEN_FILES=`ulimit -n`
    MAX_OPEN_FILESmode='e '
    if [ $MAX_OPEN_FILES -lt $FLOOR_OPEN_FILES ]; then
        ulimit -n $FLOOR_OPEN_FILES 2>/dev/null
        if [ $? -eq 0 ]; then
            MAX_OPEN_FILESmode='s '
            MAX_OPEN_FILES=`ulimit -n`
        fi
    fi
#
#--------------------------------------------------------------------------
#
    if [ "$showenv" = "1" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    (
    undefined='(variable not defined)'
    echo '------------------------------------------------------------------------'
	if [ "$SOURCED_DIR" != "" ]; then
    echo "->      (.matlab7rc.sh) sourced from directory (DIR = $SOURCED_DIR)"
    echo "->      DIR = $SOURCED_DIReval"
	else
    echo "->      (.matlab7rc.sh) not found."
	fi
    echo '------------------------------------------------------------------------'
    echo '        a = argument  e = environment  r = rcfile  s = script'
    echo '------------------------------------------------------------------------'
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo "->  $MATLABmode  MATLAB              = $MATLAB"
    echo "->      LM_LICENSE_FILE     = ${LM_LICENSE_FILE-$undefined}"
    echo "->      MLM_LICENSE_FILE    = ${MLM_LICENSE_FILE-$undefined}"
    echo "->  $AUTOMOUNT_MAPmode  AUTOMOUNT_MAP       = $AUTOMOUNT_MAP"
    echo "->  $DISPLAYmode  DISPLAY             = $DISPLAY"
    echo "->  $ARCHmode  ARCH                = $ARCH"
    echo "->  $TOOLBOXmode  TOOLBOX             = $TOOLBOX"
	if [ "$XUSERFILESEARCHPATH" != "" ]; then
    echo "->  $XAPPLRESDIRmode  XUSERFILESEARCHPATH = $XUSERFILESEARCHPATH"
	else
    echo "->  $XAPPLRESDIRmode  XAPPLRESDIR         = $XAPPLRESDIR"
	fi
    echo "->  $XKEYSYMDBmode  XKEYSYMDB           = $XKEYSYMDB"
#
# For maximum number of open file descriptors
#
    echo "->  $MAX_OPEN_FILESmode  MAX_OPEN_FILES      = $MAX_OPEN_FILES"
#
# For java
#
    echo "->  s   _JVM_THREADS_TYPE   = $_JVM_THREADS_TYPE"
    echo "->  e   MATLAB_JAVA         = $MATLAB_JAVA"
#
    echo "->  $MATLAB_MEM_MGRmode  MATLAB_MEM_MGR      = $MATLAB_MEM_MGR"
    echo "->  $MATLAB_DEBUGmode  MATLAB_DEBUG        = $MATLAB_DEBUG"
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	case "$ARCH" in
	    sol*|glnx*)
    echo "->  $LD_LIB_PATHmode  LD_LIBRARY_PATH     = $LD_LIBRARY_PATH"
		;;
	    *)
    echo "->  $LD_LIB_PATHmode  LD_LIBRARY_PATH     = $LD_LIBRARY_PATH"
		;;
	esac
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo "->  $argument  arglist             = $arglist"
    echo "->  $SHELLmode  SHELL               = $SHELL"
    echo "->  e   PATH                = $PATH"					
    echo " "									) > $temp_file
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    fi
#
# Cannot locate JRE
#
    if [ ! -d "$JRE_LOC" -a "$jvmflag" = "1" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
(
echo "---------------------------------------------------------------------------"
echo "Warning: Cannot locate Java Runtime Environment (JRE) . . ."
echo " "
echo "         1. Either a correct JRE was not available for redistribution when"
echo "            this release was shipped, in which case you should refer to the"
echo "            Release Notes for additional information about how to get it."
echo " "
echo "         2. Or you have tried to use the MATLAB_JAVA environment variable"
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	if [ "$showenv" != "1" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
echo "            to specify an alternate JRE, but MATLAB cannot find it.  Please"
echo "            run 'matlab -n' to determine what value you are using for"
echo "            MATLAB_JAVA and fix accordingly."                                
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	else
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
echo "            to specify an alternate JRE, but MATLAB cannot find it.  Check"
echo "            the value of MATLAB_JAVA above and fix accordingly."                                
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	fi
echo "---------------------------------------------------------------------------" ) >> $temp_file
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	if [ "$showenv" != "1" ]; then
	    cat $temp_file
	    rm -f $temp_file
	else
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo " "									>> $temp_file
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	fi
    fi
#
    if [ "$showenv" = "1" ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
(
    echo "->  $MATLABPATHmode  MATLABPATH          = (initial version)"
	if [ "$MATLABPATH" != "" ]; then
	    for dir in `echo $MATLABPATH | tr ':' ' '`
	    do
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo "	$dir"
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	    done
	fi
#
    echo " "
        if [ -f $MATLAB/bin/$ARCH/$VARIANTmatlab -a -f $MATLAB/bin/ldd ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo '->      $MATLAB/bin/'"$ARCH/$VARIANTmatlab shared library information -"
    echo "|-----------------------------------------------------------------------"
            $MATLAB/bin/ldd -$ARCH $MATLAB/bin/$ARCH/$VARIANTmatlab 2>/dev/null | awk '{ print "| " $0 }'
    echo "|-----------------------------------------------------------------------"
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
        fi
#
    echo " "
    echo '->      $MATLAB/toolbox/local/pathdef.m -'
    echo "|-----------------------------------------------------------------------"
	if [ -f $MATLAB/toolbox/local/pathdef.m ]; then
	    cat $MATLAB/toolbox/local/pathdef.m | awk '{ print "| " $0 }'
	else
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo '    Warning: $MATLAB/toolbox/local/pathdef.m not found . . .'
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	fi
    echo "|-----------------------------------------------------------------------"
#
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo '------------------------------------------------------------------------') >> $temp_file
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	more $temp_file
        rm -f $temp_file
	if [ "$showenv_all" != "1" ]; then
	     exit 0
	fi
    fi
#
# Export the variables
#
    export MATLAB
    export AUTOMOUNT_MAP
    export DISPLAY
    export ARCH
    export TOOLBOX
    export MATLABPATH
    export XAPPLRESDIR
    export XKEYSYMDB
    if [ "$MATLAB_MEM_MGR" != "" ]; then
        export MATLAB_MEM_MGR
    fi
    export MATLAB_DEBUG
    export SHELL

#
# Start MATLAB unless we were asked to simply set the environment
#
    if [ "$SOURCE_MATLAB_ENV_FROM" = "" ]; then

      if [ ! -d $MATLAB/bin/$ARCH ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ''
    echo '    matlab: No MATLAB bin directory for this machine architecture.'
    echo ''       
    echo "           ARCH = $ARCH" 
    echo ''
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	if [ "$showenv_all" = "1" ]; then
	   env
	fi
        exit 1
      fi
#
      if [ ! -f $MATLAB/bin/$ARCH/$VARIANTmatlab ]; then
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
    echo ''
    echo "	matlab: No MATLAB executable for this machine architecture."
    echo ''       
    echo "           $MATLAB/bin/$ARCH/$VARIANTmatlab does not exist!"
    echo ''
#++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++++
	if [ "$showenv_all" = "1" ]; then
	   env
	fi
        exit 1
      fi
#
      exec_path=$MATLAB/bin/$ARCH/$VARIANTmatlab
#
      case "$ARCH" in
        sol*)
	    if [ -d $MATLAB/rtw/bin/$ARCH ]; then
	        PATH=$MATLAB/rtw/bin/$ARCH:$PATH; export PATH
	    fi
            if [ "$debugger" != "" ]; then
                if [ "$MATLAB_DEBUG" = "gdb" -o "$MATLAB_DEBUG" = "xxgdb" ]; then
                    SHELL=/bin/sh; export SHELL
                fi
		if [ "$showenv_all" = "1" ]; then
		    env
		    exit 0
	        fi
		eval exec $debugger $exec_path $arglist
            else
		if [ "$showenv_all" = "1" ]; then
		    env
		    exit 0
	        fi
		eval exec $exec_path $arglist
            fi
	    ;;
        *)
            if [ "$debugger" != "" ]; then
                if [ "$MATLAB_DEBUG" = "gdb" -o "$MATLAB_DEBUG" = "xxgdb" ]; then
                    SHELL=/bin/sh; export SHELL
                fi
		if [ "$showenv_all" = "1" ]; then
		    env
		    exit 0
	        fi
		eval exec $debugger $exec_path $arglist
            else
		if [ "$showenv_all" = "1" ]; then
		    env
		    exit 0
	        fi
		eval exec $exec_path $arglist
            fi
	    ;;
      esac
    fi
```

---

### Post by tramir on 2008-07-12
Can you post the output of "matlab -e"? There seem to be some problems in initializing some of these environment variables and I'm trying to figure out where/why.

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ matlab -e
ARCH=glnx86
LESSOPEN=| /usr/bin/lesspipe %s
GNOME_KEYRING_PID=6428
USER=chris
GNOME_KEYRING_SOCKET=/tmp/keyring-HMejwE/socket
LD_LIBRARY_PATH=/home/chris/sys/os/glnx86:/home/chris/bin/glnx86:/home/chris/extern/lib/glnx86:/usr/lib/jvm/java-6-sun/jre//lib/i386/native_threads:/usr/lib/jvm/java-6-sun/jre//lib/i386/client:/usr/lib/jvm/java-6-sun/jre//lib/i386:/home/chris/matlab2008a/sys/os/glnx86/:
SHLVL=1
BASEMATLABPATH=
XKEYSYMDB=/home/chris/X11/app-defaults/XKeysymDB
AUTOMOUNT_MAP=
OLDPWD=/home/chris
HOME=/home/chris
DESKTOP_SESSION=default
XDG_SESSION_COOKIE=52baab6828273fdd162eb3104843b550-1215872165.429458-1126476169
GTK_RC_FILES=/etc/gtk/gtkrc:/home/chris/.gtkrc-1.2-gnome2
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-v9kTgEXJQS,guid=c988f353ef32fd0124db9c724878bca7
GDM_XSERVER_LOCATION=local
COLORTERM=gnome-terminal
LOGNAME=chris
MATLABPATH=/home/chris/toolbox/local
_=/home/chris/bin/matlab
WINDOWID=65011805
USERNAME=chris
TERM=xterm
GNOME_DESKTOP_SESSION_ID=Default
WINDOWPATH=7
HISTCONTROL=ignoreboth
GDM_LANG=en_US.UTF-8
SESSION_MANAGER=local/chris-laptop:/tmp/.ICE-unix/6429
PATH=/home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/
TOOLBOX=/home/chris/toolbox
LIBXCB_ALLOW_SLOPPY_LOCK=1
DISPLAY=:0.0
LANG=en_US.UTF-8
DESKTOP_STARTUP_ID=
XAUTHORITY=/home/chris/.Xauthority
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SSH_AUTH_SOCK=/tmp/keyring-HMejwE/ssh
XFILESEARCHPATH=/usr/lib/jvm/java-6-sun/jre//lib/locale/%L/%T/%N%S:
MATLAB=/home/chris
SHELL=/bin/bash
GDMSESSION=default
LESSCLOSE=/usr/bin/lesspipe %s %s
OSG_LD_LIBRARY_PATH=/home/chris/sys/openscenegraph/lib/glnx86
XAPPLRESDIR=/home/chris/X11/app-defaults
GPG_AGENT_INFO=/tmp/seahorse-Dl1aof/S.gpg-agent:6482:1
PWD=/home/chris
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/

```

---

### Post by tramir on 2008-07-12
Let's try the following changes. Open again the matlab file and change the lines
```
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86/:$LD_LIBRARY_PATH
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

```
to
```
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre

```

That is, drop the "/" and the "$LD_LIBRARY_PATH in the first line and the last "/" in the second line. And try running matlab again :)

---

### Post by link- on 2008-07-12
> **tramir said:**
> Let's try the following changes. Open again the matlab file and change the lines
```
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86/:$LD_LIBRARY_PATH
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre/

```
to
```
export LD_LIBRARY_PATH=/home/chris/matlab2008a/sys/os/glnx86
export MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre

```

That is, drop the "/" and the "$LD_LIBRARY_PATH in the first line and the last "/" in the second line. And try running matlab again :)
```

chris@chris-laptop:~$ ---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /home/chris/sys/java/jre/glnx86/jre does not exist.
---------------------------------------------------------------------------
```

---

### Post by tramir on 2008-07-12
Let's try a "last-resort solution":
```
ln -s /usr/lib/jvm/java-6-sun/jre /home/chris/sys/java/jre/glnx86/jre
```
And, again, try running matlab...

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ ln -s /usr/lib/jvm/java-6-sun/jre /home/chris/sys/java/jre/glnx86/jre
ln: creating symbolic link `/home/chris/sys/java/jre/glnx86/jre': No such file or directory
chris@chris-laptop:~$ matlab
chris@chris-laptop:~$ ---------------------------------------------------------------------------
Error: Cannot locate Java Runtime Environment (JRE).
The directory /home/chris/sys/java/jre/glnx86/jre does not exist.
---------------------------------------------------------------------------
```

---

### Post by tramir on 2008-07-12
There's a "matlab2008a" that's lost there. It can't find the JRE because the folder is "/home/chris/**matlab2008a**/sys/java/jre/glnx86/jre", NOT "/home/chris/sys/java/jre/glnx86/jre". Can you post again the output of "matlab -e"?

---

### Post by link- on 2008-07-12
> **tramir said:**
> There's a "matlab2008a" that's lost there. It can't find the JRE because the folder is "/home/chris/**matlab2008a**/sys/java/jre/glnx86/jre", NOT "/home/chris/sys/java/jre/glnx86/jre". Can you post again the output of "matlab -e"?
```
chris@chris-laptop:~$ matlab -e
ARCH=glnx86
LESSOPEN=| /usr/bin/lesspipe %s
GNOME_KEYRING_PID=6428
USER=chris
GNOME_KEYRING_SOCKET=/tmp/keyring-HMejwE/socket
LD_LIBRARY_PATH=/home/chris/sys/os/glnx86:/home/chris/bin/glnx86:/home/chris/extern/lib/glnx86:/usr/lib/jvm/java-6-sun/jre/lib/i386/native_threads:/usr/lib/jvm/java-6-sun/jre/lib/i386/client:/usr/lib/jvm/java-6-sun/jre/lib/i386:/home/chris/matlab2008a/sys/os/glnx86
SHLVL=1
BASEMATLABPATH=
XKEYSYMDB=/home/chris/X11/app-defaults/XKeysymDB
AUTOMOUNT_MAP=
OLDPWD=/home/chris
HOME=/home/chris
DESKTOP_SESSION=default
XDG_SESSION_COOKIE=52baab6828273fdd162eb3104843b550-1215872165.429458-1126476169
GTK_RC_FILES=/etc/gtk/gtkrc:/home/chris/.gtkrc-1.2-gnome2
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-v9kTgEXJQS,guid=c988f353ef32fd0124db9c724878bca7
GDM_XSERVER_LOCATION=local
COLORTERM=gnome-terminal
LOGNAME=chris
MATLABPATH=/home/chris/toolbox/local
_=/home/chris/bin/matlab
WINDOWID=65011805
USERNAME=chris
TERM=xterm
GNOME_DESKTOP_SESSION_ID=Default
WINDOWPATH=7
HISTCONTROL=ignoreboth
GDM_LANG=en_US.UTF-8
SESSION_MANAGER=local/chris-laptop:/tmp/.ICE-unix/6429
PATH=/home/chris/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
MATLAB_JAVA=/usr/lib/jvm/java-6-sun/jre
TOOLBOX=/home/chris/toolbox
LIBXCB_ALLOW_SLOPPY_LOCK=1
DISPLAY=:0.0
LANG=en_US.UTF-8
DESKTOP_STARTUP_ID=
XAUTHORITY=/home/chris/.Xauthority
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SSH_AUTH_SOCK=/tmp/keyring-HMejwE/ssh
XFILESEARCHPATH=/usr/lib/jvm/java-6-sun/jre/lib/locale/%L/%T/%N%S:
MATLAB=/home/chris
SHELL=/bin/bash
GDMSESSION=default
LESSCLOSE=/usr/bin/lesspipe %s %s
OSG_LD_LIBRARY_PATH=/home/chris/sys/openscenegraph/lib/glnx86
XAPPLRESDIR=/home/chris/X11/app-defaults
GPG_AGENT_INFO=/tmp/seahorse-Dl1aof/S.gpg-agent:6482:1
PWD=/home/chris
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/

```

---

### Post by tramir on 2008-07-12
OK, I think I have an idea of what's going on. Matlab tries to figure out which directory it's installed in by using the parent of the directory from which it's run. Since you (implicitly) run matlab from /home/chris/bin, it thinks that it's installed in /home/chris (hence the value of MATLAB in the output of "matlab -e"). But it is actually installed in /home/chris/matlab2008a. So we need to figure out a way to let it know it's there. Can you copy the file matlab from /home/chris/bin to /home/chris/matlab2008a/bin? I guess there should be a directory called something like that. If it gives an error that you're not allowed to copy it, then do it from the terminal:

```
sudo cp ~/bin/matlab ~/matlab2008a/bin/
```

Then, run the matlab we just created:

```
~/matlab2008a/bin/matlab
```

---

### Post by link- on 2008-07-12
```
chris@chris-laptop:~$ sudo cp ~/bin/matlab ~/matlab2008a/bin/
[sudo] password for chris: 
chris@chris-laptop:~$ ~/matlab2008a/bin/matlab

```
Matlab ran after that.
I guess you were right.

---

### Post by tramir on 2008-07-12
Great! If that didn't work, I was losing all hope in humankind :) 

Then the last thing you need to do is to change the default "matlab" that gets run, so that you don't have to type the full path every time:

```
mv ~/bin/matlab ~/bin/matlab_old
ln -s ~/matlab2008a/bin/matlab ~/bin/
```

From there on, you should only need to type "matlab" and it should run.

---

### Post by tramir on 2008-07-12
Also, don't forget to mark the thread as solved -- maybe other people will run into similar problems and this'll help them find a way out.

---

### Post by link- on 2008-07-12
Yes...that made it.

Thanks a lot for the help. =D>

---

### Post by tramir on 2008-07-12
Glad I could help - that's what this great community is for!

---

### Post by hugmenot on 2008-07-16
Maybe it would have been quicker if he had cleanly uninstalled everything, his ~/matlab2008a and his ~/.matlab.

But you got there so happy hacking.

---

### Post by jhaitas on 2009-01-23
the following command will fix the problem without all the aforementioned nonsense

```
sudo chown -R ${USER}:${USER} ~/.matlab
```

---

### Post by bigstras on 2009-01-26
one more tip: 
if you want matlab to run without having to keep the terminal window open and have no splash screen, you can run the command like this:
```
matlab -desktop -nosplash &
```
you can also make it into a launcher on your desktop.

---

### Post by jolindbe on 2009-03-03
I've got the same issue, but the solution doesn't work for me. My output of matlab -e shows

```
ARCH=glnx86
LESSOPEN=| /usr/bin/lesspipe %s
GNOME_KEYRING_PID=5816
USER=johan
GNOME_KEYRING_SOCKET=/tmp/keyring-GaE4M9/socket
LD_LIBRARY_PATH=/opt/matlab/sys/os/glnx86:/opt/matlab/bin/glnx86:/opt/matlab/extern/lib/glnx86:/opt/matlab/sys/java/jre/glnx86/jre/lib/i386/native_threads:/opt/matlab/sys/java/jre/glnx86/jre/lib/i386/client:/opt/matlab/sys/java/jre/glnx86/jre/lib/i386
SHLVL=1
ORBIT_SOCKETDIR=/tmp/orbit-johan
BASEMATLABPATH=
XKEYSYMDB=/opt/matlab/X11/app-defaults/XKeysymDB
AUTOMOUNT_MAP=
OLDPWD=/opt/matlab
HOME=/home/johan
DESKTOP_SESSION=default
XDG_SESSION_COOKIE=39a55cf2dd45b3b954cf8ff44971f625-1236066604.87083-2041716129
GTK_RC_FILES=/etc/gtk/gtkrc:/home/johan/.gtkrc-1.2-gnome2
DBUS_SESSION_BUS_ADDRESS=unix:abstract=/tmp/dbus-0mfzJBzTuJ,guid=0b9f7deb0b8350e48f2ba28749ace12d
GDM_XSERVER_LOCATION=local
PGPLOT_FONT=/home/johan/Dokument/Exjobb/pgplot/dist/grfont.dat
COLORTERM=gnome-terminal
LOGNAME=johan
MATLABPATH=/opt/matlab/toolbox/local
_=/usr/local/bin/matlab
WINDOWID=58720459
USERNAME=johan
TERM=xterm
GNOME_DESKTOP_SESSION_ID=this-is-deprecated
WINDOWPATH=7
HISTCONTROL=ignoreboth
GDM_LANG=sv_SE.UTF-8
SESSION_MANAGER=local/wasa:/tmp/.ICE-unix/5827
PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/usr/games
TOOLBOX=/opt/matlab/toolbox
DISPLAY=:0.0
LANG=sv_SE.UTF-8
XAUTHORITY=/home/johan/.Xauthority
LS_COLORS=no=00:fi=00:di=01;34:ln=01;36:pi=40;33:so=01;35:do=01;35:bd=40;33;01:cd=40;33;01:or=40;31;01:su=37;41:sg=30;43:tw=30;42:ow=34;42:st=37;44:ex=01;32:*.tar=01;31:*.tgz=01;31:*.svgz=01;31:*.arj=01;31:*.taz=01;31:*.lzh=01;31:*.lzma=01;31:*.zip=01;31:*.z=01;31:*.Z=01;31:*.dz=01;31:*.gz=01;31:*.bz2=01;31:*.bz=01;31:*.tbz2=01;31:*.tz=01;31:*.deb=01;31:*.rpm=01;31:*.jar=01;31:*.rar=01;31:*.ace=01;31:*.zoo=01;31:*.cpio=01;31:*.7z=01;31:*.rz=01;31:*.jpg=01;35:*.jpeg=01;35:*.gif=01;35:*.bmp=01;35:*.pbm=01;35:*.pgm=01;35:*.ppm=01;35:*.tga=01;35:*.xbm=01;35:*.xpm=01;35:*.tif=01;35:*.tiff=01;35:*.png=01;35:*.svg=01;35:*.mng=01;35:*.pcx=01;35:*.mov=01;35:*.mpg=01;35:*.mpeg=01;35:*.m2v=01;35:*.mkv=01;35:*.ogm=01;35:*.mp4=01;35:*.m4v=01;35:*.mp4v=01;35:*.vob=01;35:*.qt=01;35:*.nuv=01;35:*.wmv=01;35:*.asf=01;35:*.rm=01;35:*.rmvb=01;35:*.flc=01;35:*.avi=01;35:*.fli=01;35:*.gl=01;35:*.dl=01;35:*.xcf=01;35:*.xwd=01;35:*.yuv=01;35:*.aac=00;36:*.au=00;36:*.flac=00;36:*.mid=00;36:*.midi=00;36:*.mka=00;36:*.mp3=00;36:*.mpc=00;36:*.ogg=00;36:*.ra=00;36:*.wav=00;36:
SSH_AUTH_SOCK=/tmp/keyring-GaE4M9/ssh
XFILESEARCHPATH=/opt/matlab/sys/java/jre/glnx86/jre/lib/locale/%L/%T/%N%S:
MATLAB=/opt/matlab
SHELL=/bin/bash
GDMSESSION=default
LESSCLOSE=/usr/bin/lesspipe %s %s
OSG_LD_LIBRARY_PATH=/opt/matlab/sys/openscenegraph/lib/glnx86
XAPPLRESDIR=/opt/matlab/X11/app-defaults
GPG_AGENT_INFO=/tmp/seahorse-kpxJAh/S.gpg-agent:5902:1
PWD=/usr/local/bin
XDG_DATA_DIRS=/usr/local/share/:/usr/share/:/usr/share/gdm/

```

My matlab is installed in /opt/matlab, and I've got a file named matlab files both in /opt/matlab/bin/ and /usr/local/bin

EDIT: By chown-ing all files in all matlab folders, I managed to get rid of the errors.

---

### Post by freak42 on 2009-03-03
I also have the command ```
matlab -desktop
```as my launcher command, no problems with it..

---

### Post by J-F on 2009-05-11
The only reason I registered is to say THANK YOU to all of those who contributed to this thread.

---

### Post by jhaitas on 2009-05-11
J-F you are very welcome. I would like to amend my previous advice...

to fix the permissions problem the following command should work every time.

```
sudo chown -R ${USER}:${USER} ~/.matlab
```

I have updated the Ubuntu Community Documentation for MATLAB.

It should address issues regarding installing MATLAB on Ubuntu.

Let me know if there are gaps in information.

You can find the documentation at:

[https://help.ubuntu.com/community/MATLAB]("https://help.ubuntu.com/community/MATLAB")

---

### Post by lethalfang on 2009-05-12
When I install matlab, I use "sudo chmod" to allow myself to write into the directory that I am about to install matlab, and then install matlab as user (i.e., ./install as supposed to sudo ./install), then I reset the permission after installation is complete.  
It makes things a bit easier to me, since now I know that every file I've created during matlab installation has the ownership that I can access without sudo.

---

### Post by jhaitas on 2009-05-12
> **lethalfang said:**
> When I install matlab, I use "sudo chmod" to allow myself to write into the directory that I am about to install matlab, and then install matlab as user (i.e., ./install as supposed to sudo ./install), then I reset the permission after installation is complete.  
It makes things a bit easier to me, since now I know that every file I've created during matlab installation has the ownership that I can access without sudo.

lethalfang,
You can do this if you want. But MATLAB is designed so that only the administrator should have permission to modify files available to all users on the system. If you need to modify any functions, you can create your own local version of the file. For example, you can create a sin.m file in your working directory to replace the MATLAB version of the sin() function. This way other users on the system will not be affected by your modifications (unless you choose to share with them).

I am glad you choose Ubuntu over alternatives. Welcome to the community.

---

### Post by bender1234 on 2009-08-29
Thank you guys.

Setting proper permissions for the entire .matlab directory solved the issue.

---

### Post by emanuelvianna on 2010-04-06
Thanks! It works for me!

I have to do two changes in the standard Matlab installation:

1. Add a launcher with "-desktop" argument in GNOME menu (which has not been created)
    ### /usr/share/applications/matlab.desktop ###
    [Desktop Entry]
    Version=7.8
    Name=Matlab
    GenericName=Matlab R2009a
    Comment=Matlab R2009a: The Language of Technical Computing
    Exec=sh /opt/matlab/bin/matlab -desktop
    Icon=/home/bob/Pictures/matlab.png
    StartupNotify=true
    Terminal=false
    Type=Application
    Categories=Application;Office;

2. Change the matlab preference file permissions (as you said):
    $ sudo chown -R bob /home/bob/.matlab/

---

### Post by Gemechu on 2013-01-22
> **tramir said:**
> I don't think the issue was running Matlab as root, but rather why it only works when run as root. Here's what I think happened: during the installation (which was done as root), Matlab created the .matlab folder and/or some files in it. Which means that, when you try to run it as user "chris" and overwrite those files, you're going to get errors because you're not allowed to write over files owned by root. So the idea is to "reclaim" those files to yourself - there's no reason I can think of that "root" should have files in your .matlab folder. The one file you identified is that matlab.prf file, that's why I told you to chown it to yourself. Alternatively, you could try to chown the folder and everything in it, that might be an even safer way to go:
```
sudo chown -R chris /home/chris/.matlab
```Let us know if it worked.
Worked like charm. Great!

---

### Post by jhaitas on 2013-01-22
Rather use:

```
sudo chown -R ${USER}:${USER} ${HOME}/.matlab
```

This will work no matter what your username is and what your home directory is.

---

