---
title: "Pyclutter (python-clutter) examples, anyone?"
date: 2008-11-16
forum: Programming Talk
---

### Post by Mr. Picklesworth on 2008-11-16
After some extensive poking at options, it seems that Clutter is the best choice for me to render graphics within an application. I'm working on a "fun" hardware simulator (two words that I don't think have ever been said in the same sentence). One goal is to have reasonably attractive graphics. Of course, that graphics area has to be totally interactive, preferably in an easy way. I want to have little animated effects going on to demonstrate the flow of logic, zooming in on points to see more detail, room for angry robot add-ons, among other things. Straight Cairo (maybe with Gaphas examples from Labyrinth's source code) seemed likely candidates except that I haven't really seen plain Cairo doing any, err, "exciting" graphics. (Just really attractive functional 2D graphics; graphs, charts and the like).
Feel free to yell at me if I am wrong.

Anyhow, I am going with Clutter for now. Moreover, I am using Python to write this thing, so that means I am using Clutter's Python bindings! I can probably find my way around this using the articles on the C bindings, but it's always nice to have some native examples. Anyone know of Python programs that use Clutter, so I can download their source code?

Also, something that's bothering me: I notice that python-clutter in Ubuntu is at version 0.6.2 while Clutter itself is 0.8! Does it just have a weird versioning scheme?
Edit: Indeed, Ubuntu *is* [a bit behind]("http://www.clutter-project.org/sources/pyclutter/").

Oooh, and a download for PyClutter (as well as an example) here. Thanks!
[http://ubuntuforums.org/showthread.php?t=968962](http://ubuntuforums.org/showthread.php?t=968962)

So I guess this has become the "why Dylan should / should not use Clutter" thread, (sorry, I could have sworn I looked for that stuff to no avail before) although examples are still nice :)


Err, since the original point is completely lost, I officially reclassify this an *informative thread!*
Here are some examples to get going. First of all, I highly recommend downloading and installing pyclutter from source if you are going to be developing with it. Get it from clutter-project.org. Here is [a link to 0.8]("http://www.clutter-project.org/sources/pyclutter/0.8/") to get started.
Run the usual steps to compile and install. For the configure script, use this:
./configure --enable-docs --prefix=/usr/local
By default documentation is not installed. This way, DevHelp gets a shiny new PyClutter Reference Manual!

Some basic examples are right there in the sources you downloaded, in the directory named "examples".

---

