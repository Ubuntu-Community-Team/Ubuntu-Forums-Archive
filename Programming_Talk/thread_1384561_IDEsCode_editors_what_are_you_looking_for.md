---
title: "IDEs/Code editors: what are you looking for?"
date: 2010-01-18
forum: Programming Talk
---

### Post by spupy on 2010-01-18
People, it is this time of the year again. But! This is not the typical "What is your favorite editor?" thread, which goes on 10 pages with posts that contain only "eclipse,vim,gedit,geany,emacs" etc.

Now I want to know not so much which is your favorite editor, but WHY did you make that choice. What are you looking for in an IDE/editor? Which features are 100% needed and which are dreaded? What are your working habits?

I will not mention the editors I use. (You can try guess them from my list of features I like) 
The features that I look for in an IDE/code editor:
* interface customization (I really need the new/open/save buttons </sarcasm>). This includes keys and colors.
* nice overview of opened files and their structure (file tree & members outline)
* no bloat
* fast search + replace (regex)
* little text-editing gizmos (like insert matching bracket, some auto-completion and snippet support, auto-indentation)

---

### Post by not_a_phd on 2010-01-18
So, is this market research for a new IDE? For me, it depends on the task.

For command line applications or daemons:

[LIST]
[*]Stability
[*]Good integration with the GNU Debugger
[*]Float over value information from variables during debug sessions
[*]Float over variable type and function header data during coding
[*]Tight integration with a function  man pages, and F1 access to help on the language
[/LIST]

For GUI programs:

[LIST]
[*]I would like all of the above, plus...
[*]Autogeneration of code necessary to start the GUI event loop and show the main window for the framework
[*]Autogeneration of function stubs for handling GUI events
[/LIST]
Too much to ask?

---

### Post by spupy on 2010-01-18
> **not_a_phd said:**
> So, is this market research for a new IDE? For me, it depends on the task.

For command line applications or daemons:

[LIST]
[*]Stability
[*]Good integration with the GNU Debugger
[*]Float over value information from variables during debug sessions
[*]Float over variable type and function header data during coding
[*]Tight integration with a function  man pages, and F1 access to help on the language
[/LIST]

For GUI programs:

[LIST]
[*]I would like all of the above, plus...
[*]Autogeneration of code necessary to start the GUI event loop and show the main window for the framework
[*]Autogeneration of function stubs for handling GUI events
[/LIST]
Too much to ask?

I have thrown away the urge to write my own code editor long ago.
I've never been on friendly terms with gdb. I was once talking with a fellow student, and I made an inquiry: "Does vim has good integration with gdb?" (I was (and still am) total gdb noob). And he answered: "Yes, '!gdb'." I loled. (for those not familiar with vim, '!gdb' only starts gdb like in a shell)
I do like the way eclipse has integrated a debugger.

---

### Post by Jonmarc on 2010-01-18
I have been learning XHTML/CSS in gedit and so for I have used the default preferences. I have heard a lot about the "live" css editor plugin for firefox, but I want to use an editing program not a browser. So...

- immediate screen update on css and other code
- customs colors
- clear and easy to understand tag and attribute descriptions ( so I can learn )
- else , I don't know cause I'm new

However any suggestions on what I should try or point me to a forum with suggestions.

---

### Post by spupy on 2010-01-18
> **Jonmarc said:**
> I have been learning XHTML/CSS in gedit and so for I have used the default preferences. I have heard a lot about the "live" css editor plugin for firefox, but I want to use an editing program not a browser. So...

- immediate screen update on css and other code
- customs colors
- clear and easy to understand tag and attribute descriptions ( so I can learn )
- else , I don't know cause I'm new

However any suggestions on what I should try or point me to a forum with suggestions.

Check **cssed**. It's an editor for CSS files.

---

### Post by Jonmarc on 2010-01-19
> **spupy said:**
> Check **cssed**. It's an editor for CSS files.

cssed looks great. It took a little while to get used to the auto tabs and auto fill. The only thing is it's missing is a real-time preview. The validator was very helpful. 

I wish gedit had a real-time preview like fire bug plugin.

---

### Post by diesch on 2010-01-19
> **spupy said:**
> 
Now I want to know not so much which is your favorite editor, but WHY did you make that choice. What are you looking for in an IDE/editor? Which features are 100% needed and which are dreaded? What are your working habits?


[LIST]
[*] Decent support for different tasks:
    [LIST]
    [*] writing at least HTML, Restructured Text, LaTeX, Python, Makefiles
    [*] editing config files
    [*] usable as editor for mail and news readers
    [/LIST]
[*] Fully configurable keyboard shortcuts for everything
[*] Good integration of external tools, at least make, CVS, SVN, Bazaar
[*] Decent support for makros and templates
[*] Multi window support, the same file should be editable in different windows at the same time
[/LIST]

---

