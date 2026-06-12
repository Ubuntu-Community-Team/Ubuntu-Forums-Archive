---
title: "PHP shell_exec not executing serial commands."
date: 2012-12-02
forum: Programming Talk
---

### Post by dchurch24 on 2012-12-02
Hi all,

I have an ongoing development of a home automation system that I've been building/amending/adding to for years.

Now I want to be able to control all the devices in my house via an internal web page.

I've set up a RPi box and installed lamp - I now have a prototype web page ([www.cidb.co.uk/homecontrol](www.cidb.co.uk/homecontrol) if anyone is interested), when I click any of the buttons it executes a PHP page via ajax and returns the results.

I have a set of scripts that are as such:

switch_1_on.sh
switch_1_off.sh

etc...

if I'm at the command prompt and I type ./switch_1_on.sh it executes the following command successfully and switches a relay on, that in turn switches a remote 433mhz device.

```

echo -e '\xff\x05\x01' > /dev/ttyUSB0

```

At the terminal, this works fine and executes as expected.

The php page that calls this script is this:

```

<?php
$inp = shell_exec('./switch_1_on.sh'); // > /dev/null 2> /dev/null &');
echo $inp;
?>


```

The code is executed (I know this as I added 'echo "hello";' into it and that is returned correctly....but the shell scripts never switches the relay.

I guessed that it was a permissions problem, so temporarily changed the file to 777, that didn't work, so I made the owner www-user, but that didn't work either.

I'm now at a complete loss.

Anyone got any ideas why the script can run normally at the terminal, and run all the parts of the script through php apart from the serial parts?

---

### Post by SeijiSensei on 2012-12-02
Try specifying a complete path to the script.  

```
shell_exec('/path/to/switch_1_on.sh')
```

Also, when you spoke about setting permissions, are you sure the www-data user can write to /dev/ttyUSB0?  Try this:

```

sudo su -
[enter your password]
su www-data
echo -e '\xff\x05\x01' > /dev/ttyUSB0
exit
exit

```

---

### Post by dchurch24 on 2012-12-02
I think you've hit the nail on the head. I did what you said with the www-data user and this is the result:

```

sh: 1: cannot create /dev/ttyUSB0: Permission denied

```

How can I give www-data rights to write to /dev/ttyUSB0?

---

### Post by SeijiSensei on 2012-12-02
> **dchurch24 said:**
> How can I give www-data rights to write to /dev/ttyUSB0?

I don't have that particular tty device on my machine, but an "ls -l /dev/tty*" shows that most of them are owned by root with write privileges granted to group "tty".  If that is true for /dev/ttyUSB0 as well, the best solution is to add www-data to the tty group by editing (as root with sudo) /etc/group and adding "www-data" after the final colon in the line [noparse]"tty:x:5:"[/noparse].

A less secure solution is simply to use "sudo chmod a+w /dev/ttyUSB0" to make the device world-writable.  I don't know if that will survive a reboot, though, unless you put the command into /etc/rc.local which is the last script run when the system boots up.

---

### Post by dchurch24 on 2012-12-02
Hi, thanks for your time, it's really appreciated.

I'm getting closer....

I did as you said, and now I can run the command and NOT get the permission denied error....it simply does nothing.

I copied and pasted the command after I exited back to my user (rather than the www-user) to check that the syntax was correct, and it works fine again.

Stumped!

---

### Post by SeijiSensei on 2012-12-02
The only other thing I might suggest is granting the tty group read permissions on /dev/ttyUSB0 as well.  Try "sudo chmod g+r /dev/ttyUSB0" and see if that helps.  Otherwise, I'm afraid I'm out of suggestions.

---

### Post by dchurch24 on 2012-12-03
Hi, thanks for you help again.

I've tried g+r as well, but no joy.

I checked the php.ini file for anything obvious in there, I removed 'pcntl_exec' from the disabled line, and restarted apache, but still no go.

I'm trying to think of another way of doing it as it seems that this is not possible through php.

I'll post up if I think of a way.

Thanks again.

---

### Post by dchurch24 on 2012-12-03
Ok, not very secure I don't think, but I got it.

I added www-data to the sudoers file, then in my shell script executed this:

```

sudo -u dave echo -e '\xff\x03\x00' > /dev/ttyUSB0

```

...so that the tty execution is now handled by user 'dave'.

It's only on a local network, so I'm happy to go this way...for the moment.

EDIT: After a reboot, this no longer worked. I changed the permissions on /dev/ttyUSB0 to....arggghhh...777...and then it works. So not quite cracked yet.

---

