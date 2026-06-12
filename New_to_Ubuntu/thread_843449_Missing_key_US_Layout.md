---
title: "Missing key US Layout"
date: 2008-06-28
forum: New to Ubuntu
---

### Post by peshkata on 2008-06-28
Hello everybody,

I have the button "z" on my US keyboard broken, so I tried to replace it in the xkb us layout with the button next to it - less, greater, pipe : (<>|).
However, I couldn't find it in the file for US basic layout. It starts directly with AB01 - the button z. Any suggestions where I could find it ?

---

### Post by erginemr on 2008-07-10
First, please read this thread thoroughly to get acquainted with the tools xev and xmodmap:
[http://ubuntuforums.org/showthread.php?t=624051](http://ubuntuforums.org/showthread.php?t=624051)

Then, you can try the following:
1. Use xev to find out the keycode for your pipe (|) key. It turned out as 94 in my system.

2. Create a config file .Xmodmap in your home folder with:
```
Alt+F2 >> gedit .Xmodmap
```
and put the following line inside:
```
keycode 94 = z
```

3. When you close and restart the Gnome session, Xmodmap daemon will come in and ask you the configuration you would like to use. Select the one we have just created.

4. Then, you should be able to use both z and Z (Shift+z) in lieu of |.

But you will still need the pipe, greater and less than symbols in the terminal jargon. So, you should also map them to another rarely used key on your keyboard.

---

