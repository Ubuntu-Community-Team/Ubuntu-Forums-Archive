---
title: "beginner steps with python, trouble with modules"
date: 2014-06-21
forum: Programming Talk
---

### Post by Drone4four on 2014-06-21
Here is a python script I have been playing with which I encountered in a tutorial on udemy.  The course is called, &#8220;Learn Python, it's CAKE (Beginners)&#8221; .  The instructor is Jason Elbourne.

I am stuck on **modules** covered in Lecture 20.

Some sample code from this lecture looks like this:

```

1 def main_xyz():
2         print "F1 Executed"
3 
4 if __name__ == '__main__':
5         main_xyz()
6 

```

If I run the script from my terminal, it prints &#8216;F1 Executed&#8217;.  I get that if I had a placeholder in the string, then I&#8217;d need a default argument in the definition.  As is, there is no argument needed to be passed to the function because its just a print statement.  I also gather that since the function, main_xyz, is the consequent in the conditional, the antecedent must be true first. Here is where I am getting hung up.  When I run this script it prints F1 Executed, but neitherdid I  satisfy the antecedent condition in the script nor manually did so somewhere in the shell.  No where did I input &#8216;__main__&#8217;, which was the condition to call the main_xyz function. I&#8217;m at a loss here.  Where is the __name__  condition satisfied? Can someone please clarify?  

Thanks for your attention.

---

### Post by michael171 on 2014-06-22
Hello, the condition __name__ == '__main__' is satisfied behind the scene when you launch
the script directly.  Because your script file can be imported into another script file
as a module, the if statement alows you to specify code that gets executed only
when your script is directly executed.  Any code after the condition only executes
when you run python yours.py and not if your script was imported from another script

also look at [http://stackoverflow.com/questions/419163/what-does-if-name-main-do](http://stackoverflow.com/questions/419163/what-does-if-name-main-do)
    
yours.py

```

def main_xyz():
     print 'F1 Executed'
    
if __name__ == '__main__':
          main_xyz()
```

loader.py:
```

import yours

```

Now if I launch python yours.py, I get 'F1 Executed' printed to the screen, if I launch loader.py
nothing happens, though it has now got your main_xyz() in memory and you can call this function
at any point inside loader.py or whatever.py

If your script had a bunch of functions, but your building a much larger application with many
script files, you could import yours.py into any of your other scripts and add special testing code
after the conditon that is not executed when your script is used as a module import, but does
get executed if you directly execute your script.

if you import your script from another script python sets __name__ to be the name of the
module and not __main__ so that the condition fails and the only code that executes
is the code outside of the condition

I had to edit this because I made a mistake in my explanation, as well I tryed to make it 
more understandable, and more acurate

---

### Post by Drone4four on 2014-06-22
OK ...so lemme get this straight:  The pseudocode form of the conditional could read something like this:

“If it’s the original script, then run the function specified.” 

This means that if its not the original script (for example if its being imported in loader.py), the function won’t be called automatically.  If I import the script in loader.py, then I’ll have the option to execute the function explicitly.  Likewise, if I were to remove the conditional from yours.py, then there would be two implications: (#1) running yours.py in the shell would yield nothing BUT also (#2) the funciton defined in yours.py could still be called in loader.py as long as its imported and referenced properly.  

I searched the official python 2.7 docs online for __main__ and for __name__ . The first result for both queries is the documentation, "[10.3 stat — Interpreting stat() results]("https://docs.python.org/2/library/stat.html?highlight=__name__")". 

Searching the docs for module returned 1000+ hits.  So I decided to browse the table of contents and came across “[27.5. __main__ -- Top-level script environment]("https://docs.python.org/2/library/__main__.html#module-__main__")” which speaks directly to what I am trying to learn.  The doc reads:
> This module represents the (otherwise anonymous) scope in which the interpreter’s main program executes — commands read either from standard input, from a script file, or from an interactive prompt. It is this environment in which the idiomatic “conditional script” stanza causes a script to run:
```

 1 if __name__ == "__main__":
 2    main()

```

The conditional just self references the script (in my case, yours.py) and runs whatever is in the code block. 

Furthermore, learning from **michael171**’s post, I also now realize that I could reuse
```

 1 if __name__ == "__main__":
 2    main()

```
in multiple modules (e.g. yours1.py, yours2.py, yours3.py) and also have it present in the parent (e.g. loader.py).  In total there would be four instances of those two lines of code, but in each instance, python would only read __name__ as a reference to itself in each script.  Python won’t run into a problem conflating __name__ across a large problem with multiple modules that have those two lines.

Is all this an accurate understanding of the modules issue I initially raised?

---

### Post by Drone4four on 2014-06-22
Interesting. I think I just learned how necessary it is to keep the conditional in.  Here are two code samples I’ve been working with:

Here is a module, saved as f2.py:
```

  1 def print_name(name):
  2         """ This will print a name """
  3         return "This is my name is, %s" % name
  4 
  5 def main():
  6         print 'F2 Executed'
  7 
  8 if __name__ == '__main__':
  9         main()
 10 

```

Here is the parent, saved as f1.py:
```

  1 import f2
  2 
  3 def main():
  4         print "F1 Executed"
  5         n = f2.print_name("Daniel")
  6         print n
  7         m = f2.main()
  8         print m
  9 
 10 if __name__ == '__main__':
 11         main()

```
It executes perfectly, I think.  Here is the output:

```

$ python f1.py 
F1 Executed
This is my name is, Daniel
F2 Executed
None
$

```
I wasn’t sure why None was printed.  I figured it might have to do with the conditional.  So I tried commenting out both lines in the module and in the parent.  Now when I execute the f1.py in the shell, nothing prints.  Likewise if I comment out the conditional in f1 but keep the conditional in in f2, then nothing gets executed.  With the conditional commented out in f2 but still kept in f1, everything prints just fine.  I figure the conditional is necessary but I don’t know why as I have been under the impression that it's only necessary when executing the script/module alone.  What is really going on?

EDIT: added a few sentences when interchanging the comments from both scripts

---

### Post by Vaphell on 2014-06-22
None is printed because you requested printing of the result of that function with *print f2.main()* ( *m=f2.main(); print m;* ). The problem here is f2.main() doesn't have any return statement that would give that function value, so None is used.

[COLOR="#0000FF"]print[/COLOR] [COLOR="#008000"]f2.main()[/COLOR]
*1. execute [COLOR="#008000"]f2.main()[/COLOR] = print some stuff from it*
**F2 Executed**
*2. [COLOR="#0000FF"]print[/COLOR] the result established during the execution of f2.main()*
**None**

you either need to change *print* to *return* in the function or call *f2.main()* alone, without *print* in front of it.

---

### Post by michael171 on 2014-06-23
Sorry for the delayed response, Vaphell is correct f2.main does not return anything so None is printed.

> This means that if its not the original script (for example if its being  imported in loader.py), the function won’t be called automatically.  If  I import the script in loader.py, then I’ll have the option to execute  the function explicitly

I think you have captured the essence of what the condition does and why it is needed. That explains it nicely, great job.

---

### Post by ofnuts on 2014-06-23
This "feature" is a good way to add test code to a module. To test the module you just have to call it from the command line and it will run its own unit testing.

---

### Post by Drone4four on 2014-06-23
This feature is useful because it gives the programmer the ability to debug/troubleshoot.  My concluding remark is a simple question: Is it best practices to include this conditional as boilerplate appended to the bottom of EVERY python script I write in the future? How common are situations where it wouldn't be necessary?

btw, thanks goes out to: **michael171**, **Vaphell**, and **ofnuts** for your helpful comments.

---

