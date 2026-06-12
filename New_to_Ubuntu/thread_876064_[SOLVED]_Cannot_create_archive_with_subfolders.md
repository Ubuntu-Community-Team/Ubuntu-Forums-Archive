---
title: "[SOLVED] Cannot create archive with subfolders"
date: 2008-07-31
forum: New to Ubuntu
---

### Post by Paddy Landau on 2008-07-31
I need an archive (a .zip file) of all the files in a folder, including its subfolders.

To do this, I did the following.

[LIST=1]
[*]Open nautilius and navigate to the folder.
[*]Highlight all the files and folders.
[*]Right-click and select "Create Archive..."
[*]Fill in the archive name, select ".zip", and press "Create".
[/LIST]
Well...

This creates the archive, but it only includes the files. The archive does contain the subfolders, but they're empty! The subfolders in the archive don't contain any of the files from the original folders.

I've tried opening the archive (with Archive Manager) and adding the files through "Add Folder", but I'm not managing to make sense of the interface. Nothing I try actually adds the folders. I tend to get an error complaining that the folder doesn't exist; but the folder it quotes is muddled. E.g., one of my folders is called "tmpl". The error message reads, "name not matched: tmpl/l" (I don't have any file called "l").

How do I create an archive (a .zip file) of all the files in a folder *including* its subfolders?

---

### Post by acidsolution on 2008-07-31
try using from commandline 

open the terminal
```
 
    zip -r folder.zip folder

```

this will zip the folder with all its subfolders 
if you dont have zip installed than 
```
 sudo apt-get install zip


```
this might help you :)

---

### Post by Zalbor on 2008-07-31
Very strange, though... I often make .zip files with this method, and all subfolders are zipped correctly.

---

### Post by Paddy Landau on 2008-07-31
> **acidsolution said:**
> try using from commandline
Thank you, that worked.

> **Zalbor said:**
> Very strange, though... I often make .zip files with this method, and all subfolders are zipped correctly.
I wonder if my Archive Manager is corrupted. Tomorrow, I'll uninstall and reinstall through Synaptic Manager. I'll post back whether it works.

---

### Post by cariboo on 2008-07-31
I would check permissions on the files and folders in your archive. There is no need to reinstall a program because it doesn't work the way you expect to, **Remember Linux is not Windows**

Jim

---

### Post by Paddy Landau on 2008-07-31
> **cariboo907 said:**
> I would check permissions on the files and folders in your archive. There is no need to reinstall a program because it doesn't work the way you expect to, **Remember Linux is not Windows**
LOL - Yes, I know. It's not working how Zalbor's works, though... And that error message doesn't make sense, to me at any rate. It's complaining that it cannot stat a file that doesn't exist.

All my files are owned by me and have permissions -rw-r--r--.
All my folders are owned by me and have permissions drwxr-xr-x.

The zip program worked perfectly, first time.

Incidentally, I've found that archiving as .tar, .tar.gz and .tar.bz2 have the same fault.

---

### Post by Paddy Landau on 2008-07-31
Well, I've reinstalled Archive Manager, and (unsurprisingly) it's made no difference.

It really looks like a bug to me. Look at these errors:
```
tar: 445/5: Cannot stat: No such file or directory
tar: ekuvuf/f: Cannot stat: No such file or directory
tar: tmpl/l: Cannot stat: No such file or directory
```With some experimentation on other folder names, I see that it always copies the last letter of the folder and expects there to be a file with that name within the folder.

As an experiment, I deleted all subfolders apart from tmpl, and created a new file called "l" (the last letter of tmpl) within it.

Then, Archive Manager created the archive without displaying an error; but the subfolder tmpl had only the one file "l" in it, and none of the other files.

---

### Post by El Chupacabras on 2008-08-15
I'm having the same issue!. If I try and zip up a source tree, I get a zip file that is 144 KB (It's basically a zip header with a couple of trailing zeros). 

It's really annoying. One thing I have ruled out though, is that it's a system issue.

@Paddy:Try creating a test user account, and try zipping/taring a few folders a few times through it. Make sure to copy some from your regular user account to see if its the permissions. 

I found that it wasn't. I'm beginning to think it may have to do with how Nautilus sends file-roller it's commands. 

I did a quick test, and I think nautilus is doing a:
```
file-roller file:///home/user/testDir/ -a archive.zip
```

When it should be doing:
```
file-roller testDir -a archive
```

Or perhaps file-roller is supposed to respond to a file:// command.
Either way, when I used the file:// method, I got a 144 KB zip, as usual.

---

### Post by El Chupacabras on 2008-08-16
I applied an update today and it seems to be working. Is this still an issue for anyone?

---

### Post by Paddy Landau on 2008-08-17
> **El Chupacabras said:**
> I applied an update today and it seems to be working. Is this still an issue for anyone?
Yes, I still have the same problem.

---

### Post by El Chupacabras on 2008-08-17
Odd. Maybe I changed something... Did you try testing it in a new User account, as I mentioned [here](http://ubuntuforums.org/showpost.php?p=5596964&postcount=8)?
Steps to add a User:
[LIST=1]
[*]Go to the menu bar.
[*]Click Sytem->Administration->Users and Groups
[*]Click the 'Unlock' button. Enter your password.
[*]Click 'Add User'. Enter 'test' for username and make up an easy password. Fill out Real Name
[*]Select 'Unprivileged' from the Profile Drop-down menu.
[*]You may leave the rest of the fields blank. (Click OK)
[*]Click 'Manage Group'. If a group called 'test' is there, click 'properties'. If not, make it. Make sure your test account is in the group and close.
[*] Log out and log in to your new account.
[/LIST]

Create files and subfolders in a folder, and archive it. If it works, something is wrong with your normal account's configuration.

To reset nautilus and file-roller settings, I did:
[LIST=1]
[*][FONT="Monospace"]$ sudo apt-get purge nautilus file-roller[/FONT]
(pay attention to what gets uninstalled here! You should reinstall them in step 4)
[*]
[*][FONT="Monospace"]$ killall nautilus[/FONT]
[*][FONT="Monospace"]$ sudo apt-get install nautilus file-roller[/FONT]
[*][FONT="Monospace"]$ sudo apt-get install nautilus-cd-burnder nautilus-sendto nautilus-share[/FONT] 
(If you had to reinstall more than this, or didn't have these to begin with, replace the list of packages with what was uninstalled in step #1)

[*][FONT="Monospace"]$ nautilus[/FONT]
[*] Reboot, to be safe.
[/LIST]

PS:
To Delete the test account, Log in to your regular account, go back to the Users and Accounts dialog box, select the test account, and delete it. Then make sure the 'test' group is deleted as well.

---

### Post by Paddy Landau on 2008-08-18
Thanks for your suggestion! Create Archive worked perfectly in the test account. That led me on a trial-and-error search, and I found the problem!

The folder in question has a parent folder named "Documents & Utilities".

When I replaced the ampersand, as "Documents and Utilities", then Create Archive worked!

So, obviously, the Create Archive function doesn't work if any of the parent folder names contains an ampersand. (I found that it works fine if any of the children folder or file names has an ampersand; just not a parent directory.)

Whew!

Perhaps we could raise this as a bug? (Do you know how to do that?)

---

### Post by Paddy Landau on 2008-08-18
I've reported this as a bug.

[https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259054](https://bugs.launchpad.net/ubuntu/+source/nautilus/+bug/259054)

---

### Post by El Chupacabras on 2008-08-18
Glad I could help. =]

---

### Post by Paddy Landau on 2008-08-20
The bug has been confirmed as fixed in the next Intrepid release.

---

