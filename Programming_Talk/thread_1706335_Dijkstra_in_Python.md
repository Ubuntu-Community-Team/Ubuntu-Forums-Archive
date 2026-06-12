---
title: "Dijkstra in Python"
date: 2011-03-13
forum: Programming Talk
---

### Post by vity01 on 2011-03-13
Hi there,

I am trying to implement Dijkstra's algorithm in Python, but unfortunately I am struggling to get it to work because of the following error:

```
if nodeIndex != 0 and nodeTable[nodeIndex].visited == False:
TypeError: list indices must be integers, not list
```Here is my code:

```
infinity = 1000000
invalid_node = -1
startNode = 0
nodeIndex = 0

#Values to assign to each node
class Node:
     def __init__(self):
       self.distFromSource = infinity
       self.previous = invalid_node
       self.visited = False

#read in all network nodes
#node = the distance values between nodes
def network():
    f = open ('network.txt', 'r')
    theNetwork = [[int(networkNode) for networkNode in line.split(',')] for line in f.readlines()]
    #theNetwork = [[int(node) for node in line.split(',')] for line in f.readlines()]
    print theNetwork

    return theNetwork

#for each node assign default values
#populate table with default values
def populateNodeTable(): 
    nodeTable = [] #table to hold intial values
    index = 0 #to cycle through each node in file
    f = open('network.txt', 'r')
    for line in f: 
      networkNode = map(int, line.split(',')) #split at the comma in file
      nodeTable.append(Node()) #append to nodeTable
      
      print "The previous node is " ,nodeTable[index].previous 
      print "The distance from source is " ,nodeTable[index].distFromSource
      #print networkNode
      index +=1
    nodeTable[startNode].distFromSource = 0 

    return nodeTable

currentNode = startNode

#find the nearest neighbour to a particular node
def nearestNeighbour(currentNode, theNetwork):
     listOfNeighbours = [] #neighbours of a node
     nodeIndex = 0 #to cycle through nodes
     for nodeIndex in theNetwork:
          if nodeIndex != 0 and nodeTable[nodeIndex].visited == False:
            listOfNeighbours.append(networkNode)
            nodeIndex +=1
     print "The nearest neighbours are", listOfNeighbours
##     #print node.distFromSource, node.previous, node.visited
##
     return listOfNeighbours

def tentativeDistance (theNetwork, listOfNeighbours):
    shortestPath = []
    for node in theNetwork:
         currentDistance = theNetwork[currentNode] + startNode
         print currentDistance
         if currentDistance[theNetwork][nodeIndex] < Node.distFromSource:
            theNetwork[node].previous = nodeIndex
            theNetwork[node].distFromSource = nodeIndex
            theNetwork[node].visited = True;
            shortestPath.append(indexNode)
            nodeIndex +=1
    print shortestPath
        
        
#def shortestPath(tentativeDistance)
#     shortestPath = []
#     f = open ('shortestPath.txt', 'w')
#     f.write(shortestPath) 


#     f.close()

#currentNode = startNode

if __name__ == "__main__":
     nodeTable = populateNodeTable()
    #nodeTable = populateNodeTable(self)
     theNetwork = network()
     listOfNeighbours = nearestNeighbour(currentNode, theNetwork)
     #tentativeDistance(theNetwork, listOfNeighbours)
    

```As a beginner, I am struggling to see what the answer is and i'm not sure what else to do :confused:

---

### Post by cgroza on 2011-03-13
Are you sure that the nodeIndex variable does not end up a list somehow? That is what the 
error is saying, nodeIndex is a list.

---

### Post by vity01 on 2011-03-13
I have changed 'nodeIndex' to 'x' and then 'y' but on both occasions I still get the same error :s

---

### Post by vity01 on 2011-03-13
On second thoughts, I think it's because my variable 'nodeTable' is a list itself. I am not sure how I map this list into integers though? I have tried without success

---

### Post by The Cog on 2011-03-13
Well, it looks like when you read the file, theNetowrk comes out as a list of lists of integers. A 2D array of integers. But the meaning of that structure isn't clear to me.

---

### Post by vity01 on 2011-03-13
Yes, I understand now, however, i've hit another problem! I have updated my nearestNeighbour function like so:

```
def nearestNeighbour(nodeTable, networkNode):
     listOfNeighbours = []
     nodeIndex = 0 
     for y in theNetwork:
          if y != 0 and nodeTable[index].visited == False:
            listOfNeighbours.append(networkNode)
     nodeIndex +=1

     print "The nearest neighbours are", listOfNeighbours
     
     return listOfNeighbours
```

The output I am getting though is:

```
The nearest neighbours are [0, 0, 0, 0, 0, 0, 0]
```

I have defined index as 0 as a global variable, which I know is causing the problem. I am unsure on how I get the correct value from my populateNodeTable function though to ensure I get the correct output

---

