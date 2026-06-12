---
title: "Newb Installer....Yes I did search."
date: 2008-08-02
forum: New to Ubuntu
---

### Post by jcway212 on 2008-08-02
Ok, I did do some searching, but I am having issues with my confidence in installing something. 

I downloaded eschalon book 1. I have the tar.gz file...I tired to do a ./configure and a sudo make install, but nothing worked.

If anybody could help me that would be great.

Thanks,
Paul

---

### Post by collinp on 2008-08-02
can you run ls in the directory your program is in, and put the output in code tags please?

---

### Post by jcway212 on 2008-08-02
```

paul@paul-laptop:~$ cd Desktop
paul@paul-laptop:~/Desktop$ ls
Eikon.tar.gz                 ubuntu-8.04.1-desktop-i386.iso
eschalon_book_1_demo         ubuntu-8.04.1-desktop-i386.iso.part
eschalon_book_1_demo.tar.gz
paul@paul-laptop:~/Desktop$ cd eschalon_book_1_demo/
paul@paul-laptop:~/Desktop/eschalon_book_1_demo$ ls
data                         gfx.pak          music
eschalon_book_1_demo         help.html        Purchase Eschalon: Book I.desktop
eschalon.cfg                 launch_icon.png  sound
Eschalon Players Manual.pdf  license.txt
paul@paul-laptop:~/Desktop/eschalon_book_1_demo$ 



```

---

### Post by mevets on 2008-08-02
I downloaded the tar.gz from their site and I got it do work doing this.
```

sudo apt-get install libstdc++5

```
Then in the folder that is extracted you can double and run the file eschalon_book_1_demo

If this doesnt work, try dragging the file to the terminal then running it and posting the output. The only way I found out libstdc++5 was necessary was because I ran it this way and it told me that file couldnt be found.

---

### Post by jcway212 on 2008-08-02
> **mevets said:**
> I downloaded the tar.gz from their site and I got it do work doing this.
```

sudo apt-get install libstdc++5

```
Then in the folder that is extracted you can double and run the file eschalon_book_1_demo

If this doesnt work, try dragging the file to the terminal then running it and posting the output. The only way I found out libstdc++5 was necessary was because I ran it this way and it told me that file couldnt be found.

Awesome that worked...thanks man. Another question, where would I put that folder for the game and I click on the game, and it ran....but did it install? Should I install it?

---

### Post by mevets on 2008-08-02
No it didnt install. You see this a lot, especially with programs written in a language that is cross platform (like java). The company spent the time to compile it for Linux, but not to make an installer whether it be a deb package or a install script. I didnt download the Windows version but im sure an installer is offered.

Easiest way to acheive something close to the benefits you get from installing would be to move that folder into your home folder (so it doesnt litter your desktop) and setup shortcuts to it manually. You do this by Right clicking on your gnome panel > Add to Panel > Then create a custom launcher. You can do the same for the menu bar by right lcicking it then going to Edit menus.

---

### Post by jcway212 on 2008-08-02
> **mevets said:**
> No it didnt install. You see this a lot, especially with programs written in a language that is cross platform (like java). The company spent the time to compile it for Linux, but not to make an installer whether it be a deb package or a install script. I didnt download the Windows version but im sure an installer is offered.

Easiest way to acheive something close to the benefits you get from installing would be to move that folder into your home folder (so it doesnt litter your desktop) and setup shortcuts to it manually. You do this by Right clicking on your gnome panel > Add to Panel > Then create a custom launcher. You can do the same for the menu bar by right lcicking it then going to Edit menus.



 beautiful response....thank you.

---

