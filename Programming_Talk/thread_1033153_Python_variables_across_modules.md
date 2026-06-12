---
title: "Python variables across modules"
date: 2009-01-07
forum: Programming Talk
---

### Post by tom66 on 2009-01-07
In my main.py module, which is the one which is launched by me to start the program, I have this variable definition:

```

view_xpos = 100
view_ypos = 100
view_width = 800
view_height = 600

```

among other lines. Later (i.e. after the variable definitions), I import the module 'ship', which tries to use these definitions, but fails:

```

Traceback (most recent call last):
  File "main.py", line 68, in <module>
    main()
  File "main.py", line 64, in main
    player_ship.draw()
  File "/home/thomas/asteroids/ship.py", line 65, in draw
    if is_bbox_polygon(adjusted_points, view_xpos, view_ypos, view_xpos + view_width, view_ypos + view_height):
NameError: global name 'view_xpos' is not defined

```

What could be going wrong here? Any help appreciated.

Thanks

---

### Post by Tony Flury on 2009-01-07
Since the variables are defined in the main module, you should using :

```

main.view_xpos

```
And similiar to access them - after all main.py has no special significance in python

I think you can declare them as global - but, to be honest, i thhink that is bad practice, and you would be better served by at least using the "main." notation.

---

### Post by Tony Flury on 2009-01-07
Just re-read what you wrote, and the way you have things organised (with all your definition in the main module and the functionality in the ship module), then the ship module needs to import main before you can access any items defined in the main module.

If you need items from the main module in more than one other module you might want to look at doing a singleton class, so that all your modules get the same data from main.

---

