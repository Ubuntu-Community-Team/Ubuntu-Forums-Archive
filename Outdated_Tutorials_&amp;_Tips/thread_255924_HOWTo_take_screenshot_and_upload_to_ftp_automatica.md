---
title: "HOWTo take screenshot and upload to ftp automatically"
date: 2006-09-12
forum: Outdated Tutorials &amp; Tips
---

### Post by grizzly on 2006-09-12
My first HOWTo!! - hope it helps :)
I have tried to make it as easy as possible for those unfamiliar  with ftp, suggest any improvements plz.

**Step 1. Install the apps:**
 > sudo aptitude install ncftp scrot 

**Step 2. Get the script > save it as 'shoot' > make it executable > put it in your path /usr/bin**

**Step 3. Get yourself a free ftp account ( [www.ripway.com](www.ripway.com) is OK) **

**Step 4. Open the script, fill in the variables**
**Done! Just use the script by typing "shoot filenameforimage"**

** The Script**

```

#!/bin/bash

[COLOR="Red"]#VARIABLES - change them as required[/COLOR]

FTPSERVER=[COLOR="Red"]ftphost.ripway.com [/COLOR] # No need to change if you are going with ripway.
USERNAME=[COLOR="Red"]WRITE USERNAME HERE[/COLOR]
PASSWORD=[COLOR="Red"]WRITE PASS HERE[/COLOR]
dir=~[COLOR="Red"]/documents/pictures/screenshots[/COLOR] # directory for screenshots

###

scrot -d 3 -q 1  "$dir/$1.png"  # screenshot taken in png format after a delay of 3 seconds

echo "Upload to ftp?"
read ans

if [[ "$ans" == "y" ]]
then
ncftpput -u $USERNAME -p $PASSWORD   $FTPSERVER /  $dir/$1.png

[COLOR="Red"]## OPTIONAL PART!![/COLOR]
# path of uploaded file - use this to paste ; would depend on youR ftp server;username
#echo http://h1.ripway.com/chesss/$1.png
else

echo not uploaded

fi

exit
```

---

