---
title: "howto run a script and to copy the output into a file?"
date: 2007-09-15
forum: Programming Talk
---

### Post by adhg on 2007-09-15
Hi all,
I'm writing a bash script that creates a backup of my db and send it to a remote site (this will be done on a daily basis and the remote site will have a folder name of the day of backup, eg., 2007-09-09)

When I run the script, I placed some 'echo' to tell what/where the script is doing.

Since this will be done on automatically and on a daily basis, I would like to create a text file that includes all the *echos* and place it under the folder I created for that specific date (just like a log file that tells what happens and if something went wrong)

on the terminal I can do this:

adhg@ubuntu$ ./backup>out.txt

and all echos will go into out.txt. Problem is, of course, that I can't do this in the script:

cp out.txt $remoteFolder 

this is because the out.txt is not completed yet :confused:

any idea how to circumvent this problem? 
thanks
adhg

---

### Post by Biswajit Bhuyan on 2007-09-15
Hi,

You can directly route the output to the remote destination.
**adhg@ubuntu$ ./backup>$remotefolder/out.txt**

And since you want to aggregate the logs datewise;
You might as well do
**adhg@ubuntu$ ./backup>$remotefolder/`date +%Y-%m-%d-%T`/out.txt**

HTH.

---

### Post by dwhitney67 on 2007-09-16
> **adhg said:**
> Hi all,
I'm writing a bash script that creates a backup of my db and send it to a remote site (this will be done on a daily basis and the remote site will have a folder name of the day of backup, eg., 2007-09-09)

When I run the script, I placed some 'echo' to tell what/where the script is doing.

Since this will be done on automatically and on a daily basis, I would like to create a text file that includes all the *echos* and place it under the folder I created for that specific date (just like a log file that tells what happens and if something went wrong)

on the terminal I can do this:

adhg@ubuntu$ ./backup>out.txt

and all echos will go into out.txt. Problem is, of course, that I can't do this in the script:

cp out.txt $remoteFolder 

this is because the out.txt is not completed yet :confused:

any idea how to circumvent this problem? 
thanks
adhg

The easiest solutions is to write a wrapper script that does exactly what you want:

For instance:
```

#!/bin/bash

bash ./backup > ./out.txt

cp ./out.txt $remoteFolder
```

---

### Post by zero-9376 on 2007-09-16
or change all the echos in your script to echo to the file and then cp at the end of the script/loop 

log=`date +%Y-%m-%d-%T`.txt

echo "put this in the log" >> $log

---

