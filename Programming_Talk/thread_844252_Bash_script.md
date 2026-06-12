---
title: "Bash script"
date: 2008-06-29
forum: Programming Talk
---

### Post by coombesy on 2008-06-29
Hi,

my mission is to password protect a folder. Was going to do this by chmoding the folder to 000.
The script would then ask for password, chmod to +rwx, then when nautilus closes it would chmod back to 000.

Problem is that as nautilus is opening the rest of the script runs and chmods it back to 000. Need to have script wait till nautilus is closed before going to next line on the script.

```

#! /bin/bash

#ask for password
gksudo

#chmod to allow access
chmod +rwx /home/coombes/filth;
#run nautilus to view folder
nautilus /home/coombes/filth;
#chmod back to 000
chmod 000 /home/coombes/filth
exit

```

I thought that having ';' at the end of a line would solve this, but unfortunatly no joy.

any help would be appreciated.

---

### Post by HalPomeranz on 2008-06-29
The problem with your approach is that anybody who has root access on the system can see the files regardless of the permissions settings.  Why not just make the files/directories so that they're only readable by a certain Unix group and then add the appropriate people to the group?  Or better still, create an encrypted folder using something like Truecrypt and only give the password to people who need to be able to see the files.

---

