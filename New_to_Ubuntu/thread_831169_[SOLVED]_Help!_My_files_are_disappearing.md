---
title: "[SOLVED] Help! My files are disappearing?"
date: 2008-06-16
forum: New to Ubuntu
---

### Post by hman469 on 2008-06-16
I was transferring an .avi file from a thumb drive to my 'videos' folder and both folders went dark and froze up:confused:. After 15 minutes I finally did a force quit on it and now every time I go to the video folder it freezes up and shows fewer files in the folder. Also I am a noob so please be explicit with any answers and help, Thanks

---

### Post by fatality_uk on 2008-06-16
If you can use the terminal (Application->Termninal) and navigate to that folder by using this command:
> cd /home/{USER}/Videos
Where user is your user name and then type the command
> ls
Does this bring up a list of files?

---

### Post by hman469 on 2008-06-16
yes the files show up there but some are in green while some are purple and others are blue

---

### Post by fatality_uk on 2008-06-16
That's good. They are different colours denoting the file types.
Can you see the missing files in that list?

---

### Post by hman469 on 2008-06-16
yes everything is showing in the terminal that should be there.

---

### Post by fatality_uk on 2008-06-16
Ok, now try opening a file that isn't visibile through Nautilus by using mplayer

mplayer -fs the_name_of_your_file.avi

---

### Post by tjwoosta on 2008-06-16
try to move the file to a different location, then try to access it through nautilus again

this is the terminal command to move the file

first navigate to the directory the file is in (like fatality said)

then 
```

sudo mv filename /new/directory/filename

```
(where filename is the file name and /new/directory is the directory you want to move it to)

---

### Post by hman469 on 2008-06-16
the files and folders seem to open with everything except nautilus. whether thru terminal or burning to a disk with the gui via brasero.:confused:

---

### Post by hman469 on 2008-06-16
> **tjwoosta said:**
> try to move the file to a different location, then try to access it through nautilus again

this is the terminal command to move the file

first navigate to the directory the file is in (like fatality said)

then 
```

sudo mv filename /new/directory/filename

```
(where filename is the file name and /new/directory is the directory you want to move it to)


Maybe my syntax is off but this is what I tried and got.

hman@hman-ubuntu:~$ cd /home/hman/Videos
hman@hman-ubuntu:~/Videos$ sudo mv God father part I.avi /home/hman
[sudo] password for hman: 
mv: cannot stat `God': No such file or directory
mv: cannot stat `father': No such file or directory
mv: cannot stat `part': No such file or directory
mv: cannot stat `I.avi': No such file or directory
hman@hman-ubuntu:~/Videos$

---

### Post by fatality_uk on 2008-06-16
Enter this into the terminal

cd /home/hman/Videos
sudo mv God father part I.avi /home/hman/God_father_part_I.avi

---

### Post by RomeReactor on 2008-06-16
Hi. When manipulating files in the terminal that have spaces in their names, try adding quotes to the filename:
```
mv "God father part I.avi" /home/hman
```

Also, you shouldn't need to use sudo if the files are in your home folder.

You could also make a new folder and move them all at once:
```
cd /home/hman
```
```
mkdir "New Videos"
```
```
mv /home/hman/Videos/*.* /home/hman/"New Videos"
```

---

### Post by hman469 on 2008-06-16
> **fatality_uk said:**
> Enter this into the terminal

cd /home/hman/Videos
sudo mv God father part I.avi /home/hman/God_father_part_I.avi

this is what happened. 

hman@hman-ubuntu:~$ cd /home/hman/Videos
hman@hman-ubuntu:~/Videos$ sudo mv God father part I.avi /home/hman/God_father_part_I.avi
[sudo] password for hman: 
mv: target `/home/hman/God_father_part_I.avi' is not a directory
hman@hman-ubuntu:~/Videos$

---

### Post by RomeReactor on 2008-06-16
Sorry; I also made that mistake. That's because we specified the filename at the end of the command, when the last part should only be the destination directory; try it like this:
```
mv "God father part I.avi" /home/hman
```

Or try to move them all at once to a new folder (see my previous post).

---

### Post by hman469 on 2008-06-16
> **RomeReactor said:**
> Hi. When manipulating files in the terminal that have spaces in their names, try adding quotes to the filename:
```
mv "God father part I.avi" /home/hman
```

Also, you shouldn't need to use sudo if the files are in your home folder.

You could also make a new folder and move them all at once:
```
cd /home/hman
```
```
mkdir "New Videos"
```
```
mv /home/hman/Videos/*.* /home/hman/"New Videos"
```

Thanks! This worked and now I can access the original 'Videos' folder and the remaining folders inside of it. Is it safe to start using the original folder again or what should I do? Thanks again!:)

hman@hman-ubuntu:~$ cd /home/hman/Videos
hman@hman-ubuntu:~/Videos$ mv "God father part I.avi" /home/hman
hman@hman-ubuntu:~/Videos$ cd /home/hman
hman@hman-ubuntu:~$ mkdir "New Videos"
hman@hman-ubuntu:~$ mv /home/hman/Videos/*.* /home/hman/"New Videos"
hman@hman-ubuntu:~$

---

### Post by hman469 on 2008-06-16
Now my 'pictures folder is doing the same thing.:confused:. At least I know how to fix it now.

---

### Post by RomeReactor on 2008-06-16
> **hman469 said:**
> Now my 'pictures folder is doing the same thing.:confused:. At least I know how to fix it now.

That's an *odd* behavior; have you done anything in your home folder recently involving premissions? Try logging out and back in, or rebooting.

---

### Post by hman469 on 2008-06-16
> **RomeReactor said:**
> That's an *odd* behavior; have you done anything in your home folder recently involving premissions? Try logging out and back in, or rebooting.


I was letting it update while burning a data dvd, when I was moving the file that started it all. But I have not done anything to the pictures folder at all. When it initially froze up on me I rebooted thinking that the updates needed to reboot to start working right, but I have not rebooted since.

---

### Post by RomeReactor on 2008-06-16
Try logging out or rebooting now and see if that makes a difference.

Also, if you pictures folder is the stock one (the one that's already in your home folder from the start) try changing its permissions:
```
sudo chmod -R 777 /home/hman/Pictures
```

---

### Post by hman469 on 2008-06-17
> **RomeReactor said:**
> Try logging out or rebooting now and see if that makes a difference.

Also, if you pictures folder is the stock one (the one that's already in your home folder from the start) try changing its permissions:
```
sudo chmod -R 777 /home/hman/Pictures
```


That made no difference so I moved everything into new folders and deleted the old ones, restarted the computer, then recreated the original folders and everything is back to normal.

---

### Post by hman469 on 2008-06-17
I want to thank fatality_uk, tjwoosta, and RomeReactor, for their coutious and prompt help with my problem. Everything seems to be back to normal now.

Thanks again!

---

### Post by fatality_uk on 2008-06-17
Glad to of been part of the solution. :D
Can you please mark this thread as solved if you are happy that you have the answer.
Cheers

---

### Post by hman469 on 2008-06-17
It's already been marked. Thanks again.

---

