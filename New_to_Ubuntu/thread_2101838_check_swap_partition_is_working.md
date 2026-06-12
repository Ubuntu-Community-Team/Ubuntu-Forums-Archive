---
title: "check swap partition is working"
date: 2013-01-05
forum: New to Ubuntu
---

### Post by faceshed on 2013-01-05
I didn't have enough space to make a swap partition when I first installed Ubuntu, but I made one now. All I did was partition a chunk as swap. Will that be recognised automatically, or is there a easy way to check it's working?

Thanks guys.

---

### Post by ibjsb4 on 2013-01-05
Look here

[https://help.ubuntu.com/community/SwapFaq#Why_is_my_swap_not_being_used.3F](https://help.ubuntu.com/community/SwapFaq#Why_is_my_swap_not_being_used.3F)

and fstab

[http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+swap+partition&as_qdr=all&sa=Google+Search&lang=en](http://www.googlubuntu.com/results/?cx=006238239194895611142%3Au-ocqbntw_o&cof=FORID%3A9&ie=UTF-8&q=install+swap+partition&as_qdr=all&sa=Google+Search&lang=en)

And welcome to the forums  :)

---

### Post by deadflowr on 2013-01-05
Open system monitor and click over to resources to view swap, or run the command line 'free -m' in a terminal.

Follow the advice in post #2 to add the swap partition to your fstab, otherwise it won't be loaded at start up.

---

### Post by faceshed on 2013-01-05
Thanks for the quick solution!
Heres my free output:
```
             total       used       free     shared    buffers     cached
Mem:       1016780     917824      98956          0      26352     381992
-/+ buffers/cache:     509480     507300
Swap:            0          0          0

```I've had enough for today, but I guess I'm going to be fixing this tomorrow.

---

### Post by faceshed on 2013-01-05
```
turnup@turnup-MK90:~$ free
             total       used       free     shared    buffers     cached
Mem:       1016780     870504     146276          0      11308     292616
-/+ buffers/cache:     566580     450200
Swap:      1075196       3584    1071612

```Yay me. I tied to follow advice about putting commands into the terminal and nothing came out like they said or did what they said it would. In the end I used gparted to "swapoff" and then "swapon" then it worked.

What I've learned today:
Avoid all advice that has anything to do with the terminal and use programs whenever you can.

---

