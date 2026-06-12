---
title: "c++ stumped on simple vector problem"
date: 2010-04-09
forum: Programming Talk
---

### Post by Xender1 on 2010-04-09
So I was working on coding a dynamic array of pointers, aka I had my graph class have a dynamic array point to the Vertices set up like so:
```

//in graph .h
Vertex* *vertices;

```
Vertex was my class name for the vertices of the graph. I kept getting a problem when trying to add a vector to this list (segmentation fault):
```

bool Graph::AddVertex(int myx, int myy) {
    Vertex *vert = new Vertex(numVertices, myx, myy);
    vertices[numVertices] = vert;  //seg fault here
    numVertices++;
    return true;
}

```
i figured that it was because in my graph constructor i have vertices=NULL;
and that i never allocated space for this array. So the fix i decided to ues was to #include <vector> at the top of my graph class and so now i declare my list of vertices as:
```

vector<Vertex*> vertices;

```
for some reason (even when I do a test main and just do vector<int> avec; i get this error:main.cpp:14: error: ‘vector’ was not declared in this scope. i look at the vector and see  that it says it is unable to resolve identifier vector.  (yes, i DID #include <vector>). so this is really stumping me. 

Some extra info is i am coding in netbeans and compiling with g++-4.4.

Thanks!

---

### Post by Zugzwang on 2010-04-09
Use "std::vector" instead of "vector" - All STL stuff resides in the namespace "std". In your .cpp files, you can also all "using namespace std;" such that you can omit these "std::" prefixes, however in header files, you shouldn't do this. Search the forum to find out why.

---

### Post by TheBuzzSaw on 2010-04-09
```
vertices[numVertices] = vert;  //seg fault here
```
When you want to add a new element, you cannot just force it in at the end. There is a method for doing that.

```
vertices.push_back(vert);
```

You can also do away with numVertices. Just access **vertices.size()** when you want to know how many you have. The vector container is very powerful. ;)

[http://www.cplusplus.com/reference/stl/vector/](http://www.cplusplus.com/reference/stl/vector/)

---

### Post by Xender1 on 2010-04-09
i set a private variable up as: vector<Vertex*> vertices;  in my constructor do I need to do anything with this?

---

### Post by TheBuzzSaw on 2010-04-09
> **Xender1 said:**
> i set a private variable up as: vector<Vertex*> vertices;  in my constructor do I need to do anything with this?

...only if you intend on making some call to a particular vector constructor different from the default one. In other words, no.

---

