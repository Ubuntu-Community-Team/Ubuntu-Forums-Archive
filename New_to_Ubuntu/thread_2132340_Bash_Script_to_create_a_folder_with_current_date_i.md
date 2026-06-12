---
title: "Bash Script to create a folder with current date in the name"
date: 2013-04-04
forum: New to Ubuntu
---

### Post by GrouchyGaijin on 2013-04-04
Hi Guys,

I routinely move photos from a digital camera to a folder on a hard drive.
I usually name the destination folder  today's date.  Example: 4-april-2013
I was wondering is it possible to write a script that would make a folder and name it the current date? 

I'd really appreciate any advice.  It seems that should be doable, but I don't know how.

---

### Post by matt_symes on 2013-04-04
Hi

You could use an alias but put it ~/.bashrc

```
matthew-S206:/home/matthew/tmp % alias mkdate='mkdir "$(date)"'
matthew-S206:/home/matthew/tmp % mkdate
matthew-S206:/home/matthew/tmp % ls
Thu Apr  4 19:13:03 BST 2013/
matthew-S206:/home/matthew/tmp % 

```

You can change the format string date returns as well.

Kind regards

---

### Post by steeldriver on 2013-04-04
You can use the mkdir command with the result of the data command, e.g.

```
mkdir $(date '+%d-%b-%Y')
```

```
man date
```

---

### Post by GrouchyGaijin on 2013-04-04
WOW thanks guys!  That was quick.
I actually did a bit of playing around came back to mark the thread as solved.
I came up with a script to do what I wanted.

```
#!/bin/bash
now=$(date +"%m_%d_%Y")
mkdir /media/Elements/"Image Staging"/$now &&
mv *.JPG *.jpg /media/Elements/"Image Staging"/$now
```

Now I can just run the script to dump all of the photos my wife takes into a folder on my external drive.

Thanks again for the really quick and helpful replies.

---

### Post by matt_symes on 2013-04-04
Hi

I am glad we were able to help you :D

BTW: I would probably use a function instead of a script for something that small and keep it in ~/.bashrc.

By doing that (well i keep them in a separate file and source it in ~/.bashrc), i have built up a library of functions and i don't have to think about where i have stored them.

Kind regards

---

### Post by GrouchyGaijin on 2013-04-04
> **matt_symes said:**
> 

BTW: I would probably use a function instead of a script for something that small and keep it in ~/.bashrc.

By doing that (well i keep them in a separate file and source it in ~/.bashrc), i have built up a library of functions and i don't have to think about where i have stored them.

Kind regards
That sounds like a good idea.  Can you explain how to do so?
(I just learned about variables - I'm not sure what how a function is written or where exactly to put one in the ~./bashrc file.  I also don't know what is meant by source the function from another file.)

Thanks again!

---

### Post by matt_symes on 2013-04-04
Hi

Open a terminal and type

```
nano ~/.bashrc
```

At the bottom of the file add this.

```

function mkdate
{
        now=$(date +"%m_%d_%Y");
        mkdir -p /media/Elements/"Image Staging"/$now &&
        mv *.JPG *.jpg /media/Elements/"Image Staging"/$now
}
```

You can source the file but it's easier if you just reboot your PC. This will ensure your ~/.bashrc file is re-read and you will have access to the function mkdate.

At the terminal you should just be able to type

```
mkdate
```

This will call that function, creating the directory with the date (make sure you have permissions to do this on the drive) and then copy the jpeg files in your current directory into the directory just created.

Incedently, i have used mkdir with the -p switch.

Kind regards

---

### Post by GrouchyGaijin on 2013-04-04
Hey, thanks a lot!
What does the -p switch do?

---

### Post by matt_symes on 2013-04-04
Hi

mkdir wil fail if all the directories in the path you are creating do not exist.

The -p switch will ensure it creates all the directories in the path and so not fail.

Take a look

```
matthew-S206:/home/matthew % sudo mkdir /media/test1/test2
[sudo] password for matthew: 
mkdir: cannot create directory `/media/test1/test2': No such file or directory
matthew-S206:/home/matthew % sudo mkdir -p /media/test1/test2
matthew-S206:/home/matthew % ls /media/test1 
test2/
matthew-S206:/home/matthew %
```

Kind regards

---

