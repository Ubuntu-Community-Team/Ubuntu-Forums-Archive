---
title: "Pygame: draw.lines has huge pointlist"
date: 2012-04-27
forum: Programming Talk
---

### Post by baumanno on 2012-04-27
Hi together,

I'm working on a little pygame-demo; one surface, one player-icon which can be moved around and the event loop (well, that's the gist, anyway).

So, now I want to have my player-icon draw a line along the path it takes, think "Tron"! I'm using pygame.draw.lines for this.

The problem: as everything is redrawn in the event loop, and seeing as I want to track the whole path of movement, I have to keep track of many, many... MANY points, which causes considerable lag once the pointlist reaches ~15000 items.

I'll provide some code below, but does anyone have an idea on how to improve this? 

```

#!/usr/bin/env python

# Pointlist needed for drawing
points = []

[SNIP]

# Event loop
while True:            
    for event in pygame.event.get():                                       
        if event.type == MOUSEBUTTONDOWN:
            if event.button == 1:                
                # Update player coordinates on Left Click
                playerx, playery = pygame.mouse.get_pos()

                # draw.lines needs startPt and endPt
                # which is why this is duplicate
                points.append(pygame.mouse.get_pos())
                points.append(pygame.mouse.get_pos())

[SNIP]

    # Move in appropriate direction
    if left == True:        
        playerx -= 5
        points.append((playerx, playery))
    # The previous lines are repeated for each movement-type

    pygame.draw.lines(screen, (0,0,0), False, points)
    pygame.display.update()

                

```


In short, the code does the following: 
- Place figure on field with leftclick -> Add coords to points[]
- Move around with arrow-keys -> after each coord-increment (say, playerx += 5), the new point is added to the list
- Draw lines between the points in the pointlist **after every redraw**


It's working as it should, but, like I said, the longer the path the slower the movement becomes. I'm merely interested in how this can be improved, if at all...

Cheers!

---

### Post by DaviesX on 2012-04-29
If not every point can be seen, why not cull those :-)

---

### Post by baumanno on 2012-04-29
Thing is, they can all be seen, as the player can never move beyond the window borders. 
The problem results in every point being appended to the list, so if I set a speed of, say, 0.01, that means
```

player_x_new = player_x_old + 0.01

```
which in turn causes 0.01 pixel increments being added to the data structure that keeps track of these points; so moving a mere 5px in any direction adds 500 elements to the list...

---

### Post by DaviesX on 2012-04-29
Ok, I know what you mean. 

I think some point might be merged if there are on the same line. But I think it's not necessary to merge them on every frame, may be every 5 frames or so.
```

struct list
{
    // point all merged
}

```

```

struct acc_points
{
    // incremented points, then merge those points and add to the list every 5 
    // frames and the points in it has almost overflowed
}

```

---

### Post by DaviesX on 2012-04-29
And I come up with a merging algorithm which is not fast. just compute the slope for every new points
```

for all new added points
    Yn` = Y0 + (Yn-1 - Y0)/(Xn-1 - X0) * (Xn - X0)

    if ( |Yn` - Yn| < ERROR_BOUND )
        MergePoint ( Pn-1, Pn )
    else
        Pn as a new P0
end loop


```

---

### Post by DaviesX on 2012-04-29
Another portal solution is: if you use arrow key only instead of a moving cursor, why not REFRESH the last point only. So that you don't have to keep adding points until the direction changed ^_^

---

### Post by GeneralZod on 2012-04-29
Do *all* of the lines between points need to be redrawn every frame? Surely only a very small portion of the screen should look different each frame (the portion immediately surrounding the player's location, most probably)? If that's the case, you only need to re-draw the lines that intersect with this small portion.

---

