---
title: "Automation software: Any experience?"
date: 2011-12-04
forum: Programming Talk
---

### Post by Fracta on 2011-12-04
I am looking at various languages to do the task automation thing, and need help deciding which to use. These forums have always had a ton of users to help with other problems I've had, so I thought I would ask here first.
The basic purpose is to sit and wait for countdowns until access is granted to files and videos etc, and then downloading them and naming them correctly and keeping track of things etc.
I have used scripting languages like sikuli and autohotkey before, and they aren't up to this challenge (or in sikuli's case, I don't like it), so don't bother recommending those two.
The software needs to be able to do these things:
Loops
Methods, subroutines, anything modular! I HATE goto's. Messy code.
File manipulation
String interpretation etc (find "click here to continue")
Mouse and keyboard control

And these optional extras would be great:
Works in linux. Because I only really use windows for gaming.
gui creation. Not essential if I can use a different language as a frontend. I will be distributing the finished product to a few people that need guis.
Image recognition. this is actually more of an essential, for controlling things like downthemall and clicking play buttons.

Also, just mentioning the best automation software that runs in linux would be helpful, because working with sikuli was painful. Lots of hoop jumping. 

Thanks for your help

p.s. I just had a thought. Is it possible to code this all into an addon for firefox? Like download certain files from these links or all of the open tabs and click on play buttons etc? That would work in linux too.

---

### Post by trent.josephsen on 2011-12-04
> **Fracta said:**
> I am looking at various languages to do the task automation thing, and need help deciding which to use. These forums have always had a ton of users to help with other problems I've had, so I thought I would ask here first.
The basic purpose is to sit and wait for countdowns until access is granted to files and videos etc, and then downloading them and naming them correctly and keeping track of things etc.
I have used scripting languages like sikuli and autohotkey before, and they aren't up to this challenge (or in sikuli's case, I don't like it), so don't bother recommending those two.
The software needs to be able to do these things:
Loops
Methods, subroutines, anything modular! I HATE goto's. Messy code.
File manipulation
String interpretation etc (find "click here to continue")
Mouse and keyboard control

And these optional extras would be great:
Works in linux. Because I only really use windows for gaming.
gui creation. Not essential if I can use a different language as a frontend. I will be distributing the finished product to a few people that need guis.
Image recognition. this is actually more of an essential, for controlling things like downthemall and clicking play buttons.


It's interesting that you should ask that in Programming Talk because pretty much anything people talk about here meets those requirements.  GUI stuff and image recognition will need libraries in some cases, though.

Are you looking for the kind of thing that clicks the mouse and types for you to use other programs, or a more general purpose programming language?

---

### Post by Fracta on 2011-12-05
Exactly, I want to be able to write a program that uses other programs for me while I sleep, predominantly browsers. Move mouse, click buttons, type stuff. But it also needs to be more than a basic scripting language. Auto hotkey does not fit the role. If possible, I would like something low level. I am in love with ending each line of code with a semicolon.

---

### Post by trent.josephsen on 2011-12-05
Hmm, I'm not familiar with automation tools as such; my experience is mostly on a lower level.  Python/Perl type stuff (all the way down to digital logic).

I have to imagine that people have made Python modules to do this kind of thing, but a cursory Google search didn't bring up anything cross-platform.  [This](http://stackoverflow.com/questions/1946181/how-can-i-control-the-keyboard-and-mouse-with-python) stackoverflow question got some interesting responses you might want to look into.  Similarly, Perl searching brought up only Win32::GuiTest, which is not only obviously single-platform but looks to be maybe a bit more granular than what you're looking for.

Java has the java.awt.Robot class, which is designed to take control of the mouse and keyboard in what might be exactly the way you want.  I've used it before a little and found it pretty nifty, but I was already a fairly decent Java programmer at the time -- it might well be a bit overwhelming for someone with little prior experience.

Like I said, I specialize in programs that solve problems on a slightly lower level, so I don't know how closely these solutions could match what you're looking for.  Best of luck!

---

