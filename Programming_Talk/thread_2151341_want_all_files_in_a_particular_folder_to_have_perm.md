---
title: "want all files in a particular folder to have permission 755"
date: 2013-06-04
forum: Programming Talk
---

### Post by IAMTubby on 2013-06-04
Hello,
Assume I have a folder called /home/IAMTubby/shellscrtipts .I want all files created in this folder to have permission 755.

Use case:
Otherwise, for every shell script I write, before running, it , I have to go and do a **chmod +x myshellscript.sh** or **sh myshellscript.sh**.

Thanks.

---

### Post by ofnuts on 2013-06-04
I don't think it can be done (and that would be a nice security hole)... I circumvent the problem with a "newscript" script: creates a stub (shebangs for bash & python and I drop the one I don't need) in my ~/bin, sets it executable, and starts the editor on it.

---

### Post by Vaphell on 2013-06-04
nautilus supports such a feature already. Whatever you put in your Templates dir will be accessible from rightclick/new document menu. Filename is used as the entry name and that barebone template file is simply copied to where you need the new instance. I have templates named 'Bash script.sh' and 'Python script.py' with hashbangs and permissions set, plus Libre office doc and spreadsheet.

---

### Post by IAMTubby on 2013-06-04
> **ofnuts said:**
> I don't think it can be done (and that would be a nice security hole)... I circumvent the problem with a "newscript" script: creates a stub (shebangs for bash & python and I drop the one I don't need) in my ~/bin, sets it executable, and starts the editor on it.
ofnuts, thanks for the reply, but can't it be done by changing the folder properties or something? Sorry, don't know what's technically possible, just talking from an end-user point of view :). I couldn't understand the solution you gave, I'm sorry :( 


> **Vaphell said:**
> nautilus supports such a feature already. Whatever you put in your Templates dir will be accessible from rightclick/new document menu. Filename is used as the entry name and that barebone template file is simply copied to where you need the new instance. I have templates for 'Bash script.sh' and 'Python script.py' with hashbangs and permissions set, plus Libre office doc and spreadsheet.
Vaphell, thanks, but I'm not running a nautilus sadly. Is there a solution by editing the folder properties ?

---

### Post by Morbius1 on 2013-06-04
What version of Ubuntu are you using? - 12.04, 12.10, 13.04, .....

There's a way to do this using bindfs but it different in 12.04 than in newer versions.

---

### Post by sanderj on 2013-06-04
> **IAMTubby said:**
> Hello,
Assume I have a folder called /home/IAMTubby/shellscrtipts .I want all files created in this folder to have permission 755.

Use case:
Otherwise, for every shell script I write, before running, it , I have to go and do a **chmod +x myshellscript.sh** or **sh myshellscript.sh**.

Thanks.

Put in a crontab entry * * * * *, and ... problem solved.

So: "crontab -e" and then

```
* * * * *               chmod +x /home/IAMTubby/shellscrtipts/*.sh
```

HTH

---

### Post by IAMTubby on 2013-06-08
> **Morbius1 said:**
> What version of Ubuntu are you using? - 12.04, 12.10, 13.04, .....

There's a way to do this using bindfs but it different in 12.04 than in newer versions.
Morbius1, I'm very sorry for the late reply.
I'm running 11.04 but ideally I would like to have a solution which fits all versions, because I use other systems as well.

---

### Post by IAMTubby on 2013-06-08
> **sanderj said:**
> Put in a crontab entry * * * * *, and ... problem solved.

So: "crontab -e" and then

```
* * * * *               chmod +x /home/IAMTubby/shellscrtipts/*.sh
```

HTH
sanderj, I'm sorry for the late reply, I  added that line after doing  a crontab -e. (I did make sure all my paths are correct.)


I then went and wrote a 1-line shell script in the same directory as above and tried executing once again as **./test.sh**, but it still gave me the same Permission denied message.
Am I executing incorrectly ?

---

### Post by sanderj on 2013-06-09
post the output of:

```
crontab -l
ls -al /home/IAMTubby/shellscrtipts/*.sh
```

---

### Post by Vaphell on 2013-06-09
which DE/file browser do you use that it doesn't support the file templates?

---

### Post by IAMTubby on 2013-06-11
> **sanderj said:**
> post the output of:

```
crontab -l
ls -al /home/IAMTubby/shellscrtipts/*.sh
```

sanderj,
this is the output of my crontab -l command

I first did a [COLOR=#000000][FONT=Consolas]export VISUAL=vi[/FONT][/COLOR]

```

droid@droid-Inspiron-1545:~/Desktop/shellscripts$ crontab -l
# Edit this file to introduce tasks to be run by cron.
# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
* * * * *               chmod +x /home/droid/Desktop/shellscripts/*.sh

```
I then went and created a shell script called test.sh at this location, which has nothing but an echo "hello world";

On running the script, it gave me the following
[B]droid@droid-Inspiron-1545:~/Desktop/shellscripts$ ./test.sh
bash: ./test.sh: Permission denied
[/B]

---

### Post by sanderj on 2013-06-11
It works for me:
```
sander@hapee:~/shellscripts$ ll
total 12
drwxrwxr-x  2 sander sander 4096 jun 11 20:03 ./
drwxr-xr-x 41 sander sander 4096 jun 11 20:01 ../
-rw-rw-r--  1 sander sander   12 jun 11 20:03 weg.sh
sander@hapee:~/shellscripts$ date
di jun 11 20:03:42 CEST 2013
sander@hapee:~/shellscripts$ date
di jun 11 20:03:58 CEST 2013
sander@hapee:~/shellscripts$ date
di jun 11 20:04:00 CEST 2013
sander@hapee:~/shellscripts$ date
di jun 11 20:04:01 CEST 2013
sander@hapee:~/shellscripts$ ll
total 12
drwxrwxr-x  2 sander sander 4096 jun 11 20:03 ./
drwxr-xr-x 41 sander sander 4096 jun 11 20:01 ../
-rwxrwxr-x  1 sander sander   12 jun 11 20:03 weg.sh*
sander@hapee:~/shellscripts$ ./weg.sh 
Hallo
sander@hapee:~/shellscripts$ 

```

So, why doesn't it work for you?

What if you run

```
chmod +x /home/droid/Desktop/shellscripts/*.sh
```

from a terminal? Does it make the scripts executable?

---

### Post by JonnyPython on 2013-06-11
Hi,
Can't you do something like chmod 755 *.* ?

Greets

---

### Post by IAMTubby on 2013-06-11
> **sanderj said:**
> It works for me:
So, why doesn't it work for you?
sanderj, thanks for the constant feedback.
But are the outputs which I posted giving expected values ?

> 
What if you run
chmod +x /home/droid/Desktop/shellscripts/*.sh
from a terminal? Does it make the scripts executable?
Yes, that surely does, but weren't we trying to automate it in the first place?

> **JonnyPython said:**
> Hi,
Can't you do something like chmod 755 *.* ?
Greets
Hello JonnyPython I tried doing as you said
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ vi new
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ ./new
bash: ./new: Permission denied

---

### Post by sanderj on 2013-06-11
> **IAMTubby said:**
> sanderj, thanks for the constant feedback.
But are the outputs which I posted giving expected values ?


Yes, that surely does, but weren't we trying to automate it in the first place?


Good, and: yes, absolutely, it should be automated. But if that does not work, first do it manual. And that works. Good. But I'm puzzled why the crontab does not work. Possibilities:
- crontab is not run at all
- crontab does run, but the entry does not work correctly
- you're mixing directory or file names. I'm still not sure you're sharing exactly the exact names and results ...

---

### Post by drmrgd on 2013-06-12
> **ofnuts said:**
> I don't think it can be done (and that would be a nice security hole)... I circumvent the problem with a "newscript" script: creates a stub (shebangs for bash & python and I drop the one I don't need) in my ~/bin, sets it executable, and starts the editor on it.

I do the same, and think this is a much easier solution.  With the crontab solution, you have to constantly update the directories that you process (assuming you script in more than 1 directory).  Vaphell's solution is good too, but for me I usually am coding from the terminal.  Here's an example of a quick and dirty shell script I use for creating new perl scripts from a stub template I have in my Dropbox dir so that I can access it from home or work:

```
template="/home/dave/Dropbox/scripts/templates/perlScriptTemplate.pl"
if [[ ! -f $template ]]; then
        echo "ERROR: The Perl template file does not exist or has been moved"
        exit 1
fi

if [ -z $1 ]; then
        printf "No filename indicated\n"
        printf "What filename would you like to give the new script: "
        read filename
else
        filename=$1 
fi

cp "$template" ./"$filename" && chmod 755 ./"$filename"
vim ./"$filename"
exit

```

You can of course mess with the above and choose a different template and editor as you like.  You could also get crazy and add commandline opts to choose which language you want to use as the template (perl, python, bash, C, etc) or whatever. 

Hope that helps!

---

### Post by Meghnaad on 2013-06-13
**[COLOR="#006400"][SIZE=4][SIZE=5]drmrgd's Solution is perfect.[/SIZE][/SIZE][/COLOR]**

I just want to add one more solution:

How about creating a Function & putting in your profile file (typically ~/.bashrc):

```

function CreateScript
{
    if [ $# -ne 1 ]         #Check if you've received exactly a single argument
    then
        echo "Pass One File name as argument...." >&2
        echo "Usage: CeateScript  filename"          >&2
    else
        if [ -e $1 ]              #Check if file with that name already exists if exists open it for editing if possible
        then
            if [ -f $1 ]
            then
                vim $1            #Open it for editing
            else
                echo "$1 is not a regular file can not edit it..." >&2
            fi
        else
            touch $1            #Create an empty file with whatever name you want
            chmod 755 $1     #Set the permissions you want
            vim $1               #Start Writing Script
        fi
    fi
}

```

Now you can execute this function as follows:

```
CreateScript  filename
```

No matter where you create the file with this function it will have 755 permissions
Also in function in place of touch you can make copy of a template file.

I have not thoroughly tested the script.

---

### Post by IAMTubby on 2013-06-17
> **sanderj said:**
> Good, and: yes, absolutely, it should be automated. But if that does not work, first do it manual. And that works. Good. But I'm puzzled why the crontab does not work. Possibilities:
- crontab is not run at all
- crontab does run, but the entry does not work correctly
- you're mixing directory or file names. I'm still not sure you're sharing exactly the exact names and results ...
sanderj,
I was out of town with no access to mail. These are the things I have done regarding crontab.
**1.When I do crontab -l at the terminal, this is what I get**
```
# Edit this file to introduce tasks to be run by cron.# 
# Each task to run has to be defined through a single line
# indicating with different fields when the task will be run
# and what command to run for the task
# 
# To define the time you can provide concrete values for
# minute (m), hour (h), day of month (dom), month (mon),
# and day of week (dow) or use '*' in these fields (for 'any').# 
# Notice that tasks will be started based on the cron's system
# daemon's notion of time and timezones.
# 
# Output of the crontab jobs (including errors) is sent through
# email to the user the crontab file belongs to (unless redirected).
# 
# For example, you can run a backup of all your user accounts
# at 5 a.m every week with:
# 0 5 * * 1 tar -zcf /var/backups/home.tgz /home/
# 
# For more information see the manual pages of crontab(5) and cron(8)
# 
# m h  dom mon dow   command
* * * * *               chmod +x /home/droid/Desktop/shellscripts/*.sh



```

> **sanderj said:**
> Possibilities:
- crontab does run, but the entry does not work correctly
- you're mixing directory or file names. I'm still not sure you're sharing exactly the exact names and results ...
**2.The below 2 commands tell you about the path and contents of the folder on which I am trying to enforce the permission**
```
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ pwd
**/home/droid/Desktop/shellscripts**
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ **ls**
command-line   concatenate    exprOR        hello        increment  minus-e  multiline
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ 

```

**3.These are my commands to create a new script and execute it**
```

droid@droid-Inspiron-1545:~/Desktop/shellscripts$ pwd
/home/droid/Desktop/shellscripts
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ vi test.sh
droid@droid-Inspiron-1545:~/Desktop/shellscripts$ ./test.sh
bash: ./test.sh: Permission denied

```

**4.My script is as follows**
```

#!/bin/bash
echo "this is a test to see if crontab is working
```

**5.I'm getting some really weird scenarios**
Sometimes it works when I open a terminal, write in the test.sh script, close the terminal, reopen the terminal to the required directory and then execute.
It's like it needs a terminal closing trigger to activate the permission or something.
**But that's again only sometimes, some other times, the same steps do not work, and so I cannot rely on it.**

6.> **sanderj said:**
> - crontab is not run at all
Is there something else to do, to run crontab, or would it just start running when the system boots up ?

Should I post any other output which may assist you ?
Thanks.

---

### Post by IAMTubby on 2013-06-17
> **drmrgd said:**
> cp "$template" ./"$filename" && chmod 755 ./"$filename"
vim ./"$filename"
Hope that helps!
Thank you drmrgd, that's useful. :)
However, I would like to go with a crontab entry because we are not doing a chmod +x 755 explicitly there.

> **Meghnaad said:**
> 
            touch $1            #Create an empty file with whatever name you want
            chmod 755 $1     #Set the permissions you want
            vim $1               #Start Writing Script

Thanks Mehgnaad, appreciate your help. :)
But would like to go with a crontab entry.

---

### Post by spjackson on 2013-06-18
> **IAMTubby said:**
> 
**5.I'm getting some really weird scenarios**
Sometimes it works when I open a terminal, write in the test.sh script, close the terminal, reopen the terminal to the required directory and then execute.
It's like it needs a terminal closing trigger to activate the permission or something.
**But that's again only sometimes, some other times, the same steps do not work, and so I cannot rely on it.**

You do appreciate, don't you, that crontab entries are scheduled to run at set times, or set time intervals? The one you have scheduled (with * in every field) runs once each minute. If you save your script then try to run it before the minute has changed, your cron entry won't have had chance to run yet.

If you want to run it more frequently (e.g. every second) then you can't. Use one of the other suggested methods, or have a looping script:
```

while [ forAsLongAsYouWant ]
do
    chmod da de da de da
    sleep 1
done

```
Or use filesystemwatcher, or bindfs (which was suggested very early in this thread).

---

### Post by shawnhcorey on 2013-06-18
> **IAMTubby said:**
> Hello,
Assume I have a folder called /home/IAMTubby/shellscrtipts .I want all files created in this folder to have permission 755.

Use case:
Otherwise, for every shell script I write, before running, it , I have to go and do a **chmod +x myshellscript.sh** or **sh myshellscript.sh**.

Thanks.

See:
man find
man chmod

---

### Post by IAMTubby on 2013-06-19
> **spjackson said:**
> The one you have scheduled (with * in every field) runs once each minute.
> **sanderj said:**
> Put in a crontab entry * * * * *, and ... problem solved.
Thanks a lot spjackson, no I didn't know that :) . I have now read up about cronjobs using crontab and appreciate sanderj's method. So basically, every minute we are doing a chmod +x to my shell scripts under that folder. Cool!

I just have one final question(/need confirmation really) regarding scheduling cronjobs. So since cronjobs are of this format
**[COLOR=#111111][FONT=Consolas]MIN HOUR DOM MON DOW CMD[/FONT][/COLOR]**, just wanted to confirm that no one writes a cronjob with both the DOM(day of month) and DOW(day of week) both filled in right, it wouldn't make any sense if they were not consistent with each other ?(Assume June19 is a Wednesday and along with filling this, you also fill a Thursday(4) to the DOW column.
Something like *** * 19 6 4 /execute-my-script.sh**.
Just confirming.

Thanks a lot for the other replies too, I truly appreciate.

---

### Post by ofnuts on 2013-06-19
Note that executing "chmod +x ..." on all the files each time resets their "change date" so they will be picked up by backup managers each time. You may want to change the flag only on files where it is not set yet (see the various filtering options of the "find" command.

---

### Post by trent.josephsen on 2013-06-19
> **IAMTubby said:**
> I just have one final question(/need confirmation really) regarding scheduling cronjobs. So since cronjobs are of this format
**[COLOR=#111111][FONT=Consolas]MIN HOUR DOM MON DOW CMD[/FONT][/COLOR]**, just wanted to confirm that no one writes a cronjob with both the DOM(day of month) and DOW(day of week) both filled in right, it wouldn't make any sense if they were not consistent with each other ?

```
$ man 5 crontab
```

---

### Post by spjackson on 2013-06-19
> **IAMTubby said:**
> 
I just have one final question(/need confirmation really) regarding scheduling cronjobs. So since cronjobs are of this format
**[COLOR=#111111][FONT=Consolas]MIN HOUR DOM MON DOW CMD[/FONT][/COLOR]**, just wanted to confirm that no one writes a cronjob with both the DOM(day of month) and DOW(day of week) both filled in right, it wouldn't make any sense if they were not consistent with each other ?
It depends what you mean by "make any sense", and precisely what you are trying to do. If you schedule a job for Sunday 1 January, then it won't happen next year, or in 2015 or 2016, but it will in 2017. If for some reason that was your intent, then that would be a way to express it.

So when you say "Assume [COLOR=#000000]June19 is a Wednesday...", well some years it is and some years it isn't.

Using this kind of combination is probably unusual but that doesn't make it nonsensical or pointless.[/COLOR]

---

### Post by IAMTubby on 2013-06-19
> **spjackson said:**
> "Assume [COLOR=#000000]June19 is a Wednesday...", well some years it is and some years it isn't.[/COLOR]
thanks spjackson, I didn't think about that. so basically 30 1 19 6 2 will execute at 1:30 on 19th June only in a year when it is a Tuesday.
So we represent this as a logical condition as follows
```

/* assume format : MIN HOUR DAYOFMONTH MONTHNO DAYOFWEEK script.sh */
if(currentmin==MIN && currenthour==HOUR && currentdayofmonth==DAYOFMONTH && currentmonth==MONTHNO && currentdayofweek==DAYOFWEEK)
{
 system("./script.sh");
}

```
Thanks for clearing this. **If not this year, but some year didn't strike me at all.**

---

### Post by trent.josephsen on 2013-06-19
[quote=crontab(5)]       Note: The day of a command's execution can be specified in the  follow&#8208;
       ing two fields — 'day of month', and 'day of week'.  If both fields are
       restricted (i.e., do not contain the "*" character), the  command  will
       be run when **either** field matches the current time.  For example,
       "30  4  1,15 * 5" would cause a command to be run at 4:30 am on the 1st
       and 15th of each month, plus every Friday.[/quote]

Like I said...

---

### Post by spjackson on 2013-06-20
> **trent.josephsen said:**
> Like I said...
Indeed. My mistake. Apologies. I have long held the mistaken impression that all fields are ANDed, Clearly not.

---

### Post by trent.josephsen on 2013-06-20
Eh, understandable. I think that's the only exception.

---

### Post by IAMTubby on 2013-06-23
> **trent.josephsen said:**
> Like I said...
Thanks a lot trent.josephsen.

---

