---
title: "Dijkstra"
date: 2007-12-28
forum: Programming Talk
---

### Post by joebanana on 2007-12-28
I have a list of vertexes and each vertex has list of Edges that link to another vertex(GRAPH build with adj List). Edges have weight. I need to implement dijkstra on this structure. I found some dijkstra algorithms but my knowlage is to limited to apply it to my graph. Please help** I am working on this proble 2 whole days now...**

```

class Vertex
{
      Edge* firstEdge;
     int ID;
     Vertex* next;
    ......
};

class Edge
{
      Vertex* v;
      Edge* next;
      float weight;
     .....
};

``` 

need to apply it to :

    * G.size() is the number of vertices in our graph
    * G[i].size() is the number of vertices directly reachable from vertex with index i
    * G[i][j].first is the index of j-th vertex reachable from vertex i
    * G[i][j].second is the length of the edge heading from vertex i to vertex G[i][j].first

We assume this, as defined in the following two code snippets:

typedef pair<int,int> ii;
typedef vector<ii> vii;
typedef vector<vii> vvii;


```

      vi D(N, 987654321); 
      // distance from start vertex to each vertex

      priority_queue<ii,vector<ii>, greater<ii> > Q; 
      // priority_queue with reverse comparison operator, 
      // so top() will return the least distance
      // initialize the start vertex, suppose it’s zero
      D[0] = 0;
      Q.push(ii(0,0));

      // iterate while queue is not empty
      while(!Q.empty()) {

            // fetch the nearest element
            ii top = Q.top();
            Q.pop();
                        
            // v is vertex index, d is the distance
            int v = top.second, d = top.first;

            // this check is very important
            // we analyze each vertex only once
            // the other occurrences of it on queue (added earlier) 
            // will have greater distance
            if(d <= D[v]) {
                  // iterate through all outcoming edges from v
                  tr(G[v], it) {
                        int v2 = it->first, cost = it->second;
                        if(D[v2] > D[v] + cost) {
                              // update distance if possible
                              D[v2] = D[v] + cost;
                              // add the vertex to queue
                              Q.push(ii(D[v2], v2));

                        }
                  }
            }
      }

```

---

### Post by LaRoza on 2007-12-28
Why are you doing this?

It smells like homework.

---

### Post by joebanana on 2007-12-28
We had to implement graph with adj List in java and we have dikstra written. But I decided to go with c++. Of course it's 4 school I am not going to lie. I would write that it's 4 school in the beginning if it was relevant :) . And as I said I builded graph from file but now having problem applying dijkstra.
 Or can someone point me how priority_queue functions. I read the reference but am confused. How do I insert vertex in the priority_queue based on vertex's path length.

---

