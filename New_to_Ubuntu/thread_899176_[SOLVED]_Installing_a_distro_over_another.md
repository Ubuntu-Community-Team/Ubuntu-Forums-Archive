---
title: "[SOLVED] Installing a distro over another"
date: 2008-08-24
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-08-24
Now, I know this board is basically for Ubuntu questions, but I'm hoping someone will know about other distro's.

Ok, I installed Ubuntu a few days ago as a dual boot with XP(mainly because Ubuntu's partitioner was easier to use than Mints). After playing with Linux Mint for the past week or so on a live cd, I want to use this distro now, so I want to install it on the partition that my Ubuntu is on. And now that I've read up on it more, I feel more comfortable using Mints partitioner.

Now, I was asking about it somewhere else. And was told that when I run the Linux Mint live cd, pick Installation, and get to the partitioning part of the installer, I could just simply format the partition that Ubuntu is on and install Mint on it.

Here is a screenshot of what the Mint partitioner shows about my paritions:

[http://www.lookpic.com/getimg.php?img=partition.png](http://www.lookpic.com/getimg.php?img=partition.png)

As you can see I have a partition for Windows, one for Ubuntu, and one for Swap.

Now, when I get to the partitioning part of the Mint installer, I right-click on my Ubuntu partition, and hit Edit Partition. There is a box for Format Partition, but it won't allow me to tick it. Like it's unavailable for me. Here is a screen of what it shows.

[http://www.lookpic.com/getimg.php?img=edit.png](http://www.lookpic.com/getimg.php?img=edit.png)

Now, do I have to select an option from the Use As: box, so I'm able to tick the Format box? It's set on Do Not Use Partition by default. But i didn't want to miss with the other options and mess something up. The other options that Use As: box gives you are:


Ext3 Journaling File System
Ext2 File System
ReiserFS Journaling File System
JFS Journaling File System
XFS Journaling File System
FAT 16 File System
FAT 32 File System
Swap Area

If I choose any of those options besides Swap Area, then the Formatting box can then be ticked. So what option should I choose?

And if I can't get the install to format that partition for me, then how do you guys suggest me installing Mint on the Ubuntu partition? I'm wanting to get rid of Ubuntu altogether and install Mint on it.

Also, should I leave the Swap partitioner as it is, so Mint can use it? I've seen dual boot tutorials for Mint, and it tells you to make a Swap partition for Mint to use. Well, when I installed Ubuntu the Ubuntu installer did that for me.

So basically all I'm wanting to do is get Ubuntu off that partition(the one that says ext3), and get Mint on it. If anyone has anyone recommendations for me I'll really appreciate it.

Thanks.

---

### Post by eightmillion on 2008-08-24
Choose **Ext3 Journaling File System** and format. Choose your swap partition (/dev/sda6) for the mint swap partition and you should be fine.

---

### Post by Elfy on 2008-08-24
In the use as box - pick ext3, format it and pick / as mountpoint; it should deal with swap.

Edit - funny isn't it - no answer for nearly an hour, then 2 at the same time :) bit like buses I suppose

---

### Post by rampageoberon on 2008-08-24
If you want to overwrite the ubuntu partition, in this box

[http://www.lookpic.com/getimg.php?img=edit.png](http://www.lookpic.com/getimg.php?img=edit.png)

Select "Ext3 Journaling File System", tick the box to format and set Mount Point to "/"

Like you found out if you don't select anything it will not let you tick the box to format.

Hope that answers your question

---

### Post by h8uthemost on 2008-08-26
EDIT: Ah wait, I see. When I right click on my ext3 partition and hit Edit Partition, I pick the Ext3 from the Use As: box, then tick the Format box. Then...in this same window, where it says Mount Point, choose the / option? So everything would look like this?

[http://tinyurl.com/5oxvsm](http://tinyurl.com/5oxvsm)

So after I do that I'll be all good to go to install Mint? Now, that Edit Window is for my Ext3 partition(ubuntu partition). I choose / for the Mount Point when I edit the Ext3 partition right? I don't need to right-click on the Swap partition, hit Edit Partition, and choose /?

Thank you for the help. This is a great community.

---

### Post by Elfy on 2008-08-26
>  So everything would look like this?Yes that's right

> I don't need to right-click on the Swap partition, hit Edit Partition, and choose /?swap will look after itself, no need to touch it at all.

---

### Post by h8uthemost on 2008-08-26
Nice. Thank you so much for your help forestpixie. Looks like I'm ready to install it now.

---

### Post by Elfy on 2008-08-26
Off you go then - good luck with it :D

---

### Post by h8uthemost on 2008-08-26
I have one more question. I'm actually going to install tomorrow when I have more time to defrag.

Now, once I press Ok in the Edit a Partition window, will the installer then format my partition **and** install Mint? Or just format, then I'll have to run the installer again to install?

Thank you.

---

### Post by Elfy on 2008-08-26
The partitioner should just be part of the install process, once you've done the partitioning next should carry on.

That is at least how the ubuntu process works - I guess mint works the same way.

Make sure you defrag a couple of times.

---

### Post by h8uthemost on 2008-08-26
Ok, I just wanted to make sure that I'm not in for any surprises. I'll make sure to defrag more than once. I'm also guessing that Grub will take care of itself? Ubuntu will be taken off and Mint will be put on? I'm really hoping so, I don't really want to go into Grub and take Ubuntu off myself.

And that is my final question. You have been more than helpful forestpixie. And so has everyone else that has contributed in my thread. Thank you.

---

### Post by Elfy on 2008-08-26
afaik mint will install it's grub and that will be it - it's not hard to edit menu.lst if you have to :)

I'm sure that all will be fine.

---

### Post by h8uthemost on 2008-08-27
Thank you for your help. Everything got installed just fine. I got Ubuntu off and Mint on.

One little problem I'm having. Grub is off-centered on my screen. How can I make the Grub screen sit center?

Thanks again.

---

