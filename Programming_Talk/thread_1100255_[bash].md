---
title: "[bash]"
date: 2009-03-19
forum: Programming Talk
---

### Post by detorresrc on 2009-03-19
Is there a way to detect when i copy a file from client to server. Here's the sample.

[PHP]
# NO NEED TO INPUT SERVER PASSWORD
#!/bin/sh

if [ scp <myfilename> user@xxx.xxx.xxx:/home/ ]
    echo "Failed";
else
    echo "Success";
fi
[/PHP]

---

### Post by movieman on 2009-03-19
There's a way to check the return code of the program you ran, I think it's something like '$?' So if scp returns an error when it can't copy, you should be able to check it that way.

Yeah, if I run:

#!/bin/bash
scp foo someone@somewhere:
echo $?

Then it prints out an error because it can't connect, followed by a 1 for the $? variable.

---

### Post by detorresrc on 2009-03-19
Tnx tnx tnx...

---

### Post by nelskurian on 2009-03-19
Just FYI...May be some others in need of..

Code:

```
#!/bin/bash

ftp_site=ftp://yoursite.com
username=roger
passwd=abc123
backupdir=$HOME
filename="backup-$(date '+%F-%H%M').tar.gz"

echo "Creating a backup file $filename of $backupdir."

# Make a tar gzipped backup file
tar -cvzf  "$filename" "$backupdir"

ftp -in <<EOF
open $ftp_site
user $username $passwd
bin
put $filename 
close 
bye
EOF

```
*Thanks moma*

---

### Post by geirha on 2009-03-19
Your first attempt was very close. Just remove those []'s, add a then, and switch the messages.
```

if scp <myfilename> user@xxx.xxx.xxx:/home/
then
    echo "Success";
else
    echo "Failed";
fi

```

---

### Post by detorresrc on 2009-03-19
Tnx to all of you guys.!!!!!

---

