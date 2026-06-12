---
title: "[SOLVED] &amp;quot;Send To&amp;quot; Nautilus script...?"
date: 2008-09-04
forum: New to Ubuntu
---

### Post by sdim on 2008-09-04
Hi,again.
Though I've already asked it before,I'm trying to find a Nautilus script that adds the right-click command "Send To",but NOT to a removable media.
I'd like to move sth to another disc partition.
The one I already have is this:[http://gnome-look.org/content/show.php/Send+to...?content=67627]("http://gnome-look.org/content/show.php/Send+to...?content=67627"),but it diplays this screenshot,whenever I try to move sth.However,I don't have a floppy disk,and I'd like to move files to other partitions (if it could move them to USB sticks,as well,it would be good).
Can anyone help,please?
Thank you.

---

### Post by quibbler on 2008-09-04
> **sdim said:**
> Hi,again.
Though I've already asked it before,I'm trying to find a Nautilus script that adds the right-click command "Send To",but NOT to a removable media.
I'd like to move sth to another disc partition.
The one I already have is this:[http://gnome-look.org/content/show.php/Send+to...?content=67627]("http://gnome-look.org/content/show.php/Send+to...?content=67627"),but it diplays this screenshot,whenever I try to move sth.However,I don't have a floppy disk,and I'd like to move files to other partitions (if it could move them to USB sticks,as well,it would be good).
Can anyone help,please?
Thank you.
Look here: [https://help.ubuntu.com/community/Nautilus_Scripts](https://help.ubuntu.com/community/Nautilus_Scripts)

Regards quibbler

---

### Post by Thelasko on 2008-09-04
I prefer [g-scripts]("http://g-scripts.sourceforge.net/").  The root-nautilus-here, and mountiso scripts are very handy.  They are bash scripts, so you can make changes to them easily.  A little knowledge in scripting and you can edit one of those scripts to make it do whatever you want.

---

### Post by sdim on 2008-09-04
Many thanks to both of you.
To quibbler: I think this might be it.I'll try it out,though,and let you know.

To Thelasko:I don't have the knowledge to make such scripts...It would be good though...

---

### Post by sdim on 2008-09-05
To quibbler : What exactly do you mean by "*_make it executable with chmod a+x moveto_*"?
I went to Properties-->Permissions-->and checked the Execute box.
Is there another way of making a script executable?
Also,I succeeded in moving folders from Home to Desktop,but it doesn't work the other way round,i.e. I can't send a file from Desktop to Home...
Any ideas?
Thanks for the help...

---

### Post by anotherdisciple on 2008-09-05
> **sdim said:**
> To quibbler : What exactly do you mean by "*_make it executable with chmod a+x moveto_*"?
I went to Properties-->Permissions-->and checked the Execute box.
Is there another way of making a script executable?
Also,I succeeded in moving folders from Home to Desktop,but it doesn't work the other way round,i.e. I can't send a file from Desktop to Home...
Any ideas?
Thanks for the help...

I hope this isn't too much information, but the terminal does everything the gui can and more. They were saying to open a termina (Applications > Accessories > Terminal) and type the command:

```
chmod a+x moveto
```

That means "**ch**ange the **mod**e for **a**ll users to e**x**ecutable for the file **moveto**"

If you want to learn the whole syntax for chmod go here>>> [http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=c/chmod]("http://www.linuxdevcenter.com/linux/cmd/cmd.csp?path=c/chmod")

And if you are wanting to learn the basics of the Terminal... check out my signature. "Terminal for Beginners" is an awesome way to learn the basics... I think it teaches changing ownership and mode also.

---

### Post by sdim on 2008-09-05
Many thanks for the clarification,anotherdisciple.
By the way,do you happen to know anything about the issue I mentioned in my previous post,i.e. how to make the Move To script function properly?

---

### Post by anotherdisciple on 2008-09-05
Yeah... I'll try to help you out on your other thread.

---

