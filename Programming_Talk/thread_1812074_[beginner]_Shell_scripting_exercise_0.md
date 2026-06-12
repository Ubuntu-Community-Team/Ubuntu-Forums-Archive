---
title: "[beginner] Shell scripting exercise 0"
date: 2011-07-25
forum: Programming Talk
---

### Post by sisco311 on 2011-07-25
The rules are simple:
[list]
[*]post a working shell code;
[*]you can use whatever shell you like (bash, csh, zsh, dash, ...). bash is the de facto standard shell on most modern Linux and Unix systems;
[*]this is a shell scripting exercise, so try to avoid using external commands like cut, sed, awk...
[*]comment your code and use proper indentation and
[*]QUOTE YOUR VARIABLES, otherwise I will yell at you. :evil: :)
[/list]

Exercise 0:
Write a script which prints: 
[list=i]
[*]the total number of (local) users on the system; 

[*]the number and list of normal users (with an UID greater that or equal to 1000); 

[*]the number and list of system users (with an UID less than 1000, but not 0) and

[*]the shortest and the longest usernames 
[/list]

Sample output:
```

number of users - 35
 4 normal users - nobody:sisco:fo:bar
30 system users - daemon:bin:sys:sync:games:man:lp:mail:news:uucp:proxy:www-data:backup:list:irc:gnats:libuuid:syslog:messagebus:avahi-autoipd:avahi:usbmux:gdm:speech-dispatcher:kernoops:pulse:rtkit:saned:hplip:couchdb:

shortest username(s) - lp:fo
longest  username(s) - speech-dispatcher

```

PS:
Most of the things you have to know to solve this exercise are covered at [BashFAQ](http://mywiki.wooledge.org/BashFAQ/) (you can use it as a reference even if you don't use bash).

---

### Post by AlphaLexman on 2011-07-26
This is harder than I thought...

Still working on it though...

---

### Post by sisco311 on 2011-07-26
If you get stuck or have any questions, feel free to ask.

---

### Post by Bachstelze on 2011-07-26
> **sisco311 said:**
> bash is the de facto standard shell on most modern Linux and Unix systems;

But [sh](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/sh.html) is the de jure one.

---

### Post by papibe on 2011-07-26
Can I participate? I haven't participated much in the Programming Forum. Sorry if not.

This is my script:
```
#!/bin/bash

# [beginner] Shell scripting exercise 0
# proposed by sisco311 at ubuntuforums.org
# link: http://ubuntuforums.org/showthread.php?t=1812074
#
# Author: papibe
# Tue Jul 26 19:32:07 CDT 2011

# Counters.
total_users=0       # Number of users.
normal_users=0      # Number of normal users.
system_users=0      # Number of system users.

# Lists of users.
Lnormals=""         # List of normal usernames.
Lsystems=""         # List of system usernames. 

# Longest and shortest counters.
clongest=0          # Start with longest at 0.
cshortest=256       # Start with shortest at 256.

# Longest and shortest usernames.
longest=""          # Longest username.
shortest=""         # Shortest username.


# Read ines using ':' as separation from /etc/passwd (see while's done).
# Only care about username and uid. Ignore rest by asign it to x.
while IFS=: read -r username x uid x x x x
do
    # Counting users.
    let total_users+=1

    # Check if user is normal or system.
    if [ "$uid" -ge 1000 ]; then
        let normal_users+=1
        Lnormals="$username":"$Lnormals"
    else
        # System user.
        let system_users+=1
        Lsystems="$username":"$Lsystems"
    fi

    # Length of usename string.
    length=${#username}


    # Test for shortest.
    if [ "$length" -lt "$cshortest" ]; then
        # 'The' shortest.
        cshortest="$length"
        shortest="$username"
    else
        if [ "$length" -eq "$cshortest" ]; then
            # Same length as actual shortest.
            shortest="$username":"$shortest"
        fi
    fi

    # Test for longest.
    if [ "$length" -gt "$clongest" ]; then
        # 'The' longest.
        clongest="$length"
        longest="$username"
    else
        if [ "$length" -eq "$clongest" ]; then
            # Same length as actual longest.
            longest="$username":"$longest"
        fi
    fi
done < /etc/passwd

# Final report.
echo "number of users - " "$total_users"
echo "$normal_users" "normal users - " "$Lnormals"
echo "$system_users" "system users - " "$Lsystems"

echo
echo "shortest username(s) - " "$longest"
echo "longest  username(s) - " "$shortest"

```

---

### Post by sisco311 on 2011-07-27
> **Bachstelze said:**
> But [sh](http://pubs.opengroup.org/onlinepubs/9699919799/utilities/sh.html) is the de jure one.

Indeed it is.

> **papibe said:**
> Can I participate? I haven't participated much in the Programming Forum. Sorry if not.


If you consider yourself beginner or intermediate in shell scripting, then why not?

About your code. It would be nice if you could get rid of the extra : from the end of the user lists. In bash you could use an array to store the names.

root is not a system user and you mixed up the variables in the last two lines.

Otherwise your code is well structured and commented. The solution you provided is pretty much what I was thinking of.

Good job! :KS

---

### Post by papibe on 2011-07-27
Thanks a lot sisco311 for taking the time to review my code. I really appreciate your suggestions. I'm starting by researching about bash lists.

Thanks again,
Regards.

---

