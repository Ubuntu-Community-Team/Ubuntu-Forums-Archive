---
title: "A loop question (pygame related)"
date: 2006-03-20
forum: Programming Talk
---

### Post by flummoxed on 2006-03-20
I've been working on a pygame-based beginning to a minigame. The basic idea is that a bar goes up and down, and the player has to hit the key just as it's at its peak for maximum power. The closer to maximum power the better the score, etc. To start off, I decided to write two functions, pbUp (power bar Up) and pbDown (power bar down). You start off with pbUp. Every 0.1 of a second, it adds 1 to the variable 'bar', which represents how close to the max the bar is. When it gets to 10, pbUp calls pbDown, which does the same thing except it takes away 1 from 'bar' every 0.1 seconds. These functions work on their own in a simple program. 

To start off, I decided to try to write a pygame program using those two functions. In main( ), I set up the screen, font, etc. and call the function pbUp. Then, the mainloop starts. It checks for if the player exits, and if the player hits space. If the player hits space, it breaks the loop, giving you the final number that bar would have been at. It takes the value from bar, and turns it into a string called 'barStr'. It then uses this to render text to the screen displaying the number. In theory, it should go  '1 2 3 4 5 6 7 8 9 10 9 8 7 6 5 4 3 2 1 ' just like the other program, but it doesn't. It just shows a black screen, and you can't even exit properly, you have to force it to quit. I don't know why it's not working, I had it working at one point, where it kept slapping the numbers on the same place and not erasing the previous numbers, but then I changed something and it hasn't worked at all since. Got any ideas on how to get it working?

Here's the code:

Working (without pygame):
```

from time import sleep

def pbUp(BAR):
	""" A function that initializes the bar from the variable 'BAR', and until the bar is at 10,
	sets it up +1 every 100 miliseconds (0.1 of a second). Once it hits 10,
	an if statement calls pbDown to push the bar down. """
	bar = BAR
	while bar <= 10:
		sleep(0.1)
		if bar == 10:
			pbDown(bar)	
		else:
			bar = bar + 1
		print bar	
			
def pbDown(BAR):
	""" A function that initializes the bar from the variable 'BAR', and until the bar is at 0,
	sets it down -1 every 100 miliseconds (0.1 of a second). Once it hits -,
	an if statement calls pbUp to push the bar up. """
	bar = BAR
	while bar >= 0:
		sleep(0.1)
		if bar == 0:
			pbUp(bar)
		else:
			bar = bar - 1
		print bar
def main():
	pbUp(0)
	
if __name__ == "__main__":
	main()

```

Non-working(with pygame)
```

from time import sleep
import sys
import pygame
from pygame.locals import *

def pbUp(BAR):
	""" A function that initializes the bar from the variable 'BAR', and until the bar is at 10,
	sets it up +1 every 100 miliseconds (0.1 of a second). Once it hits 10,
	an if statement calls pbDown to push the bar down. """
	global bar
	bar = BAR
	while bar <= 10:
		sleep(0.1)
		if bar == 10:
			pbDown(10)	
			break
		else:
			bar = bar + 1
		
def pbDown(BAR):
	""" A function that initializes the bar from the variable 'BAR', and until the bar is at 0,
	sets it down -1 every 100 miliseconds (0.1 of a second). Once it hits -,
	an if statement calls pbUp to push the bar up. """
	global bar
	bar = BAR
	while bar >= 0:
		sleep(0.1)
		if bar == 0:
			pbUp(0)
			break
		else:
			bar = bar - 1
			
def main():
	""" Initializes pygame, creates the background, calls pbUp with the value of 0. Starts the loop
	rolling. """
	
	#Initialize Everything
	pygame.init()
	screen = pygame.display.set_mode((640,480))
	pygame.display.set_caption('Megaton Punch')
	pygame.mouse.set_visible(0)
	
	#Create The Backgound
	background = pygame.Surface(screen.get_size())
	background = background.convert()
	background.fill((0, 0, 0))
    
	# Set up font
	font = pygame.font.Font(None, 36)
	
	#Display The Background
	screen.blit(background, (0, 0))
	pygame.display.flip()
	
	# Get powerbar up function going
	bar = pbUp(0)
	
	while 1:
		""" Main loop. If the user hits space, it breaks the loop, and gives you the final bar. 
		The bar's value is blitted to the screen every frame. """
		for event in pygame.event.get():
			if event.type == pygame.QUIT: 
				return
			elif event.type == KEYDOWN:
				if event.key == K_SPACE:
					break
		screen.blit(background, (0, 0))
		barStr = str(bar)
		text = font.render(barStr, 1, (255, 255, 255))  
		textpos = text.get_rect(centerx=background.get_width()/2)
		background.blit(text, textpos)	
		pygame.display.flip()
			
	
if __name__ == "__main__":
	main()


```

---

### Post by snoop on 2006-06-08
Okay to get the loop working, you are thinking that the for loop (event loop) is the only one being run until the user presses the spacebar. This is incorrect, because as I am writing a game myself, everything in the while 1: loop is being executed. So, what you must do is to make a method do something while the user presses on the spacebar. the method should do the desired thing that you want to happen.

---

