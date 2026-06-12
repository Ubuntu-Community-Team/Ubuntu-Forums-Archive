---
title: "python: get item using player x/y"
date: 2012-02-06
forum: Programming Talk
---

### Post by daweefolk on 2012-02-06
I'm making a text-based game and I need a way to create items, place them on the map, and reference them using the player's x/y coordinates. 
My current idea is create them in a nested list so list[1][2] would reference the item I created at x1y2. 
So far this has proved cumbersome as I would like to be able to have multiple items in one spot.
I also want to be able to place most items at random locations on the map but some need to stay in the space I place them in.

I'm sure there's a better way to go about the creation of items, and it's probably easy to leave some items statically placed but so far it's eluding me.
Could a python guru help me out with a tip or two?
Thanks!

---

### Post by JDShu on 2012-02-06
Nested lists is probably the simplest and best way to do it. If you want to have multiple items in one position, you could even have a list within each slot. So L[x][y] = [item 1, item 2 ,..., item n].

Of course the data structure at this point is a bit complicated and hard to manage, so I would implement a class for your game map. You could have methods that placed/removed/modified an item in a particular position so that instead of having to do game_map[x][y] += [item_x] to place item x, you could have a method for a GameMap class where you can call something like game_map.place_item(item_x, (x,y))

---

### Post by Tony Flury on 2012-02-07
If your map is going to be sparesely populated - i.e. not every place has an item, you might want to use a dictionary rather than a nested list of lists of lists. The Key to your dictionary is a tuple (x,y), and the value is a list of items at that x,y co-ordinate.

I too would recommend a GameMap class to manage your dictioary (add items at a given co-ord, pick up items, drop them etc), and maybe even MapItems class to manage the list of items that could be at a specific place.

---

