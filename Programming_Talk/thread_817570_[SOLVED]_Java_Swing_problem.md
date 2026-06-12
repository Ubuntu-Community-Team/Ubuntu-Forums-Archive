---
title: "[SOLVED] Java Swing problem"
date: 2008-06-03
forum: Programming Talk
---

### Post by smmalis on 2008-06-03
I am working on  a little Java program, but it doesn't want to work for me.  It is supposed to solve SuDoKu puzzles.  This is a port of the text-based version, which worked perfectly.  Any ideas?

---

### Post by Zugzwang on 2008-06-04
Ok, so
[LIST=1]
[*]First of all, when seeking help, please tell us what the problem is. "It doesn't work" isn't very precise.
[*]When drawing a grid, use a Layout made for grids, like GridBagLayout (my personal favourite for almost everything in Swing). Resize your window and you'll see what I mean.
[*]In your ActionListener, use *curled braces* to seperate the cases. You in fact just trapped into the "dangling else" problem. Use google to find out what this is. For fixing it, just transform every code of the form
```

if (bar)
  foo
else
  foobar

```
into:
```

if (bar) {
  foo
} else {
  foobar
}

```
And suddenly, your "Clear" button will start working.

With regards to the "Solve" button: Your solving procedure doesn't seem to work. But it is called correctly. For seeing this, add an 'System.out.println("I am solving!");' as the first line of the solve procedure and see that this is printed to the console whenever you click the "Solve" button.
[/LIST]

---

### Post by smmalis on 2008-06-04
Thank you for the help.  I've never heard of the 'dangling else' problem, but it does make sense.  Any ideas as to why the solve function doesn't work?  It worked in the text version.  It is being called, but it doesn't seem to do anything.

---

### Post by Zugzwang on 2008-06-04
> **smmalis said:**
> Any ideas as to why the solve function doesn't work?  It worked in the text version.  It is being called, but it doesn't seem to do anything.

No, I don't even have a clue what algorithm you are using. Just one general tip: It is considered to be good style to read all values out of the GUI beforehand, use the algorithm and then write everything back, separating GUI and algorithmic stuff. Most people will also separate these into different classes.

Then you can use your debugger to inspect the input & output values before/after the solve() function is/has been called. This will help you to spot the error.

---

### Post by smmalis on 2008-06-04
I've figured out the problem (sort of).  The if statement:
```
if (grid[i][j].getText() != "")
```
always evaluates to true.  I can't figure out why this is.

---

### Post by smmalis on 2008-06-04
Fixed it!  I forgot that Strings can't use == or !=.  so the if statement is now:
```
if (!grid[i][j].getText().equals(""))
```

---

### Post by NormR2 on 2008-06-04
That's true for most classes. To compare the contents of a class requires a method call.

---

