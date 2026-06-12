---
title: "Creating a new home partition"
date: 2008-05-01
forum: New to Ubuntu
---

### Post by mtonsbeek on 2008-05-01
If, after having installed Hardy I realise that having a separate home partition is a good idea, I suppose that booting from the LiveCD and using GParted I can resize.

I have currently got:
/dev/sda1 ext3
/dev/sda2 extended (???)
/dev/sda5 linux swao

Now I have resized the sda1 which was too big and have now got some 46 GB of unallocated drive.

If I create a new partition within that space I get "New Parttition #1" ext2.

I was expecting to see something like /dev/sda* 
Why ext2 instead of ext3?

Edited to say that the extended and Swap seems to be the same partition according to the grafic display in Gparted. The have the same size as well.
Thanks

---

### Post by herbster on 2008-05-01
Ext2 would be because you chose to make it ext2 in GParted, as that's the default option IIRC.

---

### Post by Daan on 2008-05-01
> **mtonsbeek said:**
> 
Why ext2 instead of ext3?


Hello. :) In gparted, right click on the unallocated space in the graphic display and select **new**. Then choose ext3 from the drop down menu on the right before continuing.

---

### Post by forestpixie on 2008-05-01
I think you get new partition until you have applied the action - then when gparted rescans it should be /dev/blah

---

### Post by mtonsbeek on 2008-05-01
> **Daan said:**
> Hello. :) In gparted, right click on the unallocated space in the graphic display and select **new**. Then choose ext3 from the drop down menu on the right before continuing.

Correct, thank you. 

> **forestpixie said:**
> I think you get new partition until you have applied the action - then when gparted rescans it should be /dev/blah

Also correct, many thanks.

> **herbster said:**
> Ext2 would be because you chose to make it ext2 in GParted, as that's the default option IIRC.

Many thanks, all sorted.

The only think I am still wondering about is why I have an extended and swap partition that seem to be one and the same thing?

---

### Post by forestpixie on 2008-05-01
If you let ubuntu sort out your original partitions on install that is what it does, means you can still put partitions within it - given the space.

---

### Post by mtonsbeek on 2008-05-01
> **forestpixie said:**
> If you let ubuntu sort out your original partitions on install that is what it does, means you can still put partitions within it - given the space.

Ok, understood.

Now that I have created my extra partition, is it now just a matter of cut and past my home directory over to the new partition?

Edited to say I will probably need to do this whilst being logged in as root, I do not seem to have the privilages to do this with my normal login.

---

### Post by forestpixie on 2008-05-01
no it's a bit more than that I believe - I vaguely remember using this

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

---

### Post by mtonsbeek on 2008-05-01
> **forestpixie said:**
> no it's a bit more than that I believe - I vaguely remember using this

[http://www.psychocats.net/ubuntu/separatehome](http://www.psychocats.net/ubuntu/separatehome)

Thanks, that seems to be what I am looking for.
That psychocats site has a lot of useful info on it!
Thanks for your help.

---

