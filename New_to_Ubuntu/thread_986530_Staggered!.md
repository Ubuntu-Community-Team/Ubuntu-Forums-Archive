---
title: "Staggered!"
date: 2008-11-18
forum: New to Ubuntu
---

### Post by cypher000 on 2008-11-18
Hi Guy's. Received my Ubuntu 8.10 Cd today and really did think that I could install it and see Ubuntu on my screen. Well I am staggered because all I got was something reminiscent of DOS with my screen showing me >Grub and waiting for me to type in something but what?

Why did I think that it would come up like windows? I have studied the Ubuntu site and noted all the lovely programs on there, but not one of them can I see. So what have I done wrong because the software installed okay on my hard drive. 

Can anyone give me a fgew pointers here or show me where there is a dummies guide to get me going? I sure hope so because I shall cry myself to sleep tonight. Regards Cypher:lolflag:

---

### Post by taurus on 2008-11-18
What's the spec of your machine?

---

### Post by cypher000 on 2008-11-18
Thanks for the reply. My machine is a Dell Optiplex 260. Pentium 4. 1.80GHZ. 1024MB memory and running Win XP Pro. I installed from the CD and tried every option on the Cd. I have failed to get the Demo or the option of installing in various ways. I did eventually get it to make a boot program to boot from the Cd, even though all the files are installed on my hard drive. All I have seen to date is DOS command lines. I have dreamed of running Ubuntu for a long time and am so dissapointed. Thanks again for coming in on this. Regards Cypher:lolflag:

---

### Post by taurus on 2008-11-18
So, you have actually already installed Intrepid on your machine but you are not able to boot it?

And when you said DOS command, you don't mean grub> thing, did you?  If it's not, can you describe what it prints on the screen?

---

### Post by The Cog on 2008-11-18
What you are describing is not normal, so you are going to have to describe it in great detail I think. You may be describing something that no-one reading has ever actually seen.

Bearing that in mind, how far did you get with the CD? When you boot it, what do you see? You should normally get a text menu asking what you want to do - try without installing, install, test memory and a few other options. I don't recall ever seeing a GRUB prompt.

---

### Post by meierfra. on 2008-11-18
at the grub prompt at boot up type:

```
find /boot/grub/stage2

find /boot/grub/menu.lst
```

and post the result. You might also try a direct kernel boot:

[http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.]("http://users.bigpond.net.au/hermanzone/p15.htm#First_method:_direct_kernel_boot.")

(type "uuid" at the grub prompt to figure out the correct  numbers for "root (hd?,?)"

---

