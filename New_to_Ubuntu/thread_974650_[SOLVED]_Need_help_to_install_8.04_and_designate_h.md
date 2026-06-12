---
title: "[SOLVED] Need help to install 8.04 and designate /home on a seperate partition."
date: 2008-11-07
forum: New to Ubuntu
---

### Post by tahitiwibble on 2008-11-07
I am finally going to install 8.04 and use a separate partition for /home.

I have copied my current /home folder to a second internal HD and was going to;

1/ Boot from a live 8.04 CD
2/ Resize my original sole partition to 20GB to receive 8.04 and create a new partition for my /home folder
3/ Install 8.04
4/ Copy my backed up /home folder to the new partition
5/ Designate new /home folder 
6/ Reinstall currently used programs [http://ubuntuforums.org/showthread.php?t=261366](http://ubuntuforums.org/showthread.php?t=261366)

Is my plan flawed?

My problem is with designating the new /home. Can someone please explain to me what to do in simple terms.

Also, what are the unforeseen problems I may run into with my rather simplistic approach? Permissions? for example. I have checked my internet connection with the live CD and it worked perfectly but the thought of not being able to immediately use my Firefox bookmarks in case of trouble with permissions scares me.

---

### Post by Idefix82 on 2008-11-07
May I suggest the following alternative approach:
1. Create a new Ext3 partition with GParted and copy the content of your /home folder there.
2. Install 8.04 from the Live CD. During the installation process, pick the manual install option. You will be asked which partitions you want to create and what the mount points should be. You will want to create one partition for /, one for SWAP. In the same step you can select the already existing partition with your /home content and tell the installer to mount it as /home. Make sure you untick the "format" box so that the content of the partition is not erased.

Of course, you also want to create the same user name for you as before, so that the right subfolder of /home is used for your account.

Feel free to ask if that was unclear.

---

### Post by tahitiwibble on 2008-11-07
> **Idefix82 said:**
> May I suggest the following alternative approach:
1. Create a new Ext3 partition with GParted and copy the content of your /home folder there.
2. Install 8.04 from the Live CD. During the installation process, pick the manual install option. You will be asked which partitions you want to create and what the mount points should be. [COLOR="Blue"]You will want to create one partition for /, one for SWAP. In the same step you can select the already existing partition with your /home content and tell the installer to mount it as /home.[/COLOR] Make sure you untick the "format" box so that the content of the partition is not erased.

Of course, you also want to create the same user name for you as before, so that the right subfolder of /home is used for your account.

Feel free to ask if that was unclear.

Is the manner in which to accomplish the steps highlighted in blue obvious during "installation"? Especially how to tell the installer to mount the new /home folder as "/home".

Your procedure does seem to be simpler than mine.

I imagine step 6 to remain unchanged.

---

### Post by Idefix82 on 2008-11-07
Yes. You will see the different partitions that already exist, as well as unallocated space. You can delete partitions, create new partitions and use existing ones. You will be able to tell the installer to "use" your existing partition and you will be asked to specify a mount point for it, which you should choose to be /home. For each existing partition which you use you can specify whether you want to format it. Of course you won't want to format the /home partition.

And you are right, step 6 will remain unchanged.

---

### Post by tahitiwibble on 2008-11-07
> **Idefix82 said:**
> Yes. You will see the different partitions that already exist, as well as unallocated space. You can delete partitions, create new partitions and use existing ones. You will be able to tell the installer to "use" your existing partition [COLOR="Blue"](which I had previously created)[/COLOR] and you will be asked to specify a mount point for it, which you should choose to be /home [COLOR="Blue"](I am unsure as to how to specify a mount point and how to choose "/home". Will "/home" be a visible option at this stage in the process?)[/COLOR]. For each existing partition which you use you can specify whether you want to format it. Of course you won't want to format the /home partition.

And you are right, step 6 will remain unchanged.

Please forgive my slowness of wit.

---

### Post by Idefix82 on 2008-11-07
> **tahitiwibble said:**
> Please forgive my slowness of wit.

No worries.
You understood me correctly: you choose the partition which you created before in step 1 of my plan and which contains the data from your old home partition. You will recognise the partition by its size and by the fact that it will be formatted as Ext3.
If you tell the installer to use it, it will ask you what to mount it as. You tell it to mount it as /home. As far as I remember, you will have no way to avoid this question. When you choose the mount point, there will be a drop down list of suggestions, like /, /var, /etc, /tmp and among them will be /home. Of course, you can just type in any mount point, even if it's not in the list, but you won't need to do that.

---

### Post by tahitiwibble on 2008-11-07
A mouse click on a yellow ribbon does little to demonstrate my appreciation to you :-), but here goes. 

You've quieted an old man's wrenching guts down a tone or two. Thanks.

---

### Post by Idefix82 on 2008-11-07
No problem. Please report back whether it worked!

---

