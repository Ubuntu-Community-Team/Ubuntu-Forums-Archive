---
title: "SD format"
date: 2008-06-26
forum: New to Ubuntu
---

### Post by chadwit on 2008-06-26
Anyone know if it's possible to format an SD card plugged into a USB port? I can see it in the computer browser and see the files, but there's a ton of files I see on it in Windows that Ubuntu doesn't so I just want to wipe it. If formatting is possible, how do I switch to the card in terminal and what would the command be to reformat?

Thanks...

---

### Post by paul101 on 2008-06-26
in the terminal:

```
sudo apt-get install gparted
```



**[COLOR="Red"]edit: couldnt you just go into windows, go to "my computer" right click and select "format"??[/COLOR]**

---

### Post by chadwit on 2008-06-26
Yea, I could do it in Window$ but ultimately I'm looking to just eliminate it entirely. I need to be able to do everything in Ubuntu that I currently do there.

What do I do with gparted once it's installed?

---

### Post by paul101 on 2008-06-26
just switch it to your memory card (so that your not erasing your hard disk :lolflag: )


and format it to whatever you want :)

---

### Post by Warpedflash on 2008-06-26
in gparted there is a drop down list on the top right. make sure that you select the sd card in there. then you need to unmount the sd card (right click the main bar and click unmount) then format and partition to your hearts content :D

---

