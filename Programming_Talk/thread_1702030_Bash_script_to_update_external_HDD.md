---
title: "Bash script to update external HDD"
date: 2011-03-07
forum: Programming Talk
---

### Post by CaptainMark on 2011-03-07
I was looking to write a simple bash script to automatically update 5 folders to my external hdd when i run the script, it works fine and was quite easily done. A few weeks/months later i realised that files I delete locally wont be removed from the hdd but remain there so i building up a back up of redundant files, how would i alter my script to fix this, im thinking my pseudocode would be something like ```
copy -recursively local_dir to ext_dir
for ext_file in ext_dir:
    if ext_file not in local_dir:
        remove ext_file
```Any ideas? I know I could use other software, im just curious to understand bash in more detail. It probaly seems silly but everyones gotta start somewhere, im learning as and when a task comes up

and heres the script now ```
#!/bin/bash

# bash script to update files in /home/mark to my passport


echo 'Copying Music'
cp -ru ~/Music/* /media/passport/Music
echo 'Done' && aplay -q ~/Documents/sounds/zelda/stereo/emptytrash.wav

echo 'Copying Documents'
cp -ru ~/Documents/* /media/passport/Documents
echo 'Done' && aplay -q ~/Documents/sounds/zelda/stereo/emptytrash.wav

echo 'Copying Pictures'
cp -ru ~/Pictures/* /media/passport/Pictures
echo 'Done' && aplay -q ~/Documents/sounds/zelda/stereo/emptytrash.wav

echo 'Copying Videos'
cp -ru ~/Videos/* /media/passport/Videos
echo 'Done' && aplay -q ~/Documents/sounds/zelda/stereo/emptytrash.wav

echo 'Copying Downloads'
if [ -e ~/Downloads/* ]; then
    cp -ru ~/Downloads/* /media/passport/Downloads;
else
    echo 'Downloads Folder Empty';
fi
echo 'Done'
echo 'Exiting'
aplay -q ~/Documents/sounds/zelda/stereo/email.wav


```

---

### Post by oldfred on 2011-03-07
First question is - do you really want to delete?  I have many times deleted something by accident and been glad there was a backup. If the backup auto deletes then it is not there. I might delete if I have an offline copy i.e. DVD with all the files and then delete the on line versions obsolete files.

You may want to look at rsync. It has lots more options including deletes.

man rsync

Originally Posted by MountainX View Post #20 also other backup apps
[http://ubuntuforums.org/showthread.php?t=868244&highlight=backup](http://ubuntuforums.org/showthread.php?t=868244&highlight=backup)
use a text editor and paste this into a file. name it mybackup.sh

[http://ubuntuforums.org/showthread.php?t=1701292](http://ubuntuforums.org/showthread.php?t=1701292)

Someone posted this comment which I think relates to my deletion of files issue above. Then you have a full image backed up, where cp or rsync do not.
Use tar and gzip to make backups. The rsync tool is not as effective for backup.

---

### Post by CaptainMark on 2011-03-07
yeah i would want to delete i only do it once it every few weeks so i wouldnt run the script until i am sure everything is okay, saying that about zips is a good thought, if i just zipped all the folders i wanted to back up to the passport any subsequent zips would overwrite the first, thanks

---

### Post by Grenage on 2011-03-07
I'll throw a 'me too' in there for rsync; it's an excellent program for backups.

---

### Post by CaptainMark on 2011-03-07
What would be a good compression type to use for backing up, im not worried about how much it compresses or infact how fast it is seen as it will only be occasional use, but i want one that will be no risk of quality reduction, ive heard of files becoming corrupt when compressed/uncompressed often,

---

### Post by Grenage on 2011-03-07
I normally use tar.gz (gzip), but I hear good things about 7zip.

While corruption with compressed archives does occasionally happen, it's not very common.  No more so than with other mediums, and missing data chunks.

---

### Post by CaptainMark on 2011-03-07
hmhm, i always thought rsync was another over bloated non-free gui application, i see now i completely wrong, i think im just going to use this, will save a lot of time compressing everything everytime will take a lot longer than i expected seen as i seed about 10 various linux torrents at all times, and all my music files documents photos etc, it would take too long

---

### Post by CaptainMark on 2011-03-07
okay ive played around with rsync a bit, i dont know how to accept input from bash scripts but i want to do something like this:```
rsync -vaEn --delete ~/* /media/passport/back_up/     # verbosive dry-run (no writing)

var1= input("Do you want to continue with this backup? (y/n)")

if var1 == y:
    rsync -vaE --delete ~/* /media/passport/back_up/

else:
   echo "Backup Aborted"
```Haha, this is my made up splice of bash and python, ill work on this but any tips would be appreciated seen as i have no idea even about how to store variables in bash. :P

ps. verbosive is not a word, i checked

---

### Post by oldfred on 2011-03-07
Another thread and this user creates a list of files to be deleted.

rsync confirmation list:
[http://ubuntuforums.org/showthread.php?t=1692800](http://ubuntuforums.org/showthread.php?t=1692800)

---

### Post by CaptainMark on 2011-03-07
@oldfred thanks i will definately look into that too,

this is beyond weird though, i think ive knocked up the correct script, it uses the delete function and it works fine, i have absolutley not problem about what it does, but look ??? ```
#!/bin/bash

echo "\n"

rsync -vaEn --delete ~/* /media/passport/back_up/;

echo -e "\nThe above folers/files will be affected.\nDo you want to continue? (y/n): ";
read choice;
yes="y"
no="n"

if [ $choice == $yes ]; then
    echo "\nUpdating"
    rsync -vaE --delete ~/* /media/passport/back_up/;

elif [ $choice == $no ]; then
echo "\nAborting"

else
    echo "\nResponse not recognised"

fi
```here is how it acts in the terminal```
mark@mark-desktop:~/Documents/scripts$ ./backup_home 
\n
sending incremental file list
Desktop/
Documents/
Documents/scripts/
Documents/scripts/backup_home
Downloads/
Music/
Pictures/
Videos/

sent 196893 bytes  received 1298 bytes  79276.40 bytes/sec
total size is 26982566300  speedup is 136144.26 (DRY RUN)

The above folers/files will be affected.
Do you want to continue? (y/n): 
n
\nAborting

```What on earth is going on with those escape characters, its printing \n instead of a newline, how is that even possible, the newline character is working okay on the line "the above files and folders will be affected" but at the top and before aborting \n is printed, i must be overlooking something blindingly obvious now, Aaah help?

Also the -e option for echo should leave off the new line and display the end of the question as "continue? (y/n): n" but it prints on a new line, 

come on what have i missed, im ready to slap myself when im told ive missed something stupid

---

### Post by CaptainMark on 2011-03-10
Thanks for all the help, ive finally finished, im quite proud of it seen as two days ago the only bash scripts id written were about two lines long for playing banshee on login :P  heres the finished product, im quite interested on getting feedback on how my coding is and how you would change it etc. ```
#!/bin/bash
# mark skinner
# created 08/03/2011
# last modified 10/03/2011

echo 'Finding Passport'
pass=`ls /media | grep passport | wc -l`
if [ $pass == 0 ]; then
    echo -e 'Passport not mounted.\nExiting' && sleep 4 && exit
fi

echo 'Updating new files'
rsync -aE /home/mark/ /media/passport/mark/
echo 'New files copied.'

echo 'Isolating hidden files'
IFS=$'\n'
for file in `rsync -avn --delete /home/mark/ /media/passport/mark/ | grep deleting | sed "s:deleting :/media/passport/mark/:g" | grep -F /.`
do
rm -r $file
done
echo 'Hidden files synced.'

num_files=`rsync -avn --delete /home/mark/ /media/passport/mark/ | grep deleting | sed 's/deleting / /' | wc -l`
if [ $num_files != 0 ]; then
    echo -e '\nThe following files/folders will be deleted:'
    rsync -avn --delete /home/mark/ /media/passport/mark/ | grep deleting | sed 's/deleting / /'
    
    echo -en '\nDo you want these files to be erased? (y/n): '
    read choice1;
    yes='y'
    no='n'
    
    if [ $choice1 = $yes ]; then
        echo -e 'Please wait'
        echo -n '5 ' && sleep 1
        echo -n '4 ' && sleep 1
        echo -n '3 ' && sleep 1
        echo -n '2 ' && sleep 1
        echo '1' && sleep 1
        
        echo -en '\nAre you sure you want to delete? (y/n): '
        read choice2
        
        if [ $choice2 = $yes ]; then
            echo ''
            rsync -av --delete /home/mark/ /media/passport/mark/ | grep deleting | sed 's/deleting/Deleting - /'
            echo $num_files ' deleted'
        else 
            echo 'No files deleted'
        fi
    
    else
        
        echo -en 'Would you like to delete interactivly? (y/n): '
        read inter
        
        if [ $inter == $yes ]; then
            echo -e 'Interactive Removal\n:'
            
            IFS=$'\n'
            for file in `rsync -avn --delete /home/mark/ /media/passport/mark/ | grep deleting | sed 's:deleting :/media/passport/mark/:g'`
            do
                echo -n 'Remove: ' $file ' (y/n)? '
                read response
                if [ $response == $yes ]; then
                    rm -r $file
                else
                    echo 'File not deleted'
                fi
            done
            unset IFS
            

        else
            echo 'No files deleted'
            
        fi
    fi 
else
    echo -e 'No files to delete'
    
fi

echo -e '\nExiting.' && sleep 4
    
    
```I isolated and synch the hidden files seperately and not interactivly because otherwise id get loads and loads of files listed in the delete list when i only need the important ones
EDIT: not to say hidden files arent important obviously but i mean they are not irreplaceable data

---

