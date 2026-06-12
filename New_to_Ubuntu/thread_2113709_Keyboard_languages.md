---
title: "Keyboard languages"
date: 2013-02-08
forum: New to Ubuntu
---

### Post by ChickenNoodle on 2013-02-08
Hi,
I'm trying to change the language .... my keyboard is in US style and I would prefere it UK, but there are no options when I select keyboard settings...

When I click the** +**  button to add a language, its just asks for a source...

ANyone any ideas ?

Thanks

---

### Post by fantab on 2013-02-08
System Settings -> Keyboard ->  Layout Settings - click the + and choose your layout. 

What Ubuntu version are you using? It is working on all my 12.04, 12.10 and 13.04

---

### Post by ChickenNoodle on 2013-02-08
Thanks for your reply but thats the problem, when I click +...it tells me to select location...as in location of files and not my geographical location....

So its asking for a location from where to pick languages...I guess...

---

### Post by fantab on 2013-02-08
Take a look in /etc/default/keyboard ... and try changing it to UK... I am not sure but UK means Ukranian and GB means Great Britain... perhaps that is the reason why you are being asked to enter the location of the file... I am guessing here. 

to change it manually in the file use:

```
$ sudo gedit /etc/default/keyboard
```Also have a look in /usr/share/X11/xkb/symbols.. to make sure what it is...

After changing the Keyboard layout you may have to run:

```
$ sudo dpkg-reconfigure keyboard-configuration
```

See [**this**]("http://ubuntuforums.org/showthread.php?t=188761") for more detailed info.

---

### Post by ChickenNoodle on 2013-02-11
Thanks for your replies.   Well, I opened the /etc/default file and found the following:

XKBMODEL="pc105" XKBLAYOUT="gb" XKBVARIANT="" XKBOPTIONS=""

This would apprear to be right ?  Like you say gb (not UK) 
but still my keyboard layout its wrong :(

I looked in the usr/share/x11/xkb folder also....it looked fine from what I can tell.  A GB file existed, it looked to conatin the correct information !

Any further thoughts would be most appreciated !

---

### Post by fantab on 2013-02-12
Did you run the following after changing and saving the /etc/default/keyboard?

> **fantab said:**
> 
After changing the Keyboard layout you may have to run:

```
$ sudo dpkg-reconfigure keyboard-configuration
```

Also, What exactly do you want to change, Keyboard layout OR the System Language? (Perhaps I should have asked this earlier).

---

