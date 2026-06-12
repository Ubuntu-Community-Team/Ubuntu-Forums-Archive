---
title: "&quot;cdtar not found&quot; when trying to backup to file"
date: 2012-07-02
forum: New to Ubuntu
---

### Post by remmian on 2012-07-02
Hello,  

I am not even good enough to be a newbie @ Linux. So please spell out any answers as if you are speaking to someone who knows absolutely (and I mean absolutely) nothing.   

I found this handy thread that explained how to manually backup the entire drive to a single file for quick restore in case of catastrophe: [http://ubuntuforums.org/showthread.php?t=35087 ]("http://ubuntuforums.org/showthread.php?t=35087")

It worked great for Ubuntu 11.01, but now that I upgraded to 11.10, when I run the command I get the error "cdtar: command not found" .

I realize Ubuntu 11.10 has built-in backup, but it only backs up user files, it does not create a disk image. And pls don't advise upgrading to 12.x as the upgrade process is why I went looking for a backup remedy. When I let it upgrade itself from 11.10 to 12.x it hung halfway through the upgrade process, making the machine unbootable. Hence, I had to start from scratch reinstalling 11.10... backing up... then letting it upgrade to 11.10... and now I want to backup again before I try the upgrade to 12.x again. I have also looked at Clonezilla but it is very confusing to me... (i.e. server or client and have to make a bootable USB or disc to backup or restore....) I just want a file I can easily create/restore through manual means.  

Thanks to anyone who can help...!

---

### Post by anewguy on 2012-07-03
There are a LOT of posts in that thread - can you point us to the one you are referencing?

I also have a suspicion, but since I don't know that thread I'll feed you my suspicion:

Are you sure there isn't a space between cd and tar:

cd tar

not

cdtar

---

### Post by remmian on 2012-07-03
> **anewguy said:**
> There are a LOT of posts in that thread - can you point us to the one you are referencing?

I also have a suspicion, but since I don't know that thread I'll feed you my suspicion:

Are you sure there isn't a space between cd and tar:

cd tar

not

cdtar

Thanks.... the post I was referring to was the very first one in the thread.

I suspected I left out a space too, went and retried the command again making sure to leave a space after the cd and before the / and the command worked, so was coming back here to say so and saw your reply. You guessed right. :)

And for anyone interested, the entire command is in that first post in the other thread I mentioned, but it reads like this:

sudo su     [enter]

(Here is might ask for your admin password but won't register your keystrokes... just type the password  and hit Enter)

cd /         [Enter]   (And here's where I left the space out after the cd)

tar cvpzf backup.tgz --exclude=/proc --exclude=/lost+found --exclude=/backup.tgz --exclude=/mnt --exclude=/sys /   [Enter]    

At this point it backs up the entire drive to a compressed file in the root (filename backup.tgz or whatever you name it). You can then copy the file to an external drive for safekeeping.

To restore you would boot into the OS, or if it isn't bootable, a live drive, then make sure the backup.tgz is in the root and type:

tar xvpfz backup.tgz -C /

Once the file is restored the excluded directories need to be recreated with the command:

mkdir proc
mkdir lost+found
mkdir mnt
mkdir sys

etc... (if you excluded other directories)

And again, all credit goes to "Heliode's" tutor in the first post of this thread:
[http://ubuntuforums.org/showthread.php?t=35087](http://ubuntuforums.org/showthread.php?t=35087)

Thanks for replying.... hope this helps someone else.

---

