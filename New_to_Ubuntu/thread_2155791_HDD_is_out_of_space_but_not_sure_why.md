---
title: "HDD is out of space but not sure why"
date: 2013-06-19
forum: New to Ubuntu
---

### Post by kc5hwb on 2013-06-19
One of my Ubuntu boxes has a 160GB HDD which keeps running out of space.  The reason I think this is an error or some program misbehaving is that if I reboot the box 2 times, it frees up 40-50GB of space.  And it works great with all that free space for a few days or a week, then I start getting system messages again, saying I am running out of space. Another couple of reboots "fixes" this again.

If I go to Examine the drive, it shows me that most of the files are in my /home/<user> directory, but underneath that directory the Disk Usage Analyze shows nothing.  It sounds strange, but it shows all these files in my /home/<user> directory, but underneath it shows all of my folders are barely used.  I can provide a screenshot of this if needed.

I would guess that I have a program running somewhere that is doing this.  I do have a Subsonic server running on this box 100% of the time.  But how can I verify this?  Is there a way to see where temp files or cached files are going, and to remove them without a reboot?  Is there a way to verify if it is the Subsonic server app?  I only mention this app because it is the only thing I have running 100% of the time.

Let me know what other info I need to provide.

---

### Post by 2F4U on 2013-06-19
My guess would be that the files are located in a hidden directory (starting with ".") and that disk usage application maybe ignores these directories.

---

### Post by 1clue on 2013-06-19
There's probably a tool for this, but I'll show you what I do:
[B]
cd /
sudo du -hs `ls -A`
[/B]
Notice the type of quotes here.  It's the one to the left of the 1 key on a US keyboard.

The first time you do this it will take awhile, subsequent searches will be faster.

This prints a human-readable total size of every folder, visible or not, at the current level.  This is a size including all contents.

Look for the biggest stuff, ignore anything that doesn't end with G for the size.  Scan the entire directory first to be sure you understand what's going on at that level, then pick a directory, cd into it and do it again.

---

### Post by agillator on 2013-06-19
Another thing to check: do you delete a lot of files through the file manager? Sometimes this will not truly delete the files but moves them to a trash directory which does not always show up as being in the trash bin. Empty the trash bin and then search a few of the directories for a hidden directory .Trash something or other. See if there are any files left in there. Deleting a file with the rm command on the command line does in fact delete a file.

---

### Post by mcduck on 2013-06-19
I recommend checking the disk usage with tools like *df* and *du*.

While the Disk Usage Analyzer is an excellent tool, it's output can be rather confusing if you don't know exactly what it's doing. For example the percentages it displays are not about how much there is available/used space, but instead about how large percentage of the used space in the parent folder a certain file/folder is taking. And to complicate things even more, depening on your Ubuntu version the tool might also count in all the mounted filesystems unless you specifically tell it to only scan a specific partition, which of course means that you don't get any usefull information about free/used space on a certain filesystem. (The main purpose of the tool it to analyze where space is being used, not how much free space there is). Also it's usually running as  your normal user, which means it's not even able to scan things when the permissions only allow root to access them.

---

### Post by kc5hwb on 2013-06-19
> **1clue said:**
> There's probably a tool for this, but I'll show you what I do:
[B]
cd /
sudo du -hs `ls -A`
[/B]
Notice the type of quotes here.  It's the one to the left of the 1 key on a US keyboard.

The first time you do this it will take awhile, subsequent searches will be faster.

This prints a human-readable total size of every folder, visible or not, at the current level.  This is a size including all contents.

Look for the biggest stuff, ignore anything that doesn't end with G for the size.  Scan the entire directory first to be sure you understand what's going on at that level, then pick a directory, cd into it and do it again.

I'm going to try this when I get home.  My remote connection to the box stopped working, I expect due to no more HDD space.


> **agillator said:**
> Another thing to check: do you delete a lot of files through the file manager? Sometimes this will not truly delete the files but moves them to a trash directory which does not always show up as being in the trash bin. Empty the trash bin and then search a few of the directories for a hidden directory .Trash something or other. See if there are any files left in there. Deleting a file with the rm command on the command line does in fact delete a file.

Sometimes, yes.  I also empty the trash bin after I delete from the GUI, tho.  I'll look for the .trash folder, that is a good idea.  I've seen this folder several times on a external USB device that I mount and use, and then move to another computer.  Windows doesn't hide the .filename folders like Ubuntu does.

---

### Post by 1clue on 2013-06-19
Somehow I keep thinking you have a log file that's being spammed uncontrollably.  Probably that's in /var/log, but it doesn't have to be.

---

### Post by kc5hwb on 2013-07-06
> **1clue said:**
> There's probably a tool for this, but I'll show you what I do:
[B]
cd /
sudo du -hs `ls -A`
[/B]
Notice the type of quotes here.  It's the one to the left of the 1 key on a US keyboard.

The first time you do this it will take awhile, subsequent searches will be faster.

This prints a human-readable total size of every folder, visible or not, at the current level.  This is a size including all contents.

Look for the biggest stuff, ignore anything that doesn't end with G for the size.  Scan the entire directory first to be sure you understand what's going on at that level, then pick a directory, cd into it and do it again.


OK here is the result of the command above:

> 4.0K	.dmrc
4.0K	Documents
4.0K	Downloads
12K	examples.desktop
68K	.fontconfig
220K	.gconf
24K	.gnome2
0	.goutputstream-9TGVZW
392K	.gstreamer-0.10
4.0K	.gtk-bookmarks
du: cannot access `.gvfs': Permission denied
4.0K	.ICEauthority
80M	.local
12K	.mission-control
17M	.mozilla
4.0K	Music
4.0K	Pictures
4.0K	.profile
40K	.pulse
4.0K	.pulse-cookie
110G	Samson
8.0K	.ssh
4.0K	Templates
304K	.thumbnails
4.0K	Videos
4.0K	.Xauthority
8.0K	.xscreensaver
1.5T	.xsession-errors
143G	.xsession-errors.old

I'm not sure where this .xsession-errors folder or file is.  I can't see it in the Videos directory.  Obviously this is causing my problem but not sure what errors there are and not sure how to fix.

---

### Post by dannyboy79 on 2013-07-06
[http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable](http://askubuntu.com/questions/177058/xsession-errors-file-is-huge-how-can-i-disable)

---

### Post by oldos2er on 2013-07-06
> **kc5hwb said:**
> I'm not sure where this .xsession-errors folder or file is.  I can't see it in the Videos directory.  Obviously this is causing my problem but not sure what errors there are and not sure how to fix.

```
rm .xsession-errors*
```

---

### Post by 1clue on 2013-07-07
.xsession-errors is errors in your graphical interface.  You have a problem and you need to fix it.

Remove it (see above from oldos2er) and then log back in again, and open it in a text editor to figure out what the problem is.

You can't see it in a file browser because any file starting with a period is an invisible file in UN*X.  You can probably check a box in the file dialog or folder window to show hidden files.  Sorry I'm a command line guy, so I'm not much help here.

---

### Post by 1clue on 2013-07-07
Sorry for the double post.  .xsession-errors is very verbose.  There's a whole lot of "Starting this" and "Found that" in there.

The first thing is, if you have a 1.5T file, nothing is going to open it.  If you're not comfortable with command line tools you won't even be able to look at it I think.  So you need to delete it and start with something you can work with.

You won't hurt anything by deleting it, it's just a log file for your personal login.  If you delete it, log out and log back in again then you get a single session start in there, and it's easier to dissect.

Look for stuff that says something bad happened, it may be hard to spot for all the "good" noises in there.  We can't really be specific until then.

---

### Post by kc5hwb on 2013-07-15
I found the file and deleted it, then it came back again a couple of days later, though it wasn't as large.

Now I am getting an error when booting...the screen stays at "battery check....ok" and doesn't move forward.  I read in another post that this is a graphics driver issue, so I guess that might be related to this.

---

### Post by 1clue on 2013-07-15
You can delete that file again, but it reappears every time you log in to a graphical session.  Your computer is having problems and you need to diagnose that file or you will fight it until you throw the computer out the window.

---

### Post by fosterD on 2013-07-16
I used to experience a similar problem when one of my application, Spotify had issues with its graphic. the size of .xsession-errors kept increasing until my hard drive run out of space, then my computer would crash
When I removed the .xsession-errors to free my hard drive, every thing would operated normally. Yes, but it kept increasing. My problem was solved when Spotify updated to a new version.
You may want to make a script to clear up this file as a temporary solution

---

### Post by 3rdalbum on 2013-07-16
Can't you just remove the owner's write permission to the file? That would presumably stop the logging.

---

### Post by 1clue on 2013-07-16
Why not delete it, restart, log in and copy it to a second file.  Then try to debug what's in there, because the reason it's big is YOU HAVE  A PROBLEM WITH YOUR BOX.

If you don't fix the problem, the problem will not go away.  At some point your problem will probably get worse, possibly causing your GUI login to no longer work.  Removing write permission is akin to putting your head in the sand, it doesn't solve the problem.

To get better expertise, start a new thread with "Huge .xsession-errors" as the topic, post the file and there will be lots of people who can help you.

---

### Post by 3rdalbum on 2013-07-16
1clue: Not necessarily. If everything is working well and as it should, these could be erroneous error messages or simply "warnings" that are being printed out.

I doubt it would get worse, unless it is hardware failure.

If the OP wants to try and debug the problem that's okay. If the messages are not worth worrying about then removing the ability to write to the file is a workaround.

---

### Post by kc5hwb on 2013-07-16
> **1clue said:**
> Why not delete it, restart, log in and copy it to a second file.  Then try to debug what's in there, because the reason it's big is YOU HAVE  A PROBLEM WITH YOUR BOX.


Why are you yelling at me?  I didn't post anything about changing write permissions.  Read the poster's name, IMO.

I can't currently login due to the other error I posted, so I don't know if the file is still there or not.  I'll attempt to SSH into the box and browse to that directory to see.

---

### Post by 1clue on 2013-07-16
So does it hurt anything to look in the file?  A simple configuration change might fix the problem, and then it would behave perfectly.

This sort of attitude is irrational IMO.  If you ignore warnings and errors in log files, thinking that they're normal, then when you have a REAL problem and you're trying to look for warnings and errors in log files, you spend a hundred times longer because there's so many.

Log files shouldn't have any errors and very few warnings when your system is working properly.

---

### Post by kc5hwb on 2013-07-16
I'm not ignoring anything.  I agreed with you earlier that I want to find the problem and will look at the log file once I can log back in, but as previously stated, I cannot login to the GUI to look around due to the boot error.

I also just confirmed that I also cannot SSH into the box, even after getting to a cmd prompt with CTRL-ALT-F1.  So I will have to wait until I get home this evening before I can even check if that file is still there.

---

### Post by dannyboy79 on 2013-07-16
> **kc5hwb said:**
> I found the file and deleted it, then it came back again a couple of days later, though it wasn't as large.

Now I am getting an error when booting...the screen stays at "battery check....ok" and doesn't move forward.  I read in another post that this is a graphics driver issue, so I guess that might be related to this.
i've had this happen to me before, i've had to hard reboot several times before it ended up getting me to lightdm so that I could login. did you recently install a new kernel possibly? can you ctrl-alt-f1 to see if there are other messages? have you tried removing "quiet splash" from your grub boot line so you can see where it's hanging up?

also, that .xsession-errors file size getting gigantic isn't a new bug. if you can view the file when it's a readable size you may want to check out what the error that is being logged is, most likely it's nothing serious and just a warning. in that case you may want to try a few of the solutions that exist to have the errors log to /dev/null

---

### Post by 1clue on 2013-07-16
You can't log in at all?

Wait for the login screen, then type <ctrl>+<alt>+<f1>.

You'll get a text login, you can delete the file, then you can go back to the gui, log in and then follow my earlier instructions.

Getting back to the gui is done by <ctrl>+<alt>+<fsomething>.  I change the number of text terminals on mine, but I think the default is f7.

---

### Post by kc5hwb on 2013-07-16
I couldn't login remotely via SSH.

Yes I can login to the box using CTRL-ALT-F1.  This is after the error comes up about [battery check....OK] which, as I understand it, is a graphics error.

Can't get back into the GUI at all.

---

### Post by 1clue on 2013-07-16
Try removing the file as I mentioned, and then 'sudo reboot' from the shell.

You might want to check the size of /var/log/Xorg.*.log files too, they might be getting pretty big.

---

### Post by kc5hwb on 2013-07-16
How can I show hidden files in cmd line?

---

### Post by 1clue on 2013-07-16
ls command, the -a option gets all files.  ls -alh is what I use, it puts sizes in human readable form.

---

### Post by 1clue on 2013-07-16
You might want to use this:
ls -alh | less

which will give you the listing a page at a time.  Space bar gives you the next page, 'q' quits, up and down arrow work as you would expect.

You also might want:
ls -alh .xs*

in your home directory to get the size of the .xsession-errors file, or:

ls -alh /var/log/X*

to get the log file sizes.

---

### Post by kc5hwb on 2013-07-19
I ran the command from earlier:
```
sudo du -hs `ls -A`
```

Which returned alot of files, but only 1 was huge at 1.5TB and it is now named .local

The .xsessions-errors is no longer showing.  I did delete it the last time I was in the GUI, but now of course, I can't boot into the GUI.

Here is the other thread I am posting in for the boot problem:
[http://ubuntuforums.org/showthread.php?t=2162755]("http://ubuntuforums.org/showthread.php?t=2162755")

Not sure, but I am wondering if these 2 issues are related.  This install of Ubuntu is less than a month old, with a brand new 2TB HDD.

---

### Post by kc5hwb on 2013-08-02
Well welcome back, Ubuntu Forums...

Here is the latest......


```
^[[Ajape@samson:~$ sdu -hs `ls -A`
[sudo] password for jape: 
4.0K	.bash_history
4.0K	.bash_logout
4.0K	.bashrc
33M	.cache
12K	.compiz
12K	.compiz-1
2.7M	.config
12K	.dbus
18M	Desktop
4.0K	.dmrc
4.0K	Documents
4.0K	Downloads
12K	examples.desktop
396K	.fontconfig
220K	.gconf
24K	.gnome2
0	.goutputstream-9TGVZW
392K	.gstreamer-0.10
4.0K	.gtk-bookmarks
du: cannot access `.gvfs': Permission denied
4.0K	.ICEauthority
1.5T	.local
12K	.mission-control
15M	.mozilla
4.0K	Music
4.0K	Pictures
4.0K	.profile
40K	.pulse
4.0K	.pulse-cookie
8.0K	.remmina
193G	Samson
8.0K	.ssh
4.0K	syncclientconfig.xml
4.0K	Templates
308K	.thumbnails
3.3G	TonidoSync
688K	TonidoSyncData
4.0K	Videos
4.0K	.Xauthority
8.0K	.xscreensaver
16K	.xsession-errors
```

---

