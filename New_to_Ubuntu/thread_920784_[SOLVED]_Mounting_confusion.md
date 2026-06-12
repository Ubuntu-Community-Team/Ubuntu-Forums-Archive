---
title: "[SOLVED] Mounting confusion"
date: 2008-09-15
forum: New to Ubuntu
---

### Post by moody_mark on 2008-09-15
:confused:

Perhaps someone can explain to me... I have a Linux box at work, its not a ubuntu box, its actually a red hat one, but its still linux (so hope its ok to ask here). Anyway, I had some files in /home/user which was mounted on /dev/hda1. I added a shared folder under /opt/shared but the /opt partition was too small, heres what it looked like using the output of "df -h";

```

/dev/hda1             428G  200G  207G  50% /home
/dev/hda2              31G  484M   29G   2% /opt

```

So i mounted the shared folder onto the hda1 partition using the command;

```

mount /dev/hda1 /opt/shared/

```

So the output of df -h looked like this;

```

/dev/hda1             428G  200G  207G  50% /home
/dev/hda2              31G  484M   29G   2% /opt
/dev/hda1             428G  200G  207G  50% /opt/shared

```

So this is what I wanted, one problem now, any users looking in the /opt/shared folder can also see the contents of the /home folder.

Now for the dumb question: why is this happening? Im finding understanding mounts a bit confusing. Any recommendations for learning?

---

### Post by k33bz on 2008-09-15
> **moody_mark said:**
> :confused:

Perhaps someone can explain to me... I have a Linux box at work, its not a ubuntu box, its actually a red hat one, but its still linux (so hope its ok to ask here). Anyway, I had some files in /home/user which was mounted on /dev/hda1. I added a shared folder under /opt/shared but the /opt partition was too small, heres what it looked like using the output of "df -h";

```

/dev/hda1             428G  200G  207G  50% /home
/dev/hda2              31G  484M   29G   2% /opt

```

So i mounted the shared folder onto the hda1 partition using the command;

```

mount /dev/hda1 /opt/shared/

```

So the output of df -h looked like this;

```

/dev/hda1             428G  200G  207G  50% /home
/dev/hda2              31G  484M   29G   2% /opt
/dev/hda1             428G  200G  207G  50% /opt/shared

```

So this is what I wanted, one problem now, any users looking in the /opt/shared folder can also see the contents of the /home folder.

Now for the dumb question: why is this happening? Im finding understanding mounts a bit confusing. Any recommendations for learning?

it is because you had mounted the home folder. Pay attention to the drive you mount. 
 use this instead, if you dont want someone to see the home folder as well.
```
mount /dev/hda2 /opt/shared/
```

---

### Post by moody_mark on 2008-09-15
> **k33bz said:**
> it is because you had mounted the home folder. Pay attention to the drive you mount. 
 use this instead, if you dont want someone to see the home folder as well.
```
mount /dev/hda2 /opt/shared/
```

Hi, thanks but this is what I intended, as the /dev/hda1 is the bigger "slice" of the same drive. the /opt/shared was already on /dev/hda2 as it is under /opt anyway (thats how i understand it).

So I guess my question is, if you mount two different parts of the file system on the same partition, will they see each other?

---

### Post by k33bz on 2008-09-15
I am not sure I understand what you are trying to do.

But I can tell you this, If you put in the terminal to mount hda1, then you will mount it with what ever name you give it to mount with. Which is what you have done, mounting hda1 with the name of /opt/shared

---

### Post by moody_mark on 2008-09-15
> **k33bz said:**
> If you put in the terminal to mount hda1, then you will mount it with what ever name you give it to mount with. Which is what you have done, mounting hda1 with the name of /opt/shared

I think this is where im confusing myself. Im thinking you that /home contains some files, and then you mount that lot onto a device like /dev/hda1. If I unmount /home and mounted it on another location like /dev/hdb1 for example, I would expect to still see all my home files, but I guess im wrong here?

---

### Post by eggdeng on 2008-09-15
I think you have got it exactly backwards as far as mounting is concerned. You _mount a partition to a folder_, not vice versa. The point is to make the file system on the partition available under a directory.
So when you did
```
mount /dev/hda1 /opt/shared/
```
you were making the contents of hda1 available under /opt/shared.

---

### Post by k33bz on 2008-09-15
ok I get what you are saying now. MMMMMMM, 
What you really want to do is basically provide a shortcut of just the home folder and everything in it, and have that shortcut accessible on a different partition.

tell you the truth i dont know if that is possible. I know I dont have the knowledge to pull that off. Nor have I heard of that being done.

Thanks eggdeng that was better put than what I was trying to say :)

---

### Post by moody_mark on 2008-09-15
Ok.... so, im not trying to do anything special, it was that my understanding of mounting was completely back to front.

Thank you both for your help, and sorry for confusing anyone :D

---

### Post by k33bz on 2008-09-15
No problem.

---

