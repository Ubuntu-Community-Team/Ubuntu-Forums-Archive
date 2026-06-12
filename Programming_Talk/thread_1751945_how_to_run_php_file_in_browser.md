---
title: "how to run php file in browser"
date: 2011-05-07
forum: Programming Talk
---

### Post by ravikanth.vva on 2011-05-07
i have the php5,apache2 and mysql installed....i just cant run the php file...i try to double click it and an endless loop of new tabs get opend......i did php myfile,php  from terminal and u know wat happens(my code)

---

### Post by satanselbow on 2011-05-07
I can only think that you php is bad and you have infinity recursing loop somewhere?

does:

```

<?php
       phpinfo();
?>



```

If you still get the error you may have a recursive virtualhost / .htaccess rewrite ;)

---

### Post by ravikanth.vva on 2011-05-07
no dude...i dont have php script in my php file...its plain html....but is double clicking the .php file the right way of runin a php file.....
..
..i thought we have to configure the sever and do some process.....im hoppin to find the process

---

### Post by ravikanth.vva on 2011-05-07
this is what happens if i open the file in firefox...and if i click ok another new tab and same screen

---

### Post by dozycat on 2011-05-07
the answer is simple you must copy your php, I believe the hello world will be best to /var/www.
And open from any navigator.....firefox is cool
localhost/hello.php

dont forget to have php packet for apache.

---

### Post by ravikanth.vva on 2011-05-07
i cant copy it..permission denied.....im new to ubuntu and sudo thing needs some practice to me....is the a way to be a root user in the normal gui

---

### Post by satanselbow on 2011-05-07
/* completely irrelevant so removed to avoid confusion */

---

### Post by ravikanth.vva on 2011-05-07
ok...now tweekin my apache...:)  i did not put the file in server...i just opend a texteditor and typed the file......i hav to submit my project on monday and i have no clue how to get startd......

---

### Post by dozycat on 2011-05-07
go to package administrator get the package:

libapache2-mod-php5

go to accesories, terminal, type:
cd /home/ravikanth/scribble/wt

sudo cp menu.php /var/www

type your password to answer to the sudo and try the link:

localhost/menu.php

---

### Post by ravikanth.vva on 2011-05-07
im getting the 404 not found error

---

### Post by ravikanth.vva on 2011-05-07
thanks man its working....i tried it without sudo...i thought 1 sudo was enought for one terminal :D

---

### Post by dozycat on 2011-05-07
I am happy you learned, know you can get the homework on time.

---

### Post by ravikanth.vva on 2011-05-07
so do i have to copy every php file and pictures and videos in to /var/www to run them.....is there a way to organise em there...i mean can we create a sub directory say library for my current project?????

---

### Post by ravikanth.vva on 2011-05-07
and if i want to edit the file i have to do it through terminal ??...i have download a book abt shell commands then???

---

### Post by ravikanth.vva on 2011-05-07
hope i could...thanks for help

---

### Post by satanselbow on 2011-05-07
open a terminal

type:

```
gksu nautilus
```

This will open up nautilus file explorer with root permission - so caution required!

get to the folder you files are in - CTRL+A to select them all CTRL+C to copy

navigation to /var/www and CTRL+V to paste ;)

---

### Post by dozycat on 2011-05-07
> **ravikanth.vva said:**
> and if i want to edit the file i have to do it through terminal ??...i have download a book abt shell commands then???

There is one tool I really like: bluefish.

Get it from package manager.

Go to terminal, and type:

Sudo bluefish

Now you can edit the file in /var/www

and magic you can see your code in colors and another tools.

---

### Post by satanselbow on 2011-05-07
It would be simple to have you public folder (ie /var/www) pointed to a folder under your home folder... but that is a tutorial all of it's own ;)

So if you need to get work done rather than server config-ing you might want to leave it until after the weekend :popcorn:

---

### Post by ravikanth.vva on 2011-05-07
> **satanselbow said:**
> open a terminal

type:

```
gksu nautilus
```This will open up nautilus file explorer with root permission - so caution required!

get to the folder you files are in - CTRL+A to select them all CTRL+C to copy

navigation to /var/www and CTRL+V to paste ;)
thanks especially "for get to the folder you files are in - CTRL+A to select them all CTRL+C to copy

navigation to /var/www and CTRL+V to paste" theres no way i could have known that......:)

---

### Post by ravikanth.vva on 2011-05-07
> **dozycat said:**
> There is one tool I really like: bluefish.

Get it from package manager.

Go to terminal, and type:

Sudo bluefish

Now you can edit the file in /var/www

and magic you can see your code in colors and another tools.
i instantly switchd to bluefish...thanks

---

