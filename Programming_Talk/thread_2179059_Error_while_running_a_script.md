---
title: "Error while running a script"
date: 2013-10-06
forum: Programming Talk
---

### Post by ndnd on 2013-10-06
Hello all,
I have ubunutu 12.10 LTS version. 
I am trying to run a script posted below and get an error when it reads the line at the end. I am not able to understand why (I have posted the error below)


> #!/bin/csh -f
#
#
#

if ($?TARGET != 0) goto RUN

set uname=`uname`

switch($uname)

case "SunOS":
	if (-x /bin/isainfo) then
		set osbits=`/bin/isainfo -k`
		if ( $osbits == "sparcv9" ) then
			setenv TARGET SUN64
			goto RUN
			endif
		endif
		
	setenv TARGET SUN
	goto RUN
	breaksw

case "Linux":
	set machine=`uname -m`
	if ( $machine == "ia64" ) then
		setenv TARGET PC_LINUX64
		set processor=`uname -p`
		goto RUN
		endif
		
	if ( $machine == "x86_64" ) then
		setenv TARGET AMD_LINUX64
		goto RUN
		endif
	
	setenv TARGET PC_LINUX
	goto RUN
	endsw

case "Darwin":
	set machine=`uname -m`

	if ( "$machine" == "x86_64" ) then
		setenv TARGET MAC_I64
		goto RUN
		endif	
		
	if ( "$machine" == "i386" ) then
		set rev=`uname -r`
		@ rmajor = `echo $rev | awk -F. '{print $1}'`
		if ( $rmajor < 9) then
			setenv TARGET MAC_I32
			goto RUN
			else
			set bits=`sysctl -n hw.cachelinesize`
			if ( "$bits" == "64" ) \
				setenv TARGET MAC_I64
				set OVERRIDE=1
				goto RUN
				endif
			setenv TARGET MAC_I32
			goto RUN
			endif
		endif	
		
	setenv TARGET MAC_I32
	goto RUN
	breaksw

RUN:

set OVERRIDE=0

if ($1 == "SUN" || $1 == "-SUN") then
	setenv TARGET SUN
	set OVERRIDE=1
	shift
	endif

if ($1 == "PC_LINUX" || $1 == "-PC_LINUX") then
	setenv TARGET PC_LINUX
	set OVERRIDE=1
	shift
	endif

if ($1 == "MAC_I64" || $1 == "-MAC_I64") then
	setenv TARGET MAC_I64
	set OVERRIDE=1
	shift
	endif

if ($1 == "MAC_I32" || $1 == "-MAC_I32") then
	setenv TARGET MAC_I32
	set OVERRIDE=1
	shift
	endif

set d=`dirname $0`
cd $d

./.Installers/Installer_$TARGET




> 
./.Installers/Installer_AMD_LINUX64: Command not found.



If it helps the name of the file I am trying to run is 'Installer'

Any help in this matter would be appreciated.

---

### Post by Iowan on 2013-10-06
Moved to Programming Talk.
FYI - Ubunutu 12.10 is not an LTS version.
From where (which directory) are you running the script?

---

### Post by ndnd on 2013-10-06
sorry about that Iowan 

This is the update of my O.S ofcourse this is not the main issue here but thanks for pointing it out. 
> No LSB modules are available.
Distributor ID: Ubuntu
Description:    Ubuntu 12.04.3 LTS
Release:        12.04
Codename:       precise


I am running the script from the local folder with 

> ./ Installer

So it does run but then gives the error message I have posted. I believe you are hinting at the path and that script not being able to search for the file. I suspect that too but then I maybe wrong...as I don't have much experience with linux scripts

---

### Post by ofnuts on 2013-10-06
> **ndnd said:**
> 

```

./.Installers/Installer_$TARGET

```


If it helps the name of the file I am trying to run is 'Installer'



Given the code above, what you are trying to run isn't "Installer" but "Installer_something" (in a "hidden" directory" called ".Installers" (with leading dot)) under your current directory. Easy enough to add one line to check of the file is there or not...

---

### Post by ndnd on 2013-10-07
Worked like a charm.....ofnuts.....Thanks!

The folder .installer was missing somehow because it was hidden didn't get copied or extracted from .iso file so searched for the folder and transferred and everything was golden :p

---

### Post by ofnuts on 2013-10-07
Who in their right mind would use a dot-name for such a thing?

---

