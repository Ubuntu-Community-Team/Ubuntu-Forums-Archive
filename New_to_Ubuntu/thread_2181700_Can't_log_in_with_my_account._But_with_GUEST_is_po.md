---
title: "Can't log in with my account. But with GUEST is possible."
date: 2013-10-18
forum: New to Ubuntu
---

### Post by thiago-canaes on 2013-10-18
Hello!
I'm pretty new with unbuntu. Been using for 2 month now for learning purposes.
My PC has been running nonstop for 3 weeks as a minecraft server and today we had a black out.
I booted my pc, pressed F to fix any possible error and It didn't log in with my account. (it is set to auto login) It displayed the log in screen, wher I had to type my password.
I typed my password, the screen blinked and then returned to the loging screen. (i know its the correct one, cos i tried a wrong password, and a red "wrong password" message appeared)
I could log in with the guest account (which is the one im currently using).
I gess there might be some error with my account startup, but there is no message and I don't know how to see or search where a error message could be seen...
I don't remmember installing anything that could affect my account startup without rebooting the system to see if it would work properly. (including updates)

Im using the 12.04 LTS version.

well, tnks in advance!
Thiago.

---

### Post by papibe on 2013-10-18
Hi thiago-canaes. Welcome to the forum ):P

Try to login in text mode to see if it is a core problem, or a problem with the GUI login: boot normally, and when you get to the GUI login, press Ctrl+Alt+F1. You'll be presented with a text mode login.

Note that you can always go back to the GUI by pressing Ctrl+Alt+F7

Let us know how it goes.
Regards.

---

### Post by thiago-canaes on 2013-10-18
Hi! Tnks for the quick reply.
I was able to log in in text mode. There is a message, though. It says: "No directory, logging with HOME = /" Is it an error?

Can I start the GUI from text mode?

---

### Post by papibe on 2013-10-18
It looks like there is a problem with the disk or partition where your user files are.

Boot into recovery mode, and then choose from the menu the option ''fsck  - Check all filesystems'. See if errors are found and if they were repaired.

Then select the option 'root - Drop a root shell prompt', and run this to reboot:
```
reboot
```

Let us know how it goes.
Regards.

---

### Post by Bashing-om on 2013-10-18
thiago-canaes; Hi !

Not so much an error as an advisory, unusual and certainly not common.
Post back the output of terminal commands:
```

pwd
ls -la

```
Where "pwd" = Present Working Directory, so we know where you are in the file system;
"ls" = list, to list the contents of where you are, looking to see if you are in a /home directory and also if the files .Xauthority and .ICEauthority exist.

[INDENT][INDENT]a mystery unfolding ?[/INDENT][/INDENT]

---

### Post by thiago-canaes on 2013-10-18
Ok.. I gess I have a clue.
I have a SSD and a HD.
When I installed, I set the "/" to the SSD and "/home" to the HD.
Maybe, ubuntu is not "seeing" the HD, only the SSD.
How can I see if its true?

---

### Post by thiago-canaes on 2013-10-18
yep.. gess thats the problem.
I booted in Recovery Mode, and the error is: "/dev/sdb1: Unexpected Inconsistency: Run [COLOR=#000000]fsck manually.
...
mountall: Filesystem has error: /home
mountall: Skipping mounting /home since Plymouth is not available[/COLOR]

---

### Post by thiago-canaes on 2013-10-18
I booted with[COLOR=#000000] in root shell option.
umounted /dev/sdb1 and executed FSCK.
It returned: "error reading block (attempt to read block from filesystem resulted in short read)"
I gess I lost my HD... 
I have another one, how can I make linux sees it as a new /home?[/COLOR]

---

### Post by Bashing-om on 2013-10-18
thiago-canaes;

See papibe's most excellent advise, suggested to follow and advise results.

To aid in your thought process, to see what the disks are and the booting relationships:
```

sudo fdisk -lu
sudo parted -l
sudo parted /dev/sda unit s print
sudo parted /dev/sdb unit s print
sudo blkid
cat /etc/fstab
mount

```

[INDENT][INDENT]just try'n to help
[/INDENT][/INDENT]

---

### Post by Bashing-om on 2013-10-19
thiago-canaes;
Let's not get to far ahead of our selves, but, if it is a bad superblock, there are means to using alternative superblocks.
At this stage for thinking purposes only:
```

sudo dumpe2fs /dev/sdb1 | grep -i backup

```
to see the backups.
It is late for me and my thinking processes have become forced and difficult to focus. I am ceasing for my evening.

[INDENT][INDENT]where there is a will there is a way
[/INDENT][/INDENT]

---

### Post by papibe on 2013-10-19
Sorry to hear that. Yes you can get a new HD as your new home.

First start by physically installing the new HD. Then you need to format it, and finally edit your fstab to permanently mount it as your /home.
 
There's a couple of approaches to do this:
[LIST]
[*]Do all the work on the command line, or
[*]Make a quick fix, so you can boot into the GUI, and use the available tools there (gparted and gedit).
[/LIST]
I'm going to guess you would like to get to the GUI, as most of us would so do this:
[LIST]
[*]Boot into recovery mode and get a root prompt.
[*]Comment out the current /home mount to avoid the system keep trying to access to bad HD:
```
nano /etc/fstab
```
[*]Look for the line with '/home' in the 2nd column, and put a comment at the begining of the line. It should end up looking something like this:
```
# /home was on /dev/sda2 during installation
#UUID=4498aa1b-7d1b-4612-bbee-dfe456091814 /home           ext4    defaults      
```
[*]Save the file and exit.


[*]Run this command to double check the path of your user:
```
awk -F: '/youruser/ {print $6}' /etc/passwd
```
(replace 'youruser' for your actual user).
[*]The result should be very straight forward: your home should be /home/youruser. Then create that directory on the / partition:
```
mkdir /home/youruser
```
[*]Then copy the basic bash files there:
```
cp /etc/skel/.* /home/youruser
```
[*]Now set the ownnership to your user:
```
chown -R youruser:youruser
```
[*]Now reboot:
```
reboot
```
[*]Now you should get back to the GUI, with an empty user directory.
[/LIST]
After that use gparted to format the new HD. Then get the UUID of your new partition run 'sudo blkid', and the run 'gksudo gedit /etc/fstab' to both change the new UUID of the new partition and comment out the line.

Hope it helps. Let us know how it goes.
Regards.

---

### Post by thiago-canaes on 2013-10-19
Since Ill have to wait till monday to get me another HD, I'll attach what happened with all the commands.

---

### Post by rburkartjo on 2013-10-19
you can try this. after you get to the logon screen open a virtual terminal by ctrl+alt+f1. log into terminal then type rm .Xauthority
after that type in sudo shutdown -r now. see if that worked. i had a similiar problem and it worked for me. worth a try

---

