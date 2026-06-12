---
title: "Bash &amp; Postgre Error capturing"
date: 2012-08-13
forum: Programming Talk
---

### Post by Dragonbite on 2012-08-13
I have a shell script on a FreeBSD web server for work that is taking a text file (generated from the office server) and updates a table in the Postgre database.  

It works and emails me success messages.  I have verified that it does copy the data into the table, and it does send me an email with the success message.

Unfortunately I cannot get it to recognize there is an error in the code though when I manually run the script I see a message about a field that does not accept NULL values but the script doesn't see it.

Ideally I want to be able to capture the actual error message, which I can put into the email, if not then at least to register there IS an error which I can go and start investigating manually.

Here is my code, after removing comments and other clutter
```

#!/bin/sh
set -e

ERRMSG="/usr/home/dbupdater/error.msg"
SENDTO="me@work.com"
SUBJECT="Database update status"

# 
# If the file exists, remove it so we can create a new empty file
#

if [ -f $ERRMSG ]
then
     rm $ERRMSG
fi
echo "Started $(date)" > $ERRMSG

#
# run this block of actions in the Postgre database
#

/usr/local/bin/psql database_name -U user_name <<EOF

     TRUNCATE table_name;

    \copy table_name (field1, field2, field3 ) from '/usr/home/dbupdater/update.txt' with NULL 'NULL'

EOF

#
# If there is an error ( $? ) then do something. The problem is the process
# never goes into this loop. 
#

if [ $? != 0 ]; then
{
     echo "     Error loading the table." >> ${ERRMSG]
     exit 1
}
else
{
     echo "     Successfully loaded table." >> ${ERRMSG}
} fi

mail -s "$SUBJECT" "$SENDTO" < $ERRMSG



```

I have been using Linux, but am relatively new to actual shell scripting.  I know this is FreeBSD, not Linux but I have gotten good advice from these forums and am sure the issue isn't all FreeBSD-specifc (I could be wrong though).

Any help would be appreciated! Thanks!

---

### Post by Vaphell on 2012-08-13
psql ends with 0 status?

capture the output with *psql_out=$( psql ... 2>&1 )* with stderr redirected to stdout and see if $psql_out contains relevant info.

---

### Post by Dragonbite on 2012-08-13
> **Vaphell said:**
> psql ends with 0 status?

capture the output with *psql_out=$( psql ... 2>&1 )* with stderr redirected to stdout and see if $psql_out contains relevant info.

I am getting a status of 0 even when I get some error or other. 

Please forgive me, can you explain the coding you are suggesting?  I am not sure how to do what you are recommending.

I understand you are trying to redirect stderr to stdout but are you talking about 
```
psql_out=$(/usr/local/bin/psql database_name -U user_name <<EOF
    TRUNCATE table_name;

    \copy table_name (field1, field2, field3 ) from '/usr/home/dbupdater/update.txt' with NULL 'NULL'

EOF)
```

Will that work?  What do I get with that?

---

### Post by Vaphell on 2012-08-13
yes, that's what i am talking about and you will never know if that works if you don't try :)
psql_out should contain the string psql would otherwise spit to terminal and you can grep it for errors or whatever.

---

### Post by Dragonbite on 2012-08-14
That didn't work for me, but elsewhere it was suggested to add ```
\set ON_ERROR_STOP TRUE
``` so that "$?" will return some value (0 = success, 1 & 2 = database connectivity and 3 = script code error)

---

### Post by Dragonbite on 2012-08-14
I had posted this at other locations and was weeding through some of their responses as well as here and trying to read what I found online.

Using "\set ON_ERROR_STOP TRUE" is working and returning the error code. I may move it to the opening PostgreSQL line just in case, though.

So for reference in case anybody stumbles upon this thread is 

```
#!/bin/sh

ERRMSG="/usr/home/dbupdater/error.msg"
SENDTO="me@work.com"
SUBJECT="Database update status"

# 
# Remove previous $ERRMSG file because if file exists it assumes there is an error 
# and will send an email to the person in charge.
#

if [ -f $ERRMSG ]
then rm $ERRMSG
fi

#
# Run this block against the PostgreSQL database
#

/usr/local/bin/psql database_name -U user_name <<EOF 

     \set ON_ERROR_STOP TRUE 
    
     TRUNCATE table_name; 
   
     \copy table_name (field1, field2, field3 ) from '/usr/home/dbupdater/update.txt' with NULL 'NULL'

EOF

#
# Clear the variable and capture any error codes from the PostgreSQL database running above
# 

ERRCODE=0
ERRCODE=$?

#
# Compare returned $ERRCODE to focus the message to be sent
# 

case $ERRCODE in
     3) echo "Script error(3) loading the table." >> $ERRMSG
     ;;
     2) echo "Connectivity error(2) loading the table." >> $ERRMSG
     ;;
     1) echo ""Fatal (out of memory, file not found) error(1) loading the table." >> $ERRMSG
     ;;
esac

#
# If the $ERRMSG file exists, assume file is populated with some error code and must be sent to
# the person in charge of this.
#

 if [ -f $ERRMSG ]
then mail -s "$SUBJECT" "$SENDTO" < $ERRMSG
fi
```

---

