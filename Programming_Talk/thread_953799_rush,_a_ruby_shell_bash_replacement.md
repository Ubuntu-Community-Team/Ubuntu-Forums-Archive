---
title: "rush, a ruby shell bash replacement"
date: 2008-10-20
forum: Programming Talk
---

### Post by rye_ on 2008-10-20
I noticed on rubyplus.org a screencast about a pure ruby unix shell, rush.
Has anyone tried this? Any comments?

[rush]("http://rush.heroku.com/")

I'm a real fan of ruby, and have always wondered why people learn a general purpose mainstream scripting langauge (python,perl,ruby) and bash concurrently.

---

### Post by geirha on 2008-10-20
I gave it a try just now since you mentioned it, by doing the following:
```
sudo aptitude install git-core rubygems
git clone git://github.com/adamwiggins/rush.git

```
And then to execute:
```

$ exec rush/bin/rush
rush> ls
Exception NameError -> undefined local variable or method `ls' for localhost:Rush::Box
   /tmp/rush/lib/rush/shell.rb:37:in `eval'
   /tmp/(eval):1:in `initialize'
   /tmp/rush/bin/rush:6:in `new'
   /tmp/rush/bin/rush:6
rush>

```

I haven't learnt ruby yet, so all of my initial tries gave errors :) The examples on the homepage worked though. A bit different way of doing things than sh/bash, that's for sure.

---

### Post by rye_ on 2008-10-20
yeah,  I must say that it's also taking me a bit of getting used to :confused:

---

### Post by metasoarous on 2010-01-18
Yeah, you can't just call ls or any random bash command form the main prompt. rush dispenses entirely with the idea of being in a specific directory at any given instant. You have to assign directories to variables and then you can call bash methods on the variables, sometimes in a straightforward manner, as is the case with ls. Others, you have to call directory.bash "ls" or whatever. I'm pretty new to it myself, but I'm pretty comfy with ruby so it's kind of exciting for me. It definitely has it's strengths and its weaknesses, but I kinda like it. For me personally though, I'm gonna have to fuss with it a bit before it will become as functional for me as I would need it to be to switch. (This largely has to do with having to manage ruby version with multiruby for stuff that I work on). I don't know where things were at when you folks were checking it out, but it has a pretty good guide now that will help you get oriented if you feel inclined. 

For me the biggest iffy bit is the directory thing. It has some definite advantages and definite weaknesses. It means you don't have to cd all over the place to be doing things that involve multiple directories or when you need to be switching back and forth between directories, but when all you really need to do is work in one, it can be a bit annoying. The cool part is that if you are a rubyist, the power of the language opens up so many cool possibilities for you. 

Anyway, I see this is an old thread but I thought that I would throw my two sense in.

Cheers

---

