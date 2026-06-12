---
title: "Parallel processing"
date: 2008-08-20
forum: Programming Talk
---

### Post by Qtips on 2008-08-20
Hi,

I have 3 computers at home and i want to connect them in parallel to practice the MPI parallel programming using Python. 

Is there any good tutorials out there that show how to connect 3 computers, what i need to have in order to do so, which operating system i need and all that ?

Thanks

---

### Post by mike_g on 2008-08-21
You will want a switch or a hub. Then three straight through ethernet cables to connect the computers. They should all be given a differet IP address on the same subnet. For example:
```
192.168.1.1
192.168.1.2
192.168.1.3
```and make sure the adresses arent confilcting with any othe devices on the network. Pretty much any modern OS should work for this.

Edit: dont know what that emoticons doing in the title. crappy eee pc controls o_O

---

