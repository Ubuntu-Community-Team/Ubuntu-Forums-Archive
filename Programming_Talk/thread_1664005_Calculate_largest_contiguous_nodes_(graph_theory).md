---
title: "Calculate largest contiguous nodes (graph theory)"
date: 2011-01-10
forum: Programming Talk
---

### Post by Asday on 2011-01-10
I've been googling and googling, but can't seem to find any help for my promble.

I'm trying to recreate [Dice Wars]("www.gamedesign.jp/flash/dice/dice.html") in Python, with some multiplayer support, for a college project.

I can't seem to work my head round a certain algorithm though.

I have a [graph]("http://en.wikipedia.org/wiki/Graph_(mathematics)") of nodes that are of two or more different types, (territories owned by different players), and need to calculate the largest contiguous string of similar nodes, (largest amount of territories owned by a player, that are contiguous).

Any help whatsoever would be greatly appreciated.

(Here is some simple sample data I'm using):

```
dict_nodes = {
    0: {
        "owner" : 0,
        "links" : (2,),
        },

    1: {
        "owner" : 1,
        "links" : (2,),
        },

    2: {
        "owner" : 1,
        "links" : (0,1,3,4),
        },

    3: {
        "owner" : 1,
        "links" : (2,4),
        },

    4: {
        "owner" : 0,
        "links" : (2,3,5),
        },

    5: {
        "owner" : 1,
        "links" : (4,),
        }}
```

---

### Post by PaulM1985 on 2011-01-10
I don't quite understand the data.  In the example here:

```

  2: {
        "owner" : 1,
        "links" : (0,1,3,4),
        },

```


Does this mean that node 2 is owned by player number 1 and it is linked with nodes 0, 1, 3 and 4?

Paul

---

### Post by Some Penguin on 2011-01-10
By "string", do you mean "connected component"?

[http://en.wikipedia.org/wiki/Tarjan's_strongly_connected_components_algorithm]("http://en.wikipedia.org/wiki/Tarjan's_strongly_connected_components_algorithm")

---

### Post by PaulM1985 on 2011-01-10
I think I would, assuming I was correct with my previous post, I would create a dynamic list of tested nodes and have a value of largest area for each owner.

I would then iterate over each node, getting the owner and the current size of the tested list then doing the test:

```

if not in tested list
    Add to tested list
    GetConnectedNodes()
    For each returned node,
       Test if owner is same as original node and the node is not in the tested list
          If true, add one to area for owner.
          Call this function recursively for this node.

```

Once the whole thing backs out, I think the new size of the tested list minus the original size before testing the node will be the size for the owner.  If this is larger than the current contigous size for the owner, add it to the owners largest space.

I think this works.  Just something I thought about.

Paul

---

### Post by Asday on 2011-01-12
> **Some Penguin said:**
> By "string", do you mean "connected component"?

[http://en.wikipedia.org/wiki/Tarjan's_strongly_connected_components_algorithm]("http://en.wikipedia.org/wiki/Tarjan's_strongly_connected_components_algorithm")

Unfortunately, no.

> **PaulM1985 said:**
> I don't quite understand the data.  In the example here:

```

  2: {
        "owner" : 1,
        "links" : (0,1,3,4),
        },

```


Does this mean that node 2 is owned by player number 1 and it is linked with nodes 0, 1, 3 and 4?

Paul

Yeah, here's an illustration of my data.  (Kinda hoped the dictionary woulda made things easier to see, but eh.)

[[img]http://g.imagehost.org/0270/lolgraph.gif[/img]](http://g.imagehost.org/view/0270/lolgraph)

Blue's largest contiguous is 3, and red's is 1.

> **PaulM1985 said:**
> I think I would, assuming I was correct with my previous post, I would create a dynamic list of tested nodes and have a value of largest area for each owner.

I would then iterate over each node, getting the owner and the current size of the tested list then doing the test:

```

if not in tested list
    Add to tested list
    GetConnectedNodes()
    For each returned node,
       Test if owner is same as original node and the node is not in the tested list
          If true, add one to area for owner.
          Call this function recursively for this node.

```

Once the whole thing backs out, I think the new size of the tested list minus the original size before testing the node will be the size for the owner.  If this is larger than the current contigous size for the owner, add it to the owners largest space.

I think this works.  Just something I thought about.

Paul

I didn't quite understand what you meant here, but while looking at your pseudocode and trying to understand it, I came up with a way that works brilliantly, thank you.

I'll post it on Thursday, when I next have access to it.

---

### Post by schauerlich on 2011-01-12
It's essentially a bunch of depth first searches, except any edge that leads to an opponent's node can be ignored. Keep a set of counted and uncounted nodes. Pick a random uncounted node, and run a DFS on it, adding each visited node to the counted set and removing it from the uncounted set. When the DFS terminates, take another element from the uncounted set and do it again until the uncounted set is empty. Keep track of the largest and return it. The algorithm could terminate early if you already have discovered a section that's larger than the amount of nodes remaining to be tested.

---

### Post by Some Penguin on 2011-01-12
In other words, it's precisely Tarjan's search for connected components, on the embedded graph (i.e. adjacency is filtered by ownership).

---

### Post by Asday on 2011-01-14
[php]def contig(land, owner):
    largest = 0
    larger = 0
    tested = []
    for i in xrange(len(land)):
        if i not in tested:
            if land[i]["owner"] == owner:
                tested.append(i)
                larger += 1
                for l in land[i]["links"]:
                    if l in tested:
                        break
                    if land[l]["owner"] == owner:
                        tested.append(l)
                        larger += 1
            if larger > largest:
                largest = larger
            larger = 0
            tested = []
    return(largest)[/php]

That's what I got to eventually.  It pulls any friendly node, then marks it off as seen, and checks each link in turn, marking them off too.

It's probably very inefficient, and I will look into this clever-people Tarjan business, but for now I think something I can explain will be better for my exam.

Thank you for your help.

---

### Post by PaulM1985 on 2011-01-14
I think you want to be using recursion rather than a normal method call.  If person A was linked with nodes 1 2 and 3 and the link of the nodes was like this:

1 -> 2 -> 3

Your algorithm would only pick up that 1 and 2 are related to person A, rather than 1, 2 and 3.

Paul

---

### Post by Asday on 2011-01-28
(Good god it's hard to find an image hosting site that isn't blocked at college.)

[[img]http://www.freeimagehosting.net/uploads/8300336dff.gif[/img]](http://www.freeimagehosting.net/)

That's the new graph I made up.  Contains cycles at 4-5-7-4 and 5-6-7-8-5, the former being all red, and the latter being a mix.  The dictionary for the graph is as follows:

(Forgot to start from 0, whoosp.)

[PHP]dict_nodes = {
    0: {
        "owner" : 1,
        "links" : (2,)
        },

    1: {
        "owner" : 2,
        "links" : (1,3)
        },

    2: {
        "owner" : 1,
        "links" : (2,5)
        },

    3: {
        "owner" : 1,
        "links" : (5,7)
        },

    4: {
        "owner" : 1,
        "links" : (3,4,6,7)
        },

    5: {
        "owner" : 2,
        "links" : (5,8)
        },
    6: {
        "owner" : 1,
        "links" : (4,5,8)
       },
    7: {
        "owner" : 2,
        "links" : (6,7)
       }}[/PHP]

My algorithm spits out 2 for owner 1, and 1 for owner 2.

God curses damnit.

---

### Post by worksofcraft on 2011-01-28
I need a similar algorthim for the following:

I have sets of dynamically allocated objects.
Some are directly or indirectly reachable from statically allocated objects and I don't want to garbage collect them.

Others are only reachable from other dynamically allocated objects and so to my application they are "unreachable" garbage that should be destroyed and memory released...

Replacing the word object with node... I didn't manage to make it work yet :confused:

---

### Post by cgroza on 2011-01-28
> **Asday said:**
> [php]def contig(land, owner):
    largest = 0
    larger = 0
    tested = []
    for i in xrange(len(land)):

That for loop is not very pythonic. The real python way should be:

```

for i in land:
    #do your thing           
```

much cleaner and easier.

---

### Post by Asday on 2011-01-28
> **cgroza said:**
> That for loop is not very pythonic. The real python way should be:

```

for i in land:
    #do your thing           
```

much cleaner and easier.

Cleaner, yes, but easier, no.  You'll notice I pass the i into dict_nodes[i] a lot.

---

### Post by cgroza on 2011-02-01
> **Asday said:**
> Cleaner, yes, but easier, no.  You'll notice I pass the i into dict_nodes[i] a lot.
It would still work, the 2 versions do the same thing.

---

### Post by Asday on 2011-02-03
> **cgroza said:**
> It would still work, the 2 versions do the same thing.

[PHP]    for i in xrange(len(land)): 
        if i not in tested: 
            if land[i]["owner"] == owner: 
                tested.append(i) 
[/PHP]

That last line is the vital one here.  Without the unPythonic intro, I'd need an i counter somewhere and an i+=1 somewhere else, which isn't as efficient.

---

