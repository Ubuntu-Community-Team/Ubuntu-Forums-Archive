---
title: "Stupid tar Question"
date: 2012-09-22
forum: New to Ubuntu
---

### Post by congnelius on 2012-09-22
Hello All,

I'm new here and hope to become a contributing member in time, but for now you'll have to put up with my stupid questions :)

I'm doing something very simple here just to get used to the OS (Running 32-bit 12.04.1 LTS). I've created [B]~/Documents/file.txt
[/B]
I then compress it using [B]tar -czvf backup.tar.gz ~/Documents

[/B]No errors. Next I delete the file **~/Documents/file.txt**

I try to unpack it with **tar -xzvf backup.tar.gz**

I check for the file and I can't see it under **~/Documents/** or just under **~/**

Am I doing something wrong? It seems like it should be pretty straightforward. Just to throw a wrench in to things, I opened the tar.gz file in the GUI and tried to extract **file.txt** to **~/** and got a message asking if I wanted to replace the file! I don't see it in the GUI either!

---

### Post by coffeecat on 2012-09-22
Here's your mistake:

> **congnelius said:**
> 
I then compress it using [B]tar -czvf backup.tar.gz ~/Documents

If you are already in your home folder in the terminal, you need to use:

```
tar -czvf backup.tar.gz Documents
```

If you look in your home folder you'll see that a folder called "home" has appeared, and inside that.... Put another way, what you created after you extracted the tar.gz file is:

/home/yourname/home/yourname/Documents/file.txt

Which is entertaining, at the very least! :)

If you want to experiment with tar, I suggest you create a special folder in home and work inside that. Creating and unpacking the tarball the way you describe might overwrite your original Documents folder and you'll lose the document icon on the folder icon.

---

### Post by congnelius on 2012-09-22
You're absolutely right! I hadn't even noticed that. It makes complete sense now. I was packing the entire path thinking I was only packing the Documents folder.

Thank You very much coffeecat! I thought I was going crazy.

---

