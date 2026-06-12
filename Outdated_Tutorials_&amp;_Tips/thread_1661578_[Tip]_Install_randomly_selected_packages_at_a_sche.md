---
title: "[Tip] Install randomly selected packages at a scheduled time with sudo authentication"
date: 2011-01-06
forum: Outdated Tutorials &amp; Tips
---

### Post by gimfred on 2011-01-06
I've been trying to schedule the installation of packages because of bandwidth restrictions. Now, sure I can set at, cron, or gnome-schedule to run at a later time, download the deb etc. But that is a lot of work. such as the following 'solutions'
[LIST=1]
[*][http://ubuntuforums.org/showthread.php?t=1502457&highlight=schedule+sudo](http://ubuntuforums.org/showthread.php?t=1502457&highlight=schedule+sudo)
[*][http://ubuntuforums.org/showthread.php?t=1567817&highlight=schedule+sudo](http://ubuntuforums.org/showthread.php?t=1567817&highlight=schedule+sudo)
[*][http://ubuntuforums.org/showpost.php?p=8922715&postcount=2](http://ubuntuforums.org/showpost.php?p=8922715&postcount=2)
[*][http://ubuntuforums.org/showthread.php?t=1567817&highlight=schedule+sudo](http://ubuntuforums.org/showthread.php?t=1567817&highlight=schedule+sudo)
[/LIST]
I'm not knocking the solutions or other similar around the web, as they are probably good for some problems; they just didn't do what I wanted.

[LIST]
[*]At: finding the correct url to the deb and dependencies can be tiresome.

[*]Cron: extra work to script for an one-off job

[*]Gnome-schedule: the worst of both cron and at. Shudder --- didn't like.
[/LIST]

The solution is 4 useful tools. 'at', 'echo', 'sudo' and intelligence. (Yes, I'm pleased with myself)

Previously to run a schedule as root, I've been advised to use cron because running sudo apt-get install <new you-beaut program> | at 2am tommorow won't work as you aren't around at 2am to input the password or, if you are just sitting around trying to do just that, you can't find the display at runs the command on (Least I couldn't).

So what you actually need to do is get root to schedule the task not schedule a task to run authorised command.

Here is how I tested it: (around 1am this morning)
Note the permissions of the test.file.
```
:~$ touch test.file
:~$ echo 'chmod 466 ./test.file' | sudo at 00:54 today
warning: commands will be executed using /bin/sh
job 20 at Fri Jan  7 00:54:00 2011
:~$ ls -l test.file 
-rw-r--r-- 1 <user> <user> 0 2011-01-07 00:51 test.file

```
5 minutes later ~
```
:~$ ls -l test.file 
-rwxr-xr-x 1 <user> <user> 0 2011-01-07 00:51 test.file

```
Suck Cess!

Schedule task for later:
```
:~$ echo 'chmod 466 ./test.file' | sudo at 0500 today
warning: commands will be executed using /bin/sh
job 21 at Fri Jan  7 05:00:00 2011
```
Time to sleep... 
At 10:30 today:
```
:~$ ls -l test.file 
-rwxr-xr-x 1 <user> <user> 0 2011-01-07 00:51 test.file

```
You can probably make various tasks start after the previous job has finished; Unix gurus were pretty thorough. Be aware that this can be a security breach if you have a timed delay on authentication, i.e., malware running sudo seconds after you have authenticated. I've never heard of it being done though.


[Actual Solution]
So to run random task requiring authentication at a non-interactive time:

you must echo the task to a sudo 'at'. Not as hard as it sounds.
```
echo '<command you normal prefix sudo to' | sudo at <time>*
```
for example you normally need to sudo apt-get install wine
```
echo 'apt-get install wine | sudo at 2:20am tommorrow
```

CLI rocks pwned GUI again :guitar:

---

