---
title: "Batch to delete files under 7 KB size in one folder"
date: 2011-03-27
forum: Programming Talk
---

### Post by ITC on 2011-03-27
Hi.

I have no ideas about writing batch scripts so i will ask you at this great forum for some help.

I like to have a batch file/script the will remove/delete files under 7 KB from a folder.
I run a AssaultCube server and the demos stored that are under 7 KB i do not need.

So i like a script to delete all demos under 7 KB every hour.

The server stores demos in /home/username/.games/1.1.0.4/demos/serverdemos
The demos are ending with .dmo

So, can anyone pls write this script for me and tell me how to use it?

Thanks.

---

### Post by MadCow108 on 2011-03-27
use
```
find /folder/ -size -7k -type f -delete
```
or similar as a cronjob
[http://adminschoice.com/crontab-quick-reference](http://adminschoice.com/crontab-quick-reference)

test without -delete before using!!

---

### Post by sisco311 on 2011-03-27
EDIT: 
MadCow108 beat me to it. :)


You could use the find command. Check out this howto: [http://mywiki.wooledge.org/UsingFind](http://mywiki.wooledge.org/UsingFind)

```
find /home/username/.games/1.1.0.4/demos/serverdemos  -iname '*.dmo' -size -7k -type f **-print**
```
will print the files. If you want to delete them, replace the **-print** option with **-delete**.

EDIT: the -iname test comes before the -type and -size tests in  order  to  avoid having to call stat(2) on every file.
[/EDIT]

You can create a cron job to run the command every hour: 
[uhelp]community/CronHowto[/uhelp]

---

### Post by ITC on 2011-03-27
Thanks a lot for the quick responses.

Ill give this a try.

I can see the commands will work, but im a noob so i may be coming back for some more help.

:)

Edit: So, this is what i got now:
00 * * * * find /home/username/.games/1.1.0.4/demos/serverdemos  -size -7k -iname '*.dmo' -type f -delete

This i added using crontab -e
Of course username is changed to my username.

Can someone confirm this will delete all .dmo files under 7K in the path?

Thx again.

---

### Post by sisco311 on 2011-03-27
I tested the command before posting it, so it should work. :)

find by default operates recursively which means that the command will remove any .dmo file under 7k from serverdemos and its subdirectories. If you don't want to delete .dmo files from the subdirectories, then use the **-maxdepth 1** option.

Also check out my edit in my previous post. To make the command more efficient, you  should put the -iname test before the -size test.

I don't have much experience with cron, but as far as I tell it should work. But it's a good practice to specify the full path to a command in cron:
```
0 * * * * /usr/bin/find **/path -options**
```

---

### Post by ITC on 2011-03-27
So, this is what i added with crontab -e

# m h  dom mon dow   command
0 * * * * /usr/bin/find /home/username/.games/1.1.0.4/demos/serverdemos  -iname '*.dmo' -size -7k -type f -delete

And this will delete all .dmo files under 7KB (7000b) from the path?
Again, username is of course set to my username.

There are no subfolders in serverdemos, the only thing stored there are demos from the server.

Thanks again for all the help.

Edit: Guess i cet set this thread as solved.

---

