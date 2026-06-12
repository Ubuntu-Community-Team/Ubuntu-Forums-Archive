---
title: "personalize Ubuntu installer?"
date: 2007-08-19
forum: Programming Talk
---

### Post by youbunt2 on 2007-08-19
I just installed Ubuntu on my amd computer and I'm totally new at this so go easy on me.:)

 I was wondering if there is a program for Ubuntu that can personlize my entire system once for me so I never have to do any sort of customizations again. Like make an empty folder named "my pics" and place it in the area of the system where I like it. Empty genre folders for my music folders, my favourite taskbar settings and desktop settings get automatically set. My favourite themes get installed and set for my favourite browsers. Just anything to do with customizing is automatically done for me.

I realize I would have to do the settings once for the installer but after that if I ever have to change computers or reinstall I could just install this program and I'm ready to go.

Is there anything like what I just explained for Ubuntu?:confused:

---

### Post by raja on 2007-08-19
You can use a program called reconstructor to make a customized Ubuntu live cd with a different theme and with more programs installed, etc. However, you cant save your directory structure. 
If you have installed and set up everything, you can make an image of your hard drive so that you can get back to that state if you want to later. To do this, you can use a system rescue cd and partimage to do the image.

---

### Post by Diabolis on 2007-08-19
You could make a script that will set everything and I think it will do all what you want. you write it was and then use it as many times as needed. Create a file with the extension .sh in your home folder, probably something like personalization.sh. Now assuming that the file is in your home folder. This command will make it executable.
```
chmod +x personalize.sh
```

Lets say you want to make 3 different folders in 3 different locations, so you'll script would look like this:
```
#!/bin/bash

#this will make a folder called "my pics" in your systems folder
sudo /mkdir /my\ pics

#this one will create the same folder but it will be located in your home folder
mkdir my\ pics

#and this one will create the folder in your desktop
mkdir desktop/my\ pics
```

then you just run the script by typing
> sh personalize.sh

Probably you can change themes through commands too, but I don't know how to do that yet.

---

### Post by youbunt2 on 2007-08-19
> **Diabolis said:**
> You could make a script that will set everything and I think it will do all what you want. you write it was and then use it as many times as needed. Create a file with the extension .sh in your home folder, probably something like personalization.sh. Now assuming that the file is in your home folder. This command will make it executable.
```
chmod +x personalize.sh
```

Lets say you want to make 3 different folders in 3 different locations, so you'll script would look like this:
```
#!/bin/bash

#this will make a folder called "my pics" in your systems folder
sudo /mkdir /my\ pics

#this one will create the same folder but it will be located in your home folder
mkdir my\ pics

#and this one will create the folder in your desktop
mkdir desktop/my\ pics
```

then you just run the script by typing


Probably you can change themes through commands too, but I don't know how to do that yet.
So would that be from the text editor? I think I might do that constructor thing and then find something else to do my folders. Would an archiver work for making the empty folders? Thanks for the suggestions.

---

### Post by Diabolis on 2007-08-19
What I posted will make your empty folders. Actually you can just copy and paste the script I posted and you'll get 3 folders called "my pics". And yes, it is plain text. You can go back always and edit it with openoffice, nano, vi, gedit (I suggest this one), etc. You can also just open you home folder, right click on it, create an empty file, give a name to it and then add the **extension .sh** that will automatically make it a shell script. Just don't forget to make it executable with **chmod +x**. 

If for some reason you want to delete all the folders, you can do it really quick with another script. For example this one would remove all the folders created by the script that I posted above.
```
!/bin/bash

sudo /rmdir /my\ pics

rmdir my\ pics

rmdir desktop/my\ pics
```

---

### Post by pmasiar on 2007-08-19
> **Diabolis said:**
> 
sudo /mkdir /my\ pics


Why spaces in file names? Is it windows or what? Or is the advice somehow related to your nick? ;-)

Seriously, you will have to escape spaces, and think about that all the time. Of course these are your pics - it is your home directory, just call it pics. All lowercase please. :-)

---

