---
title: "Moving files from one user to another"
date: 2011-10-21
forum: New to Ubuntu
---

### Post by Swaly on 2011-10-21
Well, I've been searching for a while on how to move my files from my original admin account to my new admin account (and then I would delete the older one, as I was fooling around with it's appearence, and before I knew it Unity was gone...  and I've been unable to do pretty much anything in it.  Except, there was still a bar at the top after I restarted my netbook and I've able to use the normal settings and see its files.).  The best information I found was here: [http://ubuntuforums.org/showthread.php?t=514493]("http://ubuntuforums.org/showthread.php?t=514493&page=2")

So I tried the following code in terminal:

[HTML]sudo mv /home/lewnna home/swaly[/HTML]And then it asked for my password, and I entered it, and after that I got:

[HTML]mv: cannot move `/home/lewnna' to `home/swaly': No such file or directory[/HTML]I tried a whole bunch of other ways to write in the user files, as I'm not a pro with computers, so I just basically tried anything.  And the only other result I could get from terminal was:

[HTML]mv: cannot stat `/home/lewnna': No such file or directory[/HTML]Is there something I'm doing wrong?  All I want to do is move my stuff from lewnna to swaly.  If there are any other ways of doing so, please let me know.  Any help would really be appreciated.

And I am using Ubuntu 11.10, if that's important to know....

[I]EDIT:
[/I]
I also tried:

[HTML]sudo cp -r /home/lewnna/ /home/swaly/[/HTML]Didn't work.

I also understand that using the following code should've helped:

[HTML]gksu nautilus[/HTML]But it didn't.  I tried looking through the root folder but it always took me back to the home folder and all I could get was the desktop.

---

### Post by Paqman on 2011-10-21
> **Swaly said:**
> 
I also tried:

[HTML]sudo cp -r /home/lewnna/ /home/swaly/[/HTML]Didn't work.


Try:
```
sudo cp -r /home/lewnna/* /home/swaly/
```
The difference is that you want to copy everything *within* those folders, rather than the folders themselves.

You'll also have to make sure the permissions are set for the right user. So after moving all the files over take ownership of them by:
```
sudo chown -R swaly:swaly /home/swaly
```

---

### Post by cozumel on 2011-10-21
@ Swaly

I don't think you are writing the code correctly.  You missed out one of the /

Should be```
sudo mv /home/lewnna /home/swaly
```which would copy the directory.  Correction it would move the directory
or

```
sudo mv /home/lewnna/* home/swaly/
```which would just copy the files.  Correction, it would move the files

Don't forget about changing ownership

I should mention that I am noob and only 7 days into Ubuntu so wait for someone else to confirm that I am understanding the code correctly as I don't wish to create problem with your OS

---

### Post by cozumel on 2011-10-21
Posted the same time as paqman lol.

Don't know if it is important.  But if you do choose the copy option I think that it merely copies all the files without placing them in correct locations or sub-folders.  Again, I could be wrong.

---

### Post by Paqman on 2011-10-21
> **cozumel said:**
> But if you do choose the copy option I think that it merely copies all the files without placing them in correct locations or sub-folders.

No it'll copy them in exactly the same structure as they were in the original.

---

### Post by AlphaLexman on 2011-10-21
One of the mistakes I made as a new Linux user was trying to copy MY files to another user, which requires 'root' privileges. In doing so, the files have 'root' ownership and group.

Instead it is much easier (and better IMO) to copy files **from** another user **to** your own home directory. So, login as the other user, and given that you have 'read' permissions, copy the file, and it will be owned by the user that needs the file.

Good Luck!

---

### Post by Swaly on 2011-10-21
I tried all of the codes...  they didn't work.  But I'm beginning to think that this isn't a code problem, but rather the account.

I restarted my computer and tried logging into lewnna again, with gnome classic, hoping it would work because I thought unity was the problem.  But I wasn't able to log in...  I just went to a black space and right back to the login screen.  And I tried going into gnome, and just ubuntu, but the same thing happened.

I didn't delete the account but it seems like it disappeared even though lewnna's still listed under the users....

---

### Post by Paqman on 2011-10-21
> **AlphaLexman said:**
> 
Instead it is much easier (and better IMO) to copy files from another user to your own home directory. So, login as the other user, and given that you have 'read' permissions, copy the file, and it will be owned by the user that needs the file.


Yep, that would work, and you're right it would be easier. The only thing that might trip you up is that it would copy absolutely everything. Other users have no read access to your Private folder, for example.

---

### Post by Paqman on 2011-10-21
> **Swaly said:**
> I tried all of the codes...  they didn't work.  But I'm beginning to think that this isn't a code problem, but rather the account.


Possibly, have you got the home folders encrypted? See if you can navigate to another user's home folder, if you can't view their files then it's probably encrypted.

If that's the case the easiest thing to do is probably copy the files to an external source (USB stick?) then copy them back from the other account.

> I didn't delete the account but it seems like it disappeared even though lewnna's still listed under the users....

Sounds like lewnna's home folder isn't there any more. One of your mv commands probably b0rked it. The account is still on the system, it just doesn't have all the required config files that live in /home.

---

### Post by Swaly on 2011-10-21
> **Paqman said:**
> Possibly, have you got the home folders encrypted? See if you can navigate to another user's home folder, if you can't view their files then it's probably encrypted.

If that's the case the easiest thing to do is probably copy the files to an external source (USB stick?) then copy them back from the other account.

It's encrypted, then.  If it were possible to access lewnna, I think I'd just use my verbatim, then.

> **Paqman said:**
> Sounds like lewnna's home folder isn't there any more. One of your mv commands probably b0rked it. The account is still on the system, it just doesn't have all the required config files that live in /home.

Well... I really have no clue what to do then.  I guess it's back to googling for me.

---

### Post by cozumel on 2011-10-21
@paqman

Is it possible to ALT+F2, run "gksu nautilus" and move or copy the files via gui? (not forgetting to change ownership too)

---

### Post by Paqman on 2011-10-21
> **cozumel said:**
> @paqman

Is it possible to ALT+F2, run "gksu nautilus" and move or copy the files via gui? (not forgetting to change ownership too)

Yes, absolutely.

---

### Post by Swaly on 2011-10-21
Ah!  I just checked my folders.  I must've confused myself thinking nautilus was my normal home after switching between them so many times....

It appears that the folders have been moved!

I'm sorry for confusing anyone here.  I'm not very experienced with computers and I was really confusing myself with all this....

But I noticed that some of the folders' icons have little "x"s on them?  It says I don't have permission to access them...  this part, I really don't get....

---

### Post by old_yarrow on 2011-10-21
Hmm, if you moved or created anything as root you won't be able to access them as another user.  You'll need to change ownership of those files and folders.

Unless you mean the folders are inaccessible *as* root..

---

### Post by cozumel on 2011-10-21
You don't have ownership from your current account as they were owned by your old account

You need to run the chown command to change ownership to gain full access

---

### Post by Paqman on 2011-10-21
> **Swaly said:**
> 
But I noticed that some of the folders' icons have little "x"s on them?  It says I don't have permission to access them...  this part, I really don't get....

On Linux every file and folder has an owner, and access permissions. It's possible to set the permissions so that only the owner has access. Because those files came from another user's home folder, they're owned by that user (or possibly root if root moved them over).

If you take ownership of the file/folder you should have as much access as you need. You can do this through Nautilus, but it's one of those little jobs that's quicker from the command line. Use the command I gave you earlier:
```
sudo chown -R swaly:swaly /home/swaly
```

sudo = use super user privileges
chown = Change owner
-R = Apply to all files within this directory ("recursive")
swaly:swaly = change the owner and group to swaly
/home/swaly = your home folder. You can also use the shorthand ~ to refer to the current user's home folder.

---

### Post by Swaly on 2011-10-21
Aha, sorry for being so vague.  I meant that they were owned by the other account (lewnna).

And I used the command...  it worked like a charm.  Thank you all so much!  I feel so relieved now.  :)  I'm never going to mess with computers again.  Though, I still feel tempted to put CompizConfig Settings Manager for the blame...

---

### Post by AlphaLexman on 2011-10-21
> **old_yarrow said:**
> Hmm, if you moved or created anything as root you won't be able to access them as another user.  You'll need to change ownership of those files and folders.
> **cozumel said:**
> You don't have ownership from your current account as they were owned by your old account
You need to run the chown command to change ownership to gain full access
> **paqman said:**
> Because those files came from another user's home folder, they're owned by that user (or possibly root if root moved them over).
Isn't this what I said in post #6 ??

---

