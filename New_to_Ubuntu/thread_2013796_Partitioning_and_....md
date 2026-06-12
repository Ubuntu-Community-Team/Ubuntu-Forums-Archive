---
title: "Partitioning and ..."
date: 2012-07-01
forum: New to Ubuntu
---

### Post by czgirb on 2012-07-01
Dear all! I'm a newbie to Ubuntu.
I wish to ask a thing regarding to the partitioning and placing a file.
I partitioning my HDD in 3 parts
*** 20GB** for **/** let say it's **A**
*** 10GB** for **swap**
*** 100GB** for **/home** let say it's **B**

If I opened a **nautilus**, and put my file in **Documents** section, is it will be placed at **/home or B partition**? ... *SORRY for being Windows minded*.
If not, how can I put the file in **B** (**100GB**'s **/home**) partition.

Now, I'm using **Ubuntu 12.04** ... if next month I wish for having **Lubuntu** installed on my computer ... if I installed in **A (/ partition)**, it will not affect my **B (/home partition)**, right?

---

### Post by Paqman on 2012-07-01
10GB is quite large for swap, you'd only need it to be that big if you had 10GB of RAM. Your swap needs to be the same size as your RAM to use hibernation, otherwise 1GB or so is plenty on any reasonably modern computer.

> If I opened a nautilus, and put my file in Documents section, is it will be placed at /home or B partition?

Yes.

What you see as Documents, Pictures , etc are located at /home/username/Documents within the filesystem. So all the folders in all user's home folders are on the partition you mount /home on.

> if next month I wish for having Lubuntu installed on my computer ... if I installed in A (/ partition), it will not affect my B (/home partition), right?

Correct.

If you want to be extra-sure you can manually assign which partitions to mount what on. During installation chose "do something else..." and assign them manually.

You actually don't need to reinstall just to try or switch to Lubuntu. Just install either the package [lxde](apt:lxde) or [lubuntu-desktop]("apt:lubuntu-desktop") and if you want remove the old Gnome packages using [this command]("http://www.psychocats.net/ubuntu/purelubuntu"). Lxde contains just the basic desktop, lubuntu-desktop contains lxde plus all the extra apps you'd get if you install Lubuntu from a disk. When you have both desktops installed you can choose which you want to log into by clicking the little icon next to your user name on the login screen.

---

### Post by spiky001 on 2012-07-01
Hi  You have 20gig for / which is plenty. 10gig swap normally swap is double your ram  Home is where all the documents pics etc go yes you are correct that is where they will be /home/username/Documents.  As long as you set **B **As long as that is where you set home to be when you installed.
When/if you install lubuntu instead, you can use the same home Providing you dont format it when installing ( as always back up data).

---

### Post by czgirb on 2012-07-01
> **Paqman said:**
> 
... Yes.
What you see as Documents, Pictures , etc are located at /home/username/Documents within the filesystem. So all the folders in all user's home folders are on the partition you mount /home on.


Today I installed **Calibre**. And it was informed that **my Calibre's Library** will be placed in **/home/username/calibre** ... but I don't see any options, which say **calibre** in my **nautilus**.
How can I find it?

---

### Post by angry_johnnie on 2012-07-01
10 gigs for swap is a lot!  if you have plenty of ram, swap is, really, never used, unless you're planning to let your computer hibernate.  i usually allocate about 500 megabytes for swap.  i only have 2 gigs of ram, but still i've never seen swap actually being used.

---

### Post by Paqman on 2012-07-01
> **czgirb said:**
> Today I installed **Calibre**. And it was informed that **my Calibre's Library** will be placed in **/home/username/calibre** ... but I don't see any options, which say **calibre** in my **nautilus**.
How can I find it?

I have Calibre too, and it has placed it's library at /home/username/Calibre Library for me. Have you put any books in the library yet? It may only create the folder when you put something in it...

---

### Post by spiky001 on 2012-07-01
Hi   I dont have Calibre but looking at FAQ [URL="http://manual.calibre-ebook.com/faq.html#where-are-the-book-files-stored"]here 
[/URL]It sayes it will ask where to save the books
[]("http://manual.calibre-ebook.com/faq.html#library-management")

---

### Post by czgirb on 2012-07-01
> **Paqman said:**
> 
10GB is quite large for swap


> **angry_johnnie said:**
> 
10 gigs for swap is a lot


OK ... now, what should I do with **G-Parted**?
**Reduce (Resize) the SWAP** and **Enlarged (Resize) /home** or what?
Please guide me ....

---

### Post by oldfred on 2012-07-01
It depends on exactly where swap is and whether it is primary or logical.

GParted partitioning software - Full tutorial 
[http://www.dedoimedo.com/computers/gparted.html](http://www.dedoimedo.com/computers/gparted.html)
Screenshots of using gparted
[http://www.howtoforge.com/partitioning_with_gparted](http://www.howtoforge.com/partitioning_with_gparted)

I generally do not like moving partitions left as then gparted has to copy and delete everything to move it. Be sure to have good backups as any interruption, power failure in the middle will corrupt system. I have moved partitions and not had problems, but it only takes once. And if a lot of data, it can take a long time.

I might just add the space to / if swap is next to your root partition. I like to keep root not much more than about 25% full.

---

### Post by Paqman on 2012-07-02
> **czgirb said:**
> OK ... now, what should I do with **G-Parted**?
**Reduce (Resize) the SWAP** and **Enlarged (Resize) /home** or what?
Please guide me ....

If you've already installed and aren't short on space then you don't need to do anything necessarily. It's a just a bit of a waste of space. Not a big problem.

If you want you can boot into your LiveCD, run Gparted, right click on swap and "swapoff", shrink your swap and add the space to one of the adjacent partitions. Up to you.

---

### Post by czgirb on 2012-07-02
> **Paqman said:**
> 
... if you want you can boot into your LiveCD, run Gparted ...


Why I should boot into my **LiveCD** ?
Is the process can not be do directly from **Ubuntu 12.04** ?

---

### Post by Paqman on 2012-07-02
You can't change any partition while it's mounted. So if you ran Gparted from your hard drive you wouldn't be able to make changes to some of the partitions, which may not be convenient. Booting into a CD or USB stick removes this obstacle.

---

### Post by oldfred on 2012-07-02
You cannot edit the partition you are running the software from. And if it is a logical partition that includes all logicals since it really is the extended that is mounted.

So use liveCD and most liveCDs also automount the swap to speed things up a bit, so you have to click on it in gparted and right click swap off.

---

### Post by czgirb on 2012-07-02
Thank you for all of your guidance
It was very very very appreciated ....

---

