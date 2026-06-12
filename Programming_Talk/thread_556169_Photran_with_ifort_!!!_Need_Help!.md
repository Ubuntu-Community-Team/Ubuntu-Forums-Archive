---
title: "Photran with ifort !!! Need Help!"
date: 2007-09-21
forum: Programming Talk
---

### Post by asbefore on 2007-09-21
When I make the fortran file and the following error message is shown, I don't  know what is wrong with it! Thank you very much for your help!

make -k all 
Building file: ../h.f90
Invoking: Intel Fortran Compiler
ifort -g -O0 -Ob0 -c -o "h.o" "../h.f90"
[COLOR="Black"]**/bin/sh: ifort: command not found**[/COLOR]
make: *** [h.o] Error 127
make: Target `all' not remade because of errors.
Build complete for project test

I installed the intel fortran yesterday by this passage, [http://ubuntuforums.org/showthread.php?t=89571](http://ubuntuforums.org/showthread.php?t=89571)
Actually if I use "**/home/li/ ifort  test.f90**" in command window, it works so I think the installation is all right.
But there should be something wrong with setting the environment. Could you please help with this problem? Thanks a lot!

---

### Post by yabbadabbadont on 2007-09-21
Looks like you just need to add the directory to which you installed the compiler to your PATH environment variable.

---

### Post by LaRoza on 2007-09-21
For Fortran, you can use g77, and gfortran. They work like gcc. 

(This is just a suggestion, in case you didn't already know about them.)

---

### Post by jdrodrig on 2007-09-21
Just for completeness, you can also use the quite nice (to my taste) SunStudio 12 for linux (downloadable)...it has the command line option, but also the IDE if you need one.

D.

---

### Post by asbefore on 2007-09-21
> **yabbadabbadont said:**
> Looks like you just need to add the directory to which you installed the compiler to your PATH environment variable.

I am sorry and I am a newbie. I don't know how to do that!
Would you please help me with it?

---

### Post by gs_g6 on 2007-09-24
add this line to your .bashrc file in your home foler
```
source /opt/intel/fc/10.0.023/bin/ifortvars.sh
```
This should work, but you may have another path to this script which is locate in bin folder in fc folder(default is /opt/intel/fc/nr.version/bin).
for next time please read carrfully softwer documentation ;)
best regards

---

### Post by tschoel on 2007-10-10
I'm sorry, but I'm having trouble with this problem as well.  Whether I use a managed or standard make project, Photran complains that it cannot find ifort, such as:

**** Build of configuration Debug_ia32 for project simple_program ****

make -k all 
Building file: ../main.f90
Invoking: Intel Fortran Compiler
ifort -g -O0 -Ob0 -c -o "main.o" "../main.f90"
/bin/sh: ifort: not found
make: *** [main.o] Error 127
make: Target `all' not remade because of errors.
Build complete for project simple_program

I do have these lines in my /home/username/.bashrc file already:
# For intel fortran
source /opt/intel/fc/10.0.023/bin/ifortvars.sh
source /opt/intel/idb/10.0.023/bin/idbvars.sh

Further, I can compile the programs from the command line. It seems that Photran cannot find the ifort even though the command line can.  Can anyone help?  Thanks!

---

### Post by xtacocorex on 2007-10-10
Make sure your version numbers are the same as what you have in your .bashrc.
 
And it's FORTRAN, for everyone who's spelling it wrong.

---

### Post by tschoel on 2007-10-10
Yes, the version number in the .bashrc file matches that of the folders for the intel installation.

---

### Post by xtacocorex on 2007-10-10
Wait, those source commands won't work right, you need to actually edit the PATH variable.
 
You need to remove the two source lines in the .bashrc file that you added then add at the bottom:
```

PATH=$PATH:/opt/intel/fc/10.0.023/bin:/opt/intel/idb/10.0.023/bin
export PATH
 
LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/intel/fc/10.0.023/lib:/opt/intel/idb/10.0.023/lib
export LD_LIBRARY_PATH

```

---

### Post by tschoel on 2007-10-10
Thanks for trying to help, but that command does not seem to work.  I commented out the other commands and added the ones you gave.  I am still able to compile from command line, but Photran still does not compile properly.  The errors are identical.

---

### Post by xtacocorex on 2007-10-10
Wow, I thought you all were mis-spelling FORTRAN, but instead you are trying to install an Eclipse plugin for FORTRAN.
 
I'd suggest contacting the people who make Photran, most of the FORTRAN programmers here don't use an IDE, at least LaRoza and I don't and we seem to be the only ones still using it.

---

### Post by tschoel on 2007-10-10
Yeah, I've noticed that most "serious" programmers skip the IDE's in Linux.  But I prefer it as I transition over from Windows.

Anyway, I found a workaround... I copied the program ifort into the /bin directory.  Someone mentioned it on another site elsewhere.  I'm guessing that if I had all of my PATHs set correctly it wouldn't be necessary, but it works and now I'm happy (at least temporarily).

---

### Post by bruj0 on 2009-03-17
Yes, for some reason the Photran does not see the $PATH variable: ifort command works in the shell command line, but does not work in the Photran's makefile. Simple solution would be just to use the full path to ifort in the Photran's makefile.

---

