---
title: "python game problem"
date: 2008-10-19
forum: New to Ubuntu
---

### Post by cosine352 on 2008-10-19
Hi all,
I was trying to play this game. [http://www.pygame.org/project/881/](http://www.pygame.org/project/881/)
I have downloaded the source file and did the unzip. when I run 

> python src/pydza.py

It gives this error
> laptop:~/python/pydza-0.2.2$ python src/pydza.py 
Traceback (most recent call last):
  File "src/pydza.py", line 34, in <module>
    import main_menu
  File "/home/user/python/pydza-0.2.2/src/main_menu.py", line 29, in <module>
    import world
  File "/home/user/python/pydza-0.2.2/src/world.py", line 34, in <module>
    import game
  File "/home/user/python/pydza-0.2.2/src/game.py", line 35, in <module>
    import level
  File "/home/user/python/pydza-0.2.2/src/level.py", line 31, in <module>
    from map import *
  File "/home/user/python/pydza-0.2.2/src/map.py", line 26, in <module>
    from actors import *
  File "/home/user/python/pydza-0.2.2/src/actors/__init__.py", line 32, in <module>
    from player import *
  File "/home/user/python/pydza-0.2.2/src/actors/player.py", line 23, in <module>
    from mini_star import *
  File "/home/user/python/pydza-0.2.2/src/actors/mini_star.py", line 27, in <module>
    class MiniStar(Actor):
  File "/home/user/python/pydza-0.2.2/src/actors/mini_star.py", line 30, in MiniStar
    masks[1] = pygame.mask.from_surface(pydzafw.load_image(os.path.join('blocks', 'star1-mask.png')))
AttributeError: 'module' object has no attribute 'mask'


Does anyone has any idea? Help will be appreciated. 

Thanks

---

### Post by neurostu on 2008-10-19
Yes those are python errors. They mean that the python script cannot find the correct files its trying to import. Try:
```

cd src
python pydza.py

```
If that doesn't work make sure you downloaded all the files you needed.

---

### Post by cosine352 on 2008-10-19
> Yes those are python errors. They mean that the python script cannot find the correct files its trying to import. Try:
Code:

cd src
python pydza.py

If that doesn't work make sure you downloaded all the files you needed.

still not working. Anyway thanks though.

---

### Post by unutbu on 2008-10-20
Notice in the error message:
```

masks[1] = pygame.mask.from_surface(pydzafw.load_image(os.pat h.join('blocks', 'star1-mask.png')))
AttributeError: 'module' object has no attribute 'mask'

```
it is saying pygame has no attribute called 'mask'.

According to [http://www.pygame.org/docs/ref/mask.html](http://www.pygame.org/docs/ref/mask.html)
pygame.mask is "New in pygame 1.8".

So run 
```
apt-cache policy python-pygame
```

If it shows that you have pygame version less than 1.8, then you need to upgrade your pygame installation to version >= 1.8.

It appears Hardy ships with version 1.7.1 and Intrepid ships with version 1.8.1.

If you are using a pre-Intrepid version of Ubuntu, there is a .deb available [https://bugs.launchpad.net/ubuntu/+source/pygame/+bug/209967](https://bugs.launchpad.net/ubuntu/+source/pygame/+bug/209967) 
but it comes from an unknown source. To be safe, you would be better off installing it from the .tar.gz source: [http://www.pygame.org/ftp/pygame-1.8.1release.tar.gz](http://www.pygame.org/ftp/pygame-1.8.1release.tar.gz) (See [http://www.pygame.org/download.shtml](http://www.pygame.org/download.shtml))

---

