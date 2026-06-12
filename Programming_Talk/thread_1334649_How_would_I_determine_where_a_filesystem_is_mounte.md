---
title: "How would I determine where a filesystem is mounted in bash?"
date: 2009-11-22
forum: Programming Talk
---

### Post by shaggy999 on 2009-11-22
I've got a curious little problem that I'm trying to figure out. Let's say I have a script file located on a partition in a file system. When I run this script I want it to be able to calculate where the mountpoint is for the filesystem that it's on.

So let's say the script is called 'mountlocater.sh" and it's in folder 'foo' on the partition. The full location of the file is '/media/bar/foo/mountlocater.sh'. When I execute this file it should be able to spit out '/media/bar'.

Any ideas?

---

### Post by Reiger on 2009-11-22
Well the basic idea is:

Parse output of `mount' (pattern is: "{$dev} on {$mountpoint}") and scan for all $mountpoint that amount to the start of $PWD (when run from a removeable device you will typically find 2). Compare the mountpoints that match: longest string wins call it $mountpointIFound. Check back with the original output of mount and find the corresponding {$dev} in the string {$dev} on {$mountpointIFound}...

... Return that $dev.

---

### Post by stroyan on 2009-11-22
You can use "${BASH_SOURCE[0]}" to get the file that bash is reading the script from.
You may want to then follow symlinks with "readlink -f" and
strip off the file name with "dirname".

script_dir="$(dirname "$(readlink -f ${BASH_SOURCE[0]})")"

You can get mount point information from the "mount" command or the "/etc/mtab" file or from the "df" command.  You may need to
use the /etc/mtab file and special parsing of octal escape sequences to correctly handle mount points that have spaces in the name.  (Or you could parse the output of df and take everything after the first "/" as part of the directory name.)

---

### Post by slakkie on 2009-11-22
I would use the mount command.

---

### Post by shaggy999 on 2009-11-22
Thanks, guys. This is what I got and thought I'd share it:

```

#!/bin/bash

SCRIPT_DIR="$(dirname "$(readlink -f ${BASH_SOURCE[0]})")"

MOUNTS=`mount | awk -- '{print $3}'`

LONGEST_LENGTH=0
LONGEST_MATCH=""

for MOUNT in $MOUNTS
do
    RESULT=`echo "$SCRIPT_DIR" | grep -ce "$MOUNT"`

    if [ $RESULT -ne 0 ]
    then
	if [ ${#MOUNT} -gt ${#LONGEST_LENGTH} ] ; then
	    LONGEST_LENGTH=${#MOUNT}
	    LONGEST_MATCH="$MOUNT"
	fi
    fi
done

echo $LONGEST_MATCH

```

This appears to work pretty well. As mentioned above, this probably won't work with directories that have spaces in them, but that's not a worry for me.

Thanks a bunch!

---

### Post by falconindy on 2009-11-22
Same idea; a little more concise. Also, this should work on mounts with white space in the path, though I didn't directly test that theory:
```
#!/bin/bash

script_dir=$(readlink -f "${BASH_SOURCE[0]}")

for mount in $(mount | grep ^/dev | cut -d\  -f3-); do 
	result=($(echo "$script_dir" | grep -o "$mount"))
	if [[ ${#result} -gt ${#mount_point} ]]; then
		mount_point="$result"
	fi
done

echo $mount_point
```

---

### Post by shaggy999 on 2009-11-22
That's much more concise, yes. I eventually put this all into a larger script, which I thought I'd share. The whole point of this task was to make it easy for me to bootstrap newly installed machines with my portable external HD that contains several mirrored repositories. The main problem I have found is that two Ubuntu machines never seem to mount the same way. When I plug the drive into my machine I have it set to mount to '/media/repositories' while other machines will mount it to '/media/disk-0' or even '/media/$UUID'. This makes it easy and quick for me to generate the /etc/apt/sources.list files without hand-editing everything.

Check it out:

```

#!/bin/bash
 
LOCAL=false

# Parse options
while getopts ":d:lh" opt; do
  case $opt in
    d)  DIST="$OPTARG" ;;
    l)  LOCAL=true ;;
    h)  echo "usage: -d dist [ -l ]" >&2 ;;
    \?) echo "Invalid option: -$OPTARG" >&2 ; exit 1 ;;
    :)  echo "Option -$OPTARG requires an argument." >&2 ; exit 1 ;;
  esac
done

# Ensure a distribution is chosen before continuing
if [[ -z $DIST ]] ; then echo "usage: -d dist [ -l ]" >&2 ; exit 1 ; fi

if $LOCAL ; then
	SCRIPT_DIR="$(dirname "$(readlink -f ${BASH_SOURCE[0]})")"

	MOUNTS=`mount | awk -- '{print $3}'`

	LONGEST_LENGTH=0
	LONGEST_MATCH=""

	for MOUNT in $MOUNTS
	do
	    RESULT=`echo "$SCRIPT_DIR" | grep -ce "$MOUNT"`

	    if [ $RESULT -ne 0 ]
	    then
		if [ ${#MOUNT} -gt ${#LONGEST_LENGTH} ] ; then
		    LONGEST_LENGTH=${#MOUNT}
		    LONGEST_MATCH="$MOUNT"
		fi
	    fi
	done
   sed -e s:{DIST}:$DIST:g -e s:{MOUNT}:"$LONGEST_MATCH": sources.list.local.generic
else
   sed -e s/{DIST}/$DIST/g sources.list.remote.generic
fi

```

The following two files are also included in the same directory:

sources.list.local.generic
```

deb file://{MOUNT}/{DIST}/canonical	        {DIST}		main restricted universe multiverse
deb file://{MOUNT}/{DIST}/canonical	        {DIST}-updates	main restricted universe multiverse
deb file://{MOUNT}/{DIST}/canonical	        {DIST}-security	main restricted universe multiverse
deb file://{MOUNT}/{DIST}/medibuntu	        {DIST}		free non-free
deb file://{MOUNT}/{DIST}/virtualbox		{DIST}		non-free


```


sources.list.remote.generic
```

deb http://ubuntu.osuosl.org/ubuntu                     {DIST}		main restricted universe multiverse
deb http://ubuntu.osuosl.org/ubuntu                     {DIST}-updates	main restricted universe multiverse
deb http://ubuntu.osuosl.org/ubuntu                     {DIST}-security	main restricted universe multiverse
deb http://packages.medibuntu.org	                {DIST}		free non-free
deb http://download.virtualbox.org/virtualbox/debian	{DIST}		non-free


```

Now I can update systems with the following steps:
1) ./sourcemaker -d distro -l | sudo tee /etc/apt/sources.list
2) Install stuff
3) ./sourcemaker -d distro | sudo tee /etc/apt/sources.list

Yay.

Next comes the post where somebody says, "You know... you could have done the same in this single line of code..." :)

---

