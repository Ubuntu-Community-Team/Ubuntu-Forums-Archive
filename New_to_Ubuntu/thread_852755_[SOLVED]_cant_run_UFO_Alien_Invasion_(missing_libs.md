---
title: "[SOLVED] cant run UFO: Alien Invasion (missing libs) ?"
date: 2008-07-07
forum: New to Ubuntu
---

### Post by tjwoosta on 2008-07-07
i found this thread and saw a game that i want (UFO:AI) 
its under "top runners"
[http://ubuntuforums.org/showthread.php?t=427205]("http://ubuntuforums.org/showthread.php?t=427205")

i downloaded the .run from the sourceforge link that was provided in that thread

it seemed to install fine

i did 
```
sh ufoai-2.2.1-linux.run
```

then a window poped up and asked me some questions like where i want to install and i installed 

when it was finished it asked me if i wanted to start the game so i clicked yes but the game never started

so i restarted ubuntu thinking maybe i just needed a restart but when i booted back up i noticed there is no menu entry for the game

so i navigated to the directory where i installed but i dont know how to start the game

this is what is in ~/ufoai
```

tj@tj-laptop:~/ufoai$ ls
base        ufo      ufo2map.x86_64  ufoded         ufo.x86_64  uninstall
gtkradiant  ufo2map  ufoai           ufoded.x86_64  ufo.xpm
tj@tj-laptop:~/ufoai$ 

```

i tried doing ./ufoai but i got this 
```
tj@tj-laptop:~/ufoai$ ./ufoai
./ufo: error while loading shared libraries: libcurl-gnutls.so.4: cannot open shared object file: No such file or directory
tj@tj-laptop:~/ufoai$ 

```
then i tried ./ufo.x86_64  (im using 64bit Hardy) but i got this
```
tj@tj-laptop:~/ufoai$ ./ufo.x86_64
./ufo.x86_64: error while loading shared libraries: libSDL_ttf-2.0.so.0: cannot open shared object file: No such file or directory
tj@tj-laptop:~/ufoai$ 

```


so first question is "am i even doing it right?"

second question "where do i get theese missing libs?"


[B]
EDIT: Nevermind I found a .deb for the same game at [www.getdeb.net](www.getdeb.net) and it installed perfectly[/B]

---

