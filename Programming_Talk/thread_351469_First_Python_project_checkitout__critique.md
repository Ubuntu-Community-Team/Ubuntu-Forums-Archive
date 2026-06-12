---
title: "First Python project checkitout / critique"
date: 2007-02-02
forum: Programming Talk
---

### Post by chipmonk010 on 2007-02-02
Ok so i got the idea from here:
[http://learnpydia.pbwiki.com/TasksBeginners](http://learnpydia.pbwiki.com/TasksBeginners)

And decided i would make a game like the infamous board game Battleship. I would like you all to check it out make suggestions as to my coding style practice etc or additions things i should go about differently. Any discussion criticism is welcome!!

The script is commented and i also included my own improvement ideas at the bottom but here they are again for ease in discussion.

Keep track of high scores, write to file ask for username etc
Use OOP to make some parts neater/more flexible (see comments)

Its fairly simple but obviously more advanced then rock paper scissors so i thought other beginners might find it interesting as well

here it is:

```

import random

# Builds a 2D square gameboard of the desired size
def make_grid (grid_size):	
	grid =[]
	for x in range(grid_size):
		grid.append([])
		for y in range(grid_size):
			grid[x].append('x')
	return grid

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (grid):
	while 1:
		possible_coords = []
		count = 0
		for x in range(len(grid)):
			count += 1
			possible_coords.append(count)
		random.shuffle(possible_coords)
		x = possible_coords[0] - 1
		random.shuffle(possible_coords)
		y = possible_coords[0] - 1
		if grid[y][x] == 'x': 				#Selects a point that is not occupied
			break
		else:
			continue
	return (x, y)						#format 0-9,0-9

# Prints the grid to the screen in human readable form
def paint_grid (grid):
	count = 0
	for x in range(len(grid)):
		for x in grid[count]:
			print x,
		print ""
		count += 1

# Used when drawing boats, prevents boats from overlaping
def check_points (grid, points_list):
	for point in points_list:
		if grid[point[1]][point[0]] != 'x':
			return False
	return True


def make_boat (grid, length):							
	while 1:
		#Randomly decide boat orientation
		pos_orient = ['v','h']
		random.shuffle(pos_orient)
		orient = pos_orient[0]	
		#Get a random starting point for a new boat
		start_point = rand_point(grid)
		x = start_point[0]
		y = start_point[1]
		#List of all current boats points
		point_list = [(x,y)]		
		count = 0
		#Randomly decides whether to build boat from start-right or start-left
		#Changes random decision if it conflicts with the edge of the board
		if orient == 'h':				 
			pos_directions = ['l','r']
			random.shuffle(pos_directions)
			direction = pos_directions[0]
			if direction == 'r' and x + 1 + length > len(grid):
				direction = 'l' 		
			elif direction == 'l' and x - length < 0:
				direction = 'r'
		#Same as above but for vertical boats
		elif orient == 'v':				
			pos_directions = ['u','d']
			random.shuffle(pos_directions)
			direction = pos_directions[0]
			if direction == 'd' and y + 1 + length > len(grid):	
				direction = 'u'	
			elif direction == 'u' and y - length < 0:
				direction = 'd'
		#These four blocks generate the correct number of points 
		#for the curent boat, 
		if direction == 'l':
			for num in range(length - 1):
				count += 1
				point_list.append((x-count,y))
		if direction == 'r':
			for num in range(length - 1):
				count += 1
				point_list.append((x+count,y))
		if direction == 'u':
			for num in range(length - 1):
				count +=1
				point_list.append((x,y-count))
		if direction == 'd':
			for num in range(length - 1):
				count +=1
				point_list.append((x,y+count))
		#Rebuild the boat if it crosses another boat
		if check_points(grid, point_list) == False:
			continue
		else:
			break
	#Writes 'b's for each point of this boat to the computers game board
	for point in point_list:
		grid[point[1]][point[0]] = 'b'		
	
	return point_list		
	
#Computer game board and variables
grid = make_grid(10)		
scout = make_boat(grid, 3)
patrol = make_boat(grid, 2)
battleship = make_boat(grid, 4)
carrier = make_boat(grid, 5)
hit_list = scout + patrol + battleship + carrier

#User game board and variables
user_grid = make_grid(len(grid))
hits = []
scout_hits = []
patrol_hits = []
battleship_hits = []
carrier_hits = []
moves = 0
	
while 1:	
	moves += 1
	#Paint the users grid
	paint_grid(user_grid)
	print ""
	#Cheaters uncomment below
	#paint_grid(grid)
	
	#Get coordinates from user
	while 1:
		try:
			coordx = int(raw_input('Enter an x coordinate from 1 to ' + str(len(grid)) + '\n' ))
		except ValueError:
			continue
		if coordx > 0 and coordx < 11: break
	while 1: 
		try:
			coordy = int(raw_input('Enter a y coordinate from 1 to ' + str(len(grid)) + '\n' ))
		except ValueError:
			continue
		if coordy > 0 and coordy < 11: break
	
	#Convert user perspective of x and y dimensions to a format compatible with the grid-list-matrix	
	user_point = (coordx - 1, len(grid) - coordy)
	userx = user_point[0]
	usery = user_point[1]
	
	#Prints user moves to the screen 
	if user_point in hit_list:
		user_grid[usery][userx] = 'h'
	else:
		user_grid[usery][userx] = 'm'	
		
	#Following blocks keep track of user hits on speciffic boats
	#if a hit occurs a message is displayed telling the user the boat type
	#**consider implimenting a boat class to reduce text and allow easy
	#change of boat roster**
	if user_point in scout:
		print "Scout Hit!"
		count = 0
		for point in scout:
			if scout[count] == user_point and user_point not in scout_hits:
				scout_hits.append(scout[count])
			count += 1
		if len(scout) == len(scout_hits):
			print "Scout Sunk!"

	elif user_point in patrol:
		print "Patrol Boat Hit!"
		count = 0
		for point in patrol:
			if patrol[count] == user_point and user_point not in patrol_hits:
				patrol_hits.append(patrol[count])
			count += 1
		if len(patrol) == len(patrol_hits):
			print "Patrol boat Sunk!"
 
	elif user_point in battleship:
		print "Battleship Hit!"
		count = 0
		for point in battleship:
			if battleship[count] == user_point and user_point not in battleship_hits:
				battleship_hits.append(battleship[count])
			count +=1
		if len(battleship) == len(battleship_hits):
			print "Battleship Sunk!"
	
	elif user_point in carrier:
		print "Carrier Hit!"
		count  = 0
		for point in carrier:
			if carrier[count] == user_point and user_point not in carrier_hits:
				carrier_hits.append(carrier[count])
			count += 1
		if len(carrier) == len(carrier_hits):
			print "Carrier Sunk!"
	
	else:	
		#If no boats are hit then a miss message is displayed
		#**Consider moving to block that writes user moves to the screen**
		print "Miss: No boats were hit"
		
	
	#Adds each hit to the users hit list
	count = 0
	for point in hit_list:
		if hit_list[count] == user_point and user_point not in hits:
			hits.append(hit_list[count])
		count += 1 	
	#Compares the user and computer hit lists
	#If the user has hit all targets possible the game ends
	if len(hit_list) == len(hits):
		print "You Win!!"
		print "Your score(lower = better): " + str(moves)
		break

#Inprovement ideas:
#High score: take users name and score and write to file, keep track of top 10
#Optimize with OOP: Use a boat class to cut down of code and allow easier roster changes

```

---

### Post by RHTopics on 2007-02-02
Good start for your first project.

Some observations:

The 'y' coordinate is backward.  Entering 'x' = 1 and 'y' = '1', put the 'm' at bottom left corner instead of at the top left corner.

Need a way to gracefully quit the running program.  'Ctrl-D' works, but it creates an error message.

In the original battleship game, letters (A through J for y coordinate) and numbers (1 through 10 for x coordinate) were used.  Thus, the game player could call out the coordinate like 'A1' for a target position.  You could incorporate this coordinate approach in your program and have just one user entry for a strike.

To help the user, print the coordinate numbers/letters on the outside of the grid.  And for easier distinguishing of hits and misses, may consider replacing the 'x's in the grid with '-'s.

The nice thing about python is that it lends itself to rapid application development, yet it is also easy to improve the code through refactoring.  In your comments you have already seen possible opportunities for implementing classes to reduce redundancies (refactoring).  You may also want to reduce the number of hard coded literals (magic numbers) in your program and replace them with constants or class attributes.

---

### Post by meng on 2007-02-02
Instead of defining a function make_grid(grid_size) you could just use this syntax:
size = 10
grid = size * [size * ['x']]

---

### Post by &lt;mawe&gt; on 2007-02-02
[quote="meng"]Instead of defining a function make_grid(grid_size) you could just use this syntax:
size = 10
grid = size * [size * ['x']][/quote]
Na, I don't think this is a good idea ;) Look:
```
In [1]: size = 4

In [2]: grid = size * [size * ["x"]]

In [3]: grid
Out[3]: 
[['x', 'x', 'x', 'x'],
 ['x', 'x', 'x', 'x'],
 ['x', 'x', 'x', 'x'],
 ['x', 'x', 'x', 'x']]

In [4]: grid[1][1] = "o"

In [5]: grid
Out[5]: 
[['x', 'o', 'x', 'x'],
 ['x', 'o', 'x', 'x'],
 ['x', 'o', 'x', 'x'],
 ['x', 'o', 'x', 'x']]
```
This would probably be better:
```
grid = [ [ "x" for i in range(size) ] for j in range(size) ]
```

Regards, mawe

---

### Post by meng on 2007-02-02
Doh! (can't find the slapping forehead smiley)
Back to the basics of assignment.
Nice catch mawe.

---

### Post by yaaarrrgg on 2007-02-03
Hey, great job for a first program!!! One of the best ways to learn a language is to try to write a game.  Creates challenging problems, and there's more than one solution.

My overall comment is that IMO you are working a bit harder than you need to.  Especially in  lines with lots of specifics checks and tests like:

```

        if orient == 'h':
            pos_directions = ['l','r']
            random.shuffle(pos_directions)
            direction = pos_directions[0]
            if direction == 'r' and x + 1 + length > len(grid):
                direction = 'l'
            elif direction == 'l' and x - length < 0:
                direction = 'r'

```

This is confusing to me.... In a multidimensional array, you can combine a lot of this logic, by how you increment the indices.  For example (disclaimer: I'm not a Python programmer :) !!! )

```

fun somefunction(n):

    # randomly pick an orientation, change in x will either be 1 or 0
    dx = random.randint(0,1)
    # change in y index will be the opposite
    dy = 1 - dx

    # then you can loop through like
    # remember that 0*num = 0, 1 * num = num
    for num in range(n):
        do_something( x + num * dx , y + num * dy )


```

I'd just randomly pick a square, check that there's enough space (all 'x' chars for the length of the boat), and write the boat.  If there's not enough space, this repeats... 

One other thing (which is just personal preference) is I'd treat the board as the representation of all the data (or game state).  I wouldn't track the ships seperately.  For example, I'd just write out a different letter for each boat.  Then, a function that counted the letters on the grid, which would let me know if a ship was still there, or the game was over.

---

### Post by chipmonk010 on 2007-02-03
Thanks guys lots of good stuff up there!

> The 'y' coordinate is backward. Entering 'x' = 1 and 'y' = '1', put the 'm' at bottom left corner instead of at the top left corner.

This was intentional because for some reason i had the picture of a math graph stuck in my head(aka center is 0 anything to the right or up is an increase in x or y respectively)
BUT now that you mention it NOT the way the game is! So ill fix that and i agree that some sort of numbering or number/letter system is needed along the outside of the grid to help the user pick a spot. good advice.

> grid = [ [ "x" for i in range(size) ] for j in range(size) ]

now that i like. much clearer shorter better all the way around.

For this part:

```

if orient == 'h':
            pos_directions = ['l','r']
            random.shuffle(pos_directions)
            direction = pos_directions[0]
            if direction == 'r' and x + 1 + length > len(grid):
                direction = 'l'
            elif direction == 'l' and x - length < 0:
                direction = 'r'

```

i randomly decide whether the boat should be vertical or horizontle then i also randomly decide which direction to draw to boat (aka from start point right or start point left etc)
Then if the random decision to go in a certain direction causes the boat to go off the map i reverse it. 

trying to understand your version. 

```

fun somefunction(n):
    # n = length of boat?

    # randomly pick an orientation, change in x will either be 1 or 0
    dx = random.randint(0,1)
    # change in y index will be the opposite
    dy = 1 - dx
    
    #ok so if dy = 1 we are vertical if dx = 1 we are horiz

    # then you can loop through like
    # remember that 0*num = 0, 1 * num = num
    for num in range(n):
        do_something( x + num * dx , y + num * dy )
    #increases only 1 dimension their by moving either up or right but not both


```

ok so i think i understand that but i would have to do some restructuring to use this method since i would have to check if the new point generated was off the grid or not
and it only accounts for up and right i would need a second similar block for start-down and start-left.
Am i understanding this correct?

whew! well tomorrow ill have to mess around with some changes, maybe i can go back and try to shrink the code a little like the example above.

Thanks all

---

### Post by yaaarrrgg on 2007-02-03
> **chipmonk010 said:**
> ok so i think i understand that but i would have to do some restructuring to use this method since i would have to check if the new point generated was off the grid or not
and it only accounts for up and right i would need a second similar block for start-down and start-left.
Am i understanding this correct?

Actually that's a good point.  I was thinking that the orientation wouldn't matter, although it will skew the random distribution of boats to one corner a little.  To fix this, you might multiply dx dy by -1 half the time:

```

    dx = random.randint(0,1)
    dy = 1 - dx
    if random.randint(0,1) == 1:
        dx = -1 * dx
        dy = -1 * dy

```

then this would go in all four directions.  With this approach  there would also need to be a function that checked the bounds of a point: to see that it was valid, roughly like:

```

#roughly, although probaby want to define all numeric literals as constants
fun in_bounds(x,y):
    return x>= 0 && x <= 9 && y >= 0 && y<= 9

```

Of course, my background is in math, so i tend to model things as arrays and use a lot of simple equations (involving 1, 0, -1 for example).  My approach might not make much sense, although I understand things better this way :)   It might help collapse some of the repeated checks, which seem to form a larger pattern.

---

### Post by chipmonk010 on 2007-02-03
> **yaaarrrgg said:**
> Actually that's a good point.  I was thinking that the orientation wouldn't matter, although it will skew the random distribution of boats to one corner a little.  To fix this, you might multiply dx dy by -1 half the time:

```

    dx = random.randint(0,1)
    dy = 1 - dx
    if random.randint(0,1) == 1:
        dx = -1 * dx
        dy = -1 * dy

```

then this would go in all four directions.  With this approach  there would also need to be a function that checked the bounds of a point: to see that it was valid, roughly like:

```

#roughly, although probaby want to define all numeric literals as constants
fun in_bounds(x,y):
    return x>= 0 && x <= 9 && y >= 0 && y<= 9

```

Of course, my background is in math, so i tend to model things as arrays and use a lot of simple equations (involving 1, 0, -1 for example).  My approach might not make much sense, although I understand things better this way :)   It might help collapse some of the repeated checks, which seem to form a larger pattern.

I was trying to figure out how i would handle this area with a less repetitive code and i think this is exactly what you are showing me. I agree its a little difficult to understand at first glance but perhaps a hybrid of sorts would be better similar structure to yours and some more verbose variable names.

thanks yaaarrrg for your input and explanations!

---

### Post by pmasiar on 2007-02-03
> **chipmonk010 said:**
> Ok so i got the idea from here:
[http://learnpydia.pbwiki.com/TasksBeginners](http://learnpydia.pbwiki.com/TasksBeginners)


I hope you had fun, and you are welcome to try other posted problems too.

You did a great work for a beginner. I will give you couple of suggestions for improvement - these is not a critique but suggestions.

1) using "magic" string and numbers. For making changes/enhancements easier in the future, define bunch of constants, or even consider moving all "magic" variables to separate module, like config.py. If you want, you can make these variables real constants, ActiveState maintains great cookbook recipes and Google knows about it [http://www.google.com/search?q=activestate+python+cookbook+constant](http://www.google.com/search?q=activestate+python+cookbook+constant)

Of course making it real constants is not of concern for this little example, but for real tasks you may want to do it. Or not, it depends ...  :-)

2) You are working very hard to represent your data. Python has very flexible data structures. String is array of characters, so your grid (10 by 10) can be list of 10 strings, 10 char long.

3) you are working even harder to print the grid - something original requirements did not asked for :-) Good habit is to use LAW- Least Amount of Work - because often your guess that user wanted is wrong, and you need to refactor your code anyway. The more code you have, the harder is it to refactor, and sometimes you coded some functionality that used did not asked for but you added it anyway, you might be reluctant to throw it out, so you maintain it even if users did not use it at all.

4) random module has many other useful methods: random.choice('up", "down", "left", "right") does exactly what you would expect :-)

But you will get there - try solving other problems, and keep us posted :-)

---

### Post by chipmonk010 on 2007-02-05
Version 2.0:

I made some improvements, mostly shortening the functions using ideas from yaaarrrgg et all. I added reference numbers to the users board, although i did not go with the number/letter reference system yet because it conflicts with changing the board size and also limits the maximum size. 

There are also some better variable name choices and other things that i have probably forgotten.

There is alot more i want to do with this script (implementing a boat class being at the top of the list) but i thought a little update was in order so here it is.

```

import random
#Configuration variables
board_size = 10
board_char = 'x'
boat_char = 'b'

# Prints the grid to the screen in human readable form
def paint_grid (grid):
	for i in range(len(grid)):
		for j in grid[i]: 
			print str(j) + str(' ')* (1/len(str(j))),
		print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point ():
	while 1:
		x = random.randint(0,board_size-1)
		y = random.randint(0,board_size-1)
		#check that point is empty
		if game_board[y][x] == board_char: 			 
			break
	#format (0-9,0-9)
	return (x, y)						

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list):
	for point in point_list:
		x = point[0] 
		y = point[1]
		if x < 0 or x > board_size - 1:
			return False
		if y < 0 or y > board_size - 1:
			return False
		if game_board[y][x] != board_char:
			return False
	return True

def make_boat (length):							
	while 1:
		#Randomly decide axis on which to draw boat
		dx = random.randint(0,1)
		dy = 1 - dx	
		#Randomly decide direction on given axis
		if random.randint == 1:
			dx = -1 * dx
			dy = -1 * dy
		#Get a random starting point for a new boat
		start_point = rand_point()
		point_list = [start_point]
		for i in range(length - 1):
			last_point = point_list[-1]
			x = last_point[0]+dx
			y = last_point[1]+dy
			point_list.append((x,y))
		if check_points(point_list): break
		else: continue
	for point in point_list:
		game_board[point[1]][point[0]] = boat_char		
	return point_list		
	
#Computer game board and variables
game_board = [[board_char for i in range(board_size)] for j in range(board_size)]
scout = make_boat(3)
patrol = make_boat(2)
battleship = make_boat(4)
carrier = make_boat(5)
hit_list = scout + patrol + battleship + carrier

#User game board and variables
user_grid = [[board_char for i in range(board_size+1)] for j in range(board_size+1)]
user_grid[0][0] = '  '
for i in range(board_size):
	user_grid[0][i+1] = i+1
	user_grid[i+1][0] = i+1
	if i < 9:	
		user_grid[i+1][0] = " " + str(user_grid[i+1][0])

hits = []
scout_hits = []
patrol_hits = []
battleship_hits = []
carrier_hits = []
moves = 0
	
while 1:	
	moves += 1
	#Paint the users grid
	paint_grid(user_grid)
	print ""
	#Cheaters uncomment below
	#paint_grid(game_board)
	
	#Get coordinates from user
	while 1:
		try:
			input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(board_size) + '\n' ))
		except ValueError:
			continue
		if input_x > 0 and input_x < board_size + 1: break
	while 1: 
		try:
			input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(board_size) + '\n' ))
		except ValueError:
			continue
		if input_y > 0 and input_y < board_size + 1: break	
	
	user_point = (input_x, input_y)
	
	#Prints user moves to the screen 
	if user_point in hit_list:
		user_grid[input_y][input_x] = 'h'
	else:
		user_grid[input_y][input_x] = 'm'	
		
	#Following blocks keep track of user hits on speciffic boats
	#if a hit occurs a message is displayed telling the user the boat type
	#**consider implimenting a boat class to reduce text and allow easy
	#change of boat roster**
	if user_point in scout:
		print "Scout Hit!"
		count = 0
		for point in scout:
			if scout[count] == user_point and user_point not in scout_hits:
				scout_hits.append(scout[count])
			count += 1
		if len(scout) == len(scout_hits):
			print "Scout Sunk!"

	elif user_point in patrol:
		print "Patrol Boat Hit!"
		count = 0
		for point in patrol:
			if patrol[count] == user_point and user_point not in patrol_hits:
				patrol_hits.append(patrol[count])
			count += 1
		if len(patrol) == len(patrol_hits):
			print "Patrol boat Sunk!"
 
	elif user_point in battleship:
		print "Battleship Hit!"
		count = 0
		for point in battleship:
			if battleship[count] == user_point and user_point not in battleship_hits:
				battleship_hits.append(battleship[count])
			count +=1
		if len(battleship) == len(battleship_hits):
			print "Battleship Sunk!"
	
	elif user_point in carrier:
		print "Carrier Hit!"
		count  = 0
		for point in carrier:
			if carrier[count] == user_point and user_point not in carrier_hits:
				carrier_hits.append(carrier[count])
			count += 1
		if len(carrier) == len(carrier_hits):
			print "Carrier Sunk!"
	
	else:	
		#If no boats are hit then a miss message is displayed
		#**Consider moving to block that writes user moves to the screen**
		print "Miss: No boats were hit"
		
	
	#Adds each hit to the users hit list
	count = 0
	for point in hit_list:
		if hit_list[count] == user_point and user_point not in hits:
			hits.append(hit_list[count])
		count += 1 	
	#Compares the user and computer hit lists
	#If the user has hit all targets possible the game ends
	if len(hit_list) == len(hits):
		print "You Win!!"
		print "Your score(lower = better): " + str(moves)
		break

#Inprovement ideas:
#High score: take users name and score and write to file, keep track of top 10
#Optimize with OOP: Use a boat class to cut down of code and allow easier roster changes

```

P.S Thanks again for everyone input/comments!

---

### Post by yaaarrrgg on 2007-02-05
Hey, that's looking good!   Much easier to understand now, at least for me :)

One other idea: what if you use a '.' char for an unused space...?  May be easier to read, for example:

```

    Battleship Hit!
       1  2  3  4  5  6  7  8  9  10
     1 .  .  .  .  .  .  .  .  .  .
     2 m  m  .  .  .  .  .  .  .  .
     3 .  h  m  .  .  .  .  .  .  .
     4 .  h  m  .  .  .  .  .  .  .
     5 .  .  .  .  .  .  .  .  .  .
     6 .  .  .  .  m  .  .  .  h  .
     7 .  .  .  .  .  h  .  .  .  .
     8 .  .  .  .  .  .  m  .  .  .
     9 .  .  .  .  .  .  .  .  .  .
    10 .  .  .  .  .  .  .  .  .  .

```

Edit: well, this might look screwy if it's not showing as a monospaced font.... :)

---

### Post by chipmonk010 on 2007-02-06
Version 3: boat classes

sorry for the short time between versions but i had some time last night and i decided to knock out the boat class and restructuring that goes along with it. So here it is.

also set the default board_char to '.' as suggested by yaaarrg which is much easier on the eyes.

```

import random

# Prints the grid to the screen in human readable form
def paint_grid (grid):
	for i in range(len(grid)):
		for j in grid[i]: 
			print str(j) + str(' ')* (1/len(str(j))),
		print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point ():
	while 1:
		x = random.randint(0,board_size-1)
		y = random.randint(0,board_size-1)
		#check that point is empty
		if game_board[y][x] == board_char: break
	return (x, y)						

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list):
	for point in point_list:
		x = point[0] 
		y = point[1]
		if x < 0 or x > board_size - 1:
			return False
		if y < 0 or y > board_size - 1:
			return False
		if game_board[y][x] != board_char:
			return False
	return True

class boat:
	def __init__ (self):
		self.hit_list = []
		self.sunk = False							
		while 1:
			#Randomly decide axis on which to draw boat
			dx = random.randint(0,1)
			dy = 1 - dx	
			#Randomly decide direction on given axis
			if random.randint == 1:
				dx = -1 * dx
				dy = -1 * dy
			#Get a random starting point for a new boat
			self.start_point = rand_point()
			self.point_list = [self.start_point]
			for i in range(self.length - 1):
				last_point = self.point_list[-1]
				x = last_point[0]+dx
				y = last_point[1]+dy
				self.point_list.append((x,y))
			if check_points(self.point_list): break
			else: continue
		for point in self.point_list:
			game_board[point[1]][point[0]] = boat_char				
	def is_hit (self, point):
		if point in self.point_list:
			print self.name, "Hit!"
			user_grid[point[1]+1][point[0]+1] = 'h'
			if point not in self.hit_list:
				self.hit_list.append(point)
			if len(self.point_list) == len(self.hit_list):
				print self.name, "Sunk!"
				self.sunk = True		
class patrol(boat):
	def __init__ (self):
		self.name = "Patrol Boat"
		self.length = 2
		boat.__init__(self)
class destroyer(boat):
	def __init__ (self):
		self.name = "Destroyer"
		self.length = 3
		boat.__init__(self)
class battleship(boat):
	def __init__ (self):
		self.name = "Battleship"
		self.length = 4
		boat.__init__(self)
class carrier(boat):
	def __init__ (self):
		self.name = "Carrier"
		self.length = 5
		boat.__init__(self)

#Configuration variables
board_size = 10
board_char = '.'
boat_char = 'b'

#Computer game board
game_board = [[board_char for i in range(board_size)] for j in range(board_size)]
#User game board
user_grid = [[board_char for i in range(board_size+1)] for j in range(board_size+1)]
user_grid[0][0] = '  '
for i in range(board_size):
	user_grid[0][i+1] = i+1
	user_grid[i+1][0] = i+1
	if i < 9:	
		user_grid[i+1][0] = " " + str(user_grid[i+1][0])
user_moves = 0

#Boat roster
boat_list = [patrol(),destroyer(),battleship(),carrier()]

#Main loop
while 1:	
	user_moves += 1
	#Paint the users grid
	paint_grid(user_grid)
	print ""
	#Cheaters uncomment below
	#paint_grid(game_board)
	
	#Get coordinates from user
	while 1:
		try:
			input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(board_size) + '\n' ))
		except ValueError:
			continue
		if input_x > 0 and input_x < board_size + 1: break
	while 1: 
		try:
			input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(board_size) + '\n' ))
		except ValueError:
			continue
		if input_y > 0 and input_y < board_size + 1: break	
	#Change coordinates to computer readable form
	input_x -= 1
	input_y -= 1
	#When ever writing to the user grid add 1 to each coord.
	user_grid[input_y+1][input_x+1] = 'm'

	user_point = (input_x, input_y)
	total_boats = len(boat_list)
	sunk_boats = 0
	for boat in boat_list:
		boat.is_hit(user_point)
		if boat.sunk == True:
			sunk_boats +=1
	if sunk_boats == total_boats:
		print "You Win!!"
		print "Completed in " + str(user_moves) + " moves."
		break

```

---

### Post by RHTopics on 2007-02-06
Played around with your code and made the following changes:

    Changed constants to be upper case to improved their visibility.

    Removed global variables from classes and functions, instead passed
    the former globals as arguments to the classes and functions.

    Separated the non function and non class code under a
    if __name__ == "__main__":  to better identify opportunities for
    modularity.

    Converted a hard "while" into a conditional "while" statement.

The code is below for your consideration.
```

import random

#Configuration constants
BOARD_SIZE = 10
BOARD_CHAR = '.'
BOAT_CHAR = 'b'

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, user_grid, point):
        if point in self.point_list:
            print self.name, "Hit!"
            user_grid[point[1]+1][point[0]+1] = 'h'
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print self.name, "Sunk!"
                self.sunk = True        
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = i+1
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    #Main loop
    while 1:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print ""
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while 1:
            try:
                input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            if input_x > 0 and input_x < BOARD_SIZE + 1: break
        while 1: 
            try:
                input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            if input_y > 0 and input_y < BOARD_SIZE + 1: break    
        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = 'm'

        user_point = (input_x, input_y)
        total_boats = len(boat_list)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_grid, user_point)
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            print "You Win!!"
            print "Completed in " + str(user_moves) + " moves."
            break
```

---

### Post by chipmonk010 on 2007-02-07
Thanks RHTopic for your revisions!

In the spirit of your changes I decided to move the writing of h's to the users grid out of the class and into the main function. Seems more readable having the only two writes to the user grid in the same function and it also means the user grid doesnt have to be passed into the class.



heres the result:

```

import random

#Configuration constants
BOARD_SIZE = 10
BOARD_CHAR = '.'
BOAT_CHAR = 'b'

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
	if point in self.point_list:
            	print self.name, "Hit!"
		self.hit = True
        	if point not in self.hit_list:
                	self.hit_list.append(point)
        	if len(self.point_list) == len(self.hit_list):
                	print self.name, "Sunk!"
			self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = i+1
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    #Main loop
    while 1:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print ""
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while 1:
            try:
                input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            if input_x > 0 and input_x < BOARD_SIZE + 1: break
        while 1: 
            try:
                input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            if input_y > 0 and input_y < BOARD_SIZE + 1: break    
        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = 'm'

        user_point = (input_x, input_y)
        total_boats = len(boat_list)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
	    if boat.hit == True:
		user_grid[input_y+1][input_x+1] = 'h'
            if boat.sunk == True:
		sunk_boats +=1
        if sunk_boats == total_boats:
            print "You Win!!"
            print "Completed in " + str(user_moves) + " moves."
            break

```

---

### Post by dannyboy79 on 2007-02-07
I want to learn python but it's going very slow for me. I have never programmed before in my life. i am using this ([http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)) as a starting guide. and after reading all the posts in this thread I have to admit I have no idea what any of you guys are even talking about. I wanted to tell you that this is the coolest ever!!!! is there any reason why you're not incorporating the A thru J along the top? and then also, being able to just enter B7 all at once instead of having to enter your location you want to strike twice? Don't get me wrong, as I have said, I have no idea how hard it would be to incorporate those ideas into your program, I am merely asking so I can understand how hard it would be. no matter what, this is making me even more excited to learn how to do this kind of thing. i do have to admit, I am only at the end of the Raw Materials Section so that is probably why I don't understand much of what you guys are saying.

---

### Post by dannyboy79 on 2007-02-07
alright, well I finally finished playing it for the very first time. It took me 63 moves. that darn patrol boat is tiny. only 2 spaces, WOW. anyway, just a few things. when I entered the last location, x=2 and y=3, it stated Patrol Boat Hit, Patrol Boat Sunk, You Win!! but when I look at the graph, there is no "h" in x=2 y=3 spot??  here is the pic for your reference
   1  2  3  4  5  6  7  8  9  10
 1 m  m  h  m  m  m  m  m  m  m
 2 m  m  h  m  m  m  m  m  m  m
 3 h  .  h  .  m  .  .  .  .  m
 4 m  m  h  m  .  .  m  .  m  .
 5 .  .  m  m  .  m  .  m  .  .
 6 m  m  .  m  m  .  m  .  .  h
 7 .  .  .  m  .  m  .  .  m  h
 8 m  h  h  h  h  h  .  m  .  h
 9 .  .  m  .  m  .  m  .  .  m
10 m  m  .  m  .  m  .  m  .  .

Enter an x coordinate from 1 to 10
2
Enter a y coordinate from 1 to 10
3
Patrol Boat Hit!
Patrol Boat Sunk!
You Win!!
Completed in 63 moves.

also, couldn't you use something that stuck out more for a HIT, like maybe the * or + or maybe even the @. just a thought, otherwise great job for your first program!!!!!

---

### Post by chipmonk010 on 2007-02-07
> **dannyboy79 said:**
> I want to learn python but it's going very slow for me. I have never programmed before in my life. i am using this ([http://www.freenetpages.co.uk/hp/alan.gauld/](http://www.freenetpages.co.uk/hp/alan.gauld/)) as a starting guide. and after reading all the posts in this thread I have to admit I have no idea what any of you guys are even talking about. I wanted to tell you that this is the coolest ever!!!! is there any reason why you're not incorporating the A thru J along the top? and then also, being able to just enter B7 all at once instead of having to enter your location you want to strike twice? Don't get me wrong, as I have said, I have no idea how hard it would be to incorporate those ideas into your program, I am merely asking so I can understand how hard it would be. no matter what, this is making me even more excited to learn how to do this kind of thing. i do have to admit, I am only at the end of the Raw Materials Section so that is probably why I don't understand much of what you guys are saying.


You might find this site helpful:
[http://learnpydia.pbwiki.com/#Tasksforpythonlearners](http://learnpydia.pbwiki.com/#Tasksforpythonlearners)

i'd also recomend: Learning Python (O'Reilly pub.)

As for the A thru J on top thats gonna be my next goal now that the rest of the code is up to snuff. It shouldnt be insanely difficult but its not as simple as just printing A thru J. 
The main factors:
I want to be able to retain the ablility to resize the game board 10x10 to 25x25
need to re-write the code that takes the user input to parse a string aka 'A5'
it would also be nice if i could generate an ordered list of the A-Z without having to type it out(have to look into that one)

python is lots of fun good luck!

---

### Post by chipmonk010 on 2007-02-07
> **dannyboy79 said:**
> alright, well I finally finished playing it for the very first time. It took me 63 moves. that darn patrol boat is tiny. only 2 spaces, WOW. anyway, just a few things. when I entered the last location, x=2 and y=3, it stated Patrol Boat Hit, Patrol Boat Sunk, You Win!! but when I look at the graph, there is no "h" in x=2 y=3 spot??  here is the pic for your reference
   1  2  3  4  5  6  7  8  9  10
 1 m  m  h  m  m  m  m  m  m  m
 2 m  m  h  m  m  m  m  m  m  m
 3 h  .  h  .  m  .  .  .  .  m
 4 m  m  h  m  .  .  m  .  m  .
 5 .  .  m  m  .  m  .  m  .  .
 6 m  m  .  m  m  .  m  .  .  h
 7 .  .  .  m  .  m  .  .  m  h
 8 m  h  h  h  h  h  .  m  .  h
 9 .  .  m  .  m  .  m  .  .  m
10 m  m  .  m  .  m  .  m  .  .

Enter an x coordinate from 1 to 10
2
Enter a y coordinate from 1 to 10
3
Patrol Boat Hit!
Patrol Boat Sunk!
You Win!!
Completed in 63 moves.

also, couldn't you use something that stuck out more for a HIT, like maybe the * or + or maybe even the @. just a thought, otherwise great job for your first program!!!!!

Nice catch with the final move not showing up i didnt notice it. heres the fixed code and i also added constants for the hit character and the miss character at the top of the file so you can easily set them to whatever you like. 

```

import random

#Configuration constants
BOARD_SIZE = 10
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
	if point in self.point_list:
            	print self.name, "Hit!"
		self.hit = True
        	if point not in self.hit_list:
                	self.hit_list.append(point)
        	if len(self.point_list) == len(self.hit_list):
                	print self.name, "Sunk!"
			self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = i+1
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    #Main loop
    while 1:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print ""
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while 1:
            try:
                input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            if input_x > 0 and input_x < BOARD_SIZE + 1: break
        while 1: 
            try:
                input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            if input_y > 0 and input_y < BOARD_SIZE + 1: break    
        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = MISS_CHAR

        user_point = (input_x, input_y)
        total_boats = len(boat_list)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
	    if boat.hit == True:
		user_grid[input_y+1][input_x+1] = HIT_CHAR
            if boat.sunk == True:
		sunk_boats +=1
        if sunk_boats == total_boats:
         	paint_grid(user_grid)	   
		print "You Win!!"
            	print "Completed in " + str(user_moves) + " moves."
            	break

```

---

### Post by RHTopics on 2007-02-07
I am glad you liked and incorporated the revisions.  Yes, I see where you made the changes to "is_hit" and the main function.  That does make it cleaner.

I have revised your latest revision with some interface improvements by including a way to gracefully quit the game by using Ctrl-d.  Also, included print statements to clear the screen between plays.


The code is below: (note: tabs have been converted to 4 spaces)
```

#!/usr/bin/env python

import random

#Configuration constants
BOARD_SIZE = 10
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        print "\n" * 50
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = i+1
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    # Setup for Main Loop
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * 50

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print "\n Press Ctrl-d to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue

            if input_x > 0 and input_x < BOARD_SIZE + 1: break
        while continueGame: 
            try:
                input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue

            if input_y > 0 and input_y < BOARD_SIZE + 1: break

        if not continueGame:
           continue

        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_grid[input_y+1][input_x+1] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_grid)       
            print "You Win!!"
            print "Completed in " + str(user_moves) + " moves."

```

---

### Post by yaaarrrgg on 2007-02-07
> **chipmonk010 said:**
> You might find this site helpful:
[http://learnpydia.pbwiki.com/#Tasksforpythonlearners](http://learnpydia.pbwiki.com/#Tasksforpythonlearners)
As for the A thru J on top thats gonna be my next goal now that the rest of the code is up to snuff. It shouldnt be insanely difficult but its not as simple as just printing A thru J. 
The main factors:
I want to be able to retain the ablility to resize the game board 10x10 to 25x25
need to re-write the code that takes the user input to parse a string aka 'A5'
it would also be nice if i could generate an ordered list of the A-Z without having to type it out(have to look into that one)
python is lots of fun good luck!

If you are worried about size restrictions < 26, you might design it so that it can take double and and triple letters too.  Perhaps like "A  B C ... X Y Z AA AB AC ..." like a base 26 number.

Otherwise, one quick edit, might just be to write some functions that convert between the chars and ints, like:

```

# convert chars to and from int ( A == 1 )
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
def ctoi( c ):
    return ALPHA.find( c.upper() ) + 1
def itoc( i ):
    return ALPHA[i - 1]

```

then, a change in two lines:

```

input_x = ctoi(raw_input('Enter an x coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))

```

and 

```

user_grid[0][i+1] = itoc(i+1)

```

but will need to change the check for i < 9....    course this doesn't parse input like 'A5' yet.

---

### Post by RHTopics on 2007-02-07
The last code that I posted introduced a problem with printing hit messages.

For the function is_hit, I put in a print statement to clear the screen, yet it also rolls off the
the hit messages.  Remove the print statement to stop this.  Need to find another place to put it.

```

def is_hit (self, point):
        self.hit = False
        print "\n" * 50   <----------- remove
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True
```

---

### Post by RHTopics on 2007-02-07
I located where the print should be to clear the screen after each play.

Below is the complete code:

```

#!/usr/bin/env python

import random

#Configuration constants
BOARD_SIZE = 10
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = i+1
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    # Setup for Main Loop
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * 50

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print "\n Press Ctrl-d to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input_x = int(raw_input('Enter an x coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue

            if input_x > 0 and input_x < BOARD_SIZE + 1: break
        while continueGame: 
            try:
                input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue

            if input_y > 0 and input_y < BOARD_SIZE + 1: break

        if not continueGame:
           continue

        print "\n" * 50

        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_grid[input_y+1][input_x+1] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_grid)       
            print "You Win!!"
            print "Completed in " + str(user_moves) + " moves."

```

---

### Post by dannyboy79 on 2007-02-07
2 more comments, i tried the game all the way down to grid being 5 and it still worked. when I tried 4 it got stuck and I just hit ctrl-c and just assumed that was to small. also, I don't like the clear that you put into the game. for instance, I shot at 4,3 and it stated that I hit a destroyer, then I did 4,4, then it said I hit a carrier. then since you added that clear, I couldn't see what my last move was and what spot it was just prior to hitting the carrier. so it made me kind of double think myself as to whether I had hit a carrier before or if I do remember hitting the destroyer. luckily I was able to scroll up and it was there but I like it like it was before, I would think you'll always want to know exactly the last time you got a hit and what it was. this is most likely a preference thing but you did ask for feedback. thanks again, i love this little game. oh, I did the 5 grid in 21 moves, c if you can beat that?

---

### Post by dannyboy79 on 2007-02-07
5 grid.
You Win!!
Completed in 17 moves.

---

### Post by chipmonk010 on 2007-02-07
latest version:
added number/letter coordinates using yaaargg's technique only used the char_to_int
function tho.
string formated "You Win" to match RHtopics addtions
added WHITE_SPACE constant so user can set how much white space between plays
(gotta love those constants)
also left comment on game_board size limitations as tested by dannyboy
incorperated RHTopics additions:
string formating
self execution
whitespace
and graceful exit Control-D

RHtopic could you explain how this works i see it has something to do with the EOF exception.....does control-D just throw an EOF error?

thanks all its lookin goood
```


#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 15	 	
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

def char_to_int (char):
	return ALPHA.find(char.upper() ) + 1

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = ALPHA[i]
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    # Setup for Main Loop
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * WHITE_SPACE

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print "\n Press Ctrl-d to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input_x = char_to_int(raw_input('Enter a letter from A to ' + ALPHA[BOARD_SIZE-1] + '\n' ))
	    except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue

            if input_x > 0 and input_x < BOARD_SIZE + 1: break
        while continueGame: 
            try:
                input_y = int(raw_input('Enter a y coordinate from 1 to ' + str(BOARD_SIZE) + '\n' ))
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue

            if input_y > 0 and input_y < BOARD_SIZE + 1: break

        if not continueGame:
           continue

        print "\n" * WHITE_SPACE

        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_grid[input_y+1][input_x+1] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_grid)       
            print "You Win!!"
            print "Completed in %i moves." % moves



```

---

### Post by chipmonk010 on 2007-02-07
yet another version:

Number/letter combo input :guitar:

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 15	 	
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"

def char_to_int (char):
	return ALPHA.find(char.upper() ) + 1

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects an 'x'
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        #check that point is empty
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = [[BOARD_CHAR for i in range(BOARD_SIZE)] for j in range(BOARD_SIZE)]
    #User game board
    user_grid = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    user_grid[0][0] = '  '
    for i in range(BOARD_SIZE):
        user_grid[0][i+1] = ALPHA[i]
        user_grid[i+1][0] = i+1
        if i < 9:    
            user_grid[i+1][0] = " " + str(user_grid[i+1][0])
    user_moves = 0

    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    # Setup for Main Loop
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * WHITE_SPACE

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users grid
        paint_grid(user_grid)
        print "\n Press Ctrl-d to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input = raw_input('Enter a letter/number combination\n' )
		if len(input) > 3: continue
		input_x = char_to_int(input[0])
	        input_y = int(input[1:3])
	    except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue
  	    if input_x > 0 and input_x < BOARD_SIZE +1:
		if input_y > 0 and input_y < BOARD_SIZE + 1:
		    break        
        if not continueGame:
           continue

        print "\n" * WHITE_SPACE

        #Change coordinates to computer readable form
        input_x -= 1
        input_y -= 1
        #When ever writing to the user grid add 1 to each coord.
        user_grid[input_y+1][input_x+1] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_grid[input_y+1][input_x+1] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_grid)       
            print "You Win!!"
            print "Completed in %i moves." % moves


```

---

### Post by RHTopics on 2007-02-07
> RHtopic could you explain how this works i see it has something to do with the EOF exception.....does control-D just throw an EOF error?

That's exactly right.  If you go back to an earlier versions, you can see the error on the last line of screen after doing a Control D.  Doing a Control C produces the error KeyboardInterrupt, which also could be trapped and ignored.

It is looking good.

If you wanted to streamline the input, you could have the player enter both the letter and number together at one time.  That is, like the way Calc in OpenOffice.org would reference a cell (i.e.  A10).  Then the program could convert it.

Edit: you already did it.  Wow, this program is quickly evolving

---

### Post by chipmonk010 on 2007-02-07
fixing:
the moves print that i broke
indent stupidity with value error exception
both user and comp now use a board with numbered/lettered sides:
    makes cheating easier lol
    reduces confusion userboard[1][1] now == gameboard[1][1]
    also created newboard() func to make it neater

ok i promise i wont post another version untill its something substantial

```


#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50

# Build empty board
def new_board ():
    new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    new_board[0][0] = '  '
    for i in range(BOARD_SIZE):
        new_board[0][i+1] = ALPHA[i]
        new_board[i+1][0] = i+1
        if i < 9:    
            new_board[i+1][0] = " " + str(new_board[i+1][0])
    return new_board
    
# Converts chars to ints (A == 1)
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
def char_to_int (char):
    return ALPHA.find(char.upper() ) + 1

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects a spot
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board):
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
class patrol(boat):
    def __init__ (self, game_board):
        self.name = "Patrol Boat"
        self.length = 2
        boat.__init__(self, game_board)
class destroyer(boat):
    def __init__ (self, game_board):
        self.name = "Destroyer"
        self.length = 3
        boat.__init__(self, game_board)
class battleship(boat):
    def __init__ (self, game_board):
        self.name = "Battleship"
        self.length = 4
        boat.__init__(self, game_board)
class carrier(boat):
    def __init__ (self, game_board):
        self.name = "Carrier"
        self.length = 5
        boat.__init__(self, game_board)

if __name__ == "__main__":

    #Computer game board
    game_board = new_board()
    #User game board
    user_board = new_board()
    #Boat roster
    boat_list = [patrol(game_board),destroyer(game_board),
        battleship(game_board),carrier(game_board)]

    # Setup for Main Loop
    user_moves = 0
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * WHITE_SPACE

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users board
        paint_grid(user_board)
        print "\nPress Ctrl-D to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if len(input) > 3: continue
                input_x = char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue
            except KeyboardInterrupt:
                continueGame = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    break        
        
        if not continueGame:
           continue
        print "\n" * WHITE_SPACE
        
        user_board[input_y][input_x] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_board[input_y][input_x] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_board)       
            print "You Win!!"
            print "Completed in %i moves." % user_moves
    



```

---

### Post by RHTopics on 2007-02-07
chipmonk010,

It continues to look good.

I did some refactoring with your code:

Eliminated your classes for individual boats.  Instead, I passed their former attributes as arguments into new instances of the boat class.

Created a dictionary to hold the boat names and their lengths.  Iterated through this dictionary to create instances of the boat class.

For your consideration, the code is below:

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50

#Boat length dictionary
boatLengths = {"Patrol Boat":2, "Destroyer":3, "Battleship":4,
               "Carrier":5}

# Build empty board
def new_board ():
    new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    new_board[0][0] = '  '
    for i in range(BOARD_SIZE):
        new_board[0][i+1] = ALPHA[i]
        new_board[i+1][0] = i+1
        if i < 9:    
            new_board[i+1][0] = " " + str(new_board[i+1][0])
    return new_board
    
# Converts chars to ints (A == 1)
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
def char_to_int (char):
    return ALPHA.find(char.upper() ) + 1

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects a spot
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board, name, length):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 

if __name__ == "__main__":

    #Computer game board
    game_board = new_board()
    #User game board
    user_board = new_board()
    
    #Build boat roster from boat lengths dictionary
    boat_list = []
    for boatName, boatLength in boatLengths.iteritems():
        boat_list.append(boat(game_board, boatName, boatLength))

    # Setup for Main Loop
    user_moves = 0
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * WHITE_SPACE

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users board
        paint_grid(user_board)
        print "\nPress Ctrl-D to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if len(input) > 3: continue
                input_x = char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue
            except KeyboardInterrupt:
                continueGame = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    break        
        
        if not continueGame:
           continue
        print "\n" * WHITE_SPACE
        
        user_board[input_y][input_x] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_board[input_y][input_x] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_board)       
            print "You Win!!"
            print "Completed in %i moves." % user_moves

```

---

### Post by chipmonk010 on 2007-02-07
RHTopic:
I like your idea but i modified it slightly using a list of tuples instead of a dictionary.
This way you can have more then one of the same boat, for instance three patrol boats and a scuba guy(see code), and you also get the ability to have custom sizes/names(like suba guy) as in your version. The possible boat rosters are unlimited.

Check it out:

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),('Scuba Guy',1)]
ROSTER = EASY

# Build empty board
def new_board ():
    new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] for j in range(BOARD_SIZE+1)]
    new_board[0][0] = '  '
    for i in range(BOARD_SIZE):
        new_board[0][i+1] = ALPHA[i]
        new_board[i+1][0] = i+1
        if i < 9:    
            new_board[i+1][0] = " " + str(new_board[i+1][0])
    return new_board
    
# Converts chars to ints (A == 1)
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
def char_to_int (char):
    return ALPHA.find(char.upper() ) + 1

# Prints the grid to the screen in human readable form
def paint_grid (grid):
    for i in range(len(grid)):
        for j in grid[i]: 
            print str(j) + str(' ')* (1/len(str(j))),
        print ""

# Takes a 2D game board of any size randomly selects a spot
def rand_point (game_board):

    positionOccupied = True
    while positionOccupied:
        x = random.randint(0,BOARD_SIZE-1)
        y = random.randint(0,BOARD_SIZE-1)
        if game_board[y][x] == BOARD_CHAR:
            positionOccupied = False

    return (x, y)                        

# Used when drawing boats, prevents boats from overlaping
def check_points (point_list, game_board):
    for point in point_list:
        x = point[0] 
        y = point[1]
        if x < 0 or x > BOARD_SIZE - 1:
            return False
        if y < 0 or y > BOARD_SIZE - 1:
            return False
        if game_board[y][x] != BOARD_CHAR:
            return False
    return True

class boat:
    def __init__ (self, game_board, name, length):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False                            
        while 1:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if check_points(self.point_list, game_board): break
            else: continue
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR

    def is_hit (self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
if __name__ == "__main__":

    #Computer game board
    game_board = new_board()
    #User game board
    user_board = new_board()
    #Boat roster
    boat_list = []
    for boat_name, boat_length in ROSTER:
        boat_list.append(boat(game_board,boat_name,boat_length))

    # Setup for Main Loop
    user_moves = 0
    total_boats = len(boat_list)
    sunk_boats = 0
    continueGame = True
    print "\n" * WHITE_SPACE

    #Main loop
    while sunk_boats < total_boats and continueGame:    
        user_moves += 1
        #Paint the users board
        paint_grid(user_board)
        print "\nPress Ctrl-D to Quit Game\n"
        #Cheaters uncomment below
        #paint_grid(game_board)
        
        #Get coordinates from user
        while continueGame:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if len(input) > 3: continue
                input_x = char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except EOFError:
                continueGame = False
                continue
            except KeyboardInterrupt:
                continueGame = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    break        
        
        if not continueGame:
           continue
        print "\n" * WHITE_SPACE
        
        user_board[input_y][input_x] = MISS_CHAR

        user_point = (input_x, input_y)
        sunk_boats = 0
        for boat in boat_list:
            boat.is_hit(user_point)
            if boat.hit == True:
                user_board[input_y][input_x] = HIT_CHAR
            if boat.sunk == True:
                sunk_boats +=1
        if sunk_boats == total_boats:
            paint_grid(user_board)       
            print "You Win!!"
            print "Completed in %i moves." % user_moves
    


```

---

### Post by dannyboy79 on 2007-02-08
a few last comments and questions but it looks AWESOME. I love that you made it so that location entry is just a1 etc etc. Does the game add a number to your total if you accidentally typed in a65. It shouldn't as this isn't a valid number. Just curious as it happend to me when I was typing to fast and I hit enter before I was able to delete the 5.  Also, I like how you left what you hit when you hit it, For Example: Battleship Hit! stays at the top of the board after I hit enter BUT I think it would also be beneficial to the player if you also inform him what the spot was that he just chose. I know you're thinking well he just typed it in, how can he forget what he just entered. I am saying this because for example, I was playing and I got a hit when I did b5, then another hit when I did b6. I was looking a the board and saw 2 hits, 1 at b5 and 1 at b6, for some reason I would have just liked to see above the board that it said, Battleship Hit at b6. Which tells me that I last tried b6 spot, this way I don't forget and think my last spot was b5. I don't know, maybe I am getting to picky here but it's jsut a comment. Again, great job. I love it and it makes me want to learn how to program even more now!!! 

An idea for you to make it more complex (a challange I suppose you could say), make it have you enter your initials or whatever, and have it keep track of the last 3 best scores. Would that be hard to incoporate into your program???

---

### Post by RHTopics on 2007-02-08
chipmonk010,  I like your modification to my idea.  Using lists of tuples for boat rosters and making them appear as constants does indeed open up unlimited possibilities.

dannyboy79,  You are right, the total counter is at the top of the main loop and is incremented every time regardless whether it was a valid entry.  I guess chipmonk10, will have to decide whether that is a bug or a feature.:)

---

### Post by RHTopics on 2007-02-08
For your consideration,

Took the code and made it all into classes, creating a new class Game and moved the previous stand alone functions under the appropriate class.

With this change you can now import the code into another program or run it interactively from the python interpreter.

That is, if you copy and save the code listed below into a file.  Let say you name the file "battleship.py".  And then in a terminal session, you change directory to where you have saved the file, you should be able to do the following:  

note: (my file is saved in /home/rhtopics/tmp)

rhtopics@ubuntu:~/tmp$ python
>>> import battleship
>>> my_game = battleship.Game() 


You can also run it the way you have before.

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Computer game board
        self.game_board = self.new_board()
        #User game board
        self.user_board = self.new_board()
        #Boat roster
        self.boat_list = []
        for self.boat_name, self.boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                self.boat_name, self.boat_length))

        # Setup for Main Loop
        self.user_moves = 0
        self.total_boats = len(self.boat_list)
        self.sunk_boats = 0
        self.continue_game = True
        print "\n" * WHITE_SPACE

        #Main loop
        while self.sunk_boats < self.total_boats and self.continue_game:    
            self.user_moves += 1
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(self.game_board)
        
            #Get coordinates from user
            self.waiting_for_correct_input = True
            while self.continue_game and self.waiting_for_correct_input:
                try:
                    self.input = raw_input('Enter a letter/number combination:\n')
                    if len(self.input) > 3: continue
                    self.input_x = self.char_to_int(self.input[0])
                    self.input_y = int(self.input[1:3])
                except ValueError:
                    continue
                except (EOFError, KeyboardInterrupt):
                    self.continue_game = False
                    continue
                if self.input_x > 0 and self.input_x < BOARD_SIZE +1:
                    if self.input_y > 0 and self.input_y < BOARD_SIZE + 1:
                        self.waiting_for_correct_input = False        
        
            if not self.continue_game:
               continue
               
            print "\n" * WHITE_SPACE
        
            self.user_board[self.input_y][self.input_x] = MISS_CHAR

            self.user_point = (self.input_x, self.input_y)
            self.sunk_boats = 0
            for self.boat in self.boat_list:
                self.boat.is_hit(self.user_point)
                if self.boat.hit == True:
                    self.user_board[self.input_y][self.input_x] = HIT_CHAR
                if self.boat.sunk == True:
                    self.sunk_boats +=1
            if self.sunk_boats == self.total_boats:
                self.paint_grid(self.user_board)       
                print "You Win!!"
                print "Completed in %i moves." % self.user_moves

    # Build empty board
    def new_board(self):
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = ALPHA[i]
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1

    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""

class Boat:
    def __init__(self, game_board, name, length):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False
        
        self.boat_is_positioned = False
                                    
        while not self.boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = self.rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                self.boat_is_positioned = True
                
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False

        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True


    def is_hit(self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! \n" %  self.name
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
if __name__ == "__main__":

    my_game = Game()
    

```

---

### Post by chipmonk010 on 2007-02-08
Heres a little update:
using all-class setup for now(see below)
moved the loop that gets user input to a seperate function
moved the location at which the users moves are added
(solves the bug noticed by dannyboy in which typos are counted as moves)

@ RHTopic: I have adopted your all-classes version for the time being but im running into some problems. Check out the code below especially the FIXME line near the end of the boat class. Im trying to call a method of the curent game instance from within a boat instance. Is this even possible? Would I be better off reverting to my previous setup with the general functions being outside of a class? 

@ all: Just wanted to add another Thanks to everyone. This thread has really taught me the importance of testing and collaboration in a project. 

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Computer game board
        self.game_board = self.new_board()
        #User game board
        self.user_board = self.new_board()
        #Boat roster
        self.boat_list = []
        for self.boat_name, self.boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                self.boat_name, self.boat_length))
        # Setup for Main Loop
        self.user_moves = 0
        self.total_boats = len(self.boat_list)
        self.sunk_boats = 0
        self.continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while self.sunk_boats < self.total_boats and self.continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            self.paint_grid(self.game_board) 
            #Get coordinates from user
            
            self.input_x, self.input_y, self.continue_game = self.get_input()
            if not self.continue_game:
                continue

            self.user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[self.input_y][self.input_x] = MISS_CHAR
            self.user_point = (self.input_x, self.input_y)
            self.sunk_boats = 0
            for self.boat in self.boat_list:
                self.boat.is_hit(self.user_point)
                if self.boat.hit == True:
                    self.user_board[self.input_y][self.input_x] = HIT_CHAR
                if self.boat.sunk == True:
                    self.sunk_boats +=1
            if self.sunk_boats == self.total_boats:
                self.paint_grid(self.user_board)       
                print "You Win!!"
                print "Completed in %i moves." % self.user_moves

    # Builds an empty board
    def new_board(self):
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = self.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]

    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if len(input) > 3: continue
                input_x = self.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
        
class Boat:
    def __init__(self, game_board, name, length):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False
        
        self.boat_is_positioned = False
                                    
        while not self.boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = self.rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                self.boat_is_positioned = True
                
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False

        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True


    def is_hit(self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit \n" self.name
            #FIXME print "   %s Hit! (%s%i) \n" % (self.name, Game.int_to_char(self,point[1]),point[0]) 
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
if __name__ == "__main__":

    my_game = Game()


```

---

### Post by RHTopics on 2007-02-09
chipmonk010,

Got you fixed up.  Passed the instance of the Game class to the instance of the Boat class to get access to the functions in the Game class.  Also, fixed your logic for displaying the coordinates when a hit occurs.

Hang in there with classes, they are the way to go.:) 

Fixed code is below:

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Computer game board
        self.game_board = self.new_board()
        #User game board
        self.user_board = self.new_board()
        #Boat roster
        self.boat_list = []
        for self.boat_name, self.boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                self.boat_name, self.boat_length, self))
        # Setup for Main Loop
        self.user_moves = 0
        self.total_boats = len(self.boat_list)
        self.sunk_boats = 0
        self.continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while self.sunk_boats < self.total_boats and self.continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(self.game_board) 
            #Get coordinates from user
            
            self.input_x, self.input_y, self.continue_game = self.get_input()
            if not self.continue_game:
                continue

            self.user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[self.input_y][self.input_x] = MISS_CHAR
            self.user_point = (self.input_x, self.input_y)
            self.sunk_boats = 0
            for self.boat in self.boat_list:
                self.boat.is_hit(self.user_point)
                if self.boat.hit == True:
                    self.user_board[self.input_y][self.input_x] = HIT_CHAR
                if self.boat.sunk == True:
                    self.sunk_boats +=1
            if self.sunk_boats == self.total_boats:
                self.paint_grid(self.user_board)       
                print "You Win!!"
                print "Completed in %i moves." % self.user_moves

    # Builds an empty board
    def new_board(self):
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = self.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]

    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if len(input) > 3: continue
                input_x = self.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
        
class Boat:
    def __init__(self, game_board, name, length, caller):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False
        self.caller = caller
        
        self.boat_is_positioned = False
                                    
        while not self.boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = self.rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                self.boat_is_positioned = True
                
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False

        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True


    def is_hit(self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, self.caller.int_to_char(point[0]),point[1]) 
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
if __name__ == "__main__":

    my_game = Game()

```

---

### Post by dannyboy79 on 2007-02-09
> **RHTopics said:**
> 

That is, if you copy and save the code listed below into a file.  Let say you name the file "battleship.py".  And then in a terminal session, you change directory to where you have saved the file, you should be able to do the following:  

note: (my file is saved in /home/rhtopics/tmp)

rhtopics@ubuntu:~/tmp$ python
>>> import battleship
>>> my_game = battleship.Game() 


You can also run it the way you have before.



Could you maybe explain this? I used to run the program by simply typing in
python /usr/games/battleship.py
and that's it. I tried what you suggested but nothing happened, what is the purpose of doing the import etc etc. This is what happened when I tried it:

daniel@UBUNTU:~$ cd /usr/games
daniel@UBUNTU:/usr/games$ python
Python 2.4.3 (#2, Oct  6 2006, 07:52:30)
[GCC 4.0.3 (Ubuntu 4.0.3-1ubuntu5)] on linux2
Type "help", "copyright", "credits" or "license" for more information.
>>> import battleship
>>> my_game = battleship.Game()
Traceback (most recent call last):
  File "<stdin>", line 1, in ?
AttributeError: 'module' object has no attribute 'Game'
>>>

---

### Post by dannyboy79 on 2007-02-09
this is aimed at the developer. I tried mentioning before how important it is to leave the info pertaining to hits at the top and I can show you a great example. My suggestion is to leave the last 2 hits along with there coordinates and here is why.

I did f4 and got (i know it doesn't look like f4 but it is, this is from copying and pasting)
Carrier Hit!

   A  B  C  D  E  F  G  H  I  J
 1 .  .  .  .  .  .  .  .  .  .
 2 .  .  .  .  .  .  .  .  .  .
 3 .  .  .  .  .  .  .  .  .  .
 4 .  .  .  .  .  +  .  .  .  .
 5 .  .  .  .  .  .  .  .  .  .
 6 .  .  .  .  .  .  .  .  .  .
 7 +  .  .  .  .  .  .  .  .  .
 8 +  .  .  .  .  .  .  .  .  .
 9 .  .  .  .  .  .  .  .  .  .
10 .  .  .  .  .  .  .  .  .  .

then i did f3 and got
  Destroyer Hit!

   A  B  C  D  E  F  G  H  I  J
 1 .  .  .  .  .  .  .  .  .  .
 2 .  .  .  .  .  .  .  .  .  .
 3 .  .  .  .  .  +  .  .  .  .
 4 .  .  .  .  .  +  .  .  .  .
 5 .  .  .  .  .  .  .  .  .  .
 6 .  .  .  .  .  .  .  .  .  .
 7 +  .  .  .  .  .  .  .  .  .
 8 +  .  .  .  .  .  .  .  .  .
 9 .  .  .  .  .  .  .  .  .  .
10 .  .  .  .  .  .  .  .  .  .

and as you can see I am super pumped because I destroyed the partrol boat with only 2 shots and now I have hit what I think the same boat twice in a row. at this point I am thinking that I am going to make a record. but since I forgot the previous hit was the Carrier I figured I would get a hit no matter whether I used f2 or f5, well guess what. I missed both times!
   A  B  C  D  E  F  G  H  I  J
 1 .  .  .  .  .  .  .  .  .  .
 2 .  .  .  .  .  m  .  .  .  .
 3 .  .  .  .  .  +  .  .  .  .
 4 .  .  .  .  .  +  .  .  .  .
 5 .  .  .  .  .  m  .  .  .  .
 6 .  .  .  .  .  .  .  .  .  .
 7 +  .  .  .  .  .  .  .  .  .
 8 +  .  .  .  .  .  .  .  .  .
 9 .  .  .  .  .  .  .  .  .  .
10 .  .  .  .  .  .  .  .  .  .

and that's because I didn't know or pay attention that the first time I hit the Carrier and then the second time I hit the Destroyer. If I had seen that at the top of the board, I would have either tried g3 or e3 OR g4 or e4. See what I mean. It's your program, I am simply trying to point out what would help the player. No matter what, I love this little game. I ssh into my box from work, and can waste some time here and there. You should make a tic tac toe game. I think that's what I should try for my first program in python. Good job. ALso, you didn't comment about keeping track of top scores?

---

### Post by chipmonk010 on 2007-02-09
Thanks RHTopic:

I know some of my resistance was being confused by the restructuring and reordering. My temporary solution was to put just the main program flow into a class. so i would have a bunch of functions a boat class and a game class. But from what you say im thinking puting the functions within a class is better correct?

---

### Post by chipmonk010 on 2007-02-09
Latest code:
RHTopics class style with fix
added boat hit location display, example:

"Patrol Boat(A1) Hit!"

since this happens for every hit you can scroll up to see previous ones. you may want to reduce your WHITE_SPACE constant if your going to be scrolling back and forth

also fixed a bug:
if the user just hits enter when asked for a point the game would throw an error,
this is now fixed

@dannyboy
The point of being able to import the entire program is really code reuse and good coding practice. It not critical in this program but its good practice and make it easy for other programs to utilize this one. you can still run it just as you have been. took make things easier you can also do: chmod +x battleship.py and run with ./battleship.py

Also I didnt forget about the high scores idea. The conversion to an all class program has been slightly confusing for me. Thanks to RHTopic i think i have it nailed down for now so I can now focus on new features.

I was thinking of making a top10/5 and writing results to a file when i get some time ill mess with it.

heres the latest code(I definitely understand why people use CVS):

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Computer game board
        self.game_board = self.new_board()
        #User game board
        self.user_board = self.new_board()
        #Boat roster
        self.boat_list = []
        for self.boat_name, self.boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                self.boat_name, self.boat_length, self))
        # Setup for Main Loop
        self.user_moves = 0
        self.total_boats = len(self.boat_list)
        self.sunk_boats = 0
        self.continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while self.sunk_boats < self.total_boats and self.continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            self.paint_grid(self.game_board) 
            #Get coordinates from user
            
            self.input_x, self.input_y, self.continue_game = self.get_input()
            if not self.continue_game:
                continue

            self.user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[self.input_y][self.input_x] = MISS_CHAR
            self.user_point = (self.input_x, self.input_y)
            self.sunk_boats = 0
            for self.boat in self.boat_list:
                self.boat.is_hit(self.user_point)
                if self.boat.hit == True:
                    self.user_board[self.input_y][self.input_x] = HIT_CHAR
                if self.boat.sunk == True:
                    self.sunk_boats +=1
            if self.sunk_boats == self.total_boats:
                self.paint_grid(self.user_board)       
                print "You Win!!"
                print "Completed in %i moves." % self.user_moves

    # Builds an empty board
    def new_board(self):
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = self.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]

    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if not input or len(input) > 3: continue
                input_x = self.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
        
class Boat:
    def __init__(self, game_board, name, length, caller):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False
        self.caller = caller 
        self.boat_is_positioned = False
                                    
        while not self.boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = self.rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                self.boat_is_positioned = True
                
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False

        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True


    def is_hit(self, point):
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, self.caller.int_to_char(point[1]),point[0]) 
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
if __name__ == "__main__":

    my_game = Game()


```

---

### Post by RHTopics on 2007-02-09
chipmonk010,

I think by using classes, IMO, you are better able to see relationships in the code.  That is, what logic belongs where.

With your latest code:

  The cheaters board is being displayed.  For those following along, put a comment (#) on line 45, like so:
```

#self.paint_grid(self.game_board)

```
  
  Also the coordinates are backwards on line 178

This:
```

print "   %s Hit! (%s%i) \n" % (self.name, self.caller.int_to_char(point[1]),point[0])

```

should be this:

```

print "   %s Hit! (%s%i) \n" % (self.name, self.caller.int_to_char(point[0]),point[1])

```

---

### Post by dannyboy79 on 2007-02-09
RHtopics
thanks for the fix, I was thnking to myself, hey, why are the boats showing me where they are??? ha. 

developer
thank you so much for incorporating the feature I have pasted below as well as the number being shown along with the boat name.

 Carrier Hit! (H9)

   Carrier Sunk!

this is progressing fast. again, good job!

---

### Post by RHTopics on 2007-02-09
dannyboy79,

per fix, you are welcome.  That is great that you are enjoying the game.

When you got the AttributeError message when trying to use the battleship game within python's interpreter, that error probably means the python program you imported was an earlier version that did not contain the class "Game".

Was chipmonk010's explanation about why one would use "import" sufficient?

I can envision taking the battleship game and using it with a more sophisticated interface.  That could be a web page interface coming from a web server or having a "gui" interface using something like pyGTK.  With the main logic of the game being in a module that could be imported into the user interface portion, you could treat the main logic as a "black box" and not have to worry about accidentally changing it.

There are many ways that this program could be developed and doing it with python is fun!

---

### Post by chipmonk010 on 2007-02-09
oops....sry guys sloppy post on my part.
Just for clarity of the thread heres the whole code fixed:


```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Computer game board
        self.game_board = self.new_board()
        #User game board
        self.user_board = self.new_board()
        #Boat roster
        self.boat_list = []
        for self.boat_name, self.boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                self.boat_name, self.boat_length, self))
        # Setup for Main Loop
        self.user_moves = 0
        self.total_boats = len(self.boat_list)
        self.sunk_boats = 0
        self.continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while self.sunk_boats < self.total_boats and self.continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(self.game_board) 
            #Get coordinates from user 
            self.input_x, self.input_y, self.continue_game = self.get_input()
            if not self.continue_game:
                continue
            #Post point prompt tasks
            self.user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[self.input_y][self.input_x] = MISS_CHAR
            #Iterate through boat roster
            self.sunk_boats = 0
            for self.boat in self.boat_list:
                self.boat.is_hit(self.input_x,self.input_y)
                if self.boat.hit == True:
                    self.user_board[self.input_y][self.input_x] = HIT_CHAR
                if self.boat.sunk == True:
                    self.sunk_boats +=1
            if self.sunk_boats == self.total_boats:
                self.paint_grid(self.user_board)       
                print "You Win!!"
                print "Completed in %i moves." % self.user_moves

    # Builds an empty board
    def new_board(self):
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = self.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]

    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if not input or len(input) > 3: continue
                input_x = self.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
        
class Boat:
    def __init__(self, game_board, name, length, caller):
        self.name = name
        self.length = length
        self.hit_list = []
        self.sunk = False
        self.caller = caller 
        self.boat_is_positioned = False
                                    
        while not self.boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            self.start_point = self.rand_point(game_board)
            self.point_list = [self.start_point]
            # Make the boat
            for i in range(self.length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                self.boat_is_positioned = True
                
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False

        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True

    def is_hit(self,x,y):
        point = (x,y)
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, self.caller.int_to_char(point[0]),point[1]) 

            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 
       
if __name__ == "__main__":

    my_game = Game()


```

---

### Post by chipmonk010 on 2007-02-09
@ RHTopic et all
I have a couple questions about some variables and whether they really need to be in each instances namespace or can just reside in the class name space (self.var_name vs var_name)

```

#Boat roster
        self.boat_list = []
        for self.boat_name, self.boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                self.boat_name, self.boat_length, self))

```

Would it be better or worse to write the above like this:

```

#Boat roster
        self.boat_list = []
        for boat_name, boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                boat_name, boat_length, self))

```

I know that both work I really am just trying to figure out what it better practice. When I'm writing code like this my instinct is to use the latter example and only prepend variables that need to be different in each instance with self. boat_name and boat_length get changed everytime the loop iterates so each instance doesnt really need them AFAIK.

Is this good practice or a bad habit? or does it depend on the situation?

---

### Post by RHTopics on 2007-02-09
chipmonk010,

You have asked a good question.  One I have been pondering myself on when to prepend variables with "self." and when it is unnecessary.

I am going to research that question.  In the mean time maybe someone else with knowledge about it will respond.

---

### Post by RHTopics on 2007-02-09
chipmonk010,

After doing some reading on using classes in Python.  I believe your second example code of not using "self." is more appropriate.  Unless a variable needs to be available outside of class method(function), there is really no need for it to be prepended with "self."  

So, I probably went overboard  prepending variables with "self." in converting your code to classes .  

If the code works without the "self." prepends, I would think that is the best way to go.

---

### Post by RHTopics on 2007-02-10
chipmonk010,

For your consideration:

The code below has all but the required "self."s removed.  
It looks much cleaner.

Also, I moved the character to/from integer functions into their own class, 
thus removing the need for a callback from the Boat class to the Game class.

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Computer game board
        game_board = self.new_board()
        #User game board
        user_board = self.new_board()
        #Boat roster
        boat_list = []
        for boat_name, boat_length in ROSTER:
            boat_list.append(Boat(game_board, 
                boat_name, boat_length))
        # Setup for Main Loop
        user_moves = 0
        total_boats = len(boat_list)
        sunk_boats = 0
        continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while sunk_boats < total_boats and continue_game:     
            #Paint the users board
            self.paint_grid(user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(game_board) 
            #Get coordinates from user 
            input_x, input_y, continue_game = self.get_input()
            if not continue_game:
                continue
            #Post point prompt tasks
            user_moves += 1
            print "\n" * WHITE_SPACE
            user_board[input_y][input_x] = MISS_CHAR
            #Iterate through boat roster
            sunk_boats = 0
            for boat in boat_list:
                boat.is_hit(input_x,input_y)
                if boat.hit == True:
                    user_board[input_y][input_x] = HIT_CHAR
                if boat.sunk == True:
                    sunk_boats +=1
            if sunk_boats == total_boats:
                self.paint_grid(user_board)       
                print "You Win!!"
                print "Completed in %i moves." % user_moves

    # Builds an empty board
    def new_board(self):
        tools = Util()
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = tools.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        tools = Util()
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if not input or len(input) > 3: continue
                input_x = tools.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
        
class Boat:
    def __init__(self, game_board, name, length):
        self.name = name
        self.hit_list = []
        self.sunk = False
        boat_is_positioned = False
                                    
        while not boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            start_point = self.rand_point(game_board)
            self.point_list = [start_point]
            # Make the boat
            for i in range(length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                boat_is_positioned = True
                
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False

        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True

    def is_hit(self,x,y):
        tools = Util()
        point = (x,y)
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, tools.int_to_char(point[0]),point[1]) 

            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 

class Util:
    def __init__(self):
        pass

    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]
       
if __name__ == "__main__":

    my_game = Game()

```

---

### Post by chipmonk010 on 2007-02-11
@RHTopic:
My research confirmed a lack of need for the extra 'self' prefixes and my solution was identical to yours. I like your addition of the utils class i think it makes things a little neater.

I would be comfortable with calling the above post the current snapshot for the battleship program.  

Now off to do some more reading and so I can add new features!

---

### Post by chipmonk010 on 2007-02-12
Update:
Added high scores feature
keeps track of high scores and writes them to a file
user is prompted for name at game end and highsores are displayed
also added an algorithm to generate a numeric score from the number of moves
also had to add some 'self' prefixes back into the Game class

heres the code:

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Game Specific variables
        self.game_board = self.new_board()
        self.user_board = self.new_board()
        self.boat_list = []
        #Make boats in ROSTER
        for boat_name, boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                boat_name, boat_length))
        # Setup for Main Loop
        user_moves = 0
        total_boats = len(self.boat_list)
        sunk_boats = 0
        continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while sunk_boats < total_boats and continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(self.game_board) 
            #Get coordinates from user 
            input_x, input_y, continue_game = self.get_input()
            if not continue_game:
                continue
            #Post point prompt tasks
            user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[input_y][input_x] = MISS_CHAR
            #Iterate through boat roster
            sunk_boats = 0
            for boat in self.boat_list:
                boat.is_hit(input_x,input_y)
                if boat.hit == True:
                    self.user_board[input_y][input_x] = HIT_CHAR
                if boat.sunk == True:
                    sunk_boats +=1
            if sunk_boats == total_boats:
                self.paint_grid(self.user_board)       
                print "Game Over"
                final_score = self.format_score(user_moves)
                print "Final score: %i" % final_score
                self.high_scores(final_score)

    # Builds an empty board
    def new_board(self):
        tools = Util()
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = tools.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        tools = Util()
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if not input or len(input) > 3: continue
                input_x = tools.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
    
    def format_score(self, moves):
        pos_moves = 0
        for boat in self.boat_list:
            for point in boat.point_list:
                pos_moves += 1.00
        return (pos_moves / moves) * 1000
            

    def high_scores(self, score):
        NUM_SCORES_TO_KEEP = 5 
        new_highscore = False
        new_top_list = []
        file_exists = True
        try:
            top_scores = open('highscores', 'r')
            top_scores.close()
        except IOError:
            file_exists = False
        if file_exists:
            top_scores = open('highscores', 'r')
            score_inserted = False
            for line in top_scores:
                top_name, top_score = line.split('\t')
                top_score = float(top_score[:-1])
                if score > top_score and not score_inserted:
                    new_top_list.append(self.new_high_score(score))
                    score_inserted = True
                new_top_list.append(line)
        top_scores.close()
        if not file_exists:
            new_top_list.append(self.new_high_score(score))
            for x in range(NUM_SCORES_TO_KEEP-1):
                new_top_list.append('none\t0\n')
        #Write the new file
        top_scores = open('highscores', 'w')
        count = NUM_SCORES_TO_KEEP
        for line in new_top_list:
            top_scores.write(line)
            count -=1 
            if count == 0: break
        top_scores.close()
        self.show_highscores()
    
    def new_high_score(self, score):
        try:
            new_name = str(raw_input('New High Score!!\nPlease enter your name: \n'))
        except (EOFError, KeyboardInterrupt):
            new_name = none
            score = 0
        new_score = str(score)
        new_line = "%s\t%s\n" % (new_name, new_score)
        return new_line
    
    def show_highscores(self):
        scores_file = open('highscores', 'r')
        print '#'*30
        print '#'*9 + ' HIGH SCORES ' + '#'*8
        print '#'*30
        for line in scores_file:
            if line != "none\t0\n":
                print line
        
class Boat:
    def __init__(self, game_board, name, length):
        self.name = name
        self.hit_list = []
        self.sunk = False
        boat_is_positioned = False              
        while not boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            start_point = self.rand_point(game_board)
            self.point_list = [start_point]
            # Make the boat
            for i in range(length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                boat_is_positioned = True
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False
        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True

    def is_hit(self,x,y):
        tools = Util()
        point = (x,y)
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, tools.int_to_char(point[0]),point[1]) 
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 

class Util:
    def __init__(self):
        pass

    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]
       
if __name__ == "__main__":

    my_game = Game()


```

---

### Post by RHTopics on 2007-02-12
chipmonk010,

Good enhancement to the game.  Although to make it work the following code on line 140 will need to be moved 4 spaces to the right.

```

top_scores.close()

```

This only causes a problem for first time winners or if you are executing the program from a different directory than where the "highscores" file exists.

Some related thoughts about the new code.  Using some of the methods from the "os" module (i.e. import os), will streamline your code.

Using the "os.path" tools for checking file type and existence can replace your own logic (i.e os.path.exists("highscores") )

Also, if you consider this game will only be used in a linux environment, you could store the "highscores" file in a specific place like "/home/chipmonk010/.battleship/highscores".

You could use the os.environ['HOME'] to get the "/home/chipmonk010" part of the path.

Then use os.mkdir to create the new hidden directory ".battleship" 
example: os.mkdir('/home/chipmonk010/.battleship')

That way the 'highscores' file will be out of view and in a known location.

---

### Post by chipmonk010 on 2007-02-12
RHTopics,

Thanks for the correction. I will deffinately read up on the os module it sounds like a better solution. The code in this section feels a little sloppy and like it could be shorter. I think the os module is just the ticket. ill have to mess around with it and get back to ya.

Thanks for your continued effort to help with the progy and my programming skilzz 

heres the code with your fix:

```

#!/usr/bin/env python

import random

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

class Game:
    def __init__(self):
        #Game Specific variables
        self.game_board = self.new_board()
        self.user_board = self.new_board()
        self.boat_list = []
        #Make boats in ROSTER
        for boat_name, boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                boat_name, boat_length))
        # Setup for Main Loop
        user_moves = 0
        total_boats = len(self.boat_list)
        sunk_boats = 0
        continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while sunk_boats < total_boats and continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(self.game_board) 
            #Get coordinates from user 
            input_x, input_y, continue_game = self.get_input()
            if not continue_game:
                continue
            #Post point prompt tasks
            user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[input_y][input_x] = MISS_CHAR
            #Iterate through boat roster
            sunk_boats = 0
            for boat in self.boat_list:
                boat.is_hit(input_x,input_y)
                if boat.hit == True:
                    self.user_board[input_y][input_x] = HIT_CHAR
                if boat.sunk == True:
                    sunk_boats +=1
            if sunk_boats == total_boats:
                self.paint_grid(self.user_board)       
                print "Game Over"
                final_score = self.format_score(user_moves)
                print "Final score: %i" % final_score
                self.high_scores(final_score)

    # Builds an empty board
    def new_board(self):
        tools = Util()
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = tools.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        tools = Util()
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if not input or len(input) > 3: continue
                input_x = tools.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
    
    #Converts number of moves to numeric score
    def format_score(self, moves):
        pos_moves = 0
        for boat in self.boat_list:
            for point in boat.point_list:
                pos_moves += 1.00
        return (pos_moves / moves) * 1000
            
    #Main high score handler function
    def high_scores(self, score):
        NUM_SCORES_TO_KEEP = 5 
        new_highscore = False
        new_top_list = []
        file_exists = True
        try:
            top_scores = open('highscores', 'r')
            top_scores.close()
        except IOError:
            file_exists = False
        if file_exists:
            top_scores = open('highscores', 'r')
            score_inserted = False
            for line in top_scores:
                top_name, top_score = line.split('\t')
                top_score = float(top_score[:-1])
                if score > top_score and not score_inserted:
                    new_top_list.append(self.new_high_score(score))
                    score_inserted = True
                new_top_list.append(line)
            top_scores.close()
        if not file_exists:
            new_top_list.append(self.new_high_score(score))
            for x in range(NUM_SCORES_TO_KEEP-1):
                new_top_list.append('none\t0\n')
        #Write the new file
        top_scores = open('highscores', 'w')
        count = NUM_SCORES_TO_KEEP
        for line in new_top_list:
            top_scores.write(line)
            count -=1 
            if count == 0: break
        top_scores.close()
        self.show_highscores()
    
    #Prompts user for name to add to top scores
    def new_high_score(self, score):
        try:
            new_name = str(raw_input('New High Score!!\nPlease enter your name: \n'))
        except (EOFError, KeyboardInterrupt):
            new_name = none
            score = 0
        new_score = str(score)
        new_line = "%s\t%s\n" % (new_name, new_score)
        return new_line
    
    def show_highscores(self):
        scores_file = open('highscores', 'r')
        print '#'*30
        print '#'*9 + ' HIGH SCORES ' + '#'*8
        print '#'*30
        for line in scores_file:
            if line != "none\t0\n":
                print line
        
class Boat:
    def __init__(self, game_board, name, length):
        self.name = name
        self.hit_list = []
        self.sunk = False
        boat_is_positioned = False              
        while not boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            start_point = self.rand_point(game_board)
            self.point_list = [start_point]
            # Make the boat
            for i in range(length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                boat_is_positioned = True
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False
        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True

    def is_hit(self,x,y):
        tools = Util()
        point = (x,y)
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, tools.int_to_char(point[0]),point[1]) 
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 

class Util:
    def __init__(self):
        pass

    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]
       
if __name__ == "__main__":

    my_game = Game()


```

---

### Post by chipmonk010 on 2007-02-14
Update: new code using os module and RHTpoics' suggestions


```

#!/usr/bin/env python

import random
import os

#Configuration constants

#Valid sizes 5 to 26
BOARD_SIZE = 10     
BOARD_CHAR = '.'
BOAT_CHAR = 'b'
HIT_CHAR = '*'
MISS_CHAR = 'm'
WHITE_SPACE = 50
ALPHA = "ABCDEFGHIJKLMNOPQRSTUVWXYZ"
EASY = [('Patrol Boat',2), ('Destroyer',3),('Battleship',4),
        ('Carrier',5)] 
HARD = [('Patrol Boat',2),('Patrol Boat',2),('Patrol Boat',2),
        ('Scuba Guy',1)]
ROSTER = EASY

NUM_SCORES_TO_KEEP = 5 
BATTLESHIP_DIR = os.environ['HOME']+'/.battleship/'
SCORE_FILE = 'highscores'


class Game:
    def __init__(self):
        #Game Specific variables
        self.game_board = self.new_board()
        self.user_board = self.new_board()
        self.boat_list = []
        #Make boats in ROSTER
        for boat_name, boat_length in ROSTER:
            self.boat_list.append(Boat(self.game_board, 
                boat_name, boat_length))
        # Setup for Main Loop
        user_moves = 0
        total_boats = len(self.boat_list)
        sunk_boats = 0
        continue_game = True
        print "\n" * WHITE_SPACE
        
        #Main loop
        while sunk_boats < total_boats and continue_game:     
            #Paint the users board
            self.paint_grid(self.user_board)
            print "\nPress Ctrl-D to Quit Game\n"
            #Cheaters uncomment below
            #self.paint_grid(self.game_board) 
            #Get coordinates from user 
            input_x, input_y, continue_game = self.get_input()
            if not continue_game:
                continue
            #Post point prompt tasks
            user_moves += 1
            print "\n" * WHITE_SPACE
            self.user_board[input_y][input_x] = MISS_CHAR
            #Iterate through boat roster
            sunk_boats = 0
            for boat in self.boat_list:
                boat.is_hit(input_x,input_y)
                if boat.hit == True:
                    self.user_board[input_y][input_x] = HIT_CHAR
                if boat.sunk == True:
                    sunk_boats +=1
            if sunk_boats == total_boats:
                self.paint_grid(self.user_board)       
                print "Game Over"
                final_score = self.format_score(user_moves)
                print "Final score: %i" % final_score
                self.high_scores(final_score)

    # Builds an empty board
    def new_board(self):
        tools = Util()
        new_board = [[BOARD_CHAR for i in range(BOARD_SIZE+1)] \
                    for j in range(BOARD_SIZE+1)]
        new_board[0][0] = '  '
        for i in range(BOARD_SIZE):
            new_board[0][i+1] = tools.int_to_char(i+1)
            new_board[i+1][0] = i+1
            if i < 9:    
                new_board[i+1][0] = " " + str(new_board[i+1][0])
        return new_board
    
    # Prints the grid to the screen in human readable form
    def paint_grid(self, grid):
        for i in range(len(grid)):
            for j in grid[i]: 
                print str(j) + str(' ')* (1/len(str(j))),
            print ""
    
    # Gets input from user returns x,y,and whether user wants
    # to continue the game
    def get_input(self):
        tools = Util()
        input_x = 0
        input_y = 0
        continue_game = True
        waiting_for_correct_input = True
        while continue_game and waiting_for_correct_input:
            try:
                input = raw_input('Enter a letter/number combination:\n')
                if not input or len(input) > 3: continue
                input_x = tools.char_to_int(input[0])
                input_y = int(input[1:3])
            except ValueError:
                continue
            except (EOFError, KeyboardInterrupt):
                continue_game = False
                continue
            if input_x > 0 and input_x < BOARD_SIZE +1:
                if input_y > 0 and input_y < BOARD_SIZE + 1:
                    waiting_for_correct_input = False
        return (input_x,input_y,continue_game)
    
    #Converts number of moves to numeric score
    def format_score(self, moves):
        pos_moves = 0
        for boat in self.boat_list:
            for point in boat.point_list:
                pos_moves += 1.00
        return (pos_moves / moves) * 1000
            
    #Main high score handler function
    def high_scores(self, new_score):
        #Variables    
        new_top_list = []
        file_exists = True
        score_inserted = False
        #Check if needed files/dirs exist
        if not os.path.exists(BATTLESHIP_DIR):
            os.mkdir(BATTLESHIP_DIR)
        if not os.path.exists(BATTLESHIP_DIR + SCORE_FILE):
            file_exists = False
        os.chdir(BATTLESHIP_DIR)
        #Scan the curent highscores insert new if needed 
        if file_exists:
            top_scores = open(SCORE_FILE, 'r')
            for line in top_scores:
                top_name, top_score = line.split('\t')
                top_score = float(top_score[:-1])
                #Iterate through file see if new high score
                if new_score > top_score and not score_inserted:
                    new_top_list.append(self.new_high_score(new_score))
                    score_inserted = True
                new_top_list.append(line)
            top_scores.close()
        #Makes a new highscore list with the correct num of empty spots
        if not file_exists:
            new_top_list.append(self.new_high_score(new_score))
            score_inserted = True
            for x in range(NUM_SCORES_TO_KEEP-1):
                new_top_list.append('none\t0\n')
        #Writes new score list to file, if a new highscore was added
        if score_inserted:
            top_scores = open(SCORE_FILE, 'w')
            count = NUM_SCORES_TO_KEEP
            for line in new_top_list:
                top_scores.write(line)
                count -=1 
                if count == 0: break
            top_scores.close()
            self.show_highscores()
    
    #Prompts user for name to add to top scores
    def new_high_score(self, score):
        try:
            new_name = str(raw_input('New High Score!!\nPlease enter your name: \n'))
        except (EOFError, KeyboardInterrupt):
            new_name = none
            score = 0
        new_score = str(score)
        new_line = "%s\t%s\n" % (new_name, new_score)
        return new_line
    
    def show_highscores(self):
        scores_file = open(SCORE_FILE, 'r')
        print ''
        print '#'*30
        print '#'*9 + ' HIGH SCORES ' + '#'*8
        print '#'*30
        for line in scores_file:
            if line != "none\t0\n":
                print line
        scores_file.close()

class Boat:
    def __init__(self, game_board, name, length):
        self.name = name
        self.hit_list = []
        self.sunk = False
        boat_is_positioned = False              
        while not boat_is_positioned:
            #Randomly decide axis on which to draw boat
            dx = random.randint(0,1)
            dy = 1 - dx    
            #Randomly decide direction on given axis
            if random.randint == 1:
                dx = -1 * dx
                dy = -1 * dy
            #Get a random starting point for a new boat
            start_point = self.rand_point(game_board)
            self.point_list = [start_point]
            # Make the boat
            for i in range(length - 1):
                last_point = self.point_list[-1]
                x = last_point[0]+dx
                y = last_point[1]+dy
                self.point_list.append((x,y))
            if self.check_points(self.point_list, game_board):
                boat_is_positioned = True
        for point in self.point_list:
            game_board[point[1]][point[0]] = BOAT_CHAR
            
    # Takes a 2D game board of any size randomly selects a spot
    def rand_point(self, game_board):
        position_occupied = True
        while position_occupied:
            x = random.randint(0,BOARD_SIZE-1)
            y = random.randint(0,BOARD_SIZE-1)
            if game_board[y][x] == BOARD_CHAR:
                position_occupied = False
        return (x, y)
                                
    # Used when drawing boats, prevents boats from overlaping
    def check_points(self, point_list, game_board):
        for point in point_list:
            x = point[0] 
            y = point[1]
            if x < 0 or x > BOARD_SIZE - 1:
                return False
            if y < 0 or y > BOARD_SIZE - 1:
                return False
            if game_board[y][x] != BOARD_CHAR:
                return False
        return True

    def is_hit(self,x,y):
        tools = Util()
        point = (x,y)
        self.hit = False
        if point in self.point_list:
            print "   %s Hit! (%s%i) \n" % (self.name, tools.int_to_char(point[0]),point[1]) 
            self.hit = True
            if point not in self.hit_list:
                self.hit_list.append(point)
            if len(self.point_list) == len(self.hit_list):
                print "   %s Sunk! \n" % self.name
                self.sunk = True 

class Util:
    def __init__(self):
        pass

    # Converts chars to ints (A == 1)
    def char_to_int(self, char):
        return ALPHA.find(char.upper() ) + 1
    
    # Converts ints to chars (1 == A)
    def int_to_char(self, int):
        return ALPHA[int-1]
       
if __name__ == "__main__":

    my_game = Game()


```

---

