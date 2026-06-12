---
title: "terminal command to external drive"
date: 2017-10-30
forum: New to Ubuntu
---

### Post by smokeyone2 on 2017-10-30
Hello

I have been trying to access my external drive via the terminal and a command line without success. I am hoping someone can tell me my mistake -

So far - I have changed currect directory to desktop and then tried to change to my external drive which is mounted - I can copy and paste if I needed to -
copy & paste from the top of my screen shows    /media/owner/3CF67E51F67E0C00      as my external drive

owner@owner-HP-xw6400-Workstation:~$ cd ~/Desktop
owner@ownerl-HP-xw6400-Workstation:~/Desktop$ cd /media/owner/3CF67E51F67E0C00
owner@owner-HP-xw6400-Workstation:/media/owner/3CF67E51F67E0C00$ 

Many thanks

---

### Post by deadflowr on 2017-10-30
Seems like you're in it already
```
owner@owner-HP-xw6400-Workstation:/media/owner/3CF67E51F67E0C00$ 
```
one would assume.....

Now what do you want to do?
Since you seem to have it, use something like
```
ls
```
to view it's contents.

---

### Post by smokeyone2 on 2017-10-30
Thanks for the advice

This command works on my desktop but not on my external drive

find b123 -type d -print0 | xargs -0 -n1 bash -c 'echo -n "$1:"; ls -1 "$1" | wc -l' &#8211;
find: &#8216;b123&#8217;: No such file or directory
:ls: cannot access '': No such file or directory


It lists all the names and the number of files in each folder - the folder is called b123 and inside are scores of image files each containing around a 100 images

london 99
Birmingham 23
Manchester 76

just examples

---

### Post by yancek on 2017-10-30
The find command you show would need to be run from the directory in which the sub-directory b123 resides.  Is it in the windows partition you refer to under the /media directory?

---

### Post by smokeyone2 on 2017-10-30
I am not sure I understand correctly - [COLOR=#000000]Is it in the windows partition you refer to under the /media directory? - thanks again for the help

Top of the screen tools - open the current folder in terminal !

[/COLOR]owner@owner-HP-xw6400-Workstation:/media/owner/3CF67E51F67E0C00$ find b123 -type d -print0 | xargs -0 -n1 bash -c 'echo -n "$1:"; ls -1 "$1" | wc -l' &#8211;
find: &#8216;b123&#8217;: No such file or directory
:ls: cannot access '': No such file or directory
0
owner@owner-HP-xw6400-Workstation:/media/owner/3CF67E51F67E0C00$

---

### Post by yancek on 2017-10-31
> owner@owner-HP-xw6400-Workstation:/media/owner/3CF67E51F67E0C00$ 

The UUID you show above indicates that is an ntfs parttion/filesystem so if you navigate there in a file manager, you should see the director "b123", same result if you navigate there and run the ls command.  So is that the location of b123?  Is the problem that the b123 directory is not there or is it there and your find command has problems.  Your last post would seem to indicate that b123 is not in that location?

If the b123 directory is on that partition, running the following from anywhere in the system should show it:

> ls /media/owner/3CF67E51F67E0C00

---

### Post by smokeyone2 on 2017-10-31
Hello

If I type   ls   all the folders in the external driver are listed including b123 but when I try various commands involving b123 all I get is no such file or directory etc

owner@nigel-HP-xw6400-Workstation:/media/owner/3CF67E51F67E0C00$ ls
20171004   Japan                         Aircraft 3
b123                                              Aircraft 4
Desktop to back up                       NewDatabase.kdbx
Documents to delete in Januart
etc                                                 etc

Update to my problems - at last I have succeeded although at a lost to understand why ....

I just changed the name of my folder inside my external drive from b123 to 123456 - anything to do with letters in the name - anyways the command listed all the files inside the folder and the number of images inside each file.
Thanks to everyone for their advice

---

### Post by yancek on 2017-10-31
I'm not clear on the situation as this:  > b123                                              Aircraft 4 would indicate 3 different directories or files; b123, Aircraft, 4.  If you have spaces in a name of a directory or file, you need to enclose in quotes " " using a command from a terminal.  Not sure if that was the case??  If not, I don't know why changing the name from b123 to 123456 would make any difference.

---

### Post by leunam12 on 2017-10-31
Do you have to use quotes or escape it? Example ```
find b123\ Aircraft\ 4/
``` ??
I'm confused now.

---

### Post by oldfred on 2017-10-31
I learned a long time ago when swithing from Windows to Linux to stop using spaces.
I use CamelCase, under_score or justonelongname for every thing now.

There also are some characters that you must avoid.

I have seen the parameter windows_names and used it on fstab entries, but with an external drive usually not mounted with fstab.

 window_names prevents the use of invalid windows characters:
(which are the nine characters &#8221; * / : < > ? \ | and those whose code is less than 0×20)

---

### Post by smokeyone2 on 2017-10-31
b123 & Aircraft 3 & Aircraft 4 are three separate directories or folders each containing scores of files with each file containing loads of images and as mentioned previously when using the command     [COLOR=#000000]find b123 -type d -print0 | xargs -0 -n1 bash -c 'echo -n "$1:"; ls -1 "$1" | wc -l' &#8211;
on my desktop     it works fine but when tried on my external hard drive message always says   no such file - just changing the folder name to just a number seems to work[/COLOR]

---

### Post by yancek on 2017-10-31
> b123 & Aircraft 3 & Aircraft 4 are three separate directories

From a terminal in Linux, there would be 4 directories:  b123, Aircraft, 3, 4.  Not sure what will happen with 2 directories named Aircraft?  You can either use the escap character around spaces or simply use quotes which I find easier.

I created a test directory named b123 under /mnt and two empty files within it.  Then cd /mnt and run your command:

> [COLOR=#000000]find b123 -type d -print0 | xargs -0 -n1 bash -c 'echo -n "$1:"; ls -1 "$1" | wc -l' &#8211;[/COLOR]]

The output I got was:  b123:2
which is the b123 folder showing 2 files in it.  

You can also run it from anywhere in the filesystem by including the cd command as below:  This gives the same output as above.

> cd /mnt/ && find b123 -type d -print0 | xargs -0 -n1 bash -c 'echo -n "$1:"; ls -1 "$1" | wc -l' -


It does seem weird to me that just changing the directory name worked??

---

### Post by smokeyone2 on 2017-11-01
I have spent ages trying to find the problem and although the result is strange at least it works. Thank you for all your advice.
I use the find 123456 command to list all the files inside the 123456 folder together with the number of images inside each file

Just as an example - the list will look something like this - also listed will be the total number of files (not images)

123456/20081026   Rome:16
123456/20081106   London:54
123456/20090116   Paris:10
123456/20090205   Brussels:285
123456/20090403   Paris:2
123456/20090417   Paris:25
123456/20090418   London:3
123456/20090420   Amsterdam:21
123456/20090430   Berlin:21
123456/20090430 London:15

---

