---
title: "Intel Fortran Compiler 10.0.023 on Gutsy"
date: 2007-10-21
forum: Programming Talk
---

### Post by nav211 on 2007-10-21
Ok, so I just installed Gusty and tried to put the Intel(R) Fortran Compiler 10.0.023 on it. Here is the error I got. 

The  Intel(R) Software  Setup Assistant  may  attempt to  connect  to  the
Intel(R) Registration Center to validate your Serial Number. This may take
several minutes depending on your network.  Please wait...

You may press Ctrl+C to cancel.
./install.sh: line 332: 14075 Floating point exception(core dumped) $install_prog $@

If anyone knows a workaround please help, else I'll just go back to Feisty and wait for a new version of the compiler. I am not an expert Linux user but am capable of following guides/comments.

Thanks..

---

### Post by LaRoza on 2007-10-22
Can you use G77 or GFortran? They would be much easier to set up. (In case you didn't know of them)

Sorry, I never tried the Intel Fortran Compiler.

---

### Post by masebase on 2007-10-22
I get the same error.  I tried a lot of thing but nothing seems to work.  If I scroll up to the top of the were I try to install it I see

```
sh: Syntax error: Bad fd number
```

right after I ran install.sh.

I also echoed $install_prog and see it is not set anything and it should be set to "./secore -t --launch" it tried to set it to that right be line 332 but that did not work.  I have searched for the Bad fd number thing and have not come up with anything.

---

### Post by masebase on 2007-10-22
Well I got the intel C++ and fortran compiler to work in ubuntu 7.10.  It took some hacking.  The first thing I did was get the lastest version off the intel website 10.0.026.  Then I installed it using the LICENSE FILE because the key would not work I keep getting the same error.  Once I had it installed I changed the PATH and LD_LIBRARY_PATH in /etc/bach.bashrc with the below.

```

# for intel compiler
export PATH=$PATH:/opt/intel/cce/10.0.026/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/intel/cce/10.0.026/lib

export PATH=$PATH:/opt/intel/fce/10.0.026/bin
export LD_LIBRARY_PATH=$LD_LIBRARY_PATH:/opt/intel/fce/10.0.026/lib

```

Then I tried using icc or ifort and got some an error like

```
export: 36: Illegal option -n
```

So I opened up /opt/intel/fce/10.0.026/bin/ifort and deleted the -n in line 36.  I run into an error with exec and the -a in the last line of the file so I hacked them to look like

```

if [ $# != 0 ]
then
 exec /opt/intel/fce/10.0.026/bin/ifortbin "$@";
else
 exec /opt/intel/fce/10.0.026/bin/ifortbin;
fi

```

I did the same of icc for the c++ side.  So it seem export and exec don't have the same options as before. I don't know why this is,but this will make it work.  If anyone know a better way of fixing it that would be great.

---

### Post by nav211 on 2007-10-22
> **LaRoza said:**
> Can you use G77 or GFortran? They would be much easier to set up. (In case you didn't know of them)

Sorry, I never tried the Intel Fortran Compiler.

The Photran IDE from Eclipse works well with the Intel Fortran Compiler. I use gfortran with Windows but haven't tried it in Ubuntu. Maybe I should. Well, for now I am back to Ubuntu 6.10 as it has been stable on my PC for a while. My simulations run for months sometimes therefore I need something that works for sure. 


Masebase:

Thanks for the help. I will try your method on my other PC when I get home. It seems Intel is always behind in supporting the latest distros.

---

### Post by LaRoza on 2007-10-24
[http://ubuntuforums.org/showthread.php?p=3620521#post3620521](http://ubuntuforums.org/showthread.php?p=3620521#post3620521)

---

### Post by xtacocorex on 2007-10-24
The only reason to use Intel FORTRAN is if your code uses NAMELISTS as gfortran won't support them.  I haven't tried g77 in a while since it won't install on my Macbook and my Dell running Edgy keeps shutting off due to some critical overtemperature.

---

### Post by DoktorSeven on 2007-10-24
**masebase**: did you try running the script with **bash** instead of just executing it?  My bet is that it tries executing with /bin/sh, which is linked to **dash**, a bash clone that doesn't support a few options and will break scripts.

Do **bash ./nameofscript**.

Sigh.  Why Ubuntu insists on linking **dash** to /bin/sh by default, I'll never know.

---

### Post by Zwic on 2007-10-24
Hi!
First of all, excuse my poor english.
To do the install y follow these steps as root:

 tar -zxvf l_fc_p_10.0.023.tar.gz 
 cd l_fc_p_10.0.023/data/
#to do a deb package:
 sudo alien -cv intel-ifort100023-10.0.023-1.i386.rpm 
#install it:
 sudo dpkg -i intel-ifort100023_10.0.023-2_i386.deb 
#go to
 cd ../../fc/10.0.023/bin

and at beginning of some files (look here [http://www.intel.com/support/performancetools/sb/CS-025939.htm](http://www.intel.com/support/performancetools/sb/CS-025939.htm))
you must replace #!bin/sh for #!bin/bash, and ...

 chmod 770 ifortvars.sh

 root@myubuntu:/opt/intel/fc/10.0.023/bin# ./ifort --version
 ifort (IFORT) 10.0 20070426
 Copyright (C) 1985-2007 Intel Corporation.  All rights reserved.

It's done. And now:

source /opt/intel/fc/10.0.023/bin/ifortvars.sh

to add the ifort vars. 

Good luck.

---

### Post by Zwic on 2007-10-24
Upps, the license file must be in the license directory /opt/intel/licenses
intel mailed you with that file.
 ;-)

---

### Post by aerorahul on 2007-11-12
Here is the procedure. It worked for me.
1. Download the latest 10.0.026  noncommercial Intel Fortran compiler off Intel website.
2. Untar the directory
3. place the license file emailed to you by intel in the directory /opt/intel/licenses
4. run the install script. It will recommend to install via the license file it detected. proceed with the installation.

5. after the installation is complete, ie. sucessful I had to tweak a few things.
a. open /opt/intel/fc/10.0.026/ifort
b. in last few lines there is a statement export -n  IA32ROOT; Remove the -n flag
c. then there are 2 lines which should be changed to look like the following.
exec   /opt/intel/fc/10.0.026/bin/ifortbin,
inshort take out the "/opt/intel/fc/10.0.026/bin/ifortbin" and simply keep
 exec   /opt/intel/fc/10.0.026/bin/ifortbin 
do not touch the "$@";

6. you might also want to include path to the library in your .bashrc file. This is discussed in the previous posts on this thread.

A few things I noted were:
1. the license file emailed by intel did not work with 10.0.023 but worked with 10.0.026
2. 10.0.023 is the default for download, choose 10.0.026 when downloading the compiler.
3. same process holds for installing the Intel C/C++ complier.

Hope this helps.
Happy compiling.

---

### Post by mommebu on 2007-11-15
In fact the copying of the license file  to /opt/intel/licenses resolves the problem of the floating point error.
For what concerns the -n option in the shell script, as mentioned earlier in this script, it's maybe quicker to simply  change the script used in the first line of the file from '/bin/sh' to '/bin/bash'.
However installing compiler version 10.1.008 this was not necessary anymore for me.

cheers,
Momme

---

