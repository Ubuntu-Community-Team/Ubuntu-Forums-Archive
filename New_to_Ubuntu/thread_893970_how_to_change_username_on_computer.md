---
title: "how to change username on computer"
date: 2008-08-18
forum: New to Ubuntu
---

### Post by freedomstudent7 on 2008-08-18
i read in a post from last year that one should go to administrator and then to users, and then to properties to change a username and password.   i did this, however i am only given the option of changing my password, not my username.   can someone direct me how i can change my username?   i am the computer's administrator.   thanks!

---

### Post by st33med on 2008-08-18
I don't think you can change your username unless you create a new user and move the contents of the home directory to your new name. It isn't advisable too because the user would loose all privileges he had in his other account.

---

### Post by Dr Small on 2008-08-18
You can't change you username, as far as I am aware of.

---

### Post by freedomstudent7 on 2008-08-18
thanks for the responses.   i know it's possible because i had this same problem before and the fellow who installed ubuntu on my computer the first time was able to do this.   he had to go into the terminal, and maybe that has something to do with what you were saying.   when it was done, however something went wrong with the system and i had to start all over by reinstalling ubuntu.   when the new guy put it in he used a different name than i wanted, and now it seems i'm stuck with it. (but hopefully not!)

---

### Post by cariboo on 2008-08-18
I think the guy that did your origional install did the same thing in a terminal, that you can do from System-->Administration--Users And Groups. Just create a new user, transfer the files you want from the old user to the new user, then delete the old user.

Jim

---

### Post by eightmillion on 2008-08-19
You will have to create a new user as outlined above and then run a couple of commands:
```

sudo cp -r /home/olduser/* /home/newuser/
sudo chown -R newuser:newuser /home/newuser/
sudo rm -rf /home/olduser

```
Make sure you replace all instances of **olduser** and **newuser** above with the appropriate values.
Then logout and log back in as the newuser.

---

### Post by jerome1232 on 2008-08-19
and don't forget to make the new user a member of the "admin" group before you delete your old user.

---

### Post by bab1 on 2008-08-19
Say it aint so...

You can't change your login (user) name.  But it really is no big loss.  The only thing the user owns is his /home/<user> directory.   
All that root needs to:
[LIST=1]
[*]Create a new user (make sure you have all of the same groups)
[*]Move the old users files to the new users home directory.
[*]Change the ownership of the files to the new user.
[/LIST]

Edit:  See 4 people with the same thought.  :-)

---

### Post by pauper on 2008-08-19
[http://ubuntuforums.org/showpost.php?p=5504884](http://ubuntuforums.org/showpost.php?p=5504884)

---

### Post by hyper_ch on 2008-08-19
I think you can change your login name by altering the /etc/passwd file. As long as the UID stays the same it should not be any problem. But then you may also want to rename your home directory.

---

### Post by jerome1232 on 2008-08-19
What about this usermod command
```
USERMOD(8)                System Management Commands                USERMOD(8)



NAME
       usermod - modify a user account

SYNOPSIS
       usermod [options] LOGIN

DESCRIPTION
       The usermod command modifies the system account files to reflect the
       changes that are specified on the command line.

OPTIONS
       The options which apply to the usermod command are:

       -a, --append
           Add the user to the supplemental group(s). Use only with -G option.

       -c, --comment COMMENT
           The new value of the user´s password file comment field. It is
           normally modified using the chfn(1) utility.

       -d, --home HOME_DIR
           The user´s new login directory. If the -m option is given the
           contents of the current home directory will be moved to the new
           home directory, which is created if it does not already exist.

       -e, --expiredate EXPIRE_DATE
           The date on which the user account will be disabled. The date is
           specified in the format YYYY-MM-DD.

       -f, --inactive INACTIVE
           The number of days after a password expires until the account is
           permanently disabled. A value of 0 disables the account as soon as
           the password has expired, and a value of -1 disables the feature.
           The default value is -1.

       -g, --gid GROUP
           The group name or number of the user´s new initial login group. The
           group name must exist. A group number must refer to an already
           existing group. The default group number is 1.

       -G, --groups GROUP1[,GROUP2,...[,GROUPN]]]
           A list of supplementary groups which the user is also a member of.
           Each group is separated from the next by a comma, with no
           intervening whitespace. The groups are subject to the same
           restrictions as the group given with the -g option. If the user is
           currently a member of a group which is not listed, the user will be
           removed from the group. This behaviour can be changed via the -a
           option, which appends the user to the current supplementary group
           list.

       -l, --login NEW_LOGIN
           The name of the user will be changed from LOGIN to NEW_LOGIN.
           Nothing else is changed. In particular, the user´s home directory
           name should probably be changed manually to reflect the new login
           name.

       -L, --lock
           Lock a user´s password. This puts a ´!´ in front of the encrypted
           password, effectively disabling the password. You can´t use this
           option with -p or -U.

       -o, --non-unique
           When used with the -u option, this option allows to change the user
           ID to a non-unique value.

       -p, --password PASSWORD
           The encrypted password, as returned by crypt(3).

       -s, --shell SHELL
           The name of the user´s new login shell. Setting this field to blank
           causes the system to select the default login shell.

       -u, --uid UID
           The numerical value of the user´s ID. This value must be unique,
           unless the -o option is used. The value must be non-negative.
           Values between 0 and 999 are typically reserved for system
           accounts. Any files which the user owns and which are located in
           the directory tree rooted at the user´s home directory will have
           the file user ID changed automatically. Files outside of the user´s
           home directory must be altered manually.

       -U, --unlock
           Unlock a user´s password. This removes the ´!´ in front of the
           encrypted password. You can´t use this option with -p or -L.

CAVEATS
       usermod will not allow you to change the name of a user who is logged
       in. You must make certain that the named user is not executing any
       processes when this command is being executed if the user´s numerical
       user ID is being changed. You must change the owner of any crontab
       files manually. You must change the owner of any at jobs manually. You
       must make any changes involving NIS on the NIS server.

FILES
       /etc/group
           Group account information.

       /etc/passwd
           User account information.

       /etc/shadow
           Secure user account information.

SEE ALSO
       chfn(1), chsh(1), passwd(1), crypt(3), gpasswd(8), groupadd(8),
       groupdel(8), groupmod(8), login.defs(5), useradd(8), userdel(8).



System Management Commands        10/28/2007                        USERMOD(8)
```

---

### Post by freedomstudent7 on 2008-08-20
thanks for the info everyone.   been busy, but gonna try some of these suggestions

---

