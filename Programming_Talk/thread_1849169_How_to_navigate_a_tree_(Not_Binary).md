---
title: "How to navigate a tree? (Not Binary)"
date: 2011-09-24
forum: Programming Talk
---

### Post by WinterMadness on 2011-09-24
Assume each node has four children, how would I navigate through it?

Im using Java, but I would like to know how to do it in general, without relying on too many API's. I understand theres a mathematical way of doing it


Also, the only way I know how to deal with a tree is to store it into a one dimension array (or arraylist etc)

---

### Post by Bachstelze on 2011-09-24
Define "navigate".

---

### Post by WinterMadness on 2011-09-24
> **Bachstelze said:**
> Define "navigate".

Okay. Imagine a tree structure it has the root, and four children, and the children have four children each (this process continues as far as necessary)

Each one of these nodes would have data in it, like a number(stored as a string). The root would have "1", the left most child would have "2" in it, one over from that has "3" etc

Its important to note, that I assume that I want to store this tree as a one dimensional array(string type) in the form of:
0: Root
[COLOR="Red"]**1**[/COLOR]: Left most child of the room
2: next child over of root
3: third child of root
4: fourth child of root
5: left most child of index [COLOR="Red"]**1**[/COLOR]
etc
So if I wanted to navigate to the third level down, right most node, how would I find it?

---

### Post by NovaAesa on 2011-09-24
I doesn't really matter how you store the tree for tree traversal algorithms, as long as you have a way of getting from a parent node to its children (and possibly from a child to its parent).

For third level down, right most child, simply loop through 3 times each time setting current node to the current node's rightmost child. Obviously start with current node equal to the root node.

---

### Post by Bachstelze on 2011-09-24
> **WinterMadness said:**
> 
So if I wanted to navigate to the third level down, right most node, how would I find it?

It would of course be at index 4+4^2. ;)

---

### Post by lisati on 2011-09-24
In short, use a [linked list]("http://en.wikipedia.org/wiki/Linked_list").
> **NovaAesa said:**
> I doesn't really matter how you store the tree for tree traversal algorithms, as long as you have a way of getting from a parent node to its children (and possibly from a child to its parent).
^^^ This. Your data structure should include at least the means link to each of the potential children. Sometimes a link back to the parent is useful. If the child hasn't been created yet, initialise it to  a "nonsense" value that you can use to easily recognize this - if you're using pointers, a value of NULL can work well.

*** End of homework tip ???? ***

---

### Post by Bachstelze on 2011-09-24
> **lisati said:**
> In short, use a [linked list]("http://en.wikipedia.org/wiki/Linked_list").

^^^ This. Your data structure should include at least the means link to each of the potential children. 

The fact that the tree is stored in a one-dimensional array and that its structure is known gives a link from a node to its children/parent: just add/substract the right value, which is easy to calculate.

Also a linked list doesn't give any real benefit over an array for storing a tree.

---

### Post by WinterMadness on 2011-09-24
> **Bachstelze said:**
> It would of course be at index 4+4^2. ;)

is there like a general way to apply that?

For example, if instead I wanted to find the left most node in the second row, or some other value. X+Y^Z

what does each variable represent? Is z always two? What if the number of nodes is different, how would I change the calculations?

Sorry to ask for all of this, but im not finding the appropriate information through google.

---

### Post by simeon87 on 2011-09-24
> **WinterMadness said:**
> is there like a general way to apply that?

For example, if instead I wanted to find the left most node in the second row, or some other value. X+Y^Z

what does each variable represent? Is z always two? What if the number of nodes is different, how would I change the calculations?

Sorry to ask for all of this, but im not finding the appropriate information through google.

You don't need a formula to find a node a few steps down in the tree. All you need is a formula to find the four children, given the index of the root node. If you then want a child of one of the children, you simply apply the formula twice: once to the root node, and once to the index of the child node that you have obtained from the previous calculation.

---

### Post by cgroza on 2011-09-24
You could use a recursive function and an argument to keep track of the dept to loop through the tree.
This is how I see it:
```

def get_node(tree_node, cur_level, target_level, node_index):
     if cur_level == target_level:
         return tree_node.child_nodes[node_index]
     for node in tree_node.child_nodes:
          get_node(node, cur_lever + 1, target_level, node_index)


```

---

