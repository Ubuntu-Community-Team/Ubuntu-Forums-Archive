---
title: "Help fixing a shell script error."
date: 2008-03-26
forum: Programming Talk
---

### Post by Gerlads Mod on 2008-03-26
Whenever I save my shell script and try to run it in terminal, it outputs the following:
```

line 181: syntax error: unexpected end of file

```

My script:
```

#!/bin/bash

$disk
$device
$root
$despertar
$despertar37
$despertar38
$format_disision
pwd = $cd

CheckIfDiskExists()
{
	echo "Verifing that disk exists..."
	if [ !-e "$disk" ]
	then
		echo "The Disk you have supplied does not exist."
		echo "Make sure your PSP is correctly plugged in."
		echo 'You can also check "sudo fdisk -l" to find Disk.'
		exit 0
	fi
	
	if [ -e "$disk" ]
	then
		echo "Verification complete. Disk exists."
	fi
	return
}syntax error: unexpected end of file


CheckIfDeviceExists()
{
	echo "Verifing that device exists..."
	if [ ! -e "$device" ]
	then
		echo "The Device you have supplied does not exist."
		echo "Make sure your PSP is correctly plugged in."
		echo 'You can also check "sudo fdisk -l" to find Device.'
		exit 0  # there had better be a directory

	fi
	
	if [ -e "$device" ]
	then
		echo "Verification complete. Device exists."
	fi
	return
}

CheckIfRootExists()
{
	echo "Verifying that PSP's root dir. exists..."
	if [ ! -e "$root" ]
	then
		echo "The PSP root direcotry you have supplied does not exist."
		echo "Make sure the PSP is mounted."
		exit 0
	fi
	
	if [ -e "$root" ]
	then
		echo "Verification complete. Root dir. exists."
	fi
	return
}

format_memory_stick()
{
	while [ ! "$format_desision" = y -o ! "$format_desision" != n ]
	do
		echo "You are about to completetly format your Memory Stick."
		echo "Proceed with formatting? [y/n]"
		read format_desision
		if [ "$format_desisiif [ "$despertar" = false ]
then
	cp -r $cd/Pandora/* $root
	echo "Please disable USB connection and then renable it."
	echo "Push Enter when ready..."
	read pause
	cp $root/msipl.bin /tmp
	cd /tmp
	dd if=msipl.bin of=$disk bs=512 seek=16
	sync
	echo "Pandora Memory Stick made with success!"
	echo "Enjoy your homebrew."
	exit 0
fi
exit 0on" = y ]
		then
			fdisk $disk < $cd/files/command
			mkfs.vfat $device
		else 
			if [ "$format_desision" = n ]
			then
				echo "Formatting aborted."
				exit 0
			else
				echo "Please enter a \"y\" or \"n\""
			fi
		fi
	done
	return
}

battery_install()
{
	cd $root
	if [ "$batteryinstall" = true ]
	then
		mkdir PSP
		cd ./PSP
		mkdir GAME
		cd $cd
		cp pandora_battery $root/PSP/GAME
		cp pandora_battery% $root/PSP/GAME
	fi
	return
}

# Main code here ---------------------------------
 
if [ "$2" = -d ]
then
	$despertar = true
else 
	$despertar = false 
fi


if [ "$despertar" = true ]
then
	if [ "$3" = 3.7 ]
	then
		$despertar37 = true
	else
		if [ "$3" = 3.8 ]
		then
			$despertar38 = true
		else
			echo "You did not enter a valid firmware number."
			echo "You must enter 3.7 or 3.8"
			exit 0
		fi
	fi
fi
	
if [ "$despertar" = true ]
then
	$4 = $disk
	$5 = $device
	$6 = $root
else
	$2 = $disk
	$3 = $device
	$4 = $root
fi
	
CheckIfDiskExists
CheckIfDeviceExists
CheckIfRootExists


if [ "$#" = -b ]
then
	$batteryinstall = true
else
	$batteryinstall = false
fi
sudo umount $device
format_memory_stick

echo "Please disable USB connection and then renable it."
echo "Push Enter when ready..."
read pause
if [ "$batteryinstall" = true ]
then
	battery_install
fi

if [ "$despertar" = false ]
then
	cp -r $cd/Pandora/* $root
	echo "Please disable USB connection and then renable it."
	echo "Push Enter when ready..."
	read pause
	cp $root/msipl.bin /tmp
	cd /tmp
	dd if=msipl.bin of=$disk bs=512 seek=16
	sync
	echo "Pandora Memory Stick made with success!"
	echo "Enjoy your homebrew."
	exit 0
fi
exit 0

```

Anyone know what is wrong here?
I spent about 2 hours throughly checking this thing.

---

### Post by LaRoza on 2008-03-26
The last "if" isn't ended with a "fi"

---

### Post by Gerlads Mod on 2008-03-26
Never mind I fixed that error. But now I got more.
It's not finding my file.
When I enter this:
```

./PandoraInstaller /dev/sdb /dev/sdb1 /media/disk

```

It outputs:
```

./PandoraInstaller: line 112: =: command not found
./PandoraInstaller: line 139: /dev/sdb1: Permission denied
./PandoraInstaller: line 140: /media/disk: is a directory
./PandoraInstaller: line 141: =: command not found
Verifing that disk exists...
The Disk you have supplied does not exist.
Make sure your PSP is correctly plugged in.
You can also check "sudo fdisk -l" to find Disk.

```

---

### Post by LaRoza on 2008-03-26
> **Gerlads Mod said:**
> Never mind I fixed that error. But now I got more.
It's not finding my file.
When I enter this:
```

./PandoraInstaller /dev/sdb /dev/sdb1 /media/disk

```

It outputs:
```

./PandoraInstaller: line 112: =: command not found
./PandoraInstaller: line 139: /dev/sdb1: Permission denied
./PandoraInstaller: line 140: /media/disk: is a directory
./PandoraInstaller: line 141: =: command not found
Verifing that disk exists...
The Disk you have supplied does not exist.
Make sure your PSP is correctly plugged in.
You can also check "sudo fdisk -l" to find Disk.

```
Does your editor have line numbers? Those errors point to them.

---

### Post by Gerlads Mod on 2008-03-26
Yeah I fixed some of them now.
But I just keep running into more problems now.
I may be able to just work these bugs out myself now.

---

### Post by ghostdog74 on 2008-03-26
you don't declare variables with "$" sign in bash.
eg
variable="some value" , not $variable="some value"

also, from your code posting, you have some typos
eg 
```

..
exit 0on" = y ]
..

```
you can use set -x in your script for debugging.

---

