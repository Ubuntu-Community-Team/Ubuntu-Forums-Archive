---
title: "script templates"
date: 2012-05-22
forum: New to Ubuntu
---

### Post by iceman30ad on 2012-05-22
ok  i am trying for an automated script  using djb's daemontools as its backbone

```
#!/bin/bash
find /dir1/ -iname ".avi" -exec mv '{}' /target/dir/

```as you see i have the idea on how to find a given file format  but i would  like  to be able to  grab the rest of a file type and send it for automatic conversion

aka  move  the avi's out and send the rest of the video(wma mkv or what else you have) files to get converted to avi and deposited with the rest. 

ill be doing the same thing with her audio files i am tired of doing it it every week  any help will be much appreated

---

### Post by papibe on 2012-05-23
Hi iceman30ad

I would use a command like this:
```
find  /dir1/  -iname '**[COLOR="Red"]*[/COLOR]**.avi' -exec mv -vb '{}' /target/dir/
```
(note the *)

I added the -v to move so you can see what's going on. Also, the -b option would take care of repeated filenames (just once).

Does that help?

I don't understand the other part? Do you need to move all video files?

Regards.

---

### Post by iceman30ad on 2012-05-25
yes and no i want to convert them to avi then delete the original

and im wanting this to be running in the back ground not manually

---

### Post by papibe on 2012-05-26
For task automation, I would recommend taking a look at crontab. Here's a good [tutorial]("https://help.ubuntu.com/community/CronHowto").

As for scripts for converting video, search the forums for the term 'ffmpeg'. There are several examples spread around.

Just some thoughts.
Regards.

---

