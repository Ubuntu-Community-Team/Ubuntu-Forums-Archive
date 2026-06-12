---
title: "Script: To ease mounting iso-image files."
date: 2007-06-17
forum: Outdated Tutorials &amp; Tips
---

### Post by ©TriMoon® on 2007-06-17
Here is a little script i wrote to aid in everyday use of iso-images.
To use this script you need these packages:
- fuse-utils
- fuseiso

If you dont have them installed yet you should run these commands according to which you dont have:
```
sudo apt-get install fuse-utils
sudo apt-get install fuseiso

```

Don´t forget to give the script execute permissions after you have downloaded the script, see attachment
```
chmod +x iso_fuse.sh
```

To see the usage just run the script without any arguments.
Feel free to adjust the defaults under ***#Define our defaults***

For those that just like to see the inners without downloading here &#305;s the contents:
```
#!/bin/bash
#Copyrights:	(C)2007+ TriMoon inc.
#Author:	TriMoon <tripple.moon[at]yahoo.com>
#
# This work is licensed under the Creative Commons Attribution-Share Alike 3.0 License.
# To view a copy of this license, visit http://creativecommons.org/licenses/by-sa/3.0/
# or send a letter to Creative Commons, 171 Second Street, Suite 300, San Francisco, California, 94105, USA.

#Define our defaults
readonly mountoptions="ro,allow_other"
readonly mountpoint="/mnt/iso"

##### No need to edit beyond this point.
readonly version="1.00"
readonly scriptname="`basename $0`"
isofile=""

#Script help
function HELP () {
	cat <<-TEXT >&2
		$scriptname version $version
	
		1) Getting help or info about $scriptname :
		   $scriptname -h|--help   Print this message
	
		2) Running $scriptname :
		   $scriptname [iso filename]
		   When invoked without an argument, the currently mounted iso-image is unmounted.
	
		3) Defaults used by $scriptname :
		   mount-point = $mountpoint
		   mount-options = $mountoptions

		Known bug: does not recognize as iso when using "~/" at start of iso-filename.
	TEXT
}

#Check if mountpoint already in use.
function CheckInUse () {
	local RetVal=`mount | grep -c "$mountpoint"`
	if [ $RetVal -gt 0 ]; then
		UnMount
	fi
	return $RetVal
}

#Get the fullpath of the ISO-image
function GetFullPath () {
	local is_absolutepath

	#Checks to see if an absolute path was supplied.
	is_absolutepath=`echo "$1" | grep -c ^[~/\|/]`

	#Add the current working directory onto the isofile if it had no absolute path
	if [ $is_absolutepath -eq 0 ]; then
		isofile=`echo "$PWD/$1"`
	else
		#Replace "~" with "$HOME"
		isofile=`echo "$1" | sed 's/^~/$HOME/'`
	fi
	return
}

#Check to see if the argument is an ISO-file
function CheckISO () {
	local RetVal=`file "$isofile" | grep -c "ISO 9660"`
	if [ $RetVal -eq 0 ]; then
		echo "The file/image you try to mount is not an ´ISO 9660´ !"
		exit
	fi
	return $RetVal
}

#Unmount the currently mounted iso-image
function UnMount () {
	local RetVal
	echo "$scriptname: Unmounting previous iso"
	RetVal=`sudo fusermount -u "$mountpoint"`
	if [ $RetVal -eq 0 ]; then
		echo "$scriptname: Success."
	else
		echo "$scriptname: Failed !"
	fi
	return $RetVal
}

#Mount the requested ISO-image
function Mount () {
	local RetVal
	echo "$scriptname: Mounting ´$isofile´"
	echo "$scriptname:   on ´$mountpoint´"
	echo "$scriptname:   with options: $mountoptions"
	if [ -d $mountpoint ]; then
		RetVal=`sudo fuseiso "$isofile" "$mountpoint" -o "$mountoptions"`
		if [ $RetVal -eq 0 ]; then
			echo "$scriptname: Success."
		else
			echo "$scriptname: Failed !"
		fi
	else
		echo "Mount-point '$mountpoint' does not exist, aborting !"
		exit
	fi
	return $RetVal
}

#Parse command line.
if [ $# -eq 0 ]; then
	CheckInUse
	if [ $? -gt 0 ]; then
		UnMount
	else
		HELP
	fi
else
	case "$1" in
	-h | --help)
		clear
		HELP
		exit 0
		;;
	*)
		#Unmount previous iso if needed.
		CheckInUse
		GetFullPath "$1"
		CheckISO
		#Mount the requested ISO-image
		Mount
		;;
	esac
fi
exit

```

---

### Post by hraposo on 2007-06-23
When I type:
$sh iso_fuse.sh

Give me that message:

$iso_fuse.sh: 19: Syntax error: "(" unexpected

How can I solve it?

---

### Post by ©TriMoon® on 2010-06-28
> **hraposo said:**
> When I type:
$sh iso_fuse.sh

Give me that message:

$iso_fuse.sh: 19: Syntax error: "(" unexpected

How can I solve it?

lol i was skimming through what i posted before when i came along this, thats why the late reaction :D
Your problem is due to the fact that you are trying to run it as a sh script while the script is written for bash.
But i guess you already found that out ;)

---

