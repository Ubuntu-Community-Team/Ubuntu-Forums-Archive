---
title: "A simple introduction to GUI with Ruby, anyone?"
date: 2008-11-16
forum: Programming Talk
---

### Post by howbag on 2008-11-16
Hey! I have desperately been looking for a gui-tutorial for Ruby, most of the stuff I find is rather hardcore. All I need is a dialogue box with some ruby-defined text, and a function happening when you press "ok" or similar.. and the source code ofc :), just to get me going.

I know some actionscript, and know how to do stuff in flash, but been wanting to try it in ruby.

Anyone knows of something like this?

---

### Post by Majorix on 2008-11-16
Look here:
[http://www.fxruby.org/](http://www.fxruby.org/)

---

### Post by Phenax on 2008-11-16
[http://shoooes.net/](http://shoooes.net/)

It's not just a gem, it's a full distro of Ruby. But it is fantastically easy.

---

### Post by rye_ on 2008-11-16
I agree with shoes, it's really excellent.

---

### Post by Sorivenul on 2008-11-16
> **Majorix said:**
> Look here:
[http://www.fxruby.org/](http://www.fxruby.org/)
+1

Outside of that, a simple Tk interface may work as well:
*[From the Ruby-Doc website]("http://www.ruby-doc.org/docs/ProgrammingRuby/html/ext_tk.html")
*[A Ruby/TK tutorial]("http://members.chello.nl/k.vangelder/ruby/learntk/")
*[Another Ruby/Tk tutorial]("http://rubylearning.com/satishtalim/ruby_tk_tutorial.html")

I've never used Shoes, so I can't vouch for it, try it is you wish, I guess.

---

### Post by howbag on 2008-11-16
I got myself the shoes manual (looks like its made for kids. kudos.) and am getting into that first :) maybe Ill have a look at the fxruby and the tk-thing when I'm pro-er (that's the new word for tonight) Thanks guys! :D

---

### Post by stevescripts on 2008-11-17
Nice tutorial on using Tk with Ruby:

[http://www.tkdocs.com/tutorial/index.html](http://www.tkdocs.com/tutorial/index.html)

Includes using Tk with Tcl, Ruby and Perl.  Python coming
before long.

Hope this helps a bit.

Steve
(who has enjoyed tinkering with RubyTk a bit)

---

### Post by stevescripts on 2008-11-17
Finding a few minutes after lunch, a simple example:

```

#! /usr/local/bin/ruby

require 'tk'

def plus1(var)
 var = var + 1
end

$result = TkVariable.new(0)

plus = TkRoot.new() { title 'PlusOne' }

lbl = TkLabel.new(plus, 'textvariable'=> $result, 'foreground'=>'red', 'width'=>10).grid('row'=>0, 'column'=>0)

btn = TkButton.new(plus) {text'Add 1'; command {$result.value = plus1($result)}}.grid('row'=>0, 'column'=>1)

plus['resizable'] = false, false

Tk.mainloop
```

Note, that the link I posted earlier to the tkdocs website, focuses
on tcl/tk 8.5, which includes the new tile widgets - there is documentation
on that site, which will tell you how to install and use Tk 8.5 with Ubuntu.

The code above works with a default tcl/tk and Ruby install on Ubuntu
Gutsy.

Hope this helps a bit.

Steve

---

### Post by howbag on 2008-11-17
TK looks more strict and organized imo. After using shoes, i get the impression that the little use of curly brackets just adds to the confusion. I did manage to make a imagemagick-program tho :guitar:

Will check out tk aswell, thanks.

---

### Post by Phenax on 2008-11-17
> **howbag said:**
> TK looks more strict and organized imo. After using shoes, i get the impression that the little use of curly brackets just adds to the confusion. I did manage to make a imagemagick-program tho :guitar:

Will check out tk aswell, thanks.


You are misinterpreting a stylistic ruby feature for something Shoes-centric. In ruby, you can either do something like:

```

Shoes.app { 
  button "PUSH!"
}

```
or
```

Shoes.app do
  button "PUSH!"
end

```

It's the same thing, and you can do it with vanilla Ruby too. The author of Shoes just tends to use brackets sometimes.

---

