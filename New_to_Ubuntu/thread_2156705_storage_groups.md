---
title: "storage groups"
date: 2013-06-22
forum: New to Ubuntu
---

### Post by deanie44 on 2013-06-22
Hi.  I am really not a beginner to Ubuntu, but I am stumped at how to configure directories in Mythtv.  I would like to add a directory in the default storage group.  I am using Mythbuntu 12.04. I have the Ubuntu desktop installed, so the partition is already mounted.  I have read many articles on storage groups and directories, but I still do not understand.  I tried to install a new directory under the default storage group and a received an error message stating that /media/MYTHTV RECORDINGS/ does not exist.  What I am doing wrong?  Any help will be appreciated.  mary

---

### Post by grahammechanical on 2013-06-22
May be you are unaware that in Linux a directory/folder (they are the same thing) spelt MYTHTV is a different folder to one spelt mythtv. Also could you please explain how you tried to create a folder/directory. Did you use the file manager? A command in the terminal? Tell us what you did and then we may be able to tell you what you did wrong.

To create a folder inside another folder we have to be in or have the first folder open. For example, Ubuntu creates a default folder called Music. And suppose that I want to create a folder called Recordings inside the Music folder. I load the file manager. I open the Music folder and I right click the background of the opened Music folder and I select New Folder and one is created. I right click the new folder (called new folder) and select Rename and I rename the folder Recordings.

Now if I want to save a file into the Recordings folder I have to tell the application doing the saving where to put the file. I need to tell the application the path to the place where I want the file to be put. In this example, it would be /home/myusername/Music/Recordings. Usually the application has a graphical user interface that makes it easier, especially if we want the file to go on another partition. We browse the Save dialog to the partition and folder by selecting each in turn until we get to the folder we want the file to be put into.

I hope this helps a little bit. I do not have MythTV so I cannot give you directions but there usually is a GUi way to do things.

Regards.

---

### Post by deanie44 on 2013-06-23
Hi grahammechanical.  Thank you for answering my post.  In the mythtv wiki it says to go to the storage groups and you can add a directory.  I opened the backend of mythtv and navigated to the storage groups.  In the storage group section I highlighted the "add a directory".  I typed it /media/mythtv recordings.  That when i go the error that it is not the correct path and /media/mythtv recordings does not exist.  What i am trying to do is have mythtv send my recordings of the tv show "Castle" the Mythtv Recordings instead of the default storage group.  Does that make any sense?  Any assistance will be appreciated.  mary

---

### Post by bab1 on 2013-06-23
> **deanie44 said:**
> ...

 In the mythtv wiki it says to go to the storage groups and you can add a directory.  I opened the backend of mythtv and navigated to the storage groups.  In the storage group section I highlighted the "add a directory".  I typed it /media/mythtv recordings.  That when i go the error that it is not the correct path and /media/mythtv recordings does not exist.  What i am trying to do is have mythtv send my recordings of the tv show "Castle" the Mythtv Recordings instead of the default storage group.  Does that make any sense?  Any assistance will be appreciated.  mary

This is not a valid directory ```
/media/mythtv recordings
```

A valid directory would be one of these```

/media/"mythtv recordings"

/media/mythtv

```

If you are at the directory that you want to add a subdirectory to, you just need to declare the subdirectory name (recordings).  If you are not then you need to declare the entire path and subdirectory (i.e. /media/mythtv/recordings) with no spaces.  There can be more problems if the directory you are trying to create has spaces in the name (e.g. mythtv recordings).

In any event we need more information.  What are you using to navigate to the directory where you want to add a subdirectory?  What is the name of the subdirectory (recordings or "mythtv recordings")?

I don't use mythtv, but I can help you create a subdirectory where you want it.

---

### Post by deanie44 on 2013-06-27
Hi bab1.  Sorry it took me so long to reply.  Busy with work, school and kid.  What i am trying to do is place mythtv recordings on another partition which is windows.  In Mythbuntu 12.04.2 the partitions are already mounted.  I still do not understand how to complete this task.  Everytime I type /media/mythtvrecordings/Castle, i receive an error message stating that the path does not exist.  The partition --mythtvrecording--is mounted.  Is the path i typed incorrect?  Can you please help me?  mary

---

### Post by bab1 on 2013-06-28
> **deanie44 said:**
> Hi bab1.  ...
What i am trying to do is place mythtv recordings on another partition which is windows.

Are you saying that the partition that is mounted somewhere in the Linux file system (e.g /media/mythtvrecordings/Castle) is an NTFS formatted partition?  Is this partition on an external USB drive?
> 
In Mythbuntu 12.04.2 the partitions are already mounted.  

Do you mean *selected*?  Only the OS can mount or dismount a partition.  Earlier you mentioned *MythTV Storage Groups*, is that what you are referring to?  I'm not sure you have gotten the best MythTV advice at this forum in the past.  Although I don't use MythTV at all, I did read a bit on *Storage Groups*.  But that is the extent of my MythTV knowledge at this point.  I think it is important for us to separate the Linux file system support from the MythTV commands.
> 
I still do not understand how to complete this task.  Everytime I type /media/mythtvrecordings/Castle, i receive an error message stating that the path does not exist.  The partition --mythtvrecording--is mounted.  Is the path i typed incorrect? ...
Where are you typing these commands?  If it is in a MythTV dialog box, what is the EXACT error message.  If you are typing this into the terminal you are not giving the bash shell a command, only the directory ( /media/mythtvrecordings/Castle).  Lets start out by making sure the partition is mounted correctly to the file system.  Post the terminal output for these commands```

mount | grep /dev/sd

df -h

ls -l /media/mythtvrecordings

```

---

### Post by deanie44 on 2013-06-28
Hi bab1.  The entire system--Mythbuntu 12.04.2--on an usb external hard drive.  I partitioned the hard drive to include a ntfs file system.  I am hoping that i can use it to place the recordings there.  
i started the backend of mythtv and went to storage groups.  I sucessfully created a new storage group called TV SHOWS.  I am getting ahead of myself.  First I auto mounted a ntfs partition, which showed up in the TV SHOW partition.  Then I created the storage group called TV SHOWS.  Inside the new storage group they want a directory, which i try to do.  /media/TV SHOWS/mythtvrecordings.
Mythtv's backend says the path does not exist.  What a mess!  I followed your directions and took a screenshot of the terminal.  Help!  mary

---

### Post by steeldriver on 2013-06-28
Well, your immediate issue is that your filename contains a space - in the terminal, you need to either escape the space or quote the filename (or at least the part of the filename that includes the space) i.e. any of the following are 'legal' (NB filenames are also case sensitive - as you seem to have figured out)

```
ls /media/TV\ SHOWS
```

```
ls "/media/TV SHOWS"
```

```
ls /media/"TV SHOWS"
```

I won't comment on the broader picture except to agree with bab1 that the mythtv-specific advice you are getting here (although undoubtedly well meaning) should be treated with some care... I *do* use mythtv but I find the whole storage group / recording group / playback group thing VERY confusing and even the official wiki isn't very clear in places imho. FWIW (probably not a lot) my *limited* understanding is that **storage** groups are a behind-the-scenes feature meant for load / disk space balancing - if you want to catagorise recordings by genre / program / whatever so that they are easier to find in the frontend it *looks* like **recording** groups are the way to do that - I have just managed to set up some recording groups for that purpose on my own setup. But I am as likely to wrong as anyone else.

You *may* find that mythtv doesn't like having storage on NTFS... I don't know (NTFS doesn't support the same kind of file / directory permissions and ownerships as *nix - and mythtv seems to be picky about that)

---

### Post by bab1 on 2013-06-28
> **deanie44 said:**
> Hi bab1.  The entire system--Mythbuntu 12.04.2--on an usb external hard drive.  I partitioned the hard drive to include a ntfs file system.  I am hoping that i can use it to place the recordings there.

Was there a specific reason you *"partitioned the hard drive to include a ntfs file system"*.  This puts some limitations on you and ad @ steeldriver has said, might affect MythTV's operation.
> 
i started the backend of mythtv and went to storage groups.  I sucessfully created a new storage group called TV SHOWS.  I am getting ahead of myself.  First I auto mounted a ntfs partition, which showed up in the TV SHOW partition.

Do you mean *The NTFS partition?  The one you mentioned above; or a different one?*
> 
  Then I created the storage group called TV SHOWS.  Inside the new storage group they want a directory, which i try to do.  /media/TV SHOWS/mythtvrecordings.
Mythtv's backend says the path does not exist.  What a mess!  I followed your directions and took a screenshot of the terminal.  Help!  mary
Remember I don't know anything about MythTV.  What I'm trying to determine first is what the underlying file system looks like.  The Linux stuff if you will.

It's easier for both of us if you post a text output of the screen.  Do you have a desktop environment on the computer that you took the screenshot of the terminal?  If yes it would be better to just copy and paste the text into the forum editor.  If you can do that return the output of ```
ls -l /media
```

---

### Post by deanie44 on 2013-06-29
Hi Bab1.  Is this what you mean?

maryhigginsrice55@maryhigginsrice55:~$ ls -l /media
total 0
maryhigginsrice55@maryhigginsrice55:~$

---

### Post by bab1 on 2013-06-29
> **deanie44 said:**
> Hi Bab1.  Is this what you mean?

Yes it is.  But I expected to see directories below /media
> 
```
maryhigginsrice55@maryhigginsrice55:~$ ls -l /media
total 0
maryhigginsrice55@maryhigginsrice55:~$
```
Earlier you said this[QUOTE]... i try to do. /media/TV SHOWS/mythtvrecordings.
Mythtv's backend says the path does not exist. ... 

I believe MythTV needs you to make the directories you will need.  Make the directories and then retry the command ```
ls -l /media
```

[/QUOTE]

---

