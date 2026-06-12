---
title: "Can we check weather the user is Admin or Normal user"
date: 2012-10-26
forum: Programming Talk
---

### Post by Mohan1289 on 2012-10-26
hi friends

Can we check weather the user is normal user or administrator by using a command??

---

### Post by spjackson on 2012-10-26
How do you define what an "Admin" user is, or "administrator"?
```

id username

```
will tell you which groups the user belongs to. You can use this and grep for whichever group(s) that you decide define an admin user, e.g. adm, sudo, admin.

---

### Post by Mohan1289 on 2012-10-26
> **spjackson said:**
> How do you define what an "Admin" user is, or "administrator"?
```

id username

```will tell you which groups the user belongs to. You can use this and grep for whichever group(s) that you decide define an admin user, e.g. adm, sudo, admin.


well suppose in a shell script i have to check weather user got Admin permissions or not

If he doesn't have the permission i have to display Authentication failure??

or can i give the command in shell script like

**$sudo some_command**

then echo enter password since it will asks for password

then can i read the entered password and supply it to script

and if the root password and the supplied password or correct then proceed to next statement
else
it has to display Wrong password

can we do that??

or it's not possible?

---

### Post by codemaniac on 2012-10-26
You can use something like below in your shell script 

```

#!/bin/bash
ROOT_UID=0 # Only users with $UID 0 have root privileges.
E_NOTROOT=87 #Non-root exit error.

# Run as root, of course.
if [ "$UID" -ne "$ROOT_UID" ]
then
echo "Must be root to run this script."
exit $E_NOTROOT
fi
```

---

### Post by Lars Noodén on 2012-10-26
You can check for membership in certain groups, like 'sudo'

```

if id -Gn ${USER} | tr " " "\n" | grep -qx sudo;then echo Admin;fi

```

But that's only for the unmodified default setup of Ubuntu. If the basic capabilities of sudo have been expanded, there might be other admin privileges added via other groups.

/etc/sudoers can be modified so that specific users have access to specific programs or even specific programs with specific sets of options.  So there is no surefire way to tell whether or not a user has full or partial or no admin privileges short of actually running sudo.

For example,,

```

%adm ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service

```

---

### Post by Mohan1289 on 2012-10-26
> **Lars Noodén said:**
> You can check for membership in certain groups, like 'sudo'

```

if id -Gn ${USER} | tr " " "\n" | grep -qx sudo;then echo Admin;fi

```But that's only for the unmodified default setup of Ubuntu. If the basic capabilities of sudo have been expanded, there might be other admin privileges added via other groups.

/etc/sudoers can be modified so that specific users have access to specific programs or even specific programs with specific sets of options.  So there is no surefire way to tell whether or not a user has full or partial or no admin privileges short of actually running sudo.

For example,,

```

%adm ALL=(ALL:ALL) NOPASSWD:/usr/sbin/service

```

can we supply the password to the script too??
like 

echo enter password
read p

can't we do that  too?

---

### Post by Vaphell on 2012-10-26
can't you simply do **sudo script**? either the user authenticates or not

afaik this works but never tried it
```
echo $pw | sudo ...
```

---

### Post by Mohan1289 on 2012-10-26
> **Vaphell said:**
> can't you simply do **sudo script**? either the user authenticates or not

afaik this works but never tried it
```
echo $pw | sudo ...
```

can you explain that to me i don't understand

suppose i have to move a file/folder to the directory in a root..

Can i do that without the permission as root??

---

### Post by spjackson on 2012-10-26
> 
well suppose in a shell script i have to check weather user got Admin permissions or not

What are "Admin permissions"? You've had replies about how to check for membership of specific groups. What do you mean by "Admin permissions" other than group membership?

> 
can we supply the password to the script too??
like 

echo enter password
read p

can't we do that too?

"sudo -S" allows you to supply the password via stdin rather than the terminal. However, this is not recommended practice. What are you trying to do? Why doesn't normal use of sudo meet your requirements?

---

### Post by Mohan1289 on 2012-10-26
> **spjackson said:**
> What are "Admin permissions"? You've had replies about how to check for membership of specific groups. What do you mean by "Admin permissions" other than group membership?


"sudo -S" allows you to supply the password via stdin rather than the terminal. However, this is not recommended practice. What are you trying to do? Why doesn't normal use of sudo meet your requirements?

Because i have to write a shell script which deploys packages automatically in Jboss server so that i must be a sudo Right?? 

that's why i wanna check weather the user is in the sudo group or not

if he is i will use

sudo mv pacakge/folder to the specified location

Since i used sudo it will prompt for password
that's the reason i want to prompt in the command prompt too

---

### Post by Vaphell on 2012-10-26
is it all the script does? moving stuff to restricted directories?

```
deploy.sh:
sudo mv $from $to


$ ./deploy.sh
```

---

### Post by Mohan1289 on 2012-10-26
> **Vaphell said:**
> is it all the script does? moving stuff to restricted directories?

```
deploy.sh:
sudo mv $from $to


$ ./deploy.sh
```

No it's more than just moving

i have to restart j boss server

service stop jboss

then check for the processes using
[B]ps ax | grep jboss
[/B]kill all the other processes except Jboss
then start the jboss again..

then connect to mysql database in the server
then using mysqldump import database from the package

That's what i have to do

---

### Post by Vaphell on 2012-10-26
what about
```
deploy.sh:
mv
jboss things
mysql things
...


$ sudo deploy.sh

```

---

### Post by Mohan1289 on 2012-10-26
> **Vaphell said:**
> what about
```
deploy.sh:
mv
jboss things
mysql things
...


$ sudo deploy.sh

```

how can a normal user can do that..
i mean if i run the script normally in bash shell($) rather than (#)

does it move the jboss things??

what i want to say is. in server there are alot of users right?? if every one of them runs this script to move a certain package since this script does it automatically where lies the security they may corrupt the system so i want to check weather they are sudo or not if sudo then proceed if not Authentication failure

---

### Post by spjackson on 2012-10-26
```

#!/bin/bash

id=$(/usr/bin/id -u)

if [ $id -ne 0 ] ; then
  echo "You must use sudo to run this script"
  exit 1
fi

# other stuff goes here...
# mv
# jboss things
# mysql things
# ...

echo Done.

```
```

$ ./deploy.sh
You must use sudo to run this script
$ sudo ./deploy.sh
Done.

```
If the user tries to use sudo and fails to authenticate, your script is not called. If sudo succeeds, then they are authenticated. If the user tries to execute the script without using sudo, then they get an error message. Isn't that what you want?

---

### Post by Mohan1289 on 2012-10-26
> **spjackson said:**
> ```

#!/bin/bash

id=$(/usr/bin/id -u)

if [ $id -ne 0 ] ; then
  echo "You must use sudo to run this script"
  exit 1
fi

# other stuff goes here...
# mv
# jboss things
# mysql things
# ...

echo Done.

``````

$ ./deploy.sh
You must use sudo to run this script
$ sudo ./deploy.sh
Done.

```If the user tries to use sudo and fails to authenticate, your script is not called. If sudo succeeds, then they are authenticated. If the user tries to execute the script without using sudo, then they get an error message. Isn't that what you want?

Thank you but how can i kill all the remaining processes except Jboss?? how is that possible normally we will check with 

ps ax | grep jboss 
and then by using kill -9 and their pid's we will kill them but how can i do this here??

since the pid's are dynamic how can i kill all except jboss?

---

### Post by Lars Noodén on 2012-10-26
Can you provide some sample output from ps that shows the processes you want to kill and the process(es) you don't want to kill?

Also, -9 is a bit heavy handed.  It would give the processes a chance to shutdown gracefully if a different signal were used.  [TERM](http://manpages.ubuntu.com/manpages/precise/en/man7/signal.7.html) is the default for kill, is it not working?

---

### Post by Mohan1289 on 2012-10-26
> **Lars Noodén said:**
> Can you provide some sample output from ps that shows the processes you want to kill and the process(es) you don't want to kill?

Also, -9 is a bit heavy handed.  It would give the processes a chance to shutdown gracefully if a different signal were used.  [TERM]("http://manpages.ubuntu.com/manpages/precise/en/man7/signal.7.html") is the default for kill, is it not working?

Sorry i will give the sample of process which i don't want to kill tomorow i don't know why i can't connect to server through ssh...

Why i said kill -9 is i don't know about the TERM signal... Thank you i will try that

---

### Post by Mohan1289 on 2012-10-29
> **Mohan1289 said:**
> Sorry i will give the sample of process which i don't want to kill tomorow i don't know why i can't connect to server through ssh...

Why i said kill -9 is i don't know about the TERM signal... Thank you i will try that

in this i don't want to kill last process jboss

---

### Post by Lars Noodén on 2012-10-29
Maybe you can check using [pgrep](http://manpages.ubuntu.com/manpages/precise/en/man1/pgrep.1.html) or pkill.  They can take a regex pattern and the -u option allows you to specify a user.

---

### Post by Mohan1289 on 2012-10-29
> **Lars Noodén said:**
> Maybe you can check using [pgrep]("http://manpages.ubuntu.com/manpages/precise/en/man1/pgrep.1.html") or pkill.  They can take a regex pattern and the -u option allows you to specify a user.

pardon i don't get can you please explain it to me... 

i want the script for all users(sudo's) i can'y specify a single user 

may be can i can specify a single process which i don't want to kill but i want to kill all the remaining processes is it possible??
 
i mean in the server the jboss server process id is static right?? since run's continuously without stopping


can i do that??

---

### Post by Lars Noodén on 2012-10-29
You might be able to do that.  Try experimenting with pgrep until the results show what you want and it excludes the jboss process.  Then you can apply the same syntax to pkill and have it kill the processes it finds.

---

### Post by Mohan1289 on 2012-10-29
> **Lars Noodén said:**
> You might be able to do that.  Try experimenting with pgrep until the results show what you want and it excludes the jboss process.  Then you can apply the same syntax to pkill and have it kill the processes it finds.

I will try

---

### Post by Mohan1289 on 2012-10-29
> **Lars Noodén said:**
> You might be able to do that.  Try experimenting with pgrep until the results show what you want and it excludes the jboss process.  Then you can apply the same syntax to pkill and have it kill the processes it finds.


but how can i display description too there is no option for Description..

---

### Post by Mohan1289 on 2012-10-29
> **Mohan1289 said:**
> but how can i display description too there is no option for Description..

Sorry i found it **-l **option is there which displays it's name

---

### Post by Lars Noodén on 2012-10-29
You could also pipe the output of ps through "grep -v" to exclude the jboss pattern.

---

### Post by Vaphell on 2012-10-29
pgrep/pkill support -v too, the problem is i don't think killing everything but the jboss process is a good idea, what about that crapton of system processes running?

---

### Post by Mohan1289 on 2012-10-31
> **codemaniac said:**
> You can use something like below in your shell script 

```

#!/bin/bash
ROOT_UID=0 # Only users with $UID 0 have root privileges.
E_NOTROOT=87 #Non-root exit error.

# Run as root, of course.
if [ "$UID" -ne "$ROOT_UID" ]
then
echo "Must be root to run this script."
exit $E_NOTROOT
fi
```


I got an error when i run this script i can't say it's an error it's a warning i think 
It's saying 
[B]
$sh test.sh 
test.sh: 6: test.sh: if[: not found
You Must be root to run this script
[/B]
The script contains nothing but what you told me
[B]
#!/bin/bash
#Only Sudo can run the script
ROOT_UID=0 #Since Only users with $UID 0 have root privileges
E_NOTROOT=87 #Non-root Exit Error

if["$UID" -ne "$ROOT_UID"]; then
echo "You Must be root to run this script"
exit $E_NOTROOT
fi[/B]

Can you please tell me what's the error where am i mistaken?

---

### Post by Vaphell on 2012-10-31
you need spaces there
```
[[COLOR="Blue"]_[/COLOR]"$UID"[COLOR="Blue"]_[/COLOR]-ne[COLOR="Blue"]_[/COLOR]"$ROOT_UID"[COLOR="Blue"]_[/COLOR]]
```
think of it as command **[** that gets parameters:
$uid
-ne
$root_uid
]
obviously parameters can't be glued together


also don't call shell explicitly, you override hashbang line. It says 'run using bash' but you tell 'forget that, run using sh'
make it executable and run it by its name
```
chmod +x script
./script
```

---

### Post by Mohan1289 on 2012-10-31
> **Vaphell said:**
> you need spaces there
```
[[COLOR=Blue]_[/COLOR]"$UID"[COLOR=Blue]_[/COLOR]-ne[COLOR=Blue]_[/COLOR]"$ROOT_UID"[COLOR=Blue]_[/COLOR]]
```think of it as command **[** that gets parameters:
$uid
-ne
$root_uid
]
obviously parameters can't be glued together


also don't call shell explicitly, you override hashbang line. It says 'run using bash' but you tell 'forget that, run using sh'
make it executable and run it by its name
```
chmod +x script
./script
```

It's the same when i applied executive permission it's displaying 
[B]
./test.sh: line 6: syntax error near unexpected token `then'
./test.sh: line 6: `if[ "$UID" -ne "$ROOT_UID" ]; then'

[/B]and it is showing same when i am running as root like

[B]su 
password
[/B]
or 

**sudo sh test.sh**

evn so it's displaying the same out put i am uploading a Screen shot.
Can you tell me where i am wrong??

---

### Post by Vaphell on 2012-10-31
well, you don't get syntax highlighting on **if** while it's on **then** and **fi**, and you get '**if[** not found' - what does it tell you? ;-)

---

### Post by Mohan1289 on 2012-10-31
> **Vaphell said:**
> well, you don't get syntax highlighting on **if** while it's on **then** and **fi**, and you get '**if[** not found' - what does it tell you? ;-)

do i have to give space?

yes that's it i got it thank you vaphell

---

