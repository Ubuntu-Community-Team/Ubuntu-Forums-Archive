---
title: "[SOLVED] Moving a range of files in a folder with mv command?"
date: 2008-11-20
forum: New to Ubuntu
---

### Post by woodybrando on 2008-11-20
Hi All,
I'm trying to move the first 9999 pictures in one of my folders to a new folder. Nautilus being so slow, I want to do it in terminal. But i don't know how to move more the one file with the mv commmand. can anyone help? thanks, jayson

---

### Post by bswilson on 2008-11-20
I wish I had a magic answer for you.  Here's [a good resource]("http://www.howtogeek.com/howto/ubuntu/shell-geek-rename-multiple-files-at-once/") here that might help you.

---

### Post by rbprogrammer on 2008-11-20
I would agree!  Something like what you want to do is perfect for a shell script to handle.  Unfortunately I don't have to much experience to really get in depth with this idea, but I know shell scripting can (and would probably be the best option to) do this. 

However, have you thought about just moving the folder, or at least copying the folder to a new location and then remove the unwanted files?  But that would all depend on how many "unwanted" files are in that folder.

---

### Post by porchrat on 2008-11-20
What are the file extensions of the pictures?  If you could give a few examples of the names it would make it easier.  For example if they are all .jpg files then just do a "mv *.jpg"

---

### Post by aeiah on 2008-11-20
to move all files in a folder to another folder that are older than a certain number of days (64 in this example):

(use the terminal to navigate to the directory your photos are in first, else you'll move the entire contents of your home directory. be careful).
```

find -mtime 64 -execdir mv {} ~/yournewlocation/ \;
```

to find the first 9999 files (alphabetically speaking) and move them you'll have to wait until i mess around or until someone else chimes in :p

---

### Post by aeiah on 2008-11-20
ok this will move the first 9999 files alphabetically speaking.

```
find . | head -10000 | xargs mv -t /home/username/destination/

```

not the nicest way to do it. again, make sure you create the destination directory first, and make sure you've navigated to the directory you want too.

---

### Post by woodybrando on 2008-12-16
Hey guys, thanks for all the replies. Sorry about my late response, I had posted this with three hours till show time (those 9999 images were an animation I'd made for a friends play) and I forgot I'd posted this question till now. I did make showtime by the way. What I ended up doing was installing thunar file manager. that same folder full of 9999 images opened in just seconds in thunar. SO then I just moved the folder in the thunar gui. But I'm trying to ween myself off gui's so I'll check out all of your suggestions soon. It's nice to know there's such a great community of folks willing to help here. I just dove head first into linux from os X. It's been love hate love hate but the more I learn about linux the less I like os x and their pay to play philosophy. 
thanks again,
jayson
[www.oldchildprojects.com](www.oldchildprojects.com)

---

