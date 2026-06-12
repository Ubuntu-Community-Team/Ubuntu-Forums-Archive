---
title: "USB mouse issues"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by BOMEz on 2008-06-08
I have 2 small annoyances right now with Ubuntu:

1. For my USB mouse to work with the OS it needs to be plugged in before I power on my laptop. If I plug it in once its started its just dead...I don't even see the red infrared light coming on indicating that it is being powered. Strange thing is that it will see my USB drive no problems if I plug it in after the OS is booted up.

2. Additionally my scroll wheel button does not act as I would expect it would, ie: it does not allow me to click and drag to scroll down any page or window. It can scroll up and down just fine, but when it comes to the click functionality its way off. I noticed if I click with it, it seems to set the focus to where ever I click, additionally in text boxes if I do a middle click it just pastes whatever text I have copied in there. Is this by design or am I missing a setting somewhere?

Any suggestions as to why this is happening? Unfortunately I don't have another USB mouse to try out, and strangely all my other room mates use desktops and have PS/2 mouses.

---

### Post by Happy_Man on 2008-06-08
The middle-click functions are different. The middle-click paste is extremely useful and is a feature that is carried throughout linux (therefore it'll work in any application, use it and you'll fall in love in no time)

As for your mouse not working when inserted after the OS starts, that just seems to be a computer-specific bug. Sorry we can't help much :( .

---

### Post by BOMEz on 2008-06-08
Ah ha...so it is by design. Though is there anyway I could click and drag to scroll up and down a page? Like a key combination or something?

Additionally does anyone know how I can see devices plugged into my USB port?

---

### Post by Happy_Man on 2008-06-08
I'm not sure... maybe you could define it in keyboard shortcuts? (I never used that, so I'm afraid I can't help much.)

If you open up a terminal (Applications --> Accessories --> Terminal) and type ```
lsusb
``` it should list everything USB that is plugged in.

---

### Post by BOMEz on 2008-06-09
Awsome, thanks for that command. 

Strangely enough my USB mouse is now sometimes recognized when I plug it in after start up, but if it doesn't by entering that line of code my mouse lights up and starts working.

I was now wondering: is there anyway I could now make what would be the equivalent to a windows batch file? So I could just run that file with the code *lsusb*...you know just to make life a little more convenient?

---

### Post by gr4nf on 2008-06-10
Yes.

Go into the terminal and open up ~/.bashrc with your preferred text editor (i.e. "vi ~/.bashrc" for me). Add the line:
```
lsusb
```
at the end, and save the document. Now, the command "lsusb" is run every time you log in.

---

