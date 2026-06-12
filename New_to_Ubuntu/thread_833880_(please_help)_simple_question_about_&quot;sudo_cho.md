---
title: "(please help) simple question about &quot;sudo chown&quot;"
date: 2008-06-19
forum: New to Ubuntu
---

### Post by oarion7 on 2008-06-19
Hey there

I recently moved my home directory to a different partition and set up my fstab to mount that partition as my home directory, ran into a few minor problems in doing so but managed to straighten everything out. anyway, i did run into a small problem with permissions. many of the items in my home directory are now owned by root and this causes some apps to run incorrectly

so i tried:

```
cd /home/myname
sudo chown -R myname *
```

however this only makes me own every IMMEDIATE directory and files, it does not make me own files/folders inside SUBDIRECTORIES. is there a way i can suffix the chown command so that i take-own of everything in my home folder? thanks so much in advance

---

### Post by EXCiD3 on 2008-06-19
Interesting because i thought the -R mean recursive...

---

### Post by iaculallad on 2008-06-19
:confused: Appending the -R should recurse to sub-directories. Try this:

```
sudo chown -R username Folder_Name
```

---

### Post by RequinB4 on 2008-06-19
try using sudo chown -R -L myname *

---

### Post by sam_delta on 2008-06-19
try
```
sudo chown username -R /home/username/
```

note that the "-R" parameter goes just before the directory

sam

---

### Post by oarion7 on 2008-06-19
> **RequinB4 said:**
> try using sudo chown -R -L myname *

Tried this, also didn't work.


Actually, I think the reason the recursive command wasn't working was because of the syntax involved with the home directory, as if I type "cd /home/myname" it displays it as "myname@mycomputer:~$" - if that is the real reason or not, I actually was able to fix the problem by instead doing:

```
sudo chown -R -L myname /home/myname
```

for whatever reason using cd to get there and then using * just didn't cut it, I had to include the location in the command in this case. Not really sure why, but it worked! :)

Thanks for your help.

EDIT: Yep, exactly. Thanks Sam!

---

### Post by sam_delta on 2008-06-19
np, glad its working, enjoy ubuntu :)
sam

---

### Post by jamesisin on 2009-01-04
Are all the files/folders in my home directory supposed to be owned by me (and not root, for instance)?

I ran a recursive ownership/permissions change on my home directory (trying to fix something) and it seems to have borked my audio (no app actually plays any sound) and my Skype (won't quit) and maybe some other stuff.

What are the permissions supposed to look like in a working home directory so I can put things back in order?

I am apprehensive to use another recursive ownership/permissions command.

Oh, and for chmod and chown the syntax is always:

command -arguments NewOwnerOrPermissions /Directory/Or/File
chown -R Betty /home/Tom/Secrets.xml

---

### Post by GepettoBR on 2009-01-05
> **jamesisin said:**
> Are all the files/folders in my home directory supposed to be owned by me (and not root, for instance)?

I ran a recursive ownership/permissions change on my home directory (trying to fix something) and it seems to have borked my audio (no app actually plays any sound) and my Skype (won't quit) and maybe some other stuff.

What are the permissions supposed to look like in a working home directory so I can put things back in order?

I am apprehensive to use another recursive ownership/permissions command.

Oh, and for chmod and chown the syntax is always:

command -arguments NewOwnerOrPermissions /Directory/Or/File
chown -R Betty /home/Tom/Secrets.xml

The /home/usernameA folder should always belong to userA, and /home/usernameB to userB and so on and so forth, as well as every single file in each of those folders. If they belong to root, that's a problem because it can keep many applications from reading files they need to work properly. And yes you got the syntax right, though I don't know why Betty should own Tom's home.

---

### Post by jamesisin on 2009-01-05
Thanks for the information.  I don't know what's going on with my system at the moment, but I am literally chasing my tail.

Is there a way to search for files within my home directory which are NOT owned by me?  A search filter method to exclude my ownership (or alternatively to seek specific permission sets)?

---

### Post by GepettoBR on 2009-01-05
> **jamesisin said:**
> Thanks for the information.  I don't know what's going on with my system at the moment, but I am literally chasing my tail.

Is there a way to search for files within my home directory which are NOT owned by me?  A search filter method to exclude my ownership (or alternatively to seek specific permission sets)?

Probably, though I know of none. An easy way to set all permissions and ownerships right in your home directory without chown is via nautilus: right-click the folder (for example, /home/tom)&#12288;and select "Properties". On the Permissions tab, you should see that To is the owner. Make sure Tom has "Create and delete files" folder access and "Read and write" file access selected, click "Apply permissions to enclosed files" in the bottom of the window (this will reset the file access field to "---") and close the window. Tom should now own and have read-write access to everything in /home/tom.

---

### Post by jamesisin on 2009-01-06
I appreciate your concern/interest in my troubles.

I have gone through fixing my ownership/permissions thrice:

[http://ubuntuforums.org/showthread.php?t=976610](http://ubuntuforums.org/showthread.php?t=976610)

I'm not clear why it kept getting the bump, but it's stable for the moment (and I am checking my home directory permissions on occasion--feels like checking the fridge light).

I have also gone through these instructions a second time:

[http://ubuntuforums.org/showthread.php?t=789578](http://ubuntuforums.org/showthread.php?t=789578)

And again, I'm not clear why this one got mixed up from my fixing the above issue.  Anyway, I can play audio again.

Now I am just having an odd encoding issue:

[http://ubuntuforums.org/showthread.php?p=6501861](http://ubuntuforums.org/showthread.php?p=6501861)

---

