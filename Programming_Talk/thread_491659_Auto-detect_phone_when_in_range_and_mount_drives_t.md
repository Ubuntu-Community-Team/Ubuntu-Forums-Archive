---
title: "Auto-detect phone when in range and mount drives to filesystem?"
date: 2007-07-03
forum: Programming Talk
---

### Post by liquid circuit on 2007-07-03
**Summary: **Attempting to auto-mount my phone's disks into my file system when it is in Bluetooth range (so when I get home from work, the device mounts; am I lazy?)

**System Info:**  [Ubuntu 7.04]("http://releases.ubuntu.com/feisty/"), [Logitech MX5000]("http://www.logitech.com/index.cfm/products/details/US/EN,CRID=2158,CONTENTID=10776") bundled Bluetooth dongle, [bluez-utils]("http://www.bluez.org/") (et al, for enabling bluetooth support), [p3nfsd]("http://www.koeniglich.de/p3nfs.html") (for mounting S60 filesystem), [Nokia 6620 Symbian S60 Smartphone]("http://seap.forum.nokia.com/devices/6620"), [nfsapp]("http://www.koeniglich.de/p3nfs.html") (S60 app to allow NFS access to phone's filesystem)

**Issue:  **I have built a script (using the script on [this page]("http://nerdvittles.com/index.php?p=79") as a base) that will periodically check if my phone (Nokia 6620) is within range and has bluetooth turned on.  If the device is within range, the script will attempt to mount the phone into the filesystem using **p3nfsd**.  In order to successfully mount the phone, an app called **nfsapp** must be running on my phone.

So, I've gotten the script working correctly when run from a terminal via:
```
sh /home/USER/Scripts/DetectPhone.sh
```
It doesn't seem to work correctly when I invoke it at start-up by adding the following command to **/etc/init.d/rc.local**
```
start-stop-daemon --start --exec /home/USER/Scripts/DetectPhone.sh -b
```
Also, the preceding command doesn't seem to get it working correctly if entered into a terminal/alias.

Now, as a **disclaimer**, I am a total noob to Linux/Ubuntu...I've managed to get my widescreen LCD working in its native resolution, I got Beryl running, I got my Logitech MX5000 bluetooth keyboard and MX1000 bluetooth mouse working using Bluetooth (not RF), and now I've built the following script which works if invoked using sh in a terminal, but not as a daemon... I'm learning/adjusting!:
```
#!/bin/bash
# Syntax: ./whereib
#
# This script was based off of a script found at http://nerdvittles.com/index.php?p=79
#
# On a clunker PC it takes about 20 seconds for a test to fail
# and it takes about 5 seconds for a test to succeed, i.e. BT MAC found
# 
# To run this script at startup in the background in Ubuntu, add the
# following command (no quotes, replace $PATH TO SCRIPT$ with the script
# location) to /etc/init.d/rc.local
# "start-stop-daemon --start --exec /$PATH TO SCRIPT$/DetectPhone.sh -b"


# Bluetooth MAC address for device to be mounted
deviceid=AA:BB:CC:DD:EE:FF

# Bluetooth name for device to be mounted
devicename=DEVICENAME

# Parameters to be passed to p3nfsd when called
mountparameters="-series60 -tty /dev/rfcomm2 -dir /mnt/phone -speed 115200 -timeout 10000"

# Assume device is out of range when script is initially executed
# status == 0 if device is not within range
# status == 1 if device is within range
# status == 2 if device is mounted
# status == 3 if mounting failed
status=0

# When mounted, check for status change ever X seconds (60 = 1 minute)
mountedsleep=60

# When unable to connect, retry every X seconds (1800 = 30 minutes)
errorsleep=300

# When out of range, scan for device every X seconds (30 = 30 seconds)
outofrangesleep=30


# Run script in endless loop
count=0
while [ $count -lt 1 ] ; do

	# Check if device's C: disk is mounted to the file system.
	# If mounted, wait, then check again.
	if [ -d /mnt/phone/C: ] ; then

		# Print debug message and date/time stamp
		echo $devicename STILL MOUNTED ;
		date

		# Pause script for X seconds
		sleep $mountedsleep

	# If device's C: disk is not mounted, proceed...
	else

		# Probe specified MAC address (device), return device name
		hcitool name $deviceid > /tmp/$devicename

		# If any device name is returned, the specified
		# device is in range.
		if [ -s /tmp/$devicename ] ; then
			status=1

			# Print debug message and date/time stamp
			echo $devicename IN RANGE ;
			date

		# If no device name is returned, the specified
		# device is out of range, or its Bluetooth is off.
		else
			status=0

			# Print debug message and date/time stamp
			echo $devicename OUT OF RANGE ;
			date

			# Pause script for X seconds
			sleep $outofrangesleep
		fi

		# If device is in range, proceed...
		if [ $status -eq 1 ] ; then

			# Print debug message and date/time stamp
			echo $devicename TRYING TO MOUNT ;
			date

			# Attempt to mount device
			p3nfsd $mountparameters

			# If the mount command's exit state is succesful
			# change status to mounted
			if [ $? -eq 0 ] ; then
				status=2
				echo $devicename SUCCESSFULLY MOUNTED ;
				date

			# If the mount command's exit state is unsuccesful
			# an error occured attempting to mount (usually
			# indicating NFSAPP was not running on device, or
			# the NFSAPP not set to Bluetooth mode)
			else
				status=3
				echo $devicename COULD NOT MOUNT ;
				date

				# Pause script for X seconds
				sleep $errorsleep
			fi
		fi
	fi

# Repeat loop
done
```

Any suggestions why this does not work correctly when I try to run it as a daemon, considering that it runs correctly when run as a script in a terminal?  Also, any suggestions on streamlining the script for efficiency, and conservation of battery charge in the phone?

---

