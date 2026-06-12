---
title: "Delete Xubuntu."
date: 2011-11-12
forum: New to Ubuntu
---

### Post by dep0 on 2011-11-12
Hi. I installed xubuntu and ubuntu in my pc and i decided to keep only ubuntu. How do i delete xubuntu?

---

### Post by WasMeHere on 2011-11-12
Hi dep0,

Did you install them as two separate systems in separate partitions? Which system did you install last? Grub is run from there, and you should think about that.

Have fun finding out!
Olle

---

### Post by PaulW2U on 2011-11-12
Did you install both Ubuntu and Xubuntu desktops onto the same installation and do you select the one you want to you at the log-in screen? Or did you install into separate partitions and select the one you want from the grub menu?

We need to know as the solutions are different.

---

### Post by dep0 on 2011-11-12
yes i did installed them as two seperate systems in separate partitions and i installed xubuntu last. so i selecte the one i want from the grub menu.

---

### Post by WasMeHere on 2011-11-12
First backup your personal data (documents pictures ...)!

Since you installed Xubuntu last, and you want to take it away, you will also lose the current grub. This kind of problem can be solved using the following link
[[COLOR="RoyalBlue"]_https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files_[/COLOR]]("https://help.ubuntu.com/community/Grub2#Copy_LiveCD_Files")

If you are prepared to do that piece of work, then just erase, reformat or delete the xubuntu partition! But of course, be sure to do it to the right partition!

Then go on ***Reinstalling GRUB2***

Have fun finding out about Ubuntu :-)
Olle

---

### Post by raja.genupula on 2011-11-12
I have one method

1...boot into Ubuntu(if you wanna keep this)
2...install the grub to ubuntu sda with this command
```
sudo dpkg-reconfigure grub-pc
```
3...open disk utility and format Xubuntu partition 
4...open your terminal and do ```
sudo update-grub
```

everything will be fine.
all the best.

---

### Post by dep0 on 2011-11-12
&#932;hank you both. I'll try raja's advice cause it looks less scary!

---

### Post by dep0 on 2011-11-12
I just read in another post that i can use gparted to delete the partition that xubuntu is installed.
This is safe for my files in ubuntu right?

---

### Post by Paqman on 2011-11-12
> **dep0 said:**
> I just read in another post that i can use gparted to delete the partition that xubuntu is installed.
This is safe for my files in ubuntu right?

Yup. Just double-check that you delte the right partition. You can also use Gparted to expand one of the partitions adjacent to the one you're deleting so that it takes up the space. Expanding partitions can be quite slow, and it's prudent to take a backup of your data first.

Alternatively you could simply format the Xubuntu partition and use it as a data storage partition in Ubuntu (this is the more cautious option)

---

### Post by BertN45 on 2011-11-12
You do not need gparted, since you can do the same with Disk Utility and that is already installed.

---

### Post by dep0 on 2011-11-12
How do i use disk utility?

---

### Post by Paqman on 2011-11-12
> **BertN45 said:**
> You do not need gparted, since you can do the same with Disk Utility and that is already installed.

You can use disk Utility to delete and/or format the unwanted partition, but to expand any adjacent partitions into the space you'll need to use Gparted from the LiveCD.

dep0: Disk Utility is pretty straightforward. Just click on your drive on the list in the left pane and you'll see all the partitions on it represented graphically in the centre of the big window. Click on the partition you want to nuke and you'll get buttons for a range of actions you could perform on it. Using Disk Utility to delete it this way has the major advantage that it will be impossible to delete the wrong partition.

---

