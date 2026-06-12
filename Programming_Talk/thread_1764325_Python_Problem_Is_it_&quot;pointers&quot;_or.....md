---
title: "Python Problem: Is it &quot;pointers&quot; or....?"
date: 2011-05-21
forum: Programming Talk
---

### Post by skytreader on 2011-05-21
Hi all. I'm trying to create an n-puzzle solver in Python. I've coded my A* but it doesn't work as I expected.

```

	def solve(self):
		depth = 1
		current_state = deepcopy(self)
		path = []
		
		while not current_state.is_solved():
			print(current_state.__str__())
			path.append(current_state)
			
			move_left = deepcopy(current_state)
			move_right = deepcopy(current_state)
			move_up = deepcopy(current_state)
			move_down = deepcopy(current_state)
			
			move_left.__move(MOVEMENTS["LEFT"])
			move_right.__move(MOVEMENTS["RIGHT"])
			move_up.__move(MOVEMENTS["UP"])
			move_down.__move(MOVEMENTS["DOWN"])
			
			next_states = [i for i in range(len(MOVEMENTS))]
			next_states[MOVEMENTS["LEFT"]] = move_left
			next_states[MOVEMENTS["RIGHT"]] = move_right
			next_states[MOVEMENTS["UP"]] = move_up
			next_states[MOVEMENTS["DOWN"]] = move_down
			mindex = Npuzzle.__get_min(current_state, next_states, depth, path)
			
			current_state.__move(mindex)
			print("Has it been there? " + str(next_states[mindex] in self.path)) # FUNNY LINE 1
			print("Have we been there? " + str(current_state in path) + str(mindex)) # FUNNY LINE 2
			print("Are they in the same state? " + str(Npuzzle.__is_same_state(current_state, next_states[mindex]))) # FUNNY LINE 3
			
			depth += 1
		
		logdog.close()
		return path
	
	def __get_min(self, current_state, next_states, depth, path):
		i = 0
		limit = len(next_states)
		costs = list(map(lambda puzzle_state: puzzle_state.__manhattan_distance() + depth, next_states))
		#Will hold (current minimum, index of current_minimum)
		minimum = (max(costs) + 1, max(costs) + 1)
		
		while i < limit:
			this_cost = next_states[i].__manhattan_distance() + depth
			if this_cost < minimum[0] and \
			   not Npuzzle.__is_in_path(next_states[i], path): # FUNNY LINE 4
				minimum = (this_cost, i)
			
			i += 1
		
		return minimum[1]
	
	def __is_in_path(puzzle, path):
		i = 0
		limit = len(self.path)
		
		while i < limit:
			if not Npuzzle.__is_same_state(puzzle, self.path[i]):
				return False
			
			i += 1
		
		return True
	
	def __is_same_state(p1, p2):
		i = 0
		limit = len(p1.puzzle)
		
		while i < limit:
			if p1.puzzle[i] != p2.puzzle[i]:
				return False
			
			i += 1
		
		return True

```

What is of interest to me are those lines I marked as funny. From FL4, the next state which will be returned is a state I never encountered yet. However, FL0 prints False, then FL1 (checking if current_state returned to a state already encountered) prints True and yet so does FL2. I'm confused >.<

Something funnier...

Code above behaves like this: Puzzle solves normally till it moves, say, cell at (row, col) upwards so it becomes (row - 1, col). Next step, (row - 1, col) will be moved to (row, col) into an endless loop, tile traveling back and forth.

Change FL4 to

```
next_states[i] not in path
```

and, when it reaches move up on (row, col) I don't see it move at all (i.e., puzzle state doesn't change in my print log).

I understand why my program behave as such---that's why I'm checking if the state has already been encountered. However, I don't understand how "not Npuzzle.__is_in_path(next_states[i], path)" is any different from "next_states[i] not in path". Is there anything I'm missing?

Thanks a lot!!!

---

### Post by simeon87 on 2011-05-22
> **skytreader said:**
> Hi all. I'm trying to create an n-puzzle solver in Python. I've coded my A* but it doesn't work as I expected.

```

	def solve(self):
		depth = 1
		current_state = deepcopy(self)
		path = []
		
		while not current_state.is_solved():
			print(current_state.__str__())
			path.append(current_state)
			
			move_left = deepcopy(current_state)
			move_right = deepcopy(current_state)
			move_up = deepcopy(current_state)
			move_down = deepcopy(current_state)
			
			move_left.__move(MOVEMENTS["LEFT"])
			move_right.__move(MOVEMENTS["RIGHT"])
			move_up.__move(MOVEMENTS["UP"])
			move_down.__move(MOVEMENTS["DOWN"])
			
			next_states = [i for i in range(len(MOVEMENTS))]
			next_states[MOVEMENTS["LEFT"]] = move_left
			next_states[MOVEMENTS["RIGHT"]] = move_right
			next_states[MOVEMENTS["UP"]] = move_up
			next_states[MOVEMENTS["DOWN"]] = move_down
			mindex = Npuzzle.__get_min(current_state, next_states, depth, path)
			
			current_state.__move(mindex)
			print("Has it been there? " + str(next_states[mindex] in self.path)) # FUNNY LINE 1
			print("Have we been there? " + str(current_state in path) + str(mindex)) # FUNNY LINE 2
			print("Are they in the same state? " + str(Npuzzle.__is_same_state(current_state, next_states[mindex]))) # FUNNY LINE 3
			
			depth += 1
		
		logdog.close()
		return path
	
	def __get_min(self, current_state, next_states, depth, path):
		i = 0
		limit = len(next_states)
		costs = list(map(lambda puzzle_state: puzzle_state.__manhattan_distance() + depth, next_states))
		#Will hold (current minimum, index of current_minimum)
		minimum = (max(costs) + 1, max(costs) + 1)
		
		while i < limit:
			this_cost = next_states[i].__manhattan_distance() + depth
			if this_cost < minimum[0] and \
			   not Npuzzle.__is_in_path(next_states[i], path): # FUNNY LINE 4
				minimum = (this_cost, i)
			
			i += 1
		
		return minimum[1]
	
	def __is_in_path(puzzle, path):
		i = 0
		limit = len(self.path)
		
		while i < limit:
			if not Npuzzle.__is_same_state(puzzle, self.path[i]):
				return False
			
			i += 1
		
		return True
	
	def __is_same_state(p1, p2):
		i = 0
		limit = len(p1.puzzle)
		
		while i < limit:
			if p1.puzzle[i] != p2.puzzle[i]:
				return False
			
			i += 1
		
		return True

```

What is of interest to me are those lines I marked as funny. From FL4, the next state which will be returned is a state I never encountered yet. However, FL0 prints False, then FL1 (checking if current_state returned to a state already encountered) prints True and yet so does FL2. I'm confused >.<

Something funnier...

Code above behaves like this: Puzzle solves normally till it moves, say, cell at (row, col) upwards so it becomes (row - 1, col). Next step, (row - 1, col) will be moved to (row, col) into an endless loop, tile traveling back and forth.

Change FL4 to

```
next_states[i] not in path
```

and, when it reaches move up on (row, col) I don't see it move at all (i.e., puzzle state doesn't change in my print log).

I haven't checked in detail but it's indeed possible to see things you haven't seen before. A variable name in Python refers to an object which means you can alter any object that refers to that variable as well. For example, you can do:

```
>>> p = [1,2,3]
>>> q = p
>>> q[0] = 5
>>> p
[5, 2, 3]

```

In this situation it may seem obvious but it can also occur in more complex situations when you're not carefully making a new list.

> **skytreader said:**
> I understand why my program behave as such---that's why I'm checking if the state has already been encountered. However, I don't understand how "not Npuzzle.__is_in_path(next_states[i], path)" is any different from "next_states[i] not in path". Is there anything I'm missing?

Thanks a lot!!!

From what I can see it has to do with equality between the objects. The function Npuzzle.__is_in_path calls Npuzzle.__is_same_state which explicitly compares p1.puzzle[i] with p2.puzzle[i]. But could p1 and p2 also have other attributes on which they can be equal or not equal? If you use ```
next_states[i] not in path
``` then it uses the equality function of a next_states[i] object, which may give different results. If you want to change the behaviour then you have to define ```
def __eq__(self, other)
``` for that object. For example, you can do:

```
>>> class A:
...     def __init__(self):
...             self.a = 3
...             self.b = 5
... 
>>> A() == A()
False
```

but also: ```
>>> class A:
...     def __init__(self):
...             self.a = 3
...             self.b = 3
...     def __eq__(self, other):
...             return self.a == other.a
... 
>>> 
>>> A() == A()
True
```

---

