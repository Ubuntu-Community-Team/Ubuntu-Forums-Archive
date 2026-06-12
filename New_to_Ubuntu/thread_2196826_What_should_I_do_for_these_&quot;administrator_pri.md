---
title: "What should I do for these &quot;administrator priviliges&quot; requirements?"
date: 2013-12-31
forum: New to Ubuntu
---

### Post by ruwan2 on 2013-12-31
Hi,
I install an SDK setup script on Ubuntu 12.04, 32 bit. This script has the following echos. I think that I have the administrator priviliges for this computer (Is it not? How to verify it).
Because the system already has a [COLOR=#ff0000]minirc.dfl [/COLOR]file, I think that I simply run (which is also shown by the instruction of the SDK):
./setup.**** is refused to overwritten the old minirc.dfl. (I am not totally sure because I am still new to Linux yet).

I don't know what is wrong with my part and how to do is right. I don't see that there is opportunities to add 'sudo' when the script runing. Or, I should run the script as: 
sudo ./setup.sh Could you tell me and give some explanations? 
Thank you.




```
setup package script
This script will make sure you have the proper host support packages installed
This script requires administrator priviliges (sudo access) if packages are to be installed.
-------------------------------------------------------------------------------
System has required packages!
--------------------------------------------------------------------------------
Package verification and installation successfully completed
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
In which directory do you want to install the target filesystem?(if this directory does not exist it will be created)
[ /home/robert/ti-sdk-am335x-evm-06.00.00.00/targetNFS ] 
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
This step will extract the target filesystem to /home/robert/ti-sdk-am335x-evm-06.00.00.00/targetNFS

Note! This command requires you to have administrator priviliges (sudo access) 
on your host.
Press return to continue

Successfully extracted tisdk-rootfs-image-am335x-evm.tar.gz to /home/robert/ti-sdk-am335x-evm-06.00.00.00/targetNFS
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
This step will set up the SDK to install binaries in to:
    /home/robert/ti-sdk-am335x-evm-06.00.00.00/targetNFS/home/root/am335x-evm

The files will be available from /home/root/am335x-evm on the target.

This setting can be changed later by editing Rules.make and changing the
EXEC_DIR or DESTDIR variable (depending on your SDK).

Press return to continue
Rules.make edited successfully..
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
This step will export your target filesystem for NFS access.

Note! This command requires you to have administrator priviliges (sudo access) 
on your host.
Press return to continue

 * Stopping NFS kernel daemon                                            [ OK ] 
 * Unexporting directories for NFS kernel daemon...                      [ OK ] 
 * Exporting directories for NFS kernel daemon...                        [ OK ] 
 * Starting NFS kernel daemon                                            [ OK ] 
--------------------------------------------------------------------------------
--------------------------------------------------------------------------------
Which directory do you want to be your tftp root directory?(if this directory does not exist it will be created for you)
[ /tftpboot ] 
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------
This step will set up the tftp server in the /tftpboot directory.

Note! This command requires you to have administrator priviliges (sudo access) 
on your host.
Press return to continue

/tftpboot already exists, not creating..

Successfully copied uImage-am335x-evm.bin to tftp root directory /tftpboot

/etc/xinetd.d/tftp already exists..
/tftpboot already exported for TFTP, skipping..

Restarting tftp server
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service xinetd stop

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the stop(8) utility, e.g. stop xinetd
xinetd stop/waiting
Rather than invoking init scripts through /etc/init.d, use the service(8)
utility, e.g. service xinetd start

Since the script you are attempting to invoke has been converted to an
Upstart job, you may also use the start(8) utility, e.g. start xinetd
xinetd start/running, process 8299
--------------------------------------------------------------------------------

--------------------------------------------------------------------------------"
This step will set up minicom (serial communication application) for
SDK development


For boards that contain a USB-to-Serial converter on the board such as:
    * BeagleBone
    * AM335x EVM-SK
    * OMAP5 uEVM

the port used for minicom will be automatically detected. By default Ubuntu
will not recognize this device. Setup will add a udev rule to
/etc/udev/ so that from now on it will be recognized as soon as the board is
plugged in.

For other boards, the serial will defualt to /dev/ttyS0. Please update based
on your setup.

--------------------------------------------------------------------------------


NOTE: For boards with a built-in USB to Serial adapter please press
      ENTER at the prompt below.  The correct port will be determined
      automatically at a later step.  For all other boards select
      the serial port that the board is connected to
Which serial port do you want to use with minicom?
[ /dev/ttyS0 ] 

Copied existing /home/robert/.minirc.dfl to /home/robert/.minirc.dfl.old
tee: /home/robert/.minirc.dfl: Permission denied
Failed setup, aborting..
Failed setup, aborting..
robert@M5100:~/ti-sdk-am335x-evm-06.00.00.00$ 

```

---

### Post by JKyleOKC on 2014-01-01
Yes, run the script as "sudo ./setup.sh" and you should be okay. The first thing that will happen after you hit Enter on that command will be a system request for your password. Type in your own login password, keeping in mind that it's case sensitive. You won't see any indication that you have hit any keys; this is a security measure to prevent anyone peeking over your shoulder from learning anything at all about your password. After typing the password, hit Enter, and the script should begin just as it did without the "sudo" prefix -- but now the overwriting should take place.

This will work if you are logged in as the very first user created during installation of Linux itself; only that user has automatic access to the "sudo" features, so if you have added other users and are doing this as one of them, "sudo" won't work -- it will give an official-sounding message that this attempt will be reported, instead. If that happens, just logout, log back in as that first user, change directory to the SDK location, and try again.

Hope this helps!

---

