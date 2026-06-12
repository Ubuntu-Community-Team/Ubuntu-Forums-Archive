---
title: "[SOLVED] moving files"
date: 2008-07-10
forum: New to Ubuntu
---

### Post by nothingspecial on 2008-07-10
In a day or 2 I`m going to have a external hard drive full of mp3 files arranged in folders artist/album/track.mp3.
I want to point gtkpod to this but also store other stuff on there.
I should have created a mp3 directory before I started but it`s too late now.
I saw in a post a few days ago a command that moves all directories, subdirectories and files into one directory but can`t for the life of me find it.
 So I want to move every file (except .trash) on the hard drive into one called mp3.
 What`s the command.
Thanks

---

### Post by stoneybroke on 2008-07-10
If you enter  sudo nautilus at command prompt you will get nautilus file browser with root privileges so you can create, modify move files and folders from that.

Hope that helps.

---

### Post by halitech on 2008-07-10
depending on how you mount the drive you may not need sudo (my 200gig external shows on my desktop and I have full read/write permissions so no need for using gksudo nautilus). Now as far what you are wanting to do, is it just the files on the external that you want to move from being in individual folders to one called mp3 or from your internal drive to the external?

---

### Post by nothingspecial on 2008-07-10
All the files are on the hard drive. I want to move all of them into one file called mp3. There are 15,000 files so I don`t want to drag and drop them.:)

---

### Post by nhandler on 2008-07-10
Well, it sounds like you are trying to move a large collection of mp3s. You can use the find command to search your computer for mp3 files, and then move them to a folder of your choice.

This command should work:

```
find / *.mp3 -execdir mv {} /path/to/folder
```

You can replace '/' with '~' to restrict the search to your home directory. 'mv' can be replaced with 'cp' if you simply want to copy the files, and '/path/to/folder' should be replaced with the actual path to the new folder.

---

### Post by nothingspecial on 2008-07-11
> **Cheater said:**
> Well, it sounds like you are trying to move a large collection of mp3s. You can use the find command to search your computer for mp3 files, and then move them to a folder of your choice.

This command should work:

```
find / *.mp3 -execdir mv {} /path/to/folder
```

You can replace '/' with '~' to restrict the search to your home directory. 'mv' can be replaced with 'cp' if you simply want to copy the files, and '/path/to/folder' should be replaced with the actual path to the new folder.

But wont that give me a huge file full of individual mp3s?
 I want to keep the file structures.
 
For example the first folder is called "AC-DC".

 Within that folder are 6 folders - "Back in Black", "For Those About To Rock" etc etc

Within those folders are the mp3 files.

This goes on and on right up to ZZTop.

There is nothing else on the hard drive.

I want to move all the Artist folders (containing album folders and mp3 files) into one folder on the hard drive called mp3.

Will

```
mkdir /media/New\ Volume/mp3
```

followed by ```


mv /media/New\ Volume/* /media/New\ Volume/mp3
```

do it, or will there be a problem because the new folder called "mp3" is in the same directory as all the folders I want to move?

I`m sorry if I`m not explaining myself very well.:)

---

### Post by hyper_ch on 2008-07-11
question 1: where on the harddisk have you stored your music files?
question 2: where do you want to move the music files to?

---

### Post by nothingspecial on 2008-07-11
It`s an external hard drive. It was empty.
Using the script found in this post I am in the process of converting all my flac files to mp3 files. I thought it was going to create a folder called mp3 to put the folders and files in. It didn`t.
When I click on the New Volume icon on my desktop I see hundreds of files. I just want to see one file called mp3
:)

Solved it all by myself by experimenting. 
mv /media/New\ Volume/* /media/New\ Volume/mp3
works it just gives an error about not being able to move mp3 into a subdirectory of itself.
Thanks

---

