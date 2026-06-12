---
title: "Create guest account that can't see filenames/ folder names in main user's home"
date: 2012-03-30
forum: New to Ubuntu
---

### Post by hanzj on 2012-03-30
Hello,
We created a new guest account for people to do basic things like check their email on our computer. We did a quick test and logged on to this guest account. After going into the guest home folder, we went up one level and noticed that the home folder of the main user (us) is also visible. We double clicked the main user's home folder and were able to see the names of the files and folders  and subfolders. How do we hide EVERYTHING but the guest's home folder to the guest?

In other words, we want the guest account to only be able to view and save to guest home folder (where the prepopulated "Documents", Videos, Pictures, Music folders are) and not be able to see our main user's folder and subfolders and files and not be able to see the any other folder and subfolders. 

Thank you.

---

### Post by hanzj on 2012-03-30
While in the main user's account, we right-clicked the main user's home folder, selected "Properties", and chose the permission tab. We then chose "None" for "Others/Folders Access". We went back to the guest account and in the "home" folder container,  we tried to access the main user's home folder. We successfully got a "Permission Denied" message. But we want to take this one step farther. How can we hide the main user's folders AND hide ALL other  folders except the guest user's folder from the guest user?

We do NOT want the guest account to be able to see or access the "File System" location from the Nautilus file explorer.

---

### Post by Bucky Ball on 2012-03-30
Have you tried this:

System>Users and Groups>Choose 'Guest' account>Advanced Settings>User Privileges>Untick 'Administer System'.

Not sure how you would achieve exactly what you're after but could be possible to 'hide' everything but Guest folder ...

Perhaps ... 

Nautilus > Folder-you-want-to-hide > Properties > Permissions > Others > Folder Access: None

... from here:

[http://brainstorm.ubuntu.com/idea/6111/](http://brainstorm.ubuntu.com/idea/6111/)

---

