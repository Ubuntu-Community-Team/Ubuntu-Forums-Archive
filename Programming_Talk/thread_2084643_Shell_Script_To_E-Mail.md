---
title: "Shell Script To E-Mail"
date: 2012-11-16
forum: Programming Talk
---

### Post by SalientAnimal on 2012-11-16
Hi All,

I'm having some problems with my shell script. The script is meant to gather some system information and then add these into an html file and send of the mail. Currently it is sending the attachment, but the html file is blank.
 
Any help will be greatly appreciated.
 
```
#!/bin/bash
# ===================================================================== #
#      BACKUP SCRIPT WITH SYSTEM INFORMATION    #
#       SCRIPT CREATED 15/11/2012      #
#      SCRIPT LAST MODIFIED 15/11/2012      #
# ===================================================================== #

# ===================================================================== #
#      VARIABLES THAT CAN BE USED IN THE SCRIPT     #
# ===================================================================== #
# DIRECTORY WHERE FILES ARE STORED
BACKUPDIR="/mnt/data6/reports"
# CREATES A TITLE VARIABLE
TITLE=" System Status"
# SPECIFY THE CONTENT OF THE E-MAIL TO BE SENT
MAILCONTENT="files"
# SETS THE MAXIMUM SIZE OF THE E-MAIL 4000 = +/- 5MB
MAXATTSIZE="4000"
# E-MAIL ADDRESS WHERE THE E-MAIL WILL BE SENT
MAILADDR="[EMAIL="myemail@domai.com"]myemail@domai.com[/EMAIL]"
# DEFINE THE E-MAIL BODY
SUBJECTFILE=$BACKUPDIR/sqldump.txt
# CREATE THE FILE TO ATTACH
ATTACHMENT=$BACKUPDIR/Status.html

# ===================================================================== #
#        FUNCTIONS         #
#      STUBBING IS USED AS A TEMPORY PLACE HOLDER FOR FUTURE CODE       #
# ===================================================================== #
 
 
function drive_space
{
    echo "<h2>Filesystem Space</h2>"
    df -h
}
# ---- END OF DRIVE SPACE ---- #

function backup_size
{
    echo "<h2>Backup Size</h2>"
    du -h _sqldump.sh
}
# ---- END OF BACKUP SIZE ---- #

function additional_function
{
    # TEMPORARY FUNCTION STUB
    echo "function additional_function"
}
# ---- END OF ADDITIONAL FUNCTIONS ---- #
 
 
# ===================================================================== #
#     GATHERS AND DISPLAYS THE STATUS OF THE SYSTEM   #
# ===================================================================== #
function ATTACHMENT
{
"cat <<-Status
  <html>
  <head>
  <title>$TITLE</title>
  </head>
  
  <body>
  <h1>$TITLE</h1>
  <p></p>
  $(drive_space)
  $(backup_size)
  <body>
  </html>
Status"> $ATTACHMENT
}
# ===================================================================== #
#    GATHERS INFORMATION AND SEND MESSAGE ATTACHMENT    #
# ===================================================================== #
 
if [ "$MAILCONTENT" = "files" ]
 then
 mutt -e "set content_type=text/html" -s " System Status $DATE" -a $ATTACHMENT -- $MAILADDR < $SUBJECTFILE
fi

exit 0

```

---

### Post by drmrgd on 2012-11-16
I see you use the variable $ATTACHMENT as an argument to your mutt call, but I don't see you call the function ATTACHMENT in order to generate data for that variable.  I think you need to call that function before you pass the variable to mutt.

---

