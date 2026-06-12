---
title: "[SOLVED] 'Byte of Python' backup script question"
date: 2008-03-22
forum: Programming Talk
---

### Post by BandD on 2008-03-22
I've recently started learning Pyhton (my first programming language actually) using the 'Byte of Python' guide by Swaroop.  I'm currently at the stage where he walks us through writing a backup script and I've run into one small problem.  Here is the code:

```
import os
import time

    # 1. The files and directories to be backed up are specified in a list.
source = ['/home/bandd/Python\ Scripts/']

    # 2. The backup must be stored in a main backup directory
target_dir = '/media/Backup\ Bitch/BandD\ Backup/bandd/Python\ Scripts/'

    # 3. The files are backed up into a zip file
    
    # 4. The name of the zip archive isthe current date and time
target = target_dir + time.strftime('%Y%m%d%H%M%S') + '.zip'

    # 5. We use the zip command (in Unix/Linux) to put the files in a zip archive
zip_command = "zip -vr '%s' %s" % (target, ' '.join(source))

    #Run the back up
if os.system(zip_command) == 0:
    print 'Successful backup to', target
else:
    print 'Backup FAILED!'
```

The target_dir is an external USB HDD, but I get an I/O error in the zip program that says:

```
zip I/O error: No such file or directory

zip error: Could not create output file (/media/Backup\ Bitch/BandD\ Backup/bandd/Python\ Scripts/20080321212955.zip)
Backup FAILED!
```

If I change the target_dir to my home folder, it works fine.  I even copied and pasted the mount point from the drive properties into the script after it failed the first time, with no luck.  Is there something special I have to do to allow this python script access to the external hard drive?  Just curious.


Thanks,

Dustin

---

### Post by Can+~ on 2008-03-22
When working with strings, you need to escape the backslash.

"\" should be "\\".

Also, you should use methods of the os.dir if you are interested in portability, if it's only for you, then go ahead. And try to check if folders/files exist before doing anything, it's always a good practice.

---

### Post by BandD on 2008-03-22
Thanks for the reply Can+~

It helped me see my error.  I'm learning to write bash scripts at the moment as well, and I forgot that Python handles spaces just fine with out the need of an escape.  So I changed the path in the script to ```
/media/Backup Bitch/BandD Backup/bandd/Python Scripts
``` and it worked.  

Also thanks for the tip on os.dir.  Much appreciated!

---

### Post by ghostdog74 on 2008-03-23
you can check out [raw strings.]("http://docs.python.org/ref/strings.html"). Its also in the [tutorial]("http://docs.python.org/tut/node5.html"). please read the tutorial.

---

### Post by AkashS on 2010-05-27
> **Can+~ said:**
> When working with strings, you need to escape the backslash.

"\" should be "\\".

Also, you should use methods of the os.dir if you are interested in portability, if it's only for you, then go ahead. And try to check if folders/files exist before doing anything, it's always a good practice.

Hi,

I also using the same but the prob I am getting is that when zip command zip files, it takes full path like /home/user/Desktop/Backup/. 

I also tried to use gllo.glob but that also just include files form main folder and subfolders but no file from subfolders.

Similarly I used os.walk(source) but in that one also it takes all files form main folders and subfolders and then write to .zip file without directory structure. 

Can you please suggest if I can use zip command to create actual Folder path only or glob.glob so that it include subfolder's files also or os.walk for real directory structure. Thanks in advance.

Regards,
Akash...

---

