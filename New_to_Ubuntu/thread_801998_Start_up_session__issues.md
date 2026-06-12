---
title: "Start up/ session  issues"
date: 2008-05-21
forum: New to Ubuntu
---

### Post by Ohwii on 2008-05-21
Hi guys,

well there are some problems when I boot up ubuntu. I used the sessions preference for  most of the settings.  I attached a picture so you might have a look.
[LIST]
[*]the cairo clock is kind of messed up. I used the command: ```
cairo-clock
``` and then it looks bad.

[*] Gnome-do always loads on top. I just want it quiet so it doesnet show at the beginning. current command  ```
gnome-do –-quiet 
```

[*] after the log in theres always a 'window' loading saying *gnome* and *nautilus.* It appeared after I installed ```
star-up manager
```. unchecking bootloader menu does not work.

[*] * there is a issue that sometimes pops up, but not on the screen shot: sometimes the AWN bar is messed up instead of icons. there are multiple bars stacked.  
[/LIST]

it would be nice if someone could help 

cheers 

Oh wii

---

### Post by rburkartjo on 2008-05-21
oh i had the same problem when i upgrade to 8.04. cairo clock will not work properly if it loads up at startup but will work properly after you start up if you go to appl/access/cario. so i would suggest you go to system/pref/sessions and uncheck cario clock. now it wouldnt auto start on start up. after you have started you computer manually start cario and it will work fine/cheesemaker

---

### Post by N.N. on 2008-05-21
As for the gnome-do command: make sure that you only have two dashes in front of "quiet": ```
gnome-do --quiet
``` Right now it looks as if you have three, or an em-dash and a regular dash. :-?

---

### Post by Ohwii on 2008-05-21
thanks for the post. 

most unfortunate with the cairo clock, but what can you do? ...

Well there is way to let the cairo clock to work. there is some program that gets in the way of cairo, therefore if it could wait for 10 sec before it starts it should work . I used ```
sleep 10; cairo clock 
``` did not work yet. i am working on it. 

concerning the gnome do command. actually there should be only 2 dashes. I do not know what a emdash is but i will copy your text. and it should work. ... and it worked 

thanks again for the help 
2 down 1 and half to go ! ;)

---

