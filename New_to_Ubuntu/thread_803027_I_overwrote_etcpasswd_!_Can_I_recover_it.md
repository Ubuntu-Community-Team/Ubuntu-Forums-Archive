---
title: "I overwrote /etc/passwd ! Can I recover it?"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by JameoPotato on 2008-05-21
When the 8.04 server starts up it seems to be going well until it I see numerous processes beginning to fail all because of incorrect logins.
ex, "invalid user 'www-data'" shows up for a lot of things including saying users are "Dovecoat" and "root"

Along with this i cannot login to my regular account anymore.

UPDATE:
So after doing a bit of googling i discovered that i overwrote a crucial file that store login information... /etc/passwd .
Just in my defense the reasoning behind me choosing that file was because htpasswd was refusing to write to /etc/vsftpd/passwd... so i decided "Hey lets just move it up a directory" well go figure that one directory up was a crucial file.

So new question is:
How do I get myself out of this pickle. It there anyway to recover this file? Would it have been unique to my user? Could I copy and write it from the recovery shell??? Is there a such this as system restore in ubuntu??

---

### Post by Bakon Jarser on 2008-05-21
> **JameoPotato said:**
> When the 8.04 server starts up it seems to be going well until it I see numerous processes beginning to fail all because of incorrect logins.
ex, "invalid user 'www-data'" shows up for a lot of things including saying users are "Dovecoat" and "root"

Along with this i cannot login to my regular account anymore.

UPDATE:
So after doing a bit of googling i discovered that i overwrote a crucial file that store login information... /etc/passwd .
Just in my defense the reasoning behind me choosing that file was because htpasswd was refusing to write to /etc/vsftpd/passwd... so i decided "Hey lets just move it up a directory" well go figure that one directory up was a crucial file.

So new question is:
How do I get myself out of this pickle. It there anyway to recover this file? Would it have been unique to my user? Could I copy and write it from the recovery shell??? Is there a such this as system restore in ubuntu??

I'm no expert so you may want to wait for better advice but I just opened psswd and then opened passwd- and except for the very last line they are identical.  Maybe you could overwrite psswd with psswd-
I don't know if this will work or even maybe make things worse so maybe you shouldn't.

---

### Post by JameoPotato on 2008-05-22
okay so i went into recover mode.
ran, "cp /etc/passwd- /etc/passwd"
rebooted and all processes started without complaining about a bad username.
But I still couldn't logon to my user account.

I haven't tested this yet but I believe that all I have to do is run recovery again, login as root, run "passwd jameo" (jameo being my username) and then i should be all set.

i'll update when I know

---

### Post by Bakon Jarser on 2008-05-22
Yeah, the last line in the file specifically referenced my user account.  I probably should have mentioned that.  Good Luck.

---

### Post by sdennie on 2008-05-22
That may be all that is needed or, from recovery mode, you may have to do something like:

```

adduser your_username
addgroup your_username admin

```

---

### Post by JameoPotato on 2008-05-22
Fix it! 

Here is a guide for anyone who runs into the same problem:
-Start GRUB on boot (press ESC while booting)
-Press e over (recovery mode)
-Press e over the line beginning with kernel
-Press Space bar and enter "init=/bin/bash"
-Press enter
-Press b
-At command prompt type: "cp /etc/passwd- /etc/passwd"
-reboot to GRUB again
-Press e over (recovery mode)
-Press e over the line beginning with kernel
-Press Space bar and enter "init=/bin/bash"
-Press enter
-Press b
-At command prompt type "mount -o remount,rw /"
-Type "passwd *YOURUSERNAMEHERE*" (IF you don't know your user name type "ls /home" (that is a Lower case L and lower case S) for a list of users)
-Enter new password at prompt
-reboot to normal boot.

Hope that helps others like it did me!

---

