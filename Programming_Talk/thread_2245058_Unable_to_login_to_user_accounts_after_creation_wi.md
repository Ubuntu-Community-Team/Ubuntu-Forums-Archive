---
title: "Unable to login to user accounts after creation with script"
date: 2014-09-20
forum: Programming Talk
---

### Post by alextrottier2014 on 2014-09-20
I'm taking a Linux system administration course at school, and one of our regular tasks is creating multiple users. I decided I was tired of entering the command time after time, so I created a script that prompts me for username+password, than adds it to the useradd command.

However, I'm unable to login to the user through terminal, or through the GUI login screen. Not sure what I'm doing wrong.

```
while [ $a -ne $b ]; do
    echo -e '\'n 
    echo "What is the username:"
    read username                      
    echo "What is the password:"
    read password                          
    echo -e '\'n
    if [ $fullyes = Y ]; then
     echo "What do you want the home location to be:"
     read homedir
     echo "What do you want the comment to be:"
     read comment
     sudo useradd $username -p $password --home $homedir -c $comment
     let a=a+1
    elif [ $fullyes = N ]; then
     sudo useradd $username  -p $password
     let a=a+1
    fi
done
```

---

### Post by steeldriver on 2014-09-20
I don't think it will work if you pass the plaintext password - from man useradd:

```

       -p, --password PASSWORD
           **The encrypted password, as returned by crypt(3)**. The default is to disable the password.

           Note: This option is not recommended because the password (or encrypted password) will be visible
           by users listing the processes.

           You should make sure the password respects the system's password policy.

```

In any case, you are largely re-inventing the wheel here since there is already an 'adduser' script that does most of what you want (and is probably configurable to do the rest via its configuration file /etc/adduser.conf)

```

ADDUSER(8)                                                                                         ADDUSER(8)

NAME
       adduser, addgroup - add a user or group to the system

SYNOPSIS
       adduser  [options]  [--home DIR] [--shell SHELL] [--no-create-home] [--uid ID] [--firstuid ID] [--las&#8208;
       tuid ID] [--ingroup  GROUP  |  --gid  ID]  [--disabled-password]  [--disabled-login]  [--gecos  GECOS]
       [--add_extra_groups] [--encrypt-home] user
.
.
.
   COMMON OPTIONS
       [--quiet] [--debug] [--force-badname] [--help|-h] [--version] [--conf FILE]

DESCRIPTION
       adduser and addgroup add users and groups to the system according to command line options and configu&#8208;
       ration  information  in /etc/adduser.conf.  They are friendlier front ends to the low level tools like
       useradd, groupadd and usermod programs, by default choosing Debian policy conformant UID and GID  val&#8208;
       ues,  creating  a  home directory with skeletal configuration, running a custom script, and other fea&#8208;
       tures.  adduser and addgroup can be run in one of five modes:

```

---

### Post by alextrottier2014 on 2014-09-20
Ah alright, do you have any suggestion on how to add a password then?

I understand that there's already a script to this, however I'm in the process of teaching my self how to properly script in bash, so I figured this would be a good way to do it, instead of using something that's already been built.

The one thing I don't get though is every time I try logging in, it fails, and when I try logging in through terminal I get
```

su: Authentication Failure

```

Edit: The reason why I wasn't able to login through command line is that I had to sudo the the login command

---

