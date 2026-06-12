---
title: "Desktop Thinks its the Home Directory"
date: 2008-04-21
forum: New to Ubuntu
---

### Post by SILLAT on 2008-04-21
couple days back i got some updates from ubutu an as usual i installed them an evry things ok . . tonight wen i turn on my pc all of my folders that was in my home folder eg. Music Document, an program files are all spead out over my desktop . . my destop is full of folders like music, gpass,rkhunter and so much more other files that was in my home folder.
when i got to places --> Home folder i see desktop filesystem music an all them other folder yet still they r on my desk top ...
i didnt copy any of them to my desktop and if i delete any of the folders on my desktop they completely move off the system...
another thing if i try to create a file in my home directory it goes straight to my desktop
 why is that so? does anyone kno wat caused this or wat happen can it be fixed...i'm kinda new to ubuntu can i get som simplified steps to fix this problem

---

### Post by Vadi on 2008-04-21
I don't know what caused that, but I know Ubuntu Tweak has an option to enable that. So getting it and disabling that option could do the trick:

[http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.2.10-1%7Eppa1_all.deb](http://ubuntu-tweak.googlecode.com/files/ubuntu-tweak_0.2.10-1%7Eppa1_all.deb)

Then go to applications - system tools - ubuntu tweak, desktop, desktop icons, and disable "use home folder as desktop".

---

### Post by SILLAT on 2008-04-21
i hav ubuntu tweak already installed . .
jus tried wat u said but the box is already UNCHECKED
got anymore ideas:(

---

### Post by 3rdalbum on 2008-04-21
Have you maybe been playing around with gconf-editor?

Press Alt-F2 and type in "gconf-editor". Press Ok. In the left panel, go to apps > nautilus > preferences.

In the right-pane, you'll see an option called "desktop_is_home_dir". This should have a tick in a box next to it. Click that little box and everything should go back to normal.

---

### Post by SILLAT on 2008-04-21
thnx man but that dont seem to work either
take a look at this thread here (below): [http://ubuntuforums.org/showthread.php?t=757894&highlight=desktop+thinks+home](http://ubuntuforums.org/showthread.php?t=757894&highlight=desktop+thinks+home)
see if u can simplify it a bit so i can understand and try it

---

### Post by laffinet on 2008-04-21
Alright, to translate that other post into easy chunks:

- open a terminal (Alt+F2)

go to /home/[username]
```
cd /home/[username]
```

enter
```
mkdir Desktop
```

go to /home/[username]/.config
```
cd /home/[username]/.config
```

edit user-dirs.dirs
```
sudo gedit user-dirs.dirs
```

find the line that starts with 
XDG_DESKTOP_DIR

make sure it says
XDG_DESKTOP_DIR="$HOME/Desktop"

Save the file

Reboot

---

