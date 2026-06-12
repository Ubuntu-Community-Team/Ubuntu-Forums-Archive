---
title: "Shell Scripting Problem"
date: 2007-12-19
forum: Programming Talk
---

### Post by brentos2004 on 2007-12-19
I Have a basic script that unzips a load of zip files. The zip files are password protected so the script contains a range of passwords that are used to unzip the folders. 

What I want to be able to do is to run a check on each folder once unzipped to confirm that two particular files are contained within the unzipped folders ie file1.mdb and file2.mdb. I need it to perform this check after it has unzipped each individual folder. I would like it to just carry on with the process of unzipping if the files are there and if there not there then write to a file which will then be emailed after the process is complete. 

Can these checks be done and is it possible to get the script to automatically email the log file after the script has completed? 

Any help would be appreciated. 

Here is the basic script at the moment.

#!/bin/bash
for Z_FILE in '/location/*.zip'; do
for PASSWD in [ password1, password2, password3 ]; do
unzip -P $PASSWD $Z_FILE;
if [ $? = 0 ]; then # successful unzip
break
fi
done
done

Thanks

---

### Post by Cappy on 2007-12-19
> **brentos2004 said:**
> I Have a basic script that unzips a load of zip files. The zip files are password protected so the script contains a range of passwords that are used to unzip the folders. 

What I want to be able to do is to run a check on each folder once unzipped to confirm that two particular files are contained within the unzipped folders ie file1.mdb and file2.mdb. I need it to perform this check after it has unzipped each individual folder. I would like it to just carry on with the process of unzipping if the files are there and if there not there then write to a file which will then be emailed after the process is complete. 

Can these checks be done and is it possible to get the script to automatically email the log file after the script has completed? 

Any help would be appreciated. 

Here is the basic script at the moment.

#!/bin/bash
for Z_FILE in '/location/*.zip'; do
for PASSWD in [ password1, password2, password3 ]; do
unzip -P $PASSWD $Z_FILE;
if [ $? = 0 ]; then # successful unzip
break
fi
done
done

Thanks

Something like
```

rm unzip_errors.txt
for Z_FILE in `ls /location/*.zip`; do
    for PASSWD in password password2 password3; do
        unzip -P "$PASSWD" "$Z_FILE"
        if [ $? -eq 0 ]; then # successful unzip
            break
        fi
    done
    if [ ! -f "/location/$Z_FILE/file1.mdb] && [ ! -f "/location/$Z_FILE/file2.mdb]; then
        echo "$Z_FILE did not unzip" >> unzip_errors.txt
    fi
done

if [ -f unzip_errors.txt ]; then
   cat unzip_errors.txt | sendmail 'me@anothercomputer.com'
fi

```

Note that if password password2 or password3 contain spaces the for loop won't work

---

### Post by psusi on 2007-12-19
I suggest that you just have the script print its results to stdout normally, and if you want to run it in the background and have the results emailed to you, submit it via the batch command.

---

