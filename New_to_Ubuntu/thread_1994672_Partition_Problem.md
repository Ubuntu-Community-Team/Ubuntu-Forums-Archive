---
title: "Partition Problem"
date: 2012-06-03
forum: New to Ubuntu
---

### Post by Diggory on 2012-06-03
Hi all.

This one maybe obvious if you are in the know.

I used GParted to reformat an NTFS partition to Ext4 (using the "Format To" option).
The format completed okay and I then added a Label to partition so I  could identify more easily (my previous NTFS label was lost).
When I mounted the partition I found it was owned by Root and I have no  permission to use usefully. I thought okay, I can use properties to  change permission but because I don't own it will not play. 

How do I change this access permission.

Thanks D.

---

### Post by shafi.dude99 on 2012-06-03
try running this command :

sudo chmod 777 /media/"your drivename"

---

### Post by mapes12 on 2012-06-03
Boot from a live CD. Applications>Terminal ```
gksu nautilus
```should launch Nautilus as Root. Right click the partition>Properties>Permissions. Then see if you can change it the GUI way.

EDIT: If you already have Ubu on another partition you don't need to boot from a live CD. Just launch Nautilus as Root and have a go from there.

---

### Post by Diggory on 2012-06-03
Many thanks for the two options

What does; sudo chmod 777 /media/"your drivename", actually do.  

& yes, Ubu is on a separate partition, the one I am trying to sort is a second data partition.

Not sure I understand the launch Nautilus as Root - what will this do.

Thanks D

---

### Post by shafi.dude99 on 2012-06-03
> **Diggory said:**
> Many thanks for the two options

What does; sudo chmod 777 /media/"your drivename", actually do.  

& yes, Ubu is on a separate partition, the one I am trying to sort is a second data partition.

Not sure I understand the launch Nautilus as Root - what will this do.

Thanks D

chmod will change the permission for accessing drive.... (777) stands for every user can read write and execute..... for more detail u can read man page

write in terminal
man chmod (it will tell everything about it)

---

### Post by shafi.dude99 on 2012-06-03
> **Diggory said:**
> Many thanks for the two options

What does; sudo chmod 777 /media/"your drivename", actually do.  

& yes, Ubu is on a separate partition, the one I am trying to sort is a second data partition.

Not sure I understand the launch Nautilus as Root - what will this do.

Thanks D

is your problem solved

---

### Post by Diggory on 2012-06-03
Hi - I am not at my Ubu machine at the mo.
I would like to try the gksu nautilus option.
Could someone talk me through simple steps.

Thanks D

---

### Post by Diggory on 2012-06-04
Dear All,

I have just done a search for the two options above and probably confused myself.
*(but I dont like implementing commands unless I have some idea what they are doing)*

Seems some folk say the 777 command should be avoided 
& others say that running graphical interface as Root is also not advised as it creates other Root owned files.

Some advice much appreciated. Thanks D.

---

### Post by mapes12 on 2012-06-04
> running graphical interface as Root is also not advised as it creates other Root owned filesOnly if you create them while you're running Nautilus as Root. Once you have completed the task then close down Nautilus and you will be back to your normal user account. 

One thing about running Nautilus as Root is to be careful deleting anything. You need to press the shift key at the same time as the delete key to permanently delete. If you don't then whatever it is you're deleting gets moved to Root's trash bin without telling you.

---

### Post by Morbius1 on 2012-06-04
> **Diggory said:**
> Seems some folk say the 777 command should be avoided 
Then don't do it. A new ext4 partition will automatically mount with owner=root and permissions of 755. Root can do anything it wants to it (7) and everyone else can only read (5). Simply change ownership:
```
sudo chown Diggory /path/to/mounted/partition
```*Just make sure the partition is mounted first since changing ownership / permissions on a folder before a partition is mounted will do nothing.*
> 
& others say that running graphical interface as Root is also not advised as it creates other Root owned files. There's 2 issues there:
"sudo nautilus" should be avoided and will eventually mess you up.
"gksu nautilus" is the preferred way.

[COLOR=Blue]*Note: an interesting comment came about in a bug report recently about root and gedit that you might find disturbing and / or humorous:  *[/COLOR][https://bugs.launchpad.net/ubuntu/+s...it/+bug/838404]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404")

> Quote:
                                                 [Sam_ (and-sam)]("https://launchpad.net/%7Eand-sam")             wrote             on 2011-10-09:                                                            [ #2]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/2")                                                               Quote comment from upstream developer:
< You shouldn't start GNOME programmes with elevated privileges, it's not
supported. In any case, not a gnome-terminal bug. >

              
                                                                                                                                      [Sean Fitzpatrick (sean-fitzpatrick)]("https://launchpad.net/%7Esean-fitzpatrick")             wrote             on 2011-10-09:                                                            [ #3]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/3")                                   
                            I see.  So does  that make the official  GNOME position "editing system files should be  done with nano or  similar" or "system files?  why would a user want to  edit a system  file?"

              
     
                                                                                                                                [Sam_ (and-sam)]("https://launchpad.net/%7Eand-sam")             wrote             on 2011-10-09:                                                            [ #4]("https://bugs.launchpad.net/ubuntu/+source/gedit/+bug/838404/comments/4")                                   
                            Yep, from my understanding they don't agree with running graphical apps as root. [Bug #805682]("https://bugs.launchpad.net/bugs/805682")When you open up say "gksu gedit /etc/fstab" a secondary tab is opened up titled "untitled document 1" . The official response from Gnome is don't do that. My guess is that they don't know why that's happening since all the Gnome2 developers who never had this problem were all fired to make way for the Gnome3 developers.

---

