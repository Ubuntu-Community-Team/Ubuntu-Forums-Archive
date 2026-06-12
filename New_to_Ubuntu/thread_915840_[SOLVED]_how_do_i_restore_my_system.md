---
title: "[SOLVED] how do i restore my system?"
date: 2008-09-10
forum: New to Ubuntu
---

### Post by ejv on 2008-09-10
Hi

is there  a way to restore the system as it was, for example, 5 hours ago?

I was following an old manual (one year old) trying to learn to independize my /home in a new partition and now the system won't boot anymore. i created a new /home where i was supposed to copy the original one and i edited fstab so that it would boot from the newly created home...but it went all wrong.  so now i'm working from the live cd.

It's only a week since i downloaded ubuntu; i'm really enjoying but i've got very little idea of what i'm doing!

Thanks

ejv

---

### Post by philinux on 2008-09-10
The answer to the question is no.

I guess you were following psychocats.

To be honest if your system is that new and you've nothing of importance or it's backed up, I would reinstall. Choose manual partition and set a separate /home partition from the word go. You will be back up and running within an hour.

---

### Post by yragrelluf on 2008-09-10
DONT PUT HOME ON ITS OWN PARTITION!!!!!!! you should reinstall, and make a separate fat32 partition to store your pics and music or whatever, and you can have it mount at startup. Even if home is on its own partition, when you reinstall, it will get wiped out, thats why you should make the fat32, because it can be shared with any OS, and when you reinstall, all your files will be intact. Trust me on this, I learned the hard way. Now I have windows xp on a 30gb part., ubuntu on a 30gb part., and 3gb swap space, and a 100gb fat32 shared part. with all my documents.

---

### Post by bumanie on 2008-09-10
Personally, I disagree with your setup. It is not wrong, but FAT32 has limitations re file sizes etc. I have a separate /home and it keeps data safe if something happens to / On a few occassions, i hve reinstalled to / and data in /home has always been in tact. Also with ntfs-3g and the ability to read/write to ntfs, there is no real need for a separate data partition when one has a separate /home - however one can set up their computer however they wish. Having a separate /home does keep data safe, it's unfortunate you had trouble with this setup previously.
To answer the original question, unless you have backed up, there is no equivalent of system restore.

---

### Post by yragrelluf on 2008-09-10
OK then, how do you reinstall ubuntu without affecting the separate /home partition? what file size limits do you speak of? fat32 is the only format Ive been able to share with windows and ubuntu. ubuntu can read and write to the windows partition, but windows cant access ubuntu partition.

---

### Post by hyper_ch on 2008-09-10
yragrelluf:

(1) linux can read/write to ntfs
(2) windows can read/write to ext3
(3) that makes fat32 somewhat oboslete

And you reinstall with your /home partition using manual partitioning and mount the /home partition as /home and don't select the option to overwrite that partition.

---

### Post by philinux on 2008-09-10
The OP makes no mention of windows or dual booting.

When you reinstall as hyper says you just tell the installer not to format /home which is the default in any case.

---

### Post by insane_alien on 2008-09-10
using FAT32 these days is like using a teaspoon to bail water out of a ship when you have multiple high capacity bilgepumps.

and a seperate /home partition is always a good idea. it allows you to reinstall or install other linuxes without having to format your data.

if you need sharing you can set up a partition to do that as well. i'd recommend ntfs as this prevents windows from seeing your OS partition so if it gets a viruse it won't mess with your ubuntu.

---

### Post by hyper_ch on 2008-09-10
a seperate home is generally a good idea... but not always ;)

---

### Post by philinux on 2008-09-10
I seem to remember reading that in Intrepid +1 they are looking at ways to preserve home on a reinstall. As hyper implies it's really up to the individual what they go for. There is no wrong or right.

---

### Post by tarps87 on 2008-09-10
I maybe wrong but I did not think Ubuntu boots from the /home partition. Before reinstalling it might be an idea to describe what you mean by it won't boot i.e. any error messages, strange behaviour

---

### Post by bumanie on 2008-09-10
I indicated in my original post that FAT 32 data partition is not necessarily wrong, but superceded these days due to its limitations. FAT is used on most usb sticks, but rarely used otherwise. As philinux has said choose manual at the partitioning stage and the separate /home partition will not be formatted unless you direct it to be. A separate /home can be placed on a different hard drive, / if one wishes. Saying all this reminds me that one of the reasons I use linux is to have a choice to set my system up how I like it, which is difficult to do with some other monolithic-structured OSes - so if you like having a FAT 32 data partition, use it; but there are better ways.

---

### Post by yragrelluf on 2008-09-10
Then why cant windows recognize my ubuntu partition if it can supposedly read/write ext3? Is there something wrong with my setup? I use the fat32 because I dont want music and pics and stuff on both drives, I like them to get along and share.

---

### Post by hyper_ch on 2008-09-10
> **yragrelluf said:**
> Then why cant windows recognize my ubuntu partition if it can supposedly read/write ext3?

because you need to install drivers for it.

and it's not supposedly ;) it is real ;)

---

### Post by tarps87 on 2008-09-10
Search for ext3 on windows, you have to add it into the windows os. I have never used it as I don't like the idea of windows having access to my Linux partitions

Edit: got beaten to it
heres a link to a viewer, it runs in read only mode
[http://www.diskinternals.com/linux-reader/](http://www.diskinternals.com/linux-reader/)

---

### Post by bmwman on 2008-09-10
> **yragrelluf said:**
> DONT PUT HOME ON ITS OWN PARTITION!!!!!!! you should reinstall, and make a separate fat32 partition to store your pics and music or whatever, and you can have it mount at startup. Even if home is on its own partition, when you reinstall, it will get wiped out, thats why you should make the fat32, because it can be shared with any OS, and when you reinstall, all your files will be intact. Trust me on this, I learned the hard way. Now I have windows xp on a 30gb part., ubuntu on a 30gb part., and 3gb swap space, and a 100gb fat32 shared part. with all my documents.

It will not format the separate partition unless you use the automatic (guided) partitioning. I've done it at least 10 times and always use Manual. I have a 500GB HDD which is EXT3 file system and all my movies, pictures, music, etc. it's all on there. When you reinstall and set your partitions, select the SWAP, select the Root partition and click on the checkbox to format it. Next you set your other partition as /home but make sure format is not checked and also select the file system that's currently on. Ex if it's fat32 you select fat32, ext3 - select ext3.

Bottom line, if you don't know exactly what you're doing, better don't risk losing all your stuff.

---

### Post by yragrelluf on 2008-09-10
So is there a way that I could change my fat32 over to /home without reinstalling anything, as I really like my current OS's config?

---

### Post by hyper_ch on 2008-09-10
you can't use a fat32 partition as /home

---

### Post by bmwman on 2008-09-10
I haven't tried it with Fat32 and it may not work. I haven't used Fat32 since Win98 :). It's a terrible file system and it gets so much errors, together with all the other limitations for file names/size, permissions, etc. I would recommend to at least convert it to NTFS if you're dual booting with XP but then don't put the /home on there.

---

### Post by ejv on 2008-09-10
Hello

Thanks for all your advices.  i just reinstalled everything and also solved some other minor problems i'd already caused...

i'm still interested in a step by step way of independizing my home, so any link or advice is welcome.

Maybe from now on i'll just go a bit slower.

And now a formal question:  should i mark this thread as solved?

Thanks once more

ejv

---

### Post by yragrelluf on 2008-09-10
So what was your final outcome? How did you partition?:guitar:

---

### Post by ejv on 2008-09-12
I just did the guided partition from the installation cd.  I needed it working back again fast, and was not sure about how to create an extra partition for my home.

---

