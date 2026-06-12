---
title: "Simple Java Instance Question"
date: 2009-09-23
forum: Programming Talk
---

### Post by JCoster on 2009-09-23
Hi guys,
Just a quick question.
I currently have a main class in Java defined as follows:
```
import java.util.ArrayList();

public class Graph {
   private ArrayList<Vertex> exampleList;

   public static void main(String[] args) {
       // create the graph instance
       new Graph();
   }

   public Graph() {
       exampleList = new ArrayList<Vertex>;
       // Populate the list as an example
       exampleList.add(new Vertex("example1"));
       exampleList.add(new Vertex("example2"));
   }

   public Integer getValue(Vertex tempVertex) {
       return exampleList.get(tempVertex);
   }

   public void printMessage() {
       System.out.println("Added successfully.");
   }
}
```

This is just an example...  I actually want to do something more meaningful than what I'm about to say BUT, from creating each vertex, can I call the printMessage() function from within the Vertex class?  

For example:
```
public class Vertex {
     private String value;
     
     public Vertex(String value) {
          this.value = value;

          /* 
           * Now I want to call the 'printMessage()' method from this
           * class.
           */
     }

}
```

Of course I know I could put the printMessage() method inside the Vertex class but really I want to do a method which can return a vertex from the ArrayList to the Vertex.

So it's actually more a case of the printMessage() method being:

```
public Vertex returnVertex(String value) {
     Vertex tempVertex = ..get vertex through some code and 
                         the Value parameter..
     /*
      * Where temp vertex is the vertex I've selected from some code
      * above.
      */
      return tempVertex;
}
```

Actually, I guess a simpler way to put this is that from each vertex in the ArrayList, I would like to be able to call a method **in** the Graph class **from** the Vertex class which allows me to get a different Vertex into the original Vertex instance.

And yes, I'm very bad at explaining things...

---

### Post by slavik on 2009-09-23
no, you can't.

printMessage is part of the Graph class and Vertex isn't told about who is initializing it. Besides, the Graph knows if the Vertex was created without issues.

---

### Post by dwhitney67 on 2009-09-23
You could expand the Vertex class to maintain a reference to its Graph container.

```

public class Vertex {
     private String value;
     private Graph graph;
     
     public Vertex(String value, Graph graph) {
          this.value = value;
          this.graph = graph;

          this.graph.printMessage();
     }
}

```

The Graph constructor would be something like:
```

   public Graph() {
       exampleList = new ArrayList<Vertex>;
       // Populate the list as an example
       exampleList.add(new Vertex("example1", this));
       exampleList.add(new Vertex("example2", this));
   }

```
Now whether this is a good design is debatable.

---

### Post by Reiger on 2009-09-23
You can have methods like this:
```

public Vertex deriveVertex(Vertext original) {
  /* stuff here */
}

```

As well as static equivalents (just add the static keyword after public); called like this: Vertex.deriveVertex(Vertex original);

This technique can be used if your Graph instance is static:
```

public class Graph {
  public static Graph graphInstance = new Graph();
  // other stuff here
  public static Vertex deriveVertex(Graph theGraph) {
    // stuff here...
  }
}

class Vertex {
  public void test() {
    Graph.deriveVertex(Graph.graphInstance);
  }
}

```

---

### Post by JCoster on 2009-09-23
Thanks for all your replies, but I've decided to go for this implementation:

> **dwhitney67 said:**
> You could expand the Vertex class to maintain a reference to its Graph container.

```

public class Vertex {
     private String value;
     private Graph graph;
     
     public Vertex(String value, Graph graph) {
          this.value = value;
          this.graph = graph;

          this.graph.printMessage();
     }
}

```

The Graph constructor would be something like:
```

   public Graph() {
       exampleList = new ArrayList<Vertex>;
       // Populate the list as an example
       exampleList.add(new Vertex("example1", this));
       exampleList.add(new Vertex("example2", this));
   }

```
Now whether this is a good design is debatable.

Thank you once again.

---

