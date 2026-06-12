---
title: "Ho do i navigate to my downloads directory from a terminal"
date: 2008-05-03
forum: New to Ubuntu
---

### Post by Peterfc on 2008-05-03
Can anybody help 

I am trying to install Google earth for research i am doing.

I have found Ubuntu Guide and can install some things from the terminal.

Below is from Google on how to install Google Earth. It says to navigate to where i have my downloads. I keep them on my desttop but how do i navigate to the desktop from a terminal. Thanks for reading this post i refuse to go back to Windows.


3. Open a terminal window/console and navigate to your default downloads directory. Enter the following command in the directory: > sh GoogleEarthLinux.bin
4. Follow the prompts to complete the installation. The default location for the program is "/usr/local/google/google-earth." If Google Earth was installed in its default location, you can launch it using the following command: > /usr/local/google/google-earth/googleearth 

Dell Demention 2400, 2.6 Celeron, 200gb drive, 1gb ram, Ubuntu 8.4

---

### Post by spiderbatdad on 2008-05-03
```
cd Desktop
```

or: ```
cd De<tab key>
```

---

### Post by Nepherte on 2008-05-03
Navigating is done in the terminal with the 'cd' (change directory) command. Open up a terminal (the current start directory is typically the home directory):
```
cd Desktop
```

---

### Post by frup on 2008-05-03
To go to the desktop in terminal you only need to go 

*cd Desktop *

make sure it is a capital D.

cd means change directory. The terminal starts in your home directory and your Desktop is located in there.

to go back a directory go *cd ..*

to see what's in a directory go *ls* have fun.

Edit:

[http://linuxcommand.org/](http://linuxcommand.org/)
[http://www.pixelbeat.org/cmdline.html](http://www.pixelbeat.org/cmdline.html)
[http://www.ss64.com/bash/](http://www.ss64.com/bash/)
[http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9030259](http://www.computerworld.com/action/article.do?command=viewArticleBasic&articleId=9030259)
[http://howtoforge.com/useful_linux_commands](http://howtoforge.com/useful_linux_commands)

Read all those and practice and with in a week you'll almost be a pro! :D Makes learning other parts of linux a lot easier too (in other ways you could argue that is everything that you need to learn in linux).

---

### Post by hyper_ch on 2008-05-03
add the mediubuntu repos and google earth is in there... that's a lot simpler...

---

### Post by Nythain on 2008-05-03
and since no one actually bothered to mention it that i saw, that would be somewhere along the lines of

/home/<name>/Desktop
otherwise known as
~/Desktop
or
$HOME/Desktop

if you happen to find yourself somewhere other than in your home directory in the terminal ever :P

---

