---
title: "[SOLVED] Vista partition empty?"
date: 2008-06-04
forum: New to Ubuntu
---

### Post by kevn3k on 2008-06-04
Hi everyone,

I recently installed Ubuntu 8.04 on my work computer (while keeping my Vista install intact, just in case, it *is* at work, after all, haha) and I've managed to mount my vista partition.  However, when I open the partition, I hardly see any of my files.  Lots of folders, but if I go to the My Documents folder for my username, there are just a bunch of empty folders (Start Menu, My Music etc... all empty) and a couple NTUser.dat files.  Am I doing something wrong?

---

### Post by KingTermite on 2008-06-04
I suspect its a file permission issue. Personal folders (like your "my docs") won't display for just "anybody". It does have "some" security.

You probably  have to let it know who you are (as the windows user), but I'm not sure how you can do that.

---

### Post by dracayr on 2008-06-04
> **KingTermite said:**
> I suspect its a file permission issue. Personal folders (like your "my docs") won't display for just "anybody". It does have "some" security.

You probably  have to let it know who you are (as the windows user), but I'm not sure how you can do that.

NTFS doesn't support owners. If it's a permission issue, I don't see how he would see some but not all. 

@kevn3k: to rule a permission issue out, type

```
gksudo nautilus
```

in a terminal and try again. If it works, post the output of ```
cat /etc/fstab
```

dracayr

---

### Post by KingTermite on 2008-06-04
> **dracayr said:**
> NTFS doesn't support owners. If it's a permission issue, I don't see how he would see some but not all.Unless I'm misunderstanding your statement, sure it does.

User A can not just plop around the drive and look at "any" file. User B's documents and personal directories are "off limits" to User A (unless User A is an admin).

Now, I'm not sure if this is file system supported or OS supported, but I know a level of user protection exists.

---

### Post by dracayr on 2008-06-04
> **KingTermite said:**
> Unless I'm misunderstanding your statement, sure it does.

User A can not just plop around the drive and look at "any" file. User B's documents and personal directories are "off limits" to User A (unless User A is an admin).

Now, I'm not sure if this is file system supported or OS supported, but I know a level of user protection exists.

In linux, which uses the ext3 filesystem, that's true. Not so for windows, whose filesystem ntfs doesn't support owners.

dracayr

---

### Post by kevn3k on 2008-06-04
Well, that wasn't it... I still get the same errors... any other ideas?  If I boot into Vista, my files are all still there, so I know they're there... I just don't know why I can't see them.

(On an aside note, how would I use sudo to give myself read/write permissions to a USB flash drive?  Somehow they got revoked when I was transferring files...)

---

### Post by dracayr on 2008-06-04
> **kevn3k said:**
> 
(On an aside note, how would I use sudo to give myself read/write permissions to a USB flash drive?  Somehow they got revoked when I was transferring files...)

You should have read/write permissions for an USB flash by default. Anyway, If you haven't, just use the same command I posted above

dracayr

---

### Post by kevn3k on 2008-06-04
I know I *should* but for some reason or another I don't... is there a way to enable it so that my regular user can have those privileges again?  I'm still having no luck with recovering my Vista files directly through Ubuntu, and I'm not looking forward to transferring them all on a USB key...

---

### Post by wannadumpwindows on 2008-06-04
Not really any help, but I also have a dual boot set up with Vista, and I didn't have to do anything special to be able to see my files. After the first time I installed, all I ever had to do was enter the sudo password when I tried to open it up. Everything was always there all on it's own, and I can see and use every single file on the partition. So it might be something more specific to your machine or set-up.

---

### Post by wannadumpwindows on 2008-06-04
P.S. I have Vista Home Basic, so I don't have BitLocker or any other type of drive encryption on the vista drive. Could it be an issue with that?

---

### Post by kevn3k on 2008-06-04
It might be an issue with securities at work then... That's not a huge deal, I'm really  more concerned since I want to try this out at home and I don't want to have to lose all my files, though I run XP at home... shouldn't be an issue, both are NTFS, right?

---

### Post by KingTermite on 2008-06-04
Found some possible help elsewhere via Google:
[http://www.linuxforums.org/forum/debian-linux-help/34923-mounted-ntfs-permissions-ubuntu.html](http://www.linuxforums.org/forum/debian-linux-help/34923-mounted-ntfs-permissions-ubuntu.html)

---

### Post by Shazaam on 2008-06-04
ctrl+h while in nautilus? (view hidden folders/files)

---

### Post by dracayr on 2008-06-04
> **Shazaam said:**
> ctrl+h while in nautilus? (view hidden folders/files)

ctrl+h lets you see files and folders that begin wit a dot ('.'). That doesn't have anything to do with hidden, they are just not shown because else your home directory would look very messy. However, I don't assume that all his files begin wit a dot :P

dracayr

---

### Post by The Cog on 2008-06-04
I have a feeling the files are not where you are thinking they are. I am guessing that the contents of My Documents changes depending on who is lgged in - the real files are elsewhere, somewhere under Profiles or Documents and Settings perhaps.

---

### Post by KingTermite on 2008-06-04
> **The Cog said:**
> I have a feeling the files are not where you are thinking they are. I am guessing that the contents of My Documents changes depending on who is lgged in - the real files are elsewhere, somewhere under Profiles or Documents and Settings perhaps.

That's a good point....the "my documents" for a particular user is normally in something like:
C:\Documents and Settings\<username>\My Documents

If you just had a c:\my documents or something like that you were looking in, that isn't where your files are really kept.

---

### Post by kevn3k on 2008-06-05
Sorry for the delay... went home and had to build a computer, watch the stanley cup finals (good job red wings!) and such...

Haha, no, sorry, I should've mentioned that I had thought instantly that "of course it's not my user" and checked the other users, too, but nothing shows up anywhere, really, as far as my personal files go.  Other files, like programs, etc... installed into the C:\ drive are still there, though.

---

### Post by kevn3k on 2008-06-05
Aha! It turns out they weren't under my username at all!  I sort of maybe forgot that I was simply using that name to log onto the server, rather than the actual computer itself. >.<  Sorry about that.  The entire time my files were being saved under the name of the computer rather than my login simply because of the way the network's set up.  Thanks for all your help though, exploring your solutions definitely made me more comfortable with Ubuntu!

---

### Post by Sef on 2008-06-05
> Aha! Found the files. I was right, it had to do with securities at work. Thanks for all your help guys!

Could you post more exactly what you did to solve your problem.  Thank you.

---

