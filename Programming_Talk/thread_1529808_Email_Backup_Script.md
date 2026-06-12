---
title: "Email Backup Script"
date: 2010-07-12
forum: Programming Talk
---

### Post by WRDN on 2010-07-12
I've been working on a little script to backup my data, and send it to a desired email address, and thought I would share it with the community.

If the file size is more than the limit (MAX_GMAIL_SIZE_MB) the file will be split into chunks, with each file being less than or equal to this size. These will then be emailed separately, with the email containing info about the file, the date and tell you which file in the series it is (i.e. file X of a total Y).

If the file size is less than the limit, it will be sent without splitting.

```

#!/bin/bash

# Get the current EMAIL environmental variable, that we will restore later
CURRENT_EMAIL=`echo $EMAIL`

# Set the "from" address of the emails we will send, comment this line if 
# you're happy with the current EMAIL environmental variable
# In this case, karoo is my SMTP relay, you need to set the SMTP relay 
# address etc in the ~/.muttrc file
export EMAIL="backups@username.karoo.co.uk"

# Max upload size is 25Mb for GMAIL, set to max relay upload size if one used
MAX_GMAIL_SIZE_MB=8
MAX_GMAIL_SIZE_KB=$((MAX_GMAIL_SIZE_MB*1024))
MAX_GMAIL_SIZE_B=$((MAX_GMAIL_SIZE_KB*1024))

# First argument is email address to send to
if [ -n "$1" ]
then
EMAIL_ADDR=$1
else
echo "email address not specified"
exit
fi

# The script argument is the file you want to send to the email
# address in EMAIL_ADDR (see below). Useful if you want to pipe the
# output of one program (e.g. tar) to this e.g. so you can compress the files
# then send them
if [ -n "$2" ]
then
FILE=$2
else
echo "file not specified"
exit
fi

# Date time formatted so it can be used in a file/folder name
DT=`date +%d%m%Y_%S%M%H`
DT_HUMAN=`date`

# Get the size of the file (first column only)
ZSIZE=`du -b $FILE | cut -f -1`
ZSIZE_HUMAN=`du -h $FILE | cut -f -1`

# If the file size is more than GMAILs max size, split it!
if [ $ZSIZE -gt $MAX_GMAIL_SIZE_B ]
then
echo "File size over max attachment size ($MAX_GMAIL_SIZE_MB), splitting into $MAX_GMAIL_SIZE_MB"MB" chunks"
# Create the date/time directory (most likely unique!)

# 0 if doesnt exist, more than 0 if does
EX=0
if [ -a split_files ]
then
EX=1
fi

mkdir split_files/$DT -p
# Split in bytes and put in the date time directory we just created
split --line-bytes=$MAX_GMAIL_SIZE_B -d $FILE split_files/$DT/$FILE'_'
# Get the total number of files we just created
TOTAL_COUNT=`ls -a split_files/$DT | grep $FILE'_' | wc -l`
i=1

echo "Emailing the split files, to: $EMAIL_ADDR"
# Here is where we email the files!!!!
for f in `find split_files/$DT -name "$FILE"_"*"`
do
echo "Emailing $f,file $i of $TOTAL_COUNT"
FSIZE=`du -b $f | cut -f -1`
echo -e "$DT   -   $DT_HUMAN\n$f   -   $FSIZE byte(s) of a total $ZSIZE byte(s)\n$i of $TOTAL_COUNT" | mutt -s "Backup $DT_HUMAN , $f - $FSIZE byte(s) of $ZSIZE byte(s), $i of $TOTAL_COUNT" -a $f $EMAIL_ADDR
i=$(( $i + 1 ))
done

# If the directory didnt exist when the script started, delete it, otherwise just remove the DT
# directory and leave the rest. If you are using an SMTP relay that sends mail synchronously, 
#and want the files split created to be deleted, then uncomment this code.
#if [ $EX -eq 0 ]
#then
#rm -rf split_files
#else
#rm -rf split_files/$DT
#fi

export EMAIL=$CURRENT_EMAIL
exit
fi

# Else, if we dont need to split the file, just send it (its under MAX_GMAIL_SIZE_MB)
echo "File under $MAX_GMAIL_SIZE_MB""Mb, not splitting, sending to $EMAIL_ADDR"
echo -e "$DT   -   $DT_HUMAN\n$FILE   -   $ZSIZE byte(s)" | mutt -a $FILE -s "Backup $DT_HUMAN , $FILE (file 1 of 1) - $ZSIZE byte(s)" $EMAIL_ADDR

# Restore the old EMAIL
export EMAIL=$CURRENT_EMAIL

```

You can run it by typing:

```
./my_script.sh recipient@gmail.com my_file_to_send
```

Feel free to use this if you wish. Note, you don't need to use an SMTP relay, you can set "EMAIL" to anything suitable if your machine can send email to GMAIL/Hotmail etc etc.

WRDN.

---

