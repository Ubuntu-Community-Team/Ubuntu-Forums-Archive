---
title: "Can't get the &quot;adb push&quot; command to work"
date: 2012-01-13
forum: Programming Talk
---

### Post by bgryderclock on 2012-01-13
I am trying to develop a simple pygame with Ubuntu Linux 11.10 for my Motorola android phone. I am having trouble getting the "**adb push**" command to work. I get an "failed to copy 'foo.txt' to '/media/MOT': No such file or directory" error message. What am I doing wrong? 

**Here is what I tried so far:**

The phone's SD card is mounted at /media/MOT/ and I am able to ls, create a folder and delete a folder in it. 

```
user@linuxlappy:~$ 
user@linuxlappy:~$ cd /media/MOT/
user@linuxlappy:/media/MOT$ ls
Android  burstlyImageCache  burstlyVideoCache  data  DCIM  download  gstomperdemo  LOST.DIR  slacker  temp.apk
user@linuxlappy:/media/MOT$ mkdir writetest
user@linuxlappy:/media/MOT$ rmdir writetest/
```

the file that I am trying to copy is foo.txt in my /home/user/ directory

```
user@linuxlappy:/media/MOT$ cd /home/user/
user@linuxlappy:~$ ls foo.*
foo.txt  foo.txt~
```


I enabled USB debugging on the phone with: ```
Settings > Applications > Development > USB debugging.
```

I believe I have adb installed correctly, I am able to list the phone with adb devices. 

```
user@linuxlappy:~$ adb devices
List of devices attached 
0910E8201700B017	device
```

when I try to push a simple text file to the SD card I get this error message.

```
user@linuxlappy:~$ adb push foo.txt /media/MOT
failed to copy 'foo.txt' to '/media/MOT': No such file or directory
user@linuxlappy:~$ 
```

---

