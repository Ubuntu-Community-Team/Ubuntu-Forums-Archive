---
title: "killall -i[id] init command working ?"
date: 2015-11-13
forum: Programming Talk
---

### Post by Abdul_Haseeb on 2015-11-13
when i use killall -1 init command in terminal it will give me an error that   " init(1): Operation not permitted "

  for i in `seq 1 100`;
        do
                killall -$i init
        done  

but the above script will kill some process. Can any one guide me what actually  this command do and why it will restart my system when i run this script ?

After several runs of the script my system became halt, i want to know that reason ? 

i am not using sudo permission.

---

### Post by Habitual on 2015-11-13
[COLOR=#663333]init 1  :[/COLOR]   Single user mode or emergency mode means no network no multitasking is  present in this mode only root has access in this runlevel

[http://www.krishnababug.com/2009/04/what-are-init-0-init-1-init-2-init-3.html](http://www.krishnababug.com/2009/04/what-are-init-0-init-1-init-2-init-3.html)

Not a very 'smart' script. What are you trying to achieve?

---

### Post by Abdul_Haseeb on 2015-11-14
i have an assignment to crash the kernel from user mode so i find this script that&#8217;s all. It is working but i want to know whats going on behind that ?

---

### Post by Habitual on 2015-11-14
Well then, carry on!

---

### Post by Abdul_Haseeb on 2015-11-15
can you guide me what that script is doing ? why and how this script crash my system ?

---

### Post by Habitual on 2015-11-15
Sorry, I cannot.
And it is considered poor manners to send PMs to folks who haven't asked you to do so.

We're volunteers, not dedicated support staff.

Good day and good luck.

---

### Post by Abdul_Haseeb on 2015-11-16
i just ask you for a help if you can not just ignore it. Is this a good manner to  advices some one publicly? just think :) Good Day Sir

---

### Post by Habitual on 2015-11-16
> **Abdul_Haseeb said:**
> Is this a good manner to  advices some one publicly?

Yes, lots of people read these posts, sometime years from now. So publicly saying "PMing is poor manners" publicly is doing not just you, but others a service.

---

