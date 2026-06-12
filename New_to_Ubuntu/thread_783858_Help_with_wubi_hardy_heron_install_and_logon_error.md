---
title: "Help with wubi hardy heron install and logon error"
date: 2008-05-06
forum: New to Ubuntu
---

### Post by NastyT23 on 2008-05-06
alright so i installed hardy using wubi and everything was good and gravy. i stopped using windows completely i downloaded a bunch of files, customized ubuntu to my liking...installed all updates...then i started experimenting a little bit with folder permissions...i added a guest user account for when someone else wants to use my laptop, so i wanted to set permissions for the guest account in a way so that they could not modify or access any of my files, or my windows system files, basically only the files under the guest account home folder would be accessible to them. Well i ended up blocking permissions on my main account somehow..:(  i think i took away privelages to my own home folder...or maybe the host folder....anyways, when i restarted my laptop and tried logging into ubuntu i recieved an error saying:

User's $HOME/.dmrc file has incorrect permissions and is being
ignored. ... file sould be owned by user and have 644 permissions...??

Is there anyway around this? I tried logging into the guest account and that doesn't work either.
I ctrl+alt+f1 into that terminal window and tried to creat a whole new username using useradd but it wouldn't even let me do that.
I did a google search on the error message and came up with a solution but it didn't work for me...tried:

sudo chmod 644 .dmrc

and

chmod 644 ~/.dmrc

sudo chown me /home/me/.dmrc
sudo chmod 700 /home/me

but nothing is working for me. 
I would like to get the files i have downloaded and if possible save my configurations and settings...but i really just want to be able to access and copy the files from my home folder.
I logged into windows to try and access them but with the wubi installation i have no way of getting them. (i don't know how to acces those files through windows, if at all possible) Please help me!

Im new to linux and love it so far, this has been the only issue i've had and it was my own fault...
Thanks in advance for your help.

---

### Post by shifty_powers on 2008-05-06
I've been getting this message myself, and tbh, it's made not the slightest bit of difference. Just ignore it, that's what i'm doing ;)

edit: oh and i'm not using wubi either ;) but i did do a reinstall and not reformat my home folder, which is when it started. keep meaning to back up the file and then delete it, just to see what happens.... (i'm not recommending that as i don't know what'll happen ;))

---

### Post by NastyT23 on 2008-05-06
I can't just ignore it....i cant log in AT ALL...i can log into the terminal (alt+ctrl+f1). I cant get past the login screen...i would try uninstalling and reinstalling thru wubi but im afraid of losing all my data in the home folder...

---

### Post by Aearenda on 2008-05-06
That file remembers the default desktop manager for when there is more than one installed (Gnome and KDE, for example). On my system it has 0600 not 0644. Here is the ls -l output for mine:
```
-rw------- 1 aea aea 28 2008-05-06 19:18 .dmrc
```

It is recreated at logon if it does not exist. I suggest you do this at a console: ```
mv ~/.dmrc ~/.dmrc-old
```and then log off and on again. If this is the underlying problem, it should go away. If it does not go away, do this:```
ls -ld ~
```which will list the permissions on your home folder - mine are:```
drwxr-xr-x 87 aea aea 12288 2008-05-06 19:18 /home/aea
```
Let us know how you get on please.

---

### Post by NastyT23 on 2008-05-06
> **Aearenda said:**
> That file remembers the default desktop manager for when there is more than one installed (Gnome and KDE, for example). On my system it has 0600 not 0644. Here is the ls -l output for mine:
```
-rw------- 1 aea aea 28 2008-05-06 19:18 .dmrc
```

It is recreated at logon if it does not exist. I suggest you do this at a console: ```
mv ~/.dmrc ~/.dmrc-old
```and then log off and on again. If this is the underlying problem, it should go away. If it does not go away, do this:```
ls -ld ~
```which will list the permissions on your home folder - mine are:```
drwxr-xr-x 87 aea aea 12288 2008-05-06 19:18 /home/aea
```
Let us know how you get on please.

Alright i tried what you said but i still get the same error message at the login screen. I forgot to mention i get this error as well (i have to write everything down in a notebook, log onto windows and type it in here lol)

Your home directory is listed as: '/home/terry' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

I say yes and then it gives me the error i mentioned above about user's $home/.dmrc file is being ignored...

alright then i did the 
ls -ld ~
it returned:

drwxr-xr-x 22 root root 4096 2008-05-05 02:24 /

any idea what that means?

Is there a way i can log in at the login screen as root? that would let me backup my files right? I'd rather fix this than have to back up my files and start from scratch but if i have to then i will.

---

### Post by NastyT23 on 2008-05-06
Well i figured out how to set a root password, and i tried logging in at the login screen as root but it tells me that the system administrator is not allowed to login at this screen.

---

### Post by Aearenda on 2008-05-06
> Your home directory is listed as: '/home/terry' but it does not appear to exist. Do you want to log in with the /(root) directory as your home directory? It is unlikely anything will work unless you use a failsafe session.

This is much more serious, and is certain to cause the other problem. 

> drwxr-xr-x 22 root root 4096 2008-05-05 02:24 /
This shows that you are using the root directory '/' of the filesystem as your home directory!

Unless there is more you haven't told us :-), it should be able to be recovered.

First, we need to know whether your logon user is 'terry' or 'me'? 
Second, please do ```
ls -l /home
```
Post the results and I will suggest the next steps.

---

### Post by NastyT23 on 2008-05-06
My username is terry, i hope i didn't do anything else to screw it up!

alright i tried
```
ls -l /home
```
i got back
```
ls: cannot open directory /home: Permission denied
```
so i did 
```
sudo ls -l /home
```
and got 
```
total 8
drwx------ 47 terry terry 4096 2008-05-06 02:34 terry
drwxr-xr-x 27 username username 4096 2008-05-05 03:05 username
```

(My main login is: terry
and the secondary account i created is: username)

---

### Post by Aearenda on 2008-05-06
Ok, so when logged on to the console as terry, try this (after doing the extra step I added at the end of the post):
```
sudo chmod 755 /home/terry
```
This sets your home directory itself so that it can be accessed by other users. The logon process runs as another user, so this is necessary.

Next, do this: 
```
sudo chown -R terry.terry /home/terry
```
The -R flag makes this recursive, so that all files below this folder are modified. This makes sure all your files are really yours; the first terry is the owner, the second the group name.

Next:
```
sudo chmod 600 /home/terry/.dmrc
```
I think that should fix things so you can log on to Gnome. There may be other permission settings that need to be tidied, but please let us know how well this works so far.

If it does not work, please do
```
cat /etc/passwd
``` and show us the 'terry' line.

EDIT: as an afterthought, also do this before you try to logon to Gnome:
```
sudo chmod 755 /home
sudo chown root.root /home
```

---

### Post by NastyT23 on 2008-05-06
IM IN!!! Those last 2 commands you added did the trick!  Thank you so much! Is there anything else i should do now that im in?
I need to get some sleep now, but i'll check back tomorrow. Once again THANK YOU!! :)

---

### Post by questant on 2008-05-06
Yea, this one seems to be a bear.  The first time I got it I took it for what the error message says, tried to correct it and then couldn't log on at all.  It told me something like "Your X session lasted less than 10 seconds ..."
Those of us who used to work with windows like to muck around with permissions as we might with win.  If you're told anywhere you should change your home directory permissions to share the directory with win or lin machines DON'T DO IT!!!  That truck load of good intentions will get you lost in a slough of despond.  Neither smb nor nfs requires that.
The message is misleading:
"User's $HOME/.dmrc file is being ignored.  This prevents the default session and language from being saved.  File should be owned by user and have 644 permissions.  User's $HOME directory must be owned by user and not writable by other users."
The real problem is NOT /.dmrc.  The real problem is not $HOME.  The real problem is the username home directory.  For the record, the HOME directory permissions should be dwrxr-xr-x.  With the numbering system for setting permissions, this should be 755 (the full number is 1600755).  Your user directory permissions should be the same (the full number is 1200755).  If you change YOUR home directory to anything beside 755 you'll get the error message typed above.  Ergo, if you change your user permissions back to the default for that directory you will be able to boot into the system again without the error message (provided you haven't mucked up other permissions as well).  I wouldn't feel too bad.  I've done it and really diddled my system in the past.  Some of us really learn best the hard way (you can say AMEN here).  One other comment:  It's tragic the message is so cryptic and, for all intents and purposes, misleading.  It is absolutely correct in what it says but is opaque to the real core of the problem.

Boot the machine to the recovery prompt. You won't need to use sudo.  At this point you're sudo redivivus.

Use ls -l both to familiarize yourself on where you are and to get the permissions of the directories you see.  If you see the name of your user directory you're ready to change the permissions.  If you do not (you see your desktop, etc., your one subdirectory too far in.) cd .. to move up one subdirectory and then ls -l again.  If you see the system directories including home, cd into home with cd home.  Frankly, I don't remember where the recovery prompt dumps us when it arrives but my memory is it's in the home directory where one can see the suer names.

ls -l will list out the permissions for files and directories.  They should read drwxr-xr-x for your username home.  if they do not you must change them:
chmod 755 username <Enter>

If you've actually mucked around with the bona fide home home directory you will have to back yourself up to the root directory (cd ../..) to check the permissions and use the same correction for home.

If you've changed any other permissions, you'll may need to correct them as well (such as /.dmrc, etc.)

Now:
shutdown -r now
to reboot.
In my case, Viola, the system returned to peaceful tranquility and so did my spirit.

Additional note:  The X session less than 10 seconds error was an $HOME permission error in my case, requiring the same corrections for that home as well as my usernamehome.  Nothing like making horrendous mistakes to learn that Linux isn't Microsoft either for problems to be solved or solutions to solve them.

An observation:  If you're new to Linux and/or Ubuntu, keep a log of what you do (this is good advice even for a veteran).  I know it's tedious but if you blow it, it's easier to retrace your steps with a log than it is to do it from memory.  Sometimes we can make so many changes in one pass we can't recover our minds, let alone our machines.

Good luck to you all in getting the system back without having to reinstall.  That's overkill in most cases.

NB:  Over time I've known this solution to work on Hardy and on Dapper and I suspect on Linux in general but I've not tested that claim and don't intend to do so.  I am very satisfied with Debian and Ubuntu (with a little Kubuntu and Mepis thrown in).

---

### Post by Aearenda on 2008-05-06
Great news! Now that it is working, I would review the permissions of the files inside your home directory. To prevent guest access, do this:
```
chmod -R o-r ~/*
```
This says 'change the access mode (chmod) for all files and folders named and the files and folders they contain (-R), removing read access for those not the owner and not in the group this file is assigned to (o-r), for all files and folders BELOW your home directory (~/*). This way you don't affect the home directory itself, you don't affect hidden files in your home directory, and you don't mess with access for the owner and group.

You may also want to change the permission on your Firefox/Thunderbird and Evolution hidden folders, like this:
```
chmod -R o-r ~/.mozilla ~/.evolution
```

To make sure that new files are created without read access to everyone, do this:
```
gedit ~/.profile
```
Go down to find a line like this:
```
#umask 022
```
Change it to be like this:
```
umask 026
```
Then save the file.

This should have the result of no guest read access being allowed for new files created after you have logged off and on again. There used to be a Nautilus bug that made the file manager ignore this setting, but it seems to be fixed now.

You could instead change the system-wide umask default in /etc/profile to 026, but I don't know if that will break anything. It shouldn't.

By the way, these setting will not hide the files from the guest - it just means the guest won't be able to actually see their contents or change them in any way. To hide the files, you need to take away 'execute' permission for the owning folders. I don't recommend you try this.

To return to what you were trying to achieve in the first place, by default only root has access to change system files on Ubuntu (and most other Linux)  systems - that why you have to use 'sudo' on Ubuntu when doing this, and it makes the system much more secure against viruses than Windows, where most home users ARE administrators because it is too painful not to be. The 'admin' group governs access to sudo in Ubuntu.

Make sure your guest user is not a member of the 'admin' group like this:
Start system->administration->users and groups
Click on 'Unlock' and supply your password
Click on 'Manage groups'. 
Find the 'admin' group, select it and click 'Properties'. 
Make sure the box next to your guest user is unchecked.

That's all the follow-up steps I can think of for the present. It seems likely that some of your files will still have different permissions from normal, but I don't think it will matter much apart from the files in ~/.ssh which will only show up if use ssh for remote access, and it will tell you what to do to fix it (getting it right, as well - unlike the .dmrc message).

I hope you enjoy using Ubuntu from now on!

---

### Post by NastyT23 on 2008-05-07
Thank you so much for your help! I'd be lost without it lol.
I'll be sure not to mess around with file permissions anymore. I did all the commands you said and that's all i need, i dont need to hide them, just want to prevent them from being modified or deleted. Also i store a lot of files on an external hard drive, music, movies, etc...is there a way to prevent guest users from deleting or modifying them?
Thanks

---

### Post by Aearenda on 2008-05-07
Happy to help. Concerning the external drive, is it normally left connected, do you know what the device is seen as in Ubuntu (eg /dev/sdc), how many partitions, and what is the filesystem? (NTFS, ext3, etc)

The answer is 'yes, we can restrict guest usage of the external drive', but the detail depends on how it is formatted. In essence, it needs to have a umask set as well, and we normally do this in /etc/fstab - but to put an entry in there we need these details.

---

### Post by NastyT23 on 2008-05-07
I have hardy installed on the external drive with a seperate partition for my other files, when i go into gparted it shows me:
/dev/sdb1   ext3    /media/disk    19.53gb
/dev/sdb3   fat32   /media/disk-1   51.89
/dev/sdb2   extended                  3.08gb
/dev/sdb5   linux-swap                3.08gb


(i sometimes boot from the external drive to test something out if im not sure i want the changes on my internal)

---

### Post by Aearenda on 2008-05-07
So I'm guessing that the files you are concerned about here are those in the large fat32 partition, sdb3. I haven't tried this out, but what follows is my understanding of what other people have done as reported in the forums.

To fix the permissions for this, since FAT is very simplistic and has no concept of recording ownership and permissions, you have to set a umask in /etc/fstab. 

First, discover the UUID of the partition:
```
sudo vol_id --uuid /dev/sdb3
```
Copy the short UUID that will appear to the clipboard. We could just use the device name, but that's likely to lead to difficulty later.

```
gksudo gedit /etc/fstab
```

You will probably find there is no entry for sdb3 there yet, and that it is automatically mounted for you at the moment as /media/disk<something>.
Add a couple of lines like this:
```

#/dev/sdb3
UUID=1234-5678  /home/terry/external  vfat  auto,users,uid=1000,gid=1000,umask=022  0 0

```
Replace the UUID 1234-5678 by pasting the real one.
The umask 022 should allow reading but not changing the files.
The uid and gid are numerical equivalents to username and group name, and are set to 1000 because those are the defaults for the first user created, which I guess is you. Otherwise look through /etc/passwd for your uid and gid - they are the first two numbers on your line, in that order.

You will need to create an empty directory at which to mount it:
```
mkdir ~/external
```
(No need for sudo)

You should find the drive contents appear below the 'external' directory on reboot. In the mean time, you can do this for testing:
```
sudo umount /dev/sdb3
sudo mount ~/external
```

Again, I haven't tested this stuff - it may need some wrinkles removed :-)

---

### Post by NastyT23 on 2008-05-10
Okay im gonna hold off before i try any of that. I just ran into another problem and im afraid to restart my system in fear of being locked out again! :confused:

okay i get this message when i go to system>admin>hardware drivers:
```
Failed to run /usr/bin/jockey-gtk as user root.

Unable to copy the user's Xauthorization file.
```

and if i try to run remastersys:

```
Failed to run /usr/bin/remastersys-gui as user root.

Unable to copy the user's Xauthorization file.
```

Im seeing a trend....what could be causing this:confused:
Should i run all the commands that fixed my log in problem? will that help or is this something entirely diff? I don't know what i could have done wrong this time.

---

### Post by Aearenda on 2008-05-10
This won't lock you out completely - command line sessions will be unaffected by it. It's probably left over from the original lockout. There may be a few more oddities like this that show up. 

Do this:
```
ls -l ~/.Xauthority
```
It should look like this:
```
-rw------- 1 terry terry 167 2008-05-10 23:09 /home/terry/.Xauthority
```
..but the numbers will differ.

In your case, it probably has the wrong permissions or owner.

To fix the owner and group:
```
chown terry.terry ~/.Xauthority
```

To fix the permissions:
```
chmod 600 ~/.Xauthority
```

That should be it.

---

### Post by NastyT23 on 2008-05-11
Thanks it worked! How did you become so familiar with linux? I'd like to be able to troubleshoot problems on my own someday :)

---

### Post by Aearenda on 2008-05-11
Excellent! 

Troubleshooting needs research, logical thought, an understanding of what should be happening, and a willingness to test theories before committing to solutions. It helps to have similar systems - I test much of what I suggest on my own computers. 

I wouldn't say that I am 'that familiar with Linux' - I worked in the computer industry for 27 years, on many different operating systems, including Unix. They differ in detail, but are usually similar in principle. I only started using Linux seriously in 2004, first with Fedora, then Ubuntu and Debian. The truth is, I am a bit more persistent with Google and forum searches than most, and I can modify what I find for different circumstances. But I am not always right, by any means!!!

---

