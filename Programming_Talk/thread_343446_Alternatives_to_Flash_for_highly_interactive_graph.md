---
title: "Alternatives to Flash for highly interactive graphical web design"
date: 2007-01-21
forum: Programming Talk
---

### Post by WebDrake on 2007-01-21
Hello all,

Some years ago I was involved in a research project where my colleagues and I asked people to play a game on a website, and measured behaviour.  After some trials with a rather dodgy PHP setup that generated JPG files (which had to be reloaded at each step of the game....) we switched to using Flash for the game interface.

The problem was that we had to present a graph that measured a player's performance in the game, and reacted in real-time to their actions.  We also had to ensure that players were not cheating, that they could not go back and "correct" a wrong action.

Flash let us set up a very pretty interface, but I am wondering if there is an alternative way to achieve this that does not involve using a proprietary format.  I would prefer not to use a Java applet [open-source since ... how long?] since in my experience they look horrible and ugly....

Any suggestions?

Many thanks,

     -- Joe

---

### Post by Grey on 2007-01-21
Java or Flash would be the easiest way of accomplishing this.  And if it works for you, then it's probably not worth rewriting it.

But I would personally just do it with AJAX.  It's a lot more powerful than people give it credit.  I've been using it since before there was a word for AJAX.  It's similar to your dodgy solution with PHP, but it uses JavaScript for all logic, and doesn't refresh the page.  It just queries a page on the server, and returns the results to the client.

---

### Post by 23meg on 2007-01-21
You can do pretty good interaction handling and animation using Javascript / AJAX. Ready made toolkits such as Dojo, Script.aculo.us etc. can make the job easier.

---

### Post by WebDrake on 2007-01-21
Cool, thanks for the suggestions---I shall have to look into Ajax. :KS 

Rewriting the thing is on the cards anyway; we are creating a new version, and it would be nice to do something that is "open" rather than something locked away.  At the moment I'm working on a new version (from scratch---the old stuff was crap:)) the underlying simulation code that the website talks to.

---

### Post by bbharatsony on 2008-04-05
Try going to 

[http://code.google.com/more/#label=ProductsAll&product=ajax](http://code.google.com/more/#label=ProductsAll&product=ajax)

Google has a lot of APIs

If you want your games to run offline then try Google Gears

---

