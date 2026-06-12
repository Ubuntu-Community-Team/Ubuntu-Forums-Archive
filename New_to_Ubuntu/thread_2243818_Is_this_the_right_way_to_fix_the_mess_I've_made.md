---
title: "Is this the right way to fix the mess I've made?"
date: 2014-09-11
forum: New to Ubuntu
---

### Post by GaryTheCat on 2014-09-11
Hello

I had some problems with ubuntu 14.04 in that it would just hang after entering my password. To solve this, I decided to install xubuntu to replace the installed ubuntu (to dual boot with windows).  What I now have is windows, ubuntu and xubuntu.

I have 2 HDDs one with windows on it and a few other partitions and the other with the linux distros in 2 partitions and a larger 'data' partition that I use for files I might want to access in Windows and Linux (Music, Videos, etc.)

What I plan to do is to:

[LIST=1]
[*]use gparted from a live usb to delete the partition containing ubuntu (sdb5)
[*]enlarge the 'data' partition (sdb1) to include the space that was taken up by the ubuntu partition deleted above.
[*]update grub and hope it works.
[/LIST]

Does that sound about right? Will the data partition become corrupt by resizing it / will I lose data (I don't have anything large enough to hand to back this lot up)? Could I resize the xubuntu partition without causing problems?

My other option would be to format the ubuntu partition sdb5 and use it as a /home partition.

gparted screenshot of sdb attached.....

[ATTACH=CONFIG]256366[/ATTACH]

Thanks in advance

G

---

### Post by jdeca57 on 2014-09-11
sdb1 is an ntfs partition. Can you expand it while keeping data? Well, according to this link [http://www.disk-partition.com/resource/resize-NTFS-partition-windows.html](http://www.disk-partition.com/resource/resize-NTFS-partition-windows.html) the answer is yes but I would be prudent and not go that way unless you have a backup. Safest is to use sdb5 as /home. I would do that if it were my data.

---

### Post by Bucky Ball on 2014-09-11
Go ahead with your plan. BUT ... boot to Xubuntu first, and:

```
sudo grub-install /dev/sda
```

... if the grub doesn't already belong to Xubuntu, and as it was installed second, I'm presuming it does ...

Incidentally, you have a great big problem with enlarging sdb1 into free space. It is called sdb2. That's an extended partition start and you can't merge across that without deleting the whole extended partition (and everything in it) and starting again.

You could, though, shrink sdb7 and expand into that free space. Not as much, but something.

You could also shrink sdb1 (with the worrying exclaimation mark next to it) and expand the extended partition into that free space, then what is now sdb5 in to that. 

Just a few suggestions ... :-k

PS: As I think jdeca57 was alluding to, if sdb1 is a Windows 7 and above, you must use the Win7 software to resize it. Using Gparted can seriously screw up your Windows boot. Regular NTFS data drives, shouldn't be a problem.

---

### Post by GaryTheCat on 2014-09-11
I think I'll just keep it simple and delete sdb5 and extend sdb7 into the free space - everything I needed from sdb5 is backed up anyway and I haven't really done anything with the Xubuntu install on sdb7 so there's nothing at stake if it all goes wrong.

Will post back when I'm out the other side!

---

### Post by GaryTheCat on 2014-09-27
I finally bit the bullet - and reformatted the drive in question and installed Xubuntu 14.04 in the place of Ubuntu 13.10.

It meets my needs and the old laptop is purring like a kitten and in other news, my car crash partition table looks a lot neater now.

Thanks for your help!

G

---

### Post by Bucky Ball on 2014-09-27
Good news. Enjoy! ;)

---

