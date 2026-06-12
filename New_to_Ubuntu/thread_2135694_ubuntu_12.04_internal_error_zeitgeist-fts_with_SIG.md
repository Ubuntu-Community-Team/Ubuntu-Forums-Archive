---
title: "ubuntu 12.04 internal error: zeitgeist-fts with SIGABRT in raise"
date: 2013-04-15
forum: New to Ubuntu
---

### Post by cluelesswonder on 2013-04-15
I got an internal error message this morning and am not sure what to do about it.
The error report is for zeitgeist-core 0.9.0-1ubuntu1
with the title: zeitgeist-fts with SIGABRT in raise()

I'm not sure what other information is necessary to address this issue.
Please help if possible!

---

### Post by snowmethod on 2013-04-15
Hi

These errors are memory related. Please try this solution: 

[http://ubuntuforums.org/showthread.php?t=1991729&p=12129423#post12129423](http://ubuntuforums.org/showthread.php?t=1991729&p=12129423#post12129423)

Regards

---

### Post by cluelesswonder on 2013-04-15
Thank you for the link.

I'm relatively new at ubuntu and don't know how to manipulate code. Typing in the suggested code as listed in the comment you linked me to doesn't have any result.
> 
My solution was to take ownership of /usr/bin/zeitgeist* and make it  *not* executable. I figure if it can't Execute, it won't be in my  processes eating my RAM.
 
I used
 
sudo chown [username] /usr/bin/zeitgeist* 
 
and opened the Properties of the files, under Permissions un-checked the Executable box.
 
Could have probably just used 

sudo chmod a-x /usr/bin/zeitgeist*   (IF that's the correct syntax)

It doesn't seem to recognize or do anything with this. I'm not sure what else I need to do. . .any suggestions?

---

### Post by snowmethod on 2013-04-15
Try this :

```
sudo chmod [COLOR=#660033]-rw[/COLOR] ~[COLOR=#000000]**/**[/COLOR].local[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]zeitgeist[COLOR=#000000]**/**[/COLOR]activity.sqlite
```

This removes the possibility to read and write to the file ~/.local/share/zeitgeist/activity.sqlite 

Follow with this command:

```
zeitgeist-daemon --replace
```

And you should get an error like this:

```
[WARNING[COLOR=#7a0874]][/COLOR] Could not access the database file. Please check the permissions of **file** [COLOR=#000000]**/**[/COLOR]home[COLOR=#000000]**/**[/COLOR]linuxaria[COLOR=#000000]**/**[/COLOR].local[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]zeitgeist[COLOR=#000000]**/**[/COLOR]activity.sqlite.
```


Which is correct...

You might have some follow up errors - try rebooting machine and report here if the issue persist.

---

### Post by cluelesswonder on 2013-04-15
Ok. I tried all of that and got 

bash: /usr/bin/zeitgeist-daemon: Permission denied

which seems close (enough?) to what I should get.
I will post again if I get the error next time.

Thank you!!

---

### Post by snowmethod on 2013-04-15
Do this first:

```
sudo zeitgeist-daemon --quit
```

and follow with the commands from the previous post

---

### Post by cluelesswonder on 2013-04-15
I'm getting 
sudo: zeitgeist-daemon: command not found
when I do that :confused:

I also just got another internal error: this time with usr/share/apport-checkreports
in the apport log of the error report
usr/lib/zeitgeist/zeitgeist-fts is coming up as an error though

---

### Post by snowmethod on 2013-04-15
Can you post the output of the command :

```
ps aux | grep zeit
```

---

### Post by cluelesswonder on 2013-04-15
yes.

enigma    2085  0.0  0.1  55232  5704 ?        Sl   08:08   0:01 zeitgeist-datahub
enigma    2092  0.0  0.1  47380  7116 ?        Sl   08:08   0:02 /usr/bin/zeitgeist-daemon
enigma   10883 96.1 11.6 482056 439040 ?       Rl   10:51 154:02 /usr/lib/zeitgeist/zeitgeist-fts
enigma   15250  0.0  0.0   5612   828 pts/2    S+   13:32   0:00 grep --color=auto zeit

---

### Post by snowmethod on 2013-04-15
Last try mate :

do:
```
sudo -s
```
it will prompt you for the root/admin password 
then
```
chmod [COLOR=#660033]-rw[/COLOR] ~[COLOR=#000000]**/**[/COLOR].local[COLOR=#000000]**/**[/COLOR]share[COLOR=#000000]**/**[/COLOR]zeitgeist[COLOR=#000000]**/**[/COLOR]activity.sqlite
```
and finally 
```
zeitgeist-daemon --replace
```
and this should come up with the warning as from previous posts.

---

### Post by cluelesswonder on 2013-04-15
Thanks for your help on this. Sorry for so much trouble!
I still got the same result though. . . .

enigma@Peanut:~$ sudo -s
[sudo] password for enigma: 
root@Peanut:~# chmod -rw ~/.local/share/zeitgeist/activity.sqlite
root@Peanut:~# zeitgeist-daemon --replace
bash: /usr/bin/zeitgeist-daemon: Permission denied

---

