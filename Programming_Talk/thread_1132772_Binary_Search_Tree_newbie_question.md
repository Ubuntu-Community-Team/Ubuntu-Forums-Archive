---
title: "Binary Search Tree newbie question"
date: 2009-04-22
forum: Programming Talk
---

### Post by fredscripts on 2009-04-22
Hi!

I've been reading about binary trees, and I have give them a try in python.

I've copied the implementation from here: [http://en.wikipedia.org/wiki/Binary_search_tree](http://en.wikipedia.org/wiki/Binary_search_tree)

Which includes a test. I put here the code for clarity:

```
class Node:
    def __init__(self, lchild=None, rchild=None, value=-1, data=None):
        self.lchild = lchild
        self.rchild = rchild
        self.value = value
        self.data = data
 
class Bst:
    """Implement Binary Search Tree."""
 
    def __init__(self):
        self.l = []  # Nodes
        self.root = None
 
    def add(self, key, dt):
        """Add a node in tree."""
        if self.root == None:
            self.root = Node(value=key, data=dt)
            self.l.append(self.root)
            return 0
        else:
            self.p = self.root
            while True:
                if self.p.value > key:
                    if self.p.lchild == None:
                        self.p.lchild = Node(value=key, data=dt)
                        return 0  # Success
                    else:
                        self.p = self.p.lchild
                elif self.p.value == key:
                    return -1  # Value already in tree
                else:
                    if self.p.rchild == None:
                        self.p.rchild = Node(value=key, data=dt)
                        return 0  # Success
                    else:
                        self.p = self.p.rchild
        return -2  # Should never happen
 
    def search(self, key):
        """Search Tree for a key and return data; if not found return None."""
        self.p = self.root
        if self.p == None:
            return None
 
        while True:
#            print self.p.value, self.p.data
            if self.p.value > key:
                if self.p.lchild == None:
                    return None  # Not found
                else:
                    self.p = self.p.lchild
            elif self.p.value == key:
                return self.p.data
            else:
                if self.p.rchild == None:
                    return None  # Not found
                else:
                    self.p = self.p.rchild
        return None  # Should never happen
 
    def deleteNode(self,key):
        """Delete node with value == key."""
 
        if self.root.value == key:
            if self.root.lchild == None and self.root.rchild == None: #No Children
               self.root = None
            elif self.root.lchild != None and self.root.rchild == None: #Only a left child
                self.root = self.root.rchild
            elif self.root.lchild == None and self.root.rchild != None: #Only a right child
                self.root = self.root.rchild
            else: #it has both children
                #in-order predecessor 
                self.p = self.root.lchild
                pParent = None
                while self.p.rchild != None: #find the right most child
                    pParent = self.p
                    self.p = self.p.rchild 
 
                if pParent != None: #it's not the first node on the left
                    pParent.rchild = self.p.lchild #Bottom of the tree is corrected
                    self.p.rchild = self.root.rchild #Swap the nodes
                    self.p.lchild = self.root.lchild #Swap the nodes
                    self.root = self.p
                else:
                    self.p.rchild = self.root.rchild
                    self.root = self.p
 
        else: #it's not the root
            self.p = self.root
            parent = self.root
            isLeft = 1
            Continue = 1
            while Continue:
                if self.p.value > key:
                    if self.p.lchild == None:
                        return None  # Not found
                    else:
                        parent = self.p
                        isLeft = 1
                        self.p = self.p.lchild
                elif self.p.value == key: #i'm at the right node
                    Continue = 0
                else:
                    if self.p.rchild == None:
                        return None  # Not found
                    else:
                        parent = self.p
                        isLeft = 0
                        self.p = self.p.rchild
 
            self._erase(parent,self.p,isLeft)
 
    def _erase(self, parent, node, isLeft):
        if node.lchild == None and node.rchild == None: #node has no children
            if isLeft:
                parent.lchild = None
            else:
                parent.rchild = None
        elif node.lchild != None and node.rchild == None: #node has only left child
            if isLeft:
                parent.lchild = node.lchild
            else:
                parent.rchild = node.lchild
        elif node.lchild == None and node.rchild != None: #node has only right child
            if isLeft:
                parent.lchild = node.rchild
            else:
                parent.rchild = node.rchild
        else: #node has 2 children
            #in-order predecessor 
            self.p = node.lchild
            pParent = node
            while self.p.rchild != None: #find the right most child
                pParent = self.p
                self.p = self.p.rchild 
 
            pParent.rchild = self.p.lchild #Bottom of the tree is corrected
            self.p.rchild = node.rchild #Swap the nodes
            self.p.lchild = node.lchild #Swap the nodes
            if isLeft: #place the node at the correct place
                parent.lchild = self.p 
            else:
                parent.rchild = self.p
 
    def sort(self):
        self.__traverse__(self.root, mode=1)
 
    def __traverse__(self, v, mode=0):
        """Traverse in: preorder = 0, inorder = 1, postorder = 2."""
        if v == None:
            return
        if mode == 0:
            print (v.value, v.data)
            self.__traverse__(v.lchild)
            self.__traverse__(v.rchild)
        elif mode == 1:
            self.__traverse__(v.lchild, 1)
            print (v.value, v.data)
            self.__traverse__(v.rchild, 1)
        else:
            self.__traverse__(v.lchild, 2)
            self.__traverse__(v.rchild, 2)
            print (v.value, v.data)
 
def main():
    tree = Bst()
    tree.add(4, "test1")
    tree.add(10, "test2")
    tree.add(23, "test3")
    tree.add(1, "test4")
    tree.add(3, "test5")
    tree.add(2, "test6")
    tree.sort()
    print tree.search(3)
    print tree.deleteNode(10)
    print tree.deleteNode(23)
    print tree.deleteNode(4)
    print tree.search(3)
    tree.sort()
if __name__ == "__main__": main()
```

My idea is to use the BST like a list, to insert an element, delete an element and searching for an element.

Once I run the test, I got:

```
(1, 'test4')
(2, 'test6')
(3, 'test5')
(4, 'test1')
(10, 'test2')
(23, 'test3')
test5
None
None
None
None
```

So I see that the insertions, sort ,and search are well-done.

What I don't understand is the delete operation. It seems that I have 6 elements on my BST, then I delete 3 of them.

So when I print again the BST, I should have the 3 remaining elements!!, the delete method of the class BST is long enough to handle that operation (I mean given a key to delete, just delete the node with that key).

What I'm missing here? Could anyone help me finding a code to delete properly from a BST? (delete in a array/list fashion).


Thanks so much in advance!

---

### Post by fredscripts on 2009-04-22
I've been reading the wikipedia info again and again, and I think I'm missing something here, because if this code really doesn't removes a single element from the binary tree, then the article in wikipedia should mention it (and it does not). But on the other hand, just copy and run the code and it works like that.

Any ideas? Please help!

---

### Post by fredscripts on 2009-04-23
No one can help me? :(

---

### Post by Arndt on 2009-04-23
> **fredscripts said:**
> I've been reading the wikipedia info again and again, and I think I'm missing something here, because if this code really doesn't removes a single element from the binary tree, then the article in wikipedia should mention it (and it does not). But on the other hand, just copy and run the code and it works like that.

Any ideas? Please help!

Debug output is a fine thing.

What tree.deleteNode returns is not the new tree, it always returns None. tree.sort() on the other hand prints the tree. If you use it at the end of the test, you'll see that the tree looks like it should.

---

### Post by fredscripts on 2009-04-23
> **Arndt said:**
> Debug output is a fine thing.

What tree.deleteNode returns is not the new tree, it always returns None. tree.sort() on the other hand prints the tree. If you use it at the end of the test, you'll see that the tree looks like it should.

Thanks for answering.

I understand that the delete operations return None.

What I still don't understand is why the last tree.sort() (after deleting 3 of the 6 elements) returns None. Shouldn't it print the remaining 3 items from the tree?

---

### Post by Arndt on 2009-04-23
> **fredscripts said:**
> Thanks for answering.

I understand that the delete operations return None.

What I still don't understand is why the last tree.sort() (after deleting 3 of the 6 elements) returns None. Shouldn't it print the remaining 3 items from the tree?

I missed this, sorry. Yes, it seems you've found an error in the implementation. Strange. Maybe you're the first person to actually run it? This code

```
            elif self.root.lchild != None and self.root.rchild == None: #Only a left child
                print "root3";
                self.root = self.root.rchild
```

ought to set self.root to the left child, not the right child. I'll let you change the wiki page.

---

### Post by fredscripts on 2009-04-23
> **Arndt said:**
> I missed this, sorry. Yes, it seems you've found an error in the implementation. Strange. Maybe you're the first person to actually run it? This code

```
            elif self.root.lchild != None and self.root.rchild == None: #Only a left child
                print "root3";
                self.root = self.root.rchild
```

ought to set self.root to the left child, not the right child. I'll let you change the wiki page.

Thanks so much! Now it works!!

---

### Post by fredscripts on 2009-04-26
It seems that there are more bugs in that implementation that I can't figure out.

Running this simple test:

```
    tree = Bst()
    ides = []
    for i in range(10000):
    	id = int(random.random()*10000)
    	if id not in ides:
    		ides.append(id)
    	tree.insert(id,"test "+str(id))

    
    tree.traverse("inorder")
    
    print "HAY"
    for i in range(0,len(ides)-1):
    	print "LAST: ",i," ",ides[i]
    	tree.deleteNode(ides[i])
```

which mainly add to the bst some entries like (3456,"test3456"), and then delete all of them. It crashes always.

I've focused the problem in deleteNode, the big else , in the while Continue:

```
if self.p.value > key:
	if self.p.lchild == None:
	   return None  # Not found
	else:
		parent = self.p
		isLeft = 1
         	print "CHANGE ",self.p.value, "BY: ",self.p.lchild.value
		self.p = self.p.lchild
```

That print statement tells the error because keep apearing that is changing the node with the same node.


I can't believe I cannot found a simple BST python code on the net that works just fine after 2 days of intensing googling.

Anyone can help me? I just want to test some benchmarks using BST vs lists in python.

---

### Post by fredscripts on 2009-04-26
Never mind, a friend gave me his own implementation with recursion and now works everything fine.

With this situations and the annoying indentation-errors of python when copying code from the internet I thing I'm gonna leave python.

In Perl I lasted half a second to find this: [http://search.cpan.org/~stevan/Tree-Binary-0.07/lib/Tree/Binary/Search.pm](http://search.cpan.org/~stevan/Tree-Binary-0.07/lib/Tree/Binary/Search.pm), same in Java, and even in C++.

Anyway ,thanks for the help!

---

