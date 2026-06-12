---
title: "Two classes including each chother"
date: 2007-12-14
forum: Programming Talk
---

### Post by joebanana on 2007-12-14
I have two classes in different .h files. How do I compile this. The compiler can't determine the type of eg endVertex...

```

#ifndef EDGE_H
#define EDGE_H

#include "Vertex.h"

#endif

class Edge
{
        Vertex* endVertex;
}

```

```

#ifndef VERTEX_H
#define VERTEX_H

#include "Edge.h"

#endif

class Vertex
{
      Edge* firstEdge;
}


```

---

### Post by HueyLuey on 2007-12-14
Is this C++? If so there are a few issues.

Put the #endif around the whole class declaration, not just the includes.

You don't actually need the includes in the headers in any case as you have used pointers. Instead use forward declarations above the class declaration as follows:

// Forward Declarations
class Vertex;

class Edge
{
private:
   Vertex* endVertex;
}; // note semi-colon at end of class declaration

You only need include Vertex.h from inside your Edge.cpp file.

Good luck:0)

---

### Post by joebanana on 2007-12-14
Turns out I was missing a semi-colon on the end of class headers. Thanks for help. :)

---

