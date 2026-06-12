---
title: "I need some help with a FrozenBubble clone in Java"
date: 2008-06-01
forum: Programming Talk
---

### Post by Yes on 2008-06-01
I've got to make a [FrozenBubble](http://glenn.sanson.free.fr/v2/?select=fb:play) clone in Java for my computer science class.  I'm having trouble figuring out how to put the bubbles into some sort of data structure so that I can a) check if the bubble being shot up needs to stop because it hit another bubble, b) whether or not the new bubble has completed a set of three or more bubbles of the same color, at which point c) the bubbles in that set needs to fall down (be removed from the data structure), as well as any bubbles that are now no longer connected to either the top of the game screen or any other bubbles.  I've been reading around and it seems like a graph is what I need, but I'm not sure how I would implement it.  Can anyone give me some pointers?

Thanks!

---

### Post by mike_g on 2008-06-01
You could check for collisions with other bubbles using pythagoras to get the distance. IE: distance = square_root((dx*dx)+(dy*dy)). Then snap it to its closest grid cell - hexagonal cells should work well here. So each bubble could have 6 references to neighbors attached, which would be null if theres no neighbor on that side.  Whenever a bubble sticks check its neighbors, and its neighbors neighbors and you would be able to find if theres 3 in a row or not. I havent done this myself, but I think thats how I would go about it.

---

### Post by Can+~ on 2008-06-01
Bubble Node (ASCII art):

```
   1\   2/
-3-{Color}-4-
   5/   6\
```

So each node remembers the one next to each other in 6 directions (taking note from what mike_g) said.

When a new one is sticked to an old one, check if there are 3 connected in chain. Meaning, that if you find a single node with two childs of the same color than him (making them 3) the chain reaction can start recursively.

Nodes without any superior attachment (1, 2, 3 and 4) will fall down.

I'm not sure if this is the "ideal" way to do it, but that's how I imagine it, maybe with less pointers to child objects.

---

### Post by Yes on 2008-06-02
Ok, thanks for the replies.

First, it's got to be an 8-sided nodes - I've played around with it and you can get two bubbles on the left and right sides.  But that shouldn't change anything, right?  I'd just have to check more children for the same color and for superior attachments.

Next, I forgot to mention, but the bubbles can bounce off the walls.  How would I check for collisions, then?  If you still think I could use the Pythagorean theorem, how that work?  Would I use figure out where the bubble is going, and then check all those coordinates for bubbles?

Thanks!

---

### Post by Can+~ on 2008-06-02
The bouncing on Frozen bubble is dead simple:

```
////|
////|   /
////|  / V2
////| /
WALL|/)______
////|\
////| \ V1
////|  \ movement
////|   \

|y
|___x

```

If the direction of movement is represented by the vector V1(-x, y), then, the second after hitting the wall, it will be represented by V2(x, y).

Since walls are just there, you can test for position, if the x distance of the bubble to the wall is less or equal than the radius of said bubble, then it bounces.

```
| Bubble
| /   \
|(--r  )
| \___/
```

---

### Post by mike_g on 2008-06-02
If the walls are vertical lines you could simply check the x positions of the bubble against the wall. If it touches or overlaps then invert the angle.

---

### Post by Yes on 2008-06-02
Well I got the bouncing working fine, I was just asking for some clarification as to how I should use Pythagoras theorem to test for collisions.  Sorry for not making that clearer.

---

### Post by mike_g on 2008-06-02
Going from the center point of each bubble get the difference in distance horizontally and vertically:
```
int dx = BubbleA.x - BubbleB.x;
int dy = BubbleA.y - BubbleB.y;
```
The distance between the two points is the square root of dx squared + dy squared. If the distance between center points is less than or equal to the diameter of a bubble then a collision has occurred.

---

### Post by Yes on 2008-06-03
Ok, where is the X and Y coordinates for images drawn with the drawImage method in java.awt.Graphics?  It's the upper left corner, right?

Your method would require me to know what bubble the traveling bubble is going to hit, right?  How would I figure that out?

e: Also, could someone check out the method I use to check for groups of three or more bubbles of the same color?  Right now, it prints 1 when there's one bubble up, and then 1,2,3 when I add another, and then 1,2,3 for every other bubble I add.

```
public void checkColors (BubbleNode node) {

    	if (node.topLeft != null && node.topLeft.imageX == node.imageX) {

    		fallingList.add (node.topLeft);

    		if (node.topLeft != null)    	

    			checkColors (node.topLeft);

    	}

    	if (node.topRight != null && node.topRight.imageX == node.imageX) {

    		fallingList.add (node.topRight);

    		if (node.topRight != null)    	

    			checkColors (node.topRight);

    	}

    	if (node.bottomRight != null && node.bottomRight.imageX == node.imageX) {

    		fallingList.add (node.bottomRight);

    		if (node.bottomRight != null)    	

    			checkColors (node.bottomRight);

    	}

    	if (node.bottomLeft != null && node.bottomLeft.imageX == node.imageX) {

    		fallingList.add (node.bottomLeft);

    		if (node.bottomLeft != null)   	

    			checkColors (node.bottomLeft);

    	}

    	if (node.rightBottom != null && node.rightBottom.imageX == node.imageX) {

    		fallingList.add (node.rightBottom);

    		if (node.rightBottom != null)    	

    			checkColors (node.rightBottom);

    	}

    	if (node.leftBottom != null && node.leftBottom.imageX == node.imageX) {

    		fallingList.add (node.leftBottom);

    		if (node.leftBottom != null)    	

    			checkColors (node.leftBottom);

    	}

    	if (node.rightTop != null && node.rightTop.imageX == node.imageX) {

    		fallingList.add (node.rightTop);

    		if (node.rightTop != null)    	

    			checkColors (node.rightTop);

    	}

    	if (node.leftTop != null && node.leftTop.imageX == node.imageX) {

    		fallingList.add (node.leftTop);

    		if (node.leftTop != null)    	

    			checkColors (node.leftTop);

    	}

    	fallingList.add (node);

    	System.out.println (fallingList.size ());

    	if (fallingList.size () > 2)

    		deleteNodes ();

    }
```

Thanks

---

### Post by mike_g on 2008-06-04
> Ok, where is the X and Y coordinates for images drawn with the drawImage method in java.awt.Graphics? It's the upper left corner, right?
Why don't you try it and see?

> Your method would require me to know what bubble the traveling bubble is going to hit, right? How would I figure that out?
Not necessarily. Probably the easiest way to do this would be to simply check the moving bubble against each other bubble.

---

### Post by Yes on 2008-06-04
Ok, I got the collisions working now, but I'm having trouble adding nodes to the whole thing.  Right now, when a collision takes place, it creates a new BubbleNode, and adds it to an ArrayList so that I can easily travers the list and get the centers of all the bubbles, and check if a collision occured.  But when I try adding a second node to the list, the program freezes without an exception.  How would you suggest I do this?  Should I not be using ArrayLists?

Thanks for all the help :)

---

### Post by RIchard James13 on 2008-06-05
Some thoughts:

Even though the bubbles are in a hex like position at the top of the screen there is no need to store them like that. You can just store them as rows of blocks. Every 2nd row is slightly offset so that it has 1 less bubble in it.

```
On Screen

 B B B B B B B B
  B B B B B B B
 B B B B B B B B
  B B B B B B B
In an array

BBBBBBBB
BBBBBBB
BBBBBBBB
BBBBBBB
```

In this way you need to calculate the offsets only for every second row. Also you need a more complicated algorithm to work out what falls. But at least you won't be confused as to what bubbles are where. Also as the bubbles come up the screen they just snap into that array. Say the player shoots a bubble and now you get
```
01234567
BBBBBBBB
BBBBBBB
BBBBBBBB
BBBBBBB
   B
```

Although the offset for that bubble appears to be 3 it is joined to both 2 and 3 above it. So on screen it would appear as.

```


 B B B B B B B B
  B B B B B B B
 0 1 2 3 4 5 6 7
  0 1 2 3 4 5 6
       3       

```

---

### Post by Yes on 2008-06-05
Thanks, but it's kind of too late to redo everything like that.  Right now, I'm having some trouble with the checkColors method.  What exactly should the algorithm look like.  What I have now is it checks the nodes all around it, and if they're the same color, it calls the ckeckColors method again, this time passing in whatever node next to it was the same color.  But of course this is infinite recursion, because it ends up checking left, then if that's the same color it checks right, and so on.

Can anyone help?  I don't want to sound desperate, but this is a fairly big grade and it's already late...

---

### Post by mike_g on 2008-06-05
Personally I dont think that using a grid would be necessary anyway. As for checking colours you could send in the address of the parent node as well, then when you iterate over neighbors only call the function for ones that don't match the parent class reference (on the first function call this can be null). I take it you also added a counter variable to break the recursion too?

---

### Post by Yes on 2008-06-05
It stops calling iteslf when there are no more new nodes around it that are the same color.  I tried passing in the previous node, is that what you meant by address?

Right now, it's just calling the method twice and then stopping, so I think I'm missing something.  Here's what I have right now:

[php]    public void checkColors (BubbleNode node, BubbleNode prevNode) {

    	if (node.left != null && node.left.imageX == node.imageX && node.left != prevNode) {

    		checkColors (node.left, node);

    		fallingList.add (node);

		}

    	if (node.right != null && node.right.imageX == node.imageX && node.right != prevNode) {

    		checkColors (node.right, node);

    		fallingList.add (node);

		}

    	if (node.topLeft != null && node.topLeft.imageX == node.imageX && node.topLeft != prevNode) {

    		checkColors (node.topLeft, node);

    		fallingList.add (node);

		}

    	if (node.topRight != null && node.topRight.imageX == node.imageX && node.topRight != prevNode) {

    		checkColors (node.topRight, node);

    		fallingList.add (node);

		}

    	if (node.bottomLeft != null && node.bottomLeft.imageX == node.imageX && node.bottomLeft != prevNode) {

    		checkColors (node.bottomLeft, node);

    		fallingList.add (node);

		}

    	if (node.bottomRight != null && node.bottomRight.imageX == node.imageX && node.bottomRight != prevNode) {

    		checkColors (node.bottomRight, node);

    		fallingList.add (node);

		}

    		

    	if (fallingList.size () > 2) {

    		deleteNodes ();

    	}

    }[/php]

---

### Post by mike_g on 2008-06-05
Yeah, thats what I meant by the address. I dont think you want to be adding nodes to the falling list until you know you have a row tho. Also, I cant see a counter in your code to break the recursion after moving across 2 bubbles. This is roughly what I was thinking about when checking for 3 in a row:
```
int checkColors(Bubble parent, Bubble child, int time_to_live)
{
	time_to_live--;	
	if(parent.col != child.col) return 0;	// wrong color
	if(time_to_live == 0) return 1; 	// row found 
	for(int i=0; i<6; i++)
		if(child.neighbor[i] != null && child.neighbor[i] != parent)
			if(checkColors(child, child.neighbor[i], time_to_live)==1)
				searchForFallingNodes(); 	
}
```
There may be a few glitches with it as i wrote it off the top of my head, but anyway hopefully it should give you an idea.

---

### Post by Yes on 2008-06-05
Well the falling list is cleared everytime a new node is added to the whole thing, and I only delete anything if there's three or more nodes in the list.  

What would searchForFallingNodes do?  Just delete them?

e: And the first time I call checkColors, I should pass in 3, right?  Also, it needs to be able to delete more than three nodes at a time.  Would that change anything?

Lemme see if I understand what that code does -

First, it decrements the counter, and checks if the child and parent nodes are the same color.  If they're not, it returns 0, which would stop from looking further in that direction.  Then it checks to see if the counter is 0, which would mean that there has been 3 nodes if the same color in a row.  It returns 1, which deletes the nodes (I'm assuming that's what searchForFallingNodes does).  If the colors are the same but there hasn't been 3 in a row yet, it iterates through all the neighbors of the child.  If a neighbor isn't the parent and isn't null, it calls checkColors again, this time with the child as the parent and the neighbor as the child.  If that equals 1, it means that it found a row of 3 and it deletes the nodes.

Is that close?

---

### Post by mike_g on 2008-06-05
That was just a stub function. It would search start seraching nodes below / next to it and add them to the falling list. 

Basically starting a new recursive search that ends when you reach: a falling node, an empty cell, or a node that is attached to a non falling bubble above it. 

Before adding these nodes to the list you will want to make sure, that they are not still attached to a non falling bubble above. So, it would require another recursive search. Once you have reached the limit of the search, on the way back, flag the nodes as falling if they are not connected to stuck nodes above. 

Sorry if this sounds confusing. A good analogy for the way this works is if you imagine climbing a tree, checking all the branches, then climbing back down doing stuff as you go back.

You would also want to add each bubble to the falling list once a match as been found. I also realised that you would want to search for falling nodes immediately when a row has been found so I added that to the pseudocode.

```
int checkColors(Bubble parent, Bubble child, int time_to_live)
{
	time_to_live--;	
	if(parent.col != child.col) return 0;	// wrong color
	if(time_to_live == 0) 
	{
		addToFallingList(child);
		searchForFallingNodes();
		return 1; 	// row found 
	}
	for(int i=0; i<6; i++)
	{
		if(child.neighbor[i] != null && child.neighbor[i] != parent)
		{
			if(checkColors(child, child.neighbor[i], time_to_live)==1)
			{
				addToFallingList(child);
				searchForFallingNodes(); 
			}
		}
	}	
}
```

Edit: 
> Is that close?
Yep.

---

### Post by Yes on 2008-06-05
Ugh, I don't think I understand this.  So searchForFallingNodes would check for nodes no longer attached and remove them?

Here's my latest attempt.  The neighbor nodes aren't in an array so I couldn't use a for loop, and the deleteNodes method takes care of nodes that aren't attached anymore.  

```
public int checkColors (BubbleNode node, BubbleNode prevNode, int counter) {
    	counter--;
    	if (node != null && prevNode != null && node.imageX != prevNode.imageX)
    		return 0;
    	if (counter == 0) {
    		fallingList.add (node);
    		return 1;
		}   		

    	if (node.left != null && node.left != prevNode) {
    		if (checkColors (node.left, node, counter) == 1)
    			fallingList.add (node);
		}
    	if (node.right != null && node.right != prevNode) {
    		if (checkColors (node.right, node, counter) == 1)
    			fallingList.add (node);
		}
    	if (node.topLeft != null && node.topLeft != prevNode) {
    		if (checkColors (node.topLeft, node, counter) == 1)
    			fallingList.add (node);
		}
    	if (node.topRight != null && node.topRight != prevNode) {
    		if (checkColors (node.topRight, node, counter) == 1) 
    			fallingList.add (node);
		}
    	if (node.bottomLeft != null && node.bottomLeft != prevNode) {
    		if (checkColors (node.bottomLeft, node, counter) == 1)
    			fallingList.add (node);
		}
    	if (node.bottomRight != null && node.bottomRight != prevNode) {
    		if (checkColors (node.bottomRight, node, counter) == 1)
    			fallingList.add (node);
		}

    	if (fallingList.size () > 2) {
    		deleteNodes ();
    	}
    	return 0;
    }
```

---

### Post by mike_g on 2008-06-05
Well, you have part of it. The only thing with the code you have at the moment is that it would only remove the nodes of matching colours; not the ones attached below it.

There is one important thing I forgot to add. Thats that the nodes need to pass the return value back to all calling functions. EG:
```
public int checkColors (BubbleNode node, BubbleNode prevNode, int counter) {
    	counter--;
    	if (node != null && prevNode != null && node.imageX != prevNode.imageX)
    		return 0;
    	if (counter == 0) {
    		fallingList.add (node);
    		return 1;
		}   		

    	if (node.left != null && node.left != prevNode) {
    		if (checkColors (node.left, node, counter) == 1)
    		{
			fallingList.add (node);
			return 1;
		}
		else
		{
			return 0;
		}
	}

```
Anyway, if you can get how this part works then the second part (searching for falling nodes) is a pretty similar process.

---

### Post by Yes on 2008-06-05
Ok, I've added the return statements, but it still never calls the deleteNodes method.

Here's what it looks like now:

```
public int checkColors (BubbleNode node, BubbleNode prevNode, int counter) {

    	counter--;
    	if (node != null && prevNode != null && node.imageX != prevNode.imageX)
    		return 0;    		

    	if (counter == 0) {
    		fallingList.add (node);
    		return 1;
		}
    	if (node.left != null && node.left != prevNode) {
    		if (checkColors (node.left, node, counter) == 1) {
    			fallingList.add (node);
    			return 1;
			}
			else 
				return 0;
		}
    	if (node.right != null && node.right != prevNode) {
    		if (checkColors (node.right, node, counter) == 1) {
    			fallingList.add (node);
    			return 1;
			}
			else 
				return 0;
		}
    	if (node.topLeft != null && node.topLeft != prevNode) {
    		if (checkColors (node.topLeft, node, counter) == 1) {
    			fallingList.add (node);
    			return 1;
			}
			else 
				return 0;
		}
    	if (node.topRight != null && node.topRight != prevNode) {
    		if (checkColors (node.topRight, node, counter) == 1)  {
    			fallingList.add (node);
    			return 1;
			}
			else 
				return 0;
		}
    	if (node.bottomLeft != null && node.bottomLeft != prevNode) {
    		if (checkColors (node.bottomLeft, node, counter) == 1) {
    			fallingList.add (node);
    			return 1;
			}
			else 
				return 0;
		}
    	if (node.bottomRight != null && node.bottomRight != prevNode) {
    		if (checkColors (node.bottomRight, node, counter) == 1) {
    			fallingList.add (node);
    			return 1;
			}
			else 
				return 0;
		}
   
    	if (fallingList.size () > 2) {
    		deleteNodes ();
    	}
    	return 0;
    }
```

---

### Post by mike_g on 2008-06-05
Out of curiosity what is imageX? It sounds like part of a co-ord. You want to be comparing the image references for equality.

Thats the first thing that springs to mind. Also, maybe try printing out the return values to debug it. That could help give you an idea of where the problem is.

---

### Post by Yes on 2008-06-05
I've got one image that then has 7 different colored bubbles inside of it.  imageX is the x coordinate of the start of whatever color bubble that node is, within the larger image. 

I'll test the return values now.

e:  I'm just printing a 1 or 0 whenever either something is returned:

When I have just two of the same color connected, I get two '0's.
I also get two '0's when I have three of the same color connected.

After firing a few more up, it seems that it never returns '1'.

---

### Post by mike_g on 2008-06-06
> When I have just two of the same color connected, I get two '0's.
I also get two '0's when I have three of the same color connected.
Two of the same colour should return 0 - so thats fine. Three of the same colour should return 3 1's. The fact that its returning 2 0's seems to indicate that its not getting to the last function.

You are passing the number 3 as the count variable when you call the first function? Otherwise are you sure they are all connected? You could try printing out each bubbles neighbor cells too.

I think you will also end up with problems here:
```
    	if (fallingList.size () > 2) {
    		deleteNodes ();
    	}
```
As you can connect up to 5 bubbles with one shot. If you are deleting them as soon as you get 3, any extra wont be removed. It would be better to flag the for removal and only delete them once you are finished.

---

### Post by Yes on 2008-06-06
Yeah, I've changed that so the if statement is in the delete method, which is called outside of checkColors after it's finished.

All the nodes are connected.  And I just discovered that sometimes, nodes are deleted.  I'm not sure exactly what needs to happen, though, for that to happen.  Here's some pictures, maybe someone else will be able to make sense of it:

Before, you can see two bubbles in a horizontal line: [http://g.photos.cx/beforeBubbles-fe.png](http://g.photos.cx/beforeBubbles-fe.png)

Then, you can see the two bubbles gone, but the new bubble is still there: [http://g.photos.cx/afterBubbles-f3.png](http://g.photos.cx/afterBubbles-f3.png)

But then when there's a triangle of three, like this: [http://g.photos.cx/beforeBubbles2-77.png](http://g.photos.cx/beforeBubbles2-77.png)

None of them get removed: [http://g.photos.cx/afterBubbles2-bf.png](http://g.photos.cx/afterBubbles2-bf.png)

---

