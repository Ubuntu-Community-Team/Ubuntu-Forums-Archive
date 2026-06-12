---
title: "Incron LFTP can't output result to file"
date: 2017-12-22
forum: New to Ubuntu
---

### Post by swaitch on 2017-12-22
I've been working with incron to monitor IN_CREATE events when a remote user FTPs a file into the monitored folder. I am then using LFTP to put the file(s) to an internal server on a different that can't be accessed externally. I am unable to get the script to output the lftp results to a file for error checking. Any thoughts? I have been working on different supposed solutions for 3 days with no luck.

**Incrontab table:**

/home/custftp/upload IN_CREATE /bin/sh /usr/local/bin/transfer.sh

[B]transfer.sh:

[/B]#!/bin/sh


out="/tmp"


/usr/bin/lftp 192.168.1.140 -u user,pass -p 21 -e 'mput -O /AHDOWNLOAD/RECEIVED /home/cusftp/upload/*.txt;bye' > $out/lftp_output.txt 2>&1


if [ -f $out/lftp_output.txt ]
 then
  grep "bytes transferred" $out/lftp_output.txt > /dev/null
 if [ $? -eq 0 ]
  then
   # COMMAND TO RUN IF TRANSFER IS SUCCESSFUL
   #echo "A customer  file has been recieved and transferred to AHUPLOAD" | mail -s "File Uploaded" -aFrom:Customer-FTP\<custftp@mydomain.com\> 
   exit 0
 else
   # COMMAND TO RUN IF TRANSFER FAILS
   #echo "A customer ACH file has been received but the transfer to AHUPLOAD failed" |mail -s "File Transfer Failed" -aFrom:Customer-FTP\<custftp@mydomain.com\> 
   exit 1
 fi
 else
  # COMMAND TO RUN IF THERE IS A FAILURE TO OUTPUT RESPONSE FROM LFTP
  exit 2


 fi

The script runs but because the output doesn't go to a file for checking the "failed" email is always sent, even though the ftp transfer actually takes place. Is there anyway for me to get the results or some other way to do this?

---

