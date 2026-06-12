---
title: "File permissions and nautilus &amp; vfat partition"
date: 2008-05-22
forum: New to Ubuntu
---

### Post by NormR2 on 2008-05-22
I have a file with the extension .nss that I've created a mimetype for and created a launcher for in nautilus.  When a file with this extension is on a Win98 partition that is mounted at startup, the .nss file's permissions are: -rwxrwx---. When I try to open the file from nautilus, NOTHING happens. If I go to a Terminal commandline  and do a chmod a+rw on the file, there are no messages and the permissions remain unchanged.
If I RC on the file while it is still on the Win98 partition, chose Open with "Other application"  and chose "Slide show" (my entry) from the list, the program starts as expected.

If I copy the .nss file to a folder in my home, I can chmod and now I see the Open with "Slide show" in nautilus's RC menu and my program starts when I dblclick on the file, as expected.


It seems that I need to set the file's permissions for nautilus to recognize it and present the correct menu. 
How can I do that to the files while they are on a Win98 partition? 
The fstab entry is  ... defaults,utf8,umask=007,gid=46 ...
Is there a value for umask that will change the settings for the folders/files on that partition?

---

### Post by Hossie on 2008-05-22
The FAT32 filesystem can't hold the linux permissions so you cannot chmod anything.

Try uid=yourusername,umask=000,rw

---

### Post by NormR2 on 2008-05-22
I've tried several combinations.
chmod works at least within a login session.

I changed ummask to 020 and Restarted
 ls -l showed -rwxr-xrwx
Then  sudo chmod u-x <file>     changed to --> -rw-r-xrwx  
nautilus didn't work as desired (didn't move off folder)
then sudo chmod a-x <file>     changed to --> -rw-r--rw- 
moved nautilus off and back to folder and now DC worked!

Don't understand why x setting on file prevents nautilus from working??? When its turned off, nautilus will execute my program.
When x is set, nautilus does nothing.

---

