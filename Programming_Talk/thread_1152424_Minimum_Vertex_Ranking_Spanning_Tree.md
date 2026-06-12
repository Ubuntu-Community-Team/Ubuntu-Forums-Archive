---
title: "Minimum Vertex Ranking Spanning Tree?"
date: 2009-05-07
forum: Programming Talk
---

### Post by izint on 2009-05-07
Hi, I'm new here and I'm not sure whether this should go here or 
I need help on an algorithm 
so I am given a spanning treee

..9---8---3       
.........\ /
..7      2
....\   /   
......1                        
so assuming that each edge has a distance.
I need to minimize the maximum distance to any other vertex.  (d is distnace)
so what i mean is that, if I pick 3 as the root and lets say the distance from 3 to 9 is 4d, and 3 to 7 is 9d, so the maximum distance to any other vertex is 9d
now if I pick 2 as the root, lets say 2 to 9 is 10d and 2 to 7 is 3d, so then the maximum distance to any vertex from 2 is 10d
so then I keep doing this for each node,
and finally i find a root where I have the minimum distance to any other node, so in this case using the two examples above, the root would be 3 to minimize the maximum distance.

my TA, said something about using a binary tree? then looking at the nodes and reaching to the parents but im not sure.
I need to find a better way of doing this than O(n^2) which is 
for(each vertex)
  for(every other vertex)
     find distance and set to max if greater than current max distance
      save to array
check for smallest maximum distance in array then that node is the root

any help would be appreciated

---

### Post by MeLight on 2009-05-08
Let me check if I got this correctly: 
max(v, T) = the max distance to another vertex in T tree from v.
You need to find such v that it's max(v, T) <= max(u, T) for any u?

---

### Post by izint on 2009-05-08
> **MeLight said:**
> Let me check if I got this correctly: 
max(v, T) = the max distance to another vertex in T tree from v.
You need to find such v that it's max(v, T) <= max(u, T) for any u?

yes thats what i need to do, I know i can just brute force it by just using an n^2 algorithm going through each vertex and calculating all distances everytime but i'm trying to find an algorithm with a better time complexity.

---

### Post by MeLight on 2009-05-08
T is a binary tree? (No more the 2 children and 1 parent for each vertex?)

---

### Post by izint on 2009-05-08
The given tree is just a Minimum Spanning Tree

---

### Post by Zugzwang on 2009-05-08
Actually, the problem is not very hard, but appears to be homework, so I only give you a hint: Trees have two types of nodes: _______ and _______. Can you take advantage of that?

---

### Post by izint on 2009-05-08
yea, its for homework, im pretty sure ur trying to say parent and leaf nodes

but, my friends and I can't think of how to use that and implement better than O(n^2)

---

### Post by MeLight on 2009-05-08
yup, I can't either. Need another hint :P

Edit:
You need to check only the pathes between the leaves??

---

### Post by izint on 2009-05-08
even if I only look for the distances from the leaf nodes, wont i need to visit every node anyway in order to know the leaf nodes

---

### Post by MeLight on 2009-05-08
yeap, but that's only n, then it's the number of the leaves * path length. Which should be way less than n^2 in big trees. Unless there's something more elegant

---

### Post by izint on 2009-05-08
no, because from the spanning tree, i need to loop through each vertex (n) , and find the maximum length wouldn't i need to go through each node in order to get to the leaf nodes (n) so n^2?

---

### Post by MeLight on 2009-05-08
n - find the leaves
leaves * n - find max dist between leaves only
leaves - find min max

total - n + leaves + n*leaves ~ n*leaves

leaves*n is always < n*n (you must have at least one parent)

Although I'm not sure it's what your teacher meant. Will keep thinking

---

### Post by izint on 2009-05-08
although you have the leaf nodes, won't we need to visit the other nodes as well in order to find the root?

Edit:
for example :

   for(each vertex) O(n)
      for(each leaf) O(l)
          max(leaf, vertex) O(h) height, in order to reach the vertex

so n*l*h? h is from (log n to n)

---

