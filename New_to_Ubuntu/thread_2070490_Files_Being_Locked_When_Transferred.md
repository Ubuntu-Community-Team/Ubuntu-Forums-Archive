---
title: "Files Being Locked When Transferred??"
date: 2012-10-12
forum: New to Ubuntu
---

### Post by Akacheebe on 2012-10-12
Ubuntu 12.04 running Mate 1.4.

This computer is one of 4 on my home network, two of which have Ubuntu 12.04 and one has Mint 12.  What I'm getting is when I try to transfer anything from Ubuntu to another computer on my network the file transferred is LOCKED when I try to do anything with it on the other computer??  This includes both an SQL database backup that is a .bz compressed file and also it has done this on a .doc file.

So can someone tell me why this is happening as I didn't have this problem prior to the Ubuntu 12.04 installs??

Thanks

---

### Post by newb85 on 2012-10-12
My guess is it's a matter of permissions.

By default, when a file is created, only the user who created the file (the file owner) has write-permissions for that file.  If you're not logged on to the other machine under the same user name, then as a different user, you won't have write-permissions.

Ideally, you would set your machines up with the same user name(s) so this wouldn't be an issue.

You can also change the permissions of the file by right-clicking on the file in Nautilus (or your favorite file browser) and clicking Properties.  Then go to the Permissions tab and make the appropriate changes.

---

### Post by Wim Sturkenboom on 2012-10-13
What you're saying is that you can't access the source file during a transfer? Or the destination file? What is 'locked'? Read access? Write access? Write would definitely make sense to me as you don't want files to change / get corrupted during a transfer.

Which application are you using for transfer?

Can not help further, but answers might help others to help you ;)

---

### Post by Akacheebe on 2012-10-13
I have a document on my desktop that has info in it that I wanted to transfer to another computer on my network that is running Mint 12.  

I transfer the file to the other computer and I can read it but I can't write to it to add info.  

Keep in mind that this hasn't happened with previous versions of Ubuntu or Linux Mint 12.  Just appeared since I reloaded these computers with Ubuntu 12.04.  

I also moved a copy of my forum database from this computer to the one I normally do backups to, which is the same one I've been using since I loaded Mint 12 on it that has the document that I can't write to.  That database file also is locked when it arrives at the other computer?  

As far as usernames and passwords go, ALL my Linux computers have the exact same username and passwords!  Been there, done that one before with a drive that wouldn't boot.  

Right click and properties shows in permissions that "nobody" owns it and same for group??

So I don't know how to explain it any better than this?  Stuff is locked that didn't use to be that way and as I said, it didn't show up until I installed Ubuntu 12.04 on this computer.

---

### Post by bbemmerful on 2012-10-13
I believe for security reasons the file is locked. did you try firing up the terminal and changing the permissions. CD to file location and chmod +rwx filename.

[//help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

---

### Post by newb85 on 2012-10-13
How exactly are you transferring these files?

---

### Post by Akacheebe on 2012-10-13
> **bbemmerful said:**
> I believe for security reasons the file is locked. did you try firing up the terminal and changing the permissions. CD to file location and chmod +rwx filename.

[//help.ubuntu.com/community/FilePermissions]("https://help.ubuntu.com/community/FilePermissions")

Don't know how to do this but I'm going to "assume" that the link you posted will tell me.  I'll go look.

---

### Post by Akacheebe on 2012-10-13
> **newb85 said:**
> How exactly are you transferring these files?

I go to "Network" then find the computer I want to transfer too, then the Downloads folder then send it over by copy and paste??  How else would one transfer files on a home network?

---

### Post by Akacheebe on 2012-10-14
I think I might have figured this out.

---

### Post by Wim Sturkenboom on 2012-10-15
By now you should know if your solution worked ;) Mind to share so others can benefit from it?

And if it's solved, you can also mark your thread as such using the thread tools just above the first post on this page.

---

### Post by Akacheebe on 2012-10-15
> **Wim Sturkenboom said:**
> By now you should know if your solution worked ;) Mind to share so others can benefit from it?

And if it's solved, you can also mark your thread as such using the thread tools just above the first post on this page.

Actually I didn't fix this problem as any files/documents transferred between these Linux computers are locked upon receipt.  :confused:

However I did figure out a work around though as I just stopped storing any files/pics/documents/downloads/etc on Linux and instead save them on Windows drives that are in each of these multi-boot systems.  Any files that are transferred to the Windows drives ARE NOT LOCKED??  Go figure!:confused:

You'll have to pardon me but I'm going to be brutally honest here as to me it's asinine to have these files transfers locked by default!  What other reason would anyone have to move files from one computer to another except to use them?:confused:

Ok, I'm done!

---

### Post by Wim Sturkenboom on 2012-10-15
Are you saying they're locked AFTER the transfer? That was not clear to me.

---

### Post by newb85 on 2012-10-15
As I understand it, you're transferring the files using the machine where they originate, which has Ubuntu 12.04.  Put another way, you're "pushing" the files.

Have you tried "pulling" the files--using the Mint 12 machine to find the files on the 12.04 machine?  Will the Mint 12 machine recognize the correct file owner/group while the file is still on the 12.04 machine?

---

### Post by Akacheebe on 2012-10-19
> **Wim Sturkenboom said:**
> Are you saying they're locked AFTER the transfer? That was not clear to me.

Yes that's correct.  They are locked after the transfer and when I say locked, what I mean is they are "read only" as those .doc files can be read, just can't be written to and the zipped MySQL database files can't be unzipped and I'm not sure that I could upload those to restore the database on my forum if I needed to??

Storing those files on a Windows drive makes sense in many ways for me though as I had a Linux drive become non-bootable back a year or two ago and I had a time recovering data from it.  Only way I got that data back was to reload that computer on another drive with Linux using the same username and pass then connecting that non-bootable drive up to that same computer and I was allowed access to them then.  The way I'm doing it now eliminates that problem as those files are always available on a Windows drive and I can access them from any Windows or Linux computer on my LAN with zero problems.  Should have done this a long time ago.  Live and learn I guess. 

newbe85, yeah I tried that but that didn't work either and BTW all, this isn't just a problem with Ubuntu as it also happens with Mint transfers back to Ubuntu 12.04 computers.

Thanks all

---

### Post by newb85 on 2012-10-19
On each system, compare the results of the command

```
cat /etc/passwd | grep username
```

(where username is your username).  Are there differences?

---

