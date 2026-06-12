---
title: "[SOLVED] My wits' end: Bash, cron, and file permissions"
date: 2008-08-28
forum: Programming Talk
---

### Post by EvilMarshmallow on 2008-08-28
I hope you can help me out here...

I have a bash script that runs in cron once per minute.  Its job is to get data from a scale system in our plant and save the info into a mySQL database.  It downloads via FTP a text file with all the data, compares it to the last time it downloaded the file, and uses diff to pull the new records out.

My problem is that the data file doesn't get updated... its owner is root and its permissions are 600.  This means that my comparison doesn't work and I'm getting duplicate records.  If I could change the permissions on this file to 777 I could do everything I needed to, of course... but how do I do this from bash?  Simply adding the line "chmod 777 file.txt" doesn't work.

---

### Post by Coolcool on 2008-08-28
[http://sikh.myminicity.com/](http://sikh.myminicity.com/)

---

### Post by dwhitney67 on 2008-08-28
You are going to have to elaborate a little more on the problem you have.

Text files generally do not have the "execute" permission set, thus if you want to share to the file with every user on the system, so that the file can be read and written to, the mode for it should be 666.  But I don't recommend this; set it to 600 or 644.

The root account will have privileges to peek (and write) into any file.

IMO, your script should have permissions no greater than 744.

Does your script work when you run it manually from the command line?  It might be helpful to know, because if it doesn't, then it will never run successfully from cron either.

---

### Post by EvilMarshmallow on 2008-08-28
Ok, here's how it works:

1.  Download the file from the scale, call it "file1.txt"
2.  Compare the data in the file against the data in an existing file, "file.txt".  Using Diff, I can determine which records are new.  Store those records in a file called "newrecords.txt" and loaded into the database.

3.  Overwrite file.txt with the contents of file1.txt.  This is so that I know I've got an up-to-date list of what went into the database.  THIS IS THE PART THAT FAILS.

File permissions are as follows:

file1.txt: owned by the user who's logged in, 666.
file.txt : owned by root, 600.

The problem is that file.txt never gets updated, which I attribute to the fact that the permissions are different.  I can't delete the file unless I'm root.

So what can I do to change the permissions?  It doesn't *need* to be owned by root.  It needs to be owned by the logged-in-user.  I have set the directory in which these files reside to be owned by the logged-in user.

If I run the script from the command line, it seems to be ok.... file.txt ends up being owned by the logged-in user.  But having it run from a cron job has it owned by root.

---

### Post by dwhitney67 on 2008-08-28
Ok, well that's make sense.

When you are running the script using cron, it is in essence being executed by 'root'.  Thus the reason your file.txt has the 600 permissions (although I would have expected to see 644).

If you turn around and try to execute the script as a regular user, you will have trouble overwriting the file.txt.  Reason: permission denied.

I presume your script is moving the file1.txt to file.txt, so in your script maybe something like this would suffice:
```
mv file1.txt file.txt
chmod 666 file.txt
```
Just beware that any user on the system can remove, write to, or replace file.txt in this situation.  This is not very secure!

P.S.  This still may not work.  You may need to change the ownership of the file as well, in which case the file-mode can be stepped down (a 666 is not needed; a 644 or even a 600 would suffice).
```
chown user:user file.txt
chmod 644 file.txt
```

---

### Post by EvilMarshmallow on 2008-08-28
Thanks for getting me on the right track.  It ended up being a logic problem:  instead of deleting the file, replacing it with a new one, and modding permissions, I ended up rewriting my script to append info to the file such that it's never actually deleted.

It was a little hairy because they're actually running production on that line today, so I was making changes while they were weighing things up... but it's done.

Thanks again for your help.

---

