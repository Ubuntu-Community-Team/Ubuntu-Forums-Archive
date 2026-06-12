---
title: "Documents open as &quot;read-only&quot; and say my old user has locked them"
date: 2017-12-16
forum: New to Ubuntu
---

### Post by sterator on 2017-12-16
My Ubuntu install had an issue I couldn't fix, so I re-installed ubuntu

I just Moved my backed-up document files from another drive into my Documents folder in my new install of Ubuntu.

When I try to open a spreadsheet, I am told it's read only and that [name of my last user]  has locked it.

Is there a command I can use to instruct the system that all documents are Mine [new user]  ?

I was advised to make new log-in credentials when I reinstalled Ubuntu.

Thank you!


using the terminal, I see a lock file:   .~lock.(name of document#)

Do I need to somehow delete the lock file using the terminal?

---

### Post by yancek on 2017-12-16
> I just Moved my backed-up document files from another drive into my Documents folder in my new install of Ubuntu.


If you did this from the new system logged in as the user on that system you should have rwx access to them.  Is that what you did?  If not, you would probably need to use the chown command to change the ownership of the folders/files.

---

### Post by sterator on 2017-12-16
Here is what I did:

1. I had a functioning Ubuntu which developed a problem where I couldn't boot to the desk top. I had a files backup on another SSD

2. I re-installed Ubuntu, creating a new username and password - NOT the same as the username I had when the files backup was created

3. I Moved the files in my backup to the Documents folder of my new installation

4. Tried to open a spreadsheet containing some Ubuntu-related information I needed, and was told that the file was locked by the older User and that I could read-only or make a copy

5. Got the properties on the Documents folder, made sure permissions for Owner/Access said "create and delete files" then clicked on Change Permissions for Enclosed Files...

I'm not sure if Step 5 was correct or not, but it was the best I could think of to do to tell the system to grant me read/write priveleges over my files.

---

### Post by deadflowr on 2017-12-17
yancek's advice is right, you need to run chown against you files.
Do it for the whole Documents directory:
```
sudo chown username:username -R ~/Documents
```
change username:username to whatever your user's name is.
that should reset the ownership of all files in the Documents directory.
Make sure you change it to the right username.

---

