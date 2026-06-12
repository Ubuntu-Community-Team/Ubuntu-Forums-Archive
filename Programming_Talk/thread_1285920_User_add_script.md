---
title: "User add script"
date: 2009-10-08
forum: Programming Talk
---

### Post by PedroMagueija on 2009-10-08
Hi,

I made a script that it was supposed to add users from a TAB delimited text file.
When I ran it, the users where added (or it seems) but they don't show on Users and Groups. Also after reboot, it says the gdm user does not exist and my user (at the time sudoer) no longer is a sudoers user.

I can login in the shell, all files are there.
Here is the script that ran:

```

#!/bin/bash
if [$1 == ""]; then exit 0; fi
while read LINE
do
IFS=""
username=`echo $LINE | cut -f 1`
fname=`echo $LINE | cut -f 2`
lname=`echo $LINE | cut -f 3`
description=`echo $LINE | cut -f 4`
homedir=`echo $LINE | cut -f 5`
loginscript=`echo $LINE | cut -f 6`
profile=`echo $LINE | cut -f 7`
pwdexpire=`echo $LINE | cut -f 8`
pwdnotexpire=`echo $LINE | cut -f 9`
echo "Username: $username Name: $fname $lname Description: $description"
sudo useradd -c "$fname $lname" -d "/home/$username" -N -m  $username
done < $1

```

Can you guys help me? I had to recover my system, so I need to know what is wrong in the script, since the single ```
useradd -c "aaa" -d "/home/aaa" -N -m aaa
``` runs fine.

Thanks again.

---

### Post by geirha on 2009-10-08
The first line (after the hash-bang) is wrong at least. [ is a command, it's not part of the if-syntax, so its arguments must be delimited with spaces like with any other command.

As for parsing the file, I don't see the point in using cut, just use the built in read command.

```

#!/bin/bash
(($#)) || exit   # exit if number of arguments is 0
while IFS=$'\t' read -r username fname lname desc homedir etc; do
  useradd -c "$fname $lname" ...
done < "$1"

```

Not sure why your script would break already added users though. Take a backup of /etc/passwd, then compare it with /etc/passwd after that script has run and see what it actually did ...

---

### Post by PedroMagueija on 2009-10-08
Talk about optimization.... eheh :). Great job.

I'll do has you suggested and compare the passwd and then report back here. I'll also use your optimizations to the script if you don't mind.

Thank you.

---

### Post by PedroMagueija on 2009-10-19
Hi,

Sorry about the delay. Installed a new virtual machine with ubuntu on it. Ran original script and it ran without problems.

Any ideas?

Since it was ran before ubuntu updates, I'll update the system and run it again, to see what happens.

Thanks.

---

