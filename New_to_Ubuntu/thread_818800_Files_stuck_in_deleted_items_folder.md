---
title: "Files stuck in deleted items folder"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by Allegretto on 2008-06-04
As the title says, there are some files in my deleted items folder which refuse to budge. If I try to delete them I get a message saying I don't have permission, and the same thing happens if I try to move them to the desktop (or elsewhere). I've attached a screenshot of the permissions box for them, and if I try to change anything there I just get the error:

> Sorry, couldn't change the permissions of "tabwidget.o": Operation not supported by backend

Does anyone know how I can remove these files?

Thanks.

---

### Post by Lord Xeb on 2008-06-04
You can use the following to delete them through terminal (WARNING! THESE ARE DONE IN ROOT AND CAN POSSIBLY DESTROY YOUR SYSTEM IF DONE WRONG!!!!!!!!!)

This is for directories
```
sudo su
rm -r <path to directory>
```


Were it says <path to directory> put the path to the directory that you want to delete. That means if I have a directory (AKA: folder for you winodows types) that I want to delete in my trash (which is pics)I do:

```
rm -r /home/nathan/.Trash/pics
```

This will delete that directory.

If it is a file I want to delete then I would:

```
sudo su
rm <path to file>
```


Again, were it says <path to file> I put the path to the file (which is file1). So if it is in my trash I would:

```
rm /home/nathan/.Trash/file1
```


this will delete that file.


Remember, this command could and will destroy or harm your system if done wrong (like puting in the wrong directory or file).

Once they are deleted they cannot be recovered.

---

### Post by jamewill on 2008-06-04
did you try from the command line going to the Trash folder and then deleteding

> sudo rm filename

---

### Post by jamewill on 2008-06-04
actually for me in hardy Trash is located at

/home/myusername/.local/share/Trash

---

### Post by drs305 on 2008-06-04
If you are uncomfortable with command-line deletes and know where the files are located you can open nautilus as root, navigate to the folders and delete them that way. Just use SHIFT-DEL to make sure you are not deleting them back into the same folder. And make sure you are able to view hidden files.

```
gksudo nautilus
```

---

### Post by Allegretto on 2008-06-04
> **jamewill said:**
> actually for me in hardy Trash is located at

/home/myusername/.local/share/Trash
It was there for me too.

Thanks a lot for your help guys. I used the first terminal command that was mentioned to delete the entire folder I couldn't get rid of, and it worked like a charm. 

I'm always slightly worried I'm going to destroy my entire system when fiddling with the terminal window. :)

---

### Post by dchurch24 on 2008-07-08
Hi all, I've tried the above, but no matter what I do I get the error that the files are read-only.

I have gone in as root and chmod 777 - R * on the entire directory, but that returned the same results.

I then did a gksudo nautilus and tried to delete the files, but got the same read-only files error.

I tried to change the files to read/write and it seemed to work.

Highlighted them all and pressed delete, only to get the read-only error again.

Has anyone any idea how I can delete these files, they is 1529.9 GB in there - so it's not to be sneezed at!!

---

### Post by dchurch24 on 2008-07-08
Yes, just to clarify, that's not a typo - it really is about 1.5TB - I have 2 2tb drives.

---

### Post by philinux on 2008-07-08
Using terminal

cd .local/share/Trash/files

then 

ls -l

What do the permissions look like?

A file in mine has 
-rw-r--r--

---

### Post by dchurch24 on 2008-07-08
Hi, there's no files in that location??

Yet, when I go to 'Deleted Items' from Nautilus there are thousands of files.

My trash folder must be somewhere else I assume?

---

### Post by dchurch24 on 2008-07-08
Ahh - found them (/media/disk-1/.Trashes-1000/files)

The permissions are all:

drwx------

---

### Post by philinux on 2008-07-08
Use gksudo nautilus to get to that folder then delete from there.

---

### Post by dchurch24 on 2008-07-08
Hi thanks for that, but I tried that before and it just gets me the same results.

Won't let me delete or change from read-only.

---

### Post by drs305 on 2008-07-08
Try this. I am assuming this is a NTFS partition. You will also need to know the partition name that the trash folder is on (**sdaX**, etc). Change the values in bold. If you don't know the partition, run "mount" and look for the NTFS entry.

If it is a VFAT directory, type the same except change **ntfs-3g** to **vfat**

To remove the files:

```

sudo umount /dev/**sdaX**
sudo mount -t **ntfs-3g** -o uid=1000 /dev/**sdaX** /media/disk-1
rm -r /media/disk-1/.Trash-1000/files
sudo mount -a

```

If that does not delete them, try placing sudo in front of the rm command line, but be sure to copy the entire line.

---

### Post by bumanie on 2008-07-08
In Gutsy the code is

> sudo rm -rf /home/yourusername/.Trash/*  

In Hardy the code is

> sudo rm -rf /home/yourusername/.local/share/Trash/files/*  

This will definitely work, but it is very powerful, make sure you are deleting the correct thing.

---

### Post by IanB2 on 2008-07-31
Another way of removing files without using the command line (that worked for me) is the following:

[LIST]
[*]Open your Home folder in the browser.
[*]Select 'View' from the drop down menu and check 'Show Hidden Files'
[*]Now navigate into the .local/share folder
[*]Right click on the 'Trash' folder and select 'Properties' at the bottom of the menu list
[*]Select the 'Permissions' tab on the form
[*]Now click on the button 'Apply Permissions to Enclosed Files' - (this reset my permissions so I could delete the stuck files)
[*]Finally go back to the Wastebasket and delete as normal
[/LIST]
Hope this helps ...

---

