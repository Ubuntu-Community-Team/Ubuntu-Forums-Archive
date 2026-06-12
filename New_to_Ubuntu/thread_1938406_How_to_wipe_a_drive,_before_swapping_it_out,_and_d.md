---
title: "How to wipe a drive, before swapping it out, and disposing of it?"
date: 2012-03-09
forum: New to Ubuntu
---

### Post by mikodo on 2012-03-09
Hi,

I have a new drive to put in my one drive computer. I plan to backup my personal stuff, to an external drive and swap the internal drive. I would like to clear my data, from the first drive, before disposing of it. Here is the drive:

 ```
sudo blkid
``````
/dev/sda1: UUID="1b3bf77f-702f-45fc-831b-404daba90305" TYPE="ext4" 
/dev/sda5: UUID="387dd97f-93e1-4edb-a9ef-8ab4aa5c4a13" TYPE="ext4" 
/dev/sda6: UUID="05482d21-e398-4fd6-882c-1ecab0c146f3" TYPE="swap" 
```Is below, a good way to clear the drive? If, this would work, how  would I use the command, to remove the data from the whole drive?

```
sudo rm -r ...
```Because of what I am asking; if anyone wishes to PM me, with instructions, I will respond.

Thanks.

---

### Post by Cheesemill on 2012-03-09
You can use dd:
```
sudo dd if=/dev/zero of=/dev/sda
```

Best to do this from a Live CD as you can't zero a drive that is in use.

[SIZE=3][COLOR=Red]**BE VERY CAREFUL**[/COLOR][/SIZE]
that you use this command on the correct drive or you could lose important data.

---

### Post by mikodo on 2012-03-09
You know, I need to investigate this myself. Why, I didn't read up on it, before posting, I don't know. (I guess I am too used to hand holding on the forums)...

Sorry, please disregard this thread.

---

### Post by winh8r on 2012-03-09
Probably one of the best ways would be to get something like
```
 secure-delete
```

you can apt-get install it on a live cd and then run 

```
man srm
```

for options and instructions.

And for the sake of anyone reading this who thinks about installing it to see what it does, it destroys data securely ,but is a very powerful and potentially destructive tool if you do not know what you are doing with it.

USE WITH CAUTION

READ, ask. READ ask, act!!!

---

### Post by flemur13013 on 2012-03-09
Reformatting it makes everything unreadable to normal people (those not using recovery software).  Writing zeros to it makes recovery impossible (only one write is needed):

[How to wipe a hard drive clean in Linux]("http://how-to.wikia.com/wiki/How_to_wipe_a_hard_drive_clean_in_Linux")

But if you're going to throw away the drive, just hit it with a hammer a few times!

---

### Post by mikodo on 2012-03-09
Thanks for the suggestions guys.

I'll read up, about them.

:^)

---

### Post by sleepingdragon on 2012-03-09
Don't forget the delightful DBAN LiveCD which does a thoroughly wonderful job. 

Handy little tool to keep if wiping drives is your hobby.

[dban.org]("http://dban.org")

---

### Post by mikodo on 2012-03-09
> **sleepingdragon said:**
> Don't forget the delightful DBAN LiveCD which does a thoroughly wonderful job. 

Handy little tool to keep if wiping drives is your hobby.

[dban.org]("http://dban.org")

Actually, I think I have a CD. I forgot about it, and to use it for its' most secure wipe, if I remember correctly, for me, it was overkill.

Never used it though ... It's not exactly a "hobby". :^)

Thanks.

---

