---
title: "[Python] sys.path.append(&quot;..&quot;)"
date: 2010-08-31
forum: Programming Talk
---

### Post by dodle on 2010-08-31
I have used the following lines of code to enable importing modules from an upper directory:

[php]import sys
sys.path.append("..")[/php]

But I am wondering if this might cause problems when I install my program.  Would it be better to do the following?

[php]import sys, os
sys.path.append(os.path.join(os.path.dirname(__file__), ".."))[/php]

Is that enough detail, or do I need explain myself better?

---

### Post by ssam on 2010-08-31
when you install a python package it will go into one of the python module directories, so it will already be on the python path.

---

### Post by surfer on 2010-08-31
the second version is much better. if you start you python program from a different working directory the first version will not work.

---

### Post by dodle on 2010-08-31
> **surfer said:**
> the second version is much better. if you start you python program from a different working directory the first version will not work.

Okay, thank you.  That is what I was worried about.

---

### Post by yalyari on 2010-08-31
> **surfer said:**
> the second version is much better. if you start you python program from a different working directory the first version will not work.

Not exactly.
sys.path is relative to the directory which python program exist, regardless of the current directory you run the Python program. Both are identical.

It's surprising and looks buggy at first, but I think it's the right behavior.

---

### Post by surfer on 2010-08-31
> **yalyari said:**
> Not exactly.
sys.path is relative to the directory which python program exist, regardless of the current directory you run the Python program. Both are identical.

It's surprising and looks buggy at first, but I think it's the right behavior.

that is true, but  [COLOR=#000000][COLOR=#0000bb]sys[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]path[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]append[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]".."[/COLOR][COLOR=#007700])  [/COLOR][/COLOR]will append a path relative to the current working directory. just as [COLOR=#000000][COLOR=#0000bb]sys[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]path[/COLOR][COLOR=#007700].[/COLOR][COLOR=#0000bb]append[/COLOR][COLOR=#007700]([/COLOR][COLOR=#dd0000]"."[/COLOR][COLOR=#007700]) [/COLOR][/COLOR] will append the current working directory. 

(huh?! were do these colors come from?!)

---

### Post by Bachstelze on 2010-08-31
> **surfer said:**
> 
(huh?! were do these colors come from?!)

You are probably using the WYSIWYG editor.

---

### Post by surfer on 2010-09-01
> **Bachstelze said:**
> You are probably using the WYSIWYG editor.

you're right, i am. i'll switch back to default.

---

