---
title: "Move files on folder level back"
date: 2012-12-17
forum: Programming Talk
---

### Post by mafi127 on 2012-12-17
I have about 300 files that I need to move one folder back. I have files like this

/home/user/Folder/stuff/Folder_A/Folder_B/file.txt
/home/user/Folder/stuff/Folder_A/Folder_B/anotherfile
/home/user/Folder/stuff/Folder_A/Folder_B/Third_file

/home/user/Folder/stuff/Folder_X/Folder_u/file.txt
/home/user/Folder/stuff/Folder_X/Folder_u/anotherfile
/home/user/Folder/stuff/Folder_X/Folder_u/Third_file

....

I need to move thows file on folder  back like this

/home/user/Folder/stuff/Folder_A/file.txt
/home/user/Folder/stuff/Folder_A/anotherfile
/home/user/Folder/stuff/Folder_A/Third_file

/home/user/Folder/stuff/Folder_X/file.txt
/home/user/Folder/stuff/Folder_X/anotherfile
/home/user/Folder/stuff/Folder_X/Third_file

...

can some 1 give a help whit this script. I just need to move files one folder back.

---

### Post by bird1500 on 2012-12-17
In this case the move will be atomic, that is, a rename, not a copy/delete one.

---

### Post by mafi127 on 2012-12-17
No I dont want to rename anything I just want a files will be moved one folder level back like this

/media/-Arhiiv-/Stuff/Stuff/Top/Video/50/Level8/Level8_videos/level8_files

I want to move the files from level8_videos to level 8 folder.

---

### Post by bird1500 on 2012-12-17
There are 2 ways to move files:
1) if the source and dest are not on same partition then it involves copying the data and possibly deleting the source files. The usual slow one.
2) if the source and dest are on same partition then you can do it the smart and fast way: by renaming the file's paths. Google.

---

### Post by fdrake on 2012-12-17
i'd use cp not mv because 1 mistake can f@%7 everything...
```

cp -v -R /home/user/Folder/stuff/Folder_A/Folder_B/* /home/user/Folder/stuff/Folder_A/

```
and then rm folder-B

this command will move files and folder (and it's contents) present in folder b to folder a

---

### Post by Abhinav Kumar on 2012-12-17
> **mafi127 said:**
> I have about 300 files that I need to move one folder back. I have files like this

/home/user/Folder/stuff/Folder_A/Folder_B/file.txt
/home/user/Folder/stuff/Folder_A/Folder_B/anotherfile
/home/user/Folder/stuff/Folder_A/Folder_B/Third_file

/home/user/Folder/stuff/Folder_X/Folder_u/file.txt
/home/user/Folder/stuff/Folder_X/Folder_u/anotherfile
/home/user/Folder/stuff/Folder_X/Folder_u/Third_file

....

I need to move thows file on folder  back like this

/home/user/Folder/stuff/Folder_A/file.txt
/home/user/Folder/stuff/Folder_A/anotherfile
/home/user/Folder/stuff/Folder_A/Third_file

/home/user/Folder/stuff/Folder_X/file.txt
/home/user/Folder/stuff/Folder_X/anotherfile
/home/user/Folder/stuff/Folder_X/Third_file

...

can some 1 give a help whit this script. I just need to move files one folder back.
Hi
I suggest the following shell script.
```

for file in *
do
    cp $file ../
done

```The first line selects all the files. 
../ refers to one folder up on the level.
Just save it as shell script file and give proper permissions to make it executable.
Copy this shell script file in the folder whose files you want to move it one level. Execute in that folder

Note that I have desperately used the copy function because fdrake suggested a single mistake may prove painful.

Regards,
Abhinav

---

### Post by Vaphell on 2012-12-17
try this
```
files=()
while IFS= read -rd $'\0' f
do
  files+=( "$f" )
done < <( find /home/user/Folder/stuff -mindepth 3 -type f -print0 )

for f in "${files[@]}"
do
  echo mv "$f" "${f%/*}/../${f##*/}"
done
```

put files at least 3 levels deep in array, for each element of the array move it to <path>/../<filename>
the code is probably longer than it needed to be, but i used array as a middleman to prevent possible multiple move-up on a single file (file is returned by *find*, processed, and then *find* returns it again). I don't know how *find* works exactly, so the array is there just to be on the safe side.

---

### Post by ofnuts on 2012-12-17
> **Abhinav Kumar said:**
> Hi
I suggest the following shell script.
```

for file in *
do
    cp $file ../
done

```
No need for a loop:
```

cd {directory with the files}
mv * ..

``` will do it. You can also use the syntax:
```

mv -t .. *

```

---

### Post by ofnuts on 2012-12-17
> **bird1500 said:**
> There are 2 ways to move files:
1) if the source and dest are not on same partition then it involves copying the data and possibly deleting the source files. The usual slow one.
2) if the source and dest are on same partition then you can do it the smart and fast way: by renaming the file's paths. Google.
"mv" works across file systems and thus will do 1)  or 2)

---

### Post by Abhinav Kumar on 2012-12-17
> **ofnuts said:**
> No need for a loop:
```

cd {directory with the files}
mv * ..

``` will do it. You can also use the syntax:
```

mv -t .. *

```
Hi ofnuts,
Thank you for suggesting better code. This forum always adds something new to my knowledge. :)

Regards,
Abhinav

---

### Post by mafi127 on 2013-01-06
Thank you, got problem fixed now :)

---

