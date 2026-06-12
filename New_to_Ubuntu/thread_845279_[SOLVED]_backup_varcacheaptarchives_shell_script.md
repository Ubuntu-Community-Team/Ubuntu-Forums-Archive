---
title: "[SOLVED] backup /var/cache/apt/archives shell script"
date: 2008-06-30
forum: New to Ubuntu
---

### Post by meindian523 on 2008-06-30
Hi,
I'm trying to create a shell script,to be later added to cron,to tar and bzip /var/cache/apt/archives to an archive in my home folder.I got to this

```
#!/bin/bash

date>>$0
sudo sh -c "cd /var/cache/apt/archives && tar -cf *.deb /home/easwarh/$0 && bzip2 -z /home/easwarh/"$0.tar" "
sudo apt-get clean
```

after perusing the man pages for sudo,tar and bzip2,but I've some doubts.

1]How can I bypass having to authenticate by giving my password?[OR] is sudo needed at all?
2]Is $0,$1....$n exclusively for numbers?If yes,what variables can we use to store strings like the ones output by date?

Some background info for Q2.
I ran this script and I got this:

```
easwarh@l1nuxr0cks:~/Desktop$ ./try1
[sudo] password for easwarh: 
tar: Removing leading `/' from member names
tar: /home/easwarh/./try1: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
./try1: line 8: Mon: command not found
easwarh@l1nuxr0cks:~/Desktop$ 

```
Also,running the script adds the current date and time to the script file.Why is this and how do I get rid of this problem?

Thanks for any help in advance.

---

### Post by Inxsible on 2008-06-30
you can bypass having to give your password in multiple ways.

1)by putting the script in the root's cronjob instead of the users and using /usr/bin/tar as the command instead of just tar. Same for bzip2

2)by adding yourself to the sudoers and allowing NOPASSWD access to tar and bzip commands

---

### Post by Inxsible on 2008-06-30
to do the 2nd option. Open up a terminal and type in ```
su
``` Supply the root password and then type in ```
visudo
```At the bottom add the line```
 *your-username* ALL = (ALL) NOPASSWD: /usr/bin/tar, /usr/bin/bzip2, /usr/bin/apt-get
```Save the file. That should do it.

---

### Post by meindian523 on 2008-06-30
Thanks,what about the variable errors?I want to create the archive with the filename as the date on which it was created.Atleast,that's my objective.

EDIT:Suppose,I use the first option,will I have to be logged in as root before the cron job will run?

---

### Post by Inxsible on 2008-06-30
> **meindian523 said:**
> ....[snip]
EDIT:Suppose,I use the first option,will I have to be logged in as root before the cron job will run?No

---

### Post by geirha on 2008-06-30
1. You have write access to /home, and /var/cache/apt/archives should be readable to all, so you do not need sudo for that part, though the apt-get clean command needs root privileges.

A comment on this one:
```
tar -cf *.deb /home/easwarh/$0
```
$0 is the name of the bash-script, which is apparently try1. $1 is the first argument to the script and $2 is the second etc. And on the tar-command itself, after the -f option, then next file should be the name of the tar. You got *.deb there, so the first deb-file that *.deb expands to have now been overwritten with a tar archive. This might reveal which package has been overwritten:```
file /var/cache/apt/archives/*.deb
```

I'm guessing you want the tar file named as the date? "date>>$0" will append the date to the bottom of your script. Try:
```
filename=$(date +%Y-%m-%d)   # $filename will now be something like 2008-06-30
( cd /var/cache/apt/archives; tar -cjf "$HOME/$filename.tar.bz2" *.deb ) && sudo apt-get clean

```

---

### Post by Inxsible on 2008-06-30
you may wanna get rid of the sudo in front of the commands if you are gonna put this in the root's cron.

You might also want to add the -qy options for apt-get clean so that it assumes Yes and is quiet. That is what a cronjob should have. It should not wait on a user input.```
apt-get -qy clean
```or ```
apt-get -qy autoclean
```

---

### Post by meindian523 on 2008-06-30
> **geirha said:**
> 1. You have write access to /home, and /var/cache/apt/archives should be readable to all, so you do not need sudo for that part, though the apt-get clean command needs root privileges.

A comment on this one:
```
tar -cf *.deb /home/easwarh/$0
```
$0 is the name of the bash-script, which is apparently try1.
Yup.That's it.And I was thinking about using $1,but I remembered seeing $0 somewhere in a shell script and reasoned that variables must be counting from zero.
> **geirha said:**
> 
 $1 is the first argument to the script. And on the tar-command itself, after the -f option, then next file should be the name of the tar. You got *.deb there, so the first deb-file that *.deb expands to have now been overwritten with a tar archive. This might reveal which package has been overwritten:```
file /var/cache/apt/archives/*.deb
```

I'm guessing you want the tar file named as the date? "date>>$0" will append the date to the bottom of your script. Try:
Hmm,thanks.I will try that and get back.Actually,the overwriting is not a problem,since I already had my archives backed up,I was trying to avoid the work of doing it manually again and again.
> **geirha said:**
> 
```
filename=$(date +%Y-%m-%d)   # $filename will now be something like 2008-06-30
( cd /var/cache/apt/archives; tar -cjf "$HOME/$filename.tar.bz2" *.deb ) && sudo apt-get clean

```

Ok,we don't need to run bzip2 as a separate command?

---

### Post by meindian523 on 2008-06-30
I tried sudo apt-get clean in a terminal,and it didn't wait for any user input,so I think the -qy options are redundant.

---

### Post by geirha on 2008-06-30
> **meindian523 said:**
> Ok,we don't need to run bzip2 as a separate command?

The -j option to tar filters it through bzip2. Likewise, the -z option filters it through gzip. 

If you intend to run this from root's crontab (which is a logical thing to do), then $HOME in my code-snippet above will expand to root's homedir, which is /root. So change it to wherever you actually want the archive to go.

---

### Post by meindian523 on 2008-06-30
hmmm,thanks.

---

### Post by meindian523 on 2008-06-30
The script now looks like this:
```
#!/bin/bash

filename=$(date +%d-%m-%Y)
cd /var/cache/apt/archives && tar -cf /home/easwarh/$filename *.deb && bzip2 -z /home/easwarh/"$filename.tar"

apt-get clean
```

and I get something different now.Progress?I'm not sure.

```
easwarh@l1nuxr0cks:~/Desktop$ ./try1 
tar: *.deb: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
easwarh@l1nuxr0cks:~/Desktop$ 
```

---

### Post by meindian523 on 2008-06-30
I don't understand why tar is looking for *.deb,* is a wildcard character which takes everything in it's ambit,doesn't it?And looks like the lock needs me to be root before cleaning or tarring is allowed.

---

### Post by meindian523 on 2008-06-30
Also the sudoers file looks like this:
```

easwarh@l1nuxr0cks:~$ s cat /etc/sudoers 
# /etc/sudoers
#
# This file MUST be edited with the 'visudo' command as root.
#
# See the man page for details on how to write a sudoers file.
#

Defaults	env_reset

# Uncomment to allow members of group sudo to not need a password
# %sudo ALL=NOPASSWD: ALL

# Host alias specification

# User alias specification

# Cmnd alias specification

# User privilege specification
root	ALL=(ALL) ALL

# Members of the admin group may gain root privileges
%admin ALL=(ALL) ALL
easwarh ALL=(ALL) NOPASSWD: /usr/bin/apt-get

```

---

### Post by geirha on 2008-06-30
> **meindian523 said:**
> I don't understand why tar is looking for *.deb,* is a wildcard character which takes everything in it's ambit,doesn't it?And looks like the lock needs me to be root before cleaning or tarring is allowed.
Yes, apt-get needs to be run as root, so if you run this script as your user, you'll need the sudo infront.

Are there any files in /var/cache/apt/archives? If there are any deb-files, *.deb will be replaced by a space seperated list of those files, then given to the tar command as arguments. If there are no deb-files, it will simply send "*.deb" as a string.

You can do a simple check in the script, and exit if there are no files to archive. ls will return false if it does not find any files ...
```
ls /var/cache/apt/archives/*.deb &>/dev/null || exit 0
```

Oh, and lastly, you got «tar -cf /home/easwarh/$filename *.deb» and then «bzip2 -z /home/easwarh/"$filename.tar"». There's a mismatch there. tar creates $filename, while bzip looks for $filename.tar ...

---

### Post by meindian523 on 2008-06-30
Oh,tar doesn't automatically add tar to it's tarball?I thought it did.And true,there are no deb files in the cache.Could you explain this part please?
```
&>/dev/null || exit 0
```
I know /dev/null is an infinite sink but what kind of operator is &> and what does it do?And why is there a double pipe?

EDIT:And oh,there will never be zero files in the archive because I plan to cron this job every 100 days.

---

### Post by geirha on 2008-06-30
A tar file doesn't need to end with .tar ...

&> /dev/null is the same as >/dev/null 2>/dev/null . It sends both stdout and stderr to /dev/null, since we are not interested in it's output, only the return-value.

|| is logical or, ( and && is logical and )

If you have the two commands A and B, and you run them like this:
```
A && B
```
Then A will be run first. If and only if it returns true (return value 0), B will be run.

And with
```
A || B
```
Then A will be run first. If and only if it returns false (return value <> 0), B will be run.

---

### Post by meindian523 on 2008-06-30
Does that apply to the shell script too?I thought we use && because & sends a task to the background.Does that mean the && in the script is a logical &?

---

### Post by geirha on 2008-06-30
Yes, and you definitely do not want to use & in place of && in your script above. That would make all three commands run simultaneously ... producing odd results most likely. It makes sense to use the logical and in the above case. Because if cd to directory fails, there's no point in running the tar command, and if the tar command fails, there's no point in running bzip2 afterwards

---

### Post by Inxsible on 2008-06-30
> **meindian523 said:**
> I tried sudo apt-get clean in a terminal,and it didn't wait for any user input,so I think the -qy options are redundant.hmm that's strange because the autoclean does require user input.

---

### Post by meindian523 on 2008-06-30
hmm,thanks.In short,the script is correct.Now,I've to just mark the thread solved and figure out from man cron how to add this task to run every 100 days.And please don't spoil the fun of me finding out myself by posting here.

---

### Post by Inxsible on 2008-06-30
> **meindian523 said:**
> The script now looks like this:
```
#!/bin/bash

filename=$(date +%d-%m-%Y)
cd /var/cache/apt/archives && tar -cf /home/easwarh/$filename *.deb && bzip2 -z /home/easwarh/"$filename.tar"

apt-get clean
```and I get something different now.Progress?I'm not sure.

```
easwarh@l1nuxr0cks:~/Desktop$ ./try1 
tar: *.deb: Cannot stat: No such file or directory
tar: Error exit delayed from previous errors
E: Could not open lock file /var/cache/apt/archives/lock - open (13 Permission denied)
E: Unable to lock the download directory
easwarh@l1nuxr0cks:~/Desktop$ 
```I think you have a space between filename and *.deb. That's why you are getting the deb error

---

### Post by meindian523 on 2008-06-30
I did sudo apt-get clean,NOT autoclean.Autoclean,IIRC,cleans the archives every so many days or whatever you set.

---

### Post by geirha on 2008-06-30
For more bash-goodness, read the Bash Guide for Beginners, and if you want to get really dirty, read the Advanced Bash-Scripting Guide as well.

[http://www.tldp.org/guides.html](http://www.tldp.org/guides.html)

ps. They use a lot of examples!

---

### Post by Inxsible on 2008-06-30
> **meindian523 said:**
> ....[snip]And please don't spoil the fun of me finding out myself by posting here.

```
00 00 */100 * * /path/to/script 
```:twisted:  MUHAHAHAHAHAH

---

### Post by meindian523 on 2008-06-30
Nopes,I don't think that space is the problem,because otherwise,how do you differentiate between what has to be tarred and where it has to be tarred to.And no,I didn't read that Muhahaha post,and even if I did,I'm going to man cron. :P

---

### Post by Inxsible on 2008-06-30
> **meindian523 said:**
> .....[snip]and No,i Didn't Read That Muhahaha Post,and Even If I Did,i'm Going To Man Cron. :p
Lol

---

