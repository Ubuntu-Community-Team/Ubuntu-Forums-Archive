---
title: "DL DVD?! I need to back up /home!"
date: 2008-04-23
forum: New to Ubuntu
---

### Post by the badger on 2008-04-23
hello out there in 'buntu land...

i'm trying to back up /home and keep getting asked for a double-layer dvd. not only do i not have any, but i've backed up before and been fine with my usual dvd-rw/-r (i've tried both this morning). i've been using k3b, and i can't seem to find where i can modify the DVD type it is asking for. i've also tried using the default "make dvd?" app that launches when i insert a blank dvd-rw/-r.
i'm using the gui, so i've no output to post. any help much appreciated... i'm currently back-up-less!!

---

### Post by ace007 on 2008-04-23
The alternative is to place /home on a new partition.  This can be found here --> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am unfamiliar with k3b, but if you are having to backup your /home a lot you should really follow the guide.

---

### Post by timcredible on 2008-04-23
well, how much data is in /home?  a single layer DVD is only 4.3GB.  fwiw, i use an external usb-connected drive and grsync to do backups - it's very easy

---

### Post by shad0w_walker on 2008-04-23
Almost all CD/DVD burning software will ask for the disk that will be capable of holding what you are trying to write. Are you sure that there is enough space on a single layer DVD to hold what you are trying to write?

---

### Post by indytim on 2008-04-23
Just a near-shot-in-the-dark... :)... what's the size of /home?  Is k3b asking for a double layer because you're trying to write a filesize >~4.7G ??

IndyTim

---

### Post by the badger on 2008-04-23
hello all - thanks for the speedy replies.

the writing on the packages all say my dvds are 4.7gb - the data i'm trying to write is 4.5gb - which makes me think it *should* fit. timcredible, you mention that the average dvd holds only 4.3gb. is the other .4 spoken for?

since my original post i did manage to write to dvd a smaller amount of data (not all of /home). so i guess everyone is right about not-enough-space. (who knew 4.7 - 4.5 = -2 ?!)

thanks.

---

### Post by wannadumpwindows on 2008-04-23
I've ran into the same issue myself here and there. I don't know about you, but it happens to me for different discs in the same batch. Some seem to be able to hold more data than others. It's been plain old puzzling on this end . . . . . .

---

### Post by qamelian on 2008-04-23
> **the badger said:**
> hello all - thanks for the speedy replies.

the writing on the packages all say my dvds are 4.7gb - the data i'm trying to write is 4.5gb - which makes me think it *should* fit. timcredible, you mention that the average dvd holds only 4.3gb. is the other .4 spoken for?

since my original post i did manage to write to dvd a smaller amount of data (not all of /home). so i guess everyone is right about not-enough-space. (who knew 4.7 - 4.5 = -2 ?!)

thanks.
Don't forget that a portion of the DVD's capacity gets eaten up by the disc's table of contents. I can't remember the exact amount of  space lost, but if I recall correctly, you generally only get 4.5 GB on a 4.7 GB disc.

---

### Post by wannadumpwindows on 2008-04-23
> **qamelian said:**
> Don't forget that a portion of the DVD's capacity gets eaten up by the disc's table of contents. I can't remember the exact amount of  space lost, but if I recall correctly, you generally only get 4.5 GB on a 4.7 GB disc.

That seems like a **HUGE** amount of space for it . . . . .

Oh well, just like my 80 Gb hard drive that only holds 74 Gb of data.

---

### Post by qamelian on 2008-04-23
> **wannadumpwindows said:**
> That seems like a **HUGE** amount of space for it . . . . .

Oh well, just like my 80 Gb hard drive that only holds 74 Gb of data.
It depends on how many files need to be references in the ToC. For comparison purposes, take a look at a multi-session CD sometime and see how much capacity gets lost to the table of contents. It's very easy to waste half of the disc to ToCs if you write a number of relatively small sessions, as each session requires a new ToC. Again, I don't remember the exact capacity, but I believe the standard for data CDs is to allocate 30MB for the ToC. The first ToC is already allocated when the blank disc is produced, so you don't see the additional loss of capacity on writing a single session. You will notice it on adding a second and subsequent sessions to the same disc.

It's slightly different from the HD situation where it's genuine a numbers game of "Guess how we calculate capacity".

---

### Post by stchman on 2008-04-23
> **ace007 said:**
> The alternative is to place /home on a new partition.  This can be found here --> [http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

I am unfamiliar with k3b, but if you are having to backup your /home a lot you should really follow the guide.

You can specify a home directory in:

System--->Administration---Users

There is a tab that deals with shell and home folder selection.

The default is /home/<your home>, but that can be changed to anything.  I leave my home partition there and use another partition for all my personal data.

Now if you need the word "home" to give you a warm fuzzy then follow the instructions that you have posted.

I would use the command to backup the home folder to the new folder as the link you have says so.

---

