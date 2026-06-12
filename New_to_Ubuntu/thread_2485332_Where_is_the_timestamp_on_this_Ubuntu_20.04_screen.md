---
title: "Where is the timestamp on this Ubuntu 20.04 screenshot?"
date: 2023-03-27
forum: New to Ubuntu
---

### Post by bhubunt on 2023-03-27
Hi,
 
In the attached thumbnail, you will see a screenshot I made this afternoon of a glitch (an unexplained download) happening on an Ubuntu 20.04 OS. 

I wanted to check the timestamp on the screenshot, so I pressed properties.

But when Properties opens, there is no timestamp. 

I made the screenshot at 17:26 (5:26 PM), but there is no record of the time in the properties section of the screenshot.

---

### Post by MAFoElffen on 2023-03-27
Check like this
```

stat </path_to/filename>

```
Example
```

mafoelffen@Mikes-ThinkPad-T520:~/Pictures$ stat ./Screenshot_lunar-lander-05_2022-12-11_01:28:25.png
  File: ./Screenshot_lunar-lander-05_2022-12-11_01:28:25.png
  Size: 16964         Blocks: 40         IO Block: 4096   regular file
Device: 806h/2054d    Inode: 23593893    Links: 1
Access: (0664/-rw-rw-r--)  Uid: ( 1000/mafoelffen)   Gid: ( 1000/mafoelffen)
Access: 2023-03-27 13:55:41.985118605 -0700
Modify: 2022-12-11 01:28:30.945934262 -0800
Change: 2022-12-11 01:28:30.945934262 -0800
 Birth: 2022-12-11 01:28:30.941934224 -0800

```
The metadata of the png saved with the ScreenShot utility does not have the timestamp
```

mafoelffen@Mikes-ThinkPad-T520:~/Pictures$ identify ./Screenshot_lunar-lander-05_2022-12-11_01:28:25.png
./Screenshot_lunar-lander-05_2022-12-11_01:28:25.png [COLOR=#ff0000]PNG 1024x768 1024x768+0+0 8-bit sRGB 16964B 0.000u 0:00.000[/COLOR]

```

---

### Post by bhubunt on 2023-03-28
Thanks very much for the code.

---

### Post by fyfe54 on 2023-03-29
The time is in the file name. 
Screenshot from 2023-03.27         17-26-23
                                   yr.month.day    hr-min-sec

---

### Post by ActionParsnip on 2023-03-30
> **fyfe54 said:**
> The time is in the file name. 
Screenshot from 2023-03.27         17-26-23
                                   yr.month.day    hr-min-sec
+1
It's added to the filename for you :P

---

### Post by TheFu on 2023-04-11
**exiftool** will show lots of data in the header of image files.

---

### Post by bhubunt on 2023-04-13
> **TheFu said:**
> **exiftool** will show lots of data in the header of image files.

Cool!

---

### Post by mIk3_08 on 2023-04-13
If the issue is already been answered and want to mark it as solve.
On how to mark this thread as solve,
Please Click the "Solve thread" link below. Regards and cheers.

---

