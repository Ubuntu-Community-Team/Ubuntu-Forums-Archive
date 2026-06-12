---
title: "Unable to access Documents, Music, Pictures, Videos from left side bar in ubuntu."
date: 2016-03-22
forum: New to Ubuntu
---

### Post by sivakrishna2 on 2016-03-22
HI,

I am using ubuntu 15.10. i am new user to ubuntu. Without knowing i have deleted short cuts from Home folder for Documents, Pictures and Music. Now when i am trying to open Documents and other folders from left side pane i am getting error: 

Unable to find the requested file. Please check the spelling and try again.
Unhandled error message: Error when getting information for file '/home/sivakrishna/Videos': No such file or directory

I dont know what to do and recover these folders again. Please help me. I have some imp data in it.

Attached error screenshot.

Thanks,
-Siva Krishna K

---

### Post by deadflowr on 2016-03-22
Did you look in your Trash?

Anyway, those weren't shortcuts.
Those were the folders.
The side pane is the shortcuts to those folders.
Not vice versa.

---

### Post by sivakrishna2 on 2016-03-22
its not there at trash

---

### Post by howefield on 2016-03-22
A bit more information as to how you deleted the folders might help.

The folders are easily enough recreated, but deleting the folders has most likely also deleted whatever files you had inside them.

---

### Post by ajgreeny on 2016-03-22
Show us the output of terminal command **ls** which will list all folders (and files) in your home so we can then see if you've really deleted all those folders or just the bookmarks or shortcuts in nautilus.

---

### Post by sandyd on 2016-03-22
As the above posters have mentioned, you have deleted the actual folders from your system not the shortcuts. However, there are still avenues of recovery.

When you delete files, they are not immediately deleted from the system, that is until the space needs to be used.

If you want to recover those files, then first and foremost stop using the drive. The more you use it, the more chance something will be written over.

See the following document on file recovery options that you may use -> [https://help.ubuntu.com/community/DataRecovery#Extract_individual_files_from_recovered_image](https://help.ubuntu.com/community/DataRecovery#Extract_individual_files_from_recovered_image)
Note that in this case, your recovered image is your current HDD. Boot from a LiveCD, mount the current HDD to somewhere and you should be able to use the recovery tools to see if you can get your files back.

Please post back if you need more help.

---

