---
title: "widget for drawing graphs (nodes and edges)"
date: 2008-06-20
forum: Programming Talk
---

### Post by castudil on 2008-06-20
hey!

I need to build an application that visually manage graphs. This should consider heavy amount of nodes and edges.

I was considering the QT interface since I already have written most of my code in C++.

In the forums I've found TULIP, seems good and even I did some small programs, but the in the documentation, the section "TULIP and QT DESIGNER" is empty :( , so I was wondering if someone has used TULIP in the QT environment and can give me some insights on how to proceed, since TULIP is the best package I have seen for now

I guess someone knows this, because both TULIP and QT4.3.4 as well as QT Designer are part of the Ubuntu 8.04 - HARDY HERON distribution

or... do you know a better widget/package for this purpose?


Thanks guys for this forum, It has been of great help when I am in trouble

---

### Post by kknd on 2008-06-23
I used graphviz some time ago, to draw graphs.

My program called graphviz to generate an image file, and then the image was loaded into the app.

---

### Post by Zdravko on 2008-06-23
Update: 24.09.2008: new class interface and a few features were added for convenience.
Multiple graphs can be constructed and even rendered to different formats with no problems.

I have used the C-binding of Graphviz successfully! It works very well and produces nice graphs.
I made an incomplete but neat C++ wrapper for Graphviz. It could be used like that:
[php]
#include "graphviz.hpp"

using namespace zm::graphviz;

void test_automat()
{
    graph g;
    g.set("rankdir", "LR")
        .set_nodes("shape", "circle")
        .set_nodes("fixedsize", "true")
        .set_nodes("width", "0.6");
        
    node n1 = g.add_node("");
    n1.set("shape", "plaintext");
    node n2 = g.add_node("S");
    g.add_edge(n1, n2);
    
    n1 = g.add_node("d");
    g.add_edge(n2, n1).set("label", "p");
    n1 = g.add_node("r");
    g.add_edge(n2, n1).set("label", "q");
    
    n2 = g.add_node("E");
    n2.set("shape", "doublecircle");
    g.add_edge(n1, n2).set("label", "m");
    n1 = g.add_node("d");
    g.add_edge(n1, n2).set("label", "v");
    g.add_edge(n2, n2).set("label", "*");
    
    g.render("automat.png");
    g.render("automat.pdf", format::PDF);
}

void test_hierarchy()
{
    graph g;
    g.set("rankdir", "TB")
        .set_nodes("shape", "plaintext");

    node n1 = g.add_node("fats");
    node n2 = g.add_node("saturated");
    g.add_edge(n1, n2);
    
    node n3 = g.add_node("animals");
    g.add_edge(n2, n3).set("style", "dashed");
    
    n2 = g.add_node("unsaturated");
    g.add_edge(n1, n2);
    
    n1 = g.add_node("polyunsaturated");
    g.add_edge(n2, n1);
    
    n3 = g.add_node("monounsaturated");
    g.add_edge(n2, n3);
    
    g.add_edge(n3, g.add_node("olive oil")).set("style", "dashed");
    
    n2 = g.add_node("w-3");
    g.add_edge(n1, n2);
    
    n3 = g.add_node("w-6");
    g.add_edge(n1, n3);
    
    g.add_edge(n2, g.add_node("flax oil")).set("style", "dashed");
    g.add_edge(n2, g.add_node("fish")).set("style", "dashed");
    
    g.add_edge(n3, g.add_node("sunflower")).set("style", "dashed");

    g.render("hierarchy.png");
    g.render("hierarchy.pdf", format::PDF);
}

int main() {
    test_automat();
    test_hierarchy();
}

[/php]You can have a look at the output from this sample application (see the attachment).
Here is the interface in my header graphviz.hpp:
[php]
#ifndef GUARD_GRAPHVIZ_HPP
#define GUARD_GRAPHVIZ_HPP 1

namespace zm {
    namespace graphviz {
        
        class node;
        class edge;
        
        namespace edges {
            enum type {
                DIRECTED,
                DIRECTED_STRICT,
                UNDIRECTED,
                UNDIRECTED_STRICT
            };
        }
        
        namespace layout {
            enum type {
                DOT,
                NEATO,
                FDP,
                TWOPI,
                CIRCO
            };
        } 

        namespace format {
            enum type {
                DOT,
                GIF,
                PDF,
                PLAIN,
                PNG,
                PS,
                PS2,
                SVG
            };
        }
        
        class graph {
            struct impl;
            impl* pimpl;
            graph(const graph&); // delete
            graph& operator=(const graph&); // delete
        public:
            graph(edges::type E = edges::DIRECTED,
                layout::type L = layout::DOT);
            ~graph();
            node add_node(const char* label);
            edge add_edge(const node&, const node&);
            void render(const char* name,
                format::type T = format::PNG);
            graph& set(const char* key, const char* value);
            graph& set_nodes(const char* key, const char* value);
            graph& set_edges(const char* key, const char* value);
        };
        
        class node {
            struct impl;
            impl* pimpl;
            node(impl*);
            friend class graph;
        public:
            node(const node&); // construct a new node
            node& operator=(const node&); // reassign current node
            ~node();
            node& set(const char* key, const char* value);
        };
        
        class edge {
            struct impl;
            impl* pimpl;
            edge(impl*);
            friend class graph;
            edge& operator=(const edge&); // delete
        public:
            edge(const edge&);
            ~edge();
            edge& set(const char* key, const char* value);
        };
        
    } // namespace zm
} // namespace graphviz

#endif

[/php]In case someone here is interested, I can share the implementation.

---

### Post by rotulet on 2008-11-25
hello,
I am looking for the same kind of visualization, but I was not enable to find a good solution. The last version of Tulip with the GlMainWidget object failed to work properly. I also need to have interactions/callbacks with the node and the edge of the graph ... :/ 

Did you find a good way to do Tulip working or perhaps, something totally different ?

Thanks,
Rot Ulet.

---

### Post by ricardo_arango on 2009-12-25
> **Zdravko said:**
> In case someone here is interested, I can share the implementation.
 
Hi, I am interested in your implementation of the drawing with graphviz. I basically have to draw an n-ary tree, I think what you have done could be useful.

---

### Post by Elfy on 2009-12-26
closed - severe case of necromancy

---

