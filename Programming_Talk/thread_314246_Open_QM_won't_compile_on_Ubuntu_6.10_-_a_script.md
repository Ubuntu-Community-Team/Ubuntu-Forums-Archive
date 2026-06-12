---
title: "Open QM won't compile on Ubuntu 6.10 - a script"
date: 2006-12-07
forum: Programming Talk
---

### Post by jthompson on 2006-12-07
I am trying to compile this open source database that I use.  The creators or developers have a script that does all the work, however, for some reason on Ubuntu 6.10, the compiler completely goes nuts when you execute it.

./buildgpl

```
# This script builds the GPL OpenQM source
#
# The first argument can be a stage number to continue from the given stage
#
# This script requires a standard installed QMSYS for the same release.
# The directory from which this script is executed should have subdirectories
# for the source (gplsrc), object (gplobj) and executables (bin). The
# default names shown in brackets can be modified below.

# The gpl.source file must be in the current directory and contains a list of
# the source modules that are used to build the qm executable.

# Define a few things:
#    QMSYS           Pathname of QMSYS directory
#    GPLSRC          Source directory
#    GPLOBJ          Target directory for object files
#    GPLBIN          Target directory for executables
#    QM_GCC_OPTIONS  Compiler options
#    QMLIBS          Libraries

QMSYS=/usr/qmsys
GPLSRC=gplsrc
GPLOBJ=gplobj
GPLBIN=bin
QM_GCC_OPTIONS="-Wno-pointer-sign -Wno-packed -Wall -DLINUX -D_FILE_OFFSET_BITS=64 -DGPL"
QMLIBS="-lm -lcrypt -ldl"

STAGE=$1
if test "$STAGE" = ""
then
   STAGE=1
fi


######################### STAGE 1  -  Build QM #########################

if test $STAGE -le 1
then
   echo ===== Stage 1 =====
   echo Building C program modules...
   errors=0
   errorprogs=""
   for file in `cat gpl.source`
   do
      echo $file
      gcc -c $QM_GCC_OPTIONS -I$GPLSRC -o $GPLOBJ/$file.o $GPLSRC/$file.c
      if test $? -ne 0
      then
         errors=`expr $errors + 1`
         errorprogs="$errorprogs$file "
      fi
   done

   if test $errors -ne 0
   then
      echo "Build aborted due to compilation errors in $errors program(s):"
      echo $errorprogs
      exit
   fi

   echo
fi

######################### STAGE 2  -  Link QM ##########################

if test $STAGE -le 2
then
   echo ===== Stage 2 =====
   echo "Linking qm"

   objects=''
   for file in `cat gpl.source`
   do
      objects="$objects $GPLOBJ/$file.o"
   done
   gcc -o $GPLBIN/qm $QMLIBS $objects

   echo
fi

###################### STAGE 3  -  Build QMCLILIB ######################

if test $STAGE -le 3
then
   echo ===== Stage 3 =====
   echo "Building qmclilib.o and qmclilib.so"
   gcc -c $QM_GCC_OPTIONS -I$GPLSRC -o $GPLOBJ/qmclilib.o $GPLSRC/qmclilib.c
   cp $GPLOBJ/qmclilib.o $GPLBIN/qmclilib.o

   gcc -shared -Wl,-soname,$GPLOBJ/qmclilib.so -o $GPLOBJ/qmclilib.so $GPLOBJ/qmclilib.o -lc
   cp $GPLOBJ/qmclilib.so $GPLBIN/qmclilib.so

   echo
fi

####################### STAGE 4  -  Build QMTic ########################

if test $STAGE -le 4
then
   echo ===== Stage 4 =====
   echo "Building qmtic"
   gcc -o $GPLBIN/qmtic $QM_GCC_OPTIONS -I$GPLSRC -lc $GPLSRC/qmtic.c \
       $GPLSRC/inipath.c
   echo
fi

####################### STAGE 5  -  Build QMFix ########################

if test $STAGE -le 5
then
   echo ===== Stage 5 =====
   echo "Building qmfix"
   gcc -o $GPLBIN/qmfix $QM_GCC_OPTIONS -I$GPLSRC -lc $GPLSRC/qmfix.c \
       $GPLOBJ/ctype.o $GPLOBJ/linuxlb.o $GPLOBJ/dh_hash.o $GPLOBJ/inipath.o
   echo
fi

####################### STAGE 6  -  Build QMConv #######################

if test $STAGE -le 6
then
   echo ===== Stage 6 =====
   echo Building qmconv
   gcc -o $GPLBIN/qmconv $QM_GCC_OPTIONS -I$GPLSRC -lc $GPLSRC/qmconv.c \
       $GPLOBJ/linuxlb.o $GPLOBJ/dh_hash.o $GPLOBJ/ctype.o
   echo
fi

####################### STAGE 7  -  Build qmidx ########################

if test $STAGE -le 7
then
   echo ===== Stage 7 =====
   echo Building qmidx
   gcc -o $GPLBIN/qmidx $QM_GCC_OPTIONS -I$GPLSRC -lc $GPLSRC/qmidx.c
   echo
fi

####################### STAGE 8  -  Build qmlnxd #######################

if test $STAGE -le 8
then
   # Build qmlnxd
   echo ===== Stage 8 =====
   echo Building qmlnxd
   gcc -o $GPLBIN/qmlnxd $QM_GCC_OPTIONS -I$GPLSRC -lc \
       $GPLSRC/qmlnxd.c $GPLSRC/qmsem.c
   echo
fi

#################### STAGE 9  -  Compile terminfo ######################

if test $STAGE -le 9
then
   echo ===== Stage 9 =====
   echo Compiling terminfo library
   mkdir terminfo
   $GPLBIN/qmtic -pterminfo terminfo.src
   echo
fi
```

The output from the compiler is as follows. I acutally had to put the output in a file because there was so much of it.  This is only some of the output.

```
gplsrc/qm.c:92:20: error: setjmp.h: No such file or danalyse

Build aborted due to compilation errors in 80 program(s):
qm analyse clopts config ctype dh_ak dh_clear dh_close dh_creat dh_del
dh_exist dh_file dh_hash dh_misc dh_open dh_read dh_selct dh_split
dh_write ingroup in$
tribute__â before âuc_charsâ
gplsrc/qmdefs.h:141: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before âlc_charsâ
gplsrc/qmdefs.h:145: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before âchar_typesâ
gplsrc/qmdefs.h:162: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/qmdefs.h:163: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
In file included from gplsrc/qm.h:88,
                 from gplsrc/qm.c:99:
gplsrc/dh.h:92: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/dh.h:142: error: expected specifier-qualifier-list before
âu_charâ
In file included from gplsrc/qm.h:90,
                 from gplsrc/qm.c:99:
gplsrc/descr.h:137: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/descr.h:265: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/descr.h:281: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/descr.h:301: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/descr.h:395: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/descr.h:403: error: expected specifier-qualifier-list before
âu_charâ
gplsrc/descr.h:445: error: expected specifier-qualifier-list before
âu_charâ
In file included from gplsrc/kernel.h:91,
                 from gplsrc/qm.h:91,
                 from gplsrc/qm.c:99:
gplsrc/pcode.h:40: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:41: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:42: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:43: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:44: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:45: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:46: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token
gplsrc/pcode.h:47: error: expected â=â, â,â, â;â, âasmâ or
â__attribute__â before â*â token 
```

Anyway, I posted a message on the group for QM, I just thought there might be some C gurus floating around that could see something obvious.  This successfully worked on a Gentoo box with GCC 4.1.1.  Maybe something is different with the C environment on Ubuntu 6.10?  Any thoughts are appreciated.

---

### Post by jthompson on 2006-12-07
A simple matter of:

```
apt-get install libc6-dev
```

seems to have solved my problem.  Apparently it is not installed by default.  Is there anything else one might need to compile C programs on Ubuntu 6.10?

---

### Post by Rosicrucian on 2008-07-31
[FONT="Century Gothic"]Will this also work with 8.04 Hardy Heron?[/FONT]

---

### Post by mssever on 2008-07-31
> **Rosicrucian said:**
> [FONT=Century Gothic]Will this also work with 8.04 Hardy Heron?[/FONT]
Try it and see.

---

### Post by jthompson on 2008-07-31
This method should work on 8.04.  You need the packages openssh-server gcc and libc6-dev   Look for the install QM part in this link:

[http://billabong-services.co.uk/anji/](http://billabong-services.co.uk/anji/)

---

### Post by Rosicrucian on 2008-08-05
[FONT="Century Gothic"](This is going to sound n00b-ish)
I followed the steps on the above link, but when the compiles the files for me to install the start-up QM files, it repeatedly gives me 'Permission Denied' errors.[/FONT]

---

### Post by jthompson on 2008-08-05
Just put sudo in front of all of the commands you are running.  Or switch to a root like shell

sudo -s -H

The password should be the password to your user account.

In Ubuntu by default there really isn't a root user.  Everything is done through the sudo package.  Sudo allows a regular user to run commands as root.  Its safer than running around as root all the time.  

If you come from the windows world, think of the root user as Administrator.  In *nix most things run as regular or "limited" users and you only use root when you need to.

[http://www.gratisoft.us/sudo/man/sudo.html](http://www.gratisoft.us/sudo/man/sudo.html)

Here is a little note on understanding linux permissions

[http://www.freeos.com/articles/3127/](http://www.freeos.com/articles/3127/)

---

### Post by mssever on 2008-08-05
> **jthompson said:**
> Or switch to a root like shell

sudo -s -H
I prefer [FONT=Courier New][COLOR=Green]sudo -i[/COLOR][/FONT] over [FONT=Courier New][COLOR=Green]sudo -sH[/COLOR][/FONT]. See the man page for an explanation of the options.

---

### Post by Rosicrucian on 2008-08-06
Uh-huh...

And of the configuration parameters?

---

### Post by mssever on 2008-08-06
> **Rosicrucian said:**
> Uh-huh...

And of the configuration parameters?
I don't understand your question, or what you're responding to.

---

### Post by Rosicrucian on 2008-08-06
[FONT="Century Gothic"]Nevermind. Figured it out.

OpenQM is installed, ready to go...and now it will not run.

Great.

Perhaps, because, I installed it through Wine...?[/FONT]

---

### Post by mssever on 2008-08-06
> **Rosicrucian said:**
> [FONT=Century Gothic]Perhaps, because, I installed it through Wine...?[/FONT]
It has been my experience that very few programs work decently in Wine. Picasa is the notable exception, but Google patched Wine to make Picasa run in it.

---

