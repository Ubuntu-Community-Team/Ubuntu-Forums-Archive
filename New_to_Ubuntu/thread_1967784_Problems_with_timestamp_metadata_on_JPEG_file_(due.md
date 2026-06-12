---
title: "Problems with timestamp metadata on JPEG file (due to daylight saving hour?)"
date: 2012-04-28
forum: New to Ubuntu
---

### Post by EssexEagle on 2012-04-28
I'm having trouble understanding how Ubuntu deals with timestamps in metadata.  As an example I've just taken a photo with my camera at 18:05 (UTC+1).  On the camera itself, it shows the correct time when I view the picture on the screen.

When I copy the picture to my computer, Ubuntu adds one hour to the timestamp, thus:
```
$ ls -l P4280277.JPG
-rwxr-xr-x 1 *user* *group* 451097 2012-04-28 19:05 P4280277.JPG
```

Why is this?  Is Ubuntu trying to be clever, noting that the picture was taken during British Summer Time and assuming that the metadata actually refers to UTC?  That's the only source of the one-hour time difference I can think of.  Or is there some other reason?

To confirm the metadata has not somehow been changed when copying the image onto the computer, I used the following Python code:
```
import PIL.Image, PIL.ExifTags

# open file
f = PIL.Image.open('P4280277.JPG')

# get metadata as dictionary
info_raw = f._getexif()

# find 'DateTime' tag
for tag in info_raw.keys():
    tag_decoded = PIL.ExifTags.TAGS.get(tag, tag)
    if tag_decoded == 'DateTime':
        timestamp = info_raw[tag]
        break
```

This gives timestamp = '2012:04:28 18:05:01', so the metadata on the actual file is still correct.

Interestingly, if I run
```
$ touch -t 201204281805.01 P4280277.JPG
```
then Ubuntu no longer adds one hour onto the timestamp!
```
$ ls -l P4280277.JPG
-rwxr-xr-x 1 *user* *group* 451097 2012-04-28 18:05 P4280277.JPG
```

Can someone explain what's happening here?

---

### Post by Hadaka on 2012-04-28
Just out of curiosity...check the selected time from "system settings"
manual...or automatic?
also the  -t option for touch sets the time for the file
man touch        quantum leap??:P

---

### Post by tjwilli on 2012-04-28
Your 'ls -l' time is the modification/creation date of the file itself. Your metadata is the time the picture was taken. If you copy the file to another file w/o preserving the file time, you'll probably see that the file time changes, but the metadata inside the file should stay the same.

Another explanation could also be that the metadata stores the time in UTC, but the file time is displayed in local time.

---

### Post by tjwilli on 2012-04-28
> **tjwilli said:**
> 

Another explanation could also be that the metadata stores the time in UTC, but the file time is displayed in local time.

This always causes confusion for me when looking at data we collect at work. If I save a separate file with a datetime stamp, and I saved the timestamp in a local time format, I have to remember if the data was collected during Daylight Savings Time (EDT) or Standard Time (EST). I'm learning to now always save in UTC, and optionally local time, but definitely UTC!

---

### Post by EssexEagle on 2012-04-29
> **Hadaka said:**
> Just out of curiosity...check the selected time from "system settings"
manual...or automatic?

"Set date and time automatically" is not ticked.

> **tjwilli said:**
> Your 'ls -l' time is the modification/creation date of the file itself. Your metadata is the time the picture was taken. If you copy the file to another file w/o preserving the file time, you'll probably see that the file time changes, but the metadata inside the file should stay the same.

Another explanation could also be that the metadata stores the time in UTC, but the file time is displayed in local time.

I've tried copying the file and you're right, the metadata doesn't change.  I thought even the modification time would be saved as part of the file itself, but evidently not.  So Linux must have some kind of database which contains the last-modified time of every file?

I still don't understand why 'ls -l' should add one hour to the time originally, but not after I've run 'touch -t'.  The reason I'm doing this is because I'm building a script to edit image files, but I want to preserve the original time on the file because I often sort my photos in chronological order.  But if I have two images taken less than an hour apart, and I edit and 'touch -t' the second one but not the first, they end up in the wrong order... :-(

---

### Post by tjwilli on 2012-04-29
The modification date is part of the file's metadata as a file in the OS, but is not the metadata associated with the JPEG image you got from the PIL module. That metadata actually resides in the file's data. 

If you use os.stat(<filename>), where <filename> is the filename the file, you have access to the data that 'ls -l' is showing.

> $ ls -l samplefile 
-rw-rw-r-- 1 tim tim 29 Apr 29 12:40 samplefile


In python:

```

>>> st=os.stat('samplefile')
>>> st
posix.stat_result(st_mode=33204, st_ino=4195263, st_dev=2050L, st_nlink=1, st_uid=1000, st_gid=1000, st_size=29, st_atime=1335717649, st_mtime=1335717657, st_ctime=1335717657)
>>> import datetime
>>> st.st_mtime
>>> datetime.datetime.fromtimestamp(st.st_mtime)
datetime.datetime(2012, 4, 29, 12, 40, 57, 766674)
>>> datetime.datetime.fromtimestamp(st.st_mtime).isoformat(' ')
'2012-04-29 12:40:57.766674'
>>> datetime.datetime.utcfromtimestamp(st.st_mtime).isoformat(' ')
'2012-04-29 16:40:57.766674'


```

---

