---
title: "launcher for folder"
date: 2012-03-23
forum: New to Ubuntu
---

### Post by Carnivorum on 2012-03-23
How do I make a launcher for a folder on my desktop?

---

### Post by viipu on 2012-03-23
Quote from [this]("http://ubuntuforums.org/showthread.php?t=1945127") discussion

> **Kevin McCready said:**
> To make desktop shortcuts I use the terminal. Invoke the terminal with ctrl-alt-t

Then I use a symbolic link. I do this by
```
cd ~/Desktop
ln -s ~/[directory where my file is]/[name of file]

```This make a symbolic link on the desktop to your file. 


Leave the [name of file] bit out and you've got a symbolic link to a folder. 
Hope that's what you were looking for.

---

### Post by roger_1960 on 2012-03-23
Hi

Or if you don't want to use the terminal, in Nautilus, right click on the folder (or file) and select "make a link".  Copy the file created to the Desktop folder - done!

---

### Post by Carnivorum on 2012-03-23
> **viipu said:**
> Quote from [this]("http://ubuntuforums.org/showthread.php?t=1945127") discussion



Leave the [name of file] bit out and you've got a symbolic link to a folder. 
Hope that's what you were looking for.

Got it, thanks.

---

### Post by stinkeye on 2012-03-23
...or drag the folder with your mouse middle button to your desktop.
You will get a popup to choose move copy or link.

By default a file is **moved** when drag/dropping between folders in the same 
drive partition.
When drag/dropping between folders on different drive partitions the default is
to **copy**.

[LIST]
[*]To force the file to be **moved**, hold down the Shift key while dragging.
[*]To force the file to be **copied**, hold down the Ctrl key while dragging.
[*]To create a **link** to the file, hold down the Ctrl+shft keys while dragging.
[*]To get a dialogue popup to choose whether to **move,copy or link** drag and drop with the middle mouse button.[/LIST]

---

