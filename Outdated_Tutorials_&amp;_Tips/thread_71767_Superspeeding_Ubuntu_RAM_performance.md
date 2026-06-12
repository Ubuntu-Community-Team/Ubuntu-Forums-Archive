---
title: "Superspeeding Ubuntu RAM performance"
date: 2005-10-04
forum: Outdated Tutorials &amp; Tips
---

### Post by xthaparian on 2005-10-04
I have been watching for quite some time that the speed of the Linux system is generally slow as compared to Widows because it uses swap more rapidly than RAM.
So I discovered a great article as to how to increase the performance of Ubuntu 5.04 Horay and other linux systems.
I am extremely happy with the performance tuning and You will see great improvement.
Follow this link

PART-I
[http://www.linuxjournal.com/article/8308]("http://www.linuxjournal.com/article/8308")

PART-II
[http://www.linuxjournal.com/article/8317]("http://www.linuxjournal.com/article/8317")

PART-III
[http://www.linuxjournal.com/article/8322]("http://www.linuxjournal.com/article/8322")

Then let me know what you think ?
Any suggestions and improvements over this method?
:cool:

---

### Post by frodon on 2005-10-04
It seems interesting, but is it still interresting if your system never use swap memory (in case of enought RAM memory) ?
Sorry to answer with a question but it's the first thing that i thought.

However it's a really interesting article.

---

### Post by xthaparian on 2005-10-04
[QUOTE=frodon]It seems interesting, but is it still interresting if your system never use swap memory (in case of enought RAM memory) ?
Sorry to answer with a question but it's the first thing that i thought.

However it's a really interesting article.[/QUOTE]


Well thats the Case.

Linux by defauly relies more on SWAP than memory. If you read the website PART-I you will see the RAM usage was consistant but swap changed, if you fireup an application. So no matter if you have high RAM it will still rely more on SWAP.

So thats the point of changing reliance on RAM instead of SWAP with this tutorial

---

### Post by az on 2005-10-04
Even with only 128 megs of ram, my system rarely swaps.

It runs faster than windows, too. (Out-of-the-box)

If I add another 128 megs, it pretty much never swaps.

---

### Post by xthaparian on 2005-10-04
Did you do this on your PC??

$ sudo cat /proc/sys/vm/swappiness

Check the value. If the value is small then you are fine, but if its 60 or something else, the you are definatly using more SWAP.

I installed supekaramba and saw sudden spike in CPU usage and it would always be at 5-10% range because it was accessing HDD all the time.

It went down with the usage of this command.

Read all the Article and let me know if otherones are good too..

Thats the whole point of this article is to get your feedback and other stuff.

Thanks

---

### Post by frodon on 2005-10-04
[QUOTE=xthaparian]Well thats the Case.
Linux by defauly relies more on SWAP than memory. If you read the website PART-I you will see the RAM usage was consistant but swap changed, if you fireup an application. So no matter if you have high RAM it will still rely more on SWAP.
So thats the point of changing reliance on RAM instead of SWAP with this tutorial[/QUOTE]Ok, i ask that because like azz my computer really rarely use swap memory (maximum 10%).

---

### Post by floyd27 on 2005-10-04
i have 512 ram and whenever i look at the swap it always has 100% free. (1.5Gig swap) 
I did your command and it gave me 60..? i dont know what that is but im still using no swap?

---

### Post by tktreload on 2005-10-04
hi

my computer also has 512 megs og ram, and rarely uses swap, only after being idle all night. Then some of the data gets written to swap, and then its only about some megs...otherwize it's allways around 0-1.0%

also the swappiness cat thing puts out the value 60 and swapon -s outputs:
Filename                                Type            Size    Used    Priority
/dev/hda1                               partition       979924  2776    -1
this corrosponds to about 0.3%
so the value of the swappiness file has nothing (apparently) to do with the swap usage

---

### Post by mossholderm on 2005-10-04
I ran into thswappiness setting a while ago, while working on a different issue. The symptoms were that it would take forever to get back to a useable desktop after the system had been idle for a long period of time (say, over night). 
In the end I figured out what was happening... during the idle time, my system was being backed up. The kernel was swapping all of the idle apps out to disk, to make room for buffer space to facilitate disk copies for the backups. When I came back to the PC, it would need to swap all of the apps back in to draw the screen. 
By changing the swappiness to a lower value, I was able to achieve a good mix of desktop response and backup performance.

---

### Post by smack on 2005-10-04
[http://kerneltrap.org/node/3000](http://kerneltrap.org/node/3000)

I'm of the opinion that it's not worth adjusting. The above link is good material on which to form an opinion.

---

### Post by Joey French on 2005-10-04
Mine gives a value of 60. What would be a good way to boost performance? What value would you suggest, or should it be changed at all?

Thanks,
Joey

---

### Post by heimo on 2005-10-04
Personally I prefer to add this to my crontab-daily:
```
echo $((`date +%e`*3)) > /proc/sys/vm/swappiness
```

I feel that I need more swappiness at the end of month and less at the beginning. ;-P (Sorry, this is my attempt at "geek-humour").

---

