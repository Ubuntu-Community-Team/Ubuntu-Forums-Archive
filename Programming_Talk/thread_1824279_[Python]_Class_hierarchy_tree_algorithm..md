---
title: "[Python] Class hierarchy tree algorithm."
date: 2011-08-13
forum: Programming Talk
---

### Post by cgroza on 2011-08-13
Hello everyone.

I am working on a tool that will build a tree of my class hierarchies.
So far, each class is represented by an object like this one:
```

class Class:
     def __init__():
          self.name = ""
          self.bases = [] # list of Class objects

```

So I gather my information, build one of the above object for each class and then store all of them into a list.
Now, here is where I am stuck. I want to put them in a wx.TreeCtrl but I have no idea how to arrange my data into a tree.

I have been trying to design an algorithm that will traverse the list and and add the data to the wx.TreeCtrl but with no luck, and now I am starting to get a headache.

So I am asking you guys, probably you did this in the past or know how to do it.

Thank you.

---

### Post by simeon87 on 2011-08-13
The tree would probably be something like:

- At the first level, you'd have all classes that are root classes (i.e., those that don't have any class above them).
- Under those nodes in the tree, you'd have all the subclasses and so on.

- ParentClass1
-- Subclass1OfParent1
--- ...(and so on)...
-- Subclass1OfParent1
- ParentClass2
-- Subclass1OfParent2
-- Subclass2OfParent2

Is that what you mean? Or do you have difficulty getting it into a wx.TreeCtrl?

---

### Post by cgroza on 2011-08-13
> **simeon87 said:**
> The tree would probably be something like:

- At the first level, you'd have all classes that are root classes (i.e., those that don't have any class above them).
- Under those nodes in the tree, you'd have all the subclasses and so on.

- ParentClass1
-- Subclass1OfParent1
--- ...(and so on)...
-- Subclass1OfParent1
- ParentClass2
-- Subclass1OfParent2
-- Subclass2OfParent2

Is that what you mean? Or do you have difficulty getting it into a wx.TreeCtrl?
I have problems getting my data into a wx.TreeCtrl.
My data has the form of a list of Class object. I do not know how to process the data and get it in the wx.TextCtrl. Basically, I lack an algorithm or something similar.

---

### Post by cgroza on 2011-08-13
So my algorithm so far:
```

        for cl in self.classes:
            children = self.FindChilds(cl)
            if not cl.tree_ctrl_root:
                cl.tree_ctrl_root = self.AppendItem(self.root, cl.name)
                for child in children:
                    child.tree_ctrl_root = self.AppendItem(cl.tree_ctrl_root, child.name)


```So when I test it on this file:
```

class Test():
    pass

class Test1(Test):
    pass

class Test2(Test1):
    pass
```I get this tree:
```

Test
-------Test1
Test2

```When it should be:
Test
------Test1
------------Test2 [/CODE]

I think I need some kind of recursive algorithm, but I have no experience with them.

---

### Post by simeon87 on 2011-08-13
Basically, you want to end up with a data structure that you can easily put into a GUI control: a list of classes that don't have a parent class above them. So not a list with all classes, as you have now.

You can then add each of those classes (and its subclasses) to the control.

There are two steps:

1. Gathering data about all the classes
2. Putting the data in a wx.TreeCtrl

Now, step 2 will be easily when you've done step 1 well. I imagine it to look like this:

- Start with a list of all classes
- For each class, find out if it has a parent class X and if so, remove it from the list of classes and add it to the list of children of X.
- Do this for each of the classes until you're done.
- You'll now end up with a list of classes with all the subclasses nicely into a hierarchy.

In your example, you'd start with the list [Test, Test1, Test2] and you'd end with the list [Test], where that object then has [Test1] in its bases variable, and Test1 has Test2 in its bases variable.

Why is this called bases by the way? It's easier to have a list of children for each node so you can easily access the child nodes of a class, as that's what you want to do later when you're putting everything in your GUI control.

You can then do step 2:

For each root class, add the node to the wx.TreeCtrl and then use [pre-order traversal](http://en.wikipedia.org/wiki/Tree_traversal) to add the child nodes as well, with indentation.

---

### Post by cgroza on 2011-08-13
> **simeon87 said:**
> Basically, you want to end up with a data structure that you can easily put into a GUI control: a list of classes that don't have a parent class above them. So not a list with all classes, as you have now.

You can then add each of those classes (and its subclasses) to the control.

There are two steps:

1. Gathering data about all the classes
2. Putting the data in a wx.TreeCtrl

Now, step 2 will be easily when you've done step 1 well. I imagine it to look like this:

- Start with a list of all classes
- For each class, find out if it has a parent class X and if so, remove it from the list of classes and add it to the list of children of X.
- Do this for each of the classes until you're done.
- You'll now end up with a list of classes with all the subclasses nicely into a hierarchy.

In your example, you'd start with the list [Test, Test1, Test2] and you'd end with the list [Test], where that object then has [Test1] in its bases variable, and Test1 has Test2 in its bases variable.

Why is this called bases by the way? It's easier to have a list of children for each node so you can easily access the child nodes of a class, as that's what you want to do later when you're putting everything in your GUI control.

You can then do step 2:

For each root class, add the node to the wx.TreeCtrl and then use [pre-order traversal]("http://en.wikipedia.org/wiki/Tree_traversal") to add the child nodes as well, with indentation.

Ok, thanks for the info. So for this method to work, I have to get the children of a class instead of the bases? 
I will try to to what you said tomorrow, I am too tired right now.

Thank you.

---

### Post by cgroza on 2011-08-13
UPDATE: I made it. Thank you for the tips and guidance.
Here is what I finally came up with:

```

        # get list of children
        to_be_removed = []
        for cl in self.classes:
            for c in self.classes:
                if cl in c.bases:
                    cl.children.append(c)
                    to_be_removed.append(c)


        self.classes = [ c for c in self.classes if not c in to_be_removed ]

        def WalkAndAddTree(node,root):
            node.tree_ctrl_root = self.AppendItem(root, node.name)

            for child in node.children:
                child.tree_ctrl_root = self.AppendItem(node.tree_ctrl_root, child.name)
                if child.children:
                    WalkAndAddTree(child, child.tree_ctrl_root)

        for cls in self.classes:
            cls.tree_ctrl_root = self.AppendItem(self.root, cls.name)
            for child in cls.children:
                WalkAndAddTree(child,cls.tree_ctrl_root)


```
I was trying to do it with loops all the time until I realized it makes more sense thinking recursively. :D

---

