---
title: "[SOLVED] Am I root?"
date: 2008-06-21
forum: New to Ubuntu
---

### Post by HyperDriven on 2008-06-21
I am getting an error message in the terminal, whenever I use the code 

```
apt-get install x.y.z
```

It says 

```
Could not open lock file (permission denied) , are you root?
```

I am the only user of this pc, so I am guessing there would be a way to make me the 'root' user? :confused:

---

### Post by atomkarinca on 2008-06-21
Try

```
sudo apt-get install x.y.z
```

---

### Post by HyperDriven on 2008-06-21
Thank you, worked first time :) Is this what I will have to do for all my installs via the terminal?

EDIT: It starts to work, and then says that it can't find the package... Where would I have to extract the package to for it to install? (I'm trying to install amarock by the way) :)

---

### Post by MasterSander on 2008-06-21
Yes you must always be root to install things on your computer, it's a protection to keep you and other people from removing files, installing bad files, ... when you type sudo you log in as root, you'll have to enter your password when asked. Type gksudo when you want to be root in a graphical application.

---

### Post by MasterSander on 2008-06-21
sudo -i keeps you logged in as root for a while. Is sometimes handy.

---

### Post by HyperDriven on 2008-06-21
Ok thanks MasterSander, will do. 

Anyone know anything about the package error?

---

### Post by MasterSander on 2008-06-21
sudo apt-get install amarok is the right package.

---

### Post by MasterSander on 2008-06-21
You don't need to extract anything yourself this way. [http://monkeyblog.org/ubuntu/installing/](http://monkeyblog.org/ubuntu/installing/) gives more explanation.

---

### Post by HyperDriven on 2008-06-21
Ah ok, thank you :) Will read up - as you see I am a total n00b ^^

---

### Post by MasterSander on 2008-06-21
Everyone once was. :P I'm still learning too. Everyone is.

---

### Post by geo909 on 2008-06-21
> **HyperDriven said:**
> Thank you, worked first time :) Is this what I will have to do for all my installs via the terminal?

EDIT: It starts to work, and then says that it can't find the package... Where would I have to extract the package to for it to install? (I'm trying to install amarock by the way) :)

Maybe it's just a typo;
Did you type
```
sudo apt-get install amaro[COLOR="Red"]c[/COLOR]k
```?

It is amar**ok**, without 'c'.

---

### Post by forestpixie on 2008-06-21
Make sure you have the repos enabled - open software sources in the system > admin menu

Enable universe, multiverse and restricted - You won't need sources or cdrom so make sure they are disabled. 3rd party tab - enable partners, on the update tab make sure you don't have backports and proposed enabled then close - it will want to reload, let it and try agioan to install amarok

---

### Post by HyperDriven on 2008-06-21
I get this error when I try to install still :-/ 
If I try ```
 sudo aptitude install amarock
``` 
it starts to unpack, and gets as far as building the tag database. Then it says there is no package, and 0B will be used.

EDIT: @ Geo - thank you for pointing that out, it all works smoothly now. 

Sorry for wasting everyones time, I need to learn to spell :(

---

### Post by The Cog on 2008-06-21
Can you post the whole command/response here?

---

### Post by geo909 on 2008-06-21
That's what I am talking about, it is not "amarock" with a 'c', it is "amarok".

EDIT: sorry, didn't see your answer to me. Though, you still post it wrong at your last post (#13)

---

### Post by geo909 on 2008-06-21
> Sorry for wasting everyones time, I need to learn to spell 

Haha, it's not your problem, it's all those KDE programs..
If you make a calculator for kde it will be kalculator.
If you make a program that copies dvds it will be kopydvds and so on. :)

---

