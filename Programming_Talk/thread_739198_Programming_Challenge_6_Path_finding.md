---
title: "Programming Challenge 6: Path finding"
date: 2008-03-29
forum: Programming Talk
---

### Post by Wybiral on 2008-03-29
This weeks challenge is to find the _cheapest_ path from point A to point B.

Rules:
[list]
[*]Your program must read the grid from file
[*]Each cell can cost anywhere between 0 and 9
[*]The starting point of the path must be (0, 0) (left, top)
[*]The ending point of the path must be (N-1, N-1) (right, bottom)
[*]The path can NOT make diagonal moves, ONLY left/right/down/up
[*]You can NOT use a pre-written pathfinding library/module/etc
[/list]

The first line of the file that must be parsed contains N, which is the width & height of the grid (they are the same, it's a square). Each line after that will contain the actual cost of each cell (each line is one row, each cell will be a value between 0 and 9).

Here is an example of a 3x3 grid file:
```

3
112
291
191

```

The goal is to find the _cheapest_ path from (0, 0) to (N-1, N-1). That is, the sum of each cell visited along the path must be the lowest sum of all possible paths!

The resulting path can be presented in any way you choose. Some ideas could be:
[list]
[*]Realtime animation of something moving along the path
[*]Render the entire grid with the path being a separate color/character/object/etc
[*]Output a sequence of R/L/D/U describing the motions used to solve it
[*]Output the coordinates of each move
[/list]
Feel free to get creative with this part, provided it's clear what the solution is.

For example, the 3x3 grid above could be presented as:
```

(0,0) (1,0) (2,0) (2,1) (2,2)

```
```

RRDD

```
```

111
001
001

```

Clues: [...]("http://en.wikipedia.org/wiki/A*_search_algorithm") [...]("http://en.wikipedia.org/wiki/Dijkstra's_algorithm") [...]("http://en.wikipedia.org/wiki/Breadth-first_search") (to point you in the right wikipedia directions)

Be careful, the test file could be relatively large. I will favor fast solutions (not fast in terms of optimized code or language, but in terms of algorithm), so I won't be very impressed by purely brute-force search :)

Good luck, I'll pick the next challenge maker next Saturday (April 5).

---

### Post by WW on 2008-03-29
Are there any guidelines or requirements for how the program should handle multiple optimal solutions?

---

### Post by Wybiral on 2008-03-29
> **WW said:**
> Are there any guidelines or requirements for how the program should handle multiple optimal solutions?

Nope, as long as the cost of the path is the cheapest cost it can be.

---

### Post by mike_g on 2008-03-29
> You can NOT use a pre-written pathfinding library/module/etc
Bummer. I was going to post a module I coded in Blitz that does A* and Dijkstras pathfinding. Nevermid aye. Should be fun to see what people come up with :)

---

### Post by happysmileman on 2008-03-29
> **mike_g said:**
> Bummer. I was going to post a module I coded in Blitz that does A* and Dijkstras pathfinding. Nevermid aye. Should be fun to see what people come up with :)

I would assume that if YOU wrote the module it's ok, but ,aybe not, after all it does kidna give you an advantage in that your solution is pretty much already done.

Anyway I probably would do this challenge, but I have school tour for next 4 days, maybe I'll try it when I get back but I don't expect to be finished in time.

(I had no excuse for not entering any of the other competitions except for laziness)

---

### Post by Lster on 2008-03-30
This should be lovely to implement in Python! :)

---

### Post by nvteighen on 2008-03-30
OK, I'm gonna try this in C, you know, just to learn a bit more while coding. Expect the most messy and non-elegant solution!

---

### Post by CptPicard on 2008-03-30
I decided to turn this into my first real exercise in Scala, so here it is -- an implementation of Dijkstra's algorithm.

The parser is lame and needlessly imperative, but I'll leave it be as it's not the meat of the problem really.

Also, there is no heap, so extractMin is linear-time. I could have written it in terms of reduce for conciseness... I might update this if I find the time.

Check out the "match" clause in path discovery, that's a pretty cool feature... reminds me of Prolog.

```

package cptpicard.scalatest.dijkstra;

import java.util.Scanner;
import java.io.File;



object Dijkstra {
  
case class Cell (i : Int, j : Int, c : Int, d : Int, prev : Cell) {
  override def toString() : String = {
    return "("+i+","+j+") "+c+", "+d;
  }
  	        
  def neighbour(that : Cell) : Boolean = {
    (this.i == that.i && this.j == that.j-1) ||
    (this.i == that.i-1 && this.j == that.j) ||
    (this.i == that.i && this.j == that.j+1) ||
    (this.i == that.i+1 && this.j == that.j)   
  }
  
  def relax (that : Cell) : Cell = {
    if (that.neighbour(this)) {
      val alt = this.d + that.c
      if (alt < that.d)
        new Cell(that.i, that.j, that.c, alt, this)
      else
        that
    }        
    else
      that
  }
  
}                                                        
  			
  
  
  def parseinput(inputfile : String) : Tuple2[Int,List[Cell]] = {
    val scan : Scanner = new Scanner(new File(inputfile))
    
    val size = scan.nextInt()  
    
    // This structure is actually unnecessary as we're just processing lists of Cells
    // I don't bother actually rewriting the input parser to reflect that fact :-)
    var data : Array[Array[Cell]] = new Array[Array[Cell]](size)
    
    scan.nextLine()
    
    var row_i : Int = 0
    while (scan.hasNextLine()) {
      var linescan = new Scanner(scan.nextLine())
      var row = new Array[Cell](size)
      var col_i : Int = 0
      while (linescan.hasNextInt()) {
              row(col_i) = new Cell(row_i, col_i, linescan.nextInt(), 10000000, null : Cell)
              col_i += 1
      }
      data(row_i) = row
      row_i += 1      
    }
    
    scan.close
    (size, data.toList.flatten[Cell])
  }
  
  
  
  
  def perform (cells : List[Cell]) : List[Cell] = {
    
    def extractMin(done : List[Cell], rest : List[Cell], min : Cell) : Tuple2[Cell, List[Cell]] = {     
      if (rest == Nil)
        (min, done)
      else {
       val h = rest.head
       if (min == null)
         extractMin(done, rest.tail, h)
       else if (h.d < min.d)
         extractMin(min :: done, rest.tail, h)
       else
         extractMin(h :: done, rest.tail, min)         
      }        
    }
    
    
    def update(visited : List[Cell], queue : List[Cell]) : List[Cell] = {
    	if (queue.isEmpty)
    	  visited
        else {
	  val tup = extractMin(Nil, queue, null)
          update(tup._1 :: visited, tup._2.map[Cell]((c : Cell) => tup._1.relax(c))) 
        }
    }
  
    update(Nil, cells)
  }  
  
  
  def findPath(cells : List[Cell], max_index : Int) : List[Cell] = {
    def discover(i : Int, j : Int, cells : List[Cell], acc : List[Cell]) : List[Cell] = {
      val opt = cells.find((c : Cell) => (c.i == i && c.j == j))
      val item : Cell = opt.get      
      opt match {
        case Some(Cell(_,_,_,_,prev)) => 
        	if (prev == null)
        	  item :: acc
                else {
                 discover(prev.i, prev.j, cells.remove((n : Cell) => n == item), item :: acc)
                }
        case None => acc
      }
      
    }
    discover(max_index, max_index, cells, Nil)
  }
  
  
  def main(args : Array[String]) : Unit = {
	val tup = parseinput("/home/eneva/workspace/Dijkstra/input.txt")
        
        val dijkstra = perform (new Cell(tup._2.head.i, tup._2.head.j, tup._2.head.c, 0, null) :: tup._2.tail)
	
        Console.println(findPath(dijkstra, tup._1-1))

        ()
  }
}

```

---

### Post by nvteighen on 2008-04-01
OK, I tried to do it in C and gave up! (also, I'm a bit busy these days), but I'm very happy, to have learned some good things on how to open files and parsing them properly into an array. (well, I did a funny thing: by accident I told my program to open and parse itself... It's part of the learning process, I suppose).

I just can't wait and see how people solve this!

---

### Post by mike_g on 2008-04-01
I don't blame you. C is not the easiest language to do this in as you will have to make your ow lists for it. You may find it easier in a language that handles list for you such as java, or I expect python does too.

To me this challenge seems harder than any so far to be able to invent a solution. I tried and failed in the past, so ended up learning pathfinding algorithms from tutorials. If you decide to keep at it I'd recommend looking up A* as its well suited to the challenge task.

---

### Post by Wybiral on 2008-04-01
> **mike_g said:**
> To me this challenge seems harder than any so far to be able to invent a solution. I tried and failed in the past, so ended up learning pathfinding algorithms from tutorials. If you decide to keep at it I'd recommend looking up A* as its well suited to the challenge task.

You don't have to make an algorithm up. In fact, I encourage you to use one of the big ones (there are quite a few). It's mostly an exercise in your ability to learn an existing algorithm and implement it efficiently in your language of choice. Then creativity points for being able to present it originally.

---

### Post by ruy_lopez on 2008-04-01
> **mike_g said:**
> I don't blame you. C is not the easiest language to do this in as you will have to make your ow lists for it. You may find it easier in a language that handles list for you such as java, or I expect python does too.

To me this challenge seems harder than any so far to be able to invent a solution. I tried and failed in the past, so ended up learning pathfinding algorithms from tutorials. If you decide to keep at it I'd recommend looking up A* as its well suited to the challenge task.

I'm using C for this, with mixed results. I have a prototype that barely works. I'm using dijkstra's paper for guidance, which is probably not the best way. Most of the code "out there" uses the same basic model. None capture the spirit, or elegance, of the original paper. The paper presents some problems for a programmer. The method rejects branches, but leaves some stubs for further consideration. As a result, the solution has to be extracted from a list of branches, some of which are dead ends.

I'll probably not get finished in time. At least, not to my satisfaction. This *is* one of the toughest challenges. But it's also pretty cool.

---

### Post by mike_g on 2008-04-01
Wybiral: IMHO this challenge is flawed:
> I will favor fast solutions (not fast in terms of optimized code or language, but in terms of algorithm), so I won't be very impressed by purely brute-force search
From what I understand, for the given situation, A* will be the best algorithm for the job. So according to the quote any A* implementation should be a winner. This is nothing personal dude, I have full respect for you, but I think this seems to be is a single answer challenge. Still, I would very much like to see someone prove me wrong ;)

Edit: ruy_lopez: the way I did it was to have 2 lists. One holds open paths nd the other closed ones. Oh, and any of you guys that manage Dijkstras algorithm should find it fairly easy to convert to A*, theres not a whole lot of difference only A* uses a heuristic which produces optimal results when you know the target before beginning the search.

---

### Post by slavik on 2008-04-01
is paralelization allowed?

---

### Post by Wybiral on 2008-04-01
> **mike_g said:**
> Wybiral: IMHO this challenge is flawed:

From what I understand, for the given situation, A* will be the best algorithm for the job. So according to the quote any A* implementation should be a winner. This is nothing personal dude, I have full respect for you, but I think this seems to be is a single answer challenge. Still, I would very much like to see someone prove me wrong ;)

That's under the assumption that A* is the only good path-finding algorithm, which it is not :) Plus, there's more to it than the actual pathfinding algorithm, your use of data-types is important here (I just wanted to make it clear that language doesn't matter, but there's still room to misuse the datatypes at-hand). The main reason I say I would favor fast solutions is that I don't want to see any purely brute-force solutions here. I would also be impressed by originality, even if it's not quite as fast as the more popular pathfinding algorithms, as long as it's interesting.

And all of this said... Even if A* were the only solution (which it's not) and we all had to do it in the same language, with the same tools and datatypes (which we don't), I still left plenty of room for an interesting presentation. Find a neat and interesting way to display your results.

---

### Post by Wybiral on 2008-04-01
> **slavik said:**
> is paralelization allowed?

Absolutely :)

---

### Post by slavik on 2008-04-01
how about running this on a small cluster of 6 quadcore systems (or 50 SPARC systems) ? ^^

---

### Post by LaRoza on 2008-04-01
> **slavik said:**
> how about running this on a small cluster of 6 quadcore systems (or 50 SPARC systems) ? ^^

Sure, but I think Wybiral is going to test them, so he'd have to have access to these.

(Swipe me some parts while you are at it)

---

### Post by Wybiral on 2008-04-01
> **slavik said:**
> how about running this on a small cluster of 6 quadcore systems (or 50 SPARC systems) ? ^^

That sounds really neat, but as LaRoza said, I wouldn't be able to test it :( If the code could be run on a single computer, then I can check out the source and imagine it being run on a cluster :) (especially if it's readable and well-commented). But I would need to be able to run it to make sure it works.

---

### Post by mike_g on 2008-04-02
Sorry about all that moaning. I was drunk last night :rolleyes:

---

### Post by [h2o] on 2008-04-02
> **Wybiral said:**
> That's under the assumption that A* is the only good path-finding algorithm, which it is not :)  ...
And all of this said... Even if A* were the only solution (which it's not) and we all had to do it in the same language, with the same tools and datatypes (which we don't), I still left plenty of room for an interesting presentation. Find a neat and interesting way to display your results.

Actually, A*-search is optimal and complete as long as your search heuristic never overestimates the distance.
I quote *Artificial Intelligence: A modern approach, 2ed* by Russel and Norvig (page 97):
> 
In this case, A* is optimal if h(n) is an admissable heuristic - that is, provided that h(n) never overestimates the cost to reach the goal.


There might still be other algorithms that perform optimally and are complete.

---

### Post by nvteighen on 2008-04-02
> **mike_g said:**
> I don't blame you. C is not the easiest language to do this in as you will have to make your ow lists for it. You may find it easier in a language that handles list for you such as java, or I expect python does too.

Well, my problem were not the lists. I could manage to parse the file into an array properly in such a way that it should have been comfortable enough to use... The problem was the algorithm itself!

---

### Post by CptPicard on 2008-04-02
> **nvteighen said:**
> The problem was the algorithm itself!

Simple depth-first or breadth-first searches are actually just completely trivial to write... for depth-first you don't even need your own list, as long as you put a "mark" field into your array that lets you know when you're trying to process a node you already did.

They are of course not "good" ways to do it, but serve great as basic exercises...

---

### Post by nvteighen on 2008-04-03
> **CptPicard said:**
> Simple depth-first or breadth-first searches are actually just completely trivial to write... for depth-first you don't even need your own list, as long as you put a "mark" field into your array that lets you know when you're trying to process a node you already did.

They are of course not "good" ways to do it, but serve great as basic exercises...

I'm having a bad week. Maybe, with some more time, I could have done this... Well, I'll be watching for the next challenge.

---

### Post by CptPicard on 2008-04-03
Come on people, post something! Victory is up for grabs, mine just goes through the motions, I don't want to win by default or something! :)

---

### Post by kinghajj on 2008-04-03
[http://kinghajj.home.comcast.net/pathfinder.tar.bz2]("http://kinghajj.home.comcast.net/pathfinder.tar.bz2")

Do I win? :)

This is a custom algorithm, so it's probably terribly inefficient and/or very similar to another algorithm. But it seems to work. I'll write a README to explain the algorithm soon.

But FYI, the algorithm leans toward the bottom-left, meaning that if there are two equal paths, it will take the one that tends to go to the bottom and the left. The example grid shows this.

---

### Post by Lster on 2008-04-03
This is kind of Dijkstra's algorithm... in Python! :)

[PHP]
from heapq import heappush , heappop


try:
	handle = open ( "path.txt" )
	text = handle . read ( )
	handle . close ( )
except:
	print "Failed to read 'path.txt'.\n"
	exit ( )

try:
	lines = text . split ( "\n" )
	board = [ ]
	history = [ ]

	xsize = len ( lines [ 0 ] )
	ysize = len ( lines ) - 1
	
	if xsize < 1 or ysize < 1:
		print "Empty map!" ,
		exit ( )

	print "Dimensions:" , xsize , "," , ysize

	for i in xrange ( ysize ):
		board . append ( [ ] )
		history . append ( [ ] )
		for j in xrange ( xsize ):
			board [ i ] . append ( int ( lines [ i ] [ j ] ) )
			history [ i ] . append ( ( -1 , [ -1 , -1 ] ) )
	
except:
	print "Error parsing the file.\n"
	exit ( )

for i in xrange ( ysize ):
	for j in xrange ( xsize ):
		print board [ i ] [ j ] ,
	print



def next ( x , y ):
	if x > 0:
		yield x - 1 , y
	if x < xsize - 1:
		yield x + 1 , y
	
	if y > 0:
		yield x , y - 1
	if y < ysize - 1:
		yield x , y + 1


cands = [ ( board [ 0 ] [ 0 ] , 0 , 0 ) ]
history [ 0 ] [ 0 ] = 0 , [ -1 , -1 ]

while cands != [ ]:
	f , x , y = heappop ( cands )
	if f > history [ y ] [ x ]:
		continue
	
	if x == xsize - 1 and y == ysize - 1:
		break
	
	for nx , ny in next ( x , y ):
		nf = f + board [ ny ] [ nx ]
		
		best , q = history [ ny ] [ nx ]
		if nf < best or best == -1:
			heappush ( cands , ( nf , nx , ny ) )
			history [ ny ] [ nx ] = nf , [ x , y ]
	

path = [ ]
while x != -1 and y != -1:
	path . append ( [ x , y ] )
	c , q = history [ y ] [ x ]
	x = q [ 0 ]
	y = q [ 1 ]

path . reverse ( )

print "\nTook", f , "to move:"
for i in path:
	print i ,
print "\n"
[/PHP]

Not the best of solutions. It needs some improvements, but it works!

EDIT: I've improved the code slightly to check for an empty stack. It still does not report this, though. And it is actually, theoretically impossible to reach an empty stack as I think there is always a solution.

EDIT 2: I have updated it to use an improved (and slightly faster) algorithm, support rectangular "maps" and load maps from a file called "path.txt". Here is an example "path.txt":

[PHP]000700
881110
000000
011111
000000[/PHP]

I hope the code is bug free but have only tested it quickly. I'd welcome criticism after the challenge - especially that relating to pythonic coding. :)

EDIT 3: Some more small improvements and some error checking...

---

### Post by Wybiral on 2008-04-03
CptPicard: How do I compile / run your scala implementation? I tried using just "scala file.scala" but I get the following four errors:
```

/home/davy/Desktop/test.scala:1 error: illegal start of statement
package cptpicard.scalatest.dijkstra;
^
/home/davy/Desktop/test.scala:63 error: `)' expected
    (size, data.toList.flatten[Cell])
         ^
/home/davy/Desktop/test.scala:73 error: `)' expected
        (min, done)
            ^
<script trailer>:2 error: block must end in result expression, not in definition
} }
^
four errors found

```
I'm guessing I'm doing something wrong?


Lster: Looks good, but you need a parser (it should be trivial in Python to implement though).

---

### Post by CptPicard on 2008-04-03
Compile using "scalac", run just using Java, it's Java bytecode. :) I wrote and ran it in Eclipse (testing on a whole massive 5x5 grid :) ); I've never actually done anything in Scala outside of the plugin... so I *suspect* you just "java whatever.package.itwas.dijkstra.Dikstra". You may also need the scala jar.

(and oh yes, you might want to remove the package declaration so you don't have to mess with directories)

EDIT: Ermm.. right, it shows I have never actually run any Scala in terminal, let me get back to you... apparently the Scala implementation that comes from Ubuntu repositories is significantly older than the one that comes with the Eclipse plugin, so the older one does not like the tuple syntax, for example...

---

### Post by Lster on 2008-04-03
[QUOTE=Wybiral]Lster: Looks good, but you need a parser (it should be trivial in Python to implement though).[/QUOTE]

I forgot about that! :) If I get time I'll update my code and post in this thread to tell you I have done so.

---

### Post by CptPicard on 2008-04-03
Okay.. the associated file is not a "tar" but a .jar, had to rename it because of forum restrictions. It contains the cptpicard.scalatest.dijkstra.Dijkstra main class that takes as argument the file to parse. You need the Scala runtime .jar (scala-library.jar) as well in the classpath.

---

### Post by Lux Perpetua on 2008-04-04
> **kinghajj said:**
> [http://kinghajj.home.comcast.net/pathfinder.tar.bz2]("http://kinghajj.home.comcast.net/pathfinder.tar.bz2")

Do I win? :)

This is a custom algorithm, so it's probably terribly inefficient and/or very similar to another algorithm. But it seems to work. I'll write a README to explain the algorithm soon.

But FYI, the algorithm leans toward the bottom-left, meaning that if there are two equal paths, it will take the one that tends to go to the bottom and the left. The example grid shows this.I think your program fails on the following input: ```
5
00000
11110
00000
01111
00000
```

---

### Post by smartbei on 2008-04-04
Well, here is my entry. It is a plain Dijkstra, which uses pyGame to display the results. The code is but pretty slow, mostly due to a custom heap implementation (also attached).

You may ask, why did you write a custom heap implementation? I would answer - firstly, because I was not aware of heapq at the time, and secondly because my implementation is nicer api-wise (the heap is ordered according to a input function).

Anyway, see the code.

EDIT - fixed a small bug that caused an offset in the pygame display code.
EDIT2 - fixed a bug that caused incorrect paths in certain cases.

---

### Post by mike_g on 2008-04-04
Hmm . I just realised that A* would have been useless for this challenge as the minimum move cost is 0. Lol.

---

### Post by slavik on 2008-04-04
A* is cost to get to node + cost to get to finish from the node

even if moving to the node is 0 cost, moving from that node to the finish could be more expansive than moving to a node with cost 9 ...

---

### Post by mike_g on 2008-04-04
Yes, but to find the optimal path A* must never overestimate the heuristic. As the base cost is 0, a guranteed underestimate cannot be found so the heuristic will have to be 0. Remove the heuristic and you basically have dijkstras algo.

---

### Post by Lster on 2008-04-04
Original code updated! It now has a parser... ;)

---

### Post by slavik on 2008-04-04
> **mike_g said:**
> Yes, but to find the optimal path A* must never overestimate the heuristic. As the base cost is 0, a guranteed underestimate cannot be found so the heuristic will have to be 0. Remove the heuristic and you basically have dijkstras algo.
exactly ...

---

### Post by Lster on 2008-04-04
I have yet again updated my entry! Sorry guys!

---

### Post by nick_h on 2008-04-04
My solution is another Dijkstra algorithm written in Java.  I decided to write my own priority queue as an indirect binary heap.

The program can be run in two ways:  The first accepts an input file:
```
java Dijkstra FILE <filename>
```
Another useful for testing generates a random grid of a given size:
```
java Dijkstra RANDOM <size>
```

After reading the comment:
> Be careful, the test file could be relatively large.
I have tested the program on reasonably large files (1000x1000) and it works quite quickly (approx. 2.5s).

**Dijkstra.java**
[php]
import java.io.*;
import java.util.*;

/*
 *  Find the shortest path in an NxN grid with each vertex having a cost 
 *  between 0 and 9  and with vertices connected vertically and horizontally
 *  using Dijkstra's algorithm.
 * 
 *  Arrays store the vertices in a flat format.
 * 
 *  Costs are stored in the array, cost.
 *  The parent of each vertex is stored in the array, parent.
 *  The array visited records the progress of the search:
 *  	UNSEEN = Vertices not yet encountered.
 *  	negative = Vertices on the "fringe" but not yet on the shortest path.
 *  				The abs(value) is the shortest path length so far.
 *  				Fringe vertices are placed on the priority queue.
 *  	positive = Vertices on the shortest path.  The value is the shortest
 *                  path length to the vertex.
 *                  
 *  The priority queue uses an indirect binary heap.
 */
public class Dijkstra {

	private short[] cost;
	private int[] visited, parent;
	private int size;
	
	private static final int UNSEEN = -1000000;
	
	// Read grid from file
	public Dijkstra(File f) {
		BufferedReader r;
		String line;
		int i, j, n;

		try {
			r = new BufferedReader(new FileReader(f));
			line = r.readLine();
			size = Short.parseShort(line);
			cost = new short[size*size];
			for (i=0; i<size; i++) {
				line = r.readLine();
				for (j=0; j<size; j++) {
					n = Short.parseShort(line.substring(j, j+1));
					cost[i*size + j] = (short)n;
				}
			}
		} catch (Exception ex) {
			ex.printStackTrace();
		}
	}

	// Generate a random grid of a given size.
	public Dijkstra(int size) {
		Random generator = new Random();
		
		this.size = size;
		this.cost = new short[size*size];
		
		for (int i=0; i<size*size; i++) {
			cost[i] = (short)generator.nextInt(10);
		}
	}
	
	// Find the neighbours of a given vertex.
	public Vector<Integer> getEdges(int n) {
		
		Vector<Integer> result = new Vector<Integer>();

		int x = n % size;
		int y = n / size;
	
		if (y != 0) result.addElement(new Integer(x + (y-1)*size));
		if (y != size-1) result.addElement(new Integer(x + (y+1)*size));
		if (x != 0) result.addElement(new Integer((x-1) + y*size));
		if (x != size-1) result.addElement(new Integer((x+1) + y*size));
		
		return result;
	}
	
	public void shortest() {
		shortestPath(0, size*size-1);
	}
	// Finds the shortest path length
	private void shortestPath(int start, int end) {
		int thisVertex, nextVertex, total;
		Vector<Integer> edge;
		Iterator it;

		parent = new int[size*size];
		visited = new int[size*size];
		for (int i=1; i<size*size; i++)
			visited[i] = UNSEEN;
		
		PQueue pq = new PQueue(visited);
		
		// Initialise first vertex
		thisVertex = start;
		visited[thisVertex] = cost[thisVertex];
		parent[thisVertex] = -1;
		
		// Loop through each vertex until we get to the end
		while (thisVertex != end) {
		
			edge = getEdges(thisVertex);
			it = edge.iterator();
			// Loop through neighbours
			while (it.hasNext()) {
				nextVertex = (Integer)it.next();
				// Add to queue if lower cost or not seen yet
				if (visited[nextVertex] < 0) {
					total = -cost[nextVertex]-visited[thisVertex];
					if (pq.update(nextVertex, total)) {
						parent[nextVertex] = thisVertex;
					}
				}
			}
			// Get the lowest cost vertex (least negative)
			thisVertex = pq.remove();
			visited[thisVertex] = -visited[thisVertex];
		}
	}

	// Display the result coordinates
	public void result() {
		int thisVertex;
		thisVertex = size*size-1;
		while (thisVertex != -1) {
			System.out.print("[");
			System.out.print(thisVertex / size);
			System.out.print(", ");
			System.out.print(thisVertex % size);
			System.out.println("]");
			thisVertex = parent[thisVertex];
		}
	}

	// Display the grid
	public void display() {
		int i, j;
		for (i=0; i<size; i++) {
			for (j=0; j<size; j++) {
				System.out.print(cost[j + i*size]);
			}
			System.out.print("\n");
		}
	}
	
	public static void usage() {
		System.out.println("Usage:");
		System.out.println("java Dijkstra FILE <filename>");
		System.out.println("java Dijkstra RANDOM <size>");
	}
	
	public static void main(String[] args) {
		Dijkstra g;
		long start, stop, elapsed;
		
		if (args[0].equals("FILE")) {
			File f = new File(args[1]);
			g = new Dijkstra(f);
		} else if (args[0].equals("RANDOM")) {
			g = new Dijkstra(Integer.valueOf(args[1]));
			g.display();
		} else {
			g = null;
			usage();
			System.exit(0);
		}
		
		start = System.currentTimeMillis();
		g.shortest();
		stop = System.currentTimeMillis();
		elapsed = stop - start;
		System.out.println("Elapsed: " + elapsed + " ms");
        
		g.result();
	}

}
[/php]

Compile this and the attached file PQueue.java

---

### Post by slavik on 2008-04-04
this might not be the best code I've ever written and I wouldn't suggest using this code anywhere unless it is subjected to heavy modification.

the entire program should fit in most CPUs' L2 cache :)

and it's written in C and does just enough to conform to contest rules (and made as fast as possible while also being lazy).

I haven't thought about the design much.

---

### Post by nvteighen on 2008-04-05
> **slavik said:**
> this might not be the best code I've ever written and I wouldn't suggest using this code anywhere unless it is subjected to heavy modification.

the entire program should fit in most CPUs' L2 cache :)

and it's written in C and does just enough to conform to contest rules (and made as fast as possible while also being lazy).

I haven't thought about the design much.

Some newbie questions: why did you declared distance as an inline function instead of a regular function call? Is there a special reason to do it that way I don't see?

And what does min_cost = 0xFFFFFF do? Is it possible to assign a memory address to a regular double variable?

(Wow, now I see how far I was from getting the thing work)

---

### Post by Lster on 2008-04-05
slavik, I don't think it always gives the shortest path? When I try this:

> 6
8	0	0	7	0	0
8	8	1	1	1	0
0	0	0	0	0	0
0	1	1	1	1	1
0	0	0	0	0	0
0	0	0	0	0	0

It gives me this path:

> ( 0 , 0 )
( 0 , 1 )
( 0 , 2 )
( 1 , 2 )
( 2 , 2 )
( 2 , 3 )
( 2 , 4 )
( 2 , 5 )
( 3 , 5 )
( 4 , 5 )
( 5 , 5 )


Depending on the way round the x and y coordinates are it could produce these two paths:

[PHP]x 0 0 7 0 0
x 8 1 1 1 0
x x x 0 0 0
0 1 x 1 1 1
0 0 x x x x[/PHP]

Or:

[PHP]x x x 7 0 0
8 8 x 1 1 0
0 0 x x x x
0 1 1 1 1 x
0 0 0 0 0 x[/PHP]

I don't think either are the shortest, are they?

---

### Post by compwiz18 on 2008-04-05
> **Lster said:**
> 
[PHP]x 0 0 7 0 0
x 8 1 1 1 0
x x x 0 0 0
0 1 x 1 1 1
0 0 x x x x[/PHP]

Or:

[PHP]x x x 7 0 0
8 8 x 1 1 0
0 0 x x x x
0 1 1 1 1 x
0 0 0 0 0 x[/PHP]

I don't think either are the shortest, are they?

Howdy:

My submission (in Python):
```
#!/usr/bin/python
import sys

# turn the output grey
print "\033[1;30m"

def bruteForce(fromNode, currentNode, currentPath, noGo, currentMap, mapSize, currentCost):
	def getCostForMapPosition(currentNode, currentMap):
		return currentMap[currentNode[0]][currentNode[1]]

	if (currentNode[0] == mapSize - 1) and (currentNode[1] == mapSize -1):
		return (True, currentPath, currentCost)

	surroundingNodes = getSurroundingNodes(currentNode, currentMap, mapSize)

	smallestRoute = (None,)
	currentCost += getCostForMapPosition(currentNode, currentMap)

	extendedNoGo = list(noGo)
	extendedNoGo.extend(surroundingNodes)

	for node in surroundingNodes:
		if not node in noGo and not node in currentPath and not node is fromNode:
			extendedPath = list(currentPath)
			extendedPath.append(node)
			newPath = bruteForce(currentNode, node, extendedPath, extendedNoGo, currentMap, mapSize, currentCost)
			if newPath[0] and (smallestRoute[0] is None or newPath[2] < smallestRoute[2]):
				smallestRoute = newPath

	if smallestRoute[0]:
		return smallestRoute
	else:
		return (False,)

def getSurroundingNodes(currentNode, currentMap, mapSize):
	def appendToListIfValidNode(node, mapSize, theList):
		if (node[0] >= 0) and (node[1] >= 0) and (node[0] < mapSize) and (node[1] < mapSize):
			theList.append(node)

	theList = list() # will append nodes to this list as we find them
	appendToListIfValidNode((currentNode[0]+1, currentNode[1]), mapSize, theList)
	appendToListIfValidNode((currentNode[0], currentNode[1]+1), mapSize, theList)
	appendToListIfValidNode((currentNode[0]-1, currentNode[1]), mapSize, theList)
	appendToListIfValidNode((currentNode[0], currentNode[1]-1), mapSize, theList)

	# check to see if we are next to the final node!
	# if so, there isn't a lot of point in going around everywhere
	if (mapSize-1, mapSize-1) in theList:
		return [(mapSize-1, mapSize-1)]
	else:
		return theList
	return theList

def readMap():
	mapFile = open(sys.argv[1],"r")
	mapSize = int(mapFile.readline().strip())
	theMap = list()
	for line in mapFile.readlines():
		lineData = list(line.strip())
		lineData = [int(x) for x in lineData]
		theMap.append(lineData)

	return mapSize, theMap

def printMap(theMap, path):
	rowNumber = 0
	print
	for row in theMap:
		colNumber = 0
		for item in row:
			if (rowNumber, colNumber) in path:
				print "\033[1;31m"+str(item)+"\033[1;30m",
			else:
				print item,
			colNumber += 1
		rowNumber += 1
		print
	print

if len(sys.argv) <= 1:
	print """ERROR: Incorrect usage.
Usage:
	pathfinder.py MAPFILE"""
else:
	mapSize, theMap = readMap()
	path = bruteForce((0,0), (0,0),[(0,0)],[],theMap,mapSize,0)
	print "Cheapest path is:",path[1]
	printMap(theMap, path[1])
```
When run in a console, it will highlight the quickest path in red for you.  It isn't brilliant; it uses what one would probably call a brute force technique with some logic to achieve reasonable (for a brute search) times (7 seconds for a 7x7 grid and .2 seconds for a 6x6).  Someone with using A* will probably beat mine, but this is my first time doing path finding and A* sounded a little tricky to implement :)

Just as a note, when given the map above, it gives:
```
X X X 7 0 0
8 8 X 1 1 0
X X X 0 0 0
X 1 1 1 1 1
X 0 0 0 0 0
X X X X X X
```

:guitar:

---

### Post by nick_h on 2008-04-05
> slavik, I don't think it always gives the shortest path?
It doesn't give the shortest path with the supplied test grid either.
Type:
```
./a-star 100grid | sort | less
```
and you will see that the cell ( 2 , 3 ) appears twice.

---

### Post by nick_h on 2008-04-05
> This is a custom algorithm, so it's probably terribly inefficient and/or very similar to another algorithm. But it seems to work.

kinghajj, I tried your program on the following data:
```

6407092226
2805630863
4395994823
1176895129
1942287373
6236717886
5417561606
4318814731
0404650321
5621733672

*407092226
*805630863
*395994823
*176895129
*942287373
***6717886
54*7561606
43*8814731
04*4650321
56********

```

I think a shorter path would be to follow:
```

*407092226
*805630863
*395994823
*176895129
*942287373
***6717886
54*7561606
43*8814731
04********
562173367*

```

---

### Post by Wybiral on 2008-04-05
And the winner is ... smartbei!

The program implemented the correct file format (size as the first line, each following line contains the non-delimited node values), but mostly because it actually displays the path in a neat way, by slowly drawing it out. Now it's up to smartbei to pick the next challenge!

---

### Post by Lster on 2008-04-05
Congratulations smartbei! :KS

Looking forwards to the next challenge...

---

### Post by smartbei on 2008-04-05
Thank you Wybiral - I will be thinking of the next challenge - exect it up soon :).

---

### Post by ruy_lopez on 2008-04-05
Solid work, smartbei.

---

### Post by nvteighen on 2008-04-05
Congrats, smartbei! Really original way to output it!

---

### Post by slavik on 2008-04-05
> **nvteighen said:**
> Some newbie questions: why did you declared distance as an inline function instead of a regular function call? Is there a special reason to do it that way I don't see?

And what does min_cost = 0xFFFFFF do? Is it possible to assign a memory address to a regular double variable?

(Wow, now I see how far I was from getting the thing work)

inline asks the compiler to not do a real function call and to just expand the function as if it was a macro. if a function is inlined, you save the instruction to create a new stack, put arguments there and later removing it.

0xFFFFFF is simply a hex number which is 16777215 in decimal.
0x simply says that this is a hexadecimal number instead of decimal. :)

---

### Post by slavik on 2008-04-05
my program spits out the coordinates in y,x fashion (I should change it prolly), 0,0 is upper left corner. x and y increase towards right and down respectively.

also, this is not about the 'shortest' path, A* hels you find the cheapest path. you also can't follow the 0 nodes blindly, because they might not be getting you closer to your goal, that is the point of A*, it takes into account the distance from your goal. otherwise, it is just a greedy algorithm which would simply take longer ...

---

### Post by Lux Perpetua on 2008-04-05
Slavik, I tried your code on ```
5
0 0 0 0 0
1 1 1 1 0
0 0 0 0 0
0 1 1 1 1
0 0 0 0 0
```It doesn't work. To be honest, I can't make heads or tails of your algorithm, and I don't see any similarity between it and A* search.

---

### Post by nvteighen on 2008-04-05
> **slavik said:**
> inline asks the compiler to not do a real function call and to just expand the function as if it was a macro. if a function is inlined, you save the instruction to create a new stack, put arguments there and later removing it.

Well, this is really useful. I take notes on this! Thanks!

> 0xFFFFFF is simply a hex number which is 16777215 in decimal.
0x simply says that this is a hexadecimal number instead of decimal. :)

Ah! (well, mem address are normally expressed in hex, that's why I wondered).

---

### Post by Lux Perpetua on 2008-04-05
Where are my manners? I forgot to congratulate smartbei!

Also, thanks for posting an interesting challenge, Wybiral. I didn't end up submitting an entry (I had my own idea for an algorithm, but I couldn't work out the details), but it did make me wonder if the problem could be solved in linear time, since the graph is planar.  Apparently, linear-time algorithms have been discovered (and relatively recently); for example: [http://www.cs.brown.edu/research/pubs/pdfs/1997/Henzinger-1997-FSP.pdf](http://www.cs.brown.edu/research/pubs/pdfs/1997/Henzinger-1997-FSP.pdf)

---

### Post by nick_h on 2008-04-05
> also, this is not about the 'shortest' path, A* hels you find the cheapest path
The term "shortest" often seems to be used to mean "cheapest" when talking about weighted graphs.  I think that it may be because people tend to think about geographical graphs where cost between two vertices equates to a distance.

I used the term shortest path to mean that of least cost in my code.

---

### Post by smartbei on 2008-04-05
@slavik:
Looking at your algorithm, you seem to have implemented A*, but without an essential feature - the ability to backtrack. When you decide on the next step to take, you take into account only the nodes in direct contact with the current node, rather than all possible nodes (using a priority queue/minheap). and when you pass a node, you erase it completely.

@Lux Perpetua:
slavik is using the distance function as a heuristic function - the idea being that going in the general direction of the bottom right corner is better (an assumption that I am not sure applies here). That is why this program may fail cases where the value of the square is zero - if the increase in distance is greater than one in the direction of the zero.

BTW (@slavik again :D) - a way to solve the above zero problem may be to instead of using Pythagoras to find the distance, use a linear approximation such that the code for the distance function would be:
```

inline double distance(int ix, int iy, int fx, int fy) {
	if (ix < 0 || iy < 0) return 0xFFFFFFFF;
	int dx = fx - ix;
	int dy = fy - iy;
	if (dx < 0 || dy < 0) return 0xFFFFFFFF;
	return (dx + dy)/2;
}

```
Or something of the sort.

---

### Post by nick_h on 2008-04-05
> Also, thanks for posting an interesting challenge
Yes, this was a good challenge.  It is nice to read up about and implement some fundamental algorithms.

The implementations of A*, Dijkstra, depth-first and breadth-first are quite similar.  They differ really only in the priority given to finding the next vertex.

In addition to the winner, I liked a couple of others.  Lster's entry it worked well and quite quickly.  The use of the generator was neat.  CptPicard's entry got me looking at scala.

---

### Post by mike_g on 2008-04-05
> a way to solve the above zero problem may be to instead of using Pythagoras to find the distance, use a linear approximation such that the code for the distance function would be:

I dont see how that would work. No A* heuristic will help here, as the future tiles are unknown. Whatever way you get the distance the base move cost will still be 0. Therefore distance*base move cost will always be 0. Otherwise you risk overesitimating

---

### Post by Lster on 2008-04-05
[QUOTE=nick_h]Yes, this was a good challenge. It is nice to read up about and implement some fundamental algorithms.[/QUOTE]

Yes, thanks Wybiral! It was perfect to help my Python skills.

[QUOTE=nick_h]The term "shortest" often seems to be used to mean "cheapest" when talking about weighted graphs. I think that it may be because people tend to think about geographical graphs where cost between two vertices equates to a distance.[/QUOTE]

That was my meaning.

---

### Post by Wybiral on 2008-04-05
> **Lster said:**
> I'd welcome criticism after the challenge - especially that relating to pythonic coding. :)

The code (implementation) looked great to me, but I have two criticisms with respect to style:
[LIST=1]
[*]Too much space (I've never seen anyone space out their code as much as you :p )
[*]Tabs are evil in Python, spaces should be used exclusively
[/LIST]
One nice thing about Python is that most Python programmers use the same style (the style used in the Python standard library). It took me a while to get used to it, but it's worth it (most Python code uses this style, so it's easier to C&P or work on other peoples code). The official style guide (written by Guido himself) is [here]("http://www.python.org/dev/peps/pep-0008/"). The best example for style is the Python standard library, IMO it's a good idea to emulate that style as much as possible.

EDIT:

Wait, in my text editor your code has spaces, but when I quoted your post it was tabs... I'm confused! Take back what I said about tabs then, maybe the forums are doing something when I quote it.

---

### Post by Lster on 2008-04-05
I am using tabs. But why should I change to using spaces? If I do that I have to press backspace 4 times instead of once! :p

Many the other spaces are little to much, though. I do like my style, but no one else ever seems to use anything like it...

---

### Post by Wybiral on 2008-04-05
> **Lster said:**
> I am using tabs. But why should I change to using spaces? If I do that I have to press backspace 4 times instead of once! :p

Not if you use a good text editor :) You use them because it's just good practice in Python, that way when you C&P other code into your program (or other people C&P) it doesn't blow up. The key is to use an editor that has visual whitespace, and that treats four spaces as a tab (many modern editors do, I use gedit for instance, there are plugins available to make it behave this way, also eclipse + pydev is nice).

---

### Post by ruy_lopez on 2008-04-05
> **Lster said:**
> I am using tabs. But why should I change to using spaces? If I do that I have to press backspace 4 times instead of once! :p

Many the other spaces are little to much, though. I do like my style, but no one else ever seems to use anything like it...

For C, I wouldn't use less than 8 spaces for a tab. It's news to me that Python uses less than 8 spaces for indentation. In C, exceeding 80 columns is usually a good indication you need to restructure.

I have noticed it's harder to stick to 80 columns using Python. I guess that's why 4 space tabs are the standard.

You can define the size of tabspaces in most editors.

---

### Post by smartbei on 2008-04-05
You're right mike_g - A* is not appropriate for this challenge. My mistake above.

BTW - about python tab/spacing - I have never understood why spaces are better, as it seems to me that all reasons point to tabs being better (why should the editor need to configure something when there is a ready-made way to do it), So all of my code is tabbed. Doesn't really matter that much, as search and replace for this kind of thing is quite simple.

Tabbing also allows each person to choose his/her own size, without changing the underlying source code.

---

### Post by Wybiral on 2008-04-05
> **ruy_lopez said:**
> I have noticed it's harder to stick to 80 columns using Python. I guess that's why 4 space tabs are the standard.

Really? I find it easier personally. It's easier to modularize code and it's less verbose.

> **smartbei said:**
> I have never understood why spaces are better

Because Guido says so :)
It's just wise to follow the guidelines, that way all Python code can be a little more similar.
I try to make my code feel as much like the standard library as possible.

---

