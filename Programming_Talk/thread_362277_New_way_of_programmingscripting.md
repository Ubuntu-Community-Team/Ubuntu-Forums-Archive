---
title: "New way of programming/scripting"
date: 2007-02-15
forum: Programming Talk
---

### Post by Darling on 2007-02-15
Well, I don't have a new way of programming, I'm looking for it ;-)
Now I finally saw a working example of what I've been looking for. 

[http://pipes.yahoo.com/pipes](http://pipes.yahoo.com/pipes)

Only, it's not on your computer, it's a web2.0 module. It's a cool idea but it would be soooo much more useful if it could just generate programs/scripts on your PC.
I don't know if this already exists, I've seen approaches that look like it, but they never seemed so intuitive as yahoo pipes.
If you have components like 
[LIST]
[*]wget
[*]cat
[*]grep
[*]sed
[*].....
[/LIST]
That could make simple scripting so much easier.

---

### Post by lnostdal on 2007-02-15
uhm, i don't think i understand the question - but i can try..

wget: [http://weitz.de/drakma/](http://weitz.de/drakma/)
cat: ..any programming language/environment can do this
grep: [http://weitz.de/cl-ppcre/](http://weitz.de/cl-ppcre/)
sed: well, cl-ppcre combined with already existing language elements can do this stuff

..i suppose you also need some way of parsing xml for rss and such, here's a couple: [http://www.cl-user.net/asp/tags/XML](http://www.cl-user.net/asp/tags/XML)

what i'm saying is that these things are already available in many programmirng languages/environments

..in any case you can call/use these tools from almost any language

---

### Post by WW on 2007-02-15
I think the "new way" that the original poster is talking about is the idea of "visual programming".  See, for example, [http://en.wikipedia.org/wiki/Visual_programming_language](http://en.wikipedia.org/wiki/Visual_programming_language)

---

### Post by lnostdal on 2007-02-15
Oh, that stuff :} .. I think it has been somewhat proven a long time ago that it only works for a limited set of tasks.

Dataflow is mentioned in the wikipedia-article. I once used an interesting music/sound-tool that allowed you to place a box representing the original signal (a "generator") on the screen. Then place effect-boxes around and adjust variables in them using sliders. Then make connections from the generator, to the effect-boxes and finally to an "output-box" which sent the result to my speakers. Yup; expressing visually how data is to flow at a high level works in some cases. :)

But the "content" of the boxes themselves had to be programmed in the usual way with code. You couldn't really create new types of boxes visually. 

Maybe the OP wishes for boxes that allows him to type in regex'es and do stuff similar to doing adjustments like I made in the effect-boxes using sliders. I think you'll eventually find that the lines or borders between text/code and what is or might be handy expressing visually are there for good reasons. The amount of clutter in a visual version would end up way worse than if it was expressed using text/code. Text/code can be incredibly expressive/terse/abstract -- in ways hard to express visually. The visual version would probably end up having more than 3 dimensions .. :}

So while adding certain sliders and options to the boxes could work, I wouldn't call it a "new way" replacing the "old way" of scripting/programming. It's just a "different way" that happen to work in some, but not all cases. :)

---

### Post by studiesrule on 2007-02-15
It looks like an interesting field. What OSS projects with the same have started so far? Anything worth mention?

---

