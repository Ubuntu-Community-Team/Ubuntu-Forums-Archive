---
title: "Installation Help for PowerIso"
date: 2012-07-14
forum: New to Ubuntu
---

### Post by Nekrosilisk on 2012-07-14
I wanted to install PowerIso on my laptop so i did a quick search on the forum for installation instructions.  After finding them i followed them but after extracting and attempting to use the executable I'm given an error.

the terminal command I'm using is

sudo mv -v /home/user/Desktop/poweriso
the error i receive is

mv: missing destination operand file after sudo mv -v /home/user/Desktop/poweriso

Am i missing something on the command line?

---

### Post by Cheesemill on 2012-07-14
What do you want to use PowerIso for?
There are plenty of native Linux applications that can do everything that PowerIso can do.

---

### Post by Nekrosilisk on 2012-07-14
I'm trying to install a two disk game on my comp.  I've got a native app, but wine won't recognize when i change the images.

Edit::  I currently have Furius Iso Mount and GMount-ISO installed on my computer.

---

### Post by Nekrosilisk on 2012-07-15
anyone else who can give me some help?

---

### Post by idoitprone on 2012-07-16
> **Nekrosilisk said:**
> anyone else who can give me some help?

I recommend acetoneiso2

very easy interface

click->mount-> path to iso

open ```
winecfg
```click ->drives tab

click ->add #  specify drive letter

browse-> navigate to mounted iso

highlight drive->show Advance->type #cd-rom

---

### Post by Nekrosilisk on 2012-07-16
Thanks for the help I've got the game installed now.  part of the problem was that i didn't realize had to mount the image inside wine as well.  Thanks for all the help ^^

---

