---
title: "Changing folder permissions on an old hard drive"
date: 2011-12-24
forum: New to Ubuntu
---

### Post by toaojs on 2011-12-24
One of my old laptops running 11.10 crashed the other day and will not boot up.  A friend recommended using a SATA to USB 2.0 enclosure to retrieve my personnel files from it.  I have been successful in connecting the old hard drive to another laptop running 11.04 and viewing all of the folders.  However, I am unable to open or copy the majority of these folders and files.  I receive a pop-up message indicating I do not have the necessary permissions (See below screen-shot).  I have attempted to change the permissions in properties, but again I do not have permission (second screen shot).  Is there a way to change the permissions on the old hard drive via my second laptop?  One forum suggested reinstalling the hard drive in the old laptop to remove all password restrictions, however this time is not an option at this time. 

Any assistance is greatly appreciated.  Thank you.

---

### Post by Paqman on 2011-12-24
The quick and easy way to do this is via terminal. Hit Ctrl-T and type:
```
sudo chown -R username:username /path/to/files
```

Obviously "username" is your own user name, and the path to the drive if it's connected via USB will be something like /media/sdb1.

The command:

sudo = gives the command super user rights
chown = change ownership
-R = "recursively" which makes the command apply to every file and folder within the one your specify

---

### Post by toaojs on 2011-12-24
Apparently the screenshots I included did not make it into the message.  Sorry for any confusion.

---

### Post by toaojs on 2011-12-24
Thank you. It worked perfectly, after I figured out the path.

---

