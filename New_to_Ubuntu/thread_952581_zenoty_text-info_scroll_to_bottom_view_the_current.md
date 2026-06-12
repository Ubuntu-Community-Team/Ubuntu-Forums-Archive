---
title: "zenoty text-info scroll to bottom view the current operation"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by JohnGalt131 on 2008-10-19
How can I keep zenity --text-info at the bottom of the window, I have to manually scroll down to see the current action.  I would rather it stay at the bottom and I could scroll up to view past operations. Anyone know how to keep text-info at the bottom of its window i.e. scrolled all the way down?

```
 #!/bin/bash

#Pick a profile
cd /home/user/.rsync/Profiles
look=` ls | sed 's/\~//' | sort -u`
echo $look
for **** in $look; do
files=` echo $files | sed '$a'$****''`
done
profile=` zenity --list --text="Select Profile To Run" --column="Profile" $files`
cd /home/user/.rsync/Profiles
bash $profile | zenity --text-info
```

---

