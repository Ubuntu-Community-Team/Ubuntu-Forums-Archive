---
title: "What is the each command's different merit between su and sudo?"
date: 2020-03-18
forum: New to Ubuntu
---

### Post by Captain Cookie on 2020-03-18
At a BSD discussion board,
I know this thing that 
some BSD users prefer su command.


I know the su command permits 
the user become one like the superuser
until inputting the exit command.


The su and sudo command,
I want to each own merits and demerits!

---

### Post by malspa on 2020-03-18
Seriously, your best bet is to type something like ***su vs sudo*** in a web search engine and then start reading. You'll find tons of info on this topic.

---

### Post by yancek on 2020-03-18
The Ubuntu site has documentation on this and also includes Advantages/Disadvantages of using sudo so that would be your best place to start.

[https://help.ubuntu.com/community/RootSudo](https://help.ubuntu.com/community/RootSudo)

---

### Post by TheFu on 2020-03-18
man su
man sudo

It is all about the options, timeframe, which password is needed, security, groups, and flexibility.
If you want to allow someone to run 1 command with exactly x, y, z options and nothing else, then su doesn't allow that.  **sudo** does.
If you want to change the current userid into joesuser because you are joesuser to access some of your files while using a terminal window on a workstation someone else is using, then sudo won't allow that. Only **su - joesuser** will work.

In a typical environment today, sudo provides all the capabilities that any home user would need, plus logging of all sudo run  commands, so sudo would be the less complex choice.  Plus, **sudoedit** is the best, safest, way I know to edit system files.  Every time I see some article somewhere with *sudo gedit* I cringe a little.  Doing that can break a system, if the userid running it hadn't already used gedit before WITHOUT sudo.  Actually, this applies to almost any GUI program and sudo or su.  In general, don't use either with GUI programs is the best advice.  Sure, there are exceptions and techniques to get around the issues caused, but noob-users need to learn much more BEFORE those exceptions can make sense.

---

### Post by kevdog on 2020-03-18
My only take on the matter is I once found a problem when working with acme.sh when install let's encrypt certificates.  The process would work when run under the su user.  With sudo -- the process totally flopped.  I filed a bug and never heard back.  All this told me was the process isn't interchangeable for some reason.

---

### Post by TheFu on 2020-03-18
> **kevdog said:**
> My only take on the matter is I once found a problem when working with acme.sh when install let's encrypt certificates.  The process would work when run under the su user.  With sudo -- the process totally flopped.  I filed a bug and never heard back.  All this told me was the process isn't interchangeable for some reason.

I use acme.sh too.  sudo works with it, just requires the --force option for acme.sh.  The idea that someone can install certs to be used on a web server, but not have elevated privileges is just wrong. Exactly how do they expect certs to be deployed without root?  My only guess is they expect people to be on hosted, shared, web servers where they control certs but not apache.

Exactly how should I deploy a cert without root, here?
```
/etc/nginx/ssl/blog.jdpfu.com$ ll
total 20
**drwxr-xr-x  2 [B]root** root 4096 Jun  6  2019 .
[/B]drwxr-xr-x 14 **root** root 4096 Jun 11  2019 ..
**-rw-r--r--**  1 **root** root 1907 Mar  3 13:00 cert.pem
**-rw-r--r--**  1 **root** root 3555 Mar  3 13:00 fullchain.pem
**-rw-------**  1 **root** root 1675 Mar  3 13:00 key.pem

```
Then restart/reload nginx without root?
How?

---

### Post by Tadaen_Sylvermane on 2020-03-18
For a personal perspective I prefer sudo. I like temporary escalation vs potential full time. That being said where Ubuntu is concerned anyone in the sudo group is effectively capable of anything as root. I'm not sure if that extends to other distros use of sudo. Sudo can be tailored for specific commands via configuration. Su is just su with no real control except keeping the password secret.

---

### Post by TheFu on 2020-03-18
Many people don't know that elevating for root isn't the only purpose for these commands.  They are useful to change to other userids on the system. Linux, like all Unix systems, is multi-user from the ground up.  Processes run under different userid constantly. Not all are either root nor our personal accounts.  To manage those processes, we need the ability to become the other userid from time to time.

```
su              ==  sudo -s   # keep current env
su -            ==  sudo -i   # get new login env for the target userid
su -l www-data  ==  sudo -u www-data
```

But the real difference is which password gets typed in.
With sudo, it is the current userid's password.
With su, it is the target userid's password (unless you are already root).

So changing to the www-data userid, is 1-step easier using sudo than the 2-steps su requires.

---

### Post by kevdog on 2020-03-20
> **TheFu said:**
> I use acme.sh too.  sudo works with it, just requires the --force option for acme.sh. 

Well that's just ducky.  Using the --force option isn't ideal since its possible to overwrite things without warning. 

Is it possible to activate the su user on Ubuntu?  I know there are security warnings about this, however how dangerous could this be when BSD distributions have the su user installed by default.  Sometimes I don't understand why decisions like these are made.

---

### Post by TheFu on 2020-03-21
> **kevdog said:**
> Well that's just ducky.  Using the --force option isn't ideal since its possible to overwrite things without warning. 

Is it possible to activate the su user on Ubuntu?  I know there are security warnings about this, however how dangerous could this be when BSD distributions have the su user installed by default.  Sometimes I don't understand why decisions like these are made.

I prefer the sudo method. Fewer passwords to remember. Logging of commands.  Plus we can switch to any user needed using sudo, so there really isn't any need for su or su - .

*su user* already works in the normal, expected, way. It is only for the root userid where it doesn't work. It is an artifact that root doesn't have a password on ubuntu. Nothing else.

Lots of Linux distros don't for the use of sudo like Ubuntu does.  All the RHEL-based releases use su and a root account.  Sadly, they enable remote root logins too, which is a terrible security failure almost always. There are a few other security reasons for the root account to only be accessible using sudo.  Best for the uninformed to stick with sudo. Enabling direct root access has many negative side-effects that are better avoided.

As for acme.sh --force option overwriting things.  That's why we have daily, automatic, versioned, backups that are "pulled", not "pushed".  Right?!!! Something gets overwritten that breaks anything, just put the files back from the backup last night. 10 seconds of our time.  It isn't like someone running a website, using HTTPS, wouldn't have backups.  No way that could happen.  /s

---

### Post by kevdog on 2020-03-21
There are many ways to skin the cat.  I just don't like the --forced option due to the lack of the root user.  How backups are performed is kind of redirecting the argument here.

---

### Post by TheFu on 2020-03-21
> **kevdog said:**
> There are many ways to skin the cat.  I just don't like the --forced option due to the lack of the root user.  How backups are performed is kind of redirecting the argument here.

There's no difference in the result from acme.sh with sudo vs root provide we are consistent about using 
```
$ sudo acme.sh
```
or
```
$ sudo -H acme.sh
```
Consistency is the key.

We've probably highjacked this thread too much already.

---

### Post by kevdog on 2020-03-22
@TheFu

Agreed. No more hijacking.

---

### Post by Doug S on 2020-03-22
I will use "su" mode instead of the "sudo" command prefix when attempting to delete many many root owned files in one command.
Why, because "sudo" has an arbitrary, and rather low, limit on the argument list.

Example: 10,000 root owned files:
```
doug@s15:~/sudo/test$ ls -l | head
total 40000
-rw-r--r-- 1 root root 1024 Mar 22 09:07 ab00000000.txt
-rw-r--r-- 1 root root 1024 Mar 22 09:07 ab00000001.txt
-rw-r--r-- 1 root root 1024 Mar 22 09:07 ab00000002.txt
-rw-r--r-- 1 root root 1024 Mar 22 09:07 ab00000003.txt
...

```

Try to delete using "sudo":

```
doug@s15:~/sudo/test$ [COLOR="#FF0000"]sudo rm *[/COLOR]
sudo: unable to execute /bin/rm: Argument list too long

```Now, delete using "su" to become root:
```
doug@s15:~/sudo/test$ sudo su
root@s15:/home/doug/sudo/test# [COLOR="#FF0000"]rm *[/COLOR]
root@s15:/home/doug/sudo/test# exit
exit
doug@s15:~/sudo/test$
```note that even root (and normal users, for their owned files) has an argument list limit, it's just way bigger.
Example (100,000 files):
```
root@s15:/home/doug/sudo/test# [COLOR="#FF0000"]rm *[/COLOR]
bash: /bin/rm: Argument list too long
root@s15:/home/doug/sudo/test#
```
While not really relevant, my real life example is my tcpdump capture logs, at 10 minutes per file internal and external interfaces, which I tend to only post process every couple of months, thus I end up with thousands of files:
```
-rw-r--r-- 1 root root  65534352 Mar 22 08:47 ext-2020-03-22-08-37-59.bin
-rw-r--r-- 1 root root 516828264 Mar 22 08:57 ext-2020-03-22-08-47-59.bin
-rw-r--r-- 1 root root 515930193 Mar 22 09:07 ext-2020-03-22-08-57-59.bin
-rw-r--r-- 1 root root 536203868 Mar 22 09:17 ext-2020-03-22-09-07-59.bin
-rw-r--r-- 1 root root 323516146 Mar 22 09:28 ext-2020-03-22-09-17-59.bin
-rw-r--r-- 1 root root     81920 Mar 22 09:29 ext-2020-03-22-09-28-01.bin
```

---

### Post by TheFu on 2020-03-22
xargs --max-lines=128000
or 
xargs  --max-chars=4096
will send chunks of arguments to the command.

[https://www.gnu.org/software/findutils/manual/html_node/find_html/Limiting-Command-Size.html](https://www.gnu.org/software/findutils/manual/html_node/find_html/Limiting-Command-Size.html)

---

### Post by Captain Cookie on 2020-03-23
Hello!

Thank you for reply may times!

I've read them.

Finishing checking, I will post about what I learn with a lot comments!

---

### Post by Captain Cookie on 2020-03-23
Hello malspa!
Do you use both of command?

I want to know subjective and objective,
both opinions.

Thank you for first comment!

---

### Post by Captain Cookie on 2020-03-23
I appreciate showing the most reliable page,  yancek!

The part "Advantages and Disadvantages" seems suit
my question perfectly.

Thank you!

---

### Post by Captain Cookie on 2020-03-23
> **TheFu said:**
> 
**sudoedit** is the best, safest, way I know to edit system files.  Every time I see some article somewhere with *sudo gedit* I cringe a little.  Doing that can break a system, if the userid running it hadn't already used gedit before WITHOUT sudo.  Actually, this applies to almost any GUI program and sudo or su.  In general, don't use either with GUI programs is the best advice.  Sure, there are exceptions and techniques to get around the issues caused, but noob-users need to learn much more BEFORE those exceptions can make sense.

I understand that
Basically, it is better not to use su and sudo command with GUI programms.  
And sudoedit is the best way to edit system files.

In other topic, how to allow users run su command in BSD,
some comment shows certain better way to changing 
cunfiguration as well as you showed me.

I will break my system without such advice.

Thank you, TheFu!

---

### Post by Doug S on 2020-03-24
> **TheFu said:**
> xargs --max-lines=128000
or 
xargs  --max-chars=4096
will send chunks of arguments to the command.

[https://www.gnu.org/software/findutils/manual/html_node/find_html/Limiting-Command-Size.html](https://www.gnu.org/software/findutils/manual/html_node/find_html/Limiting-Command-Size.html)I was just trying to reply to the question, but thanks. However, I am always wanting to learn more, but so far haven't been able to use xargs to overcome the issue. Note sure what I'm doing wrong.

EDIT: (I stopped being so lazy) This seems to work for 200,000 root owned files:
```
ls | xargs rm
```However, it can have issues also:
```
doug@s15:~/sudo/test$ ls *.txt | xargs rm
-bash: /bin/ls: Argument list too long
rm: missing operand
Try 'rm --help' for more information.
doug@s15:~/sudo/test$

```which can be solved by, for example:
```
printf '%s ' *.txt | xargs rm
```
however, if I try:
```
doug@s15:~/sudo/test$ printf '%s ' *.txt | xargs sudo rm
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long
sudo: unable to execute /bin/rm: Argument list too long

``` it doesn't work because the default list limit is too long, as per my original issue with sudo.But, and as the fu suggested, this works:
```
doug@s15:~/sudo/test$ printf '%s ' *.txt | xargs --max-procs=6 --max-args=1000 sudo rm
doug@s15:~/sudo/test$ ls -l
total 0

```

---

### Post by kevdog on 2020-03-27
```
 doug@s15:~/sudo/test$ printf '%s ' *.txt | xargs --max-procs=6 --max-args=1000 sudo rm 
```

Seems like a lot of extra overhead here -- honestly it just seems easier to become the root user and and do a simple rm command.

---

### Post by Doug S on 2020-03-27
> **kevdog said:**
> ```
 doug@s15:~/sudo/test$ printf '%s ' *.txt | xargs --max-procs=6 --max-args=1000 sudo rm 
```

Seems like a lot of extra overhead here -- honestly it just seems easier to become the root user and and do a simple rm command.Yes, agreed. However that particular example was for when even that doesn't work, because the number of files even exceeds the regular (not sudo) limit. Example (200,000 .txt files and 6 .save files that I want to keep):

```
root@s15:/home/doug/sudo/test# ls -l | wc -l
200006
root@s15:/home/doug/sudo/test# rm *.txt
bash: /bin/rm: Argument list too long
root@s15:/home/doug/sudo/test#
root@s15:/home/doug/sudo/test# printf '%s ' *.txt | xargs --max-procs=6 --max-args=1000 rm
root@s15:/home/doug/sudo/test# ls -l | wc -l
6
root@s15:/home/doug/sudo/test#

```
EDIT: at the risk of self embarrassment, here is the script I use for to remove the files after my many many files types tests. The old way is still there, but commented out:

```
doug@s15:~/c$ cat rm_many_files
#!/bin/dash

# rm_many_files 2020.03.24.
#       Seems I should have been using xargs
#       for this all along.
#
# rm_many_files 2019.05.26.
#       Add some progress feedback.
#       Try other, faster, method.
#
# rm_many_files 2018.08.19.
#       Someimtes, for tests, I have so many files
#       that rm doesn't work due to "Argument list too long"
#       break it doen into smaller chunks.

# COUNTER2=0
# while [ $COUNTER2 -lt 10 ];
# do
#   COUNTER1=0
#   while [ $COUNTER1 -lt 10 ];
#   do
#     echo "Deleting: *$COUNTER2$COUNTER1???.txt"
# #   time rm *$COUNTER2$COUNTER1.txt
# #   time find . -name "*$COUNTER2$COUNTER1.txt" -delete
#     time rm *$COUNTER2$COUNTER1???.txt
#     COUNTER1=$(($COUNTER1+1))
#   done
#   COUNTER2=$(($COUNTER2+1))
# done

printf '%s ' *.txt | xargs --max-procs=6 --max-args=1000 rm

```

---

### Post by Captain Cookie on 2020-03-31
Hi!
 
I finished reading many pages,
then I have come back now!


What I understood that...


·Running as always the root privilege user is
 extreamly dangerous, so Ubuntu does not allow
 the user use the root account in default.  


·In default, the user can not use su command,
 because the root account is not made in 
 the installation.
 
·The root account does not exist in default,
 so it has no possibility to be taken over
 by anybody. 


.sudo requires the users to type THEIR OWN password.
 It is cashed for 15minutes, which could be changed
 for the user's preference.


·In Linux, users do not use su command,
 but sudo. It is better to carefully run
 command after sudo, though it expires in 
 15 minutes, but during that time the novice
 use  may run destructive commands.


·sodo leaves log that tells the users
 what they have done, which is useful for
 troubleshooting.


****

To kevdog


Thank you for tell me your experience!


In some case, two commands are not 
interchangeable.


The each power is sometimes different
between sudo and su.


It is a interesting point!


***


To Tadaen_Sylvermane


Thank you for a subjective opinion!


Su allows the users do anything,
but sudo could be limited for 
the range on the situation.


Very important point for deploying
the Linux machine.



***


To TheFu #8 #10 Reply
         


A document I read says
same as you tell me.


The sudo is also good to 
manage user accounts.


Short procedure, better for
the long run manage.


"Lots of Linux distros don't 
for the use of sudo like Ubuntu does."
from #10 reply


I knew the new fact that in the RHEL family
the user use su. 
Does Ubuntu go along the more secure way?
It is nice!

***
  
I will also reply for others next time!
Thank you, the members of the community for a lot of supports!

---

### Post by Doug S on 2020-03-31
> **Captain Cookie said:**
> ·In default, the user can not use su command,
 because the root account is not made in 
 the installation.Incorrect. The default user, the one made during the install, will be in the sudo'ers list and can use the su command.
 
> **Captain Cookie said:**
> ·The root account does not exist in default,
 so it has no possibility to be taken over
 by anybody. Incorrect. It exists, but you can not login as root directly.

---

### Post by sisco311 on 2020-03-31
If you want to know the differences between su and sudo, then start with the basics.

Start learning about Unix/Linux file permissions (including setuid bits). 

Did you know that a simple `ping' command must run as root? Or when you change your password you are escalating your privileges to root!

Most people on a modern Unix/Linux distro don't even realize when they are acting as root.


And there is PAM and polkit ....

---

### Post by Doug S on 2020-03-31
> **sisco311 said:**
> Did you know that a simple `ping' command must run as root?Disagree.

Example:

```
doug@s18:/media[COLOR="#FF0000"]$[/COLOR] ping google.com
PING google.com (172.217.3.174) 56(84) bytes of data.
64 bytes from sea15s11-in-f14.1e100.net (172.217.3.174): icmp_seq=1 ttl=57 time=21.8 ms
64 bytes from sea15s11-in-f14.1e100.net (172.217.3.174): icmp_seq=2 ttl=57 time=22.2 ms
64 bytes from sea15s11-in-f14.1e100.net (172.217.3.174): icmp_seq=3 ttl=57 time=22.1 ms
64 bytes from sea15s11-in-f14.1e100.net (172.217.3.174): icmp_seq=4 ttl=57 time=22.2 ms
^C
--- google.com ping statistics ---
4 packets transmitted, 4 received, 0% packet loss, time 3004ms
rtt min/avg/max/mdev = 21.763/22.057/22.168/0.170 ms

```

---

### Post by Captain Cookie on 2020-06-25
Thank you, Doug S!
Now I have checked replies.  
I have assumed that ubuntu does not make the root account. 
But Just impossible to log in directly. 
I got it!

---

### Post by Captain Cookie on 2020-06-25
Hello, sisco311.


I have learnt command and scripts from scratch. People around me, nobody uses any Linux and Unix-like OS, so the community is only one that I can rely on.


Thank you!

---

### Post by ActionParsnip on 2020-06-25
> **TheFu said:**
> man su
man sudo

It is all about the options, timeframe, which password is needed, security, groups, and flexibility.
If you want to allow someone to run 1 command with exactly x, y, z options and nothing else, then su doesn't allow that.  **sudo** does.
If you want to change the current userid into joesuser because you are joesuser to access some of your files while using a terminal window on a workstation someone else is using, then sudo won't allow that. Only **su - joesuser** will work.

In a typical environment today, sudo provides all the capabilities that any home user would need, plus logging of all sudo run  commands, so sudo would be the less complex choice.  Plus, **sudoedit** is the best, safest, way I know to edit system files.  Every time I see some article somewhere with *sudo gedit* I cringe a little.  Doing that can break a system, if the userid running it hadn't already used gedit before WITHOUT sudo.  Actually, this applies to almost any GUI program and sudo or su.  In general, don't use either with GUI programs is the best advice.  Sure, there are exceptions and techniques to get around the issues caused, but noob-users need to learn much more BEFORE those exceptions can make sense.

sudo vi file

Too safe?

---

### Post by ActionParsnip on 2020-06-25
> **Captain Cookie said:**
> Thank you, Doug S!
Now I have checked replies.  
I have assumed that ubuntu does not make the root account. 
But Just impossible to log in directly. 
I got it!

There is a root account. It's just disabled for logins

---

### Post by TheFu on 2020-06-25
> **Doug S said:**
> Disagree.


Well, the permissions for ping disagree:
```
$ ll -F /bin/ping
-rw**s**r-xr-x 1 root root 44168 May  7  2014 /bin/ping*

```
ping always runs with root privilege as shown by the permissions. it is a setuid program.

---

### Post by TheFu on 2020-06-25
**sudoedit** can be configured to use any editor you prefer, including GUi editors.  it is extremely safe to do that if you like.

Many admin commands really need to become habits to keep us from making mistakes.  sudoedit is one of those habits to re-re-re-enforce as much as possible.

The main reason to avoid using gui programs with sudo are because most guis have a bad habit of automatically saving config files without asking.   nano, vim and pretty much every non-gui program doesn't misbehave in that way. 

 if you can always remember to use **sudo -H {gui-program} **then those problems can be avoided, but screw up once and you could end up with an account that doesn't let you login.  With enough experience, that problem is a minor inconvenience. For someone without experience, it probably seems like the entire system is broke and useless.  it is all about file and directory permissions which are foreign ideas to most new users coming from Windows.

---

### Post by Captain Cookie on 2020-06-26
Hello, ActionParsnip.
Although this thread is old one, you have checked and replied. 
Thank you! 


I heard Ubuntu is different to handling the root account from other distributions.


Others allow users freely to log in as the root, don't  they?

---

### Post by Doug S on 2020-06-26
> **TheFu said:**
> Well, the permissions for ping disagree:
```
$ ll -F /bin/ping
-rw**s**r-xr-x 1 root root 44168 May  7  2014 /bin/ping*

```
ping always runs with root privilege as shown by the permissions. it is a setuid program.

My response was in reply to this:

> Did you know that a simple `ping' command must run as root? 

And I stand by the statement, and your own permissions example shows executable by anyone.
And just try it, no sudo or root required. Example, with no "sudo" and not from a root prompt:

```
doug@s15:~/c$ ping google.com
PING google.com (216.58.193.78) 56(84) bytes of data.
64 bytes from sea15s07-in-f14.1e100.net (216.58.193.78): icmp_seq=1 ttl=120 time=22.1 ms
64 bytes from sea15s07-in-f14.1e100.net (216.58.193.78): icmp_seq=2 ttl=120 time=21.7 ms
64 bytes from sea15s07-in-f14.1e100.net (216.58.193.78): icmp_seq=3 ttl=120 time=21.9 ms
```

I realize that the "s" (setuid) means set user ID upon execution, but fail to see the relevance to the question.

---

### Post by TheFu on 2020-06-26
That's odd. In 20.04, ping isn't setuid root.
```
-rw_x_r-xr-x 1 root root 72776 Jan 30 18:11 ping*

```
[https://www.reddit.com/r/linuxquestions/comments/aaqnat/why_does_sbinping_needhave_setuid_typically_root/](https://www.reddit.com/r/linuxquestions/comments/aaqnat/why_does_sbinping_needhave_setuid_typically_root/) says they are using **setcap cap_net_raw+ep /bin/ping** to allow ping to work without being setuid.  VERY Cool.
```
$ getcap /bin/ping
/bin/ping = cap_net_raw+ep
```

Since the beginning of Unix (pre-1980), ping has been setuid root.  I don't have an 18.04 system, so cannot check that, but on 16.04 the permissions most definitely are:
```
$ ll /bin/ping
-rw_s_r-xr-x 1 root root 44168 May  7  2014 /bin/ping*
```

So no **su** or **sudo** is needed, however that is because the ping command has "setuid root" file permissions.  Take those away and it won't work. Ping runs with the "effective userid of root".  The internal Unix process table has both the real (RUID) and the effective (EUID) userid.  There's even a way to check when those are different. The "effective" owner of the process is 'root', not our userid for a microsecond.  

Use this ps command to see the RUID and EUID
```
$ ps -eo euser,ruser,suser,fuser,f,comm,label |egrep 'ping|LABEL'
EUSER    RUSER    SUSER    FUSER    F COMMAND         LABEL
tf       tf       **root**     tf       4 **ping**            unconfined

```
Just like apache and nginx, ping "drops privilege" from root ASAP, which is why root is in the saved userid column.  It starts up as EUID=root, opens the privileged network access, then drops back to the original userid.  Any program connecting to any port under 0-1024 should do this. It is well-documented. Ping is just another one of those tools.

[https://en.wikipedia.org/wiki/Setuid](https://en.wikipedia.org/wiki/Setuid)
> Some of the tasks that require additional privileges may not immediately be obvious, though, such as the **ping** command, which must send and listen for control packets on a network interface. 
Appears a wikipedia editor should update that entry to reflect current ping using _cap_net_raw+ep_ capabilities.  All because the NSA wanted a more secure system and helped RH create SELinux. Perhaps not. Perhaps the kernel team was just following what commercial UNIX vendors had been adding since early Solaris releases.

I learned a bunch of new stuff today. Thanks for the discussion.

---

### Post by Doug S on 2020-06-26
> **TheFu said:**
> I learned a bunch of new stuff today. Thanks for the discussion.Likewise. Thanks for taking the time to do the research and writing it up for all of us.

---

### Post by Impavidus on 2020-06-27
> **ActionParsnip said:**
> sudo vi file

Too safe?

**sudoedit file** will copy the file to a temporary location, then run the text editor as the normal user and after closing the editor, will copy the (modified) file back. Only the copy operation needs root permissions.
**sudo vim file** will run the entire text editor as the root user. This means that the user can now edit other files as well and can even start a root shell. A user who can run **sudo vim file** can do everything on a system.

---

### Post by TheFu on 2020-06-27
> **Impavidus said:**
> **sudoedit file** will copy the file to a temporary location, then run the text editor as the normal user and after closing the editor, will copy the (modified) file back. Only the copy operation needs root permissions.
**sudo vim file** will run the entire text editor as the root user. This means that the user can now edit other files as well and can even start a root shell. A user who can run **sudo vim file** can do everything on a system.

That's 1 example, but humans are crafty. Gotta learn to think like a hacker to understand _some_ of the ways sudo can be abused. There are ALWAYS other methods.  Always. 

As the sudo people create mitigations against 1 potential abuse method, others are found.  sudoedit only leaves 1 thing - the copy and file permission+ownership - as risks, not hundreds of ways that any arbitrary editor can be abused.  Sudoers can be limited against running editors, for example, have been known to just copy the editor to a different name+location, then use sudo with that alternate.  Or change their PATH. Or ... 50+ other methods.

As stated above, it is best just to get into the habit of using sudoedit.  Plus we get to choose any EDITOR we like and don't have any risks with the editor creating config files (and directories) as root in the wrong places.

---

### Post by sisco311 on 2020-06-28
> **Captain Cookie said:**
> 
I heard Ubuntu is different to handling the root account from other distributions.


Others allow users freely to log in as the root, don't  they?

Not sure what do you mean by logging in, but as far as know, by default, non of the mainstream display(/login) managers will allow you to start a GUI session as root (by default).

---

### Post by The Cog on 2020-06-28
I don't think others allow login to a graphical desktop as root. But lots of other distros to allow login as root either on a text console or on a remote ssh session.
On Ubuntu, it is the fact that root's password is disabled by default that prevents login as root. It is of course possible to set a valid password, or configure password-less login to root using ssh keys.
And there are lots of system processes running as root even though user login as root is not possible because the password is disabled.

---

