---
title: "[python] automaticly draw network/flow diagrams"
date: 2008-12-19
forum: Programming Talk
---

### Post by amar on 2008-12-19
My final year project involves writing a program to simulate flow conditions. I am getting on well with the project and am now able to input all my data and run the simulation.

The problem is that my flowsheet is just a set of units/nodes and with linking streams. This is very difficult to visualise in current table form.

My supervisor suggested attempting to dynamically create a graphic representation of the flowsheet similar to the image below.

[IMG]http://www.engineeringtoolbox.com/docs/documents/467/BFD.gif[/IMG]

Unfortunately I have no idea where to start with this one (or even the best terms to search for) - Has anyone got any suggestions of python librarys or other projects which would be able to help construct such an image?

Just to point out again, this is a small section of my project and I am encouraged (where possible) to inter grate other projects/code with my own

Thanks

---

### Post by Zugzwang on 2008-12-19
A standard tool for graph drawing is the "graphviz" tool suite. Have a look at their homepage. It contains a lot of examples. Maybe one of them is close to what you need.

---

