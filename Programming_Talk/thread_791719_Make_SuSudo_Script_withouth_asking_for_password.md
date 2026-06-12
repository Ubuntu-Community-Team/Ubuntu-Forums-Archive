---
title: "Make Su/Sudo Script withouth asking for password"
date: 2008-05-12
forum: Programming Talk
---

### Post by sofamensch on 2008-05-12
I recently wrote a script that should mount all my TrueCrypt Volumes. It works just fine but is asking me for the sudo password all the time of course.

Now, what i dont want to do is "sudo visudo", i kinda only want to include my password into the script, more or less like "sudo <command> <password>" like way, only for this script.

Any way?
Thanks in Advance

---

### Post by dwhitney67 on 2008-05-12
If you were to look at the man-page for 'sudo' ($ man sudo), you will find that there is nothing that meets your requirements.

Furthermore, most *nix users will tell you that including the password of a any system account in a script is not recommended under any circumstance.

Why spend countless hours looking for a solution, which I doubt exists, when it would be just easier to enter the password when prompted by sudo?

Err, nevermind.... see the posts below.  It's your system, you do what you want.

---

### Post by LaRoza on 2008-05-12
> **sofamensch said:**
> I recently wrote a script that should mount all my TrueCrypt Volumes. It works just fine but is asking me for the sudo password all the time of course.

Now, what i dont want to do is "sudo visudo", i kinda only want to include my password into the script, more or less like "sudo <command> <password>" like way, only for this script.

Any way?
Thanks in Advance

There is a way:

```

echo $PASSWORD | sudo -S $COMMAND

```

Not really the best thing to do, but it works.

---

### Post by johnl on 2008-05-12
You can also specify in the /etc/sudoers file that your command can be run by a specific user or group without a password.  (The line for the nopasswd command should go after any other lines that may affect your user)

```
# user johnl can run the specified command as sudo with no password
johnl ALL = (ALL) NOPASSWD: /home/johnl/Applications/bin/test
```

This way, you do not need to use sudo in your script, and you can run the script using sudo without entering a password.

Hope this helps.

---

### Post by drs305 on 2008-05-14
Reference the previous post (#4), I have tried all sorts of variations of this and still can't get a sudo-less script to work. I suspect it has something to do with 1) the admin group I am in or  2) the script I am trying to run.

1) I (username) am the sole user of the computer (computer), so I guess I'm in the admin group. I have read posts that members of the admin group are uneffected by a NOPASSWD entry. This may require additional lines in sudoers but I don't know what they are or where in the sequence to put them.

2) I want to run /home/username/.scripts/test.sh  It contains a sudo command, so when I run it from terminal it requires me to enter the password. I am trying to add a line to sudoers to allow the script to run without entering the sudo password. The .scripts directory is in my PATH.

This is the way I thought the line would be written:
```
username ALL = (ALL) NOPASSWD: /home/username/.scripts/test.sh
```

```
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
# Defaults

# Defaults

Defaults !lecture,tty_tickets,!fqdn

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root    ALL=(ALL) ALL

# Members of the admin group may gain root privileges
 %admin ALL=(ALL) ALL

Defaults:username timestamp_timeout=2
username ALL = (ALL) NOPASSWD: /home/username/.scripts/test.sh

```

Thanks.

---

### Post by sofamensch on 2008-05-29
> **LaRoza said:**
> There is a way:

```

echo $PASSWORD | sudo -S $COMMAND

```

Not really the best thing to do, but it works.

This is the one that works great for me. Thanks!

---

### Post by geirha on 2008-05-29
> **drs305 said:**
> 
```

username ALL = (ALL) NOPASSWD: /home/username/.scripts/test.sh

```


This means that you are allowed to run ```
sudo /home/username/.scripts/test.sh
``` without typing a password. It does not mean that all commands in the script can be run with passwordless sudo.

In sudoers, you'll need to put all the commands you need to run as sudo inside the script.

---

### Post by Joeb454 on 2008-05-29
You could just run the script as sudo anyway, and then enter your password the once, I believe that would allow you to use the script perfectly fine :)

---

### Post by rightasrain on 2011-04-09
> **johnl said:**
> You can also specify in the /etc/sudoers file that your command can be run by a specific user or group without a password.  (The line for the nopasswd command should go after any other lines that may affect your user)

```
# user johnl can run the specified command as sudo with no password
johnl ALL = (ALL) NOPASSWD: /home/johnl/Applications/bin/test
```

This way, you do not need to use sudo in your script, and you can run the script using sudo without entering a password.

Hope this helps.

I just want to run this by double clicking it. It asks for my password. I have tried

sally ALL=(ALL) NOPASSWD: /home/sally/restartmediatomb.sh in sudoers but it still asks me for my password.

Here is my script
#!/bin/bash

sudo /etc/init.d/mediatomb restart

I have tried 
#!/bin/bash
echo $PASSWORD | sudo -S $COMMAND
sudo /etc/init.d/mediatomb restart

This is a personal computer I have no security concerns with this machine.
Does anyone know why none of these methods are working?

---

### Post by hakermania on 2011-04-09
try putting the whole command /etc/init.d/mediatomb restart in a new script and then, from the first script run echo "passwd" | sudo -S /path/to/the/second/script
This may work

---

### Post by rightasrain on 2011-04-10
> **hakermania said:**
> try putting the whole command /etc/init.d/mediatomb restart in a new script and then, from the first script run echo "passwd" | sudo -S /path/to/the/second/script
This may work

This did work. Thanks a ton.

---

### Post by slavik on 2011-04-10
sudo -S technically allows anyone booting your system with a livecd can get your password ... :D

---

### Post by hakermania on 2011-04-10
> **slavik said:**
> sudo -S technically allows anyone booting your system with a livecd can get your password ... :D

If somebody has access to the system via live cd, he can take anything, like he had the password, so, what's the problem?

I mean, by booting via livecd and becoming root, you have access to all the system's files anyway :P

---

### Post by ian dobson on 2011-04-10
Hi,

just put  /etc/init.d/mediatomb in your sudoers list, that should do it.

regards
Ian Dobson

---

### Post by Crusty Old Fart on 2011-04-10
There's a much safer way to do it in [post=10317361]This post[/post].

---

### Post by slavik on 2011-04-10
> **hakermania said:**
> If somebody has access to the system via live cd, he can take anything, like he had the password, so, what's the problem?

I mean, by booting via livecd and becoming root, you have access to all the system's files anyway :P
A truecrypt volume that requires you to enter a password any time you want to mount (not auto-mounted) and a device present (usb keyfob) would be impossible to break in any reasonable amount of time, this is especially important when your device _falls into the wrong hands_.

And if you are discounting the possibility of your device/system being stolen, what's the point of encryption with a secure password in the first place?

---

