---
title: "No more SUDO, sudoers file issue"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by Benoit65 on 2012-09-22
Hi. To make a long story short... I tried following instructions on a forum. It required that I made changes in sudoers file. In visudo, it said that it was better to save the file as sudoers.d. So logged in as root, I copied this file from "/etc/sudoers" to "/etc/sudoers.d". After that, SUDO commands would not work (too many something in line 28. It tried deleting the new file in "/etc/sudoers.d" but it's read only; I tried changing its status using "u+w" but again, it tells me it's "read only". So I deleted the sudoers file in "/etc" hoping it would correct the problem that seems to arrise from the fact that I have two sudoers files. Now, SUDO commands errors : "no valid sudoers, unable to initialize..." Is this a "catch 22" situation? I'm fairly new to Ubuntu/Linux, as you may have guess...

Thanx.

---

### Post by steeldriver on 2012-09-22
No it's not Catch-22, you can always boot into recovery mode, drop to a root shell, and fix things from there - same as if you lost your password

[http://www.psychocats.net/ubuntu/resetpassword](http://www.psychocats.net/ubuntu/resetpassword)

Try to put everything back to how it was before - DON'T mess with the sudoers file permissions, they MUST be 440

```
$ ls -l /etc/sudoers
-r--r----- 1 root root 574 2011-09-11 15:06 /etc/sudoers
```More info here

[https://help.ubuntu.com/community/Sudoers](https://help.ubuntu.com/community/Sudoers)

---

### Post by TheFu on 2012-09-22
Hopefully someone else will come up with a better answer.  This is all that I can offer....
Boot using a liveCD and enter "rescue mode".  This will be a root prompt. Tell it to mount the correct partition (often /dev/sda1) unless you are using a mixed, dualboot or wubi install.  Be careful - only.

After you mount the "root" partition, set a password for the "root account" by 
```
 # passwd
```This **should** set a root account password for your system, not just inside the installer environment. Normally, Ubuntu doesn't have a root account with a password.  Be certain to set this password so that you can barely type it in - at least 30 characters (others might have a different opinion).  ;)

* Now, reboot and login using your normal userid and password.
* open a terminal
* type ```
id
``` and validate that your userid is part of the **sudo** group.
* su to root - type ```
su -
``` and enter that nearly impossible password.
* completely remove sudo ```
apt-get purge sudo
```* install sudo ```
apt-get install sudo
```There are many other ways to accomplish what you need, but I don't know how for 100% certain, since I'm less than certain what you really did already.
* Edit the sudoers file - ```
visudo
```* Verify that this line is inside ```
%sudo   ALL=(ALL:ALL) ALL
```* Verify that your normal userid is part of the **sudo** unix group still. Type ```
id {your-userid}
```
* go back to your normal account by either opening another terminal or pressing cntl-d.
* Test the **sudo** command.
* Remove the root password - sorry, I have no idea how to accomplish that. Having root with a trivial password is very dangerous.  You can't suspend the account or remove it - both of those would be really, really, really bad.  There is probably some setting that can be easily added to the /etc/passwd or /etc/shadow file to do what you need.  Perhaps putting a "!" as the second field?
--------
Or you could just restore the /etc/sudoers file from the backup that you made automatically last night.  That would be much easier.
--------
Or find someone who will share their default /etc/sudoers file with you and use the root account to install it manually. I think the default one is fewer than 10 lines.  Ownership needs to be root.root and 440 permissions on Ubuntu 12.04.1.  I see a directory called /etc/sudoers.d/ but it isn't used on my system.
--------
In the future, be more careful following random forum howtos without understanding what the commands actually do.  Nearly every command on Linux will have a "man page" which describes what it does, what the options are, and which config files are important.  Often config files will have man pages too - ```
man sudoers 
``` would have explained all.  Before typing any of the commands above, I truly hope that you will look up what each does FIRST.

Good luck.

---

### Post by matt_symes on 2012-09-22
Hi

You can fix this through a liveCD. 

Boot into a liveCD. 

Mount the hardrive partition that has the invalid sudoers file and delete the file from your hard drive.

```
sudo rm /<partition_mount_point>/etc/sudoers.d/<invalid_sudoers_file>
```Then copy the sudoers file from /etc on your live cd to your hard drives /etc.

```
sudo cp /etc/sudoers  /<partition_mount_point>/etc/sudoers
```Make sure the permissions look like this on the partition.

```
matthew-Aspire-7540:/home/matthew % ls -l /etc/sudoers
-r--r----- 1 root root 799 Jul 31 12:47 /etc/sudoers
matthew-Aspire-7540:/home/matthew % 
```Boot into your hard drive install of Ubuntu. Ensure you are still a member of the suders group.
```

matthew-Aspire-7540:/home/matthew % groups  
matthew adm cdrom **sudo** dip plugdev fuse lpadmin sambashare
matthew-Aspire-7540:/home/matthew %
```Hopefully, you should then be good to go.

If that does not work for what ever reason then here is a copy of a sudoers file

```

# This file MUST be edited with the 'visudo' command as root.
#
# Please consider adding local content in /etc/sudoers.d/ instead of
# directly modifying this file.
#
# See the man page for details on how to write a sudoers file.
#
Defaults        env_reset
Defaults        secure_path="/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin"

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL:ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL

# Allow members of group sudo to execute any command
%sudo   ALL=(ALL:ALL) ALL

# See sudoers(5) for more information on "#include" directives:

#includedir /etc/sudoers.d
```

In future use visudo to edit the sudoers file. It will make a temporary copy of the file and perform syntax checking.

```
sudo visudo
```Kind regards

---

### Post by Benoit65 on 2012-09-22
Thanks guys, let me try some of these suggestions and I'll le tyou know how I'm doing!  :)

---

### Post by Benoit65 on 2012-09-22
OK! Problem solved! Following steeldriver's method, I started Ubuntu in **recovery** mode (holding the shift key) and typed in* mount -o rw,remount /* . This allowed me to move the *sudoers* file back where it belongs, in */etc* !

Thanks again!

---

### Post by steeldriver on 2012-09-22
Glad it turned out to be as simple as that! Both TheFu's and matt_symes' excellent advice was really much more comprehensive than mine and would have dug you out of a deeper hole (e.g. if it turned out you had substantially modified the file as well as / instead of just moving it)

---

### Post by Scott Harrison on 2012-09-22
So what were you trying to do that required you to edit the sudoers file?

---

### Post by matt_symes on 2012-09-23
Hi

@Scott Harrison

There are a whole load of reasons one may want to edit the sudoers file, but they are usually the preserve of the sysadmin and not a home user.

It can be useful for the home user to edit the sudoers file though and i have done so on my laptop.

I have a number of configured screen sessions that start up when i start my laptop and boot into my Ubuntu+1 development install (I have a number of installs). At the moment that is Quantal (the one above Precise).

One of the screen sessions is a diagnostic screen session.```


matthew-Aspire-7540:/home/matthew/storage/.shared_config % tail -n30 .screenrc.diagnostics    
scrollback 1000

# Always open htop
screen -t htop 0 htop

# see what is using the net.
screen -t vmstat 1 watch vmstat -SM -a

# see what is using disk access
screen -t iotop 2 sudo iotop

# dstat.
screen -t dstat 3 dstat

# The laptop thermal zones
screen -t temps 4 watch sensors

# Processr information
screen -t mpstat 5 watch mpstat -A

screen -t acpi 6 watch acpi

# An empty shell
screen -t zsh 7 /bin/zsh

# An empty shell
screen -t zsh 8 /bin/zsh

# Switch to window 0
select 0
matthew-Aspire-7540:/home/matthew/storage/.shared_config %
```

This runs a number if utilities including iotop. iotop requires root privilages and as i din't want to enter a password to kick it off, i have added iotop as an exception in my sudoers file.

```

matthew-Aspire-7540:/home/matthew/storage/.shared_config % sudo tail -n1 /etc/sudoers
matthew ALL=NOPASSWD: /usr/sbin/iotop
matthew-Aspire-7540:/home/matthew/storage/.shared_config % ls
```

This allows me to run the screen diagnostic session with iotop without entering a password.

And thanks, you have reminded me that i need to update that configuration file :D

Kind regards

---

