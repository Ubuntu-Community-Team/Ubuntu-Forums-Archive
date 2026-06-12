---
title: "Live CD Stuck After 'Start' Or 'Install'"
date: 2008-08-02
forum: New to Ubuntu
---

### Post by nikki93 on 2008-08-02
NOTE: Please also read the replies to the post as they may contain addition information.

I have an Acer Aspire 5571ZWXMi, T2060 (its not 64 bit, I checked), and around 1 MB RAM.

I have an existing Windows XP install with 3 partitions, all NTFS, one's the C drive, anothers the D drive, and also another hidden partition called 'PQSERVICE'. I was thinking of shrinking the D drive a bit (its extremely huge, around 70 GB), and using the free space to install Ubuntu, **without** damaging the already existing contents on D.

Not sure you require the information in the above paragraph for this issue. :)

I downloaded the .iso (the i386 one) through BitTorrent using the uTorrent client, and burned it (yes, image burn not data burn) to a CD (not a DVD). I booted the computer with the disk in the drive, and had to press a key to get the boot menu, from where I chose the CD. I was greeted with the Ubuntu screen, where at first, I chose to start the Live CD. However, it got stuck. There was no error message or notification, and I tried selecting other options (using arrow keys, but it didn't move) or using the function keys but nothing happened. I just powered off the computer.

After looking into the documentation, I found that the 'noapic nolapic, acpi=off, irqpoll, lapic pci=routeirq' options might help. I rebooted and tried them out, but they didn't by themselves, and I also tried a few combinations of them but that didn't help either.

So, my question is, how do I fix this? :)

I am thinking of running the CD check to check whether it was burned right, and I'll post the results here.

Thanks for your help!

EDIT: It seems that Check CD gets it stuck to. Read the posts below for further information.

---

### Post by eram on 2008-08-02
Yes, run the cd check and post the results back here!

---

### Post by nikki93 on 2008-08-02
Hmm... I chose 'Check CD', and it gets stuck again. I waited for a few minutes, nothing happens (I'm not a very patient fellow, especially if there's no indication of progress or something happening :) ).

I tried F1 for help, it works. It seems that it only gets stuck when I choose one of the menu options. I'll have to confirm this by checking with the other options too though.

Does anyone else have a similar problem?

BTW, these forums seem extremely fast. I got a reply in just a minute, and also, my topic gets drowned by some 10 other topics by the time I reboot and try to check the CD (and fail). :)

---

### Post by eram on 2008-08-02
do you have another computer with a cd-rom drive that you can test it on?
That way, if it freezes on that computer, you'll know you have a defective disk.

---

### Post by Riffer on 2008-08-02
My thought too.  I think your disk is no good.  Try a new disk and burn at a slower speed.

---

### Post by northern lights on 2008-08-02
> **nikki93 said:**
> BTW, these forums seem extremely fast. I got a reply in just a minute, and also, my topic gets drowned by some 10 other topics by the time I reboot
If you set automatic thread subscription for the threads you're involved in, they'll appear in your UserCP as soon as there's any new unread posts...

As for your actual problem, your CD most likely is a bad burn. Should that for whatever wicked reason not be the case, check out [unetbootin]("http://lubi.sourceforge.net/unetbootin.html")

---

### Post by nikki93 on 2008-08-02
Ok, I tried to on a Dell Inspiron laptop, and it gives this dialog box (I'm writing from memory, this is just an approximate):-

```
+-----------------------+
|       IO Error        |
+-----------------------+
|Error reading from disk|
|       [Reboot]        |
+-----------------------+
```

I believe it has something to do with an erroneous disk. I'll burn another one.

Just asking: Will a DVD work too? Is it actually better?

---

### Post by eram on 2008-08-02
> **nikki93 said:**
> Ok, I tried to on a Dell Inspiron laptop, and it gives this dialog box (I'm writing from memory, this is just an approximate):-

```
      IO Error
      --------
Error reading from disk
      [Reboot]
```

I believe it has something to do with an erroneous disk. I'll burn another one.

Just asking: Will a DVD work too? Is it actually better?

Yes a DVD will work too. But no need to do a DVD since the .iso fits on a cd.
So try a slower burn speed, like maybe 16x. If that cd still doesn't work, you might have a faulty download.

---

### Post by eram on 2008-08-02
also, one reason the disk was freezing is the computer. I mean, you should have been able to do on your Acer what you were able to do on the Dell. Since it froze on the Acer but not on the Dell, part of the problem is with the Acer. You mentioned 1 GB of RAM. That is enough. What about the processor? What processor does the Acer have?

---

### Post by nikki93 on 2008-08-02
Its got an Intel dual-core T2060 (as I said in the first post).

But I've fixed everything now, no need to worry. I just put the ISO onto a USB Flash Drive using UNetBootin (because it sounded fun :) ), ran it Live and installed it.

I must say, I am amazed by how well it works straight out of the box. I was able to check it out live, and then install it, and while it was installing, I could browse the internet with Firefox. Now *that's* what I call a fun install. I congratulate all the developers that have contributed to this awesome piece of software.

Thanks for your help eram!

---

### Post by eram on 2008-08-02
You're Welcome!
Glad you've got it working!8)

---

