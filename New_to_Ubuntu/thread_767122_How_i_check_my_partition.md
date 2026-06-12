---
title: "How i check my partition"
date: 2008-04-25
forum: New to Ubuntu
---

### Post by rgotten on 2008-04-25
How do i check my partions, I have 2 raid 1 and 3 raid 5, and would like to know how i check my partitions

Thanks

rgotten

---

### Post by ofb on 2008-04-25
In terminal enter this to list your partitions,
sudo fdisk -l

I don't have RAID, but I think that should still work.

---

### Post by rgotten on 2008-04-25
Thanks, how can i break the screen..It went so quickly that i could not see everything?

rgotten

---

### Post by ofb on 2008-04-25
If you open a terminal on your desktop, you should have a scrollbar.

If you need to break a regular screen, the Pause/Break key is over on the right, top row. 'PrtScn, ScrLk, Pause'. Hit space to resume, if I remember right. 

... I think ScrLk (Scroll Lock) does the same thing, but both start and stop. (It's been a while :) )

---

### Post by rgotten on 2008-04-25
Sorry maybe i did not express my self well, i have 6 partitions, when i hit teh fdisk -l comand it appears so qucikly that i only see the last 3 partitions. How can i go up or scroll up, or make it go and show me 3 partitions first and then 3 other, like in windows, you can do dir/p or dir/w..thanks

rgotten

---

### Post by ofb on 2008-04-25
Sorry, I don't remember the unix versions of /p and /w

If you will open a terminal application within a GUI session, then that terminal will have a scrollbar. Like from Menu > Accessories > Terminal. If you or someone else has turned the scrollbar off, you can re-enable it through preferences, just right-click. Also you can scroll the output with the scrollwheel of your mouse. Hope that helps.

---

### Post by rgotten on 2008-04-25
I am in ubuntu server, i do not believe there is a GUI...any other idea

---

### Post by Oldsoldier2003 on 2008-04-25
> **rgotten said:**
> I am in ubuntu server, i do not believe there is a GUI...any other idea

```
sudo fdisk -l | more
```

---

### Post by ofb on 2008-04-25
Try this

sudo fdisk -l | pg

Hit enter for each new page.


EDIT: aha! Thanks, Oldsoldier2003

---

