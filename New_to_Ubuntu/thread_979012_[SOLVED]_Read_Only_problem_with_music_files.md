---
title: "[SOLVED] Read Only problem with music files"
date: 2008-11-11
forum: New to Ubuntu
---

### Post by Dermot Doyle on 2008-11-11
I have all my music on a separate hard drive and it's all in a mess so I want to rearrange it. One folder contains about 30 albums, but I can't cut and paste them out of it. The folder has the padlock 'read only' symbol on it for some reason. Is that what is stopping me from moving the folders inside it and how do I turn it off? Most of the music was put on the hard drive with XP, though I haven't had any trouble with hundreds of other albums so I guess that's not the problem.
Thanks

---

### Post by Pro-reason on 2008-11-11
I'm not sure how the permissions got messed up, but it is easily fixed.

Let's say the folder in question is called “Music”, and it's on your desktop.  This will fix it:

```

sudo chown $USER:$USER -vR ~/Desktop/Music
chmod +rw ~/Desktop/Music

```

---

### Post by Dermot Doyle on 2008-11-12
Hi, thanks for the help, but maybe it wasn't quite idiot proof enough. My seperate hd is called 'LACIE'. Inside it one of the folders is called 'wma' and inside that is one called 'current playlist' which is the locked one. No matter how I type the path in the terminal It can't seem to find it as you can see:

dermot@dell-desktop:~$ sudo chown $USER:$USER -vR ~/computer/media/LACIE/wma/current playlist
chown: cannot access `/home/dermot/computer/media/LACIE/wma/current': No such file or directory
failed to change ownership of `/home/dermot/computer/media/LACIE/wma/current' to dermot:dermot
chown: cannot access `playlist': No such file or directory
failed to change ownership of `playlist' to dermot:dermot
dermot@dell-desktop:~$ 

Any ideas on exactly what I should be typing to find it?
Cheers

---

### Post by Idefix82 on 2008-11-12
It's a problem with white space in the folder name. Try
```
sudo chown $USER:$USER -vR ~/computer/media/LACIE/wma/current\ playlist
```
Alternatively, type as far as current and then hit the tab key for autocompletion.

---

### Post by Dermot Doyle on 2008-11-12
Unfortunately meither of them worked.

dermot@dell-desktop:~$ sudo chown $USER:$USER -vR ~/computer/media/LACIE/wma/current\ playlist
[sudo] password for dermot: 
chown: cannot access `/home/dermot/computer/media/LACIE/wma/current playlist': No such file or directory
failed to change ownership of `/home/dermot/computer/media/LACIE/wma/current playlist' to dermot:dermot
dermot@dell-desktop:~$ sudo chown $USER:$USER -vR ~/computer/media/LACIE/wma/current
chown: cannot access `/home/dermot/computer/media/LACIE/wma/current': No such file or directory
failed to change ownership of `/home/dermot/computer/media/LACIE/wma/current' to dermot:dermot

Anything else I coud try? I put in the path 'computer' because I found the drive there in 'PLaces' and added 'media' because it was called that when I opened the drive to get the folders inside. I think I have tried every possible permutation, but maybe I am doing something very basic wrong.

---

### Post by Idefix82 on 2008-11-12
Sorry, I overlooked it the first time round. Leave out the leading "~/computer" bit. The command should look like
```
sudo chown $USER:$USER -vR /media/LACIE/wma/current\ playlist
```

If you want to be sure, always type the first few characters of the directory name and then hit tab for autocompletion. If it doesn't autocomplete, it means that you need to type in some more characters because there are several possibilities for completion. Eg type
sudo chown $USER:$USER -vR /med** tab **LAC** tab **wm** tab **current** tab**

---

### Post by Dermot Doyle on 2008-11-12
That did it in that I think it found every track in every folder in the drive, but every one said 'Operation not permitted' and ended with 'failed to change ownership...'
By the way, I assume it found everything, but there are 91 albums in there and the terminal didn't list them all. I did notice that scrolling back up the terminal my command had disappeared so I am assuming it only shows the last of a bigger list of failures. Is that right? Whatever I have done before, I have always been able to scroll back to the begining to see how I got there.
One last thing in case it is important, Only the folder 'current playlist' is locked, the folders inside have no symbol. I am assuming it is because the 'current playlist' folder is locked that I can't move the ones inside.
Cheers

---

### Post by Idefix82 on 2008-11-12
Did you also change the permissions, not only the ownership? To do that you can do
```
sudo chmod -cR u+rwX /media/LACIE/wma/current\ playlist
```

You can't see all the output because the terminal stores only a certain number of lines in its memory. You can change this number under Settings. The reason you have always been able to scroll back to your input is that you have never had such a large output. If next time, you don't want to see any output at all, you can leave out the v option in the command, ie in this case you would have done "... chown -R ..." instead of "... chown -vR ..."

---

### Post by Dermot Doyle on 2008-11-12
Hi, another thing. I just tried your second code by cutting and pasting the file path from your last reply, but I got:

dermot@dell-desktop:~$ chmod +rw ~/media/LACIE/wma/current\ playlist
chmod: cannot access `/home/dermot/media/LACIE/wma/current playlist': No such file or directory

Seems funny that it found the folders the first time, but not now.

---

### Post by Idefix82 on 2008-11-12
As I told you before, the directory is called
/media/LACIE/wma/current\ playlist and not ~/media/LACIE/wma/current\ playlist

---

### Post by Dermot Doyle on 2008-11-12
Thanks for your patience and help. It worked and I can move the folders. One small thing, when I ran your second command I got this:

dermot@dell-desktop:~$ chmod +rw/media/LACIE/wma/current\ playlist
chmod: missing operand after `+rw/media/LACIE/wma/current playlist'

Since everything seems to work is this a problem? Otherwise I'll mark the thread solved.
Thanks again.

---

### Post by innoxium on 2008-11-12
You need to place a space between the +rw and the file path. ;)

---

### Post by Dermot Doyle on 2008-11-13
Thanks again.

---

