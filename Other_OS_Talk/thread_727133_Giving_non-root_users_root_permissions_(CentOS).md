---
title: "Giving non-root users root permissions (CentOS)"
date: 2008-03-17
forum: Other OS Talk
---

### Post by MikeeO on 2008-03-17
Hi All

Here is my scenario.

We run our store base on Red Hat but are currently in the process of upgrading to CentOS 5. 

I am having a problem with our Start of Day user. There is a script that chmod -R a directory. Now I keep getting operation not permitted. It is part of the root group and as far as I understand it should be able to chmod all directories seeing as it is part of the root group.

I have tried creating a group called sod that has a UID of 0 and that doesn't even work.

The only way I can get it to work is by chown sod:root then it works but I can't do this because then none of our programs can access the files. 

The users that log in are all under group 700 but if I add my sod user it doesn't run the scripts it puts me straight into the menus.

Please could someone try and help because I'm new to this and my project has now fallen behind.

---

### Post by Oldsoldier2003 on 2008-03-17
> **MikeeO said:**
> Hi All

Here is my scenario.

We run our store base on Red Hat but are currently in the process of upgrading to CentOS 5. 

I am having a problem with our Start of Day user. There is a script that chmod -R a directory. Now I keep getting operation not permitted. It is part of the root group and as far as I understand it should be able to chmod all directories seeing as it is part of the root group.

I have tried creating a group called sod that has a UID of 0 and that doesn't even work.

The only way I can get it to work is by chown sod:root then it works but I can't do this because then none of our programs can access the files. 

The users that log in are all under group 700 but if I add my sod user it doesn't run the scripts it puts me straight into the menus.

Please could someone try and help because I'm new to this and my project has now fallen behind.
make a cron job that runs the script as root?

---

### Post by MikeeO on 2008-03-18
We have a cron job that runs at 5 in the morning but the clever people keep turning the machine off.](*,)

---

### Post by oedha on 2008-03-18
what if .....blocking incoming port ?
maybe that guy remote it ?

---

### Post by PointyWombat on 2008-03-18
> **MikeeO said:**
> We have a cron job that runs at 5 in the morning but the clever people keep turning the machine off.](*,)

Maybe you could refine your cron job to run more frequently, or a frequent cron job to check the state, and run chmod if necessary. A startup script is also an option.

This sounds like an easy problem, but more details on exactly what you need to do would be helpful.

---

### Post by jjk7288 on 2008-03-18
What I would do is edit /etc/rc.local and put your chmod command in there. Those commands run as root. That way, every time you boot up it will perform your chmod for you.

Hope that helps.

---

### Post by MikeeO on 2008-03-18
The sod user creates files and in turn he needs to chmod them. I can't have a cron job running all the time  as a chmod on the files in use will cause complications when users access these files. The files in question are used by all the user practically all the time. 

I can't put it in rc.local as sod can log in at any time and run the Start of Day that updates/creates files.

When you log in as sod (Start of Day) it runs a script that executes a set of programs, these programs create files. The very last thing in the sod is a chmod. Now it won't chmod anything bringing up the error Operation not permitted. Sod belongs to group 0 (root). Now I really have no idea why it isn't able to Chmod a file even though it belongs to the root group. 

Hope this answers a couple questions and help in solving my problem.

---

### Post by Oldsoldier2003 on 2008-03-18
> **MikeeO said:**
> The sod user creates files and in turn he needs to chmod them. I can't have a cron job running all the time  as a chmod on the files in use will cause complications when users access these files. The files in question are used by all the user practically all the time. 

I can't put it in rc.local as sod can log in at any time and run the Start of Day that updates/creates files.

When you log in as sod (Start of Day) it runs a script that executes a set of programs, these programs create files. The very last thing in the sod is a chmod. Now it won't chmod anything bringing up the error Operation not permitted. Sod belongs to group 0 (root). Now I really have no idea why it isn't able to Chmod a file even though it belongs to the root group. 

Hope this answers a couple questions and help in solving my problem.

because sod is root *group* not root. therefore sod acts with the second set of permissions listed when you ls -l.

---

### Post by PointyWombat on 2008-03-20
The files should be created with a common group ownership, for example a group called 'workers', and crated with a 664 permission. all accounts who need to access these files should belong to the 'workers' group as a secondary group as well.  As for the account that creates the file, the script can do a 'newgrp workers' which means that any files created will have a group ownership of workers, and you'll avoid to do a chmod.

---

### Post by MikeeO on 2008-05-05
Right we have it sorted :lolflag:

I've edited /etc/sudoers and added sod user to be able to chmod ... 

I also changed the script that runs the chmod to check if the user is logged in. If they are logged in then I use "sudo chmod".

I also had to alias who to another script that shows everyone who's logged onto the server as all workstations work off the server.

Hope this will be of assistance to anyone else who might find themselves in this situation. :guitar:

---

