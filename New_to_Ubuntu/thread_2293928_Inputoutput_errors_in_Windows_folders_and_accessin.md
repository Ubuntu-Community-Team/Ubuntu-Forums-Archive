---
title: "Input/output errors in Windows folders and accessing undamaged files"
date: 2015-09-08
forum: New to Ubuntu
---

### Post by zrennif on 2015-09-08
This is my first post here and I can confirm that I've tried Googling but haven't found what I need.

A family member's laptop has a Windows startup issue also affecting it's recovery mode, and from talking to the manufacturer's technical support it could be a virus that's causing the issue.  I am therefore attempting to recover the files by launching Ubuntu (version 15.04) from a USB.  However, while I can mount the Windows drive and access some of it's files and folders, when I try to view certain folders, I get an error saying "This location could not be displayed." with the body saying "Sorry, could no display all the contents of "Pictures": [this is an example of a failing folder] Error when getting information for file '/media/ubuntu/CC503C...a92/Users/[User Name here]/Pictures/tumbler_nd...400.jpg': Input/output error".

From what I have managed to find, this could be an error with the hard drive and in a drive test I managed to find, it failed.  The big issue is that when I try to copy the folder to an external hard drive, I am told "Error while copying." with "There was an error getting information about the files in the folder "Pictures", while the details section informs me that there was an error getting information for one of the files (a different one this time) in the folder.

I've been using the default Files program and despite a couple of tries, I'm too new to Ubuntu to be able understand how to install another file explorer.  I did however use the "ls -la" command I found to list the folder contents in the terminal which printed (not sure what the technical term is, sorry) about 8 of these errors and then the information for each of the rest of the files.  As there are a large number of these "good" files and I'd like to back at least those ones up, can anyone guide me to a way to copy those files across, perhaps with a different file explorer that will open the folder and just flag the broken files so I can select the good ones or something like that.  I sadly don't think it's feasible to manually copy every good file using the terminal as there are just too many.  (Edit - I've just found there are a total of over 1400 files so I really can't individually copy them.)

If there is a way, I'll sadly need pretty basic instructions.

Thank you all very much.

---

### Post by grahammechanical on 2015-09-08
I do not think that File Managers are designed to do the task that you are setting the file manager to do. It is always worth a try but often we need a program dedicated to the specific task of file recovery.

[http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step](http://www.cgsecurity.org/wiki/PhotoRec_Step_By_Step)

[http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step](http://www.cgsecurity.org/wiki/TestDisk_Step_By_Step)

Regards.

---

### Post by zrennif on 2015-09-08
Thank you so much, I've set PhotoRec to work. You don't happen to know if it is know for overestimating the estimated completion time: I don't believe there's more than about 150gb of data on the hard drive but it's currently estimating 278 hours and going up.

Thanks again.

---

