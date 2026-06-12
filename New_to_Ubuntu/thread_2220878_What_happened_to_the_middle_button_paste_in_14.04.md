---
title: "What happened to the middle button paste in 14.04?"
date: 2014-04-29
forum: New to Ubuntu
---

### Post by benedict-m-holland on 2014-04-29
So I am going through and using highlight select middle button paste like I have done for more than 15 years and it doesn't seem to work anymore. Is there a way to change this? It seems like a really stupid change for someone to make. Having 2 copy-paste buffers was a massive benefit. Now I highlight something and middle button and it adds a space. 

Seriously. Why did this need to change? A massive amount of applications don't use ctrl-c and v like the terminal and emacs which have massive support. Can I remap the button to be paste again? It is like the UI people don't even bother with input from power users who depend on this sort of thing. Don't fix stuff that isn't broken. The inability to add a new .desktop launcher file without having to manually create it was bad enough but this change really is disruptive. 

Thanks,
~Ben

---

### Post by peter d on 2014-04-29
I don't think that anything has changed. The middle mouse button still copies the highlighted text for me on 14.04. I don't have any idea what might be causing your problem or how to solve it though.

---

### Post by Dane_Jorgensen on 2014-04-30
Mine works fine on 14.04 as well.  Maybe xmodmap?

---

### Post by kdd133 on 2015-01-24
I have an Evoluent mouse, and by default the middle click is mapped to a button other than the scroll wheel button. I've tried using xmodmap to swap buttons 2 and 9, and it seems to be working, but in my KDE desktop and in applications there is no effect -- the button mappings remain unchanged.

```
$ cat ~/.Xmodmap
pointer = 1 9 3 4 5 6 7 8 2 10 11 12 13 14

$ xmodmap ~/.Xmodmap

$ xmodmap -pp
There are 14 pointer buttons defined.

    Physical        Button
     Button          Code
        1              1
        2              9
        3              3
        4              4
        5              5
        6              6
        7              7
        8              8
        9              2
       10             10
       11             11
       12             12
       13             13
       14             14

```

Is xmodmap no longer used in Ubuntu/Kubuntu? I'm unsure what to try next.

---

### Post by greg69 on 2015-01-25
Personally I live in a middle mouse depraved world, Apart from web browsing which is now infinitely easier to open a new tab. Personally if you keep both hands on the mouse and keyboard it's a smidge of extra movement. I doubt the Devs would do it if it wasn't the right thing to do.

---

### Post by kdd133 on 2015-01-25
Nevermind, a reboot seems to have solved my problem.

---

