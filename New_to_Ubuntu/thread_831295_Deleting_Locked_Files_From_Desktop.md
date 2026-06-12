---
title: "Deleting Locked Files From Desktop"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by Anubis13 on 2008-06-16
Hi,

I am completely new to ubuntu. Trying to get my Printer up as well as my linksys wPC56G wireless card running I now have 2 files on my desktop I CANNOT move or delete. I searched the help forums and every delete or move command I tried in Terminal does not work. If I try and delete it says it is a directory if I try and move it says I do not have permission. Anyone know what this is about. Owner on both says "root" I just want to know how to move them or delete them if I can. Thanks

---

### Post by JoshuaRL on 2008-06-16
Right click it and in the Preferences menu go to the Permissions tab to change that.

---

### Post by ConMan318 on 2008-06-16
```

sudo rm FILENAME -rf

```

Just make absolutely certain your filename is correct, and don't use regex, because you could screw things up if you regex it wrong.

You could also delete everything within the directory, and then do
```

rmdir DIRECTORYNAME

```

which will remove an empty directory.

---

### Post by RomeReactor on 2008-06-16
Try this:
```
sudo chmod -R 777 ~/Desktop
```
And remove it using nautilus, or:
```
rm -R ~/Desktop
```

Note, however, that this will change permissions to **all** files and folders on the desktop and then remove them.

---

### Post by Anubis13 on 2008-06-16
Thanks  I tried all the others and only one that worked was RomeReactors. Luckily I have nothing on my desktop at the moment so all is well. Not off to try and figure out this Linksys wPC54G issue. Thanks to all for your quick response I can see why this is such good software. Mainly the community!! Thanks again!!!

---

### Post by ajgreeny on 2008-06-16
As long as you are careful, you can start nautilus with root permission by using **gksudo nautilus** in the run dialog (Alt+F2)  This will give you the ability to do things as root, so, as I said, be very careful.

---

### Post by Anubis13 on 2008-06-16
Thanks after I did a restart now I have all my files  showing up on the desktop which before did not happen. Does anyone know how I can get back to where I thought I  just had a Desktop folder and in it listed out only the files and programs I wanted. Not every file and folder. Thanks again if not I will play around with it.

---

### Post by RomeReactor on 2008-06-16
Please post a screenshot of your desktop. Also press ALT+F2, write or paste:
```
gconf-editor
```
go to 'apps->nautilus->desktop' and make sure the boxes for 'computer', 'home', 'network' and 'trash' are unchecked.

---

### Post by Anubis13 on 2008-06-16
Hopefully this is what you need. When I run that command I get Configuration Editor. I put all the  files into the "My Documents" folder to clean it up for now. Not sure if that was a good idea or not.

---

### Post by RomeReactor on 2008-06-16
Did you make that 'My Documents' folder, or did you make a link or dragged it from somewhere? Try ajgreeny's suggestion and use **gksudo nautilus** to delete the files; just be very careful not to change anything else and close Nautilus as soon as you finish.

---

### Post by Anubis13 on 2008-06-16
Yes I did make that to clean up the  desktop since I could not move anything. When I ran that command I went in as "root"  and I noticed that was how the files where set-up before I ran one of those commands. Basically, just root with Desktop. Now I have a little icon over my user name anubis which looks like the desktop so I am wondering if that is why all the files are there. Who knows I must have messes something up with one of those commands.

---

### Post by Ryklou on 2008-06-16
You can change the permissions to your username:

```
 sudo chown -R username:username <FILE> 
```

example:

```
 sudo chown -R francois:francois /opt/lampp 
```

then all you do is click on it the deleate it.

[COLOR="Red"][SIZE="2"][FONT="Courier New"][B]/*\DO NOT USE FOLLOWING CODE!!!!/*\
```
 sudo chown -R root:root /
```
This will cause root to be the only one to read/write! NEVER USE!!![/B][/FONT][/SIZE][/COLOR]

---

### Post by RomeReactor on 2008-06-16
It seems that somehow your home folder is linked to the desktop folder *within*. Not sure how to fix that, though.

---

### Post by ajgreeny on 2008-06-17
First make sure you have all your files backed up somewhere, preferably an external drive.  Open up the gconf-editor again with Alt+F2 and then go to apps>>nautilus>>preferences and make sure there is no check mark in the box for desktop_is_home_dir.  If there is, it is that which put your files, all of them, onto your desktop as home.  Remove it and if necessary restore the backup of all ther files you've just backed up, though I don't think that will be needed.

Good luck.  I hope this solves your problem.

---

### Post by MyNameUhBorat on 2008-06-22
I did what RomeReactor advised. And like someone said all my home folder files were on the desktop after I rebooted. But then I removed the folders from the desktop thinking that they would still be in the home folder in the main menu. All the files are still in the Trash but when I try to restore them my comp tells me I am out of space. Its telling me I have the same HDD space as I did prior to rebooting but I don't see any of the files except for the ones in the trash. Any suggestions?

---

### Post by RomeReactor on 2008-06-22
The commands I [posted on the previous page]("http://ubuntuforums.org/showpost.php?p=5199637&postcount=4"):
```
sudo chmod -R 777 ~/Desktop
```
and
```
rm -R ~/Desktop
```
were not correct; it's necessary to specify a wildcard to only manipulate the files, instead of the files *and* the actual desktop folder in the user's home directory. Not specifying the wildcard results in changing permissions of the desktop folder along with the files; the previous **rm** command also deletes the desktop folder, though it gets recreated almost immediately (I imagine that's why the files keep reappearing after a reboot). The correct commands are:
```
sudo chmod -R 777 ~/Desktop/*
```
and
```
rm -R ~/Desktop/*
```

I'm sorry for the inconveniences.

> **MyNameUhBorat said:**
> I did what RomeReactor advised. And like someone said all my home folder files were on the desktop after I rebooted. But then I removed the folders from the desktop thinking that they would still be in the home folder in the main menu. All the files are still in the Trash but when I try to restore them my comp tells me I am out of space. Its telling me I have the same HDD space as I did prior to rebooting but I don't see any of the files except for the ones in the trash. Any suggestions?
If possible, try to free up some space by backing up other files, so you can try to recover the ones in the trash. To try to recover them:
```
mkdir "Recovered Files"
```
to make a folder in which to move them; then:
```
sudo mv ~/.local/share/Trash/files/* ~/"Recovered Files"
```
to move them, and to set the permissions:
```
sudo chmod 777 -R ~/"Recovered Files"/*
```
If the files were correctly moved to to the 'Recovered Files' folder and you can access them:
```
rm ~/.local/share/Trash/info/*
```

Also try [ajgreeny's advice]("http://ubuntuforums.org/showpost.php?p=5205334&postcount=14") in the post right above yours.

Hope this helps.

---

### Post by MyNameUhBorat on 2008-06-22
RomeReactor thank you so much. Worked perfectly.So now I assume I use ajgreeny's advice to get all the folders off the desktop?

---

### Post by RomeReactor on 2008-06-22
Yes, try that and see if they show up again after a reboot.

---

### Post by MyNameUhBorat on 2008-06-24
Hey RomeReactor ajgreeny's advice unfortunately didn't work. The box is unchecked in nautilus. I tried as a test to delete a folder from the desktop and it removed it from both the desktop and home folder. This is very strange. Any ideas?

---

### Post by Riffer on 2008-06-24
Thanks RR.  Had a similar problem where files in my trash wouldn't be deleted because of the permissions.  With your instructions I could find them and change their permissions.  :)

---

