---
title: "secure delete data purge ubuntu"
date: 2008-04-22
forum: New to Ubuntu
---

### Post by wenhui100 on 2008-04-22
Does anyone know how to securely delete data from harddrive of ubuntu as OS. completely wipe which even the forensics can't even retrive. i have given up windows cos some people told me that linux is much more secure in sensitive datas. thanks people ...

---

### Post by Moop on 2008-04-22
[http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

---

### Post by nicedude on 2008-04-22
Why what are worried someones going to find. I gotta say you asked that kinda strangely. If you tell me its because your affraid of getting busted for something I Dont care about I will tell you.

---

### Post by wenhui100 on 2008-04-22
nicedude, well ya ... issn't that obvious. i have got sensitive data which i don't want others to know about .. u don't have to tell me if u don't want to .. i love linux because of the spirits of sharing not to question others oh y u want this and that for ..

---

### Post by wenhui100 on 2008-04-22
> **Moop said:**
> [http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php)

thanks man ..

---

### Post by scorp123 on 2008-04-22
> **wenhui100 said:**
>  completely wipe which even the forensics can't even retrive. That's difficult to achieve.

What I would suggest is that you make yourself familiar with harddrive encryption, or at least folder encryption. Please see the links below. The point here is that whatever is stored or deleted from those encrypted disks or folders is still encrypted and thus it's still impossible to decypher.

(I myself use this method: "encfs" ... It's "good enough" for what I need it.)

"HOWTO: Encrypted directory with EncFS"
[http://ubuntuforums.org/showthread.php?t=148600](http://ubuntuforums.org/showthread.php?t=148600)

"Using TrueCrypt on Ubuntu for Encryption"
[http://tombuntu.com/index.php/2007/09/03/using-truecrypt-on-ubuntu-for-encryption/](http://tombuntu.com/index.php/2007/09/03/using-truecrypt-on-ubuntu-for-encryption/)

"TrueCrypt With GUI On Ubuntu 7.10"
[http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10](http://www.howtoforge.com/truecrypt-with-gui-on-ubuntu-7.10)


Full disk encryption:

"Step-by-step: Encrypted Ubuntu 7.10"
[http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml](http://news.softpedia.com/news/Encrypted-Ubuntu-7-10-68383.shtml)


Then, there are other things you'd need to be aware of: There are important differences between the various filesystem types available on Linux. Some such as **ReiserFS** make it _very easy to retrieve data again_. **So if you value your privacy: Don't use ReiserFS!** Others such as **Ext3** make it far more difficult to retrieve deleted data again but I guess people working in computer forensics would still know how and might still have success by scanning the entire disk on a low-level and then retrieving chunk by chunk of whatever you deleted.

As far as making undelete operations very difficult is concerned, I'd say **XFS** takes the crown: Whenever you delete something from an XFS filesystem, XFS will automagically reassign the freed blocks to something else (whatever task might be in need of free blocks) and whatever just got deleted has a high chance of getting overwritten in the next second. Add to this that the XFS filesystem does know a "defrag" utility ("xfs_fsr" program from the "xfsdump" package) which technically isn't necessary (XFS will already do whatever it can to avoid fragmentation just like the other Linux filesystems too) but when executed will cause files to be rearranged on the disk, thus making it very likely that whatever just got deleted and whatever free space that generated will be overwritten in the next second with whatever is being re-arranged on the XFS disk. So it would be good to always keep a few double-layer DVD ISO images (8.5 GB size) around and then just copy them around on the XFS filesystem after you deleted something from there. Chances are that XFS will overwrite whatever you deleted with whatever large file you are copying around.

I know ... this is by no means a perfect guarantee, but it sure helps getting rid of old data fragments you don't want to ever to come back again.


As for actually deleting files: I'd suggest you install this utility from the repos: "wipe". So you'd type this into a terminal: ```
sudo apt-get install wipe
```

And then you should familiarize yourself with how it works and what it can do for you by reading its manual: ```
man wipe
``` [COLOR="Red"]Read it carefully.[/COLOR]

So to really achieve what you wanted, you'd have to:
- use full hardisk encryption
- use XFS as filesystem
- use "wipe" for secure file deletion and not any other method
- everytime after something got deleted make sure you copy and move large files around so any potentially remaining data blocks of the deleted file get overwritten again. 

In my opinion only this combo will help you achieve what you want and make it really hard for anyone to retrieve anything. 


I hope this helped.

---

### Post by scorp123 on 2008-04-22
> **Moop said:**
> [http://www.techthrob.com/tech/securedelete.php](http://www.techthrob.com/tech/securedelete.php) Nice overview ... BUT: There is one factual error on the page.

> Starting with ext3, Linux filesystems overwrite files with zeros when you delete them, rather than just marking the file as "free space."
 Sorry, but that just isn't true. Ext3 will overwrite the pointers in the superblocks (which point to the blocks which contain the actual data) with zeros, yes. That's why all the undelete utilities which used to work for Ext2 will no longer work with Ext3: Ext2 behaved as it says in the text: it just marked the pointers as being "deleted", but it didn't wipe them as Ext3 does. BUT: **Ext3 does not wipe the data contents themselves!** So while it will be very hard to get the filename back from a deleted file on an Ext3 filesystem, **getting the data back from Ext3 _is possible_ if you do a low-level search, byte by byte, chunk by chunk.** And that's precisely how they'd do that if your harddisk ever ended up in the hands of the forensics guys.

So the claim above that a standard delete operation on Ext3 will overwrite the complete file is false. Only the pointers in the superblocks get overwritten, but the data contents are still there and could still be retrieved. Details here:
[http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html](http://batleth.sapienti-sat.org/projects/FAQs/ext3-faq.html)

And here is a description how retrieving deleted files from Ext3 works:
[http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html](http://www.xs4all.nl/~carlo17/howto/undelete_ext3.html)

---

### Post by sayakb on 2008-04-22
Here is a file shredding script that you could add:
```
#!/bin/bash

if [[ -a /dev/urandom ]]; then
    randomizer=/dev/urandom;
elif [[ -a /dev/random ]]; then
    randomizer=/dev/random;
fi

echo $NAUTILUS_SCRIPT_SELECTED_URIS > ~/.gnome2/temp_shred_list

for file in $(cat ~/.gnome2/temp_shred_list); do

shortfile=$(echo $file | sed -e 's/\%20/\ /g' -e 's/.*\///g')

file_name=$(echo $file | sed -e 's/file:\/\///g' -e 's/\%20/\ /g')

zenity --question --title "Shredder" --text "Really shred $shortfile?"

if (( "$?" == 1 )) ; then
    exit
else
    if [[ $randomizer == "" ]]; then
        shred -u -z -n 50 "$file_name"
        if (( $? == 0 )); then
            zenity --info --text="$shortfile has been shred" --title "Success"
        else    zenity --info --text="$shortfile couldn't be shred" --title "Failure"
        fi
    else    shred -u -z -n 50 --random-source=$randomizer "$file_name"
        if (( $? == 0 )); then
            zenity --info --text="$shortfile has been shred" --title "Success"
        else    zenity --info --text="$shortfile couldn't be shred" --title "Failure"
        fi
    fi
fi;

done

rm -f ~/.gnome2/temp_shred_list
```

---

### Post by MongooseCage on 2008-04-22
[SIZE="2"][/SIZE]or howbout, formating your computer and then dumping more stuff on it from your external harddrive and then again format it. Do it about 7 times or so I think. 

[SIZE="1"]**Or if possible, simply burn it **[/SIZE]:twisted:

---

### Post by sayakb on 2008-04-22
> **MongooseCage said:**
> [SIZE=1]**Or if possible, simply burn it **[/SIZE]:twisted:

:-s

---

### Post by wenhui100 on 2008-04-22
cool . thanks for sharing .. good to be part of linux ..

---

### Post by wenhui100 on 2008-04-22
I came across this interesting link ... is there any other way to delete just one file without purging the whole hardisk ?? 

[http://www.sans.org/reading_room/whitepapers/forensics/2011.php](http://www.sans.org/reading_room/whitepapers/forensics/2011.php)

---

