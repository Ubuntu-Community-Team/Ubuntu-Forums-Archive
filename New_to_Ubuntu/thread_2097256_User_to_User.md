---
title: "User to User"
date: 2012-12-22
forum: New to Ubuntu
---

### Post by Rokefuller on 2012-12-22
[LEFT]How do I copy a document from one user account's documents folder to another user account's documents folder.
[/LEFT]

---

### Post by snowpine on 2012-12-22
To make changes outside of your own home folder, you need to become "superuser" with the "sudo" command. (For more info [see here]("https://help.ubuntu.com/community/RootSudo").)

For example to copy a file called "myfile" from your Documents folder to my Documents folder:

```
sudo cp /home/rokefuller/Documents/myfile /home/snowpine/Documents/
```

(For more info on cp command type 'man cp'.)

**Always triple check your spelling and syntax** before pressing Enter, as incorrect 'sudo' commands can wreck your entire system, not just your own personal documents in /home.

---

### Post by The Cog on 2012-12-22
You could do it as root like this:
```
sudo cp /home/user1/Documents/documentToCopy.odt /home/user2/Documents
sudo chown user2:user2 /home/user2/Documents/documentToCopy.odt
```
or you could have user1 copy it to the /tmp directory where user2 can see and copy it.

---

### Post by Petro Dawg on 2012-12-22
Just make a "Shared Folder" by "Right Clicking on a folder"; select Properties; then Share tab; and then click on the "Share this folder" box.  Anything you put in the folder will be available on all accounts.  (I think)

---

### Post by audiomick on 2012-12-22
+1 the shared folder. If you have had to do this once, chances are you'll have to do it again some time. The folder wont cost you any real space or anything.

The "share this folder" option wont do it, though. That will make the folder available via the network to users of other machines, like a windows share.

What you need to do is right click> properties> permissions and set the permissions to that others can read, write to the folder and documents in the folder. That is the third choice. Clicking on the "apply permissions to files" at the bottom of the tab is also not a bad idea.

---

### Post by snowpine on 2012-12-22
There's a big difference between the shared folder suggestion (which is a good tip) and the OP's question: if you share the document, then other users can edit your original copy, which may not be the desired result. If you copy it, then the other user has his/her own copy that they can edit independently without messing up your original.

Both tools are useful but make sure you choose the right one for the job. :)

---

### Post by audiomick on 2012-12-22
> **snowpine said:**
> ..then other users can edit your original copy, ...

Good point. If I distribute something I don't want changed, I make a PDF of it. In the OP's case, and using a shared folder, it would be a matter of keeping a copy in their own /home/user and putting a copy to be worked on in the shared folder.

---

### Post by Wim Sturkenboom on 2012-12-22
With the default permissions, user A can copy files from user B. If that is not possible, user B has protected the files for a reason.

Although it might be necessary to use root privileges, this is only the case under exceptional circumstances (e.g. user B passed away and had business related files protected). If those circumstances don't exist, the use of root privileges is unethical and abuse of root powers.

---

### Post by snowpine on 2012-12-22
It occurs to me there may be permission issues with files copied from another user; if that's ever the case then you can:

```
sudo chown snowpine /home/snowpine/Documents/myfile
```

Or of course you could also open it read-only and then Save As to make a copy with your user's permissions. :)

---

### Post by Morbius1 on 2012-12-22
> **Petro Dawg said:**
> Just make a "Shared Folder" by "Right Clicking on a folder"; select Properties; then Share tab; and then click on the "Share this folder" box.  Anything you put in the folder will be available on all accounts.  (I think)
Oddly enough that will work even though it's purpose is to create a shared Samba forlder for someone on the network to access not locally. The reason it works is because the very last thing it does is issue a "chmod 777".

Of course the other local user won't be able to do anything with that file other than read it. 

If you copy files between users all the time you might want to do something like this. Let's say the other user is named morbius:

Change permissions on morbius' Document folder:
```
sudo chmod 2775 /home/morbius/Documents
```[COLOR=Blue]*The "2" - the setgid bit - forces all added files to "inherit" the group of the parent folder.*[/COLOR]

Then change the group of the parent folder:
```
sudo chown :plugdev /home/morbius/Documents
```Then make sure everyone is a member of the plugdev group:
```
sudo gpasswd -a morbius plugdev
```[COLOR=Blue]*The first user you create should already be a member of the plugdev group but subsequent users may not.*[/COLOR]

All new files added will be writeable by everyone in the plugdev group.

You can do that to all users Documents folder if you with or you could create a "Shared" folder outside of everyone’s home folder:
```
sudo mkdir /home/Shared
```And do all the chmod'ing and chown'ing to that one.

[COLOR=Blue]**EDIT**[/COLOR]: If you add 1 to the chmod command you can prevent one user from deleteing the file of another:
```
 sudo chmod 3775 /home/morbius/Documents
```[COLOR=Blue]*The "3" is a combination of the " 2- setgid" plus the "1-sticky" bit.*[/COLOR]

---

### Post by Petro Dawg on 2012-12-22
I just tried making the simple "Shared Folder" I suggested earlier and accessing on another account.  It appears to be a pain to get the permissions settled (especially for a guest account). 

To be perfectly honest the easiest way I have found to move files between accounts, operating systems, and other computers, is through a file sharing program such as Ubuntu1 or DropBox.  I dual boot and often throw files between windows and ubuntu using an ubuntu1 share folder.   I am absolutely sure it would work between login accounts as well.

---

### Post by Rokefuller on 2012-12-23
Thank You All for your help.  Since I replaced my broken vista OS with ubuntu I have been operating  with one user profile.  There Are three of us sharing one machine at home.  I recently created a user profile for my daughter and wanted to get her documents into her own account.  Thank You Again!

---

### Post by Rokefuller on 2012-12-23
"or you could have user1 copy it to the /tmp directory where user2 can see and copy it."  from:  The Cog
   
This actually worked very well.  I copied the folder I created for my daughter's documents via the temp directory to her documents.  For newbies like me, this requires no code entry in the terminal and got the job done quickly.  Thank you!

---

### Post by Petro Dawg on 2012-12-23
That's the great thing about Linux, there's always many different ways to do any one thing; one solution will assuredly be easy enough to figure out.

---

