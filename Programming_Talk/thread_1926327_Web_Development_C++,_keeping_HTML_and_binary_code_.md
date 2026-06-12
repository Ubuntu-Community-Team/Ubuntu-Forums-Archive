---
title: "Web Development C++, keeping HTML and binary code separate?"
date: 2012-02-16
forum: Programming Talk
---

### Post by Lucky. on 2012-02-16
I've been developing with PHP for a few years now.  I use a general development pattern like so:

index.php = viewable page.  Contains 99% html code.  The other 1% loads up a controller page for processing, and the rest is echo statements to spit out variables amidst the HTML code.

cIndex.php = controller page.  Basically a class object with page-specific methods/variables and a main method which generates the variables that will be used in index.php.  It also loads up any other necessary objects for additional lifting.

I'd like to try C++ out for performance and stronger typing (my core competency is in C/C++ for desktop apps but never used it for web apps).

I'd rather keep my HTML code separate from my compiled C++ code (i.e. I don't want my page to be 100% hard coded with a zillion cout statements).  How do people approach this to combine rendered C++ output and HTML code? Have the program load the HTML text file and modify it with string find/replace statements?  That doesn't seem efficient but hey, maybe it's the way to go.

Just wondering if anybody else web develops with C++ and has a graceful way of keeping the HTML separate and manageable from the binary code.

---

### Post by Tony Flury on 2012-02-16
In theory the problem exists with any language - how do you keep the data separate from how the data is displayed.

In theory you should be using things like CSS to do this : your C++ application generates data that is marked up in some specific way (using divs and spans for instance) - in a perfect world your C++ app will generate XML, and the CSS is defined to describe how the various XML elements are actually displayed (or not) on the page.

---

