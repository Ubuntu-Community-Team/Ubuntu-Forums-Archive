---
title: "Recursion: real world use"
date: 2009-09-19
forum: Programming Talk
---

### Post by andrew222 on 2009-09-19
I would like to know how some people have used Recursion to solve problems in large sized projects.

---

### Post by Bachstelze on 2009-09-19
An example of recursive algorithm is [QuickSort]("http://en.wikipedia.org/wiki/QuickSort"). I hope you can see how sorting an array can help solving problems. ;)

---

### Post by jpkotta on 2009-09-19
Anything involving trees.  Here is a function I made for dumping octave structs to strings, for printing them to a file.  

```

function retstr = struct2str(thestruct, structname)

    str = cell();
    retstr = cell();
    
    for [val,key] = thestruct
        if isstruct(val)
            str = struct2str(val, key);
            for s = 1:length(str)
                retstr{end+1} = str{s};
            end
        else
            retstr{end+1} = [key ' = ' mat2str(val) ';'];
        end
    end
    
    if nargin == 2
        for s = 1:length(retstr)
            retstr{s} = [structname '.' retstr{s}];
        end
    end

```

---

### Post by hessiess on 2009-09-19
Creating iteration in functional languages.

---

### Post by Reiger on 2009-09-19
Why large sized projects, though? Anyways, to get an idea of what would not be possible without recursion: CSS & XPath, tree/Graph based file systems. Presenting a tree or walking a graph, as tree or graph is inherently recursive. Also search & path finding algorithms are typically recursive: find a path to Z from X typically involves finding a path from X to Y and then to Z, which boils down to two calls to the same algorithm: find a path between X & Y as well as a path between Y & Z.

---

### Post by MadMan2k on 2009-09-19
> **Reiger said:**
> Anyways, to get an idea of what would not be possible without recursion: CSS & XPath, tree/Graph based file systems.
you can _always_ re-write an algorithm without recursion, so this is not true ;)

---

### Post by MadCow108 on 2009-09-19
no you can always rewrite an iteration into a recursion but not the other way round (at least not without nullifying the advantage of iteration).
Examples would be the stated quicksort or tree traversals.
recursions which can be rewritten in iterations are called tail recursions.

---

### Post by escapee on 2009-09-19
> **MadCow108 said:**
> no you can always rewrite an iteration into a recursion but not the other way round (at least not without nullifying the advantage of iteration).
Examples would be the stated quicksort or tree traversals.
recursions which can be rewritten in iterations are called tail recursions.
It is possible to write Quick Sort w/o recursion, Google will come up with a few results for you.  Of course, this is not to say that this is optimal or recommended.

---

### Post by elbarto_87 on 2009-09-20
I was under the impression that any tail recursive function can be easily translated into a iterative function with a loop.

[http://en.wikipedia.org/wiki/Tail_recursion](http://en.wikipedia.org/wiki/Tail_recursion)

If the function is not tail recursive, the stack would have to be emulated in order to represent the recursive problem with an iterative function?

Regards Elbarto

---

### Post by nvteighen on 2009-09-20
Ok, this is nonsense. Recursion is related to project size exactly like addition is or whatever algorithm you know is too. Heck... Recursion is a way to write stuff... Iteration too... Man, sometimes you need recursion and sometimes you need a sandwich :P

---

### Post by NovaAesa on 2009-09-20
I use recursion all the time (especially in the algorithmics course I'm doing). The divide and conquer approach works quite well for many problems, and has recursion as its main focus. Look up the deficient tiling problem if you are interested (it's the 'hello world' of divide and conquer).

Also, anything that is recursive can be re-written iteratively - you will need one or more stacks though! (unless you are talking tail-recursion).

---

### Post by Reiger on 2009-09-20
> **nvteighen said:**
> Ok, this is nonsense. Recursion is related to project size exactly like addition is or whatever algorithm you know is too. Heck... Recursion is a way to write stuff... Iteration too... Man, sometimes you need recursion and sometimes you need a [S]sandwich[/S] coffee :P

Here fixed that for you.

---

### Post by Reiger on 2009-09-20
> **MadMan2k said:**
> you can _always_ re-write an algorithm without recursion, so this is not true ;)

That is not what I meant. On the level of algorithms you are more or less[*] right: implement you own stack and you can do recursion by simply iteratively pushing/popping execution-frames.

It is however fundamentally different from the fact that CSS, XPath and tree/graph structures present themselves as recursion incarnate: that is, they are structured in such a way a user *must* have a mental model of the recursion in order to be able to use them... and they derive all their conceptual richness & real-world applications from that mental model of recursion.

It is "a way of thinking", a "paradigm" if you will that file systems make distinction between folders (recursive definition) and files (base case definition). A folder is made up of: sub-folders or files (or both).

Recursion has this neat "encapsulation" mechanism where at any state of execution/traversal all you have to do is concern yourself with "the place where you currently are", you can ignore "the place you just were previously" and "the place you will be next" while you are "here". Without the relaxed attitude towards tree-traversal or graph traversal things like routing algorithms and CSS/Xpath would be an awful lot more hairy: read, you would have to implement (keep in mind) the stack of frames that are yet to come...

[*] Some network routing algorithms are a bit hairy for that stack based stuff though. Especially when, theoretically, the stack may have to be infinitely large because there is no clear base-case definition (there is no clear definition of when the optimum paths have been calculated because at each node this depends on the other nodes which may or may not yet be in their optimum configuration).

---

