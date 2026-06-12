---
title: "Just installed Ubuntu 8.04 and now XP won't boot."
date: 2008-06-26
forum: New to Ubuntu
---

### Post by Jube on 2008-06-26
Earlier today I installed Ubuntu as a Dual boot (With XP) on the same HD XP is loaded too. I gave XP something like 40gig and Ubuntu 30gig. The partitioning seemed to go fine and I got no errors during the install

Ubuntu loads fine and as far as I can tell seems to work fine. I haven't played around with it too much yet, but when I try to reboot back into Windows I can see Windows XP professional in GRUB but it hangs on the "Windows is starting up" screen. 

All my lights come on but it doesn't seem to be doing anything and doesn't get anywhere. Grub sees windows fine and if I edit the boot options (Not sure if that's the right word) I see

root (hd0,0)
savedefault
makeactive
chainloader +1

I'm not sure if changing them would help at all?

So, can anyone tell me what's gone wrong? What do I need to do to fix it? I got no errors anywhere, it all seemed to go fine, is GRUB messing with my XP? It seems to have the right data though (XP should be installed as the first partition, I think Ubuntu is on the 4th... Or something)

---

### Post by billgoldberg on 2008-06-26
Hmm, strange.

Pop in the windows xp repair disk.

And use the repair option.

It should have overwritten the grub and will boot straight into xp after you restarted the pc.

See if that works.

Make sure you have a copy of the [super grub disk]("http://www.supergrubdisk.org/") available to repair the grub afterwards.

Should that not work, well then it's a windows problem and it will be unrelated to Ubuntu.

Maybe you did something wrong when partitioning?

Or you could just use the super grub disk to boot straight into windows using the windows mbr. That could be better.

---

### Post by Jube on 2008-06-26
Yeah I'm wondering if it it was the partitioning that caused the problem. I'd been using the Windows Hard drive for quite a while (Even if it wasn't very full, I put almost all my programs on my other HDD) so I defragged it a bunch'a times before partitioning.

When I think about it though even after the defrags I still had some data around the 60% mark of my HDD, I may have given Ubuntu too much room and overwritten some of them (Or something, I'm woefully ignorant as to how resizing a partition actually works). Thanks for the advice anyhow, I'll try it out and see how it goes =D

---

### Post by flytripper on 2008-06-26
Maybe you should wipe the entire drive and have ubuntu as the host os. and run vista in virtualbox.... this would seriously take a load of headache out of the equation.
forgive me for saying this but dual booting is a bit last season now i think..
On a more helpful note I found [http://www.oo-software.com/home/en/products/oodefrag/]("http://www.oo-software.com/home/en/products/oodefrag/") to work well with preparing the windows partition for a dual boot install. its was  free to use for a month when i last used it and it now appears to support vista :)

Hope i was of help

---

### Post by Canis familiaris on 2008-06-26
> **flytripper said:**
> Maybe you should wipe the entire drive and have ubuntu as the host os. and run vista in virtualbox.... this would seriously take a load of headache out of the equation.
forgive me for saying this but dual booting is a bit last season now i think..

Yes. Especially if you can have this:
[IMG]http://i168.photobucket.com/albums/u178/anurag_panda/Screenshot-1.png[/IMG]

But dual booting is on for gaming though.

---

### Post by billgoldberg on 2008-06-26
> **flytripper said:**
> Maybe you should wipe the entire drive and have ubuntu as the host os. and run vista in virtualbox.... this would seriously take a load of headache out of the equation.
forgive me for saying this but dual booting is a bit last season now i think..
On a more helpful note I found [http://www.oo-software.com/home/en/products/oodefrag/]("http://www.oo-software.com/home/en/products/oodefrag/") to work well with preparing the windows partition for a dual boot install. its was  free to use for a month when i last used it and it now appears to support vista :)

Hope i was of help

Dual booting is for gaming and people low on ram.

On one of my pc's I dualboot Vista Home Premium and Ubuntu.

I only use Vista for gaming (counterstrike source and half life 2, moehaha).

That can't be done by virtualisation software ... yet.

---

