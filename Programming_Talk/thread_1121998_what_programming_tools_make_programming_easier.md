---
title: "what programming tools make programming easier?"
date: 2009-04-10
forum: Programming Talk
---

### Post by docesam on 2009-04-10
i would like to start a new programming project (employee affairs program) , and i don't 

mind to start learning a new language with it ( i used to program in visual basic 6 and know 

some c++ and java) .

So i need a solution that will meet the following criteria :

1) easy ,rapid,functional programming (do more with less code but still can do anything i 

want for the type of programs mentioned above) 
2) the source code should work in windows and linux alike(cross platform).
3) the solution should be able to easily connect to mysql , make 2D graphs and input 

images from scanner.
4) i want to design my GUI visually not in code.
5) full support for international languages and right-to-left reading order in all aspects ( 

controls ,graphs,reports ... etc)

so : what programming language / editor / tools / libraries will be the best for that ?

.NET ? java ? python ? others ?
i don't mind using open or closed source tools alike
 
thanks for help

---

### Post by cph05a on 2009-04-10
My personal favorite is Eclipse. I use it for java, c, and c++, but they have plugins for other programming languages and other development tools as well. 


Other than that, netbeans is cross platform and has a visual designer for java (but I don't personally care for netbeans). QT is also cross platform and has a visual designer for C++.

---

### Post by docesam on 2009-04-11
i think we should think about choosing a programming language ,and the reason why we choose that particular language is important

---

### Post by MicahCarrick on 2009-04-11
If you want ease of use and RAD, my vote would be Python + GTK (pyGTK) using the Glade Interface Designer. Nice thing with using Glade, is that if you decide you want to use C or C++ instead of python to implement that interface, you don't have to changed the GUI design, just the code implementing said design.

Since you have VB experience, here's a little article that discusses VB's form editor versus Glade. It's a bit dated and uses C instead of Python (python will be a bit quicker and easier to code with but C is still my "go-to" language for some types of projects). [VB Programmers Intro to Linux Programming with GTK+]("http://www.micahcarrick.com/08-19-2006/vb-in-linux-with-gtk.html")

---

### Post by rich1939 on 2009-04-11
> **MicahCarrick said:**
> If you want ease of use and RAD, my vote would be Python + GTK (pyGTK) using the Glade Interface Designer....

I agree with Micah about using Glade and GTK+. I'm not familiar with Python and use C, but the combination of Glade and GTK+ is very powerful and easy to use.

I'm currently building a fairly complex cross-platform application with many top-level windows and a PostgreSQL backend using Glade, GTK+ and C. I'm sure that Python would be a good language choice if you don't want to use C or C++.

---

