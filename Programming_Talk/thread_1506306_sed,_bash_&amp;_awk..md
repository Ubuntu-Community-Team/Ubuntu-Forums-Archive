---
title: "sed, bash &amp; awk."
date: 2010-06-10
forum: Programming Talk
---

### Post by Drenriza on 2010-06-10
Currently im reading alot about sed, bash & awk.

But a question i havnt found an answer to is.
When i make a #!/bin/bash script

can i then directly in my bash script add sed commands?

what i want to do is that i want sed to edit a (deleting all text) text file, from my bash script. Add some new text in the empty text file, that i have specified. And then continuing on with the rest of the script.

Thanks on advance
Kind Regards

---

### Post by Bachstelze on 2010-06-10
Basically, you put in you shell script the same commands you would run in a "normal" shell session, so yes, you can very well run sed from inside a shell script.

You shouldn't need sed for what you want to do, though, just do something like:

```
#!/bin/sh

echo "This is
some new text
that will go into foo.txt,
replacing the original contents." > foo.txt
```

---

### Post by Drenriza on 2010-06-10
so your saying i can use the echo command to replace some text in a file?

but will the echo command then also delete any existing text, or does it just add to the existing text in the file?

---

### Post by Bachstelze on 2010-06-10
> **Drenriza said:**
> so your saying i can use the echo command to replace some text in a file?

but will the echo command then also delete any existing text, or does it just add to the existing text in the file?

The echo command writes text to standard output. The '>' redirects output to a file, so the combination of both will write the text to the given file, overwriting its current contents. For appending at the end of the file, use '>>'.

---

### Post by Drenriza on 2010-06-10
ye thats faster.

was gonna use ```
sed 'x'xd' file
```

to delete the lines and then modify the file afterwards.

can bash understand init (number) for example ```
init 6
```

---

### Post by trent.josephsen on 2010-06-10
Bash doesn't *understand* commands, except for a few built-ins and keywords like if, elif, else, for, while, do, done, and half a dozen others I've forgotten.  Even things we often think of as integral to the language, like [ and **true**, are (sometimes) external commands.  Any line that doesn't invoke a built-in (or contain an obvious syntax error) causes bash to call an external program.

So "init 6" is fine in your program.  "init 132" would be fine as far as bash is concerned, but init will complain because 132 is not a valid runlevel.  "who what when where why" would invoke the who command with 4 additional arguments, and who will complain because it has been mis-invoked, but bash will carry on because it did what was required of it.

---

### Post by amauk on 2010-06-10
Bash is a shell
(the thing that runs when you open up a terminal, and acts on user input)

A bash script is just a scripted sequence of commands (and flow control) that Bash executes

Anything you can do on the bash CLI, you can put into a bash script

---

