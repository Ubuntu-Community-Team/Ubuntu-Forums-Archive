---
title: "Installing .sh files"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by yoramdavid on 2008-11-24
Hi,

I am trying to install a sh. file, but when I double click on it, it asks what I want to do with it, I select execute and it does nothing.
From terminal I typed the following: sh /home/kurso/install.sh

I got plenty of permission denied errors, so I typed the following:

sudo sh /home/kurso/install.sh
After enserting the password, I got the following:

tar: kurso-inst.tar.gz: Cannot open: File or directory non-existent
tar: Error not recoverable; exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I checked if the files were created, for instance in /usr/bin/kurso and there are some shortcut which are invalid... and some directories in usr/share which are empty.

What am I doing wrong?

---

### Post by cdtech on 2008-11-24
First, what are you tring to install and what instructions are you using?

---

### Post by Sand Lee on 2008-11-24
what's your output of ```
ls -l install.sh
```

---

### Post by jemate18 on 2008-11-24
> **yoramdavid said:**
> Hi,

I am trying to install a sh. file, but when I double click on it, it asks what I want to do with it, I select execute and it does nothing.
From terminal I typed the following: sh /home/kurso/install.sh

I got plenty of permission denied errors, so I typed the following:

sudo sh /home/kurso/install.sh
After enserting the password, I got the following:

tar: kurso-inst.tar.gz: Cannot open: File or directory non-existent
tar: Error not recoverable; exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I checked if the files were created, for instance in /usr/bin/kurso and there are some shortcut which are invalid... and some directories in usr/share which are empty.

What am I doing wrong?

Please post the details of the program you want to install... Can you check if the kurso-inst.tar.gz is existing?

---

### Post by BLTicklemonster on 2008-11-24
> **yoramdavid said:**
> Hi,

I am trying to install a sh. file, but when I double click on it, it asks what I want to do with it, I select execute and it does nothing.
From terminal I typed the following: sh /home/kurso/install.sh

I got plenty of permission denied errors, so I typed the following:

sudo sh /home/kurso/install.sh
After enserting the password, I got the following:

tar: kurso-inst.tar.gz: Cannot open: File or directory non-existent
tar: Error not recoverable; exiting now
tar: Child returned status 2
tar: Error exit delayed from previous errors

I checked if the files were created, for instance in /usr/bin/kurso and there are some shortcut which are invalid... and some directories in usr/share which are empty.

What am I doing wrong?

kurso-inst.tar.gz? 

I'm confused, are you installing the Esparanto language program, or is /home/kurso/ an actual directory?

If it's Esparanto, rename the file so you lose the .gz extension, and it's just kurso-inst.tar then double click the file and extract it to your /home/yourname/kurso (you'll have to create the kurso folder) folder, than install from within there.

If I'm totally wrong about it, sorry. Just trying to understand what I see up there.

---

### Post by yoramdavid on 2008-11-25
Hello all and thanks for the replies,

I will try to answer everybody here.

cdtech:
> First, what are you tring to install and what instructions are you using?

I want to install the Esperanto course from here (it is in Portuguese): [http://www.cursodeesperanto.com.br/bazo/elshuto.php?pt](http://www.cursodeesperanto.com.br/bazo/elshuto.php?pt)
The instructioins are: Download, decompact the archive "kurso.tar.gz" and execute the installation script "install.sh" (requires "root" powers).


Sand Lee:
> what's your output of
Code:

ls -l install.sh
is the following:
"ls: não consigo aceder a install.sh: Ficheiro ou directoria inexistente"
Translation: "ls: cannot access to install.sh: File or folder not existent"


jemate18:
> Please post the details of the program you want to install... Can you check if the kurso-inst.tar.gz is existing?

I want to install the Esperanto course from here (it is in Portuguese): [http://www.cursodeesperanto.com.br/bazo/elshuto.php?pt](http://www.cursodeesperanto.com.br/bazo/elshuto.php?pt)
The instructioins are: Download, decompact the archive "kurso.tar.gz" and execute the installation script "install.sh" (requires "root" powers).
I am not sure what you mean by checking if the kurso-inst.tar.gz is existing... after unpacking I get a folder with inside: install.sh and another archive called kurso-inst.tar.gz which has 7 folders all with files in it.


BLTicklemonster:
> kurso-inst.tar.gz?

I'm confused, are you installing the Esparanto language program, or is /home/kurso/ an actual directory?

If it's Esparanto, rename the file so you lose the .gz extension, and it's just kurso-inst.tar then double click the file and extract it to your /home/yourname/kurso (you'll have to create the kurso folder) folder, than install from within there.

If I'm totally wrong about it, sorry. Just trying to understand what I see up there.

It is not a language pack for the computer, it is a learning program to learn Esperanto. /home/kurso/ is the directory where I downloaded the program files installation. Rernaming the archive to the .gz extension and double clicking on it just opened the content of it.

---

### Post by Keen101 on 2008-11-25
I've installed kurso de esperanto before. It's really easy once you know what to do.

1. extract the tar.gz archive onto your desktop.

2. open a terminal and type this > cd ~/Desktop/kurso

(assuming kurso is the name of the extracted folder)

3. next type this in the terminal (while still in the folder)

> sudo ./install.sh

that should install it just fine. run "kurso" from a terminal to run the esperanto program.

You will probably not have any sound, so you will need to install mpg123. Just search for "mpg123" in synaptic package manager.

---

### Post by yoramdavid on 2008-11-25
Running the command:
[Quote]cd ~/Desktop/kurso"[Quote]
Gave me this error:
[Quote]bash: cd: /home/yoram/Desktop/kurso: Permission Denied[Quote]

If I type sudo before, I get the error of not recognized "cd" command...

---

### Post by binbash on 2008-11-25
> **yoramdavid said:**
> Running the command:
[Quote]cd ~/Desktop/kurso"[Quote]
Gave me this error:
[Quote]bash: cd: /home/yoram/Desktop/kurso: Permission Denied[Quote]

If I type sudo before, I get the error of not recognized "cd" command...

did you touch the directory via root?Own the files via command chown.

---

### Post by yoramdavid on 2008-11-25
> **binbash said:**
> 
did you touch the directory via root?Own the files via command chown.

Not sure what you mean about touching the directory via root, but I realize I could not send anything to the desktop (any idea why? - I use Dolphin).
But I solved the problem!
Instead of browsing to the Kurso on the desktop, I browsed to the folder I have on my home folder and then ran the command "sudo ./install.sh"
It installed it. So, is that what I have to proceed each time I have a .sh file?

But as said above, I get no sound and when I do a search on the Synaptic there is no return for mpg123... I realized other programs mentioned also do not appear on the synaptic such as "kcontrol".
Any idea why?
Any other way to install it?

Thanks,

Yoram

---

### Post by BLTicklemonster on 2008-11-25
Extract it to

/home/yourname/kurso

(not /home/kurso)
then 

sudo install.sh

---

### Post by Keen101 on 2008-11-26
glad to hear you got it installed. I will try to help you get the sound working.

 mpg123 (or it might be mpg321) is basically a mp3 player. Kurso De Esperanto uses mp3 files for the sound. Don't ask me why, but they do. You don't have to use mpg, and you could install a different one. But, just make sure something is installed, and open kurso and click on the >Settings tab, and then on the >Sound/Internet tab. This is where you can set your mp3 player. I just installed mpg on my system, because it was easier for me. You may also want to change it from the konquor web browser to firefox.

try searching for "mpg" if my previous search suggestion came up with no results.

EDIT: maybe you don't have the community maintained "universe" repository enabled. Maybe that's why nothing was found when you searched in synaptic. To enable/disable repositories open synaptic and go to >Settings >Repositories. If everything seems fine. try refreshing and searching again.

---

### Post by yoramdavid on 2008-11-26
Hi Keen101,

Thanks, you were right, the community maintained "universe" was unchecked.
I was now able to find mpg123 and install it and now I have sound on the course.
By curiosity, I checked to see if I could find another package "kcontrol" but nothing.
Is that because it is a KDE package and I am on Ubuntu/Gnome?

Thanks again.

Yoram

---

### Post by gandaran on 2008-11-26
> Instead of browsing to the Kurso on the desktop, I browsed to the folder I have on my home folder and then ran the command "sudo ./install.sh"
It installed it. So, is that what I have to proceed each time I have a .sh file?
if you wish so, .sh files or any other file, the terminal/console always opens the home directory.
installing from desktop you have to cd the terminal there but remember if you running a Portuguese version of ubuntu it's not 'Desktop' it's 'Área de Trabalho' you have to cd

---

### Post by yoramdavid on 2008-11-26
That is why I got the error trying to browse to the desktop.
Thanks.
But, I am still confused with the .sh files, can I not just double click on them to install? It has to be done always from the terminal?
And what means the dot "." before the slash on the command
> sudo ./install.sh?

---

### Post by yoramdavid on 2008-12-01
Hello,

I have now downloaded the dictionary for Esperanto.
It came in the format of .tar.gz
I decompressed it and in the folder created there is only one file called "espcon" without extension but in the browser it says it is an executable.
Double clicking on it does not do anything.
How do I use or install it?

Thanks,

---

