---
title: "Cron job to delete folders based on last modification date"
date: 2012-06-18
forum: New to Ubuntu
---

### Post by freethnker on 2012-06-18
We have a ubuntu server at my workplace set up as a backup box to store customers' files when they need a backup restore. We have a main folder named 'backup' and inside we create folders for each client based on the client's name, eg "jdoe" for John Doe. We then place their documents, etc. into that folder. The backup box is updated once a month, but otherwise it is not connected to the internet for security purposes. 

We're looking to create a cron job to delete the folders after 3 days, based on each folder's creation date (I'm assuming this is also the last modification date). We want  crontab to look at the client-name folders inside the 'backup' directory, and NOT the contents  inside the client-name folders to decide the date. In other words, we want the folders deleted with their contents, making sure that only the last modification date of the client-name folder is used to determine when to delete. We've had bad cron jobs in the past that would delete files inside client-name folders prematurely, leaving the folders. Any help would be greatly appreciated. 

Also, let me know if a php script would do a better job with this.

---

### Post by papibe on 2012-06-18
Hi freethnker. Welcome to the forums!

I wonder how much help do you need.

These are some general pointers. Tell us if you need more details:
[LIST]
[*]I think a bash script will do the job more efficiently than a php script.
[*]You can easily find file and folders which modification time is older that 3 days by using the 'find' command. For instance:```
find -mtime +3
```
[*]To automate a script using crontab, take a look at this [tutorial]("https://help.ubuntu.com/community/CronHowto").
[/LIST]
I hope that points you in the right direction.
Regards.

---

### Post by David Andersson on 2012-06-18
> **freethnker said:**
>  The backup box is updated once a month, (...) a cron job to delete the folders after 3 days
I don't get it. Should the backup be removed 27 days before there is a new backup? (You don't have to answer if everyone else seems to understand.)

> **freethnker said:**
> 
 based on each folder's creation date (I'm assuming this is also the last modification date). 
There is no "creation date" in Ubuntu. Unix files used to have timestamps for "creation", "modified", and "access". But now only the "modified" is reliable and useful. The modified time for a folder is basically the last time a file was created, removed or renamed in that folder (or when the folder was created if nothing have been added to it). That may be okey if files and subfolders are copied to the folder all at once. If there are subfolders and files are copied incrementally, there may be newer files in a subfolder that is not reflected in the modification time of the top folder.

> **freethnker said:**
> We want  crontab to look at the client-name folders inside the 'backup' directory, and NOT the contents  inside the client-name folders to decide the date.
Use find -maxdepth. Command **find /backup/*/ -maxdepth 0 -mtime +3** will test the custom folders only.

---

### Post by freethnker on 2012-06-18
> **David Andersson said:**
> I don't get it. Should the backup be removed 27 days before there is a new backup? (You don't have to answer if everyone else seems to understand.)

There may be many backups in there, we just want each client-folder be deleted 3 days after we created that folder and copied client's stuff in it. 

> **David Andersson said:**
> Use find -maxdepth. Command **find /backup/*/ -maxdepth 0 -mtime +3** will test the custom folders only.

Does -maxdepth () mean that the search for modified date will only be executed on the client-name folders, but not inside them? If yes, than this is exactly what I was looking for. 

I will run some tests. Thanks for your help!

---

### Post by anewguy on 2012-06-18
I'm still a little confused here myself.  You back up monthly, but you want to delete everything dealing with the client after 3 days?  Does the client have their backups or some sort of redundancy?  I'm sure you know what you're doing and we just don't understand.  I come from a tech background myself, and disaster recovery was something we kept very sacred.  We had redundancy in the way of raid,  Oracle database set to archive everything, in-house nightly backups, in-house weekly backups, in-house montly backups, as well as dups of weekly and monthly off site in storage facitility inside old limestone caves.

> There may be many backups in there, we just want each client-folder be deleted 3 days after we created that folder and copied client's stuff in it. 

So, I'm sure you must have other things happening, otherwise we have a hard time understand backing up monthly and deleting it all after 3 days.  I hope you can understand our dilema, and perhaps explain a little more about what you are doing.  That way we can help you with what's best, including help with the script.  You see, if you want to wait 3 days and then delete everything in each of the folders that were updated 3 or more days ago, it makes it clearer for how we need to help you.

Dave ;)

---

### Post by freethnker on 2012-06-18
> **anewguy said:**
> I'm still a little confused here myself.  You back up monthly, but you want to delete everything dealing with the client after 3 days?.....

Sorry for the confusion, but as stated in the original post, we do not backup the data on the server box at all. We run system updates once a month. We keep the server box disconnected from the internet pretty much all the time. The only time we connect it is about once a month to perform ubuntu system updates. 

As to the client folders, those are the ones we need to have deleted automatically 3 days after modification date. 

Hope this clarifies things.

---

### Post by anewguy on 2012-06-19
This from your opening post may be what is confusing us:

> We have a ubuntu server at my workplace set up as a backup box to store customers' files when they need a backup restore

Is what you are saying by you don't back up any data mean you are only trying to keep a backup of the initial setup?

At any rate, I'm not sure about copying things to the server and then deleting them.  Is what you are saying is that you backup to the server (whatever that backup is) once a month, and those backups are created within 3 days, so when finished you want to delete the old folders (i.e., those not created during the current monthly backup)?

At any rate, given what papibe posted, you should be able to modify the find statement to include only the folders within a certain folder (like "backups").  It may be possible to pipe that output to rmdir - I'm just not sure on deleting a folder that isn't empty.  Perhaps 2 commands are needed, 1 to pipe the output to rm to remove all the files in the folder(s), then a 2nd run to output to rmdir to remove the folders themselves.

I may be way off base here, so I'm hoping that if someone has better ideas that they will post them here.  I'm sure there has to be a simple way to do this.

Dave ;)

---

### Post by freethnker on 2012-06-20
Let's disregard the first paragraph of my initial post as it seems to be causing confusion. 


All I want is for the directories (aka folders with names based on the clients' name, for example a folder for John Doe containing his files would be named 'jdoe') to be deleted after 3 days. 

I've tested this this cron job so far:
```
0 0 * * * find /home/user/Backups/* -maxdepth() -mtime +1 delete
```I put +1 so that I don't have to wait 3 days to see if it works. Checked this morning and the folder's still there with its contents. Any ideas?

---

### Post by anewguy on 2012-06-20
Since they are non-empty folders, as you know things rmdir require a --force if I remember correctly.  Is it failing because the folder is not empty? 

For example, I think the -delete option (your sample show just delete - maybe I don't remember correctly) implies it will follow a tree.  However, with just the * I would think - and I don't have a clue - that it would not delete files within a folder (*.*, which you obviously don't want to do on the Backups folder itself).  If the result is no files are deleted, so there are still files in the folder, I don't know if the -delete option would work on a folder or not.  Perhaps you already know this and I'm just shooting in the dark ;)

Also, I *think* the -type d option says directories, but I'm not sure about that either.

It might be interesting to try your same command manually but change the "delete" (or -delete ??) to -print and see what it thinks it is processing.

Dave ;)

---

### Post by David Andersson on 2012-06-20
> **freethnker said:**
> 
I've tested this this cron job so far:
```
0 0 * * * find /home/user/Backups/* -maxdepth() -mtime +1 delete
```I put +1 so that I don't have to wait 3 days to see if it works. Checked this morning and the folder's still there with its contents. Any ideas?

It's not parenteses, it's zero: **-maxdepth NUMBER**

Just "delete" won't work. You must tell find to execute a "rm" command or pipe the found file names to something else that applies the "rm" command. In find the option is: -**exec COMMAND [COMMAND_OPTIONS] {} [COMMAND_OPTIONS] +** or **-exec COMMAND [COMMAND_OPTIONS] \;**

The "+" syntax must have a "{}" placeholder where one or more filenames will be inserted. The "\;" syntax will execute exactly once for each filename. The filename is inserted last in the -exec command. See **man find**

There is a "-delete" option for find. It will delete one file at a time. Trying to use it to recursively delete these directories would make the find expression very much more complicated and bug prone.

There should be a log file where you can see error messages from cron jobs.

---

### Post by anewguy on 2012-06-20
OK, I've been doing some testing here.  I created a folder in my home folder called "testit".  Within that I created 3 folders - test1, test2 and test3.  I copied the same file into all 3 folders.  Then I copied your statement as show in your post and pasted into a terminal, modifying it to fit my folder path, and I get the following:

dave@dave-desktop:~$ find /home/testit/* -maxdepth() -mtime +1 delete
bash: syntax error near unexpected token `('

In looking at the man page for find, I don't see a maxdepth option - I may have missed it but I didn't see it.

I would think this would mean your statement actually fails when it is run.  

Then of course, I realized that the /home folder doesn't exist in my example, so I modified the statement to:

find /home/dave/testit/* -depth -prune  -delete 

A "ls" of /home/dave/testit then showed no subfolders - the 3 test"x" subfolders were gone.

Here's the terminal screen from when it worked:

dave@dave-desktop:~$ mkdir testit
dave@dave-desktop:~$ cd testit
dave@dave-desktop:~/testit$ mkdir test1
dave@dave-desktop:~/testit$ mkdir test2
dave@dave-desktop:~/testit$ mkdir test3
dave@dave-desktop:~/testit$ cd ..
dave@dave-desktop:~$ cp GoogleEarthLinux.bin
cp: missing destination file operand after `GoogleEarthLinux.bin'
Try `cp --help' for more information.
dave@dave-desktop:~$ cp GoogleEarthLinux.bin testit/test1
dave@dave-desktop:~$ cp GoogleEarthLinux.bin testit/test2
dave@dave-desktop:~$ cp GoogleEarthLinux.bin testit/test3
dave@dave-desktop:~$ ls -al testit
total 20
drwxrwxr-x  5 dave dave 4096 Jun 20 13:15 .
drwxr-xr-x 34 dave dave 4096 Jun 20 13:15 ..
drwxrwxr-x  2 dave dave 4096 Jun 20 13:16 test1
drwxrwxr-x  2 dave dave 4096 Jun 20 13:16 test2
drwxrwxr-x  2 dave dave 4096 Jun 20 13:16 test3
dave@dave-desktop:~$ find /home/dave/testit/* -depth -prune  -delete 
dave@dave-desktop:~$ ls -al testit
total 8
drwxrwxr-x  2 dave dave 4096 Jun 20 13:16 .
drwxr-xr-x 34 dave dave 4096 Jun 20 13:15 ..
dave@dave-desktop:~$ 


Perhaps this can help you in some way.

Dave ;)

EDIT:  Tried this same thing with -print, and it showed all the files in the subfolders.  So I checked man, found out that -prune doesn't mean anything when used with -delete, as -delete implies -depth, and -depth is apparently not limited by -prune.  At least that's how it appears.  You might try playing around some more and see if you find differently.  If you can get it to prune, then it would run faster as it wouldn't be deleting the files first, but then again, maybe it won't delete a non-empty folder as I mentioned above.

---

### Post by David Andersson on 2012-06-20
( quoting with my bold face: )
> **anewguy said:**
> Then I copied **your** statement as show in **your** post and pasted into a terminal, modifying it to fit my folder path, and I get the following:

dave@dave-desktop:~$ find /home/testit/* -maxdepth() -mtime +1 delete
bash: syntax error near unexpected token `('


[s]No, that's **your** statement in **your** post.[/s] My was -maxdepth 0 and -maxdepth NUMBER

> **anewguy said:**
> 
Then of course, I realized that the /home folder doesn't exist in my example, so I modified the statement to:

find /home/dave/testit/* -depth -prune  -delete 


As I said, I would not recommend the "-delete" option. There would be different conditions what files to test for -mtime and what files to -delete. It would be unnecessary complex in one find statement. I recommend go for one of the -exec options.

EDIT: Sorry. Confused freetinker with anyguy. Still somewhat confused.

---

### Post by anewguy on 2012-06-20
Wan't mine - it freethinker's, and that's what I was going off of:

> freethnker 	
Re: Cron job to delete folders based on last modification date
Let's disregard the first paragraph of my initial post as it seems to be causing confusion.


All I want is for the directories (aka folders with names based on the clients' name, for example a folder for John Doe containing his files would be named 'jdoe') to be deleted after 3 days.

I've tested this this cron job so far:
Code:

0 0 * * * find /home/user/Backups/* -maxdepth() -mtime +1 delete

I put +1 so that I don't have to wait 3 days to see if it works. Checked this morning and the folder's still there with its contents. Any ideas? 



I never made a recommendation one way or the other on what freethinker should do, simply showed a way to make what they showed work.

I'm not arguing with you - why do you want to argue with me?

---

### Post by freethnker on 2012-07-06
We've been trying several modifications based on the input received from this post but it looks like we're still missing something. 

The following command doesn't seem to work properly: 
```
0 0 * * * find /home/user/Backups/* -maxdepth 0 -mtime +3 -delete
```Neither does this one: 
```
0 0 * * * find /home/user/Backups/* -maxdepth 0 -mtime +3 -exec rm -r {} \;
```What we're testing right now is this:
```
0 0 * * * find /home/user/Backups/* -maxdepth 0 -mtime +3 | xargs -exec rm -r {} \;
```Would appreciate more feedback.

---

