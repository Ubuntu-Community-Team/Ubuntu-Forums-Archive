---
title: "request for help with bash code"
date: 2011-02-20
forum: Programming Talk
---

### Post by Old Jimma on 2011-02-20
Ubuntu community:

In the directory /var/recovery/original I have many subdirectories named
recup_dir.1 recup_dir.1 ... recup_dir.659

Within each of those directories are many file types, and for the time being, I'm interested only in the jpg files. I want to copy all of those file jpg files into **[COLOR="Blue"]/var/recovery/original/JPG[/COLOR]**.

However, it is possible that some jpg files in different recup_dir dirctories have the same name, but are really different jpg files.

With the assistance of the forums I was able to write the following bash code. It is incompletely written.

This code loops over the recup_dir directories.

For each recup_dir directory, I want:
[LIST]
[*]the code to copy the jpg files to **[COLOR="Blue"]/var/recovery/original/JPG[/COLOR]** .... 
[*]but to rename the file in that **[COLOR="Blue"]/var/recovery/original/JPG[/COLOR]** directory to have a new "prefix" equal to the recup_dir directory nam followed by the jpg file name in that recup_dir.
[/LIST]

 Here is the code that I have.



clear
cd /var/recovery/original
[COLOR="Red"]**# LOOP OVER THE DIRECTORIES**[/COLOR]
for i in recup_dir.*/
do

	echo $i
	cd $i

              [COLOR="DarkGreen"]**for every jpg file in the [COLOR="Red"][B]$i**[/COLOR] directory, copy the jpg file to [COLOR="Blue"]/var/recovery/original/JPG[/COLOR] with a new "prefix" designated by the [COLOR="Red"]**$i**[/COLOR] value[/B][/COLOR]

		done

	cd ..
done
[COLOR="Red"]**## END LOOP OVER THE DIRECTORIES**[/COLOR]

How do I write the **[COLOR="DarkGreen"]green[/COLOR]** code so that the files are copied appropriately?

Thanks,
Phil Smith
Duluth, GA

---

### Post by CharlesA on 2011-02-20
Moved to PT, might be able to get some help there. :)

Why not just use find instead of using ls and cd?

---

### Post by gmargo on 2011-02-20
> **Phil Smith said:**
> 
              [COLOR=DarkGreen]**for every jpg file in the [COLOR=Red][B]$i**[/COLOR] directory, copy the jpg file to [COLOR=Blue]/var/recovery/original/JPG[/COLOR] with a new "prefix" designated by the [COLOR=Red]**$i**[/COLOR] value[/B][/COLOR]

How do I write the **[COLOR=DarkGreen]green[/COLOR]** code so that the files are copied appropriately?


```

DESTDIR=/var/recovery/original/JPG
for JPG in *.[jJ][pP][gG]
do
        if [ -f "$JPG" ] ; then
                echo cp -p "$JPG"  "${DESTDIR}/${i}_${JPG}"
        fi
done

```Remove the "echo" when you're ready.

---

### Post by Old Jimma on 2011-02-20
Many thanks to CharlesA and gmargo for their replies!

To let you know how this problem originated, I wiped out my hard drive and back up a few weeks ago, and used photorec to recover files. See: [http://ubuntuforums.org/showthread.php?t=1675564]("http://ubuntuforums.org/showthread.php?t=1675564") for all of the details.

The reason why find isn't a good tool for reorganizing files that photorec has recovered is that photorec can recover different files, put them in different recovery directories, an but give those files the same name! If you don't account for different files having the same file name, you'll overwrite some files and loose data!

gmargo's solution overcomes this problem! Here is the entire code that I used to loop thru the many directories created by photorec and copy the JPG files to a directory devoted only to JPG files, renaming each file to have a unique file name.

I hope someone else can use this!

[COLOR="Red"]**THANK YOU gmargo!!!**[/COLOR]

Sincerely, 
Phil Smith
Duluth, GA

```
clear
cd /var/recovery/original
# LOOP OVER THE DIRECTORIES
for i in recup_dir.*
do
echo $i
cd $i
DESTDIR=/var/recovery/original/JPG
for JPG in *.[jJ][pP][gG]
do
        if [ -f "$JPG" ] ; then
#                 echo cp -p "$JPG"  "${DESTDIR}/${i}_${JPG}"
               cp -p "$JPG"  "${DESTDIR}/${i}_${JPG}"
        fi
done
cd ..
done
# END LOOP OVER THE DIRECTORIEs
```

---

### Post by transient on 2011-11-14
I was looking for the solution to the exact same problem, thank you very much for the script! :D

---

