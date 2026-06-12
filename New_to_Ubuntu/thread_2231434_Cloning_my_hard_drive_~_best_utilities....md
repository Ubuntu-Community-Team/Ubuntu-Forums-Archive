---
title: "Cloning my hard drive ~ best utilities..."
date: 2014-06-25
forum: New to Ubuntu
---

### Post by amzolt on 2014-06-25
I have 14.04 and am nearly done loading it with all the programs I need.

I want to create a clone on my second hard disk --- Ubuntu is on D: drive, clone will be on C: drive...

Some one recommended FSArchiver...

Any comments on that utility?

Any other recommendations??

---

### Post by Quarkrad on 2014-06-25
I would recommend Clonezilla.  I didn't like it myself when I first tried it but many experts/experienced users on this forum recommended it and after 'keeping at it' I saw how good it was.  I would certainly suggest Clonezilla is worth the effort to learn it.  Once you are familiar with the layout it is pretty easy and has some really sophisticated features that become valuable later on.

---

### Post by amzolt on 2014-06-25
> **Quarkrad said:**
> I would recommend Clonezilla.  I didn't like it myself when I first tried it but many experts/experienced users on this forum recommended it and after 'keeping at it' I saw how good it was.  I would certainly suggest Clonezilla is worth the effort to learn it.  Once you are familiar with the layout it is pretty easy and has some really sophisticated features that become valuable later on.

I'll look into it Quarkrad---however, is FSArchiver actually a utility that "Clones"??

---

### Post by oldfred on 2014-06-25
Do not understand c: drive and d: drive. Those are Windows definitions and can be either two partitions on one drive or two physical drives.

You cannot keep a true clone mounted, system does not allow duplicate UUIDs. So you will have major issues if you want to restore clone and have it also working on same computer. You then have to change UUIDs, edit fstab and reinstall grub2. Perhaps a few other internal settings. Clone is best to restore to same partitions so no issue on duplicates.

---

### Post by amzolt on 2014-06-25
> **oldfred said:**
> Do not understand c: drive and d: drive.
Sorry, there are two separate hard drives
> **oldfred said:**
> You cannot keep a true clone mounted, system does not allow duplicate UUIDs.
I don't understand "keep a true clone mounted"... or, "duplicate UUIDs"....
> **oldfred said:**
> Clone is best to restore to same partitions so no issue on duplicates.
Can a clone on one drive be restored to the other drive??

---

### Post by cwmoser on 2014-06-25
I second Clonzilla.
Used it for several years cloning both Linux and Windows HD's.

---

### Post by amzolt on 2014-06-25
thanks, Carl.

---

### Post by oldfred on 2014-06-25
Are both drives, original and clone going to be plugged in when you reboot? If so they you will not know which drive is actually used.

Every partition has a unique UUID and it is used by grub & fstab for knowing which partition to use to boot and mount as root & other partition. But if the same you do not know which is really used.

to see UUIDs, they must be unique and most clone tools do not change them as then clone will not work unless grub is reinstalled and fstab edited.
       sudo blkid -c /dev/null -o list

---

### Post by amzolt on 2014-06-25
> **oldfred said:**
> Are both drives, original and clone going to be plugged in when you reboot? If so they you will not know which drive is actually used.

Every partition has a unique UUID and it is used by grub & fstab for knowing which partition to use to boot and mount as root & other partition. But if the same you do not know which is really used.

to see UUIDs, they must be unique and most clone tools do not change them as then clone will not work unless grub is reinstalled and fstab edited.
       sudo blkid -c /dev/null -o list

Well, thanks oldfred, but I'm pretty sure I posted this in Absolute Beginners Section.........

Could you explain what you said but kinda gear it toward a "beginner"??

---

### Post by oldfred on 2014-06-26
Post this so you can see your UUIDs.
sudo blkid -c /dev/null -o list

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

An UUID is just a unique code that is assigned to every partition when it is formatted. System does not allow duplicates. But the purpose of a clone is an exact duplicate. That is ok if used to restore your system or to install into a totally different computer. But you cannot use on another drive in the same computer without making a lot of internal changes.

---

### Post by amzolt on 2014-06-26
> **oldfred said:**
> Post this so you can see your UUIDs.
sudo blkid -c /dev/null -o list

[http://en.wikipedia.org/wiki/UUID](http://en.wikipedia.org/wiki/UUID)

An UUID is just a unique code that is assigned to every partition when it is formatted. System does not allow duplicates. But the purpose of a clone is an exact duplicate. That is ok if used to restore your system or to install into a totally different computer. But you cannot use on another drive in the same computer without making a lot of internal changes.

Thanks for making that a bit more understandable :-)

So...

If I have my Ubuntu on one drive and the Clone to the other drive, can I restore it back from that other drive???

---

### Post by monkeybrain20122 on 2014-06-26
If you clone a Linux system I recommend fsarchiver * Clonezilla is not so flexible, a show stopper for me is that it requires the target to restore to to be as big or bigger than the original partition even if the original is mostly empty.  So what if my hard drive get busted and I want to restore to a new hd or another computer with a smaller drive?

* doesn't work with gpt,

---

### Post by monkeybrain20122 on 2014-06-26
> **amzolt said:**
> Thanks for making that a bit more understandable :-)

So...

If I have my Ubuntu on one drive and the Clone to the other drive, can I restore it back from that other drive???

lf you want to boot the clone off the same computer you would need to change the uuids for one  (either the original or the clone)and then edit /boot/grub/grub.cfg of the one whose uuid you have changed and change the uuid accordingly. If you have a separate /home you would need to edit /etc/fstab as well. So, say you are in the original Ubuntu, attach the drive with the clone, use gparted to change the uuids of the partitions of the clone. Then edit the files mentioned above, and be careful you edit the files for the clone, not the systems that you are running on. It gets a bit confusing (the path to the files should begin with /media..)

---

### Post by amzolt on 2014-06-26
Thanks for both comments, monkeybrain :-)

---

### Post by varunendra on 2014-06-26
> **amzolt said:**
> I have 14.04 and am nearly done loading it with all the programs I need...

You are already getting best kind of advice from the most experienced minds, oldfred being 'The Master & Commander' of partition & booting matters. I would just like to add a possibly useful idea in case you didn't already know about it - If you have installed ALL the required applications in one go (no 'Updates' in-between), also try 'AptOnCD' to create an offline repository of the downloaded packages. Once you have the aptoncd disk (DVD or CD(s), as you like), you can use it as an offline repository to install the same (all or selected) applications on other computers which have the same version of Ubuntu installed, without internet connection.

Take a look at these page if this sounds interesting :
[https://wiki.ubuntu.com/APTonCD](https://wiki.ubuntu.com/APTonCD)
[https://help.ubuntu.com/community/APTonCD](https://help.ubuntu.com/community/APTonCD)

For cloning, I personally like Clonezilla, despite the problem that monkeybrain20122 mentioned. I rarely clone/restore whole disks, most often I only clone OS partitions and I keep their sizes reasonably small, so that problem never bothered me.

Two near-perfect tutorials on using clonezilla :
[http://www.geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/](http://www.geekyprojects.com/cloning/how-to-use-clonezilla-tutorial/)
[http://dedoimedo.com/computers/clonezilla.html](http://dedoimedo.com/computers/clonezilla.html)

---

### Post by amzolt on 2014-06-26
Well, I appreciate all the responses but now I'm quite confused---all the terms and different perspectives...

---

### Post by monkeybrain20122 on 2014-06-26
BTW, a nice feature of fsarchiver is that it can do live cloning, so you don't need to stop doing whatever you are doing (excpet modifying the system in significant ways like syncing with dropbox or installing software/updates)

If you have a separate /home I would just clone the / partition and a 'shell' for /home (with no or just minimal user data, in fsarchiver you can use the --exclude= option) in case you need to restore the whole system (say hd fails). This way you can just clone / regularly and typically it is quite small. There are other ways to backup data, you don't need to clone those.

There is also an easy to use, point and click gui, [http://sourceforge.net/projects/qt4-fsarchiver/](http://sourceforge.net/projects/qt4-fsarchiver/)

but it is not as flexible as the cli version as you can't exclude directories, but it is quite adequate if you use it only to clone the / partition regularly(and create a shell for /home before it is populated with a lot of data) I don't use it myself, but install it for new users I set up Ubuntu for as an easy system backup solution.

To restore you need fsarchiver (or qt4-fsarchiver) in an external medium. A live usb with persistence with (qt4) fsarchiver installed would work. I won't recommend the live iso for qt4-fsarchiver from sourceforge as gparted in it is kind of freaky and if you unmount a partition with it it may damage your data (Edited: I see they have updated the live ISO, may be the problem with gparted is fixed, the live iso based on Precise is no good)

---

### Post by amzolt on 2014-06-26
> **monkeybrain20122 said:**
> BTW, a nice feature of fsarchiver is that it can do live cloning, so you don't need to stop doing whatever you are doing (excpet modifying the system in significant ways like syncing with dropbox or installing software/updates)

If you have a separate /home I would just clone the / partition and a 'shell' for /home (with no or just minimal user data, in fsarchiver you can use the --exclude= option) in case you need to restore the whole system (say hd fails). This way you can just clone / regularly and typically it is quite small. There are other ways to backup data, you don't need to clone those.

There is also an easy to use, point and click gui, [http://sourceforge.net/projects/qt4-fsarchiver/](http://sourceforge.net/projects/qt4-fsarchiver/)

but it is not as flexible as the cli version as you can't exclude directories, but it is quite adequate if you use it only to clone the / partition regularly(and create a shell for /home before it is populated with a lot of data) I don't use it myself, but install it for new users I set up Ubuntu for as an easy system backup solution.

To restore you need fsarchiver (or qt4-fsarchiver) in an external medium. A live usb with persistence with (qt4) fsarchiver installed would work. I won't recommend the live iso for qt4-fsarchiver from sourceforge as gparted in it is kind of freaky and if you unmount a partition with it it may damage your data (Edited: I see they have updated the live ISO, may be the problem with gparted is fixed, the live iso based on Precise is no good)

Thank you for all that information---however, I'm having "tech" overload and am completely confused... Sorry...

---

### Post by Quarkrad on 2014-06-26
A 'left of field' thought.  When I first migrated to Linux/Ubuntu I looked into Cloning from my experience with Windows.  However, I have found Ubuntu is rock solid compared to Windoze and I have never needed to restore from a Clone.  What I now do on my two HD set up is to _automatically_ backup all my personal data and **/home** (**/home** also contains things like web browser and email profiles, and many other parameters) each time I power down my machine.  I have a separate **/** partition and **/home** partition so if the worst happened I could rebuild very quickly.  Maybe not as quick as a clone reinstall but re building the system (/) is fairly quick.  Just a thought, with my automatic backup set up I do not have to do anything but switch on, use the pc and then switch off - with the knowledge that everything is backup up onto my backup HD in the background.  (I don't want to get too complicated but I also have another partition for my personal data, as well as **/home**.  Of course, you can have all your personal data in **/home**, which is the default).

---

### Post by amzolt on 2014-06-26
> **Quarkrad said:**
> A 'left of field' thought.  When I first migrated to Linux/Ubuntu I looked into Cloning from my experience with Windows.  However, I have found Ubuntu is rock solid compared to Windoze and I have never needed to restore from a Clone.  What I now do on my two HD set up is to _automatically_ backup all my personal data and **/home** (**/home** also contains things like web browser and email profiles, and many other parameters) each time I power down my machine.  I have a separate **/** partition and **/home** partition so if the worst happened I could rebuild very quickly.  Maybe not as quick as a clone reinstall but re building the system (/) is fairly quick.  Just a thought, with my automatic backup set up I do not have to do anything but switch on, use the pc and then switch off - with the knowledge that everything is backup up onto my backup HD in the background.

Thank you, Quarkrad---I almost understand what you're saying and it sounds good :-)

I'm going to have to copy out this thread and let the techie at the shop interpret it for me...

---

### Post by Quarkrad on 2014-06-26
It comes to your backup methodology.   We are talking here about either cloning either the whole HD (or just specific partitions - but probably the whole drive) and then having the ability to restore from the backed up clone on your 2nd HD or, as I do, backup specific partitions onto your 2nd HD.  I use to clone somewhat in my Windows days more because Windoze clashes rather than hardware/drive failures - with Ubuntu, it has never crashed so cloning the whole drive is a bit over the top.  I find just backing up my important partitions is adequate for my needs.

---

### Post by cwmoser on 2014-06-26
For your newly cloned Hard Drive, take note of these commands:

Output all UUIDs associated with /dev/sd?? notations:
**$  sudo blkid**  or  **sudo blkid -o list**

Generate a new unique UUID that you can assign to your cloned drive:
**$  uuidgen**
bb380f29-34f1-4853-96d6-62cc5fad01f9  <-- Example output

Assign the above generated UUID to your cloned HD (copy and paste the output).
Note:  you will use your /dev/sd?? and your UUID:
**$  sudo  tune2fs  /dev/sdb4  bb380f29-34f1-4853-96d6-62cc5fad01f9**

When done, your newly cloned hard drive will have its own unique UUID.

The hard part is to discern what is the /dev/sd?? of your cloned drive.
If its not readily obvious, look for the two drives with the same UUID and 
determine which of the two is the cloned drive.  Most likely you are cloning
a drive with a / or /home mounting in which case the cloned drive is the one
without the / or /home mounting.

---

### Post by amzolt on 2014-06-26
OK -- will save your ideas, Quarkrad and cwmoser, and let my techie at the shop interpret it for me...

---

### Post by JohnPta on 2014-06-28
What about "RAID 1"?? that could also do theh job.

---

### Post by oldfred on 2014-06-28
RAID is not for backup, but for reliability to keep system going. If you delete a file it is gone in both images where a backup has an older copy.

       discussion of alternatives/strategy backups
[https://help.ubuntu.com/community/BackupYourSystem](https://help.ubuntu.com/community/BackupYourSystem)

If you install your own system you are the system admin
Sysadmins: Everything they told you about backup WAS A LIE
[http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/](http://www.theregister.co.uk/2013/07/12/storagebod_monomyth/)

---

### Post by kevdog on 2014-06-28
I kind of skimmed this thread and I can only tell you my own experience.  I have only once cloned my hard-drive -- the old one was full and I upgraded to a much larger hard-drive.  I wanted the same partition structure as on the old drive, but needed each partition bigger.  I used clonezilla to actually make the partitions on the new drive.  Unfortunately trying to clone one partition to the other wasn't so helpful and I can't remember exactly but I kept getting a lot of errors.  In the end, I simply used the dd command to direct copy byte by byte each partition to the other.  The hard part of the entire process was the /boot partition which was very tricky.  I had to reinstall grub and update grub.  I also remember updating the /etc/fstab file in order to reflect the UUIDs of the new partitions.  In the end the process took me days to figure out because I had no idea what I was doing -- although I found the Arch wiki really helpful in this regards although I had to read and try stuff about 50 times before I really understood what was being said.  The actual process of doing all the copying and /boot partition was probably only 2 hours -- the remainder reading, looking, etc.

---

### Post by Vladlenin5000 on 2014-06-28
[**[COLOR=#000000]kevdog[/COLOR]**]("http://ubuntuforums.org/member.php?u=257393"), Clonezilla works fine for your original purpose, even in "beginner mode". There are better ways to do that but Clonezilla in perfectly fine to clone an entire drive to a new bigger one. Then all you have to do is use gparted to extend the size of the cloned partitions in the new drive. Of course, cloning and entire drive also clone the swap partition and you'll have to delete it from the new drive in order to be able to increase the size of the partitions immediately to its "left", usually / or /home; create the new swap partition with the size you want at the end of the drive. Done.

---

### Post by folgers on 2014-06-28
The original Free version Helix (2009R1) is still available for download.  I use it frequently because I like to keep a backup of my harddrive. You will need to perform an ISO burn to CD.  It boots live.  In my case I clone to a removable USB for storage.  The clone program on the distro is called adepto.  The internal drive is usually called sda.  Be very careful that you clone in the correct direction.  On all these types of software you must be carefull of the what is the source and what is the destination, otherwise you know what could happen.

[http://www.e-fense.com/products.php](http://www.e-fense.com/products.php)

---

### Post by varunendra on 2014-06-29
> **folgers said:**
> ....otherwise you know what could happen...

I doubt they do, but they sure will once it happens :p

Given how soon the OP got 'Tek-Overloaded' and started requesting 'please no more', I also doubt there is much point in bumping this thread.

Cloning/Restoring a drive/partition requires above average understanding of drive structures and related stuff, and no tool or suggestion (except - "go see a pro") is going to make it easier. :)

---

