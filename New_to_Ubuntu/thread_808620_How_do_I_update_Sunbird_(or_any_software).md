---
title: "How do I update Sunbird (or any software)?"
date: 2008-05-26
forum: New to Ubuntu
---

### Post by brett123 on 2008-05-26
Hi, new here and all that... :D

Have been searching the net and these forums for a bit and cannot find this answer, although surely it's been asked before. Any help would be appreciated.

Installed Ubuntu (8.04) for the first time a few days ago. So far so good - not ready to cut Windows just yet, but I'm heading in that direction. 

Anyway, I managed to install Sunbird (standalone) from Synaptic Package Manager, however it is an older version than the current 0.8, and I cannot for the life of me figure out how to update this???

I've downloaded the tar.gz file, but have no idea what to do with it? I'm comfortable editing files and executing command lines, but am new to Linux. I'm sure what I'm trying to do is simple, but I just need simple baby instructions.

Please help, anyone, thank you. :D

---

### Post by iansane on 2008-05-26
Sometimes they are hard to understand but there is usually a readme or install text inside with the source. 

For starters, right click on the tar.gz and click extract here.

I'm going to download and install just for fun if I can, to see how it works.

---

### Post by brett123 on 2008-05-26
Thanks for reply. The readme just refers me to the generic website, which isn't a lot of help.

Further info: I do not have Lightning, nor Thunderbird, nor do I use - dare I say it? - Firefox! I just need a (any) standalone calendar. I am used to Sunbird under Windows, which is why this was my first choice.

---

### Post by iansane on 2008-05-26
well I'm stuck. I looked at the url in the readme and then the build link here. [http://www.mozilla.org/projects/calendar/sunbird/build.html](http://www.mozilla.org/projects/calendar/sunbird/build.html)   

I'll see if I can figure it out.

One option for the time being worked. I clicked on the sunbird file in the source folder and it ran and let me import from evolutions calendar.
It also put a sunbird folder in my /home/me/.mozzila folder. Maybe that's all there is to it if it's supposed to be stand alone. Still have to run it from the sunbird file so you could just put the whole directory in the .mozzila folder and make a shortcut/launcher to run it.

Don't know yet if it saves data running it without installing.

---

### Post by iansane on 2008-05-26
Yeah that seems to work.

I put all of the files from the source directory into the new "/home/me/.mozzila/sunbird" directory and then made a new launcher in my applications>internet menu. The command is "/home/me/.mozzila/sunbird/sunbird" and it seems to be working fine.

no icon though and that sucks. Guess you could make one if you know how. I don't mess with themes and icons much.

---

### Post by brett123 on 2008-05-26
Just followed your instructions... but 'sunbird' (without any extension) is a shell script, and as such does nothing when I double click it (or create a launcher to it).

The only two .exe files (sunbird-bin.exe and updater.exe) there also do nothing. I've downloaded it twice in case corrupted.

Hmmm.... :|


EDIT: This is what I downloaded, rightly or wrongly...
sunbird-0.8.en-US.linux-i686.tar.gz

---

### Post by iansane on 2008-05-26
You should not have any .exe files if it is the source for linux. Just to make sure, this is the direct link to the right tar.gz

[http://download.mozilla.org/?product=sunbird-0.8&os=linux&lang=en-US](http://download.mozilla.org/?product=sunbird-0.8&os=linux&lang=en-US)

There is a file named "sunbird" no exe extension.

double click should give you the option to "run in terminal"

otherwise open terminal, cd to the directory, and type ./sunbird

Not sure whats going on if that doesn't work.

---

### Post by brett123 on 2008-05-26
Thanks. That is the same file I downloaded. There are two .exe files in there, but ignoring those even when I double click the sunbird-no-extension, I get a message asking what to do, I say run in terminal, the terminal momentarily blinks open and shut, and I'm left blinking dumbfoundedly at a blank screen. Nothing happens. :|

---

