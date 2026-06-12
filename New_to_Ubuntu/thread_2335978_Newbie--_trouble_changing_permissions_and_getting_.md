---
title: "Newbie-- trouble changing permissions and getting files off old mac HD"
date: 2016-09-03
forum: New to Ubuntu
---

### Post by supadave on 2016-09-03
Hello!

First post, first week with Ubuntu. Love it, and have solved a few first problems with terminal. Here's one I haven't figured out yet, in spite of trying a few things. Please note that I am not super-familiar with coding or terminal, but I have done two or three tasks so far with it.
Thanks in advance for your help.

I have a macbook 2008. Took the old HD out (OS Snow Leopard) and put it in an enclosure, put in an SSD and installed ubuntu 16.04 on it.

Now, I want to get some of my files from my old Mac HD and copy them into my ubuntu (music, movies, documents) so I plug it in and get "you do not have the permissions necessary to view the contents of ____".

Here's what I have tried in terminal (many suggestions from [https://ubuntuforums.org/archive/index.php/t-852144.html):](https://ubuntuforums.org/archive/index.php/t-852144.html):)

1. Gksu Nautilus. Allows me to go into the folder, look at stuff. When I click on the music to open it in Rhythmbox, nothing happens. Can't copy stuff by dragging and dropping

2. cp /home/steveday/Music/ || cp -r /media/steveday/Macintosh HD/Users/stephenday/Music/iTunes/iTunes Media/Music/
and same thing with sudo in front.

Returns:
cp: missing destination file operand after '/home/steveday/Music/'
Try 'cp --help' for more information.
cp: target 'Media/Music/' is not a directory

"Missing destination file operand"-- googled this and quickly was taking to pages which were either too techie for my understanding, or just suggesting I play with the punctuation (which I did).

(I tried without / at the end of the file destinations as well)



3. Booting from the mac drive, going in and changing permissions to read + write.

4. sudo chown steveday.steveday
Returns: Missing operand after steveday.steveday
(also tried this with * at the end)

5. sudo nautilus then right click and copy to. Files just didn't show up.

Thanks again.

Steve

---

### Post by supadave on 2016-09-03
Update:

Tried opening 2 separate sudo nautilus windows, copying a music folder from my mac hd to my current (empty) music folder. The files show up, but they don't work in Rhythmbox, and Rhythmbox doesn't tell me why, nothing happens. Don't work in Tomahawk or in the video player either.

I assume this means the files have been copied but... maybe this is a permissions error?

---

### Post by sotiris2 on 2016-09-04
The command at 2 should be > cp -r from where . From being the Music at your Mac hd and where, where you wanna put them. If /media/steveday/Macintosh HD/Users/stephenday/Music/iTunes/iTunes Media/Music/ is your Mac music folder and you want to put them in your Ubuntu music folder the following should work bar any complications.

> cp -r /media/steveday/Macintosh HD/Users/stephenday/Music/iTunes/iTunes Media/Music/ ~/Music 

---

### Post by Impavidus on 2016-09-04
You also have to escape/quote all whitespace in a path. The command```
cp -r /media/steveday/Macintosh HD/Users/stephenday/Music/iTunes/iTunes Media/Music/
``` is interpreted as: copy the files or directories **/media/steveday/Macintosh** and **HD/Users/stephenday/Music/iTunes/iTunes**, including whatever is inside, to **Media/Music/**, which is clearly not what you want. Better make it```
cp -r "/media/steveday/Macintosh HD/Users/stephenday/Music/iTunes/iTunes Media/Music/" ~/Music
```

---

### Post by mook765 on 2016-09-04
If there are really files or directories which names include a space then you should look here how to handle that in a command-line:
[http://www.hecticgeek.com/2014/02/spaces-file-names-command-line/](http://www.hecticgeek.com/2014/02/spaces-file-names-command-line/)
Copying the folder using two "sudo nautilus-windows will change ownership of folder and files in the folder. you may not be able to access this files as a normal user.
You will have to change ownership of this folder and files.
```
sudo chown -R username: foldername
```
where username is your username and foldername is the name of the folder you want to own.
Avoid using nautilus with root-privileges. Using "sudo nautilus" is the easy way to mess up your system...

---

