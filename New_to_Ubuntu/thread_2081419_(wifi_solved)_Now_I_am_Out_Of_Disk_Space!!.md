---
title: "(wifi solved) Now I am Out Of Disk Space!!"
date: 2012-11-06
forum: New to Ubuntu
---

### Post by pjstock on 2012-11-06
Sigh,

Following a Heroic effort here, my wifi problem has been SOLVED.

But, I celebrated too soon as I now seem to be Out Of Disk Space.

How can that be on a fresh install of Xubuntu?

I installed Xubuntu because I thought it was a small footprint version of Linux that would still work on this laptop which only has a 20Gb HDD.

Now, at the end of a long wifi troubleshooting exercise, I find myself with 0 Free Space and the 18.4Gb used up.

For simplicity I did not dual partition this thing (as that has left me struggling for space in the past too.)

This is a fresh install of 11.10 first, then upgraded to 12.04. Nothing else has been installed and there is no data (music, etc.) on this at all.

What have I done wrong?

Peter

It was suggested I post these results.
does this help?

peter@peter-Latitude-D505:~$ df -Th
Filesystem     Type      Size  Used Avail Use% Mounted on
/dev/sda1      ext4       18G   17G   12K 100% /
udev           devtmpfs  367M  4.0K  367M   1% /dev
tmpfs          tmpfs     150M  800K  149M   1% /run
none           tmpfs     5.0M     0  5.0M   0% /run/lock
none           tmpfs     374M   88K  374M   1% /run/shm
peter@peter-Latitude-D505:~$ sudo parted -l 
[sudo] password for peter: 
Sorry, try again.
[sudo] password for peter: 
Model: ATA IC25N020ATMR04-0 (scsi)
Disk /dev/sda: 20.0GB
Sector size (logical/physical): 512B/512B
Partition Table: msdos

Number  Start   End     Size    Type      File system     Flags
 1      1049kB  19.5GB  19.5GB  primary   ext4            boot
 2      19.5GB  20.0GB  535MB   extended
 5      19.5GB  20.0GB  535MB   logical   linux-swap(v1)


peter@peter-Latitude-D505:~$

---

### Post by Bashing-om on 2012-11-06
pjstock; Hi !

Probably nothing you have done "wrong" ...18 G I expect to be more than sufficient for the operating system and lots of files.

To see where the space is being used:
```
df -h
```to clear out the package cache:
```
sudo apt-get clean
```to remove obsolete files:
```
sudo apt-get autoclean
```Then start looking for large directories:
```
du -h /home | sort -nr | less
```keep drilling down and around by substituting "/home" with other directories-> do not forget to look at  /boot (many old kernels and headers) and especially your logs (many, many old logs) in /var/log/.  -> deleting any un-needed un-wanted files.
[INDENT]hth <== BDQ

[/INDENT]

---

### Post by ibjsb4 on 2012-11-06
Either use boot options to get to terminal or your live cd and find those large files.

sudo find / -size +1G

---

### Post by NikTh on 2012-11-07
Hi , 

the commands [I suggested you to post the results](http://ubuntuforums.org/showpost.php?p=12340965&postcount=39) are not all there (in your first post) 

Have a look again and execute the commands one line at time and post back the results. 

Also , the brackets , do not forget the brackets because I have a difficulty to read them(the results) as a simple text. 
You can use the [CODE] tags , if you click on "New Reply" you can highlight the text (the results) and click this symbol **#** at the message toolbar.

Thanks

---

### Post by pjstock on 2012-11-07
I'll rerun things

But I am getting an error on this command:

sudo du -h --max-depth=1 / | grep '[0-9]G\>'

result is:
invalid maximum depth '1'sudo du -h --max-depth=1 / | grep '[0-9]G\>'

can you confirm the correct command?


Also, I am not clear about what I should be doing with brackets to make the results more readable.

Peter

---

### Post by NikTh on 2012-11-07
> **pjstock said:**
> I'll rerun things

But I am getting an error on this command:

sudo du -h --max-depth=1 / | grep '[0-9]G\>'

result is:
invalid maximum depth '1'sudo du -h --max-depth=1 / | grep '[0-9]G\>'

can you confirm the correct command? 

Just tried the command , copied & pasted to my terminal from here , and work as it should. Weird. 

Then run the other commands and also the command @Bashing-om suggested 
```
du -h /home | sort -nr | less
```> **pjstock said:**
> Also, I am not clear about what I should be doing with brackets to make the results more readable.

Maybe this is my English fault , but a picture is worth a thousand words they say. 
Look the attached .

---

### Post by pjstock on 2012-11-07
one problem I am having is there since (I guess) there is so little disk space left (like Zero) I cannot even run a webbrowser on the problem laptop so that I could see this thread and copy the commands from here and paste them into Terminal.

so I have to retype them and the L's (l) are not clearly distinct from the Ones (1)

but here is what I get when I try to run that command now:

```
peter@peter-Latitude-D505:~$ sudo du -h --max-depth=1/|grep '[0-9]G\>'
du: cannot access `./.gvfs': Permission denied
peter@peter-Latitude-D505:~$ 

```

---

### Post by Wim Sturkenboom on 2012-11-07
Just leave the grep part out of the above command.
```

sudo du -h --max-depth=1 /

```
Look for the largest directory (e.g. /home) and repeat the command
```

sudo du -h --max-depth=1 /home

```
Repeat a couple of times (e.g. if peter is n ow the largest directory, run _sudo du -h --max-depth=1 /home/peter_) till you can't go further or find nothing special. Next run a _ls -lS_ to find the largest files (the S option sorts by size).

---

### Post by pjstock on 2012-11-08
> **Wim Sturkenboom said:**
> Just leave the grep part out of the above command.
```

sudo du -h --max-depth=1 /

```
Look for the largest directory (e.g. /home) and repeat the command
```

sudo du -h --max-depth=1 /home

```
Repeat a couple of times (e.g. if peter is n ow the largest directory, run _sudo du -h --max-depth=1 /home/peter_) till you can't go further or find nothing special. Next run a _ls -lS_ to find the largest files (the S option sorts by size).


when I try either of these commands in Terminal all I get as a response is:

>
>
>

Nothing.

but when I do a very inelegant RightClick > Properties on the various folders under File System

the only big ones are:
Proc = 1Gb
Usr = 1.7Gb
Var 15.5 Gb (hmmm, that seems to be a space hog.)\

and then checking the folders under Var :
Log = 13.7Gb
Cache = 685Mb

but then none of the folders (at least the visible ones) under LOG seem to be bigger than 1-2Mb.

Peter

---

### Post by Wim Sturkenboom on 2012-11-08
Clean out the log directory. It's not necessarily subdirectories in there that contain big files, /var/log itself can contain them or can contain multiple 'versions' of the same file.

Look at dates of files and delete older ones. Check sizes with _ls -lS /var/log_.
Once cleaned up, keep an eye on files in that directory to see how fast they grow. If you have errors somewhere, some files can grow substantially.

---

### Post by NikTh on 2012-11-08
A graphical applications that can cleanup you system from cache and other things is Ubuntu-Tweak tool. 

To install it, run bellow commands with order 

```
sudo add-apt-repository -y ppa:tualatrix/ppa
sudo apt-get update ; sudo apt-get -y install ubuntu-tweak
```Then open it and start the janitor to clean up. 
Although I'm not agree with such tools , sometimes are useful. **Be careful with old kernels removal**. Do not remove them all, leave one Kernel as a backup. (Usually the most new)

You can run the same command for /var/log folder and see the sizes of each file in there. 
```
sudo du -h /var/log
```
**EDIT:**Also take a look inside this folder 
```
du -h .local/share/Trash/
```
Thanks

---

### Post by Impavidus on 2012-11-08
Installing a clean-up tool when you're already out of disk space may be a little difficult (it might work in a live session, I've no experience with that), but if you've already found the big log files in the terminal, you can delete them with```
sudo rm filename.log.number.gz
```substituting the correct name and number.

As long as you haven't solved the underlying problem the logs will continue to grow rapidly, so keep an eye on them and remove anything that you don't need and grows too big. Deleting files in a graphical file manager is also possible, but a bit more tricky as you probably have to be root and you should delete them right away, not put them in a waste bin.

PS: My log directory is 22MB, wich should be normal.

---

### Post by pjstock on 2012-11-08
> **Wim Sturkenboom said:**
> Clean out the log directory. It's not necessarily subdirectories in there that contain big files, /var/log itself can contain them or can contain multiple 'versions' of the same file.

Look at dates of files and delete older ones. Check sizes with _ls -lS /var/log_.
Once cleaned up, keep an eye on files in that directory to see how fast they grow. If you have errors somewhere, some files can grow substantially.

Thanks

and Wow! doing a detailed list (I really am not very good with Terminal commands) but I see that I have these rather huge files:

Kern.log = 8.7Gb
syslog = 2.9Gb
Kern.log.1 = 1.6gb

Can I delete these without fear of fouling things up?

(although when I try to delete Kern.log.1 which seems to be a legacy version of Kern, the DELETE option is greyed out and not available.
OK, that sudo rm command seems effective. I knocked out kern.log.1 and now have 2Gb which is breathing room. Can I delete Kern.log and syslog and have them regenerate as nice small fresh versions?)

---

### Post by Wim Sturkenboom on 2012-11-08
Not sure; I would delete them and reboot the system. They should be regenerated after that.

But that's at own risk, which, as said, I would take.

The reason why they are so big is possibly your attempts to get the wifi working.

PS
When booting from a liveCD / liveUSB, it's safe to remove it

---

### Post by Bashing-om on 2012-11-08
If I may make another interjection. In the var/log/ directory -> any files ending in".gz" are old compressed files and may be safely removed. To see these files do in terminal:
```
ls -la /var/log/
```then to remove a un-needed file do:
```
sudo rm /var/log/auth.log.2.gz
``` where "auth.log.2.gz" is an example of a file name, substitute this filename with any others ending in "gz". ( It is my prefernce to do things slowly - one file at a time )

As others have advised, look at your logs and make a determination for the root cause of such large logs //and correct the problem !
[INDENT]just try'n to help <== BDQ
 
[/INDENT]

---

### Post by pjstock on 2012-11-08
good news. free spae 14.1gb
thanks for your help.
Peter

> **Wim Sturkenboom said:**
> Not sure; I would delete them and reboot the system. They should be regenerated after that.

But that's at own risk, which, as said, I would take.

The reason why they are so big is possibly your attempts to get the wifi working.

PS
When booting from a liveCD / liveUSB, it's safe to remove it

Interesting.
I find myself today (after not having used the system for several days and then only very seldom since I last posted here.) down to 1Mb Free Space again.

Kern.log.1 (yesterday) had ballooned back up to 13.5Gb
and I deleted it again.

But why is this Kern.log always ballooning and how do I managed it so that it doesn't. 
The rm rm rm seems like a kluge and not stable as I would hope.

Peter

---

### Post by Bashing-om on 2012-11-12
pjstock; 

The log filling up indicates a serious error in the operating system that the logs are advising you of.

Use the "log file viewer" utility(12.04: dash->search term "log"-> icon) to read the log and see if you can determine the source of the errors.

As this thread has been marked as solved, begin a new post if help is needed to read the log and determine what is at fault.
[INDENT]try'n to help ==> BDQ

[/INDENT]

---

