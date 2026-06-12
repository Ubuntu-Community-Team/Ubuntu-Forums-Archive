---
title: "Is there a program that can detect duplicate files?"
date: 2012-02-15
forum: New to Ubuntu
---

### Post by MibunoOokami on 2012-02-15
Hi all, it's been a while since I've posted here.

As per the title, I am wondering if there is a program out there for Ubuntu that will detect duplicated files. For example, when I plug my camera in to dl pix my computer will copy ones that have been copied at an earlier time, whereas if I put the sd card straight into my computer it will detect duplicates. I have a habit of saving multiple copies of things in different folders all over my computer and on flash drives. I want a faster way of going through and seeing what I have double or triple copies of so I can clear out some space. At the moment I'm having to open a folder and then go searching through all the others individually.
I trust this makes sense but if it don't, please let me know. Thx in advance.

---

### Post by Rodney9 on 2012-02-15
FSlint is a toolkit to clean filesystem lint. It includes a GTK+ GUI
 as well as a command line interface and can be used to reclaim disk space.
It has an interface for uninstalling packages, and it can find things like:

   - Duplicate files
   - Problematic filenames
   - Temporary files
   - Bad symlinks
   - Empty directories
   - Nonstripped binaries

Available in the Software Center

Rodney

---

### Post by HermanAB on 2012-02-15
Yesh...

You can use 'find' to traverse directories recursively and let it exec 'md5sum', then write the results to a file, sort the file and identify duplicates that way.

Making a nice script for that should keep you out of trouble for a few days.

---

### Post by MibunoOokami on 2012-02-15
> **Rodney9 said:**
> FSlint is a toolkit to clean filesystem lint. It includes a GTK+ GUI
 as well as a command line interface and can be used to reclaim disk space.
It has an interface for uninstalling packages, and it can find things like:

   - Duplicate files
   - Problematic filenames
   - Temporary files
   - Bad symlinks
   - Empty directories
   - Nonstripped binaries

Available in the Software Center

Rodney

Please tell me there is a way to undo a deletion!? I found an instruction video on youtube how to use fslint, then I chose the select all but oldest and hit delete. Whilst waiting I was listening to music on rythmbox and saw my playlist starting to disappear. I went and poked around my folders, all the folders are there but _ALL_ of the music _FILES_ are gone as is around 95%+ of every other file that was on my computer.

What did I do wrong and can this be reversed? Forgot to say, trash has been partially emptied too. I was hoping the files would have gone there, but there is 2/3 less junk in there now than before.

---

### Post by MibunoOokami on 2012-02-16
I've just noticed something else strange which has me *very* confused. Before running fslink I had 180.4GB free space, now I have 158.4GB!? That makes absolutely no sense at all. How can I go from 180.4GB to 158.4GB after pretty much all my files have been deleted!? I should have gained space not lost it. 
Please help.

---

### Post by MibunoOokami on 2012-02-16
Apologies for bumping this thread but I'm desperate. Went to use open office last night, got an error message 
> Error loading BASIC of document
 file:///openoffice/3/user/basic/script.xlc/:
General Error.
General input/output error. I went to take a screen shot of this message but it went funny. I'm trying to upload it.
One website I went to is loading strangely no graphics just a bunch of lines of hyperlinks. Another site where you need to log in & have a security challenge pass phrase, accepts my login but keeps rejecting my pass phrase which cannot possibly be wrong since I have it written down and have used it many times before.
I don't know how to add the screen shot, definitely would have been worth seeing.

---

### Post by Rodney9 on 2012-02-16
I'm sorry I'm not sure what is going on.

Make sure you back up what you can.

Your hard drive may be corrupting.

If you can, it would be best to stop using that hard drive and use a live CD , the one you used to install Ubuntu, to copy/backup your files to a external drive.

You can try to run this in Terminal > sudo touch /forcefsck it will run a disk check at the next boot.

I'm sorry I can't be more help, It is hard to diagnose long distance.

Rodney

---

### Post by MibunoOokami on 2012-02-16
> **Rodney9 said:**
> I'm sorry I'm not sure what is going on.

Make sure you back up what you can.

Your hard drive may be corrupting.

If you can, it would be best to stop using that hard drive and use a live CD , the one you used to install Ubuntu, to copy/backup your files to a external drive.

You can try to run this in Terminal  it will run a disk check at the next boot.

I'm sorry I can't be more help, It is hard to diagnose long distance.

Rodney

Thanks for your reply Rodney. I have two additional questions. 1) Will I be able to get the deleted/missing files back using live CD? 2) If I reboot, will that not make the changes that have occurred permanent? 
I'm thinking back to my old windows days when it used to tell you to reboot to make changes permanent, so am a little worried.

---

### Post by Rodney9 on 2012-02-16
>  1) Will I be able to get the deleted/missing files back using live CD? 2) If I reboot, will that not make the changes that have occurred permanent? 
I'm thinking back to my old windows days when it used to tell you to reboot to make changes permanent, so am a little worried.  

You are correct the more you use the hard drive the more likely data will be overwritten.

Back up First

Maybe this will help - 

[https://help.ubuntu.com/community/DataRecovery](https://help.ubuntu.com/community/DataRecovery)

Rodney

---

### Post by MibunoOokami on 2012-02-27
Just thought I'd give an update. It's been brought to my attention that fslint isn't appropriate for beginners,  due to being not very user friendly and having a reasonably high risk of doing what it shouldn't. It's also very thorough at deleting stuff and there is no recovery for that.
The explanation I've been given for my problem is it's likely I accidentally hit a button between selecting the "select all but oldest" files and clicking delete. I don't deny this could've happened.
 As for the 20GB that has been mysteriously used... Who knows.

Anyway I'm backing up what few files I still have and I don't care how many copies I have anymore, then I'm going to install a fresh Ubuntu and try forget this ever happened. So we're clear, I'm not blaming anyone for this, sometimes shyte happens and we just move on.

---

