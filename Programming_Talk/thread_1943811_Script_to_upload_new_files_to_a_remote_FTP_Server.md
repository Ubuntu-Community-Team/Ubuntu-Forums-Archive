---
title: "Script to upload new files to a remote FTP Server"
date: 2012-03-20
forum: Programming Talk
---

### Post by mitanc on 2012-03-20
Hey All,

I need help with a script to find new files and put copy them recursively in a directory and after its done, to log into an ftp and upload them.  

For the new files aspect, I am using a program called [cpafter.sh]("http://movingtofreedom.org/2007/04/15/bash-shell-script-copy-only-files-modified-after-specified-date/").  This program allows one to search a directory and all its sub-directories and copy directories along with any files modified after a certain date.  

In my script I am trying to create a master folder where the files will copy too.  The folder will be called ZILVER_<YYYYMMDD> where that would be the date filled in.

After the folder name is made, I would copy all files newer than one day before the current date.  

This is what I got so far:
```
#!/bin/bash
# Program to copy Zilver Zoom Files
# Author: Mitan Chandihok

# Set initial Variable
FILE='/ldaphome/WorkFiles/Customers/ZILVERZOOM/PRDOUCTIONPHOTOS/'

td=`date +%Y%m%d`
oldd=$(date -d "-1 days" +%Y%m%d)

# Copy everything modified after yesterday to this folder

echo `echo sh /usr/local/bin/cpafter.sh -vf -a $oldd -s $FILE -t ./test_ZILVER/ZilverPhoto_$td/`
echo `sh /usr/local/bin/cpafter.sh -vf -a $oldd -s $FILE -t ./test_ZILVER/ZilverPhoto_$td/`

```

The Output of running this looks like:
```
sysadmin@dc01-lg:~/TEST$ sh zilver.sh
sh /usr/local/bin/cpafter.sh -vf -a 20120319 -s /ldaphome/WorkFiles/Customers/ZILVERZOOM/PRDOUCTIONPHOTOS/ -t ./test_ZILVER/ZilverPhoto_20120320/
/usr/local/bin/cpafter.sh: 24: usage+=to target dir, creating any subdirectories as needed.\n\n: not found
/usr/local/bin/cpafter.sh: 25: usage+=\tusage: cpafter.sh [-vf] -a after_date_YYYYMMDD -s source_dir -t target_dir\n: not found
/usr/local/bin/cpafter.sh: 26: usage+=\t\t-v verbose\n: not found
/usr/local/bin/cpafter.sh: 27: usage+=\t\t-f force target dir creation or copying to non-empty target dir\n: not found
/usr/local/bin/cpafter.sh: 46: [[: not found
/usr/local/bin/cpafter.sh: 46: -z: not found
/usr/local/bin/cpafter.sh: 46: -z: not found
/usr/local/bin/cpafter.sh: 46: 0: not found
/usr/local/bin/cpafter.sh: 51: [[: not found
/usr/local/bin/cpafter.sh: 63: [[: not found
/usr/local/bin/cpafter.sh: 70: [[: not found
/usr/local/bin/cpafter.sh: 74: [[: not found
/usr/local/bin/cpafter.sh: 84: cannot open 20120319: No such file
/usr/local/bin/cpafter.sh: 84: 20120320: not found
cd: 98: can't cd to ./test_ZILVER/ZilverPhoto_20120320/
cd: 102: can't cd to /ldaphome/WorkFiles/Customers/ZILVERZOOM/PRDOUCTIONPHOTOS/
/usr/local/bin/cpafter.sh: 106: [[: not found
cp: `/home/sysadmin/TEST/./zilver.sh' and `/home/sysadmin/TEST/./zilver.sh' are the same file
./zilver.sh
sysadmin@dc01-lg:~/TEST$

```

What I don't get is if I copy and paste the command, it runs fine from the terminal.  

I need help with this, and then any advice on the best way to login to an ftp and upload the directory.  Since its by date and will run once every night, I don't see any conflicts.  

Thanks for the help!

3/20/2012
Hey, I realized I spelled the directory wrong when I set the variable, so I got this working.  Can anyone help me out with figuring out how to upload this new folder to an FTP?

Thanks!

---

### Post by CynicRus on 2012-03-21
```
#!/bin/bash
if [ $# -eq 0 ]
then
  echo 'UPL - script to upload files on freedomscripts server. use only with arguments!'
  exit 0
fi

for file in $@
do
  date=$(date +%d.%m.%y)
  newUploadDir = /local_ftp_dir/server.ru/uploads/$date

  if [ -d newUploadDir ]; then
    echo "dir $date is exists"
  else
    mkdir newUploadDir
  fi
  
  cp $file newUploadDir
  echo "done! http://www.server.ru/uploads/$date/$file"
  echo "$(date +%R) http://www.server.ru/uploads/$date/$file" >> /home/user/bin/uploads.txt
  rm $file
done
``` This may will help you, if i understand the problem.
Use
```

upl.sh myfile1 myfile2 myfile3

```

---

### Post by mitanc on 2012-03-21
Hey, thanks for taking the time to get this out to me.  I actually was determined to get this done last night, so I figured it out.  I make heavy use of the cpafter.sh script and the wput program.  It worked out pretty well and wasn't too hard.  Considering I am a bash newb, only play with this kind of stuff once or twice a year am proud of it :KS


I'll post the final code in case anyone wants to use this:

```
#!/bin/bash
# Program to copy New Files to FTP
# Author: Mitan Chandihok

# Set initial Variables

HOST=ftp.xxxxxx.com
USER=username
PASS=password


SOURCE=/ldaphome/WorkFiles/Customers/ZILVERZOOM/PRODUCTIONPHOTOS/  #Source Directory

td=`date +%Y%m%d`  # Today's date in YYYYMMDD format
oldd=$(date -d "-1 days" +%Y%m%d)  # Yesterday's date in YYYYMMDD format

TARGET="ZilverPhoto_${td}/" # Target Directory Name

# Copy everything modified after yesterday to this folder
RUN="/usr/local/bin/cpafter.sh -vf -a $oldd -s $SOURCE -t /tmp/$TARGET"
$RUN

# Run wput and upload Directory to ZilverZoom FTP
cd /tmp
wput $TARGET ftp://${USER}:${PASS}@${HOST}/

# Delete the temp directory
rm -rf $TARGET

```

---

