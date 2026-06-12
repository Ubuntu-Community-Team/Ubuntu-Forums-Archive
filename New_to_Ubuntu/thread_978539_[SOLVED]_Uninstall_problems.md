---
title: "[SOLVED] Uninstall problems"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by MauriceS on 2008-11-11
First I apologise for the fact that I have uninstalled Intrepid and don't currently intend to go back to using Linux. I realise I may not be welcome in this community!

My installation was the trial version of installing on Windows XP, i.e. without creating a full ext3 partition for Ubuntu. For reasons I won't go into here I decided it was not for me. But I now have a hidden file or directory called C:\$Extend that I suspect is the Ubuntu paging file and therefore formatted in ext3. So far the only program which will find and try to access this is my antivirus (Sophos) which simply hangs trying to read it. I realise that I can configure Windows to read ext2 and ext3 partitions but I would sooner get rid of the problem altogether. So my question is: is there a way I can get back this partition in a non-destructive way so that it can be part of my main NTFS drive? Or am I asking for the moon?

Should be grateful for any insights!

---

### Post by shredder12 on 2008-11-11
You should have posted this question in some xp forums..they would have helped you in a better way..But still as far as i know they have some disk-management system where you can see all the partitions in your drive and format or delete any one..may be you should go there and try to delete that partition and format it..in NTFS..
May be that will work...

---

### Post by bumanie on 2008-11-11
Maurice, 
It is a shame you did not find ubuntu to your liking, but it is not for everyone. As for your problem, I would download a gparted live cd and see if you format the errant partition with that. I really don't know what C:\$Extend could be though.

---

### Post by Paqman on 2008-11-11
How did you uninstall Ubuntu? Through Add/Remove Programs in Windows?

If the other parts of your Wubi-installed Ubuntu have been removed then you should be able to just delete that file without it affecting Windows.

---

### Post by johntravis on 2008-11-11
In the past I found (in windows) that going to start >find/search >files & folders then typing in the programs name would bring up all the files/folders related, you can delete these and they will be gone. Use with caution as other files/folders hmay be related.

---

### Post by billgoldberg on 2008-11-11
> **shredder12 said:**
> You should have posted this question in some xp forums..they would have helped you in a better way..But still as far as i know they have some disk-management system where you can see all the partitions in your drive and format or delete any one..may be you should go there and try to delete that partition and format it..in NTFS..
May be that will work...

I'm no windows expert, but formatting the c drive (if it can be done from within windows) is a really bad idea.

--

To OP:

You will get better help in a Windows forum.

---

### Post by MauriceS on 2008-11-11
Thanks for everyone's comments and suggestions! Just to answer some of the questions:

Yes I did use add/remove programs to uninstall Intrepid and it seems to have done a clean job leaving only an empty folder called ubuntu-backup.

I can't see C:\$Extend in Windows Explorer, Search or the command prompt, only (so far) in Sophos Anti-virus. I have of course configured Explorer to see system and hidden files.

Following the suggestions above I have now installed IFS Drives and burned the Gparted live CD. Neither of these can find an ext3 partition on my hard drive. So I must apologise again, this time for having wasted your time through having wrongly diagnosed the probable source of my problem.

I have now submitted a support request to Sophos and hope they can help. While I don't worry too much about viruses in Linux, Windows is a different kettle of fish and I need to be able to scan for problems!

So thanks and apologies again - I'll mark this thread as solved (even though it isn't yet!)

---

