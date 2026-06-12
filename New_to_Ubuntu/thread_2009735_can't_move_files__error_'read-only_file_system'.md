---
title: "can't move files  error 'read-only file system'"
date: 2012-06-24
forum: New to Ubuntu
---

### Post by Rrory on 2012-06-24
I tried to move a pdf from my desktop to my kindle & suddenly I get this message: error opening files 'read-only file system.'

 I have no idea what it means also when I plug my kindle into Ubuntu & open documents all the files suddenly have little padlocks on them. I exit & reo-pen and the padlocks are gone.
 Help, I have no idea what's happening & I haven't fiddled with anything. I'm scared I'm somehow locking my own files.

---

### Post by Gone fishing on 2012-06-25
The files are read only only when the kindle is plugged in? Odd - if you run sudo nautilus can you get at the files?

---

### Post by Rrory on 2012-06-25
sorry other files too; a while back my co-writer sent me a windows doc. and suddenly I couldn't edit it. I got around it...

Okay tried: sudo nautilus
got this message:
Nautilus could not create the required folder "/root/.config/nautilus".

also 
** (nautilus:186): DEBUG syncdaemon not running waiting for  it to start in NameOwnerChanged
called 'net usershare info' but it failed  Error 255 cannot open usershare directory var/lib/samba/usershares. Error no such file or directory

GLib-GIO warning **: missing callback called fullpath=/root/.config/user-dirs.dirs


Addendum: tried this command on my other computer with Ubuntu' it said to ask the system administrator to enable user sharing.

---

### Post by Gone fishing on 2012-06-25
So your whole file system is being mounted as read only - this only happens if the kindle is plugged in?

It is possible to remount the file system as read write 

sudo mount -o remount,rw /

however this should not be happening it generally happens if there is a file system error, try starting up in recovery and checking the file system

Post Edit

Start in recovery mode and then select fsck

---

### Post by Rrory on 2012-06-25
> **Gone fishing said:**
> So your whole file system is being mounted as read only - this only happens if the kindle is plugged in?

It is possible to remount the file system as read write 

sudo mount -o remount,rw /

however this should not be happening it generally happens if there is a file system error, try starting up in recovery and checking the file system

Post Edit

Start in recovery mode and then select fsck

Yes, but it's only the kindle files that are read-only. I can move a file to a flashdrive, no problem. I tried the sudo command on my other computer and it didn't change anything. The little padlocks are on all my kindle files, I can't even delete them.

 where can I find the recovery mode? I pressed F2 but didn't see that as an option. Thanks for all your help.

---

### Post by Gone fishing on 2012-06-26
Sorry that is clearer the memory on your kindle is corrupted and there maybe a bug [http://oldbugs.calibre-ebook.com/ticket/6086](http://oldbugs.calibre-ebook.com/ticket/6086). 

Id copy your kindle files somewhere safe then reformat the kindle and copy the files back

---

### Post by Rrory on 2012-06-26
super thanks so much, will do; but how do I reformat my kindle; what do I need to do?

---

### Post by Gone fishing on 2012-06-26
You could format using Gparted partition editor or the disk utility just make sure you format as FAT32.

---

### Post by Rrory on 2012-06-27
okay, used the disk utility, reformatted, but now Ubuntu can't detect my kindle, tried on my other laptop to check, *nada*

---

### Post by Gone fishing on 2012-06-27
Can't see why but ...

You could plug into Ubuntu and use gparted and see if gparted can see the device my guess is it can and for some reason it is not formatted correctly did you use FAT32?

However, it is probably easiest to reset the kindle to its factory specs - just like it was when it came out of the box. [http://resetkindle.info/](http://resetkindle.info/)

---

### Post by Rrory on 2012-06-27
You're a god! Works perfectly.

 I tried to make sure I kept FAT32 but I may have messed up. Did the reset just now and just loaded some books onto it no problem. :KS
I am so so grateful for your help & patience with me!
again thanks so much
rory

---

### Post by HiImTye on 2012-06-27
never, ever, ever, ever run graphical programs with 'sudo' use gksudo instead

also, never use this code:
```
 sudo mount -o remount,rw /
```
unless you are in recovery mode trying to fix a broken system.

this error:
```
 Nautilus could not create the required folder "/root/.config/nautilus".
```
is because you used 'sudo' instead of 'gksudo' - don't do that

if you have problems with not being able to log in when you reboot, then ctrl+alt+f1 from your login screen, log in to the terminal and type this to fix your broken system:
```
sudo chown -R <yourusername> $HOME
```
it should be painfully obvious that you need to replace <yourusername> with your user name

hope you don't end up with problems but at least now you have a starting point if you do

---

### Post by Gone fishing on 2012-06-27
Sorry my mistake should have been gksu nautilus not sudo nautilus.

I think what I suggested was not remounting / but try starting up in recovery and checking the file system

---

### Post by Rrory on 2012-06-27
arg; I don't have problems logging in; though my computer did freeze.Should I type the code in the terminal anyway?

---

### Post by Gone fishing on 2012-06-27
HiImTye's point is a good one if you sudo instead of gksu some important files in your home directory particularly .ICEauthority this **can** become root owned and then you cant login. To correct the problem as HiImTye points out, you start in recovery mode and at a root shell change the ownership of the files back to the user. I've been using Ubuntu since 5.10 (I think this has happened to me once - although I usually gksu)

This usually isn't a problem - but can be - if you can login it isn't a problem. It will do no harm to run run sudo chown -R <yourusername> $HOME or sudo chown -R yourusername /home/yourusernamein in a terminal if you can login as long as you don't miss type your user name. The command means 

sudo - get root privileges

chown = change ownership of files

-R - recursively i.e the directory and sub directories

but I wouldn't if you had a crash I doubt its related to this.

---

### Post by Rrory on 2012-06-27
okay, just ran that code & got

bash: username:   no such file or directory  

& yeah I used my real username. But then I have it set so I don't have to log in but shouldn't a file exist/directory exist?..hmm

---

### Post by Gone fishing on 2012-06-28
Do it like this ```
sudo chown -R gonefishing /home/gonefishing
```

---

### Post by Rrory on 2012-06-28
okay, did it, got:
chown: missing operand after 'username/home/username'

---

### Post by Gone fishing on 2012-06-28
not > username/home/username

but sudo chown -R username /home/username

the space is important the first username means owned by username, /home/username is the directory that you want username to own. (This is what they call a learning curve :D)

---

### Post by Rrory on 2012-06-28
yeah, sorry I missed the space & I do like learning okay done but now I get:

chown: cannot access '/home/username.gvfs' : Permission denied

---

### Post by Gone fishing on 2012-06-29
Don't worry about it thats because you are running the command from that directory and the file is in use - you have changed the permission of all the other files, /home/username.gvfs is locked and in use and you already own it. Probably you have changed the permission of no files as you already owned them.

If you wanted to run the command with no errors either start in recovery mode or log out and press the controls alt control F1 log in from a tty and then run the command to get back to graphical mode Alt Control F7

---

