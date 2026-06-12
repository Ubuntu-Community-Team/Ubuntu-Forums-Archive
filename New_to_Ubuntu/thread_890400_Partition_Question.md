---
title: "Partition Question"
date: 2008-08-15
forum: New to Ubuntu
---

### Post by h8uthemost on 2008-08-15
Hey guys,

I'm currently running XP, and I want to do a dual boot with Linux Mint. Now, I"m a little iffy on the whole partition thing. So if anyone is pretty good with Linux, and has messed with partitions, I hope you can help me out.

When I go to install Linux, I get to the partition part. Now, the first choice is what I'm going to pick. The Guided option. As is shown here:

[http://www.lookpic.com/getimg.php?img=installinghardyplus10.png](http://www.lookpic.com/getimg.php?img=installinghardyplus10.png)

Now, this is where I get a little confused. Where should I move the slider? Meaning, should I move to where Windows is at 55% and Linux is at 45%? Or should I do it 50%/50%. Or 75%/25%? See what I'm saying? I don't know how much I should give each partition.

The last time I tried this I was trying to install Ubuntu with a dual boot. And halfway through the installation my screen went black, so I thought the installation was done. I then re-booted the computer, but my whole Windows partition was gone. Doh! I guess that screen just went into screen saver mode. But I didn't know this because it was a black screen.

So...I'm hoping I'm going to have better luck this time. So I hope any of you Linux guru's can help me out.

Thank you.

EDIT: Here's another pic:

[http://www.lookpic.com/getimg.php?img=installinghardyplus11.png](http://www.lookpic.com/getimg.php?img=installinghardyplus11.png)

Since 5gb is recommended to install Linux Mint, should I resize the partition to where Linux has 5gb? Kind of like how this picture shows Ubuntu has 2.1gb?

---

### Post by K2712 on 2008-08-15
On a hard drive of that size, you want to be sure you have enough room to resize.  The minimum space needed for XP is 1.5 Gb, but that doesn't take into account extra programs/data you have installed.  I would check to see how much space is taken up by your current XP installation after you defrag the hard-drive, then give a little bit more space for future file storage.

So, for instance if you are currently using 2.1 Gb for XP after defragging, I would split 2.5 Gb for XP, and 5.1 for Linux mint.

---

### Post by h8uthemost on 2008-08-15
Well, actually those pics aren't from my computer. They are just pics I took out of a tutorial to show you guys what I was talking about.

I was just wanting to get a general idea of what to use for each partition. I'm really scared I'm going to wipe out Windows again and have to start all over.

EDIT: To find out how much Windows is taking up after my defrag, can I just go into my C: drive and see how big my Windows folder is?

---

### Post by jualin on 2008-08-15
Check my signature for a guide on how to successfully Dual Boot. Make sure you defragment your XP partition first and backup any important data since resizing a Windows partition might make the partition not work some times. Good luck!

---

### Post by h8uthemost on 2008-08-15
Thanks jualin. I've actually seen that tutorial before. And this is the part I get stuck at:

*2: Specify the size of the new partition as a percentage of your entire hard disk. *

I have no idea how much space I should give for the Windows and the Linux side.

---

### Post by meindian523 on 2008-08-15
How big is your hard drive?

---

### Post by jualin on 2008-08-15
That "percentage of your hard disk" depends on how you use the computer. I will tell you the way I have it in my computer. I have a 160 GB hard drive partition with 50 GB for XP (more than enough for me), 20 GB for a DVD backing up partition used by Windows XP and 60 GB for Ubuntu, and the rest to try out other distros. In my case I don't have many mp3s and pictures on my computer therefore 20 GB for my Documents are more than enough. Ubuntu programs shouldn't occupy more than 15 GB unless you install many applications. Again it's just a matter of preference. I have a friend which filled his 15 GB Ubuntu partition in 2 days with his Ipod Music Library :). Feel free to ask anything else.

---

### Post by jualin on 2008-08-15
Make sure you check how much space are you using in Windows first before resizing the partition. You wouldn't want to resize your XP partition to 9 GB when you are using 20 GB.

---

### Post by h8uthemost on 2008-08-15
My hard drive is 74.5GB.

EDIT: Ok, when I go into my C: drive, and right-click on my Windows folder and go into Properties, it shows that Windows is 3.54GB. Is that how you check how much space Windows is using? 

I'm completely new to this, so that's why I"m having a lot of trouble with this and asking dumb questions.

---

### Post by meindian523 on 2008-08-15
80 GB.My HDD is the same size,I've created an extended partition for Ubuntu which contains a 
11GB /home
5 GB / 
1 GB swap and 
150 MB /boot.
As Jualin said,it's a matter of preference and what you use the computer for.

---

### Post by h8uthemost on 2008-08-15
Wow, I have no idea what to do. All I want is two partitions. One for XP, and one for Linux. That's all.

I guess I'll just forget about Linux Mint and go with Ubuntu through Wubi. I've read that Ubuntu runs slower when installed through Wubi, but I guess I would rather deal with that then totally wiping out my whole computer again when trying to mess with these partitions.

Thanks for the help guys.

EDIT: Actually, I"ll try something like K2712 mentioned:

*So, for instance if you are currently using 2.1 Gb for XP after defragging, I would split 2.5 Gb for XP, and 5.1 for Linux mint.*

What is the best way to check how much space XP is taking up after I defrag?

---

### Post by jualin on 2008-08-15
The only bad part of using Wubi is that if you have some problem on your Windows partition (hard reboot), then the Ubuntu can lock up until you run scandisk from Windows. Follow k2712 advice but make sure to back up any important data. Most of the time resizing works but in some obscure instances it may wipe the partition. Don't be afraid to try it. Good luck! ;)

---

### Post by meindian523 on 2008-08-15
Um.Linux doesn't have a parallel drive like the Windows C: and D: .Everything is under 1 root partition called /,and /home means the home folder under /.One partition can be created for each of those folders under /,and for folders inside them too.The general folders which have separate partitions dedicated to them,other than /(which is compulsory),are /home and swap(which is again copulsory,but doesn't have a folder to attach to,as in you won't find a /swap folder to attach(in Linux lingo,called mount) your swap partition to.

A corresponding arrangement in Windows would be to have D:(/home) accessible by going to a folder named D:(home) in C:(/).

---

### Post by jualin on 2008-08-15
> **h8uthemost said:**
> Wow, I have no idea what to do. All I want is 

What is the best way to check how much space XP is taking up after I defrag?

While running XP, Go to My Computer and then right click on your hard drive (usually local disk c: ) and then select properties. This should give you the size of your hard drive. Also when you defrag the computer the size is mention while the defragmentation is running.

---

### Post by h8uthemost on 2008-08-15
Ok, so the defrag window will tell me how much room Windows is taking up? Also, should I quit everything while I"m defragging? Like no browsing, or any other applications open?

---

### Post by jualin on 2008-08-15
Yes the defragmentation window will tell you the space Windows XP is taking up. You should let the computer alone while defragmentation is in process since the defragmentation will rearrange the order of the files on your computer, and browsing the internet will write new files on your hard disk such as "cookies" and "temporary files"

---

### Post by h8uthemost on 2008-08-15
Cool. Thank you for your help. I feel a little better about setting up a dual boot. I appreciate it. :)

---

### Post by jualin on 2008-08-15
Glad we made you feel that way.Let us know how it went and  Welcome to the family!

---

### Post by Pendarth on 2008-08-15
> **h8uthemost said:**
> Ok, so the defrag window will tell me how much room Windows is taking up? Also, should I quit everything while I"m defragging? Like no browsing, or any other applications open?

Hi h8uthemost,

(/me is an utter noob here too :)) ... so from one n00b to another -- don't despair, it really is quite easy.

If you use the defrag window - it will show you the number of hard disks installed (if more than one) and when you click "analyze" it will show you the total size, size used by files (currently) - in each partition on each hard disk.

Defrag the hard disk - (it'll be faster if you don't do much else while it defrags) - then try to follow jualin's instructions ... I used them and it worked like a charm.

BTW. thanks Jualin :)

---

### Post by h8uthemost on 2008-08-15
Ok. Thank you Jualin and Pendarth. :) You guys have made me feel better. And thanks to ther others that helped. I'll post back to let you know how everything went.

---

