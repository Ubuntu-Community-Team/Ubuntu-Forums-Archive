---
title: "&quot;Semantic highlighting&quot;"
date: 2009-01-15
forum: Programming Talk
---

### Post by happysmileman on 2009-01-15
Warning, this post will probably be C++ specific, as will the technology (for now, and it's also likely there are other IDEs that do this already that I'm unaware of)

I've been looking at [this blog post]("http://zwabel.wordpress.com/2009/01/08/c-ide-evolution-from-syntax-highlighting-to-semantic-highlighting/") and find the highlighting shown there to be impressive.
Basically with regular highlighting, you get words like "int", "char" etc. highlighted one way, but "string" and "vector" and any other classes wouldn't.
Strings might be in one colour and numbers in another, but other than keywords and these types there's not much going on.

The highlighting shown here (semantic highlighting) aims to use highlighting all almost all parts of the code, to overall make things more readable, for example, member variables of a class will be in one colour, while global variables will be in another, functions will be highlighted, as will the names of objects (even user-created ones).
Local variables to a function will get a (partially) unique colour (Presumably much like IRC nick colours).
This way errors should be noticeable easily, for example if you misspell a variable name it doesn't get highlighted, if you spell it right it does, same with function names etc.

So what are your opinions?
Do you think this would make things easier and better or annoying and distracting?
Do you have any experience with highlighting like this? If so, what did you think?

---

### Post by mssever on 2009-01-15
> **happysmileman said:**
> So what are your opinions?
Do you think this would make things easier and better or annoying and distracting?
Do you have any experience with highlighting like this? If so, what did you think?
I'm not a C++ programmer, so I was quite surprised by how little highlighting was in the first example. I'm all in favor of semantic highlighting, though I'm not sure I would like to have variables of the same type colored differently from each other.

Back when I first learned HTML, I had an editor that allowed me to define highlighting by tag (so <table> was one color, <b> another, etc.). I really liked that feature, which I haven't seen since. Of course, since I no longer write spaghetti-coded HTML, I don't have as much of a need for that feature. But good syntax highlighting is essential IMO.

This is actually an area where Ruby shines. Ruby uses syntax to express much of its semantics, so it's easy to do the type of syntax highlighting you linked to in Ruby. So I guess I'm kind of used to it. Examples:
```
# note the leading @s
local_variable = 42
@instance_variable = "foo"
@@class_variable = "bar"
```

---

### Post by jimi_hendrix on 2009-01-15
i first started coding with visual C#...semantic highlighting...loved it...still do

---

### Post by escapee on 2009-01-15
Xcode has something very similar to this.  Having it in KDevelop or Kate would be awesome.

---

### Post by jimi_hendrix on 2009-01-15
any clue how to do it in vim?

---

### Post by mssever on 2009-01-15
> **jimi_hendrix said:**
> any clue how to do it in vim?
```
:syntax on
```

---

### Post by jimi_hendrix on 2009-01-15
i know that...it doesnt do sematic though

---

