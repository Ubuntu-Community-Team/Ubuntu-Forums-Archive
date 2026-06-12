---
title: "std priority_queue"
date: 2007-12-28
forum: Programming Talk
---

### Post by joebanana on 2007-12-28
I have to use priority_queue. I have a list of Vertex and each Vertex has int path. I have to put the Vertexes in priority_queue which is based on the path parameter of class Vertex. (shortest is on top) How do I define priority_queue in my case?

---

### Post by dwhitney67 on 2007-12-28
Something like this should work, where Vertex is the struct or class that contains your data, including the 'path' value.  Note that the "compare" function is examining the 'path' value.

```
class PrioritizeVertices
{
  public:
    bool operator() ( const Vertex& lhs, const Vertex& rhs ) const
    {
      return rhs.path < lhs.path;
    }
};

typedef priority_queue< Vertex, vector<Vertex>, PrioritizeVertices > PQueue;

```

---

### Post by revanthedarth on 2007-12-29
You can do this too:

```

class Vertex
{
private:
int v1, v2, v3, v4, path;
public:
bool operator<(const Vertex a) const
{
return (a,path < path);
}
};
//then just 
std::priority_queue<Vertex, vector<Vertex> pq;

```

---

### Post by joebanana on 2007-12-29
I tried this, but got errors. 
ERRORS
pq.push(tmp) ->invalid conversion from Vertex* to int
pq.push(tmp)_>initializing argument 1 of Vertex::Vertex(int)
......
....

Please be patient I am just starting with std containers and templates...:(

```

#include <queue>
#include <vector>
#include <iostream>
using namespace std;

class Vertex
{
    private:
    int v2, v3, v4;
    public:
    int v1, path;
    Vertex(int j);
    bool operator<(const Vertex a) const
    {
        return (a.path < path);
    }
};

Vertex::Vertex(int j)
{v1 = j;}

int main()
{
    std::priority_queue<Vertex, vector<Vertex> > pq;
    Vertex* tmp = new Vertex(10);
    Vertex* tmp2 = new Vertex(5);
    Vertex* t;
    tmp->path = 10;
    tmp2->path = 5;
    pq.push(tmp);
    pq.push(tmp2);

      while (!pq.empty())
    {
     t = pq.top();
     cout << t->id << endl;
     pq.pop();
    }
}


```

---

### Post by joebanana on 2007-12-29
I got the program to work, but I get a segmentation foult(before that it writes 5 10 on screen, correct values). I push in priority queue the content on the address. Is that a correct use? Pls help.

```

int main()
{
    priority_queue<Vertex, vector<Vertex> > pq;
    Vertex* tmp = new Vertex(10);
    Vertex* tmp2 = new Vertex(5);
    Vertex* t;
    tmp->path = 10;
    tmp2->path = 5;
    pq.push(*tmp);
    pq.push(*tmp2);

      while (!pq.empty())
    {
       *t = pq.top();
        cout << t->v1 << endl;
        pq.pop();
    };
}

```

---

### Post by joebanana on 2007-12-29
Ok I found the problem. I need to create priority_queue and temlate input are Vertex* cuz i am storing pointer. Thx for help.

---

### Post by revanthedarth on 2007-12-30
```

#include <vector>
#include <iostream>
#include <fstream>
#include <queue>
class node{
public:
	int w, n;
	bool operator<(const node &a) const{
		return (w > a.w);
	}
};
using namespace std;
priority_queue<node, vector<node> > pq;
int V, E,i,j,k,l, adj[801][801], dis[801]; bool used[801];
vector<int> edge[801];
void dijkstra();
int main(){
	ifstream fin("graph.in");
	fin >> V >> E;
	for(i=0; i<E; i++)	{
		fin >> j >> k >> l;
		adj[j][k] =l;	adj[k][j] =l;
		edge[j].push_back(k);	edge[k].push_back(j);
	}
	dijkstra();
}
void dijkstra(){
	for(int i=1; i<801; i++)	dis[i] = INT_MAX;
	node tmp, tmp2;
	tmp.w=0;
	tmp.n=0;
	pq.push(tmp);
	while(!pq.empty())	{
		while(!pq.empty() && used[(pq.top()).n]) pq.pop();
		if(pq.empty())	break;
		tmp = pq.top();
		pq.pop();
		used[tmp.n] = true;
		dis[tmp.n] = tmp.w;
		for(k=0; k<edge[tmp.n].size(); k++)
		{
			j = edge[tmp.n][k];
			if(dis[tmp.n] + adj[tmp.n][j] < dis[j] && !used[j])
			{
				dis[j] = dis[tmp.n] + adj[tmp.n][j];
				tmp2.n = j;
				tmp2.w = dis[j];
				pq.push(tmp2);
			}
		}
	}
}

```

An example of std::priority_queue with Dijkstra's shortest path algorithm. I hope it helps. (You don't need to use pointers)

---

### Post by joebanana on 2007-12-30
I allready wrote the code. I wanted to learn more so I improvized a link list of vertex. Each has linked list of edges. But something is not working right. I really appreciate your help raven.
```


void Graph::dijkstra(Vertex* a)
{
    priority_queue<Vertex*> q;
    vector<Vertex*>::iterator i;
    vector<Vertex*> p;

    Edge* e;
    Vertex* v;
    Vertex* w;

    Vertex* tmp = firstVertex;
    while (tmp != NULL)
    {
            tmp->visited = false;
            tmp = tmp->next;
    }

    a->visited = false;
    a->parent = NULL;
    a->distance = 0.0;
    q.push(a);

    while (!q.empty())
    {
            v = q.top();
            q.pop();
            e = v->firstEdge;
            while (e != NULL)
            {
                    w = e->getEnd();
                    if (!w->visited)
                    {
                            w->visited = true;
                            w->parent = v;
                            w->distance = v->distance + e->getWeight();
                            q.push(w);
                    }
                    else if (v->distance + e->getWeight() < w->distance)
                    {
//THERE IS SOMETHING WRONG HERE I THINK...
                            w->parent = v;
                            *i = q.top();
                            for (int j = q.size(); j>0; j--)
                            {
                                if (*i == w)
                                {
                                        delete *i;
                                }
                            }
                            w->distance = v->distance + e->getWeight();
                            q.push(w);
                    }
                    e = e->next;
            }
    }

}

```

---

### Post by revanthedarth on 2007-12-30
Hmm... Can you post the Graph and Vertex class? Declarations would be sufficent. And, set Vertex class to be friend of Graph class. That way, you can use private members of Vector class, it might get a bit faster. To do this,

```

class Vertex
{
private:
	int w;
	friend class Graph;
};
class Graph
{
public:
	void func()
	{
		Vertex a;
		a.w = 2;
	}
};

```

And the proof of it being faster:
```

class Vertex
{
private:
	int w;
	friend class friendGraph;
public:
	int getW()
	{
		return w;
	}
};
class friendGraph
{
public:
	void func()
	{
		Vertex a;
		if(a.w == 35);
	}
	void loop(int a)
	{
		for(int i=0; i<a; i++)
			func();
	}
	void loop2(int a, int b)
	{
		for(int i=0; i<a; i++)
			loop(b);
	}
};
class notSoFriendGraph
{
public:
	void func()
	{
		Vertex a;
		if(a.getW() == 35);
	}
	void loop(int a)
	{
		for(int i=0; i<a; i++)
			func();
	}
	void loop2(int a, int b)
	{
		for(int i=0; i<a; i++)
			loop(b);
	}
};

int main()
{
	friendGraph fg;
	notSoFriendGraph nsfg;
	//fg.loop2(256,262144);
	//nsfg.loop2(256,262144);
}

```
with fg,
```

$ g++ test2.cpp
$ time ./a.out
real    0m0.613s
user    0m0.600s
sys     0m0.000s

```
With nsfg,
```

$ g++ test2.cpp
$ time ./a.out
real    0m0.943s
user    0m0.932s
sys     0m0.000s

```

---

### Post by joebanana on 2007-12-30
Here are my header files. The graph print ok on screen with all of its connections, so I think my dijkstra is off. And I was a little lazy and did't use encapsulation everywhere or friend class.

```

using namespace std;

#include <iostream>
#include <fstream>
#include <math.h>
#include <string>

#include "Vertex.h"
#include "Edge.h"
#include "AVLTree.h"

#define MAX_LINE_LEN 200

//DIRECTED GRAPH
class Graph {
    private:
        int         identifier;
       //LIST OF GRAPHS VERTEXES
        Vertex*     firstVertex;

    public:
        Graph(int id);
        Graph();
        ~Graph();


        Vertex*     getMin();
        Vertex*     getFirstVertex();
        int         getID();

        void        dijkstra(Vertex* a);
        void        makeNull();
        Vertex*     find(int ID);
        bool        addVertex(Vertex* v);
        bool        addEdge(Vertex* v1, Vertex* v2);
        bool        buildFromFile(string filePath);
        bool        intersects(double x1, double y1, double x2, double y2,
                                double x3, double y3, double x4, double y4);
        Edge*       firstEdge(Vertex* v);
        void        printGraph();
};

```

```

#include "Edge.h"
#include <iostream>
using namespace std;


class Vertex {
    public:
        int id;
        float x, y;

        //DIJKSTRA PARAMETERS
        bool visited;
        double distance;
        Vertex* parent;

        //LIST OF THE VERTEX EDGES
        Edge* firstEdge;

       //NEXT VERTEX IN LIST
        Vertex* next;

        Vertex(int ID, float xx, float yy);
        ~Vertex();

        void makeNull();
        void printEdges();

       //COMPARISON FOR PRIORITY_QUEUE
        bool operator<(const Vertex a) const
        {
            return (a.distance < distance);
        }
};

```

```

using namespace std;


class Vertex;

class Edge{
    private:
        float weight;

    public:
       //EDGE POINTS TO VERTEX VIA end
        Vertex* end;
        Edge* next;

        Edge(float w, Vertex* vEnd, Edge* eNext);
        ~Edge();

        float   getWeight();
        void    setWeight(float w);
        Vertex* getEnd();
        void    print();
};

```

---

### Post by revanthedarth on 2007-12-31
Linked list doesn't seem to me to be a suitable way for graph algorithms. You may need std::vector, which enables you to access elements in constant time. And it's better to use Graph::dijkstra(int k), which finds shortest paths from k.th Vertex.

And, instead of using edge class, you can have a sorted adj-like list. Think of this: Vertex class has a (sorted, so that you can use binary search for them) std::vector called edges, and its elements are ids of the vertices the Vertex has edge to. (Consider my code) You'll do just that, then:
```

v = pq.top();
for(i=0; i<v.edges.size(); i++)
	if(v.edges[i]->visited == false)
		pq.push(Vertices[v.edges[i]]);

```
Graph has vector<Vertex*>Vertices.

I hope you understand. But i can't imagine a Dijkstra with your header codes.

---

### Post by joebanana on 2008-01-01
Thanks that realy helped me.

 I am building graph from a file and the graph build's cca 4s. That 's largely due to find method. I need to check all the previous vertexes so i don't duplicate. And the complexity is of find is  n. I know 4s are not much but I like to see that timing reduced :)

 I was thinking I first read the vertexes into a set, so I have arranged order and the finding time is reduced to log n.


 What are your thoughts on that? How do i use the set's find method? I need to find it by a class id tag. How do I declare what to use for the key?

My try:

```

struct classcomp {
  bool operator() (const Vertex* lhs, const Vertex* rhs) const
  {return lhs->id<rhs->id;}
};

class Graph
{
   set<Vertex*,classcomp> vList;
  .....
}

```

My old linked list code

```

....
		if ((tmp=find(ID1)) != NULL)
                    v1 = tmp;
                else{
                          v1 = new Vertex(ID1);
                          addVertex(v1);
                       }
                if ((tmp=find(ID2)) != NULL)
                    v2 = tmp;
		else
                  {
                       v2 = new Vertex(ID2);
                       addVertex(v2);
                   }
....

```

---

### Post by revanthedarth on 2008-01-06
> **joebanana said:**
>  I am building graph from a file and the graph build's cca 4s. That 's largely due to find method. I need to check all the previous vertexes so i don't duplicate. And the complexity is of find is  n. I know 4s are not much but I like to see that timing reduced :)

 I was thinking I first read the vertexes into a set, so I have arranged order and the finding time is reduced to log n.


What are your thoughts on that? How do i use the set's find method? I need to find it by a class id tag. How do I declare what to use for the key?


Well, think of a graph, it's not vertices you need to store. It's edges. And, when you do a Dijkstra, it's better to have a vector vEdge, so that vEdge[i] is a Vector containing the edges that i.th vertex.You can vector<vector<int> > vEdge or, better way, vector<int> vEdge[size]. Normally it would be vector<Vertex>, but you'll store the location of the Vertex. So, Vertices<vEdge[i][j]> is the Vertex, which is j.th neighbor of i.th Vertex. You'll push Vertex data using this. Vertex class should contain the vertex data, and the weight. And pq will sort the vertices using the weight. 

If you sort the vEdge vector, you'll compute (whether two vertices are connected -by only one edge, of course-) in logn time. And doing this, Dijkstra will take nlogn, which is something you can't improve :)

I have a strange feeling that if i hadn't written it, i wouldn't understand anything from this post :D

Edit: And, can you show how you init the graph? I mean inputs, are they like "n m w" that n is connected to m and weight is w, or an adj list? It might be better for us, so we can choose the best data structure.

---

