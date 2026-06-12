---
title: "Using Expect in bash script"
date: 2011-04-21
forum: Programming Talk
---

### Post by rastayoupi on 2011-04-21
Hi all,

I manipulate Truecrypt and i want to automate some actions.
Truecrypt's CLI is too much verbose, this is why i use Expect language.
For those who know Truecrypt (i hope so :p) i need to automate header restoration, example in the shell:

```
leseb@leseb-Studio-1557:~/Truecrypt$ truecrypt --restore-headers tc 
Please select the type of volume header backup you want to use:

1) Restore the volume header from the backup embedded in the volume
2) Restore the volume header from an external backup file

Select: 2


Are you sure you want to restore volume header of /home/leseb/Truecrypt/tc?

WARNING: Restoring a volume header also restores the volume password that was valid when the backup was created. Moreover, if keyfile(s) were/was necessary to mount the volume when the backup was created, the same keyfile(s) will be necessary to mount the volume again after the volume header is restored.

After you click Yes, you will select the header backup file. (y=Yes/n=No) [Yes]: y

Enter filename: bkph2-tc

Enter password for the header stored in backup file: 
Enter keyfile [none]: kf

Please type at least 320 randomly chosen characters and then press Enter:


The volume header has been successfully restored.

IMPORTANT: Please note that an old password may have been restored as well. Moreover, if keyfile(s) were/was necessary to mount the volume when the backup was created, the same keyfile(s) are now necessary to mount the volume again.
```

My bash script : 

```
#!/bin/bash

VAR=$(expect -c "
spawn /usr/bin/truecrypt --volume-type=normal --restore-headers /home/leseb/Truecrypt/tc
expect \"Please select the type of volume header backup you want to use:\n1')' Restore the volume header from the backup embedded in the volume\n2')' Restore the volume header from an external backup file\nSelect:\" 
send  \"2\r\" 
expect "Are \you sure you want to restore volume header of /home/leseb/Truecrypt/.tc?\
\nWARNING: Restoring a volume header also restores the volume password that was valid when the backup was created. Moreover, if keyfile'('s')' were/was necessary to mount the volume when the backup was created, the same keyfile'('s')' will be necessary to mount the volume again after the volume header is restored.\
\nAfter \you click Yes, \you will select the header backup file. '('y=\Yes\/n=No')' [\Yes\]:"
send \"y\r\"
expect \"Enter filename:\"
send \"bkph1-tc\r\" 
")

echo "$VAR"
```

I get this error:
```
root@leseb-Studio-1557:~/Truecrypt# ./restore.sh 
couldn't read file "you": no such file or directory
spawn /usr/bin/truecrypt --volume-type=normal --restore-headers /home/leseb/Truecrypt/tc
Please select the type of volume header backup you want to use:

1) Restore the volume header from the backup embedded in the volume
2) Restore the volume header from an external backup file

Select: 2


Are you sure you want to restore volume header of /home/leseb/Truecrypt/tc?

WARNING: Restoring a volume header also restores the volume password that was valid when the backup was created. Moreover, if keyfile(s) were/was necessary to mount the volume when the backup was created, the same keyfile(s) will be necessary to mount the volume again after the volume header is restored.

After you click Yes, you will select the header backup file. (y=Yes/n=No) [Yes]: 

```

The problem is near "you" (and all the line if i move the \)
I tried an other option :

```
expect \"Are you sure you want to restore volume header of /home/leseb/Truecrypt/.tc?\
\nWARNING: Restoring a volume header also restores the volume password that was valid when the backup was created. Moreover, if keyfile'('s')' were/was necessary to mount the volume when the backup was created, the same keyfile'('s')' will be necessary to mount the volume again after the volume header is restored.\
\nAfter \you click Yes, \you will select the header backup file. '('y=\Yes\/n=No')' [\Yes\]:\"
```

I get this error :
```
root@leseb-Studio-1557:~/Truecrypt# ./restore.sh 
missing close-bracket
    while executing
"expect "Are you sure you want to restore volume header of /home/leseb/Truecrypt/.tc?\nWARNING: Restoring a volume header also restores the volume pass..."
spawn /usr/bin/truecrypt --volume-type=normal --restore-headers /home/leseb/Truecrypt/tc
Please select the type of volume header backup you want to use:

1) Restore the volume header from the backup embedded in the volume
2) Restore the volume header from an external backup file

Select: 

```

I have no idea what i'm doing wrong, so i hope you can help me :-)
Thanks more !

ps: i put ' between ( because Expect dislike ( too !

---

### Post by gzarkadas on 2011-04-27
The problem is because you are not quoting right and thus the line with 'you' appears naked to the shell, which then tries to find and execute it as a command.

You should try something like this (a "here document"):
```

VAR=$(
    { cat <<- EOF
    spawn /usr/bin/truecrypt --volume-type=normal --restore-headers /home/leseb/Truecrypt/tc
    expect -re "Please select the type of volume .*\nSelect:"  send "2\r" 
    expect -re "Are you sure .*WARNING: Rest.*select the header.*[Yes]:"  send "y\r"
    expect "Enter filename:"  send "bkph1-tc\r" 
    EOF
    } | expect -
  )

```to escape from this backshlash-quoting hell.

Read more for here documents in the bash manual: [http://www.gnu.org/software/bash/manual/bash.html](http://www.gnu.org/software/bash/manual/bash.html).

---

