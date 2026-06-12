---
title: "asking for script"
date: 2009-02-07
forum: Programming Talk
---

### Post by phaed on 2009-02-07
I know that asking to solve homework problems is prohibited, but is it appropriate to ask if someone can write a small script for you?

Basically I need something that does the following:

When I plug in my digital camera and invoke the script, it copies the images to a specific folder, resizes them to 1600x1200 (with mogrify, I guess) and converts the file names to all lower case (they are originally all .JPG files).

Also, it should keep track of the last file copied and only copy the latest files if older ones are still on the camera.

Sorry, I have no programming experience.

Also, I'm not sure where the source folder is mounted.  I'm getting this:

gphoto2://[usb:001,002]/DCIM/100CANON

But the numbers keep changing.

Destination folder: ~/Photos

Thanks.

---

### Post by unutbu on 2009-02-07
[list]
[*]First, edit ~/.gphoto/settings by adding this line
```

gphoto2=hook-script=/home/USERNAME/bin/gphoto2_hook.sh
```
Change USERNAME to your real username.

[*]Make a ~/bin directory, if you don't have one already
```

mkdir ~/bin
```
[*]Make an empty file called ~/.gphoto/last:
```
touch ~/.gphoto/last
```
This file will hold the name of the last file downloaded. 
If for some reason you wish to re-download a set of pictures, you can edit this file to the name of some previously downloaded pic.

[*]Next, create the file ~/bin/gphoto2_hook.sh
Put this in as its contents:
```

#!/bin/bash
if [ "$ACTION"=download ]; then
    mogrify -resize 1600x1200! "$ARGUMENT"
fi
```
[*]Now make a file called ~/bin/dl_pics.py, and put this in as its contents:
[php]
#!/usr/bin/env python
import os
from subprocess import Popen,PIPE,STDOUT
import re

os.chdir(os.path.join(os.environ['HOME'],'Photos'))
try:
    fh=open(os.path.join(os.environ['HOME'],'.gphoto/last'),'r')
    last_file=fh.read().strip()
except IOError:
    last_file=''
cmd='/usr/bin/gphoto2 --list-files'
proc=Popen(cmd, shell=True, stdout=PIPE, )
list_of_files=proc.communicate()[0].split('\n')

start=1
at_start=False
for line in list_of_files:
    if last_file and re.search(last_file,line):
        at_start=True
        continue
    if at_start:
        try:
            start=line.split()[0].replace(r'#','')
        except IndexError:
            print 'No new files to download'
            exit()
        at_start=False
    if line.startswith(r'#'):
        end=line.split()[0].replace(r'#','')
        end_file=line.split()[1]

cmd=('/usr/bin/gphoto2 --filename %%: --get-file %s-%s'%(start,end))
proc=Popen(cmd, shell=True, stdout=PIPE, )
proc.communicate()

fh=open(os.path.join(os.environ['HOME'],'.gphoto/last'),'w')
fh.write(end_file)
fh.close()
[/php]

[*]Make the two scripts executable:```

chmod +x ~/bin/dl_pics.py ~/bin/gphoto2_hook.sh
```

[*]When you turn on the camera, you may see a pop up window which asks if you want to download pictures using F-Spot. If you see a button which says "Unmount", click it. Otherwise, click "Cancel".

[*]To download pictures into ~/Photos, with lowercase filenames, resized to 1600x1200 and with a memory of the last pic downloaded: just issue this command in the terminal:
```

dl_pics.py
```
[/list]

---

### Post by phaed on 2009-02-07
I keep getting this error message:

> *** Error ***              
An error occurred in the io-library ('Could not lock the device'): Camera is already in use.
*** Error (-60: 'Could not lock the device') ***       

For debugging messages, please use the --debug option.
Debugging messages may help finding a solution to your problem.
If you intend to send any error or debug messages to the gphoto
developer mailing list <gphoto-devel@lists.sourceforge.net>, please run
gphoto2 as follows:

    env LANG=C gphoto2 --debug --debug-logfile=my-logfile.txt --list-files

Please make sure there is sufficient quoting around the arguments.


Also, when I try to enable f-spot-import in Removable Drives and Media, it also gives me an error that it can't lock the device.

---

### Post by unutbu on 2009-02-07
When you turn on the camera, do you get a pop up window which says "You have just inserted a medium with digital photos. Choose what application to launch."

If so, do you see three buttons at the bottom: "Unmount", "Cancel" and "Ok"? If so, click "Unmount". Then try 
```

/usr/bin/gphoto2 --list-files
```

---

### Post by phaed on 2009-02-07
Worked like a charm!

> martin@desktop:~$ /usr/bin/gphoto2 --list-files
There is no file in folder '/'.                                                
There is no file in folder '/store_00010001'.
There is no file in folder '/store_00010001/DCIM'.
There are 161 files in folder '/store_00010001/DCIM/100CANON'.
#1     IMG_0341.JPG                 2196 KB 3264x2448 image/jpeg
#2     IMG_0350.JPG                 2090 KB 3264x2448 image/jpeg
#3     IMG_0351.JPG                 2361 KB 3264x2448 image/jpeg
edit :)
#159   IMG_0514.JPG                 2127 KB 3264x2448 image/jpeg
#160   MVI_0503.AVI                 7676 KB video/x-msvideo
#161   MVI_0504.AVI                11124 KB video/x-msvideo
There is no file in folder '/store_00010001/MISC'.


---

### Post by unutbu on 2009-02-07
I've done some editing to my post #2 in the last few minutes. If you've downloaded the scripts, please download them again.

Let me know how it goes.

---

### Post by phaed on 2009-02-07
Ok, well I just wanted to post that the script as it was gave me this error:

> Traceback (most recent call last):
  File "/home/martin/bin/dl_pics.py", line 7, in <module>
    fh=open(os.path.join(os.environ['HOME'],'.gphoto/last'),'r')
IOError: [Errno 2] No such file or directory: '/home/martin/.gphoto/last'


---

### Post by unutbu on 2009-02-07
Oh yes. Sorry about that. 

Just run 
```

touch ~/.gphoto/last
```

Then try again.

Now I'll re-edit post #2...

---

### Post by phaed on 2009-02-07
Weird.  It keeps giving me an error saying the file isn't there, but it's clearly there and executable.

```
martin@desktop:~/bin$ ./dl_pics.py
execve("$HOME/bin/gphoto2_hook.sh") failed: No such file or directory
Hook script returned error code 1 (0x1)
Traceback (most recent call last):
  File "/home/martin/bin/dl_pics.py", line 30, in <module>
    cmd=('/usr/bin/gphoto2 --filename %%: --get-file %s-%s'%(start,end))
NameError: name 'end' is not defined
martin@desktop:~/bin$ ls
dl_pics.py  gphoto2_hook.sh
```

---

### Post by unutbu on 2009-02-07
In ~/.gphoto/settings, change ```

gphoto2=hook-script=$HOME/bin/gphoto2_hook.sh
```

to
```

gphoto2=hook-script=/home/martin/bin/gphoto2_hook.sh
```
I tried to be clever, but gphoto apparently doesn't expect environment variables in its config file.

And, I made yet another fix to the dl_pics.py script. Please re-download.

---

### Post by phaed on 2009-02-07
Thanks, that worked.  Now I'm getting this:

```
Traceback (most recent call last):
  File "/home/martin/bin/dl_pics.py", line 30, in <module>
    cmd=('/usr/bin/gphoto2 --filename %%: --get-file %s-%s'%(start,end))
NameError: name 'end' is not defined
```

---

### Post by phaed on 2009-02-07
Aha!  It's working!

Awesome.  Thanks a lot! :)

That would have been a lot easier if you were sitting at the computer that you were trying to code for, I'm sure.  I can hear my computer buzzing as it usually does when mogrify is resizing.

---

