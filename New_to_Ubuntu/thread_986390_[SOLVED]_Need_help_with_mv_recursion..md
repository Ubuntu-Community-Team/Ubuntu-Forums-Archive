---
title: "[SOLVED] Need help with mv recursion."
date: 2008-11-18
forum: New to Ubuntu
---

### Post by newbee70 on 2008-11-18
Hey folks, to make a long story short my 250 gig data disk got reformatted.

I used recphoto to attempt the recovery of my jpgs, txt, pdf's, and mp3's.
well: now I have over 500 directories with mixed file types.

I did the recovery by setting up a folder on my Desktop named 1, in that Directory I made a sub Directory named a into which the recovered files were placed in their directories. hence the 500 Directories named recup_dir.###. in the "a" folder.

   ~/Desktop/1/a/recup_dir.###

I mad a Directory jpg in the "1" Directory.

  ~/Desktop/1/a/recup_dir.###
            1/jpg

I thought it was the perfect place for the command line.

  mv -R ~/Desktop/1/a/recup_dir.* *.jpg ~/Desktop/1/jpg

oops no -R for the mv command.

if I manually change "cd" into each recup_dir the mv *.jpg ~/Desktop/1/jpg does work.

help please: I still have png, bmp, tiff, pdf, txt, html files to move into their folders. I don't want to go through over 500 directories for each file type. "I'm talking multi hundreds of thousands of files".

Can anyone suggest a solution to moving the files "recursively" into the folder set for that file type.

and can you suggest a program to check for file dupes that does a full file comparison?

Thanks,

---

### Post by lotharz0r on 2008-11-18
You can use 
mv `find -name *.jpg` /new/path/to/files

If you try to run find -name *.jpg from a terminal you will se that it outputs a recursive list of all jpg files.
When you use this command find will create a list of all *.jpg files recursivly FROM the dir you are currently in and further into the filesystem.

If you want to give this list to mv to specify what files to use, you only put ` ` symbols in front and at the end of command.

---

### Post by porchrat on 2008-11-18
If mv -R isn't working try "cp -R" then remove the originals afterwards

---

### Post by newbee70 on 2008-11-18
> **porchrat said:**
> If mv -R isn't working try "cp -R" then remove the originals afterwards

cp -R isn't feasible because of space limitations on my primary drive.

I'm about maxxed out with the recovery folder.

---

### Post by porchrat on 2008-11-18
Then how about a "find" for the extension you're interested in followed by a "mv" when it finds it?

That way you don't need -R

You'd have to join them with a "&&" though.

---

### Post by newbee70 on 2008-11-18
> **porchrat said:**
> Then how about a "find" for the extension you're interested in followed by a "mv" when it finds it?

That way you don't need -R

You'd have to join them with a "&&" though.


I'm not familiar with piping can you give me an example?

---

### Post by porchrat on 2008-11-18
I'm not in front of a machine at the moment to play around with it, but something along the lines of this I suppose:


```
find /location/of/the/files/ -name $1 && mv $1 /destination/
```

It is easier to just put that in a file and run it as a script.

Just name the file restore.sh or something then run "sudo chmod u+x restore.sh" to make it executable.

I can't remember whether or not "find" ouputs the entire directory path or not.  However I think it does so that shouldn't be a problem.

I don't know how familiar you are with bash, but the "$1" is an argument and it means that when you run that script you will type this (in the directory in which the script is located):

```
./restore.sh "*.ext"
```

where ext is the file extension you're interested in moving.

---

### Post by newbee70 on 2008-11-18
> **porchrat said:**
> I'm not in front of a machine at the moment to play around with it, but something along the lines of this I suppose:


```
find /location/of/the/files/ -name $1 && mv $1 /destination/
```

It is easier to just put that in a file and run it as a script.

Just name the file restore.sh or something then run "sudo chmod u+x restore.sh" to make it executable.

I can't remember whether or not "find" ouputs the entire directory path or not.  However I think it does so that shouldn't be a problem.

I don't know how familiar you are with bash, but the "$1" is an argument and it means that when you run that script you will type this (in the directory in which the script is located):

```
./restore.sh "*.ext"
```

where ext is the file extension you're interested in moving.


I am just learning Linux; tried to start with bash but quickly got lost there.

I will play around with the find command and see what I can get.

thanks.



no luck with this;

---

### Post by porchrat on 2008-11-19
what exactly does it say when you use "-R" for "mv"

I mean "mv" should have a -R option.  Mine does.

Perhaps you don't have permission to move the files?

---

### Post by lakersforce on 2008-11-19
According to the man-pages, mv does not support any -R flags, which I think means that recursion is always enabled by default.

---

### Post by hyper_ch on 2008-11-19
as lakersforce said:

mv does not need a -R option.

```

mv /path/to/folder /path/to/newfolder

```

that will move all files in folder to newfolder.

---

### Post by newbee70 on 2008-11-19
> **porchrat said:**
> what exactly does it say when you use "-R" for "mv"

I mean "mv" should have a -R option.  Mine does.

Perhaps you don't have permission to move the files?


recup_dir.188  recup_dir.277  recup_dir.365  recup_dir.453
recup_dir.189  recup_dir.278  recup_dir.366  recup_dir.454
******@desktop2:~/Desktop/1/a$ mv -R ~/Desktop/1/a/recup_dir.* / *.jpg ~/Desktop/1/jpg
mv: invalid option -- R
Try `mv --help' for more information.
*****@desktop2:~/Desktop/1/a$

---

### Post by newbee70 on 2008-11-19
> **hyper_ch said:**
> as lakersforce said:

mv does not need a -R option.

```

mv /path/to/folder /path/to/newfolder

```

that will move all files in folder to newfolder.


That may be my problem. I am trying to use mv with  the -R to move individual file types into a directory of that file type.

---

### Post by newbee70 on 2008-12-13
Re: Help with moving files.
The general format for what you want to do should be:

Code:

find /source/directory -iname '*.png' -type f -exec cp '{}' /destination/directory ';'

Just change the source and destination directories and the file extension. Spaces in file names should not be an issue.
Last edited by kaibob; 3 Hours Ago at 07:48 PM.. 


Thanks to kaibob for helping me even thought it was in a different thread!

Thanks to everyone for trying to help me out on this. I do appreciate the assists.

---

### Post by handydan918 on 2008-12-13
> **newbee70 said:**
> Re: Help with moving files.
The general format for what you want to do should be:

Code:

find /source/directory -iname '*.png' -type f -exec cp '{}' /destination/directory ';'

Just change the source and destination directories and the file extension. Spaces in file names should not be an issue.[/CODE]Uh, no. Spaces in file names are definitely an issue. They must be "escaped" using quotes, the \ (backslash character, or other escape character. ```

Last edited by kaibob; 3 Hours Ago at 07:48 PM.. 


Thanks to kaibob for helping me even thought it was in a different thread!

Thanks to everyone for trying to help me out on this. I do appreciate the assists.

Re: the mv issue. mv does not "move" a file, in the sense that Windows does. It renames it. So if you want to "move" a directory called /home/home/username to /home/username it is done by  [CODE]mv /home/home/username  /home/username
```
This is a useful thing to know when restoring a backup of /home/username to an existing /home directory....

---

### Post by newbee70 on 2008-12-13
> **handydan918 said:**
> Re: the mv issue. mv does not "move" a file, in the sense that Windows does. It renames it. So if you want to "move" a directory called /home/home/username to /home/username it is done by  ```
mv /home/home/username  /home/username
```
This is a useful thing to know when restoring a backup of /home/username to an existing /home directory....

Here is how I used it: 

I had over 500 directories recovered with the name recup_dir 1 thru recup_dir.5xx I made a folder for doc's, pdf's, mp3's, jpg's, zip's, 

I did not want to have to cd into each directory issue the move for each file type.

I had moved into the /media/D/a folder before issuing this command. 

pooter@hooters:~$ find recup_dir.* -iname '*.ppt' -type f -exec mv '{}' /media/D/a/doc ';'

it worked.

but thanks for helping me understand.

---

### Post by hyper_ch on 2008-12-14
in what sense does windows "move" a file?

---

