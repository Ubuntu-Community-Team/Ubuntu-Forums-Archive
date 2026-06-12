---
title: "HOWTO: Install Intel Fortran 9.0"
date: 2005-11-12
forum: Outdated Tutorials &amp; Tips
---

### Post by Chickenmonger on 2005-11-12
As an undergraduate student lucky enough to have been taught FORTRAN for scientific computing, I find a necessity to have not only gfortran but also Intel Fortran on my Linux boxes.

Intel Fortran has both a commercial version, and a non-commercial version, perfect for my studies.

The following was tested on a fresh install of the release version of Ubuntu Breezy, with all security updates as of 2005-11-11 applied.

1. First things first, install the prerequisite software packages:
```
sudo apt-get install rpm build-essential
```

2. Register at Intel's site for a non-commercial version of the Intel Fortran compiler.

[http://www.intel.com/cd/software/products/asmo-na/eng/compilers/flin/219857.htm](http://www.intel.com/cd/software/products/asmo-na/eng/compilers/flin/219857.htm)

Intel's site will send you an email that starts with the following:
```
Thank you for registering the Intel(R) Fortran Compiler for Linux*.

SAVE THIS SERIAL NUMBER
Your serial number for this registration is...
```

2. Download the compiler archive:

[http://www.intel.com/cd/software/products/asmo-na/eng/compilers/219717.htm](http://www.intel.com/cd/software/products/asmo-na/eng/compilers/219717.htm)

3. Extract the compiler archive
```
tar xvzf l_fc_p_9.0.021.tar.gz
```

4. Run the installer
```
cd l_fc_p_9.0.021
sudo ./install.sh
```

5. Choose Option 1 to install Intel Fortran; choose Option 1 to proceed with a serial number.

6. Type in the serial number (case-sensitive) given in the email. (XXXX-XXXXXXXX). Choose 1 for a default install.

7. Press Enter to read the license agreement. The spacebar speeds through this quickly. Type 'accept' to accept the license agreement.

8. Press Enter to accept the default install directory for the compiler. The installation of the compiler takes some time. Press Enter to continue.

9. Press Enter to accept the default install directory for the debugger. The debugger takes some time to finish. Press Enter to continue.

10. At this point, the installer seemed to stop. It can be exited with CTRL-C, and it does not seem to affect the install.

11. To make the binaries and shared libraries easily found, add the following lines to your .bashrc:
```
PATH="/opt/intel/fc/9.0/bin:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/fc/9.0/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH
```

---

### Post by phen on 2005-12-02
Hi! Thank you very much for your help on that topic. i've never been able to install it fully functional under hoary, now i will try your .bashrc tip (i was stuck there...)

---

### Post by rusi_pathan on 2005-12-03
For installing Fortran 8.0 on warty I used alien to create a deb. Instructions are available here...

[http://www.theochem.uwa.edu.au/fortran/intel_on_debian](http://www.theochem.uwa.edu.au/fortran/intel_on_debian)
[http://colt.projectgamma.com/intel/ixc-debian.html](http://colt.projectgamma.com/intel/ixc-debian.html)

---

### Post by phen on 2005-12-03
i added your howto to the ubuntuscientists website. please delete it if you don't want to be linked (or write me).... [https://wiki.ubuntu.com/UbuntuScientists](https://wiki.ubuntu.com/UbuntuScientists)

---

### Post by firehead on 2006-01-14
worked great for me
your .bashrc tip was very useful. i had to add "unset LANG" to the .bashrc as well, since calling ifort always yielded "cannot find directory in which g++ resides" which can only cured (afaik) with unset LANG...

thx alot

---

### Post by pestilence4hr on 2006-04-06
It's nice that the install actually works now, you used to have to use alien to make a deb.

In any case, I think the proper way to set the environment variables is to put the following in your .bashrc:

```

source /opt/intel/fc/9.0/bin/ifortvars.sh
source /opt/intel/idb/9.0/bin/idbvars.sh

```

This will set all of the paths, including your PATH, MANPATH, etc.

---

### Post by hutxubix on 2006-06-09
Hello¡¡

I need help. I tried to install intel fortran compiler as chikenmonger explained but I got the message:
install_fc.sh can't identify your machine type, glibc, or kernel.

This product is supported for use with the following combinations   :

    Machine Type                Kernel  glibc

1.  IA-32/EM64T                 2.4.x   2.2.5
    IA-32/EM64T                 2.4.x   2.2.4
    IA-32/EM64T                 2.4.x   2.2.93
    IA-32/EM64T                 2.4.x   2.3.2
    IA-32/EM64T                 2.6.x   2.3.x
    IA-32/EM64T                 2.6.x   2.4.x

x.  Exit

If you would you like to perform an unsupported install of this product, enter the number corresponding to the platform most similar to yours. Otherwise, enter "x" to exit   :   2.6.x
Inappropriate choice. Please try again   :   2.6.x   2.3.x
Inappropriate choice. Please try again   :   6
Inappropriate choice. Please try again   :   5

I can only choose 1 or x. If I choose 1., it doesn't install.

Can anybody help me please?

---

### Post by hutxubix on 2006-06-09
Ok, i've found another topic about this at 

[http://ubuntuforums.org/showthread.php?t=169664](http://ubuntuforums.org/showthread.php?t=169664)

where very interesting things are said. I could install the compiler following those instructions but I can not install the debugger idb, and what it worst, I can't install the libraries mkl from intel. Can somebody help me?

---

### Post by hutxubix on 2006-06-09
ups¡¡ that thread is closed, so I go on here. How can I install the debugger and the math libraries mkl?

Thanks

---

### Post by alin.elena on 2006-06-19
here I have described how to install inte compilers+debugger
[http://ubuntuforums.org/showthread.php?t=179589](http://ubuntuforums.org/showthread.php?t=179589)
i will try  to find time to write the how to for mkl too.

Alin

---

### Post by Omni-Vi on 2006-06-21
Hi All,
I had the same problem of not being able to install Intel Fortran Compiler under Dapper. The error was

...
install_fc.sh can't identify your machine type, glibc, or kernel.
...

Some of you had the same problem.
Solution:
The installation script install_fc.sh tries to determine the GLIBC version  within the function GET_SYSTEM_REQUIREMENTS () {...} with the following statement (lines 1506-1510):
```

if [ "$RPM_NOT_FOUND" = 0 ] ; then
  GLIBC="$(rpm -qa | egrep -e 'glibc-2\.2\.4' -e 'glibc-2\.2\.5' -e 'glibc-2\.2\.93' -e 'glibc-2\.3' -e 'glibc-2\.4' 2> /dev/null )"
else
  GLIBC="$(ls /lib/libc-* | grep -e '[.]so' | sed s@'\(.*\)\(\.so.*\)'@'\1'@g)"
fi

```
Now the thing is, if you are using Debian/Ubuntu and you have alien, you also have rpm. BUT the rpm database that holds a list of all installed packages under eg. SUSE is empty under Ubuntu, since it is not used.
Therefore, the GLIBC variable is left empty (rpm -qa gives back nothing). The second call (ls /lib/libc-...) should be used but is not since rpm is installed.

Okay, what do we do about it?
First of all, you can not uninstall rpm for alien depends on it. What we can do though, is to change the install_fc.sh script so that it does not use rpm. This is simple. Just go to line 226 in install_fc.sh (the IS_RPM_PRESENT () {} function) and look for
```
RPM_NOT_FOUND=$?
```.
Change it to
```
RPM_NOT_FOUND=1
```
and install.sh should work just fine. No need to convert any package by hand, the installer will do that for you.

I would be happy to hear if this works for you, I hope it will :D 
Ciao

Ps: The line numbers are for the Intel Fortran 9.1 Compiler. You might have to adapt them for 9.0 or C Compiler. Thats why I gave you the function names as well.

---

### Post by arkangel on 2006-07-04
it works  ;)

---

### Post by thermoarch on 2006-09-28
I am newbie of ubuntu and linux. I follow the guide of installing Intel Fortran. I get the lates version of fortran 91.036, it's seem to be well installed, but, as a newbie, I don't know how to access the  .bashrc to insert some code as instructed.
Please helme, thanks,

---

### Post by alin.elena on 2006-09-29
that's simple

open a terminal window.

than

```
cd
```

to be sure that you are in you home directory

than

```
vi .bashrc
```

you can substitute ```
vi
``` with your favorite text editor.

and now at the end of the file you add the source commands.

Alin

---

### Post by thermoarch on 2006-09-29
One more "stupid" question, how ho run fortran? bacause I did not find the program under Application menu. Sorry!!

---

### Post by alin.elena on 2006-09-29
intel fortran  is a compiler. a tool to generate binary files from source files.

let us assume that you have a fortran 90 source file test.f90
the simplest will be somthing like

```

program hello_world
implicit none

print *, "hello world"
end program hello_world

```

fortran will help you to generate an application that will write on the screen (standard output) "hello world".

for that in the command window you will do something like that

```
ifort -o test test.f90
```

than
```
./test
```

and that's all you have created the first fortran application.


Alin

p.s. there are plenty of resource on the web about how to programme using fortran

---

### Post by yuni on 2006-10-12
It was mistake on the path. It works.

---

### Post by easy.tiger on 2006-10-14
i could install succesfully ifort, but i should say that theres one more step for non-english ubuntu boxes, i mean, if you try to execute ifort then it will say something like

ifort: error: could not find directory in which g++ resides

i could find at intels [webpage]("http://www.intel.com/support/performancetools/fortran/linux/sb/cs-017386.htm") an interesting set of solutions, but i just had to set the LC_ALL environment variable to C 

e.g export LC_ALL=C

note for newbies(like me): this variable should be modified at etc/enviroment  ;)

---

### Post by slabdar1 on 2006-10-19
Hello every one

I tried to install Intel Fortran free compiler "9.1" on my laptoop.

during the installation I get this message.
----------------------------------
Problems with Fortran compiler:  Output not equal to < Hello, World!  F90>
See /tmp/test_fc.7127.log for details.

NOTE: If using a FLOATING or NODE-LOCKED license file, ignore this message.
Press ENTER to continue.
---------------------------------

Is it NORMAL?
Can you please help me?
Thanks

---

### Post by Relain on 2006-11-30
in response to the previous poster this is normal, the install script tries to actually compile a little test program and check the output (that's the whole hello world thing). Sadly because the variable setting scripts(ifortvars.sh) in the intel/fce/bin dir don't quite work with ubuntu.

I think this is because they start with #!/bin/sh while having some syntax which assumes bash. On ubuntu 6.10 #!/bin/sh->dash it's a symlink to dash which seems to not quite work properly with some of the shell commands. I'm no bash/dash guru but this seems stupid to me. Anyway you can fix it by changing it to directly invoke bash: #!/bin/bash. 

I managed to get the C++ compiler installed just fine like this but when i tried to get ifort going i get this error:

exec: 34: -a: not found

Anyone know wha's going wrong there?

Thanks

Chris

---

### Post by Relain on 2006-11-30
oh i just fixed my own problem turns out that (yourinstalldir)/bin/ifort is not a binary file but another script (they keep on coming :D) and i didn't change the shebang line at the top to bash. 

i don't actually know any fortran so i just did a simple hello world program:

```

program hello_world
implicit none
print *, "hello world"
end program hello_world

```

and it works! 

now what's a good book to pick up some fortran? I know C/C++ already, is there a "the C programming language" type book for F90?

Thanks

---

### Post by mrphd on 2006-12-02
When I first started to learn fortran I found that the best references to be various notes prepared for university courses. I don't think it is really worth buying a book.

If I recall correctly, [http://www.liv.ac.uk/HPC/HTMLFrontPageF90.html](http://www.liv.ac.uk/HPC/HTMLFrontPageF90.html) was quite useful. You can download a .ps version or use your browser.

---

### Post by mrphd on 2006-12-02
> **Relain said:**
> 

exec: 34: -a: not found

Anyone know wha's going wrong there?

Chris

It might be useful if you post your ifort command line options. You may have just used made an error here.

---

### Post by mohshee on 2006-12-08
Hi...I am a new Ubuntu user (but have been using linux for a while). I've tried following the installation instructions on page 1, but when I run the install.sh file, I can only get to the "Please type your selection or Serial Number  :" part. I enter the number and always get the error: "trap: 4021: SIGINT: bad trap", and the installation process sends me right to registration and claims it is done. The results is a very incomplete installation directory and I don't know how to fix this . Any ideas???

---

### Post by Relain on 2006-12-09
moshee: There's a few simple things to do: you have to change the  #!/bin/sh line at the top of all the install scripts. Install.sh and /data/install_ff.sh (i made up the latter one but it's something like that). 

Also you probably need to replace the line that uses rpm in /data/install_blah/ with a call to alien. I deleted the install dir structure so i can't recall the exact syntax. Rendering this comment fairly useless but i know that's the general shape of things and if you google / hunt through this thread you should be able to find the answers.

When it does install it'll say that hello world etc didn't work. You again have to change the #!/bin/sh lines to #!/bin/bash in a few of the scripts in the install dir: /opt/intel/ifort/blah/blah/bin

Of course you could just change #!/bin/sh from pointing to Dash (the cause of all the problems) to pointing to Bash (if you like).

hope that's some help

---

### Post by mohshee on 2006-12-11
Thanks. I went ahead and got it working (after some struggling) using the more manual setup described here: 

[http://ubuntuforums.org/showthread.php?t=285757]("http://ubuntuforums.org/showthread.php?t=285757")

But now I am curious if I could get it installed using your recommendations.

---

### Post by OvelhaNegra on 2007-02-25
Alin.Elena,

Thanks for your post! It really have helped me a lot!

Have you ever tried intel fortran with ubuntu edgy 6.10? It seems that the instalation procedures that work fine with 6.06 has some tricky problems in 6.10...

Thanks once again!
ON

---

### Post by olavjunior on 2007-03-08
OH F... THIS INTEL FORTRAN ****! I GIVE UP!

I don't consider myselfe a complete nubi anymor, but this sh.. I just can't get working!

At first I followed this thread, and got the message:
After giving the liscense-number, it won't proceed, giving a short message 
[I]trap: 4021: SIGINT: bad trap
[/I]
I found another messy thread ([http://ubuntuforums.org/showthread.php?t=285757](http://ubuntuforums.org/showthread.php?t=285757)) saying that I should change something /bin/bash. Did and ran this installer again, everythig worked, until I had accepted the license, and it was about to install, then it said: *install failed* grrr

I've read alot of thread all suggesting different ways to do this. 
This one I def couldn't get to work: (didn't ask for a serial) [http://www.theochem.uwa.edu.au/fortran/intel_on_debian](http://www.theochem.uwa.edu.au/fortran/intel_on_debian)
Neighter this one suggested here
And this one is so messy, I can't get my head around it: [http://ubuntuforums.org/showthread.php?t=285757](http://ubuntuforums.org/showthread.php?t=285757)

Anyone wanna post a simple go trough, step by step, for a complete idiot like my selfe? Explaining exactly what files to alter, wether to use rpm, alien, deb, and wich files to alter after the installation. And what command to run to see if it installed correctyl. ( I managed to install with deb, but it never asked for liscense, so I figured it wouldn't work. It didn't take all that time eighter, so I figured it didn't work. But dir /opt/intel/bla/bin was created with a lot of files in it though...

Sorry for my frustraded post! Had to get it out somehow :s

AND: A final question: Is it a graphical interface? If not, what's the difference between intels and the one in ubuntu gfortran?

EDIT: Solved: I used the deb-package method. Afterwards I altered all the script-files in /opt/intel/fc/9.1.036/bin to point to bash. Then I altered the ifort to point to the actual install-dir wherever <installdir> was. It now works. I'm on ubuntu 6.10 edgy. 

But it's only a fortran 90 compiler!! I realized that now. So then gfortran is better? Isn't there any fortran 95-compilers? Have to use the 96-language in school....

---

### Post by manybodycpa on 2007-04-24
Hi!

I have recently installed Ubuntu Feisty after updating from 6.06 to 6.10 failed. The ifort compiler (version 9.0) has worked perfectly with 6.06, but seems not to work with 7.04. 

First, it seems that the combination of kernel 2.6.x and glibc-2.5 is not supported. Ignoring this, installation seems to work (apart from the above-mentioned problem with the hello world test).
However, running ifort with no arguments, I get

"export: 36: Illegal option -n",

for which google only finds one (chinese) page.

Any help is appreciated.

---

### Post by trashie on 2007-05-13
Hi,

The error "export: 36: Illegal option -n" came from the fact that Intel do not make difference between sh shell and bash one.

So to solve the above problem, just edit "ifort" script in Intel directory and change  in the first line "sh" by "bash".

It will work !

Bye

Mathieu

---

### Post by jdrodrig on 2007-05-15
Hi,

Now that I found a thread about intel fortran installation, I was wondering if any of you have tried the IMSL ([http://www.vni.com/products/imsl/](http://www.vni.com/products/imsl/)) math libraries in Ubuntu. I used to use the Compaq Visual Fortran because my version came with such add-in but I think only the Windows version of the new Intel Fortran gives the option to include IMSL from the get go.  Besides, anyone knows of open source substitutes for IMSL?

Thanks,
Daniel

---

### Post by therealbrewer on 2007-05-24
Hopefully this will help anyone still having trouble with installing the Intel Fortran Compiler in Feisty.

The instructions in the first post outline the correct procedure, but the installation may silently fail anyway. To track down the cause, I edited the second install script  /Desktop/l_fc_c_9.1.045/data/install_fc.sh. First, I changed the widely discussed #!/bin/sh to #!/bin/bash, but that didn't take care of the problem. Next, I edited the first "if" statement to force verbose_mode, i.e. I changed it so that both branches set verbose-mode="1".

Then I re-ran the install to watch the vebose error output. What I found was that the compiler install was failing due to unmet dependencies:

error: Failed dependencies:
        ld-linux.so.2 is needed by intel-ifort91045-9.1.045-1.i386
        libc.so.6 is needed by intel-ifort91045-9.1.045-1.i386
        libdl.so.2 is needed by intel-ifort91045-9.1.045-1.i386
        libm.so.6 is needed by intel-ifort91045-9.1.045-1.i386
        libpthread.so.0 is needed by intel-ifort91045-9.1.045-1.i386
        libc.so.6(GLIBC_2.0) is needed by intel-ifort91045-9.1.045-1.i386
        libc.so.6(GLIBC_2.1) is needed by intel-ifort91045-9.1.045-1.i386
        libc.so.6(GLIBC_2.1.3) is needed by intel-ifort91045-9.1.045-1.i386
        libc.so.6(GLIBC_2.2) is needed by intel-ifort91045-9.1.045-1.i386
        libdl.so.2(GLIBC_2.0) is needed by intel-ifort91045-9.1.045-1.i386
        libdl.so.2(GLIBC_2.1) is needed by intel-ifort91045-9.1.045-1.i386
        libpthread.so.0(GLIBC_2.0) is needed by intel-ifort91045-9.1.045-1.i386
        libpthread.so.0(GLIBC_2.1) is needed by intel-ifort91045-9.1.045-1.i386
        libpthread.so.0(GLIBC_2.2) is needed by intel-ifort91045-9.1.045-1.i386
        libpthread.so.0(GLIBC_2.2.3) is needed by intel-ifort91045-9.1.045-1.i386

I Googled the problem, and found a few posts that seem to imply that the dependencies aren't really a problem. One post regarding a similar problem with Intel's C++ compiler suggested using a switch to force the rpm installer to ignore the dependency issues.

So, I went back to the install_fc.sh script, and searched for "defaultoptions". The default rpm options are set in two different sections of the code. Go to the second occurrence (about halfway through the file under the procedure "GET_RPM_OPTIONS ()") and change the default options from '-U --replacefiles --force' to '-U --replacefiles --force --nodeps' and that will take care of the silent failure.

Keep in mind that with the free license, the test compilation will fail during the installation. Nevertheless, the install will be OK, as far as I can tell...

Even if you are not having the same problem as I did, the verbose mode may help you track down the cause.

---

### Post by manybodycpa on 2007-05-26
Thanks a lot - the only thing missing in my case was to set GXX_ROOT to get the right path for the gcc library.

---

### Post by bbyy_13 on 2008-10-18
> **Chickenmonger said:**
> As an undergraduate student lucky enough to have been taught FORTRAN for scientific computing, I find a necessity to have not only gfortran but also Intel Fortran on my Linux boxes.

Intel Fortran has both a commercial version, and a non-commercial version, perfect for my studies.

The following was tested on a fresh install of the release version of Ubuntu Breezy, with all security updates as of 2005-11-11 applied.

1. First things first, install the prerequisite software packages:
```
sudo apt-get install rpm build-essential
```

2. Register at Intel's site for a non-commercial version of the Intel Fortran compiler.

[http://www.intel.com/cd/software/products/asmo-na/eng/compilers/flin/219857.htm](http://www.intel.com/cd/software/products/asmo-na/eng/compilers/flin/219857.htm)

Intel's site will send you an email that starts with the following:
```
Thank you for registering the Intel(R) Fortran Compiler for Linux*.

SAVE THIS SERIAL NUMBER
Your serial number for this registration is...
```

2. Download the compiler archive:

[http://www.intel.com/cd/software/products/asmo-na/eng/compilers/219717.htm](http://www.intel.com/cd/software/products/asmo-na/eng/compilers/219717.htm)

3. Extract the compiler archive
```
tar xvzf l_fc_p_9.0.021.tar.gz
```

4. Run the installer
```
cd l_fc_p_9.0.021
sudo ./install.sh
```

5. Choose Option 1 to install Intel Fortran; choose Option 1 to proceed with a serial number.

6. Type in the serial number (case-sensitive) given in the email. (XXXX-XXXXXXXX). Choose 1 for a default install.

7. Press Enter to read the license agreement. The spacebar speeds through this quickly. Type 'accept' to accept the license agreement.

8. Press Enter to accept the default install directory for the compiler. The installation of the compiler takes some time. Press Enter to continue.

9. Press Enter to accept the default install directory for the debugger. The debugger takes some time to finish. Press Enter to continue.

10. At this point, the installer seemed to stop. It can be exited with CTRL-C, and it does not seem to affect the install.

11. To make the binaries and shared libraries easily found, add the following lines to your .bashrc:
```
PATH="/opt/intel/fc/9.0/bin:$PATH"
export PATH
LD_LIBRARY_PATH="/opt/intel/fc/9.0/lib:$LD_LIBRARY_PATH"
export LD_LIBRARY_PATH
```
Thank you for your sharing.
However, after following your instruction, I meet this error when I try to compile a simple fortran example. Can you give me some suggsetion?

ld: /usr/lib/gcc/x86_64-linux-gnu/4.2.3/32/crtbegin.o: No such file: No such file or directory

---

### Post by nis17sep on 2010-07-24
hey i have installed intel fortran compiler and also added the path in  .bashrc file.

on giving a command to compile like ifort new.for it gives an error - 

/Desktop$ ifort new.for
/opt/intel/Compiler/11.1/064/bin/ia32/fortcom: error while loading  shared libraries: libstdc++.so.5: cannot open shared object file: No  such file or directory
ifort: error #10273: Fatal error in  /opt/intel/Compiler/11.1/064/bin/ia32/fortcom, terminated by 0x7f


well m not able to understand that... new to linux plz help :sad:

---

### Post by nis17sep on 2010-07-24
found that libstd++5 was not there on ubuntu 10.04. downloaded and installed it.. and yay now ifort running.

thanx for the installation help btw

---

### Post by rusmawan on 2010-08-07
> **nis17sep said:**
> found that libstd++5 was not there on ubuntu 10.04. downloaded and installed it.. and yay now ifort running.

thanx for the installation help btw

yes, I have a same problem,  Stuck in 4th step, I tried to Install Fortran version 11.1, and here the statement 

Step no: 4 of 7 | Installation configuration - Missing Critical Pre-requisite
--------------------------------------------------------------------------------
The following required for installation commands are missing:
libstdc++.so.5 (library)
--------------------------------------------------------------------------------
    1. Finish with prerequisites and back to Critical Pre-requisites dialog
[default]
    2. Back to Pre-requisite summary dialog

please, I need a help! :(

---

### Post by rusmawan on 2010-08-07
I have read
 [http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)
[http://swiss.ubuntuforums.org/showthread.php?t=1082782](http://swiss.ubuntuforums.org/showthread.php?t=1082782)
and get libstdc++5 from [http://packages.debian.org/stable/base/libstdc++5](http://packages.debian.org/stable/base/libstdc++5)

may be it can help :D

---

### Post by nawir on 2010-08-12
Hello.
I'm trying to follow the tutorial but i've stucked at step 2
the page cannot be opened.
anyone knows why it happen?

---

### Post by cholericfun on 2010-08-26
[http://software.intel.com/en-us/articles/non-commercial-software-download/#compilers](http://software.intel.com/en-us/articles/non-commercial-software-download/#compilers)

try this page.

after downloading, in the top Dir theres a ReleaseNotes.pdf

have a look at that as well,
[http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/](http://software.intel.com/en-us/articles/using-intel-compilers-for-linux-with-ubuntu/)

otherwise this thread is very helpfull 

one thing: when you edit you .bashrc with ```
sources ...
```
you need to provide an input argument at the end depending on you architecture. Say i have 
```
source /opt/intel/Compiler/11.1/073/bin/ifortvars.sh intel64

```

---

### Post by niziris on 2010-09-12
Ahmm...I have a problem...I did everything instructed in earlier posts and other some other threads ...

Installation of Intel went fine, I changed .bashrc
but when I try ifort in terminal ....response is 
ifort: command not found

is anyone knows how can I check what is wrong whit intel? or how can I fix problem?

Iam new to ubuntu so I apologize if this is stupid question

---

### Post by niziris on 2010-10-11
This thread helped me

[http://ubuntuforums.org/showthread.php?t=1384001](http://ubuntuforums.org/showthread.php?t=1384001)

---

