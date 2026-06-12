---
title: "Problem getting local apps to open files on Windws share..."
date: 2008-07-13
forum: New to Ubuntu
---

### Post by mingle on 2008-07-13
Hi,

Getting access to my XP shares on my Ubuntu 8.04 install (and vice-versa) was a breeze - a delight in fact!

Now I can copy files from my XP shares to my Linux box and I can view/load/play files from my Ubuntu share on my XP boxes and it all works like a charm (I have to say I'm VERY impressed with the ease it all worked!)

There was no mucking around with command lines or consoles and the only thing I had to install was Samba on my Ubuntu box - very nice!

The only minor fly in the ointment is that when I'm on my Ubuntu box and I try to double click on a picture, MP3 or video file I get a requester "Allow application access to keyring". I click on the "Always Allow" button and the picture viewer/music player/video player (or whatever) application opens, but then it can't load the file (gives various 'not found', 'unable to access' etc messages)

Obviously the apps are trying to use the password to access the XP share (to be able to access the various files) on my XP box, but it's failing.

Is there something else I need to do?

Cheers,

Mike.

---

### Post by Dedoimedo on 2008-07-13
Hello,

Might be a permissions problem.

Try copying a few files to a local (Ubuntu) system and run them from there. Check the permissions to see who is allowed to do what.

You can check permissions by typing ls -la in terminal.

Then, you'll get something like this:

r--r--r-- or rwxrwxrwx

These are permissions.

r - read
w - write
x - execute

The three times they show up are for:

U - user - owner of the file
G - group - members of the group to which the file belongs
O - other - other users

Thus for example:

rwx------ means only the owner can manipulate the files. If you're trying to access a file like this from another account, you'll fail.

XP files have their own owner, your Ubuntu account is prolly different.

So, try copying the files and if needed change their permission with sudo chmod 777 filename - to see if this solves the problem.

Dedoimedo

P.S. The permissions also have numerical values:

read - 4
write - 2
execute - 1

Thus together: 4 + 2 + 1 = 7

Thus 777 means read, write, exexute for user, group, other. Another example, 444 means read for user, group, other. 664 means read and write for user and group, but only read for other. And so forth.

---

### Post by mingle on 2008-07-13
Hi thanks for the reply.

I can play the files fine once I've copied them to my Ubuntu box, so it doesn't appear to be permissions.

The problem seems to be that the local Ubuntu apps (picture views, MP3 player, PDF viewer, etc) are unable to connect to the XP share.

I can copy files backwards and forwards (using the file manager) without any issues.

Cheers,

Mike.

---

