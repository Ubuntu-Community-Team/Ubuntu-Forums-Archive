---
title: "Python behaves strangly"
date: 2006-09-07
forum: Programming Talk
---

### Post by MdaG on 2006-09-07
I'm trying to run my python code, but python interprets the following as invalid syntax...
```
idle = False
.
.
.
             if not idle:
.
.
.
```
>   File "./main.py", line 131
    if not idle:
    ^
SyntaxError: invalid syntax

shell returned 1
I assume this has something to do with tab-space or similar, but I can't do anything about it. I'm using Vim as editor.

---

### Post by thumper on 2006-09-07
My guess is that you are missing the #! at the top, and the file is being executed by /bin/sh.

```
#!/usr/bin/env python

```

---

### Post by MdaG on 2006-09-07
Nope it's there...
```
 #! /usr/bin/env python
```

---

### Post by ifokkema on 2006-09-07
Could you post the whole script, then? Or is it too big?

---

### Post by MdaG on 2006-09-07
It's pretty large, but maybe not too large (yet)
--------------------------------------------------
```
#! /usr/bin/env python

import os, sys, cPickle
from time import clock
from copy import deepcopy
from Area_class import *
from Display_classes import *
from Ground_classes import *
from Wall_classes import *
from Character_classes import *
from help_functions import *
from FOV_class import *

def main():
    display = Display_pygame(1650, 1000)
    world = []
    world.append(Area(COLUMNS, ROWS))
    world_pos = 0
    player = Player()
    message = Message()
    fov = FOV()
    world[world_pos].generate_dungeon(player)
    update(display, world[world_pos], player, message, fov.scan(world[world_pos], player.pos))
    turn, old_tiles = 0, []

    # Event loop
    while 1:
        idle = False                                            # Flag to check if event is unimportant
        visible_tiles = []                                      # Tiles to be updated
        event = pygame.event.wait()                             # Wait for player to do stuff
        if event.type == pygame.QUIT:                           # Exit game
            return
        elif event.type == pygame.KEYDOWN:                      # Handle keyboard events
            keys = pygame.key.get_pressed()

            # Events causing a turn to be taken 
            if keys[pygame.K_KP1]:                              # Move south-west
                player.move(world[world_pos], 1)
            elif keys[pygame.K_DOWN] or keys[pygame.K_KP2]:     # Move south
                player.move(world[world_pos], 2)
            elif keys[pygame.K_KP3]:                            # Move south-east
                player.move(world[world_pos], 3)
            elif keys[pygame.K_LEFT] or keys[pygame.K_KP4]:     # Move west
                player.move(world[world_pos], 4)
            elif keys[pygame.K_RIGHT] or keys[pygame.K_KP6]:    # Move east
                player.move(world[world_pos], 6)
            elif keys[pygame.K_KP7]:                            # Move north-west
                player.move(world[world_pos], 7)
            elif keys[pygame.K_UP] or keys[pygame.K_KP8]:       # Move north
                player.move(world[world_pos], 8)
            elif keys[pygame.K_KP9]:                            # Move north-east
                player.move(world[world_pos], 9)
            elif keys[pygame.K_o]:                              # Open/close door
                door_pos = player.open(world[world_pos])
                if type(door_pos) == type(()): 
                    message.add('Open/Close door')
                elif door_pos > 1:                              # Specify direction if doors > 1
                    message.add('Which direction? (non direction to abort)')
                    display.draw_msg_area(world[world_pos], message)
                    display.update_screen(world[world_pos])
                    while 1:
                        event = pygame.event.wait()
                        if event.type == pygame.KEYDOWN:
                            keys = pygame.key.get_pressed()
                            if keys[pygame.K_KP1]:
                                door_pos = player.open(world[world_pos], 1)
                            elif keys[pygame.K_DOWN] or keys[pygame.K_KP2]: 
                                door_pos = player.open(world[world_pos], 2)
                            elif keys[pygame.K_KP3]:              
                                door_pos = player.open(world[world_pos], 3)
                            elif keys[pygame.K_LEFT] or keys[pygame.K_KP4]:
                                door_pos = player.open(world[world_pos], 4)
                            elif keys[pygame.K_RIGHT] or keys[pygame.K_KP6]:
                                door_pos = player.open(world[world_pos], 6)
                            elif keys[pygame.K_KP7]:                       
                                door_pos = player.open(world[world_pos], 7)
                            elif keys[pygame.K_UP] or keys[pygame.K_KP8]:   
                                door_pos = player.open(world[world_pos], 8)
                            elif keys[pygame.K_KP9]:                            
                                door_pos = player.open(world[world_pos], 9)
                            break
            elif keys[pygame.K_GREATER] or (keys[pygame.K_LSHIFT] and keys[60]):    # Descend 
                if world[world_pos].get_object(player.pos, 1).id == 'Descention_point':
                    world[world_pos].remove(player.pos)   # Remove player
                    world_pos += 1
                    if len(world) == world_pos:                 # If unvisited. Generate.
                        world.append(Area(COLUMNS, ROWS))
                        world[world_pos].generate_dungeon(player)
                    else:
                        world[world_pos].insert_object(player, world[world_pos].ascention_point)
                    pos = world[world_pos].ascention_point
                    player.pos = pos                            # Place player at ascention p.
                    message.add('Descending...')
                    display.reset_screen()
                    old_tiles = []                              # Make sure not to draw from previous level
                    update(display, world[world_pos], player, message, fov.scan(world[world_pos], player.pos), world[world_pos].get_remembered_objects())
            elif keys[pygame.K_LESS] or keys[60]:               # Ascend stairs/elevator
                if world[world_pos].get_object(player.pos, 1).id == 'Ascention_point':
                    if world_pos > 0:
                        world[world_pos].remove(pos)            # Remove player
                        world_pos -= 1
                        pos = world[world_pos].descention_point
                        world[world_pos].insert_object(player, pos)
                        player.pos = pos                        # Place player at descention p.
                        message.add('Ascending...')
                        display.reset_screen()
                    else:
                        message.add('You do not feel like leaving...')
                    old_tiles = []                              # Make sure not to draw from previous level
                    update(display, world[world_pos], player, message, fov.scan(world[world_pos], player.pos), world[world_pos].get_remembered_objects())
            else:
                idle = True                                     # Makes sure game doesn't get updated
            
            # Events not causing a turn to be taken
            if keys[pygame.K_s] and keys[pygame.K_LCTRL]:       # Save game
                save(world, player, world_pos)
                message.add('Current game saved!')
                update(display, world[world_pos], player, message, fov.scan(world[world_pos], player.pos))
            elif keys[pygame.K_l] and keys[pygame.K_LCTRL]:     # Load game
                world, player, world_pos = load()
                message.add('Previous game restored!')
                display.reset_screen()
                old_tiles = []
                update(display, world[world_pos], player, message, fov.scan(world[world_pos], player.pos))
            elif keys[pygame.K_c] and keys[pygame.K_LCTRL]:     # Exit game
                return
            elif keys[pygame.K_f] and keys[pygame.K_LCTRL]:     # Fullscreen/window
                display.set_fullscreen()
                display.update_screen(world[world_pos])
				
			if not idle:
				turn += 1
				pygame.display.set_caption(str(player.pos))   # Used for debugging
				#print 'Turn:', turn

				# Make creatures do their stuff
				characters = world[world_pos].characters
				for creat in characters:
					if creat.hp <= 0 and creat.alive:
						creat.die()
						world[world_pos].splash_blood(creat.pos, creat.color)
					elif creat.alive:
						creat.perform_action(world[world_pos])

				# Add all visible tiles relative player position to update list
				visible_tiles.extend(fov.scan(world[world_pos], player.pos))

				# Print to screen
				update(display, world[world_pos], player, message, visible_tiles, old_tiles)

				# Remember updated tiles so that they can be shadowed next turn
				old_tiles = []
				for i in range(len(visible_tiles)):
					obj = world[world_pos].get_object(visible_tiles[i])
					tile = (visible_tiles[i], obj.color, obj.sign)
					old_tiles.append(tile)
					if not world[world_pos].is_visited(visible_tiles[i]):
						world[world_pos].set_visited(visible_tiles[i])
						obj = world[world_pos].get_object(visible_tiles[i])
						world[world_pos].set_remembered_object(visible_tiles[i], obj)
					else:
						obj = world[world_pos].get_object(visible_tiles[i])
						world[world_pos].set_remembered_object(visible_tiles[i], obj)

					# Make sure the player is still alive
					if player.hp <= 0:
						return


def save(world, player, world_pos):
    """
    Stores all relevant data for player's progress
    
    Keyword arguments:
    world -- 2D (sometimes 3D) list containing all areas visited (and some unvisited).
    player -- The player object.
    world_pos -- 3D list containing information about where in world player is.
    """
    data = [world, player, world_pos]
    cPickle.dump(data, open('game.dat', 'w'), 1)


def load():
    """Loads data from previous game"""
    try:
        data = cPickle.load(open('game.dat'))
        return data[0], data[1], data[2]
    except IOError:
        print 'No previously saved game!'


def update(display, area, player, message, visible_tiles, old_tiles = []):
    """Redraws screen and updates everything"""
    display.draw(area, visible_tiles, old_tiles)
    display.draw_stat_area(area, player)
    display.draw_msg_area(area, message)
    display.update_screen(area)


if __name__ == '__main__':
    try:
        import pygame
        if not pygame.font: print 'Warning, fonts disabled'
        if not pygame.mixer: print 'Warning, sound disabled'
        pygame.init()
        main()
    except ImportError:
        raise GameError, "You need to install PyGame first! (http://www.pygame.org)"

```
Hmm, I think I see the problem now... "if not idle" is tabbed in one too much, but why doesn't that show in Vim (or Anjuta) ?

---

### Post by ifokkema on 2006-09-07
> **MdaG said:**
> Hmm, I think I see the problem now... "if not idle" is tabbed in one too much, but why doesn't that show in Vim (or Anjuta) ?
You seem to be right about the problem. The reason why you don't see it, is that partially, you're using spaces for indentation. And partially, you use tabs... Depending on the 'tab-size' setting, you see the issue or you don't. :)

---

### Post by steve.horsley on 2006-09-10
Aargh! That is the **worst**!

I once had to modify a python file that had been edited previously by people who used both tabs and spaces. Changing the "tab size" in the editor made different lines look to be lined up. It took me an age to sort out. Eventually, I replaced all tabs with spaces and then had to basically test the entire file again to find all the logic errors left from inconsistent indentation. 

You should set yout editor to insert spaces when you hit tab. Tabs really are evil.

---

