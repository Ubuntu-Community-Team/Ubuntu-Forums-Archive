---
title: "create grid in pygame"
date: 2013-10-05
forum: Programming Talk
---

### Post by snowlizard31 on 2013-10-05
Hi, I'm trying to create  a grid in pygame so I can place text on the screen in a uniform fashion. The problem is I don't know how to do this I'm trying to create a function that will be reusble with a different number of row and colums. I've been attempting to do with two lists each with a set of coordinates, one for height and one for width.  Also I have to be able to get the coordinates in an easy manner so I can change text color if the user has the mouse over the text. I've already implemented  the change color funtion I just need the grid. Thanks for any advise and help!

---

### Post by Tony Flury on 2013-10-07
I am not 100% sure what you are after here, but having done something similar you need will need the following functions :


```

def GridXYtoScreenXY( gridx, gridy):
    return gridx + cellWidth + GridLeftBorder, gridy+cellHeight+GridTopBorder

ScreenXYtoGridXY( screenx, screeny):
    return int((screenx - GridLeftBorder)/cellWidth),  int((screeny - GridTopBorder)/cellHeight)

```

Where GridLeftBorder and GridTopBorder are the "gaps" between the left and top of your windows and the first cell in your grid.
CellWidth and CellHeight are hopefull self explanatory.
Coordinates start from zero (of course).

Using those functions you can work out where to put the text on screen, and which grid item the user is hovering over.

---

