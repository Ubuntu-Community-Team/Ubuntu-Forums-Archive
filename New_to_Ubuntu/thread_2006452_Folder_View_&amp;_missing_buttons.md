---
title: "Folder View &amp; missing buttons"
date: 2012-06-19
forum: New to Ubuntu
---

### Post by coming_curse on 2012-06-19
Salve!

I tried a search but didn't come to useful results so...

1) I like to change the view of items in the folders so that I get a list instead of previews for every single file. One reason is that I don't like the long time it takes to create all the previews and another is that i like to see some of the details of the files (e.g. size, date or whatever needed).

Is there a possibility to get the list and if so how do I do it?

2) If I arrange a window to one half of the screen by moving it to the side (when the yellow frame appears so it is resized automatically) and later klick on the button to maximize it again, all the buttons disappear (min, max, close). Is there something wrong or do I do something wrong?

As I'm new to Ubuntu I don't know where to look for the stuff I miss so I hope you can help me out here ...

Thanks

---

### Post by stinkeye on 2012-06-19
Move your mouse to the top left and the menu and buttons will appear.
Choose your viewing style in Edit > Preferences
You can also hit alt and then start typing preferences.
The alt button shows the hud, where you can search the menu of the currently focused window.

---

### Post by coming_curse on 2012-06-19
Okay the preferences work.

The problem with the buttons is that after maximizing they do not reappear as you said. Previously they did ... 
One time when I started Wine this happened with all windows simultaneously and I didn't find any way of getting them back but restarting...

---

### Post by stinkeye on 2012-06-19
Not sure the cause.
When they disappear, try opening a terminal and running
```
gtk-window-decorator --replace & disown
```

or with alt+F2 just run
```
gtk-window-decorator --replace
```

Doesn't work...reload compiz...alt+F2
```
compiz --replace
```

Keeps happening try alt+F2
```
unity --reset
```
You will lose any compiz customizations with the **unity --reset** command.

---

### Post by coming_curse on 2012-06-20
```
compiz --replace
```
This one works ...
Is there a way of eliminating the error? I`m using the resizing functions quite often ...

Thanks a lot

---

