---
title: "From Bash to Ruby - Some questions"
date: 2008-02-18
forum: Programming Talk
---

### Post by Yuzem on 2008-02-18
I know a little bash and I like it. I even did a little [app]("http://ubuntuforums.org/showthread.php?t=486359") with it.
Now I want to make a program with gui using gtk.
The best option for me would be to use gtk from bash because bash is what I know, so I installed [gtk-server]("http://www.turtle.dds.nl/gtk-server/index.html") but for some reason it is very ugly. The widgets doesn't use the current theme.
Maybe I am doing something wrong...

Anyways, I am thinking of learning some ruby now and I have some questions, but first, be advice that I am not a programmer so I could be talking some nonsenses...

**First a simple question:**
How do I include another file in ruby?
In bash it is:
```
. /path/to/file
```
In bash that will import the file as if it were part of the script.

**Second question**
In ruby I can use bash commands like this:
```
var = `cat some_file`
```
That assigns the result to a variable named var.
How can I use that variable inside a bash command from ruby.
For example:
```
var = `echo $var | sed "s/something/something/"`
```
That doesn't work.

**Pipes**
How can I do pipes in ruby?

In bash:
```
echo $var | do-something | do-something-else
```

In ruby the following works in the same order as pipes in bash (from left to right):
```
var.do-something.do-something-else
```

The same in bash would be:
```
do-something-else $(do-something $var)
```

Maybe in python:
```
do-something-else(do-something($var))
```

---

### Post by ghostdog74 on 2008-02-18
The most logical thing to do, if you want to learn Ruby, or any other new languages you don't already know, is to at least read up some books or online guide about how to use and program in them, right?

---

### Post by Jessehk on 2008-02-18
The first edition of the "Pickaxe" Book, widely considered the best reference/tutorial for Ruby is available free [here](http://www.rubycentral.com/pickaxe/).
It is slightly out of date, but 95% of it should be relevent.

Before you're confronted with the various people telling you to look at Python instead, let me just say that if you're curious about what other languages have to offer, investigate them and make your own choice based on what appeals to you.

EDIT: answers to the first 2 questions (I don't think there was a question in that third point):
```

# . /path/to/file
require "path/to/file"

# var = `echo $var | sed "s/something/something/"`
# the "!" means that the current variable is modified in place
var.sub!(/something/, "something")

# expressions substitution in strings
name = "Joe"
puts "Hello #{name}!"

```

EDIT2: Adding Python code for comparison...
```

import re

var = re.sub(re.compile(r"/something/"), "something", var)

name = "Joe"
print "Hello %s!" % name

```

---

### Post by Yuzem on 2008-02-19
Thanks for the answers.
I already read some tutorials about ruby.
I thought that "require" was only for modules.

I test it and it isn't working for me.

file1:
```
#!/bin/ruby

require "/home/user/AsD/hello"

puts "bye"
```

file2:
```
puts "hello"
```

If I run file1 I get:
```
./bye:3:in `require': no such file to load -- /home/user/AsD/hello (LoadError)
        from ./bye:3
```

If I do the same in bash I would expect:
```
hello
bye
```

About the second question:
I want to be able to use bash commands inside ruby because I already know a lot of this commands.
I can assign the result of this commands to a variable but I want to know how to pass this variable back to this commands.
For example:
```
list = "some_list"
list_head = `echo list | head`
```

Which brings me to the last question about pipes to do something like:
```
list = "some_list"
list_head = puts list | `head`
```
In that way I could pass a variable to a bash command.
When I say pipes I mean connecting the STDOUT of a command with the STDIN of another command.
The question is:
How can I do pipes in ruby?
I have searched but didn't found anything.

Thanks in advance.

---

### Post by pmasiar on 2008-02-19
> **Jessehk said:**
> Before you're confronted with the various people telling you to look at Python instead,

That would be me :-)

>  let me just say that if you're curious about what other languages have to offer, investigate them and make your own choice based on what appeals to you.


Easiest way to "investigate" languages without actually learning them is to compare solution for a simple enough problem. Printing "Hello world" shows that Ruby is simpler than Java or C++ but does not show difference compared to other dynamically typed languages, like mentioned Python. Check [http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/) to get better feel for the language you are about to learn.

And in case you are curious: Yes, Python does have more libraries than Ruby, even if the gap is improving.

---

### Post by ghostdog74 on 2008-02-19
@OP , if you still can't find an answer, you can try posting to comp.lang.ruby. Other than those "genuinely trying to solve your real problem" posts, you can forget about the rest.

---

### Post by Yuzem on 2008-02-19
> **pmasiar said:**
> Easiest way to "investigate" languages without actually learning them is to compare solution for a simple enough problem. Printing "Hello world" shows that Ruby is simpler than Java or C++ but does not show difference compared to other dynamically typed languages, like mentioned Python. Check [http://99-bottles-of-beer.net/](http://99-bottles-of-beer.net/) to get better feel for the language you are about to learn.
I have read some tutorials on using the gtk libraries and it seems simpler to do it with ruby than with python.
Thats the reason I chose ruby.
Of course I could be wrong...

> **ghostdog74 said:**
> @OP , if you still can't find an answer, you can try posting to comp.lang.ruby. Other than those "genuinely trying to solve your real problem" posts, you can forget about the rest.
Ok, I will probably do that if nobody has an answer here.

I have found the problem with the first question.
It seems that for some reason it doesn't work on an ntfs partition.
I move the script to ext3 and it worked as you said.
The following page explains the difference between "require" and "load":
[http://ruby.about.com/od/learnruby/ss/require_load.htm](http://ruby.about.com/od/learnruby/ss/require_load.htm)

About the second question, my guess is that it isn't possible to use a variable on a bash command inside ruby.

And the last question still remains unanswered...
It has to be a way to do pipes with ruby...

---

### Post by pmasiar on 2008-02-19
> **Yuzem said:**
> I have read some tutorials on using the gtk libraries and it seems simpler to do it with ruby than with python.
Thats the reason I chose ruby.
.

OK, good for you. Sorry for answering on such a newbie level, but if you stay around longer (and I hope you will, we need ruby experts to contradict Pythoneers like me :-) ) you will see that most posters did not researched question at all. You likely made decent decision - and differences between Ruby and Python is not that big anyway.

---

### Post by Yuzem on 2008-02-19
Python seems great. I choose Ruby but I still like python. :)

Now, in case someone else is looking for the same answer I have found the solution:
```
var = "hello"
`echo #{var}`
```

This also works:
```
var = "hello"
say = "echo"
`#{say} #{var}`
```

And of course pipes:
```
var = "hello"
say = "echo"
`#{say} #{var} | sed "s/$/ and good bye/"`
```

From this page:
[http://pasadenarb.com/2007/03/ruby-shell-commands.html](http://pasadenarb.com/2007/03/ruby-shell-commands.html)

This is great for someone passing from bash to ruby. :)

---

