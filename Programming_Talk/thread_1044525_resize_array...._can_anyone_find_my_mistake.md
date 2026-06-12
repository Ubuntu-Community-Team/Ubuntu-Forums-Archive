---
title: "resize array.... can anyone find my mistake??"
date: 2009-01-19
forum: Programming Talk
---

### Post by mcweaver1 on 2009-01-19
Hi

Ive created a program which reads in data from a file, each line is of the form <word> <word> representing two nodes with an edge going from the first to the second. It stores and outputs each starter node and the nodes each one is connected to. However I'm having a bit of difficulty with resizing the array...

If anyone can give me a few pointers (har har) I would be very grateful :)

```

import java.io.*;
import java.util.*;

class Graph
{
    private static String strLine = null;
    private static String node1 = null;
    private static String node2 = null;
    private static int initsize = 10;
    private static int numelements = 0;


    void readfile (String filename) throws FileNotFoundException
    {
        try
        {
            Vertex[] edge = new Vertex[initsize];
            for(int i=0; i<initsize; i++)
            {
                edge[i] = new Vertex();
            }
            BufferedReader reader = new BufferedReader(new FileReader(filename));
            while ((reader.ready())&&((strLine = reader.readLine()) != null))   
            {
                // splits each line into seperate words at a "\\s"
                Scanner scanner = new Scanner(strLine);
                scanner.useDelimiter(" ");
                //whilst still words left in the file to read in
                if (scanner.hasNext())
                {
                    //set node1 as the word before the "\\", set node2 as the word after
                    node1 = (scanner.next());
                    node2 = (scanner.next());
                }
                for (int j=0; j<edge.length; j++)
                {
                    if (j==edge.length)
                    {
                        resize(edge, edge.length);
                    }
                    if (edge[j].startnode == null)
                    {
                        edge[j].startnode = node1;
                        edge[j].endnodes.add(node2);
                        break;
                    }
                    else if (edge[j].startnode.equals(node1))
                    {
                        edge[j].endnodes.add(node2);
                        break;
                    }
                }
                //edge.length DOES NOT ouput the right number of elements in the array here
                System.out.println("Node1 = " + node1 + " ... node2 = " + node2);
            }
            print(edge, edge.length);
        }
        catch(IOException e)
        {
        }
    }

    private void print (Vertex[] edge, int length)
    {
        System.out.println();
        for (int i=0; i<length; i++)
        {
            if (edge[i].startnode == null)
            {
                break;
            }   
            System.out.println();
            System.out.print("Node " + edge[i].startnode + " links to nodes ");
            for (int j=0; j< edge[i].endnodes.size(); j++)
            {
                System.out.print(edge[i].endnodes.get(j));
                if (!(j==(edge[i].endnodes.size()-1)))
                    System.out.print(",");
            }
        }
        System.out.println();
    }

    /*public Graph()
    {
    }*/

    private Vertex[] resize (Vertex[] edge, int length)
    {
        Vertex[] newEdge = new Vertex[length*2];
        for (int i=0; i<length*2; i++)
        {
            newEdge[i] = new Vertex();
            //newEdge[i] = edge[i];
        }
    System.arraycopy (edge, 0, newEdge, 0, length);
    edge = newEdge;
    return edge;
    }

    public static void main(String arg[]) throws FileNotFoundException
    {
        if (arg.length!=2)
        {
            System.err.println("Wrong input, two arguments needed");
            System.exit(1);
        }
        Graph program = new Graph();
        program.readfile(arg[1]);
    }
}

```

---

### Post by DFord425 on 2009-01-19
j will never equal edge.length. If it does equal edge.length, it will exit the for loop.
```
if (j==edge.length-1)
                    {
                        resize(edge, edge.length);
                    }
```

---

### Post by DFord425 on 2009-01-19
or change the for loop:
```
for (int j=0; j<=edge.length; j++)
```

---

### Post by mcweaver1 on 2009-01-19
Ah yes thats true!

However, i just corrected it and still my array refuses to resize...

One thing Ive noticed is that whenever I try and output the number of elements in the array (using edge.length) it outputs the initial size of the array that i specified at the beginning and not the actual number of elements in it......

Any ideas? This is bugging me!!
Cheers

---

### Post by DFord425 on 2009-01-19
> **mcweaver1 said:**
> Ah yes thats true!

However, i just corrected it and still my array refuses to resize...

One thing Ive noticed is that whenever I try and output the number of elements in the array (using edge.length) it outputs the initial size of the array that i specified at the beginning and not the actual number of elements in it......

Any ideas? This is bugging me!!
Cheers

Thats exactly what edge.length is supposed to print out.

As to the resize array problem. Your code:
```

    System.arraycopy (edge, 0, newEdge, 0, length);
    edge = newEdge;
    return edge;

```
Try returning newedge rather than having the line ```
edge = newedge;
```

---

### Post by stroyan on 2009-01-19
When you assign to the "edge" parameter in your resize function you are only modifying a local copy that the function is using.
This confusion about pass-by-value vs. pass-by-reference is common.
It is discussed in several articles such as-
[http://www.javaworld.com/javaworld/javaqa/2000-05/03-qa-0526-pass.html](http://www.javaworld.com/javaworld/javaqa/2000-05/03-qa-0526-pass.html)
and
[http://www.cs.umd.edu/class/sum2004/cmsc420/sum4v3e01/node6.html](http://www.cs.umd.edu/class/sum2004/cmsc420/sum4v3e01/node6.html)

You could use
```
edge = resize(edge, edge.length);
```
instead of
```
resize(edge, edge.length);
```

---

