---
title: "Can't find my NAS on Home folders..."
date: 2013-01-18
forum: New to Ubuntu
---

### Post by Tarka Dal on 2013-01-18
So far I've had several problems that seem difficult to solve.
rdp?
Sharing my NAS?

How can I get the NAS to show in my Home folder so I can Grsync my NAS to my folders.

rdp that's an entirely different question.

---

### Post by helpee on 2013-01-18
#1, make sure you have samba installed

sudo apt-get install samba

#2
I've never tried this, but you could make a symbolic link to the network location of your NAS, eg

cd ~
ln -s smb://nasAddress nasAddress

Where nasAddress is the name of your samba shared folder. It might work...

You should probably just use nautilus and navigate there through the Network Locations tab to save yourself some trouble.

Cheers

---

### Post by mapes12 on 2013-01-19
Go to your /home folder then Ctrl+h to show hidden files. Find .gvfs then right click it and create a **Link to** folder for it. It creates a similar thing to a shortcut in windoze. Drag the Link to folder to where you want it e.g. Desktop. Mount your NAS then start Grsync. In the **Destination** field browse to your **Link to** file and inside it you should see your NAS drive.

If your NAS is formatted to NTFS or FAT then set the options in Grsync for the transfer to have --no owner --no group otherwise it can screw up permissions.

---

### Post by Tarka Dal on 2013-01-19
Samba is installed.
No .gvfs folder or file?

---

### Post by mapes12 on 2013-01-19
Go to Terminal then ```
ls /home
``` and post the output back here.

EDIT: If you're running 12.10 the gvfs folder is now at /run/user/YOUR_USER_NAME/gvfs

I'm on 12.04, hence the difference.

---

### Post by Tarka Dal on 2013-01-19
See Attached:

---

### Post by Tarka Dal on 2013-01-19
Sorry I'm a complete noob!

---

### Post by mapes12 on 2013-01-19
Look in /run/user/clive to see if you can find that gvfs file.

---

### Post by mapes12 on 2013-01-19
For Remote Desktop Protocol i.e. connections outside a local area network, I use [Teamviewer]("http://www.teamviewer.com/en/index.aspx").

---

### Post by Paqman on 2013-01-19
The easiest way to sort this if you're new is to install [gigolo]("apt:gigolo") and use it to set up access. No messing about on the command line or faff.

---

### Post by mcduck on 2013-01-19
...or just configure it directly from Nautilus itself, without the need to install any extra software. ;)

Just go to File->Connect To Server and set the type to "Windows Share.

After you've connected, you can simply bookmark the share to make it stick to the left-side panel in Nautilus.

---

### Post by Tarka Dal on 2013-01-19
@mapes12
I see what you did there!

Found .gvfs and then mounted NAS.
Then I tried to grsync as requested no problems until it got stuck on this file:
See Attached:

---

### Post by Tarka Dal on 2013-01-19
Thanks mcduck
But I have already done that before I came on the forum.
The problem is it does not show up in Grsync when you want to sync your files with the NAS.

---

### Post by mapes12 on 2013-01-19
Looks like you have Grsync to now connect to your NAS :)

Did Grsync give an error report when syncing the file in the screenshot?

---

### Post by Tarka Dal on 2013-01-19
Nautilus does not like certain files and I cannot delete them without having to restart the system...
Why is that?

---

### Post by mapes12 on 2013-01-19
I guess this is now moving on to a separate issue in which case you may get more help by starting a new thread for it. That said, trying to delete certain files when you're logged on in your normal user account can be a problem if the file permissions belong to another user, usually root. To get round this launch Nautilus as root like this. Terminal ```
gksu Nautilus
```Navigate to the offending file, highlight it then press Ctrl+del on the keyboard. It's important to do it this way otherwise all you will do is move the file into roots trash and clog up your system. BE CAREFUL what you delete this way as you are in your system as root and can do anything, including things that can break stuff. Once you've finished be sure to close Nautilus.

---

### Post by Tarka Dal on 2013-01-19
Thanks for your reply mapes 12.
What I tried to do first of all was copy these files with Nautilus.
Problems occurred twice.
So I asked if there was another way of transferring the files and I was told to use Grsync.
Using Grsync caused two failures of whilst trying to copy files. So I thought same problem as before!!!
So, next I deleted those two files and Grsync worked a treat.
Basically there were corrupted files I deleted them.
No more problem.

Now question is does Teamviewer work from Windoze 8 to Ubuntu.
I tried the regular way last night and got fed up after failing several times and it was way past my bedtime...

I'll try it now...

---

