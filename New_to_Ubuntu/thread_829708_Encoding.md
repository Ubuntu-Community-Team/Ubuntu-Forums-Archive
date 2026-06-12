---
title: "Encoding"
date: 2008-06-15
forum: New to Ubuntu
---

### Post by jotnarta on 2008-06-15
Hi Everybody

I am new to ubuntu and Liunx, and I have a lot of questions, I'll start with two:

1) When open firefox browser, I found a strange keywords and letters, and I have to do it everytime I open the page. Is there any place to change the encoding permanently, so that I don't have to go to view>>>encoding>>>, and choose the proper encoding everytime?.

2) The other question is, What is .bin files? is it like .exe in windows? and how can I install them?

Your answers are higly appreciated
Thank you in advance guys
Jotnarta

---

### Post by Ub1476 on 2008-06-15
I don't know what's wrong with Firefox, but I do know what a .bin file is.

As you said, it's executable. It's usually used for propitiatory software when you have to go through licenses and such (like graphic drivers). 

They can be installed with:

```
cd /path/to/bin/file
sudo sh ./nameofbin.bin
```

Also, you can press "q" to skip long texts, like licenses.

---

### Post by Martje_001 on 2008-06-15
> **Ub1476 said:**
> As you said, it's executable. It's usually used for propitiatory software when you have to go through licenses and such (like graphic drivers).
That's not always true. It doesn't *have* to be. You can make it executeable my chmod'ing it in a terminal or selecting it in the properties menu of nautilus.

You can reset Firefox to its defaults by removing the .mozilla directory in your home folder.

---

### Post by jotnarta on 2008-06-15
> **Martje_001 said:**
> 
You can reset Firefox to its defaults by removing the .mozilla directory in your home folder.

And I'll have the proper encoding? (i.e. I will not have to change the encoding from the view menu each time I navigate to/from a page?

---

### Post by Martje_001 on 2008-06-15
I'm not sure, but I think so, yes.

---

### Post by jotnarta on 2008-06-15
I am sorry, I searched for .mozilla directory, but I didn't find it!
Would you please to tell me where could i find it exactly, sorry for inconvenience but I am a newbie for Ubuntu and it's file system

---

### Post by Martje_001 on 2008-06-15
Ok, go to your home-folder (Locations --> Personal Folder, I think) and press *CTRL + H* (shortcut for *show hidden files and folders*). Now you should be able to see the mozilla-folder. Select it and press *delete*.

For a terminal:
```
rm -r ~/.mozilla
```

---

