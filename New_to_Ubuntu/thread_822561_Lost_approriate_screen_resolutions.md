---
title: "Lost approriate screen resolutions"
date: 2008-06-08
forum: New to Ubuntu
---

### Post by nnjond on 2008-06-08
Hi, can anyone help me?

I have re-installed Hardy but lost all the cathode ray scrn options. I cant remember how I configiued my original install? It was simple.

Thanks

---

### Post by benfindlay on 2008-06-08
Have you tried a ```
sudo dpkg-reconfigure xserver-xorg
```

Then just follow the onscren prompts!

Hope this helps!

---

### Post by nnjond on 2008-06-08
Thanks for your interest. That command just asks a series of keyboard questions and then halts? I cant even exit.

---

### Post by mgmiller on 2008-06-08
Here is the new hardy heron gui for this stuff:


1) Right click Applications and select "Edit Menus"
2) Scroll to and select, by left clicking, the "Other" location on the left side.
3) On the right side put a check mark in the box next to "Screens and Graphics", then click "Close".
4) Go to Applications > Other > Screens and Graphics
5) On the screen tab, click the drop down next to model.
6) If you can find your model, great, if not, select "generic" at the top of the list and on the right find LCD of the correct resolution assuming it's an LCD, otherwise scroll down a bit and use Monitor of the correct resolution for CRT, or try Plug 'N Play.
If it is a wide screen monitor, don't forget to check the wide screen box.
7) Now you can find & select your resolution and refresh rate from the list on the right side. Click OK.
8 ) Go to the Graphics Card tab.
9) Click on Driver and select what you need.
10) Click the test button to make sure all is ok.
11) Click ok and you're done.

---

### Post by nnjond on 2008-06-09
Thanks for your help. This is the way I did it last time up to step 6; but then it doesn't accept my changes. I need to try and remember what I did lst time.

Thanks again.

---

### Post by nnjond on 2008-06-11
This Prob seems to be solved. Many thanks.

---

