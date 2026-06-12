---
title: "[SOLVED] Files will not empty from trash"
date: 2008-08-31
forum: New to Ubuntu
---

### Post by Cokedriver on 2008-08-31
Kinda new to Linux and was wondering if there is a way to delete Folders with a X on them from the Trash:/// I have 2 folders in there that contain folders with X's on them and when i try to delete them it says:

The folder "CT_UnitFrames" cannot be handled because you do not have permissions to read it.

then i hunt around the internet for answers on what to do and keep getting these people that say goto /home/.local/share/Trash and delete from there but tis not there. Then i hear goto /root/.local/Trash and it is not even on my system.

Am i missing something here or and I totaly F.U.B.A.R.'ed any help would be great.

Also cause i thought it might work i have 2 partions one with is my storage and one in which is my OS and i reformated the OS one and reinstalled Ubuntu and yet the folders still appear.

Thanks for any Help on this matter.


Im Running 32bit Ubuntu Hardy on a AMD 64bit 4200+ with 2gigs RAM and a 250g SATA hard drive with a 128mb PCI-E Video card.

---

### Post by Sycron on 2008-08-31
Type in a terminal:```
gksudo nautilus
``` then go to trash and delete what you want.

---

### Post by Cokedriver on 2008-08-31
Thanks for the quick reply Sycron but when i do that the trash is empty and when i click on it it gives me this error message.

Sorry, couldn't display all the contents of "trash": Operation not supported

So still lost here.

---

### Post by Sealbhach on 2008-08-31
Hi,
I had that problem too.

Here's how it was fixed for me in this thread:

[http://ubuntuforums.org/showthread.php?t=891892](http://ubuntuforums.org/showthread.php?t=891892)


Type in the terminal:
```

sudo chown -R username /home/username/.local/share/Trash
```

substituting both of the "username" parts for your own Ubuntu user name. This makes you the owner of the trash can.

Then empty the stuff that's in there with:

```

rm -rf /home/username/.local/share/Trash
```

again, substituting "username".

This should fix it for ya.


.

---

### Post by Cokedriver on 2008-08-31
> **Sealbhach said:**
> Hi,
I had that problem too.

Here's how it was fixed for me in this thread:

[http://ubuntuforums.org/showthread.php?t=891892](http://ubuntuforums.org/showthread.php?t=891892)


Type in the terminal:
```

sudo chown -R username /home/username/.local/share/Trash
```

substituting both of the "username" parts for your own Ubuntu user name. This makes you the owner of the trash can.

Then empty the stuff that's in there with:

```

rm -rf /home/username/.local/share/Trash
```

again, substituting "username".

This should fix it for ya.


.


Thanks for the Reply Sealbhach but again there is nothing gone. When go into root the trash can there is empty but when im on my user account it shows having this folders. I will keep trying.

---

### Post by Cokedriver on 2008-08-31
> **Sycron said:**
> Type in a terminal:```
gksudo nautilus
``` then go to trash and delete what you want.

Just nioticed something. When i do the ```
gksudo nautilus
``` is get a waringing in the termal which reads as fallows. 


```
Initializing nautilus-share extension
Nautilus-Share-Message: Called "net usershare info" but it failed: 'net usershare' returned error 255: net usershare: cannot open usershare directory /var/lib/samba/usershares. Error No such file or directory
Please ask your system administrator to enable user sharing.


** (nautilus:5915): WARNING **: Unable to add monitor: Operation not supported
```

Maybe this has something to do with it. Not sure again still new to terminal and all its power.

---

### Post by unutbu on 2008-08-31
The problem might be that you need not only ownership of the file/dir but also read/write permissions.

Try [http://ubuntuforums.org/showpost.php?p=5105589&postcount=4](http://ubuntuforums.org/showpost.php?p=5105589&postcount=4)

---

### Post by Cokedriver on 2008-08-31
> **unutbu said:**
> The problem might be that you need not only ownership of the file/dir but also read/write permissions.

Try [http://ubuntuforums.org/showpost.php?p=5105589&postcount=4](http://ubuntuforums.org/showpost.php?p=5105589&postcount=4)
Thanks unutbu for your time in looking at this but still no luck. 

Maybe i explained this wrong or maybe people are not reading my main post. 

The location of the trash bin I am having issues with is Trash:/// not /home/<username>/.local/share/Trash <-- this folder is empty. On the other hand the Trash:/// has 2 folders in it and each one of those has 3-4 folders in them with X's on the folders.

Maybe this was a better explination or maybe not. Maybe i will have to just deal with the none empty trash bin on my desktop.

Thanks for any help with this Coke

---

### Post by drs305 on 2008-08-31
> **Cokedriver said:**
> Thanks unutbu for your time in looking at this but still no luck. 

Maybe i explained this wrong or maybe people are not reading my main post. 

The location of the trash bin I am having issues with is Trash:/// not /home/<username>/.local/share/Trash <-- this folder is empty. On the other hand the Trash:/// has 2 folders in it and each one of those has 3-4 folders in them with X's on the folders.

Maybe this was a better explination or maybe not. Maybe i will have to just deal with the none empty trash bin on my desktop.

Thanks for any help with this Coke

Take a look at my Trash tutorial. The link is in my signature line. Perhaps it will cover your situation. 

Good luck.

---

### Post by unutbu on 2008-08-31
Sorry Cokedriver, my mistake.
When you right-click on an item that won't go away, and select Properties, what is the Location of the item?

---

### Post by Cokedriver on 2008-08-31
> **unutbu said:**
> Sorry Cokedriver, my mistake.
When you right-click on an item that won't go away, and select Properties, what is the Location of the item?
Location is trash:///

---

### Post by Cokedriver on 2008-08-31
> **drs305 said:**
> Take a look at my Trash tutorial. The link is in my signature line. Perhaps it will cover your situation. 

Good luck.
Thanks drs305 for the link. When i run the 
```
sudo find / -type d -iname *Trash* | grep Trash
```
I get the fallowing message.

***********************************************
[sudo] password for cokedriver: 
/home/cokedriver/.local/share/Trash
find: /home/cokedriver/.gvfs: Permission denied
/Storage/.Trash-1000
***********************************************

Not sure if there is anything I can do with this info but there it is.

Coke

---

### Post by drs305 on 2008-08-31
> **Cokedriver said:**
> Thanks drs305 for the link. When i run the 
```
sudo find / -type d -iname *Trash* | grep Trash
```
I get the fallowing message.

***********************************************
[sudo] password for cokedriver: 
/home/cokedriver/.local/share/Trash
find: /home/cokedriver/.gvfs: Permission denied
/Storage/.Trash-1000
***********************************************

Not sure if there is anything I can do with this info but there it is.

Coke

What it is telling you is that you have one Trash folder in your Storage partition named .Trash-1000. You can empty that one by running "gksu nautilus /Storage/.Trash-1000". There would be two files within it, 'info' and 'files'. Just delete the entire "Trash" folder. It will be rebuilt the next time you delete something.

The .gvfs is the "g virtual file system". There aren't any files physically located there although it appears like a real file that is taking up a lot of space. This doesn't mean there isn't something wrong with .gvfs/fuse. I would try rebooting to see if your problems in this area are fixed.

---

### Post by Cokedriver on 2008-08-31
> **drs305 said:**
> What it is telling you is that you have one Trash folder in your Storage partition named .Trash-1000. You can empty that one by running "gksu nautilus /Storage/.Trash-1000". There would be two files within it, 'info' and 'files'. Just delete the entire "Trash" folder. It will be rebuilt the next time you delete something.

The .gvfs is the "g virtual file system". There aren't any files physically located there although it appears like a real file that is taking up a lot of space. This doesn't mean there isn't something wrong with .gvfs/fuse. I would try rebooting to see if your problems in this area are fixed.
That was it the files where ther thanks alot for the help they are gone now.

---

