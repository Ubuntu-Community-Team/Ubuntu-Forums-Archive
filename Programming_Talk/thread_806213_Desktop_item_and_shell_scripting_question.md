---
title: "Desktop item and shell scripting question"
date: 2008-05-24
forum: Programming Talk
---

### Post by skullmunky on 2008-05-24
I have a shell script which sets up some path variables and then runs a binary.  I want to make  a desktop launcher for it, but whenever I launch it it just quits immediately.  Specifically, it's fcheck, the image/animation previewer for maya.

the binary is /usr/autodesk/maya/bin/fcheck.bin, and the shell script is /usr/autodesk/maya/bin/fcheck.  

It runs fine from the command line but I can't get a launcher to work.  I think it might be because fcheck.bin detaches itself from the shell it's run from (I don't know if that's the right term) but what I mean is, when I run it from the terminal I get the prompt back as if it was run with &.  So I think maybe that makes the launcher think the application has completed so it quits; or something. 

Any ideas on how I can tackle this ..?

---

### Post by Xavieran on 2008-05-24
Could you post the code of your shell script?
That would help us help you.

Maybe try to run the fcheck.bin with strace...man strace may help
usually that will give you feedback on whether you've encountered errors or not...

---

### Post by skullmunky on 2008-05-24
Here's the shell script I'm using:

```

#!/bin/csh

if  ( ! $?MAYA_LOCATION ) then
	setenv MAYA_LOCATION /usr/autodesk/maya
endif

set path = ($MAYA_LOCATION/bin $path)

if  ( ! $?LD_LIBRARY_PATH ) then
	setenv LD_LIBRARY_PATH
endif

setenv LD_LIBRARY_PATH $MAYA_LOCATION/lib:$LD_LIBRARY_PATH

setenv MAYA_WEBBROWSER firefox

setenv WF_IMF_SGI_MATTE
setenv WF_IMF_CIN_CORRECTION both
setenv WF_IMF_CIN_WHITE_POINT 685

${MAYA_LOCATION}/bin/fcheck.bin 

```

basically all it needs to do is set the PATH and LD_LIBRARY_PATH variables before launching fcheck, because fcheck needs libs that are in /usr/autodesk/maya/lib and uses a version of imagemagick's imconvert that it has in /usr/autodesk/maya/bin.  

this works fine when run from the terminal but not from a .desktop file.

Below is the original fcheck shell script that comes with maya 2008, which has the same problem:

```

#!/bin/csh -f
#Tag 0x00C98a02
#*
#*+***********************************************************************
#*
#*  Module:
#*	shell wrapper to set environment variables before exec of real function
#*
#*-***********************************************************************
#*


set real_exec = `basename $0`.bin
set real_base = `basename $0`

#
#  Determine if launched from the desktop or a shell.  This will tell
#  us how to display error messages later.
#

set tty = 1

set OSname = `/bin/uname -s`
switch ("$OSname")
    case Linux:
        set lib = lib
        set lsFlags = '-l'
        breaksw

    case IRIX*:
        set lib = lib32
        set libn32 = 1
        set lsFlags = '-Hl'
        if ( -x /bin/tty ) then
            if ( "`tty`" !~ /dev/* ) then
                set tty = 0
            endif
        endif
		breaksw

    default:
        echo "${real_base} is not supported on $OSname."
        exit 1
        breaksw
endsw

#
#  If the MAYA_LOCATION is set, use it.  Otherwise, determine it.
#

if ( $?MAYA_LOCATION ) then
    if ( -x ${MAYA_LOCATION}/bin/${real_exec} ) then
	set real = ${MAYA_LOCATION}/bin/${real_exec}
    else
	unsetenv MAYA_LOCATION
    endif
endif


#
#  Need to determine where Maya resides based on how this shell was
#  invoked.  Determine full pathname, follow soft link, and extract
#  directory.  If the "real" executable is not in a "bin" directory,
#  someone's been screwing around with the distribution, so bail.
#

if ( ! $?MAYA_LOCATION ) then
    #
    #  Create the full pathname of the invoked binary.
    #

    if ( "$0" =~ /* ) then
	set me = "$0"
    else
	set me = `pwd`/$0
    endif


    #
    #  If it's a link, find the actual file.
    #

    while ( -l $me )
		set linkdirname = `dirname $me`
		set me = `/bin/ls $lsFlags $me | tr ' ' '\012' | tail -n 1`
		if ( "$me" !~ /* ) then
	    	set me = $linkdirname/$me
		endif
    end


    #
    #  Binary should be in $MAYA_LOCATION/bin.  Verify that.
    #

    set bindir = `dirname $me`
    if ( -d $bindir ) then
	set bindir = `cd $bindir; echo $cwd`
    endif
    set binfile = `basename $bindir`
    if ( "$binfile" =~ "bin" ) then
	setenv MAYA_LOCATION `dirname $bindir`
	if ( -x ${MAYA_LOCATION}/bin/${real_exec} ) then
	    set real = ${MAYA_LOCATION}/bin/${real_exec}
	else
	    unsetenv MAYA_LOCATION
	endif
    endif
endif

# Determine the location of the A|W Common Utilties
# 
# - If AW_COMMON is set and the directory does not exist, unset AW_COMMON.
# - If AW_COMMON not set and MAYA_LOCATION is set and exists, then set
#   AW_COMMON relative to MAYA_LOCATION
# - if AW_COMMON is still not set, then use the default location

if ( $?AW_COMMON ) then
	if ( ! -d ${AW_COMMON}/COM/bin ) then
		echo "Warning: Invalid AW_COMMON location (${AW_COMMON}), redefining"
		unsetenv AW_COMMON
	endif
endif

if ( ! $?AW_COMMON && $?MAYA_LOCATION) then
	if (-d $MAYA_LOCATION/../COM/bin) then
		setenv AW_COMMON $MAYA_LOCATION/..
	endif
endif

if ( ! $?AW_COMMON) then
	setenv AW_COMMON /usr/aw
endif


if ( $?MAYA_LOCATION ) then
    #
    #  Set environment, and launch the real executable.
    #

    set path = ($MAYA_LOCATION/bin ${AW_COMMON}/COM/bin $path)

    if ( $?libn32 && $?LD_LIBRARYN32_PATH ) then
	setenv	LD_LIBRARYN32_PATH	$MAYA_LOCATION/lib:$LD_LIBRARYN32_PATH
    else if ( $?LD_LIBRARY_PATH ) then
	setenv	LD_LIBRARY_PATH		$MAYA_LOCATION/lib:$LD_LIBRARY_PATH
    else
	setenv	LD_LIBRARY_PATH		$MAYA_LOCATION/lib
    endif
endif

#
#  This allows IMF to save SGI format image files with matte.

setenv WF_IMF_SGI_MATTE

#
#   101914: color correction needed for Cineon files.

setenv WF_IMF_CIN_CORRECTION both
setenv WF_IMF_CIN_WHITE_POINT 685


if ( $?MAYA_LOCATION ) then
    if ( -x $real ) then
	$real $argv:q
	exit $status
    endif
endif

if ( ! $?real ) set real = ${real_exec}

if ( $tty == 1 ) then
    echo The executable \(\`${real}\'\) cannot be found
else
    xconfirm -c -t "The executable \(\`${real}\'\) cannot be found" \
	    -icon warning >&/dev/null
endif
exit 1

#*+
#* ==========================================================================
#* The information  in  this  file is  provided for the  exclusive use of the
#* licensees of Alias Systems Corp. Such users have the right to use, modify,
#* and  incorporate this code  into  other  products  for purposes authorized
#* by the  Alias Systems Corp. license agreement, without fee.
#*
#* Alias Systems Corp. disclaims all warranties with regard to this software,
#* including all implied warranties  of  merchantability and  fitness.  In no
#* event  shall  Alias Systems Corp. be liable for any  special,  indirect or
#* consequential  damages  or  any  damages whatsoever resulting from loss of
#* use, data  or profits, whether in  an  action of  contract,  negligence or
#* other tortious  action,  arising out of or  in connection  with the use or
#* performance of this software.
#* ==========================================================================
#*-

```

---

### Post by skullmunky on 2008-05-27
Well, I think I solved it, by making the script sleep until the main command completes, so the original shell process doesn't quit.  Seems weird but it works ...


Here's the script I came up with:

```

#!/bin/bash

export LD_LIBRARY_PATH=/usr/autodesk/maya/lib
export PATH=$PATH:/usr/autodesk/maya/bin
export MAYA_LOCATION=/usr/autodesk/maya/

export MAYA_WEBBROWSER=firefox

export WF_IMF_SGI_MATTE
export WF_IMF_CIN_CORRECTION=both
export WF_IMF_CIN_WHITE_POINT=685

/usr/autodesk/maya/bin/fcheck.bin
while ps | grep -q fcheck.bin
do
	sleep 1
done

```

---

### Post by Xavieran on 2008-05-29
Glad you fixed it!

Sorry that I couldn't be much help but I didn't quite understand the problem.

:)

---

### Post by geirha on 2008-05-29
> **skullmunky said:**
> 
```

/usr/autodesk/maya/bin/fcheck.bin
while ps | grep -q fcheck.bin
do
	sleep 1
done

```

In that case, using exec would be a bit prettier. Not sure if it will actually work, but worth a try.
```

exec /usr/autodesk/maya/bin/fcheck.bin

```

---

