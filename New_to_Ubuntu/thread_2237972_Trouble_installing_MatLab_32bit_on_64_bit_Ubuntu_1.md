---
title: "Trouble installing MatLab 32bit on 64 bit Ubuntu 14.04"
date: 2014-08-05
forum: New to Ubuntu
---

### Post by briansfractal on 2014-08-05
Hi ^_^

I'm trying to install 32bit MatLab R2011a on a 64 bit Ubuntu 14.04 . I've read there is a chance it is impossible, but I'm still trying and hopefully I can get MatLab to work with your help. 
The problem is MatLab goes through the installation and is even activated. But when I type 'matlab' in terminal this appears:

/usr/local/bin/matlab: 1: /usr/local/MATLAB/R2011a_Student/bin/util/oscheck.sh: /lib64/libc.so.6: not found---------------------------------------------------------------------------
Warning: Cannot locate Java Runtime Environment (JRE) . . .
 
         1. Either a correct JRE was not available for redistribution when
            this release was shipped, in which case you should refer to the
            Release Notes for additional information about how to get it.
 
         2. Or you have tried to use the MATLAB_JAVA environment variable
            to specify an alternate JRE, but MATLAB cannot find it.  Please
            run 'matlab -n' to determine what value you are using for
            MATLAB_JAVA and fix accordingly.
---------------------------------------------------------------------------


    matlab: No MATLAB bin directory for this machine architecture.


           ARCH = glnxa64



I tried to install lib64 and libc by typing
'sudo apt-get install lib64:i386 libc:i386'
but it didn't change the output when I type 
'matlab'
in the terminal.

I also typed 
'matlab -n'   
the output I believe is important is:

/usr/local/bin/matlab: 1: /usr/local/MATLAB/R2011a_Student/bin/util/oscheck.sh: /lib64/libc.so.6: not found
------------------------------------------------------------------------
->      (.matlab7rc.sh) sourced from directory (DIR = $MATLAB/bin)
->      DIR = /usr/local/MATLAB/R2011a_Student/bin
------------------------------------------------------------------------
        a = argument  e = environment  r = rcfile  s = script
------------------------------------------------------------------------
->  r   MATLAB              = /usr/local/MATLAB/R2011a_Student
->      LM_LICENSE_FILE     = (variable not defined)
->      MLM_LICENSE_FILE    = (variable not defined)
->  s   AUTOMOUNT_MAP       = 
->  e   DISPLAY             = :0
->  r   ARCH                = glnxa64
->  s   TOOLBOX             = /usr/local/MATLAB/R2011a_Student/toolbox
->  r   XAPPLRESDIR         = /usr/local/MATLAB/R2011a_Student/X11/app-defaults
->  r   XKEYSYMDB           = /usr/local/MATLAB/R2011a_Student/X11/app-defaults/
XKeysymDB
->  e   MAX_OPEN_FILES      = 1024
->  s   _JVM_THREADS_TYPE   = 
->  e   MATLAB_JAVA         = 
->  s   MATLAB_MEM_MGR      = 
->  s   MATLAB_DEBUG        = 
->  s   LD_LIBRARY_PATH     = /usr/local/MATLAB/R2011a_Student/sys/os/glnxa64:/u
sr/local/MATLAB/R2011a_Student/bin/glnxa64:/usr/local/MATLAB/R2011a_Student/exte
rn/lib/glnxa64:/lib/amd64/native_threads:/lib/amd64
->  a   arglist             = 
->  e   SHELL               = /bin/bash
->  e   PATH                = /usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:
/sbin:/bin:/usr/games:/usr/local/games



in the terminal and noticed that 'MATLAB_JAVA = ' equaled a blank space. 
2) in the first output above suggested changing this value. Looking up info on this question
here: [http://www.mathworks.com/matlabcentral/answers/95360-why-do-i-get-an-error-that-matlab-cannot-locate-the-jre-upon-startup-for-a-64-bit-linux-machine](http://www.mathworks.com/matlabcentral/answers/95360-why-do-i-get-an-error-that-matlab-cannot-locate-the-jre-upon-startup-for-a-64-bit-linux-machine)
and here: [http://www.mathworks.com/matlabcentral/newsreader/view_thread/292734](http://www.mathworks.com/matlabcentral/newsreader/view_thread/292734)

I decided to change the value of MATLAB_JAVA to
'MATLAB_JAVA = usr/local/MATLAB/R2011a_Student/sys/java/jre/glnx86/jre/lib'
the value differs from the example on those webpages but I believe the value I set is the corresponding value for my PC and I also believe I have a 32 bit jre installed (due to the x86) as suggested in those links. So I pressed 'v' to enter vi, then 'i' to enter insert mode, made the change and try to save my changes using 'Esc' + 'ZZ' and 'Esc' + :wq but then MatLab still
doesn't work and when I type 'matlab -n' my changes to 'MATLAB_JAVA' aren't there. 


Why are my changes not being saved? Should I just delete 'MATLAB_JAVA' assuming my changes get saved (since the first mathworks link suggest removing it)?
I tried updating java, could I have updated java incorrectly? Is there something else I haven't considered?

---

### Post by cj13579 on 2014-08-05
Before you run MatLab make sure that you export the environment variable MATLAB_JAVA. Also, I think that you will want to set the value of the variable to a level higher or possibly the *bin* folder:

```
export MATLAB_JAVA=/usr/local/MATLAB/R2011a_Student/sys/java/jre/glnx86/jre
```

---

### Post by briansfractal on 2014-08-05
Hi Chris, thanks for the input. When I install Matlab on my laptop I will try your suggestion. For now though, I typed "matlab -glnx86" and it worked 
so since it finally works I'll deal with a few more keystrokes for now. Thank you, I really appreciate it.

---

