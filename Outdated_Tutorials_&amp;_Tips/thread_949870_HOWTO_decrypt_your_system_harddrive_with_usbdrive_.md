---
title: "HOWTO: decrypt your system harddrive with usbdrive as key on boot"
date: 2008-10-16
forum: Outdated Tutorials &amp; Tips
---

### Post by StR34k on 2008-10-16
[SIZE="4"]Motivation:[/SIZE]
   To unlock my system hardrive with a removable usb drive as the key.

[SIZE="4"]Prerequisites:[/SIZE]
   1.) You must already have installed a luks encrypted system via the alternate cd. (or for the brave, manually)
   2.) a usb key. any size, to hold the key. (sd card support is experimental)

[SIZE="4"]Procedure:[/SIZE]
1.) First we must backup all the files we are going to edit, so we have somewhere to restore from:
```

sudo cp /boot/initrd.img-$(uname -r)  /boot/initrd.img-$(uname -r).orig
sudo cp /etc/crypttab /etc/crypttab.orig
sudo cp /etc/initramfs-tools/modules /etc/initramfs-tools/modules.orig

```

2.) mount the usb drive the new key is going to reside on, and create a new key.  I use a partition that is labeled 'quays' in my example, and I store the key in a file called 'crypt.0.key', in the directory '.keys' .
```

cd /media/quays/.keys/
dd if=/dev/random of=crypt.0.key bs=1c count=32

```

3.) Now that we have a new random key, we have to add it to the luks encrypted partition.  My luks encrypted partition is /dev/sda2 in the example.  This may ask for 2 passwords, one for sudo, and the luks encryption password.  We assume the default encryption install, since the installer puts the password in keyslot 0, and this new key will be in keyslot 1 by default.  note the keyslot number that is created, as this will be important for reverting.
```

sudo cryptsetup luksAddKey /dev/sda2 /media/quays/.keys/crypt.0.key

```

4.) This is where we have done some magic for you, crypt setup includes an option in the /etc/crypttab to specifiy a script to retrieve the key for an encrytpted drive.  We have written such a script, and we use this to scan for a specified usb drive, and obtain the specified key. and return that to cryptsetup to unlock the partition.  Please feel free to look over this script, so you can see the options available to you (as not all are documented here)  Save this in the file /usr/local/sbin/crypt-usb:
```

#!/bin/busybox ash
# File:crypt-usb

################################################################################
# Variables / config:
################################################################################

myname=$(basename $0)								# script name.
default_timeout='15'								# timeout (s)
prompt="Enter passphrase to unlock the disk $cryptsource ($crypttarget): "	# passphrase prompt
prompt_msg="Searching for removable keys ..."					# startup msg
mnt="/keymount"									# temp mount location
memory="/key_memory"

#
################################################################################

################################################################################
# Functions:
################################################################################

####
# Return true if usplash is running, otherwise return false.
[ -x /sbin/usplash_write ] && usplash_exists='1'
usplash_running()
{
	[ -z "$usplash_exists" ] && return 1
	pidof "usplash" >/dev/null
	return $?
} 

####
# Write output to the console. (usplash not running)
write_to_console()
{
	read system_uptime no_var < /proc/uptime 
	printf '[%8s0000] %s: %s\n' "$system_uptime" "$myname" "$@" >&2
}

####
# Write output to usplash
write()
{
	usplash_running && ( /sbin/usplash_write "TEXT $@" ) 

	write_to_console "$@"

	return 0
}
####
# Set the verbosity according to what the kernel says.
fixup_verbosity()
{
	if [ "$(expr match "$(cat /proc/cmdline)" '.*quiet')" -gt "0" ]; then
		/sbin/usplash_write "VERBOSE off" 2>/dev/null
	else
		/sbin/usplash_write "VERBOSE on" 2>/dev/null
	fi
}
####
# Ask for the password from with in usplash.
usplash_askpass()
{	#	askpass for usplash (return 1 if failure of usplash)
	FAIL_NO_USPLASH=1 /sbin/usplash_write "VERBOSE on" || return 1
	/sbin/usplash_write "CLEAR"	
	/sbin/usplash_write "TEXT $1"

	until [ -n "$BREAK" ]; do
		#	Read Character From Input
		if ! FAIL_NO_USPLASH=1 /sbin/usplash_write "INPUTCHAR"; then
			fixup_verbosity
			return 1
		fi

		ch=$( awk 'BEGIN { RS = "\x04"; FS = "" } ; 
		{ 
			if ($0 ~ /[\x0A\x0C\x0D]/) { printf "ENTER" } 
			else if ($0 ~ /[\x7F\x08]/) { printf "DEL" }
			else { printf $0 }
		}' /dev/.initramfs/usplash_outfifo )

		# 	Handle Characters (break on enter, delete 1 on backspace/delete)
		if [ "$ch" = "ENTER" ]; then
			BREAK="1"
			/sbin/usplash_write "CLEAR"
		elif [ "$ch" = "DEL" ]; then
			text=$(expr substr "$text" "1" $( expr "${#text}" "-" "1" ))
			shown=$(expr substr "$shown" "1" $( expr "${#shown}" "-" "1" ))
		else
			
			if [ -n "$ch" ]; then
				text="$text$ch"
				shown="$shown*"
			else
				/bin/sleep 0.2
				continue			
			fi

		fi

		if [ -n "$usplash_showpass" ]; then
			/sbin/usplash_write "CLEAR"
			/sbin/usplash_write "TEXT $prompt $shown"
		fi

	done
	
	if usplash_running && [ "$(expr match "$(cat /proc/cmdline)" '.*quiet')" -gt "0" ]; then
		/sbin/usplash_write "CLEAR"
		/sbin/usplash_write "VERBOSE off"
	fi	

	printf '%s' "$text"	

	return 0
}

####
# Ask for a password on the console.
ask_pass()
{
	if usplash_running; then
		if usplash_askpass "$1"; then
			return 0
		else
			exec <$(tty) >$(tty) 2>$(tty)
		fi	
	fi
	
	echo -n "$1" >$(tty)

	read -rs text <$(tty)
	printf '%s' "$text"
	
	return 0
}

####
# handle the exit conditions, success, we found the key. or fail, and take the
#   user provided fail action.
cleanup()
{
	if [ -n "$2" ]; then
		write "$2"	
	fi
	
	case "$1" in
		askpass|askpassQuiet)
			[ ! "$1" = "askpassQuiet" ] && write "DEFERRED to askpass"			
			echo -n "1" >$memory 2>/dev/null
			ask_pass "$prompt"

			exit 0
		;;
		fail|retry)
			write "Key retreival failed. Retrying ..."			
		;;
		success)
			write "SUCCESS key found"
		;;
		halt|poweroff|power-off)

			case "$1" in
			halt)
				exit_prompt="Encryption key not found. System Halted"
				exit_action=/bin/halt
			;;
			poweroff|power-off)
				exit_prompt="Encryption key not found. System will Power Down"
				exit_action=/bin/poweroff
			;;
			esac

			#	clear usplash progress bar
			if usplash_running ; then 
				/sbin/usplash_write "PROGRESS 0"
				/sbin/usplash_write "TEXT-URGENT $exit_prompt"	
			else
				write "$exit_prompt"	
			fi

			/bin/sleep 2		
			( $exit_action >/dev/null 2>/dev/null & )
			/bin/sleep 30
			exit 0
		;;
		reboot)
			if usplash_running ; then 
				/sbin/usplash_write "PROGRESS 0"
				FAIL_NO_USPLASH=1 /sbin/usplash_write  \
					"INPUTENTER Encryption key not found. Press ENTER to Reboot" \
					&& cat /dev/.initramfs/usplash_outfifo
			else
				read system_uptime no_var < /proc/uptime 
				printf '[%8s0000] %s: %s' "$system_uptime" "$myname" \
					"Encryption key not found. Press ENTER to Reboot" >&2
				read -rst600 no_var <$(tty)
			fi
	
			( /bin/reboot >/dev/null 2>/dev/null & )
			/bin/sleep 30
			exit 0
		;;
		initramfs)
			/sbin/usplash_write "QUIT"
			chvt 1
			modprobe i8042
			modprobe atkbd

			PS1='(initramfs) ' /bin/sh -i </dev/console >/dev/console 2>&1			
		;;
	esac

	exit 0
}

####
# Parse and sanity check the options we were supplied.
parse_opts()
{
	[ -z "$1" ] && exit 1	
	param="$1"
	crypt_dev="$( expr match ${param%%:*} '\(\/dev\/.\+\)$' 2>/dev/null)"	
	 param="${param#*:}"
	crypt_key="$( expr match ${param%%:*} '\([^/\].*\)$' 2>/dev/null)"	
	 param="${param#*:}"

	# 	Fail on unusable crypttab	
	[ -z "$crypt_dev" -o -z "$crypt_key" ] && \
		cleanup $crypt_fail "bad crypttab"

	crypt_fail=$( expr match ":$param:" \
		".*:\(askpass\|fail\|retry\|power-\?off\|reboot\|halt\|initramfs\):" ) 
	fstype=$( expr match ":$param:" '.*:\(auto\|vfat\|ext[234]\|xfs\):' )
	timeout=$( expr match ":$param:" '.*:\([0-9]\+\):' )
	usplash_showpass=$( expr match ":$param:" '.*:\(showpass\):' )
	
	#	Set defaults
	timeout="${timeout:-15}"
	crypt_fail="${crypt_fail:-askpass}"
	fstype="${fstype:-auto}"

}

####
# Unmount and remove the mount directory.
unmount()
{
	if umount -f "$mnt" ; then
		rm -rf "$mnt"
	fi
}

####
# Search either for the specified block device, or for the user to hit ESC.
search_wait_escape()
{
	num="0"
	time=$(expr "$timeout" "*" "4")
	ESC_KEY=$(echo -ne "\x1B")

#	Loop and check for block device or ESC key
	until [ "$time" -lt "1" ] ; do

#	Check for block device $crypt_dev
		[ -b "$crypt_dev" ] && break

#	read 1 character from input in 1 second
		if ! usplash_running ; then				#  For console interaction

			read -rst0.25 -n1 response <$(tty) || unset response
			[ "$response" = "$ESC_KEY" ] && return 1	

		else
			/bin/sleep 0.25
			while FAIL_NO_USPLASH=1 usplash_write "INPUTCHAR"; do
				response=$( awk '
					BEGIN { RS = "\x04" } ; { FS = "" } ; { printf "%s", $0 }
					' /dev/.initramfs/usplash_outfifo )
				[ -z "$response" ] && break
				[ "$response" = "$ESC_KEY" ] && return 1			
			done
		fi
#	end read 1 response character
	if [ -n "$2" ]; then
		write "$2"	
	fi
		time=$(expr "$time" "-" "1")
	done
	return 0
}
#
################################################################################


################################################################################
# MAIN:
################################################################################
parse_opts "$1"

if [ ! -b "$crypt_dev" ] ; then
	[ "$(cat $memory 2>/dev/null)" -eq "1" ] && cleanup 'askpassQuiet'
fi
write "ALIVE"

if [ "$crypt_fail" = "askpass" ]; then
	prompt_msg="$prompt_msg press ESC to cancel"
fi

if usplash_running ; then
	/sbin/usplash_write "TIMEOUT 60000"
	/sbin/usplash_write "VERBOSE on"
	/sbin/usplash_write "CLEAR"
	write "$prompt_msg"
	fixup_verbosity
else
	write "$prompt_msg"
fi

search_wait_escape

if [ "$?" -ne "0" ]  ; then						#	ESC pressed
	cleanup $crypt_fail
elif [ ! -b "$crypt_dev" ] ; then				#	timed out no block device found
	cleanup $crypt_fail "no block device found"
else										#	block device found
	write "block device found"
fi

if ! mkdir $mnt 2>/dev/null ; then
	cleanup $crypt_fail "unable to make directory $mnt"
fi

fsopts="noexec,sync"

[ "$fstype" = "auto" ] && fstype=$(/lib/udev/vol_id -t $crypt_dev)
[ -z "$fstype" ] && cleanup $crypt_fail "unable to detect the file system type"

if ! mount -rt $fstype -o $fsopts $crypt_dev $mnt 2>/dev/null ; then
	rm -rf $mnt
	cleanup $crypt_fail "unable to mount $crypt_dev as $fstype with $fsopts"
else
	write "mounted block device"
fi

if [ ! -e "$mnt/$crypt_key" ] ; then
	unmount
	cleanup $crypt_fail "keyfile not found"
else
	write "key file found"
fi
	
key=$( cat $mnt/$crypt_key 2>/dev/null )

unmount
	
[ -z "$key" ] && cleanup $crypt_fail "keyfile is blank"
printf '%s' "$key"

if usplash_running; then
	/sbin/usplash_write "VERBOSE on"
	/sbin/usplash_write "STATUS ok"

	if [ "$(expr match "$(cat /proc/cmdline)" '.*quiet')" -gt "0" ]; then
		/bin/sleep 0.5
		/sbin/usplash_write "CLEAR"
		/sbin/usplash_write "VERBOSE off"
	fi	

fi

cleanup success

exit 0

#
################################################################################


```

5.) Make sure the file is owned by root, and is executeable:
```

sudo chown root:root /usr/local/sbin/crypt-usb
sudo chmod 755 /usr/local/sbin/crypt-usb

```

6.) edit /etc/crypttab to use the keyscript:
Original:
```

sda2_crypt /dev/disk/by-uuid/595899a3-eee5-4106-ba7a-737bd3a21189 none luks

```

We replace the keyword 'none' with the parameters taken by crypt-usb, namely the device file of the usbkey that we are using, followed by a colon, and followed by the path to the key, relative to the root of the removable media.  And we add the option 'keyscript' to point to our key script.
Edited:
```

sda2_crypt /dev/disk/by-uuid/595899a3-eee5-4106-ba7a-737bd3a21189 /dev/disk/by-label/quays:.keys/crypt0.key luks,keyscript=/usr/local/sbin/crypt-usb

```

7.) We need to add the usb modueles to the initrd for it to recognize and mount usb drives. edit the file /etc/initramfs-tools/modules, and add:
```

sd_mod
scsi_mod
usb-storage

```

8.) Rebuild the initrd, and reboot
```

sudo update-initramfs -u
sudo reboot

```

Now when you boot your system it will wait 15 seconds to find the key, and if it doesn't, it will fall back to asking you for the password.

[SIZE="4"]Recovery:[/SIZE]

If for some reason your system does not boot, and goes to initramfs, then reboot, and edit the initrd line in your kernel, and append .orig to it.

When booting, hit esc to see the menu, (enter a password if required), e to edit the selected entry, select the line that refers to the initrd, and hit e to edit it.  add '.orig' and hit esc to go back, and then b to boot.

[SIZE="4"]Reverting:[/SIZE]
  So you've tried it, and don't like it.... going back is easy.
1.) first we should remove the key from the encrypted partion.  This will stop the key we created from unlocking the drive.  This is where we will need the keyslot number you noted in step 3 of the installation, by default this will be keyslot 1.
```

sudo cryptsetup luksDelKey /dev/sda2 1

```

2.) then we need to copy the original files we edited back, and remove the keyscript we created.
```

sudo cp /boot/initrd.img-$(uname -r).orig  /boot/initrd.img-$(uname -r)
sudo cp /etc/crypttab.orig /etc/crypttab
sudo cp /etc/initramfs-tools/modules.orig /etc/initramfs-tools/modules
sudo rm /usr/local/sbin/crypt-usb

```

3.) Then we update the initramfs, and reboot, and all is back to normal.
```

sudo update-initramfs -u
sudo reboot

```

[SIZE="4"]Conclusion:[/SIZE]
    There is much much more that can be done with this, one direction we are looking into is making this use an sdcard as the storage for the key ( which should just be a matter of adding the right modules to the initramfs. )  We encourage anyone to take a look at the script we wrote, and see how it can be improved.  This has been tested on hardy(i386 and amd64) and intrepid (amd64 only, but it should work on i386). If it works on other releases, we would like to know, but we haven't tested it, so we can't garuntee it.

---

### Post by echo6 on 2009-09-05
I've tried this.  My usb device is detected, my key file is found but cryptsetup fails, > cryptsetup failed, bad password or options

Just wondering what I can check to troubleshoot.

---

### Post by echo6 on 2009-09-06
```
#!/bin/sh
modprobe usb-storage
sleep
mkdir /keydev 1>&2
mount -t ext3 -o ro /dev/sdb1 /keydev 1>&2
cat /keydev/.keys/crypt0.key
umount /keydev 1>&2
```

Hmmm, this script worked, which leads me to believe there is a problem with the way the script passes the key via the console.  These lines
> [ -z "$key" ] && cleanup $crypt_fail "keyfile is blank"
printf '%s' "$key"

---

