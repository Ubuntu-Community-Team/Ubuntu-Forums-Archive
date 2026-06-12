---
title: "Python Challenge 4: Lists Part 1"
date: 2007-08-14
forum: Programming Talk
---

### Post by yuvlevental on 2007-08-14
According to the info on the site in my sig, create a program where there are 5 objects: Mercury, Venus, Earth, Mars, and Jupiter. When you type in ‘1&#8242; in a prompt, it returns ‘Mercury’, ect. Email the answer to yuval [dot] imperius [at] gmail [dot] com.

---

### Post by gnuman on 2007-08-14
Careful about that webpage you're refering to: the author is not using the correct formatting for Python code--in particular he is not indenting his code after colons.

His "challenge" is very easy.  Here I thought you were asking about the actual Python Challenge Level 4 (see [http://www.pythonchallenge.com/](http://www.pythonchallenge.com/) ).

try this:

[HTML]
#!/usr/bin/env python
# simple list program

planets=("Mercury","Venus","Earth","Mars","Jupiter")

choice=int(input("Which planet would you like?"))


print planets[choice-1]

raw_input("Press Enter to exit this program")

[/HTML]

---

### Post by yuvlevental on 2007-08-14
It's actually my blog; I would indent, but the Wordpress engine erases whitespace in a blockquote for some reason. Also, the challenges are really there to see if people can understand what I'm saying. Oh yeah, I credited you on my forums with your ubuntuforums username. I owe you 40 forum credits, If you want them, you need to register and PM me.

---

### Post by ryanoz on 2007-08-15
Maybe this page would be of some help: [http://codex.wordpress.org/Writing_Code_in_Your_Posts]("http://codex.wordpress.org/Writing_Code_in_Your_Posts")

---

### Post by gnuman on 2007-08-15
> **yuvlevental said:**
> It's actually my blog; I would indent, but the Wordpress engine erases whitespace in a blockquote for some reason. Also, the challenges are really there to see if people can understand what I'm saying. Oh yeah, I credited you on my forums with your ubuntuforums username. I owe you 40 forum credits, If you want them, you need to register and PM me.

I work with students learning to program.  The challenges like the one you posted are more appropriate for true beginners in Python, you're correct about that.  The Python Challenge is really tough and is more aimed at programmers who are new to Python and want something to get them more familiar with all the modules.

I have written up some simpler challenges myself for high school students learning Python.

Keep up the blog!:)

---

### Post by LaRoza on 2007-08-15
> **yuvlevental said:**
> It's actually my blog; I would indent, but the Wordpress engine erases whitespace in a blockquote for some reason. Also, the challenges are really there to see if people can understand what I'm saying. Oh yeah, I credited you on my forums with your ubuntuforums username. I owe you 40 forum credits, If you want them, you need to register and PM me.

Are you allowed to use entities? &nbsp; is a non-breaking space.

---

### Post by yuvlevental on 2007-08-15
I didn't think about that, but ok

---

