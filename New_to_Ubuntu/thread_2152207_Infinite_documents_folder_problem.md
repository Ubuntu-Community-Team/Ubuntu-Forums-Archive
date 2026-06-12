---
title: "Infinite documents folder problem"
date: 2013-06-07
forum: New to Ubuntu
---

### Post by kubOSuser on 2013-06-07
Can anyone please tell me how did it happened?

Today i found out i have infinite Documents folder. If i go in "Documents" folder, i can go as much as i like.. Clicked like 50times.. if i go to other folders that are in "Documents" folder they are empty and they are not infinite.

[IMG]http://i.imgur.com/HlmTMVn.jpg[/IMG]

---

### Post by zombifier25 on 2013-06-07
Post the output of this command:
```
ls -l ~/Documents
```
It's possible that you have somehow made a symlink in the folder Documents that point to itself.

---

### Post by matt_symes on 2013-06-07
Hi

It sounds like you have a symlink pointing to itself or its current folder.

Delete the symlink to remove it.

Kind regards

---

### Post by kubOSuser on 2013-06-07
how can i see symlink icon or file? is it invisible? And how to remove it if i see it?

total 3972
-rw-rw-r-- 1 dizainas dizainas  125627 Dec 20 16:07 baneris1.gif
-rw-rw-r-- 1 dizainas dizainas  657587 Dec 20 16:06 baneris1.xcf
-rw-rw-r-- 1 dizainas dizainas  212485 Dec 20 16:28 baneris2.gif
-rw-rw-r-- 1 dizainas dizainas 2152040 Dec 20 16:27 baneris2.xcf
-rw-rw-r-- 1 dizainas dizainas  890824 Dec 20 16:02 baneris.xcf
drwxrwxr-x 2 dizainas dizainas    4096 May 31 15:51 Desktop
drwxrwxr-x 6 dizainas dizainas    4096 May 31 15:51 Documents
drwxrwxr-x 5 dizainas dizainas    4096 May 31 15:51 Downloads
-rw-rw-r-- 1 dizainas dizainas    5349 May 17 13:39 font.png

---

### Post by Impavidus on 2013-06-07
I don't see a symlink.

Look at the number of hardlinks to ~/Documents/Documents: 6. These should be (assuming it has the same contents as ~/Documents):
1: ~/Documents/Documents
2: ~/Documents/Documents/.
3: ~/Documents/Documents/Desktop/..
4: ~/Documents/Documents/Downloads/..
5: ~/Documents/Documents/Documents/..
6: ???

That final hardlink may well be the key to your mystery. It could be ~/Documents/Documents/Documents, meaning you have a hardlink loop. Don't ask me where you could have got it from. Can you give the output of ```
ls -ail ~/Documents
```The inode numbers may make things clear.

Edit: Of course there could also be a hidden directory, making this:
6: ~/Documents/Documents/.hidden/..
The -a option for ls will tell. A hidden directory in the Documents directory would be strange, but this is strange anyway.

---

### Post by zombifier25 on 2013-06-08
You can't make hardlinks to folders.

Probably there are symlinks to the Documents folder inside those children Documents folder. This fiasco is confusing as heck, and I don't think the OP did it himself. Malfunctioning scripts maybe?

---

### Post by Impavidus on 2013-06-08
I know Ubuntu doesn't allow you to create hardlinks to directories, but IIRC they can theoretically exist in the file system. I've no idea how you would create one.

Best thing would be digging into those directories with the terminal and using ls to search for symlinks (and maybe hardlinks, although that would be really strange):```

ls -ali ~/Documents
ls -ali ~/Documents/Documents
ls -ali ~/Documents/Documents/Documents
...

```
The output will probably repeat at some point.

To recognise a symlink:```

egroot@Iphigeneia:~$ ls -ali ~/temp
totaal 20
2883648 [COLOR=#0000cd]d[/COLOR]rwxrwxr-x  2 egroot egroot  4096 jun  8 10:38 .
2883585 [COLOR=#0000cd]d[/COLOR]rwxr-xr-x 69 egroot egroot 12288 jun  8 08:35 ..
2883764 [COLOR=#ff0000]l[/COLOR]rwxrwxrwx  1 egroot egroot     8 jun  8 10:38 foo.txt [COLOR=#ff0000]-> test.txt[/COLOR]
2887282 -rw-rw-r--  1 egroot egroot   768 nov 16  2012 test.txt

```
A d (in blue) indicates a directory, an l and the **-> name** (in red) indicate a symlink and its target. The numbers at the start of the lines indicate the inode number. Maybe you find the 6th hardlink pointing to the same inode.

Also, if you create or modify a file in ~/Documents, do you immediately see the changes in all other Documents directories, only in alternating ones or so, or in no others? Are those copies symlinks, copies or are they identical, in which case they have the same inode number?

---

### Post by kubOSuser on 2013-06-10
Sorry for late reply... this is what i get.. Have no clue about this mess.. Doesnt seem i have symlinks.. 

dizainas@dizainas-V:~$ ls -ali ~/Documents
total 3980
6684684 drwxr-xr-x  5 dizainas dizainas    4096 Jun  7 12:00 .
6684673 drwxr-xr-x 29 dizainas dizainas    4096 Jun 10 09:17 ..
6691393 -rw-rw-r--  1 dizainas dizainas  125627 Dec 20 16:07 baneris1.gif
6691391 -rw-rw-r--  1 dizainas dizainas  657587 Dec 20 16:06 baneris1.xcf
6690604 -rw-rw-r--  1 dizainas dizainas  212485 Dec 20 16:28 baneris2.gif
6691402 -rw-rw-r--  1 dizainas dizainas 2152040 Dec 20 16:27 baneris2.xcf
6691360 -rw-rw-r--  1 dizainas dizainas  890824 Dec 20 16:02 baneris.xcf
7209880 drwxrwxr-x  2 dizainas dizainas    4096 May 31 15:51 Desktop
7209882 drwxrwxr-x  6 dizainas dizainas    4096 May 31 15:51 Documents
7209881 drwxrwxr-x  5 dizainas dizainas    4096 May 31 15:51 Downloads
6693551 -rw-rw-r--  1 dizainas dizainas    5349 May 17 13:39 font.png
dizainas@dizainas-V:~$ 
dizainas@dizainas-V:~$ ls -ali ~/Documents/Documents
total 3976
7209882 drwxrwxr-x  6 dizainas dizainas    4096 May 31 15:51 .
6684684 drwxr-xr-x  5 dizainas dizainas    4096 Jun  7 12:00 ..
7210172 -rw-rw-r--  1 dizainas dizainas  125627 Dec 20 16:07 baneris1.gif
7209950 -rw-rw-r--  1 dizainas dizainas  657587 Dec 20 16:06 baneris1.xcf
7209948 -rw-rw-r--  1 dizainas dizainas  212485 Dec 20 16:28 baneris2.gif
7210173 -rw-rw-r--  1 dizainas dizainas 2152040 Dec 20 16:27 baneris2.xcf
7209949 -rw-rw-r--  1 dizainas dizainas  890824 Dec 20 16:02 baneris.xcf
7209888 drwxrwxr-x  2 dizainas dizainas    4096 May 31 15:51 Desktop
7209930 drwxrwxr-x  6 dizainas dizainas    4096 May 31 15:51 Documents
7209924 drwxrwxr-x  5 dizainas dizainas    4096 May 31 15:51 Downloads
dizainas@dizainas-V:~$ ls -ali ~/Documents/Documents/Documents
total 1748
7209930 drwxrwxr-x  6 dizainas dizainas   4096 May 31 15:51 .
7209882 drwxrwxr-x  6 dizainas dizainas   4096 May 31 15:51 ..
7210195 -rw-rw-r--  1 dizainas dizainas 657587 Dec 20 16:06 baneris1.xcf
7210193 -rw-rw-r--  1 dizainas dizainas 212485 Dec 20 16:28 baneris2.gif
7210194 -rw-rw-r--  1 dizainas dizainas 890824 Dec 20 16:02 baneris.xcf
7209954 drwxrwxr-x  2 dizainas dizainas   4096 May 31 15:51 Desktop
7209956 drwxrwxr-x  6 dizainas dizainas   4096 May 31 15:51 Documents
7209955 drwxrwxr-x  5 dizainas dizainas   4096 May 31 15:51 Downloads
dizainas@dizainas-V:~$ ls -ali ~/Documents/Documents/Documents/Documents
total 24
7209956 drwxrwxr-x  6 dizainas dizainas 4096 May 31 15:51 .
7209930 drwxrwxr-x  6 dizainas dizainas 4096 May 31 15:51 ..
7210053 drwxrwxr-x  2 dizainas dizainas 4096 May 31 15:51 Desktop
7210055 drwxrwxr-x  6 dizainas dizainas 4096 May 31 15:51 Documents
7210054 drwxrwxr-x  5 dizainas dizainas 4096 May 31 15:51 Downloads
dizainas@dizainas-V:~$ ls -ali ~/Documents/Documents/Documents/Documents/Documents
total 24
7210055 drwxrwxr-x  6 dizainas dizainas 4096 May 31 15:51 .
7209956 drwxrwxr-x  6 dizainas dizainas 4096 May 31 15:51 ..
7340147 drwxrwxr-x  2 dizainas dizainas 4096 May 31 15:51 Desktop
7340149 drwxrwxr-x  6 dizainas dizainas 4096 May 31 15:51 Documents
7340148 drwxrwxr-x  5 dizainas dizainas 4096 May 31 15:51 Downloads
dizainas@dizainas-V:~$

---

### Post by Impavidus on 2013-06-10
No symlinks indeed. The files and directories you have there are all different files, all taking up disk space. I hope that at some point there is a loop nonetheless or it terminates, else it consumes infinite inodes and disk space, which probably doesn't fit in your file system. Also, the number of hardlinks to the Documents directories doesn't add up. The first Documents directory has 5 hardlinks pointing to it, the others have 6. They should all have 5. There are no hidden directories, so this shouldn't be possible.

I made a small script that can scan your infinite documents folder and search for loops. If you wish you can save it, make it executable and run it. It will search at most 250 levels deep and produce a small log file (infinity.log) in your home directory.```

#!/bin/bash
cd ~
output=~/infinity.log
iterations=250
echo Searching directories for a loop >"$output"
i=0
while [ $i -lt $iterations ]
do
  if [ -e Documents ]
  then :
  else
    echo Tree terminates >>"$output"
    echo Tree terminates
    exit
  fi
  line=$(ls -dli Documents)
  inode=$(expr match "$line" '\([0-9]*\)')
  if grep -q $inode "$output"
  then
    echo $line >>"$output"
    echo Loop found! >>"$output"
    echo Loop found!
    exit
  fi
  echo $line >>"$output"
  cd Documents
  (( i += 1 ))
done
echo Reached $i iterations. Terminating. >>"$output"
echo Reached $i iterations. Terminating.

```
It's probably save to copy all files you want to keep out of the first Documents directory and then recursively delete it, but it would be nice to know the cause of this. As long as we don't know the cause it could happen again or deleting it may have side effects.

---

### Post by kubOSuser on 2013-06-11
Oh.. well thanks for that.. here is the .log
********************************************

Searching directories for a loop
6684684 drwxr-xr-x 5 dizainas dizainas 4096 Jun 7 12:00 Documents
7209882 drwxrwxr-x 6 dizainas dizainas 4096 Jun 11 10:33 Documents
7209930 drwxrwxr-x 6 dizainas dizainas 4096 Jun 11 10:33 Documents
7209956 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:51 Documents
7210055 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:51 Documents
7340149 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:51 Documents
7340524 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:51 Documents
7471529 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:51 Documents
7733527 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
7995509 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
8126608 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
8257845 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
9568336 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
9699444 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
9830546 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
9961561 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10092597 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10223686 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10224169 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10355219 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10486281 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10617339 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10748396 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
10879450 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11010500 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11141550 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11272587 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11403631 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11534670 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11665705 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11796739 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
11927785 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
12058803 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
12189822 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
12320844 drwxrwxr-x 6 dizainas dizainas 4096 May 31 15:52 Documents
12451866 drwxrwxr-x 5 dizainas dizainas 4096 Jun 7 11:16 Documents
12452437 drwxrwxr-x 2 dizainas dizainas 4096 May 31 15:52 Documents
Tree terminates

******************************************************

I hope this is useful, for me its just useless same repeated information which is weird.. no clue if your script worked..

---

### Post by Impavidus on 2013-06-11
It tells me that you have 37 nested Documents folders, but no loops purely consisting of Documents folders. There are no repeating inodes. There must have been a script copying your directories. Most of them were produced at the same moment, so the script doesn't seem active any more. It will be difficult to find out what exactly happened. The last but one directory had one modification around the moment when you started this thread. A file or directory was added or deleted, but not the Documents directory inside, which is older. Also, these last two Documents directories and the first one are the only ones having the correct number of hard links, the intermediate ones have one too many. That's strange.

At this point I would probably just delete the second Documents directory and everything inside and hope the problem doesn't return, but if you wish we can go on trouble-shooting. Unfortunately, I'm running out of ideas.

---

### Post by kubOSuser on 2013-06-11
No need for you to sweat your breath for this nuisance.. Im glad this is not harmful, thus its interesting how it happened. Maybe i managed to link the documents into documents, but im not sure how ive done it.
All posibilities are: for me kubuntu is annoying as hell, so i often need to resize that "places" bar that is in folder left(has many shortcuts to different folders). And why resize? Because short folder shortcut titles makes that "bar" too short, and i prefer to resize. Nothing else comes to my mind.

Thanks for your time looking in this problem.

---

### Post by Buntu Bunny on 2013-06-18
I just started having this same problem today, with only one folder I created on my desktop. It's the first time I've accessed that folder in awhile and I didn't have this problem before. I can run ls -ali on my desktop, but not that individual folder. Perhaps this is because I used parentheses in the folder name, and terminal doesn't recognise parentheses. 

After reading through this thread, perhaps it doesn't matter. Still, it's puzzling and something I'd rather do without.

---

### Post by Impavidus on 2013-06-18
You may have to escape the parentheses in the terminal with backslashes, or use quotes.

---

### Post by Buntu Bunny on 2013-06-18
> **Impavidus said:**
> You may have to escape the parentheses in the terminal with backslashes, or use quotes.

Impavidus, thanks! Neither of those suggestions worked, so it occurred to me to rename the folders. I discovered that the folders aren't infinite, but the folder in question terminates after two duplicates. I can never get past the first two with the ls -ali command. Even so, I don't see any evidence of symlinks. Is this correct?

```
leigh@leigh-CM1740:~$ ls -ali ~/Desktop/Book_proofed
total 72
7340828 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:22 .
5898253 drwxr-xr-x 7 leigh leigh  4096 Jun 18 12:18 ..
7345796 -rw-rw-r-- 1 leigh leigh 34506 May 24 18:55 added paragraphs ch 1 - 8 (partial) 10 May 2013.odt
7340915 -rw-rw-r-- 1 leigh leigh 21730 May 24 18:55 added paragraphs ch 9 (remaining) - 21 May 2013.odt
7738126 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:28 sent
leigh@leigh-CM1740:~$ ls -ali ~/Desktop/Book_proofed/sent
total 36
7738126 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:28 .
7340828 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:22 ..
7738808 -rw-rw-r-- 1 leigh leigh  4993 May 21 06:22 acknowledgments for proofing.docx
5913704 -rw-rw-r-- 1 leigh leigh 14156 May 10 11:45 added paragraphs ch 1 - 8 (partial) 10 May 2013.docx
7738510 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:23 Book_proofed
leigh@leigh-CM1740:~$ ls -ali ~/Desktop/Book_proofed
total 72
7340828 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:22 .
5898253 drwxr-xr-x 7 leigh leigh  4096 Jun 18 12:18 ..
7345796 -rw-rw-r-- 1 leigh leigh 34506 May 24 18:55 added paragraphs ch 1 - 8 (partial) 10 May 2013.odt
7340915 -rw-rw-r-- 1 leigh leigh 21730 May 24 18:55 added paragraphs ch 9 (remaining) - 21 May 2013.odt
7738126 drwxrwxr-x 3 leigh leigh  4096 Jun 18 12:28 sent
```

---

### Post by Buntu Bunny on 2013-06-18
OK, well, after looking around for clues I moved the needed docs to another folder and deleted that one. It's only happened that once, but this thread helped, even if it wasn't for definitive answers.

---

### Post by Impavidus on 2013-06-18
Indeed, no symlinks, no hardlinks, just copies.

To type the name in a terminal you can also try tab completion: type a few characters and hit tab. Bash will guess the remaining characters as long as there is only one matching file/directory and will add the necessary escape characters.

Remarkable that multiple people have this problem at the same time. Maybe someone released a malfunctioning script into the wild.

---

### Post by Buntu Bunny on 2013-06-18
> **Impavidus said:**
> To type the name in a terminal you can also try tab completion: type a few characters and hit tab. Bash will guess the remaining characters as long as there is only one matching file/directory and will add the necessary escape characters.

Great tip, thanks!

> **Impavidus said:**
> Remarkable that multiple people have this problem at the same time. Maybe someone released a malfunctioning script into the wild.

Indeed. Fortunately I found this thread while browsing the forum last week. When I ran into the same problem myself, I knew right where to go.

---

