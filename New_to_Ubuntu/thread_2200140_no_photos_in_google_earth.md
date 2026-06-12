---
title: "no photos in google earth"
date: 2014-01-17
forum: New to Ubuntu
---

### Post by HappyAsHellas on 2014-01-17
I have just installed Ubuntu 12 LTS but cannot open any photos in google earth. Anyone know how to fix this problem?

---

### Post by oldos2er on 2014-01-17
See posts #27 and #28 in this thread: [http://ubuntuforums.org/showthread.php?t=2196304](http://ubuntuforums.org/showthread.php?t=2196304)

---

### Post by HappyAsHellas on 2014-01-18
Tried them but just got some error messages about non existence of path. Tried re installing GE with the latest 64 bit version but still the same results.

---

### Post by oldos2er on 2014-01-18
I'd be glad to help but I'll need a lot more information, starting with all the terminal output from the commands you ran. Please use [code tags]("http://ubuntuforums.org/misc.php?do=bbcode") to make it easier to read.

---

### Post by HappyAsHellas on 2014-01-18
When I copy the update links section I get this:

[email]george@george-W240HU-W250HUQ:/opt/google/earth/free.newlib[/email]s$ ln -s /opt/google/earth/free.newlibs/googleearth /usr/bin/google-earth
ln: failed to create symbolic link `/usr/bin/google-earth': Permission denied
[email]george@george-W240HU-W250HUQ:/opt/google/earth/free.newlib[/email]s$ 

I have absolutely no idea what it means I'm afraid

---

### Post by oldos2er on 2014-01-18
Ok, that's my mistake, I left out "sudo" so it should be ```
sudo ln -s /opt/google/earth/free.newlibs/googleearth /usr/bin/google-earth
```

---

### Post by HappyAsHellas on 2014-01-18
Pasted that into the terminal and got this:

ln: failed to create symbolic link `/usr/bin/google-earth': File exists
george@george-W240HU-W250HUQ:~$

---

### Post by monkeybrain20122 on 2014-01-18
[http://ubuntuforums.org/showthread.php?t=2196304&page=3](http://ubuntuforums.org/showthread.php?t=2196304&page=3)
Follow my post #28, it is simpler and don't need to change symlink.

---

### Post by oldos2er on 2014-01-18
Did you already run ```
sudo mv /usr/bin/google-earth /usr/bin/google-earth.old
``` ?

---

### Post by HappyAsHellas on 2014-01-19
Ann - I tried this but makes no difference

monkeybrain - can't run the second bit of code as I get this message:

tar: /home/george/Downloads/ge7.1.1.1580-0.x86_64-new-qt-libs-debian7-ubuntu12.tar.xz: Cannot open: No such file or directory
tar: Error is not recoverable: exiting now

---

### Post by oldos2er on 2014-01-19
Did you download [https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit](https://docs.google.com/file/d/0B2F__nkihfiNOUJSeEJfWUx0Vk0/edit) ?

---

### Post by HappyAsHellas on 2014-01-19
Yes I have downloaded the correct file and delighted to say it's now working - many thanks.

---

### Post by oldos2er on 2014-01-19
Good news. Could you please mark the thread 'Solved' under Thread Tools at the top of the page? Thanks.

---

