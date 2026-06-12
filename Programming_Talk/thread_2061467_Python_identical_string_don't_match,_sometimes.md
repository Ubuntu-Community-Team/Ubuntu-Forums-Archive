---
title: "Python identical string don't match, sometimes"
date: 2012-09-22
forum: Programming Talk
---

### Post by Frozen Forest on 2012-09-22
I got a text file containing a list of folder and file names, then i have a file system containing these items along with other files and folders. The script I'm writing scan in the file and folder names from the text file, then start searching the file system for these. The strange thing is that I get match sometimes.

Example
text file
```

file_a
file_c

```file system
```

/some/path/file_a
/some/path/file_b
/some/path/file_c
/some/path/file_d

```output from script
```

found:
/some/path/file_a

```it should have been
```

found:
/some/path/file_a
/some/path/file_c

```

---

### Post by juancarlospaco on 2012-09-22
Show code . . .

---

### Post by hakermania on 2012-09-22
Yes, show us your code. I suspect that the files are NOT identical and the thing that causes it is that in fact the contents of the 1st file are:
```

a
b
c
d

```
and the other's
```

a
b
c
d (\n)


```
So, there's a trailing \n

---

### Post by Frozen Forest on 2012-09-24
> **juancarlospaco said:**
> Show code . . .

> **hakermania said:**
> Yes, show us your code. I suspect that the files are NOT identical and the thing that causes it is that in fact the contents of the 1st file are:
```

a
b
c
d

```and the other's
```

a
b
c
d (\n)


```So, there's a trailing \n

see below

---

### Post by trent.josephsen on 2012-09-24
That's... not how you use os.path.walk... is it?

```
>>> os.path.walk('/home')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: walk() takes exactly 3 arguments (1 given)
```

os.path.walk is deprecated and has been for quite some time. Use os.walk instead.

---

### Post by Frozen Forest on 2012-09-24
> **trent.josephsen said:**
> That's... not how you use os.path.walk... is it?

```
>>> os.path.walk('/home')
Traceback (most recent call last):
  File "<stdin>", line 1, in <module>
TypeError: walk() takes exactly 3 arguments (1 given)
```os.path.walk is deprecated and has been for quite some time. Use os.walk instead.

You are correct, was using the walk function from the beginning, it show the same thing. What I actually use is a recursive tree structure. The point was the same, but it was os.walk. Here is the code. The problem is still the same 'if p in os.path.basename(tree_node.dir):' return false. I'm starting to guess it has something to do with the encoding

[PHP]
class Tree(object):
    def __init__(self, dirpath, parent = None, ignore = []):
        self.parent = parent
        self.dir = dirpath
        tmp_list = [os.path.join(dirpath, path) for path in os.listdir(dirpath)]
        subdirs = [path for path in tmp_list if os.path.isdir(path)]
        self.files = [path for path in tmp_list if os.path.isfile(path)]
        self.subdirs = []
        if subdirs:
            self.__scan__(subdirs, ignore)
    
    def __scan__(self, subdirs, ignore):
        self.subdirs = []
        for subdir in subdirs:
            if not os.path.basename(subdir) in ignore:
                self.subdirs.append(Tree(subdir, self, ignore))
                
    def __to_list__(self, dir_list):
        dir_list.append(self.dir)
        for d in self.subdirs:
            d.__to_list__(dir_list)
        return dir_list
    
    def delete(self):
        self.parent.subdirs.remove(self)
        del self
    
    def to_list(self):
        dir_list = []
        self.__to_list__(dir_list)
        return dir_list
    
    def p(self):
        print self.dir
        for d in self.subdirs:
            d.p()        
def scan(tree_node, find_other):
    for p in find_other:
        if p in os.path.basename(tree_node.dir):
            tree_node.delete()
            return
        for x in tree_node.files:
            if p in x:            
                tree_node.delete()
                return 
    if tree_node.subdirs:
        for node in tree_node.subdirs:
            scan(node, find_other)
[/PHP]

---

### Post by trent.josephsen on 2012-09-24
I'm not 100% sure, but os.path.basename may return the empty string when called on a directory -- could that be your mistake? You don't mention whether the bug affects only directory names, only file names, or both, which seems to me very relevant.

---

