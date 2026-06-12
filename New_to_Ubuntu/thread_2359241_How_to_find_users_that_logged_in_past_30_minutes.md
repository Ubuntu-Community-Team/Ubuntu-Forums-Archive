---
title: "How to find users that logged in past 30 minutes"
date: 2017-04-21
forum: New to Ubuntu
---

### Post by andrespineros on 2017-04-21
[COLOR=#242729][FONT=Arial]I need to create a command to find all the users that logged in the system in the past 30 minutes. 
The command can be split in multiple commands as I intend to call it from python. For example:[/FONT][/COLOR]
[COLOR=#7D2727]
[/COLOR][COLOR=#303336]1. Command to find all users [/COLOR][COLOR=#101094]in[/COLOR][COLOR=#303336] system
[/COLOR][COLOR=#303336]2. Loop all users [/COLOR][COLOR=#101094]in[/COLOR][COLOR=#303336] python
[/COLOR][COLOR=#303336]3. Ask if the iterated user logged [/COLOR][COLOR=#101094]in[/COLOR][COLOR=#303336] the system [/COLOR][COLOR=#101094]in[/COLOR][COLOR=#303336] the past [/COLOR][COLOR=#7D2727]30[/COLOR][COLOR=#303336] min[/COLOR][COLOR=#303336].[/COLOR][COLOR=#303336]
[/COLOR][COLOR=#303336]4. If so[/COLOR][COLOR=#303336],[/COLOR][COLOR=#303336] add iterated user to recentUsersList[/COLOR][COLOR=#303336].


[/COLOR][COLOR=#242729][FONT=Arial]From this, I only need step 3.[/FONT][/COLOR]

---

### Post by Keith_Helms on 2017-04-22
On my Xubuntu system, auth.log seems to be a good place to check for logins with messages like this
```

Apr 21 11:33:35 sager-laptop systemd-logind[906]: New session c2 of user keith

```

The logic I would use is:

1. Get the current time in seconds since 1970-01-01 00:00:00 UTC which is the start date for Linux time.
2. Subtract 30 minutes from that time.
3. Pull all the login messages from /var/log/auth.log
4. Compare the time of login to the 30 minutes ago time
5. If the login was within 30 minutes, flag that the user logged in during the period

I don't know Python, but in Bash I'd do the following:

```

#!/bin/bash

# Using a bash associative array where entries are referenced by text, not by index numbers
declare -A logins
starttm=`date +%s`
starttm=$((starttm-1800))
while IFS= read -r line; do
  timestamp=${line:0:15}
  logintime=`date --date="$timestamp" +%s`
  if [ $logintime -ge $starttm ]
  then
    # found a login within the desired window, extract the userid
    userid=`echo $line | sed 's/.*of user //' | tr -d '.'`
    # flag that the user logged on during the period
    logins[$userid]=Y
  fi
done < <( grep systemd-logind auth.log | grep "New session" )

# At this point the logins associate array has Y assigned to each userid that logged in
# Examples to check this

if [ "${logins[keith]}" == "Y" ]
then
  echo "keith logged on"
else
  echo "keith did not log on"
fi

if [ "${logins[joe]}" == "Y" ]
then
  echo "joe logged on"
else
  echo "joe did not log on"
fi

```

Hopefully you can convert that logic to Python.

---

