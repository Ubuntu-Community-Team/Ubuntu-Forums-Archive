---
title: "bash question about color"
date: 2007-09-25
forum: Programming Talk
---

### Post by peterv6 on 2007-09-25
I've searched the forums, and found out how to get the ls command to show files in colors, but what I'm trying to figure out is how to get vi (vim) to show color language syntax.  Can anyone help me out?  Also, how can I change the color choices for the ls command and the syntax?
Thanks....

---

### Post by LaRoza on 2007-09-25
[http://vimdoc.sourceforge.net/htmldoc/syntax.html](http://vimdoc.sourceforge.net/htmldoc/syntax.html)

(for vim)

---

### Post by Compyx on 2007-09-26
Since the question about vim has already been answered, here's how to change the colors of the 'ls --color=always' command:

You can use the command 'dircolors' to output the current settings. So basically you'd save that output in a file and tinker with it and then put it near the end of your .bashrc file.

As to what these codes mean in the LS_COLORS line, that's up to you to find out.

---

### Post by dwhitney67 on 2007-09-26
How does one disable the vim feature of automatically inserting a comment line when inserting above or below an existing comment line?

That link provided by LaRoza is too "thick" with generalities that the solution I seek is not apparent.

---

### Post by Compyx on 2007-09-26
> **dwhitney67 said:**
> How does one disable the vim feature of automatically inserting a comment line when inserting above or below an existing comment line?

That link provided by LaRoza is too "thick" with generalities that the solution I seek is not apparent.

A quick google search for 'vim disable comments' came up with this:
[http://www.vim.org/tips/tip.php?tip_id=1361]("http://www.vim.org/tips/tip.php?tip_id=1361")

---

### Post by dwhitney67 on 2007-09-26
Thanks for the tip.  I found that the solution presented was not exactly what I wanted because even though a "// " would not show up on the next line, the cursor was automatically indented to the column directly below the first character of the comment statement.

To clarify the problem, here is an example of what I see:

```
[FONT="Courier New"]// This is a comment.
   next line[/FONT]
```

If my cursor is on the comment line, and I select 'o' to insert a line below the comment line, then cursor ends up being at column 4, not column 0 (as I want).

However using my cleverness (:)), I was able to figure out that what I really needed was to insert this statement into my ~/.vimrc:

[FONT="Courier New"]au FileType c,cpp set comments=[/FONT]

Anyhow, once again thanks for the tip.

---

### Post by mssever on 2007-09-26
In vim, type ```
:set noautoindent
```You can put that in your ~/.vimrc if you like.

---

### Post by dcraven on 2007-10-30
I think what you actually want is ":set fo-=o" instead of the above. See ":he fo-table" for more information.

Cheers,
~djc

---

### Post by dwhitney67 on 2007-10-30
I ended up going with this:

```
au FileType * setlocal comments=
```

If I want comments in my code, regardless of the type of file I am editing, then I will type them in.  I do not require vim to do it for me.

---

