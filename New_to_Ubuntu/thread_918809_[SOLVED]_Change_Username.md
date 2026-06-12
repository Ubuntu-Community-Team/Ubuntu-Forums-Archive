---
title: "[SOLVED] Change Username"
date: 2008-09-13
forum: New to Ubuntu
---

### Post by 44tr on 2008-09-13
My son wants to change his username on his computer (I am the admin).  I went to users and groups and unlocked, but the username is greyed out.  Is there a way to change directly, or a simple way to do it effectively?

Perhaps create a new account, rename his current home directory to the new one, and then delete old account?  What is wrong with this idea?  should I copy the old home directory instead of move.  I seem to recall that the command for renaming or coping an entire directory tree is a little different than cp or mv (is it cp -r, mv -r ?). I still have trouble reading the man pages and being confident that the commands will do what I want; since this isn't a good area for experimenting, an example command would be very helpful.  Thanks.

---

### Post by Sbarton on 2008-09-13
Maybe it can be done by using ```
gksudo nautilus
```, then try!
regards

---

### Post by 44tr on 2008-09-13
I did open nautilus using gksudo; then unlocked the users and groups GUI, but username was still grayed out.  Is that what you meant?

---

### Post by unutbu on 2008-09-13
[SIZE="4"]Edited: 2008-09-13:
**WARNING: The instructions below do not work properly! Please do not use these instructions.**[/SIZE]
---------------------------------------

Suppose your username is OLDNAME. The following  will change your username to NEWNAME, and it will change your home directory to /home/NEWNAME.

[list=1]

[*]Log in as OLDNAME
[*]In a terminal type```


sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
sudo groupmod --new-name NEWNAME OLDNAME

```


Now comes the tricky part. Some programs hard code the names of certain paths in dot files. If you simply copy these over into the new account, some programs will break or complain about missing files. Editing all the dot files by hand is often prohibitively difficult. So here is a script to do the job for us.


[*]Save the attached script, alter_files.py, to your home account.
[*]Make the script executable:
```

chmod 755 alter_files.py

```
[*]Run it like this:
```
./alter_files.py -p '/home/OLDNAME' -r '/home/NEWNAME' -b /home/NEWNAME
```
This searches every file in /home/NEWNAME and replaces every occurrence of /home/OLDNAME with /home/NEWNAME.
[*]Log out, then log back in as NEWNAME.
[/list]

---

### Post by 44tr on 2008-09-13
Awesome!  I will attempt this when my son gets home and tells me what he wants his username changed TO.  Thanks.

---

### Post by 44tr on 2008-09-13
OK, I followed all directions and the account name is changed.  I got a number of errors at the end of the script though, and some things don't work now.  Can I run the script again logged in under NEWNAME and post the errors here or will that cause more problems?:confused:

---

### Post by spiderbatdad on 2008-09-13
First find the user id of oldname by running the command ```
id
```while logged in...should be 1002 or 1003 for example if you are id 1000. Or check the file /etc/passwd and find the user id next to the username.

```
sudo -i
 id oldname
 usermod -l newname oldname
 id newname
 id oldname
```

```
 id newname
 usermod -u 1002 newname
 id newname
```

---

### Post by unutbu on 2008-09-13
Please post the errors you see after running the script.

You can run it again from the newuser account if necessary.

If the errors are all the same in nature, you don't have to post them all; a few would be sufficient.

---

### Post by 44tr on 2008-09-13
> **spiderbatdad said:**
> First find the user id of oldname by running the command ```
id
```while logged in...should be 1002 or 1003 for example if you are id 1000. Or check the file /etc/passwd and find the user id next to the username.

```
sudo -i
 id oldname
 usermod -l newname oldname
 id newname
 id oldname
```

```
 id newname
 usermod -u 1002 newname
 id newname
```

Is this in response to the errors I got and how to fix or what you think I should have done instead?

---

### Post by 44tr on 2008-09-13
> **unutbu said:**
> Please post the errors you see after running the script.

You can run it again from the newuser account if necessary.

If the errors are all the same in nature, you don't have to post them all; a few would be sufficient.

Here is the output, truncated with ... when there are many similar entries.  It may help to know that NEWNAME is 'druid' and OLDNAME is 'aquown' (no, I'm not making this up; it's what my son wants ...).  

```

...
[Errno 2] No such file or directory: '/home/druid/.mozilla/firefox/dzxts3py.default/lock'
Cannot open /home/druid/.mozilla/firefox/dzxts3py.default/lock
altering /home/druid/.mozilla/firefox/dzxts3py.default/pluginreg.dat

altering /home/druid/.wine/drive_c/windows/...
altering /home/druid/.wine/drive_c/windows/profiles/aquown/Desktop
[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/Desktop'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/Desktop
altering /home/druid/.wine/drive_c/windows/profiles/aquown/My Pictures
[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/My Pictures'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/My Pictures
altering /home/druid/.wine/drive_c/windows/profiles/aquown/My Music
[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/My Music'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/My Music
altering /home/druid/.wine/drive_c/windows/profiles/aquown/My Documents
[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/My Documents'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/My Documents
altering /home/druid/.wine/drive_c/windows/profiles/aquown/My Videos
[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/My Videos'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/My Videos
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Desktop/WALL-E.lnk

altering /home/druid/.wine/drive_c/Program Files/...
altering /home/druid/.wine/drive_c/Program Files/THQ/Disney-Pixar/WALL-E/LIBPC_Common/shaders/skin_shadow.vhl
[Errno 24] Too many open files: '/tmp/tmp-QwifS'
IOError:
Traceback (most recent call last):
  File "./alter-files.py", line 85, in <module>
  File "./alter-files.py", line 63, in alter
NameError: global name 'e' is not defined
Error in sys.excepthook:
Traceback (most recent call last):
  File "/usr/lib/python2.5/site-packages/apport_python_hook.py", line 38, in apport_excepthook
ImportError: No module named packaging_impl

Original exception was:
Traceback (most recent call last):
  File "./alter-files.py", line 85, in <module>
  File "./alter-files.py", line 63, in alter
NameError: global name 'e' is not defined
druid@chris-desktop2:~/scripts$ 

```

That's it. Let me know if I left something out you need.  There are well over a 1000 lines of output.

---

### Post by unutbu on 2008-09-13
[list=1]
[*]As druid run:
```
cd ~/.wine/drive_c/windows/profiles
mv aquown druid
```
This will fix the error:
```

[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/My Videos'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/My Videos

```
Hopefully there aren't too many more directories named aquown...

[*]I made a change to the script so the output will not be so verbose.
Please download the script again from the previous post.

This should make it easier for you to isolate the errors.
[*]To increase the size of your terminal buffer, go to Edit>Preferences>Current Profile
Click the Scrolling tab and increase Scrollback to 100000. This should not be necessary because of the change in the script, but it may be useful to you at some point in the future.
[*]Try running this instead:
```
find /home/druid -maxdepth 1 -name \.\* -print0 | xargs -0 ./alter-files.py -p '/home/aquown' -r '/home/druid' -b 
```
This will alter only top-level dot files and directories. Subfiles of a top-level dot directory will be altered too, however, but this is what we want.

If you get any more errors, please post.
[*]Also post the output to these commands:
```

cd /home/druid
find . -type f -print | wc -
cat /proc/sys/fs/file-max

```
The find command will count how many files there are  in the druid account. The cat command will tell us the maximum number of files the OS can have open at one time. This might be related to an error in the output. 
[*]What programs or settings are not working?
[/list]

---

### Post by 44tr on 2008-09-13
> **unutbu said:**
> [list=1]
[*]As druid run:
```
cd ~/.wine/drive_c/windows/profiles
mv aquown druid
```
This will fix the error:
```

[Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/aquown/My Videos'
Cannot open /home/druid/.wine/drive_c/windows/profiles/aquown/My Videos

```
Hopefully there aren't too many more directories named aquown...

[*]I made a change to the script so the output will not be so verbose.
Please download the script again from the previous post.

This should make it easier for you to isolate the errors.
[*]To increase the size of your terminal buffer, go to Edit>Preferences>Current Profile
Click the Scrolling tab and increase Scrollback to 100000. This should not be necessary because of the change in the script, but it may be useful to you at some point in the future.
[*]Try running this instead:
```
find /home/druid -maxdepth 1 -name \.\* -print0 | xargs -0 ./alter-files.py -p '/home/aquown' -r '/home/druid' -b 
```
This will alter only top-level dot files and directories. Subfiles of a top-level dot directory will be altered too, however, but this is what we want.

If you get any more errors, please post.
[*]Also post the output to these commands:
```

cd /home/druid
find . -type f -print | wc -
cat /proc/sys/fs/file-max

```
The find command will count how many files there are  in the druid account. The cat command will tell us the maximum number of files the OS can have open at one time. This might be related to an error in the output. 
[*]What programs or settings are not working?
[/list]

Here is the output to running the new script version, then the other commands you suggested.  As far as changes, I can't download from the browser, the panel backgrounds are gone, probably some other stuff I haven't had time to track down but the other account on the computer is OK.

```
druid@chris-desktop2:~/scripts$ ./alter-files.py -p '/home/aquown' -r '/home/druid' -b /home/druid
IOError: [Errno 2] No such file or directory: '/home/druid/.mozilla/firefox/dzxts3py.default/lock'
Cannot read /home/druid/.mozilla/firefox/dzxts3py.default/lock
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/Desktop'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/Desktop
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Pictures'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Pictures
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Music'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Music
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Documents'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Documents
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Videos'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Videos
IOError: [Errno 24] Too many open files: '/tmp/tmp8KTalJ'
Cannot write to /tmp/tmp8KTalJ
druid@chris-desktop2:~/scripts$ 
druid@chris-desktop2:~/scripts$ find /home/druid -maxdepth 1 -name \.\* -print0 | xargs -0 ./alter-files.py -p '/home/aquown' -r '/home/druid' -b
IOError: [Errno 2] No such file or directory: '/home/druid/.mozilla/firefox/dzxts3py.default/lock'
Cannot read /home/druid/.mozilla/firefox/dzxts3py.default/lock
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/Desktop'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/Desktop
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Pictures'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Pictures
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Music'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Music
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Documents'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Documents
IOError: [Errno 2] No such file or directory: '/home/druid/.wine/drive_c/windows/profiles/druid/My Videos'
Cannot read /home/druid/.wine/drive_c/windows/profiles/druid/My Videos
IOError: [Errno 24] Too many open files: '/tmp/tmpOWZI0B'
Cannot write to /tmp/tmpOWZI0B
druid@chris-desktop2:~/scripts$ cd /home/druid
druid@chris-desktop2:~$ find . -type f -print | wc -
   3917    4955  268795 -
druid@chris-desktop2:~$ cat /proc/sys/fs/file-max
101660
druid@chris-desktop2:~$ 

```

thanks for help.

---

### Post by unutbu on 2008-09-13
Okay. I want you back up and running without so many broken apps as quickly as possible. So let's fix the browser first semi-manually. 

But first a question:

If we were to reset the GNOME defaults (which control things like panel backgrounds) to be as they were when aquown was first created, would it take a lot of work to manually redo the preferences? If you are okay with redo-ing the preferences, then try this:
[http://ubuntuforums.org/showpost.php?p=5312430&postcount=21](http://ubuntuforums.org/showpost.php?p=5312430&postcount=21)



Now to fix firefox:
```

quit firefox
mv ~/.mozilla ~/.mozilla-20080913
start firefox

```
It will create a new profile for you. Now use nautilus to copy the bookmarks file from the original .mozilla folder into the new one. The bookmarks file will be located in 
```

~/.mozilla-20080913/firefox/*.default/bookmarks.html

```
Move it to
```

~/.mozilla/firefox/*.default/bookmarks.html
```

You can also move prefs.js similarly to restore firefox preferences.

---

### Post by 44tr on 2008-09-13
Sorry I took so long.  I had a dinner engagement.  Now back to work.

---

### Post by starcannon on 2008-09-13
I changed my user name quite easily by making a new account with my desired user name. Then I moved all the files I wanted to keep from the old account to the new account. Bookmarks and email for me came over with no problems, if they hadn't, I'd have just exported them and imported them using each respective browser.

GL

---

### Post by 44tr on 2008-09-13
> **starcannon said:**
> I changed my user name quite easily by making a new account with my desired user name. Then I moved all the files I wanted to keep from the old account to the new account. Bookmarks and email for me came over with no problems, if they hadn't, I'd have just exported them and imported them using each respective browser.

GL

perhaps that might have worked, but the files and modifications were pretty extensive.  It isn't just copying over the home directory.

---

### Post by 44tr on 2008-09-13
The bookmarks were already trashed too.  I tried copying from the backup bookmark#####.json (most recent that looks like it has everything)and copying to bookmarks.html in the new profile but that doesn't seem to work/be recognized.  How to restore?  Never mind.  Got preferences and bookmarks restored.  Next...

---

### Post by 44tr on 2008-09-13
I think I have firefox fully operational and everything I see working, though still have some preferences left to deal with.  How to finish converting over the aquown files to druid?  It will be fairly painful to recreate those things from scratch.  My son's wine applications for instance have a number of saved games, etc.  It won't be the end of the world if they are trashed, but he won't be happy.  thanks.

---

### Post by unutbu on 2008-09-13
I'm really sorry my instructions have caused so many problems. I think from now on my answer to the question "how do I change my username" will have to be "I don't think it is possible" -- at least not without blood, sweat and tears. 

I don't use wine so the pitfalls associated with converting the .wine directory are things I had not anticipated. 

As long as the username aquown appears only in text files (like all GNOME configuration files),  the alter-files.py script (once fixed) will be able to convert them. But if the wine directory has files which encoded '/home/aquown' in some binary format, we will be in trouble.

I've figured out why we are getting errors when running alter-files.py. 
It has to do with the maximum number of files a process can open. I'm working on a fix.

I've also started a thread here regarding the technical problem with the script: [http://ubuntuforums.org/showthread.php?t=919340](http://ubuntuforums.org/showthread.php?t=919340). When a solution is found, I'll be able modify alter-files.py to complete the renaming.

In the meantime, I should point out there is a way to back-out of the changes so far:

```
cd ~/.wine/drive_c/windows/profiles
mv druid aquown 
./alter-files.py -p '/home/druid' -r '/home/aquown' -b /home/druid

sudo usermod --login aquown --home /home/aquown -m druid
sudo groupmod --new-name aquown druid
```
I'm not quite sure of the state of the .mozilla folder, so I didn't try to make commands for restoring that...

If you are willing to continue trying the conversion, I'm willing to help you as best I can. I just wanted you to know there is a way to back-out of the changes.

---

### Post by 44tr on 2008-09-14
Don't worry about the little pitfalls encountered in trying to help.  I understand the risks and I appreciate your time.  I'm considerably more conservative when it comes to messing with my main system, but my son's computer doubles as a bit of a test bed.  What is the worst that could happen?  My 10 year old can't play the games he wants to until I reinstall and configure from scratch?  Not the way I want to spend my time, but also not having a hurricane flood my house ...

So this is a good way to learn, and I would like to continue the process of changing.  If wine becomes a problem, I can blow those games away and reinstall; they weren't that bad to install; son will just have to start over on a few things.

Thanks for continued help; hopefully you are learning something useful as well and I don't mean learning to avoid helping people. :lolflag:

What next?

---

### Post by Corin-EU on 2008-09-14
On a Linux system, files have user and group ownership.

These are actually represented by numeric values which are then displayed by eg ls as strings found by matching the numeric id with the corresponding username and group from /etc/passwd and /etc/group.

So if you just want to change the login username of a user, go to /etc/passwd and change the entry there.

eg

fluser:x:1001:1000:Freddy Luser:/home/users/fluser:/bin/tcsh

to

frederick:x:1001:1000:Frederick Luser:/home/users/fluser:/bin/tcsh

In /etc/shadow you will also have to change the corresponding entry similar to

fluser:$1$wdfsdf98dfasdfs/:13874:0:99999:7:::

to

frederick:$1$wdfsdf98dfasdfs/:13874:0:99999:7:::

The problem now arises as to whether or not you want to rename the home directory from fluser to frederick.

If so, you will need to do

mv /home/users/fluser /home/user/frederick

and also change the penultimate field in the /etc/passwd file

from

frederick:x:1001:1000:Frederick Luser:/home/users/fluser:/bin/tcsh

to

frederick:x:1001:1000:Frederick Luser:/home/users/frederick:/bin/tcsh

The only outstanding issue is if the old path

/home/users/fluser

is hardcoded in any scripts or configuration files, but that usually only happens with user intervention since well behaved applications refer to the home path either through $HOME or better through the entry in the /etc/passwd file.

Now, is there something which I overlooked?

---

### Post by unutbu on 2008-09-14
The problem in alter_files.py has been fixed.
Please note that the script has been renamed alter_files.py instead of alter-files.py; the dash has been changed to an underscore for a technical python reason.

The old version had a problem which made the script stop after processing around 1024 files. The new version can deal with an unlimited number of files.

The old version listed every file it looked at, regardless of whether it made any changes or not. The new version lists only those files that are truly altered.

The alter_files.py script can be found in this post:
[http://ubuntuforums.org/showpost.php?p=5782217&postcount=4](http://ubuntuforums.org/showpost.php?p=5782217&postcount=4)

---

### Post by unutbu on 2008-09-14
Corin-EU, I too used to edit /etc/passwd and /etc/group manually. It was fun and it helped me learn a bit about how the system works. However, I think it is safer and simpler to use this command:
```

sudo usermod --login NEWNAME --home /home/NEWNAME -m OLDNAME
```
It accomplishes the same thing as all the commands you listed.

On Ubuntu systems the fluser home account would be located at /home/fluser, not /home/users/fluser.

Also note that you need to alter /etc/group and /etc/gshadow. Instead of doing it manually, I think it is safer to use
```

sudo groupmod --new-name NEWNAME OLDNAME

```

The real problem happens after you execute these commands. 

There are lots of programs that hard code paths into their configuration files. I agree that it would be nice if apps took into consideration that a user may want to change username, and read the $USER environment variable or use relative paths, but this too could cause problems. 

Suppose you use GNOME to set your background image. GNOME saves the path to the background image in one of its configuration directories.

Suppose you have a music playlist. Each song  has its entire path hard coded in the .m3u file.

Wine presents a particularly difficult problem. It creates a directory called
~/.wine/drive_c/windows/profiles/USERNAME. So when you change username, you also have to hunt down this directory and rename it manually too. 

The ~/.wine directory may use symlinks which also contain the old USERNAME. 

My list of things that need changing is incomplete. I do not know the full extent of the changes that need to be made, and the list will continue to grow depending on what apps a person uses.

---

### Post by unutbu on 2008-09-14
rt44, perhaps try
```

./alter_files.py -p 'aquown' -r 'druid' -b /home/druid
```

This will change every occurrence of 'aquown' into 'druid' in every file in /home/druid.
Thankfully, aquown is a pretty unusual string so I think it should be safe. 
If a user had a name like 'rick' then this would be extremely dangerous because a file
with the word 'trick' would be changed into 'tdruid'. 

The advantage of searching for 'aquown' instead of '/home/aquown' is that it will find more occurrences, and thus hopefully be less work for you to do manually.

Again, it all hinges on aquown being unique enough that it does not occur in any file in any other situation than as a username.

Also, please post the output of the following commands:
```

cd /home/druid
find  . \( -ilname '*aquown*' -o -iwholename '*aquown*' \) -print
```

If there is a lot of output, run this instead:
```

find  . \( -ilname '*aquown*' -o -iwholename '*aquown*' \) -print > problem-files
bzip2 problem-files

```
Then post problem-files.bz2 as an attachment.

These commands will list every file and every symlink that contains the string 'aquown'.
Knowing what the problem files look like will help me craft a batch rename command.

---

### Post by 44tr on 2008-09-14
> **unutbu said:**
> rt44, perhaps try
```

./alter_files.py -p 'aquown' -r 'druid' -b /home/druid
```

This will change every occurrence of 'aquown' into 'druid' in every file in /home/druid.
Thankfully, aquown is a pretty unusual string so I think it should be safe. 
If a user had a name like 'rick' then this would be extremely dangerous because a file
with the word 'trick' would be changed into 'tdruid'. 

The advantage of searching for 'aquown' instead of '/home/aquown' is that it will find more occurrences, and thus hopefully be less work for you to do manually.

Again, it all hinges on aquown being unique enough that it does not occur in any file in any other situation than as a username.

Also, please post the output of the following commands:
```

cd /home/druid
find  . \( -ilname '*aquown*' -o -iwholename '*aquown*' \) -print
```

If there is a lot of output, run this instead:
```

find  . \( -ilname '*aquown*' -o -iwholename '*aquown*' \) -print > problem-files
bzip2 problem-files

```
Then post problem-files.bz2 as an attachment.

These commands will list every file and every symlink that contains the string 'aquown'.
Knowing what the problem files look like will help me craft a batch rename command.

OK, I ran the first command (took several minutes) and then the addtional ones that didn't have much output.  Here is the total result:

```
druid@chris-desktop2:~/scripts$ ./alter_files.py -p 'aquown' -r 'druid' -b /home/druid
altering /home/druid/.mozilla/firefox/ulzgyjge.default/Cache/64C585B0d01
altering /home/druid/.mozilla/firefox/ulzgyjge.default/Cache/173FDEA4d01
altering /home/druid/.mozilla/firefox/ulzgyjge.default/Cache/54A895B0d01
altering /home/druid/.mozilla/firefox/ulzgyjge.default/Cache/54A8A5B2d01
altering /home/druid/.mozilla/firefox/ulzgyjge.default/Cache/658C8473d01
altering /home/druid/.mozilla/firefox/ulzgyjge.default/Cache/64C58621d01
altering /home/druid/.wine/drive_c/windows/system32/Macromed/Shockwave 8/Install.log
altering /home/druid/.wine/drive_c/windows/profiles/druid/Application Data/Mozilla/registry.dat
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Desktop/WALL-E.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Application Data/Microsoft/Windows/GameExplorer/{53BD21F6-5859-11DD-B49B-00508DE93351}/PlayTasks/0/Play.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Application Data/Microsoft/Windows/GameExplorer/{53BD21F6-5859-11DD-B49B-00508DE93351}/PlayTasks/1/Configure.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Application Data/Microsoft/Windows/GameExplorer/{53BD21F6-5859-11DD-B49B-00508DE93351}/SupportTasks/0/Web - THQ.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Application Data/Microsoft/Windows/GameExplorer/{53BD21F6-5859-11DD-B49B-00508DE93351}/SupportTasks/1/Web - Heavy Iron.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Application Data/Microsoft/Windows/GameExplorer/{53BD21F6-5859-11DD-B49B-00508DE93351}/SupportTasks/2/Web - Asobo Studio.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/THQ/Disney-Pixar/WALL-E/Launch WALL-E.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/THQ/Disney-Pixar/WALL-E/Visit THQ website.lnk
altering /home/druid/.wine/drive_c/windows/profiles/All Users/Start Menu/Programs/THQ/Disney-Pixar/WALL-E/Uninstall.lnk
altering /home/druid/.wine/user.reg
altering /home/druid/.wine/userdef.reg
altering /home/druid/.wine/system.reg
altering /home/druid/.evolution/secmod.db
altering /home/druid/Desktop/croNous.desktop
altering /home/druid/Desktop/WALL-E.desktop
altering /home/druid/.config/tracker/tracker.cfg
altering /home/druid/.nautilus/saved-session-L6KYEU
altering /home/druid/.nautilus/saved-session-BDKYGU
altering /home/druid/.nautilus/saved-session-W68ZFU
altering /home/druid/.nautilus/saved-session-6RMEFU
altering /home/druid/.nautilus/saved-session-7TFIHU
altering /home/druid/.local/share/Trash/info/Panels.rar.trashinfo
altering /home/druid/.local/share/Trash/info/leonardo.zip.trashinfo
altering /home/druid/.local/share/Trash/info/__MACOSX.trashinfo
altering /home/druid/.local/share/Trash/info/WALL-E.desktop.trashinfo
altering /home/druid/.local/share/Trash/info/ [=.trashinfo
altering /home/druid/.local/share/Trash/info/NHL07.desktop.trashinfo
altering /home/druid/.local/share/Trash/info/leonardo.trashinfo
altering /home/druid/.local/share/Trash/info/scouting.odg.trashinfo
altering /home/druid/.local/share/Trash/files/NHL07.desktop
altering /home/druid/.local/share/applications/wine/Programs/THQ/Disney-Pixar/WALL-E/Uninstall.desktop
altering /home/druid/.local/share/applications/wine/Programs/THQ/Disney-Pixar/WALL-E/Visit THQ website.desktop
altering /home/druid/.local/share/applications/wine/Programs/THQ/Disney-Pixar/WALL-E/Launch WALL-E.desktop
altering /home/druid/.local/share/applications/wine/Programs/EA SPORTS/NHL07/Electronic Registration.desktop
altering /home/druid/.local/share/applications/wine/Programs/EA SPORTS/NHL07/Technical Support.desktop
altering /home/druid/.local/share/applications/wine/Programs/EA SPORTS/NHL07/Uninstall NHL07.desktop
altering /home/druid/.local/share/applications/wine/Programs/EA SPORTS/NHL07/EAsy Info.desktop
altering /home/druid/.local/share/applications/wine/Programs/EA SPORTS/NHL07/NHL07.desktop
altering /home/druid/.local/share/applications/wine/Programs/EA SPORTS/NHL07/Read Me.desktop
altering /home/druid/.local/share/applications/wine/Programs/croNous/croNous.desktop
altering /home/druid/.thumbnails/normal/b5be4514b74d32ca881e582994ca42bd.png
altering /home/druid/.thumbnails/normal/3127e19dbd4c9d001974d55509569dfd.png
altering /home/druid/.thumbnails/normal/710eea49bb7dc4e8bef74d0e12a8b5b9.png
altering /home/druid/.thumbnails/normal/ab23212e4b12b916a29333ca5281e36e.png
altering /home/druid/.thumbnails/normal/5f31cf3861264649551d3299d5aebb23.png
altering /home/druid/.thumbnails/normal/bc6e6d660265f0ad1f2af90a06cb9dec.png
altering /home/druid/.thumbnails/normal/a4cb07bac5026283ef1c1f998052b4bb.png
altering /home/druid/.thumbnails/normal/53126e8f939a1004e65d93912e2be8b6.png
altering /home/druid/.thumbnails/normal/ad2f864406e3f3eaa59f4fb311b76311.png
altering /home/druid/.thumbnails/normal/19e21b1fcd706eb16eefc4a25c65f226.png
altering /home/druid/.thumbnails/normal/f7c9de70ceb2f039cad95cf5a7d16a82.png
altering /home/druid/.thumbnails/normal/0b77f7642aeeebfc2c3fe8bfc00f0158.png
altering /home/druid/.thumbnails/normal/9eb6169ec47c44772fbf7e044fe1b942.png
altering /home/druid/.thumbnails/normal/5d403b0a07fed18638b3556bf6b749d8.png
altering /home/druid/.thumbnails/normal/a2f2f3fc5a77e04e485799dbe65ac148.png
altering /home/druid/.thumbnails/normal/c52516a879fece1121932cbcea90435a.png
altering /home/druid/.thumbnails/normal/688a2c50f62c00aae120005b84ea65df.png
altering /home/druid/.thumbnails/normal/372b9f45dda225847e0584098e09c254.png
altering /home/druid/.thumbnails/normal/4d7ec78408213636608249fb1f3dfbda.png
altering /home/druid/.thumbnails/normal/ae06aaec055386fa16af2d664e3ef6e3.png
altering /home/druid/.thumbnails/normal/728b8eb40d78c5bf35d9a2814e50feaf.png
altering /home/druid/.tremulous/base/autogen.cfg
altering /home/druid/.mozilla-20080913/firefox/dzxts3py.default/Cache/173FDEA5d01
altering /home/druid/.mozilla-20080913/firefox/dzxts3py.default/Cache/54A8FF10d01
altering /home/druid/.mozilla-20080913/firefox/dzxts3py.default/Cache/E0F1AA4Ed01
altering /home/druid/.mozilla-20080913/firefox/dzxts3py.default/Cache/658C8473d01
altering /home/druid/.mozilla-20080913/firefox/dzxts3py.default/formhistory.sqlite
altering /home/druid/.java/deployment/deployment.properties
altering /home/druid/.gnome2/f-spot/addins-setup.config
altering /home/druid/.adobe/Acrobat/8.0/Preferences/reader_prefs
altering /home/druid/.wesnoth/preferences
altering /home/druid/.fontconfig/3dfc8d3fb27f4b66b19900f6eea874f6-x86.cache-2
altering /home/druid/.mozilla-thunderbird/76kgkfvt.default/secmod.db
altering /home/druid/.mozilla-thunderbird/76kgkfvt.default/prefs.js
altering /home/druid/.mozilla-thunderbird/76kgkfvt.default/panacea.dat
altering /home/druid/.openoffice.org2/user/registry/data/org/openoffice/Office/Views.xcu
altering /home/druid/.openoffice.org2/user/registry/data/org/openoffice/Office/Common.xcu
altering /home/druid/.openoffice.org2/user/registry/cache/org.openoffice.Office.Paths.dat
altering /home/druid/.openoffice.org2/user/psprint/pspfontcache
altering /home/druid/.gimp-2.4/themerc
altering /home/druid/.gimp-2.4/documents
altering /home/druid/.compiz/session/117f000101000122132818400000099180003
altering /home/druid/.gconf/apps/evolution/tasks/%gconf.xml
altering /home/druid/.gconf/apps/evolution/addressbook/%gconf.xml
altering /home/druid/.gconf/apps/evolution/calendar/%gconf.xml
altering /home/druid/.gconf/apps/evolution/memos/%gconf.xml
altering /home/druid/.gconf/apps/f-spot/import/%gconf.xml
altering /home/druid/.bash_history
altering /home/druid/.gtk-bookmarks
altering /home/druid/.recently-used
altering /home/druid/.recently-used.xbel
druid@chris-desktop2:~/scripts$ cd /home/druid
druid@chris-desktop2:~$ find  . \( -ilname '*aquown*' -o -iwholename '*aquown*' \) -print
./.wine/drive_c/windows/profiles/druid/Desktop
./.wine/drive_c/windows/profiles/druid/My Pictures
./.wine/drive_c/windows/profiles/druid/My Music
./.wine/drive_c/windows/profiles/druid/My Documents
./.wine/drive_c/windows/profiles/druid/My Videos
./.nautilus/metafiles/file:%2F%2F%2Fhome%2Faquown%2FPictures.xml
./.nautilus/metafiles/file:%2F%2F%2Fhome%2Faquown.xml
./.nautilus/metafiles/file:%2F%2F%2Fhome%2Faquown%2FDesktop.xml
./.nautilus/metafiles/file:%2F%2F%2Fhome%2Faquown%2FDownloads.xml
./.nautilus/metafiles/file:%2F%2F%2Fhome%2Faquown%2FZ-Computer.xml
./.nautilus/metafiles/file:%2F%2F%2Fhome%2Faquown%2Fscripts.xml
./.local/share/tracker/aquown_tracker_lock
druid@chris-desktop2:~$ 

```

So what popped up in the above that you did not expect?  Anything bad?  Good?  I'm learning too :)  This is an interesting exercise :popcorn:

---

### Post by unutbu on 2008-09-14
The output looks fine.

Please post
```

ls -l /home/druid/.wine/drive_c/windows/profiles/druid/{Desktop,My\ Pictures,My\ Music,My\ Documents,My\ Videos}
```

The files above are symlinks which point to paths which include the string 'aquown'.
I don't know of a good command-line tool to redirect these symlinks all in one go. Thankfully, there do not seem to be many of these, so we'll be able to fix these by hand.

Then run```


cd /home/druid/.nautilus/metafiles
rename 's/aquown/druid/g' *
cd /home/druid/.local/share/tracker
rename 's/aquown/druid/g' *

```
This will rename any file which contains 'aquown' to a new filename with all occurrences of 'aquown' replaced by 'druid'.

Please give me an update. What things are still broken?

---

### Post by starcannon on 2008-09-14
> **44tr said:**
> Don't worry about the little pitfalls encountered in trying to help.  I understand the risks and I appreciate your time.  I'm considerably more conservative when it comes to messing with my main system, but my son's computer doubles as a bit of a test bed.  What is the worst that could happen?  My 10 year old can't play the games he wants to until I reinstall and configure from scratch?  Not the way I want to spend my time, but also not having a hurricane flood my house ...

So this is a good way to learn, and I would like to continue the process of changing.  If wine becomes a problem, I can blow those games away and reinstall; they weren't that bad to install; son will just have to start over on a few things.

Thanks for continued help; hopefully you are learning something useful as well and I don't mean learning to avoid helping people. :lolflag:

What next?

Your attitude rocks! Hope it all works out perfectly for you.

GL

---

### Post by 44tr on 2008-09-14
> **unutbu said:**
> The output looks fine.

Please post
```

ls -l /home/druid/.wine/drive_c/windows/profiles/druid/{Desktop,My\ Pictures,My\ Music,My\ Documents,My\ Videos}
```

The files above are symlinks which point to paths which include the string 'aquown'.
I don't know of a good command-line tool to redirect these symlinks all in one go. Thankfully, there do not seem to be many of these, so we'll be able to fix these by hand.

Then run```


cd /home/druid/.nautilus/metafiles
rename 's/aquown/druid/g' *
cd /home/druid/.local/share/tracker
rename 's/aquown/druid/g' *

```
This will rename any file which contains 'aquown' to a new filename with all occurrences of 'aquown' replaced by 'druid'.

Please give me an update. What things are still broken?

Here is the output from the commands.

```
druid@chris-desktop2:~$ cd /home/druid/.nautilus/metafiles
druid@chris-desktop2:~/.nautilus/metafiles$ rename 's/aquown/druid/g' *
file:%2F%2F%2Fhome%2Faquown%2FDesktop.xml not renamed: file:%2F%2F%2Fhome%2Fdruid%2FDesktop.xml already exists
file:%2F%2F%2Fhome%2Faquown%2Fscripts.xml not renamed: file:%2F%2F%2Fhome%2Fdruid%2Fscripts.xml already exists
file:%2F%2F%2Fhome%2Faquown.xml not renamed: file:%2F%2F%2Fhome%2Fdruid.xml already exists
druid@chris-desktop2:~/.nautilus/metafiles$ cd /home/druid/.local/share/tracker
druid@chris-desktop2:~/.local/share/tracker$ rename 's/aquown/druid/g' *
aquown_tracker_lock not renamed: druid_tracker_lock already exists
druid@chris-desktop2:~/.local/share/tracker$ 

```

I presume we don't need to overwrite?  just delete the old ones?  and ummm, how?

I think most stuff is working now, at least on the desktop.  Firefox and the panel functions (switch workspace, etc) just fell apart, but I think it is fine now as far as I can see.  Don't have time for extensive tests ... but looks good.  Just need to clean up these last details as far as I know.

---

### Post by unutbu on 2008-09-14
From the output you posted, it looks like nautilus and tracker regenerated the files they were missing. You can use nautilus to create a directory called something like tobedeleted and move the aquown files in /home/druid/.nautilus/metafiles and /home/druid/.local/share/tracker into the directory tobedeleted. If after a week or so everything appears okay, then you can delete them.

When you run
```

ls -l /home/druid/.wine/drive_c/windows/profiles/druid/{Desktop,My\ Pictures,My\ Music,My\ Documents,My\ Videos}
```

you will probably see something like 
```

lrwxrwxrwx 1 druid druid 20 2008-09-14 22:01 Desktop -> /home/aquown/Desktop

```
It's a broken symlink -- /home/aquown/Desktop doesn't exist anymore.
To fix it type
```

cd /home/druid/.wine/drive_c/windows/profiles/druid/
ln -sf /home/druid/Desktop Desktop  # Makes a symlink from Desktop to /home/druid/Desktop
```
Run similar commands to repair My Documents, My Music, etc.

Unless something else needs fixing, I think that's it. :)

---

### Post by 44tr on 2008-09-15
I'll get to those commands above in a second.  First though, I moved the indicated files to a tobedeleted folder as suggested with nautilus opened with gksudo (I'll get better at command line).  When I closed nautilus I got some errors.  Here is the output.  Problem?

```
druid@chris-desktop2:~$ gksudo nautilus
nautilus-share extension

** (nautilus:7489): WARNING **: Unable to add monitor: Operation not supported
SSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSSNautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.

Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


--- Hash table keys for warning below:
--> file:///home/druid
--> file:///

(nautilus:7489): Eel-WARNING **: "nautilus-metafile.c: metafiles" hash table still has 2 elements at quit time (keys above)

(nautilus:7489): Eel-WARNING **: "nautilus-directory.c: directories" hash table still has 2 elements at quit time
seahorse nautilus module shutdown

```

---

### Post by 44tr on 2008-09-15
> **unutbu said:**
> 
It's a broken symlink -- /home/aquown/Desktop doesn't exist anymore.
To fix it type
```

cd /home/druid/.wine/drive_c/windows/profiles/druid/
ln -sf /home/druid/Desktop Desktop  # Makes a symlink from Desktop to /home/druid/Desktop
```
Run similar commands to repair My Documents, My Music, etc.

Unless something else needs fixing, I think that's it. :)

I did it with Desktop and it's fine.  But isn't there a problem if there is a [space] in the command line arguments like 'My Documents'?  Do I use quotes or what?  Will it work with the space?  It's funny how hard it is to find answers to questions like that.  Usually, the tutorials I've been through just say "Use underscore instead of a space; you'll thank me later ..."  Thanks again for patient help.

---

### Post by 44tr on 2008-09-15
OK, I chanced using the double quotes like "My Documents" and it appears to have worked for everything.  Now the only question marks are those nautilus errors which I didn't use to get.  Ideas?

---

### Post by Corin-EU on 2008-09-15
> **unutbu said:**
> This will change every occurrence of 'aquown' into 'druid' in every file in /home/druid.
Thankfully, aquown is a pretty unusual string so I think it should be safe. 
If a user had a name like 'rick' then this would be extremely dangerous because a file
with the word 'trick' would be changed into 'tdruid'. 
But since you appear to only want to change the occurrence for path specifications, you could limit your string substitution by bounding the start of the string with a forward slash as in

/old_user to /new_user

and then bounding the end of the string by one of space_character, tab_character or end_of_line_character, so that in case of wanting to change rick, you do not change occurrences of trick or rickie.

(man grep -- regular expressions section for the unitiated)

---

### Post by unutbu on 2008-09-15
The nautilus errors seem to have something to do with samba. 
Unfortunately, I don't know that much about samba, so I think it might be best to start a new thread to ask about this question.

Does this happen when you start up nautilus as druid, or does it only occur as root?
If it happens as druid, then perhaps try the solution posted here
[http://ubuntuforums.org/showthread.php?t=878321](http://ubuntuforums.org/showthread.php?t=878321) (in post #6).

If it happens as root, then I think you should post a new thread before trying post #6.

Corin-EU: Thanks for that. You are right it would have been better to use a regexp -- perhaps something like
```

alter_files.py -p '\baquown\b' -r 'druid' -b /home/druid
```

---

### Post by 44tr on 2008-09-16
It only happens when I open it as root.  So okay, another thread.  Thanks for all your help on this.  Hope we can work together again; you might even learn something from me someday :)

Chris

---

