---
title: "Game in Eclipse file Path Problem :) ??"
date: 2012-12-12
forum: Programming Talk
---

### Post by omar farouk lakhdhar on 2012-12-12
Hello ubuntu familly ,
i am kinnda new in ubuntu .. :))) 
i am working on this game in eclipse but my stupid question is how is the path format in ubuntu. for Example in order to open file or an image or something i copied the file location for the proprieties but it's not working any help Please . :)))

thanks in advance :)))

---

### Post by omar farouk lakhdhar on 2012-12-12
it is a stupid question please help :)) ??? 21 views and no one know this :/ please i need to reply ASAP

---

### Post by philinux on 2012-12-12
moved tp programming forum.

---

### Post by PaulM1985 on 2012-12-12
Hi

Are you trying to use absolute paths or relative paths?  I would recommend that you use relative paths so that you are able to distribute your game.  Are you using Java?  If so, have you looked at including the images as resources in your JAR files?

Paul

---

### Post by omar farouk lakhdhar on 2012-12-12
hi Paul , 
this project is developed locally , it is kind of a final exam , i am creating this game using java , so absolute path will be good , relative or absolute is not the issue here , the form of the path what matter in windows it like "c://test//map.txt" something like that , how is
it in Ubuntu , sorry for this stupid question cause i am kinna of a newbie here :p 

and thanks .

---

### Post by PaulM1985 on 2012-12-12
If you use relative paths they will be the same in Windows and Ubuntu, so I would strongly recommend that you use them since you won't run into compatibility issues.

If you are using an absolute path on linux you want to do something like:
/home/yourname/yourfile.txt
for example.  You have a "/" rather than the standard C:\ that you would get on Windows.

But, as I have said, if you start coding like this you will have issues when you come to hand in your project in that it might work on one OS and not the other.  You should look at using a relative path, or use resources if you are using Java.

Paul

---

### Post by omar farouk lakhdhar on 2012-12-12
So i am using the path as follow :

/home/user/Documents/Game/map.txt

but still not reading the file wish is driving me crazy i tried every possible form that exists but still not reading the file  ??? anyone know why ???

---

