---
title: "[SOLVED] how do i unistall ultamatix?"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by bjhome on 2008-10-19
I have this on my computer and have read comments where it is not safe.How do i remove it?

---

### Post by armageddon08 on 2008-10-19
> **bjhome said:**
> I have this on my computer and have read comments where it is not safe.How do i remove it?
First do: 
```
sudo apt-get remove ultamatix
```
Then open up your /etc/apt/sources.list and delete the repo lines(all the lines in between the headers) :
```
#ULTAMATIX REPOS START.......
..................................
......#ULTAMATIX REPOS END
```

---

### Post by Kimm on 2008-10-19
If you need help with codecs and such, take a look at Medibuntu :)

[http://www.medibuntu.org/](http://www.medibuntu.org/)

---

### Post by bjhome on 2008-10-19
I have done this already but it is still on my desktop and in my appl. under system tools?

---

### Post by armageddon08 on 2008-10-19
> **bjhome said:**
> I have done this already but it is still on my desktop and in my appl. under system tools?

Did you install the deb file or the source tarball?
Also, what does it say when you click the Ultamatix icon under system-tools? Does Ultamatix start ?

---

### Post by bjhome on 2008-10-19
it says that ultimax is uninstalled in the terminal when i put in the first command . does this mean i just need to delete the desktop icon and one in applications , system tools.??

---

### Post by Elfy on 2008-10-19
Have you run the apt-get remove - I know you've done the other :)

You might need to purge it 

```
sudo apt-get purge ultamatix
```

---

### Post by bjhome on 2008-10-19
its all good its gone now. Thanks...can you please tell me how to remove the computer, trash and home icons off my desktop . i have them in my toolbar panel and prefer a clean desktop.

---

### Post by armageddon08 on 2008-10-19
> **bjhome said:**
> its all good its gone now. Thanks...can you please tell me how to remove the computer, trash and home icons off my desktop . i have them in my toolbar panel and prefer a clean desktop.
This should help: 
```
sudo apt-get install ubuntu-tweak
```
You will find the app under applications > System Tools. In the app you will find a tab that'll allow you to get rid of those icons as well as rename them (if you want).

---

### Post by bjhome on 2008-10-19
Many thanks

---

