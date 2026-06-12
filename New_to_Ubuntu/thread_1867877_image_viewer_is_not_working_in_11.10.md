---
title: "image viewer is not working in 11.10"
date: 2011-10-23
forum: New to Ubuntu
---

### Post by beew on 2011-10-23
At some point (after a few updates) the image viewer in Ubuntu11.10 seems to have stopped working. Right click any jpg or png file nothing happens. Try opening them with the context menu, the same thing. I tried to open them in the terminal with the command ```
eog path_to_image_file 
``` and it just timed out.

Thanks for any advice in advance.

---

### Post by Pragu on 2011-10-23
i have the exact same issue. imageviewer won't boot from the ui, nor the command line, nor the root command line. any help would be appreciated.

---

### Post by hakermania on 2011-10-23
I would suggest trying running with gdb to see what's wrong unless there aren't any error messages in the output...
In my case (where eog works OK in 11.10):
```

alex@MaD-pc:~$ gdb --args eog /home/alex/Pictures/face.jpg 
GNU gdb (Ubuntu/Linaro 7.3-0ubuntu2) 7.3-2011.08
Copyright (C) 2011 Free Software Foundation, Inc.
License GPLv3+: GNU GPL version 3 or later <http://gnu.org/licenses/gpl.html>
This is free software: you are free to change and redistribute it.
There is NO WARRANTY, to the extent permitted by law.  Type "show copying"
and "show warranty" for details.
This GDB was configured as "i686-linux-gnu".
For bug reporting instructions, please see:
<http://bugs.launchpad.net/gdb-linaro/>...
Reading symbols from /usr/bin/eog...(no debugging symbols found)...done.
(gdb) run
Starting program: /usr/bin/eog /home/alex/Pictures/face.jpg
[Thread debugging using libthread_db enabled]
[New Thread 0xb7d7ab70 (LWP 6048)]
[New Thread 0xb755bb70 (LWP 6049)]
[New Thread 0xb6bffb70 (LWP 6050)]
[New Thread 0xb1dcfb70 (LWP 6051)]
[Thread 0xb1dcfb70 (LWP 6051) exited]
[Thread 0xb6bffb70 (LWP 6050) exited]
[Thread 0xb755bb70 (LWP 6049) exited]
[Thread 0xb7d7ab70 (LWP 6048) exited]
[Inferior 1 (process 6045) exited normally]
(gdb) quit
alex@MaD-pc:~$

```You could also submit a bug @ launchpad.

---

### Post by grahammechanical on 2011-10-23
First, is image viewer still installed?

Second, when I installed 11.10 alpha I tired my usual habit of double clicking an image to get it to load into Image Viewer but this did not happen.

I had to right click the image and select Open With and then select Other Application (Image Viewer was not on the Open With menu list) then choose Image Viewer from the list offered.

Now a double click on any image loads the image in Image Viewer. Doing this gives you a Open With Image Viewer option at the top of the right click menu, which in turn makes it the first choice application to load the image from a double click.

Regards.

---

### Post by beew on 2011-10-23
> **grahammechanical said:**
> First, is image viewer still installed?

Second, when I installed 11.10 alpha I tired my usual habit of double clicking an image to get it to load into Image Viewer but this did not happen.

I had to right click the image and select Open With and then select Other Application (Image Viewer was not on the Open With menu list) then choose Image Viewer from the list offered.

Now a double click on any image loads the image in Image Viewer. Doing this gives you a Open With Image Viewer option at the top of the right click menu, which in turn makes it the first choice application to load the image from a double click.

Regards.

I know that, it didn't work. See my original post: Tried double click, single click, open with and command line. In fact if you go to the dash and click the icon for the image viewer nothing would happen.

---

### Post by TheGosu on 2011-10-27
Not working to me too

---

### Post by Pest1lence on 2011-10-29
> **TheGosu said:**
> Not working to me too

same here wondering what I did wrong

---

### Post by castironpants on 2011-11-01
I had to switch to Mirage, hopefully temporarily.

---

### Post by vasa1 on 2011-11-01
I can double-click on a png file and it opens with Image Viewer 3.2.1. I haven't done anything special. Just accepted all updates offered.

And a right-click on a png file has Image Viewer as the default.

---

### Post by koolkatkiwi on 2011-11-20
It's not working for me either. Can't open it from the Launcher panel, or right click context menu on a .jpg. I used to use this program in previous Ubuntu versions, but now I guess I'll look for something else. I tried using Shotwell, but can't seem to get to a file tree to look for files. It just offers me its own "library" when I just want to look in the file folder as normal.

---

### Post by beew on 2011-11-20
Reinstalled Ubuntu 11.10 and it works now, wt???

---

### Post by Bucic on 2012-04-17
It happenned to me to, for the first time ever!

---

### Post by Ninchica on 2012-04-19
I have the same problem.

After installing gimp 2.8 image viewer and shotwell stop working.
I clicked on icon and nothing happens.

I have installed again shotwell and it works, but I don't know what to do about image viewer. It is installed, but it isn't working.
and I have used to image viewer.

---

### Post by MrWylbur on 2012-04-19
> **Ninchica said:**
> I have the same problem.

After installing gimp 2.8 image viewer and shotwell stop working.
I clicked on icon and nothing happens.

I have installed again shotwell and it works, but I don't know what to do about image viewer. It is installed, but it isn't working.
and I have used to image viewer.

Same situation for me.  Got Shotwell back up and running, but no imageviewer.

---

