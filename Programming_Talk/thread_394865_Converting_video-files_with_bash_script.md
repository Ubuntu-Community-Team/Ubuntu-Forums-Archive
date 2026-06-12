---
title: "Converting video-files with bash script"
date: 2007-03-27
forum: Programming Talk
---

### Post by rpw on 2007-03-27
Hallo,

I know how to convert video-files with ffmpeg, for example flash-files to mpeg-files. Just a single command "ffmpeg -i filename.flv -t ouptputformat fileiname.mpg".

I would like to convert all video files (flv, mov, avi, wmv, ...) in the actual directory to mpeg-files using the original name and changing te extention from .extention to .mpg. But there should be a check in the script, so that only files are touched, that do not have the extention .mpg or .mpeg so that the script does not ask what to do because a mpg-file allready exists.

It should look like this:

filename1.flv -> filename1.mpg
filename2.flv -> filename2.mpg
filename3.flv -> filename3.mpg
...

Too bad I don't have any knowledge of programing/scripting at all. Maybe someone could help a little bit.

Regards,

rpw

---

### Post by Mr. C. on 2007-03-27
I recently helped someone with something like this:

[http://ubuntuforums.org/showthread.php?t=389780&highlight=mrc+mencoder](http://ubuntuforums.org/showthread.php?t=389780&highlight=mrc+mencoder)

MrC

---

### Post by rpw on 2007-03-27
Thank's a lot, it works!

Regards,

rpw

---

