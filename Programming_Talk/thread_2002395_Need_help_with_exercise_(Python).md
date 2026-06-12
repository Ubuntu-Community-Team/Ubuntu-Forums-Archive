---
title: "Need help with exercise (Python)"
date: 2012-06-12
forum: Programming Talk
---

### Post by Kritosein on 2012-06-12
Hey guys, I'm 14 and I just started learning about programming so I am completely new at Python or any other programming languages, I am very motivated and I really want to learn so I started with this topic I found in this forum.
[http://ubuntuforums.org/showpost.php?p=1984319](http://ubuntuforums.org/showpost.php?p=1984319)
From there I found a link to some hetland.org link called instant hacking and atm I am trying to learn from there (I am only at half of the page) 
but there is an exercise I should complete but I have no idea how to complete it. The exercise itself is that: ```
Write a program that continually reads in numbers from the user and adds them together until the sum reaches 100. Write another program that reads 100 numbers from the user and prints out the sum.
```

Problem with the first one is that I have no idea how to make the numbers add to itself in the loop. I basically have a working code but the problem is that I don`t know how to make it add to itself. And in the second the problem is the same. These are my codes I tried to use.
Note: I tried many codes and most of them aren't saved but 1 example on both problems: 

First one: ```
num = input("Enter a number please: ")
numenough = 100
currentnum = num
while currentnum < numenough:
    num = input("Enter another number please: ")
    currentnum = currentnum + num
print "Yay, you exceeded 100"
```


Second one:```
num = input("Enter a number: ")
allnum = num
for number in range (1,100):
    num = input("enter a number: ")
    allnum = allnum + num

print allnum
    
```


NOTE: Finally figured them both out while typing this topic :D
Typing stuff here really helps. Well anyways if you have any ideas how to make these types of codes easier then please tell me.


Oh, one more thing. I currently have a keyboard with russian layout and I have no idea how to make stars (you know like area of square is A times A. That "times" sign as well as less than and more than signs. These make writing almost any types of programs almost impossible. Is there a way I can change the keys? Thank you.

---

### Post by trent.josephsen on 2012-06-12
Glad you figured it out, I was wondering what was wrong with them because they look fine to me! :)

Incidentally, I have some variety of Eastern European keyboard at the moment, but I have it set to use the US layout. This works great for me because I can touch type on a US layout and the letters on the keys make no difference whatsoever. If you can't touch type, you could print off a reference sheet to show you where the keys are, or use masking tape to relabel the keycaps.

Most programming languages use many of the special characters on a US keyboard. Some languages also have variant layouts for programmers that make those characters (such as []{}()*_<>/\|`~#$%^&) available whereas the "normal" variant doesn't have them.

---

### Post by Kritosein on 2012-06-12
Thanks for the answer, but could you please or anyone else who reads this tell me how to change the keys in ubuntu 12.04 so that for example when I type z it does the less than sign. Because this keyboard is messed up...

---

### Post by UbuKunubi on 2012-06-12
The easy fix is to use AutoKey - its available from the software center and can help to save a lot of repetitive typing.

For example, when I work on Android development, and I need to assign a name to a button, instead of having to manualy type ```
 click = (Button)findViewByID(R.id.myBtn);
```,I simply type ```
!btn,
``` and autokey spits it out ```
 = (Button)findViewByID(
``` for me.

---

### Post by Vaphell on 2012-06-12
if you got numeric grid on the right, * should be there, or if i am looking at the right layout - shift-8. Less than, greater than are nowhere to be found o.O

look in grid icon > system settings > keyboard layout (or keyboard layout in dash)
You can preview and add layouts there

---

