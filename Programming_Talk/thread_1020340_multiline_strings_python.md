---
title: "multiline strings python"
date: 2008-12-24
forum: Programming Talk
---

### Post by go_beep_yourself on 2008-12-24
Where can I request multiline comments for python in the new upcoming 3.0? Every other language I've encourtered has them and doesnt expect you to make them into strings. This a crappy hackish way of doing things even according to my book author who's been studying Python for over 10 years and teaching it all over the place+. I would suggest using three # hash marks to comment a code block.

---

### Post by Greyed on 2008-12-24
I'm thinking python.org?

---

### Post by Xiong Chiamiov on 2008-12-24
3.0 [is released]("http://python.org/download/"), but irc or mailing lists?

---

### Post by wmcbrine on 2008-12-24
```

# Is there something wrong
# with commenting like this?

# Do you really need to say
# all that much in a comment?

# Is the fact that "every other
# language has it" really a
# good reason to adopt it?

""" Multi-line docstrings aren't
    just comments, either. They're
    a more powerful thing. You
    should read up on them. Perhaps
    from a different book.

"""

```

Incidentally, the form of Python comments is the same as is used in shell scripts, makefiles, Perl, and other "scripting" languages. So, there are some other languages that don't have explicit multi-line comment delimiters.

---

### Post by Greyed on 2008-12-24
Pardon my devil's advocate moment here.

Mutliline comments are good for when you want to remove a large block of code from consideration but not remove it from source.  EG:

```

def foo(): # second version we're working on to replace the first version
    some code
    some other code
    even more code

/**
def foo():  # first version left in source but commented out for reference
    some other code
    even more code
    some code
**/

```Imagine 30-40 lines between the multi-line comment markers (/** **/) and having to put a hash in front of each of those.

Of course with a decent RCS and/or utilizing language constructs to their fullest that requirement is minimized.

---

### Post by scooper on 2008-12-24
Somehow I've never missed multi-line comment blocks in Python.  I've evolved to also not use them in C++ or Java.  Even to comment out code, I find that marking each line is much clearer.  I frequently enhance the comment marker, e.g. as "#XX" to flag commented out lines.  It allows me to easily search and delete commented out blocks, e.g. before checking back in to source control.

It's easy to mark and unmark block lines in a good editor, particularly with rectangular selections.  It's also easier to make mistakes when the marker is only at the beginning and end of a block, but that's admittedly a weak argument.

I generally prefer to delete code blocks and rely on Subversion, or some other SCM tool, to recover it.

Python's ease of programming also reduces the motivation to consider lines of code "precious", and I focus more on the structure and design, rather than code.  If the code is really brilliant, but unused, I'd move it to another file.  I find visual flow more important than the potential loss of historical code, particularly because Python provides such clean and readable syntax.

Just contributing my 2 cents, because your question made me try to think about why I never missed such a feature. :)

---

### Post by Greyed on 2008-12-24
> **scooper said:**
> Python's ease of programming also reduces the motivation to consider lines of code "precious", and I focus more on the structure and design, rather than code.  If the code is really brilliant, but unused, I'd move it to another file.  I find visual flow more important than the potential loss of historical code, particularly because Python provides such clean and readable syntax.

Well, my example wasn't so much for historical code.  Historical code should be relegated to the care of your RCS.  My example was when you're rewriting a function and want to keep the old functional code in place for reference until you're satisfied with the rewrite.

I do this often when I think of a better way to do something but want to leave the old way in place, but unused, so as to remind me of all that the new function needs to do as well as a reminder of where I've been as I work on where I think I need to go.  Once the new function is finished to my satisfaction the old code gets deleted, not uncommented.

---

### Post by pmasiar on 2008-12-24
> **go_beep_yourself said:**
> Where can I request multiline comments for python in the new upcoming 3.0? 

You are too late for Python 3000 - wait for Python 4000 :-)

> This a crappy hackish way of doing things 

Don't use crappy editor then. Any decent editor can be customized to toggle (comment/uncomment) selected block, and having comment char is nice reminder. 

BTW you can use """ or ''' multiline string as comments, compiler would just ignore those string literals if not assigned.

---

