---
title: "sidebar/verticalbar?"
date: 2008-07-16
forum: New to Ubuntu
---

### Post by Toliot on 2008-07-16
hey,
Are there any good side bars out there for ubuntu?
i mean like the vertical bar that tells u system info(how much ram is being used,how much pc is being used etc...)
and are there any music players that are like sidebars(ive seen them jus dont no wat there called)?
thx in advance:)

---

### Post by jbrown96 on 2008-07-17
I think the package you want is called screenlets ```
sudo apt-get install screenlets
``` There are quite a few options for system monitors and plenty more you can install via the internets.

---

### Post by Dutch70 on 2008-07-17
You may want to read up about screenlets, before you install them. not sure if this is correct, but I read somewhere that the are  "very, very, beta," (exact words) and can mess up alot. Also that it would take a power user to uninstall them.
 
 I'd really like it if someone proved me wrong on that...:lolflag:

---

### Post by UbuntuNerd on 2008-07-17
Here is everything you need to know about screenlets and i agree with  dutch70 you really have to know how to uninstall it if you're not completely happy with it 

[http://www.screenlets.org/index.php/FAQ]("http://www.screenlets.org/index.php/FAQ")

---

### Post by aktiwers on 2008-07-17
GoogleSidebar is okay i guess.

But I like Conky best. If you dont know how to configure it, you could start by installing it:
 ```
sudo apt-get install conky
```Then go here and find one you like:
[http://ubuntuforums.org/showthread.php?t=281865](http://ubuntuforums.org/showthread.php?t=281865)

And copy/paste it into .conkyrc (wich is properbly empty right now)
```
gedit .conkyrc
```copy/paste the one you liked into it

And start conky:
```
conky
```Thats also the way I learned to make my own. The code in the .conkyrc actually makes a lot of sence :)

---

