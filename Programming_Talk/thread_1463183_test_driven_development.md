---
title: "test driven development"
date: 2010-04-26
forum: Programming Talk
---

### Post by mo.reina on 2010-04-26
can anyone give a good example of test driven development?  i've read the wiki entry, but can't seem to picture how it's applied to projects.  for example, if i wanted to write a text editor, or a small script/program to connect to a wireless access point, how is this method implemented to the design process?

i usually start coding by breaking things down into little pieces and testing the algorithms one by one, usually starting with the "core" process, then slowly putting in all the other things.  i remember we were taught to use flowcharts and pseudocode in school but i almost never do, i've started looking into design methods in the chance it may help me optimize the code i write (keep it simpler).

---

### Post by nmccrina on 2010-04-26
Test driven development is when you write the test first, and then add in the code that makes it pass.

For example, suppose you're making an airplane class for a flight simulator. You would think about it abstractly, and decide "If the throttle is advanced, the speed should increase". Then you write a test case to see if this is in fact what happens. Note that you haven't actually written any implementation code yet, so you're expecting it to fail. Then once you've written the test, you work on getting it to pass. 

The idea is that you aren't like "Oh, let's make an airplane class!" and start writing throttle methods and shooting methods and landing-gear toggle methods all at the same time. Instead, you write tests for minuscule bits of functionality and focus entirely on making each one pass before moving on to the next one.

---

### Post by mo.reina on 2010-04-27
yes ok, but can you give an example with code?  i understood the theory of the approach, i'm just not sure how to implement it... and it sounds like an approach that is used more with OOP than anything else, or have i misunderstood?

---

### Post by ssam on 2010-04-27
suppose you program has a text buffer, and a function like

insert_char(char character, int position)

then have a test that creates an empty buffer, and inserts a character. then check that the buffer now has that character in it.

---

### Post by mo.reina on 2010-04-28
so basically testing each function/class/loop individually, independently from the whole program.

---

