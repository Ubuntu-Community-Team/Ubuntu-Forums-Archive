---
title: "External Hard drive mounting"
date: 2012-10-24
forum: New to Ubuntu
---

### Post by LABcqX on 2012-10-24
I got an external hard drive. I back stuff up on it. Its formatted with NTFS. When I plug the drive into Uubntu, nothing happens. When I plug into Windows the drive is listed as a connected drive in windows Explorer. Im using a usb connection. The drive is plug and play.

What causes the drive to not be listed in Ubuntu? Is this a connection problem, or is there something else that I need to be looking at?

---

### Post by NikTh on 2012-10-24
Hi , 

you can test something and see if (and how) your external HDD recognized by Ubuntu. 

You have to tell us which Ubuntu version you use . 

Do this 
Open a terminal (Ctrl+Alt+T keys combo) and then plug you HDD . Wait few seconds and then give this command to terminal 
```
dmesg | tail -n 30
```You can post here the results. Do not forget to post them between the brackets **[noparse]```
here
```[/noparse]** so can be easy to read.
Thanks

---

### Post by LABcqX on 2012-10-24
i am using the 12-4 vesion ubuntu. let me learn about this command so i understand what it does. thanks.

---

### Post by NikTh on 2012-10-24
> **LABcqX said:**
> i am using the 12-4 vesion ubuntu. let me learn about this command so i understand what it does. thanks.

This command lists all the kernel messages , but we don't want all the messages (lot of lines) we want only the 30 last lines (from the time you connect the external HDD) so the tail command will saw us only the 30 last lines we want to see. 

Give in terminal ```
man dmesg
``` and ```
man tail
``` to read about. 

Thanks

---

### Post by LABcqX on 2012-11-24
I am having diffulculty understanding this. I have been using Windows because I can't get this to work. But I have some free time over the holidays so I thought I would give Uubntu another try.

Is it possible to get the Ext HDD to appear on ubuntu Launcher or in the Nautilus when I plug in the drive? I do not know why it doesn't just pop up like it does on Windows.

---

### Post by LABcqX on 2012-11-25
> **LABcqX said:**
> I am having diffulculty understanding this. I have been using Windows because I can't get this to work. But I have some free time over the holidays so I thought I would give Uubntu another try.

Is it possible to get the Ext HDD to appear on ubuntu Launcher or in the Nautilus when I plug in the drive? I do not know why it doesn't just pop up like it does on Windows.

A classmate has showed me how to access the HDD on the ubuntu. Thank you for your help.

---

### Post by Wim Sturkenboom on 2012-11-25
Mind to share so others with the same problem can benefit in future? Make and model might be usefull as well for reference.

And after that, can you please mark the thread as solved using the thread tools just above the first post on the page ;)

---

