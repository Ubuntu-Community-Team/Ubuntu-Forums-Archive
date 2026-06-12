---
title: "Compile c files from matlab"
date: 2010-04-22
forum: Packaging and Compiling Programs
---

### Post by souraklis on 2010-04-22
Hello there i ve just installed matlab in Ubuntu and I want to compile via Matlab some c files. To be more specific i want to compile the library libSVM via MATLAB. The first step is to chooce compiler from the matlab so i typed the command 

mex -setup

Then i had 3 choices
[HTML]  1: /usr/local/matlab1212/bin/f90opts.sh : 
      Template Options file for building Fortran 90 MEX-files via the system ANSI compiler
 
  2: /usr/local/matlab1212/bin/gccopts.sh : 
      Template Options file for building gcc MEX-files
 
  3: /usr/local/matlab1212/bin/mexopts.sh : 
      Template Options file for building MEX-files via the system ANSI compiler[/HTML]

Afterthat i tried all of them as a choice for compilation and i got this message:

[HTML]cp: cannot create regular file `/home/zenitis/.matlab/R2008a/mexopts.sh': Permission denied

**************************************************************************
  Warning: The MATLAB C and Fortran API has changed to support MATLAB 
           variables with more than 2^32-1 elements.  In the near future 
           you will be required to update your code to utilize the new 
           API. You can find more information about this at: 
           http://www.mathworks.com/support/solutions/data/1-5C27B9.html?solution=1-5C27B9 
           Building with the -largeArrayDims option enables the new API. 
**************************************************************************[/HTML]

Any idea about what is happened or where can i find a more suitable compiler??

---

### Post by SevenMachines on 2010-04-22
hi, it look like the problem might be more the cp permission denied error than the warning that follows. sadly i dont have matlab so i cant verfiy anything but you might want to try creating the directory manually
$mkdir -p /home/zenitis/.matlab/R2008a/

or if it exists, check the ownership of that directory and change it if needs be, ie, something like
$chown -R zenitis.zenitis /home/zenitis/.matlab/R2008a/

if you can post more output if the above options dont work out that would be great

---

### Post by souraklis on 2010-04-22
ok i create the directory and i tried this $ chown -R zenitis.zenitis /home/zenitis/.matlab/R2008a/

and i had this:

```
zenitis@zenitis-laptop:~$ chown -R zenitis.zenitis /home/zenitis/.matlab/R2008a/
chown: changing ownership of `/home/zenitis/.matlab/R2008a/cwdhistory.m': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/history.m': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/MATLABDesktop.xml': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/toolbox_cache-7.6.0-851536275-glnx86.xml': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/matlab.prf': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/MLintDefaultSettings.txt': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/shortcuts.xml': Operation not permitted
chown: changing ownership of `/home/zenitis/.matlab/R2008a/': Operation not permitted

```

---

### Post by SevenMachines on 2010-04-22
hi, the example was assuming that zenitis was your username. if your create the directory then you dont need to change the ownership anyway. with the directory existing does compilation (as the same user that owns the directory) proceed any further?

---

### Post by souraklis on 2010-04-22
Nop i got the same if it helps the sh that it is created is this:
```
java.io.FileNotFoundException: /home/zenitis/.matlab/R2008a/MATLABDesktop.xml (Permission denied)
	at java.io.FileOutputStream.open(Native Method)
	at java.io.FileOutputStream.<init>(Unknown Source)
	at java.io.FileOutputStream.<init>(Unknown Source)
	at com.mathworks.mwswing.desk.Desktop.saveLayout(Desktop.java:3446)
	at com.mathworks.mwswing.desk.Desktop.close(Desktop.java:3938)
	at com.mathworks.mwswing.desk.Desktop$DeferredCloser.run(Desktop.java:4014)
	at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEventAdapter.executeOnSwingThread(SynchronousInvokeUtility.java:94)
	at com.mathworks.mwswing.SynchronousInvokeUtility$SynchronousEvent.run(SynchronousInvokeUtility.java:112)
	at com.mathworks.jmi.AWTUtilities$Invoker$4.runWithOutput(AWTUtilities.java:409)
	at com.mathworks.jmi.AWTUtilities$Invoker$1.run(AWTUtilities.java:331)
	at java.awt.event.InvocationEvent.dispatch(Unknown Source)
	at java.awt.EventQueue.dispatchEvent(Unknown Source)
	at java.awt.EventDispatchThread.pumpOneEventForFilters(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForFilter(Unknown Source)
	at java.awt.EventDispatchThread.pumpEventsForHierarchy(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.pumpEvents(Unknown Source)
	at java.awt.EventDispatchThread.run(Unknown Source)
```

---

### Post by SevenMachines on 2010-04-22
i thought MATLABDesktop.xml was a user preference config file to be honest. This will really need a matlab user to look into. i might have an old copy but it'll be a while before i can dig it out

---

### Post by souraklis on 2010-04-22
Nevermind i m sure that i ll find. Thanks a lot dude from your help!!

---

