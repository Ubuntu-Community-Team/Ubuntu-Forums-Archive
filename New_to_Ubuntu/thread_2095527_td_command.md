---
title: "/td command"
date: 2012-12-17
forum: New to Ubuntu
---

### Post by jhuuht9 on 2012-12-17
My program plots me a graph of my data file if i use:

~/td filename

I want to plot two graphs in the same figure and the coding wouldn't work:

~/td 'file1' 'file2'

Could you tell me why it doesn't work and what does the /td command do?

---

### Post by Zill on 2012-12-17
> **jhuuht9 said:**
> My program plots me a graph of my data file if i use...Unfortunately, we are not mind readers.

You might improve your chances of getting help if you state *which* program (and version) you are referring to.  You should also state which version of Ubuntu you are using.

---

### Post by jhuuht9 on 2012-12-17
> **Zill said:**
> Unfortunately, we are not mind readers.

You might improve your chances of getting help if you state *which* program (and version) you are referring to.  You should also state which version of Ubuntu you are using.

im accessing linux servers on ubuntu or terminal, and I was given a data fileon my university's server.

I dont actually know which one im using, because I can do the same thing on ubuntu, terminal or Rxvt on windows, so im just using linuxes commands.

---

### Post by Wim Sturkenboom on 2012-12-17
> **jhuuht9 said:**
> **My program** plots me a graph of my data file
Parse the arguments and process them; see man getopt() and look for getopt examples for your specific programming language on the web.

---

### Post by jhuuht9 on 2012-12-17
that might be a bit tricky to explain, but i managed to make the graph I wanted on the gnuplot inside linux.

When I type:

gnuplot
plot 'file', 'file1'

But then I want to save the graph as a pdf file how could I do that?

---

