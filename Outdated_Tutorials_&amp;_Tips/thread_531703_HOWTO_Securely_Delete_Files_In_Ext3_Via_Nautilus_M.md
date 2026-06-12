---
title: "HOWTO: Securely Delete Files In Ext3 Via Nautilus Menu"
date: 2007-08-21
forum: Outdated Tutorials &amp; Tips
---

### Post by maynoth on 2007-08-21
This adds a menu which securely deletes files by overwriting them 25 times

install nautilus-actions  via synaptic package manager

launch nautilus actions configuration
-->system--->preferences--->nautilus actions configuration


Add

Label = Shred

Path = /usr/bin/find

Parameters = %M -type f -exec shred -f -u -z '{}' \;

Conditions (files and folders) =   Both
Click ok and exit



in terminal type killall nautilus 


Viola!  

A note for ext3 users from the shred manual:
CAUTION:  
       [I]Note  that  shred relies on a very important assumption: that
       the file system overwrites data in place.  This is the traditional  way
       to  do  things, but many modern file system designs do not satisfy this
       assumption.  The following are examples of file systems on which  shred
       is not effective, or is not guaranteed to be effective in all file sys&#8208;
       tem modes:[/I]

In  the  case  of  ext3 file systems, the above disclaimer applies [COLOR="Red"]**only  in  data=journal  mode**[/COLOR],  which  journals  file  data  in addition to just metadata.  In both the data=ordered **(default)** and data=writeback modes, shred works as  usual.

---

### Post by analoog on 2008-06-20
can anyone explain me the ```
%M -type f -exec shred -f -u -z '{}' \;" command?
```
Are the -f and -z srm parameters? what does - u do?
what does %M -type f -exec mean?

---

### Post by maynoth on 2008-07-09
%M: space-separated list of the selected file(s)/folder(s) with their full paths



The " -type f " option for find indicates that the files should be plain, as opposed to links, directories, etc.




-exec shred  starts the shred command


 -f, --force
              change permissions to allow writing if necessary

 -u, --remove
              truncate and remove file after overwriting

 -z, --zero
              add a final overwrite with zeros to hide shredding




'{}' \;  within directory tree

---

### Post by adlibre on 2009-08-17
This is a good, useful tip.  I was freaked out by the idea that I could shred things so easily, so I wanted to add a confirmation box.  Here's how to do it.

First, install zenity (displays GUI dialogs via GTK)
```
sudo apt-get install zenity
```

Next paste the script below into a file called *shred_it.sh* and put it somewhere convenient (e.g. */home/user/bin/shred_it.sh*)

```

#!/bin/bash
# shred_it.sh: shred a selected file in nautilus through nautilus-actions

# quit if no arguments are passed
if [ $# != 1 ]; then
    exit 1
fi
if !  zenity  --question --title "shred"  --text "Permanently delete?\n$1" ; then
    # cancel deleting
    exit 0
else 
    # shred selected file
    # Optional:
    #    - change 7 to 25 for more iterations
    #    - add -z after shred command to hide shredding
    shred -f -u -n 7 "$1"
fi

```

Finally, change the path and parameters in Nautilus Actions Configuration for your shred action:

- Path: /usr/bin/find
- Parameters: %M -type f -exec /home/user/bin/shred_it.sh '{}' \;
(make sure you use a capital M above)

Due to limitations described below, this script is only good for working on single files (not folders or multiple files).  Be sure to select "Appears if selection contains: Only files" under "Conditions" for your action profile.
Lastly, refresh nautilus to see changes:
```

killall nautilus

```

And that's it, no need to [[COLOR="RoyalBlue"]_wait for this "feature"_[/COLOR]]("http://brainstorm.ubuntu.com/idea/1002/") in Ubuntu.

Limitations:
- You can only delete one file at a time.  Extending this script to work with multiple files would not be too difficult.  You would need to check the option "Appears if selection has multiple files or folders" under the Conditions tab for the shred action.  Then you would need to modify the script so that it does not ask for a "confirm delete" each time.  Similarly you could modify the script to delete an entire folder.  I experimented with these versions of the script, but I became worried about passing "bad filenames" to the script and the damage this could possibly do (see below), so I decided to post this simpler version instead.
- Be careful when using scripts like these to work on files with weird/non-standard characters (newlines, tabs, leading dashes, etc).  These can make your script behave in unexpected ways and possibly do major damage.  For more details as to why this is, see this very detailed article (if you're familiar with shell programming):
[[COLOR="RoyalBlue"]_http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html_[/COLOR]]("http://www.dwheeler.com/essays/fixing-unix-linux-filenames.html")
If you modify this script to delete multiple files/directories, think carefully about checking the filenames passed from nautilus-actions to your script and make sure the filenames don't contain non-standard characters before attempting to delete them.  As the article above makes clear, this is more complicated than you may think...

---

### Post by x-shaney-x on 2009-08-17
I find if I use this script I have to do the process twice before anything is deleted.

---

### Post by adlibre on 2009-08-17
Hmm, I'm not sure why you would have to do it twice.  Perhaps Nautilus is just not refreshing -- try pressing F5 after you shred something...

---

### Post by x-shaney-x on 2009-08-18
Not sure what the problem is, maybe I wasn't leaving it long enough to do it's job but it appears to be working ok now.

---

### Post by viking_maniac on 2009-08-28
Do you really need to securely delete files on the Ext3 file system with shred? Ext3 does this by default by overwriting the deleted data area with zeros.

> **Filesystems**
Starting with ext3, Linux filesystems overwrite files with zeros when you delete them, rather than just marking the file as “free space.” Previous Linux filesystems, as well as the Windows filesystems (NTFS, FAT) use the latter method, which is why it is so easy to recover deleted files with software tools freely downloadable on the Internet. This is something to consider when deciding how much time you should spend wiping your drive.
[B]
[http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/](http://www.techthrob.com/2009/03/02/howto-delete-files-permanently-and-securely-in-linux/)[/B]

---

### Post by Andrew.Z on 2009-09-02
Viking Maniac: I don't believe ext3 does that.  It takes way too much disk I/O to wipe the free space.

---

### Post by Face-meats on 2010-02-18
> **jonthansmith said:**
> [Permanently Erase File]("http://www.safedeleter.com")

Dude, did you seriously just link to a Windows program? Wow...You get a star today. :KS

---

### Post by Enigmapond on 2010-02-18
Windoze spam person...BEGONE!

Thank you Maynoth! I was trying to figure a way of adding that to nautilus. Works perfectly!

Cheers!

---

### Post by LintonHanes on 2010-02-18
woosh, it's eraser
-n 7 will do me thanx

---

