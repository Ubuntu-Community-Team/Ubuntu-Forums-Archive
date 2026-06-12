---
title: "Monsterz:  pygame.error"
date: 2008-11-09
forum: New to Ubuntu
---

### Post by Joe Soap on 2008-11-09
I've just upgraded to Ibex and cannot run monsterz anymore.

When I start it from the command line, this is the output:

```
Traceback (most recent call last):
  File "/usr/share/games/monsterz/monsterz.py", line 1998, in <module>
    main()
  File "/usr/share/games/monsterz/monsterz.py", line 1993, in main
    monsterz.go()
  File "/usr/share/games/monsterz/monsterz.py", line 1271, in go
    iterator()
  File "/usr/share/games/monsterz/monsterz.py", line 1381, in iterate_menu
    self.copyright_draw()
  File "/usr/share/games/monsterz/monsterz.py", line 1300, in copyright_draw
    system.blit(scroll, (13, 437))
  File "/usr/share/games/monsterz/monsterz.py", line 403, in blit
    self.background.blit(surf, coords)
pygame.error: Surfaces must not be locked during blit
```

Any ideas what the problem is and how it can be solved?

---

### Post by MasterSander on 2008-11-09
try reinstalling

---

### Post by Joe Soap on 2008-11-09
Have done that already.  No luck ...

---

### Post by R33D3M33R on 2009-02-19
The solution is described here: [http://cvs.fedoraproject.org/viewvc/devel/monsterz/monsterz-0.7.1-blit-crash.patch?revision=1.1]("http://cvs.fedoraproject.org/viewvc/devel/monsterz/monsterz-0.7.1-blit-crash.patch?revision=1.1")

Just edit the file /usr/share/games/monsterz/monsters.py (replace the lines with -, with those with +) and it should work!

---

