---
title: "Java, Hashmap, Ajdacency lists."
date: 2010-01-06
forum: Programming Talk
---

### Post by EvenStevens on 2010-01-06
Okay, so I'm coding something to make a graph out of a bunch of nodes given in a text file.

[http://www.pastebin.org/71766](http://www.pastebin.org/71766)

i've come up with this data structure and building structure for making the graph, but I want to be able to print off the nodes and its links as an end product

So if the input was

node1 node2
node1 node3
node2 node3

The output would be

node1 -> node2 and node3
node2 -> node3

I've got another class that takes in the text files and puts everything in its place with that class I've given, I just dont know how to print out the links >__<

---

### Post by LKjell on 2010-01-06
Should be something like that. But you can try out iterator. And I suggest to use the type safety. You know those <>

```

Graph graph = new Graph();

....

Vertex v = (Vertex) graph.vertexMap.get("Whatever");

int size = v.adjacent.size();

Vertex node;

System.out.println(v.name);
for (int i = 0; i < size; i++) {
	node = (Vertex) v.adjacent.get(i);
	System.out.println(node.name);
}	
```

---

### Post by EvenStevens on 2010-01-06
Hmm, I totally get that, but for some reason when I try it it says "type (Edge) cannot be cast into type (Vertex)" or something similar.

It seems all my adjacent vertices are being set as a list of Edges rather than Vertices. Balls.

---

### Post by issih on 2010-01-06
That is indeed what your code does..on line 35:

```
v1.adjacent.add(new Edge(v2));
```

I have no idea what the point of the Edge class is, at the moment it is nothing but a placeholder for a vertex, but that is definitely what you are adding into your adjacent list....

---

### Post by LKjell on 2010-01-06
> **issih said:**
> That is indeed what your code does..on line 35:

```
v1.adjacent.add(new Edge(v2));
```

I have no idea what the point of the Edge class is, at the moment it is nothing but a placeholder for a vertex, but that is definitely what you are adding into your adjacent list....

issih is right. I did not notice that. Should be 
```
v1.adjacent.add(v2);
```

or...

node = (Vertex) v.adjacent.get(i).destination;

---

### Post by EvenStevens on 2010-01-06
Hmm...

a bit hacky, but if I were to change that line to

```
v1.adjacent.add(new Vertex(vtwo));
```

Would that be okay, or would that completely destroy everything from a data structure point of view?

EDIT: Just saw your above post. It would have to be vtwo, since v2 is a vertex and the vertex class takes a string - which vtwo is.

---

### Post by issih on 2010-01-06
Dunno...what is the point of the Edge class? is it meant to achieve something?

---

### Post by EvenStevens on 2010-01-06
Well, I'm kind of half doing this from lecture notes and half not, but I put it there incase I wanted to add things like edge weights etc. later on.

---

### Post by LKjell on 2010-01-06
If it was your professor that wrote that code then you should chide him.
the problem is that it is hard to read the code. Your linked list store Object Edge but you want to have as string and I want to have as Vertex...

so here is a modified of the code using those safety type measurement.

```
import java.util.*;
import java.io.*;

class Vertex
{
	String name;
	List<Edge> adjacent;
	//List<Vertex> adjacent
	//List<String> adjacent;
	
	public Vertex(String vert)
	{
		name = vert;
		adjacent = new LinkedList<Edge>();
	}
}

class Edge
{
	Vertex destination;
	
	public Edge(Vertex dest)
	{
		destination = dest;
	}
}

public class Graph
{
	Map<String, Vertex> vertexMap;

	public Graph()
	{
		vertexMap = new HashMap<String, Vertex>();
	}
	
	public void addEdge(String vone, String vtwo)
	{
		Vertex v1 = addVertex(vone);
		Vertex v2 = addVertex(vtwo);
		v1.adjacent.add(new Edge(v2));
	}
	
	public Vertex addVertex(String vname)
	{
		Vertex v = vertexMap.get(vname);
		
		if (v == null)
		{
			v = new Vertex(vname);
			vertexMap.put(vname, v);
		}
		
		return v;
	}
}
```

---

### Post by issih on 2010-01-07
If that is the plan, to have the edge class define the link between two things then it should stay as it is. At an abstract level I'd say that an "Edge" should hold onto both objects v1 and v2, but thats not massively important.

The best way to write out your node information is to have a little tree walking method defined on the vertex class:

```

void printInfo(int noOfLeavesToWalk)
{
	System.out.println(name);
	if(noOfLeavesToWalk >1)
	{
		for (int i = 0; i < adjacent.size(); i++)
		{
			Edge anEdge = (Edge) v.adjacent.get(i);
			anEdge.destination.printInfo(noOfLeavesToWalk-1);
		}
	}
}

```

If I have my thinking right that should walk your graph to generate your information....with the integer parameter defining how many levels down the rabbit hole it should go before stopping...I'll leave it to you to sort out the formatting of the text as you want.

Be aware though that in your data-structure there is nothing stopping you defining a loop, so that the node 1 links to 2 which links back to 1, in those circumstances a tree walker can get into an infinite loop...This one can't because of the numberOfLeavesToWalk parameter, but you do need to be aware of it nonetheless

---

