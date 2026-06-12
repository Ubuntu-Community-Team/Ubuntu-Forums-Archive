---
title: "[Python / Pygame] Moving Sprite's In Any Direction"
date: 2010-03-22
forum: Programming Talk
---

### Post by glennlh on 2010-03-22
Hi, I've been learning how to code in python and been using the libary pygame to make a game. In the game I use a image of a car as a sprite, I want to be able to rotate the car by using the left and right keys and make it move in the direction that it is pointing. Would someone be able to explain how to do that, iv'e got no code I can post because I have no idea at all how to do this. Thanks.

---

### Post by Tony Flury on 2010-03-23
I am not sure you can rotate sprites in pygame - what you will need is seperate images that represent the various rotation states of the car, and keep track within your code of the direction your car is pointing and therefore how it will move on the screen - or maybe how your background will move relative to the car (or maybe even both).

There are ways (not got my head around it yet myself) of defining multiple images against a single sprite and changing the image that the sprite displays as required - I need to do some digging on the details.

I am just getting to grips with Sprites and pygame, and I intend to write a space invaders clone in pygame as a test of my understanding - 
my intention is to to extend the sprite class to give me some basic animation features, and keep track of some simple states - i.e. alive, dying etc - so I can just change the state witin my main game loop, and the class will keep track of which frame to display from which animation sequence.

---

### Post by matmatmat on 2010-03-23
Don't know if [this]("http://www.tuxradar.com/gloss") will be any good to you, it's a OpenGL layer around pygame which allows you to rotate and scale images

BTW: I'm also making a space invader clone with pygame!

---

### Post by glennlh on 2010-03-23
Thank You for the replies, I've been trying some of the suggestions. OpenGL looks good but I would still like to stick to pygame for the moment. ive managed to write a bit of code which works but the car judders a bit, does anyone know how to make it run a bit smoother, Thanks.

```
#!/usr/bin/python
# Import Pygame, Sys and Pygame Locals
import pygame, sys
from pygame.locals import *

# Set Up Pygame Libary
pygame.init()

# Create a Clock
clock = pygame.time.Clock()

# Set Up Window and Title
window = pygame.display.set_mode((800,500), 0, 32)
pygame.display.set_caption('Pickup')

# Defines Colour Constants
BLACK = (0,0,0)
WHITE = (255,255,255)

# Load Image Of Car and Background
car = pygame.image.load('Data/Image/pickup.png')
background = pygame.image.load('Data/Image/Level/level1.png')

# Define Position Of Car
carX = 114
carY = 330

# Define Speed
speed = 20
maxSpeed = 280
minSpeed = 24

# Denfine How Many Pixels To Move
pixelsToMove = 2

# Direction Of Car
carDirection = 0

# Position Of Car Center
carCenterX = 0
carCenterY = 0

# Define Boolean Values Storing If Should To Move Or Not
moveDown = False
moveUp = False
moveRight = False
moveLeft = False

# Main Loop
while True:
	
	# Search For Events
	for event in pygame.event.get():
		if event.type == QUIT:
			pygame.quit()
			sys.exit()
			
		# Search For Keys Pressed Down
		if event.type == KEYDOWN:
			if event.key == K_DOWN:
				moveDown = True
			if event.key == K_UP:
				moveUp = True
			if event.key == K_RIGHT:
				moveRight = True
			if event.key == K_LEFT:
				moveLeft = True
		
		# Search For Keys Released
		if event.type == KEYUP:
			if event.key == K_DOWN:
				moveDown = False
			if event.key == K_UP:
				moveUp = False
			if event.key == K_RIGHT:
				moveRight = False
			if event.key == K_LEFT:
				moveLeft = False
	
	# Move Car In Selected Direction			
	if moveDown == True:
		if speed > 50:
			speed = speed - 10
		
	if moveUp == True or speed > minSpeed:
		if speed < maxSpeed:
			speed = speed + 1
		
		# Move Car In Correct Direction	
		if carDirection <= 10 and carDirection >= 0:
			carY = carY - 2
		elif carDirection <= 359 and carDirection >= 350:
			carY = carY - 2
		elif carDirection <= 45 and carDirection >= 11:
			carY = carY - 2
			carX = carX - 1
		elif carDirection <= 79 and carDirection >= 46:
			carY = carY - 1
			carX = carX - 2
		elif carDirection <= 100 and carDirection >= 80:
			carX = carX - 2
		elif carDirection <= 135 and carDirection >= 101:
			carX = carX - 2
			carY = carY + 1
		elif carDirection <= 169 and carDirection >= 136:
			carX = carX - 1
			carY = carY + 2
		elif carDirection <= 190 and carDirection >= 170:
			carY = carY + 2
		elif carDirection <= 226 and carDirection >= 191:
			carX = carX + 1
			carY = carY + 2
		elif carDirection <= 227 and carDirection >= 291:
			carX = carX + 2
			carY = carY + 1
		elif carDirection <= 259 and carDirection >= 227:
			carY = carY + 1
			carX = carX + 2
		elif carDirection <= 280 and carDirection >= 260:
			carX = carX + 2
		elif carDirection <= 316 and carDirection >= 281:
			carY = carY - 1
			carX = carX + 2
		elif carDirection <= 349 and carDirection >= 317:
			carY = carY - 2
			carX = carX + 1
		
	if moveRight == True:
		if carDirection < 2:
			carDirection = 359
		else:
			carDirection = carDirection - 2
	if moveLeft == True:
		if carDirection > 358:
			carDirection = 0
		else:
			carDirection = carDirection + 2
	
	# Check If Car Is Not Moving
	if moveUp == False:
		if speed > minSpeed:
			speed = speed - 5 
	
	# Draw Background
	window.blit(background, (0,0))
	
	# Reload Car, Rotate It and Draw It
	if moveRight == True or moveLeft == True:
		if speed > minSpeed:
			carCenterX = carX + car.get_rect().width / 2
			carCenterY = carY + car.get_rect().height / 2
			car = pygame.image.load('Data/Image/pickup.png')
			car = pygame.transform.rotate(car, carDirection)
			carX = carCenterX - car.get_rect().width / 2
			carY = carCenterY - car.get_rect().height / 2		
	
	# Draw Car To Screen	
	window.blit(car, (carX, carY))
	
	# Update The Display
	pygame.display.update()
    
	# Wait X Seconds
	clock.tick(speed)

```

---

### Post by lavinog on 2010-03-24
would you mind providing the images you used?

---

### Post by lavinog on 2010-03-24
a preliminary scan makes me think that this is inefficient:
```

if moveRight == True or moveLeft == True:
		if speed > minSpeed:
			carCenterX = carX + car.get_rect().width / 2
			carCenterY = carY + car.get_rect().height / 2
			**car = pygame.image.load('Data/Image/pickup.png')**
			car = pygame.transform.rotate(car, carDirection)
			carX = carCenterX - car.get_rect().width / 2
			carY = carCenterY - car.get_rect().height / 2		

```
also you shouldn't need to calculate the center, the rect should have a center attribute
car.get_rect().center

> 
The Rect object has several virtual attributes which can be used to move and align the Rect:

    top, left, bottom, right
    topleft, bottomleft, topright, bottomright
    midtop, midleft, midbottom, midright
    center, centerx, centery
    size, width, height
    w,h


---

### Post by glennlh on 2010-03-25
> **lavinog said:**
> a preliminary scan makes me think that this is inefficient:
```

if moveRight == True or moveLeft == True:
		if speed > minSpeed:
			carCenterX = carX + car.get_rect().width / 2
			carCenterY = carY + car.get_rect().height / 2
			**car = pygame.image.load('Data/Image/pickup.png')**
			car = pygame.transform.rotate(car, carDirection)
			carX = carCenterX - car.get_rect().width / 2
			carY = carCenterY - car.get_rect().height / 2		

```
also you shouldn't need to calculate the center, the rect should have a center attribute
car.get_rect().center

I'm not making the images and haven't yet received them but I'll upload the temporary images I'm using anyway. [ATTACH]151404[/ATTACH].

Would you be able to explain how its inefficient loading the image as in the line of code you highlighted, I've haven't been learning python long and don't really know how to maker it more efficient.

Thanks

---

### Post by Tony Flury on 2010-03-25
one thing you could do is preload all of the images at the start of your program - and then just swap between images as required by your game ... That might stop some of the juddering, which may be caused by your programmin reloading the image from disk each time.

---

### Post by glennlh on 2010-03-25
> **Tony Flury said:**
> one thing you could do is preload all of the images at the start of your program - and then just swap between images as required by your game ... That might stop some of the juddering, which may be caused by your programmin reloading the image from disk each time.

Hi, I keep reloading the image as if I don't it the image for some reason blurs until it disappears (Try it without the reloading code and you'll see what I mean). The juddering seems to be because the image don't turn the right way because I don't know how to code this, what I mean by this is i've set it for example when the image is between 101 and 135 degrees it moves 2 pixels left and one pixel down. Sorry but I can't really explain this properly, the only way I can really show you is if you run the code. Thanks.

Edit: Actually Ive just tried not reloading it and it seams to work, wonder why it didn't work the first time.

---

### Post by tookyourtime on 2010-03-25
I think he means it's inefficient because your loading the image every time in the loop.

You can load the image once at the start like this:
```
# Load Image Of Car and Background
carBase = car = pygame.image.load('Data/Image/pickup.png')
```Then just rotate the carBase and put it in car, in the loop, to use. Like this:
```

#car = pygame.image.load('Data/Image/pickup.png')
car = pygame.transform.rotate(carBase, carDirection)

```So your getting rid of the image.load line and rotating carBase

---

### Post by glennlh on 2010-03-25
> **tookyourtime said:**
> I think he means it's inefficient because your loading the image every time in the loop.

You can load the image once at the start like this:
```
# Load Image Of Car and Background
carBase = car = pygame.image.load('Data/Image/pickup.png')
```Then just rotate the carBase and put it in car, in the loop, to use. Like this:
```

#car = pygame.image.load('Data/Image/pickup.png')
car = pygame.transform.rotate(carBase, carDirection)

```So your getting rid of the image.load line and rotating carBase

Thanks, I thought i fixed the error but i haven't, without the image being reloaded in the loop it messes up, I you delete the load line from the loop and run it, you'll know what i mean.

---

### Post by tookyourtime on 2010-03-25
I know if you delete the reload line in the loop it wont work, but that's only because you modified 'car' by rotating it and storing it back into car.

If you keep an unmodified image that you load at the start - 'carBase' for example, and make sure nothing changes it, then you do only need to load it once.

---

### Post by glennlh on 2010-03-25
> **tookyourtime said:**
> I know if you delete the reload line in the loop it wont work, but that's only because you modified 'car' by rotating it and storing it back into car.

If you keep an unmodified image that you load at the start - 'carBase' for example, and make sure nothing changes it, then you do only need to load it once.

Oh sorry, I understand now. Thank You very much.

Now just need to sort the steering out.

---

### Post by glennlh on 2010-03-25
Fixed the reloading of the image, here's the code. Can anyone help me with the steering.

```
#!/usr/bin/python
# Import Pygame, Sys and Pygame Locals
import pygame, sys
from pygame.locals import *

# Set Up Pygame Libary
pygame.init()

# Create a Clock
clock = pygame.time.Clock()

# Set Up Window and Title
window = pygame.display.set_mode((800,500), 0, 32)
pygame.display.set_caption('Pickup')

# Defines Colour Constants
BLACK = (0,0,0)
WHITE = (255,255,255)

# Load Image Of Car and Background
car = pygame.image.load('Data/Image/pickup.png')
background = pygame.image.load('Data/Image/Level/level1.png')

# Define Position Of Car
carX = 114
carY = 330

# Define Speed
speed = 20
maxSpeed = 180
minSpeed = 24

# Denfine How Many Pixels To Move
pixelsToMove = 2

# Direction Of Car
carDirection = 0

# Position Of Car Center
carCenterX = 0
carCenterY = 0

# Define Boolean Values Storing If Should To Move Or Not
moveDown = False
moveUp = False
moveRight = False
moveLeft = False

# Define Rotated Version Of Car
rotCar = pygame.transform.rotate(car, carDirection)

# Main Loop
while True:
	
	# Search For Events
	for event in pygame.event.get():
		if event.type == QUIT:
			pygame.quit()
			sys.exit()
			
		# Search For Keys Pressed Down
		if event.type == KEYDOWN:
			if event.key == K_DOWN:
				moveDown = True
			if event.key == K_UP:
				moveUp = True
			if event.key == K_RIGHT:
				moveRight = True
			if event.key == K_LEFT:
				moveLeft = True
		
		# Search For Keys Released
		if event.type == KEYUP:
			if event.key == K_DOWN:
				moveDown = False
			if event.key == K_UP:
				moveUp = False
			if event.key == K_RIGHT:
				moveRight = False
			if event.key == K_LEFT:
				moveLeft = False
	
	# Move Car In Selected Direction			
	if moveDown == True:
		if speed > 50:
			speed = speed - 10
		
	if moveUp == True or speed > minSpeed:
		if speed < maxSpeed:
			speed = speed + 1
		
		# Move Car In Correct Direction	
		if carDirection <= 10 and carDirection >= 0:
			carY = carY - 2
		elif carDirection <= 359 and carDirection >= 350:
			carY = carY - 2
		elif carDirection <= 45 and carDirection >= 11:
			carY = carY - 2
			carX = carX - 1
		elif carDirection <= 79 and carDirection >= 46:
			carY = carY - 1
			carX = carX - 2
		elif carDirection <= 100 and carDirection >= 80:
			carX = carX - 2
		elif carDirection <= 135 and carDirection >= 101:
			carX = carX - 2
			carY = carY + 1
		elif carDirection <= 169 and carDirection >= 136:
			carX = carX - 1
			carY = carY + 2
		elif carDirection <= 190 and carDirection >= 170:
			carY = carY + 2
		elif carDirection <= 226 and carDirection >= 191:
			carX = carX + 1
			carY = carY + 2
		elif carDirection <= 227 and carDirection >= 291:
			carX = carX + 2
			carY = carY + 1
		elif carDirection <= 259 and carDirection >= 227:
			carY = carY + 1
			carX = carX + 2
		elif carDirection <= 280 and carDirection >= 260:
			carX = carX + 2
		elif carDirection <= 316 and carDirection >= 281:
			carY = carY - 1
			carX = carX + 2
		elif carDirection <= 349 and carDirection >= 317:
			carY = carY - 2
			carX = carX + 1
		
	if moveRight == True:
		if carDirection < 2:
			carDirection = 359
		else:
			carDirection = carDirection - 2
	if moveLeft == True:
		if carDirection > 358:
			carDirection = 0
		else:
			carDirection = carDirection + 2
	
	# Check If Car Is Not Moving
	if moveUp == False:
		if speed > minSpeed:
			speed = speed - 5 
	
	# Draw Background
	window.blit(background, (0,0))
	
	# Reload Car, Rotate It and Draw It
	if moveRight == True or moveLeft == True:
		if speed > minSpeed:
			carCenterX = carX + rotCar.get_rect().centerx
			carCenterY = carY + rotCar.get_rect().centery
			rotCar = pygame.transform.rotate(car, carDirection)
			carX = carCenterX - rotCar.get_rect().centerx
			carY = carCenterY - rotCar.get_rect().centery		
	
	# Draw Car To Screen	
	window.blit(rotCar, (carX, carY))
	
	# Update The Display
	pygame.display.update()
    
	# Wait X Seconds
	clock.tick(speed)
```

---

### Post by tookyourtime on 2010-03-25
What would you like to be changed about the steering?

---

### Post by glennlh on 2010-03-25
> **tookyourtime said:**
> What would you like to be changed about the steering?

Its not very precise, when steering it jumps from one direction to another because of the way I've set it up. Is there another way to set it up correctly or a fix. Sorry buts its hard to explain in writing, but you will probably see what I mean if you run it.

---

### Post by lavinog on 2010-03-25
One thing I noticed is that the car image isn't getting updated if I turn while not moving, but once I start moving the car can start moving sideways.

Also you could simplify your car movement code by using some trig:
```

carY-= math.cos(math.radians( carDirection ) ) * (speed * adjfactor)
carX-= math.sin(math.radians( carDirection ) ) * (speed * adjfactor)

```

---

### Post by lavinog on 2010-03-25
> **glennlh said:**
> Its not very precise, when steering it jumps from one direction to another because of the way I've set it up. Is there another way to set it up correctly or a fix. Sorry buts its hard to explain in writing, but you will probably see what I mean if you run it.

When you are changing the cardirection, you are not checking that speed>minSpeed, but when you are rotating the image you are...that is part of the problem.
you should put the rotation code in with the cardirection code.

---

### Post by tookyourtime on 2010-03-25
Yes, replace your list of movements with the trig, and then that gives you some more freedom with changing speeds.

And if you indent this part, (make it come under if moveUp == True or speed > minSpeed:) so that the direction is only changed when the car is moving.

Because it makes sense to only be able to steer when going forwards. That will stop the jumping.
```
        
        if moveRight == True:
            if carDirection < 2:
                carDirection = 359
            else:
                carDirection = carDirection - 2
        if moveLeft == True:
            if carDirection > 358:
                carDirection = 0
            else:
                carDirection = carDirection + 2
```

---

### Post by glennlh on 2010-03-25
> **tookyourtime said:**
> Yes, replace your list of movements with the trig, and then that gives you some more freedom with changing speeds.

And if you indent this part, (make it come under if moveUp == True or speed > minSpeed:) so that the direction is only changed when the car is moving.

Because it makes sense to only be able to steer when going forwards. That will stop the jumping.
```
        
        if moveRight == True:
            if carDirection < 2:
                carDirection = 359
            else:
                carDirection = carDirection - 2
        if moveLeft == True:
            if carDirection > 358:
                carDirection = 0
            else:
                carDirection = carDirection + 2
```

Do you know where there is a guide to using trig for steering as I don't know how to do that. Thanks.

---

### Post by tookyourtime on 2010-03-25
Strangely, I cant really find any guides for just that.

But basically if you draw a right angled triangle like the diagram I uploaded.

The movement in your X and Y directions are unknown, but you do know your angle and Speed.

So if you draw out that triangle, you can use really basic trigonometry to find out where you should be moving.

eg. sin(angle) = opposite/hypotenuse
and cos(angle) = adjacent/hypotenuse

And there are tutorials for that allllll over the internet.

---

### Post by lavinog on 2010-03-25
> **glennlh said:**
> Do you know where there is a guide to using trig for steering as I don't know how to do that. Thanks.

did you see my example above?

Do you know about cosine and sine?

Basically you utilize vectors (magnitude and direction)

the math.cos and sin functions expect a angle in radians, but you are using degrees, so you need to convert to radians:
```

math.radians( degree )

```

normally when 0 degrees is pointing to the right you can get the x y components by using:
y = magnitude * sin(direction)
x = magnitude * cos(direction)

if your direction = 0:
y=0 and x = magnitude

if direction = 90 degrees
y=magnitude and x=0

...
in normal Cartesian coordinate systems y decreases as you go down, but screen coordinates are the opposite since y increases as you go down the screen, you need to take that into account.

so with the code I gave:
```

carY-= math.cos(math.radians( carDirection ) ) * (speed * adjfactor)
carX-= math.sin(math.radians( carDirection ) ) * (speed * adjfactor)

```
I am using cos for Y and sin for X because you have 0 pointing north instead of east.
so @ 0 degrees (north) we will have:
carY -= (speed * adjfactor)
carX -= 0

and at -90 degrees (east):
carY -= 0
carX -= (speed * adjfactor)

carY-= number is the same as carY = carY - number

---

### Post by glennlh on 2010-03-25
> **tookyourtime said:**
> Strangely, I cant really find any guides for just that.

But basically if you draw a right angled triangle like the diagram I uploaded.

The movement in your X and Y directions are unknown, but you do know your angle and Speed.

So if you draw out that triangle, you can use really basic trigonometry to find out where you should be moving.

eg. sin(angle) = opposite/hypotenuse
and cos(angle) = adjacent/hypotenuse

And there are tutorials for that allllll over the internet.

Thanks I'll have a look and see what I can do.

> **lavinog said:**
> did you see my example above?

Do you know about cosine and sine?

Basically you utilize vectors (magnitude and direction)

the math.cos and sin functions expect a angle in radians, but you are using degrees, so you need to convert to radians:
```

math.radians( degree )

```

normally when 0 degrees is pointing to the right you can get the x y components by using:
y = magnitude * sin(direction)
x = magnitude * cos(direction)

if your direction = 0:
y=0 and x = magnitude

if direction = 90 degrees
y=magnitude and x=0

...
in normal Cartesian coordinate systems y decreases as you go down, but screen coordinates are the opposite since y increases as you go down the screen, you need to take that into account.

so with the code I gave:
```

carY-= math.cos(math.radians( carDirection ) ) * (speed * adjfactor)
carX-= math.sin(math.radians( carDirection ) ) * (speed * adjfactor)

```
I am using cos for Y and sin for X because you have 0 pointing north instead of east.
so @ 0 degrees (north) we will have:
carY -= (speed * adjfactor)
carX -= 0

and at -90 degrees (east):
carY -= 0
carX -= (speed * adjfactor)

carY-= number is the same as carY = carY - number

Sorry I didn't see your example, I'll have a look at it and try and work out how it works. Thanks.

---

### Post by lavinog on 2010-03-25
Before you start expanding on this project, you may also want to take a look at using a truck object.

```

class Truck:

```

also i made a truck image you can use.

---

### Post by glennlh on 2010-03-25
> **lavinog said:**
> Before you start expanding on this project, you may also want to take a look at using a truck object.

```

class Truck:

```

also i made a truck image you can use.

Thanks

---

### Post by glennlh on 2010-03-28
Hi again, sorry another question. I've started coding it from scratch and this time using classes and functions. My question is, why when pressing the key such as left and holding it down only work once. I have to release the key and press it again for it to move it again. Here's my code, Thanks for any help.

```
# Import Pygame, Sys and Pygame Locals
import pygame, sys
from pygame.locals import *

# Pickup Class
class pickup():
	
	# Constructor
	def __init__(self, image, x, y, up, down, left, right):
		self.image = image
		self.rotImage = image
		self.x = x
		self.y = y
		self.up = up
		self.down = down
		self.left = left
		self.right = right
		self.direction = 0
		
	# Rotate Image Left Or Right
	def rotate(self):
		if self.left == True and self.right == False:
			if self.direction == 359:
				self.direction = 0
			else:
				self.direction = self.direction + 1
			pygame.transform.rotate(self.image, self.direction)
		if self.right == True and self.left == False:
			if self.direction == 0:
				self.direction = 359
			else:
				self.direction = self.direction - 1
		
		self.rotImage = pygame.transform.rotate(self.image, self.direction)
		
class colour():
	
	# Create Colour Constants
	BLACK = (0,0,0)
	WHITE = (255,255,255)

def eventChecker():
	
	up = False
	down = False
	left = False
	right = False
	
	# Check For Events
	for event in pygame.event.get():
		
		# Check If User Quits
		if event.type == QUIT:
			pygame.quit()
			sys.exit()
		
		# Check For Key Held Down	
		if event.type == KEYDOWN:
			if event.key == K_ESCAPE:
				pygame.quit()
				sys.exit()
			if event.key == K_UP:
				up = True
			if event.key == K_DOWN:
				down = True
			if event.key == K_LEFT:
				left = True
			if event.key == K_RIGHT:
				right = True
				
		# Check For Key Released	
		if event.type == KEYUP:
			if event.key == K_UP:
				up = False
			if event.key == K_DOWN:
				down = False
			if event.key == K_LEFT:
				left = False
			if event.key == K_RIGHT:
				right = False
		
	return up, down, left, right
					

def main():
	
	# Set Up Pygame
	pygame.init()
	
	# Create Key Variables
	up = False
	down = False
	left = False
	right = False
	
	# Set Up Window
	window = pygame.display.set_mode((800, 500), 0, 32)
	pygame.display.set_caption('Pickup')
	
	# Load Background
	background = pygame.image.load('Data/Image/Level/level1.png')
	
	# Load Pickup Image
	carImage = pygame.image.load('Data/Image/pickup.png')
	
	# Create Car Object
	car = pickup(carImage, 10, 10, up, down, left, right)
	
	# Main Loop
	while True:
		
		# Check For Events
		up, down, left, right = eventChecker()
		
		# Update Key Values
		car.up = up
		car.down = down
		car.left = left
		car.right = right
		
		# Rotate Image
		car.rotate()
		
		# Print Background
		window.blit(background, (0,0))
		
		# Print Car To Window
		window.blit(car.rotImage, (car.x, car.y))
		
		# Update Display
		pygame.display.update()

# Run Main Function
main()
```

---

### Post by tookyourtime on 2010-03-28
The events for keydown and key up that you were looking at are exactly what they say.
Only once for when a key is pressed down or released. In a game it is more useful to get a picture of the whole keyboard every frame.

If you replace your eventChecker function with this:
```
def eventChecker():
    
    up = False
    down = False
    left = False
    right = False
    
    # Check For Events
    for event in pygame.event.get():
        # Check If User Quits
        if event.type == QUIT:
            pygame.quit()
            sys.exit()
        
    if pygame.key.get_pressed()[K_RIGHT]:
        right = True;
    if pygame.key.get_pressed()[K_LEFT]:
        left = True;
    if pygame.key.get_pressed()[K_UP]:
        up = True;
    if pygame.key.get_pressed()[K_DOWN]:
        down = True;
        
    return up, down, left, right
```

It will check if a key is pressed or not. Which is what you need.

---

### Post by lavinog on 2010-03-28
you can also create methods in the truck class to turn the truck
this way you can do something like:
```

if right:
    car.turnright()
if up:
    car.accelerate()
...

```

---

### Post by lavinog on 2010-03-28
```

def turnright(self):
        self.direction = (self.direction + self.turnstep) % 360
        self.rotate_image()
    
    def turnleft(self):
        self.direction = (self.direction - self.turnstep) % 360
        self.rotate_image()
    
    def rotate_image(self):
        self.rotImage = pygame.transform.rotate(self.image, self.direction)

```
The % operator is a modulus.  It basically does the if <0 or > 360 stuff for you:
-5 % 360 = 355
5 % 360 = 5
365 % 360 = 5
...etc

---

### Post by glennlh on 2010-03-29
Thanks You tookyourtime and lavinog, got the steering and suggestions working.

---

### Post by glennlh on 2010-04-01
I'm going to release a BETA version soon if I can, but I'm slightly confused with collision detection. I want make to blit a separate image on top of the background image, this separate image will contain any object that I can crash into on the map. How can I make it so that the space between the images are ignored and not counted in the collision. Thanks Glennlh.

---

### Post by Tony Flury on 2010-04-01
Collisions are defined by the rectangles on the sprite, so make sure your rectangles are defined correctly - sounds to me you might have two sprites, one on top of the other - and you do your collision dection on the smaller one ?

---

### Post by glennlh on 2010-04-01
Thanks Tony, I'm not having any problems I just don't know how to actually go about doing it. If you can give me a small example I would be grateful. Thanks Glennlh.

---

### Post by lavinog on 2010-04-01
One thing you can think about using is .colliderect
[http://www.pygame.org/docs/ref/rect.html#Rect.colliderect](http://www.pygame.org/docs/ref/rect.html#Rect.colliderect)

There are a lot of breakout games written for pygame, take a look at how they handle the ball colliding with a brick.

Maybe you can post what you have so far.

---

### Post by glennlh on 2010-04-01
Hi, Ive heard that I can post my code at google but I need to license and copyright it I believe. Would someone tell me how to and i'll post it up there and leave a link. I cant really post it here as its split up into three files and many images.

---

### Post by lavinog on 2010-04-01
Compress the folder.

---

### Post by glennlh on 2010-04-01
Ive got a page on google code. Doesn't matter link below.

---

### Post by glennlh on 2010-04-01
To make it easier here it is. [ATTACH]152087[/ATTACH]

---

### Post by glennlh on 2010-04-01
Here's a new version with the colliderect method. The problem with it is that it returns True even when its not colliding. [ATTACH]152107[/ATTACH]

---

### Post by glennlh on 2010-04-05
I've got some sort of collision detection working now. The problem is that it only detects if a corner is intersecting a rectangle which means it wont work for small objects. Here's the newer version. Thanks Glennlh. [ATTACH]152442[/ATTACH].

---

### Post by lavinog on 2010-04-06
Looks pretty good.
Your truck looks nicer than mine.

The code looks much cleaner too.
I would recomend turning the other objects into class objects:

```

class Obstical:
  def __init__(self):
    self.image=None
    self.rect=Rect(1,1,1,1)  #generic rect object

  def do_stuff(self):
    # whatever functions common to all objects such as collision animation or detection

class LampPost(Obstical):
  pass

class BillBoard(Obstical):
  pass

class Man(Obstical):
  pass
...

```

---

### Post by glennlh on 2010-04-06
Ive got it working, I'll now have a go at what is suggested.

---

### Post by DrTravia on 2010-06-01
lol, I continued reading, you pretty much have your initial question answered, this post probly won't help all that much x.x

I won't delete the code though, figured I already wrote it, no point in deletion. It's also a much lower leveled directional code for all those not looking to create games with vectors just yet


```

right = true
left = false
up = false
down = false
count = 1

#replace "keypress" with whichever way you want your program to get it's controls
#this is based on wasd controls
#a is left, s is back, d is right, w is up
#count is basically just a way to keep track of the cars direction
#all the extra falses aren't really needed, just added in
#to make the idea a bit more clear

if keypress == a and count == 1:  
    right = false  
    left = false
    up = true
    down = false
    count += 1
if keypress == a and count == 2:  
    right = false  
    left = true
    up = false
    down = false
    count += 1
if keypress == a and count == 3:  
    right = false  
    left = false
    up = false
    down = true
    count += 1
if keypress == a and count == 4:  
    right = true  
    left = false
    up = false
    down = false
    count = 1
if keypress == w:
    if right == true:
        x+=1             #I'll assume you'll be moving in relation to
    if left == true:     #pixels so x = left and right movement
        x-=1             #while y = up and down movement, just remember
    if up == true:       #that pixel count starts from the top left
        y-=1
    if down == true:
        y+=1

```

---

### Post by lavinog on 2010-06-01
> **DrTravia said:**
> lol, I continued reading, you pretty much have your initial question answered, this post probly won't help all that much x.x

I won't delete the code though, figured I already wrote it, no point in deletion. It's also a much lower leveled directional code for all those not looking to create games with vectors just yet



Your approach seems to use 'a' (and I assume 'd') to toggle the direction.  In which case using a direction variable and incrementing it each time would simplify the code:
```

if keypress == 'a':
    direction-=1
    direction%=4    # ensure direction is 0 1 2 3

elif keypress == 'd':
    direction+=1
    direction%=4

elif keypress == 'w':
    if direction==0: y-=1
    if direction==1: x+=1
    if direction==2: y+=1
    if direction==3: x-=1

```

---

