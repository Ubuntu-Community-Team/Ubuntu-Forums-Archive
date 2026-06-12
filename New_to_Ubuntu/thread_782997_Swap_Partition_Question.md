---
title: "Swap Partition Question"
date: 2008-05-05
forum: New to Ubuntu
---

### Post by Sntacrz147 on 2008-05-05
Hello everyone! I apologize in advance for such a newbie question, but this is my first install of linux onto a laptop machine. What I have done is installed Ubuntu 8.04 from a Live CD onto about 30GB of unallocated space I created on my hard drive. Only I did not make any room for a SWAP partition. Is there any way to add swap a partition to linux after initial install? Also I am dual booting Vista :lolflag: thank you any and all!

---

### Post by SunnyRabbiera on 2008-05-05
No, you cant make a swap after you install.
If you have decent memory you really dont need swap though it does come in handy sometimes...
How much memory do you have?

---

### Post by artir on 2008-05-05
False. You can add swap. 
But if you have a decent PC, you dont need it. (I have 2 gb ram and 2 gb swao to hibernate)

TO make swap: boot from livecd, unmount a partition, shrink it and make the swap. reboot and ubuntu automaticlaly will use the swap if needed.

---

### Post by SunnyRabbiera on 2008-05-05
> **artir said:**
> False. You can add swap. 
But if you have a decent PC, you dont need it. (I have 2 gb ram and 2 gb swao to hibernate)

TO make swap: boot from livecd, unmount a partition, shrink it and make the swap. reboot and ubuntu automaticlaly will use the swap if needed.

yeh but it can harm the system thats why I usually say dont do it.

---

### Post by spydon on 2008-05-05
Doesn't gparted move the data that would be wiped out when shrinking a partition?

---

### Post by cherva on 2008-05-05
> yeh but it can harm the system thats why I usually say dont do it. How can you possibly harm your system by adding SWAP ?

---

### Post by spydon on 2008-05-05
> **cherva said:**
> How can you possibly harm your system by adding SWAP ?

Because when you shrink a partition you can loose systemdata...

---

### Post by SunnyRabbiera on 2008-05-05
> **spydon said:**
> Because when you shrink a partition you can loose systemdata...

right, I have made that mistake myself...
luckily I had backups

---

### Post by Sntacrz147 on 2008-05-05
I have 3GB of Ram, but I want to be able to hibernate or when I shut to just put into a "sleep" mode. I am a linux noob obviously, I have had courses, but never a full install and setup on my own. Could I shrink my other HD in vista and then just create it off of there?

---

### Post by Sntacrz147 on 2008-05-05
*bump*

---

### Post by Xiong Chiamiov on 2008-05-05
I think you'll be fine with 3GB.

> **SunnyRabbiera said:**
> No, you cant make a swap after you install.

> **SunnyRabbiera said:**
> yeh but it can harm the system thats why I usually say dont do it.

Then you should say what you actually mean in the first place.  It's better to let someone know that they **can** do something, just shouldn't, rather than hide the details from them.  We're not about making users stupid here.

---

### Post by Sntacrz147 on 2008-05-05
I just wanted to make the swap just in case, I am really just going to be fooling around on here trying to get more acclimated with linux. With Amarok and Firefox running I am only hitting about 285mb I believe. I also have the 8600mgt vid card to handle video intensive apps. Any suggestions of useful/cool apps that any of ya' have installed would be cool too. Thank you again!

---

### Post by Sntacrz147 on 2008-05-05
*bump*

---

