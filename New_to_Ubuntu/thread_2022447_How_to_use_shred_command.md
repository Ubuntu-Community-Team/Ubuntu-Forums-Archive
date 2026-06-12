---
title: "How to use shred command?"
date: 2012-07-11
forum: New to Ubuntu
---

### Post by jrc7z on 2012-07-11
I do not understand what the shred command does, as in its specific text.  I understand that it does a secure overwrite and doesn't just forget the pointer.  How would I, for instance, shred my trash bin?

---

### Post by Redblade20XX on 2012-07-11
Here is a good web page that describes what you want to do.
[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

Instead of using shred, I would recommend the secure-delete tools.
The same link describes the secure-delete tools.

```
sudo apt-get update
``````
sudo apt-get install secure-delete
```-Red

---

### Post by jrc7z on 2012-07-26
I don't really understand what he goes on about.  -f, etc.  I've not been able to find any documentation on how the filesystem is set up for ubuntu so reading all of that is pretty much jarbled information for me.  Where is a decent how-to?

edit:  I have installed secure-delete tools but it is all terminal commands.  I do not know how to use terminal and do not know how to "aim" the commands at my trash bin, hence why I want to use a way to set it up to secure delete all of the contents of my trash bin when I empty the trash.

---

### Post by uRock on 2012-07-26
Not sure about shredding within the trash bin. I usually cd to the directory with the files I want to delete, then use the shred command. After that, I simply open the file manager and send the files to the trash bin. The only part of the file that is left after the shred is the file name. Use the following command to see the particulars for the shred command.```
man shred
```

---

### Post by jrc7z on 2012-07-26
I do not know what cd to the directory means.

---

### Post by uRock on 2012-07-26
> **jrc7z said:**
> I do not know what cd to the directory means.

**cd** is the command used to change directories. Let's say you had a file named picture.jpg on your desktop and you wanted to shred it. First you would need to get the terminal into the proper folder(directory) with the **cd** command, which would look like this,```
cd ~/Desktop
```Then you would run the **shred** command, which by default writes ov the file with random bits 3 times. I use the **-v** argument with the command so the terminal will give me output as it is working and the **-u** argument which tells the terminal to rename, then delete the file. To read more about the arguments open a terminal and use the command I posted earlier. The following is an example of what I have discussed,```
urock@uRock-Desktop:~$ [COLOR="Purple"]cd ~/Desktop[/COLOR]
urock@uRock-Desktop:~/Desktop$ [COLOR="Purple"]shred -vu picture.jpg[/COLOR]
[COLOR="Red"]shred: picture.jpg: pass 1/3 (random)...
shred: picture.jpg: pass 2/3 (random)...
shred: picture.jpg: pass 3/3 (random)...
shred: picture.jpg: removing
shred: picture.jpg: renamed to 00000000000
shred: 00000000000: renamed to 0000000000
shred: 0000000000: renamed to 000000000
shred: 000000000: renamed to 00000000
shred: 00000000: renamed to 0000000
shred: 0000000: renamed to 000000
shred: 000000: renamed to 00000
shred: 00000: renamed to 0000
shred: 0000: renamed to 000
shred: 000: renamed to 00
shred: 00: renamed to 0
shred: picture.jpg: removed[/COLOR]
urock@uRock-Desktop:~/Desktop$ [COLOR="Purple"]cd ..[/COLOR]
urock@uRock-Desktop:~$ 
```The **cd ..** command wi take the terminal to the previous directory.

---

### Post by Bufeu on 2012-07-27
> **Redblade20XX said:**
> Here is a good web page that describes what you want to do.
[http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html](http://www.ubuntugeek.com/tools-to-delete-files-securely-in-ubuntu-linux.html)

Instead of using shred, I would recommend the secure-delete tools.
The same link describes the secure-delete tools.

```
sudo apt-get update
``````
sudo apt-get install secure-delete
```-RedThe link says "Even if you overwrite a file 10+ times, it can still be recovered". That's is not true. Once overwritten, always overwritten.

---

