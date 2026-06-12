---
title: "xfce &amp; mousepad?"
date: 2008-06-03
forum: New to Ubuntu
---

### Post by totlinuxnewbichik on 2008-06-03
Hi. Can anyone help me out here?

I am using xfce on an older Dell laptop, and I can't get any of my .txt files to open with mousepad. Has anyone heard of this before? :frown:

Thanks in advance.

---

### Post by wolfen69 on 2008-06-03
if you dont need printing support, try leafpad, which mousepad is based on. otherwise i cant help. there are many text editors out there.

---

### Post by totlinuxnewbichik on 2008-06-04
Printing would be a nice thing to be able to do too, but mostly I just want to be able to take a quick note here and there. I used to use notepad like 10 or 15 times a day.

I will try leafpad as you suggested, and see if I can access the .txt files  with it.

Thanks.


P.S.
Why doesn't leafpad come with printing capabilities?

---

### Post by Oldsoldier2003 on 2008-06-04
> **totlinuxnewbichik said:**
> Hi. Can anyone help me out here?

I am using xfce on an older Dell laptop, and I can't get any of my .txt files to open with mousepad. Has anyone heard of this before? :frown:

Thanks in advance.

try setting the "opens with" property for a .txt file through Thunar

---

### Post by sayakb on 2008-06-04
```
mousepad /pathtofile
```
Or simply drag n drop the file on mousepad.

---

### Post by mikewhatever on 2008-06-04
Where were those txts on the disk? Can you find other files?

---

### Post by totlinuxnewbichik on 2008-06-05
thanks for all the great feedback, everyone.

Switching to Leafpad didn't solve the problem, and dragging and dropping is
a no go (which could be an entirely different problem to solve? )

I will check into Thunar.

---

### Post by totlinuxnewbichik on 2008-07-04
This problem is solved, as well as a few others.

I added more memory to my laptop so I could go with ubuntu hardy instead of xubuntu and I ended up using Tomboy notes anyway.

Thanks to all who replied :KS

---

### Post by ChameleonDave on 2008-07-04
> **totlinuxnewbichik said:**
> Hi. Can anyone help me out here?

I am using xfce on an older Dell laptop, and I can't get any of my .txt files to open with mousepad. Has anyone heard of this before? :frown:

Thanks in advance.

OK, you say it doesn't work, but what happens?

Let's say you have a file on your desktop called Note.txt.  You should be able to open it with any of the following commands from the command line:

```

nano ~/Desktop/Note.txt

mousepad  ~/Desktop/Note.txt

gedit  ~/Desktop/Note.txt

kate ~/Desktop/Note.txt

```

If you are missing any of these programs, it is childsplay to install them using Synaptic.

---

### Post by totlinuxnewbichik on 2008-12-22
Yes Dave, ty. At the time, I had no idea whatsoever about using the command line. I still don't know what you mean by Synaptic. I know it's all childsplay to you, but not to me! I DID try to choose a user ID that lets everyone know how new I am at this. FAIL ? lmao

---

