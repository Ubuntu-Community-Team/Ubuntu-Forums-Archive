---
title: "Advice: Laying Code Out/Designing before Starting"
date: 2015-04-16
forum: Programming Talk
---

### Post by Nexusx6 on 2015-04-16
Hi everyone, 

I find myself caught in this terrible habit a lot: I start a project knowing what needs to get done, write out the basic functionalities, and then as the code gets more complex, re-write my functions to either expand or break them apart. This happens every time, and it's beginning to annoy me to no end. I'm wasting a lot of time having to refactor code because functions change, and so does there name, and/or make lots of changes because function outputs evolve, and so the functions that take the input must also. It feels sloppy, and is huge waste of time. 

I know this happens to a lot of coders so I'd love to hear advice from the field or be directed to papers written on how you guys go about white boarding program flow before you get started. Does this practice have a google-able name? How do you know what functions you're going to need, and what exactly their I/O's should be? When I first started programming, I vaguely remember being told that, if I were to write a paragraph describing the program, verbs would be functions, and nouns would be classes. Is this still along the lines of how the community lays it's code out, before hitting the keyboard?

---

### Post by ofnuts on 2015-04-18
OO design and IDEs and automated unit tests have been made to make refactoring easy and safe. The "agile" principles also mean that whatever your original design is, it will be invalidated by the harsh reality and need rework. Nobody gets it right the first time anyway. Which doiesn't mean that you souldn't hava  prelilinary design phase of course... but take its wih a grain of salt(*)...

And it all depends on the total elapsed time.... If you spend more time (over-)designing your app to avoid refactoring than you would with a lighter design phase and doing the refactoring, where is the gain? 

(*) I once participated in a project where, before writing the first lne of code, the database model was supposedly cast in concrete, so much that there was was no "database" category in the bug tracker...  This obviously didn't last long.

---

