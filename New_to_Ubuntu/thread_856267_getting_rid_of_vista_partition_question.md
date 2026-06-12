---
title: "getting rid of vista partition question"
date: 2008-07-11
forum: New to Ubuntu
---

### Post by muteXe on 2008-07-11
Hello,
i have one vista partition and one ubuntu partition.  I want to get rid of vista completely.  Is it just a case of booting from the ubuntu cd, and using gparted to delete the vista partition, and reszing my ubuntu partition?
If so, is there anything else i need to do?

Many thanks,
mute

---

### Post by MasterXandrex on 2008-07-11
Shouldn't be, other than to create a new partition or resize another to recover the space.

Though, I would probably just install gparted.


```

sudo apt-get install gparted

```

Xan

---

### Post by bumanie on 2008-07-11
If you have grub chainloading vista, you may have to reinstall grub, otherwise it is likely to give an error saying it can't find one of the OSes it is looking for.

---

### Post by MasterXandrex on 2008-07-11
I wouldn't bother reinstalling it, just remove that entry:

```

sudo nano /boot/grub/menu.lst

```


Xan

---

### Post by muteXe on 2008-07-11
Well i made my menu.lst default to ubuntu after 3 seconds, so i might just leave it like this.
okay so i'll use gparted to delete vista partition and resize my ubuntu.
cheers both :)

---

### Post by kenpogi on 2008-07-11
Just a thought, download "supergrub" to disc first, then any problems rebooting can be fixed by booting to supergrub.

---

### Post by bumanie on 2008-07-11
You can just remove the vista entry from /boot/grub/menu.lst but if you extend the ubuntu partition over the present vista partition, ubuntu's /boot/grub/menu.lst drive number will be wrong and will have to be altered to (hd0,0) [or whatever is appropriate]. The reason I didn't suggest this initially is because I don't know how you have ubuntu set up. Some people after a few reinstalls , may end up with swap as the first partition, thus the drive desiganation would have grub looking to boot from swap, which of course, would not work. You need to ensure /boot/grub/menu.lst reflects the ubuntu bootable partition.

---

### Post by Inxsible on 2008-07-11
What you need to be sure about is..do you really not want Vista?

I am not sure how long you have been using Linux...but there are a few things that Windows can do and Linux can't.

Doesn't hurt leaving a small partition of Windows - since you already have a dual boot set up.

You don't have to use it...but its there in case you do need it.

---

### Post by linux6994 on 2008-07-11
Congratualation on your decision to remove Vista. You have successfully stepped up yet another step on the evolutionary ladder.

---

### Post by MasterXandrex on 2008-07-11
> **Inxsible said:**
> What you need to be sure about is..do you really not want Vista?

I am not sure how long you have been using Linux...but there are a few things that Windows can do and Linux can't.

Doesn't hurt leaving a small partition of Windows - since you already have a dual boot set up.

You don't have to use it...but its there in case you do need it.

Of course he doesn't want Vista, what's wrong with you? Don't dissuade him. :lolflag:


Xan

---

### Post by Inxsible on 2008-07-11
> **UbuntuUser3859 said:**
> Of course he doesn't want Vista, what's wrong with you? Don't dissuade him. :lolflag:


XanYes, but I have also seen a lot of threads that start with "I want my windows back" or "I cannot do "this" in ubuntu" etc etc.

---

### Post by Foster Grant on 2008-07-11
> **muteXe said:**
> Hello,
i have one vista partition and one ubuntu partition.  I want to get rid of vista completely.  Is it just a case of booting from the ubuntu cd, and using gparted to delete the vista partition, and reszing my ubuntu partition?
If so, is there anything else i need to do?

Many thanks,
mute

You may find you have two Vista partitions --- the main C:\ partition and a smaller recovery partition.

When I deleted my Windows partition, I backed up all my personal data from both Windows and Ubuntu and then rebooted from a Live CD to reformat the drive and make a new, clean installation.

---

### Post by muteXe on 2008-07-11
> **Inxsible said:**
> What you need to be sure about is..do you really not want Vista?

I am not sure how long you have been using Linux...but there are a few things that Windows can do and Linux can't.

Doesn't hurt leaving a small partition of Windows - since you already have a dual boot set up.

You don't have to use it...but its there in case you do need it.

I been using for linux for just over a year now.  I dual boot it with xp on my main desktop, and have another 100% linux laptop with xubuntu on it.

My new laptop (the one i'm asking questions for) has been blue-screening loads since putting vista sp1 on it.  So i'm saying goodbye to it.  

Don't worry, i can live without vista on my new laptop :)

Thank you for all the advice.

---

### Post by bumanie on 2008-07-11
As I said above, it is not as simple as just removing vista and expecting everything will work, you will probably have to do some editing to /boot/grub/menu.lst - without knowing your ubuntu partitions, it is impossible to give precise advice.

---

### Post by Inxsible on 2008-07-11
> **muteXe said:**
> I been using for linux for just over a year now.  I dual boot it with xp on my main desktop, and have another 100% linux laptop with xubuntu on it.

My new laptop (the one i'm asking questions for) has been blue-screening loads since putting vista sp1 on it.  So i'm saying goodbye to it.  

Don't worry, i can live without vista on my new laptop :)

Thank you for all the advice.Oh hell yeah !! everyone can live without Vista :D

I know I can and actually want to. 

I just provided the warning because I didn't know whether you had another machine with a Windows partition on it.

---

### Post by muteXe on 2008-07-11
heh, no worries :)  thanks again.

---

