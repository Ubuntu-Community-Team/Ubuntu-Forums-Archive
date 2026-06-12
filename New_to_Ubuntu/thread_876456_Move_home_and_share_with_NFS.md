---
title: "Move /home and share with NFS"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by TJCIB on 2008-07-31
Basically, I want to move my /home directory to my second hard drive.
After that, I will share the new /home with 10 other computers via NFS.
I will create new users later, but I am waiting so that they are created in the new location, rather than having to copy them over.

Does having the /home directory on a second hard drive have any benefits when sharing over a network?  Will it increase transfer speeds and overall performance since its not on the same disk as the operating system?

What I am thinking is this:
copy current /home to second hard drive
auto mount second hard drive to /home on 1st drive
Share second hard drive via NFS, auto-mounting as well

Anyone see any pitfalls?
Should I use ext3 for the 2nd drive?
Am I wasting my time because performance won't be affected that much?

Thanks for your input and brainstorming.

---

### Post by bab1 on 2008-07-31
This is the classic way of unix to unix sharing.  Your home dir follows you whatever host you login from.  Yes on ext3 for the second drive.  When you mount off of /home have NOTHING in the directory or be prepared to not see it.  I leave a readme in my mounted directories as documentation.  It can read after you unmount the drive.

Edit:  If there is a downside it is speed (network) and complexity read up on NFS.  You also have to maintain a strict user/password structure or have a central user/password store (NIS or LDAP).

Edit2:  On re-reading your post I see some misunderstanding.  The most practical way of sharing /home is to mount the ***users*** home dir at /home.  That being said we do not put the /home on the 2nd disk.  Only the users directories.  /home is the mountpoint from the first disk.

---

### Post by Diabolis on 2008-07-31
I don't know if you'll get an increase in performace over your network. However, you do get benefits. If for some reason you need to do a ubuntu reinstall, your home folder and your files will be safe, you get to keep all your configuration too. Which I think is important, as sometimes is time consuming to make all the configurations needed to set your computer just right to meet your needs.

Recommended steps to move your home folder to another partition/drive:
[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by TJCIB on 2008-07-31
I do use NIS already.

Ideally, only the /home directory of the user that logs in would be mounted, but I don't think that's possible.

I have what you described already, mounting the users' directories from the "server" into the client's /home.
I was/am more worried about making the /home/*username* on the second hard drive, the sharing doesn't worry me.

Since its for a small school and we erase everyone's files at the end of the year, I'll probably just wait and do what I'm thinking on the next clean install.
Saving configurations and files over a long period of time is not too important.  We require students to have their own personal storage device, so as not to clog up our server.

*edit*
It is possible using autofs I believe

---

### Post by bab1 on 2008-07-31
Well -- In Solaris it is done this way /export/home.  Then you can mount the entire /home directory on the second disk.  Remember that you can't mount directly off of / !  You would not be able to see the other needed file systems (such as /etc, /usr, /bin). you can name the mountpoint as you wish; export is the traditional name.  Make sense?

Confession:  I forgot about the /export part. :-(

---

### Post by GrnFrag on 2008-07-31
what about
>  mount --move olddir newdir


?    wouldn't that move the entire contents of /home to a new partition?

---

### Post by bab1 on 2008-08-01
GrnFrag,

This is more about mounting the users home directory when logging in to any of one of multiple computers.  In Windows this called roaming profiles (and it is done in a very clumsy way).

In Linux (any unix) you can have one computer host the NFS share and have it automount your home (or any) directory to any local computer that you log into.

TJCIB,

Autofs is more for CDROM and floppy use.  It automatically unmounts the drive after you are done and allows you to remove the media.  You do not have to explicitly unmount.

---

### Post by arvevans on 2008-08-01
Quote:
[INDENT]Basically, I want to move my /home directory to my second hard drive.
After that, I will share the new /home with 10 other computers via NFS.[/INDENT]

Go to a terminal screen (the dreaded Command Line Interface/CLI) and enter "man mount".  Scroll down the man page using your keyboard arrow keys until you find:
[INDENT]Since Linux 2.5.1 it is possible to atomically move a mounted tree to another place. The call is
              mount --move olddir newdir
[/INDENT]
Use full path names for making the move.  But, first read over the rest of the information in the "mount" command.  You should find some other interesting stuff that applies to what you want to do.
_._

---

### Post by bab1 on 2008-08-01
arvevans,

I am sure that your solution (#8 ) will work on a one to one basis. TJCIB wants to have this done on a domain wide basis (in the background) as a client server solution.

Edit:  Moving the dir is not the problem.  Using NFS is the intent.

---

### Post by arvevans on 2008-08-01
OK.  Once the /home directory has been moved, go again to the CLI and enter "man nfs".  This tells all about setting up and managing an NFS file sharing system.

For even more detail you could locate and read the relative RFC documents:

[INDENT] NFS version 2 [RFC1094] 
NFS version 3  [RFC1813],
NFS version 4 [RFC3530][/INDENT]

These may be found at:

[INDENT]<http://www.faqs.org/rfcs/>[/INDENT]

Hope that helps.

Arv
_._

---

### Post by TJCIB on 2008-08-01
Thank you all.

I'll give it a whirl.

I already had NFS exporting the normal /home, so I'm sure it won't be too difficult to put /home somewhere else and then export that.

Peace!

---

