---
title: "Copying from one disk drive to another"
date: 2008-11-03
forum: New to Ubuntu
---

### Post by Mark_in_Hollywood on 2008-11-03
This is the 3rd attempt at copying /home to an external hard disk drive, today.

I have an external 80 gig usb 2.0 hard drive. I want to copy /home to it. When the 80 gig (marks80 is the icon name and 'folder' name in /media) is powered up, at OS boot time, I get the .dmrc errors. Not a problem, I click OK and dismiss that. Many times I've posted about the .dmrc problem and cannot get the permissions set correctly, so, mostly the 80 gig drive is unpowered except during copying /home.

I tried gksudo nautilus to copy the /home to the 80gig. No luck finding it as my /home is on it's own partition (sda3).

At first, opening a Gnome file manager window and copying the /home to the 80 gig balked because of the directory lost+found. So, I drilled down one level to /home/mark (my user name is: mark) and tried to copy that to the 80 gig. At first I got another permission problem about .gvfs and clicked: "skip", and the copying proceeded ok, until the last 2 gig (of 30 gigs total to copy), when another permissions problem reared it's ugly head. The error message read:

/media/marks80/.config/transmission/gtk

and the file is: socket

I'm not good at fixing permisssion, well, I have never got the .dmrc permssions fixed (2+ years), so, I would like to have a way to copy my /home to the external usb drive, without so many problems.

---

### Post by Mark_in_Hollywood on 2008-11-03
This is the 3rd attempt at copying /home to an external hard disk drive, today.

I have an external 80 gig usb 2.0 hard drive. I want to copy /home to it. When the 80 gig (marks80 is the icon name and 'folder' name in /media) is powered up, at OS boot time, I get the .dmrc errors. Not a problem, I click OK and dismiss that. Many times I've posted about the .dmrc problem and cannot get the permissions set correctly, so, mostly the 80 gig drive is unpowered except during copying /home.

I tried gksudo nautilus to copy the /home to the 80gig. No luck finding it as my /home is on it's own partition (sda3).

At first, opening a Gnome file manager window and copying the /home to the 80 gig balked because of the directory lost+found. So, I drilled down one level to /home/mark (my user name is: mark) and tried to copy that to the 80 gig. At first I got another permission problem about .gvfs and clicked: "skip", and the copying proceeded ok, until the last 2 gig (of 30 gigs total to copy), when another permissions problem reared it's ugly head. The error message read:

/media/marks80/.config/transmission/gtk

and the file is: socket

I'm not good at fixing permisssion, well, I have never got the .dmrc permssions fixed (2+ years), so, I would like to have a way to copy my /home to the external usb drive, without so many problems. The file operations icon remains on the panel and never completes it's operation. Force closing it blows up the desktop and I have to reboot.

---

### Post by inportb on 2008-11-03
I believe the right way to recursively copy while preserving attributes and permissions is *cp -a source destination*. Use *sudo* if necessary. I just backed up and restored a home directory this way and it worked fine.

---

### Post by jbrown96 on 2008-11-03
try it from the command line ```
sudo cp -R /home/mark /media/folder
```
I believe the .dmrc issue can be fixed with this ```
sudo chmod 644 /home/mark/.dmrc
``` you might need to change the location of .dmrc. 
If you are using this for backups, try rsync. I believe this is the command, but others should verify it first. ```
sudo rsync -zvvr /home/mark/ /media/folder
``` then you can run this command each time you want a backup and it will only copy info that has changed, which makes the process very fast.

---

### Post by inportb on 2008-11-03
Cross-posting much?
[http://ubuntuforums.org/showthread.php?t=969605](http://ubuntuforums.org/showthread.php?t=969605)

---

### Post by Mark_in_Hollywood on 2008-11-03
> **inportb said:**
> The right way to copy while preserving attributes and permissions is *cp -a source destination* (*-ar* for recursion). I just backed up and restored a home directory this way and it worked just fine.

OK, I'm doing this as:

cp -ar /home /media/marks80

the disks are spinning. It takes about 30 minutes. For now, I'm marking this thread as solved, but I leave the Ubuntu-Linux community with one question.

Why is this cp -ar /source /desitination command not a part of some simple to use graphical interface which shows either file copied progress, either as a percentage? (example: 33%) Or as a bar filling up (much to much Microsoft like for my taste, but I'm only 'complaining' not writing code. (I'm an author, not a programmer).

Thanks community.

---

### Post by bodhi.zazen on 2008-11-03
> **inportb said:**
> Cross-posting much?
[http://ubuntuforums.org/showthread.php?t=969605](http://ubuntuforums.org/showthread.php?t=969605)

Threads merged.

---

### Post by inportb on 2008-11-03
I guess it's because people don't usually make backup archives using the filemanager. Typically, backups are automated.

I just realized that *cp -ar* is the same as *cp -a*, since *-a* implies *-r*. Going to edit my post above now =p

---

### Post by Mark_in_Hollywood on 2008-11-03
I can't get this to work. I'm not able to explain what is happening. And I'm frightened for my data (/home of 30gig, and I don't do p2p stuff. It's all my creations or saved stuff).

Following inportb's command:

cp -a /source /desination

I have a copy of /home on my external usb drive.

Since I'm trying to shrink the size of my / (sda1) (which included /home before it was moved to it's own partition (sda3). I went back to 

gksudo nautilus

deleted /home with shift-delete.

Rebooted. Ooooooooppppppppppssssssss!!! Home is gone and now the 80 gig drive won't let me copy it back to where it came from. AND I can't figure out the last part of the command structure. Please recall that 'mark' is my username and group name.

cp -a /media/marks80/home/mark/home /home

or should that be:

cp -a /media/marks80/home/mark/home /home/mark?

For the moment that doesn't matter as:

mark@Lexington-19:/media/marks80$ cp -a home /home
cp: cannot create directory `/home/home': Permission denied

and

mark@Lexington-19:/media/marks80$ cp -a home /
cp: preserving times for `/home/lost+found': Operation not permitted

although the last one does seem to be copying something, where I do not know.

---

### Post by inportb on 2008-11-03
Boot up as far as you can and get into a terminal. Then: (assuming you don't have /home on a dedicated partition. in that case, say so and we'll do something else)

```
sudo -i
mv /home /home0
mkdir /home
cp -a /media/marks80/home/mark /home/
```

... assuming that /media/marks80/home is a copy of your old /home and mark is your username.

---

### Post by Mark_in_Hollywood on 2008-11-03
After about 24 minutes, the copy from the ext. drive completed in spite of the lost+found permissions 'error'. After that, and a warm boot, "things" appear to be O.K. Please recall that my username & group name is: [COLOR="Lime"]mark[/COLOR]

and from poster:

jbrown96

[COLOR="Red"]try it from the command line Code:

...

I believe the .dmrc issue can be fixed with this 

Code:

sudo chmod 644 /home/mark/.dmrc

you might need to change the location of .dmrc. [/COLOR]

Where should .dmrc be found if not in /home? It has both a file and a folder with that name. 


From Recovery Mode I've done this so many times, I can almost remember the lines in my sleep.


chmod 700 /home/mark
chmod 644 /home/mark/.dmrc


AND IT JUST DOESN'T WORK. Tomorrow I will cold boot and get the .dmrc permissions message. ... sorry about all that, it's been a distressful day.

Lastly, can someone please verify the following as correct?

[COLOR="Blue"]sudo rsync -zvvr /home/mark/ /media/marks80[/COLOR]

---

### Post by jbrown96 on 2008-11-04
> **Mark_in_Hollywood said:**
> After about 24 minutes, the copy from the ext. drive completed in spite of the lost+found permissions 'error'. After that, and a warm boot, "things" appear to be O.K. Please recall that my username & group name is: [COLOR="Lime"]mark[/COLOR]

and from poster:

jbrown96

[COLOR="Red"]try it from the command line Code:

...

I believe the .dmrc issue can be fixed with this 

Code:

sudo chmod 644 /home/mark/.dmrc

you might need to change the location of .dmrc. [/COLOR]

Where should .dmrc be found if not in /home? It has both a file and a folder with that name. 


From Recovery Mode I've done this so many times, I can almost remember the lines in my sleep.


chmod 700 /home/mark
chmod 644 /home/mark/.dmrc


AND IT JUST DOESN'T WORK. Tomorrow I will cold boot and get the .dmrc permissions message. ... sorry about all that, it's been a distressful day.

Lastly, can someone please verify the following as correct?

[COLOR="Blue"]sudo rsync -zvvr /home/mark/ /media/marks80[/COLOR]

The rsync command will work; the -z flag is not necessary. It compresses the files for transfer, but since it is being copied locally, there is no advantage, and it will probably use more CPU. 

I don't really know about the .dmrc issue; it was really a guess. you may want to try changing the ownership (perhaps, it got changed to root) ```
sudo chown mark:mark /home/mark/.dmrc
``` the location may be different. I'm not at a linux box right now.

---

