---
title: "HowTO Ubuntu System"
date: 2008-06-27
forum: Outdated Tutorials &amp; Tips
---

### Post by ajmorris on 2008-06-27
HowTO use and understand your Ubuntu/linux system. NOTE: not all commands are listed obviously, just ones that i thought were important
feel free to message me, or post here, if you think something else should be added. Other comments also welcome.
Ask for support here also if you wish.
Please tell me if it is too difficult to follow -- Note, pressing Ctrl+F in Firefox will allow for searching of key terms ;)
 
You may also like to see my networking tutorial:
[http://ubuntuforums.org/showthread.php?p=5532395](http://ubuntuforums.org/showthread.php?p=5532395)

[SIZE=5][COLOR=Red]Table of Contents[/COLOR][/SIZE]
[COLOR=DarkOrange][SIZE=2][COLOR=Blue]Finding Some System Info[/COLOR][/SIZE]
   [SIZE=1][COLOR=Green]*Load, statistics and messages
 [/COLOR][/SIZE][/COLOR][SIZE=1][COLOR=Green]  *Running kernel and basic system information[/COLOR][/SIZE][SIZE=1]
[/SIZE] [COLOR=DarkOrange][COLOR=Green][SIZE=1]  *Information about your hardware
      *Kernel Detected Hardware
   *Commands for Users and controlling them
   *Limits
        *Per Shell/Script
        *Per User/Process
      *System Wide Limits
   *Runlevels
      *Standard linux runlevels
      *Debian Runlevels
   *kernel
      *Kernel Modules
      *Compiling Your Kernel[/SIZE]
 [/COLOR][/COLOR][SIZE=2][COLOR=Blue]Listing and manipulating processes [/COLOR][/SIZE][SIZE=1]
   [COLOR=Green]*Listing and Manipulating Processes
      *Priorities
      *Background/Foreground
      *Using Top effectively
      *Signals/Kills
 [SIZE=2][COLOR=Blue]File Systems[/COLOR][/SIZE][/COLOR][/SIZE][SIZE=1]
   [COLOR=Green]*Permissions
   *Disk Information
   *System Mount points
   *Disk Usage
   *Find out who has which files open
   *[/COLOR][/SIZE][SIZE=1][COLOR=Green]Find opened files on a mount point with fuser or lsof:[/COLOR][/SIZE][COLOR=Green]
   *[SIZE=1]About and application[/SIZE][/COLOR]
[SIZE=1][COLOR=Green]  *About a Single File[/COLOR][/SIZE]
[SIZE=1][COLOR=Green]  *Mount/remount a file system
   *Add Swap on the fly
   *Mount a samba share
   *Mount an image
   *Create and burn an ISO image
   *Convert a .nrg file to .iso
   *Convert a cue/bin file to .iso
   *Create a file based image
   *Losetup
   *Create a memory filesystem
   *Disk Performance[/COLOR][/SIZE][SIZE=1][COLOR=Green]
[/COLOR][/SIZE]
[SIZE=4][COLOR=red]**Finding Some System Info**[/COLOR][/SIZE] 
 
*[COLOR=Blue]Load, statistics and messages[/COLOR] -- useful to find out what is happening in your system*
 
# displays and updates the top cpu processes```
top
```# displays your processors related statistics -- install via apt-get install sysstat```
mpstat 1
```# displays your virtual memory statistics```
vmstat 2
```# display I/O statistics (2 s intervals) -- also installed via sysstat```
iostat 2
``` # Last 500 kernel/syslog messages```
tail -n 500 /var/log/syslog
```# Last 500 kernel/syslog messages```
tail -n 500 /var/log/messages 
``` # System warnings messages see syslog.conf```
tail /var/log/warn
```[COLOR=Blue]*Running kernel and basic system information*[/COLOR]
 
# Get the kernel version -- Use uname --help for variations of this command```
uname -a
``` # Show how long the system has been running and CPU load```
uptime
``` # system's host name```
hostname
```# Display the IP address of the host```
hostname -i 
``` # Description of the file system hierarchy```
man hier
```# Show system reboot history```
last reboot
```# Full release info of any LSB distribution```
lsb_release -a
``` # Get Debian version (yes ubuntu gives one, it is based on debian)```
cat /etc/debian_version
```[SIZE=2][COLOR=blue]**Information about your Hardware**[/COLOR][/SIZE] 

[COLOR=Blue]*Kernel detected hardware*[/COLOR]
 
# Detected hardware and boot messages```
dmesg
```# information about installed hardware```
lsdev
```# Read the BIOS```
dd if=/dev/mem bs=1k skip=768 count=256 2>/dev/null | strings -n 8
```# Shows PCI devices```
lspci
``` # Shows USB devices```
lsusb
```# Shows DMI/SMBIOS info (hardware information from the BIOS)```
dmidecode
```# Show a list of all devices with their properties```
lshal
```# Shows a list of connected hardware```
lshw
```# Information about your CPU```
nano -w /proc/cpuinfo
``` # Info about your hardware memory```
nano -w /proc/meminfo
```# Displays your physical memory```
grep MemTotal /proc/meminfo
``` # Watch changeable interrupts continuously -- Watch -n1 is very useful to watch any changing file```
watch -n1 'nano -w /proc/interrupts'
```# Used and free memory (-m for MB)```
free -m
``` # Configured devices```
nano -w /proc/devices
```[SIZE=2][COLOR=blue]Commands for Users and Controlling them[/COLOR][/SIZE]
 
# Shows the active user id with login and group```
id
```# Shows last logins on the system```
last
```# Shows who is logged on the system```
who
``` # Shows last boot time ```
who -b
```# Add group "admin"```
groupadd admin
```# Adds user Joe Bloggs to group admin```
useradd -c "Joe Bloggs" -g admin -m joe
```# Add existing user to group```
usermod -a -G <group> <user>
```# Delete user joe```
userdel Joe
```To temporarily prevent logins system wide (for all users but root) use nologin. 
The message in nologin will be displayed (might not work with ssh pre-shared keys).
 
# Replace Sorry no login now for the message you would like to display
```
echo "Sorry no login now" > /etc/nologin
```[SIZE=2][COLOR=blue]Limits[/COLOR][/SIZE]
 
Some applications require higher limits on open files and sockets. The default limits are sometimes too low.
 
[COLOR=Blue]*Per shell/script*[/COLOR]
 
The shell limits are governed by ulimit. The status is checked
with ulimit -a. For example to change the open files limit from
1024 to 10240 do:
```

ulimit -n 10240                    
```The ulimit command can be used in a script to change the limits for the script only.
 
[COLOR=Blue]*Per user/process*[/COLOR]
 
Login users and applications can be configured in /etc/security/limits.conf. For example:
 
```
nano -w /etc/security/limits.conf
```# Limit user processes```
*   hard    nproc   250              
``` # Limit application open files```
asterisk hard nofile 409600 
```[COLOR=Blue]*System wide limits*[/COLOR]
 
Kernel limits are set with sysctl. Permanent limits are set in /etc/sysctl.conf.
 
# View all system limits```
sysctl -a
```# View max open files limit```
sysctl fs.file-max
```# Change max open files limit```
sysctl fs.file-max=102400          
```# port range```
echo "1024 50000" > /proc/sys/net/ipv4/ip_local_port_range
``````
nano -w /etc/sysctl.conf
```# Permanent entry in sysctl.conf```
fs.file-max=10240
``` # How many file descriptors are in use```
nano -w /proc/sys/fs/file-nr
```[SIZE=2][COLOR=blue]Runlevels[/COLOR][/SIZE]
 
 
Once booted, the kernel starts init which then starts rc which starts all scripts belonging to a runlevel. 
The scripts are stored in /etc/init.d and are linked into /etc/rc.d/rc#.d with # the runlevel number.
 
The actual runlevel can be changed with init. For example to go from 3 to 5:
 
# Enters runlevel 5```
init 5
``` [COLOR=Blue]*Runlevel list*[/COLOR]
 
* 0 Shutdown and halt
 
* 1 Single-User mode (also S)
 
* 2 Multi-user without network
 
* 3 Multi-user with network
 
* 5 Multi-user with X
 
* 6 Reboot
 
The above is for what most linux OSs do, however, [COLOR=Blue]debian[/COLOR] acts slightly differently:
 
* 0 System Halt
 
* 1 Single User
 
* 2 Full multi-user mode (Default)
 
* 3-5 Same as 2
 
* 6 System Reboot 
 
Debian and systems based on Debain, use the command update-rc.d to manage runlevels scripts. 
Default is to start in 2, 3, 4 and 5 and shutdown in 0, 1 and 6.
 
in the following examples, i will use sshd (the ssh server)
 
# Activates samba in the default runlevel```
update-rc.d sshd defaults
```# For use with explicit arguments```
update-rc.d sshd start 20 2 3 4 5 . stop 20 0 1 6 .
```# Disable sshd for all runlevels```
update-rc.d -f sshd remove
```# Shuts down and halts the system -- 'now' can be replace with a number # (# minutes from now)```
shutdown -h now
```Also, debian tends to want to use a tool called 'telinit' to switch init modes.
i.e. #switches to runlevel 3```
telinit 3
```Also, take caution. Whilst you can issue telinit 6 to issue a shutdown... it really is not recommended.
 
 [COLOR=Blue]
*Resetting your root password*[/COLOR] 
 
**EDIT:** Has been removed due to this forum policy: [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414) (thanks Rocket2DMn)
 
**[SIZE=2][COLOR=blue]Kernel[/COLOR][/SIZE]**
 
[COLOR=Blue]*Kernel modules*[/COLOR]
 
# Lists all modules loaded into the kernel```
lsmod
```# To load a module -- I used ndiswrapper here```
modprobe ndiswrapper
```# To unload a module ```
rmmod nidiswrapper
```[COLOR=Blue]*Compiling your Kernel*[/COLOR]
 
# Changes Directory to the current kernel source -- verify the directory with ls -l, and create if necessary with ln -s```
cd /usr/src/linux
```# Cleans everything, including config files```
make mrproper
```# Reuses the old .config if it exists```
make oldconfig
```# or xconfig or gconfig, depending on personal preference```
make menuconfig
```# Creates a compressed kernel image```
make
```# Compiles the modules```
make modules
```# Installs the modules```
make modules_install               
```# Installs the kernel```
make install
```[SIZE=3][COLOR=blue][SIZE=4]**[COLOR=red]Listing and manipulating processes[/COLOR] **[/SIZE][/COLOR][/SIZE]
 
[COLOR=Blue]  *Listing and manipulating processes*[/COLOR]
 
Each process has a unique number, a PID. A list of all running processes is retrieved with ps.
 
# List of all running processes```
ps -A
```# An Extensive list of all running processes```
ps -auxefw
```Many handy uses of ps involve a pipe (|) and grep:
 
# Looks for a process with cron -- may not actually be running, use ps -A for running commands.```
ps axww | grep cron           
``` # an example output -- in this case, cron is not running```
15087 pts/2    R+     0:00 grep --colour=auto cron
```# Finds all ssh PIDs without the grep pid```
ps aux | grep 'ss[h]'
```# Find the PIDs of processes by (part of) name```
pgrep -l sshd 
```# Echos the PID of your shell```
echo $$
```# List processes using port 22 on TCP```
fuser -va 22/tcp
``` # List processes accessing the /home partiton```
fuser -va /home
```# Trace system calls and signals```
strace df
```# Display the last 50 used commands```
history | tail -50
```[COLOR=Blue]*Priorities*[/COLOR]
 
Change the priority of a running process with renice. Negative numbers have a higher priority, 
the lowest is -20 and "nice" have a positive value.
 
# Stronger priority on PID 1070```
renice -5 1070
```# Output would look something like the following:
```
1070: old priority 0, new priority -5
```Start the process with a defined priority with nice. Positive is "nice" or weak, 
negative is strong scheduling priority. Make sure you know if /usr/bin/nice or 
the shell built-in is used (check with which nice).
 
# Stronger priority (/usr/bin/nice)```
nice -n -5 top
```# Weaker priority (/usr/bin/nice)```
nice -n 5 top                      
```# tcsh builtin nice (same as above)```
nice +5 top
```While nice changes the CPU scheduler, an other useful command ionice will schedule the disk IO. 
This is very useful for intensive IO application which can bring a machine to its knees while 
still in a lower priority. You can select a class (idle - best effort - real time), 
the man page is short and well explained.
 
# set idle class for pid 123```
ionice c3 -p123 
```# Run firefox with best effort and high priority```
ionice -c2 -n0 firefox
```# Set the actual shell to idle priority```
ionice -c3 -p$$
```For example, the last command is very useful to compile or debug a large project. 
Every command launched from this shell will have a lower priority and will not disturb the system. 
$$ is your shell pid (use echo $$ to see the PID of your shell.).
 
[COLOR=Blue]*Background/Foreground*[/COLOR]
 
When started from a shell, processes can be brought in the background and back to the foreground with <Ctrl>-<Z> (^Z), 
bg and fg. For example start two processes, bring them in the background, list the processes with jobs and bring one 
in the foreground.
```

ping google.com > ping.log
```# ping is suspended (i.e stopped) with <Ctrl>-<Z>```
^Z
```# put in background and continues running```
bg
```# List processes in background```
jobs -l
```# example output:
```
[1]  - 36232 Running                       ping google.com > ping.log
[2]  + 36233 Suspended (tty output)        less /var/log/messages
```# Bring process number 2 back in foreground```
fg %2 
```Use nohup to start a process which has to keep running when the shell is closed (it is immune to hangups).
 
# Also needs the '&' to sub-task the ping```
nohup ping -i 60 > ping.log &
```[COLOR=Blue]*Using top effectively*[/COLOR]
 
The program top displays running information of processes.
 
# runs top from the terminal```
top
```While top is running press the key h for a help overview. Useful keys are:
 
 
* u [user name] To display only the processes belonging to the user. Use + or blank to see all users
 
* k [pid] Kill the process with pid.
 
* 1 To display all processors statistics (Linux only)
 
* R Toggle normal/reverse sort.
 
 
[SIZE=2][COLOR=blue]Signals/Kill[/COLOR][/SIZE] 
 
Terminate or send a signal with kill or killall. Kill kills something with a PID, killall with the process name, see
man kill and man killall for more info.
 
```
ping -i 60 google.com > ping.log &
```#PID of the ping process```
[1] 4712
``` # same as kill -15 4712```
kill -s TERM 4712 
```# Kill HUP processes by exact name```
killall -1 httpd 
```# Kill TERM processes by (part of) name```
pkill -9 http 
```# Kill TERM processes owned by www```
pkill -TERM -u www 
```# Kill every process accessing /home (to umount)```
fuser -k -TERM -m /home 
```Important signals are (use anything above signal 3 with caution):
 
 
* 1 HUP (hang up)
 
* 2 INT (interrupt)
 
* 3 QUIT (quit)
 
* 9 KILL (non-catchable, non-ignorable kill)
 
* 15 TERM (software termination signal)
 
[SIZE=4][COLOR=red]**File Systems**[/COLOR][/SIZE]
[COLOR=Blue]*Permissions*
[/COLOR]  
Change permission and ownership with chmod and chown. 
The default umask can be changed for all users in /etc/profile. 
The default umask is usually 022. The umask is subtracted from 777, 
thus umask 022 results in a permission 0f 755:
 
1 --x execute # Mode 764 = exec/read/write | read/write | read
2 -w- write # For: |-- Owner --| |- Group-| |Oth|
4 r-- read
ugo=a u=user, g=group, o=others, a=everyone
 
 
# MODE is of the form [ugoa]*([-+=]([rwxXst]))```
chmod [OPTION] MODE[,MODE] FILE    
```# Restrict some-log -rw-r-----```
chmod 640 /var/log/some-log         
```# Same as above```
chmod u=rw,g=r,o= /var/log/some-log 
```# Recursive remove other readable for all users```
chmod -R o-r /home/*
```# Set SUID bit on executable (use with caution)```
chmod u+s /path/to/app
```# Find all programs with the SUID bit```
find / -perm -u+s -print
```# Change the user and group ownership of a file```
chown user:group /path/to/file 
```# Change the group ownership of a file```
chgrp group /path/to/file
```# Change permissions to 640 for all files```
chmod 640 `find ./ -type f -print`
```# Change permissions to 751 for all directories```
chmod 751 `find ./ -type d -print` 
```[COLOR=Blue]*Disk information*[/COLOR]
 
# information about the IDE/ATA disk```
hdparm -I /dev/sda
```# Display and manipulate the partition table```
fdisk /dev/sda
```# Display the disk SMART info (must have a SMART compatible disk) -- install with apt-get install smartmontools```
smartctl -a /dev/sda 
```[COLOR=Blue]*System mount points*[/COLOR]
 
# Show mounted file-systems on the system```
mount | column -t                  
```# display free disk space and mounted devices (use -h to show in human readable format)```
df
```# Show all registered partitions```
nano -w /proc/partitions
```*[COLOR=Blue]Disk usage[/COLOR]*
 
# Directory sizes as listing```
du -sh *                             
```# Total directory size of the current directory```
du -csh 
```# Sort everything by size in kilobytes```
du -ks * | sort -n -r
```# Show files, biggest last```
ls -lSr                              
```[COLOR=Blue]*Find out who has which files opened*[/COLOR]
 
This is useful to find out which file is blocking a partition which has to be unmounted and gives a typical error of:
 
# umount impossible because a file is locking home
```
umount /home/
umount: unmount of /home 
failed:    Device busy 
```*A lot of linux OSs can use fstat for this sort of thing, ubuntu appears not to have it, i will look for another tool for this*
 
 
Find opened log file (or other opened files), say for your Xorg log file:
 
```
ps ax | grep Xorg | awk '{print $1}'
```#example output:```
1252
```The file with inum 212042 is the only file in /var:
```

find -x /var -inum 212042
```# example ouptut: ```
/var/log/Xorg.0.log
```[COLOR=Blue]Find opened files on a mount point with fuser or lsof:[/COLOR]
 
# List processes accessing /home```
fuser -m /home
``````
lsof /home
```#example output:```
COMMAND   PID    USER   FD   TYPE DEVICE    SIZE     NODE NAME
tcsh    29029 joe  cwd    DIR   0,18   12288  1048587 /home/joe (guam:/home)
lsof    29140 joe  cwd    DIR   0,18   12288  1048587 /home/joe (guam:/home)
```[COLOR=Blue]*About an application:*[/COLOR]
 
```
ps ax | grep Xorg | awk '{print $1}'
```# example output:```
3324
``````
lsof -p 3324
```#example output```
COMMAND   PID    USER   FD   TYPE DEVICE    SIZE    NODE NAME
Xorg    3324 root    0w   REG        8,6   56296      12492 /var/log/Xorg.0.log
```[COLOR=Blue]*About a single file:*[/COLOR]
```

lsof /var/log/Xorg.0.log
```# example output```
COMMAND  PID USER   FD   TYPE DEVICE  SIZE  NODE NAME
Xorg    3324 root    0w   REG    8,6 56296 12492 /var/log/Xorg.0.log
```[COLOR=Blue]*Mount/remount a file system*[/COLOR]
 
For example, mounting your cdrom drive. If it is listed in /etc/fstab:
```

mount /dev/cdrom
```if not
 
# typical ubuntu cdrom mount command```
mount -t auto /dev/cdrom /media/cdrom
```# typical IDE```
mount /dev/hdc -t iso9660 -r /media/cdrom
```# typical SCSI cdrom```
mount /dev/scd0 -t iso9660 -r /media/cdrom
```# typical SCSI -- must have ntfs-3g tool installed either install with apt-get```
mount /dev/sdc0 -t ntfs-3g /media/windows
``` # or you could swap ntfs-3g with ntfs if you have the ntfs kernel module installed.```
mount /dev/sdc0 -t ntfs /media/windows
```Entry in /etc/fstab:
 
```
/dev/cdrom   /media/cdrom  auto noauto,fs=cdfss,ro,procuid,nosuid,nodev,exec 0 0

```[COLOR=Blue]*Remount*[/COLOR]
 
Remount a device without unmounting it. Necessary for fsck for example
 
```
mount -o remount,ro / 
```Copy the raw data from a cdrom into an iso image:
```

dd if=/dev/cdrom of=file.iso
```[COLOR=Blue]*Add swap on-the-fly*[/COLOR]
 
Suppose you need more swap (right now), say a 2GB file /swap2gb.
 
```
dd if=/dev/zero of=/swap2gb bs=1024k count=2000
```# create the swap area```
mkswap /swap2gb
```# activate the swap.```
swapon /swap2gb
```# when done deactivate the swap```
swapoff /swap2gb
``` # remove the swap```
rm /swap2gb
```[COLOR=Blue]*Mount a samba share*[/COLOR]
 
Suppose we want to access the SMB share myshare on the computer smbserver, 
the address as typed on a Windows PC is \\smbserver\myshare\. 
We mount on /mnt/smbshare. Warning> cifs wants an IP or DNS name, not a Windows name.
 
# List the shares```
smbclient -U user -I 192.168.16.229 -L //smbshare/
``````
mount -t smbfs -o username=winuser //smbserver/myshare /mnt/smbshare
``````
mount -t cifs -o username=winuser,password=winpwd //192.168.16.229/myshare /mnt/share
```Additionally with the package mount.cifs it is possible to store the credentials 
in a file, for example /home/user/.smb:
 
username=winuser
password=winpwd
 
 
And mount as follow:
 
```
mount -t cifs -o credentials=/home/user/.smb //192.168.16.229/myshare /mnt/smbshare
```[COLOR=Blue]*Mount an image*[/COLOR]
 
# Mount a CD image```
mount -t iso9660 -o loop file.iso /mnt/image
```# Mount an image with ext3 fs```
mount -t ext3 -o loop file.img /mnt/image                   [/code[COLOR=Blue]]*Create and burn an ISO image*[/COLOR]
 
This will copy the cd or DVD sector for sector. Without conv=notrunc, 
the image will be smaller if there is less content on the cd. 
See below and the dd examples.
 
[code]dd if=/dev/cdrom of=/tmp/mycd.iso bs=2048 conv=notrunc
```Use mkisofs to create a CD/DVD image from files in a directory. 
To overcome the file names restrictions: -r enables the Rock Ridge 
extensions common to UNIX systems, -J enables Joliet extensions used 
by Microsoft systems. -L allows ISO9660 filenames to begin with a period.
 
```
mkisofs -J -L -r -V TITLE -o imagefile.iso /path/to/dir

```Also use cdrecord with Linux as described above. Additionally it is possible to 
use the native ATAPI interface which is found with:
```

cdrecord dev=ATAPI -scanbus
```And burn the CD/DVD as above.
dvd+rw-tools
 
The dvd+rw-tools package can do it all and includes growisofs to burn CDs or DVDs. 
The examples refere to the dvd device as /dev/dvd which could be a symlink to /dev/scd0 
(typical scsi on Linux), although you will probably want /dev/cdrom.
 
# -dvd-compat closes the disk
# Burn existing iso image```
growisofs -dvd-compat -Z /dev/dvd=imagefile.iso
```# Burn directly```
growisofs -dvd-compat -Z /dev/dvd -J -R /p/to/data
```[COLOR=Blue]*Convert a Nero .nrg file to .iso*
[/COLOR]  
Nero simply adds a 300Kb header to a normal iso image. This can be removed with dd.
 
# Backup .nrg file first before doing this just in-case```
dd bs=1k if=imagefile.nrg of=imagefile.iso skip=300
```[COLOR=Blue]*Convert a bin/cue image to .iso*[/COLOR]
 
The little bchunk programhttp://freshmeat.net/projects/bchunk/ can do this. 
Can install from the ubuntu repos with sudo apt-get install bchunk
 
```
bchunk imagefile.bin imagefile.cue imagefile.iso
```[COLOR=Blue]*Create a file based image*[/COLOR]
 
```
dd if=/dev/zero of=/usr/vdisk.img bs=1024k count=1024
``````
mkfs.ext3 /usr/vdisk.img
``````
mount -o loop /usr/vdisk.img /mnt/mountpoint
``` # Cleanup```
umount /mnt; rm /usr/vdisk.img
```[COLOR=Blue]*Linux with losetup*[/COLOR]

/dev/zero is much faster than urandom, but less secure for encryption.
 
```
dd if=/dev/urandom of=/usr/vdisk.img bs=1024k count=1024
```# Creates and associates /dev/loop0```
losetup /dev/loop0 /usr/vdisk.img
``````
mkfs.ext3 /dev/loop0
``````
mount /dev/loop0 /mnt
```# Check used loops```
losetup -a
``````
umount /mnt
```# Detach```
losetup -d /dev/loop0
``````
rm /usr/vdisk.img
```[COLOR=Blue]*Create a memory file system*
[/COLOR]  
A memory based file system is very fast for heavy IO application. How to create a 64 MB partition mounted on /memdisk:
 
 
```
mount -t tmpfs -osize=64m tmpfs /memdisk
```[COLOR=Blue]*Disk performance*[/COLOR]
 
Read and write a 1 GB file on partition sda2 (/home)
```

time dd if=/dev/sda2 of=/dev/null bs=1024k count=1000
``````
time dd if=/dev/zero bs=1024k count=1000 of=/home/1Gb.file
``````
hdparm -tT /dev/hda 
```Happy Ubuntuing :)

---

### Post by Rocket2DMn on 2008-06-27
Debian runlevels are a little different than other linux runlevels, you may want to add info about that.
Also, take out the info about (re)setting root password, see [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
You may consider adding links to help wiki pages as well.

---

### Post by ajmorris on 2008-06-27
> **Rocket2DMn said:**
> Debian runlevels are a little different than other linux runlevels, you may want to add info about that.

Tks, added :)
> Also, take out the info about (re)setting root password, see [http://ubuntuforums.org/showthread.php?t=765414](http://ubuntuforums.org/showthread.php?t=765414)
Done, and thanks, dont want this getting jailed :P

---

### Post by jakupl on 2008-06-27
Great stuff, but why don't you use the [CODE] envelopes?

---

### Post by ajmorris on 2008-06-27
> **jakupl said:**
> Great stuff, but why don't you use the [code] envelopes?

I will if you wish :)

That looks much better... i will do the rest later, i have to leave right now

---

### Post by jakupl on 2008-06-27
Only if you like. ;)

However thanks a bunch for making this.

---

### Post by Oldsoldier2003 on 2008-06-28
Good job AJ, a nice resource for beginners and a handy refresher for folks that have been around awhile :)

---

### Post by Oldsoldier2003 on 2008-06-28
```
who -b
``` shows the last system boot time.

```
cat /etc/debian_version
``` will return the Debian version without opening nano.

---

### Post by ajmorris on 2008-06-28
> **Oldsoldier2003 said:**
> ```
who -b
``` shows the last system boot time.

```
cat /etc/debian_version
``` will return the Debian version without opening nano.

Added/changed :)

There will be lots where i used nano that you could use cat or less to view without opening ... I already changed them all from what i had before (vim) to nano... then realised that vim comes standard with ubuntu as well :P

---

### Post by NekoCodi on 2008-06-30
Yeah AJ, thanks man. I'll defnitely get a lot of use out of this!

---

### Post by NovaAesa on 2008-06-30
Nice, very helpful =D

---

### Post by Joeb454 on 2008-08-05
> **NovaAesa said:**
> Nice, very helpful =D

Only just found this, it's very helpful indeed :)

---

### Post by meindian523 on 2008-08-05
r0cks!

---

### Post by SOULRiDER on 2008-08-05
Great tut Aj! Its a really useful set of commands, it would make a nice cheat sheet.

I'll see you around on IRC.

---

### Post by DC@DR on 2008-08-06
Very good one, keep it up, thanks :-)

---

### Post by Belerophon on 2008-08-06
Just want to say thanks for this great post! It is really a good job!

In fact, I think it should be part of some kind of "documentation" of Ubuntu, so it would be more easily find by users...just my opinion, after some situations in which I just wished to kill my self after much research to find the right command...

I'll bookmark this page :D

Thanks a lot AJ!

---

### Post by meindian523 on 2008-08-06
For people who just came across this thread by chance,subscribe for notifications for such great tutorial threads by subscribing to the "Tutorial of the Week" sticky at Tutorials and Tips forum.

---

### Post by run1206 on 2008-08-06
thread bookmarked, thanks a bunch ajmorris!!

---

### Post by samjbobb on 2008-08-08
Thanks a bunch. Just downloaded the post and put it all in a Tomboy note. Useful to have at your fingertips. Great job.

---

### Post by Bruce M. on 2008-08-09
This is a keeper... wish I had this a year ago.

Thanks for your time and work.
Bruce

---

### Post by sjust on 2008-08-09
I wish I had seen this years ago life would have much smoother Nice job

---

### Post by Bodsda on 2008-08-09
Very nice Aj, looks like i know what im gonna read for the next week.

see ya on irc dude

---

### Post by Ryadt on 2008-08-12
Great post..:guitar:

---

### Post by androidkerra on 2009-03-09
a very helpful and informative post or guide rather :D
just need the patience to read it :]

great work!

:KS:KS:KS:KS:KS

---

### Post by Liviu-Theodor on 2009-03-09
Well, ajmorris, this is a laborious work. All I can say is thank you for providing it for users. I think it is helpful for new and old users alike.
=D>=D>=D>=D>=D>

---

### Post by hovzio on 2009-04-24
Thanks ajmorris, theres quite a few cool commands in there. I thought it would be nice to have this as a text file. I downloaded the page source and filtered through it for a nice list of commands including the info headers. The command I used to extract, the author (ajmorris) and the website are included in the file.

I attached the file, dunno I thought maybe somebody may also want this. Thanks again :)

---

### Post by Godly on 2009-04-24
Awesome post! Very useful. Thank you.

---

### Post by A_M_S on 2009-09-17
Great post!

Tnx!

---

### Post by gungrog on 2009-12-07
What a brilliant idea! 
As a complete newbie to Ubuntu\Linux, this is soooo useful. 
Cheers!

---

### Post by heavenwood on 2009-12-09
thank you for this great summary of commands.

may the force be with you. ;)

---

