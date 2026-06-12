---
title: "chmod changes didn't stick - a bug, or my mistake?"
date: 2012-03-22
forum: New to Ubuntu
---

### Post by scruffyeagle on 2012-03-22
Hi, I was trying to master use of chmod. I copied a text file & renamed it, then played around with changing the permissions. After a while, I thought I had it - so, I changed directory to where I had a subdirectory (named "hld") full of text files. I was tired of being repeatedly questioned by gedit re. whether it should run them. I entered in the console

```
chmod -v -R a-x hld
```.

I received a verbose listing in the console, indicating that each of the files in the subdirectory had been stripped of all executable bits ("-rw-r--r--"). To verify they wouldn't require me to say they're not executable, I used the file browser to go to the "hld" subdirectory and clicked on one of the files. NOPE. It prompted me, saying it was an executable file, and should it run it? I simply cancelled the operation. Looking more closely at the listing in the file browser, I found that all of the files were showing permissions as being "-rwxr-xr-x". I reloaded the browser, but the permissions showing didn't change. I returned to the terminal window that I hadn't closed yet. I used "ls -l hld", and got a listing of all the files in "hld". Every one of them was showing permissions as being "-rwxr-xr-x".

Is this a bug, or did I make some mistake when I tried to modify the file permissions?

TIA!

---

### Post by oklokl on 2012-03-22
## First directory... -> d  

### The default

user@user: [COLOR=Red]$ [/COLOR]

find /home/*/sev/ -type [COLOR=Red]d[/COLOR] -exec chmod -v 775 {} \;

find /home/*/sev/ -type f -exec chmod -v 644 {} \;


## It is user-defined
find /home/*/sev/ -type d -exec chmod -v 700 {} \;

find /home/*/sev/ -type f -exec chmod -v 600 {} \;



find /home/*/hld/ -type f -exec chmod -v 775 {} \;

---

### Post by scruffyeagle on 2012-03-23
> **oklokl said:**
> ## First directory... -> d  

### The default

user@user: [COLOR=Red]$ [/COLOR]

find /home/*/sev/ -type [COLOR=Red]d[/COLOR] -exec chmod -v 775 {} \;

find /home/*/sev/ -type f -exec chmod -v 644 {} \;


## It is user-defined
find /home/*/sev/ -type d -exec chmod -v 700 {} \;

find /home/*/sev/ -type f -exec chmod -v 600 {} \;



find /home/*/hld/ -type f -exec chmod -v 775 {} \;

Thank you for the reply. I knew that you'd told me something useful here, but I didn't understand it. I went & read the man page for "find", but I still don't fully understand what you've proposed. My questions are:
1) What is "sev"?, and
2) Why didn't my original command work?

Thanks!

---

### Post by oklokl on 2012-03-23
[http://www.thinkplexx.com/learn/article/unix/command/chmod-permissions-flags-explained-600-0600-700-777-100-etc](http://www.thinkplexx.com/learn/article/unix/command/chmod-permissions-flags-explained-600-0600-700-777-100-etc)

find  /home/*/[COLOR=Red]abcd[/COLOR]/123 -type d -exec chmod -v 700 {} \;

ex>
 1234
 abcd
 Folder name or file name

ls -alh file

cd /home/
1234.sh
?
chmod 700 1234.sh
rwx

chmod 600 1234.sh
rw


all
775
rwx


Attention

## First directory... -> d  
find  /home/*/[COLOR=Red]abcd[/COLOR]/123 -type d -exec chmod -v 700 {} \;


/home/abcde/[COLOR=Red]abcd[/COLOR]/123/12345.sh

find /home/*/*/*/12345.sh -type f -exec chmod -v 700 {} \; 
## ->[COLOR=Red]error[/COLOR]..

find /home/*/[COLOR=Red]abcd[/COLOR]/123/12345.sh -type f -exec chmod -v 700 {} \;  
##-> Normal

find /home/abcde/[COLOR=Red]abcd[/COLOR]/123/12345.sh -type f -exec chmod -v 700 {} \; 
##-> Normal

---

### Post by Bucky Ball on 2012-03-23
Which release are you using?

---

### Post by scruffyeagle on 2012-03-26
**_Bucky Ball_**:

The machine I'm working on here has 4 OS's installed. Each has the "home" folders within its own partition. Mastering the chmod is just a precursor to an editing task I need to do in order to make the OS's automatically mount a (separate) data partion I intend for them to share. I've installed:
*) Debian Squeeze,
*) Ubuntu,
*) Kubuntu, and
*) Xubuntu.

All of the Untu's are v10.04 LTS 32-bit. When I was experimenting trying to master the chmod's usage, I was working with Ubuntu.

**_oklokl_**:

Thank you for the reply, but I really didn't understand it. It will take some time & research into man pages (plus?) before I really understand the code you posted.

---

### Post by Bucky Ball on 2012-03-27
Pity you have come this far without knowing this:

ALL the OSs you mention will happily share the same /home **partition** which you could consider a data partition for them all to share. When you are installing the first OS you make a separate /home partition. Installing the second OS you simply untick the existing /home partition and the second install will automatically use the existing /home as its /home also, and third and fourth OS etc.

May not be much use now but might help in future. 

If you're wanting to create a data partition for all OSs to share why not just create one? You shouldn't need to tweak permissions once it's there but you may need to add it to fstab so it mounts at boot.

As you already have four partitions (and presuming they are primary) you will need to do some repartitioning to realise your intention as the limit for a physical drive is four partitions. You'll need to create an extended partition as the fourth partition and, theoretically, you can put as many logical drives in there as you like (read: as your hardware can handle). It's still considered to be four partitions on one physical drive. ;)

---

### Post by scruffyeagle on 2012-03-31
> **Bucky Ball said:**
> Pity you have come this far without knowing this:

ALL the OSs you mention will happily share the same /home **partition** which you could consider a data partition for them all to share. When you are installing the first OS you make a separate /home partition. Installing the second OS you simply untick the existing /home partition and the second install will automatically use the existing /home as its /home also, and third and fourth OS etc.

May not be much use now but might help in future. 

If you're wanting to create a data partition for all OSs to share why not just create one? You shouldn't need to tweak permissions once it's there but you may need to add it to fstab so it mounts at boot.

As you already have four partitions (and presuming they are primary) you will need to do some repartitioning to realise your intention as the limit for a physical drive is four partitions. You'll need to create an extended partition as the fourth partition and, theoretically, you can put as many logical drives in there as you like (read: as your hardware can handle). It's still considered to be four partitions on one physical drive. ;)

I did what you describe during my 1st attempt at setting up this HD; i.e., I assigned placement of "home" into the same extra partition during the installation of each OS. It worked well enough at first, but there were problems w/ accessing the home folders. It seemed as if there was scripting (environment variables being set?) going on that caused conflicts. I was getting messages that the home folder was corrupted. Then I'd go use a different OS and have no problem at all. I wish I could be more specific for you, but I've forgotten the details & didn't write them down. My solution was to simply let each OS make its mandatory "home" folders in its own partition. Simply making the folders doesn't take up much space at all. I don't consider myself obligated to actually USE them! So, I've been studying the fstab mount process, to make mounting of the extra data partition automatic. Problem is, I'd never mastered the chmod process. I had to learn that, in order to edit for fstab. Which is when I ran into trouble w/ chmod - with changes in permissions made being echoed as accomplished by verbose, but then being found unchanged via ls.

gparted shows my layout of partitions is:
sda1 : 11.72GB - Ext4 - Debian
sda2 :  3.91GB - Linux Swap
sda3 : 96.16GB - Extended
sda5 : 11.72GB - Ext4 - Ubuntu
sda6 : 11.72GB - Ext4 - Kubuntu
sda7 : 11.72GB - Ext4 - Xubuntu
sda8 : 50.78GB - Ext4 - Data
sda9 : 10.22GB - FAT32 - (Haven't decided yet)

It probably would have been a better choice to make sda3 the Data partition, and sda4 the Extended... But, at this point I don't think it will make much difference.

At the moment, my big problem is the failure of chmod to actually change the permissions on my test file(s). I need to know why it didn't work, before I can proceed.

---

