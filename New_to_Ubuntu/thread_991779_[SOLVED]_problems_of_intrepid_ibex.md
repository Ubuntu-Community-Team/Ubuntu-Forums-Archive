---
title: "[SOLVED] problems of intrepid ibex"
date: 2008-11-24
forum: New to Ubuntu
---

### Post by jorge ortega on 2008-11-24
I hope I am using the right forum the right way I'm totally new to this and this is my first help petition.
I recently started using Ubuntu Hardy Heron together with Windows vista in my PC. Happy enough with it, I'm trying to stop using Windows altogether. Two days ago I updated to Intrepidibex and it is just a disaster, many things go wrong. I want to go back to Hardy Heron, How do I do this? Can I downgrade or can I uninstall Ibex and then reinstall Heron with my live cd like the first time.
Please any instruction should not assume any knowlodege of computers. Any help would be very welcome, thanks in advance

---

### Post by clive littlewood on 2008-11-24
Hi

If you wish to give us your problems i am sure that help will be given to you.

If you wish to go back to HH then hopefully you have or can backup any important data.

Then simply install HH from the original CD which will erase ibex and reformat your hard drive as you require.

Regards

Clve     :)

---

### Post by jorge ortega on 2008-11-24
Thanks Clive. I did a bit of research and it seems to me that it is not so easy. There seems to be something called grub that needs to be manually deleted or something. If I just reinstall HH would that not crash with II or create a third partition?

---

### Post by Bölvaður on 2008-11-24
> **jorge ortega said:**
> I hope I am using the right forum the right way

Um... sorry to say this but you are doing it wrong :lolflag: as you should have had more descriptive title (it seems like this thread is suffering from to low clicks per minute compared to others that do have good descriptive title).

Any way.

I have always said that people should not use the update option to go to the next release unless if they are ready to fix it afterwards.

It might also be that your hardware currently isn't too suitable for 8.10, so staying with 8.04 might be the easiest thing.
There is nothing wrong with staying with the long term service releases like 8.04.

What you would want to do is either using your current cd (8.04) or get the 8.10 one and install it again. There is no need to uninstall as you will overwrite the OS anyway.


The new installation goes just the the other one but with just with 2 extra steps.

1. Backup your personal data.
2. Connect the partitions manually

There are many tutorials on this forum and other places on the net which depict and explain the process on how to manually do the partitions (not make them.. just tell ubuntu to use the already made ones when it installes it self over the old ubuntu which you currently have installed.. omg this sounds confusing)

here is a little preview (but you need to find better source to learn how to do this): when you are installing you are prompted with partitioning table. You should choose to do it manually (bottom choice). There you put / as mount point for the place ubuntu is supposed to be installed at, and use ext3 as filesystem.



hope if this wasnt too confusing for you

---

### Post by Bölvaður on 2008-11-24
> **jorge ortega said:**
> There seems to be something called grub that needs to be manually deleted or something. If I just reinstall HH would that not crash with II or create a third partition?
No, grub (which is a boot loader, the thing you see when you pick what os to run) is kept in your /boot section of your ubuntu partition.
So when you install 8.04 again it will be over written and hence it will be a fresh install with everything new.

The only troubles you might get is if you are booting with more versions of ubuntu already on your system and there will be kernel update... you dont need to worry about it.


Also if you do as I suggested and manually install 8.10 or 8.04 over your current partitions there would be no partitions created and you would end up with fresh and clean install (feels good doesnt it)

The only thing you should avoid is making the partitioning be automaticly handled. see my post above and search on this forum for more detailed information.

---

### Post by Tom--d on 2008-11-24
If you want to go back to HH just do a clean install from CD.

Of course backup all your data first.

---

### Post by jorge ortega on 2008-11-24
Thanks to all of you, I am at work now so I won't be able to do anything till tonight late at the earliest. I will keep you informed. Thanks again

---

### Post by Michael.Godawski on 2008-11-24
When you come back from work here is something to read:

[LIST]
[*]Aysiu's site: [http://www.psychocats.net/ubuntu/index](http://www.psychocats.net/ubuntu/index)
[/LIST]
and

[LIST]
[*]Herman's Illustrated Dual Boot site: [http://users.bigpond.net.au/hermanzone/p3.htm](http://users.bigpond.net.au/hermanzone/p3.htm)
[/LIST]
Some really essential stuff which will also take some fear away.

---

### Post by jorge ortega on 2008-11-25
Thanks everyone, I'm back to HH now. Problems solved

---

