---
title: "Intersection of 2 vectors in C"
date: 2010-03-25
forum: Programming Talk
---

### Post by Jacks0n on 2010-03-25
Hi,

I'm writing a game in C for a University course, and I'm stuck at a certain point. I have two single lines/vectors, and I store them in a linked list. How can I tell if they overlap at any stage? I have the starting and ending x and y coordinates of both lines/vectors.

I have NO idea where to go from here :-/. My initial ideas were to loop through (4 for loops?) manually and brute force to check every single coordinate and see if it matched the other line. But that was very ugly and I got stuck.

Another idea was to make an array of every single coordinate in each list, and compare lists and see if 1 coordinate matched. Except there's no tuples in C...

And I bet there's some relatively simple mathematical algorithm out there to determine if two vectors overlap, but I couldn't find one.

I know you can't code this for me, but does anyone know where to go from here? Hope that makes sense :-/.


Jackson

---

### Post by uljanow on 2010-03-25
[http://www.cppreference.com/wiki/stl/algorithm/set_intersection](http://www.cppreference.com/wiki/stl/algorithm/set_intersection)

---

### Post by MadCow108 on 2010-03-25
this is a rather standard problem and thus there are a ton of quite efficient algorithms
in the references of this page you might find some useful information
[http://en.wikipedia.org/wiki/Line_segment_intersection](http://en.wikipedia.org/wiki/Line_segment_intersection)

---

