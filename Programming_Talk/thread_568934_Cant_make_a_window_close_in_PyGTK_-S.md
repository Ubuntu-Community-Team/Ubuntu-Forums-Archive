---
title: "Cant make a window close in PyGTK :-S"
date: 2007-10-06
forum: Programming Talk
---

### Post by marcos.linux on 2007-10-06
Hi, I'm developing a small program but I am having a tough time trying to solve this one thing..the program I am developing uses Glade for the interface and pygtk as language. OK so I have 2 buttons and 2 windows..

Open and Quit.

open button launches window2

inside window2 theres a close button wich should close window2 instead of window2 and window1

how can I make that happen? everytime I click on the button in window2 gtk.main_quit() gets launched and closes all windows. I tried using .destroy() but it didnt work for me.

Help plz.

---

### Post by marcos.linux on 2007-10-06
heh.....solved it by using

.destroy()==True

---

### Post by ngrieb on 2010-12-14
Thanks, exactly what I was looking for at the moment.

---

