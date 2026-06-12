---
title: "[Python] Problem with pushing two objects at a time to heapq"
date: 2011-05-27
forum: Programming Talk
---

### Post by skytreader on 2011-05-27
The way I understand it, when you push a tuple to a list using heapq.heappush, Python assumes that the element (number) at index 0 is the priority of the item. The elements at index 1 to till-Python-can-take-it, are irrelevant.

If that is so, I can't understand what Python3 is complaining about in here,

Code:
```

while i < limit:
				cost = neighbor_nodes[i].__manhattan_distance() + depth
				candidate_tuple = (cost, neighbor_nodes[i], current_node[PUZZLE_INDEX])
				
				if candidate_tuple in traversed:
					pass
				else:
					print("heapq.heappush(", choice_space, ",", candidate_tuple, ")")
					print(type(choice_space))
					print(type(candidate_tuple))
					heapq.heappush(choice_space, candidate_tuple) #Mark this line!
					print("Valid push!")
				
				i += 1

```

(Of course, that's just a snippet. Will post more is needed.)

Sorry for the spacing. Assume it works.

For which it can produce a trace like

```

heapq.heappush( [] , (28, <npuzzle_oo.Npuzzle object at 0xb761b48c>, <npuzzle_oo.Npuzzle object at 0xb762546c>) )
<class 'list'>
<class 'tuple'>
Valid push!
heapq.heappush( [(28, <npuzzle_oo.Npuzzle object at 0xb761b48c>, <npuzzle_oo.Npuzzle object at 0xb762546c>)] , (26, <npuzzle_oo.Npuzzle object at 0xb75d91cc>, <npuzzle_oo.Npuzzle object at 0xb762546c>) )
<class 'list'>
<class 'tuple'>
Valid push!
heapq.heappush( [(26, <npuzzle_oo.Npuzzle object at 0xb75d91cc>, <npuzzle_oo.Npuzzle object at 0xb762546c>), (28, <npuzzle_oo.Npuzzle object at 0xb761b48c>, <npuzzle_oo.Npuzzle object at 0xb762546c>)] , (27, <npuzzle_oo.Npuzzle object at 0xb761b4ac>, <npuzzle_oo.Npuzzle object at 0xb762546c>) )
<class 'list'>
<class 'tuple'>
Valid push!
heapq.heappush( [(26, <npuzzle_oo.Npuzzle object at 0xb75d91cc>, <npuzzle_oo.Npuzzle object at 0xb762546c>), (28, <npuzzle_oo.Npuzzle object at 0xb761b48c>, <npuzzle_oo.Npuzzle object at 0xb762546c>), (27, <npuzzle_oo.Npuzzle object at 0xb761b4ac>, <npuzzle_oo.Npuzzle object at 0xb762546c>)] , (28, <npuzzle_oo.Npuzzle object at 0xb761b46c>, <npuzzle_oo.Npuzzle object at 0xb762546c>) )
<class 'list'>
<class 'tuple'>

```

And then an error message,
```

File "filepath/filename.py", line 416, in solve
    heapq.heappush(choice_space, candidate_tuple)
TypeError: unorderable types: Npuzzle() < Npuzzle()

```

(Line 416 is the line commented with "Mark this line!")

Anything I'm missing? Why was it successful in pushing the first few times then suddenly throws an error?

Thanks!

---

### Post by skytreader on 2011-05-28
Found an answer to my own question. It seems that, when keys are equal, Python resorts to comparing the values by call to __lt__.

[http://stackoverflow.com/questions/3954530/how-to-make-heapq-evaluate-the-heap-off-of-a-specific-attribute](http://stackoverflow.com/questions/3954530/how-to-make-heapq-evaluate-the-heap-off-of-a-specific-attribute)

---

