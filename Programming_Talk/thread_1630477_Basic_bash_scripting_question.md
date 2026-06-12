---
title: "Basic bash scripting question"
date: 2010-11-25
forum: Programming Talk
---

### Post by Hosser on 2010-11-25
Hi guys,

I wonder if anyone can help me. I've created a pretty simple but working script for automating the creation of new users. 

I'm using the **useradd** and **read** commands to do most of the work. I'd like to add the **useradd -c** argument to the script so that the user can enter their full name as part of the user creation process. 

However, if you enter **John Smith** as your full name when prompted by the script, it fails due to the space between the first and last names.

My question is, can I get around this? 

I'll post the relveant code snippet below, if you need the rest of the script let me know and I'll post it.

Thanks in advance for any help.

```
## Enter the user's full name.
read -p "Enter the user's full name (e.g. John Smith) : " fullname
```

```
useradd -m -p $pass -g $group -s $shell -c $fullname -k /etc/skel $username
```

And finally, the script in action:

```
root@zeta-reticuli:/var/www/vhosts/zeta-reticuli.co.uk/httpdocs/test# ./adduser.sh
Enter username (e.g. john) : john
Enter the user's full name (e.g. John Smith) : John Smith
Enter the user's primary group membership : users
Enter the path to the user's desired login shell : /bin/bash
Enter the user's password : Usage: useradd [options] LOGIN

Options:
  -b, --base-dir BASE_DIR       base directory for the new user account
                                home directory
  -c, --comment COMMENT         set the GECOS field for the new user account
  -d, --home-dir HOME_DIR       home directory for the new user account
  -D, --defaults                print or save modified default useradd
                                configuration
  -e, --expiredate EXPIRE_DATE  set account expiration date to EXPIRE_DATE
  -f, --inactive INACTIVE       set password inactive after expiration
                                to INACTIVE
  -g, --gid GROUP               force use GROUP for the new user account
  -G, --groups GROUPS           list of supplementary groups for the new
                                user account
  -h, --help                    display this help message and exit
  -k, --skel SKEL_DIR           specify an alternative skel directory
  -K, --key KEY=VALUE           overrides /etc/login.defs defaults
  -m, --create-home             create home directory for the new user
                                account
  -o, --non-unique              allow create user with duplicate
                                (non-unique) UID
  -p, --password PASSWORD       use encrypted password for the new user
                                account
  -r, --system                  create a system account
  -s, --shell SHELL             the login shell for the new user account
  -u, --uid UID                 force use the UID for the new user account


Operation failed. You screwed up. If you need help, open the script in a text editor and read the comments!
```

---

### Post by pawhtiobo on 2010-11-25
I´m no script expert, but have you tried to run your script with the sudo command (with root privileges)? It may be a permissions issue.

See ya..

---

### Post by DaithiF on 2010-11-25
enclose fullname in quotes, like:
```
-c "$fullname"
```

---

### Post by Hosser on 2010-11-25
Sadly no, it's not a permissions issue. I've taken measures to ensure the script won't run unless the user is logged on as root.

Thanks for your reply.

---

### Post by Hosser on 2010-11-25
> **DaithiF said:**
> enclose fullname in quotes, like:
```
-c "$fullname"
```

Oh man, that simple? :(

```
root@zeta-reticuli:/var/www/vhosts/zeta-reticuli.co.uk/httpdocs/test# ./adduser.sh
Enter username (e.g. john) : john
Enter the user's full name (e.g. John Smith) : John Smith
Enter the user's primary group membership : users
Enter the path to the user's desired login shell : /bin/bash
Enter the user's password :
User created successfully.
root@zeta-reticuli:/var/www/vhosts/zeta-reticuli.co.uk/httpdocs/test# su john

Welcome to zeta-reticuli.co.uk, john

Active Sessions:

 13:10:12 up 5 days, 14:14,  1 user,  load average: 0.00, 0.01, 0.00
USER     TTY      FROM              LOGIN@   IDLE   JCPU   PCPU WHAT
root     pts/0    213.120.128.73   13:09    0.00s  0.01s  0.00s bash

System Uptime:

 13:10:12 up 5 days, 14:14,  1 user,  load average: 0.00, 0.01, 0.00
```

Works perfectly. Thanks very much, DaithiF.

---

