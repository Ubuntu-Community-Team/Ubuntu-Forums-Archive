---
title: "how to execute rest of script with another user"
date: 2020-12-26
forum: New to Ubuntu
---

### Post by danielb630 on 2020-12-26
Hi everyone, I need to write a script that creates a new sudo user and then need to continue running the same script 
When I do it everything works fine but then the script just stops, it looks like this:

    read -p "enter new sudo username: " -r newsudo
    sudo adduser "$newsudo"
    sudo usermod -aG sudo "$newsudo"
    su - "$newsudo"


 Thanks for helping

---

### Post by TheFu on 2020-12-26
You need 2 different scripts. The first runs as root. The second would be called using su. You can view examples in su manpage.  No need for 'sudo' command inside the first script, as it would be run with sudo on the outside.

```
sudo /path/to/script1
```
then
```
sudo -i -u  "$newsudouser" /path/to/script2
```


Someone doing scripting like this should be very familiar with manpages. There are many caveats, especially security related, for what is being done. 

I suspect there is a better method to accomplish whatever the end-goal of this script, but without that end goal, we cannot advise.

---

### Post by danielb630 on 2020-12-26
I am trying to create a script that adds new users and adds them to different groups with different permissions. 
Part of the script has to create new sudo user and then continue to create the new users and do more tasks, Do you think I can do that in one script?
thank you for your comment

---

### Post by TheFu on 2020-12-26
No need for more than 1 user or script.  If it was me, I'd have a 2 column table. 
```
user1  users,group1,grp4,project
user2  users,group2,grp4,project
user3  users,group4,grp4,project
user4  users,group4
user10 users
user5 users
user13 users
user145 users
user19 users
```

Then just loop over each entry, creating the user, default group (1st in list), then add groups after that.

ZERO need for extra users or calling su - or sudo.

Sounds like a homework assignment.  Heck, I probably wouldn't bother with a fancy script. Just create it in a file with each user's creation and groups on 1 line.

```
sudo adduser user1  --ingroup users ; sudo addgroup --add_extra_groups group1,grp4,project user1
sudo adduser user2  --ingroup users ; sudo addgroup --add_extra_groups group2,grp4,project user2
```

A little pre-processing to ensure the groups already exist wouldn't be too hard with some **sort -u** options on the list.
Always choose batch over interactive, if possible.  Best to accept inputs from stdin when possible too so the output from some prior work can become the input to the next script.

Groups just exist as objects for downstream needs.

I'd be worried about providing wide sudo access to just anyone.  If only limited elevated privileges are needed, only provide those specific privileges and nothing more. Be certain to limit commands AND command options, since many commands have ways to break out and do other stuff temporarily.

---

