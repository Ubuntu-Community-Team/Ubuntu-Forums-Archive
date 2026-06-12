---
title: "Python list of classes issue"
date: 2012-02-20
forum: Programming Talk
---

### Post by Anstice on 2012-02-20
Hi guys,

I'm running into trouble with some Python stuff. I have a list that has seven copies of a class and I am intending to change just the values of one of them but whenever I do it changes the value for all. 

Here is the class:

```

class Node:
    previous = -1
    distFromSrc = 1000000
    visited = False

``` 

And here is how I create the list:

```

def createNodeTable(network):
    nodeTable = []
    for line in network:
        nodeTable.append(Node)
    return nodeTable

```

'network' is a list of length 7 so when I print the 'nodeTable[x].visited' before I attempt to make any changes to the values I get 'False' for every one.

If I call the following function however all of the '.visited' values change to false not just the one I am intending to change.

Whatever 'currentNode' is changed to I get the same issue:

```

def setVisited(currentNode, nodeTable):
    nodeTable[currentNode].visited = True
    return nodeTable

```

Is there an issue with the setVisited function or is it to with the nodeTable? I don't even know where to start to try to fix this.

---

### Post by r-senior on 2012-02-20
I'm no Python expert, but doesn't an instance variable need to be prefixed with self?

```
class Node:
    def __init__(self):
        self.previous = -1
        self.distFromSrc = 1000000
        self.visited = False

```

Otherwise they will be class variables.

---

### Post by Anstice on 2012-02-20
That's one way of fixing it. The way I found after however was just to change the append line to Node() so each is a new instance.

---

### Post by Tony Flury on 2012-02-21
you have to do both I think.

Your original code creates a new instance once, and appends it to the list 7 times, and creates within the class a set of Class variables - i.e. every instance of the class you create will share the same data.

---

