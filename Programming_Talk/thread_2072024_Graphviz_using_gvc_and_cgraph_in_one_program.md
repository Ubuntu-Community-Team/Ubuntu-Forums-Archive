---
title: "Graphviz using gvc and cgraph in one program"
date: 2012-10-16
forum: Programming Talk
---

### Post by csnafu on 2012-10-16
Hi!
I'm trying to produce a visualization of a graph with graphviz. I have no problems generating a graph with libcgraph (or even the libgraph), the problem occurs when I want to create an image as well using libgvc. As soon as I use both functions from libcgraph (or libgraph) and libgvc I get a segfault when calling gvContext().

Sample code:
```
#include <stdio.h>

#include <graphviz/gvc.h>
#ifdef WITH_CGRAPH
# include <graphviz/cgraph.h>
#else
# include <graphviz/graph.h>
#endif

int main(int argc, char **argv)
{
    GVC_t *gvc;
    Agraph_t *g;
    Agnode_t *t, *h;

#ifdef WITH_CGRAPH
    g = agopen("test", Agdirected, NULL);
    printf("agopen %p\n", g);
    t = agnode(g, "a", 1);
    h = agnode(g, "b", 1);
    agedge(g, t, h, "x", 1);
#else
    aginit();
    g = agopen("test", AGDIGRAPH);
    printf("agopen %p\n", g);
    t = agnode(g, "a");
    h = agnode(g, "b");
    agedge(g, t, h);
#endif

    FILE *f = fopen("foo.dot", "w");
    agwrite(g, f);
    fclose(f);
    agclose(g);

    gvc = gvContext();
    printf("gvContext %p\n", gvc);
    gvLayout(gvc, g, "dot");
    printf("gvLayout\n");


    return 0;
}
``````
$ pkg-config libcgraph --cflags --libs
-I/usr/include/graphviz  -lcgraph -lcdt  
$ pkg-config libgvc --cflags --libs 
-I/usr/include/graphviz  -lgvc -lgraph -lcdt
$ gcc foo.c -o foo -DWITH_CGRAPH `pkg-config libcgraph libgvc --cflags --libs`
$ ./foo
agopen 0x956d050
Segmentation fault (core dumped)
```I've been trying to resolve this for hours now and couldn't find anything useful. All posts and tutorials I can find are all using libcgraph or libgraph only and not also libgvc.

libgvc requires libgraph but even if I rewrite the program to use libgraph it crashes (although then it crahes at gvLayout).
Does anybody know how this stuff works? I've only done my first graphviz stuff today so I'm not too familiar with all this.

```
$ uname -a
Linux mybox 3.2.0-32-generic #51-Ubuntu SMP Wed Sep 26 21:32:50 UTC 2012 i686 i686 i386 GNU/Linux
$ dpkg -l | grep -E "libgraph|libcgraph|libgvc|libcdt"
ii  libcdt4                                2.26.3-10ubuntu1                           rich set of graph drawing tools - cdt library
ii  libcgraph5                             2.26.3-10ubuntu1                           rich set of graph drawing tools - cgraph library
ii  libgraph4                              2.26.3-10ubuntu1                           rich set of graph drawing tools - graph library
ii  libgraphicsmagick3                     1.3.12-1.1build1                           format-independent image processing - C shared library
ii  libgraphviz-dev                        2.26.3-10ubuntu1                           graphviz libs and headers against which to build applications
ii  libgvc5                                2.26.3-10ubuntu1                           rich set of graph drawing tools - gvc library
```

---

### Post by csnafu on 2012-10-19
Could at least someone compile this and tell me if it segfaults for him as well?

---

### Post by glennric on 2012-10-19
I compiled it.  It segmentation faults for me to.  A backtrace shows that it is from your agopen call.  I haven't looked any deeper than that though.

---

### Post by glennric on 2012-10-19
Actually, I didn't look close enough.  I get the same crash points as you do.

---

