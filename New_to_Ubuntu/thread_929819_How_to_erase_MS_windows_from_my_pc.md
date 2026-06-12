---
title: "How to erase MS windows from my pc?"
date: 2008-09-25
forum: New to Ubuntu
---

### Post by kramer65 on 2008-09-25
Hello,

Since I installed virtualbox and can use windows in there for my last need (photoshop photomerge function) I have not started the windows installation which I have next to ubuntu anymore for the last year. Since my home partition is getting in need of more space I thought I would erase the useless partitions off my hard disk; MS Windows   :-)

So my questions is; how do I increase the size of my home parition to also include the space of the former windows installation? In gparted I gave the command to delete the ntfs parition of windows. But I can't seem to be able to increase the size of the /home parition to include that space as well?

Can anybody help me out with that? What do I do now?

Also, since ubuntu would be my only OS, I guess I wouldn't need grub anymore. How do I get rid of that?

---

### Post by snowpine on 2008-09-25
> **kramer65 said:**
> Hello,

Since I installed virtualbox and can use windows in there for my last need (photoshop photomerge function) I have not started the windows installation which I have next to ubuntu anymore for the last year. Since my home partition is getting in need of more space I thought I would erase the useless partitions off my hard disk; MS Windows   :-)

So my questions is; how do I increase the size of my home parition to also include the space of the former windows installation? In gparted I gave the command to delete the ntfs parition of windows. But I can't seem to be able to increase the size of the /home parition to include that space as well?

Can anybody help me out with that? What do I do now?

Also, since ubuntu would be my only OS, I guess I wouldn't need grub anymore. How do I get rid of that?

Hi Kramer, you are on the right track with GParted, you just need to run it from the Live CD because you can't resize a partition while it's in use. :)

---

### Post by coldcoffee on 2008-09-25
> Also, since ubuntu would be my only OS, I guess I wouldn't need grub anymore. How do I get rid of that?

I am a newbie to Linux myself. And I love it. I am so happy to not be relying on MS anymore. I am by no means a geek, but I am pretty sure you are still going to need grub. It is the bootloader - hope that is the correct terminology. You are still gonna have to be able to boot up your computer.

---

### Post by TriSwords on 2008-09-25
You will still need GRUB, even if you only have Ubuntu on your system. Dont delete it.

---

### Post by Idefix82 on 2008-09-25
What you will be able to do once Windows is gone is edit the /boot/grub/menu.lst file and delete the menu entry for Windows. I guess you can then also set the timer of the boot loader to some low value like 2 seconds, rather than the default 10 secs. Feel free to ask if you need more detailed instructions on how to do these things.

---

### Post by kramer65 on 2008-09-25
ok. So lets start with erasing windows. I need to do it from a live cd. I think I still have that lying around. After that I will come back to this threat to let you guys know what I did and so that I can go on with the grub thing.. :-)

Thanks for now!

---

### Post by twitch2197 on 2008-09-25
> **TriSwords said:**
> You will still need GRUB, even if you only have Ubuntu on your system. Dont delete it.
i concur. NEVER delete grub. i have linux-only computer and it still boots with grub. The function of grub is to boot the computer... without it you'll get an error and your computer will become unbootable.

---

### Post by snowpine on 2008-09-25
```
gksu gedit /boot/grub/menu.lst
```

That will let you edit your grub menu. The "chunk" of code to boot Windows is pretty easy to find; just delete the entire 3- or 4-line chunk (there may be a 2nd "chunk" for Windows recovery mode, delete that too). 

Near the top of the menu.lst file, you'll see where you can change the timeout. 2 seconds should be plenty. :)

---

### Post by kramer65 on 2008-10-08
We are a bit later now and it may not be relevant anymore. I just wanted to say that although it took very long (5 hours) to delete the partition and resize the existing partition, everything worked out fine in the end.
I just changed the grub menu as well so it doesn't include windows anymore and so that it only takes 2 seconds for me to choose. Although I haven't tested that yet, I don't expect any problems with that.

Thanks anyway!

---

