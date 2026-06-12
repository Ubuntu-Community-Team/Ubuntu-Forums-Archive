---
title: "[SOLVED] changing permissions with gui after copying from CD/DVD"
date: 2008-06-25
forum: New to Ubuntu
---

### Post by leemajors on 2008-06-25
quick question-

after copying files from a disc, they all have the "locked" emblem overlaying their icons.

how do you change permissions so these files are no longer locked?

---

### Post by terrorsathan on 2008-06-25
You need to change the permissions of the file(s). Open the terminal.

To unlock a single file enter:
```
sudo chmod 600 /path/to/file.txt
```
Where /path/to/file.txt is the file which you want to unlock.

To unlock all files in a directory and its sub-directories:
```
sudo chmod 600 -R /path/to/directory/
```
Where /path/to/directory/ is the directory.

I hope it helps.

---

### Post by starcannon on 2008-06-25
to do so using the GUI:

Alt-F2
gksudo nautilus

browse to the directory or file or files you'd like to change permissions on.

R-click on said directory, files, or file and look in the permissions tab, edit to your hearts content.

Warning, be very careful not to open permissions to wide on system or mission critical files, also BE WARNED you can delete anything you want intentionally or unintentionally while running nautilus as a super user, don't get hasty.

GL and have fun.

---

### Post by leemajors on 2008-06-25
many thanks! Tell me, whats the differecnce between gksudo and sudo?

---

### Post by starcannon on 2008-06-25
I haven't read up on it, but the local guru's say that you should use gksudo when you want to open a gui tool as super user, I believe I have heard them say it is more secure, its also nice because you don't have to leave a terminal(cli) window open while your doing your gui work.

Now I'm gonna have to go read on it and find out why its more secure, or perhaps someone here would be kind enough to give us the short answer?

---

### Post by mc4man on 2008-06-25
Just a little info on this "bug"( maybe it's a feature). Here's a short thread on it. [http://ubuntuforums.org/showthread.php?t=801528](http://ubuntuforums.org/showthread.php?t=801528)
In this case you don't need to be root to change permissions, you already own the files, folders, they're just set as read only for files, access only for folders. You could simply just right click -> properties -> permissions and change.
In the case where you have a folder with alot of files inside that could be time consuming
Or if you have alot of individual files same thing. In this case create a folder and initially copy all your files to it. (can do the same thing with folders if you choose)  
Then you can change permissions in one go
Ex. I copy a folder The Grateful Dead (Skull & Roses) with songs inside
from the terminal ```
cd Desktop; chmod u+rw -R 'The Grateful Dead (Skull & Roses)'
``` that will change the permissions of the folder and all the songs (files) inside.
The only problem is you have to type the full name of the folder correctly ect.
A better solution would be to create a holding folder for stuff you copy that needs the permissions changed with a simple name. 
Ex. I copy 3 folders and a # of files to a folder on desktop named copy
Then it's as simple as 
```
cd Desktop; chmod u+rw -R copy
``` this fixes the permissions of everything inside copy
note:
If you copy your files or folders to home dir. or to a holding folder in home dir then you don't need to 'cd Desktop' in your command
sudo vs.gksudo
[http://psychocats.net/ubuntu/graphicalsudo](http://psychocats.net/ubuntu/graphicalsudo)

---

