---
title: "GraphViz and Ruby in Eclipse"
date: 2009-01-06
forum: Programming Talk
---

### Post by Wtrz on 2009-01-06
Hi All,

for school i have to output a tree within a ruby application. I found out that graphviz is a suited toolkit for this task. 

[http://www.oreillynet.com/mac/blog/2005/10/graphviz_why_draw_when_you_can.html](http://www.oreillynet.com/mac/blog/2005/10/graphviz_why_draw_when_you_can.html)
[http://www.igvita.com/2007/04/16/decision-tree-learning-in-ruby/](http://www.igvita.com/2007/04/16/decision-tree-learning-in-ruby/)

I've installed Eclipse (with ruby), GraphViz, libgraphviz4 and libgv-ruby. When I use ```
require 'graphviz' 
``` the console shows: ```
no such file to load -- graphviz (LoadError)
```
I think i need to add the graphviz library to my project, but i can't figure out how to add the graphviz library to a ruby project. 
Can someone help me out?

---

### Post by Wtrz on 2009-01-09
I found the answer myself. After installing the graphviz package go to

[http://rockit.sourceforge.net/subprojects/graphr/](http://rockit.sourceforge.net/subprojects/graphr/) and download the tarball package

   1.  unpack tarball (if you haven't already)
   2. Run tests: ruby -I./lib tests/runtests.rb (OPTIONAL)
   3. Install: ruby install.rb 

Drag the 'graph' folder into the eclipse project. 
```

<%
        # Lets crank out a simple graph...
        require 'graph/graphviz_dot'

        # We create a DotGraphPrinter from some links.
        # In this simple example we don't even have a "real" graph
        # just an Array with the links. The optional third
        # element of a link is link information. The nodes in this graph
        # are implicit in the links. If we had additional nodes that were
        # not linked we would supply them in an array as 2nd parameter to new.
        links = [[:start, 1, "*"], [1, 1, "a"], [1, 2, "~a"], [2, :stop, "*"]]
        dgp = DotGraphPrinter.new(links)

        # We specialize the printer to change the shape of nodes
        # based on their names.
        dgp.node_shaper = proc{|n|
          ["start", "stop"].include?(n.to_s) ? "doublecircle" : "box"
        }

        # We can also set the attributes on individual nodes and edges.
        # These settings override the default shapers and labelers.
        dgp.set_node_attributes(2, :shape => "diamond")

        # Add URL link from node (this only work in some output formats?)
        # Note the extra quotes needed!
        dgp.set_node_attributes(2, :URL => '"node2.html"')

        # And now output to files
        dgp.write_to_file("public/img/g.png", "png") # Generate png file
      
%>
<img src="/img/g.png" />
```

The output is a png image.

Cheers, 

Wtrz

---

